# Newsletter Review Checklist

This is the complete, structured checklist the newsletter-reviewer works through. Every item must be evaluated before a verdict is issued.

---

## Layer 1: Template Completeness

All 10+1 sections must be present and properly structured. Mark each as PRESENT / MISSING / WEAK.

| # | Section | What "present" means | Common weakness |
|---|---------|---------------------|-----------------|
| 0 | **Subject Line** | Mission-driven, curiosity-heavy. Sounds like a challenge, not a blog title. | Generic ("How We Built X"), passive ("A Look at X"), or clickbait without substance |
| 1 | **The Hook** | 3-5 lines. What happened, why it matters, what challenge is being taken on. | Too long (becomes a paragraph), too vague ("We found something cool"), or missing the challenge framing |
| 2 | **The Object** | Compact profile card: name, source, why trending, value prop, signal snapshot. Visual callouts for hero screenshot + signal card. | Missing signal data, no source attribution, or bloated into a full essay |
| 3 | **Why It Worked** | Three distinct subsections: what users saw, what made it feel magical, what drove virality. Visual callouts for annotated screenshot + magic breakdown. | Only one subsection, or all three say the same thing in different words |
| 4 | **The Rebuild Brief** | Objective, constraints, tool stack, success criteria, what is deliberately ignored. Visual callouts for challenge card + feature checklist. | Missing constraints (makes it feel like a tutorial, not a mission), missing "what we're ignoring" |
| 5 | **How We Think It Works** | Probable inputs, model/workflow, orchestration, UX layer, hidden complexity. Visual callouts for architecture diagram. | Surface-level ("it uses an LLM"), no diagram, or overly speculative without grounding |
| 6 | **The Build Log** | Attempt progression with failures and pivots. Must show real iteration. Visual callouts for iteration screenshots. | Jumps from start to success (no failures shown), reads like polished documentation, or dumps raw code |
| 7 | **Final Comparison** | Original vs rebuilt. What matched, what didn't, harder/easier than expected. Visual callouts for side-by-side + scorecard. | Only says "ours was close" without specifics, no visual comparison planned |
| 8 | **The Real Lesson** | 3-5 sharp, transferable lessons. Visual callouts for framework card. | Generic lessons ("AI is powerful"), only 1-2 lessons, or lessons that only apply to this specific build |
| 9 | **Build Takeaway** | Reusable asset: prompt template, mini architecture, starter repo, workflow, pattern, checklist. Visual callout for template preview. | No actual asset (just advice), or asset is too specific to reuse |
| 10 | **Next Week's Tease** | Open loop that creates return motivation. | Absent, or closed loop ("Next week we'll cover X" without curiosity) |

**Verdict rule:** If any section is MISSING, the draft cannot pass. If 3+ sections are WEAK, the draft cannot pass.

---

## Layer 2: Core Content Test

Five non-negotiable checks. Every piece must satisfy all five. Fail any one and the draft needs revision.

### Check 1: Strong External Hook
- Is the source object genuinely trending right now?
- Can you verify the signal (upvotes, stars, engagement, rank)?
- Would a reader recognize this as timely, not stale?
- **Fail indicators:** Source is weeks old with no fresh signal. Product is obscure with no public traction. Hook relies entirely on the writer's opinion rather than external evidence.

### Check 2: Clear Challenge
- Is the rebuild brief specific and compelling?
- Are constraints defined (not just "we'll rebuild it")?
- Is there a clear success/fail criteria?
- Does it feel like a mission, not a task?
- **Fail indicators:** Brief says "we'll try to rebuild it" without scope. No constraints. Success criteria is vague ("make something similar"). Reader wouldn't feel tension about whether it will work.

### Check 3: Visible Progress
- Does the build log show real iteration?
- Are failures and pivots documented, not just the happy path?
- Can the reader follow the journey from attempt to result?
- Does it feel alive and honest, not sanitized?
- **Fail indicators:** Build log jumps from "we started" to "here's the result." No failures mentioned. Every attempt works perfectly. Log reads like post-hoc documentation, not a live account.

### Check 4: Satisfying Comparison
- Is original vs rebuilt genuinely insightful?
- Does the comparison reveal something non-obvious?
- Are specific differences called out, not just "ours was close"?
- Is there a "harder than expected" or "easier than expected" insight?
- **Fail indicators:** Comparison is superficial ("looks similar"). No specific feature-by-feature breakdown. Missing the insight about what was surprisingly hard or easy. No visual comparison planned.

