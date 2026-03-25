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

Thumbnails use **high-contrast, saturated color pops** against bold backgrounds (black, white, or a dominant color). Each palette pairs 2-3 punchy colors. Rotate across issues for variety.

| Palette | Primary Pop | Secondary | Background | Best For | Vibe |
|---------|------------|-----------|------------|----------|------|
| **Electric Teal** | Turquoise (#00CED1) | Mustard yellow (#E8A317) | Black or off-white | Speed, discovery, exploration | Fresh, energetic |
| **Fire & Gold** | Electric red (#FF2D2D) | Mustard (#F5A623) | Deep black | Launches, power, competition, comebacks | Bold, confident |
| **Grape Soda** | Deep purple (#7C3AED) | Mint green (#6EE7B7) | White or cream | Vision pieces, future thinking, big ideas | Playful, imaginative |
| **Coral Punch** | Coral (#FF6B6B) | Teal (#20808D) | Off-white (#FAFAF5) | Critiques, audits, honest takes | Sharp, editorial |
| **Neon Garden** | Mint green (#34D399) | Electric pink (#FF69B4) | Black | Open source, building, community | Alive, organic |
| **Monochrome Pop** | One saturated pop color | Black | White | Technical deep-dives, precision, architecture | Clean, striking |

**Rotation rule:** Never repeat the same palette two issues in a row. Alternate warm and cool dominants.

**The key:** Colors should POP. These thumbnails should look punchy at phone size in a crowded feed — not subtle, not muted, not dark-and-moody. Think magazine cover, not art gallery.

---

## The Visual System: Collage Surrealism

The aesthetic is **high-contrast collage surrealism** — mixing photography, classical engravings/sculpture, and bold vector shapes to create an "idea" rather than a literal image. Read `references/templates.md` for exact prompt templates.

### Core Aesthetic

1. **Collage + mixed media.** Combine real photography with classical engravings, halftone textures, bold geometric shapes, and hand-drawn elements in the same frame. The clash of styles IS the style.
2. **High contrast, saturated pops.** Colors should be bold and unapologetic — teal, electric red, mustard yellow, purple, mint green. Pair them with black or white for maximum punch. No muddy midtones.
3. **Indian classical sculpture + modern props.** Indian classical sculptures (Chola bronzes, Khajuraho sandstone, Gandhara style) wearing headphones, holding smartphones, interacting with floating UI elements. The collision of ancient and digital is the signature move.
4. **Visual metaphor > literal.** Never show the actual thing. Show what the thing FEELS like. "AI agent" → puppet master strings. "Planning" → chess pieces on a calendar. "Speed" → a cheetah skeleton in a wind tunnel. "Hype audit" → a golden mask being peeled off.
5. **Bold shapes and framing.** Large geometric blocks of color, cut-out silhouettes, oversized objects that break the frame. Think poster design, not photography.
6. **Texture layers.** Halftone dot patterns, paper grain, risograph printing effects, newsprint textures. These add editorial warmth and prevent the "AI-generated" look.

### What This IS

- Collage zine meets editorial magazine
- Classical art remixed with tech concepts
- Surrealist visual metaphors that make you laugh or go "wait, what?"
- Bold, fun, slightly irreverent
- The kind of image someone would put on a sticker

### What This Is NOT

- Dark moody atmospheric landscapes
- Flat corporate design or UI mockups
- Photorealistic people or faces
- Literal screenshots or product demos
- Generic "AI brain" or "glowing circuit" imagery
- Subtle or muted — if it doesn't pop at thumbnail size, it fails

---

## Step 1: Extract the Concept

### The Weirdness Engine

The thumbnail's job is to stop the scroll. Your concept needs to make someone's brain glitch: "Wait, what IS that?"

**The collision technique — always use this:**

1. **Identify the EMOTIONAL CORE** (the feeling, not the topic): "the tension between good-enough-fast vs best-but-slow" not "AI model comparison"
2. **Find the physical analog** — what experience in the real world creates this exact feeling? Racing on a narrow track while a highway blazes in the distance. A pocket knife vs a chef's knife. A sprinter vs a marathon runner.
3. **Render it in the Perplexity aesthetic** — take that physical concept and place it in a dark atmospheric landscape with glass objects, light trails, and nature-digital fusion.

**Concept quality test:**
- **Visual hook:** The image needs ONE element that grabs the eye and won't let go — a cracked golden egg, a statue wearing airpods, a giant kitchen timer with app icons for numbers. If you can't point to the single "wait, what?" element, the concept isn't done yet.
- Would someone screenshot this and send it to a friend without context? If not, push weirder.
- Is the concept from a domain unrelated to tech? Good — cross-domain collisions are what stop scrolling.
- Does it capture the article's FEELING, not just its TOPIC? A piece about "fast but not frontier" should feel like speed-with-limits, not like "AI model."
- Is it FUN? These thumbnails should make people smile or do a double-take — not nod respectfully. Irreverence > elegance.

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
- `negative_prompt`: "text, watermark, words, letters, typography, logo, blurry, low quality, stock photo, generic, clipart, cartoon, anime, bright white background, flat design, UI mockup, realistic human face, neon grid, generic AI brain, circuit board cliche, scattered geometric shapes, floating circles, floating rectangles, floating triangles, decorative confetti, sprinkled shapes"
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
