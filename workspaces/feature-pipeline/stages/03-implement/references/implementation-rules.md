# Implementation Rules

You are executing an approved spec. Your job is to write code that matches the spec, leaves no garbage behind, and passes tests.

## Pre-Flight Check

Before anything else, verify the workspace is ready:

1. Ensure the working tree is clean (`git status`). If there are uncommitted changes, ask the user how to proceed.
2. Ensure you are on the correct base branch (usually `main` or `master`). Pull latest if behind remote.
3. Create a feature branch: `git checkout -b feat/<slug>` from the base branch. If a branch for this slug already exists (iteration after REQUEST CHANGES), check it out instead of creating a new one.
4. Confirm the target repo path matches what the spec expects.

## Before You Write Code

1. Read the spec fully. End to end. Do not start implementing after reading only the first task.
2. Read every project rule the stack-and-rules detection found. The spec lists which rules are most relevant. Read those carefully.
3. If anything in the spec is ambiguous, contradictory, or seems wrong, stop and ask the user before writing code. Do not interpret silently.
4. If re-entering after REQUEST CHANGES, read the review findings in `../04-review/output/<repo>/<slug>-review.md` before resuming. Address every finding marked as blocking.

## While You Write Code

- Implement task by task in the order the spec lists. The order may matter.
- Do not expand scope. The spec is the contract.
- Do not add features, configurability, or abstractions the spec did not ask for. "I might need this later" is not a reason.
- Follow project rules over existing code patterns. If the surrounding code uses a style that contradicts a project rule, follow the rule.
- If existing code the feature touches violates a project rule, note it in the implementation summary under "Out-of-scope findings" — do not fix it unless the spec asks for it.
- Add tests where the spec asks for them or where the project rules require them.

### Checkpoints (for specs with 5+ tasks)

If the spec has 5 or more tasks, pause after completing each task and present:
- What was just completed (one sentence).
- Files touched.
- Any decisions made or ambiguities encountered.
- Ask: "Continue with next task, or review what's done so far?"

For specs with fewer than 5 tasks, implement all tasks before reporting.

## After You Write Code

Clean up everything your changes make obsolete:

- Remove unused imports.
- Delete tests that no longer apply. Do not leave stale test cases.
- Remove dead code, unused variables, orphaned functions.
- Update existing tests whose assertions changed because of your work.

The diff you leave behind should be ready for review with zero cleanup needed.

## Verify

1. Run the full test suite. Not just the tests you touched. The full suite.
2. If anything fails, fix it before finishing. Do not hand off red tests.
3. Run any linters or type checkers the project uses.

## Implementation Summary

Write a summary to `output/<repo>/<slug>-implementation-summary.md` so the review stage has a handoff. Keep it short. One page or less. The diff itself is the canonical record of what changed.

Structure:

```
# {{slug}} - Implementation Summary

**Date:** YYYY-MM-DD
**Branch or commit:** {{branch-name or sha}}

## Files Touched
{{git diff --name-only output, grouped by area}}

## Decisions
{{Any place the spec was ambiguous and you made a call. One bullet per decision. Be specific.}}

## Deferred or Skipped
{{Anything the spec asked for that you did not do, with the reason. Empty section is fine.}}

## Out-of-Scope Findings
{{Existing code that violates project rules but is outside this feature's scope. One bullet per finding: what, where, which rule. Empty section is fine.}}

## Tests
{{What you ran and the result.}}
```
