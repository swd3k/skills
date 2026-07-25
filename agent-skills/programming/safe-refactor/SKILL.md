---
name: safe-refactor
description: Refactor without breaking behavior: characterization tests, small steps, feature flags. Use when cleaning architecture, renaming widely, or extracting services from UI code.
---

# Safe Refactor

## Rules
1. **Green before green** — tests or manual script pass first.
2. Change structure **or** behavior, not both in one commit.
3. Prefer extract method/class over rewrites.
4. Keep public behavior identical unless ticket says otherwise.

## Steps
1. Characterization test around the mess.
2. Extract interface at the boundary you need.
3. Move implementation; keep façade.
4. Delete dead code only after call graph check.
5. Run full test suite + smoke the UI path.

## Pitfalls
- Drive-by formatting across the repo
- Renaming and logic change together
- "Temporary" dual code paths that become permanent

## Acceptance
- Behavior checklist from before still passes
- Diff is reviewable in < ~400 lines per commit when possible
