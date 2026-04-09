# Stage 03 - Implement

Execute the spec. No re-design, no scope changes. If the spec is wrong or ambiguous, stop and ask before writing code.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Spec | `../02-design/output/<repo>/<slug>-spec.md` | Full file | Contract to execute |
| Implementation rules | `references/implementation-rules.md` | Full file | Pre-flight, coding rules, cleanup, verification |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Full file | How to find the target repo's project rules |
| Review findings (iteration only) | `../04-review/output/<repo>/<slug>-review.md` | Full file | Blocking findings to address (only when re-entering after REQUEST CHANGES) |
| Target repo | `git rev-parse --show-toplevel` of cwd or as set during target detection | The files the spec touches, plus tests | Where the changes go |

## Process

1. Run the pre-flight check: clean working tree, correct base branch, create or checkout `feat/<slug>` branch. See implementation rules.
2. Read the spec fully before writing any code.
3. If re-entering after REQUEST CHANGES, read the review findings and address every blocking issue.
4. Run stack and rules detection on the target repo. Apply the rules.
5. Implement the spec task by task. Do not deviate from scope. For specs with 5+ tasks, checkpoint after each task (see implementation rules).
6. Clean up everything your changes make obsolete (see implementation rules).
7. Run the full test suite. If anything fails, fix it before finishing.
8. Write `output/<repo>/<slug>-implementation-summary.md` with branch name, files touched, decisions made, and anything deferred.
9. Tell the user it is ready for review.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Code changes | The target repo (commits or staged diff) | Code |
| Implementation summary | `output/<repo>/<slug>-implementation-summary.md` | See "Implementation Summary" in `references/implementation-rules.md` |

## What This Stage Does NOT Do

- Re-architect or change scope. If something seems wrong, stop and ask.
- Add features the spec did not request.
- Skip the pre-flight check or commit to the wrong branch.
- Skip the cleanup step.
- Skip running the full test suite.
