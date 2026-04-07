# Stage 03 — Draft

Turn categorized commits into a user-facing changelog. Translate technical commits into language end users understand.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../02-categorize/output/<slug>-categorized.md` | Full file | What to write about |
| Run metadata | `../01-collect-commits/output/release-meta.md` | `audience` field | Tone and depth |
| Voice reference | `references/voice.md` | Full file (if exists) | Your project's voice and tone |

## Process

1. Read the categorized commits and run metadata.
2. For each `Features` commit, write a 1-3 sentence user-facing description: what changed, why it matters to the user, how to use it.
3. For each `Improvements` commit, write a 1-2 sentence description focused on the user benefit.
4. For each `Fixes` commit, write a 1 sentence description: what was broken from the user's perspective.
5. Skip `Internal` and `Dropped` unless the audience is developers.
6. Open with a 2-3 sentence summary highlighting the headline change.
7. Run the audit. Revise if anything fails.
8. Save to `output/`.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 6 | The draft with the summary at top | Whether the headline is right; reorder/rewrite if not |

## Audit

| Check | Pass Condition |
|---|---|
| User-facing language | No commit hashes, no file paths, no internal jargon |
| Concrete benefit | Every entry says what changed for the user, not what changed in code |
| Length | Under 600 words for end-user audience, no limit for dev audience |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Changelog draft | `output/<slug>-changelog.md` | Markdown with `## Summary`, `## New`, `## Improved`, `## Fixed` sections |
