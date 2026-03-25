---
name: thumbnail-creator
description: "Creates newsletter thumbnail images using the nano banana MCP. Analyzes the newsletter topic, picks the right visual concept and metaphor, selects the best template, fills all placeholders, and generates a 16:9 abstract thumbnail. Trigger on 'create thumbnail', 'generate thumbnail', 'newsletter thumbnail', 'make a thumbnail for this issue', 'hero image for the newsletter', or whenever a newsletter draft is ready and needs a thumbnail. Also trigger when someone says 'I need an image for this post' or describes a newsletter topic and wants a visual. This skill handles concept extraction — the user does NOT need to describe the visual, just the topic."
---

# Thumbnail Creator for Newsletters

You create abstract, editorial-quality 16:9 thumbnails for newsletter issues. The user gives you a topic, newsletter draft, or description — you figure out the right visual concept, pick the best template, fill every placeholder, and generate the image using the `mcp__nanobanana__generate_image` tool.

The thumbnails should feel like premium editorial art — abstract, high-contrast, minimal. No text. No clutter. One focal subject that captures the concept at a glance.

## What to Provide

To get the best thumbnail, provide any of the following:
- **A newsletter draft** — the skill will extract the concept from the content
- **A topic + angle** — e.g., "This issue is about rebuilding a viral AI coding assistant, the reveal was that the hard part was docs parsing not AI"
- **A hook score or pillar** — if available, helps pick the right template
- **Brand preferences** — if you have specific colors or style preferences (otherwise defaults are used)

You do NOT need to describe the visual. The skill's job is to translate your topic into the right visual metaphor.

---

## Brand Defaults

These are the defaults. Override any of them if the user specifies preferences.

