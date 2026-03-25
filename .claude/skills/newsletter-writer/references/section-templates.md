# Section Templates — Newsletter Writer

Detailed templates and example content for each of the 10 newsletter sections plus subject line. The SKILL.md file describes what each section achieves; this file shows HOW to write each one.

---

## Subject Line

### Template
```
[Action verb] + [Specific trending object] + [Implicit challenge or discovery]
```

### Example Subject Lines
- "We Rebuilt Today's #1 Product Hunt Launch"
- "This AI Demo Went Viral. Here's How We'd Build It"
- "We Tried to Recreate a Trending GitHub Project"
- "The Real Trick Behind This Viral AI Product"
- "Can Claude Code Rebuild This?"
- "This GitHub Repo Has 12K Stars. We Tested the Hype."
- "We Reverse Engineered a Trending AI Agent Framework"
- "We Had 90 Minutes to Rebuild This AI Product"

### Anti-Patterns (never do these)
- "Newsletter Issue #14: Rebuilding Cool AI Tools"
- "This Week in AI Rebuilds"
- "Our Latest Build Challenge"
- "Weekly AI Product Teardown"

### Decision Test
Read the subject line out loud. Does it sound like something you would text to a friend who builds things? If it sounds like a corporate email subject, rewrite it.

---

## Section 1: Opening Hook

### Template
```
[What happened — one sentence establishing the trending object]
[Why it matters — one sentence on the signal/scale]
[The challenge — one sentence on what you are doing about it]
```

### Length
3-5 lines. Absolute maximum. This is a cold open.

### Example — Good
> A GitHub repo called AutoAgent hit 8,000 stars in 72 hours. It claims to turn any API documentation into a working AI agent with a single prompt. We gave ourselves two hours to rebuild the core loop and find out what is actually going on under the hood.

### Example — Bad
> Hey everyone! Welcome back to another issue of our newsletter. This week, we found a really interesting GitHub repository that has been getting a lot of attention lately. It's called AutoAgent and it does some cool things with AI agents. We decided to take a closer look and try to rebuild it. Here's what happened.

### Why the Good Version Works
- Starts with the object, not with "welcome back"
- Includes a specific number (8,000 stars, 72 hours)
- States the claim that creates skepticism/curiosity
- Sets up the challenge with a constraint (two hours)
- Reader knows exactly what this issue is about by line 3

---

## Section 2: The Object

### Template
```
**[Product/Repo/Demo Name]**

| | |
|---|---|
| **Source** | [Product Hunt / GitHub / Show HN / X] |
| **Discovered** | [Date or "trending since..."] |
| **What it does** | [One-line value proposition] |
| **Why it's trending** | [1-2 sentences — the hook that made people notice] |
| **Signal snapshot** | [Stars/upvotes/engagement + timeframe] |

[VISUAL: hero screenshot of [product name] showing [specific view]]
[VISUAL: signal card — [specific metrics, e.g., "8,247 GitHub stars, 1,200 forks, trending #1 in Python"]]
```

### Example
```
**AutoAgent**

| | |
|---|---|
| **Source** | GitHub Trending |
| **Discovered** | Trending since March 18 |
| **What it does** | Turns API docs into working AI agents with one prompt |
| **Why it's trending** | The demo video shows a user pasting Stripe's API docs and getting a working payment agent in under a minute. That video has 2.1M views on X. |
| **Signal snapshot** | 8,247 stars, 1,200 forks in 5 days. Trending #1 in Python. |

[VISUAL: hero screenshot of AutoAgent's GitHub repo page with star count visible]
[VISUAL: signal card showing 8,247 stars, 1,200 forks, 5-day growth curve]
```

### Notes
- Keep this section factual — no opinion yet
- The signal snapshot should use real numbers, not "a lot of engagement"
- If the trending source is X/Twitter, include the specific post metrics

---

## Section 3: Why It Worked

