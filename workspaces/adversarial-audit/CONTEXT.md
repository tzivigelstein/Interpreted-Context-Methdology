# Adversarial Audit - Task Routing

Use this file to decide which stage to enter and which model to use.

## Mental Frame

Read `shared/why-this-audit-works.md` before any audit work. It explains why this protocol finds bugs that normal reviews miss. Skipping it produces a normal review, not an adversarial audit.

## Recommended Model

The whole pipeline benefits from Opus. Each stage requires investigation, judgment, and skepticism. Sonnet is acceptable for stage 02 (prioritization is more mechanical) but Opus is better for stages 01, 03, 04, and 05.

## Per-Run Inputs

Before entering any stage, the agent must know:

1. **Target repo**: which external repo the audit is for. See `/_core/target-repo-detection.md`.
2. **Audit slug**: a kebab-case identifier for this audit. See `shared/audit-conventions.md`. The slug is set in stage 01 and does not change.
3. **Audit scope** (optional): if the audit covers a specific area (e.g., "auth flow", "skin upload pipeline"), capture it in the slug. If it covers the full repo, use a date-based slug.

## Stage Entry Points

| User intent | Enter |
|-------------|-------|
| Start a new audit ("auditemos X", "let's audit Y") | `stages/01-identify-borders/CONTEXT.md` |
| Pick top borders ("rankeemos esto", "what is high priority") | `stages/02-prioritize/CONTEXT.md` |
| Trace the top flows ("traceemos los top", "trace these") | `stages/03-trace-flows/CONTEXT.md` |
| Look for broken assumptions ("hagamos las preguntas", "what could be wrong") | `stages/04-question-assumptions/CONTEXT.md` |
| Validate and write the report ("validemos esto", "write findings") | `stages/05-validate-and-report/CONTEXT.md` |

## Pipeline

```
01-identify-borders -> 02-prioritize -> 03-trace-flows -> 04-question-assumptions -> 05-validate-and-report
```

Linear per audit. Skipping a stage is allowed only when the user provides the upstream artifact themselves (e.g., "I already have the borders list, just prioritize").

## Shared Resources

| Resource | Location | Contains |
|----------|----------|----------|
| Why this audit works | `shared/why-this-audit-works.md` | Mental frame: why standard reviews miss assumption bugs |
| Borders | `shared/borders.md` | Definition of a border + checklist of common border types |
| What not to report | `shared/what-not-to-report.md` | Exclusions: style, impossible states, performance without evidence |
| Audit conventions | `shared/audit-conventions.md` | Audit slug naming |
| Target repo detection | `/_core/target-repo-detection.md` | Identify which external repo |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Read the target repo's stack and project rules |
