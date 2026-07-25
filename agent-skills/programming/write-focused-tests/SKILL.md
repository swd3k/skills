---
name: write-focused-tests
description: Write high-value unit and integration tests without brittle UI snapshots. Use when adding coverage, fixing regressions, or deciding what not to test.
---

# Focused Tests

## What to test first
1. Pure domain rules and parsers
2. File/network adapters with temp dirs / handlers
3. Regression cases that already burned you

## What to skip early
- Exact pixel UI
- Third-party SDK internals
- Framework boilerplate

## Patterns
- Arrange–Act–Assert
- One logical assert theme per test
- Name: `Method_Scenario_Expected`
- Deterministic: no wall-clock flakiness without fakes

## Desktop
- Core tests on Linux CI
- Windows-only tests gated with traits / `windows-latest` job

## Acceptance
- `dotnet test` green locally and in CI
- New bug → new test when feasible
