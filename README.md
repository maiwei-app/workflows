# workflows

Reusable GitHub Actions workflows for every repo in `maiwei-app`. Community
health files (PR/issue templates, CODEOWNERS, SECURITY.md) live in the
separate `maiwei-app/.github` repo.

All release PRs are customized to remove third-party tool attribution.

## Available workflows

| File | Job | Purpose |
|---|---|---|
| `no-ai-attribution.yml` | `check` | Blocks commits/PRs with AI-attributed authorship (required org-wide) |
| `ci-python.yml` | `quality` | ruff lint + JSON schema validation (see below) + pytest |
| `ci-flutter.yml` | `quality` | flutter analyze + flutter test |
| `ci-hugo.yml` | `quality` | strict Hugo build (fails on warnings) |
| `ci-yml-sch-linter.yml` | `quality` | YAML syntax lint + GitHub Actions workflow validation (runs on this repo's workflows) |
| `sonar-scan.yml` | `sonar` | CI-based SonarCloud scan (needs `SONAR_TOKEN` + `SONAR_ORGANIZATION`, both org-level) |

## Usage example

```yaml
name: CI

on:
  pull_request:
    branches: [main]
  push:
    branches: [main]

jobs:
  no-ai-attribution:
    uses: maiwei-app/workflows/.github/workflows/no-ai-attribution.yml@main

  quality:
    uses: maiwei-app/workflows/.github/workflows/ci-python.yml@main

  sonar:
    needs: quality
    uses: maiwei-app/workflows/.github/workflows/sonar-scan.yml@main
    with:
      project-key: maiwei-app_<repo-name>
    secrets:
      sonar-token: ${{ secrets.SONAR_TOKEN }}
```

`secrets: inherit` does **not** work for `sonar-scan.yml` — it requires a
secret named exactly `sonar-token`, and `inherit` only passes secrets
through under their original name (the org secret is `SONAR_TOKEN`). Map
it explicitly as shown above, or the `sonar` job fails with "Secret
sonar-token is required, but not provided".

`sonar-scan.yml` applies no path exclusions — it analyzes the full
consuming repo, `.github/**` included. There's no per-repo opt-out input;
if a repo genuinely needs to exclude a path, that's a call to make
explicitly in that repo's own Sonar project settings, not a default to
inherit silently from here.

## `ci-python.yml`'s JSON schema validation

Files matching a known name are validated against their real published
schema (via `check-jsonschema --schemafile`); anything else falls back to
syntax-only validation (`json.tool`) with an explicit log line saying so —
never silently treated as if it were spec-validated. The mapping lives in
`ci-python.yml`'s "Validate JSON against known schemas" step:

| Filename | Schema |
|---|---|
| `.release-please-config.json` | `googleapis/release-please` `schemas/config.json` |
| `.release-please-manifest.json` | `googleapis/release-please` `schemas/manifest.json` |
| `.commitlintrc.json` | `json.schemastore.org/commitlintrc.json` |
| `.markdownlint.json` | `json.schemastore.org/markdownlint.json` |

When a repo adopts a new JSON config file that has a real schema (check
[SchemaStore](https://www.schemastore.org/json/) first, or the tool's own
repo), add it to this table **and** to the `schemas` map in
`ci-python.yml` — otherwise it silently falls back to syntax-only
validation instead of failing loudly, which defeats the point.

## Planned, not yet built

- `release-please.yml` — versioning/release automation
- `inline-comments.yml` — in-line code review comments

Both are backlog for after the org migration is complete.
