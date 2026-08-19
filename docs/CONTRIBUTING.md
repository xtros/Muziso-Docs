# 🤝 Contributing to Muziso & Bug Hunter Program

Thank you for your interest in contributing to **Muziso**! We welcome open-source contributions, bug reports, feature proposals, and code improvements.

---

## 🎯 Bug Hunter Reward Program

Found a functional playback bug, stream resolution failure, or UI glitch in **Muziso**? Help us keep the app stable and get recognized!

### How to Submit Bug Reports:
1. **Search Existing Issues**: Check [GitHub Issues](https://github.com/xtros/Muziso/issues) to avoid duplicate reports.
2. **Open a New Bug Report**:
   - Provide a clear title describing the issue.
   - Include OS version, Muziso version (e.g. `v0.1.8`), and audio format.
   - Attach relevant console logs or screenshots.
3. **Rewards & Recognition**: Confirmed bug reports will be credited in release notes and eligible for bug bounty rewards!

---

## 🛠️ Pull Request Workflow

1. **Fork the Repository**:
   Create your own fork of [Muziso on GitHub](https://github.com/xtros/Muziso).

2. **Create a Feature Branch**:
   ```bash
   git checkout -b feature/awesome-feature
   ```

3. **Code Style Standards**:
   - **Frontend**: Follow React 19 functional component standards, TypeScript strict typing, and Framer Motion transitions.
   - **Styling**: Maintain the signature cyber-minimal dark palette (`#09090b` background, `#ccff00` neon accent).
   - **Backend**: Adhere to standard Rust code formatting (`cargo fmt`) and check for warnings (`cargo check`, `cargo clippy`).
   - **Deduplication Rules**: Use `getSmartDedupKey` / `clean_dedup_key` for version-preserving song deduplication.

4. **Submit Your PR**:
   Push to your branch and open a Pull Request targeting the `main` branch. Provide a brief summary of what changes were made and how to test them.

---

## 📜 Legal Policies & License

- **License**: By contributing to Muziso, you agree that your contributions will be licensed under the project's [MIT License](https://github.com/xtros/Muziso/blob/main/LICENSE).
- **Privacy Policy**: Review our data protection policy in **[PRIVACY.md](PRIVACY.md)**.
- **Terms & Conditions**: Review software terms in **[TERMS.md](TERMS.md)**.
