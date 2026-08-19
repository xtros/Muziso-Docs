# 🏗️ Muziso Architecture Documentation

**Current Version:** v0.1.8  

---

## Overview

Muziso is built as a cross-platform desktop application leveraging **Tauri v2** for system integration and performance, **React 19 (TypeScript)** for its glassmorphic user interface, **JioSaavn & Spotify Web APIs** for instant audio stream resolution and official artwork, **GStreamer & Rodio** for native audio decoding and FFI playback, and **SQLite (`rusqlite`)** for local metadata persistence.

---

## 🏛️ High-Level System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                       React 19 Frontend                         │
│         (TypeScript, Framer Motion, Cyber-Minimal UI)           │
└────────────────────────────────┬────────────────────────────────┘
                                 │  Tauri v2 IPC (Events/Commands)
┌────────────────────────────────▼────────────────────────────────┐
│                        Rust Desktop Core                        │
│                   (Tauri v2, Async Tokio)                       │
├─────────────────────┬──────────────────┬────────────────────────┤
│ Audio & Resolvers   │ Database         │ Sidecars & Art Engine  │
│ - JioSaavn 320kbps  │ - SQLite         │ - yt-dlp sidecar       │
│ - GStreamer (FFI)   │   (rusqlite)     │ - Spotify Cover API    │
│ - Rodio Engine      │                  │ - spotiflac-cli        │
└─────────────────────┴──────────────────┴────────────────────────┘
```

---

## 🎧 Audio Engine & Stream Resolvers

Muziso implements a multi-tier hybrid audio resolution pipeline:

1. **JioSaavn 320 kbps Direct CDN Resolver (`jiosaavn.rs`)**:
   - Audio URLs are resolved in **<30ms** via Strategy 0 direct API lookup (`song.getDetails&pids={id}`).
   - Streams are fetched directly from high-speed 320 kbps CDN endpoints without intermediary conversion steps.

2. **Stream Resolution Engine (`yt-dlp` sidecar)**:
   - For YouTube/SoundCloud URLs, direct audio streams are resolved on-demand via a sandboxed `yt-dlp` sidecar binary located in `src-tauri/bin/yt-dlp.exe`.

3. **Native GStreamer & Rodio Audio Pipeline (`audio.rs`)**:
   - Decodes high-bitrate network streams (`.mp3`, `.flac`, `.opus`, `.m4a`, `.wav`) using native Rust GStreamer FFI bindings.
   - Dynamically injects bundled GStreamer dynamic libraries (`.dll`) at runtime on Windows.

---

## 🎨 Guaranteed Official Cover Image Engine (`news.rs` & `spotify.rs`)

1. **Deep Field Extraction**:
   - Parses `item["image"]`, `item["more_info"]["image"]`, `item["more_info"]["album_image"]`, and `item["album_image"]`, scaling thumbnails up to **500x500 official high-res album covers**.

2. **Spotify Cover Enrichment Resolver**:
   - Any track lacking a cover image is enriched asynchronously via Spotify's official Web API (`fetch_spotify_cover_image`), returning verified **640x640 album artwork**.

---

## 🔄 Smart Version-Preserving Deduplication Engine (`getSmartDedupKey` / `clean_dedup_key`)

- **Compilation Collapse**: Strips movie/subtitle metadata tags (e.g. `(From "3")`, `(The Innocence of Love)`, `(Best of 2025)`) to collapse duplicate entries of the exact same audio track across different compilation albums into 1 single clean entry.
- **Version Protection**: Preserves version descriptor keywords (`Remix`, `Reprise`, `Unplugged`, `Acoustic`, `Lofi`, `Extended`, `Instrumental`, `Tamil`, `Telugu`, `Hindi`, `Malayalam`, `Kannada`) so alternate versions remain accessible.

---

## 👨‍🎤 Official Artist Discography Sourcing

- Artist Pages query official studio albums and singles exclusively (`include_groups=album,single`), bypassing third-party playlists and compilations.
- Strict performing-artist metadata filtering ensures only songs performed by the target artist are listed.

---

## 💾 Local Storage & Database Schema (`muziso.db`)

Muziso utilizes a local SQLite database (`muziso.db`) managed via `rusqlite` bundled with static compilation.

### Key Entities:
- **Tracks**: Stores track title, artist, album, duration, file path / stream URL, bitrate, cover art blob reference, and local file checksum.
- **Playlists**: User-created playlists with custom ordering and artwork.
- **Play History & Analytics**: Tracks play counts, skip ratios, and date timestamps for smart queue recommendations.
- **Offline Cache**: Index of downloaded tracks stored in the user's `$APPDATA` directory.

---

## 🎮 Discord Rich Presence (`discord_rpc.rs`)

When enabled in app settings, Muziso broadcasts active playback state to Discord:
- **Activity State**: Track title & Artist name
- **Timestamps**: Elapsed track duration and total length
- **Image Assets**: Muziso logo and album artwork references
