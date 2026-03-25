---
name: virality-scorer
description: "Scores whether a content piece's PACKAGING will actually spread. Trigger on 'score virality', 'will this go viral', 'check the packaging', 'is the angle strong enough', 'virality score', or when someone has a titled/angled content piece and wants to know if the packaging will spread. Also trigger when someone is unsure why a good idea isn't clicking as content — that's almost always a packaging problem, not an idea problem."
---

# Virality Scorer

## What This Skill Does

This skill scores the **story packaging** of a content piece across 8 dimensions (max 57.5 points). It answers: "Will this presentation actually spread?"

This is fundamentally different from hook scoring. Hook scoring evaluates the **idea itself** — is this product worth rebuilding, will the audience learn something, can we execute it? Virality scoring evaluates the **wrapper around the idea** — the title, angle, framing, and emotional structure that determine whether anyone clicks, watches, reads, or shares.

A hook can score 50+ (must cover) and still die as content if the packaging is generic. A mediocre idea with brilliant packaging will outperform a brilliant idea with flat packaging every time.

**Brand context:** We reverse engineer trending AI products and rebuild what actually matters. Our audience is builders, founders, and developers.

---

## When to Use This

- After hook scoring and pillar matching are done
- When you have: idea name + chosen pillar + proposed title/angle
- When someone asks "will this go viral" or "is this angle strong enough"
- When a good idea feels flat and you cannot figure out why
- When you want to compare two different angles for the same idea

## What to Provide

To score virality, provide:
- **Idea name** — what product/demo/repo this is about
- **Chosen pillar** — which content pillar (Viral Rebuild, Hype Audit, etc.)
- **Proposed title** — the working headline you want to test
- **Draft angle** — 1-3 sentences on how you plan to frame the piece
- **Hook score** — the score from hook-scorer (needed for the repackaging trigger: if hook >= 42 but virality < 30, repackaging kicks in automatically)

If you want to compare two different angles for the same idea, run the skill twice with different titles/angles and compare the scores.

## Required Inputs

1. **Idea name** — the product/demo/repo being covered
2. **Chosen pillar** — which of the 7 content pillars this falls under
3. **Proposed title** — the working title or headline
4. **Draft angle/framing** — how you plan to present the piece (1-3 sentences)
5. **Hook score** (if available) — needed to trigger repackaging logic

If the user does not provide a hook score, ask for it. If they do not have one, note that the repackaging system cannot be evaluated without it.

---

## The 8 Dimensions

Score each dimension from 1 to 5. Apply the weight. Sum for total.

### 1. Instant Curiosity (weight: x2)

**Question:** Would the title alone trigger "Wait, what?"

| Score | Meaning |
|-------|---------|
| 1 | Generic — could be any AI newsletter |
| 2 | Mildly interesting but no pull |
| 3 | Would pause scrolling briefly |
| 4 | Strong pull — would click to find out |
| 5 | Irresistible — must know what happened |

**Scoring guidance:**
- Does the title contain a specific, concrete element (product name, number, constraint)?
- Does it create an information gap the reader needs to close?
- Would you click this if you saw it in a crowded feed?
- Test: read the title cold. If your reaction is "okay" instead of "wait, what?" — it is a 1-3.

**Low curiosity:** "Building an AI App with Claude" (no gap, no tension)
**High curiosity:** "We Had 90 Minutes to Rebuild Today's #1 Product Hunt Launch" (specific, tense, outcome unknown)

### 2. Stakes (weight: x1.5)

**Question:** Is there clear tension or consequence?

| Score | Meaning |
|-------|---------|
| 1 | No stakes — just "we built a thing" |
| 2 | Vague challenge, no real consequence |
| 3 | Some tension — time or scope pressure |
| 4 | Clear stakes — pass/fail, comparison, constraint |
| 5 | High drama — blind test, public challenge, ticking clock |

