# 🚀 ChronoVault Pro Release Notes

## [v1.0.1] - 2026-08-12

### 🛡️ Native Background Daemon & Window Management
- **Menu Bar Background Retention**: Closing the main window (clicking the red "X") now hides the window while keeping the background daemon 100% active in the Menu Bar. Scheduled backups and multi-cloud sync continue seamlessly.
- **Smart Safety Quit Protection**: If you attempt to quit ChronoVault Pro while a backup or restore transfer is actively running, an interactive `NSAlert` will warn you first to prevent accidental transfer interruptions.

### 📁 Restore Explorer Enhancements
- **In-App New Folder Creation**: When selecting a restore target directory in the Time Capsule Explorer, you can now click the **"New Folder"** button directly inside the macOS Finder folder picker to create designated destination folders instantly.

### 📊 Dashboard & UI Layout Refinements
- **Active Snapshot Count Indicator**: Updated the green stat card to display the actual number of active, non-pruned snapshot points as the primary metric, with the latest revision integer in the subtitle (e.g. `175 Active Snapshots · Latest Rev #718`).
- **Equal Height Card Grid & Text Auto-Scaling**: Locked executive metric cards to uniform heights and added text scale protection (`minimumScaleFactor`) to prevent title and metric text from breaking lines on smaller window sizes.

---

## [v1.0.0] - 2026-08-08

Welcome to **ChronoVault Pro**, the next-generation native macOS cloud backup system powered by the high-performance Duplicacy Engine!

### ✨ Key Features & Highlights
- ⚡ **Native macOS Interface**: Built 100% with SwiftUI & Swift Charts for macOS 14+.
- 🔒 **AES-256 Military Encryption**: Client-side zero-knowledge encryption before uploading to Google Drive & secondary clouds.
- ⏳ **Time Capsule Explorer & 1-Click Single-File Restore**: Browse historical snapshot revisions and restore single files in under 1 second.
- 🛡️ **Smart Battery & Hotspot Guard**: Pauses background backups automatically when running on MacBook battery or meter-billed iPhone Personal Hotspots.
- 🔄 **3-2-1 Offsite Storage Copy**: Replicate backups across multiple cloud destinations.
- 🎨 **Modern Dark/Light Mode & Wavy Charts**: Real-time storage capacity growth charts with smooth glowing line indicators.
- 🗑️ **Dual Uninstallation Wizard**: Choose between preserving configuration files or performing a complete wipe.
- 🚀 **1-Click Engine Installer & Auto Updates**: Integrated GitHub release checker and 1-click Duplicacy engine onboarding.