- **Primary Color:** deep navy (#0A1628)
- **Accent Color:** electric amber (#F59E0B)
- **Neutral:** warm gray (#D4D0C8)
- **Brand Style:** "retro collage meets futuristic blueprint"
- **Mood:** confident, analytical, slightly rebellious
- **Negative prompt:** "text, watermark, words, letters, typography, logo, blurry, low quality, stock photo feel, generic, clipart, cartoon, anime"

---

## The Process

### Step 1: Extract the Concept

Read whatever the user provides (draft, topic, description) and identify:

1. **TOPIC** — the core concept in 2-4 words
2. **TOOL/TECH** — the primary technology involved
3. **THE WEIRD ANGLE** — this is the creative heart and the hardest part. See the Weirdness Engine below.
4. **MOOD** — the emotional tone

### The Weirdness Engine

The thumbnail's job is to stop the scroll. A "brain with circuits" or a "glowing orb" will never do that — those are the first things anyone would think of, which means they're invisible. Your concept needs to make someone's brain glitch for a split second: "Wait, what IS that? Why is it making me feel something?"

**The 3-step concept escalation:**

For every topic, generate three concept levels. Always use Level 3.

**Level 1 (obvious — never use this):** The literal metaphor. Brain = intelligence. Hourglass = time. Gears = engineering. These are clip art thinking. Skip entirely.

**Level 2 (abstract — still not enough):** One creative leap. Brain in a protective sphere. Hourglass with gears inside. These are better but still predictable. You'd see them in a Medium article.

**Level 3 (weird + magnetic — use this):** Cross-domain collision. Take the emotional core of the article and smash it into something from a completely unrelated world. The result should feel wrong at first glance but deeply right on reflection. This is what stops the scroll.

**How to reach Level 3 — the collision technique:**

1. Identify the EMOTIONAL CORE (not the topic, the feeling): "relief from cognitive overload" not "AI agent for productivity"
2. Ask: "What physical experience in the real world creates this exact feeling?" — a deep breath after being underwater, removing a heavy backpack, silence after noise, the first bite of food when starving
3. COLLIDE that physical experience with a tech/abstract element from the article — render the physical feeling, not the tech concept

**Level 3 examples:**

| Article Topic | Emotional Core | Physical Feeling | Level 3 Concept |
|--------------|---------------|-----------------|-----------------|
| AI agent that saves mental energy | Relief from cognitive drain | Removing a diving helmet after being underwater | A vintage deep-sea diving helmet sitting on a desk surrounded by calm amber light, the glass fogged from the inside, a single breath of mist escaping — as if the person just took it off and can finally breathe |
| Rebuilding a viral product | The thrill of cracking something open | A surgeon's first incision revealing something unexpected | A polished consumer product split open like a geode — the outside is sleek and glossy, the inside reveals raw crystal formations in amber and navy, geological layers where you expected circuits |
| Hype audit — is this product real? | Skepticism piercing through performance | Pulling back a stage curtain | A magician's top hat on a spotlight-lit table, but instead of a rabbit, a single raw circuit board is being pulled out — the glamour meets the mundane |
| 90-minute rebuild challenge | Pressure, adrenaline, ticking clock | A kettle about to whistle | A massive industrial pressure gauge with the needle in the red zone, but the gauge face shows tiny app icons instead of numbers, and a single crack in the glass with amber light leaking through |
| The magic was just orchestration | Disappointed awe, pulling back the wizard's curtain | Finding out a magic trick's simple mechanism | A beautiful marionette puppet of a robot, but the camera angle reveals the simple wooden cross controller above — just two sticks and four strings making something look alive |

**Concept quality test:** Before proceeding, ask yourself:
- Would someone screenshot this thumbnail and send it to a friend even without reading the article? If not, push weirder.
- Could you describe this image at a dinner party and get a reaction? If it sounds boring when described aloud, it'll be invisible in a feed.
- Does it feel slightly uncomfortable or uncanny? Good. That's what stops scrolling.
- Is it from a domain completely unrelated to tech? (diving, geology, cooking, theater, surgery, botany, astronomy) — cross-domain collisions are what make thumbnails magnetic.

### Step 2: Select the Template

Choose the template that best fits the content:

| Template | Best For | When to Pick |
|----------|----------|--------------|
| **Object Metaphor** | Tools, tutorials, frameworks, rebuilds | The concept has one clear central metaphor. Most common choice. |
| **Neoclassical Hero** | AI + human collaboration, writing, decision-making | The piece is about a PERSON using AI, or human judgment in AI contexts. |
| **Duotone Portrait** | Interviews, opinion pieces, personal experience | The piece has a strong personal perspective or "from the trenches" angle. |
| **Blueprint/Engineering** | Architecture, systems design, workflows, reverse engineering | The piece is about HOW something works under the hood. |
| **App Grid Series** | Tool stacks, multi-tool roundups, productivity setups | The piece covers multiple tools or a technology stack. |

**Default choice:** If unsure, go with **Object Metaphor** — it's the most versatile and works for the majority of newsletter content.

**For the "We rebuilt X" newsletter format:** Alternate between Object Metaphor (for the concept) and Blueprint/Engineering (for the technical angle). Use Neoclassical Hero sparingly for pieces where the human-vs-AI tension is the main story.

### Step 3: Fill the Template

Take the extracted concept and fill every placeholder in the chosen template. Read `references/templates.md` for the exact prompt templates.

**Placeholder filling rules:**
- **[TOPIC]** — Use the 2-4 word concept from Step 1
- **[TOOL/TECH]** — The specific technology. If multiple, pick the most visually interesting one
- **[KEY SYMBOL]** — The metaphor from Step 1. Be specific: not "technology" but "a single glowing circuit board with one pathway highlighted in amber"
- **[BRAND STYLE]** — Use the brand default unless user overrides
- **[PRIMARY COLOR] + [ACCENT COLOR]** — Use brand defaults unless user overrides
- **[MOOD]** — From Step 1 extraction
- **[ROLE]** — (Template 2 only) Pick the archetype: engineer, architect, analyst, builder
- **[MODERN PROP]** — (Template 2 only) Something that bridges classical and modern: headphones, VR goggles, holographic display
- **[PERSON/ARCHETYPE]** — (Template 3 only) The perspective: "a focused engineer", "a skeptical analyst", "a determined builder"

### Step 4: Enhance the Prompt

Before sending to nano banana, enhance the filled template:

1. **Add specificity to the key symbol** — "chess piece" becomes "a single obsidian chess knight, dramatically lit from below, casting a long amber shadow"
2. **Add atmosphere details** — "subtle dust particles in the light", "faint grid lines in the background", "soft bokeh in the periphery"
3. **Add the negative prompt** to prevent text and clutter
4. **Keep it under 300 words** — nano banana works best with focused prompts, not novels

### Step 5: Generate

Call `mcp__nanobanana__generate_image` with:
- `prompt`: your enhanced, filled template
- `aspect_ratio`: "16:9"
- `negative_prompt`: "text, watermark, words, letters, typography, logo, blurry, low quality, stock photo feel, generic, clipart, cartoon, anime, busy background, multiple focal points, collage of many items"
- `model_tier`: "pro" (for best quality on editorial thumbnails)
- `output_path`: save to the current working directory or a path the user specifies
- `n`: 1 (generate one image; offer to regenerate with a different template if the user wants alternatives)

### Step 6: Present and Iterate

Show the user:
1. The generated image
2. Which template you chose and why
3. The concept extraction (topic, symbol, mood)
4. The full prompt you used

If the user wants changes:
- "Too busy" → simplify the key symbol, reduce background elements
- "Wrong vibe" → adjust the mood and brand style
- "Try a different angle" → re-extract the concept with a different metaphor
- "Try another template" → switch templates and regenerate

---

## Concept Extraction Examples (Level 3 — Weird + Magnetic)

**Topic:** "We rebuilt a viral AI coding assistant"
- Emotional core: the thrill of opening something up and seeing how it ticks
- Physical feeling: a watchmaker opening a beautiful timepiece
- CONCEPT: A pristine Swiss watch face, but when you look through the crystal, the movement inside is made of tiny glowing code blocks and API calls instead of gears — one ruby jewel bearing is replaced by an amber LED
- Template: Object Metaphor
- MOOD: obsessive precision, the beauty of mechanism

**Topic:** "The hardest part wasn't the AI, it was parsing messy API docs"
- Emotional core: the mundane thing was actually the monster
- Physical feeling: stepping on a Lego in the dark
- CONCEPT: An enormous, menacing ball of tangled fishing line sitting on a pristine lab bench, casting a shadow shaped like a simple arrow pointing right — the chaos IS the obstacle, the solution is embarrassingly simple once you untangle it
- Template: Object Metaphor
- MOOD: darkly funny, the horror of the mundane

**Topic:** "Hype audit — is this viral product actually hard to build?"
- Emotional core: peeling back performance to find the truth
- Physical feeling: biting into a beautiful chocolate and finding it hollow
- CONCEPT: A gorgeous, ornate Fabergé egg cracked open on a velvet surface — but inside, instead of jeweled treasure, there's just a single Post-it note with a smiley face. Lit dramatically with amber rim lighting.
- Template: Object Metaphor
- MOOD: theatrical disappointment, wry humor

**Topic:** "We had 90 minutes to rebuild this Product Hunt launch"
- Emotional core: controlled panic, racing against yourself
- Physical feeling: a chef plating a dish as the ticket printer screams
- CONCEPT: A chef's hands in motion blur, plating an elaborate dish — but the plate is a laptop screen, the garnish tweezers hold a single line of code, and a ticket printer in the background spits out error logs. Shot from directly above, overhead kitchen-cam style.
- Template: Object Metaphor
- MOOD: kinetic urgency, beautiful chaos

**Topic:** "Our open-source stack for AI product building"
- Emotional core: pride in your toolkit, the craftsperson's workbench
- Physical feeling: a carpenter's wall of perfectly organized hand tools
- CONCEPT: A Japanese woodworker's tool wall — every chisel, plane, and saw in its exact place, backlit in amber — but the tools are subtly wrong: one chisel blade is a cursor, one saw has pixel teeth, one plane has a terminal prompt on its sole
- Template: Object Metaphor
- MOOD: quiet mastery, analog warmth with digital undercurrent

---

## Important Principles

- **Abstract over literal.** Never generate a screenshot of an app or a realistic photo of someone coding. Think editorial illustration — the kind of image a premium magazine would use.
- **One focal subject.** The thumbnail must read at phone size. One dominant element, not a collage.
- **No text in the image.** The newsletter's subject line handles the words. The thumbnail handles the feeling.
- **The metaphor IS the skill.** Anyone can type "generate a thumbnail." Your value is in translating "we rebuilt a viral product and the hard part was docs parsing" into "a crystal prism refracting chaos into clean light." That translation is the creative work.
- **Brand consistency.** Deep navy + electric amber + grain texture + cinematic lighting should make every thumbnail feel like it belongs to the same publication, even though the subjects vary.

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
