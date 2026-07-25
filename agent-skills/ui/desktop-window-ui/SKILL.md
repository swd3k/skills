---
name: desktop-window-ui
description: Design desktop application window chrome: title bar density, navigation, panels, status bars, and utility layouts. Use when building Photino/Electron/Tauri/WPF tool UIs rather than marketing pages.
---

# Desktop Window UI

Desktop tools are **dense, keyboard-friendly, calm**. Not landing pages in a frame.

## Defaults
- Content-first: max space for the task
- 12–16px base spacing; 8px grid
- System font stack unless brand requires custom
- Primary action visible without scroll on default size
- Status/footer for version, connection, last error

## Layout patterns
| Pattern | Use |
|---------|-----|
| Single panel + footer actions | Simple fixers, wizards |
| List + detail | Config, logs, multi-item |
| Sidebar nav + content | Multi-section settings |
| Toolbar + canvas | Editors |

## Controls
- Buttons: Primary / Secondary / Danger
- Destructive actions need confirm
- Progress: determinate when known; spinner + label otherwise
- Inline help via `?` popover, not walls of text

## Density
- Prefer compact rows for power users
- Touch targets ≥ 32px if touch possible
- Don't mimic mobile bottom-nav on desktop

## Pitfalls
- Marketing hero inside a 900×600 utility
- Unlabeled icon-only critical actions
- Error only in console

## Acceptance
- Default window shows task complete path
- Keyboard: Tab order logical; Enter activates primary
- Resize to min size still usable
