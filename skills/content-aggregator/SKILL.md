---
name: content-aggregator
description: "Aggregates recent content from YouTube channels, blogs, Substacks, and X/Twitter accounts to create a visual content blueprint document. Use this skill whenever the user wants to research what others are posting, find content ideas, do competitive content analysis, check what's trending in their niche, scout content from creators they follow, or build a content calendar based on what's working. Triggers on phrases like aggregate content, content research, what are people posting, content ideas, content blueprint, scout content, content roundup, what's trending, or any request to monitor multiple content sources and compile findings into a report."
---

# Content Aggregator

You are a content research assistant. Your job is to read from `competitors.json` in the working directory, research all sources in parallel, capture data + visuals, and compile everything into a content blueprint the user can use to plan content across YouTube, newsletter, LinkedIn, and X.

## Architecture

- **Data source**: `competitors.json` — the single source of truth for all tracked sources (YouTube channels, Substacks, blogs, X/Twitter)
- **Data extraction**: WebFetch + WebSearch for scraping content and metadata
- **YouTube deep-dive**: `yt-dlp` for thumbnails, transcripts, and metadata
- **Visual capture**: Playwright for screenshots and PDF generation
- **X/Twitter**: Playwright to open Chrome, scroll the timeline 30 times, take screenshots at each batch
- **Parallelism**: Dedicated subagents per source category, all running simultaneously

## Step 1: Load competitors.json

Read `competitors.json` from the current working directory. If `competitors.json` is not in the working directory, you can find a starter template in this plugin's `references/competitors.json`. This file contains:
- `youtube_channels[]` — each with `videos_url` pointing to the /videos tab
- `substacks[]` — each with `profile_url`
- `blogs[]` — each with source URLs
- `x_twitter[]` — with `url`, `scroll_count`, and `scan_approach`
- Schema examples for each type (`youtube_video_schema`, `substack_post_schema`, `blog_post_schema`, `x_twitter_schema`)

If `competitors.json` doesn't exist, ask the user for their sources and create it.

## Step 2: Create Workspace

Create a timestamped workspace directory:
```
content-runs/YYYY-MM-DD/
├── screenshots/
│   ├── youtube/{channel_id}/
│   ├── substacks/{substack_id}/
│   ├── blogs/{blog_id}/
│   └── x/
├── thumbnails/
├── transcripts/
├── raw/
└── output/
```

## Step 3: Spawn Parallel Subagents

Launch subagents simultaneously — one per category. Each subagent writes its results into the workspace and updates the relevant section of `competitors.json`.

---

### Subagent 1: YouTube Research

For each channel in `youtube_channels[]`:

**A) Metadata via yt-dlp**
```bash
# Get latest 5 videos metadata as JSON
yt-dlp --flat-playlist --playlist-end 5 --dump-json "{videos_url}" > raw/youtube_{id}_playlist.jsonl

# For each video found, get full metadata + thumbnail + transcript
yt-dlp --write-thumbnail --write-auto-sub --sub-lang en --skip-download \
  --write-info-json -o "thumbnails/{channel_id}/%(id)s" "{video_url}"

# Get transcript text
yt-dlp --write-auto-sub --sub-lang en --skip-download --sub-format vtt \
  -o "transcripts/{channel_id}_%(id)s" "{video_url}"
```

**B) For each video, extract:**
- `video_id`, `title`, `url`, `published_date`, `duration`
- `thumbnail_url` + download to `thumbnails/{channel_id}/{video_id}_thumb.jpg`
- `views`, `likes`, `comments_count` from yt-dlp JSON
- `timestamps` — parse from video description (lines matching `0:00 - Label` or `00:00 Label` patterns)
- `transcript_summary` — read the .vtt file, clean it, summarize the content
- `transcript_file` — path to saved transcript
- `hook` — first 1-2 sentences of description
- `tags` — from yt-dlp metadata

**C) Screenshots via Playwright**
- Navigate to each channel's `/videos` page
- Full-page screenshot → `screenshots/youtube/{channel_id}_videos_page.png`
- Screenshot individual video cards for top 2-3 videos

**D) Analysis per video**
- `content_format`: tutorial, listicle, reaction, deep-dive, news, vlog, etc.
- `estimated_performance`: high/medium/low relative to channel's typical views
- `why_it_works`: brief analysis of title, thumbnail, topic appeal
- `content_ideas_inspired`: list of content angles this video suggests

