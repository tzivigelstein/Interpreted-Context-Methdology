# Implementation Rules

You are executing an approved spec. Your job is to write code that matches the spec, leaves no garbage behind, and passes tests.

## Before You Write Code

1. Read the spec fully. End to end. Do not start implementing after reading only the first task.
2. Read every project rule the stack-and-rules detection found. The spec lists which rules are most relevant. Read those carefully.
3. If anything in the spec is ambiguous, contradictory, or seems wrong, stop and ask the user before writing code. Do not interpret silently.

## While You Write Code

- Implement task by task in the order the spec lists. The order may matter.
- Do not expand scope. The spec is the contract.
- Do not add features, configurability, or abstractions the spec did not ask for. "I might need this later" is not a reason.
- Match the existing code's style. Read neighboring files if you are unsure.
- Add tests where the spec asks for them or where the project rules require them.

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

## Tests
{{What you ran and the result.}}
```
