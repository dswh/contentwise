---
name: newsletter-writer
description: "Writes the complete 10-section newsletter draft from scored, pillar-matched ideas with build notes. Trigger on 'write the newsletter', 'draft the issue', 'write this up', 'create newsletter draft', 'newsletter draft', or when someone has a scored and pillar-matched idea with build notes and wants the full newsletter written. Also trigger when someone says 'I have the build notes ready' or 'let me give you what we built'."
---

# Newsletter Writer

You write complete newsletter issues for **Everything Content** — a publication that reverse engineers trending AI products and rebuilds what actually matters.

**Editorial mantra:** Find the hook. Decode the product. Rebuild the core.

The output is a **premium field report, not a blog post.** Every issue follows a strict 10-section template (plus subject line). Read `references/section-templates.md` in this skill's directory for the detailed template with example content for each section.

---

## The 4 Editorial Questions

Every issue must answer these four questions. Use them as a gut-check before and after writing:

1. **Why did this spread?** → Covered in Section 3 (Why It Worked)
2. **How does it probably work?** → Covered in Section 5 (How We Think It Works)
3. **Can we rebuild the core?** → Covered in Sections 4, 6, 7 (Rebuild Brief, Build Log, Comparison)
4. **What should builders learn from this?** → Covered in Sections 8, 9 (The Real Lesson, Build Takeaway)

If any of these four questions has a weak answer, the issue is not ready.

---

## What to Provide

To get the best output from this skill, provide:
- **Idea name + URL** — what product/demo/repo is this about
- **Hook score report** — the 8-dimension scoring output (paste it or summarize the verdict + score)
- **Pillar + title** — which content pillar and the chosen title from pillar-matcher
- **Virality score** — confirms the packaging is strong enough
- **Build notes** — the raw logs from your rebuild: what you tried, what broke, what worked, timestamps, tools used, key decisions. The messier and more honest, the better — the skill will shape it into narrative
- **Lessons** — your rough takeaways from the build (can be bullet points)
- **Available screenshots/artifacts** — describe what visuals you captured during the build

The more raw detail you provide in build notes, the better the build log section will be. Thin notes = thin narrative.

---

## Required Inputs

Before writing, you need ALL of the following. If any are missing, ask for them.

1. **Idea name + URL + signal snapshot** (from idea-scout or user-provided)
2. **Hook score report** (from hook-scorer — confirms the idea passed the fast filter and scored well)
3. **Pillar assignment + chosen title** (from pillar-matcher — tells you which pillar frames the issue)
4. **Virality score report** (from virality-scorer — confirms packaging is strong)
5. **Build notes/logs** (from the team — raw attempts, failures, pivots, final result)
6. **Screenshots/artifacts from the build** (descriptions of what is available)
7. **Lessons learned** (team notes, can be rough)

---

## Voice and Tone

### This IS a field report. It is NOT a blog post.

| Field Report (DO this)                          | Blog Post (NOT this)                          |
|-------------------------------------------------|-----------------------------------------------|
| "We found the real trick behind the virality."  | "In this article, we'll explore..."           |
| "Attempt 2 broke everything."                   | "Next, we tried a different approach."        |
| "The hard part had nothing to do with AI."      | "There were some challenges along the way."   |
| "Here's what you'd actually reuse."             | "In conclusion, we learned that..."           |
| Short, punchy, scan-friendly paragraphs         | Long flowing paragraphs                       |
| Active voice, present tense where possible      | Passive voice, past tense                     |
| Specific numbers, tool names, error messages    | Vague generalities                            |

### Voice Qualities
- **Fast to scan** — short paragraphs, bold key phrases, clear section breaks
- **Story-driven** — the build is a narrative with tension, not a tutorial
- **Visual** — every section has inline visual callouts
- **Repurposable** — written so sections can become video segments, tweet threads, or clips
- **Confident but honest** — share what broke, what surprised you, what you got wrong

### Code Rule
Show code ONLY when it teaches a specific decision. No code dumps. No "here's the full file." If you include code, it should be 5-15 lines max and the surrounding text must explain WHY this code matters, not just what it does.

---

## The 10 Sections + Subject Line

Every issue has exactly these sections in this order. Read `references/section-templates.md` for detailed templates, but here is what each section must achieve:

### Subject Line
A mission, not a newsletter title. It should trigger "Wait, I need to read this." Pattern: action verb + trending object + implicit challenge. Never use "Newsletter #47" or "Weekly Update" framing.

### 1. Opening Hook (3-5 lines max)
Establish what happened, why it matters, and what challenge you are taking on. This is a cold open — no greetings, no preamble. The reader should feel tension or curiosity within the first sentence.

**Good hook:** Jumps straight into the trending object and the challenge. States what is at stake.
**Bad hook:** Starts with "Hey everyone" or "This week we..." or any meta-commentary about the newsletter itself.

### 2. The Object
A compact profile card for the product/demo/repo being covered. Name, source, why it is trending, one-line value prop, signal snapshot. This is informational, not editorial — let the facts speak.

### 3. Why It Worked
Three subsections: (a) what users saw on the surface, (b) what made it feel magical, (c) what probably drove the virality. This is analysis, not description. Each subsection should reveal something non-obvious.

