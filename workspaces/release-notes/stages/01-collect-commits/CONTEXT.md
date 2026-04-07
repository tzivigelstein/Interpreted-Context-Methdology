# Stage 01 — Collect Commits

Pull the raw commit list from git for the release range. No interpretation, just collection.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| User input | Conversation | `release-meta.md` from CONTEXT.md questions | Range, audience, channels |
| Git history | `git log` | Range from latest tag to HEAD (or user-specified) | Source material |

## Process

1. Read `release-meta.md` (or ask the user if it's missing).
2. Run `git log --oneline --no-merges <range>` to get the commit list.
3. Run `git log --stat <range>` to get touched files per commit (helps Stage 02 categorize).
4. Save both as a single markdown file in `output/`.
5. Do NOT categorize, summarize, or interpret. Stage 02 does that.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Raw commit list | `output/<release-slug>-commits.md` | Markdown with two sections: `## Oneline` and `## With Files` |
| Run metadata | `output/release-meta.md` | Key-value markdown (range, audience, channels) |

The release-slug is `vX.Y.Z` if a version was specified, otherwise the date `YYYY-MM-DD`.
