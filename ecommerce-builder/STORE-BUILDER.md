# StoreForge — Ecommerce Store Builder Skill
> Source: StoreForge Guide by ScaleUP Media / @mattganzak
> Installed: 2026-02-12

---

## CORE TARGETS (Non-Negotiable)
- Build time: Full store in **< 4 hours** from brand brief to live
- Baseline CVR: **> 2.5%** at launch (industry avg 1.8%)
- Tracking completeness: **100%** of funnel events instrumented from day one
- Page speed: **LCP < 2.5s** on all pages
- API cost: **$30-50/month** max

---

## WORKSPACE STRUCTURE
| File | Role | Load When |
|------|------|-----------|
| SOUL.md | Philosophy, session rules, model routing | Every session |
| IDENTITY.md | Persona, tone, emoji | Every session |
| USER.md | Info, projects, success metrics | Every session |
| AGENTS.md | Build sequence, memory rules | Every session |
| TOOLS.md | Account IDs, tracking stack, benchmarks | Every session |
| HEARTBEAT.md | Periodic check-in protocol (Ollama) | On heartbeat only |
| MEMORY.md | Long-term: lessons, client prefs, tech gotchas | On-demand only |
| memory/YYYY-MM-DD.md | Daily notes: built, decisions, next steps | Today's file on start |
| skills/ecommerce-builder/STORE-BUILDER.md | This file — 10-phase framework | On-demand when building |
| projects/[brand]/... | Per-brand: briefs, audits, design systems, tracking | On-demand per project |

---

## TOKEN OPTIMIZATION (Built-In Rules)
- Session init: **8KB startup** (5 lean files, not full history)
- Model routing: **Haiku default**. Sonnet only for architecture/strategy/complex code review
- Heartbeat: **Ollama llama3.2:3b** locally — $0/month for check-ins
- Prompt caching: SOUL.md, USER.md, TOOLS.md cached at 90% discount
- Budget caps: **$5/day, $200/month** with 75% warnings

---

## ONE-PROMPT BUILD MODE (Default)
When the user says anything like:
- “build a store”, “design the frontend”, “make it look like X”, “improve this website”, “redo the homepage/PDP/collection”

…treat it as a **single integrated prompt** that ALWAYS includes:
1) Phase 0.2 Competitor Continuation Loop (direct + aspirational comps)
2) A prioritized change plan (Now / Next)
3) Implementation (theme edits / components / copy / layout)
4) A quick QA checklist (mobile, LCP, tracking sanity)

**Output format (required):**
- (A) “What we’re copying” (bullet list)
- (B) “What we’re changing on your site” (ordered checklist)
- (C) “Implementation notes” (files/sections to touch)
- (D) “Before/after success metrics to watch” (CVR, ATC, checkout completion, LCP)

---

## PHASE 0: Brand Discovery
**Files:** `projects/[brand]/brand-brief.md`, `projects/[brand]/competitor-audit.md`, `projects/[brand]/inspiration-swipefile.md`

### Step 0.1 — Brand Inputs (collect ALL before writing code)
| Input | Why It Matters |
|-------|---------------|
| Brand name | Logo, domain, SEO title tags |
| What they sell | Page structure, filtering, product complexity |
| Target customer | Voice, imagery, price anchoring, trust signals |
| Price range | Layout (luxury vs. value), urgency tactics |
| Brand personality | Drives entire design system |
| USP | Hero copy, comparison tables, badge messaging |
| Competitors (2-5 URLs) | Direct benchmark + positioning |
| Existing assets | Logo, colors, fonts, photography |
| Business model | One-time, subscription, bundles, hybrid |
| Traffic sources | Landing page strategy, UTM personalization |

### Step 0.2 — Competitor Continuation Loop (MANDATORY for any build/design request)
Whenever the user asks to **build a site**, **design a storefront**, or **improve a frontend**, ALWAYS do this loop before implementing UI changes:

1) **Direct competitors (2–5)**
- Use user-provided URLs; if none, find them.

