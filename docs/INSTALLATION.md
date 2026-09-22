# ⚡ Muziso Installation & Developer Build Guide

Official installation and developer build guide for **Muziso** (v0.1.8) across **Desktop (Windows, macOS, Linux)** and **Mobile (Android)**.

---

## 📥 End-User Installation

Visit the **[Muziso GitHub Releases](https://github.com/xtros/Muziso/releases)** page to download the latest installer or APK (`v0.1.8`).

### 🤖 Android Mobile
- **Downloads**: [Download `Muziso_v0.1.8.apk`](https://github.com/xtros/Muziso/releases/latest/download/Muziso_v0.1.8.apk) (Direct Sideload) or [Google Play Store](https://github.com/xtros/Muziso/releases)
- **Sideloading Instructions**:
  1. Download `Muziso_v0.1.8.apk` on your Android phone or tablet.
  2. Open the downloaded `.apk` file.
  3. If prompted with *"Install unknown apps"*, navigate to **Settings** &rarr; toggle on **"Allow from this source"**.
  4. Tap **Install** and launch Muziso!

### 🪟 Windows Desktop
- **Downloads**: [Download Setup.exe](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64-setup.exe), [Download .msi](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64_en-US.msi), or [Download .zip](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64.zip)
- **SmartScreen Notice**: Because Muziso is an open-source binary without a paid commercial certificate, Windows Defender SmartScreen may display an *"Unknown Publisher"* prompt on first launch. Click **"More info"** &rarr; **"Run anyway"** to continue.

### 🍎 macOS Desktop
- **Downloads**: [Download .dmg](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_x64.dmg) or [Download .app Bundle](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_universal.app.tar.gz) (Apple Silicon & Intel supported)
- **First Launch**: Drag Muziso to your Applications folder. If macOS displays a gatekeeper warning, right-click `Muziso.app` and select **Open**.

### 🐧 Linux Desktop
- **Downloads**: [Download .AppImage](https://github.com/xtros/Muziso/releases/latest/download/Muziso_0.1.8_amd64.AppImage) or [Download .deb](https://github.com/xtros/Muziso/releases/latest/download/muziso_0.1.8_amd64.deb)
- **AppImage Execution**:
  ```bash
  chmod +x Muziso_0.1.8_amd64.AppImage
  ./Muziso_0.1.8_amd64.AppImage
  ```

---

## 🛠️ Developer Build Instructions

### 💻 1. Desktop Build (Tauri v2 + React 19 + Rust)

#### Prerequisites:
- **Node.js**: `v18.0.0` or higher
- **Rust Toolchain**: `1.75.0` or higher (`rustup`)
- **Tauri CLI**: Installed automatically via `package.json` (`@tauri-apps/cli`)
- **Platform Dependencies**:
  - **Windows**: Visual Studio 2022 C++ Build Tools & GStreamer development runtime
  - **macOS**: Xcode Command Line Tools (`xcode-select --install`) & Homebrew GStreamer
  - **Linux**: `build-essential`, `libssl-dev`, `libgtk-3-dev`, `libgstreamer1.0-dev`, `libgstreamer-plugins-base1.0-dev`

#### Commands:
```bash
# Clone the repository
git clone https://github.com/xtros/Muziso.git
cd Muziso

# Install Frontend dependencies
npm install

# Run Desktop app in development mode
npm run tauri dev

# Compile standalone production installers
npx tauri build
```

---

### 📱 2. Android Mobile Build (Native Kotlin + Gradle)

#### Prerequisites:
- **Java Development Kit (JDK)**: JDK 17 or higher
- **Android SDK**: API Level 34+ (Android 14) and Android Build Tools
- **Android Studio / Gradle**: Latest Android Studio Hedgehog or higher

#### Commands:
```bash
# Navigate to the Android project root
cd android

# Compile debug APK
./gradlew assembleDebug

# Compile production release APK
./gradlew assembleRelease
```

Generated APKs will be located at `android/app/build/outputs/apk/release/app-release.apk`.