**E) Update competitors.json**
Write results into each channel's `recent_videos[]` array following `youtube_video_schema`. Set `last_scanned` to current timestamp.

---

### Subagent 2: Substack Research

For each substack in `substacks[]`:

**A) Data extraction via WebFetch**
- Fetch the profile URL
- Extract recent posts: title, URL, publish date, preview text
- For each post, WebFetch the full post URL to get content text (first 500 words)

**B) Engagement via WebSearch**
- Search for `"{post_title}" site:substack.com` to find like counts, comments, restacks
- Search for social shares of the post

**C) Screenshots via Playwright**
- Full-page screenshot of the Substack profile page
- Screenshot of each recent post's header/hero area

**D) Content scraping**
- Save full post content text (or first 500 words) to `content_text`
- Generate `content_summary` — a 2-3 sentence summary

**E) Analysis per post**
- `content_format`: newsletter, essay, tutorial, listicle, interview, etc.
- `why_it_works`: what makes this post engaging
- `content_ideas_inspired`: angles for the user's own content

**F) Update competitors.json**
Write results into each substack's `recent_posts[]` array following `substack_post_schema`. Set `last_scanned`.

---

### Subagent 3: Blog Research

For each blog in `blogs[]`:

**A) Data extraction via WebFetch**
- Fetch the blog URL, extract recent posts with titles, URLs, dates, authors
- WebFetch each post URL for content text

**B) Screenshots via Playwright**
- Full-page screenshot of blog homepage
- Screenshot of each recent post

**C) Content scraping + analysis**
- Same pattern as Substack: content_text, content_summary, engagement, analysis

**D) Update competitors.json**
Write results into `blogs[]` following `blog_post_schema`.

---

### Subagent 4: X/Twitter Timeline Research

This is a scroll-and-capture approach using Playwright on the user's Chrome profile:

**A) Write and run a Playwright script that:**
```javascript
const { chromium } = require('playwright');

(async () => {
  // Connect to user's Chrome or launch with their profile for auth
  const browser = await chromium.launch({
    channel: 'chrome',
    headless: false  // Need visible browser for auth state
  });
  const context = await browser.newContext({
    viewport: { width: 1280, height: 900 }
  });
  const page = await context.newPage();
  await page.goto('https://x.com/', { waitUntil: 'networkidle', timeout: 30000 });

  // Scroll loop — 30 iterations
  const scrollCount = 30;
  for (let i = 0; i < scrollCount; i++) {
    // Screenshot current viewport
    await page.screenshot({
      path: `screenshots/x/scroll_batch_${String(i+1).padStart(2,'0')}.png`,
      fullPage: false
    });

    // Extract visible post data from DOM
    const posts = await page.evaluate(() => {
      // Extract tweet elements, text, engagement counts, author info
      // Return structured data
    });

    // Save batch data
    // Scroll down
    await page.evaluate(() => window.scrollBy(0, window.innerHeight));
    await page.waitForTimeout(2000); // Wait for new content to load
  }

  await browser.close();
})();
```

**B) Post-processing**
- Read all scroll batch screenshots
- Parse extracted post data from each batch
- Deduplicate posts (same post can appear across scroll batches)
- Identify notable high-engagement posts (likes > 1000, views > 50K, lots of retweets)
- Take individual screenshots of standout posts if possible

**C) Analysis**
- What topics are trending in the timeline
- Which post formats are getting traction (threads, images, short takes, polls)
- Engagement patterns — what ratio of likes-to-views suggests virality

**D) Update competitors.json**
Write results into `x_twitter[0].scans[]` following `x_twitter_schema`.

---

## Step 4: Merge & Analyze

Once all subagents complete:

1. Read the updated `competitors.json` — it now has all scraped data
2. Create `content-runs/YYYY-MM-DD/raw_data.json` as a snapshot of all findings
3. Cross-source analysis:
   - **Top performers**: Posts/videos with unusually high engagement
   - **Trending topics**: Common themes across YouTube + Substack + X
   - **Content gaps**: Topics covered by some sources but not others
   - **Format patterns**: What content formats are getting traction
   - **Title/hook patterns**: What language, structure, and hooks are working

## Step 5: Generate the Blueprint Document

Write a Node.js script that builds a styled HTML report and converts it to PDF via Playwright.

The script should:
1. Read `raw_data.json` and all screenshots/thumbnails
2. Convert images to base64 for embedding
3. Generate rich HTML with this structure:

```
CONTENT BLUEPRINT — {date}

## Executive Summary
- Sources scanned: X channels, Y substacks, Z blogs, X timeline
- Posts/videos analyzed: N
- Top trending topics: [list with brief context]
- Highest engagement content: [title] by [creator] — [metrics]

## What's Working Right Now
For each trending topic/theme:
- The posts/videos that exemplify it (with embedded screenshots/thumbnails)
- Engagement numbers side-by-side
- Why it's resonating (analysis)

## YouTube Deep Dive
For each channel:
- Channel screenshot
- Recent videos with thumbnails, view counts, like counts
- Transcript summaries — what they covered
- Timestamp breakdowns — how they structure content
- Title + thumbnail analysis

## Substack & Newsletter Insights
For each substack:
- Profile screenshot
- Recent posts with engagement
- Content summaries
- What angles they're taking

## X/Twitter Pulse
- Timeline screenshots showing what's trending
- Top posts by engagement
- Format analysis (threads vs single tweets vs images)

## Content Ideas by Platform

### YouTube Video Ideas
1. [Idea] — Inspired by [source]. Why: [reasoning]. Suggested angle: [specifics]
   [embedded thumbnail/screenshot of inspiring content]

### Newsletter Ideas
1. [Idea] — ...

### LinkedIn Post Ideas
1. [Idea] — ...

### X/Twitter Post Ideas
1. [Idea] — ...

## Source-by-Source Breakdown
For each source:
- Page screenshot
- Recent content with metrics
- What they're doing well
- Notable patterns
```

4. Convert HTML to PDF:
```javascript
const { chromium } = require('playwright');
const page = await browser.newPage();
await page.setContent(html, { waitUntil: 'networkidle' });
await page.pdf({
  path: 'output/content-blueprint.pdf',
  format: 'A4',
  printBackground: true,
  margin: { top: '1cm', bottom: '1cm', left: '1cm', right: '1cm' }
});
```

## Step 6: Save Outputs

Final outputs in `content-runs/YYYY-MM-DD/`:
- `output/content-blueprint.pdf` — Visual blueprint document
- `output/content-blueprint.html` — HTML version (viewable in browser)
- `raw_data.json` — Snapshot of all scraped data
- `screenshots/` — All captured screenshots organized by category
- `thumbnails/` — Downloaded YouTube thumbnails
- `transcripts/` — YouTube video transcripts

Also update `competitors.json` with `aggregation_runs[]` entry:
```json
{
  "run_date": "2026-03-23",
  "workspace": "content-runs/2026-03-23",
  "sources_scanned": 19,
  "posts_found": 85,
  "blueprint_pdf": "content-runs/2026-03-23/output/content-blueprint.pdf"
}
```

Tell the user where the files are and open the HTML blueprint in their browser.

## Error Handling

- If yt-dlp fails for a video, fall back to WebFetch on the YouTube page for basic metadata
- If WebFetch fails for a URL, fall back to WebSearch for that source's recent content
- If Playwright can't connect to Chrome for X/Twitter (auth issues), note the failure and suggest the user log into X in the Playwright browser window
- If a source URL fails, log the error and continue with other sources
- If no posts from the last 24h exist, capture the most recent 3-5 posts regardless
- If engagement metrics aren't visible, capture the post with a note
- If PDF generation fails, fall back to the HTML version
- If yt-dlp isn't installed, run `pip install yt-dlp` or `brew install yt-dlp`
- If Playwright isn't installed, run `npx playwright install chromium`

## Adding New Sources

The user can add sources anytime by providing URLs. Update `competitors.json` directly:
- New YouTube channel → add to `youtube_channels[]` with `videos_url` pointing to /videos
- New Substack → add to `substacks[]` with `profile_url`
- New blog → add to `blogs[]`
- The skill reads `competitors.json` fresh each run, so changes take effect immediately

## Pipeline Context
This skill is part of the contentwise plugin pipeline:
1. `/contentwise:content-aggregator` — Research what competitors are posting
2. `/contentwise:idea-validator` — Validate a trending idea
3. `/contentwise:hook-scorer` — Score the idea (0-62.5)
4. `/contentwise:pillar-matcher` — Pick content pillar + titles
5. `/contentwise:virality-scorer` — Score the packaging (0-57.5)
6. `/contentwise:newsletter-writer` — Write the 10-section draft
7. `/contentwise:visual-asset-planner` — Generate shot list
8. `/contentwise:newsletter-reviewer` — Final quality gate
9. `/contentwise:thumbnail-creator` — Generate hero thumbnail
