
<div align="center">

<img width="120" height="120" alt="Aero logo" src="https://github.com/user-attachments/assets/57c2adf9-b5ef-453a-a9df-de9e573b8560"/>

# 🪟 Aero

[![windows](https://img.shields.io/badge/Windows-10%20%2F%2011-0078d6?style=flat&logo=windows)](https://www.microsoft.com/windows)
[![python](https://img.shields.io/badge/Python-3.12+-3776AB?style=flat&logo=python)](https://www.python.org/)
[![status](https://img.shields.io/badge/V1-Released-success?style=flat)](https://github.com/your-username/aero/releases)
[![v2](https://img.shields.io/badge/V2_Pro-C%23_%2B_WPF-6f42c1?style=flat&logo=.net)](https://github.com/your-username/aero)

> **Lightweight, native-feeling Windows utility for precise File Explorer window opacity control.**  
> *Designed for minimal resource footprint, persistent state, and seamless tray integration.*

</div>

---

## 🧭 Project Status

| Version | Stack | State | Architecture |
| :--- | :--- | :--- | :--- |
| **V1 (Current)** | Python + CustomTkinter + `ctypes` | ✅ Stable, Feature-Complete | Polling-based window enumeration |
| **V2 Pro (Planned)** | C# + WPF + Windows API | 🔮 Design Phase | Event-driven (WinEventHook), native Mica/Acrylic |

---

## ✨ Core Capabilities

> **🌫️ Transparency Engine**
> - **Granular Control**: 0–255 opacity slider with real-time preview.
> - **Auto-Apply**: Hooks into newly spawned Explorer instances automatically.
> - **State Persistence**: Atomic `config.json` writes, surviving OS reboots without corruption.

> **🖥️ System Integration**
> - **System Tray**: Minimized by default, native context menu (`Show` / `Exit`).
> - **Startup**: Registry-based autostart toggle (no scheduled tasks overhead).
> - **Theming**: Light/Dark mode sync, custom accent color picker, and extensible JSON theme support.

> **🛡️ Reliability**
> - Graceful shutdown handling (prevents orphaned tray processes).
> - Structured JSON logging (`aero.log`) for deterministic diagnostics.

---

## 📸 Interface

<div align="center">
  <img width="801" alt="Main window" src="https://github.com/user-attachments/assets/d218909e-ac49-4d59-9551-ec51625d175b"/>
  <br/>
  <sub>Main Window & Opacity Slider</sub>
  <br/><br/>
  <img width="802" alt="Appearance settings" src="https://github.com/user-attachments/assets/1b34b7bf-08f0-4249-9e71-7aedb3743dbf"/>
  <br/>
  <sub>Appearance & Theme Configuration</sub>
</div>

---

## ⚙️ Engineering Notes

*As an Independent Developer, I prioritize architectural integrity over feature bloat. Key design decisions for V1:*

- **KISS Deployment**: Packaged via `PyInstaller` into a single, standalone `.exe`. Zero Python runtime required for the end-user.
- **Atomic Config Writes**: Settings are saved to a temporary file first, then renamed (`os.replace`), preventing `config.json` corruption during unexpected crashes or power loss.
- **V1 Limitation Acknowledgment**: Current window detection relies on periodic polling (`EnumWindows`). This is a deliberate trade-off for rapid V1 delivery. It introduces minor CPU overhead (~0.1%) and may miss transient windows. **V2 will eliminate this entirely via `SetWinEventHook`**.
- **Elevation Boundary**: UAC prompts and elevated Explorer instances run in a different integrity level. Aero V1 cannot modify their opacity without matching admin privileges (by design of Windows security model).

---

## ⚠️ Known Limitations (V1)

- **Scope**: Strictly targets standard File Explorer windows (`CabinetWClass`, `ExploreWClass`).
- **Compatibility**: Third-party Explorer shell extensions (e.g., old context menu handlers) may interfere with window rendering.
- **Permissions**: Cannot alter opacity of elevated (Administrator) windows unless Aero is also run as Administrator.

---

## 🚀 Roadmap — V2 Pro (C# + WPF)

- [ ] **Event-Driven Architecture**: Replace polling with `SetWinEventHook` (zero CPU overhead).
- [ ] **Per-Process Rules**: Granular opacity profiles based on executable name or window title.
- [ ] **Context Profiles**: One-click switching between "Gaming", "Focus", and "Default" presets.
- [ ] **Global Hotkeys**: System-wide shortcuts for opacity adjustment and tray toggle.
- [ ] **Native Materials**: First-class support for Windows 11 Mica and Acrylic backdrop effects.
- [ ] **Silent Auto-Updates**: Background update checks with delta patching.

---

## 📦 Installation & Usage

### Prerequisites
- Windows 10 (1903+) or Windows 11.
- **No dependencies**: The release is a fully standalone executable.

### Quick Start
1. Navigate to [Releases](https://github.com/your-username/aero/releases) and download the latest `Aero.exe`.
2. Execute the file. It will silently start in the system tray.
3. Left-click the tray icon to open the control panel.

### File Structure
| File | Purpose |
| :--- | :--- |
| `Aero.exe` | Standalone packaged application. |
| `config.json` | Auto-generated user settings (atomic writes). |
| `aero.log` | Auto-generated diagnostic log (rotated/truncated on startup). |
| `icon.ico` | Source icon (only needed for building from source). |

---

## 🔧 Building from Source

For contributors or custom builds. Requires Python 3.12+.

```bash
# 1. Initialize virtual environment and install dependencies
python -m venv .venv
.venv\Scripts\activate
python -m pip install -r requirements.txt

# 2. Build standalone executable (PowerShell)
python -m PyInstaller `
  --clean `
  --noconfirm `
  --onefile `
  --windowed `
  --name Aero `
  --icon "icon.ico" `
  --add-data "icon.ico;." `
  --collect-all customtkinter `
  --hidden-import PIL `
  --hidden-import pystray `
  main.py
```
*Output:* `dist\Aero.exe`

> **Note for CMD users**: Collapse the PowerShell backticks into a single line command.

---

## 🐛 Reporting Issues

To ensure fast resolution, please provide deterministic reproduction steps:

1. **Environment**: Windows version (e.g., `Win 11 23H2`) and Aero version.
2. **Logs**: Attach the relevant tail of `aero.log`.
3. **Context**: What action triggered the issue? (e.g., "Opened elevated Explorer after changing opacity to 150").
4. **System Events**: For crash-to-desktop issues, check `Event Viewer → Windows Logs → Application` for `.NET Runtime` or `Application Error` entries.

---

## 📝 License

MIT License
