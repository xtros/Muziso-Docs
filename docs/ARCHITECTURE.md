# 🏗️ Muziso Architecture Documentation

## Overview

Muziso is built as a cross-platform desktop application leveraging **Tauri v2** for system integration and performance, **React 19 (TypeScript)** for its glassmorphic user interface, **GStreamer & Rodio** for native audio decoding and FFI playback, and **SQLite (`rusqlite`)** for local metadata storage.

---

## 🏛️ High-Level System Architecture

```
┌────────────────────────────────────────────────────────┐
│                   React 19 Frontend                    │
│      (TypeScript, Framer Motion, Lucide Icons)        │
└───────────────────────────┬────────────────────────────┘
                            │  Tauri v2 IPC (Events/Commands)
┌───────────────────────────▼────────────────────────────┐
│                    Rust Desktop Core                   │
│               (Tauri v2, Async Tokio)                  │
├─────────────────────┬───────────────────┬──────────────┤
│ Audio Pipeline      │ Database          │ Sidecars     │
│ - GStreamer (FFI)   │ - SQLite          │ - yt-dlp     │
│ - Rodio             │   (rusqlite)      │ - spotiflac  │
│ - Lofty (Metadata)  │                   │              │
└─────────────────────┴───────────────────┴──────────────┘
```

---

## 🎧 Audio Engine & Pipeline

Muziso implements a dynamic hybrid audio playback model:

1. **GStreamer FFI Binding (`gstreamer`, `gstreamer-audio`)**:
   - Handles high-bitrate network streams, custom audio sink routing, and multi-format audio decoding (`.flac`, `.opus`, `.m4a`, `.mp3`).
   - On Windows, the app programmatically injects paths to bundled GStreamer dynamic libraries (`.dll`) at runtime, preventing system dependency conflicts.

2. **Rodio Audio Engine (`rodio`)**:
   - Serves as a fallback for local playback streams and lightweight sound effect rendering using `symphonia-all` feature set.

3. **Stream Resolution Engine (`yt-dlp`)**:
   - Online audio streams are resolved on-demand by invoking a sandboxed `yt-dlp` sidecar binary located in `src-tauri/bin/yt-dlp.exe`.
   - Extracted direct audio URLs are passed directly into the GStreamer FFI pipeline.

---

## 💾 Local Storage & Database Schema

Muziso utilizes a local SQLite database (`muziso.db`) managed via `rusqlite` bundled with static compilation.

### Key Entities:
- **Tracks**: Stores track title, artist, album, duration, file path / stream URL, bitrate, cover art blob reference, and local file checksum.
- **Playlists**: User-created playlists with ordering and custom thumbnail configurations.
- **Play History & Analytics**: Tracks play counts, skip ratios, and date timestamps for smart queue recommendations.
- **Offline Cache**: Index of downloaded tracks stored in the user's `$APPDATA` directory.

---

## 🎮 Discord Rich Presence (`discord-rich-presence`)

When enabled in app settings, Muziso broadcasts active playback state to Discord:
- **Activity State**: Track name & Artist
- **Timestamps**: Elapsed track duration and total length
- **Small / Large Images**: Muziso logo and album art artwork references

---

## 🛡️ Security & Sandboxing

- **Asset Protocol**: Configured via Tauri's `assetProtocol` with restricted filesystem scope limited to `$HOME/**/*` and `$APPDATA/**/*`.
- **Sidecar Isolation**: External binaries (`yt-dlp`, `spotiflac-cli`) are declared strictly in `tauri.conf.json` under `externalBin` and `resources`.
