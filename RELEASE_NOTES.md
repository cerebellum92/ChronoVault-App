# 🚀 ChronoVault Pro Release Notes

## [v1.0.6] - 2026-11-04

This major release consolidates all performance optimizations, multi-cloud replication enhancements, scheduling resilience, and UI refinements developed since v1.0.2.

### ⚡ 8-Thread Accelerated Retention Pruning (`-threads 8`)
- **Multi-Threaded Cloud Pruning**: Enabled concurrent 8-thread execution (`-threads 8`) in `DuplicacyPruneService`, accelerating chunk identification and deletion operations across Google Drive, Microsoft OneDrive, Amazon S3, and Backblaze B2.
- **Slashed Maintenance Window**: Cuts daily midnight snapshot pruning duration by up to 75%, preventing long-running cloud queries from consuming extended network and CPU resources.

### ⏱️ Transparent Timing & Isolated Midnight Prune Reporting
- **Granular Duration Breakdown**: Disentangled regular daytime backup durations from the once-a-day midnight retention pruning maintenance.
- **Transparent Notifications**: Telegram daily digests and macOS system notifications now report clear individual metrics:
  - `⏱️ Regular Backup Duration`: Accurate time spent on delta scanning and file uploading.
  - `🧹 Daily Prune Maintenance`: Explicitly tagged as running once daily at midnight.
- **Eliminated False Duration Alarms**: Solved the confusion where combined ~26-minute maintenance runs were mistaken for regular 6-minute daytime backups.

### 🟢 Instant Timestamp & Repository State Persistence
- **Immediate `lastBackupDate` Writing**: Fixed an issue where repository timestamps and revision stats were only flushed to disk during midnight prune cycles. The background runner now immediately and unconditionally persists updated metadata to `repositories.json` after every single repository backup.
- **Glowing LED Task Indicator Fix**: Ensures the sidebar repository status light correctly stays healthy green (Normal / Up-to-date) instead of mistakenly flipping to yellow (`>48h stale backup`).

### ☁️ 3-2-1 Multi-Destination Cloud Replication Resilience
- **Full Destination Topology**: Verified and restored active replication support for all secondary cloud and local endpoints:
  - ☁️ **Microsoft OneDrive**: Native OAuth token-based replication (`one://`)
  - 💾 **Local & External Drives**: Direct local path syncing (`/Volumes/...`)
  - 🪣 **Amazon AWS S3**: High-durability object storage (`s3://`)
  - 📦 **Backblaze B2**: Cost-effective cloud archive (`b2://`)
- **Keychain Fallback Lookup**: Enhanced Keychain credentials resolution with snapshot-specific and storage-specific fallback keys.
- **Isolated Failure Tracking**: Replication warnings no longer overwrite primary backup success status, providing clear visibility into each individual destination's sync health.

### 🛡️ System Sleep Guard & Monotonic Active Uptime
- **Smart Power Assertion (`IOPMAssertion`)**: Automatically prevents system sleep during active file transfers, offsite replication, and retention pruning, releasing power locks safely upon completion.
- **Monotonic Active Uptime (`systemUptime`)**: Replaced wall-clock backup calculations with active system uptime, preventing misleading hours-long duration spikes when a MacBook is put to sleep mid-run.
- **Keychain Wake-Up Resilience**: Added adaptive retry handling for Keychain queries following system wake events, eliminating false "password not found" errors.

### 💎 Rolling Chunk Scrubbing (Deep Integrity Verification)
- **Newest-First Automated Inspection**: Added automated background integrity checking (`duplicacy check -r <rev> -chunks`) that checks the latest snapshot revisions first to prioritize recent data.
- **Strict Quota & Timeout Guard**: Automatically bounds each post-backup scrub check to a single revision with an automatic timeout, preventing background tasks from saturating system resources.
- **Full Cycle Tracking**: Tracks completed inspection cycles and surfaces health badges in the Dashboard, with proactive Telegram and system alerts if corrupt chunks are detected.

