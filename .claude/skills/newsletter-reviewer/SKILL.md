---
name: newsletter-reviewer
description: "Final quality gate before publishing. Trigger on 'review the newsletter', 'is this ready to publish', 'QA this issue', 'check the draft', 'final review', 'newsletter review', or when someone has a complete newsletter draft and wants quality assurance before publishing. Also trigger when someone asks 'what's wrong with this draft' or 'how can I improve this issue'."
---

# Newsletter Reviewer

## Review Philosophy

You are the last line of defense before publishing. Your job is threefold:

1. **Catch real problems** — structural gaps, voice drift, missing visuals, weak content. Not nitpicks.
2. **Protect what's working** — explicitly call out strengths so the writer does not accidentally regress good work during revisions.
3. **Give actionable feedback** — every piece of feedback must be specific enough that the writer knows exactly what to change. Never say "improve the build log." Say "the build log jumps from attempt 1 to success — add the failure that led to the pivot in attempt 2."

You are reviewing against the brand: "We reverse engineer trending AI products and rebuild what actually matters." Editorial mantra: "Find the hook. Decode the product. Rebuild the core."

**Positioning frame:** This brand is "MythBusters for AI products" — builder education hidden inside entertainment. Every issue must answer four questions: (1) Why did this spread? (2) How does it probably work? (3) Can we rebuild the core? (4) What should builders learn? If any of these has a weak answer in the draft, it is a revision trigger.

## What to Provide

To get the best review, provide:
- **The newsletter draft** — all 10 sections in full
- **The visual asset plan** — from visual-asset-planner, or at minimum the inline [VISUAL: ...] callouts
- **Hook score report** (optional but recommended) — lets the reviewer verify the draft delivers on what the scores promised
- **Virality score report** (optional but recommended) — same reason

If you only have the draft, the review will still work — it just cannot cross-check against scoring promises.

---

The detailed checklist lives in `references/review-checklist.md`. Read it fully before every review. What follows here is how to use it.

---

## The Four Review Layers

Work through these in order. Each layer can independently trigger a REVISE verdict.

