# 🔒 Muziso Privacy Policy

**Effective Date:** February 19, 2026  
**App Version:** v0.1.8  

---

## 🛡️ Overview & Privacy Commitment

**Muziso** ("the Application") is an open-source desktop music player created by **Webs By JTS**. We respect your privacy and are committed to protecting your personal data. 

Muziso is designed around a **privacy-first, offline-capable architecture**. The Application does **not** collect, store, or sell your personal information, browsing history, listening habits, or library metadata.

---

## 📊 Data Collection & Usage

### 1. Local Storage & Database (`muziso.db`)
- All user data—including liked songs, playlists, play counts, history, and app preferences—is stored **100% locally** on your device inside an encrypted/sandboxed SQLite database (`muziso.db`).
- This data never leaves your computer and is not transmitted to external analytics servers.

### 2. External Audio Stream & Metadata Resolution
When you stream online audio or view artist discographies, Muziso sends direct requests to public music providers (e.g., JioSaavn, Spotify Web API, YouTube via `yt-dlp` sidecar):
- Requests contain only necessary query parameters (track/artist title, song ID, regional language headers).
- No user identification tokens, email addresses, or personal accounts are transmitted during audio stream resolution.

### 3. Optional Features

#### A. Discord Rich Presence (`discord-rich-presence`)
If you enable **Discord RPC** in App Settings, Muziso broadcasts your current playing track title, artist name, and duration to the local Discord client running on your machine. This feature is opt-in and can be toggled off at any time.

#### B. Software Update Checker (`tauri-plugin-updater`)
Muziso checks GitHub Releases for software updates using Tauri's updater plugin. This check fetches public release metadata to determine if a newer version (e.g., `v0.1.8`) is available.

---

## 🚫 Third-Party Analytics & Tracking

- Muziso contains **zero telemetry**, **zero analytics scripts**, and **zero tracking pixels**.
- We do not use Google Analytics, Mixpanel, Sentry, or any telemetry services.

---

## 🔐 Children's Privacy

Muziso is suitable for users of all ages. Because we do not collect any personal data, we do not knowingly request or store data from children under 13.

---

## 📜 Changes to This Policy

We may update this Privacy Policy to reflect future software enhancements. Any modifications will be documented in official release notes and updated on the [GitHub Documentation Site](https://xtros.github.io/Muziso/).

---

## 📬 Contact Information

For questions regarding this Privacy Policy or app security, please open an issue on the [GitHub Repository](https://github.com/xtros/Muziso/issues) or contact **Webs By JTS**.
