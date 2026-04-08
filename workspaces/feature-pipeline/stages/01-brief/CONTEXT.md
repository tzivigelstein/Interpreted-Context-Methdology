# Stage 01 - Brief

Capture a feature idea before any analysis. The brief is raw user input. The agent's job here is to format and store, not to investigate or judge.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| User | Conversation | A description of what they want and why | Source material |
| Brief template | `references/brief-template.md` | Full file | Structure to populate |
| Conventions | `../../shared/conventions.md` | "Target Repo Detection" and "Slug Naming" sections | Where to write, how to name |

## Process

1. Identify the target repo. Follow "Target Repo Detection" in conventions.
2. Ask the user what they want to do, why, and any constraints they already know about. Use their own words. Do not investigate the codebase. Do not propose scope. The brief is raw input.
3. Pick an initial slug. If the user proposed a name, slugify it. Otherwise generate a rough one from their description. The slug may be in any language. It is provisional. Stage 02 will normalize it.
4. Populate `references/brief-template.md` with the user's answers. Leave any field empty rather than fabricating content.
5. Write to `output/<repo>/<slug>-brief.md`.
6. Tell the user the path and what the next stage is.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Feature brief | `output/<repo>/<slug>-brief.md` | Markdown matching `references/brief-template.md` |

## What This Stage Does NOT Do

- Investigate the codebase
- Decide what is in or out of scope
- Suggest implementation approaches
- Normalize the slug to English (that happens in stage 02)
