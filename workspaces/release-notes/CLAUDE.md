# Release Notes

Turn raw git history into a user-facing changelog ready to publish to your project's community channels.

## Folder Map

```
release-notes/
├── CLAUDE.md          (you are here)
├── CONTEXT.md         (start here for task routing)
└── stages/
    ├── 01-collect-commits/   (pull commits since last release tag)
    ├── 02-categorize/         (group by type: feat / fix / refactor / chore)
    ├── 03-draft/              (write user-facing changelog)
    └── 04-publish/            (format for Discord / Telegram / web post)
```

## Triggers

| Keyword | Action |
|---|---|
| `status` | Scan `stages/*/output/` and show which stages have artifacts |

## Routing

| Task | Go To |
|---|---|
| New release, start from scratch | `stages/01-collect-commits/CONTEXT.md` |
| Already have commits, need to categorize | `stages/02-categorize/CONTEXT.md` |
| Already categorized, need to draft | `stages/03-draft/CONTEXT.md` |
| Have draft, need to format for publication | `stages/04-publish/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|---|---|---|
| Collecting commits | Stage 01 CONTEXT.md only | Other stage CONTEXT.md |
| Categorizing | Stage 02 CONTEXT.md + Stage 01 output | Stage 03/04 CONTEXT.md |
| Drafting | Stage 03 CONTEXT.md + Stage 02 output | Stage 01 raw output |
| Publishing | Stage 04 CONTEXT.md + Stage 03 output | Earlier outputs |

## Stage Handoffs

Each stage writes to its own `output/`. The next stage reads the previous stage's `output/`. Edits to output files are picked up automatically by the next stage.
