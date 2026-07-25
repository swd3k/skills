---
name: tauri-desktop-app
description: Build lightweight cross-platform desktop apps with Tauri 2 (Rust shell + web UI). Use when the user wants small binaries, system APIs, or an Electron alternative with strong security defaults.
---

# Tauri Desktop App

Rust shell + web frontend. Small binaries, OS webview, capability-based permissions.

## When to use
- Cross-platform, size matters
- Team can maintain a small Rust boundary
- Need fine-grained FS/network permissions

## Defaults
- Tauri 2
- Frontend: Vite + any framework
- Capabilities: least privilege in `capabilities/*.json`
- Bundle: MSI/NSIS on Windows, DMG on macOS

## Workflow
1. `npm create tauri-app` (or pnpm/yarn).
2. List every native API the UI needs → map to commands.
3. Implement `#[tauri::command]` with explicit error types.
4. Lock capabilities: only grant `fs:allow-read` paths you need.
5. Build and smoke-test on each target OS.

## Security
- No broad `shell:allow-execute` in production
- Validate paths; reject `..` traversal
- CSP in `tauri.conf.json` for production

## Pitfalls
- Debugging only the web side while Rust panics
- Over-granting scopes "just to make it work"
- Forgetting to rebuild after capability changes

## Acceptance
- Binary size competitive with native tools
- Denied API fails with clear UI message
- Offline install works without Node on the machine
