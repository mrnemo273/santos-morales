# Santos-Morales® — Design Language

> **Parent file:** `BRAND.md`
> **Version:** 1.0

---

## Composition Patterns

### Canvas-Within-Page (Primary Layout)

The foundational layout device of Santos-Morales. All content lives inside a rounded container that floats on a vermillion background. This creates depth, framing, and a sense of intentional space.

```
┌──────────────────────────────────────────┐
│  Vermillion body (#F15A30)               │
│  padding: 2vw                            │
│  ┌────────────────────────────────────┐  │
│  │  Cream canvas (#F5F4EC)            │  │
│  │  border-radius: 24px              │  │
│  │  max-width: 1600px                │  │
│  │  height: calc(100vh - 4vw)        │  │
│  │                                    │  │
│  │  [Header]                          │  │
│  │  [Content]                         │  │
│  │                                    │  │
│  └────────────────────────────────────┘  │
└──────────────────────────────────────────┘
```

| Property | Value |
|---|---|
| Body background | `--color-bg-outer` (Vermillion) |
| Body padding | `2vw` all sides |
| Canvas background | `--color-surface` |
| Canvas border-radius | `24px` (`--radius-lg`) |
| Canvas max-width | `1600px` (default) |
| Canvas height | `calc(100vh - 4vw)` or fixed `960px` |
| Canvas overflow | `hidden` on outer, `auto` on scroll container |
| Canvas shadow | `0 40px 100px rgba(0,0,0,0.1)` or `0 0 0 1px rgba(0,0,0,0.05)` |

**Dark mode:** Canvas becomes Warm Obsidian `#1A1714`. Body stays Vermillion. The pattern is identical.

### Surface Texture (Noise Grain)

All canvas surfaces carry a subtle noise texture to create a tactile, paper-like quality. This is applied as a `::before` pseudo-element on the canvas container.

```css
.canvas::before {
    content: '';
    position: absolute;
    inset: 0;
    border-radius: var(--radius-lg);
    background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 256 256' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='noise'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noise)'/%3E%3C/svg%3E");
    background-size: 200px 200px;
    opacity: 0.03;
    pointer-events: none;
    z-index: 0;
    mix-blend-mode: multiply;
}
```

| Property | Value |
|---|---|
| Opacity | `0.03` (barely perceptible — felt more than seen) |
| Blend mode | `multiply` (light mode), `screen` (dark mode) |
| Tile size | `200px` |
| Filter | `fractalNoise`, baseFrequency `0.9`, 4 octaves |

**Important:** All direct children of `.canvas` must have `position: relative; z-index: 1;` to sit above the noise layer.

### Header (Global Navigation)

Always a three-column grid: logo left, navigation center, CTA right.

```css
.header {
    display: grid;
    grid-template-columns: 1fr auto 1fr;
    align-items: center;
    padding: 24px 40px;
    border-bottom: var(--border-width) solid var(--color-border);
}
```

| Element | Spec |
|---|---|
| Logo | Helvetica Neue, 22px, weight 800, tracking -0.02em |
| Nav links | Inter, 15px, weight 500, 24px gap |
| Active nav | Underline with `text-underline-offset: 4px` OR `font-weight: 700` with `border-bottom: 2px solid` |
| CTA button | Vermillion bg, cream text, 12px 24px padding, 8px radius |
| Header border | `--color-border` (1.5px) |

### Content Grid Patterns

Santos-Morales uses several recurring grid layouts:

**Featured + Grid (Case Studies)**
```
┌──────────────────────┬───────────┐
│                      │           │
│  Featured (span 2)   │  Card     │
│                      │           │
├───────────┬──────────┼───────────┤
│           │          │           │
│  Card     │  Card    │  Card     │
│           │          │           │
└───────────┴──────────┴───────────┘
```

**Split Content (Insights)**
```
┌──────────────────┬─────────────┐
│                  │  List item  │
│  Featured hero   ├─────────────┤
│  (1.5fr)         │  List item  │
│                  ├─────────────┤
│                  │  List item  │
└──────────────────┴─────────────┘
```

**Content + Sidebar (Services)**
```
┌──────────────────────┬──────────┐
│                      │          │
│  Main content        │  Sticky  │
│  (services list)     │  card    │
│                      │          │
└──────────────────────┴──────────┘
grid-template-columns: 1fr 320px;
gap: 80px;
```

### Vermillion-Gap Grid

A signature technique where the grid container uses vermillion as background-color, and cells use the surface color. The gap between cells (set to `--border-width`) reveals the vermillion underneath, creating bordered cells without explicit border properties.

```css
.grid {
    display: grid;
    gap: var(--border-width);                    /* 1.5px */
    background-color: rgba(241, 90, 48, 0.3);   /* or --color-brand */
    border: var(--border-width) solid rgba(241, 90, 48, 0.3);
    border-radius: var(--radius-sm);
    overflow: hidden;
}
.grid > .cell {
    background-color: var(--color-surface);
}
```

---

## Shape System

### Border Radius

