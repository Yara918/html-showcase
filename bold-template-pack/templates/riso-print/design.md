---
version: alpha
name: Riso Print (Risograph Zine)
description: A tactile print-shop system modeled on Risograph printing — two or three flat ink colors per slide, coarse halftone dots, misregistered offset type, and paper grain. Anton condensed heavy display and Archivo body carry the zine voice; "+" registration marks, rotated collage cards, and ink fields make every slide read as a freshly printed sheet. Flat inks only, no shadows, no gradients — the paper is the texture.

colors:
  paper: "#FBF7EE"
  paper-deep: "#F3EDDD"
  riso-red: "#E8472F"
  riso-blue: "#2266CC"
  riso-yellow: "#FFCD00"
  riso-green: "#008A72"
  ink: "#2A2723"
  graphite: "#8A847A"

color-aliases:
  c-bg: paper
  c-bg-light: paper
  c-bg-cream: paper-deep
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite
  c-accent: riso-red
  c-border: ink
  c-border-light: graphite

typography:
  display:
    fontFamily: "Anton, Noto Sans SC, sans-serif"
    fontSize: 10vw
    fontWeight: 400
    lineHeight: 0.95
    letterSpacing: 0.01em
    textTransform: uppercase
  h1:
    fontFamily: "Anton, Noto Sans SC, sans-serif"
    fontSize: 6vw
    fontWeight: 400
    lineHeight: 1.0
    textTransform: uppercase
  h2:
    fontFamily: "Anton, Noto Sans SC, sans-serif"
    fontSize: 3.6vw
    fontWeight: 400
    lineHeight: 1.1
    textTransform: uppercase
  h3:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 1.7vw
    fontWeight: 600
    lineHeight: 1.3
  lead:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 1.4vw
    fontWeight: 500
    lineHeight: 1.55
  body:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.65
  caption:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 0.85vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 0.8vw
    fontWeight: 600
    letterSpacing: 0.22em
    textTransform: uppercase
  stat-value:
    fontFamily: "Anton, Noto Sans SC, sans-serif"
    fontSize: 7vw
    fontWeight: 400
    lineHeight: 1.0
  sticker:
    fontFamily: "Archivo, Noto Sans SC, sans-serif"
    fontSize: 1.1vw
    fontWeight: 600
    letterSpacing: 0.1em
    textTransform: uppercase

spacing:
  pad-x: 5vw
  pad-y: 5vh
  gap-lg: 5vh
  gap-md: 3vh
  gap-sm: 1.5vh

canvas:
  width: 100vw
  height: 100vh

components:
  halftone-panel:
    background: "radial-gradient(circle, {colors.ink} 2.5px, transparent 3px)"
    backgroundSize: "7px 7px"
    description: "Coarse halftone dot pattern — a tiled radial-gradient of 2.5px dots on a 7px grid — used for image and texture areas, printed in one ink color."
  misreg-headline:
    position: relative
    textShadow: "2px 2px 0 {colors.riso-blue}"
    description: "The signature misregistration: a display headline with its own ghost duplicated 2–4px away in a second ink color via text-shadow, simulating a press misregister."
  grain-overlay:
    filter: "url(#riso-grain)"
    pointerEvents: none
    description: "Paper-grain overlay driven by an inline SVG feTurbulence noise filter at low opacity, applied to the whole slide."
  registration-mark:
    content: "+"
    color: "{colors.ink}"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    description: "A '+' registration mark in the four corners of content slides — the print-shop version of a chrome frame."
  ink-field:
    background: "{colors.riso-yellow}"
    description: "A flat full-bleed ink field in a single process color; text on it flips to ink or paper by contrast."
  stamp:
    border: "2px solid {colors.riso-red}"
    padding: "0.4em 1em"
    transform: "rotate(-3deg)"
    fontFamily: "{typography.sticker.fontFamily}"
    color: "{colors.riso-red}"
    description: "A rotated bordered stamp label in a single ink color — used for tags, dates, and 'SPECIAL' markers."
  torn-edge:
    clipPath: "polygon(0 0, 100% 0, 100% 92%, 96% 88%, 92% 94%, 85% 87%, 78% 93%, 70% 88%, 62% 95%, 54% 89%, 46% 94%, 38% 87%, 30% 93%, 22% 88%, 15% 94%, 8% 89%, 0 93%)"
    description: "A torn-paper bottom edge built with an irregular clip-path polygon, used on section-break panels."
  zine-card:
    background: "{colors.paper}"
    border: "1px solid {colors.ink}"
    transform: "rotate(1.5deg)"
    description: "A collage card with a 1px ink border and a slight rotation — the zine grid tolerates and expects skew."
  index-num:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "1.4vw"
    fontWeight: 600
    color: "{colors.riso-blue}"
    description: "A large index numeral in a single ink color (01, 02, 03) marking steps and sections."
  ink-splotch:
    borderRadius: 50%
    background: "{colors.riso-green}"
    description: "A soft-edged ink circle — a solid dot with a feathered edge via a radial-gradient mask — placed as a print artifact behind collage elements."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Riso Print is a **print-shop system** built on the honest mechanics of Risograph printing: flat process inks, coarse halftone dots, misregistered offsets, and paper grain. A Risograph is a stencil duplicator that prints one translucent ink color per pass, so every real riso job is a layered object — red on top of yellow, blue shifted 3 millimeters from where it should be, dots and solids coexisting on cream paper. This system reproduces those mechanics in CSS, and the deck becomes a freshly printed zine: 1920×1080 sheets of warm paper with two or three inks per slide, everything slightly imperfect, everything tactile.

