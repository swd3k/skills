---
name: agent-skill-authoring
description: Author portable agent skills (SKILL.md) compatible with Codex, Claude, Cursor, and Grok. Use when creating or refining skills in this repo.
---

# Agent Skill Authoring

## Contract
```
agent-skills/<category>/<skill-name>/
  SKILL.md       # required
  REFERENCES.md  # links only, optional
  ARTICLE.md     # long form, optional
  demo/          # optional proof
```

## SKILL.md frontmatter
```yaml
---
name: skill-folder-name
description: What it does + when to use (triggers). One tight paragraph.
---
```

## Body sections that work
- When to use
- Defaults
- Step workflow
- Snippets
- Pitfalls
- Acceptance checks
- Questions to ask if vague

## Style
- Procedural, skimmable, confident
- Defaults over essays
- No secrets, no private paths
- Portable across repos

## Validation
- [ ] Clear trigger in description
- [ ] Concrete steps
- [ ] At least one acceptance check
- [ ] Name matches folder
