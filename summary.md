Use the YouTube MCP server to fetch the transcript (with timestamps) for this video:

$ARGUMENTS

Then check if the video has significant visual content (slides, code, diagrams, demos) by extracting screenshots:
- Use youtube_get_screenshots to capture key frames at scene changes
- Read a few of the extracted screenshots to understand what's shown on screen

Produce a structured summary combining what was **said** and what was **shown**:

**Core Thesis**
One or two sentences capturing the central argument or purpose of the video.

**Key Points**
Bullet list of the most important ideas, findings, or moments — in order of significance, not timestamp. Where relevant, note what was shown on screen (e.g., "demonstrated X in a live demo", "showed a slide comparing Y vs Z").

**Visual Highlights**
If the video contains slides, code, diagrams, or demos: summarize the key visual content that adds information beyond what was spoken. Reference timestamps. Skip this section if the video is purely talking-head with no meaningful visual content.

**Actionable Takeaways**
Concrete things a viewer could do, apply, or look into based on the content. Skip this section if the video has no actionable content (e.g. pure entertainment or news).

Keep the summary tight. Prioritize signal over completeness.
