# Stage 04 — Publish

Format the changelog for each target channel. One artifact per channel.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../03-draft/output/<slug>-changelog.md` | Full file | The draft to format |
| Run metadata | `../01-collect-commits/output/release-meta.md` | `channels` field | Which channels to format for |
| Channel specs | `references/channel-specs.md` | Per-channel section | Length/format constraints |

## Process

1. Read the draft and the channel list.
2. For each target channel, produce a formatted version:
   - **Discord**: under 2000 chars per message, use markdown bold/italics, emoji for section markers if your project's voice allows.
   - **Telegram**: under 4096 chars, basic markdown, no nested formatting.
   - **Web post**: full markdown, no length limit, may include images.
3. Save each as a separate file.
4. Do NOT actually post. The human reviews and posts manually.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Discord version | `output/<slug>-discord.md` | Plain text + Discord-flavored markdown |
| Telegram version | `output/<slug>-telegram.md` | Plain text + Telegram markdown |
| Web post version | `output/<slug>-web.md` | Full markdown |

If a channel is not in `release-meta.md`, skip it. If a channel exists in metadata but no spec exists in `references/channel-specs.md`, ask the user before generating.
