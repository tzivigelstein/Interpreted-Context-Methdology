# Prioritization Criteria

Four factors for ranking borders. Score each border on each factor as low/medium/high. Do not invent numeric weights. They fake precision.

## Impact

What breaks if the assumption at this border is wrong?

- **High**: data loss, silent corruption, security breach, compliance violation
- **Medium**: wrong display to users, broken UI flows, lost messages
- **Low**: log noise, transient errors, minor display issues

Data loss > wrong display > log noise.

## Complexity

How many steps are in this border's flow? More steps means more places for assumptions to break.

- **High**: multi-step flow with branching, retries, or async coordination
- **Medium**: 2 to 4 steps with some conditional logic
- **Low**: single read or write, no branching

## Visibility

When the border breaks, how soon is it noticed?

- **High visibility (low priority)**: synchronous user-facing operation that errors immediately. The user sees it fail.
- **Medium visibility**: async operation with retries or alerting. Failures are surfaced eventually.
- **Low visibility (HIGH priority)**: background jobs, fire-and-forget writes, swallowed exceptions. Failures hide for weeks.

Counterintuitively, low visibility means high audit priority. The bug exists. You just have not noticed yet.

## Novelty

How recently was this code written or changed?

- **High novelty (high priority)**: new feature, recent refactor, fresh integration. Untested assumption surface.
- **Medium novelty**: changed in the last few months
- **Low novelty**: stable for a year or more, has weathered real production traffic

New code has more untested assumptions than mature code. Mature code's bugs have already been found.

## Composite Ranking

Compare borders pairwise. There is no formula. The four factors are inputs to your judgment, not values to multiply.

A typical "top of the list" border has:

- High impact (data loss potential)
- Medium-high complexity (multi-step)
- Low visibility (background or async)
- High novelty (recently changed)
