# Santos-Morales® — Typography

> **Parent file:** `BRAND.md`
> **Version:** 1.0

---

## Font Families

Santos-Morales uses a two-font system. No monospaced font is part of the brand identity.

### Display — Helvetica Neue

The typographic backbone of the brand. Used for all headings, hero text, statistics, and any element that needs to command attention.

```css
--font-display: "Helvetica Neue", Helvetica, Arial, sans-serif;
```

**Why Helvetica Neue:** It is authoritative without being decorative. It lets the weight, size, and tracking do the expressive work rather than relying on letterform personality. This aligns with the brand's "engineered precision" identity.

### UI — Inter

The workhorse for body text, navigation, labels, metadata, and interface elements. Clean, highly legible at small sizes, and stays out of the way.

```css
--font-ui: "Inter", -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
```

---

## Type Scale

### Display Scale (Helvetica Neue)

Used for headings, hero text, statistics, and brand moments. All display text uses negative letter-spacing.

| Token | Size | Weight | Tracking | Line Height | Transform | Usage |
|---|---|---|---|---|---|---|
| `--type-display-hero` | `140px` | `900` | `-0.06em` | `0.85` | capitalize | Homepage hero, landing pages |
| `--type-display-xl` | `120px` | `900` | `-0.06em` | `0.85` | capitalize | Section heroes (clamp: 60px–120px) |
| `--type-display-lg` | `96px` | `900` | `-0.06em` | `0.85` | capitalize | Featured article headlines |
| `--type-display-md` | `80px` | `900` | `-0.05em` | `0.85` | capitalize or uppercase | Page titles |
| `--type-display-sm` | `64px` | `900` | `-0.05em` | `0.90` | — | Featured card headlines |
| `--type-display-stat` | `72px` | `400` | `-0.03em` | `1.0` | — | Large statistics, metrics |
| `--type-display-stat-sm` | `48px` | `400` | `-0.03em` | `1.0` | — | Inline statistics |
| `--type-display-stat-xs` | `24px` | `400` | `-0.02em` | `1.0` | — | Small metric values |

### Heading Scale (Helvetica Neue)

Used for card titles, section headings, and editorial elements.

| Token | Size | Weight | Tracking | Line Height | Usage |
|---|---|---|---|---|---|
| `--type-heading-xl` | `48px` | `800` | `-0.03em` | `1.1` | Featured card titles |
| `--type-heading-lg` | `40px` | `800` | `-0.03em` | `1.1` | Phase titles, section names |
| `--type-heading-md` | `32px` | `800` | `-0.03em` | `1.1` | Card titles, editorial headlines |
| `--type-heading-sm` | `24px` | `800` | `-0.02em` | `1.1` | Sub-service titles, sidebar headings |
| `--type-heading-xs` | `18px` | `800` | `-0.02em` | `1.2` | Sticky card titles, footer notes |

### UI Scale (Inter)

Used for body copy, navigation, labels, and interface elements.

| Token | Size | Weight | Tracking | Line Height | Usage |
|---|---|---|---|---|---|
| `--type-body-lg` | `18px` | `400–500` | `0` | `1.4–1.6` | Hero descriptions, featured excerpts |
| `--type-body-md` | `16px` | `400` | `0` | `1.5–1.6` | Body copy, card descriptions |
| `--type-body-sm` | `14px` | `400–500` | `0` | `1.5–1.6` | Secondary body text, descriptions |
| `--type-nav` | `15px` | `500` | `0` | `1.0` | Navigation links |
| `--type-nav-active` | `15px` | `500–700` | `0` | `1.0` | Active navigation (underline or bold) |
| `--type-button` | `14px` | `600–700` | `0` | `1.0` | Button labels, CTAs |
| `--type-button-lg` | `18px` | `700` | `0` | `1.0` | Large CTA buttons |
| `--type-meta` | `13px` | `600` | `0` | `1.5` | Footer text, sidebar metadata |

