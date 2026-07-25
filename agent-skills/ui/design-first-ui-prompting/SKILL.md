---
name: design-first-ui-prompting
description: Turn vague UI ideas into tight design-first specs for consistent generation. Use when prompting for screens, dashboards, marketing sections, or desktop chrome; covers hierarchy, constraints, variants, and negative prompts.
---

# Design-First UI Prompting

**Prompt like a design system, not a wish.**

## Skeleton
```text
GOAL
- What screen / component?
- Who is it for?
- Success criteria (clarity, speed, conversion, calm)

FORMAT
- Platform: web / desktop window / mobile
- Size or density: compact utility vs marketing

LAYOUT
- Grid / columns
- Hierarchy: title → support → body → primary action
- Zones: nav, main, aside, status

TYPE
- Font vibe (system UI vs editorial)
- Weights and sizes for H1/body/meta
- One mono face only if data-dense

COLOR + MATERIAL
- Background, surface, text, one accent
- Elevation: flat / soft shadow / hairline border

STATES
- default, hover, active, disabled, loading, error, empty

COPY (exact strings)
- ...

CONSTRAINTS (change 1–2 only per variant)
- ...

NEGATIVE
- No extra logos, no lorem in final, no rainbow accents
```

## Iteration
1. Lock layout + hierarchy + copy.
2. Variants change **one** variable: accent, density, or image crop.
3. If text breaks: generate layout without labels, typeset after.

## Questions when vague
- Single message of this screen?
- Primary action verb?
- Utility tool vs marketing vibe?
