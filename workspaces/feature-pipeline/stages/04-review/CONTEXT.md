# Stage 04 - Review

Audit the implementation against the spec, the project rules, and general quality. Produce a verdict and a debt report. Do not fix the code yourself.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Spec | `../02-design/output/<repo>/<slug>-spec.md` | Full file | Contract to verify against |
| Implementation summary | `../03-implement/output/<repo>/<slug>-implementation-summary.md` | Full file | Where to look, what was decided |
| Review protocol | `references/review-protocol.md` | Full file | Behavior, output structure for review and debt |
| Stack and rules detection | `../../shared/stack-and-rules-detection.md` | Full file | How to find the target repo's project rules |
| Target repo | `git diff --staged` or `git diff` if nothing is staged | The actual changes | Source of truth for what was done |

## Process

1. Read the spec to understand what was supposed to happen.
2. Read the implementation summary to know where to look and what was decided.
3. Run stack and rules detection. Read the project rules.
4. Run `git diff --staged` (or `git diff` if nothing is staged) on the target repo to get the changes.
5. Review the diff against (a) the spec, (b) the project rules, (c) general quality.
6. Investigate the surrounding code yourself if you need context. Do NOT ask the user to look at files.
7. Write the verdict to `output/<repo>/<slug>-review.md`.
8. Write any out-of-scope findings to `output/<repo>/<slug>-debt.md`. In-scope findings stay in the review. Out-of-scope findings go to debt. The two are separate documents for separate decisions.

## Audit

| Check | Pass Condition |
|-------|---------------|
| Spec coverage | Every task in the spec is implemented or explicitly listed as deferred in the implementation summary |
| Rules compliance | No project rule is violated by the new code |
| Cleanup | No dead imports, no stale tests, no orphan functions left behind |
| Tests | Tests for the new behavior exist; the full suite passes |
| Scope discipline | The diff does not contain refactors or changes the spec did not ask for |

If any check fails, the verdict is REQUEST CHANGES.

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Review verdict | `output/<repo>/<slug>-review.md` | See "Review Output" in `references/review-protocol.md` |
| Out-of-scope debt | `output/<repo>/<slug>-debt.md` | See "Debt Output" in `references/review-protocol.md` |

## What This Stage Does NOT Do

- Fix the code. You only review.
- Mix in-scope review findings with out-of-scope debt.
- Propose refactors beyond the feature scope in the review. Those go in the debt doc.
- Ask the user to look at files. You have the repo.
- Skip the debt doc when there is nothing to report. Write the empty version.
