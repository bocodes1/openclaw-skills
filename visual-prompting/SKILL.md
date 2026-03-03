---
name: visual-prompting
description: Generate and iterate ecommerce-ready image/video prompts for product photography, website banners, Meta ads, and short-form video creatives. Use when users ask for better prompts, competitor-style visuals, asset specs, or conversion-focused creative iteration for Shopify and paid ads.
---

# Visual Prompting

Use this skill to produce production-grade prompts and creative iterations for ecommerce assets.

## Workflow

1. Classify the visual request (product photo, website asset, static ad, video ad, social, brand conceptual).
2. Build a concise creative brief in `projects/[brand]/creative-briefs/[date]-[type].md`.
3. Use the 8-layer prompt architecture from `references/master-instruction-set.md`.
4. Generate 1-3 variants first, then run Evaluate → Diagnose → Adjust.
5. Save winning prompts in project prompt files and record wins/gotchas in memory.

## Phase routing

- Product photos → Phase 3
- Website hero/banner assets → Phase 4
- Meta static ads → Phase 5 (+ Phase 1 for research)
- Video ads / image-to-video → Phase 6
- Prompt debugging → Phase 2 + Phase 7

## Rules for output quality

- Keep product geometry/materials consistent with references.
- Require usable composition for placement (e.g., negative space for hero headline/CTA).
- Prefer platform-native dimensions from Phase 8.
- Include artifact-prevention constraints in prompt text for FLUX endpoints.

## Resources

- Full framework: `references/master-instruction-set.md`
