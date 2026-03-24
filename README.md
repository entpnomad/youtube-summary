# youtube-summary

A [Claude Code](https://claude.ai/code) slash command that summarizes YouTube videos using MCP transcript extraction.

## What it does

Fetches the transcript for a YouTube video and produces a structured summary:

- **Core Thesis** — the central argument in one or two sentences
- **Key Points** — most important ideas, ranked by significance
- **Actionable Takeaways** — things you can apply from the content

## Requirements

- [Claude Code](https://claude.ai/code)
- A YouTube MCP server configured in Claude Code, e.g. [youtube-mcp-server](https://github.com/nicholasgriffintn/youtube-mcp-server)

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

## License

MIT
