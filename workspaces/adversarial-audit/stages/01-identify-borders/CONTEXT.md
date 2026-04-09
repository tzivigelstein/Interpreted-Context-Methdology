# Stage 01 - Identify Borders

List every point where the target repo touches something external. Be exhaustive. Do not judge or prioritize. The goal is completeness, not focus.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Target repo | `git rev-parse --show-toplevel` of cwd or as set during target detection | Full repo | What you are auditing |
| Borders definition | `../../shared/borders.md` | Full file | What counts as a border, plus the checklist |
| What not to report | `../../shared/what-not-to-report.md` | Full file | What to skip even at this stage |
| Why this audit works | `../../shared/why-this-audit-works.md` | Full file | Mental frame |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Full file | Stack hints at what borders to expect (API libs, ORMs, file IO, etc.) |
| Target repo detection | `/_core/target-repo-detection.md` | Full file | Identify which repo and assign the audit slug |
| Audit conventions | `../../shared/audit-conventions.md` | "Audit Slug" section | How to name this audit |

## Process

1. Run target repo detection. Set the audit slug per `../../shared/audit-conventions.md`.
2. Run stack and rules detection. The stack hints at what borders exist (e.g., SQLAlchemy means database; Celery means async jobs).
3. Read `../../shared/borders.md` to internalize what counts as a border.
4. Walk the repo systematically using the checklist in `borders.md`. Look at network borders, storage borders, input borders, concurrency borders, user flow borders, and time borders.
5. For each border found, capture: ID, what it is, where it lives (file:line), direction (in/out/both), what external system it touches.
6. Be exhaustive. Do not skip borders that "look fine". Stage 02 will judge.
7. Save the list to `output/<repo>/<audit-slug>-borders.md` as a markdown table.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Borders list | `output/<repo>/<audit-slug>-borders.md` | Markdown table: ID, Border, Location, Direction, External System |

## What This Stage Does NOT Do

- Judge which borders are risky (stage 02 does that)
- Trace flows (stage 03 does that)
- Look for bugs (stages 04 and 05 do that)
- Skip borders that "feel safe"
