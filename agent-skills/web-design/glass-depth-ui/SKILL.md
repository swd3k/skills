---
name: glass-depth-ui
description: Apply restrained glassmorphism and depth: blur, borders, elevation — without illegible text. Use when building glass cards, overlays, or dark glassy dashboards.
---

# Glass & Depth UI

## Recipe
```css
.glass {
  background: color-mix(in srgb, var(--surface) 72%, transparent);
  border: 1px solid var(--border);
  backdrop-filter: blur(12px);
  box-shadow: var(--elev-2);
}
```

## Rules
- Glass only on a **busy or gradient** background — else it's muddy
- Keep text contrast; never white 40% on light blur
- Limit blur radius for performance (8–16px typical)
- Prefer hairline borders + soft shadow over heavy skeuomorphism

## Pitfalls
- Every card glassed → visual noise
- Backdrop-filter on huge regions → jank
- Ignoring Firefox/safari fallbacks (solid surface)

## Acceptance
- Text passes contrast on glass samples
- Fallback without backdrop-filter still readable
