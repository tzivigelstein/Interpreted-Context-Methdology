# Stage 04 - Question Assumptions

For each traced flow, apply the 4 questions to find broken assumptions. Generate hypotheses about what could be wrong. Do not validate them yet.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Traces | `../03-trace-flows/output/<repo>/<audit-slug>-traces.md` | Full file | The flows to question |
| Four questions | `references/four-questions.md` | Full file | The 4 categories of broken assumptions |

## Process

1. Read all traces from stage 03.
2. For each trace, apply the four questions from `references/four-questions.md`:
   - Q1: Are we the source of truth?
   - Q2: Does input follow the expected format?
   - Q3: Do operations happen in the expected order?
   - Q4: Is our data complete?
3. For each question, generate hypotheses ("what could go wrong here?"). Be paranoid. A hypothesis does not need to be confirmed yet, just plausible.
4. Capture each hypothesis with: which trace it belongs to, which of the 4 questions it answers, the assumption the code makes, and what reality might be.
5. Save all hypotheses to `output/<repo>/<audit-slug>-hypotheses.md`.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| 4 | The hypotheses, grouped by trace and question | Which hypotheses to validate first in stage 05, or which to discard as implausible |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Hypotheses | `output/<repo>/<audit-slug>-hypotheses.md` | One section per trace, with hypotheses grouped under Q1 through Q4 |

## What This Stage Does NOT Do

- Validate hypotheses (stage 05 does that)
- Write final findings (stage 05 does that)
- Discard hypotheses for being "unlikely". Generate freely; validation filters
