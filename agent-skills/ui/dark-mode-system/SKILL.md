---
name: dark-mode-system
description: Implement light/dark (and system) themes with design tokens and accessible contrast. Use when adding theme toggles, desktop dark UI, or fixing unreadable dark styles.
---

# Dark Mode System

## Token approach
```css
:root {
  --bg: #f6f7f9;
  --surface: #ffffff;
  --text: #12141a;
  --muted: #5c6370;
  --accent: #3b82f6;
  --danger: #dc2626;
  --border: rgba(0,0,0,.08);
}
[data-theme="dark"] {
  --bg: #0e1014;
  --surface: #171a21;
  --text: #eef1f6;
  --muted: #9aa3b2;
  --accent: #60a5fa;
  --danger: #f87171;
  --border: rgba(255,255,255,.10);
}
```

## Rules
- Theme via tokens, not scattered hex
- Follow `prefers-color-scheme` when mode = system
- Persist user choice in settings
- Test contrast for text, borders, focus rings
- Images/icons may need theme variants

## Pitfalls
- Pure `#000` backgrounds with gray text (muddy)
- Box-shadows that disappear on dark
- Hardcoded white modals in dark app

## Acceptance
- Toggle switches all chrome in one frame
- Focus ring visible in both themes