### Template
```
### What Users Saw
[2-3 sentences on the surface-level experience. What did the demo show? What did the landing page promise? What was the first impression?]

[VISUAL: annotated screenshot of [specific UI element or demo moment] with callouts highlighting [specific interaction points]]

### What Made It Feel Magical
[2-3 sentences on the moment of delight or surprise. What was the "wait, really?" moment? What felt impossibly smooth or fast?]

### What Probably Drove the Virality
[2-3 sentences on the sharing mechanics. Why did people retweet/upvote/star this? What identity signal did sharing it send? What emotion drove the spread?]

[VISUAL: magic breakdown diagram showing [surface experience] -> [perceived magic] -> [sharing trigger]]
```

### Example
```
### What Users Saw
The demo video is 47 seconds. A user pastes Stripe's API documentation URL, types "build me a payment agent," and watches as the tool generates a complete agent with error handling, retry logic, and a test suite. The agent runs successfully on the first try.

[VISUAL: annotated screenshot of AutoAgent's demo — arrows pointing to (1) the URL input, (2) the single prompt, (3) the generated agent code, (4) the successful test output]

### What Made It Feel Magical
The speed. From URL to working agent in under 60 seconds with zero configuration. No schema definitions, no tool descriptions, no prompt engineering. Just a URL and a sentence. The test suite running green on the first try seals it — this looks like it "just works."

### What Probably Drove the Virality
Every developer who has spent hours writing agent tool definitions saw this and thought "wait, that entire step is automated now?" The share trigger is competence aspiration — forwarding this says "I found the shortcut before everyone else." The 47-second demo format is also perfectly clippable.

[VISUAL: virality breakdown — "speed of demo" + "solves known pain point" + "clippable format" = sharing trigger]
```

### Notes
- Each subsection should reveal something the reader did not already think of
- "What probably drove the virality" is your analysis, not just restating that it went viral
- The annotated screenshot is a MUST-HAVE visual for this section

---

## Section 4: The Rebuild Brief

### Template
```
[VISUAL: build brief card with the following fields]

**Objective:** [One sentence — what you are trying to rebuild]

**Constraints:**
- [Constraint 1 — e.g., time limit, tool restriction]
- [Constraint 2]
- [Constraint 3]

**Stack:**
- [Tool/framework 1]
- [Tool/framework 2]
- [API/model]

**Success looks like:** [1-2 sentences defining what "done" means]

**What we're ignoring:** [List of features/aspects you are deliberately skipping and WHY]
```

### Example
```
[VISUAL: build brief card — "Rebuild AutoAgent's core: API docs to working agent in one prompt"]

**Objective:** Rebuild the core loop — take an API documentation URL and generate a functional AI agent from a single natural language prompt.

**Constraints:**
- 2-hour time limit
- No peeking at AutoAgent's source code until after our first working attempt
- Must generate runnable code, not just pseudocode

**Stack:**
- Claude 3.5 Sonnet (for code generation)
- Python + httpx (for API calls)
- Claude Code (as the build environment)

**Success looks like:** Given a public API docs URL and a one-sentence prompt, our system generates an agent that can execute at least 3 API calls correctly without manual fixes.

**What we're ignoring:** The test suite generation (impressive but not the core value), the UI (we are building CLI-only), multi-API orchestration (the demo only shows single-API anyway).
```

### Notes
- "What we're ignoring" is critical — it shows you are thoughtful about scope, not just cutting corners
- Constraints should create tension — they make the build log more interesting
- Success criteria must be specific enough to evaluate in the comparison section

---

## Section 5: How We Think It Works

### Template
```
Before building, here is our best guess at how [product] actually works under the hood.

**Probable inputs:** [What the system takes in]

**Model/Workflow:** [What LLM or pipeline processes the input]

**Orchestration:** [How multiple steps are chained together]

**UX layer:** [What makes it feel smooth to the user]

**Hidden complexity:** [What is probably harder than it looks]

[VISUAL: architecture diagram showing [input] -> [processing steps] -> [output] with labeled components]
```

