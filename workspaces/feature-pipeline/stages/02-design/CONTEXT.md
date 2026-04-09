# Stage 02 - Design

Turn a feature idea into a spec detailed enough that an implementation agent can execute without follow-up questions. This is the most critical stage. Do it slowly.

This stage can be entered directly — a prior brief from stage 01 is not required. If the user describes what they want in conversation, capture it as a brief inline (see Phase 0 in the design protocol).

## Inputs

| Source | File/Location | Section/Scope | Why |
|--------|--------------|---------------|-----|
| Brief (if exists) | `../01-brief/output/<repo>/<slug>-brief.md` | Full file | What the user wants (optional — can be captured inline) |
| Brief template | `../01-brief/references/brief-template.md` | Full file | Structure for inline capture when no prior brief exists |
| Design protocol | `references/design-protocol.md` | Full file | Behavior, phases, scope philosophy, spec structure |
| Stack and rules detection | `/_core/stack-and-rules-detection.md` | Full file | How to identify the target repo's stack and project rules |
| Slug conventions | `../../shared/conventions.md` | "Slug Naming" and "When the Slug Changes" sections | How to rename the brief during phase 1 |
| Target repo | `git rev-parse --show-toplevel` of the cwd, or as set during target detection | The files the agent investigates | Source of truth for the code being changed |

## Process

1. If a brief already exists, read it. If not, run Phase 0 from the design protocol: capture the user's intent, write the brief, then continue.
2. Run stack and rules detection on the target repo. Read every project rule found before asking any question.
3. Phase 1 (Discovery): rename the slug to clean English if needed, investigate the codebase, ask the user PO-level questions. Full rules in `references/design-protocol.md`.
4. Wait for the user's explicit approval before writing the spec. If you are unsure whether they approved, ask "should I write the spec now?".
5. Phase 2 (Spec generation): write the spec to `output/<repo>/<new-slug>-spec.md` following the structure in the design protocol.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|------------|---------------|---------------|
| 3 | What the agent now understands, what gaps remain, the full scope landscape (everything connected to the problem) | Where to draw the scope line, then explicit approval to write the spec |

## Outputs

| Artifact | Location | Format |
|----------|----------|--------|
| Renamed brief | `../01-brief/output/<repo>/<new-slug>-brief.md` | Same content, new filename |
| Spec | `output/<repo>/<new-slug>-spec.md` | See "Spec Structure" in `references/design-protocol.md` |

## What This Stage Does NOT Do

- Implement anything
- Generate the spec without explicit user approval
- Hide findings to keep scope small (see "Scope Philosophy" in the protocol)
- Ask the user to find or read files that the agent could investigate itself
