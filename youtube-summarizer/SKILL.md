# YouTube Video Summarizer (Apify-powered with Language Preference)

Use this skill when the user wants to summarize a YouTube video, extract its transcript, and provide output in either original language or English translation (with special handling for Hindi). The output will be formatted in Markdown with separate Summary and Transcript sections.

## How to Use

When a user provides a YouTube URL, follow these steps:

### 1. Extract Video ID
- Accept YouTube URLs in these formats:
  - `https://www.youtube.com/watch?v=VIDEO_ID`
  - `https://youtu.be/VIDEO_ID`
  - `https://www.youtube.com/embed/VIDEO_ID`
- Extract the VIDEO_ID parameter/value

### 2. Fetch Transcript via Apify
- Use the Apify YouTube Transcript Scraper actor (if available in your account)
- Input: YouTube URL or video ID
- The actor returns the full transcript with timestamps and language detection
- If the actor is not available, fall back to YouTube's timedtext API (as backup)

### 3. Process Transcript
- Extract plain text from Apify result (remove timestamps if desired)
- Detect the language of the transcript from Apify metadata

### 3.5. Handle Language Preference (Special for Hindi)
- If the detected language is Hindi:
  - Ask the user: **"Would you like the summary and transcript translated to English, or kept in Hindi?"**
  - Wait for user response
  - If user chooses English: set translation flag to TRUE
  - If user chooses Hindi: set translation flag to FALSE (keep original Hindi)
- If language is not Hindi:
  - If language is English: set translation flag to FALSE (no translation needed)
  - If language is neither English nor Hindi: set translation flag to TRUE (translate to English)

### 4. Translate if Needed
- If translation flag is TRUE:
  - Translate the full transcript to English using Claude's translation
  - Note any translation uncertainties if applicable
- If translation flag is FALSE:
  - Keep transcript in original language (Hindi or other)

### 5. Generate Summary
- Create a concise summary focusing on:
  - Main topics covered
  - Key points or arguments
  - Conclusions or takeaways
  - Actionable insights (if applicable)
- Summary length should adapt to video duration:
  - < 5 minutes: 2-3 bullet points or 3-4 sentences
  - 5-15 minutes: 3-5 bullet points or short paragraph
  - > 15 minutes: 5-7 bullet points or multi-paragraph summary
- Use neutral, informative tone
- **Important**: Generate the summary in the same language as the final transcript (English if translated, Hindi if kept in Hindi, etc.)

### 6. Format Output
Present the results in this Markdown structure:

```markdown
## Summary

[Summary text here - can be bullet points or paragraph, in the selected language]

## Transcript

[Full transcript here - in the selected language (English if translated, Hindi if kept in Hindi, etc.)]
```

## Error Handling
- If Apify actor fails or unavailable: Inform user and suggest checking Apify account or try backup method
- If transcript unavailable: Inform user that captions may not be available for this video
- For videos exceeding context limits: Process transcript in chunks and note any truncation
- If translation quality seems poor: Mention that accuracy depends on source material clarity

## Notes
- Requires access to Apify YouTube Transcript Scraper actor in your Apify account
- Works best with videos having official captions
- Auto-generated captions may contain errors
- Translation quality depends on source material clarity
- For Hindi videos specifically, the user will be prompted to choose between English output or Hindi output
- For all other languages: non-English videos are translated to English by default (except English itself)
