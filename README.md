# workflows

Reusable GitHub Actions workflows for every repo in `maiwei-app`. Community
health files (PR/issue templates, CODEOWNERS, SECURITY.md) live in the
separate `maiwei-app/.github` repo.

## Available workflows

| File | Job | Purpose |
|---|---|---|
| `no-ai-attribution.yml` | `check` | Blocks commits/PRs with AI-attributed authorship (required org-wide) |
| `ci-python.yml` | `quality` | ruff lint + JSON schema validation + pytest |
| `ci-flutter.yml` | `quality` | flutter analyze + flutter test |
| `ci-hugo.yml` | `quality` | strict Hugo build (fails on warnings) |
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
    secrets: inherit
    with:
      project-key: maiwei-app_<repo-name>
```

## Planned, not yet built

- `release-please.yml` — versioning/release automation
- `inline-comments.yml` — in-line code review comments

Both are backlog for after the org migration is complete.
