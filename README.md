# Aero V1 (Legacy)
<p align="center"><img width="180" height="180" alt="_jjf830gdbfp7fnqjekoe_0" src="https://github.com/user-attachments/assets/57c2adf9-b5ef-453a-a9df-de9e573b8560"/>
</p>

Aero is a lightweight Windows utility for controlling File Explorer window opacity.

## Features
- Adjustable File Explorer opacity with a 0–255 slider
- Automatic opacity application to newly opened Explorer windows
- Windows startup support
- Starts minimized to the system tray
- Tray menu with Show and Exit actions
- Persistent settings stored locally
- Light and Dark appearance modes
- Custom accent color picker
- Reset appearance to default
- Improved shutdown handling and safer Explorer monitoring
- Basic event logging for diagnostics
<p align="center"><img width="801" height="471" alt="image" src="https://github.com/user-attachments/assets/d218909e-ac49-4d59-9551-ec51625d175b" />
 </p>
 
<p align="center"> <img width="802" height="468" alt="image" src="https://github.com/user-attachments/assets/1b34b7bf-08f0-4249-9e71-7aedb3743dbf" />  </p>


## Download
Go to the latest GitHub Release and download latest release.

## Requirements
- Windows 10 or Windows 11
- No separate Python installation required for the release executable

## How to run
1. Download `Aero` from Releases.
2. Double-click it.
3. Use the tray icon to hide or restore the app.

## Files
- `Aero.exe` — packaged app.
- `icon.ico` — app icon used by the build.
- `config.json` — generated automatically next to the exe.
- `aero.log` — generated automatically next to the exe.

## Building from source
Install dependencies:
```powershell
python -m pip install -r requirements.txt
```

Build:
```powershell
python -m PyInstaller --clean --noconfirm --onefile --windowed --name Aero --icon=icon.ico --add-data "icon.ico;." --hidden-import=PIL --hidden-import=pystray main.py
```

## Notes
If the tray icon does not appear correctly, make sure `pystray` and `Pillow` are installed in the build environment.