**What creates stakes:** time limits, quality targets, blind comparisons, feature-matching requirements, constrained toolsets, same-day launches, head-to-head matchups.

**Key insight:** Low virality almost always comes from low stakes. "We rebuilt X" is weaker than "We had 90 minutes to rebuild X." Same idea, completely different energy.

### 3. Novelty (weight: x2)

**Question:** Does this feel fresh, not like generic AI content?

| Score | Meaning |
|-------|---------|
| 1 | Seen this exact framing a hundred times |
| 2 | Slight twist on a common format |
| 3 | Familiar structure but fresh subject |
| 4 | Noticeably different angle |
| 5 | Never seen this framing before |

**Low-novelty packaging examples:**
- "Claude Code Tutorial"
- "How to Use AI Agents"
- "Build an App with AI"
- "Top 10 AI Tools for Developers"
- "We Built X with Y" (no angle beyond the build itself)

**High-novelty packaging examples:**
- "We Rebuilt a Viral Product and Found Out the AI Was the Easy Part"
- "We Tested Whether the Hype Was Fake — Here's What We Found"
- "We Isolated the One Feature That Made This App Blow Up"
- "This Product Looked Like Magic. It Was Mostly Orchestration."
- "Is This Viral AI Startup Actually Hard to Build? (We Found Out)"

**The test:** If you could swap your brand name for any other AI newsletter and the title still works, novelty is low. Your packaging should feel like something only your brand would produce.

### 4. Visual Promise (weight: x1.5)

**Question:** Can the thumbnail or hero image tell a story fast?

| Score | Meaning |
|-------|---------|
| 1 | No obvious visual — mostly text/code/backend |
| 2 | Could show something but not compelling |
| 3 | Decent visual hook — product screenshot with context |
| 4 | Strong visual — clear before/after or comparison |
| 5 | Instantly compelling — tells the whole story in one frame |

**Strong visual ingredients:**
- Original product vs your version (side-by-side)
- Countdown timer overlay
- Progress board showing attempts
- Before/after transformation
- Dramatic feature comparison
- Score card or verdict badge

**Scoring tip:** Imagine the thumbnail at phone size. Can someone understand the premise without reading? If yes, score 4-5. If they need the title to get it, score 2-3.

### 5. Emotional Engine (weight: x1.5)

**Question:** What emotion drives the piece?

| Score | Meaning |
|-------|---------|
| 1 | Purely informative — no emotional pull |
| 2 | Mildly interesting but no feeling |
| 3 | One clear emotion present |
| 4 | Strong emotional throughline |
| 5 | Multiple emotions layered (curiosity into tension into surprise) |

**Best emotions for our audience:**
- **Curiosity** — "How does this actually work?"
- **Challenge tension** — "Can they pull this off?"
- **Surprise** — "I did not expect that to be the hard part"
- **Competence aspiration / competence fantasy** — "I could build this myself" / "Maybe I could build cool things too." This is huge for our audience. People do not just want to watch — they want to feel that the distance between them and the builder is closeable. Content that makes the reader feel empowered, not excluded, scores highest here.
- **Skepticism** — "Is this actually real?"
- **Delight** — "That is clever"
- **Progress dopamine** — The feeling of watching measurable improvement unfold. Scoreboards, checkpoints, version comparisons, before/after moments. People stay when they can see things getting better in real time. This is why the build log section of the newsletter is so critical — it IS the emotional engine for most issues.

**Warning:** If the piece is purely informative with no emotional arc, virality drops hard. Even technical content needs an emotional engine. "Here is how X works" is informational. "We thought X was magic until we looked inside" has curiosity + surprise.

**The layering principle:** The strongest pieces layer multiple emotions across the arc — curiosity in the hook, challenge tension in the build brief, progress dopamine through the build log, surprise in the reveal, competence aspiration in the lessons. Score 5 means this layering is present. Score 1 means the piece is flat and informational throughout.

