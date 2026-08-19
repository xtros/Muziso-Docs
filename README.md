# 🎵 Muziso Documentation Repository

<p align="center">
  <img src="https://i.postimg.cc/yYvXBWK5/Muziso.png" alt="Muziso Showcase" width="100%" />
</p>

<p align="center">
  <a href="https://xtros.github.io/Muziso/"><img src="https://img.shields.io/badge/Documentation-GitHub%20Pages-ccff00?style=for-the-badge&logo=githubpages&logoColor=black" alt="Documentation Site" /></a>
  <a href="https://github.com/xtros/Muziso/releases"><img src="https://img.shields.io/github/v/release/xtros/Muziso?color=ccff00&label=Release&style=for-the-badge" alt="Latest Release" /></a>
  <a href="https://github.com/xtros/Muziso/blob/main/LICENSE"><img src="https://img.shields.io/badge/License-MIT-ccff00?style=for-the-badge" alt="MIT License" /></a>
  <img src="https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-181825?style=for-the-badge&logo=github" alt="Platforms" />
  <img src="https://img.shields.io/badge/Tauri-v2-FFC107?style=for-the-badge&logo=tauri&logoColor=black" alt="Tauri v2" />
  <img src="https://img.shields.io/badge/React-19-61DAFB?style=for-the-badge&logo=react&logoColor=black" alt="React 19" />
</p>

<p align="center">
  <b>Muziso</b> is a premium, dark-themed, glassmorphic desktop music player built for modern listeners. Powered by a high-performance <b>React (TypeScript)</b> + <b>Rust (Tauri v2)</b> engine, Muziso seamlessly combines local library playback, high-fidelity web audio resolution, and offline caching.
</p>

<p align="center">
  📖 <b><a href="docs/index.html">View Local HTML Documentation Page</a></b>
</p>

---

## 📚 Quick Documentation Links

- 🌐 **[GitHub Pages Documentation Site](docs/index.html)**: Interactive documentation, feature breakdowns, and API references.
- 🏗️ **[Architecture Guide](docs/ARCHITECTURE.md)**: Deep dive into Tauri IPC, GStreamer audio pipeline, SQLite persistence, and yt-dlp sidecar integration.
- ⚡ **[Installation & Build Guide](docs/INSTALLATION.md)**: Detailed setup steps for Windows, macOS, and Linux.
- 🤝 **[Contributing & Bug Hunter Program](docs/CONTRIBUTING.md)**: Guidelines for code contributions and bug bounty rewards.

---

## 🌟 Key Features

- 🎧 **Hybrid Audio Engine**: Play local music collections (`.mp3`, `.m4a`, `.wav`, `.opus`, `.flac`) alongside dynamic online streams.
- ⚡ **IP-Bound Stream Resolution**: Dynamically extracts high-quality audio streams using a local, platform-decoupled `yt-dlp` sidecar engine.
- 📥 **Offline Download & Library Management**: Save tracks locally for immediate offline playback with custom metadata and artwork indexing.
- 🔀 **Smart Queue & Shuffle Pipeline**: Shuffled play queue with intelligent un-shuffle state tracking and deterministic historical navigation.
- 📣 **Developer Announcement Feed**: In-app announcements feed with read/unread tracking and remote notification sync.
- 🎨 **Glassmorphic Cyber-Minimal UI**: High-fidelity dark mode with signature neon branding (`#ccff00`), smooth Framer Motion transitions, custom modal overlays, and responsive routing resets.
- 🎚️ **Decoupled Controls**: Native event isolation preventing gesture overlap between drag sliders, volume controllers, and swipe overlays.

---

## ⚡ Download & Installation

Visit the **[Muziso Releases Page](https://github.com/xtros/Muziso/releases)** to grab the latest standalone installer for your system:

| Platform | Package Format | Download Link |
| :--- | :--- | :--- |
| **Windows** | `.exe` / `.msi` / `.zip` | [Latest Windows Release](https://github.com/xtros/Muziso/releases/latest) |
| **macOS** | `.dmg` / `.app` | [Latest macOS Release](https://github.com/xtros/Muziso/releases/latest) |
| **Linux** | `.deb` / `.AppImage` | [Latest Linux Release](https://github.com/xtros/Muziso/releases/latest) |

> [!NOTE]
> **Windows SmartScreen Notice**: Because Muziso is an open-source binary without a paid commercial certificate, Windows Defender SmartScreen may display an *"Unknown Publisher"* prompt on first launch. Click **"More info"** &rarr; **"Run anyway"** to continue.

---

## 🛠️ Tech Stack & Architecture

- **Frontend Core**: React 19, TypeScript, Framer Motion, Lucide Icons, Cyber-Minimal Design System
- **Desktop Architecture**: Tauri v2 (Rust)
- **Audio Pipeline**: GStreamer (Native Rust FFI bindings) + Rodio
- **Local Persistence**: SQLite (`rusqlite`) for library indexing, play counts, and queue state
- **Stream Engine**: `yt-dlp` packaged as a platform-decoupled sidecar binary

---

## 🚀 Development Setup

For complete, step-by-step developer build instructions across all platforms, see **[INSTALLATION.md](docs/INSTALLATION.md)**.

```bash
# 1. Clone the Repository
git clone https://github.com/xtros/Muziso.git
cd Muziso

# 2. Install Frontend Dependencies
npm install

# 3. Run Development Server
npm run tauri dev
```

---

## 🎯 Bug Hunter Reward Program

Found a functional bug, stream error, or UI glitch in **Muziso**? Help improve the platform and get rewarded! See **[CONTRIBUTING.md](docs/CONTRIBUTING.md)** for issue templates and guidelines.

---

## 📜 License

Distributed under the MIT License. See [`LICENSE`](https://github.com/xtros/Muziso/blob/main/LICENSE) for more details.