The premise is *imperfection as honesty*. Misregistration — the offset ghost behind a headline — is the system's signature move, and it is not a glitch: it is the visible evidence that the thing was printed, one ink at a time. The halftone dot pattern, the "+" registration marks in the corners, the paper-grain noise overlay, and the slight rotations on collage cards all serve the same fiction: this slide is a physical artifact that came off a machine, not a vector rendered on a screen. A perfectly crisp, perfectly aligned riso-style slide would be a lie about the medium.

Color is ink, not decoration. The palette is a short list of process colors — `{colors.riso-red}`, `{colors.riso-blue}`, `{colors.riso-yellow}`, `{colors.riso-green}` — plus ink black `{colors.ink}` and two paper tones. The discipline is **two to three inks per slide, maximum**. A slide using all four colors at once has broken the print run — real riso jobs limit inks because every pass costs money and time, and that economic honesty is part of the aesthetic. The accent is `{colors.riso-red}` by default; the others rotate by slide, but never more than three in one composition.

**Density philosophy: medium-high, but chaotic-intentional.** Riso zines are dense by nature — collage grids, overlapping cards, stamps, index numerals — yet the density must stay legible because the inks are flat and the paper is warm. The layout system is a collage grid: cards and blocks are allowed to overlap, rotate ±3°, and bleed off the frame, but each one must remain readable. The visual interest comes from arrangement, not from effects.

