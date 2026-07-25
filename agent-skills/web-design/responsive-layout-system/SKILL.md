---
name: responsive-layout-system
description: Implement robust responsive layouts with breakpoints, fluid type, and container patterns. Use when fixing mobile breakage, overflow, or inconsistent section widths.
---

# Responsive Layout System

## Defaults
```css
:root {
  --content: 72rem;
  --gutter: clamp(1rem, 4vw, 2rem);
}
.container {
  width: min(100% - 2*var(--gutter), var(--content));
  margin-inline: auto;
}
```

## Breakpoints (example)
- sm 640 · md 768 · lg 1024 · xl 1280
- Design mobile structure first for content sites; desktop-first OK for dense tools

## Rules
- Prefer `min`, `clamp`, flex/grid over hard px pages
- Avoid horizontal scroll on 360px width
- Tables: cardify or scroll with shadow hints
- Images: `max-width:100%; height:auto`

## Pitfalls
- Fixed 1440px mockups shipped as-is
- Hover-only critical actions on mobile

## Acceptance
- 360 / 768 / 1280 checked for main templates
