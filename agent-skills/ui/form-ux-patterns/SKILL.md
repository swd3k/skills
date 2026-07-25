---
name: form-ux-patterns
description: Design usable forms: labels, validation, multi-step, submit states. Use when building settings, onboarding, checkout, or desktop configuration forms.
---

# Form UX Patterns

## Rules
1. Label every field (visible, not only placeholder).
2. Validate on blur + on submit; don't yell on first keystroke.
3. Preserve user input on error.
4. Submit button shows progress and disables double-submit.
5. Success is explicit (toast, inline, or next step).

## Field order
- Ask only what you need now
- Group related fields
- Dangerous fields separated

## Validation copy
- Say how to fix: "Enter an IPv4 like 1.2.3.4"
- Not only "Invalid"

## Multi-step
- Show step N of M
- Back never destroys data without warning
- Summary before irreversible apply

## Desktop-specific
- Map Enter to primary submit when safe
- Escape closes dialog without save unless dirty-guard

## Acceptance
- Keyboard-only completion works
- Error summary for long forms
