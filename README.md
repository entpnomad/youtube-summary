🌐 [English](README.md) | [Español](README.es.md) | [Français](README.fr.md) | [Italiano](README.it.md) | [Português](README.pt.md) | [Deutsch](README.de.md)

# youtube-summary

A [Claude Code](https://claude.ai/code) slash command that summarizes YouTube videos using MCP transcript extraction and visual scene analysis.

## Why

YouTube is where the best ideas live — conference talks, founder interviews, deep dives on strategy. But I don't always have 40 minutes to watch a video just to pull out 3 key takeaways. This command gives me the substance in seconds. I read the summary, decide if it's worth the full watch, and move on.

For tutorials, presentations, and demos, the transcript alone misses half the story — what's shown on screen matters. This command captures both.

## What it does

Fetches the transcript and extracts key screenshots from a YouTube video, then produces a structured summary combining what was **said** and what was **shown**:

- **Core Thesis** — the central argument in one or two sentences
- **Key Points** — most important ideas, ranked by significance, with visual references where relevant
- **Visual Highlights** — key slides, code, diagrams, or demos shown on screen (skipped for talking-head videos)
- **Actionable Takeaways** — things you can apply from the content

## Requirements

- [Claude Code](https://claude.ai/code)
- A YouTube MCP server configured in Claude Code with `youtube_get_transcript` and `youtube_get_screenshots` tools
- `yt-dlp` and `ffmpeg` installed (`brew install yt-dlp ffmpeg`) — for screenshot extraction

## Install

```bash
cp summary.md ~/.claude/commands/summary.md
```

Or fetch directly:

```bash
curl -o ~/.claude/commands/summary.md \
  https://raw.githubusercontent.com/entpnomad/youtube-summary/main/summary.md
```

## Usage

```
/summary https://www.youtube.com/watch?v=<video_id>
```

## Examples

```
/summary https://www.youtube.com/watch?v=dQw4w9WgXcQ
```

```
/summary https://youtu.be/dQw4w9WgXcQ
```

## How it works

1. Fetches the timestamped transcript via the YouTube MCP server
2. Extracts screenshots at visual scene changes using ffmpeg scene detection (via `youtube_get_screenshots`)
3. Reads key screenshots to understand visual content
4. Combines spoken + visual content into a structured summary

## License

MIT
