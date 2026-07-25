---
name: css-motion-fundamentals
description: Add purposeful CSS/JS motion: hover, enter, scroll reveals, without harming performance or a11y. Use when animating UI, fixing jank, or reducing motion.
---

# CSS Motion Fundamentals

## Principles
- Motion explains state change; it is not decoration tax
- Animate `transform` and `opacity` primarily
- 150–300ms UI; longer only for narrative hero
- `prefers-reduced-motion: reduce` → instant final state

## Patterns
- Hover: 120–180ms ease-out
- Enter: fade+raise 8–16px
- Scroll reveal: once, subtle, staggered children ≤ 60ms
- Page transitions: optional; never block content

## Performance
- Avoid animating large `blur`/`box-shadow` continuously
- Pause offscreen loops
- One scroll library max

## Pitfalls
- Infinite bounce attention spam
- Scroll-jacking without purpose
- Motion required to read content

## Acceptance
- Reduced-motion path verified
- No layout thrash in DevTools performance sample
