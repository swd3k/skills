---
name: web-typography-system
description: Set modular type scales, readable measure, and pairing for marketing and product web UI. Use when text looks uneven, cramped, or unstyled.
---

# Web Typography System

## Defaults
- Body 16–18px marketing, 14–16px product
- Measure ~60–75ch for long reading
- Modular scale (e.g. 1.25)
- Line-height: ~1.5 body, ~1.15 display
- Limit to 2 families (display + body) + optional mono

## Hierarchy
H1 page goal · H2 section · H3 sub · body · meta/label

## CSS sketch
```css
:root {
  --step-0: clamp(1rem, 0.95rem + 0.2vw, 1.125rem);
  --step-1: clamp(1.25rem, 1.1rem + 0.6vw, 1.5rem);
  --step-2: clamp(1.5rem, 1.2rem + 1.2vw, 2rem);
  --step-3: clamp(2rem, 1.4rem + 2vw, 3rem);
}
```

## Pitfalls
- All-caps long sentences
- Gray body on gray bg
- Decorative fonts for forms

## Acceptance
- H1 not wrapping awkwardly at mobile
- Legal/footer text still readable
