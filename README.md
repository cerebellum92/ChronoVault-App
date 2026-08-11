# ChronoVault App

**ChronoVault** is a macOS backup utility that securely backs up your data to Google Drive (or other cloud storage). This repository provides the **free version** of ChronoVault, which already lets you:

- Back up any folder on your Mac.
- Add one or more remote or local backup slots.
- Restore the latest backup with a single click.

The installer is distributed **exclusively via GitHub** for now. Future purchase or subscription links will be added once the product is officially launched.

---

## 📦 Download & Install (GitHub only)

1. **Download the installer**
   - Click the DMG file directly: [ChronoVault‑Pro‑1.0.0‑Installer.dmg](https://github.com/cerebellum92/ChronoVault-App/raw/main/ChronoVault-Pro-1.0.0-Installer.dmg)
2. **Mount the DMG** by double‑clicking the file.
3. **Drag `ChronoVault Pro.app`** into your `Applications` folder.
4. Launch the app and follow the on‑screen setup wizard.

> The installer is signed and notarized for macOS 13+.

---

## 🔄 Manual Update

ChronoVault does **not** currently perform automatic updates. To upgrade:

1. Visit the **Releases** page: https://github.com/cerebellum92/ChronoVault-App/releases
2. Download the latest DMG.
3. Replace the existing `ChronoVault Pro.app` in your Applications folder with the new version (you may need to quit the app first).

Future versions will include an automatic update mechanism for a smoother upgrade experience.

---

## 📖 Release Notes

See the full changelog in [`RELEASE_NOTES.md`](RELEASE_NOTES.md).

---

## 🛠️ Build & Development (optional)

If you want to build ChronoVault from source (private core repo required):

```bash
# Clone the core repository (private)
# git clone git@github.com:cerebellum92/ChronoVaultPro-Core.git
# Follow the internal documentation to build the macOS app.
```

> This public repository only contains the installer binary; source code lives in the private `ChronoVaultPro-Core` repo.

---

## 📧 Support

For questions, bugs, or feature requests, please contact:

- **Support email**: support@chronovaultapp.com
- **GitHub Issues**: Open an issue here (you may need to be a collaborator for private details).

---

## ⚖️ License

The installer is provided under the same license as the core product. See the `LICENSE` file in the private repository for details.

---

*This README was generated automatically. Feel free to edit and improve it.*
