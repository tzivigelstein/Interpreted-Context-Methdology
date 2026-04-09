# Stage 03 - Trace Flows

For each top border, trace the FULL flow from trigger to side effect. Do not stop at function boundaries. The bugs hide where the flow crosses files.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Priorities | `../02-prioritize/output/<repo>/<audit-slug>-priorities.md` | Full file | The top N borders to trace |
| Tracing method | `references/flow-tracing-method.md` | Full file | How to trace a flow end-to-end |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Full file | Knowing the stack helps follow framework call paths |

## Process

1. Read the priorities list. Take the top N.
2. For each border, follow the tracing method in `references/flow-tracing-method.md`:
   - What triggers the flow?
   - What data does it read?
   - What transformations does it apply?
   - What does it write?
   - What does it report (success/failure signal)?
3. Write each trace as a numbered narrative, with file:line citations.
4. Do NOT ask the user to look at files. You have the repo. Trace it yourself.
5. Save all traces to `output/<repo>/<audit-slug>-traces.md`.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Flow traces | `output/<repo>/<audit-slug>-traces.md` | One section per traced border, each with the 5-step narrative and file:line refs |

## What This Stage Does NOT Do

- Generate hypotheses about what could be wrong (stage 04 does that)
- Validate any suspected bug (stage 05 does that)
- Trace borders that were not in the top N
