# Stage 03 — Hook and Mechanism

Generate hooks (the first 3 seconds) and a unique mechanism (the named "secret sauce" that differentiates the product). Pick winners with the human.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../02-offer-value-stack/output/<slug>-offer.md` | Full file | What we're hooking them on |
| Positioning | `../01-avatar-positioning/output/<slug>-positioning.md` | `## Avatar`, `## Current Pain` | Whose attention we're grabbing |
| Run metadata | `../01-avatar-positioning/output/video-meta.md` | `format`, `channel` | Hook style depends on platform |
| Hormozi reference | `references/hook-formulas.md` | Full file | 10 hook patterns to draw from |
| Hormozi reference | `references/unique-mechanism.md` | Full file | How to find and name the mechanism |

## Process

1. Read offer, positioning, metadata, and both references.
2. Generate **5-10 hook variations** drawing from at least 5 different patterns in `hook-formulas.md`. For each hook, label which pattern it uses and which audience pain/desire it activates.
3. For each hook, predict whether it works for the chosen format/channel from metadata. Short-form (Reels, TikTok) needs harder hooks than landing videos.
4. Apply `unique-mechanism.md` to find the product's mechanism: what does it do differently? Name it in 3-5 words. Memorable, ideally with alliteration or an acronym.
5. Run the audit.
6. Save.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 3 | The 5-10 hooks ranked by predicted strength | Pick 1 winner + 1 backup |
| 4 | 2-3 candidate mechanism names | Pick the one to use in the script |

## Audit

| Check | Pass Condition |
|---|---|
| Pattern diversity | At least 5 distinct patterns from `hook-formulas.md` represented |
| Avatar-specific | Every hook references something specific from the avatar's world, not generic |
| Mechanism is named | The mechanism has a memorable 3-5 word name, not a description |
| Mechanism is testable | The mechanism can be summarized in one sentence by a stranger |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Hooks and mechanism | `output/<slug>-hook-mechanism.md` | Markdown with `## Hook Variations` (table: hook / pattern / target emotion / format fit), `## Selected Hook`, `## Mechanism Candidates`, `## Selected Mechanism` (name + one-line definition) |
