# Stage 03 — Script

Write the full tutorial. Prose for blog posts, narration + screen actions for videos.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../02-outline/output/<slug>-outline.md` | Full file | Section structure |
| Research | `../01-research/output/<slug>-research.md` | `## Happy Path`, `## Prerequisites` | Concrete steps |
| Run metadata | `../01-research/output/tutorial-meta.md` | `format`, `audience` | Tone and structure |
| Voice reference | `references/voice.md` | Full file (if exists) | Your project's voice and tone |

## Process

1. Read the outline, research, and metadata.
2. For each section in the outline, write:
   - For **blog posts**: 2-4 paragraphs of prose with screenshots noted as `[SCREENSHOT: description]`.
   - For **videos**: narration + screen actions in a two-column or alternating format. Mark camera/zoom cues if relevant.
3. Use the user's actual UI labels (from research). Do not invent button names.
4. Add concrete examples wherever a step is abstract.
5. Run the audit. Revise if anything fails.
6. Save the script.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 2 | The first section as a sample, in the chosen format | Whether the tone, length per section, and structure are right before scripting the rest |

## Audit

| Check | Pass Condition |
|---|---|
| Real UI labels | All button/menu/field names match what's in the templates |
| Prerequisites mentioned | The first section explicitly states what the user needs before starting |
| Concrete examples | Every abstract step has at least one concrete example |
| No invented features | Nothing in the script that isn't in the research notes |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Tutorial script | `output/<slug>-script.md` | Markdown matching the chosen format (blog post or video script) |