**Key Characteristics:**
- Cream paper (`{colors.paper}`) is the default ground on every slide; ink fields are full-bleed exceptions.
- Two to three flat ink colors per slide — never more, never blended.
- Misregistered display headlines: the headline is duplicated and offset 2–4px in a second ink color with `mix-blend-multiply` or layered `text-shadow`.
- Coarse halftone dots (`{components.halftone-panel}`) fill image and texture areas — 2.5px dots on a 7px grid.
- Paper grain via an inline SVG `feTurbulence` filter at low opacity, applied to the whole slide.
- "+" registration marks in the corners of content slides — the print-shop chrome.
- Flat inks only — no box-shadows, no gradients (except the dot pattern), no elevation.
- Zine collage compositions with slight rotations, overlapping cards, and stamps.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.paper}` | #FBF7EE | Default slide surface — warm cream print paper |
| `{colors.paper-deep}` | #F3EDDD | Deeper paper for inset panels and quote strips |
| `{colors.riso-red}` | #E8472F | Process red — default accent, stamps, misregistration ghost |
| `{colors.riso-blue}` | #2266CC | Process blue — index numerals, second ink, cool fields |
| `{colors.riso-yellow}` | #FFCD00 | Process yellow — fields, highlights, halftone areas |
| `{colors.riso-green}` | #008A72 | Process green — the rarest ink, for organic or eco-flavored moments |
| `{colors.ink}` | #2A2723 | Text and structural black — a warm dark brown-black, not pure #000 |
| `{colors.graphite}` | #8A847A | Secondary text, captions, registration marks when muted |

### Defaults

- **Default surface background**: `{colors.paper}`. Slides are sheets of cream paper; ink fields are the full-bleed exceptions.
- **Default text color**: `{colors.ink}` for primary copy; `{colors.graphite}` for secondary and captions.
- **Default accent color**: `{colors.riso-red}` — the first ink and the default for stamps, splotches, and misregistration ghosts.
- **Default field color**: `{colors.riso-yellow}` — yellow fields carry black ink text best.
- **Default border color**: `{colors.ink}` for zine-card borders; `{colors.riso-red}` for stamps.
- **Default halftone ink**: `{colors.ink}` for neutral texture; any single process color when the texture should carry hue.
- **Default ink budget**: three inks per slide maximum, counting the ink black as one.

### Semantic Notes

Riso inks are translucent process colors, and the system treats them as such: ink over paper reads lighter than the swatch, and two inks that overlap in a misregister read as a muddy overprint (that muddiness is *correct* — `mix-blend-multiply` reproduces it faithfully). Yellow is the loudest and lightest ink; it takes `{colors.ink}` text and never white text. Red and blue are the workhorse pair — red for warm energy, blue for index and data. Green is the deliberate rarity: it should appear at most once or twice in a deck, like a special fourth pass. The warm `{colors.ink}` (#2A2723) matters — a neutral black against warm paper looks digital, while the warm ink looks printed.

## Typography

### Font Family

The system loads three faces: **Anton** (weight 400 only — a condensed, all-caps poster grotesque) for every display, headline, and stat; **Archivo** (weights 400, 500, 600) for every body, lead, label, and sticker; and **Noto Sans SC** as the CJK fallback behind both.

The register is a print-shop pairing:
- Anton reads as **poster ink, condensed, shouting** — it has no lowercase by design, so uppercase is not a style choice but the face's nature. It is the type of zine covers and riso event posters.
- Archivo reads as **job printing, mechanical, straightforward** — a grotesque built for legibility at many weights; it holds body copy and labels without drama.
- Noto Sans SC is the Chinese fallback; Chinese display matches Anton's mass at weight 900 (see the CJK section).

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 10vw | Anton | 400 | Cover poster headline — enormous, condensed, offset-ghosted |
| `{typography.h1}` | 6vw | Anton | 400 | Chapter-opening or section-break headline |
| `{typography.h2}` | 3.6vw | Anton | 400 | Primary content-slide headline |
| `{typography.stat-value}` | 7vw | Anton | 400 | Large numerical figure in a stat block |
| `{typography.h3}` | 1.7vw | Archivo | 600 | Sub-headline, region heading, card title |
| `{typography.lead}` | 1.4vw | Archivo | 500 | Lead paragraph or large bullet item |
| `{typography.body}` | 1.05vw | Archivo | 400 | Body paragraph |
| `{typography.caption}` | 0.85vw | Archivo | 400 | Image caption, source note, zine fine print |
| `{typography.label}` | 0.8vw | Archivo | 600 | Kicker, index label — uppercase, tracked 0.22em |
| `{typography.sticker}` | 1.1vw | Archivo | 600 | Stamp text — uppercase, tracked 0.1em, often rotated |

### Defaults

- **Default section headline**: `{typography.h2}` (3.6vw). `{typography.h1}` is for chapter breaks; `{typography.display}` for covers.
- **Default cover display**: `{typography.display}` (10vw).
- **Default body size**: `{typography.body}` (1.05vw).
- **Default lead size**: `{typography.lead}` (1.4vw at weight 500).
- **Default label size**: `{typography.label}` (0.8vw at weight 600, tracked 0.22em).
- **Default stat readout**: `{typography.stat-value}` (7vw).

When unsure, the canonical pairing is an Anton `{typography.h2}` headline with a misregistration ghost, one `{typography.body}` paragraph, and an index numeral in a second ink — three inks, one idea.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every Anton display, h1, h2, and stat is uppercase** — the face has no lowercase; do not fight it.
- **Display headlines carry a misregistration ghost**: the headline text is duplicated and offset 2–4px in a second ink color. Implement with layered `text-shadow` (`2px 2px 0 {colors.riso-blue}`) or a positioned duplicate with `mix-blend-multiply`. The ghost is the system's signature and must appear on every display or h1 moment.
- **No more than three inks per slide**, counting ink black — a hard, visible budget.
- **Halftone dots fill image and texture areas** (`{components.halftone-panel}`), never body text zones.
- **"+" registration marks sit in the corners** of content slides (`{components.registration-mark}`).
- **Paper grain overlays every slide** via the inline SVG `feTurbulence` filter at low opacity.
- **Labels and kickers are Archivo 600 uppercase tracked ≥ 0.2em.**
- **Stamps are rotated** (`rotate(-3deg)` or similar) and carry a 2px single-ink border.
- **Flat inks only**: no box-shadow, no linear-gradient washes, no blur on text.

### Typography Principles

The rhythm of Riso Print is **condensed Anton shouts + Archivo job print + tracked labels**. The system tolerates — wants — typographic collisions: a stamp crossing a headline, a rotated card overlapping body text. The one thing it does not tolerate is hierarchy confusion: display is Anton, body is Archivo, and a body paragraph set in Anton would be unreadable. Emphasis comes from ink color, from the misregister ghost, and from the stamp, never from italics (Archivo italic exists but reads as a web convention here — avoid) and never from underlines.

## Layout

### Canvas System

The system targets a `100vw × 100vh` print sheet with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `stamp-in`, `rotate-in`, `slide-up`) are available with stagger delays via `data-delay` attributes.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 5vw | Slide horizontal padding — tighter than editorial systems, like a print margin |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 5vh | Between major collage groups |
| `{spacing.gap-md}` | 3vh | Between related blocks |
| `{spacing.gap-sm}` | 1.5vh | Between tightly related elements |

### Collage Grid

The layout system is a **collage grid**, not a column grid. Blocks — cards, text zones, plates, stamps — are absolutely or grid-positioned with deliberate overlap and slight rotation (0.5–3°). The rules that govern the collage:

- One anchor element per slide (usually the Anton headline) stays within 3° of upright; everything else may skew more.
- Overlap is allowed but must never bury an entire block — every element keeps at least one readable corner.
- Elements may bleed off the frame; a cropped card or stamp reads as a print sheet, not an accident.
- Cards use `{components.zine-card}`: warm paper fill, 1px ink border, small rotation.
- The registration marks in the corners act as the layout's outer frame; keep content inside them, bleeding elements excepted.

### Chrome Frame

The system's chrome is the print furniture. Content slides carry the four **"+" registration marks** (one per corner), a **stamp page number** (`NO. 03` in a rotated red-bordered stamp in a corner), and optionally a halftone strip at the foot. Cover and closing slides drop the registration marks and show a clean sheet with only the grain and the inks.

## Depth and Elevation

### Flat Inks, Print Depth

The system uses **zero box-shadow elevation**. Depth is created by the print-shop mechanics themselves:

1. **Misregistration** — the offset ghost behind a headline creates a 3D "plate shift" depth that no shadow can match; it is the system's primary depth cue.
2. **Overprint** — two inks overlapping through `mix-blend-multiply` produce a darker third region, which reads as physical layering.
3. **Halftone density** — a dot field denser than its surroundings reads as a darker, "closer" print area.
4. **Rotation and overlap** — rotated cards stacked on each other create physical collage depth.
5. **Paper grain** — the feTurbulence noise at 3–6% opacity gives the whole sheet a surface that catches light, the way real paper does.

### No Atmospheric Effects

There are no gradients (the halftone dot pattern is a repeating tile, not a wash), no glows, no blur, no glass. The grain is the only texture, and it is applied to the whole slide uniformly, never per-element. A drop shadow on a zine card would be the fastest way to break the print fiction — real riso prints have no shadows because they are flat ink on paper.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every structural element — cards, stamps, fields, image plates |
| 50% (circle) | Ink splotches (`{components.ink-splotch}`) and halftone dots only |
| 999px (pill) | None — pills do not exist in the print shop |

The system is square-cornered; even the stamps and cards are 0px rectangles. Circles belong to ink splotches and halftone dots, which are print artifacts, not UI elements.

### Border Weights

- **1px solid `{colors.ink}`** — zine-card borders and fine structural rules.
- **2px solid `{colors.riso-red}`** — stamp borders (`{components.stamp}`), the system's thickest border, in ink color only.
- There is no 3px+, no dashed border (except a dashed crop line inside dense diagrams), no colored structural border beyond the stamp.

### Decorative Element Types

**Halftone panel** — `{components.halftone-panel}`: `background: radial-gradient(circle, {colors.ink} 2.5px, transparent 3px); background-size: 7px 7px`. Coarse 3–5px dots; used for image placeholders, texture strips, and decorative fills, printed in one ink color. When the panel needs hue, swap the dot color for a process ink.

**Misregistered headline** — `{components.misreg-headline}`: the Anton headline with a ghost offset 2–4px in a second ink. Two implementations: layered `text-shadow: 2px 2px 0 {colors.riso-blue}, 0 0 0 {colors.ink}` or a duplicated text node with `mix-blend-multiply` and a 3px translate. The ghost must be visible but not muddy the letterforms.

**Paper grain** — `{components.grain-overlay}`: an inline SVG `<filter id="riso-grain">` with `feTurbulence` (baseFrequency ~0.9, numOctaves 2) and `feColorMatrix`, applied to a full-slide overlay at 3–6% opacity with `pointer-events: none`.

**Registration mark** — `{components.registration-mark}`: a "+" glyph in `{colors.ink}` mono-style label, placed in the four corners of content slides. These are the print-shop's alignment crosses; they double as the system's chrome.

**Ink field** — `{components.ink-field}`: a full-bleed flat rectangle in one process color. Text on red and blue fields flips to `{colors.paper}`; text on yellow stays `{colors.ink}`.

**Stamp** — `{components.stamp}`: a rotated bordered label (`2px solid {colors.riso-red}`, `rotate(-3deg)`) in Archivo 600 uppercase, used for tags, dates, and markers like `SPECIAL` or `NO. 03`.

**Torn edge** — `{components.torn-edge}`: an irregular `clip-path: polygon(...)` on a section-break panel, simulating a torn sheet bottom. Use once per section break maximum.

**Zine card** — `{components.zine-card}`: a warm-paper rectangle with a 1px ink border and slight rotation; the collage unit. Cards hold body text, quotes, or small stats.

**Index numeral** — `{components.index-num}`: a large Archivo 600 numeral in a single ink color (`01`, `02`, `03`) marking steps and sections; often set inside a halftone circle.

**Ink splotch** — `{components.ink-splotch}`: a soft-edged ink circle — a solid dot feathered with a radial-gradient mask — placed behind collage elements as a print artifact.

## Do's and Don'ts

### Do
- Keep the cream paper ground (`{colors.paper}`) on most slides; reserve full-bleed ink fields for high-contrast moments.
- Budget two to three inks per slide, counting ink black. Fewer is always acceptable.
- Add a misregistration ghost to every display and h1 headline — offset 2–4px in a second ink.
- Fill image and texture areas with coarse halftone dots.
- Put "+" registration marks in the corners of content slides.
- Apply the paper-grain overlay to every slide.
- Use rotated stamps and slightly rotated zine cards in the collage grid.
- Let elements overlap and bleed — the print sheet tolerates it.
- Flip text on ink fields: paper-white on red and blue, ink on yellow.

### Don't
- Don't use more than three inks on a slide — the budget is the discipline.
- Don't blend two inks into a decorative gradient; inks only overprint through `mix-blend-multiply` in misregistration.
- Don't use box-shadows, glows, or blur — flat ink only, and the grain is the only texture.
- Don't set body copy in Anton; Archivo is the reading voice.
- Don't use italics or underlines for emphasis; use ink color, the ghost, or a stamp.
- Don't put white text on `{colors.riso-yellow}` — yellow takes ink text.
- Don't align everything to a strict column grid; the collage grid expects skew and overlap.
- Don't use pure `#000` — the ink is `{colors.ink}` (#2A2723), a warm print black.
- Don't use rounded rectangles or pills for cards or buttons; everything structural is 0px.
- Don't set labels in sentence case or without tracking; labels are Archivo 600 caps tracked ≥ 0.2em.