2) **Best-in-class references (5–10)** ("aspirational comps")
- Pick the strongest stores in/near the category + a few general best-in-class ecommerce UX patterns.

3) **Extract patterns (copy structure, not branding)**
- Homepage section order + above-the-fold composition
- Collection page grid + filters + sorting
- PDP: ATF layout, gallery behavior, sticky ATC, reviews, FAQs
- Cart UX: slideout, free-ship bar, upsells
- Trust: shipping/returns clarity, guarantees, payment badges, social proof density

4) **Decide: what we’re copying + what we’re differentiating**
- Make a short checklist of "Implement now" (highest impact) vs "Later".

5) **Ship improvements in the same session**
- Prioritize: (a) clarity, (b) trust, (c) speed, (d) friction removal.

Save the output as `projects/[brand]/inspiration-swipefile.md` (bullets + links + screenshots-notes if available).

### Step 0.3 — Competitor Audit (save to projects/[brand]/competitor-audit.md)
Score each competitor 1-10:
- First Impression, Visual Quality, Navigation, Product Pages, Mobile, Checkout, Page Speed, Trust Signals, Conversion Tactics, Differentiation

### Memory Rules for Phase 0
- **Daily memory**: Brand name, personality adjectives, USP, platform, top 3 competitor insights
- **Long-term MEMORY.md**: Client preferences that recur
- **Projects/**: Full brand brief + competitor audit permanently
- **DON'T store**: Raw HTML, full screenshots, verbose notes — summarize insights only

---

## PHASE 1: Store Architecture
**Files:** `projects/[brand]/sitemap.md`

### Site Map Template
```
/ (Root)
├── Homepage
├── /collections/all
├── /collections/[category]
├── /collections/bestsellers
├── /collections/new-arrivals
├── /collections/sale
├── /products/[product-slug]
├── /pages/ (about, faq, contact, shipping)
├── /blogs/[article-slug]
├── /account/ (login, register, orders)
├── /cart
├── /checkout
└── /policies/ (privacy, terms, refund)
```

### Navigation Rules
- Main nav: **Max 5-7 items**. Mega menus with imagery (outperforms text-only 20-30%)
- Search: Persistent, prominent, autocomplete + product images (search users convert **2-3x higher**)
- Sticky header: Logo + search + cart at minimum
- Footer: Full nav + social + email signup + payment icons + legal
- **Never deeper than 3 clicks to any product**

---

## PHASE 2: UI Design System
**Files:** `projects/[brand]/design-system.md`

### Color Palette (exactly 6 roles)
| Role | Purpose |
|------|---------|
| Primary | CTA buttons, links, active states |
| Primary Dark | Hover states, headings, footer background |
| Secondary | Secondary buttons, badges, tags |
| Neutral Dark | Body text, headings (#1A1A1A — never pure black) |
| Neutral Light | Backgrounds, cards, section alternation (#F7F7F7) |
| White | Page background, card backgrounds (#FFFFFF) |

- CTA contrast ratio: **≥ 4.5:1** (WCAG AA)
- Sale prices: Always red/bold — **never same color as regular price**
- Section rhythm: Alternate white and neutral light backgrounds

### Typography (2 fonts max)
| Element | Size | Weight |
|---------|------|--------|
| Hero headline | 48-72px desktop / 28-36px mobile | Bold, tight letter-spacing |
| Section headline | 32-40px | Bold or semibold |
| Body text | **16px minimum** | Regular, 1.6 line-height |
| Price | 20-28px | Bold (must stand out) |
| Labels/badges | 12px uppercase | Wide letter-spacing (0.05-0.1em) |

### Spacing (8px base grid)
4px=micro | 8px=tight | 16px=small | 24px=medium | 32px=large | 48px=section-gap | 64px=section-padding | 96px=hero-padding

---

## PHASE 3: Homepage Layout
**Files:** `projects/[brand]/pages/homepage.md`

**Homepage's one job: get visitors to a product page as fast as possible.**

### Proven High-Converting Section Order
| # | Section | Notes |
|---|---------|-------|
| 1 | Announcement Bar | Free shipping threshold, rotating messages |
| 2 | Hero Section | Full-width image, benefit-driven headline, ONE CTA |
| 3 | Social Proof Bar | "As seen in" logos OR "10,000+ happy customers" |
| 4 | Featured Categories | 3-4 category cards with lifestyle imagery |
| 5 | Bestsellers | 4-8 product cards, "Shop All" link |
| 6 | Value Props Strip | Free Shipping | Easy Returns | Secure Pay + brand-specific |
| 7 | Brand Story | Split layout: image + 2-3 sentences + Learn More |
| 8 | UGC / Reviews | Customer photos or 3 featured review cards |
| 9 | New Arrivals | 4-6 product cards, time-sensitive framing |
| 10 | Email Signup | "10% off first order" — email only |

### Critical Homepage Rules
- Hero LCP **< 2.5 seconds**
- **ONE primary CTA** above the fold — not three
- Product cards viewable within 1.5 viewport heights
- Alternate section backgrounds (white / light gray / white)
- **NO auto-playing carousels** — static images convert **30-40% better**

---

## PHASE 4: Product Pages
**Files:** `projects/[brand]/pages/product-template.md`
**The product page is where money is made or lost.**

### Above-the-Fold Layout (Desktop)
```
[IMAGE GALLERY]          [PRODUCT INFO]
Main image (zoomable)    Breadcrumb
Thumbnails               Product Name (H1)
                         Stars + Review Count
                         Price (or Sale Price)
                         Short description
                         Variant selectors
                         Quantity picker
                         [ADD TO CART] button
                         [Express Pay buttons]
                         Trust badges row
```

### Below-the-Fold Sections
- Product Details (tabs/accordion: Description, Specs, How to Use, Shipping)
- Social Proof — 3 highlighted reviews with photos
- Comparison Table (vs. competitors if applicable)
- "You May Also Like" — 4 related products
- Recently Viewed
- Full Reviews — sortable, filterable, with summary bar
- FAQ — product-specific, collapsible, with FAQ schema

### Must-Have Conversion Elements
| Element | Impact |
|---------|--------|
| Star rating + count (clickable → reviews) | Builds trust instantly |
| Trust badges below Add to Cart | Reduces purchase anxiety |
| "Only X left in stock" (only when TRUE) | Creates urgency |
| Estimated delivery date ("Get it by Friday") | Reduces uncertainty |
| Sticky Add to Cart bar (appears when main CTA scrolls away) | Never lose buy button |
| Express checkout (Apple Pay, etc.) | 1-tap purchase path |
| Installment messaging ("4 payments of $12 with Afterpay") | Lowers perceived price |

---

## PHASE 5: Cart & Checkout
**Files:** `projects/[brand]/checkout-config.md`
**Cart abandonment averages 70%. Every friction removed = direct revenue.**

### Use Slide-Out Cart (Not Cart Page)
- Free shipping progress bar — **lifts AOV 5-15%**
- Upsell in cart: "Add [product] for just $12 more"
- Product images + variant details visible
- Promo code field **COLLAPSED by default** (expanded = people leave to Google)

### Checkout Flow (Max 3 Steps)
Each extra step loses 10% of remaining customers.
1. Information — Email, shipping, phone (Google autocomplete, guest checkout ALWAYS)
2. Shipping — Methods with prices + **concrete delivery dates** (not "5-7 business days")
3. Payment — Card, Shop Pay, Apple Pay, Google Pay, PayPal, BNPL

### Checkout Musts
- **Guest checkout ALWAYS available** — 34% abandon due to forced account creation
- Express payment buttons above the fold
- Auto-save progress
- Order confirmation: order number + email notice + "Continue Shopping" CTA

---

## PHASE 6: Conversion Infrastructure (Tracking)
**Files:** `projects/[brand]/tracking-plan.md`
**Never skip this. Without tracking, all design work flies blind.**

### Google Tag Manager
- GTM is the foundation — **never hardcode pixels into the theme**
- Shopify: Use Custom Pixels (Settings > Customer Events) — required 2025+
- Store all IDs as Constant Variables

### GA4 Data Layer Events
| Event | Fires When | Key Data |
|-------|-----------|----------|
| page_view | Every page load | page_type, user_logged_in |
| view_item | Product page | item_id, name, price, currency |
| view_item_list | Collection page | item_list_name, items[] |
| add_to_cart | Add to cart click | items[], value, currency |
| view_cart | Cart open | items[], value |
| begin_checkout | Checkout start | items[], value, coupon |
| add_shipping_info | Shipping step | items[], shipping_tier |
| add_payment_info | Payment step | items[], payment_type |
| **purchase** | **Confirmation page (CRITICAL)** | transaction_id, value, tax, shipping, items[] |
| sign_up | Email capture | method |
| search | Site search | search_term |

### Meta Pixel + CAPI
- Install via GTM (Stape tag supports GA4 data layer natively)
- Map: view_item→ViewContent, add_to_cart→AddToCart, purchase→Purchase
- **Always implement CAPI alongside browser pixel** — browser alone misses 10-30% (ad blockers)
- Event deduplication with matching event_id (prevent double-counting)

### Google Ads + Enhanced Conversions
- Create Conversion Tracking tag in GTM, fire on purchase
- Pass: value, currency, transaction_id
- Enable Enhanced Conversions (hashed first-party data, better attribution)

### Tracking QA Checklist
- [ ] All tags fire correctly (GTM Preview mode)
- [ ] GA4 events appear (GA4 DebugView)
- [ ] Meta events fire (Meta Events Manager > Test Events)
- [ ] Purchase fires ONCE only (refresh confirmation — must not re-fire)
- [ ] Transaction value matches actual order
- [ ] CAPI deduplication works
- [ ] Tags respect cookie preferences (GDPR/CCPA)

---

## PHASE 7: SEO Foundation
**Files:** `projects/[brand]/seo-plan.md`

### Every Page Must Have
- Unique `<title>`: "Product Name | Brand" or "Collection - Brand"
- Unique `<meta description>`: 150-160 chars with keyword + CTA
- Canonical URL, Open Graph tags, Twitter Card tags
- Schema.org structured data (JSON-LD in head)

### Schema by Page Type
| Page | Schema Type |
|------|------------|
| Homepage | Organization + WebSite (name, url, logo, searchAction) |
| Product | Product + Offer (name, image, price, availability, aggregateRating) |
| Collection | CollectionPage + ItemList |
| Blog post | Article (headline, author, datePublished, image) |
| FAQ | FAQPage (mainEntity[].Question + Answer) |

### Page Speed Targets
| Metric | Target | Impact |
|--------|--------|--------|
| LCP | < 2.5s | 1s delay = 7% conversion loss |
| FID | < 100ms | Interactivity perception |
| CLS | < 0.1 | Visual stability |
| Page weight | < 1.5MB ideal, < 3MB max | Mobile speed |

---

## PHASE 8: Mobile-First Optimization
**60%+ of ecommerce traffic is mobile. Design mobile-first, adapt upward.**

- Sticky bottom bar on product pages: [Wishlist] [Add to Cart]
- Image gallery: Horizontal swipe with dots (not thumbnails)
- Buttons: **Minimum 48px tap target height**
- Body text: **14-16px minimum** (nothing smaller than 12px anywhere)
- Accordion for details (saves vertical space)
- Serve smaller images: use srcset with responsive sizes
- Product grid on collection pages: **2 columns** (never 1 — wastes space)

---

## PHASE 9: Post-Launch Playbook
**Files:** `projects/[brand]/optimization-log.md`

### Pop-Up & Email Capture Strategy
| Type | Trigger | Offer |
|------|---------|-------|
| Welcome popup | 5-8s, new visitors only | 10-15% off for email |
| Exit-intent | Mouse toward close (desktop) | Free shipping |
| Cart abandonment | 30s on cart without checkout | "Complete order in 10 min for free shipping" |
| Post-purchase | Confirmation page | "Refer a friend, get $15" |

### Abandoned Cart Email Sequence
1. 1 hour — cart contents + images + simple CTA
2. 24 hours — cart + social proof (review snippet)
3. 72 hours — cart + small discount (5-10% or free shipping)

### A/B Testing Priority (Highest Impact First)
1. CTA button text ("Add to Cart" vs. "Add to Bag" vs. "Buy Now")
2. Hero (image vs. video, headline variants)
3. Free shipping threshold ($50 vs. $75 vs. $100)
4. Product page layout (image placement variants)
5. Pop-up offer (% off vs. free shipping vs. free gift)
6. Checkout flow (single-page vs. multi-step)

### Key Metrics Dashboard (Weekly)
| Metric | Good | Great | Elite |
|--------|------|-------|-------|
| Conversion rate | 2% | 3% | 4%+ |
| Add-to-cart rate | 8% | 10% | 12%+ |
| Cart-to-checkout | 40% | 50% | 60%+ |
| Checkout completion | 45% | 55% | 65%+ |
| Bounce rate (homepage) | < 45% | < 35% | < 25% |
| Mobile conversion | 1.5% | 2% | 3%+ |
| Email capture rate | 3% | 4% | 5%+ |
| LCP (seconds) | < 3.0 | < 2.5 | < 1.5 |

---

## PROJECTS FOLDER CONVENTION
Each brand gets: `projects/[brand-slug]/`
```
brand-brief.md         ← Phase 0 output
competitor-audit.md    ← Phase 0 output
sitemap.md             ← Phase 1 output
design-system.md       ← Phase 2 output
pages/
  homepage.md          ← Phase 3 output
  product-template.md  ← Phase 4 output
checkout-config.md     ← Phase 5 output
tracking-plan.md       ← Phase 6 output
seo-plan.md            ← Phase 7 output
optimization-log.md    ← Phase 9 output
```

---

## CONVERSION WINS (Track Across All Stores)
> Updated: 2026-02-12 | NutriScale deep rebuild research

1. **Trust badges next to ATC button** — 49% of shoppers see missing badges as fraud signal. Place 3 max: shipping, returns, security. Impact: +15-20% CVR lift.

2. **Sidebar filters on collection pages** — Real-time filtering with applied filter chips + clear all. Reduces bounce by 20%+ and increases time-on-site.

3. **Hero banner on collection pages** — Context-setting banner with headline + CTA above the product grid. Reduces bounce and frames the shopping experience.

4. **Product-type-specific content** — Dynamic descriptions, FAQ, specs, benefits that change based on product type (hardware vs subscription vs accessory). Dramatically better than one-size-fits-all.

5. **Star ratings as scroll-to-reviews link** — Clickable rating near title that smooth-scrolls to review section. Builds trust above fold, drives engagement below fold.

6. **Sticky ATC bar** — Appears when main button scrolls off-screen. Never lose the buy button. Especially critical on mobile where product pages are long.

7. **Quantity stepper with -/+ buttons** — Better UX than plain number input. Reduces friction, feels premium. Always default to 1.

8. **Collapsible "What's Included" / "Key Specs" above fold** — Progressive disclosure keeps ATF clean while making details accessible. Outperforms tabs for mobile.

9. **Final CTA section at page bottom** — Dark gradient banner with "Ready to [outcome]?" + ATC button + trust indicators. Catches users who scrolled the entire page.

10. **Quick-add buttons on collection cards** — Hover-reveal "Quick Add" that fires AJAX cart. Reduces friction for repeat buyers and impulse purchases. Show "✓ Added!" confirmation.

11. **Remove ALL emojis from product/store copy** — Replace with inline monochromatic SVG icons. Emojis signal AI-generated content and reduce trust. Use Feather/Heroicons-style stroke icons (1.5px weight).

12. **Use eyebrow text (uppercase label above heading) instead of emoji-prefixed headings** — Small, tracked-out uppercase text in brand color above the main heading. Oura Ring pattern.

13. **Trust badges: SVG icon + text in a horizontal row** — No colored background boxes. Icon in brand color, text in neutral. Clean, premium, functional.
