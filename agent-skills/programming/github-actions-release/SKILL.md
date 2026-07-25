---
name: github-actions-release
description: Design GitHub Actions CI/CD for build, test, tag-driven releases, and artifacts. Use when adding workflows, fixing tag-only jobs, or publishing GitHub Releases from CI.
---

# GitHub Actions Release Pipeline

## Pattern
```yaml
on:
  push:
    branches: [main]
    tags: ['v*']
  pull_request:
  workflow_dispatch:

jobs:
  check:        # PR + main — tests
  release-win:  # tags only — publish + installer
  publish:      # upload GitHub Release assets
```

## Critical rules
1. **Workflow file is taken from the tag commit.** Fixing `main` does not heal old tags.
2. Install tools from **stable URLs** (GitHub releases), not flaky marketing download.php pages.
3. Fail on missing artifacts (`if-no-files-found: error`).
4. SHA256 only over files, not directories.
5. `permissions: contents: write` only on release jobs that need it.

## Version from tag
```bash
echo "version=${GITHUB_REF_NAME#v}" >> "$GITHUB_OUTPUT"
```

## Acceptance
- PR runs tests only
- Tag `vX.Y.Z` produces installers + Release
- Re-run after fixing main requires retag or new tag
