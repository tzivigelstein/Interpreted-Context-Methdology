# Marketing Video — Task Routing

## Per-Run Inputs (collected at entry)

Before entering Stage 01, ask the user:

1. **Product**: what is being marketed? (one sentence + landing URL or short description)
2. **Format and length**: 15s social ad / 30s social ad / 60s landing video / 90s explainer / 3-5 min sales video / long-form VSL? Default: 60s landing video.
3. **Distribution channel**: where will it run? (landing page hero / Instagram Reels / TikTok / YouTube pre-roll / paid Meta ad / etc.) This affects pacing and aspect ratio.
4. **Output language**: which language for the script and on-screen text? Default: same language the user is asking in.
5. **Production approach**: screen recording + voiceover / live action / motion graphics / animation / hybrid? Default: ask if unclear.
6. **Existing assets**: do you have brand guidelines, logos, voiceover talent, footage? Default: assume nothing exists.

Save the answers as `video-meta.md` in `stages/01-avatar-positioning/output/` so every stage can read them.

## Stage Entry Points

| If the user says... | Enter |
|---|---|
| "I need a marketing video for [product]" | `stages/01-avatar-positioning/CONTEXT.md` |
| "Here's my avatar, build the offer" | `stages/02-offer-value-stack/CONTEXT.md` |
| "I need hooks for this offer" | `stages/03-hook-mechanism/CONTEXT.md` |
| "Write the script" | `stages/04-script/CONTEXT.md` |
| "Turn this script into a production package" | `stages/05-production-package/CONTEXT.md` |

## Pipeline

```
01-avatar-positioning → 02-offer-value-stack → 03-hook-mechanism → 04-script → 05-production-package
```

The pipeline is linear but every stage has a human checkpoint. Creative work needs steering between stages, not after the fact.
