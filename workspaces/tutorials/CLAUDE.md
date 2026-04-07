# Tutorials

Produce tutorials (written + optional video script) explaining a project's features to its users.

## Folder Map

```
tutorials/
├── CLAUDE.md          (you are here)
├── CONTEXT.md         (start here for task routing)
└── stages/
    ├── 01-research/      (investigate the feature in the codebase + UI)
    ├── 02-outline/       (structure the tutorial: scenes/sections)
    ├── 03-script/        (write the full script — narration + screen actions)
    └── 04-publish/       (format for blog post and/or YouTube description)
```

## Triggers

| Keyword | Action |
|---|---|
| `status` | Scan `stages/*/output/` and show which stages have artifacts |

## Routing

| Task | Go To |
|---|---|
| New tutorial, no research yet | `stages/01-research/CONTEXT.md` |
| Have research, need to structure it | `stages/02-outline/CONTEXT.md` |
| Have outline, need full script | `stages/03-script/CONTEXT.md` |
| Have script, need to format for publication | `stages/04-publish/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|---|---|---|
| Researching | Stage 01 CONTEXT.md + relevant source files | Other stage CONTEXT.md |
| Outlining | Stage 02 CONTEXT.md + Stage 01 output | Source code |
| Scripting | Stage 03 CONTEXT.md + Stage 02 output | Stage 01 raw research |
| Publishing | Stage 04 CONTEXT.md + Stage 03 output | Earlier outputs |

## Stage Handoffs

Each stage writes to its own `output/`. The next stage reads the previous stage's `output/`. The user can edit any output file before running the next stage.
