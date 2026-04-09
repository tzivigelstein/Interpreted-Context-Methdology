# Feature Pipeline

A spec-driven loop for shipping code features in any external repo. Each feature flows through brief -> design -> implement -> review, with explicit human gates between stages.

## Folder Map

```
feature-pipeline/
├── CLAUDE.md                          (you are here)
├── CONTEXT.md                         (start here for task routing)
├── stages/
│   ├── 01-brief/                      (capture what to do and why)
│   ├── 02-design/                     (Architect designs a spec from the brief)
│   ├── 03-implement/                  (Builder executes the spec)
│   └── 04-review/                     (Architect reviews the diff and writes debt)
└── shared/
    └── conventions.md                 (slug naming and when slugs change)
```

Cross-workspace techniques live in `/_core/`:

- `/_core/target-repo-detection.md` - identify which external repo a feature belongs to
- `/_core/stack-and-rules-detection.md` - read any target repo's stack and project rules

## Triggers

| Keyword | Action |
|---------|--------|
| `status` | Scan all `stages/*/output/<repo>/` and show feature progress per repo |

## Routing

| Task | Go To |
|------|-------|
| Batch-capture feature ideas without designing them | `stages/01-brief/CONTEXT.md` (optional) |
| Start a new feature or design from an existing brief | `stages/02-design/CONTEXT.md` (default entry point) |
| Implement an approved spec | `stages/03-implement/CONTEXT.md` |
| Review a finished implementation | `stages/04-review/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|------|-----------|-------------|
| Batch-capturing briefs | `stages/01-brief/CONTEXT.md`, `/_core/target-repo-detection.md`, `shared/conventions.md` | Other stage CONTEXT.md, design protocol |
| Designing a spec (default entry) | `stages/02-design/CONTEXT.md`, `stages/02-design/references/design-protocol.md`, `/_core/stack-and-rules-detection.md`, `/_core/target-repo-detection.md`, `shared/conventions.md`, the brief (if exists) | Implementation rules, review protocol |
| Implementing a spec | `stages/03-implement/CONTEXT.md`, `stages/03-implement/references/implementation-rules.md`, `/_core/stack-and-rules-detection.md`, the spec, the target repo's project rules | Brief, design protocol, review protocol |
| Reviewing changes | `stages/04-review/CONTEXT.md`, `stages/04-review/references/review-protocol.md`, `/_core/stack-and-rules-detection.md`, the spec, the implementation summary, the target repo's project rules | Brief, design protocol, implementation rules |

## Stage Handoffs

Each stage writes to `stages/0N-name/output/<repo-name>/` using the file pattern `<slug>-<artifact>.md`:

- `01-brief/output/<repo>/<slug>-brief.md` (written by stage 01 or inline by stage 02)
- `02-design/output/<repo>/<slug>-spec.md`
- `03-implement/output/<repo>/<slug>-implementation-summary.md`
- `04-review/output/<repo>/<slug>-review.md` and `<slug>-debt.md`

The slug may be renamed once in stage 02 when the design agent normalizes it to clean English. After that rename, every later stage uses the new slug.

## Iteration

When stage 04 returns REQUEST CHANGES, the feature re-enters the pipeline:

- **Implementation fixes**: re-enter stage 03. The implementer reads the review findings, fixes the issues, appends to the implementation summary, and re-triggers stage 04.
- **Spec amendments**: re-enter stage 02. The architect amends the spec (appending a "Revision" section, not rewriting), then the feature flows through 03 → 04 again.

APPROVE or APPROVE WITH NOTES ends the pipeline. The next step is PR creation (see stage 04 post-approval).
