# 🏗️ Muziso Architecture Documentation

**Current Version:** v0.1.8  
**Supported Ecosystems:** Desktop (Windows, macOS, Linux) &amp; Mobile (Android)

---

## 🌟 Ecosystem Overview

Muziso is engineered across two dedicated native architectures tailored for high-fidelity audio playback:
1. **Desktop Engine**: Built with **React 19 (TypeScript)** + **Tauri v2 (Rust)** + **GStreamer FFI** + **SQLite (`rusqlite`)**.
2. **Mobile Engine**: Built with **Native Android (Kotlin)** + **Jetpack Media3 / ExoPlayer** + **MediaSessionCompat Foreground Service** + **Room SQLite Database**.

---

## 🏛️ High-Level System Architecture

### 💻 Desktop Architecture (Tauri v2 + Rust)
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

### 📱 Mobile Architecture (Android Kotlin)
```
┌─────────────────────────────────────────────────────────────────┐
│                     Native Kotlin UI Layer                      │
│        (Jetpack Compose / ViewBinding, MVI Architecture)        │
└────────────────────────────────┬────────────────────────────────┘
                                 │  ViewModel & Kotlin StateFlow
┌────────────────────────────────▼────────────────────────────────┐
│                   Foreground Audio Service                      │
│            (MediaSessionCompat, Audio Focus Manager)            │
├─────────────────────┬──────────────────┬────────────────────────┤
│ Playback Engine     │ Persistence      │ Network & CDN          │
│ - Jetpack Media3    │ - Room Database  │ - OkHttp Client        │
│ - ExoPlayer 320kbps │ - Encrypted DAO  │ - JioSaavn API Engine  │
│ - Hardware Offload  │ - Offline Cache  │ - Spotify Art Resolver │
└─────────────────────┴──────────────────┴────────────────────────┘
```

---

## 🎧 Audio Engine & Stream Resolvers

Muziso implements a multi-tier hybrid audio resolution pipeline across Desktop and Mobile:

1. **JioSaavn 320 kbps Direct CDN Resolver**:
   - Audio URLs are resolved in **<30ms** via Strategy 0 direct API lookup (`song.getDetails&pids={id}`).
   - Streams are fetched directly from high-speed 320 kbps CDN endpoints without intermediary transcoding delay.

2. **Native GStreamer Audio Pipeline (Desktop)**:
   - Decodes high-bitrate network streams (`.mp3`, `.flac`, `.opus`, `.m4a`, `.wav`) using native Rust GStreamer FFI bindings.
   - Dynamically injects bundled GStreamer dynamic libraries (`.dll`) at runtime on Windows.

3. **Jetpack Media3 & ExoPlayer Pipeline (Android Mobile)**:
   - Leverages hardware audio offloading and gapless buffer preloading.
   - Coordinates with `MediaSessionCompat` to keep background music active while device is locked.

---

## 🎨 Guaranteed Official Cover Image Engine

1. **Deep Metadata Extraction**:
   - Parses `item["image"]`, `item["more_info"]["image"]`, `item["more_info"]["album_image"]`, and `item["album_image"]`, scaling thumbnails up to **500x500 official high-res album covers**.

2. **Spotify Cover Enrichment Resolver**:
   - Any track lacking a verified cover image is enriched asynchronously via Spotify's official Web API, returning verified **640x640 album artwork**.

---

## 🔄 Smart Version-Preserving Deduplication Engine

- **Compilation Collapse**: Strips redundant album compilation prefixes to collapse duplicate entries of the same song across compilation albums into 1 clean listing.
- **Version Protection**: Preserves version descriptor keywords (`Remix`, `Reprise`, `Unplugged`, `Acoustic`, `Lofi`, `Extended`, `Instrumental`, `Tamil`, `Telugu`, `Hindi`, `Malayalam`, `Kannada`) so alternate studio recordings remain distinct.

---

## 💾 Local Storage & Database Schema

All user data is stored strictly on the local client:
- **Desktop**: SQLite database (`muziso.db`) managed via `rusqlite`.
- **Mobile**: Room SQLite database with typed DAOs and Kotlin Flow observers.

### Key Entities:
- **Tracks**: Title, artist, album, duration, file path / stream URL, bitrate, cover art blob reference, and local checksum.
- **Playlists**: Custom user-ordered playlists and tags.
- **Play History**: Local play counts and playback timestamps for smart autoplay recommendations.
- **Offline Cache**: Registry of downloaded audio files stored in sandboxed local application directories.
