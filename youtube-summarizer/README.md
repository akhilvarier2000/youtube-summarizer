# YouTube Summarizer Skill for Claude

A Claude skill that summarizes YouTube videos, provides English transcripts, and formats output in Markdown with Summary and Transcript sections.

## Features
- ✅ YouTube URL parsing (watch, youtu.be, embed formats)
- ✅ Apify-powered transcript scraping (with YouTube API fallback)
- ✅ Automatic language detection and English translation
- ✅ Adaptive-length summarization based on video duration
- ✅ Clean Markdown output with `## Summary` and `## Transcript` sections
- ✅ Error handling for unavailable captions or API issues

## Installation

### Option 1: Manual Installation
1. Clone or download this repository
2. Place the `youtube-summarizer` directory in your Claude skills folder:
   - macOS: `~/Library/Application Support/Claude-3p/local-agent-mode-sessions/*/skills/`
   - Or use Claude's skill management interface

### Option 2: Via Claude (if published as a plugin)
Use Claude's skill discovery to find and install this skill.

## Usage
Once installed, simply ask Claude to summarize a YouTube video:
> "Summarize this YouTube video: https://www.youtube.com/watch?v=VIDEO_ID"

Claude will automatically apply this skill and return:
```markdown
## Summary

[Concise summary of the video]

## Transcript

[Full English transcript]
```

## Requirements
- For Apify-powered scraping: Access to the [Apify YouTube Transcript Scraper](https://apify.com/) actor in your Apify account
- Without Apify: Falls back to YouTube's native transcript API (works for most videos with captions)

## License
[Choose your preferred license - see Step 4 below]

## Contributing
Feel free to submit issues or pull requests!