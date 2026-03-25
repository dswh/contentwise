---
name: thumbnail-creator
description: "Creates newsletter thumbnail images using the nano banana MCP. Analyzes the newsletter topic, picks the right visual concept and metaphor, selects the best template, fills all placeholders, and generates a 16:9 abstract thumbnail. Trigger on 'create thumbnail', 'generate thumbnail', 'newsletter thumbnail', 'make a thumbnail for this issue', 'hero image for the newsletter', or whenever a newsletter draft is ready and needs a thumbnail. Also trigger when someone says 'I need an image for this post' or describes a newsletter topic and wants a visual. This skill handles concept extraction — the user does NOT need to describe the visual, just the topic."
---

# Thumbnail Creator for Newsletters

You create cinematic, editorial-quality 16:9 thumbnails inspired by Perplexity's blog aesthetic — dark atmospheric landscapes, 3D glass objects, nature-digital fusion, cosmic depth, and dreamlike compositions. The user gives you a topic or draft — you extract the concept, pick a color mood, choose a visual template, and generate the image using `mcp__nanobanana__generate_image`.

## What to Provide

- **A newsletter draft or article** — the skill extracts the concept from the content
- **A topic + angle** — e.g., "This issue is about a new AI model that's fast but not frontier"
- **Brand/tool context** — mention any specific tools so the skill can use logos from `logos/` directory
- **Color preference** (optional) — or let the skill pick from the rotating palette

You do NOT need to describe the visual. The skill translates your topic into the right concept.

---

## Logo Integration (2-Step Process)

Image generators cannot reliably render real logos. Instead, use a 2-step process:

**Step 1: Generate the thumbnail** without any logo — focus purely on the concept, palette, and atmosphere.

**Step 2: Composite the logo** by calling `mcp__nanobanana__generate_image` a second time in edit mode:
- `input_image_path_1`: the generated thumbnail from Step 1
- `input_image_path_2`: the relevant logo from `logos/` in this skill's directory
- `prompt`: "Place the logo from the second image subtly into the lower-right corner of the first image. The logo should be small (about 8-12% of frame width), slightly translucent at 70-80% opacity, with a soft glow matching the scene's accent color. Do not alter the rest of the image."
- `mode`: "edit"

Available logos: `supabase_logo.png`, `linkedin_learning_logo.png`, `openai.svg`, `claude_logo.jpeg`, `gemini_logo.jpeg`, `openai_logo.png`, `n8n_logo.png`, `cursor_logo.png`, `gumloop_white_logo.jpeg`, `claude_cowork.png`, `lovable_logo.png`, `claude_code_logo.png`

If the article doesn't focus on a specific product, skip the logo entirely — not every thumbnail needs one.

---

## The Rotating Color Palette

Every thumbnail uses a dark atmospheric base, but the accent color shifts to prevent visual monotony. Pick the palette that matches the article's emotional tone — not just the topic.

| Palette | Base | Accent | Glow | Best For | Emotional Tone |
|---------|------|--------|------|----------|----------------|
| **Teal Depths** | #091717 | #20808D | Turquoise aurora | Speed, search, discovery, exploration | Curiosity, possibility |
| **Amber Signal** | #0D0D0D | #F5A623 | Warm golden haze | Announcements, launches, power, authority | Confidence, warmth |
| **Coral Tension** | #1A0A0A | #FF6B6B | Red-pink atmospheric glow | Critiques, audits, comparisons, skepticism | Tension, honest assessment |
| **Violet Dream** | #0D0A1A | #A78BFA | Soft purple nebula | Vision pieces, future thinking, big ideas | Wonder, imagination |
| **Emerald Growth** | #0A1A0D | #34D399 | Green bioluminescence | Open source, community, building, growth | Organic energy, empowerment |
| **White Light** | #0D0D0D | #F0F0F0 | Cool white radiance | Technical deep-dives, architecture, precision | Clarity, sharp focus |

**Rotation rule:** Check the last 3 thumbnails generated (if the user mentions them or you have context). Avoid using the same palette twice in a row. If no context, pick based on emotional tone.

**Blending:** You can blend two palettes — e.g., Amber Signal base with a hint of Teal Depths in the atmosphere. This creates richer, more unique compositions.

---

## The Visual System (Perplexity-Inspired)

Every thumbnail shares these DNA traits. Read `references/templates.md` for the exact prompt templates.

### Core Aesthetic

1. **Dark atmospheric base** — always starts from darkness. Deep blacks, teal-blacks, or near-black with color. Never white or light backgrounds.
2. **Atmospheric depth** — haze, mist, aurora-like light streaks, particle effects. The image should feel like it has physical depth — foreground, midground, background layers.
3. **3D glass/crystal objects** — translucent spheres, hexagons, prisms, cubes that catch and refract light. These are the "hero objects" — they float, they glow, they feel tactile.
4. **Nature meets digital** — lush organic elements (moss, ferns, coral, clouds, water, rock formations) growing alongside or merging with digital wireframes, particle grids, light trails.
5. **Cinematic lighting** — always dramatic. Side-lit, rim-lit, backlit. Strong contrast. Light sources should feel motivated — a glow from within an object, light streaking from the horizon, bioluminescence.
6. **Subtle grain and texture** — slight film grain, chromatic aberration at edges, lens flare where light sources peak. Analog warmth in a digital composition.

### What This Is NOT

- Not flat design or UI mockups
- Not bright/white corporate tech aesthetics
- Not photorealistic people or faces
- Not literal screenshots or product demos
- Not generic "AI brain" or "glowing circuit" imagery

