# Feature Pipeline - Task Routing

Use this file to decide which stage to enter and which model to use.

## Roles

The pipeline is built around two distinct roles. Each stage assumes one of them.

| Role | Stages | Capability Profile | Why |
|------|--------|--------------------|-----|
| Architect | 02-design, 04-review | Deep reasoning, codebase investigation, architectural judgment | Investigation, scope decisions, quality audit |
| Builder | 03-implement | Precise instruction execution, high code output, spec adherence | Spec execution without re-architecting |

The brief stage (01) has no capability preference. It is mostly user-driven.

The split is intentional. When the same agent designs and implements, specs drift toward what is easy to write and away from what is correct. When the same agent implements and reviews, the review excuses the implementer's choices. Use the strongest reasoning model available for Architect stages, and a fast, precise model for Builder.

## Per-Run Inputs

Before entering any stage, the agent must know:

1. **Target repo**: which external repo the feature is for. See `/_core/target-repo-detection.md`.
2. **Feature slug**: a kebab-case identifier. Provisional in stage 01, normalized in stage 02. See `shared/conventions.md` "Slug Naming".

## Stage Entry Points

| User intent | Enter |
|-------------|-------|
| Batch-capture ideas for later ("anotame esto", "track this idea") | `stages/01-brief/CONTEXT.md` (optional) |
| Start a new feature or design from a brief ("quiero hacer X", "armemos el spec") | `stages/02-design/CONTEXT.md` (default entry) |
| Build an approved spec ("dale, hacelo", "implement it") | `stages/03-implement/CONTEXT.md` |
| Review an implementation ("revisame esto", "review the diff") | `stages/04-review/CONTEXT.md` |

## Pipeline

```
[01-brief] -> 02-design -> 03-implement -> 04-review
                                  ^              |
                                  |   REQUEST CHANGES
                                  +------<-------+
```

Stage 01 is optional — stage 02 captures the user's intent inline if no brief exists. The default entry point is stage 02.

When stage 04 returns REQUEST CHANGES, the loop depends on the nature of the findings:
- **Implementation issues** (bugs, missing cleanup, test failures): re-enter stage 03 with the review as additional input. The implementer reads the review, fixes the issues, updates the implementation summary, and re-triggers stage 04.
- **Spec issues** (wrong scope, missing requirements, design flaws): re-enter stage 02 to amend the spec, then flow through 03 → 04 again.

## Shared Resources

| Resource | Location | Contains |
|----------|----------|----------|
| Slug naming | `shared/conventions.md` | Slug rules and when slugs change |
| Target repo detection | `/_core/target-repo-detection.md` | How to identify the target repo from cwd |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | How to read any target repo's stack and project rules at runtime |
