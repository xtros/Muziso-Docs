# 🎵 Muziso

<p align="center">
  <img src="assets/logo.png" alt="Muziso Official Logo" width="160" />
</p>

<p align="center">
  <img src="assets/dashboard.png" alt="Muziso Dashboard" width="70%" />
</p>

<p align="center">
  <a href="https://xtros.github.io/Muziso-Docs/"><img src="https://img.shields.io/badge/Documentation-GitHub%20Pages-ccff00?style=for-the-badge&logo=githubpages&logoColor=black" alt="Documentation Site" /></a>
  <a href="https://github.com/xtros/Muziso/releases"><img src="https://img.shields.io/github/v/release/xtros/Muziso?color=ccff00&label=Release%20v0.1.8&style=for-the-badge" alt="Latest Release v0.1.8" /></a>
  <a href="https://github.com/xtros/Muziso/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-ccff00?style=for-the-badge" alt="MIT License" /></a>
  <img src="https://img.shields.io/badge/Platforms-Desktop%20%7C%20Android%20Mobile-181825?style=for-the-badge&logo=android" alt="Platforms" />
  <img src="https://img.shields.io/badge/Desktop-Tauri%20v2%20%2B%20Rust-FFC107?style=for-the-badge&logo=tauri&logoColor=black" alt="Tauri v2" />
  <img src="https://img.shields.io/badge/Mobile-Native%20Kotlin-7F52FF?style=for-the-badge&logo=kotlin&logoColor=white" alt="Kotlin Android" />
</p>

<p align="center">
  <b>Muziso</b> is a premium, dark-themed music player ecosystem engineered for both <b>Desktop (Windows, macOS, Linux)</b> and <b>Mobile (Android)</b>. Powered by high-performance <b>React 19 + Tauri v2 (Rust)</b> on Desktop and <b>Native Kotlin + Jetpack Media3</b> on Android Mobile, Muziso delivers sub-30ms 320 kbps JioSaavn streaming, smart version-preserving deduplication, official Spotify 640x640 artwork resolution, local library playback, and 100% offline caching.
</p>

<p align="center">
  📖 <b><a href="https://xtros.github.io/Muziso-Docs/">Visit the Live Interactive Documentation Web Site</a></b>
</p>

---

## 📚 Documentation & Legal Links

