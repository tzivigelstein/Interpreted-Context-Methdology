# Stage 02 — Outline

Structure the tutorial into sections (or scenes, if it's a video). Each section has a single purpose.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../01-research/output/<slug>-research.md` | Full file | Source material |
| Run metadata | `../01-research/output/tutorial-meta.md` | `audience`, `format`, `length` | Drives section count and depth |

## Process

1. Read research notes and metadata.
2. Decide on a section count appropriate for the length target:
   - Short: 3-5 sections
   - Medium: 5-8 sections
   - Long: 8-12 sections
3. For each section, define: title, one-sentence purpose, what the reader/viewer learns.
4. Open with a "Why this matters" section (2-4 sentences). Close with a "Next steps" section pointing to related features.
5. If format includes video, mark sections that need a screen recording vs. those that are voice-over only.
6. Save the outline.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 4 | The full section list with one-sentence purposes | Reorder, merge, split, or drop sections before scripting |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Tutorial outline | `output/<slug>-outline.md` | Markdown with numbered sections, each having `### Section N: Title`, `**Purpose**`, `**Reader learns**`, optional `**Screen recording**` |
