# OpenClaw — Visual Prompting Skill: Master Instruction Set

> **Version:** 1.0
> **Purpose:** Step-by-step instructions for an AI agent to generate professional-quality images and videos for any ecommerce use case — product photography, website banners, Meta ads, video ads, social content, and more. This skill teaches you HOW to prompt, what to prompt, and how to iterate until the output is professional-grade.

---

## Table of Contents

1. [Phase 0: Understand the Request](#phase-0-understand-the-request)
2. [Phase 1: Visual Research & Competitor Intelligence](#phase-1-visual-research--competitor-intelligence)
3. [Phase 2: The Prompt Architecture (How Every Prompt Works)](#phase-2-the-prompt-architecture)
4. [Phase 3: Product Photography Prompts](#phase-3-product-photography-prompts)
5. [Phase 4: Website Asset Prompts](#phase-4-website-asset-prompts)
6. [Phase 5: Meta Static Ad Prompts](#phase-5-meta-static-ad-prompts)
7. [Phase 6: Meta Video Ad Prompts](#phase-6-meta-video-ad-prompts)
8. [Phase 7: Iteration & Refinement Framework](#phase-7-iteration--refinement-framework)
9. [Phase 8: Export Specs & Platform Requirements](#phase-8-export-specs--platform-requirements)
10. [Appendix A: Prompt Modifier Library](#appendix-a-prompt-modifier-library)
11. [Appendix B: Negative Prompt Library](#appendix-b-negative-prompt-library)
12. [Appendix C: Tool-Specific Syntax Guide](#appendix-c-tool-specific-syntax-guide)

---

## How to Use This Skill

This skill is loaded ON-DEMAND, not on every session start (it's large). Load specific phases as needed:

- User wants product photos? → Load Phase 3
- User wants website banners? → Load Phase 4
- User wants Meta ads? → Load Phase 5 + Phase 1 (competitor research)
- User wants video ads? → Load Phase 6
- User struggling with prompts? → Load Phase 2 (architecture) + Phase 7 (iteration)
- User says "make it look like [competitor]"? → Load Phase 1 first

**Web Research:** When you need to research competitors, trends, or references, use Perplexity web search (the user has the API key integrated). Use it for competitor ad lookups, visual trend research, and finding reference images.

---

## Phase 0: Understand the Request

Before writing a single prompt, you MUST classify what the user is asking for. Different visual outputs require completely different prompt strategies.

### Step 0.1 — Identify the Visual Type

Ask or infer which category this falls into:

| Category | Examples | Key Requirement |
|----------|----------|-----------------|
| **Product Photography** | Hero shots, lifestyle shots, flat-lays, detail close-ups, multi-angle, unboxing | Product accuracy — the generated image must look like the REAL product |
| **Website Assets** | Homepage hero banners, collection headers, about page imagery, email headers, pop-up backgrounds | Brand consistency — must match the site's design system |
| **Static Ads (Meta/Social)** | Facebook feed ads, Instagram story ads, carousel cards, Pinterest pins | Scroll-stopping hook — must grab attention in 0.3 seconds |
| **Video Ads** | Product demos, UGC-style, before/after, unboxing, lifestyle, testimonial-style | First 3 seconds — the hook determines if anyone watches |
| **Social Content** | Instagram posts, TikTok stills, story templates, behind-the-scenes | Platform-native feel — should NOT look like an ad |
| **Brand/Conceptual** | Mood boards, brand world imagery, abstract lifestyle, texture/pattern | Emotional resonance — captures the brand's feeling, not just its products |

### Step 0.2 — Gather Inputs

For EVERY visual generation request, collect or infer:

1. **What is the product?** — Name, category, what it looks like, materials, colors, size
2. **Who is the audience?** — Demographics, lifestyle, aspirations
3. **Where will this be used?** — Shopify PDP, Meta feed ad, Instagram story, website hero, email
4. **What's the mood/vibe?** — Clean/minimal, warm/cozy, bold/energetic, luxurious, playful, clinical
5. **Any reference images?** — "Make it look like [this competitor]" or "similar to [this style]"
6. **Brand guidelines?** — Colors, fonts, existing photography style (check `projects/[brand]/creative-system.md` if it exists)
7. **Aspect ratio needed?** — Square, portrait, landscape, story format (see Phase 8 for exact specs)

### Step 0.3 — Store the Creative Brief

Save to: `projects/[brand]/creative-briefs/[date]-[type].md`

```
## Creative Brief: [Description]
- **Type:** [Product Photo / Website Banner / Meta Ad / Video / Social / Brand]
- **Product:** [name, description, key visual features]
- **Audience:** [who this is for]
- **Placement:** [where it will be used + dimensions]
- **Mood:** [adjectives describing the vibe]
- **References:** [competitor URLs, reference images, mood descriptions]
- **Brand colors:** [hex codes if known]
- **Prompts used:** [filled in after generation]
- **Best result:** [which prompt/version won]
```

---

## Phase 1: Visual Research & Competitor Intelligence

Before generating anything, know what's already working in the market. This phase applies to ALL visual types, not just ads.

### Step 1.1 — Research Using Perplexity

Use Perplexity web search to find:

**For product photography style:**
```
Search: "[competitor brand name] product photography style"
Search: "[product category] ecommerce product photo examples 2025"
Search: "[product category] best Shopify store design product images"
```

**For ad creative inspiration:**
```
Search: "[competitor brand name] Facebook ads Meta Ad Library"
Search: "[product category] best performing Meta ads 2025"
Search: "[product category] ad creative trends [current year]"
```

**For website/banner imagery:**
```
Search: "[competitor brand name] website homepage design"
Search: "[product category] ecommerce hero banner examples"
Search: "best Shopify homepage hero section [product category]"
```

**For video ad styles:**
```
Search: "[product category] best video ads Meta TikTok 2025"
Search: "[competitor brand name] video ad creative"
Search: "UGC style video ads [product category] examples"
```

### Step 1.2 — Meta Ad Library Research (For Ad Creatives)

When the user needs ad creatives, research competitors using Meta Ad Library:

**How to guide the user through Meta Ad Library research:**

1. **Go to:** `facebook.com/ads/library`
2. **Select country** (usually US, or user's target market)
3. **Select "All Ads"** as category
4. **Search by:** competitor brand name, OR broad product keyword (e.g., "organic skincare")
5. **Filter by:** Media type (images, videos, memes), active status, platform (Facebook, Instagram)

**What to look for (the winner signals):**

- **Long-running ads (30+ days active) = WINNERS.** If they're still paying to run it, it's profitable.
- **Multiple variations of the same concept** = they're testing that angle heavily, which means it's working
- **Ad format:** Is it static image, video, carousel, or collection? What dominates?
- **Visual style:** Studio white? Lifestyle? UGC-style? Text-heavy? Clean minimal?
- **Hook:** What's the first thing you see? Bold text? A face? Before/after? Product close-up?
- **Copy structure:** How is the headline written? What's the CTA?
- **Offer:** Discount, free shipping, bundle, limited time?

**Other research sources:**

| Tool | URL | What It's For | Cost |
|------|-----|---------------|------|
| **Meta Ad Library** | facebook.com/ads/library | See all active Meta ads from any brand | Free |
| **TikTok Creative Center** | ads.tiktok.com/business/creativecenter | Trending TikTok ad formats and hooks | Free |
| **Google Ads Transparency** | adstransparency.google.com | See Google Display/Search ads from any brand | Free |
| **Pinterest Trends** | trends.pinterest.com | Visual trends by category | Free |
| **Foreplay** | foreplay.co | Save & organize ads from Meta Library into boards | Paid (free trial) |
| **Minea** | minea.com | Connect winning ads to products & stores | Paid |
| **BigSpy** | bigspy.com | Search ads across Meta, TikTok, Pinterest | Freemium |
| **AdSpy** | adspy.com | Largest searchable ad database, granular filters | Paid |

### Step 1.3 — Build a Competitor Visual Profile

After research, create a profile for each competitor (store in `projects/[brand]/ad-intelligence.md`):

```
## Competitor: [Brand Name]
- **Visual style:** [studio/lifestyle/UGC/mixed]
- **Dominant format:** [static/video/carousel]
- **Color palette:** [describe their visual tones]
- **Photography style:** [bright/moody/natural/studio]
- **Text overlay approach:** [heavy text/minimal text/no text]
- **Hook type:** [product close-up/face/before-after/bold claim/social proof]
- **Longest-running ad:** [describe it — this is their best performer]
- **What they do well:** [specific strengths]
- **Gap we can exploit:** [what they're NOT doing that we could]
```

### Step 1.4 — Define Our Creative Direction

Based on research, decide:

1. **What format(s) to lead with** — match or counter what competitors do
2. **What visual style differentiates us** — if everyone's doing studio white, go lifestyle. If everyone's lifestyle, go clean minimal.
3. **What hooks we'll test** — pick 3-5 hook approaches to generate variants of
4. **What our "look" is** — the consistent visual thread across all creatives

Store in: `projects/[brand]/creative-system.md`

---

## Phase 2: The Prompt Architecture (How Every Prompt Works)

This is the core of the skill. Every image prompt — regardless of tool — follows the same structural framework. Master this and you can prompt anything.

### The 8-Layer Prompt Formula

Every professional image prompt has up to 8 layers. Not every layer is required for every image, but knowing all 8 gives you total control:

```
[MEDIUM] + [SUBJECT] + [SETTING/ENVIRONMENT] + [LIGHTING] + [CAMERA/COMPOSITION] + [STYLE/MOOD] + [DETAILS/PROPS] + [TECHNICAL SPECS]
```

#### Layer 1: MEDIUM (What type of image is this?)
This is the FIRST thing in your prompt. It sets the AI's entire interpretation.

| Medium | When to Use | Example |
|--------|-------------|---------|
| `Professional product photograph` | Shopify product pages, catalog | Realistic, clean, commercial |
| `Commercial lifestyle photograph` | Website heroes, brand imagery | Aspirational, contextual |
| `High-end advertising photograph` | Meta ads, campaign imagery | Polished, attention-grabbing |
| `Editorial fashion photograph` | Clothing, accessories on models | Magazine-quality |
| `UGC-style casual photograph` | Social ads, testimonial-style | Authentic, phone-camera feel |
| `Flat-lay product photograph` | Collection shots, social content | Overhead, arranged composition |
| `3D product render` | Tech products, packaging mockups | Perfect geometry, controlled |
| `Cinematic film still` | Brand world, storytelling | Dramatic, narrative |
| `Clean vector illustration` | Icons, infographics, diagrams | Simple, scalable |

#### Layer 2: SUBJECT (What is the main thing in the image?)
Be EXTREMELY specific. Don't say "a bottle of serum." Say:

```
"A 30ml frosted glass dropper bottle of facial serum with a gold cap and minimalist white label reading 'Lunar Botanics'"
```

Describe:
- Exact product type and form factor
- Material and texture (glass, matte plastic, brushed aluminum, woven cotton)
- Color and finish (frosted, glossy, matte, metallic, transparent)
- Key visual details (label design, logo placement, cap style)
- Size/scale cues (30ml, 8oz, hand-sized, palm-sized)

#### Layer 3: SETTING/ENVIRONMENT (Where is this?)
The background and context around the subject.

**For product photography (clean):**
```
"on a pure white background (#FFFFFF)"
"on a light gray seamless paper backdrop"
"on a marble countertop with soft shadows"
"floating against a solid [brand color] background"
```

**For lifestyle photography:**
```
"on a sunlit bathroom vanity with eucalyptus sprigs and a white towel"
"on a rustic wooden kitchen table next to a cup of coffee, morning light"
"in a modern minimalist apartment, neutral tones, linen textures"
"outdoors on a mossy rock beside a stream in a Pacific Northwest forest"
```

**For ad photography:**
```
"held in a woman's hand against a blurred urban street background"
"on a gym bench next to a water bottle and wireless earbuds"
"on a bedside table with warm lamp light and a book"
```

#### Layer 4: LIGHTING (How is it lit?)
Lighting is the #1 differentiator between amateur and professional images.

| Lighting Type | Look | Best For |
|--------------|------|----------|
| `Soft studio lighting with even illumination` | Clean, no harsh shadows | Product photos (Shopify PDP) |
| `Natural window light, soft and diffused` | Warm, inviting | Lifestyle, UGC-style |
| `Golden hour sunlight` | Warm, aspirational | Outdoor lifestyle, brand world |
| `Dramatic side lighting` | Moody, high-contrast | Luxury products, editorial |
| `Ring light illumination` | Even, beauty-focused | Beauty/skincare products |
| `Backlit with rim light` | Glowing edges, premium | Hero images, transparent products |
| `Overhead diffused softbox` | Flat, even, no shadows | Flat-lay photography |
| `Warm ambient interior lighting` | Cozy, homey | Home goods, candles, food |
| `Cool clinical lighting` | Clean, precise, scientific | Supplements, tech, medical |
| `Neon accent lighting` | Edgy, modern | Streetwear, nightlife, tech |

#### Layer 5: CAMERA/COMPOSITION (How is the shot framed?)
Think like a photographer. These terms directly affect the output.

**Camera angle:**
```
"shot from a straight-on eye-level angle"
"shot from a 30-degree elevated angle"
"shot from a low angle looking up" (makes product feel powerful)
"shot from directly overhead" (flat-lay)
"shot from a 45-degree three-quarter view" (shows depth and dimension)
```

**Lens/focus:**
```
"shot with an 85mm portrait lens, shallow depth of field, f/2.8"
"shot with a macro lens, extreme close-up, sharp detail throughout"
"shot with a 35mm wide-angle lens" (shows environment)
"shot with a 50mm standard lens, natural perspective"
"tilt-shift effect, selective focus" (makes products look miniature/dreamy)
```

**Composition:**
```
"rule of thirds composition, subject off-center"
"centered symmetrical composition"
"negative space on [left/right/top] for text overlay"
"tight crop, filling the frame"
"product positioned in the lower third, sky/background fills upper two-thirds"
```

#### Layer 6: STYLE/MOOD (What feeling does this evoke?)

**Clean/Minimal:**
```
"clean, minimal, modern aesthetic. Muted color palette. Lots of white space."
```

**Warm/Organic:**
```
"warm, earthy tones. Natural textures. Inviting and approachable."
```

**Luxurious/Premium:**
```
"luxurious, elevated aesthetic. Rich tones, soft shadows, premium feel."
```

**Bold/Energetic:**
```
"vibrant, high-energy. Bold colors, dynamic composition, youthful."
```

**Clinical/Trust:**
```
"clean, clinical precision. White and blue tones. Scientific credibility."
```

**UGC/Authentic:**
```
"casual, authentic, slightly imperfect. Like a customer took this photo on their phone. Natural, unpolished."
```

#### Layer 7: DETAILS/PROPS (What else is in the frame?)
Props add context, tell a story, and make images feel real.

```
"accompanied by fresh lavender sprigs and a linen napkin"
"next to a pair of reading glasses and an open book"
"surrounded by ice cubes and water droplets for a refreshing feel"
"with a hand model's fingers gently holding the product"
"alongside complementary products from the same line"
"with subtle brand-colored confetti scattered around"
```

#### Layer 8: TECHNICAL SPECS (Resolution, format, quality)
Add these at the end to control output quality.

```
"8K resolution, ultra-detailed, sharp focus throughout"
"high resolution, photorealistic, professional quality"
"4K, RAW photo quality, fine detail"
"aspect ratio 1:1" (or 4:5, 9:16, 16:9 depending on placement)
```

### The Universal Negative Prompt

Always append a negative prompt to prevent common AI failures:

```
NEGATIVE: blurry, out of focus, low resolution, pixelated, watermark, text overlay, logo, poor lighting, harsh shadows, overexposed, underexposed, amateur, low quality, plastic-looking, distorted, extra limbs, bad anatomy, unrealistic proportions, jpeg artifacts, compression artifacts, stock photo watermark
```

Add category-specific negatives (see Appendix B).

---

## Phase 3: Product Photography Prompts

These are for Shopify product pages, catalog images, and anywhere you need the product to look EXACTLY like the real thing.

### 3.1 — Hero Product Shot (The Main PDP Image)

**Goal:** Clean, professional, the product as the star on a neutral background.

**Template:**
```
Professional product photograph of [EXACT PRODUCT DESCRIPTION including material, color, size, label details]. Shot on a [pure white / light gray / subtle gradient] background. [LIGHTING: soft studio lighting with even illumination, eliminating harsh shadows]. Shot from a [ANGLE: slight 30-degree angle to show dimension / straight-on / three-quarter view]. [LENS: 85mm lens, shallow depth of field, product in razor-sharp focus]. Clean, commercial, high-end ecommerce quality. 8K resolution, ultra-detailed.
```

**Example (skincare):**
```
Professional product photograph of a 30ml frosted glass dropper bottle of facial serum with a gold-tone dropper cap and a minimalist off-white label reading "Lunar Botanics Vitamin C Serum." Shot on a pure white background. Soft studio lighting with even illumination, no harsh shadows, subtle natural shadow beneath the bottle. Shot from a slight 30-degree elevated angle to show the bottle's depth and the gold cap detail. 85mm lens, shallow depth of field. Clean, commercial, premium ecommerce quality. 8K resolution, ultra-detailed, sharp focus throughout.
```

**Example (kitchen scale):**
```
Professional product photograph of a modern digital kitchen scale with a sleek brushed stainless steel platform and a compact white base with a backlit LCD display showing "0.00g". Shot on a clean white background. Soft diffused studio lighting from above and to the left, creating a subtle natural shadow to the right. Shot from a 45-degree three-quarter view to show the platform depth and the display face simultaneously. 50mm lens, sharp focus throughout. Clean, modern, technical product photography. 8K resolution.
```

### 3.2 — Lifestyle Product Shot (Product in Context)

**Goal:** Show the product in a real-world setting that resonates with the target customer.

**Template:**
```
Commercial lifestyle photograph of [EXACT PRODUCT DESCRIPTION] placed [WHERE: on a bathroom shelf / kitchen counter / bedside table / gym bag / desk]. [ENVIRONMENT: describe the full scene — materials, colors, other objects]. [LIGHTING: natural window light / golden hour / warm ambient]. Shot with a [LENS: 35mm wide-angle to show environment / 50mm for balanced / 85mm for shallow depth]. [MOOD: warm and inviting / energetic / calm and serene / modern and minimal]. The product is the clear focal point but feels naturally placed in the scene, not staged. Photorealistic, editorial quality.
```

**Example (kitchen scale with food — the "demo in action" shot):**
```
Commercial lifestyle photograph of a modern digital kitchen scale on a clean white marble countertop. A person's hand is placing a bright red apple onto the scale's brushed steel platform. The LCD display reads "182g". In the background, slightly blurred: a wooden cutting board with sliced vegetables, a ceramic bowl, and a window casting soft natural morning light. Shot with a 50mm lens, shallow depth of field — the scale and hand are sharp, background gently blurred. Warm, inviting, health-conscious lifestyle. The scene feels like a real kitchen moment, not a studio setup. 4K, photorealistic.
```

**Example (skincare in bathroom):**
```
Commercial lifestyle photograph of a Lunar Botanics Vitamin C Serum dropper bottle on a white marble bathroom vanity. Beside it: a small ceramic tray with a jade roller, a folded organic cotton washcloth, and a sprig of dried eucalyptus. Soft diffused natural light streaming from a frosted window to the left. Shot with an 85mm lens, shallow depth of field — serum bottle is in sharp focus, surrounding items gently soft. Clean, spa-like, elevated but approachable. The scene feels aspirational yet attainable. 4K, photorealistic.
```

### 3.3 — Product Detail / Texture Close-Up

**Goal:** Show quality, materials, craftsmanship up close.

**Template:**
```
Macro product photograph, extreme close-up of [SPECIFIC DETAIL: the texture of the fabric / the clasp mechanism / the ingredient texture / the stitching / the surface finish]. [LIGHTING: side lighting to emphasize texture / backlit to show transparency / soft even light for clarity]. Shot with a macro lens at f/4, tack-sharp focus on the detail, surrounding areas gently falling out of focus. The texture and quality of the material should be the hero. 8K resolution, fine detail visible.
```

### 3.4 — Scale / Sizing Shot

**Goal:** Help the customer understand how big/small the product is.

**Template:**
```
Product photograph of [PRODUCT] being held in [a person's hand / placed next to a common reference object like a coffee mug, phone, coin, or pen]. Shot on a [clean / lifestyle] background. [LIGHTING]. The purpose of this image is to communicate the product's physical size. The product and the reference object should both be in sharp focus. Natural, unforced composition. High resolution.
```

### 3.5 — Product Video Demo Prompt (Image-to-Video)

**Goal:** Animate a still product shot to show it in use — like someone placing an apple on a scale and the display changing.

This requires an image-to-video tool (Runway, Kling, Pika, fal.ai). The process is:

1. **Generate the starting frame** using a product photography prompt (Phase 3.1 or 3.2)
2. **Write a motion prompt** describing ONLY the movement, not the scene (the scene comes from the image)

**Motion prompt template:**
```
[SUBJECT MOTION]: [describe exactly what moves and how]
[CAMERA MOTION]: [static / slow push-in / slow pan left / orbit around product]
[DURATION]: [3-5 seconds for product demos]
[SPEED]: [real-time / slight slow-motion for premium feel]
```

**Example (kitchen scale demo):**
```
Starting frame: The lifestyle shot of the kitchen scale on the marble counter, empty.

Motion prompt: A hand enters from the right side of frame and gently places a green apple onto the scale platform. The scale's LCD display flickers and changes from "0.00g" to "195g". The hand releases the apple and exits frame. Camera stays static. Real-time speed. 4 seconds.
```

**Example (serum application):**
```
Starting frame: Close-up of a woman's hand holding the Lunar Botanics serum dropper.

Motion prompt: The dropper slowly releases a single golden drop of serum onto the back of the woman's other hand. The drop catches the light as it falls. Camera holds static on the hands, slight slow-motion. 3 seconds.
```

### 3.6 — Collection / Group Shot

**Goal:** Show multiple products together — the full line, a bundle, a gift set.

**Template:**
```
Professional product photograph of [NUMBER] products from the [BRAND] [COLLECTION NAME] arranged in a [composition style: staggered diagonal / symmetrical row / casual scattered / pyramid formation]. Products include: [list each product with brief description]. Shot on a [background]. [LIGHTING]. Each product is clearly visible and identifiable. The arrangement feels intentional but not rigid. [MOOD]. 8K resolution.
```

---

## Phase 4: Website Asset Prompts

These are for hero banners, collection page headers, about page imagery, email headers, and any image that lives on the website.

### 4.1 — Homepage Hero Banner

**Key requirement:** Must have NEGATIVE SPACE for text overlay (headline + CTA button).

**Template:**
```
[MEDIUM: Commercial lifestyle photograph / Brand world imagery / Cinematic film still] of [SCENE DESCRIPTION that represents the brand's world]. [LIGHTING]. [MOOD]. Wide format, 16:9 aspect ratio. CRITICAL: Leave [generous negative space on the left side / right side / center] for text overlay — the [left/right] [one-third / half] of the image should be relatively clean and uncluttered (soft gradient, blurred background, or solid-ish area) to allow white or [brand color] text to be readable on top. The product or subject should be positioned on the [opposite side]. [STYLE]. High resolution, web-optimized.
```

**Example:**
```
Commercial lifestyle photograph of a sunlit kitchen scene. A woman in a linen apron is preparing a colorful salad on a bright white countertop. Modern kitchen with natural wood accents and green plants on open shelving. Warm, natural morning light streaming from large windows. Wide format, 16:9 aspect ratio. CRITICAL: Leave generous negative space on the left third of the image — the left side should be a clean, bright, softly blurred area suitable for white text overlay. The woman and countertop activity should be positioned in the right two-thirds. Warm, inviting, health-conscious lifestyle. High resolution.
```

### 4.2 — Collection Page Header

**Template:**
```
[MEDIUM] representing the concept of "[COLLECTION NAME]" — [describe the mood and visual world of this collection]. Wide format banner, 3:1 or 4:1 aspect ratio. [LIGHTING]. [MOOD]. Negative space in the center or lower portion for the collection title text. Slightly abstract or environmental — this is about the VIBE of the collection, not showing specific products. [STYLE]. High resolution.
```

### 4.3 — About Page / Brand Story Image

**Template:**
```
[MEDIUM: Documentary-style photograph / Editorial portrait / Behind-the-scenes photograph] of [SCENE: founders in their workspace / product being handmade / raw ingredients being sourced / the team collaborating]. [LIGHTING: natural, authentic]. The image should feel genuine and human — not overly polished or stock-photo-like. [MOOD: authentic, passionate, purpose-driven]. High resolution, warm tones.
```

### 4.4 — Email Header / Pop-Up Background

**Template:**
```
[MEDIUM] for an email header or website pop-up background. [SCENE: related to the offer or campaign]. [DIMENSIONS: 600px wide for email / varies for pop-up]. CRITICAL: Heavy negative space for text — the image serves as an atmospheric backdrop, not the focal point. The center area must be clean enough for readable text overlay. [MOOD]. Slightly desaturated or softened so text pops. High resolution.
```

---

## Phase 5: Meta Static Ad Prompts

### 5.1 — The Scroll-Stop Rule

Every Meta ad image must pass this test: **Would someone stop scrolling in 0.3 seconds?**

What stops scrolls:
- **Contrast** — bright subject on dark background (or vice versa)
- **A human face** — especially making eye contact with the camera
- **Before/after** — immediate visual comparison
- **Bold, large text** — 3-5 words max, readable at thumbnail size
- **Unexpected context** — product in a surprising setting
- **Extreme close-up** — texture, detail that triggers curiosity
- **Social proof overlay** — star rating, review quote, "10,000+ sold"

What does NOT stop scrolls:
- Generic stock-photo-style lifestyle
- Small product on a white background (works for PDP, fails for ads)
- Too much text (turns into visual noise)
- Muted, low-contrast images
- Anything that looks like every other ad in the feed

### 5.2 — Ad Layout Templates

Each layout below is a PROVEN format. Generate variants of each and test.

#### Layout A: Product Hero with Bold Text

**What it is:** Product front and center, bold benefit headline overlaid.

**Prompt template:**
```
High-end advertising photograph of [PRODUCT] centered in the frame against a [bold solid color / gradient / lifestyle] background. [DRAMATIC LIGHTING — slightly more contrast than standard product photography]. Shot from a [slight low angle to make product feel powerful / straight-on]. The product occupies roughly 50-60% of the frame. Clean composition with space above and below the product for text overlay. Bold, premium, attention-grabbing. Aspect ratio [1:1 for feed / 4:5 for feed / 9:16 for story]. 4K resolution.
```

**Post-generation:** Add text overlay with:
- Top: Small social proof ("★★★★★ 2,400+ Reviews")
- Center-bottom: Bold headline (max 5 words: "Your Skin, Transformed.")
- Bottom: CTA ("Shop Now" or offer)

#### Layout B: Problem → Solution Split

**What it is:** Left side shows the "before" (problem), right side shows "with product" (solution).

**Prompt template:**
```
Split-screen advertising photograph. LEFT HALF: [describe the "problem" state — messy desk, tired skin, disorganized kitchen, tangled cables]. RIGHT HALF: [describe the "solution" state — same scene but organized, glowing, clean, with the product visible and integrated into the improved scene]. Clean dividing line down the center. Both halves should have matching lighting and perspective so they feel like the same space transformed. [MOOD: dramatic contrast between problem and solution sides]. Aspect ratio 1:1 for feed. 4K resolution.
```

#### Layout C: UGC-Style (Looks Like a Customer Photo)

**What it is:** Intentionally imperfect, like a real customer posted it. These outperform polished ads on Meta.

**Prompt template:**
```
Casual, UGC-style photograph of [a person / a hand] holding [PRODUCT] in a [natural, everyday setting — kitchen, bathroom, living room, outdoors]. Shot as if taken with a smartphone camera — slightly warm color cast, natural imperfections, not perfectly centered. Natural lighting, no studio setup visible. The person looks [genuine, happy, relaxed] — NOT model-perfect or overly posed. The product is clearly visible and identifiable. This should feel like a customer's Instagram story, not a brand's ad. Aspect ratio 4:5. Phone-camera quality, NOT 8K studio quality.
```

#### Layout D: Lifestyle Aspiration

**What it is:** Shows the LIFE the customer wants, with the product naturally present.

**Prompt template:**
```
Editorial lifestyle photograph of [ASPIRATIONAL SCENE: a beautifully set dinner table / a serene morning routine / a vibrant outdoor adventure / a cozy evening in]. [PRODUCT] is visible in the scene but is NOT the focal point — it's naturally integrated into this desirable lifestyle. [LIGHTING: golden hour / warm ambient / bright and airy]. The image sells the FEELING, not the product directly. Wide enough composition that text can be overlaid on a cleaner area. [MOOD: aspirational, inviting — "I want that life"]. Aspect ratio [4:5 / 1:1]. High resolution, editorial quality.
```

#### Layout E: Social Proof Overlay

**What it is:** Product image with a review quote, star rating, and "As seen in" or "X,000+ happy customers."

**Prompt template:**
```
Clean, professional product photograph of [PRODUCT] on a [neutral / brand-colored] background. [SOFT STUDIO LIGHTING]. Shot from a [flattering angle]. Generous negative space on [top and bottom / one side] specifically designed for text overlay containing: a 5-star rating, a customer review quote, and a credibility badge. The product should be sharp and well-lit but not take up more than 40-50% of the total frame. Aspect ratio [1:1 / 4:5]. 4K resolution.
```

**Post-generation text overlay:**
- Top: ★★★★★ "[short review quote]" — [Customer Name]
- Bottom: "[X],000+ Happy Customers" | "As Seen in [publications]"

#### Layout F: Comparison (Us vs. Them)

**Prompt template:**
```
Side-by-side comparison photograph. LEFT: [generic competitor-style version of the product — plain packaging, boring, generic]. RIGHT: [YOUR PRODUCT — vibrant, premium, well-designed, clearly superior]. The left side should feel slightly dull (cooler tones, less dynamic lighting). The right side should feel premium (warmer tones, better lighting, more appealing). Both products should be the same size in frame for fair comparison. Clean dividing line. Space at top for headline. Aspect ratio 1:1. 4K resolution.
```

---

## Phase 6: Meta Video Ad Prompts

### 6.1 — Video Ad Structures That Convert

Every video ad follows a structure. The structure determines whether people watch.

**Structure A: Hook → Problem → Solution → CTA (5-15 seconds)**
```
[0-3s] HOOK: Attention-grabbing visual or statement
[3-7s] PROBLEM: Show the pain point
[7-12s] SOLUTION: Introduce product as the answer
[12-15s] CTA: "Shop now" / offer / urgency
```

**Structure B: Product Demo (5-10 seconds)**
```
[0-2s] Product appears (unboxing, hand placing it down)
[2-6s] Product in action (being used, demonstrating the key feature)
[6-8s] Result/benefit shown
[8-10s] Product beauty shot + CTA
```

**Structure C: Testimonial/UGC-Style (10-20 seconds)**
```
[0-3s] Person speaks directly to camera: "I've been using [product] for [time]..."
[3-10s] B-roll of them using the product intercut with talking
[10-15s] Before/after or result shown
[15-20s] "Link in bio" / CTA
```

**Structure D: Unboxing / Reveal (5-10 seconds)**
```
[0-2s] Package arrives / hands tear open packaging
[2-5s] Product revealed — slow, satisfying reveal
[5-8s] Product displayed beautifully / key feature highlighted
[8-10s] CTA overlay
```

### 6.2 — Video Prompt Templates (Image-to-Video)

**Step 1:** Generate the starting frame using a product photography or ad prompt from Phases 3-5.
**Step 2:** Write a motion prompt describing ONLY what changes.

**Product demo video:**
```
Starting frame: [product sitting on surface, clean background]

Motion: A hand enters from [direction] and picks up the product. The hand [demonstrates the key action: opens the lid, presses the button, squeezes the tube, flips the switch]. Camera stays [static / slow push-in]. Natural, real-time speed. [Duration] seconds.
```

**Unboxing video:**
```
Starting frame: [branded shipping box on a clean surface, closed]

Motion: Two hands enter frame and open the box. Tissue paper is parted to reveal the product nestled inside. One hand lifts the product out and holds it up to the camera. Camera starts tight on the box, slowly pulls back as the product is revealed. 6 seconds.
```

**Lifestyle scene with subtle motion:**
```
Starting frame: [lifestyle product shot — product on a table, morning setting]

Motion: Gentle ambient movement — steam rises from a coffee cup in the background, curtain sways slightly from a breeze, sunlight shifts subtly. The product remains still and sharp. Camera holds static or very slow push-in (barely noticeable). Creates a "living photograph" effect. 5 seconds.
```

### 6.3 — Video Specs by Placement

| Placement | Aspect Ratio | Max Duration | Safe Zone |
|-----------|-------------|-------------|-----------|
| Facebook Feed | 1:1 or 4:5 | 240s (but 15s optimal) | Keep key info in center 90% |
| Instagram Feed | 1:1 or 4:5 | 60s (but 15s optimal) | Center 90% |
| Instagram Stories/Reels | 9:16 | 60s (but 5-15s optimal) | Avoid top 14% (username) and bottom 20% (CTA) |
| TikTok | 9:16 | 60s (but 5-15s optimal) | Avoid bottom 20% and top 10% |
| Facebook Stories | 9:16 | 15s | Same as IG Stories |

---

## Phase 7: Iteration & Refinement Framework

Prompts rarely produce a perfect result on the first try. This phase teaches you how to systematically improve.

### 7.1 — The Evaluate → Diagnose → Adjust Loop

After each generation:

**Step 1: Evaluate** — Look at the output and ask:
- Does it match the brief? (Category, mood, product accuracy)
- Would I use this on a live Shopify store / in a live ad?
- What's wrong? (Be specific — not "it looks bad" but "the lighting is too harsh on the left side")

**Step 2: Diagnose** — Map the problem to a prompt layer:

| Problem | Which Layer to Fix | Example Adjustment |
|---------|-------------------|-------------------|
| Product looks wrong / inaccurate | Layer 2 (Subject) | Add more physical detail: material, color hex, specific dimensions |
| Background is distracting | Layer 3 (Setting) | Simplify: "clean white background" or add "blurred background" |
| Lighting looks amateur / flat | Layer 4 (Lighting) | Change lighting type: "dramatic side lighting" or "soft diffused window light" |
| Composition feels off | Layer 5 (Camera) | Change angle/lens: "shot from a lower angle" or "tighter crop" |
| Mood/vibe is wrong | Layer 6 (Style) | Adjust mood descriptors: "warmer," "more minimal," "higher contrast" |
| Image has AI artifacts | Layer 8 (Technical) + Negative prompt | Add to negative: "artifacts, distorted, unrealistic" |
| Looks too AI-generated | Layer 6 + Medium | Add "photorealistic" and photography terms (lens, aperture) |
| No space for text overlay | Layer 5 (Composition) | Add: "negative space on [side] for text overlay" |

**Step 3: Adjust** — Change ONLY the problematic layer. Don't rewrite the whole prompt.

### 7.2 — The 3-Generation Rule

For any important visual:

1. **Generation 1:** Full prompt, see what the AI interprets
2. **Generation 2:** Fix the biggest issue from Gen 1 (adjust 1-2 layers)
3. **Generation 3:** Fine-tune the details (props, lighting nuance, crop)

If Gen 3 isn't working, the problem is usually Layer 1 (Medium) or Layer 2 (Subject) — the AI fundamentally misunderstood what you want. Rewrite from scratch with a clearer foundation.

### 7.3 — Replicating a Competitor's Style

When the user says "make it look like [this competitor's ad]":

1. **Analyze the reference:** Break it down into the 8 layers — what medium, subject, setting, lighting, camera, style, details, technical specs?
2. **Write each layer explicitly** based on what you see, NOT what you assume
3. **Swap the product:** Replace their product with the user's product
4. **Adjust the brand codes:** Change colors, props, and mood to match the user's brand
5. **Generate → Compare → Iterate**

**Example analysis of a competitor ad:**
```
Reference: Competitor's ad shows a serum bottle on a sandy beach with golden hour light.

Analysis:
- Medium: Commercial lifestyle photograph
- Subject: 30ml glass serum bottle (their product — swap with ours)
- Setting: Sandy beach, ocean blurred in background, seashells as props
- Lighting: Golden hour, warm, side-lit from the left
- Camera: Low angle (about 15 degrees up), 85mm, shallow DoF
- Style: Warm, natural, organic, aspirational
- Details: Fine sand grains visible, one shell beside the bottle
- Technical: 4:5 aspect ratio, high resolution

Our version prompt:
Commercial lifestyle photograph of [OUR PRODUCT DESCRIPTION] on fine golden sand, ocean blurred in background. Golden hour sunlight, warm side-lighting from the left creating a soft warm glow on the bottle. Shot from a low 15-degree angle with an 85mm lens, shallow depth of field — bottle in sharp focus, sand and ocean softly blurred. A small piece of driftwood beside the bottle. Warm, natural, organic, aspirational mood. Aspect ratio 4:5. High resolution, photorealistic.
```

### 7.4 — What to Remember (Memory Rules)

After successful generations, save to `MEMORY.md` under "Creative Wins":

```
- [Date] [Brand] [Type]: "[shortened prompt]" → Great result. Key was [specific detail that made it work, e.g., "specifying 85mm lens + shallow DoF made it look pro" or "adding 'UGC-style, phone camera quality' made it stop looking like an ad"]
```

After failed attempts, save to `MEMORY.md` under "Creative Gotchas":

```
- [Date] [Tool]: [What went wrong and how to avoid it, e.g., "FLUX ignores camera angle keywords — need to use 'perspective' language instead" or "Midjourney v6 makes all skincare bottles look cylindrical — need to specify 'rectangular bottle' explicitly"]
```

---

## Phase 8: Export Specs & Platform Requirements

### 8.1 — Image Dimensions by Platform

| Placement | Aspect Ratio | Minimum Size | Recommended |
|-----------|-------------|-------------|-------------|
| **Shopify Product (main)** | 1:1 (square) | 800x800px | 2048x2048px |
| **Shopify Product (additional)** | 1:1 | 800x800px | 2048x2048px |
| **Shopify Collection Banner** | 16:9 or 3:1 | 1200x400px | 2400x800px |
| **Shopify Homepage Hero** | 16:9 | 1920x1080px | 2560x1440px |
| **Meta Feed Ad (square)** | 1:1 | 1080x1080px | 1080x1080px |
| **Meta Feed Ad (portrait)** | 4:5 | 1080x1350px | 1080x1350px |
| **Meta Story/Reels Ad** | 9:16 | 1080x1920px | 1080x1920px |
| **Meta Carousel Card** | 1:1 | 1080x1080px | 1080x1080px |
| **Instagram Post** | 1:1 or 4:5 | 1080x1080px | 1080x1350px |
| **Pinterest Pin** | 2:3 | 1000x1500px | 1000x1500px |
| **Google Display Ad** | varies | 300x250, 728x90, 160x600 | Multiple sizes |
| **Email Header** | ~3:1 | 600x200px | 1200x400px |

### 8.2 — File Format Requirements

| Use Case | Format | Max Size | Notes |
|----------|--------|----------|-------|
| Shopify product images | JPEG or WebP | < 20MB | WebP preferred (30-50% smaller) |
| Website banners/heroes | WebP or JPEG | < 200KB optimized | Compress after generation |
| Meta ad images | JPEG or PNG | < 30MB | PNG if transparency needed |
| Meta ad videos | MP4 (H.264) | < 4GB | 15s optimal for feed |
| Email images | JPEG | < 200KB | Some clients block large images |

### 8.3 — Meta Ad Text Rules

- **Primary text (above image):** 125 characters optimal, 240 max before truncation
- **Headline (below image):** 27 characters optimal, 40 max
- **Description:** 27 characters optimal
- **CTA button:** Choose from: Shop Now, Learn More, Sign Up, Book Now, Get Offer, Download
- **Text on image:** Meta reduces reach if > 20% of the image is text. Keep text overlays minimal.

### 8.4 — Naming Convention for Assets

```
[brand]-[type]-[variant]-[dimensions]-[version].[ext]

Examples:
lunarbotanics-hero-lifestyle-2048x2048-v1.webp
lunarbotanics-metaad-ugc-1080x1350-v3.jpg
lunarbotanics-video-demo-1080x1920-v1.mp4
lunarbotanics-banner-collection-summer-2400x800-v2.webp
```

Store in: `projects/[brand]/assets/[type]/`

---

## Appendix A: Prompt Modifier Library

### Lighting Modifiers
```
soft studio lighting | hard directional light | natural window light
golden hour sunlight | overcast diffused light | backlit rim light
ring light | neon accent lighting | candlelight warm glow
cool clinical LED | dramatic chiaroscuro | flat even illumination
dappled sunlight through leaves | moonlit | twilight ambient
```

### Camera/Lens Modifiers
```
85mm portrait lens f/2.8 | 50mm standard lens | 35mm wide-angle
macro lens extreme close-up | 24mm ultra-wide | 135mm telephoto
tilt-shift selective focus | fish-eye distortion | anamorphic lens flare
top-down overhead | eye-level straight-on | low angle hero shot
Dutch angle tilted | over-the-shoulder | POV first-person
```

### Style/Mood Modifiers
```
clean minimal modern | warm earthy organic | luxurious premium elevated
bold vibrant energetic | soft muted pastel | dark moody dramatic
clinical precise scientific | playful colorful fun | rustic vintage nostalgic
futuristic sleek tech | cozy hygge homey | editorial high-fashion
raw authentic UGC | cinematic widescreen | ethereal dreamlike
```

### Surface/Material Modifiers
```
brushed aluminum | matte black | glossy white | frosted glass
polished marble | raw concrete | weathered wood | woven linen
soft velvet | crinkled kraft paper | smooth ceramic | cork texture
hammered copper | satin finish | crystalline transparent | embossed leather
```

### Color/Tone Modifiers
```
warm golden tones | cool blue undertones | neutral balanced
high contrast black and white | desaturated muted | vibrant saturated
monochromatic [color] | duotone [color1] and [color2] | pastel soft
earth tones | jewel tones | neon accents on dark | sepia vintage
```

---

## Appendix B: Negative Prompt Library

### Universal (Always Include)
```
blurry, out of focus, low resolution, pixelated, watermark, text, logo, poor lighting, harsh shadows, overexposed, underexposed, amateur, low quality, jpeg artifacts, compression, distorted, deformed
```

### Product Photography Specific
```
plastic-looking metal, fake materials, incorrect texture, poor reflections, unrealistic surface, cheap appearance, wrong proportions, melted edges, floating objects, inconsistent shadows, background bleed
```

### People/Models Specific
```
bad anatomy, extra limbs, extra fingers, mutated hands, distorted face, uncanny valley, plastic skin, overly smooth skin, cross-eyed, wrong number of fingers, disproportionate body
```

### Ad Creative Specific
```
cluttered, busy background, too many elements, stock photo feeling, generic, corporate, dated design, clip art, low effort, template-looking
```

### Video Specific
```
jittery motion, flickering, morphing, temporal inconsistency, frame drops, unnatural movement, object warping between frames, sudden appearance/disappearance
```

---

## Appendix C: Tool-Specific Syntax Guide

Different AI image tools interpret prompts differently. Here's how to adjust:

### FLUX (via fal.ai or Replicate)
- Responds best to: natural language descriptions, photography terms
- Strength: photorealism, text rendering, prompt adherence
- Tip: Be very descriptive. FLUX follows prompts closely.
- Negative prompts: Not natively supported — bake quality terms into the positive prompt
- Example prefix: `"A professional product photograph, 8K, ultra-detailed, sharp focus,"`

### Midjourney
- Responds best to: concise prompts, style keywords, `--parameters`
- Strength: artistic quality, aesthetic coherence, color harmony
- Tip: Front-load the most important elements. Use `--ar` for aspect ratio, `--s` for stylization, `--q` for quality.
- Negative prompts: Use `--no [thing to exclude]`
- Example: `product photo of glass serum bottle, marble surface, soft lighting, editorial --ar 4:5 --s 250 --q 2 --no text watermark`

### Stable Diffusion / SDXL (via fal.ai, Replicate, ComfyUI)
- Responds best to: keyword-heavy prompts with weight syntax
- Strength: control via ControlNet, inpainting, outpainting
- Tip: Use parentheses for emphasis: `(sharp focus:1.3)`, `(professional lighting:1.2)`
- Negative prompts: Full negative prompt support — use extensively
- Example: `professional product photograph, (glass serum bottle:1.3), marble surface, (soft studio lighting:1.2), 8K, ultra detailed`

### Flair.ai / Claid.ai / CreatorKit
- These are ecommerce-specific tools — they work differently
- You typically upload a real product photo and describe the SCENE, not the product
- Prompt focuses on: background, setting, props, lighting, mood
- Example: `"Place on a marble bathroom vanity with eucalyptus, soft morning light, spa-like"`

### Image-to-Video Tools (Runway, Kling, Pika, Luma)
- Prompt describes MOTION ONLY — the starting image provides the scene
- Keep motion prompts short and specific
- Describe: what moves, direction of movement, camera movement, speed
- Example: `"Hand enters from right, picks up the bottle, turns it slowly to show the label. Camera stays static. Real-time speed."`

---

## Memory & File Structure

```
projects/[brand]/
├── creative-briefs/
│   └── [date]-[type].md           ← Phase 0: Brief for each generation request
├── ad-intelligence.md             ← Phase 1: Competitor visual profiles
├── creative-system.md             ← Phase 1: Our visual direction and rules
├── prompts/
│   ├── product-shots.md           ← Phase 3: Prompts that worked for products
│   ├── website-assets.md          ← Phase 4: Prompts for site imagery
│   ├── static-ads.md              ← Phase 5: Meta ad prompts
│   └── video-ads.md               ← Phase 6: Video prompts
└── assets/
    ├── hero/                      ← Product hero images
    ├── lifestyle/                 ← Lifestyle product shots
    ├── detail/                    ← Close-up / texture shots
    ├── website/                   ← Banners, headers, about imagery
    ├── ads/
    │   ├── feed/                  ← 1:1 and 4:5 ad creatives
    │   ├── story/                 ← 9:16 story/reel creatives
    │   └── carousel/              ← Carousel card images
    └── video/                     ← Generated video files
```

**MEMORY.md entries:**
- `Creative Wins`: Prompts/approaches that produced great results
- `Creative Gotchas`: Tool-specific issues and how to avoid them
- `Client Preferences`: "[Brand] prefers warm/cool lighting, hates [X style]"

**Daily memory** (`memory/YYYY-MM-DD.md`): What was generated, which prompts worked, which brand/project, next steps.

---

*End of Visual Prompting Skill. Load specific phases on demand. Use Perplexity for all web research. Save working prompts to project files. Learn from every generation.*