## Responsive Behavior

The system is viewport-fluid by design, with all sizes in `vw`/`vh` so the print sheet holds at any 16:9 viewport without breakpoints; per the Fixed-Stage Policy, the generated deck renders at a fixed 1920×1080 stage scaled uniformly, and the `vw`/`vh` values are treated as design proportions only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (`fade-up`, `fade-in`, `stamp-in`, `rotate-in`, `slide-up`) with stagger delays via `data-delay="N"` mapped to discrete steps (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Elements with `[data-anim]` start at `opacity: 0` and animate on `.is-active`; re-visiting a slide replays the entrance.
- Use `stamp-in` (scale from 0.8 + slight rotation) for stamps and `rotate-in` for collage cards — the entrance should feel like things being placed on a print bed.

### Print Behavior
The template declares no `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. The grain overlay and halftone tiles survive PDF export well — verify only that the misregistration text-shadows and the feTurbulence filter render in the target PDF engine (some rasterizers drop SVG filters).

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Anton) | Anton | Noto Sans SC (思源黑体) | 900 (the only weight matching Anton's condensed mass) |
| Body / lead (Archivo) | Archivo | Noto Sans SC (思源黑体) | 400 |
| Sub-headline (Archivo 600) | Archivo | Noto Sans SC (思源黑体) | 700 |
| Label / kicker (Archivo 600) | Archivo | Noto Sans SC (思源黑体) | 700 |
| Sticker / stamp (Archivo 600) | Archivo | Noto Sans SC (思源黑体) | 700 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Anton, Noto Sans SC, sans-serif"` or `"Archivo, Noto Sans SC, sans-serif"`. Latin glyphs render in the primary face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed sentences like `活动海报 — FLYER 03` render as one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Archivo:wght@400;500;600;700&family=Noto+Sans+SC:wght@400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.7–1.8, display 1.05–1.15
- Letter-spacing: 0 on CJK (reset the 0.22em label tracking on Chinese runs)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `活动海报 FLYER` not `活动海报FLYER`)
- One font per sentence