### 6. Shareability (weight: x1.5)

**Question:** Would someone send this to a founder, builder friend, colleague, or AI enthusiast?

| Score | Meaning |
|-------|---------|
| 1 | No share impulse — interesting only to the reader |
| 2 | Might bookmark, would not send |
| 3 | Would share if it came up in conversation |
| 4 | Would actively send to 1-2 specific people |
| 5 | Would post publicly or send to a group chat |

**High-share triggers (what the sender would say):**
- "You should see how simple this actually was"
- "This breakdown explains why this product spread"
- "This is how you would build it yourself"
- "They actually tested if the hype was real"
- "This is the best explanation I have seen of how X works"

**Scoring tip:** Imagine a developer seeing this in their feed. Do they just consume it, or do they forward it? The difference is whether the content makes the *sharer* look smart or helpful.

### 7. Identity Pull (weight: x1.5)

**Question:** Does consuming this make the viewer feel like an insider, smart builder, or someone who understands what is actually happening?

| Score | Meaning |
|-------|---------|
| 1 | No identity connection — generic content |
| 2 | Loosely relevant to builders |
| 3 | Makes reader feel informed |
| 4 | Makes reader feel like an insider |
| 5 | Makes reader feel like part of an elite group who gets it |

**What creates identity pull for our audience:**
- "Now I understand what is actually behind this trending product"
- "I know the real story, not the hype"
- "I could actually build this — I am that kind of builder"
- "I am the person who looks deeper, not the person who just retweets"

**Low identity pull:** "10 AI Tools You Should Know" (anyone could read this)
**High identity pull:** "The Real Architecture Behind This Viral AI Demo" (only builders who want to understand the mechanism care)

**Key insight from our brand positioning:** We are "MythBusters for AI products" — builder education hidden inside entertainment. The identity we reinforce is: smart, early, builder-minded, not just a passive consumer of AI hype. Content that makes the reader feel like they see through the hype while everyone else just retweets it — that is maximum identity pull.

### 8. Clipability (weight: x1)

**Question:** Can you extract 3-5 short standalone moments?

| Score | Meaning |
|-------|---------|
| 1 | Monolithic — no natural clip points |
| 2 | One possible clip moment |
| 3 | 2-3 decent clip moments |
| 4 | 4-5 strong standalone moments |
| 5 | Every section has a clip-worthy moment |

**Good clip moments:**
- "We found the real trick behind this product"
- "The hardest part had nothing to do with AI"
- "This took 4 prompts to crack"
- "This one feature made the whole product work"
- "Here is the part nobody is talking about"
- The moment your rebuild first works
- The final side-by-side reveal

---

## Scoring Formula

```
Virality Score =
  (Instant Curiosity x 2)
+ (Stakes x 1.5)
+ (Novelty x 2)
+ (Visual Promise x 1.5)
+ (Emotional Engine x 1.5)
+ (Shareability x 1.5)
+ (Identity Pull x 1.5)
+ (Clipability x 1)

Max = 5(2) + 5(1.5) + 5(2) + 5(1.5) + 5(1.5) + 5(1.5) + 5(1.5) + 5(1)
    = 10 + 7.5 + 10 + 7.5 + 7.5 + 7.5 + 7.5 + 5
    = 57.5
```

## Thresholds

| Score Range | Verdict | Action |
|-------------|---------|--------|
| 46+ | **High Viral Potential** | Ship it. This packaging is strong. |
| 38-45 | **Strong** | Good to go, minor tweaks optional. |
| 30-37 | **Decent — Improve Packaging** | The idea is fine but the wrapper needs work. Identify the weakest 2-3 dimensions and rework. |
| Below 30 | **Weak Packaging** | Even if the build is good, this will underperform. Repackage before proceeding. |

---

## The Repackaging System

### When It Triggers

**Trigger condition:** Hook score >= 42 AND Virality score < 30