### 🔄 Mutually Exclusive Scheduler Engine
- **Decoupled Architecture**: Enforced strict mutual exclusion between macOS system-level `LaunchAgent` daemon and the in-app SwiftUI timer.
- **Cross-Process File Locking (`BackupProcessLease`)**: Coordinates headless background tasks and interactive GUI runs via atomic `flock` file locking to eliminate concurrent execution risks.
- **Automatic Interval Reconciliation**: Detects interval changes in Settings and dynamically synchronizes `com.chronovault.scheduler.plist` without interrupting in-flight operations.

### 🌐 Complete UI Localization & Polish
- **Full Multilingual Coverage**: Added complete English, Traditional Chinese, and Simplified Chinese translations for all modal buttons (`btn_done`, `btn_cancel`, `btn_browse`, `btn_refresh`).
- **Eliminated Placeholder Tags**: Replaced all raw localization keys with native localized labels across storage management, folder picker, and restore explorer dialogs.

### 📝 Log File Protection & Disk I/O Optimization
- **Filtered CLI Stdout**: Prevented massive 119k+ line directory listings from writing to `backup.log` during automatic runs, sparing unnecessary SSD write cycles and preventing rapid 18MB log rotations.
- **Focused Diagnostics**: Preserves meaningful CLI logs, errors, and replication stats without noise.

### 🏗️ Modular Clean Architecture
- **Domain-Driven Service Separation**: Refactored monolithic services into clean, testable Swift submodules:
  - `Services/Backup/`: Headless runners, process lease locking, and backup orchestrators.
  - `Services/Executor/`: Sandboxed process execution and environment injection.
  - `Services/Prune/`: Multi-threaded retention prune engine.
  - `Services/Restore/`: Snapshot inspection and file extraction.
  - `Services/Scrub/`: Rolling chunk integrity verification.
  - `Services/Stats/`: SQLite cache and analytics aggregation.
  - `Services/Storage/`: Multi-cloud credentials and destination binding.
  - `Views/Dashboard/`: Componentized dashboard views and view models.

---

## [v1.0.2] - 2026-08-20

### 🌲 Native Collapsible Directory Tree
- **Interactive Folder Tree**: Upgraded snapshot file explorer to a macOS Finder-style collapsible tree view with infinite nesting support (`▶ / ▼`).
- **Cross-Depth Multi-Selection**: Multi-select files and folders across disparate folder depths with instant aggregate item counts for batch restoration.
- **Expand / Collapse All**: Dedicated toolbar actions to expand or collapse entire directory hierarchies instantly.
- **Sub-Millisecond Response**: Powered by a local SQLite cache and in-memory Trie structure for instantaneous offline exploration.

### ⚡ Upload Bandwidth Rate Limiting
- **Flexible Bandwidth Caps**: Configurable upload throttling in Settings (`1 MB/s`, `2 MB/s`, `5 MB/s`, `10 MB/s`, `Custom kB/s`, or `Unlimited`).
- **Engine-Level Rate Control**: Directly interfaces with Duplicacy `-limit-rate` and `-upload-limit-rate` flags.
- **Persistent Synchronization**: Keeps limits synchronized across `app_config.json` and background runner configs.

### 📁 Restore Target Folder Creation
- **Finder "New Folder" Support**: Enabled native macOS "New Folder" creation directly inside the restore directory selection dialog.

### 📊 Dashboard & UI Refinements
- **Active Snapshot Count**: Enhanced metric cards to display verified active snapshot counts alongside latest revision numbers.
- **Uniform Card Grid Layout**: Locked metric cards to fixed uniform heights with text auto-scaling protection.
- **Window Management Fix**: Prevented background window accumulation upon multiple dashboard reopenings.

---

## [v1.0.0] - 2026-08-08

Initial release of **ChronoVault Pro** — the high-performance native macOS cloud backup system powered by the Duplicacy Engine.
- ⚡ 100% native SwiftUI & Swift Charts interface for macOS 14+.
- 🔒 Client-side zero-knowledge AES-256 encryption.
- ⏳ Time Capsule historical snapshot explorer with instant file restore.
- 🛡️ Smart Battery & Cellular Hotspot protection.
- 🔄 3-2-1 multi-cloud destination replication.
- 🎨 Adaptive Dark / Light theme with smooth capacity growth curves.
- 🚀 One-click Duplicacy engine onboarding & GitHub update checker.
