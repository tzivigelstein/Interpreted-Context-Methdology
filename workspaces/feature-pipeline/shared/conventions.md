# Conventions

Cross-stage conventions for this workspace.

## Target Repo Detection

The pipeline operates on EXTERNAL repos. The agent must know which repo a feature belongs to before reading or writing any artifact.

Detection logic:

1. Run `git rev-parse --show-toplevel` from the current working directory.
2. If the result is the icm repo itself (this workspace's home), the cwd is icm. The agent does NOT yet know the target. Ask the user: "which repo is this feature for?" and accept either a repo name or an absolute path.
3. Otherwise, the result is the target repo. The basename of that path is `<repo>` for all output paths in this workspace. Example: `/home/tzivigelstein/codes/ac-hub` -> `<repo>` is `ac-hub`.
4. If the cwd is not inside any git repo, ask the user explicitly. Do not guess.

The `<repo>` value is used as a subfolder in every stage's `output/` so that artifacts from different repos do not collide.

## Slug Naming

A slug identifies a feature across all four stages.

Rules:

- Lowercase
- Hyphens (no underscores, no spaces)
- English (the user may propose any language; the design stage normalizes)
- Maximum 5 words
- Descriptive of what the feature does, not how
- No leading or trailing hyphens

Examples:

| Bad | Good |
|---|---|
| `pasar-download_url-a-acsm-durante-push-de-mods` | `acsm-mod-push-download-url` |
| `Fix Bug` | `fix-payment-rounding-bug` |
| `feature-1` | `signup-form-validation` |
| `add-new-page-for-the-checkout-flow-with-validation-and-error-states` | `checkout-page-validation` |

## When the Slug Changes

The slug usually changes once, in stage 02-design, when the design agent renames the rough user-provided slug to a clean English version. After that rename, all subsequent stages use the new slug. Stage 02 also renames the brief file in `01-brief/output/<repo>/`.

If the slug needs to change after stage 02, the user does it manually with `mv` and tells the agent the new name.