This is the critical case. The idea is genuinely worth covering (strong hook), but the current packaging will kill it. **NEVER recommend dropping the idea.** Instead, output specific repackaging strategies.

Even outside the formal trigger (e.g., virality 30-37), you should suggest improvements for the weakest dimensions. The formal trigger just makes repackaging mandatory and prominent.

### The 5 Repackaging Strategies

#### Strategy 1: Add a Time Constraint
Turn an open-ended build into a ticking-clock challenge.

- **Before:** "We Rebuilt This Viral AI Product" (virality ~25)
- **After:** "We Had 90 Minutes to Rebuild Today's #1 Product Hunt Launch" (virality ~44)
- **Why it works:** Adds stakes (dimension 2), emotional tension (dimension 5), and visual promise via timer (dimension 4). Often lifts 3 dimensions at once.
- **Best for:** Viral Rebuild and Better Than the Original pillars.

#### Strategy 2: Narrow to One Killer Feature
Stop trying to rebuild everything. Zoom into the one feature that made the product spread.

- **Before:** "We Rebuilt This AI Writing Tool" (virality ~22)
- **After:** "We Rebuilt the One Feature That Made This AI App Blow Up" (virality ~41)
- **Why it works:** Boosts curiosity (what feature?), novelty (specific vs generic), and shareability (people want to know the one thing). Narrow focus also makes it more clipable.
- **Best for:** Feature Extraction pillar, but can rescue any pillar.

#### Strategy 3: Add a Blind Test
Introduce a comparison where testers do not know which version is which.

- **Before:** "We Built Our Own Version of This Trending AI Tool" (virality ~24)
- **After:** "We Showed 5 Developers Our Rebuild vs the Original — Nobody Could Tell the Difference" (virality ~46)
- **Why it works:** Massive curiosity boost, high stakes (will they get caught?), strong visual promise (reaction shots, reveal moment), extremely shareable.
- **Best for:** Hype Audit and Better Than the Original pillars.

#### Strategy 4: Frame as Myth-Busting
Position the piece as investigating whether the hype is real.

- **Before:** "We Tried to Build This Popular AI Product" (virality ~23)
- **After:** "Is This Viral AI Startup Actually Hard to Build? We Found Out." (virality ~43)
- **Why it works:** Curiosity becomes irresistible (real or fake?), emotional engine shifts to skepticism + surprise, strong identity pull (insider knowledge), very shareable (people love debunking).
- **Best for:** Hype Audit pillar, but works anywhere the hype-vs-reality angle is credible.

#### Strategy 5: Compare Your Version Against the Original
Make the head-to-head comparison the centerpiece, not just a section.

- **Before:** "We Rebuilt a Trending GitHub AI Tool" (virality ~26)
- **After:** "We Rebuilt This Viral AI Tool — Then Put Them Side by Side" (virality ~42)
- **Why it works:** Visual promise jumps (side-by-side is instant thumbnail), stakes are clear (who wins?), curiosity is strong (how close did they get?), highly clipable (the reveal moment).
- **Best for:** Viral Rebuild and Better Than the Original pillars.

### Choosing the Right Strategy

When repackaging triggers, pick the strategies that lift the **weakest scoring dimensions**:

| If weakest dimensions are... | Best strategies |
|------------------------------|-----------------|
| Curiosity + Stakes | Time Constraint, Blind Test |
| Novelty + Identity Pull | Myth-Busting, Narrow to One Feature |
| Visual Promise + Shareability | Compare Against Original, Blind Test |
| Emotional Engine + Stakes | Time Constraint, Myth-Busting |
| Clipability + Visual Promise | Narrow to One Feature, Compare Against Original |

Always suggest 2-3 strategies, not all 5. Pick the ones that address the specific weaknesses.

---

## Output Format

Present the report in this exact structure:

```
## Virality Score Report

**Idea:** [name]
**Pillar:** [chosen pillar]
**Title:** [proposed title]
**Angle:** [draft framing]

---

### Hook vs Packaging Distinction
[1-2 sentences: why the hook score and virality score differ, if they do.
Example: "The hook is strong — this product is genuinely trending and
rebuildable. But the current title sounds like every other AI newsletter.
The packaging needs more tension."]

---

### Dimension Scores

| # | Dimension | Raw (1-5) | Weight | Weighted |
|---|-----------|-----------|--------|----------|
| 1 | Instant Curiosity | X | x2 | XX |
| 2 | Stakes | X | x1.5 | XX |
| 3 | Novelty | X | x2 | XX |
| 4 | Visual Promise | X | x1.5 | XX |
| 5 | Emotional Engine | X | x1.5 | XX |
| 6 | Shareability | X | x1.5 | XX |
| 7 | Identity Pull | X | x1.5 | XX |
| 8 | Clipability | X | x1 | XX |
| | **TOTAL** | | | **XX / 57.5** |

### Dimension Reasoning

1. **Instant Curiosity (X/5):** [reasoning referencing the actual title]
2. **Stakes (X/5):** [reasoning about specific tension present or absent]
3. **Novelty (X/5):** [reasoning about freshness of the framing]
4. **Visual Promise (X/5):** [reasoning about thumbnail/visual potential]
5. **Emotional Engine (X/5):** [reasoning about which emotions drive the piece]
6. **Shareability (X/5):** [reasoning about forward/share impulse]
7. **Identity Pull (X/5):** [reasoning about audience identity connection]
8. **Clipability (X/5):** [reasoning about extractable moments]

---

### Verdict: [HIGH VIRAL POTENTIAL / STRONG / DECENT — IMPROVE PACKAGING / WEAK PACKAGING]

[1-3 sentences summarizing the verdict and what drives it.]

---

### Top Weaknesses
[The 2-3 lowest-scoring dimensions and what specifically drags them down.]

### Top Strengths
[The 2-3 highest-scoring dimensions and what makes them work.]
```

**If repackaging is triggered (hook >= 42 AND virality < 30), add this section:**

```
---

### REPACKAGING REQUIRED

Do not drop this idea. The hook score of [X] confirms it is worth covering.
The packaging score of [X] means the current framing will underperform.

**Recommended repackaging strategies:**

1. **[Strategy Name]**
   Rewritten title: "[new title]"
   How to apply: [1-2 sentences specific to this idea]
   Projected lift: [which dimensions improve and by roughly how much]

2. **[Strategy Name]**
   Rewritten title: "[new title]"
   How to apply: [1-2 sentences specific to this idea]
   Projected lift: [which dimensions improve and by roughly how much]

3. **[Strategy Name]**
   Rewritten title: "[new title]"
   How to apply: [1-2 sentences specific to this idea]
   Projected lift: [which dimensions improve and by roughly how much]

**Strongest option:** [Pick the single best one and explain why in 1-2 sentences.]
**Estimated new score:** [projected total after repackaging]
```

---

## Worked Example: Repackaging Transforms a Weak Score

### Original Packaging (Weak — Score 26.5/57.5)

**Idea:** Bolt.new (trending AI code generation tool)
**Pillar:** Viral Rebuild
**Title:** "We Rebuilt Bolt.new"
**Angle:** We reverse engineered Bolt.new and built our own version.
**Hook score:** 48 (strong candidate)

| # | Dimension | Raw | Weight | Weighted | Problem |
|---|-----------|-----|--------|----------|---------|
| 1 | Instant Curiosity | 2 | x2 | 4 | Title is flat — no gap, no tension |
| 2 | Stakes | 1 | x1.5 | 1.5 | No stakes — just "we built a thing" |
| 3 | Novelty | 2 | x2 | 4 | Sounds like every other AI rebuild post |
| 4 | Visual Promise | 3 | x1.5 | 4.5 | Product is visual but framing does not promise comparison |
| 5 | Emotional Engine | 2 | x1.5 | 3 | Informative only, no feeling |
| 6 | Shareability | 2 | x1.5 | 3 | Nothing makes someone forward this |
| 7 | Identity Pull | 3 | x1.5 | 4.5 | Somewhat relevant to builders |
| 8 | Clipability | 2 | x1 | 2 | No natural moments promised |
| | **TOTAL** | | | **26.5** | |

