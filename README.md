# Aero — Windows Explorer Customizer

<p align="center"><img width="180" height="180" alt="Aero logo" src="https://github.com/user-attachments/assets/57c2adf9-b5ef-453a-a9df-de9e573b8560"/></p>

> **Lightweight Windows utility for controlling File Explorer window opacity.**

![windows](https://img.shields.io/badge/Windows-10%20%2F%2011-0078d6)
![python](https://img.shields.io/badge/Python-CustomTkinter-blue)
![status](https://img.shields.io/badge/V1-status%3A%20released-success)
![v2](https://img.shields.io/badge/V2-C%23%20%2B%20WPF%20%28planned%29-6f42c1)

---

## 🧭 Status

| Version | Language | Status |
|---|---|---|
| **V1** | Python (CustomTkinter) | ✅ Released — stable, feature-complete |
| **V2 Pro** | C# + WPF | 🔮 Planned — full rewrite |

---

## ✨ Features

### Core
- **Adjustable opacity** — 0–255 slider for File Explorer windows
- **Auto-apply** — opacity applied automatically to newly opened Explorer windows
- **Persistent settings** — stored locally, survives restarts

### Tray & Startup
- Starts minimized to the system tray
- Tray menu with **Show** and **Exit** actions
- Windows startup support (registry)

### Appearance
- Light and Dark modes
- Custom accent color picker
- Custom **JSON themes**
- Reset appearance to default

### Reliability
- Improved shutdown handling and safer Explorer monitoring
- Basic event logging for diagnostics

---

## 📸 Screenshots

### Main window & slider

<p align="center"><img width="801" height="471" alt="Main window" src="https://github.com/user-attachments/assets/d218909e-ac49-4d59-9551-ec51625d175b"/></p>

### Appearance settings

<p align="center"><img width="802" height="468" alt="Appearance settings" src="https://github.com/user-attachments/assets/1b34b7bf-08f0-4249-9e71-7aedb3743dbf"/></p>

---

## ⚠️ Limitations (V1)

- Aero is designed for **Windows only**.
- Current release targets **File Explorer windows only**.
- Some Windows updates, third-party Explorer extensions, or non-standard Explorer windows may affect behavior.
- Aero cannot guarantee opacity changes for **elevated windows** when Aero itself is not running with matching permissions.
- v1.0 uses **periodic Explorer window checks** — V2 will use Windows Event Hooks instead.

---

## 🚀 Roadmap — V2 Pro (C# + WPF)

- [ ] **System Event Hooks** — replace polling (no periodic checks)
- [ ] **Per-process opacity** — select transparency for specific processes
- [ ] **Profiles** — Gaming / Work / Custom presets
- [ ] **Global hotkeys** — show/hide, opacity up/down
- [ ] **Mica / Acrylic effects** — native Windows 11 materials
- [ ] **Auto-updates** — built-in updater

---

## 📦 Download

Go to the latest GitHub Release and download the latest `Aero.exe`.

## ✅ Requirements

- Windows 10 or Windows 11
- **No Python installation required** — the release executable is standalone

## 🚀 How to run

1. Download `Aero` from Releases.
2. Double-click it.
3. Use the tray icon to hide or restore the app.

## 📁 Files

| File | Purpose |
|---|---|
| `Aero.exe` | Packaged app |
| `icon.ico` | App icon used by the build |
| `config.json` | Generated automatically next to the exe |
| `aero.log` | Generated automatically next to the exe |

---

## 🔧 Building from source

Install build dependencies:

```bash
python -m pip install -r requirements.txt
```

Build the application (PowerShell):

```powershell
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

The executable is created here:

```text
dist\Aero.exe
```

For Command Prompt (`cmd.exe`), use one line:

```bat
python -m PyInstaller --clean --noconfirm --onefile --windowed --name Aero --icon "icon.ico" --add-data "icon.ico;." --collect-all customtkinter --hidden-import PIL --hidden-import pystray main.py
```

---

## 🐛 Reporting Issues

If Aero crashes or behaves unexpectedly:

1. Open `aero.log` next to `Aero.exe`.
2. Note your Windows version and the Aero version.
3. Describe what you were doing when the issue occurred.
4. Attach the relevant part of the log.
5. Create an issue in this repository.

For shutdown-related issues, also check:

```text
Event Viewer → Windows Logs → Application
```

---

## 📝 Notes

If the tray icon does not appear correctly, make sure `pystray` and `Pillow` are installed in the build environment.