### Example
```
Before building, here is our best guess at how AutoAgent works under the hood.

**Probable inputs:** A URL pointing to API documentation + a natural language task description.

**Model/workflow:** The system likely (1) scrapes and parses the API docs into structured endpoint definitions, (2) feeds those definitions + the user prompt to a large context model, (3) generates agent code with tool definitions derived from the parsed endpoints.

**Orchestration:** Probably a two-pass system. First pass: extract API schema. Second pass: generate agent code using the schema as context. The demo speed suggests these run in sequence, not parallel.

**UX layer:** The "magic" is that users never see the intermediate schema extraction step. They give a URL, they get code. The parsing is invisible.

**Hidden complexity:** API documentation is wildly inconsistent. Stripe's docs are structured and excellent. Most API docs are not. Our bet: this works great on well-documented APIs and breaks on messy ones.

[VISUAL: architecture diagram — URL input -> Doc Parser (scrape + structure) -> Schema Extractor (endpoints, params, auth) -> Code Generator (LLM + schema context) -> Agent Code Output]
```

### Notes
- This is a HYPOTHESIS — be explicit that you might be wrong
- The "hidden complexity" section is often the most interesting part
- Compare your hypothesis to what you actually find in the build log

---

## Section 6: The Build Log

### Template
```
### Attempt 1: [Title describing the approach]
[What you tried, how you set it up, what happened]

[What broke or surprised you]

[VISUAL: screenshot of [specific state — error message, unexpected output, first attempt result]]

### Attempt 2: [Title describing the pivot]
[What you changed based on Attempt 1]

[What happened this time]

[VISUAL: screenshot showing [progress or new problem]]

### Attempt N: [Title — "The One That Worked" or similar]
[What finally clicked]

[The specific insight or change that made the difference]

[VISUAL: screenshot of working result]

[VISUAL: iteration gallery — side by side of Attempt 1 output, Attempt 2 output, final output]
```

### Example
```
### Attempt 1: The Naive Approach — Just Feed It the Docs
**Time: 0-25 minutes**

We started simple. Scrape the raw HTML from Stripe's API docs page, dump it into Claude's context window along with the prompt "build me a payment agent," and see what comes out.

The result was... a mess. The raw HTML included navigation elements, code samples in three languages, changelog entries, and marketing copy. Claude generated an agent, but it hallucinated endpoints that do not exist and mixed up parameter names from different API versions.

[VISUAL: screenshot of Attempt 1 output — highlighting the hallucinated endpoint names circled in red]

### Attempt 2: Parse First, Generate Second
**Time: 25-55 minutes**

Clearly, raw HTML is not the move. We built a docs parser that extracts just the endpoint definitions: URL pattern, method, required parameters, response schema. Fed THAT to Claude instead.

Night and day. The generated agent had correct endpoints and proper parameter names. But it failed on authentication — our parser grabbed the endpoint structure but missed the auth section entirely. The agent tried to call Stripe without an API key.

[VISUAL: side-by-side — Attempt 1 garbled output vs. Attempt 2 correct-structure-but-no-auth output]

### Attempt 3: The Auth Problem
**Time: 55-80 minutes**

We almost went down a rabbit hole building a generic auth detector. Then we realized: AutoAgent probably does not solve auth generically either. It likely just looks for common auth patterns (Bearer token, API key header, OAuth) and templates them in.

We added a simple pattern matcher for three auth styles. Took 10 minutes. The agent now authenticates correctly.

But the generated code had no error handling. Every API call was a bare request with no retry logic and no status code checking. The original AutoAgent demo showed clean error handling. Where does that come from?

### Attempt 4: The Template Insight
**Time: 80-105 minutes**

This is where it clicked. AutoAgent probably does not generate error handling from scratch each time. It almost certainly uses code templates — pre-written patterns for retry logic, error handling, and response parsing — and slots the API-specific details into those templates.

We built three templates (basic request, paginated request, webhook handler) and had Claude select and populate the right template for each endpoint. Suddenly our generated agents looked production-grade.

[VISUAL: iteration gallery — four screenshots showing progression from garbled Attempt 1 to clean final output]

**Total build time: 1 hour 45 minutes.**
```