**Hook: 48. Virality: 26.5. Repackaging triggered.**

### After Repackaging (High Viral Potential — Score 46/57.5)

**Strategies applied:** Time Constraint + Compare Against Original

**New title:** "We Had 2 Hours to Rebuild Bolt.new — Then We Tested Them Side by Side"
**New angle:** Can we recreate the core Bolt.new experience in a single session? We rebuilt it, then ran the same 5 prompts through both versions to see how close we got.

| # | Dimension | Raw | Weight | Weighted | What changed |
|---|-----------|-----|--------|----------|--------------|
| 1 | Instant Curiosity | 4 | x2 | 8 | Time pressure + comparison = "I need to see this" |
| 2 | Stakes | 4 | x1.5 | 6 | 2-hour clock + direct comparison = real tension |
| 3 | Novelty | 4 | x2 | 8 | Dual constraint (time + comparison) feels fresh |
| 4 | Visual Promise | 4 | x1.5 | 6 | Side-by-side + timer = instant thumbnail |
| 5 | Emotional Engine | 4 | x1.5 | 6 | Curiosity + challenge tension + anticipation |
| 6 | Shareability | 3 | x1.5 | 4.5 | "You need to see how close they got" |
| 7 | Identity Pull | 3 | x1.5 | 4.5 | Builders want to know what is behind Bolt |
| 8 | Clipability | 3 | x1 | 3 | Timer moments, comparison reveal, first working version |
| | **TOTAL** | | | **46** | |

Same idea. Same build. Completely different packaging. **26.5 to 46** — from weak to high viral potential.

---

## Common Scoring Mistakes to Avoid

1. **Scoring the idea, not the packaging.** If you catch yourself thinking "this is a great product to cover," you are scoring the hook, not the virality. Refocus on the title, angle, and framing.

2. **Inflating novelty because the product is novel.** A novel product with generic packaging ("We Built X") still scores low on novelty. Novelty measures the *framing*, not the subject.

3. **Giving high stakes just because there is a build.** Building something is not stakes. Stakes require consequences, constraints, or comparison. "We rebuilt X" = no stakes. "We had 90 minutes to rebuild X" = stakes.

4. **Confusing information with emotion.** "Here is how X works under the hood" is informative, not emotional. Emotion requires tension, surprise, curiosity gaps, or aspiration.

5. **Overscoring shareability.** Ask: would someone *actually* open their messaging app and send this link? Not "could they" — "would they." Most content is a 2-3 on shareability.

---

## Quick Reference: Hook Scoring vs Virality Scoring

| Aspect | Hook Scoring | Virality Scoring |
|--------|-------------|-----------------|
| **Evaluates** | The idea itself | The packaging of the idea |
| **Key question** | "Is this worth building?" | "Will this spread?" |
| **Max score** | 62.5 | 57.5 |
| **Dimensions** | Attention, Rebuildability, Teachability, Visual Payoff, Reveal Potential, Originality Safety, Audience Fit, Format Elasticity | Instant Curiosity, Stakes, Novelty, Visual Promise, Emotional Engine, Shareability, Identity Pull, Clipability |
| **When to use** | Before committing to cover an idea | After choosing the idea, when framing the content |
| **High score means** | This idea is worth our time | This presentation will reach people |
| **Low score means** | Skip this idea | Repackage this idea |
| **Low score action** | Drop the idea | NEVER drop — repackage instead (if hook is strong) |

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
