---
name: yt-pipeline
description: Full YouTube video processing pipeline. Fetches transcript, summarizes, extracts key insights, and saves both raw transcript and distilled wiki note to the user's notes directory. Trigger on "yt-pipeline", "process this YouTube video", "summarize this video", "ingest this video", "yt:", or any YouTube URL the user wants ingested into their knowledge base.
---

# YouTube Pipeline

## Objective

Turn a YouTube URL (or video ID, optionally with a focus angle like "extract the framework") into two artifacts: the raw transcript, and a distilled wiki note good enough that the user never needs to watch the video, plus content angles that feed downstream content skills.

Paths below are relative to the working directory. If the user keeps a notes folder or an Obsidian-style vault, write there instead and tell them where the files landed.

## Getting the transcript

Use whatever works. `yt-dlp --write-auto-sub --skip-download --sub-format vtt --sub-lang en <url>` is usually fastest; fetch the page for title/channel/duration metadata. If automated fetching fails, ask the user for the transcript. Never fabricate one.

## Deliverables (hard contracts)

**Raw transcript**: `notes/raw/YYYY-MM-DD-yt-<slug>.md`
- Frontmatter: `source: <url>`, `ingested: <date>`, `type: transcript`, `title:`, `channel:`, `duration:`
- Body: full transcript, timestamps if available.

**Wiki note**: `notes/wiki/<slug>.md`
- Frontmatter: `title`, `source`, `created`, `tags`
- Must cover: a tight TL;DR; key points with `[mm:ss]` timestamps where available; any named frameworks/models with their definitions; quotable lines; open questions worth following up; and a `## Related` section of wikilinks to existing wiki notes (search the notes directory before writing it).
- Ends with `## Content Angles`: a handful of hooks ordered by punch, written so they can feed directly into a downstream content skill such as `outlines` (github.com/sva-admin/outlines) or `yt-hooks` (github.com/sva-admin/yt-hooks).

**Slug**: lowercase, spaces → `-`, punctuation stripped, ≤ 60 chars; drop "the"/"a" only if length-constrained.

## Done looks like

Both files exist at the paths above, and the user got: a clickable link to the wiki note, a ~3-sentence TL;DR, and the top content angle as a one-liner.

Verify by re-reading the wiki note: could someone act on it without watching the video? Do the timestamps point at the claims they annotate? Do the wikilinks resolve to notes that actually exist?

## When NOT to distill

Video under ~3 minutes, pure entertainment, or user says "just transcript" → save raw only, skip the wiki note.

## Output style

Terse. The wiki note is the deliverable: link to it, don't paste it into chat.
