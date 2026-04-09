# Slug Conventions

Slug naming for features and when the slug may change.

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
