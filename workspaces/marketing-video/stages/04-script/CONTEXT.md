# Stage 04 — Script

Write the full script using Hormozi's 7-part VSL structure, adapted to the target length.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Hook + mechanism | `../03-hook-mechanism/output/<slug>-hook-mechanism.md` | `## Selected Hook`, `## Selected Mechanism` | Opens and frames the script |
| Offer | `../02-offer-value-stack/output/<slug>-offer.md` | `## Bonus Stack`, `## Guarantee`, `## Urgency` | The offer beat (Part 6 of the structure) |
| Positioning | `../01-avatar-positioning/output/<slug>-positioning.md` | `## Avatar`, `## Current Pain`, `## Dream Outcome` | The problem and promise beats |
| Run metadata | `../01-avatar-positioning/output/video-meta.md` | `format`, `length`, `language` | Drives length-aware compression and output language |
| Hormozi reference | `references/vsl-7-part-structure.md` | Full file | Structure to follow |
| Hormozi reference | `references/length-aware-rules.md` | Section matching the chosen length | What gets compressed or cut |

## Process

1. Read all inputs and references. Pay attention to the length section in `length-aware-rules.md`.
2. Draft the script following the 7 parts: Hook → Problem → Promise → Mechanism → Proof → Offer → CTA.
3. Adapt to length: shorter formats compress or cut beats per `length-aware-rules.md`. The hook and CTA never get cut.
4. Write in the language specified in `video-meta.md`. If unspecified, mirror the user's conversation language.
5. Mark on-screen text suggestions inline as `[ON-SCREEN: ...]` (used by Stage 05).
6. Run the audit.
7. Save.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 2 | The hook + first 2 beats only | Whether the tone and pacing feel right before drafting the rest |

## Audit

| Check | Pass Condition |
|---|---|
| Length match | Spoken script word count fits the target duration (≈150 words/min for clear delivery) |
| Hook in 3 seconds | The hook is deliverable in under 3 seconds when spoken aloud |
| One CTA | Exactly one call-to-action, repeated in the closing beat |
| Mechanism named | The selected mechanism appears by name in the script, not described generically |
| No filler | Every sentence either advances a beat or builds emotion. Cut anything else. |
| Output language matches | The script is in the language requested in `video-meta.md` |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Script | `output/<slug>-script.md` | Markdown with one section per beat: `## 1. Hook`, `## 2. Problem`, `## 3. Promise`, `## 4. Mechanism`, `## 5. Proof`, `## 6. Offer`, `## 7. CTA`. Each section shows the spoken line and any inline `[ON-SCREEN: ...]` markers. |
