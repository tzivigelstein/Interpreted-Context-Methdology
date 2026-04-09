# Validate and Report Protocol

How to confirm a hypothesis cheaply, and how to write the resulting finding.

## Cheap Validation Methods

For each hypothesis, try these in order. Stop at the cheapest one that gives a confident answer.

### Method 1: Read the exact code path

Trace the hypothesis's claim through the code. If the assumption is broken, you should be able to point to the line where it breaks.

- **Pass:** you can cite file:line and explain why the code matches the broken assumption.
- **Fail:** the code actually handles the case the hypothesis worried about. Reject the hypothesis with a one-line note.

### Method 2: Write a test that fails

If reading is ambiguous, write a small test that exercises the suspected case. If the test fails (or produces wrong output), the hypothesis is confirmed. If it passes, reject the hypothesis.

- **Pass:** the test demonstrates the bug. Capture the test in the finding.
- **Fail:** the system handles the case correctly. Reject.

### Method 3: Reproduce locally

If a test cannot easily exercise the case (e.g., requires external service state), reproduce it in a local environment with a minimal change. Then capture the reproduction steps.

Do NOT propose a fix until you have validated. Hypotheses are cheap. Reports of unvalidated bugs are noise.

## Finding Format

Each confirmed finding becomes a section in `output/<repo>/<audit-slug>-findings.md`:

```
## [SEV] - [One-line title]

**What the code assumes:** [the broken assumption, in one or two sentences]

**What reality is:** [the actual behavior of the external system, user, or data]

**Impact:** [what breaks in production]

**Where:** [file:line, possibly multiple]

**How it was confirmed:** [read | test | reproduce] - [one-line note]

**Proposed fix:** [concrete suggestion. Not vague. Cite the file and the change.]
```

Severity tags:

- **CRITICAL**: data loss, security, compliance
- **HIGH**: incorrect behavior visible to users, lost messages
- **MEDIUM**: wrong reporting, minor data inconsistency
- **LOW**: noise, edge cases unlikely to be hit

## Rejected Hypotheses

For hypotheses you considered and rejected, add a short appendix at the end of the findings file:

```
## Rejected Hypotheses

- [Hypothesis]: rejected because [one-line reason].
```

This shows the user you did not just ignore the hypothesis. It also creates an audit trail in case they disagree with the rejection.

## Empty Findings

If you found zero confirmed bugs after validating all hypotheses, write the file anyway with the heading and a single line "No confirmed findings." plus the rejected hypotheses appendix. The empty case is also a signal. It tells the user you ran the audit and the borders are healthier than expected.
