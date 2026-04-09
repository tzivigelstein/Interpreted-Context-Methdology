# Stage 05 - Validate and Report

Confirm or reject each hypothesis from stage 04, cheaply. Write the confirmed bugs as findings in the prescribed format. The output is the audit deliverable.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Hypotheses | `../04-question-assumptions/output/<repo>/<audit-slug>-hypotheses.md` | Full file | What to validate |
| Validate and report protocol | `references/validate-and-report-protocol.md` | Full file | Validation method + finding format |
| What not to report | `../../shared/what-not-to-report.md` | Full file | Exclusions to filter findings |

## Process

1. Read the hypotheses list.
2. For each hypothesis, follow the validation method in `references/validate-and-report-protocol.md`:
   - Can you confirm by reading code alone? Trace the exact path.
   - Can you write a test that demonstrates the bug?
   - Can you reproduce it locally with a minimal change?
3. If confirmed: write the finding in the prescribed format.
4. If rejected: note it briefly so the user knows you considered it.
5. Apply the exclusions from `shared/what-not-to-report.md`. Some confirmed issues should not be reported (style, architectural preference, performance without evidence).
6. Save all findings to `output/<repo>/<audit-slug>-findings.md`.

## Audit

| Check | Pass Condition |
|-------|---------------|
| Every hypothesis addressed | Each hypothesis from stage 04 is either confirmed (with finding) or rejected (with reason) |
| Findings are concrete | Each finding cites file:line and includes a proposed fix that is not vague |
| Exclusions applied | No finding violates `shared/what-not-to-report.md` |
| Severity assigned | Each finding has a severity tag in the title |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Findings report | `output/<repo>/<audit-slug>-findings.md` | One section per confirmed finding in the prescribed format |

## What This Stage Does NOT Do

- Fix the code. The audit reports; the user (or a feature-pipeline run) fixes.
- Report unvalidated hypotheses as findings.
- Report things in the exclusions list.
- Be vague about location or fix.
