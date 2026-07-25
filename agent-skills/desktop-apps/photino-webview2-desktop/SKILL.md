---
name: photino-webview2-desktop
description: Build Windows desktop apps with Photino.NET + WebView2 (HTML/CSS/JS UI, C# backend). Use when creating or fixing Photino shells, WebView2 white screens, file:// vs raw HTML loading, host bridge messages, or .NET 8 Windows-only desktop tools.
---

# Photino + WebView2 Desktop App

Ship a thin native shell: **C# for system work**, **HTML/CSS/JS for UI**, WebView2 for rendering.

## When to use
- Windows-only utility, fixer, tray tool, local admin app
- Need small installers (framework-dependent ~2–5 MB)
- Electron is too heavy; WPF/WinUI is overkill for web-ish UI

## Defaults
- Target: `net8.0-windows`
- UI: static HTML in `wwwroot` or embedded resources
- Bridge: Photino `WebMessageReceived` / `SendWebMessage`
- Privilege: `asInvoker` + elevate only the action that needs admin
- Publish: framework-dependent (FDD) unless offline install is required

## Architecture
```
UI (HTML/JS)  --postMessage-->  Host (C#)  -->  Services (hosts, files, net)
     ^                              |
     +--------- JSON events --------+
```

## Workflow
1. **Define capabilities** — what must run as admin, what is pure UI, what is network.
2. **Scaffold** — Core / Infrastructure / Ui projects; keep UI project `net8.0-windows`.
3. **Load UI reliably**
   - Prefer `file://` to real files on disk (CSS/JS work).
   - Fallback: `LoadRawString` with **fully inlined CSS/JS** (about:blank blocks external CSS).
   - Never mix half-relative assets with raw-string load.
4. **Host bridge** — versioned JSON commands: `{ "cmd": "apply", "payload": {...} }`.
5. **Errors** — surface host failures as toast/banner in UI, never silent catch.
6. **Publish** — FDD + Inno Setup; document .NET Desktop Runtime + WebView2 Runtime.

## White screen checklist
- [ ] DevTools: CSS 404 / blocked?
- [ ] Loading via file:// vs LoadRawString?
- [ ] Path separators / encoding of HTML path?
- [ ] WebView2 runtime installed?
- [ ] JS exception before first paint?

## Pitfalls
- Self-contained publish balloons to ~40–60 MB
- Always-admin manifest → Defender / SmartScreen noise
- PowerShell Bypass for hosts edits → AV false positives
- Absolute `C:\...` paths baked into release UI

## Acceptance
- Cold start shows real UI in < 2s on mid PC
- Apply/cancel/error states all visible
- Works after install without Visual Studio
- Elevated action prompts UAC only when needed
