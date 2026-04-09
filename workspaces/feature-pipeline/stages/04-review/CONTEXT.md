# Stage 04 - Review

Audit the implementation against the spec, the project rules, and general quality. Produce a verdict and a debt report. Do not fix the code yourself.

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Spec | `../02-design/output/<repo>/<slug>-spec.md` | Full file | Contract to verify against |
| Implementation summary | `../03-implement/output/<repo>/<slug>-implementation-summary.md` | Full file | Branch name, files touched, decisions made |
| Review protocol | `references/review-protocol.md` | Full file | Behavior, output structure for review, debt, and PR creation |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Full file | How to find the target repo's project rules |
| Target repo | `git diff <base>...<feature-branch>` using branch from implementation summary | The actual changes | Source of truth for what was done |

## Process

1. Read the spec to understand what was supposed to happen.
2. Read the implementation summary to get the branch name, files touched, and decisions made.
3. Run stack and rules detection. Read every project rule found — including layer-scoped rules (domain, infrastructure, etc.). Review needs the full picture to catch violations across all layers.
4. Get the diff using `git diff <base-branch>...feat/<slug>` (branch name from implementation summary). Fallback: `git diff --staged`, then `git diff`.
5. Review the diff against (a) the spec, (b) the project rules, (c) general quality.
6. Investigate the surrounding code yourself if you need context. Do NOT ask the user to look at files.
7. Write the verdict to `output/<repo>/<slug>-review.md`.
8. Write any out-of-scope findings to `output/<repo>/<slug>-debt.md`. In-scope findings stay in the review. Out-of-scope findings go to debt. The two are separate documents for separate decisions.
9. If the verdict is APPROVE or APPROVE WITH NOTES, offer to create a PR (see "Post-Approval: PR Creation" in the review protocol). If the verdict is REQUEST CHANGES, tell the user which stage to re-enter (03 for implementation fixes, 02 for spec amendments).

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