### Critical Rules
- Every attempt needs a title that describes the APPROACH, not just "Attempt N"
- Include time markers — they create pacing and tension
- Name specific errors and tools — "Claude hallucinated endpoints" not "we got some errors"
- The pivot between attempts is the most important part — WHY did you change approach?
- Include at least one moment of "this is where it clicked" or "we almost went down a rabbit hole"
- End with total build time

---

## Section 7: Final Comparison

### Template
```
[VISUAL: side-by-side comparison — original [product] on left, our rebuild on right]

### What Matched
- [Specific feature/behavior that our rebuild replicated correctly]
- [Another match]

### What Didn't Match
- [Specific feature/behavior where the original was better and WHY]
- [Another gap]

### Harder Than Expected
[1-2 sentences on what you underestimated]

### Easier Than Expected
[1-2 sentences on what you overestimated]

[VISUAL: feature matrix — rows for key features, columns for Original / Rebuilt / Notes]
[VISUAL: scorecard — "Matched: X/Y features | Build time: Z | Hardest part: [thing]"]
```

### Example
```
[VISUAL: side-by-side — AutoAgent generating a Stripe agent (left) vs. our rebuild generating a Stripe agent (right)]

### What Matched
- **Core loop works.** Give it a URL and a prompt, get a working agent. Our version handles Stripe, GitHub, and OpenWeather APIs correctly.
- **Speed is comparable.** Our version generates in ~45 seconds vs. AutoAgent's ~30 seconds. The difference is likely their optimized parsing pipeline.
- **Code quality is similar.** Both produce agents with proper typing, docstrings, and structured error handling.

### What Didn't Match
- **Test suite generation.** AutoAgent generates a test suite alongside the agent. We skipped this (deliberately), but it is a genuine value-add, not just a demo gimmick.
- **Multi-API support.** AutoAgent can take multiple API docs and generate an agent that orchestrates across them. Our version is single-API only.
- **Edge case handling.** AutoAgent gracefully handles docs pages that require JavaScript rendering. Our parser chokes on SPAs.

### Harder Than Expected
The docs parsing. We assumed this was a solved problem — just scrape and extract. It is not. API documentation varies wildly in structure, and getting reliable endpoint extraction across different doc formats was the majority of our build time.

### Easier Than Expected
The code generation. Once we had clean, structured API schemas, Claude generated correct agent code on the first try nearly every time. The "AI magic" in this product is mostly about FEEDING the model clean data, not about clever prompting.

[VISUAL: feature matrix — Core Loop: YES/YES, Auth Handling: YES/YES, Test Generation: YES/NO (skipped), Multi-API: YES/NO (out of scope), SPA Docs: YES/NO]
[VISUAL: scorecard — "Matched: 3/5 core features | Build time: 1h 45m | Hardest part: docs parsing"]
```

---

## Section 8: The Real Lesson

### Template
```
**Lesson 1: [Sharp one-line insight]**
[2-3 sentences of context explaining why this matters beyond this specific build]

**Lesson 2: [Sharp one-line insight]**
[2-3 sentences of context]

**Lesson 3: [Sharp one-line insight]**
[2-3 sentences of context]

[Optional: Lessons 4-5 if genuinely valuable]

[VISUAL: lessons card — all lessons as a compact, shareable graphic]
```

### Example
```
**Lesson 1: The magic is in the data cleaning, not the AI.**
AutoAgent's secret is not a clever prompt or a fine-tuned model. It is a really good docs parser. The product that looks like "AI turns docs into agents" is actually "a parser turns messy docs into clean schemas, then AI does the easy part." If you are building AI tools, your competitive advantage is probably in the preprocessing, not the model call.

**Lesson 2: Code templates beat code generation.**
Generating error handling, retry logic, and response parsing from scratch every time is slow and unreliable. Using pre-built templates and letting the AI fill in the API-specific details is faster, more consistent, and produces better code. This is a pattern you can steal for any code generation tool.

**Lesson 3: Demo-friendly does not mean production-ready.**
AutoAgent's demo uses Stripe — one of the best-documented APIs in existence. Our rebuild works great on well-documented APIs and breaks on messy ones. The gap between "works on Stripe" and "works on any API" is enormous. When evaluating AI tools, always ask: how carefully was the demo's input chosen?

[VISUAL: lessons card — three lessons as a compact card with icons: (1) wrench icon "Magic = data cleaning", (2) template icon "Templates > generation", (3) warning icon "Demo input is cherry-picked"]
```

