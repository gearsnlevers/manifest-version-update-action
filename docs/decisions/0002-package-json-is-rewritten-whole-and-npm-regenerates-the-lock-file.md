---
status: accepted
date: 2026-10-25
decision-makers:
  - maintainers
applies-to:
  - scripts/update-manifest.sh
---

# package.json is rewritten whole and npm regenerates the lock file

## Context and problem statement

Recorded retroactively from the script. The reasons are not written down; the consequences are what callers see.

## Decision

- `package.json` is parsed, its `version` set and the file written back with two-space indentation and a trailing newline.
- `package-lock.json` is not edited by hand. When `update-package-lock` is true (the default) and the file exists, it is regenerated with `npm install --package-lock-only --ignore-scripts`, so no lifecycle script runs.
- A manifest that does not exist is skipped, not an error. The outputs `packageJsonUpdated` and `packageLockUpdated` say what was written.

## Consequences

- A `package.json` formatted differently is reformatted by the first run.
- What changes in the lock file is whatever npm writes, which can be more than the version line.
