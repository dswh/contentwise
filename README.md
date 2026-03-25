# ContentWise

**7 Claude Code skills that take your team from "I saw something trending" to "published newsletter" — with scoring, brand alignment, and quality gates at every step.**

Brand: *We reverse engineer trending AI products and rebuild what actually matters.*

---

## The Pipeline

```
Screenshot / Link
       ↓
  /idea-validator       →  Is this worth pursuing?
       ↓
  /hook-scorer          →  How strong is the idea? (score /62.5)
       ↓
  /pillar-matcher       →  What format + title?
       ↓
  /virality-scorer      →  Will the packaging spread? (score /57.5)
       ↓
  /newsletter-writer    →  Full 10-section draft
       ↓
  /visual-asset-planner →  Shot list for every image
       ↓
  /newsletter-reviewer  →  PASS or REVISE with feedback
```

---

## Quick Start

### Step 1: Validate an Idea

Someone on your team spots a trending AI product. They paste a screenshot or link:

```
/idea-validator

[paste screenshot of Product Hunt launch / GitHub trending repo / viral X post]
```

**What to provide:** A screenshot, URL, or just a name + description.

**What you get back:** An Idea Profile card with:
- Product name, source, signal snapshot
- Fast filter results (3 yes/no questions)
- Recommendation: PROCEED / SKIP / CONDITIONAL

---

### Step 2: Score the Hook

If the idea passes validation, run the full 8-dimension scoring:

```
/hook-scorer

Score this: [product name + URL]
It's a [brief description]. Currently [signal data — stars, upvotes, etc.]
```

**What to provide:** Idea name, URL, description, and signal data. Or paste the Idea Profile from Step 1.

**What you get back:**
- Fast filter gate (pass/fail)
- 8 dimensions scored 1-5 with reasoning
- Weighted total out of 62.5
- Verdict: MUST COVER (50+) / STRONG (42-49) / TIMING DEPENDENT (34-41) / REJECT (<34)

---

### Step 3: Pick a Pillar + Title

Choose the best content format and generate title options:

```
/pillar-matcher

[paste hook score report or describe the idea]
Previous issues used: 3 Viral Rebuilds, 1 Hype Audit, 1 Feature Extraction
```

**What to provide:** Idea + hook score report. Optionally, your recent issue pillar history for mix tracking.

**What you get back:**
- Primary pillar recommendation with reasoning
- Secondary pillar as backup
- 3-5 title options (top pick marked)
- Pillar mix status (warns if a format is overused)

**The 7 pillars:**

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

### Step 4: Score the Packaging

Check if the title and angle will actually spread:

```
/virality-scorer

Idea: [name]
Pillar: [chosen pillar]
Title: [proposed title]
Angle: [1-3 sentences on how you'll frame it]
Hook score: [number from step 2]
```

**What to provide:** Idea + pillar + proposed title + angle + hook score.

**What you get back:**
- 8 packaging dimensions scored with reasoning
- Weighted total out of 57.5
- Verdict: HIGH VIRAL (46+) / STRONG (38-45) / IMPROVE PACKAGING (30-37) / WEAK (<30)
- If hook is high but virality is low: automatic repackaging suggestions with rewritten titles

---

### Step 5: Write the Newsletter

Once scoring is complete, provide your build notes and let the skill write the full issue:

```
/newsletter-writer

Idea: [name + URL]
Hook score: 48.5 — STRONG CANDIDATE
Pillar: Viral Rebuild
Title: "We Rebuilt Today's #1 Product Hunt Launch"
Virality score: 42 — STRONG

Build notes:
- Started with [approach], hit [problem] at [time]
- Pivoted to [new approach] because [reason]
- [What finally worked]
- Total time: [X minutes]
- Key surprise: [what was harder/easier than expected]

Lessons:
- [Rough takeaway 1]
- [Rough takeaway 2]
- [Rough takeaway 3]
```

**What to provide:** All prior skill outputs + raw build notes (the messier and more honest, the better) + rough lessons.

