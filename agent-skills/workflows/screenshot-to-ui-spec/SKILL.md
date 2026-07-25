---
name: screenshot-to-ui-spec
description: Turn screenshots or screen recordings into structured UI implementation specs and prompts. Use when recreating interfaces from references or briefings with images.
---

# Screenshot → UI Spec

## Steps
1. Inventory regions (nav, hero, cards, forms, footer).
2. Measure hierarchy: what draws the eye first?
3. Extract tokens: colors, radii, shadows, type sizes (approx OK).
4. Note interactions if video: hover, scroll, loaders.
5. Write implementation spec:
   - layout
   - components list
   - states
   - copy (exact if legible)
6. Call out **originality**: inspire structure, don't steal brand assets/copy.

## Output template
```text
## Thesis
## Layout
## Tokens
## Components
## Motion
## Copy
## Non-goals / differences from reference
```

## Pitfalls
- Pixel-copying trademarked brands
- Ignoring responsive behavior not visible in one frame
