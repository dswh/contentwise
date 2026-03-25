# Thumbnail Prompt Templates — Collage Surrealism

These are the exact prompt templates. Fill every placeholder, then send to nano banana with `model_tier: "nb2"` (Gemini 3.1 Flash Image — 4K at Flash speed).

---

## Logo Compositing (Step 2 — after generating the thumbnail)

When the article features a specific product/tool, composite the logo AFTER generating the base thumbnail. Never try to bake the logo into the generation prompt — image generators can't render real logos accurately.

**Prompt for logo compositing step:**
```
Place the logo from the second image into the lower-right corner of the first image. The logo should be small (about 8-12% of frame width), slightly translucent at 70-80% opacity, with a soft glow or drop shadow matching the scene's accent color [PALETTE_PRIMARY]. Blend it naturally into the composition. Do not alter the rest of the image.
```

**nano banana call:**
- `mode`: "edit"
- `input_image_path_1`: the generated thumbnail from Step 1
- `input_image_path_2`: the logo file from `logos/` directory
- `prompt`: the compositing prompt above
- `model_tier`: "nb2"

**Available logos:** supabase_logo.png, linkedin_learning_logo.png, openai.svg, claude_logo.jpeg, gemini_logo.jpeg, openai_logo.png, n8n_logo.png, cursor_logo.png, gumloop_white_logo.jpeg, claude_cowork.png, lovable_logo.png, claude_code_logo.png

**When to skip:** If the article is about a concept/trend rather than a specific product, skip the logo. Not every thumbnail needs one.

---

## Style DNA (inject into every prompt)

Append this to every prompt, adapting colors per palette:

```
Style: high-contrast collage surrealism. Mix photography, classical engraving, and bold vector shapes. Saturated [PALETTE_PRIMARY] and [PALETTE_SECONDARY] color pops against [PALETTE_BG]. Halftone dot texture, risograph grain, paper texture overlays. Bold editorial composition — magazine cover energy, not subtle art. Ultra-readable at phone size. No text.
```

---

## Palette Reference

