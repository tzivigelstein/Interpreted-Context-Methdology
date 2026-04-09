# Why This Audit Works

Read this before any audit work. It is the mental frame for the whole pipeline.

## Why Standard Reviews Fail

A standard review reads code and checks: "is this logic correct?" The answer is almost always yes. The code does what it says it does. The bugs that reach production are almost never in what the code does, but in what the code **assumes**.

These assumptions are invisible to the reviewer because the code is internally consistent. The reviewer validates the code against itself and concludes it is correct.

## What to Look For Instead

Do not read code looking for errors. Read code looking for **borders**, every point where the system touches something external. Then question the assumptions at each border.

A border is anywhere the system trusts something it does not control:

- An external API trusts that its caller sends the right shape
- The code trusts that the API returns the documented shape
- Both trust each other to handle errors a specific way
- Both trust that nothing else is touching the same data

Every trust is an assumption. Every assumption can be wrong.

## The Four Categories of Broken Assumptions

Bugs at borders fall into one of four patterns. Stage 04 has the full list with examples; in short:

1. **Source of truth confusion**: we write data assuming we know the complete state, but the external system has fields or actors we do not model.
2. **Input format assumptions**: we assume inputs have a structure that real-world data violates.
3. **Operation order assumptions**: we assume steps happen in a sequence that users, concurrency, or partial failures can break.
4. **Data completeness assumptions**: we assume our queries return everything that matters, but limits, sync gaps, and missing entries cause silent truncation.

Each category has a different question to ask. Each question generates hypotheses. Hypotheses get validated cheaply. Confirmed hypotheses become findings.

## Why the Pipeline Has Five Stages

The discipline matters more than the steps:

- **01 Identify**: be exhaustive before judging. Premature pruning hides bugs.
- **02 Prioritize**: spend expensive effort on the borders most likely to hide real bugs.
- **03 Trace**: read flows end-to-end, not function by function. Bugs live in the gaps.
- **04 Question**: be paranoid. Generate hypotheses freely.
- **05 Validate**: be cheap. Confirm before reporting. Reject the rest with a note.

Skipping or merging stages collapses the discipline. The result is a normal review with an "adversarial" label.