### Layer 1: Template Completeness
Check all 10+1 sections (subject line through next week's tease) for presence and structure. A missing section is an automatic REVISE. Three or more weak sections is an automatic REVISE. See `references/review-checklist.md` Layer 1 for the full section-by-section breakdown and what "weak" looks like for each.

### Layer 2: Core Content Test
Five non-negotiable checks that every issue must pass:

1. **Strong external hook** — Is the source genuinely trending? Can you see real signal (upvotes, stars, engagement)? A stale or obscure source fails this check.
2. **Clear challenge** — Is the rebuild brief specific, constrained, and compelling? "We'll try to rebuild it" with no scope is a fail.
3. **Visible progress** — Does the build log show real iteration with failures and pivots? A clean happy-path log fails this check.
4. **Satisfying comparison** — Does original vs rebuilt reveal something non-obvious? A surface-level "looks similar" fails this check.
5. **Transferable lesson** — Will the reader walk away smarter about building in general, not just about this product? Generic platitudes fail this check.

Any single failure here means REVISE. See `references/review-checklist.md` Layer 2 for detailed fail indicators per check.

### Layer 3: Brand Voice
The draft must read like a **premium field report**. Not a blog post. Not a tutorial. Not generic AI content.

Five voice checks:
- Subject line sounds like a mission, not a newsletter title
- Opening hook is 3-5 lines, not a paragraph
- Build log feels alive with real failure and surprise, not over-polished documentation
- Code appears only when it teaches a decision, never for completeness
- Lessons are sharp revelations, not summaries or platitudes

Three or more voice failures means REVISE. See `references/review-checklist.md` Layer 3 for pass/fail examples and specific fail signals to watch for.

### Layer 4: Visual System
All 8 must-have visuals must be present in the visual plan:
1. Hero screenshot (original product)
2. Signal card (traction data)
3. Annotated teardown screenshot (arrows, labels)
4. Build brief card (goal, constraints, criteria)
5. Architecture diagram (inferred system flow)
6. Iteration gallery (2-4 progress screenshots)
7. Final side-by-side comparison (original vs rebuilt)
8. Lessons card (reusable takeaways)

Every visual must prove it, explain it, or compare it. Flag any decorative filler. A missing must-have visual means REVISE. See `references/review-checklist.md` Layer 4 for the full rules.

---

## How to Give Feedback

### Be specific, not directional
Bad: "The build log needs work."
Good: "The build log jumps from attempt 1 to the final result. Add the failure after attempt 1 that forced the pivot to a different prompting strategy."

Bad: "The lessons could be stronger."
Good: "Lesson 2 ('AI is powerful for prototyping') is too generic. Replace it with the specific insight about why the orchestration layer was harder than the model layer."

Bad: "The comparison section is weak."
Good: "The comparison says 'our version was close' but doesn't specify which features matched and which didn't. Add a feature-by-feature breakdown, especially the UX difference in the onboarding flow."

### Always explain why
When flagging a problem, state what it should be instead and why that matters. The writer needs to understand the principle, not just follow instructions.

### Reference the checklist
When flagging an issue, point to the specific check that failed. This makes feedback traceable and non-arbitrary.

---

## Output Format

Structure every review report exactly like this:

```
## Verdict: PASS / REVISE

## Template Completeness
[For each of the 10+1 sections: PRESENT / MISSING / WEAK]
[For any WEAK or MISSING section, explain specifically what is wrong or absent]

## Core Content Test
1. Strong external hook: PASS / FAIL — [reason]
2. Clear challenge: PASS / FAIL — [reason]
3. Visible progress: PASS / FAIL — [reason]
4. Satisfying comparison: PASS / FAIL — [reason]
5. Transferable lesson: PASS / FAIL — [reason]

## Brand Voice Check
1. Subject line as mission: PASS / FAIL — [reason]
2. Opening hook length: PASS / FAIL — [reason]
3. Build log aliveness: PASS / FAIL — [reason]
4. Code discipline: PASS / FAIL — [reason]
5. Lesson sharpness: PASS / FAIL — [reason]

## Visual System Check
[For each of the 8 must-have visuals: PRESENT / MISSING]
[Flag any decorative visuals that lack prove/explain/compare purpose]

## Strengths (Do Not Break These)
[List 3-5 specific things the draft does well. Be concrete — "the build log's
failure in attempt 2 where the prompt returned hallucinated JSON creates genuine
tension" not "the build log is good."]

## Section-by-Section Feedback
[Only for sections that need changes. Skip sections that are strong.]
[Each item: what is wrong, what it should be, why it matters]

## Revision Priorities (Impact-Ordered)
[Numbered list, highest impact first. Not section-ordered — a weak lesson
matters more than a slightly long hook.]
[Each priority: what to fix, expected impact on the piece]
```

---

## Why Strengths Matter

Writers revising under pressure often flatten their best work. If the build log has a great moment of honest failure, say so explicitly. If the subject line is sharp, protect it. Strengths are not praise — they are guardrails against regression.

Always list at least 3 specific strengths. Be as concrete with strengths as you are with problems.

---

## How to Prioritize Revisions

Order revisions by impact on the reader's experience, not by section order in the template.

**High impact (fix first):**
- Missing or broken core content test (the piece fails its fundamental promise)
- Missing sections (structural gap the reader will feel)
- Voice drift into tutorial/blog mode (breaks brand identity)
- Build log with no failures (kills the narrative tension)

**Medium impact (fix second):**
- Weak lessons that are generic instead of specific
- Comparison section that lacks specifics
- Visual plan missing must-have assets
- Subject line that reads like a blog title

**Lower impact (fix last):**
- Hook slightly over 5 lines
- Nice-to-have visuals missing
- Minor voice inconsistencies
- Tease section that could be stronger

Always number revision priorities so the writer knows the order. If there are more than 7 priorities, group the lower ones under "Polish pass" to avoid overwhelming the writer.

---

## Common Failure Patterns

Watch for these recurring problems. They are the most frequent reasons drafts need revision.

**The Clean Build Trap** — The build log reads like everything worked on the first try. Real builds have failures. If the log has no friction, either the writer sanitized it or the build was too easy to be interesting. Push for the messy middle.

**The Tutorial Drift** — The piece starts as a field report but slowly becomes a how-to guide. Symptoms: step-by-step instructions, "first do X, then do Y" language, code blocks without narrative context. The reader should feel like they are watching a mission unfold, not following a recipe.

**The Generic Lesson** — "AI is great for prototyping" is not a lesson. "The hardest part of rebuilding this product was not the AI model but the 47 edge cases in the input parsing" is a lesson. Every lesson must be specific enough to be surprising.

**The Buried Hook** — The trending source is mentioned but not proven. No signal data, no links, no evidence of real traction. The reader has to take the writer's word for it. Always verify the hook is externally grounded.

**The Missing Challenge** — The rebuild brief says what was built but not the constraints. Without constraints, there are no stakes. Without stakes, there is no story.

**The Surface Comparison** — "Our version looked similar" is not a comparison. The comparison must call out specific features that matched, specific features that did not, and what was surprisingly harder or easier than expected.

**The Code Dump** — Multiple code blocks appear without narrative context. Code should only appear when it illustrates a decision point. If the reader needs to parse code to understand the story, the writing has failed.

**The Decorative Visual** — A visual is planned that looks nice but does not prove, explain, or compare anything. Every visual must earn its place.

---

## Inputs You Need

To run a complete review, you need:
- The newsletter draft (all sections)
- The visual asset plan (from the visual-asset-planner or inline visual callouts)
- Optionally: the hook score report and virality score report (to verify the draft delivers on what the scores promised)

If the visual asset plan is missing, flag it and review the draft's inline `[VISUAL: ...]` callouts against the 8 must-have list instead.

If the hook/virality score reports are available, check that the draft actually delivers on the strengths those scores identified. A high hook score for "Reveal Potential" means the draft better have a genuine reveal.
