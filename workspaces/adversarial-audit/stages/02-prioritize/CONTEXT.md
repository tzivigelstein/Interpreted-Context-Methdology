# Stage 02 - Prioritize

Rank the borders by which ones are most likely to hide bugs. Pick the top N to investigate in stages 03 through 05. Time spent here pays off because the next stages are expensive per border.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Borders list | `../01-identify-borders/output/<repo>/<audit-slug>-borders.md` | Full file | What you are ranking |
| Prioritization criteria | `references/prioritization-criteria.md` | Full file | The four ranking factors |

## Process

1. Read the borders list.
2. Read the prioritization criteria.
3. For each border, score it on the four factors: impact, complexity, visibility, novelty. Use plain language ("high/medium/low"), not numbers. Numbers fake precision.
4. Sort the borders by composite ranking. Top of the list is what stage 03 traces.
5. Decide N (how many borders to investigate). Default: top 5 to 10. Ask the user if they want more or fewer.
6. Save the prioritized list to `output/<repo>/<audit-slug>-priorities.md`.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| 4 | The ranked list with rationale per border | How many to take into stage 03 (the top N), or to re-rank specific borders |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Prioritized borders | `output/<repo>/<audit-slug>-priorities.md` | Markdown table: Rank, Border ID, Impact, Complexity, Visibility, Novelty, Rationale |

## What This Stage Does NOT Do

- Add new borders not in stage 01's output
- Trace flows (stage 03 does that)
- Investigate hypotheses (stage 04 does that)
