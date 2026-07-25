---
name: accessibility-basics
description: Ship accessible web and desktop-web UIs: keyboard, focus, contrast, labels, reduced motion. Use when auditing a11y, fixing focus traps, or implementing dialogs.
---

# Accessibility Basics

## Must
- Full keyboard path for primary tasks
- Visible `:focus-visible` rings
- Buttons are `<button>`, links are `<a href>`
- Icon-only controls have `aria-label`
- Dialogs: focus trap + Escape + restore focus
- Honor `prefers-reduced-motion`

## Forms
- `<label for>` association
- Errors linked with `aria-describedby`
- Don't rely on color alone

## Desktop webviews
- Tab order shouldn't jump to hidden tray clones
- Don't remove outlines globally

## Quick audit
1. Unplug mouse — complete the main task
2. 200% zoom — layout holds
3. High contrast / dark mode — text readable

## Acceptance
- No critical axe/lighthouse a11y blockers on primary pages
