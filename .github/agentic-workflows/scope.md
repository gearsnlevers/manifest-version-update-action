# Project scope

Read by the issue gate's scope check (Repo Concierge). The check is off for a repository without this file.

## Purpose

Update the version in `package.json` and, optionally, `package-lock.json` to a given version.

## In scope

- Writing a version into `package.json` and, optionally, `package-lock.json`
- Choosing the manifest paths and the working directory
- The action's inputs and outputs, documentation, tests, and release pipeline

## Out of scope

<!-- Every item here can close an issue automatically as not planned. Keep the list short and specific. -->

- Computing the next version, creating git tags or GitHub releases, or publishing. The action only writes the version it is given.

## Needs a maintainer

- Manifest formats other than `package.json` and `package-lock.json`, such as `pyproject.toml`, `Cargo.toml` or `pom.xml`
- Updating other lock files, such as `yarn.lock` or `pnpm-lock.yaml`

## Where to go instead

- Computing versions: version-bump-action. Preflight checks: release-preflight-action. Publishing: npm-trusted-publish-action.
