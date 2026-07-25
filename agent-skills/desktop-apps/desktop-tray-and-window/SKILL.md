---
name: desktop-tray-and-window
description: Implement system tray, single-instance, minimize-to-tray, and window lifecycle for desktop utilities. Use when building tray apps, background helpers, or fixing multi-window/instance bugs.
---

# Tray, Window, Single-Instance

Utility apps live in the tray more than the taskbar.

## Defaults
- Single instance via named mutex / lockfile
- Close button → hide to tray (configurable)
- Tray menu: Open, Status, Quit
- Balloon/toast only for important state changes

## Workflow
1. Create mutex at startup; if owned → focus existing window and exit.
2. Main window: sensible default size, min size, remember last position (user folder).
3. Tray icon: monochrome variants for light/dark taskbar when possible.
4. Exit path: dispose icon, release mutex, flush settings.

## UX rules
- Never trap the user: Quit must always be reachable
- First run: show window once, then tray is OK
- Status in tooltip: "Connected", "Needs attention", "Idle"

## Pitfalls
- Orphan tray icons after crash (dispose on all exit paths)
- Multiple instances fighting over ports/files
- Modal dialogs behind hidden windows

## Acceptance
- Second launch focuses first instance
- Quit removes tray icon immediately
- Settings persist across restarts
