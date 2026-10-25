---
status: accepted
date: 2026-10-25
decision-makers:
  - maintainers
applies-to:
  - action.yml
  - scripts/update-manifest.sh
  - README.md
---

# The action writes the version it is given and nothing else

## Context and problem statement

Writing a version into the manifests is a separate step from deciding it. Recorded retroactively from the README and `.github/agentic-workflows/scope.md`.

## Decision

- The action writes a version into `package.json` and, optionally, `package-lock.json`. The manifest paths and the working directory are inputs.
- It does not compute versions, create tags or releases, or publish. Those are other actions: version-bump-action (computes the version), release-preflight-action (checks collisions and drift), manifest-version-update-action (writes the version), ai-changelog-action (writes the changelog) and npm-trusted-publish-action (publishes).
- Other manifest formats (`pyproject.toml`, `Cargo.toml`, `pom.xml`) and other lock files (`yarn.lock`, `pnpm-lock.yaml`) need a maintainer's decision.

## Consequences

- Nothing else to watch; the decision is the boundary of the action.
