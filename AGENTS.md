# AI Marketplace Package Catalog Guide

## Purpose

This repository is a reusable AI Marketplace package catalog template. Use neutral, user-owned names and publish only `ai_marketplace.yaml` schema v1 manifests. Do not introduce legacy filenames, compatibility aliases, deprecated branding, or historical metadata from another catalog.

## Layout

Place each package at `<type>/<group>/<package-id>/ai_marketplace.yaml`. Keep the declared entrypoint at the package root and add resource directories only when they are used.

For MCP packages, keep `.mcp.json`, `install.py`, and `uninstall.py` at the package root. Lifecycle scripts must be non-interactive and idempotent. Use a catalog-specific launcher prefix and ownership-state filename; do not reuse identifiers from another repository.

## Manifest contract

```yaml
schema_version: 1
minimum_reader_schema_version: 1
package:
  name: "@example/sample-skill"
  type: skill
  version: "1.0.0"
  description: "Briefly describe what this package provides."
  group: Example
  entrypoint: SKILL.md
targets:
  platforms: [codex, github-copilot]
  delivery: [workspace, global]
metadata:
  tags: [example]
```

- Names use `@scope/package-id` and match the package folder.
- Types: `skill`, `command`, `mcp`, `agent`, `hook`, or `rule`.
- Platforms: `codex`, `cursor`, `github-copilot`, or `claude`.
- Delivery: `workspace`, `global`, or `cloud`; MCP packages are global-only and cloud delivery is agent-only.
- Put tags in `metadata.tags` and Git revisions in `history.previous_revision`.
- Add a one-decimal `metadata.evaluation_score` only for skills after completing the catalog's chosen quality evaluation.

## Workflow

1. Choose the package type and group directory.
2. Add the entrypoint and required resources.
3. Add the canonical manifest; preserve a package version for schema-only changes.
4. Update README inventory data if the catalog maintains one.
5. Validate manifests, entrypoints, paths, UTF-8 encoding, and package-local tests.

Keep package metadata and any README inventory consistent.