### Electric Teal
- Primary: turquoise (#00CED1)
- Secondary: mustard yellow (#E8A317)
- Background: black or off-white
- Texture: halftone dots in teal, newsprint grain

### Fire & Gold
- Primary: electric red (#FF2D2D)
- Secondary: mustard (#F5A623)
- Background: deep black
- Texture: risograph grain, bold red halftone

### Grape Soda
- Primary: deep purple (#7C3AED)
- Secondary: mint green (#6EE7B7)
- Background: white or cream (#FAFAF5)
- Texture: soft paper grain, vintage print feel

### Coral Punch
- Primary: coral (#FF6B6B)
- Secondary: teal (#20808D)
- Background: off-white (#FAFAF5)
- Texture: newsprint, editorial halftone

### Neon Garden
- Primary: mint green (#34D399)
- Secondary: electric pink (#FF69B4)
- Background: black
- Texture: organic noise, spore-like grain

### Monochrome Pop
- Primary: one saturated pop color (chosen per article)
- Secondary: black
- Background: white
- Texture: sharp halftone, high contrast

---

## Template 1: Statue Remix

**Use for:** AI + human collaboration, tool reviews, "AI is/isn't replacing X," human judgment pieces.

```
16:9 thumbnail. A classical Greek/Roman marble statue bust or figure, [STATUE_POSE], recolored in bold [PALETTE_PRIMARY] and [PALETTE_SECONDARY] duotone. The statue is wearing [MODERN_PROP] and interacting with [METAPHOR_OBJECT]. Background: large flat [PALETTE_BG] color block with [GEOMETRIC_SHAPE] in contrasting color behind the statue. Halftone dot texture overlay at 30% opacity. Bold cut-out style — the statue feels like a magazine clipping pasted onto the background. Risograph printing effect on edges. Composition: statue fills 60% of frame, off-center. Vibe: [MOOD] — irreverent, editorial, like a zine cover. No text.
```

**Placeholders:**
- [STATUE_POSE]: "in profile looking right" / "hand raised thoughtfully" / "looking down at something in its hands"
- [MODERN_PROP]: headphones, sunglasses, VR goggles, airpods, a smartwatch, a baseball cap worn backwards
- [METAPHOR_OBJECT]: the visual metaphor for the article's concept — a lobster claw, a chess piece, a golden key, a magnifying glass, a tiny rocket

---

## Template 2: Object Metaphor (Surreal Scale)

**Use for:** Concept pieces, tutorials, rebuilds, "here's what we found" — the workhorse template.

```
16:9 thumbnail. A single [METAPHOR_OBJECT] rendered at surreally oversized scale — [SIZE_CONTEXT]. Style: photographic realism on the object but placed against a bold flat [PALETTE_BG] background with [PALETTE_PRIMARY] geometric shapes and [PALETTE_SECONDARY] accents. The object casts a sharp dramatic shadow. Halftone texture on the shadow. A small [CONTRASTING_ELEMENT] placed near the object for scale contrast. Composition: object occupies 50-70% of frame, slightly off-center. Bold, punchy, editorial. Vibe: [MOOD]. No text.
```

**Placeholders:**
- [METAPHOR_OBJECT]: the weird Level 3 concept — "a cracked golden egg with a Post-it note inside" / "a massive vintage pressure gauge" / "a Swiss watch with code for gears"
- [SIZE_CONTEXT]: "filling most of the frame as if it's 6 feet tall" / "so large it breaks the edges of the frame"
- [CONTRASTING_ELEMENT]: something tiny that shows scale — "a miniature office chair" / "a tiny laptop" / "a small plant"

---

## Template 3: Split / Versus

**Use for:** Comparisons, audits, "X vs Y," "old way vs new way," tension between approaches.

```
16:9 thumbnail. The frame split vertically (or diagonally) into two contrasting halves. Left side: [LEFT_CONCEPT] rendered in [PALETTE_PRIMARY] tones with [LEFT_TEXTURE]. Right side: [RIGHT_CONCEPT] rendered in [PALETTE_SECONDARY] tones with [RIGHT_TEXTURE]. The split line is [SPLIT_STYLE]. Where the two halves meet, elements from each side bleed slightly into the other — a controlled collision. Background elements: halftone dots, geometric shapes, cut-out arrows or lines connecting elements across the divide. Vibe: [MOOD] — visual tension, the viewer's eye bounces between sides. No text.
```

**Placeholders:**
- [LEFT_CONCEPT]: one side of the comparison — "a polished chrome robot hand" / "a sleek modern building"
- [RIGHT_CONCEPT]: the other side — "a weathered human hand" / "a classical Greek temple"
- [SPLIT_STYLE]: "a jagged tear like ripped paper" / "a clean diagonal" / "a zigzag line" / "a bold colored stripe"
- [LEFT_TEXTURE] / [RIGHT_TEXTURE]: "smooth gradient" vs "halftone grain" / "clean vector" vs "vintage engraving"

---

## Template 4: Collage Board

**Use for:** Tool stacks, roundups, multi-concept pieces, "lessons learned" compilations.

```
16:9 thumbnail. An editorial collage arrangement on a [PALETTE_BG] background. Elements layered and overlapping at playful angles: [ELEMENT_1], [ELEMENT_2], [ELEMENT_3], connected by [CONNECTING_ELEMENT]. Each element has a different visual treatment — one is photographic, one is classical engraving style, one is bold flat vector. Halftone dots, paper tape strips, and risograph texture throughout. One element is significantly larger than the others, creating hierarchy. Small geometric shapes (circles, triangles) scattered as accents in [PALETTE_PRIMARY] and [PALETTE_SECONDARY]. Composition: controlled chaos — busy but composed, like a designer's mood board. Vibe: [MOOD]. No text.
```

**Placeholders:**
- [ELEMENT_1/2/3]: 3-4 visual objects that represent the article's key concepts
- [CONNECTING_ELEMENT]: "hand-drawn arrows" / "dotted lines" / "a flowing ribbon" / "electrical wire illustrations"

---

## Template 5: Hero Landscape (Surreal)

**Use for:** Big-picture takes, paradigm shifts, journey pieces, "the landscape is changing."

```
16:9 thumbnail. A surreal landscape scene combining photography and illustration. [LANDSCAPE_BASE] stretching to the horizon, but with [SURREAL_ELEMENT] that makes it dreamlike and impossible. The sky is a bold flat [PALETTE_PRIMARY] with [SKY_DETAIL]. In the midground: [FOCAL_OBJECT] — rendered in contrasting [PALETTE_SECONDARY], sharply defined, the eye goes here first. Classical engraving-style clouds or flora mixed with geometric vector shapes. Halftone grain on the landscape, clean bold color on the focal object. Vibe: [MOOD] — epic but playful, surreal but grounded. No text.
```

**Placeholders:**
- [LANDSCAPE_BASE]: "a vast desert" / "rolling green hills" / "a calm ocean" / "a city seen from above"
- [SURREAL_ELEMENT]: "the sand is made of tiny keyboard keys" / "the hills are circuit boards covered in moss" / "the ocean waves are made of paper pages"
- [FOCAL_OBJECT]: the article's central metaphor placed in this landscape

---

## Concept Examples (Level 3 — Fun, Weird, Magnetic)

**Article:** "GPT-5.4 — OpenAI is Back"
- Emotional core: The comeback kid. They were down and now they're swinging.
- Palette: **Fire & Gold** (comeback energy, bold confidence)
- Template: **Statue Remix**
- Concept: A classical Greek boxer statue, muscles tensed, recolored in electric red and gold duotone, wearing modern boxing gloves. One glove is raised in victory. Behind: a massive gold circle like a rising sun. Halftone texture. The statue has a fresh black eye but is grinning.

**Article:** "We rebuilt today's #1 Product Hunt launch"
- Emotional core: Cracking something open to see how it works
- Palette: **Electric Teal**
- Template: **Object Metaphor**
- Concept: A gorgeous golden Fabergé egg cracked open at surreal scale, revealing tiny clockwork gears and springs inside — but one gear is replaced by a teal cursor arrow. The egg sits on a black background with bold teal geometric shapes behind it.

**Article:** "Is this viral product hype or real?"
- Emotional core: Peeling back the performance
- Palette: **Coral Punch**
- Template: **Split / Versus**
- Concept: Left half: a gleaming polished gold mask, smooth, perfect, lit beautifully. Right half: the same mask flipped to show the rough unpainted inside — scratches, seams, hot glue. Split by a jagged paper-tear line. Coral and teal halftone textures.

**Article:** "90-minute rebuild challenge"
- Emotional core: Adrenaline, controlled chaos, racing yourself
- Palette: **Fire & Gold**
- Template: **Object Metaphor**
- Concept: A massive vintage kitchen timer at surreal scale (filling 70% of frame), the dial cranked to 90, vibrating with motion blur lines. The timer is classic red and chrome, sitting on a black background with bold mustard yellow geometric speed lines radiating outward.

**Article:** "What 10 viral AI products had in common"
- Emotional core: Finding the pattern, the aha moment
- Palette: **Grape Soda**
- Template: **Collage Board**
- Concept: A mood board arrangement — 10 small objects (a key, a magnet, a mirror, a spark, a bridge, a mask, a clock, a seed, a lens, a thread) overlapping at angles on a cream background, connected by hand-drawn purple arrows, one object (the thread) highlighted in mint green and pulling through all the others.

**Article:** "Open-source alternative to a popular AI product"
- Emotional core: Empowerment, anyone can build this
- Palette: **Neon Garden**
- Template: **Hero Landscape**
- Concept: A surreal garden scene where mint-green plants grow through and over the skeleton of an abandoned chrome machine. The plants are lush and alive, the machine is geometric and rusted. Pink flowers bloom from the exhaust pipes. Black background with scattered green geometric shapes.
