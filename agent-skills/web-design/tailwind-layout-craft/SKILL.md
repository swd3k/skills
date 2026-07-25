---
name: tailwind-layout-craft
description: Use Tailwind CSS with disciplined tokens, reusable patterns, and readable markup. Use when implementing UI in Tailwind or cleaning utility soup.
---

# Tailwind Layout Craft

## Rules
- Extend theme for brand colors/spacing — don't invent random hex in class strings all over
- Extract repeated clusters to components
- Prefer `gap`, `grid`, `flex` patterns over magic margins
- Keep responsive prefixes consistent (`md:`, `lg:`)

## Anti-patterns
- 40 utilities on a single div with no component boundary
- Fighting Tailwind with heavy custom CSS without reason
- Ignoring `container` / max-width system

## Accessibility
- Don't remove focus rings (`outline-none` without replacement)
- Use semantic elements; utilities don't replace structure

## Acceptance
- Design tokens live in tailwind config
- Key components reusable without copy-paste novels
