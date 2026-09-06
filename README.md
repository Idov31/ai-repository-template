# AI Marketplace Package Catalog Template

Use this repository as a starting point for a public or private catalog of AI Marketplace packages. Replace the placeholder values below with your own catalog identity, repository URL, and package inventory before publishing.

## Repository layout

- `Skills/`: skill packages.
- `Commands/`: command packages.
- `Mcps/`: MCP server packages.
- `Agents/`: agent packages.
- `Hooks/`: hook packages.
- `Rules/`: rule packages.

Each package belongs at `<type>/<group>/<package-id>/`. It contains an `ai_marketplace.yaml` manifest and the entrypoint declared by that manifest.

## Add the catalog

Replace the placeholders, then add the entry to your AI Marketplace configuration:

```json
{
  "id": "your-catalog-id",
  "label": "Your Catalog Name",
  "url": "https://github.com/your-org/your-catalog",
  "branch": "main",
  "enabled": true,
  "allowDefaultPackages": false
}
```

Configure repository access and credentials to suit your hosting and visibility requirements.

## Package manifest

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
  evaluation_score: 0.0
history:
  previous_revision: 0123456789abcdef0123456789abcdef01234567
```

`metadata.evaluation_score` is optional and applies only to skill packages. Omit `history.previous_revision` for a package's first revision.

## Publishing checklist

1. Replace this template's placeholders and remove unused package-type directories.
2. Add each package's entrypoint, resources, and canonical manifest.
3. Validate manifest schema, entrypoints, paths, encoding, and package-local tests.
4. Update this README with a package inventory if you want the catalog to list published packages.