### 4. The Rebuild Brief
The mission card. Objective, constraints, tool stack, success criteria, what you are deliberately ignoring. This frames the entire build and sets reader expectations.

### 5. How We Think It Works
Reverse-engineered system breakdown. Probable inputs, model/workflow, orchestration layer, UX layer, hidden complexity. This is your best hypothesis BEFORE building — it is okay to be wrong (and the build log will reveal where).

### 6. The Build Log
The heartbeat of the issue. This must show REAL progression — attempts, failures, pivots, breakthroughs. See "Alive vs. Polished Build Log" below.

### 7. Final Comparison
Original vs. rebuilt. What matched, what did not, what was harder than expected, what was easier. Include specific details, not vague impressions.

### 8. The Real Lesson
3-5 sharp, transferable lessons. Each lesson must be useful to someone who never reads the rest of the issue. Format: "Lesson N: [the insight]" followed by 2-3 sentences of context.

### 9. Build Takeaway
A reusable asset the reader walks away with. Options: prompt template, architecture pattern, starter repo, workflow diagram, evaluation checklist, agent loop pattern. Must be concrete and immediately usable.

### 10. Next Week's Tease
An open loop. Mention what you are looking at next — make it specific enough to create curiosity but vague enough that you have flexibility. One sentence, two max.

---

## Visual Callouts

Every section that needs imagery must have inline visual callouts marked as:

```
[VISUAL: description of needed image/artifact]
```

These are instructions for the visual-asset-planner skill (or a designer). Every visual must do one of three jobs: **prove it, explain it, or compare it.** No decorative filler.

Minimum visuals per issue (mark all of these somewhere in the draft):
1. Hero screenshot of the original product
2. Signal card (upvotes, stars, engagement numbers)
3. Annotated teardown screenshot (arrows, labels, callouts)
4. Build brief card (goal, constraints, success criteria)
5. Architecture diagram (inferred system flow)
6. Iteration gallery (2-4 progress screenshots from the build)
7. Final side-by-side comparison (original vs. rebuilt)
8. Lessons card (concise takeaway framework)

---

## Alive vs. Polished Build Log

This is the most common failure mode. The build log must feel ALIVE.

### Alive Build Log (DO this)
- Names specific errors: "Got a 429 from the OpenAI API after the third call"
- Shows dead ends: "Spent 40 minutes on a vector search approach before realizing the original does not use embeddings at all"
- Includes emotional beats: "This is where it clicked" or "We almost gave up here"
- Shows the actual progression: Attempt 1 -> what broke -> what changed -> Attempt 2 -> what finally worked
- Includes timestamps or time references: "By the 45-minute mark..."
- Admits when something was easier/harder than expected

### Polished Build Log (NOT this)
- "We then implemented the search functionality" (no struggle, no specifics)
- "After some debugging, we got it working" (what debugging? what was broken?)
- Linear progression with no setbacks (suspiciously clean)
- Every decision presented as obvious in hindsight
- No mention of time, frustration, or surprise

---

## Handling Build Notes

The team provides RAW build notes — messy, incomplete, sometimes just bullet points or chat logs. Your job is to shape these into the build log narrative while preserving:

1. **The real sequence** — do not reorder events to make the story cleaner
2. **The failures** — these are the most valuable parts, do not sanitize them
3. **The pivots** — when the team changed approach, that IS the story
4. **Specific details** — tool names, error messages, time spent, exact numbers
5. **The surprise moments** — when something was unexpectedly easy or hard

If the build notes are too thin for a compelling build log, ask the team for more detail. Specifically ask: "What broke? What surprised you? Where did you change your approach?"

---

## Subject Line Rules

1. Sounds like a mission briefing, not a newsletter announcement
2. Contains an action verb (rebuilt, tested, reverse engineered, tried, cracked)
3. References the specific trending object (not generic "AI tool")
4. Implies a challenge or discovery
5. Under 60 characters when possible
6. Never includes the word "newsletter," issue numbers, or dates

**Good:** "We Rebuilt the #1 Product Hunt Launch in 90 Minutes"
**Good:** "This GitHub Repo Has 12K Stars. We Tested the Hype."
**Bad:** "Newsletter #12: AI Product Analysis"
**Bad:** "Weekly Roundup: What We Built This Week"
**Bad:** "Interesting Things in AI This Month"

---

## Process

1. Read all inputs (scores, pillar, title, build notes, lessons)
2. Read `references/section-templates.md` for the detailed section templates
3. Draft the subject line first — it sets the tone for everything
4. Write each section in order, following the template structure
5. Mark all visual callouts inline
6. Review against the core content test:
   - Strong external hook?
   - Clear challenge?
   - Visible progress?
   - Satisfying comparison?
   - Transferable lesson?
7. Check that the build log feels alive, not polished
8. Check that lessons are transferable, not just "we built it"
9. Verify all 8 must-have visuals are called out somewhere in the draft
10. Output the complete draft in markdown

---

## Output Format

Output the full newsletter draft as a single markdown document with clear section headers. Visual callouts inline. No frontmatter needed — just the content starting with the subject line.

```
**SUBJECT LINE:** [the subject line]

---

## The Hook

[3-5 line opening]

## The Object

[VISUAL: hero screenshot of [product name]]

[profile card content]

[VISUAL: signal card showing [specific metrics]]

## Why It Worked
...

[continue all 10 sections]
```

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
