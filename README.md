# ContentWise

**A Claude Code plugin with 9 skills that take your team from "I saw something trending" to "published newsletter" — with scoring, brand alignment, and quality gates at every step.**

Brand: *We reverse engineer trending AI products and rebuild what actually matters.*

---

## Installation

### Option A: Direct Install (Simplest)

In Claude Code, run:

```
/plugin install github:harshit/contentwise
```

All 9 skills become available immediately.

### Option B: Custom Team Marketplace

Create a separate marketplace repo with `.claude-plugin/marketplace.json`:

```json
{
  "name": "content-team-marketplace",
  "description": "Content team's Claude Code plugins",
  "owner": { "name": "Content Team" },
  "plugins": [
    {
      "name": "contentwise",
      "description": "9-skill newsletter pipeline",
      "source": {
        "source": "github",
        "repo": "harshit/contentwise"
      }
    }
  ]
}
```

Team members add the marketplace to `~/.claude/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "content-team-marketplace": {
      "source": { "source": "github", "repo": "harshit/content-team-marketplace" }
    }
  }
}
```

Then install: `/plugin install contentwise@content-team-marketplace`

### Option C: Official Claude Code Marketplace

1. Push the plugin repo to a public GitHub repo
2. Submit at **https://clau.de/plugin-directory-submission**
3. After acceptance, anyone can install via `/plugin install contentwise`

### Prerequisites