### Critical Rules
- Each lesson must be TRANSFERABLE — useful even if the reader never touches this specific product
- Never write "Lesson: We built it and it was cool"
- The one-line insight should be provocative enough to share on its own
- Context should answer "so what?" for someone building their own thing
- 3 lessons minimum, 5 maximum

---

## Section 9: Build Takeaway

### Template
```
### This Week's Takeaway: [Name of the asset]

[1-2 sentences on what this is and when to use it]

[The actual asset — prompt template, architecture, checklist, workflow, pattern]

[VISUAL: template preview card or cheat sheet showing the asset in a clean, saveable format]
```

### Example
```
### This Week's Takeaway: The API-to-Agent Pipeline Template

If you are building any tool that generates code from documentation, here is the three-stage pipeline that worked for us:

**Stage 1: Parse and Structure**
- Input: Raw documentation URL
- Process: Scrape -> extract endpoints -> normalize to schema (endpoint, method, params, auth, response format)
- Output: Structured JSON schema

**Stage 2: Template Selection**
- Match each endpoint to a code template (basic request, paginated, webhook, streaming)
- Templates include error handling, retry logic, and type hints pre-written

**Stage 3: Generate and Assemble**
- Feed structured schema + selected template to LLM
- Prompt: "Populate this template with the following API details: {schema}. Do not modify the error handling or retry logic."
- Assemble generated functions into a single agent file with imports and entry point

**When to use this:** Any time you are generating code that calls external APIs. Works for agent builders, SDK generators, and integration scaffolding tools.

[VISUAL: pipeline template as a one-page cheat sheet — three boxes with arrows: Parse -> Template -> Generate, with key details in each box]
```

### Notes
- The asset must be IMMEDIATELY usable — not "go read this repo"
- Prompt templates should be copy-pasteable
- Architecture patterns should be drawable on a whiteboard
- Checklists should be checkable

---

## Section 10: Next Week's Tease

### Template
```
**Next week:** [One sentence creating an open loop about the next issue]
```

### Example
```
**Next week:** A Hugging Face Space hit 50K users in 48 hours by doing something we have never seen in an AI demo. We are pulling it apart.
```

### Anti-Patterns
- "Next week we'll have another great issue!" (no open loop)
- "Stay tuned for more content!" (generic)
- "We haven't decided yet what to cover next." (breaks immersion)

### Rules
- Must be specific enough to create curiosity
- Must be vague enough that you have flexibility
- One sentence, two absolute max
- Should make the reader think "wait, what is it?"

---

## Full Issue Assembly Checklist

Before submitting the draft, verify:

- [ ] Subject line sounds like a mission, not a newsletter
- [ ] Opening hook is 3-5 lines, no greetings or preamble
- [ ] The Object has a complete profile card with real signal numbers
- [ ] Why It Worked has all three subsections with non-obvious analysis
- [ ] Rebuild Brief has objective, constraints, stack, success criteria, and "ignoring" list
- [ ] How We Think It Works is framed as a hypothesis
- [ ] Build Log shows real progression with failures, pivots, and timestamps
- [ ] Build Log has attempt titles that describe the approach
- [ ] Final Comparison has specific matches, gaps, harder/easier callouts
- [ ] Lessons are transferable (useful even without reading the full issue)
- [ ] Build Takeaway is a concrete, immediately usable asset
- [ ] Next Week's Tease creates a genuine open loop
- [ ] All 8 must-have visuals are marked inline with [VISUAL: ...] callouts
- [ ] Code appears ONLY when it teaches a specific decision (5-15 lines max)
- [ ] No section starts with "In this section..." or similar meta-commentary
- [ ] Voice is field report, not blog post — check for passive voice and vague generalities
- [ ] Core content test passes: strong hook, clear challenge, visible progress, satisfying comparison, transferable lesson
