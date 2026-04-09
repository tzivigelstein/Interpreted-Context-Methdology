# What Not to Report

Findings that should NOT appear in the audit output, even when confirmed. Filter at every stage but enforce strictly in stage 05.

## Style and Naming

Code style, variable naming, formatting, indentation, docstring presence. These belong in code review, not in an adversarial audit.

## Missing Error Handling for Impossible States

If the code path is genuinely unreachable, do not report missing error handling for it. "What if Python suddenly returns a string from `len()`" is not a finding. Defensive code for impossible states is its own anti-pattern.

The exception: if the "impossible" state is reachable via one of the four borders questions (input format, operation order, data completeness), then it IS reportable. The audit's job is precisely to find those reachable-but-unmodeled states.

## Performance Without Evidence

"This query could be slow" is not a finding without evidence that it IS slow in production. Performance findings need: a measured baseline, an observed problem, or a clear scaling argument tied to expected load.

## Architectural Preferences

"I would have used a repository pattern here" is not a finding. The audit looks for broken assumptions, not for choices the auditor would have made differently.

## Anything Internally Consistent

If the code is correct within the system's own model, no broken assumption about the outside world, it is not a finding. The audit's whole purpose is to find where the model diverges from reality. Code that is wrong in some abstract sense but correct given its own assumptions belongs in a regular review.

## What If You Find One of These Anyway

If you find something interesting that does not fit the audit format, capture it in a separate `<audit-slug>-side-notes.md` file at the same path. Do not put it in the main findings file. The findings file is the deliverable for "real bugs". Side notes are for "interesting things I noticed".
