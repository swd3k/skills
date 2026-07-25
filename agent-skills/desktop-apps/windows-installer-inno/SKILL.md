---
name: windows-installer-inno
description: Create Windows Setup.exe with Inno Setup 6: multi-arch FDD packages, silent install, CI-friendly portable Inno install. Use when packaging .NET/desktop apps, GitHub Actions release jobs, or fixing corrupt jrsoftware download.php installs.
---

# Windows Installer (Inno Setup)

Produce trustworthy **Setup.exe** for Windows desktop apps.

## Defaults
- Inno Setup 6.7.x
- Framework-dependent payload when app is .NET 8 FDD
- One Setup per RID or multi-arch sections if needed
- Compression: `lzma2/max` is fine; avoid extreme settings that trigger AV heuristics
- AppId GUID stable across versions

## Local build
```powershell
# ISCC path common locations
& "${env:ProgramFiles(x86)}\Inno Setup 6\ISCC.exe" installer\App.iss /DMyAppVersion=1.2.3
```

## CI install (reliable)
Do **not** use `https://jrsoftware.org/download.php/is.exe` in CI (often corrupt).

Use official GitHub portable installer:
```powershell
$url = "https://github.com/jrsoftware/issrc/releases/download/is-6_7_3/innosetup-6.7.3.exe"
$dest = Join-Path $env:RUNNER_TEMP "InnoSetup6"
# /VERYSILENT /CURRENTUSER /PORTABLE=1 /DIR=$dest
# Then ISCC = Join-Path $dest "ISCC.exe"
```

## .iss checklist
- `[Setup]` AppName, AppVersion, DefaultDirName, PrivilegesRequired
- Prefer `PrivilegesRequired=lowest` if app elevates only for specific actions
- `[Files]` SourceDir absolute or script-relative consistently
- `[Icons]` Start Menu + optional desktop
- Uninstall deletes only app-owned files

## Pitfalls
- Baking absolute machine paths into OutputDir
- Self-contained 50MB+ Setup when FDD would be 3MB
- Silent install flags not tested (`/VERYSILENT /NORESTART`)

## Acceptance
- Clean install + run + uninstall on fresh Windows 10/11 VM
- Version string matches assembly + GitHub release tag
