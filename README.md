<p align="center"><a href="https://loop.sv-academy.org"><img src="https://raw.githubusercontent.com/sva-admin/claude-skills/main/assets/sv-academy-512.png" width="88" alt="Silicon Valley Academy"/></a></p>

# yt-pipeline

Full YouTube processing pipeline that fetches the transcript, summarizes it, extracts key insights, and saves both the raw transcript and a distilled note.

An original skill by Silicon Valley Academy.

## What it does

- Fetches the transcript with `yt-dlp`, then asks you for it rather than fabricating one if the fetch fails.
- Writes two files: the raw transcript, and a distilled wiki note with a TL;DR, timestamped key points, named frameworks, quotes, and open questions.
- Ends every note with content angles written to feed straight into a downstream content skill.
- Skips the distillation step for videos under about three minutes, pure entertainment, or when you just want the transcript.

## Install

Paste this into Claude Code:

```
Install the yt-pipeline skill from github.com/sva-admin/yt-pipeline
```

Or install it by hand: copy `SKILL.md` into `~/.claude/skills/yt-pipeline/SKILL.md`, then
restart Claude Code. The skill loads itself whenever a request matches its triggers.

## Use it

Just ask. The skill picks up phrasing like the triggers listed at the top of
`SKILL.md`, so a plain request in your own words is enough.

## Learn

Learn free at https://loop.sv-academy.org/tutorials

---

More skills: https://github.com/sva-admin/claude-skills

Silicon Valley Academy: https://sv-academy.org