### Check 5: Transferable Lesson
- Will the reader walk away smarter about building, not just about this product?
- Are lessons applicable beyond this specific rebuild?
- Would a builder change their approach after reading this?
- **Fail indicators:** Lessons are product-specific ("this product uses good UX"). Lessons are generic platitudes ("AI is changing everything"). Reader learns facts but not frameworks. No reusable takeaway.

---

## Layer 3: Brand Voice

The draft must feel like a **premium field report**, NOT a blog post, tutorial, or generic AI content.

### Voice check 1: Subject Line
- Sounds like a mission, not a newsletter title
- Creates instant curiosity
- Implies action taken, not information shared
- **Pass examples:** "We Rebuilt Today's #1 Product Hunt Launch" / "This AI Demo Went Viral. We Tried to Recreate It"
- **Fail examples:** "A Deep Dive Into [Product]" / "How to Build Your Own [Product]" / "Everything You Need to Know About [Product]"

### Voice check 2: Opening Hook
- 3-5 lines maximum
- States what happened, why it matters, what challenge is ahead
- Punchy and specific, not general or meandering
- **Fail signals:** More than 5 lines. Starts with background context instead of action. Uses phrases like "In today's issue" or "Welcome back."

### Voice check 3: Build Log Aliveness
- Feels like you are reading field notes, not a tutorial
- Includes moments of failure, confusion, surprise
- Shows the human decision-making process
- Language is direct and specific, not polished corporate prose
- **Fail signals:** Every step works on first try. Language is overly formal. No personality. Reads like documentation. Uses phrases like "First, we implemented" / "Next, we configured."

### Voice check 4: Code Discipline
- Code appears only when it teaches a specific decision
- No large code dumps
- Code is annotated with why, not just what
- Most technical content is explained in prose or visuals, not code blocks
- **Fail signals:** Multiple code blocks without context. Code shown for completeness rather than insight. Reader would need to be a developer to follow the piece.

### Voice check 5: Lesson Sharpness
- Lessons are specific and transferable
- Each lesson could be a standalone insight
- Written as revelations, not summaries
- **Fail signals:** "We learned a lot." Lessons restate what happened instead of extracting a principle. Generic advice that could apply to anything.

---

## Layer 4: Visual System

### Must-have visuals (all 8 required)

| # | Visual | Purpose | Section it belongs to |
|---|--------|---------|----------------------|
| 1 | Hero screenshot | Prove it: show the original product/demo/repo | The Object |
| 2 | Signal card | Prove it: show real traction data (upvotes, stars, engagement) | The Object |
| 3 | Annotated teardown screenshot | Explain it: highlight what makes the product work (arrows, labels, callouts) | Why It Worked |
| 4 | Build brief card | Explain it: summarize goal, constraints, success criteria | The Rebuild Brief |
| 5 | Architecture diagram | Explain it: show inferred system flow | How We Think It Works |
| 6 | Iteration gallery | Prove it: 2-4 screenshots showing build progress | The Build Log |
| 7 | Final side-by-side comparison | Compare it: original vs rebuilt | Final Comparison |
| 8 | Lessons card | Explain it: concise, reusable takeaways in visual form | The Real Lesson |

### Visual rules
- Every visual must do one of three jobs: **prove it**, **explain it**, or **compare it**
- No stock images
- No decorative visuals with no informational value
- No huge code dumps as images
- No long screenshots without annotations
- Nice-to-have visuals (timeline, timer, failure log card, benchmark chart, etc.) are welcome but do not replace must-haves

**Verdict rule:** If any of the 8 must-have visuals are missing from the plan, the visual system check fails. If any visual serves no clear prove/explain/compare purpose, flag it.

---

## Verdict Decision Tree

```
IF any section is MISSING → REVISE
IF 3+ sections are WEAK → REVISE
IF any core content test FAILS → REVISE
IF brand voice has 3+ failures → REVISE
IF any must-have visual is missing → REVISE
ELSE → PASS
```

A PASS means the draft is ready for final polish and publishing. A REVISE means specific changes are needed before it can publish.