| Token | Value | Usage |
|---|---|---|
| `--radius-lg` | `24px` | Canvas container, major sections |
| `--radius-sm` | `16px` | Cards, inner containers, images, stat bars |
| `--radius-button` | `8px` | Standard buttons |
| `--radius-button-lg` | `12px` | Large CTA buttons |
| `--radius-pill` | `100px` | Filter chips, category pills |
| `--radius-avatar` | `50%` | Author avatars, circular elements |
| `--radius-icon-lg` | `40px` | Large icon containers (service hero) |

### Border Width

The brand uses a single border width across all elements:

| Token | Value | Notes |
|---|---|---|
| `--border-width` | `1.5px` | Thinner than the typical 1px or 2px — this is a subtle brand signature |

### Shape Principles

- **No sharp corners.** Every container, card, and interactive element has border-radius applied.
- **No gradients.** All surfaces are flat, solid colors.
- **No drop shadows on cards.** Cards are defined by borders, not elevation. The only shadow is on the canvas container itself.
- **Circular elements** are used for: arrow buttons (48px diameter, 2px border), author avatars (32px), status dots (6–8px).

---

## Photography Treatment

### Grayscale + Multiply

All photography in the Santos-Morales system is presented in grayscale with a multiply blend mode over the surface color. This ensures images never introduce off-brand colors and feel integrated into the palette.

```css
.photo {
    filter: grayscale(100%);
    mix-blend-mode: multiply;
}
```

**On Cream surfaces:** The multiply blend produces a warm, sepia-tinted effect. Vermillion tones in the underlying surface bleed through subtly.

**On Vermillion surfaces:** The multiply blend creates a deep, dramatic duotone where the photo takes on the full vermillion character.

**On Dark surfaces:** Convert to grayscale and use `mix-blend-mode: screen` instead of multiply to maintain visibility.

```css
/* Dark mode variant */
.photo--dark {
    filter: grayscale(100%);
    mix-blend-mode: screen;
    opacity: 0.7;
}
```

### Photography Style

| Guideline | Rule |
|---|---|
| Subject matter | Architecture, workspaces, hands-at-work, abstract textures |
| Framing | Considered, editorial — not candid or lifestyle |
| People | Avoid faces when possible; show hands, posture, silhouettes |
| Contrast | High contrast originals work best with multiply/screen |
| Resolution | Minimum 2x for retina displays |

### Image Containers

Photos are always contained within rounded-rect frames:

```css
.image-container {
    border-radius: var(--radius-sm);  /* 16px */
    overflow: hidden;
    aspect-ratio: 16 / 9;            /* default, can vary */
}
```

---

## Iconography

Santos-Morales does not use a traditional icon set. Visual accents are limited to:

| Element | Spec |
|---|---|
| **Arrow icons** | Simple stroke arrows, 2–2.5px stroke weight, used in circular containers |
| **Geometric shapes** | Star (4-point), circle, vesica piscis — used at large scale (120px+), low opacity (0.1–0.2), as background decoration |
| **Status dots** | Solid circles, 6–8px, used for active indicators |
| **Dot lists** | 8px solid circles in vermillion, used instead of traditional bullet points |

**No filled icon sets.** No Phosphor, Lucide, or similar. The brand relies on type and color, not iconography.

---

## Motion & Animation

### Easing Curves

Santos-Morales uses two signature easing curves:

| Token | Value | Usage |
|---|---|---|
| `--ease-out-expo` | `cubic-bezier(0.16, 1, 0.3, 1)` | Card hover transitions, major state changes |
| `--ease-out-quint` | `cubic-bezier(0.19, 1, 0.22, 1)` | Logo entrance, loading animations |
| `--ease-standard` | `cubic-bezier(0.4, 0, 0.2, 1)` | General UI transitions |

### Duration Scale

| Token | Value | Usage |
|---|---|---|
| `--duration-fast` | `0.2s` | Hover states, opacity changes, button feedback |
| `--duration-medium` | `0.3s` | Card transforms, arrow rotations |
| `--duration-slow` | `0.4s` | Color transitions (background-color on hover) |
| `--duration-entrance` | `0.8s–1.0s` | Page entrance animations, logo fade-in |
| `--duration-progress` | `2.5s` | Loading bar, progress animations |

### Interaction Patterns

| Interaction | Animation |
|---|---|
| **Card hover** | `translateY(-4px)` or `translateY(-5px)` at `--duration-medium` with `--ease-out-expo` |
| **Button hover** | `translateY(-1px)` or `scale(1.02)` at `--duration-fast` |
| **Arrow hover** | `rotate(-45deg)` or `rotate(45deg)` at `--duration-medium` |
| **List item hover** | `translateX(10px)` at `--duration-fast` |
| **Color inversion** | Background-color transition at `--duration-slow` with `--ease-out-expo` |
| **Logo entrance** | Opacity 0→1 + translateY(20px→0) at `--duration-entrance` with `--ease-out-quint` |
| **Loading bar** | Width 0%→100% at `--duration-progress` with `cubic-bezier(0.65, 0, 0.35, 1)` (ease-in-out-cubic) |

### Motion Principles

