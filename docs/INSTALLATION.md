# ⚡ Muziso Installation & Developer Build Guide

Official installation and developer build guide for **Muziso** (v0.1.8) across Windows, macOS, and Linux.

---

## 📥 End-User Installation

Visit the **[Muziso GitHub Releases](https://github.com/xtros/Muziso/releases)** page to download the latest installer (`v0.1.8`) for your system.

### 🪟 Windows
- **Downloads**: `.exe` Installer, `.msi` Package, or Standalone `.zip`
- **SmartScreen Notice**: Because Muziso is an open-source binary without a paid commercial certificate, Windows Defender SmartScreen may display an *"Unknown Publisher"* prompt on first launch. Click **"More info"** &rarr; **"Run anyway"** to continue.

### 🍎 macOS
- **Downloads**: `.dmg` Disk Image or `.app` Bundle (Apple Silicon & Intel supported)
- **First Launch**: Drag Muziso to your Applications folder. If macOS displays a gatekeeper warning, right-click `Muziso.app` and select **Open**.

### 🐧 Linux
- **Downloads**: `.deb` (Debian/Ubuntu) or `.AppImage` (Universal Linux)
- **AppImage Execution**:
  ```bash
  chmod +x Muziso_0.1.8_amd64.AppImage
  ./Muziso_0.1.8_amd64.AppImage
  ```

---

## 🛠️ Developer Build Instructions

### 1. Prerequisites

- **Node.js**: `v18.0.0` or higher
- **Rust**: `1.75.0` or higher (`rustup`)
- **Tauri CLI**: Installed automatically via `package.json` (`@tauri-apps/cli`)
- **C++ Build Tools**:
  - **Windows**: Visual Studio 2022 C++ Build Tools
  - **macOS**: Xcode Command Line Tools (`xcode-select --install`)
  - **Linux**: `build-essential`, `libssl-dev`, `libgtk-3-dev`, `libgstreamer1.0-dev`, `libgstreamer-plugins-base1.0-dev`

### 2. Setup & Development

```bash
# Clone the repository
git clone https://github.com/xtros/Muziso.git
cd Muziso

# Install Node dependencies
npm install

# Run the Tauri v2 desktop app in development mode
npm run tauri dev
```

### 3. Production Build

To compile standalone production installers (`.exe`, `.msi`, `.dmg`, `.deb`, `.AppImage`):

```bash
npx tauri build
```

Compiled binaries will be generated inside `src-tauri/target/release/bundle/`.
