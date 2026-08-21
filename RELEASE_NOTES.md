# 🚀 ChronoVault Pro Release Notes

## [v1.0.2] - 2026-08-20

### 🚀 新增功能與重大優化 (Major Features & Improvements)

- **🌲 macOS Finder 原生階層式展開目錄樹 (Collapsible Directory Tree)**
  - **原生摺疊展開 (`▶ / ▼`)**：Snapshot 檔案結構全面升級為 macOS Finder 列表檢視，支援資料夾無限層級點擊展開/收合。
  - **跨目錄/跨層級多選還原 (Cross-Depth Multi-Selection)**：可在不同深度的目錄中自由勾選多個檔案與資料夾，上方即時統計選取總數，支援一鍵批量還原。
  - **一鍵展開/收合全部 (`Expand All / Collapse All`)**：提供快速工具列按鈕，毫秒級秒開所有子項目。
  - **極致 0.001s 效能**：基於本地 SQLite 快取與記憶體 Trie 架構，展開/收合完全不需網路請求，極致流暢零卡頓。

---

### 📁 Restore Explorer Enhancements
- **In-App New Folder Creation**: When selecting a restore target directory in the Time Capsule Explorer, you can now click the **"New Folder"** button directly inside the macOS Finder folder picker to create designated destination folders instantly.

### 📊 Dashboard & UI Layout Refinements
- **Active Snapshot Count Indicator**: Updated the green stat card to display the actual number of active, non-pruned snapshot points as the primary metric, with the latest revision integer in the subtitle (e.g. `175 Active Snapshots · Latest Rev #718`).
- **Equal Height Card Grid & Text Auto-Scaling**: Locked executive metric cards to uniform heights and added text scale protection (`minimumScaleFactor`) to prevent title and metric text from breaking lines on smaller window sizes.

### 🛡️ Stability, Performance & UI Refinements
* **Background Size Calculation**: Storage size refreshing now executes asynchronously in the background, eliminating beachballs and UI freezes on massive repositories.
* **Strict Recursive File Filtering**: Enhanced regex filter prevents `.DS_Store` and temporary OS metadata from syncing across all nested subdirectories.
* **Smooth Window Management**: Fixed an issue where re-opening the main dashboard multiple times could cause background windows to stack up.

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
