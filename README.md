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

## Limitations

- Aero is designed for Windows only.
- The current release targets File Explorer windows only.
- Some Windows updates, third-party Explorer extensions, or non-standard Explorer windows may affect behavior.
- Aero cannot guarantee opacity changes for elevated windows when Aero itself is not running with matching permissions.
- The app uses periodic Explorer window checks in v1.0. A future version may use Windows Event Hooks instead.

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
Install build dependencies:

```bash
python -m pip install -r requirements.txt
```

Build the application:

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
## Reporting Issues

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
## Notes

If the tray icon does not appear correctly, make sure `pystray` and `Pillow` are installed in the build environment.
