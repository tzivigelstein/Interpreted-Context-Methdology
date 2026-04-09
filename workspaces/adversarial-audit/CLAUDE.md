# Adversarial Audit

A protocol for finding bugs that standard code reviews miss. Designed for an agent auditing a codebase it has not worked on before. The audit looks for **broken assumptions** at every point where the system touches something external, instead of looking for logic errors in code that is internally consistent.

## Folder Map

```
adversarial-audit/
├── CLAUDE.md                          (you are here)
├── CONTEXT.md                         (start here for task routing)
├── stages/
│   ├── 01-identify-borders/           (list every external interaction point)
│   ├── 02-prioritize/                 (rank borders, pick top N to investigate)
│   ├── 03-trace-flows/                (trace full flows for the top borders)
│   ├── 04-question-assumptions/       (apply the 4 questions, generate hypotheses)
│   └── 05-validate-and-report/        (confirm hypotheses, write findings)
└── shared/
    ├── why-this-audit-works.md        (why standard reviews miss these bugs)
    ├── borders.md                     (definition + checklist of border types)
    ├── what-not-to-report.md          (exclusions: style, impossible states, etc.)
    └── audit-conventions.md           (audit slug naming)
```

Cross-workspace techniques live in `/_core/`:

- `/_core/target-repo-detection.md` - identify which external repo the audit is for
- `/_core/stack-and-rules-detection.md` - read the target repo's stack and project rules

## Triggers

| Keyword | Action |
|---------|--------|
| `status` | Scan all `stages/*/output/<repo>/` and show audit progress per repo |

## Routing

| Task | Go To |
|------|-------|
| Start a new audit on a target repo | `stages/01-identify-borders/CONTEXT.md` |
| I have a borders list, prioritize them | `stages/02-prioritize/CONTEXT.md` |
| I have priorities, trace the top flows | `stages/03-trace-flows/CONTEXT.md` |
| I have traces, generate hypotheses | `stages/04-question-assumptions/CONTEXT.md` |
| I have hypotheses, validate and write findings | `stages/05-validate-and-report/CONTEXT.md` |

## What to Load

| Task | Load These | Do NOT Load |
|------|-----------|-------------|
| Identifying borders | `stages/01-identify-borders/CONTEXT.md`, `shared/why-this-audit-works.md`, `shared/borders.md`, `shared/what-not-to-report.md`, `/_core/target-repo-detection.md`, `/_core/stack-and-rules-detection.md` | Other stage CONTEXT.md, four-questions, validation protocol |
| Prioritizing | `stages/02-prioritize/CONTEXT.md`, `stages/02-prioritize/references/prioritization-criteria.md`, the borders artifact | Borders definition (already used), four-questions |
| Tracing flows | `stages/03-trace-flows/CONTEXT.md`, `stages/03-trace-flows/references/flow-tracing-method.md`, the priorities artifact, `/_core/stack-and-rules-detection.md` | Earlier stage CONTEXT.md beyond the priorities artifact |
| Questioning assumptions | `stages/04-question-assumptions/CONTEXT.md`, `stages/04-question-assumptions/references/four-questions.md`, the traces artifact | Earlier stage references |
| Validating and reporting | `stages/05-validate-and-report/CONTEXT.md`, `stages/05-validate-and-report/references/validate-and-report-protocol.md`, the hypotheses artifact, `shared/what-not-to-report.md` | Earlier stage references |

## Stage Handoffs

Each stage writes to `stages/0N-name/output/<repo-name>/` using the file pattern `<audit-slug>-<artifact>.md`:

- `01-identify-borders/output/<repo>/<audit-slug>-borders.md`
- `02-prioritize/output/<repo>/<audit-slug>-priorities.md`
- `03-trace-flows/output/<repo>/<audit-slug>-traces.md`
- `04-question-assumptions/output/<repo>/<audit-slug>-hypotheses.md`
- `05-validate-and-report/output/<repo>/<audit-slug>-findings.md`

The audit slug is set in stage 01 and stays the same through stage 05.
