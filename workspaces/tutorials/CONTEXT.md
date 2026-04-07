# Tutorials — Task Routing

## Per-Run Inputs (collected at entry)

Before entering Stage 01, ask the user:

1. **Feature/topic**: which feature is the tutorial about? (e.g. "uploading a file", "configuring a project", "publishing content")
2. **Audience**: who is this tutorial for? Be specific about user role (e.g. admin, end user, developer). Default: end user.
3. **Format**: written blog post only, video script only, or both? Default: both.
4. **Length target**: short (under 5 min read / 3 min video), medium (5-10 / 5 min), long (10+ / 10 min)? Default: medium.

Save the answers as `tutorial-meta.md` in `stages/01-research/output/` so later stages can read them.

## Stage Entry Points

| If the user says... | Enter |
|---|---|
| "I want to write a tutorial about X" | `stages/01-research/CONTEXT.md` |
| "Here's the research, structure it" | `stages/02-outline/CONTEXT.md` |
| "Write the full script" | `stages/03-script/CONTEXT.md` |
| "Format this for the blog" | `stages/04-publish/CONTEXT.md` |

## Pipeline

```
01-research → 02-outline → 03-script → 04-publish
```

Pipeline is strictly linear. Each stage produces a single artifact that becomes the next stage's input.