- **Thumbnail generation**: The `/contentwise:thumbnail-creator` skill requires the [nanobanana MCP server](https://github.com/nanobanana) configured in your Claude Code setup.
- **Content aggregation**: The `/contentwise:content-aggregator` skill reads `competitors.json` from your working directory. A starter template is included in `references/competitors.json` — copy it to your project to get started.

---

## The Pipeline

```
Screenshot / Link
       |
  /contentwise:idea-validator       ->  Is this worth pursuing?
       |
  /contentwise:hook-scorer          ->  How strong is the idea? (score /62.5)
       |
  /contentwise:pillar-matcher       ->  What format + title?
       |
  /contentwise:virality-scorer      ->  Will the packaging spread? (score /57.5)
       |
  /contentwise:newsletter-writer    ->  Full 10-section draft
       |
  /contentwise:visual-asset-planner ->  Shot list for every image
       |
  /contentwise:newsletter-reviewer  ->  PASS or REVISE with feedback
```

**Bonus skills:**
- `/contentwise:content-aggregator` — Research what competitors are posting across YouTube, Substack, blogs, and X
- `/contentwise:thumbnail-creator` — Generate a 16:9 hero thumbnail for the issue

---

## Quick Start

### Step 1: Validate an Idea

Paste a screenshot or link of a trending AI product:

```
/contentwise:idea-validator

[paste screenshot of Product Hunt launch / GitHub trending repo / viral X post]
```

**Output:** Idea Profile card with PROCEED / SKIP / CONDITIONAL recommendation.

### Step 2: Score the Hook

Run the full 8-dimension scoring:

```
/contentwise:hook-scorer

Score this: [product name + URL]
It's a [brief description]. Currently [signal data - stars, upvotes, etc.]
```

**Output:** 8 dimensions scored, weighted total /62.5, verdict: MUST COVER (50+) / STRONG (42-49) / TIMING DEPENDENT (34-41) / REJECT (<34).

### Step 3: Pick a Pillar + Title

```
/contentwise:pillar-matcher

[paste hook score report]
Previous issues used: 3 Viral Rebuilds, 1 Hype Audit, 1 Feature Extraction
```

**Output:** Primary pillar + 3-5 title options + pillar mix status.

### Step 4: Score the Packaging

```
/contentwise:virality-scorer

Idea: [name]
Pillar: [chosen pillar]
Title: [proposed title]
Angle: [1-3 sentences]
Hook score: [number from step 2]
```

**Output:** 8 packaging dimensions scored, total /57.5. If hook is high but virality is low: automatic repackaging suggestions.

### Step 5: Write the Newsletter

```
/contentwise:newsletter-writer

Idea: [name + URL]
Hook score: 48.5
Pillar: Viral Rebuild
Title: "We Rebuilt Today's #1 Product Hunt Launch"
Virality score: 42

Build notes:
- Started with [approach], hit [problem]
- Pivoted to [new approach]
- [What finally worked]
- Key surprise: [what was unexpected]

Lessons:
- [Takeaway 1]
- [Takeaway 2]
```

**Output:** Complete 10-section newsletter draft with `[VISUAL: ...]` callouts.

### Step 6: Plan the Visuals

```
/contentwise:visual-asset-planner

[paste the newsletter draft]
```

**Output:** Per-section visual checklist with 8 must-have visuals + nice-to-haves.

### Step 7: Final Review

```
/contentwise:newsletter-reviewer

[paste the newsletter draft]
[paste the visual asset plan]
```

**Output:** PASS or REVISE with section-by-section feedback.

---

## Skill Reference

| Skill | Trigger Phrases | Input | Output |
|-------|----------------|-------|--------|
| `/contentwise:idea-validator` | "validate this", "is this worth covering" | Screenshot, URL, or description | Idea Profile + PROCEED/SKIP |
| `/contentwise:hook-scorer` | "score this hook", "rate this idea" | Idea + signal data | Score /62.5 + verdict |
| `/contentwise:pillar-matcher` | "which pillar", "suggest titles" | Scored idea + optional history | Pillar + 3-5 titles |
| `/contentwise:virality-scorer` | "score virality", "check packaging" | Idea + pillar + title + angle | Score /57.5 + repackaging |
| `/contentwise:newsletter-writer` | "write the newsletter", "draft the issue" | All scores + build notes | Full 10-section draft |
| `/contentwise:visual-asset-planner` | "plan visuals", "shot list" | Newsletter draft | Visual checklist |
| `/contentwise:newsletter-reviewer` | "review the newsletter", "final review" | Draft + visual plan | PASS/REVISE + feedback |
| `/contentwise:content-aggregator` | "aggregate content", "content research" | competitors.json in project | Content blueprint doc |
| `/contentwise:thumbnail-creator` | "create thumbnail", "newsletter thumbnail" | Newsletter topic/draft | 16:9 hero image |

---

## The 7 Content Pillars

| Pillar | Core Question | Frequency |
|--------|---------------|-----------|
| Viral Rebuild | Can we recreate the core? | 5 per 12 |
| Hype Audit | Is this real or just packaging? | 2 per 12 |
| Feature Extraction | What one feature made it spread? | 2 per 12 |
| Better Than the Original | What would we improve? | 2 per 12 |
| Build Under Constraint | Can we do it with limits? | As needed |
| Open-Source Equivalent | What's the free version? | As needed |
| Lessons From the Build | What patterns keep appearing? | 1 per 12 |

---

## Brand Guidelines (Built Into Every Skill)

- **Tagline:** We reverse engineer trending AI products and rebuild what actually matters.
- **Mantra:** Find the hook. Decode the product. Rebuild the core.
- **Voice:** Premium field report, not a blog post.
- **Core content test:** Every issue must have a strong hook, clear challenge, visible progress, satisfying comparison, and transferable lesson.
- **Visual rule:** Every image must PROVE it, EXPLAIN it, or COMPARE it. No decorative filler.

---

## Plugin Structure

```
contentwise/
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   ├── idea-validator/SKILL.md
│   ├── hook-scorer/SKILL.md
│   ├── pillar-matcher/SKILL.md
│   ├── virality-scorer/SKILL.md
│   ├── newsletter-writer/
│   │   ├── SKILL.md
│   │   └── references/section-templates.md
│   ├── visual-asset-planner/SKILL.md
│   ├── newsletter-reviewer/
│   │   ├── SKILL.md
│   │   └── references/review-checklist.md
│   ├── content-aggregator/SKILL.md
│   └── thumbnail-creator/
│       ├── SKILL.md
│       └── references/templates.md
├── references/
│   ├── strategy.md
│   ├── prd.json
│   ├── content-sources.yaml
│   ├── competitors.json
│   └── newsletter_branding
├── README.md
├── LICENSE
└── .gitignore
```
