# Stage 01 — Research

Investigate the feature being tutorialized. Read the code, identify the user flow, capture the relevant entry points, UI surfaces, and business logic.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| User input | Conversation | `tutorial-meta.md` from CONTEXT.md questions | Topic, audience, format, length |
| Project source | UI/route layer | Handlers or routes touching the feature | Real entry points |
| Project source | View/template layer | What the user actually sees | UI flow |
| Project source | Application/business layer | Logic invoked from those routes | Business logic |
| Project glossary | Project's domain glossary, README, or docs | Relevant terms | Avoid ambiguous wording |

## Process

1. Read `tutorial-meta.md`. Note the topic and audience.
2. Search the codebase for routes, templates, and use cases related to the topic. List file paths with line numbers.
3. Trace the happy path from the user's first click to the final result. Note any forks (e.g. error states, optional steps).
4. Note any prerequisites the user needs (login, permissions, prior setup).
5. Save findings to `output/`. Do NOT write tutorial prose yet — Stage 02 does the structuring.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Research notes | `output/<topic-slug>-research.md` | Markdown with `## Entry Points`, `## Happy Path`, `## Forks`, `## Prerequisites`, `## Open Questions` sections |
| Run metadata | `output/tutorial-meta.md` | Key-value markdown (topic, audience, format, length) |

If you find that the feature works differently than the user described, flag it in `## Open Questions` instead of guessing.
