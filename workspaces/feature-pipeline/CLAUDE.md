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
| Capture a new feature idea | `stages/01-brief/CONTEXT.md` |
| Turn a brief into a detailed spec | `stages/02-design/CONTEXT.md` |
| Implement an approved spec | `stages/03-implement/CONTEXT.md` |
| Review a finished implementation | `stages/04-review/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|------|-----------|-------------|
| Writing a brief | `stages/01-brief/CONTEXT.md`, `/_core/target-repo-detection.md`, `shared/conventions.md` | Other stage CONTEXT.md, design protocol |
| Designing a spec | `stages/02-design/CONTEXT.md`, `stages/02-design/references/design-protocol.md`, `/_core/stack-and-rules-detection.md`, `/_core/target-repo-detection.md`, `shared/conventions.md`, the brief | Implementation rules, review protocol |
| Implementing a spec | `stages/03-implement/CONTEXT.md`, `stages/03-implement/references/implementation-rules.md`, `/_core/stack-and-rules-detection.md`, the spec, the target repo's project rules | Brief, design protocol, review protocol |
| Reviewing changes | `stages/04-review/CONTEXT.md`, `stages/04-review/references/review-protocol.md`, `/_core/stack-and-rules-detection.md`, the spec, the implementation summary, the diff, the target repo's project rules | Brief, design protocol, implementation rules |

## Stage Handoffs

Each stage writes to `stages/0N-name/output/<repo-name>/` using the file pattern `<slug>-<artifact>.md`:

- `01-brief/output/<repo>/<slug>-brief.md`
- `02-design/output/<repo>/<slug>-spec.md`
- `03-implement/output/<repo>/<slug>-implementation-summary.md`
- `04-review/output/<repo>/<slug>-review.md` and `<slug>-debt.md`

The slug may be renamed once in stage 02 when the design agent normalizes it to clean English. After that rename, every later stage uses the new slug.