### Aesthetic Notes for This System

Riso Print's defining trait is **Anton — a condensed, all-caps poster face with no CJK coverage.** Chinese display goes in **Noto Sans SC 900**, which is the only weight that carries comparable visual mass; the condensed shout becomes a dense black shout, which suits the zine voice. Accept that Chinese headlines are wider than Anton's compressed Latin — plan fewer characters per line rather than fighting the width.

The misregistration ghost works identically with Chinese characters — the offset duplicate in a second ink is script-agnostic and looks just as physical on Han glyphs. Keep the ghost on Chinese display headlines. The halftone panels, registration marks, stamps, and rotations all transfer without adjustment; they are print mechanics, not typography.

The uppercase rule and the 0.22em label tracking do not transfer to CJK. Chinese has no case, and tracking a Chinese label breaks its full-width rhythm — set Chinese labels in Noto Sans SC 700 with letter-spacing 0. The stamp's `text-transform: uppercase` applies only to its Latin segments; Chinese segments render as written.

### Known CJK Gap

Anton at 10vw is extremely wide for Latin; a pure-Chinese display at Noto Sans SC 900 is wider still per character. Reduce pure-Chinese display to ~8.5vw and keep headlines to ≤ 7 characters per line, or the headline wraps and the condensed-poster energy collapses. Also, dense Chinese body copy inside rotated zine cards can lose legibility — for Chinese cards, keep rotation under 2° and prefer `{colors.ink}` on `{colors.paper}` over any ink-field reversal.

