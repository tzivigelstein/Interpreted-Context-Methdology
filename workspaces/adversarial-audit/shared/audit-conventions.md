# Audit Conventions

Naming and structure for adversarial audit runs.

## Audit Slug

An audit slug identifies one audit run across all five stages.

Rules:

- Lowercase
- Hyphens (no underscores, no spaces)
- English
- Maximum 5 words
- Descriptive of what was audited

The audit can be scoped:

- A specific flow: `acsm-push-flow`, `skin-upload-pipeline`, `signup-onboarding`
- A subsystem: `auth-routes`, `mods-package-cache`, `payment-webhooks`
- A full repo: append the date, e.g. `full-repo-2026-04`

Examples:

| Bad | Good |
|---|---|
| `audit1` | `acsm-push-flow` |
| `let_me_check_skins` | `skin-upload-pipeline` |
| `full_audit_2026_04_08` | `full-repo-2026-04` |

## Slug Stays Constant

Unlike the feature pipeline (where the design stage may rename the slug), the audit slug is fixed at stage 01 and does not change. If you need to rename, the user does it manually with `mv` across all five stages' output folders.

## Output Per Stage

Each stage writes one file under its output folder, using the slug:

```
stages/01-identify-borders/output/<repo>/<audit-slug>-borders.md
stages/02-prioritize/output/<repo>/<audit-slug>-priorities.md
stages/03-trace-flows/output/<repo>/<audit-slug>-traces.md
stages/04-question-assumptions/output/<repo>/<audit-slug>-hypotheses.md
stages/05-validate-and-report/output/<repo>/<audit-slug>-findings.md
```

If the audit produces side notes (see `what-not-to-report.md`), they go alongside the findings:

```
stages/05-validate-and-report/output/<repo>/<audit-slug>-side-notes.md
```
