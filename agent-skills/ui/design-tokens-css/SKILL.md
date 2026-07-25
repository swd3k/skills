---
name: design-tokens-css
description: Define and apply a small design token set (color, space, type, radius, elevation) for consistent UI. Use when starting a design system or cleaning inconsistent spacing/colors.
---

# Design Tokens (CSS)

## Minimal set
- **Color**: bg, surface, text, muted, accent, danger, success, border
- **Space**: 4, 8, 12, 16, 24, 32, 48
- **Type**: 12, 14, 16, 20, 28 / weights 400–700
- **Radius**: 6, 10, 14, full
- **Elevation**: e1 hairline, e2 soft shadow
- **Motion**: 120ms, 200ms, 320ms — ease-out

## Usage
```css
.card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius-md);
  padding: var(--space-4);
  box-shadow: var(--elev-2);
}
```

## Rules
- No random `13px` / `#3a3a3a` in components
- Semantic names (`--danger`) over raw (`--red-500`) in app code
- Document tokens in one file

## Acceptance
- New component can be built without new colors
