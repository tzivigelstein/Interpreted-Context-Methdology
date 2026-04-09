# Feature Pipeline - Task Routing

Use this file to decide which stage to enter and which model to use.

## Roles

The pipeline is built around two distinct roles. Each stage assumes one of them.

| Role | Stages | Recommended Model | Why |
|------|--------|-------------------|-----|
| Architect | 02-design, 04-review | Opus | Investigation, scope decisions, quality audit |
| Builder | 03-implement | Sonnet | Spec execution without re-architecting |

The brief stage (01) has no model preference. It is mostly user-driven.

The split is intentional. When the same model designs and implements, specs drift toward what is easy to write and away from what is correct. When the same model implements and reviews, the review excuses the implementer's choices.

## Per-Run Inputs

Before entering any stage, the agent must know:

1. **Target repo**: which external repo the feature is for. See `/_core/target-repo-detection.md`.
2. **Feature slug**: a kebab-case identifier. Provisional in stage 01, normalized in stage 02. See `shared/conventions.md` "Slug Naming".

## Stage Entry Points

| User intent | Enter |
|-------------|-------|
| Capture a feature idea ("anotame esto", "track this idea") | `stages/01-brief/CONTEXT.md` |
| Design the spec ("armemos el spec", "design the feature") | `stages/02-design/CONTEXT.md` |
| Build an approved spec ("dale, hacelo", "implement it") | `stages/03-implement/CONTEXT.md` |
| Review an implementation ("revisame esto", "review the diff") | `stages/04-review/CONTEXT.md` |

## Pipeline

```
01-brief -> 02-design -> 03-implement -> 04-review
```

Linear per feature. Skipping a stage is allowed only when the user provides the upstream artifact themselves.

## Shared Resources

| Resource | Location | Contains |
|----------|----------|----------|
| Slug naming | `shared/conventions.md` | Slug rules and when slugs change |
| Target repo detection | `/_core/target-repo-detection.md` | How to identify the target repo from cwd |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | How to read any target repo's stack and project rules at runtime |
