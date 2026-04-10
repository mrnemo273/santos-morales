# Santos-Morales® — Brand System

> **Version:** 1.0
> **Last updated:** 2026-04-10
> **System owner:** Santos-Morales®

---

## Brand Identity

**Name:** Santos-Morales®
**Registered mark:** Always display with ® superscript
**Logo format:** Wordmark only — "Santos-Morales" set in Helvetica Neue, weight 800, letter-spacing -0.02em, with ® as superscript (font-size 55% of wordmark, weight 600, top-aligned). In dark mode, the hyphen is rendered in Vermillion (`--color-brand`) as a subtle brand accent against the cream text.

**Tagline:** Strategic Execution
**Positioning statement:** Santos-Morales is a premium design and strategy studio that synthesizes high-level strategy with granular operational execution. The firm is co-led by a designer and a project manager, bringing complementary lenses — creative precision and operational rigor — to every engagement.

**Personality in one line:** Bold precision with human warmth — an engineered brand that never feels cold.

---

## Brand Pillars

| Pillar | Description |
|---|---|
| **Bold** | We lead with confidence. Large type, strong color, decisive layouts. Nothing is tentative. |
| **Precise** | Every token, every spacing decision, every weight is intentional. The system is tight. |
| **Premium** | We signal quality through restraint — limited palette, generous whitespace, refined details like 1.5px borders. |
| **Warm** | Despite the precision, the brand feels human. Warm colors, warm surfaces, approachable language. |

---

## System Architecture

This design system is organized as a modular file family. Each file is self-contained but cross-referenced.

| File | Purpose |
|---|---|
| `BRAND.md` | This file. Router, identity, positioning. |
| `personality.md` | Voice, tone, language guidelines, personality traits. |
| `colors.md` | Full color token specification — light mode, dark mode, semantic mappings, print values. |
| `typography.md` | Type scale, font families, weights, tracking, hierarchy rules. |
| `design-language.md` | Composition patterns, shape system, photography treatment, motion, spacing, channel-specific rules. |

---

## Core Visual Signature

The Santos-Morales visual identity is built on three interlocking principles:

1. **Canvas-within-page** — Content lives inside a rounded-corner cream (light) or obsidian (dark) container that floats on a vermillion background, with a subtle noise grain texture on the surface. This creates depth, framing, and tactile warmth. The brand always feels like it exists inside a considered space.

2. **Typographic authority** — Display type is set at extreme sizes (80px–140px), extreme weights (800–900), and tight tracking (-0.03em to -0.06em). The type does the emotional heavy lifting. Photography and illustration are secondary.

3. **Disciplined palette** — Three colors maximum in any composition: Vermillion, a warm neutral (Cream or Obsidian depending on mode), and Taupe for muted states. The 60-30-10 rule governs all applications.

---

## Usage Notes for AI Agents

When generating designs, layouts, or code for Santos-Morales:

- **Always** use the exact hex values defined in `colors.md` — do not approximate.
- **Always** apply the canvas-within-page pattern as the outermost layout container.
- **Always** set display text in Helvetica Neue at weight 800 or 900 with negative letter-spacing. Exception: statistics and sequence numbers use weight 300–400 (see `typography.md`).
- **Never** introduce new colors outside the defined palette without explicit approval.
- **Never** use cool grays, pure black (#000000), or pure white (#FFFFFF) anywhere. Surfaces are always Cream (#EDEBD8) or Warm Obsidian (#1A1714).
- **Never** use decorative slashes or similar geometric motifs — these are not part of the Santos-Morales identity.
- **Prefer** vermillion as both text color (on light surfaces) and accent color. It serves dual duty.
- **Prefer** generous whitespace and large type over dense layouts.
- Photography must always be grayscale with `mix-blend-mode: multiply` applied over the surface color. See `design-language.md` for full spec.