### Label Scale (Inter or Helvetica Neue)

Used for category tags, filter chips, metadata, and uppercase micro-copy.

| Token | Size | Weight | Tracking | Line Height | Transform | Usage |
|---|---|---|---|---|---|---|
| `--type-label-lg` | `12px` | `700–800` | `0.10em` | `1.0` | uppercase | Category tags, filter labels |
| `--type-label-md` | `11px` | `700` | `0.05–0.15em` | `1.0` | uppercase | Meta tags, date labels, outcome labels |
| `--type-label-sm` | `10px` | `700` | `0.05–0.08em` | `1.0` | uppercase | Status badges, read times, smallest labels |

---

## Tracking Rules

Letter-spacing (tracking) is a core expressive tool in the Santos-Morales system:

| Context | Tracking | Rationale |
|---|---|---|
| Display text (40px+) | `-0.03em` to `-0.06em` | Tighter = more authoritative and monumental |
| Heading text (18px–40px) | `-0.02em` to `-0.03em` | Still tight, slightly more readable |
| Body text | `0` (default) | Inter's native spacing is optimized for reading |
| Uppercase labels | `+0.05em` to `+0.15em` | Wide tracking on small uppercase improves legibility |
| Logo wordmark | `-0.02em` | Consistent with brand identity |

**Rule:** Display type gets tighter as it gets larger. Label type gets wider as it gets smaller.

---

## Weight Usage

| Weight | Helvetica Neue | Inter | Usage |
|---|---|---|---|
| `300` | ✓ (sequence numbers) | — | Numbered sequences (01, 02...) at low opacity |
| `400` | ✓ (statistics) | ✓ | Statistics/metrics (Helvetica Neue), body text (Inter) |
| `500` | — | ✓ | Navigation, slightly emphasized body |
| `600` | ✓ (® mark only) | ✓ | Buttons, bold labels, editorial strong |
| `700` | — | ✓ | Active nav, CTAs, labels, read-more links |
| `800` | ✓ | ✓ (rare) | Headings, logo wordmark, card titles |
| `900` | ✓ | — | Display/hero text, statistics |

**Rule:** Helvetica Neue is almost always 800 or 900. Inter is almost always 400–700. Crossing these boundaries should be rare and intentional.

---

## Text Rendering

Always apply anti-aliasing for consistent rendering:

```css
-webkit-font-smoothing: antialiased;
-moz-osx-font-smoothing: grayscale;
```

---

## Responsive Type

For display text, use CSS `clamp()` to scale between viewport sizes:

```css
/* Example: Display XL */
font-size: clamp(60px, 8vw, 120px);
```

| Token | Mobile Min | Fluid | Desktop Max |
|---|---|---|---|
| `--type-display-hero` | `60px` | `10vw` | `140px` |
| `--type-display-xl` | `48px` | `8vw` | `120px` |
| `--type-display-md` | `40px` | `6vw` | `80px` |
| `--type-display-stat` | `36px` | `5vw` | `72px` |

Body and UI text does not scale fluidly — it uses fixed sizes with breakpoint adjustments.

---

## Hierarchy Rules

1. **One hero per page.** Only one element should use `--type-display-hero` or `--type-display-xl` on any given page.
2. **Max two levels of heading per section.** Don't stack more than two heading sizes in a single content section.
3. **Statistics are display type at thin weights.** Numbers and metrics always use Helvetica Neue but at weight 300–400 — never bold. This creates contrast with the heavy 800–900 headings beside them and gives numbers an elegant, refined quality. The size stays large; the weight stays light.
4. **Sequence numbers are lightweight.** Numbering (01, 02, 03...) uses Helvetica Neue at weight 300 with reduced opacity (0.15–0.2). They are structural markers, not focal points.
5. **Labels are always uppercase.** Any text under 13px that serves as a category, tag, or metadata must be uppercase with positive tracking.
6. **Navigation is Inter, never Helvetica Neue.** The nav stays functional, not expressive.