- 🌐 **[GitHub Pages Documentation Site](https://xtros.github.io/Muziso-Docs/)**: Interactive documentation, dual download hubs, architecture diagrams, and release notes.
- 🏗️ **[Architecture Guide](docs/ARCHITECTURE.md)**: Deep dive into Desktop (Tauri IPC, GStreamer, Rust FFI) and Mobile (Kotlin, MediaSessionCompat, Jetpack Media3, Room SQLite).
- ⚡ **[Installation & Build Guide](docs/INSTALLATION.md)**: Step-by-step installation guides for Windows, macOS, Linux, and Android APK sideloading.
- 🤝 **[Contributing & Bug Hunter Program](docs/CONTRIBUTING.md)**: Contribution standards and bounty rewards.
- 🔒 **[Privacy Policy](https://xtros.github.io/Muziso-Docs/#privacy)**: Privacy-first commitment, zero telemetry disclosure, local SQLite encryption.
- ⚖️ **[Terms & Conditions](https://xtros.github.io/Muziso-Docs/#terms)**: Open-source licensing terms and third-party media disclaimers.

---

## 🌟 Key Features (v0.1.8)

### ⚡ Universal & Streaming Capabilities
- 🚀 **JioSaavn Direct 320 kbps Streaming**: Sub-30ms instant CDN audio resolution (`song.getDetails&pids={id}`) for tracks, albums, search queries, and playlists.
- 🔄 **Smart Version-Preserving Deduplication**: Automatically collapses identical song re-releases across compilation albums while preserving legitimate alternate versions & language dubs (`Remix`, `Unplugged`, `Acoustic`, `Lofi`, `Tamil`, `Telugu`, `Hindi`, `Malayalam`, `Kannada`).
- 🎨 **Guaranteed Official High-Res Artwork Engine**: Deep artwork metadata extraction paired with an automatic Spotify **640x640 official cover resolver** for every track.
- 👨‍🎤 **Official Artist Discography Sourcing**: Queries official studio albums and singles exclusively (`include_groups=album,single`), filtering out third-party playlists and compilations.
- 📥 **Offline Download & Local Caching**: Save tracks locally for immediate offline playback with custom metadata and artwork indexing.
- 🔒 **100% Local Privacy**: Zero telemetry, zero analytics scripts. All library data and playlists remain sandboxed on your device.

### 💻 Desktop-Specific Features (Windows, macOS, Linux)
- 🎚️ **10-Band Graphic Equalizer & Studio DSP**: 31Hz–16kHz faders with live frequency DSP curve and genre presets.
- 🎮 **Discord Rich Presence**: Real-time display of currently playing track, artist name, duration, and cover art on your Discord profile.
- ⌨️ **Global Hotkeys**: Control playback (Play/Pause, Next, Previous) system-wide even when minimized.
- 🎧 **Hybrid Audio Engine**: Scan and play local music folders (`.mp3`, `.m4a`, `.wav`, `.opus`, `.flac`) alongside dynamic streams.

### 📱 Mobile-Specific Features (Android)
- 🔔 **Background Playback & Lockscreen Controls**: Android `MediaSessionCompat` foreground audio service with persistent notification tray scrubbing.
- 🎧 **Smart Audio Focus & Bluetooth**: Auto-pause on headphone disconnect / incoming calls; auto-resume on Bluetooth reconnect.
- 🔋 **Battery-Optimized Kotlin Engine**: Hardware audio decoding and low-power coroutine dispatchers for all-day listening.
- 📂 **Local Device Storage Indexing**: Scan SD cards and internal storage for local audio tracks.

---

## 🖼️ Gallery

<table>
  <tr>
    <td align="center" colspan="2" width="100%">
      <b>🏠 Main Dashboard &amp; High-Res Music Explorer</b><br/>
      <sub>Trending charts, 320 kbps JioSaavn direct streaming &amp; instant search</sub><br/><br/>
      <img src="assets/dashboard.png" alt="Muziso Main Dashboard" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <b>🎧 Immersive Fullscreen Audio Player</b><br/>
      <sub>Ambient artwork blur &amp; 3D vinyl disc animation</sub><br/><br/>
      <img src="assets/player.png" alt="Muziso Audio Player" width="100%" />
    </td>
    <td align="center" width="50%">
      <b>📂 Your Library &amp; Custom Playlists</b><br/>
      <sub>Local music import, Liked Songs &amp; playlist management</sub><br/><br/>
      <img src="assets/library.png" alt="Muziso Your Library" width="100%" />
    </td>
  </tr>
  <tr>
    <td align="center" width="50%">
      <b>🎚️ 10-Band Graphic Equalizer &amp; Studio DSP</b><br/>
      <sub>31Hz–16kHz faders, live frequency curve &amp; genre presets</sub><br/><br/>
      <img src="assets/equalizer.png" alt="Muziso Graphic Equalizer" width="100%" />
    </td>
    <td align="center" width="50%">
      <b>👤 Account Profile &amp; Listening Statistics</b><br/>
      <sub>Avatar customization, member status &amp; playback stats</sub><br/><br/>
      <img src="assets/profile.png" alt="Muziso Account Profile" width="100%" />
    </td>
  </tr>
</table>

---

## ⚡ Download & Installation

Visit the **[Muziso Releases Page](https://github.com/xtros/Muziso/releases)** to download the latest installer or APK (`v0.1.8`):

### 💻 Desktop Packages
| Platform | Package Format | Direct Download |
| :--- | :--- | :--- |
| **Windows** | `.exe` / `.msi` / `.zip` | [Download Setup.exe](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64-setup.exe) • [.msi](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64_en-US.msi) • [.zip](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64.zip) |
| **macOS** | `.dmg` / `.app` | [Download .dmg (Universal)](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64.dmg) • [Bundle](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_universal.app.tar.gz) |
| **Linux** | `.AppImage` / `.deb` | [Download .AppImage](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_amd64.AppImage) • [.deb](https://github.com/xtros/Muziso/releases/latest/download/muziso_0.1.8_amd64.deb) |

### 📱 Mobile Packages
| Platform | Package Format | Direct Download |
| :--- | :--- | :--- |
| **Android** | `.apk` (Direct Sideload) | [Download Muziso_v0.1.8.apk](https://github.com/xtros/Muziso/releases/latest/download/Muziso_v0.1.8.apk) |
| **Google Play** | App Store Listing | [Muziso on Google Play](https://github.com/xtros/Muziso/releases) |

> [!NOTE]
> **Windows SmartScreen Notice**: Because Muziso is an open-source binary without a paid commercial certificate, Windows Defender SmartScreen may display an *"Unknown Publisher"* prompt on first launch. Click **"More info"** &rarr; **"Run anyway"** to continue.

---

## 🛠️ Technology Stack

### 💻 Desktop Architecture
- **Frontend Core**: React 19, TypeScript, Framer Motion, Lucide Icons
- **Desktop Runtime**: Tauri v2, Rust FFI
- **Audio Pipeline**: JioSaavn 320kbps CDN Resolver + GStreamer (Rust Bindings) + Rodio
- **Artwork Engine**: Spotify Official 640x640 Web API Resolver
- **Database**: SQLite (`rusqlite`)

### 📱 Mobile Architecture (Android)
- **Application Core**: Native Android (Kotlin), Coroutines, ViewModel, Flow
- **Audio Pipeline**: Jetpack Media3, ExoPlayer, MediaSessionCompat Foreground Service
- **Network & CDN**: OkHttp, Retrofit 320kbps Stream Decoder
- **Database**: Room SQLite Database (Encrypted DAOs)

---

## 🚀 Development Setup

### 1. Desktop Development (Tauri v2 + React 19)
```bash
# Clone the repository
git clone https://github.com/xtros/Muziso.git
cd Muziso

# Install Node dependencies
npm install

# Run Desktop app in development mode
npm run tauri dev
```

### 2. Android Mobile Development (Kotlin + Gradle)
```bash
# Navigate to Android directory
cd android

# Compile debug build APK
./gradlew assembleDebug
```

---

## 🎯 Bug Hunter Reward Program

Found a functional bug, stream error, or UI glitch in **Muziso** Desktop or Mobile? Help improve the platform and get rewarded! See **[CONTRIBUTING.md](docs/CONTRIBUTING.md)** for issue templates and guidelines.

---

## 📜 License & Legal

- **Software License**: Distributed under the MIT License. See [`LICENSE`](https://github.com/xtros/Muziso/blob/main/LICENSE) for details.
- **Privacy Policy**: See **[Privacy Policy](https://xtros.github.io/Muziso-Docs/#privacy)** for data handling details.
- **Terms & Conditions**: See **[Terms & Conditions](https://xtros.github.io/Muziso-Docs/#terms)** for user agreements and media disclaimers.
