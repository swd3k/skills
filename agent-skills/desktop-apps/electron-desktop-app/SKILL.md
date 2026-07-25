---
name: electron-desktop-app
description: Scaffold and harden Electron desktop apps: main/preload/renderer isolation, contextBridge, auto-update, packaging. Use when building or auditing Electron shells, IPC, security, or distributable installers.
---

# Electron Desktop App

Use Electron when you need **cross-platform** desktop with full Chromium + Node ecosystem.

## When to use
- macOS + Windows + Linux required
- Heavy web stack already exists
- Photino/Tauri not viable for the team

## Security defaults (non-negotiable)
```js
webPreferences: {
  contextIsolation: true,
  nodeIntegration: false,
  sandbox: true,
  preload: path.join(__dirname, 'preload.js')
}
```
- Expose APIs only via `contextBridge`
- Validate every IPC channel; never pass untrusted paths to `shell.open` / `fs`
- Disable remote module; avoid `enableRemoteModule`

## Structure
```
main/        # process lifecycle, windows, menus, auto-update
preload/     # thin safe API surface
renderer/    # UI (React/Vue/Svelte or plain)
shared/      # types + channel names
```

## Workflow
1. One BrowserWindow first; add tray/menu later.
2. Define typed IPC channels in `shared/channels.ts`.
3. Preload exposes only needed methods.
4. Package with `electron-builder` or `electron-forge`.
5. Code-sign on macOS/Windows for SmartScreen/Gatekeeper.

## Packaging defaults
- NSIS (Windows), DMG (macOS), AppImage (Linux)
- Publish updates via GitHub Releases + `electron-updater`
- Ship asari symbols only if debugging crashes

## Pitfalls
- `nodeIntegration: true` in production
- Huge asar from bundling entire monorepo
- Auto-update without code signing → silent failure
- Blocking main process with sync FS/network

## Acceptance
- Renderer cannot `require('fs')`
- Quit cleans timers and windows
- Update check fails gracefully offline
