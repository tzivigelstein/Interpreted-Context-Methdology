# Stage 03 - Implement

Execute the spec. No re-design, no scope changes. If the spec is wrong or ambiguous, stop and ask before writing code.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Spec | `../02-design/output/<repo>/<slug>-spec.md` | Full file | Contract to execute |
| Implementation rules | `references/implementation-rules.md` | Full file | How to write the code, what to clean up, what to verify |
| Stack and rules detection | `../../shared/stack-and-rules-detection.md` | Full file | How to find the target repo's project rules |
| Target repo | `git rev-parse --show-toplevel` of cwd or as set during target detection | The files the spec touches, plus tests | Where the changes go |

## Process

1. Read the spec fully before writing any code.
2. Run stack and rules detection on the target repo. Apply the rules.
3. Implement the spec task by task. Do not deviate from scope.
4. Clean up everything your changes make obsolete (see implementation rules).
5. Run the full test suite. If anything fails, fix it before finishing.
6. Write `output/<repo>/<slug>-implementation-summary.md` with branch or commit, files touched, decisions made, and anything deferred.
7. Tell the user it is ready for review.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Code changes | The target repo (commits or staged diff) | Code |
| Implementation summary | `output/<repo>/<slug>-implementation-summary.md` | See "Implementation Summary" in `references/implementation-rules.md` |

## What This Stage Does NOT Do

- Re-architect or change scope. If something seems wrong, stop and ask.
- Add features the spec did not request.
- Skip the cleanup step.
- Skip running the full test suite.
