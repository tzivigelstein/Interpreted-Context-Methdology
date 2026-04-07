# Stage 02 — Categorize

Group raw commits into release-note categories. Drop noise.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../01-collect-commits/output/<slug>-commits.md` | Full file | Raw commit list |
| Run metadata | `../01-collect-commits/output/release-meta.md` | `audience` field | Drives what counts as "user-facing" |

## Process

1. Read the commit list and the metadata.
2. Bucket each commit into one of: `Features`, `Improvements`, `Fixes`, `Internal` (chores/refactors/tests/CI).
3. If audience is "end users", move all `Internal` commits to a separate `Dropped` section (do not delete; user might want to keep some).
4. For each bucket, sort by impact (your judgment). Note any commit that's ambiguous in a `Needs Review` section.
5. Save to `output/`.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 4 | The categorized list with `Needs Review` highlighted | Whether to recategorize / drop / keep ambiguous items |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Categorized commits | `output/<slug>-categorized.md` | Markdown with `## Features`, `## Improvements`, `## Fixes`, `## Internal`, `## Dropped`, `## Needs Review` sections |
