# workflows

Reusable GitHub Actions workflows for every repo in `maiwei-app`. Community
health files (PR/issue templates, CODEOWNERS, SECURITY.md) live in the
separate `maiwei-app/.github` repo.

## Available workflows

| File | Job | Purpose |
|---|---|---|
| `no-ai-attribution.yml` | `check` | Blocks commits/PRs with AI-attributed authorship (required org-wide) |
| `ci-python.yml` | `quality` | ruff lint + JSON schema validation (see below) + pytest |
| `ci-flutter.yml` | `quality` | flutter analyze + flutter test |
| `ci-hugo.yml` | `quality` | strict Hugo build (fails on warnings) |
| `ci-yml-sch-linter.yml` | `quality` | YAML syntax lint + GitHub Actions workflow validation (runs on this repo's workflows) |
| `lint-frontend.yml` | `quality` | stylelint (CSS/SCSS) + eslint (browser JS) + vitest (only if test files exist) |
| `lint-toml.yml` | `quality` | TOML syntax validation (taplo) |
| `lint-yaml.yml` | `quality` | YAML syntax lint (yamllint) across the whole consuming repo, not just workflows |
| `sonar-scan.yml` | `sonar` | CI-based SonarCloud scan (needs `SONAR_TOKEN` + `SONAR_ORGANIZATION`, both org-level) |
| `sonar-api.yml` | `query` | Manual bridge to SonarCloud's REST API — see "AI/model access to gated org secrets" below |

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

`secrets: inherit` does **not** work for `sonar-scan.yml`: it requires a
secret named exactly `sonar-token`, and `inherit` only passes secrets
through under their original name (the org secret is `SONAR_TOKEN`). Map
it explicitly as shown above, or the `sonar` job fails with "Secret
sonar-token is required, but not provided".

`sonar-scan.yml` applies no path exclusions: it analyzes the full
consuming repo, `.github/**` included. There's no per-repo opt-out input;
if a repo genuinely needs to exclude a path, that's a call to make
explicitly in that repo's own Sonar project settings, not a default to
inherit silently from here.

## `ci-python.yml`'s JSON schema validation

Files matching a known name are validated against their real published
schema (via `check-jsonschema --schemafile`); anything else falls back to
syntax-only validation (`json.tool`) with an explicit log line saying so,
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
`ci-python.yml`, otherwise it silently falls back to syntax-only
validation instead of failing loudly, which defeats the point.

## `lint-frontend.yml`'s config fallback

`stylelint` and `eslint` respect a config file already present in the consuming
repo (`.stylelintrc.json`/`.stylelintrc`/`stylelint.config.js`,
`.eslintrc.json`/`.eslintrc.js`/`eslint.config.js`). If none exists, the
workflow falls back to a minimal default (`stylelint-config-standard-scss` for
CSS/SCSS, `eslint:recommended` with a browser environment for JS), same
never-silently-skip-validation principle as the JSON schema fallback below.
JS unit tests (`vitest`) only run if `*.test.js`/`*.spec.js` files exist; no
placeholder tests are added to force the check green, same as `pytest` in
`ci-python.yml`.

## `release.yml`'s release-please customization

`.release-please-config.json` sets `pull-request-header` and
`pull-request-footer` at the config root to replace release-please's
default PR text (attribution footer, `:beep: :boop:` header) with
project-specific wording. Both are root-level keys, not nested under
`packages`: this repo has a single package (`.`), configured directly
at the root.

## AI/model access to gated org secrets — `sonar-api.yml`

GitHub Actions secrets are write-only via every API: no permission level,
including org admin, can ever read a secret's value back — only a workflow
run gets it injected at runtime. That means an AI agent (Claude, or any
future model) can never fetch `SONAR_TOKEN` directly, no matter what App
permissions it holds.

`sonar-api.yml` is the standing workaround: a manually-dispatched workflow
in this repo that calls the SonarCloud API from inside a runner, where
`SONAR_TOKEN` is available, and writes only the (non-secret) response to
the run's job summary. The token itself never appears in any log, output,
or API response the agent can read.

**How the agent uses it:**

```bash
gh workflow run sonar-api.yml --repo maiwei-app/workflows \
  -f method=GET \
  -f 'path=settings/values?component=maiwei-app_<repo>&keys=sonar.analysis.mode'

# then find the run and read its summary, e.g.:
gh run list --repo maiwei-app/workflows --workflow=sonar-api.yml --limit 1 --json databaseId --jq '.[0].databaseId'
gh api /repos/maiwei-app/workflows/actions/runs/<run-id>/jobs --jq '.jobs[0].id' \
  | xargs -I{} gh api /repos/maiwei-app/workflows/actions/jobs/{}/logs
```

`method` is `GET` or `POST`; `path` is the SonarCloud API path and query
string with no leading slash; `body` (optional) is a form-encoded POST
body. This is generic on purpose — it's the one door for any future
Sonar-API need, not a single-purpose script that gets re-created every
time. If a genuinely different gated secret needs the same treatment
later, copy this pattern rather than building a one-off.

Requires the App triggering it to have `actions: write` on this repo (to
dispatch the run and read its logs) — a separate permission from the
`contents`/`workflows`/`issues` ones already granted for other tasks.

## Planned, not yet built

- `release-please.yml`: versioning/release automation
- `inline-comments.yml`: in-line code review comments

Both are backlog for after the org migration is complete.
