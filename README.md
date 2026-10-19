# YouTube Summarizer Skill for Claude

A Claude skill that summarizes YouTube videos, provides transcripts in user-selected language (with special Hindi handling), and formats output in Markdown with Summary and Transcript sections.

## Features
- ✅ YouTube URL parsing (watch, youtu.be, embed formats)
- ✅ Apify-powered transcript scraping (with YouTube API fallback)
- ✅ **Hindi language preference**: User chooses English/Hindi output for Hindi videos
- ✅ Automatic language detection and translation (English default for non-Hindi)
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

**For Hindi videos**: Claude will ask: *"Would you like the summary and transcript translated to English, or kept in Hindi?"*

Claude will return:
```markdown
## Summary

[Concise summary in selected language]

## Transcript

[Full transcript in selected language]
```

## Requirements
- For Apify-powered scraping: Access to the [Apify YouTube Transcript Scraper](https://apify.com/) actor in your Apify account
- Without Apify: Falls back to YouTube's native transcript API (works for most videos with captions)

## Language Handling
- **English videos**: Output in English (no translation needed)
- **Hindi videos**: User chooses between English or Hindi output
- **Other languages** (Spanish, French, etc.): Output in English by default

## License
[Choose your preferred license - see below]

## Contributing
Feel free to submit issues or pull requests!
