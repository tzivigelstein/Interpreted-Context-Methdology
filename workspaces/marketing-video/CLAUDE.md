# Marketing Video

Produce conversion-focused marketing videos for any product, applying Alex Hormozi's frameworks (Value Equation, Grand Slam Offer, Hook formulas, VSL structure). Format-agnostic: works for 15s ads, 60s landing videos, 90s social, multi-minute VSLs, and long-form sales letters.

## Folder Map

```
marketing-video/
├── CLAUDE.md          (you are here)
├── CONTEXT.md         (start here for task routing)
├── skills/
│   └── frontend-design/   (bundled: design rules for on-screen text, layout, polish)
└── stages/
    ├── 01-avatar-positioning/   (who is the dream client, what do they want, what hurts)
    ├── 02-offer-value-stack/    (Value Equation + bonuses + guarantee + urgency)
    ├── 03-hook-mechanism/       (5-10 hook variations + unique mechanism)
    ├── 04-script/               (full script in Hormozi 7-part VSL structure)
    └── 05-production-package/   (storyboard + shot list + voiceover + on-screen text)
```

## Triggers

| Keyword | Action |
|---|---|
| `status` | Scan `stages/*/output/` and show which stages have artifacts |

## Routing

| Task | Go To |
|---|---|
| Starting from scratch on a new product | `stages/01-avatar-positioning/CONTEXT.md` |
| Already know the audience, need the offer | `stages/02-offer-value-stack/CONTEXT.md` |
| Have the offer, need hooks and mechanism | `stages/03-hook-mechanism/CONTEXT.md` |
| Have hook + mechanism, write the script | `stages/04-script/CONTEXT.md` |
| Have a script, build the production package | `stages/05-production-package/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|---|---|---|
| Avatar work | Stage 01 CONTEXT.md + its references | Other stages |
| Offer work | Stage 02 CONTEXT.md + its references + Stage 01 output | Stage 03/04/05 |
| Hook work | Stage 03 CONTEXT.md + its references + Stage 02 output | Stage 04/05 |
| Scripting | Stage 04 CONTEXT.md + its references + Stages 01-03 output | Stage 05 |
| Production package | Stage 05 CONTEXT.md + its references + Stage 04 output + skills/frontend-design/SKILL.md | Earlier raw research |

## Output Language

The workspace files are in English. The output artifacts (scripts, hooks, copy) follow the language the user requests at runtime. If the user asks in Spanish, output goes in Spanish. If unspecified, default to the same language the user is conversing in.

## Stage Handoffs

Each stage writes to its own `output/`. The next stage reads the previous stage's `output/`. Edits to output files between stages are picked up automatically.
