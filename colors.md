# Santos-Morales® — Color System

> **Parent file:** `BRAND.md`
> **Version:** 1.0

---

## Palette Overview

The Santos-Morales palette is intentionally constrained to three core colors plus their dark-mode counterparts. Every application follows the **60-30-10 rule** — no exceptions.

---

## Core Tokens

### Vermillion (Brand Color)
The constant. Vermillion does not change between light and dark mode. It is the single most recognizable element of the Santos-Morales identity.

| Property | Value |
|---|---|
| **Hex** | `#F15A30` |
| **RGB** | `241, 90, 48` |
| **HSL** | `13°, 87%, 57%` |
| **CMYK** | `0, 76, 86, 0` (print — verify with press proof) |
| **Pantone** | Pantone 172 C (nearest match — verify with swatch) |

**Hover/Pressed state:** `#D94B26` (darkened 10%)
**Disabled state:** `rgba(241, 90, 48, 0.3)`

### Cream (Light Surface)
The warm neutral for light mode surfaces. Must read as unmistakably warm/tan — never as white. Never use pure white (#FFFFFF) as a primary surface.

| Property | Value |
|---|---|
| **Hex** | `#EDEBD8` |
| **RGB** | `237, 235, 216` |
| **HSL** | `54°, 39%, 89%` |
| **CMYK** | `5, 3, 14, 0` |

### Warm Obsidian (Dark Surface)
The dark mode counterpart to Cream. A warm near-black with amber/brown undertones. Never use pure black (#000000) or cool grays.

| Property | Value |
|---|---|
| **Hex** | `#1A1714` |
| **RGB** | `26, 23, 20` |
| **HSL** | `30°, 13%, 9%` |

### Taupe (Muted)
Secondary text and subdued UI elements. Shifts between modes to maintain readable contrast.

| Property | Light Mode | Dark Mode |
|---|---|---|
| **Hex** | `#A29F8B` | `#6B6860` |
| **Role** | Muted text on cream | Muted text on obsidian |

### Elevated Surface
A subtle step up from the base surface for cards and containers. Must stay within the warm cream family — never pure white.

| Property | Light Mode | Dark Mode |
|---|---|---|
| **Hex** | `#E5E3D0` | `#242220` |
| **Role** | Card backgrounds | Card backgrounds |

---

## Semantic Token Mapping

These semantic tokens map to the core palette based on mode. Use semantic names in code — never hard-code hex values.

| Semantic Token | Light Mode | Dark Mode | Usage |
|---|---|---|---|
| `--color-surface` | `#EDEBD8` | `#1A1714` | Page/canvas background |
| `--color-surface-elevated` | `#E5E3D0` | `#242220` | Cards, modals, popovers |
| `--color-brand` | `#F15A30` | `#F15A30` | Accent, interactive elements, featured sections |
| `--color-brand-hover` | `#D94B26` | `#D94B26` | Hover/pressed state on brand elements |
| `--color-text-primary` | `#F15A30` | `#EDEBD8` | Primary body and heading text |
| `--color-text-muted` | `#A29F8B` | `#6B6860` | Secondary text, captions, metadata |
| `--color-border` | `rgba(241, 90, 48, 0.2)` | `rgba(245, 244, 236, 0.1)` | Dividers, card borders, separators |
| `--color-border-strong` | `rgba(241, 90, 48, 0.3)` | `rgba(245, 244, 236, 0.2)` | Active borders, grid gaps |
| `--color-bg-outer` | `#F15A30` | `#F15A30` | Body background (behind canvas) |
| `--color-on-brand` | `#EDEBD8` | `#EDEBD8` | Text on vermillion backgrounds |

---

## 60-30-10 Distribution

The ratio governs visual weight across any composition:

### Light Mode
| Ratio | Color | Role |
|---|---|---|
| **60%** | Cream `#EDEBD8` | Surfaces, backgrounds, whitespace |
| **30%** | Vermillion `#F15A30` | Text, headings, brand moments, featured sections |
| **10%** | Taupe `#A29F8B` | Muted text, secondary labels, subtle borders |

### Dark Mode
| Ratio | Color | Role |
|---|---|---|
| **60%** | Warm Obsidian `#1A1714` | Surfaces, backgrounds |
| **30%** | Cream `#EDEBD8` | Primary text, headings |
| **10%** | Vermillion `#F15A30` | Accent moments, CTAs, brand highlights |

Note: In dark mode, Vermillion shifts from being the primary text color (30%) to being the accent (10%), and Cream takes over as the primary text color. This is the key inversion.

---

## Color Inversion Pattern

Santos-Morales uses a signature **color inversion** for featured/highlighted content:

| Element | Default | Inverted (Featured) |
|---|---|---|
| Background | `--color-surface` | `--color-brand` (Vermillion) |
| Text | `--color-text-primary` | `--color-on-brand` (Cream) |
| Borders | `--color-border` | `rgba(237, 235, 216, 0.3)` |

This pattern is used for: featured case study cards, hero sections, stat bars, CTAs. It works identically in both light and dark modes because the vermillion background is constant.

---

## Border Colors

Borders in Santos-Morales are always semi-transparent, using the opposing surface color:

| Context | Value |
|---|---|
| **Light mode — subtle** | `rgba(241, 90, 48, 0.1)` |
| **Light mode — standard** | `rgba(241, 90, 48, 0.2)` |
| **Light mode — strong** | `rgba(241, 90, 48, 0.3)` |
| **Dark mode — subtle** | `rgba(237, 235, 216, 0.06)` |
| **Dark mode — standard** | `rgba(237, 235, 216, 0.1)` |
| **Dark mode — strong** | `rgba(237, 235, 216, 0.2)` |

---

## Scrollbar Colors

Custom scrollbar styling maintains brand consistency:

| Mode | Thumb | Track |
|---|---|---|
| **Light** | `rgba(241, 90, 48, 0.2)` | `transparent` |
| **Dark** | `rgba(237, 235, 216, 0.15)` | `transparent` |

---

## Accessibility Notes

| Pair | Contrast Ratio | WCAG |
|---|---|---|
| Vermillion on Cream | ~4.6:1 | AA ✓ |
| Cream on Vermillion | ~4.6:1 | AA ✓ |
| Taupe on Cream | ~2.7:1 | Use for large text / decorative only |
| Cream on Obsidian | ~14.2:1 | AAA ✓ |
| Vermillion on Obsidian | ~4.8:1 | AA ✓ |

**Note:** The deeper cream improves contrast with Vermillion to full AA compliance. Taupe on Cream remains marginal — use only for large text or decorative elements.

---

## Print Specifications

| Color | CMYK | Pantone (nearest) | Notes |
|---|---|---|---|
| Vermillion | `0, 76, 86, 0` | Pantone 172 C | Always proof on press — screen ≠ print |
| Cream | `3, 2, 7, 0` | Pantone 7527 C | On uncoated stock, may appear warmer |
| Taupe | `18, 18, 30, 8` | Pantone Warm Gray 6 C | Use for secondary text in print |

**Paper stock recommendation:** Uncoated warm white (e.g., Mohawk Superfine, French Paper Speckletone) — coated stock will make cream appear too clinical.

---

## Forbidden Colors

Do not introduce any of the following into Santos-Morales designs:

- Pure black `#000000` — use Warm Obsidian instead
- Pure white `#FFFFFF` — never use anywhere. Elevated surfaces use `#E5E3D0`
- Cool grays (any gray with blue undertone)
- Neon or saturated accent colors
- Gradients of any kind — the palette is flat
