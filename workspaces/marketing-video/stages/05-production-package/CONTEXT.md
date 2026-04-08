# Stage 05 — Production Package

Turn the script into everything an editor or filmmaker needs to actually produce the video. No more decisions left for production day.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../04-script/output/<slug>-script.md` | Full file | The script to package |
| Run metadata | `../01-avatar-positioning/output/video-meta.md` | `format`, `channel`, `production approach`, `language` | Drives pacing, aspect ratio, asset list |
| Hormozi reference | `references/pacing-rules.md` | Section matching the chosen length | Cut frequency and rhythm |
| Hormozi reference | `references/b-roll-strategy.md` | Full file | What to show under each spoken line |
| Hormozi reference | `references/cta-design.md` | Full file | How to land the CTA visually |
| Bundled skill | `../../skills/frontend-design/SKILL.md` | Index, then load relevant rules | On-screen text design and visual polish |

## Process

1. Read the script, metadata, and all references. Load `frontend-design/SKILL.md` for on-screen text guidelines.
2. Break the script into shots. One shot per spoken sentence (or one per visual beat for shorter forms).
3. For each shot, fill in:
   - Spoken line (from script)
   - On-screen text (from inline `[ON-SCREEN: ...]` markers + your additions)
   - Visual / b-roll (specific: "screen recording of dashboard with cursor clicking the primary button" not "app demo")
   - Camera/transition note (if relevant)
   - Approximate duration in seconds
4. Apply pacing rules from `pacing-rules.md` based on the chosen length.
5. Apply CTA design from `cta-design.md` to the closing shots: visible button, repeated verbal, end card.
6. Compile the deliverables (see Outputs below).
7. Run the audit.
8. Save.

## Checkpoints

| After Step | Agent Presents | Human Decides |
|---|---|---|
| 3 | The first 3 shots fully filled in | Whether the level of specificity is right before doing all of them |

## Audit

| Check | Pass Condition |
|---|---|
| Total duration matches | Sum of shot durations matches the target length within ±10% |
| Every line has a visual | No spoken line lacks an associated on-screen visual or b-roll |
| CTA is unmissable | The CTA appears verbally, on-screen, and as an end card |
| Pacing within range | Average cut frequency matches `pacing-rules.md` for the chosen length |
| Aspect ratio specified | Vertical (9:16) for Reels/TikTok, square (1:1) for feed, horizontal (16:9) for landing/YouTube |

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Shot list | `output/<slug>-shot-list.md` | Markdown table: shot # / spoken line / on-screen text / visual / camera note / duration |
| Voiceover script | `output/<slug>-voiceover.md` | Plain text optimized for reading aloud (no markdown formatting, line breaks at natural pauses) |
| On-screen text list | `output/<slug>-on-screen-text.md` | Numbered list of every text overlay with timing |
| Production brief | `output/<slug>-production-brief.md` | One-page summary: format, aspect ratio, total duration, music brief, asset checklist |