## Iteration Guide

1. Any new slide background is `{colors.paper}` — or a single full-bleed ink field for a high-contrast moment.
2. Any new headline uses uppercase Anton at weight 400 — display (10vw), h1 (6vw), or h2 (3.6vw) — and carries a 2–4px misregistration ghost in a second ink.
3. Any new body or lead uses Archivo at `{typography.body}` or `{typography.lead}` size in `{colors.ink}`.
4. Any new label, kicker, or index numeral uses Archivo 600 uppercase tracked ≥ 0.2em, in `{colors.ink}` or a single ink color.
5. Any new stamp is a rotated bordered label with a 2px ink border, in one ink color.
6. Count the inks on every slide — two to three maximum, ink black included. Cut an ink before adding content.
7. Any new image or texture area is a halftone panel (`{components.halftone-panel}`) in one ink color.
8. Any new collage element is a `{components.zine-card}` with a 1px ink border and a slight rotation; overlap and bleed are allowed.
9. Content slides carry "+" registration marks in all four corners; cover and closing slides do not.
10. The grain overlay is applied once per slide, to the whole sheet, at 3–6% opacity — never per-element.

## Known Gaps

- Anton ships as a single weight (400) and has no lowercase; all display hierarchy comes from size and ink contrast.
- The misregistration text-shadow is position-tuned: on very large display sizes the 2px offset can read as a blur rather than a plate shift — verify at 10vw and widen the offset to 3–4px for covers.
- The `feTurbulence` grain filter is dropped by some PDF rasterizers; printed export may lose the paper texture even though the slide looks correct on screen.
- The ink budget (three inks per slide) is a design rule, not a CSS rule; nothing enforces it mechanically, so it must be checked per slide during generation.
- `mix-blend-multiply` overprint requires a compositing-capable browser; older engines render the second ink as a solid layer instead of a translucent overprint.
- The collage grid's rotations and overlaps are tuned for 1920×1080; after stage scaling, re-verify that no rotated card's corner collides with a registration mark on dense slides.

---

## Related

This is a standalone design system in the `html-showcase` template library. For other aesthetics in the same pack, see the `ticker-console`, `bauhaus`, `gallery-label`, and `washi` design docs.
