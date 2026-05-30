# tuneops-ai/.github — Org-Wide Defaults

This repo holds tuneops-ai organization-level defaults consumed automatically by
GitHub or by org-wide tooling.

## Current contents

| File | Purpose | Consumed by |
|------|---------|-------------|
| `renovate-config.json` | Shared Renovate config (Phase 0: Go modules only) | Per-repo `renovate.json` files via `"extends": ["github>tuneops-ai/.github:renovate-config"]` |

## How Renovate consumption works

Each tuneops-ai repo that wants Renovate adds a thin `renovate.json` like:

```json
{
  "extends": ["github>tuneops-ai/.github:renovate-config"]
}
```

That repo inherits all defaults from `renovate-config.json` here. To override
a default for a single repo, add the override field in the per-repo file:

```json
{
  "extends": ["github>tuneops-ai/.github:renovate-config"],
  "automerge": true
}
```

## Governance

Filed via F-09cb6 (versioning policy rule) + CHORE-493c2 (Renovate minimal
config). Phase 0 of the CI/CD master plan. See:

- `tuneops-docs/workspace/tasks/features/F-09cb6_VERSIONING_POLICY_RULE.md`
- `tuneops-docs/workspace/tasks/chores/CHORE-493c2_RENOVATE_MINIMAL_CONFIG.md`
- `tuneops-docs/workspace/analysis/CICD_COMPREHENSIVE_ANALYSIS.md`

## Phase 2 expansion (future)

When Phase 2 of the CI/CD master plan lands, this repo will expand to include:

- npm + Docker + GHA action pin managers (currently `enabledManagers: ["gomod"]`)
- Stricter rangeStrategy + automerge policies per the F-09cb6 versioning tier
- Possibly community/PR templates (CONTRIBUTING.md, ISSUE_TEMPLATE/) shared
  across all tuneops-ai repos