**What you get back:** Complete 10-section newsletter draft:
1. Subject line (mission-driven)
2. Opening hook (3-5 lines)
3. The Object (profile card)
4. Why It Worked (3 subsections)
5. The Rebuild Brief (goal, constraints, stack, success criteria)
6. How We Think It Works (reverse-engineered architecture)
7. The Build Log (attempts, failures, pivots — alive, not polished)
8. Final Comparison (original vs rebuilt)
9. The Real Lesson (3-5 transferable insights)
10. Build Takeaway (reusable asset)
11. Next Week's Tease (open loop)

All sections include `[VISUAL: ...]` callouts for the visual planner.

---

### Step 6: Plan the Visuals

Generate a complete shot list from the draft:

```
/visual-asset-planner

[paste the newsletter draft from step 5]
```

**What to provide:** The complete newsletter draft. Optionally, describe what screenshots/artifacts you already captured during the build.

**What you get back:** Per-section visual checklist with:
- 8 must-have visuals (hero screenshot, signal card, annotated teardown, build brief card, architecture diagram, iteration gallery, side-by-side comparison, lessons card)
- Nice-to-have visuals where the content warrants them
- Each asset tagged: type, description, priority, purpose (PROVE / EXPLAIN / COMPARE), specs, source

---

### Step 7: Final Review

Run the quality gate before publishing:

```
/newsletter-reviewer

[paste the newsletter draft]
[paste the visual asset plan]
```

**What to provide:** The newsletter draft + visual plan. Optionally, the hook and virality score reports.

**What you get back:**
- **Verdict: PASS or REVISE**
- Template completeness (10+1 sections checked)
- Core content test (5 checks: strong hook, clear challenge, visible progress, satisfying comparison, transferable lesson)
- Brand voice check (field report, not blog post)
- Visual system check (all 8 must-haves present)
- Strengths to protect
- Section-by-section feedback (only for sections that need changes)
- Revision priorities ordered by impact

If REVISE: fix the flagged issues and run the reviewer again.
If PASS: publish.

---

## Skill Reference

| Skill | Trigger Phrases | Input | Output |
|-------|----------------|-------|--------|
| `/idea-validator` | "validate this", "is this worth covering", "check this out" | Screenshot, URL, or description | Idea Profile card + PROCEED/SKIP |
| `/hook-scorer` | "score this hook", "rate this idea", "hook score" | Idea + signal data | 8-dim score /62.5 + verdict |
| `/pillar-matcher` | "which pillar", "suggest titles", "what format" | Scored idea + optional history | Pillar + 3-5 titles + mix status |
| `/virality-scorer` | "score virality", "will this spread", "check packaging" | Idea + pillar + title + angle | 8-dim score /57.5 + repackaging |
| `/newsletter-writer` | "write the newsletter", "draft the issue" | All scores + build notes + lessons | Full 10-section draft |
| `/visual-asset-planner` | "plan visuals", "shot list", "what images" | Newsletter draft | Per-section visual checklist |
| `/newsletter-reviewer` | "review the newsletter", "is this ready", "final review" | Draft + visual plan | PASS/REVISE + feedback |

---

## Brand Guidelines (Built Into Every Skill)

- **Tagline:** We reverse engineer trending AI products and rebuild what actually matters.
- **Mantra:** Find the hook. Decode the product. Rebuild the core.
- **Voice:** Premium field report, not a blog post.
- **Core content test:** Every issue must have a strong hook, clear challenge, visible progress, satisfying comparison, and transferable lesson.
- **Visual rule:** Every image must PROVE it, EXPLAIN it, or COMPARE it. No decorative filler.

---

## Project Structure

```
contentwise/
├── .claude/skills/
│   ├── idea-validator/SKILL.md
│   ├── hook-scorer/SKILL.md
│   ├── pillar-matcher/SKILL.md
│   ├── virality-scorer/SKILL.md
│   ├── newsletter-writer/
│   │   ├── SKILL.md
│   │   └── references/section-templates.md
│   ├── visual-asset-planner/SKILL.md
│   └── newsletter-reviewer/
│       ├── SKILL.md
│       └── references/review-checklist.md
├── prd.json              # Full PRD with all skill specs
├── strategy.md           # Content strategy reference
├── newsletter_branding   # Complete branding guidelines
├── competitors.json      # Tracked content sources
└── content-sources.yaml  # Monitored channels
```