---

## Step 1: Extract the Concept

### The Weirdness Engine

The thumbnail's job is to stop the scroll. Your concept needs to make someone's brain glitch: "Wait, what IS that?"

**The collision technique — always use this:**

1. **Identify the EMOTIONAL CORE** (the feeling, not the topic): "the tension between good-enough-fast vs best-but-slow" not "AI model comparison"
2. **Find the physical analog** — what experience in the real world creates this exact feeling? Racing on a narrow track while a highway blazes in the distance. A pocket knife vs a chef's knife. A sprinter vs a marathon runner.
3. **Render it in the Perplexity aesthetic** — take that physical concept and place it in a dark atmospheric landscape with glass objects, light trails, and nature-digital fusion.

**Concept quality test:**
- Would someone screenshot this and send it to a friend without context? If not, push weirder.
- Is the concept from a domain unrelated to tech? Good — cross-domain collisions are what stop scrolling.
- Does it capture the article's FEELING, not just its TOPIC? A piece about "fast but not frontier" should feel like speed-with-limits, not like "AI model."

---

## Step 2: Pick the Palette

Match the emotional tone:

| Article Feeling | Palette |
|----------------|---------|
| "This is exciting / a big launch" | Amber Signal |
| "Let's investigate / is this real?" | Coral Tension |
| "Speed, discovery, exploration" | Teal Depths |
| "The future is changing" | Violet Dream |
| "Build it yourself / open source" | Emerald Growth |
| "Here's exactly how it works" | White Light |
| "Nuanced take / both sides" | Blend Coral + Amber |

---

## Step 3: Select the Template

Choose from the 5 templates in `references/templates.md`:

| Template | Visual Style | When to Pick |
|----------|-------------|--------------|
| **Floating Object** | A 3D glass/crystal object floating in atmospheric darkness, refracting light | The article has one clear central concept or metaphor |
| **Landscape Journey** | Dark terrain with a luminous path, atmospheric sky, cosmic depth | The article is about a journey, comparison, choice between paths, or progression |
| **Nature-Digital Fusion** | Organic growth (moss, coral, crystals) merging with wireframes and particle effects | The article is about building, growing, ecosystems, or organic + engineered tension |
| **Cosmic Vista** | Vast atmospheric sky with aurora/nebula, a lone figure or object in silhouette | The article has a grand theme — the future, a paradigm shift, a big-picture take |
| **Artifact Study** | A single beautiful object on a dark surface, dramatically lit, museum-like | Product review, model comparison, "what we found when we tested this" |

**Default:** Floating Object — most versatile.

---

## Step 4: Build the Prompt

Read `references/templates.md` for the exact template strings. Fill the placeholders:

- **[CONCEPT]** — The weird-angle metaphor from Step 1, described in vivid physical detail
- **[PALETTE]** — The chosen palette's base, accent, and glow colors
- **[ATMOSPHERE]** — Haze, particles, aurora, mist — what fills the space between objects
- **[LIGHTING]** — Where the light comes from and what it reveals
- **[MOOD]** — The emotional word (e.g., "tension," "serenity," "urgency," "wonder")

**Enhancement rules:**
1. Be hyper-specific with objects — "a translucent obsidian hexagon with internal amber veins" not "a geometric shape"
2. Describe the light physically — "warm amber light leaking through a crack" not "golden lighting"
3. Keep under 250 words — focused prompts generate better images
4. Always include the negative prompt

---

## Step 5: Generate

Call `mcp__nanobanana__generate_image` with:
- `prompt`: the filled, enhanced template
- `aspect_ratio`: "16:9"
- `negative_prompt`: "text, watermark, words, letters, typography, logo, blurry, low quality, stock photo, generic, clipart, cartoon, anime, bright white background, flat design, UI mockup, realistic human face, neon grid, generic AI brain, circuit board cliche"
- `model_tier`: "nb2" (Gemini 3.1 Flash Image — 4K at Flash speed, best balance of quality and speed for thumbnails)
- `output_path`: save to `thumbnails/` in the working directory or user-specified path
- `n`: 1
- Do NOT pass logos as input images at this step — logos are composited in a separate Step 6b (see Logo Integration above)

---

## Step 6: Present and Iterate

Show the user:
1. The generated image
2. Palette chosen + why
3. Template chosen + why
4. The emotional core → physical concept → prompt chain

If the user wants changes:
- "Too dark" → add more accent glow, brighten the atmosphere
- "Wrong color" → switch palette, regenerate
- "Concept doesn't match" → re-extract with a different emotional core
- "Too similar to last one" → force a different palette + template combo

---

## Important Principles

- **Dark atmospheric base, always.** This is the visual signature. Light comes from within, not from above.
- **Color variety across issues.** Rotate palettes. A teal thumbnail followed by another teal thumbnail feels like the same article. Alternate warmth and coolness.
- **The concept maps to the article's feeling, not its topic.** A piece about "AI model benchmarks" could feel like a horse race (Coral Tension) or a precision instrument (White Light) or a vast landscape of possibilities (Violet Dream). The feeling determines the visual.
- **Logo integration should be subtle.** The logo is a supporting element — a reflection in glass, a small floating element in the background, a texture. Never the focal point.
- **One focal composition.** Must read at phone size. One dominant visual element, atmospheric layers for depth, nothing competing for attention.
- **No text in the image.** The title handles words. The thumbnail handles feeling.

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
