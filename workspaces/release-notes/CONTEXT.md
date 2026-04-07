# Release Notes — Task Routing

Use this file to decide which stage to enter based on what the user wants.

## Per-Run Inputs (collected at entry)

Before entering Stage 01, ask the user:

1. **Release tag or commit range**: from which point should we collect changes? Default: from the latest git tag to `HEAD`.
2. **Audience**: end users or developers? Default: end users.
3. **Channels to publish to**: Discord, Telegram, web post, all? Default: all.

Save the answers as a small `release-meta.md` file in `stages/01-collect-commits/output/` so later stages can read them.

## Stage Entry Points

| If the user says... | Enter |
|---|---|
| "Let's start the next release notes" | `stages/01-collect-commits/CONTEXT.md` |
| "I have the commit list, group them" | `stages/02-categorize/CONTEXT.md` |
| "Write the changelog" | `stages/03-draft/CONTEXT.md` |
| "Format this for Discord" | `stages/04-publish/CONTEXT.md` |

## Pipeline

```
01-collect-commits → 02-categorize → 03-draft → 04-publish
```

The pipeline is strictly linear. Skip stages only if the user explicitly provides the corresponding artifact themselves.