- **Subtle over dramatic.** Maximum translate is 10px. No bounces, no spring physics.
- **Vertical for emphasis.** Cards lift up on hover (translateY negative).
- **Horizontal for navigation.** List items slide right on hover (translateX positive).
- **No parallax.** No scroll-triggered animations. The brand is confident enough to be still.

---

## Spacing System

### Base Unit

All spacing is derived from a **4px base unit**:

| Token | Value | Usage |
|---|---|---|
| `--space-1` | `4px` | Tight internal padding (logo sup offset) |
| `--space-2` | `8px` | Icon gaps, small internal spacing |
| `--space-3` | `12px` | Chip padding, small element gaps |
| `--space-4` | `16px` | Standard internal padding, heading margins |
| `--space-6` | `24px` | Section padding, nav gaps, card internal spacing |
| `--space-8` | `32px` | Card padding, detail card internal spacing |
| `--space-10` | `40px` | Page content padding, major section gaps |
| `--space-12` | `48px` | Large button padding block |
| `--space-15` | `60px` | Section margins, content layout gaps |
| `--space-20` | `80px` | Major content layout gaps, vertical rhythm |
| `--space-25` | `100px` | Large vertical spacing between major sections |

### Padding Conventions

| Element | Padding |
|---|---|
| Canvas body padding | `2vw` (responsive) |
| Content container | `40px` all sides |
| Standard card | `32px–40px` |
| Button (standard) | `12px 24px` |
| Button (large) | `24px 48px` |
| Filter chip | `8px 16px` or `6px 16px` |
| Header | `24px 40px` |

---

## Channel-Specific Rules

### Web

| Property | Spec |
|---|---|
| Max content width | `1600px` |
| Breakpoints | `480px` (mobile), `768px` (tablet), `1024px` (desktop), `1440px` (wide) |
| Min canvas height | `800px` |
| Font loading | Inter via Google Fonts or self-hosted; Helvetica Neue via system fonts |
| Anti-aliasing | Always apply `-webkit-font-smoothing: antialiased` |
| Scrollbar | Custom-styled (see `colors.md`) |

### Print

| Property | Spec |
|---|---|
| Paper stock | Uncoated warm white recommended |
| Minimum logo size | 20mm wide |
| Logo clear space | 1x height of "S" in Santos on all sides |
| Color mode | CMYK values in `colors.md` |
| Body text minimum | 9pt Inter or equivalent |
| Display text | Helvetica Neue, same weight/tracking rules as digital |

### Social Media

| Format | Canvas Treatment |
|---|---|
| Square post (1080×1080) | Full vermillion background, centered cream rounded-rect at ~90% width, content inside |
| Story (1080×1920) | Same pattern, vertical orientation |
| Avatar/Profile | Vermillion circle with cream "SM" initials (Helvetica Neue, 800) |
| Banner/Cover | Full-bleed vermillion with cream display type, no canvas container |
| LinkedIn article | Use the color inversion pattern — vermillion header hero, cream body |

### Email

| Element | Spec |
|---|---|
| Header | Santos-Morales® wordmark in vermillion, left-aligned |
| Body font | Inter (with system fallbacks) at 16px |
| Accent | Vermillion for links and CTAs |
| Background | Cream `#F5F4EC` — never pure white |
| CTA button | Vermillion bg, cream text, 8px radius |

---

## Component Patterns

### Cards

| Variant | Background | Border | Hover | Content |
|---|---|---|---|---|
| **Standard** | `--color-surface` | `--color-border` at `--radius-sm` | `translateY(-4px)` + border darkens | Tag, headline, metric, arrow |
| **Featured** | `--color-brand` | none | background darkens to `#D94B26` | Same content, cream text |
| **Empty/Placeholder** | transparent | `2px dashed --color-text-muted` | border and bg darken slightly | Title + status badge |
| **Sticky sidebar** | `--color-surface-elevated` | `--color-border` | none (static) | Title, description, CTA, status |

### Buttons

| Variant | Background | Text | Padding | Radius | Hover |
|---|---|---|---|---|---|
| **Primary** | `--color-brand` | `--color-on-brand` | `12px 24px` | `8px` | `translateY(-1px)` + darken |
| **Primary Large** | `--color-brand` | `--color-on-brand` | `24px 48px` | `12px` | `scale(1.02)` |
| **Circle Arrow** | transparent | current | `0` (48×48) | `50%` | `rotate(-45deg)` + fill brand |

### Filter Chips / Pills

```css
.chip {
    padding: 8px 16px;
    border: var(--border-width) solid var(--color-brand);
    border-radius: 100px;
    font-size: 12px;
    font-weight: 600;
    text-transform: uppercase;
}
.chip.active {
    background: var(--color-brand);
    color: var(--color-on-brand);
}
```

### Stat / Outcomes Bar

A full-width vermillion section displaying 3 key metrics in a row:

```css
.outcomes-bar {
    background-color: var(--color-brand);
    border-radius: var(--radius-sm);
    padding: 40px;
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: 40px;
    color: var(--color-on-brand);
}
```

Stat values use `--type-display-stat-sm` (48px, weight 400 — always thin). Labels use `--type-label-lg`. The contrast between lightweight numbers and heavy uppercase labels is a key brand signature.
