# ⚡ Muziso Installation & Developer Build Guide

Official installation guide for **Muziso** across Windows, macOS, and Linux.

---

## 📥 End-User Installation

Visit the **[Muziso GitHub Releases](https://github.com/xtros/Muziso/releases)** page to download the latest installer for your system.

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

## 🛠️ Developer Setup & Build Instructions

### Prerequisites
- **Node.js**: v18.0 or higher
- **Rust Toolchain**: Install via [rustup.rs](https://rustup.rs)
- **GStreamer Engine**:

#### 1. Windows Setup
Install GStreamer MSVC packages using Chocolatey:
```powershell
choco install gstreamer-runtime gstreamer-devel pkgconfiglite -y
$env:PKG_CONFIG_PATH = "C:\gstreamer\1.0\msvc_x86_64\lib\pkgconfig"
$env:GSTREAMER_1_0_ROOT_X86_64 = "C:\gstreamer\1.0\msvc_x86_64\"
```

#### 2. macOS Setup
Install via Homebrew:
```bash
brew install gstreamer gst-plugins-base gst-plugins-good gst-plugins-bad gst-plugins-ugly pkg-config
```

#### 3. Linux (Ubuntu / Debian) Setup
Install via APT:
```bash
sudo apt update && sudo apt install -y \
  build-essential pkg-config libasound2-dev \
  libgstreamer1.0-dev libgstreamer-plugins-base1.0-dev \
  libgstreamer-plugins-good1.0-dev libgstreamer-plugins-bad1.0-dev \
  gstreamer1.0-plugins-ugly libwebkit2gtk-4.1-dev
```

---

### Step-by-Step Local Compilation

1. **Clone Repository**:
   ```bash
   git clone https://github.com/xtros/Muziso.git
   cd Muziso
   ```

2. **Install Frontend Dependencies**:
   ```bash
   npm install
   ```

3. **Start Development Server**:
   ```bash
   npm run tauri dev
   ```

4. **Build Production Desktop Package**:
   ```bash
   npm run tauri build
   ```
