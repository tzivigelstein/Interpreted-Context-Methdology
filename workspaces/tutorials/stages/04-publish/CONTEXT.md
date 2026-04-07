# Stage 04 — Publish

Format the tutorial for publication. Blog post for the web, description + chapters for video.

## Inputs

| Source | File/Location | Section/Scope | Why |
|---|---|---|---|
| Previous stage | `../03-script/output/<slug>-script.md` | Full file | The script to format |
| Run metadata | `../01-research/output/tutorial-meta.md` | `format` | What to produce |

## Process

1. Read the script and metadata.
2. If format includes blog post, generate:
   - Final markdown ready to paste into your project's blog/docs
   - SEO-friendly title (60 chars max)
   - Meta description (155 chars max)
   - Tags (3-5)
3. If format includes video, generate:
   - YouTube/video description (under 5000 chars)
   - Chapter markers with timestamps (placeholders if recording hasn't happened)
   - Suggested thumbnail text (under 6 words)
4. Save each as a separate file.
5. Do NOT actually publish. The human reviews and publishes manually.

## Outputs

| Artifact | Location | Format |
|---|---|---|
| Blog post | `output/<slug>-blog.md` | Markdown + frontmatter (title, description, tags) |
| Video description | `output/<slug>-video-description.md` | Plain text with chapter markers |
| Thumbnail text | `output/<slug>-thumbnail.md` | Single line |

Skip artifacts whose format isn't in metadata.
