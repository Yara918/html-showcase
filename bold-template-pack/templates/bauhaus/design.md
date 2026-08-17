---
version: alpha
name: Bauhaus (Geometric Poster)
description: A poster-language system in the Bauhaus tradition — primary-color circles, semicircles, triangles, and bars balanced against heavy geometric type on warm paper. Archivo Black carries every uppercase display headline; Inter handles body copy; Josefin Sans supplies a geometric voice for numerals and labels. Each slide is one strict asymmetric composition: content pushed to one side, a single dominant shape balancing the other.

colors:
  paper: "#F2EFE9"
  paper-deep: "#E9E4D8"
  white: "#FFFFFF"
  black: "#141414"
  red: "#D0342C"
  yellow: "#EAB308"
  blue: "#1F4FA3"
  cyan: "#2AA7C9"
  graphite: "#5A5A55"
  graphite-light: "#8A8A82"

color-aliases:
  c-bg: paper
  c-bg-light: white
  c-bg-cream: paper-deep
  c-fg: black
  c-fg-light: black
  c-fg-2: graphite
  c-fg-3: graphite-light
  c-accent: red
  c-border: black
  c-border-light: graphite

typography:
  display:
    fontFamily: "Archivo Black, Noto Sans SC, sans-serif"
    fontSize: 9vw
    fontWeight: 400
    lineHeight: 0.9
    letterSpacing: -0.02em
    textTransform: uppercase
  h1:
    fontFamily: "Archivo Black, Noto Sans SC, sans-serif"
    fontSize: 5.5vw
    fontWeight: 400
    lineHeight: 1.0
    letterSpacing: -0.01em
    textTransform: uppercase
  h2:
    fontFamily: "Archivo Black, Noto Sans SC, sans-serif"
    fontSize: 3.2vw
    fontWeight: 400
    lineHeight: 1.1
    textTransform: uppercase
  h3:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.7vw
    fontWeight: 600
    lineHeight: 1.3
  lead:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.4vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.7
  caption:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 0.85vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "Josefin Sans, Noto Sans SC, sans-serif"
    fontSize: 0.85vw
    fontWeight: 600
    letterSpacing: 0.28em
    textTransform: uppercase
  stat-value:
    fontFamily: "Archivo Black, Noto Sans SC, sans-serif"
    fontSize: 6.5vw
    fontWeight: 400
    lineHeight: 1.0
  outline-num:
    fontFamily: "Archivo Black, Noto Sans SC, sans-serif"
    fontSize: 14vw
    fontWeight: 400
    lineHeight: 0.9
  flow-num:
    fontFamily: "Josefin Sans, Noto Sans SC, sans-serif"
    fontSize: 3vw
    fontWeight: 700
    lineHeight: 1.0

spacing:
  pad-x: 6vw
  pad-y: 6vh
  gap-lg: 6vh
  gap-md: 3.5vh
  gap-sm: 1.8vh

canvas:
  width: 100vw
  height: 100vh

components:
  shape-circle:
    width: "min(38vw, 60vh)"
    height: "min(38vw, 60vh)"
    borderRadius: 50%
    background: "{colors.red}"
    description: "The dominant circle of a slide — one per slide, off-center, in a primary color. The system's most iconic element."
  shape-semicircle:
    width: "min(44vw, 66vh)"
    height: "min(22vw, 33vh)"
    borderRadius: "min(44vw, 66vh) min(44vw, 66vh) 0 0"
    background: "{colors.yellow}"
    description: "A semicircle built from 50% top radii — a Bauhaus 'arch' made of pure CSS."
  shape-triangle:
    clipPath: "polygon(50% 0, 100% 100%, 0 100%)"
    background: "{colors.blue}"
    description: "A triangle via clip-path polygon, filled with a primary color; usually cropped at the slide edge."
  shape-bar:
    width: "100%"
    height: 14vh
    background: "{colors.red}"
    description: "A full-bleed horizontal bar in a primary color, used as a ground for white display text or as a color break."
  rule-heavy:
    width: "100%"
    height: 5px
    background: "{colors.black}"
    description: "The 5px black rule — the system's structural signature, used under headlines and above foot bands."
  rule-hair:
    width: "100%"
    height: 1px
    background: "{colors.black}"
    description: "1px hairline rule for fine separations inside dense content and captions."
  color-field:
    background: "{colors.yellow}"
    description: "A full-bleed or half-bleed flat color rectangle; text on it flips to black or white by contrast."
  outlined-numeral:
    WebkitTextStroke: "2px {colors.black}"
    color: "transparent"
    fontFamily: "{typography.outline-num.fontFamily}"
    description: "A huge section numeral with transparent fill and a 2px black stroke via -webkit-text-stroke — the section-break signature."
  kicker-label:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.28em
    textTransform: uppercase
    color: "{colors.graphite}"
    description: "Tracked uppercase label above a headline; often preceded by a small 36px black square marker."
  index-number:
    fontFamily: "{typography.flow-num.fontFamily}"
    fontSize: "{typography.flow-num.fontSize}"
    color: "{colors.red}"
    description: "A Josefin Sans 700 index numeral (01, 02, 03) in primary red marking steps or sections."
  dot-grid:
    background: "radial-gradient(circle, {colors.black} 3px, transparent 3.5px)"
    backgroundSize: "24px 24px"
    description: "A pattern of 3px black dots generated by a two-stop radial-gradient tiled at 24px — used as a secondary texture field."
  img-block:
    border: "3px solid {colors.black}"
    background: "{colors.white}"
    description: "Image block with a 3px solid black frame and zero radius — the poster way to hold photography."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Bauhaus is a **poster system**, not a presentation system. The governing idea is the one the Bauhaus workshop taught a century ago: form follows function, and a composition is a set of visible tensions — shape against space, color against color, text against geometry — resolved on a flat plane. Every slide is treated as a printed poster at 1920×1080: a warm paper field, one dominant geometric figure in a primary color, and heavy geometric type set in strict asymmetry. There is no chrome, no footer furniture beyond a page mark, no elevation, no gradient, no rounded corner that isn't a circle. The slide is a piece of paper that happens to be displayed on a screen.

The color vocabulary is deliberately the Bauhaus triad — red `{colors.red}`, yellow `{colors.yellow}`, blue `{colors.blue}` — plus black, white, warm paper, and graphite for text. This is a radical restriction by presentation standards: most decks use color as a semantic highlighter, but here color is *form*. A red circle is not "highlighting" anything; it is the composition. Slides work because each one commits to a single dominant figure and a single dominant hue, and everything else — type, white space, rules — negotiates with that figure. When two primary colors appear on one slide, they appear as separate fields or shapes, never blended and never multiplied into a third color.

Typography carries the poster's voice. **Archivo Black** is a single-weight, extremely heavy grotesque — the closest common face to the poster lettering of the era without being a display-only revival. It is uppercase, tight-tracked, and used for every display moment. **Inter** is the quiet workhorse for body and leads; it must never compete with the display voice. **Josefin Sans** is the geometric voice for numerals and labels — its circular construction echoes the shapes on the slide, so every number and every kicker visually rhymes with the geometry. The result is a three-voice system with strict job descriptions, exactly like a print shop.

Composition is the discipline. The default layout pushes content to one side of the canvas and lets a single shape balance it from the other: text lower-left, circle upper-right; headline right, bar left. The rule is *asymmetry with balance* — never centered, never symmetric, never left-aligned-by-inertia. The grid exists but is felt, not drawn: content aligns to the 6vw gutter, and the shape is free to break the frame (bleed to the edge, crop the triangle, run the bar full-bleed). **Density philosophy: medium, poster-clean.** One idea per slide, one headline, one figure, generous air. A slide with two competing headlines and two shapes has failed — it is a page, not a poster.

**Key Characteristics:**
- Warm paper background (`{colors.paper}`) on most slides; full-bleed color-field slides (`{colors.red}`, `{colors.yellow}`, `{colors.blue}`) are the high-contrast moments.
- Exactly one dominant geometric figure per slide — circle, semicircle, triangle, or bar — in a primary color, placed off-center.
- Black 3–5px rules structure headlines and foot bands; 1px hairlines do the fine work.
- Every display headline is uppercase Archivo Black with tight or negative tracking.
- Section numerals are huge outlined glyphs (`-webkit-text-stroke: 2px black`, transparent fill).
- Josefin Sans supplies numerals and tracked uppercase labels; the label voice is tracked ≥ 0.25em.
- Strict asymmetric composition: content on one side, the shape balancing the other.
- Flat inks only — no shadows, no gradients except the dot-grid pattern, no elevation.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.paper}` | #F2EFE9 | Default slide surface — warm poster paper, never white |
| `{colors.paper-deep}` | #E9E4D8 | Slightly deeper paper for inset bands and caption strips |
| `{colors.white}` | #FFFFFF | Text on primary fields, and the inside of image blocks |
| `{colors.black}` | #141414 | All text, rules, borders, numerals — a soft black, not pure #000 |
| `{colors.red}` | #D0342C | Primary triad red — dominant shape, accent numeral, field slides |
| `{colors.yellow}` | #EAB308 | Primary triad yellow — dominant shape, field slides |
| `{colors.blue}` | #1F4FA3 | Primary triad blue — dominant shape, field slides |
| `{colors.cyan}` | #2AA7C9 | Rare fourth ink — only when a specific slide needs to break the triad, and never on two slides in a row |
| `{colors.graphite}` | #5A5A55 | Secondary text, kickers, captions |
| `{colors.graphite-light}` | #8A8A82 | Tertiary metadata, source notes |

### Defaults

- **Default surface background**: `{colors.paper}`. The warm paper is the poster ground; pure white is reserved for text-on-field and image insets.
- **Default primary headline color**: `{colors.black}` on paper; `{colors.white}` on primary-color fields.
- **Default body text color**: `{colors.black}`; muted secondary copy in `{colors.graphite}`.
- **Default accent color**: `{colors.red}` — the first among the triad and the default for index numerals and small markers.
- **Default border / rule color**: `{colors.black}`; the 5px rule is the structural signature, the 1px hairline the fine detail.
- **Default label color**: `{colors.graphite}`.
- **Default full-bleed field color**: `{colors.red}` or `{colors.yellow}` — these two carry most field slides; `{colors.blue}` is the colder, rarer choice.

### Semantic Notes

The triad is a closed system. Red, yellow, and blue are used as *form* — shapes and fields — and only secondarily as small accent marks (index numerals, square markers). Cyan is a documented exception, permitted when one slide in a deck genuinely needs a fourth voice; using it twice consecutively reads as a new palette rather than an exception. Black and white are structural, not decorative: black for every rule, numeral, and text run; white only where a primary field needs a text color. Graphite never appears in shapes — graphite is a text tone. The paper is deliberately warm (#F2EFE9) so that pure white elements — image blocks, type on fields — pop against it; a neutral gray paper would flatten that relationship.

## Typography

### Font Family

The system loads four faces: **Archivo Black** (weight 400 only — the face ships as a single heavy weight) for every display, headline, stat, and outline numeral; **Inter** (weights 400, 500, 600) for body, leads, and h3 sub-headlines; **Josefin Sans** (weights 400, 600, 700) for the geometric label and numeral voice; and **Noto Sans SC** as the CJK fallback behind all three.

The emotional register is deliberate:
- Archivo Black reads as **poster ink, printed, heavy, immediate**. Its single weight forces hierarchy through size — which is exactly what a poster wants. There is no "Archivo Black light"; there is only size.
- Inter reads as **quiet, modern, neutral** — the typographic equivalent of a blank wall in the workshop. It holds body copy without competing with the display voice.
- Josefin Sans reads as **geometric, circular, playful-precise** — its round letterforms mirror the circles and semicircles on the slide. It is the voice of numbers, indexes, and labels.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 9vw | Archivo Black | 400 | Cover poster headline — huge, uppercase, tight |
| `{typography.h1}` | 5.5vw | Archivo Black | 400 | Chapter-opening or section-break headline |
| `{typography.h2}` | 3.2vw | Archivo Black | 400 | Primary content-slide headline |
| `{typography.outline-num}` | 14vw | Archivo Black | 400 | Huge outlined section numeral (01, 02, 03) |
| `{typography.stat-value}` | 6.5vw | Archivo Black | 400 | Large numerical figure in a stat block |
| `{typography.flow-num}` | 3vw | Josefin Sans | 700 | Step numeral in a process diagram (01, 02…) |
| `{typography.h3}` | 1.7vw | Inter | 600 | Sub-headline, region heading, card title |
| `{typography.lead}` | 1.4vw | Inter | 400 | Lead paragraph or large bullet item |
| `{typography.body}` | 1.05vw | Inter | 400 | Body paragraph |
| `{typography.caption}` | 0.85vw | Inter | 400 | Image caption, source note, fine print |
| `{typography.label}` | 0.85vw | Josefin Sans | 600 | Kicker, chrome label, index label — uppercase, tracked 0.28em |

### Defaults

- **Default section headline**: `{typography.h2}` (3.2vw). `{typography.h1}` is for chapter breaks, `{typography.display}` for covers.
- **Default cover display**: `{typography.display}` (9vw).
- **Default body size**: `{typography.body}` (1.05vw).
- **Default lead size**: `{typography.lead}` (1.4vw) when a paragraph is the single supporting block under a headline.
- **Default label size**: `{typography.label}` (0.85vw at weight 600, tracked 0.28em).
- **Default stat readout**: `{typography.stat-value}` (6.5vw).

When unsure, the canonical pairing is `{typography.h2}` for the headline, one `{typography.lead}` paragraph, and a `{typography.label}` kicker above — set against one dominant shape.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every display, h1, h2, and label element is uppercase.** Sentence case in Archivo Black does not exist in this system; the poster voice is caps-only.
- **Every display headline carries negative or tight tracking** (−0.02em for display, −0.01em for h1).
- **Every section numeral is an outlined glyph**: transparent fill, `-webkit-text-stroke: 2px {colors.black}` — never solid-fill numerals at that size.
- **Every kicker and chrome label is Josefin Sans 600, uppercase, tracked ≥ 0.25em** (default 0.28em).
- **Every slide carries exactly one dominant geometric shape** in a primary color, off-center.
- **Structural rules are black**: 5px (`{components.rule-heavy}`) under headlines and above foot bands; 1px (`{components.rule-hair}`) for fine separation.
- **Index and flow numerals are Josefin Sans 700** — numbers never appear in Inter or in solid Archivo Black at small sizes.
- **Text on primary fields flips to `{colors.white}`; text on paper and on `{colors.yellow}` fields stays `{colors.black}`.** (Yellow has too little luminance contrast with white — see Colors.)

### Typography Principles

The rhythm of Bauhaus is **heavy caps + quiet sans body + geometric numerals**. Switching the display voice to a lighter weight (Archivo Black has none — don't fake it with Inter 700) reads as a different system. Setting a label in Inter rather than Josefin Sans breaks the number-label rhyme. Underlining does not exist; emphasis comes from size, color-field reversal, or the shape behind the text. Body text is never bolded — h3 at weight 600 is the heaviest body-adjacent moment.

## Layout

### Canvas System

The system targets a `100vw × 100vh` poster plane with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `slide-left`, `slide-right`, `scale-in`) are available with stagger delays via `data-delay` attributes, and shapes animate separately from text so the geometry can arrive on its own beat.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding — the poster margin |
| `{spacing.pad-y}` | 6vh | Slide vertical padding |
| `{spacing.gap-lg}` | 6vh | Between major sections (headline block → figure → foot band) |
| `{spacing.gap-md}` | 3.5vh | Between related blocks |
| `{spacing.gap-sm}` | 1.8vh | Between tightly related elements (label and headline, caption and image) |

The 6vw gutter is the only grid the system admits. Content columns align to it; shapes are free to bleed past it to the slide edge.

### Asymmetric Composition

The default composition is a two-zone poster: **content zone** (text, lists, stats) anchored to one side, **shape zone** (the dominant figure) occupying the other. Canonical arrangements:

- **Lower-left content, upper-right shape** — the workhorse: headline + lead in the lower-left third, a large circle or semicircle cropping the upper-right corner.
- **Left-aligned headline, full-bleed bar bottom** — a heavy `{components.shape-bar}` grounds the slide while type floats above it.
- **Right-aligned headline, triangle from the left edge** — the triangle cropped by the frame, text right-aligned into the space it leaves.

Never center. Never split the canvas into two symmetric halves. The shape is allowed to exit the frame (clip-path crops, full-bleed bars), which is what makes the composition feel like a poster crop rather than a centered infographic.

### Chrome Frame

Most content slides carry a minimal **foot band**: a 5px black rule, then a `flex space-between` row of two Josefin Sans tracked labels — section name on the left, `PAGE n` on the right, both in `{colors.graphite}`. Cover, color-field, and closing slides suppress the foot band entirely. There is no top header: the headline is the header, and the poster does not need a second one.

## Depth and Elevation

### Flat Inks Only

The system uses **zero box-shadow, zero elevation, zero blur**. Depth is created through four poster-native mechanisms:

1. **Overlap** — shapes sit *behind* text (negative z-index or DOM order), so type visually floats in front of a red circle or a blue triangle. This is the system's primary depth cue.
2. **Contrast layering** — white type on a primary field reads "front"; black type on paper reads "ground"; the outlined numeral at 60% of the canvas reads "background layer" through its transparency.
3. **Full-bleed fields** — a color-field slide has no depth at all; it is a flat sheet of ink, and the text on it is the only "object."
4. **The dot-grid pattern** (`{components.dot-grid}`) — a tiled radial-gradient of 3px black dots used as a secondary texture behind captions or on section-break slides; it is the only "texture" in the system and must be used at very low visual weight.

### No Atmospheric Effects

There are no gradients (except the dot-grid, which is a repeating pattern, not a wash), no glows, no grain, no glass. A gradient would immediately read as "web design" against the flat poster ground. If a slide needs atmosphere, it gets a larger shape and more paper, not a gradient.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every structural element — image blocks, fields, rules, buttons, stat blocks |
| 50% | Circles and semicircle curves only (`{components.shape-circle}`, `{components.shape-semicircle}`) |
| 999px (pill) | None — pills do not exist in the poster vocabulary |

The system is aggressively square. The only curves in the entire system belong to circles and semicircles — and those are drawn with 50% radii or the half-circle border trick, never with `border-radius` approximations on rectangles.

### Border Weights

- **5px solid `{colors.black}`** — the structural rule (`{components.rule-heavy}`): under headlines, above foot bands, as a vertical accent edge.
- **3px solid `{colors.black}`** — the frame weight: image blocks (`{components.img-block}`), poster frames on cover slides, thick shape outlines when a shape is drawn as a ring.
- **1px solid `{colors.black}`** — hairline separations inside dense content, captions, tables.
- There is no dashed border, no colored border. A shape's edge is its fill edge, not a border.

### Decorative Element Types

**Dominant circle** — `{components.shape-circle}`: `min(38vw, 60vh)` circle in a primary color, off-center, often cropped by the slide edge. Built with `border-radius: 50%`; if it must read as a ring, use a same-color inner circle via `::after`, never `border`.

**Semicircle (arch)** — `{components.shape-semicircle}`: a rectangle with `border-radius: min(44vw, 66vh) min(44vw, 66vh) 0 0`, filled `{colors.yellow}` or `{colors.blue}`. The classic poster "arch."

**Triangle** — `{components.shape-triangle}`: `clip-path: polygon(50% 0, 100% 100%, 0 100%)` on a filled rectangle, typically cropped at the frame edge so only two of its three points are visible.

**Full-bleed bar** — `{components.shape-bar}`: a 14vh-tall rectangle spanning the full width, in a primary color, used as a ground for white display text or as a pure color break between sections.

**Color field** — `{components.color-field}`: a full-bleed or half-bleed flat rectangle in a primary color; text on it flips to `{colors.white}` (red, blue) or `{colors.black}` (yellow).

**Outlined numeral** — `{components.outlined-numeral}`: `font-size: 14vw; color: transparent; -webkit-text-stroke: 2px {colors.black}`. Section-break slides show a single giant outline numeral as the entire composition.

**Kicker label** — `{components.kicker-label}`: Josefin Sans 600 uppercase tracked 0.28em in `{colors.graphite}`, optionally preceded by a small 36px solid black square marker (`width: 36px; height: 36px; background: {colors.black}`) — the square is the label's signature punctuation.

**Index numeral** — `{components.index-number}`: Josefin Sans 700 in `{colors.red}` — `01`, `02`, `03` markers for steps, chapters, and process flows.

**Dot grid** — `{components.dot-grid}`: `background: radial-gradient(circle, {colors.black} 3px, transparent 3.5px); background-size: 24px 24px`. Used as a subtle secondary texture, at low contrast, never behind body text.

**Image block** — `{components.img-block}`: a 3px solid black framed rectangle, zero radius, white ground, with the caption in `{typography.caption}` Inter below it.

**Geometric arrow** — A directional marker made of a 5px black bar plus a triangle head via `border-top/bottom/left` tricks — used only in process flows, where it must be the chunky poster arrow, never a thin chevron.

## Do's and Don'ts

### Do
- Keep the warm paper background (`{colors.paper}`) on all non-field slides. The poster ground is the system's surface identity.
- Place exactly one dominant geometric shape per slide, off-center, in a primary color.
- Set every display headline in uppercase Archivo Black with tight or negative tracking.
- Use the 5px black rule (`{components.rule-heavy}`) for structural separations and the 1px hairline for fine ones.
- Use Josefin Sans 600–700, uppercase, tracked ≥ 0.25em for every label, kicker, and index numeral.
- Render section numerals as outlined glyphs (`-webkit-text-stroke`) at 14vw.
- Flip text color on primary fields: white on red and blue, black on yellow.
- Let shapes bleed off the frame — a cropped circle or triangle reads as a poster crop, which is the goal.
- Use `{colors.cyan}` sparingly and only as a deliberate exception, never twice in a row.

### Don't
- Don't center compositions. Symmetry is the enemy of this system — every slide is an asymmetric two-zone balance.
- Don't use more than one dominant shape per slide. Two shapes and one headline is a page, not a poster.
- Don't introduce a gradient wash, box-shadow, or blur. Flat inks only; the dot-grid is the only texture.
- Don't use sentence case in Archivo Black — the caps rule is absolute for display voices.
- Don't set body copy in Archivo Black; Inter at 400 is the reading voice.
- Don't put labels in Inter or numerals in Inter — the Josefin Sans geometric voice owns numbers and labels.
- Don't use pure `#000` — the system black is `{colors.black}` (#141414), a soft ink that sits better on warm paper.
- Don't blend two primary colors into a third (no orange made of red+yellow, no purple made of red+blue) — the triad stays unmixed.
- Don't put white text on `{colors.yellow}` — luminance contrast is too low; yellow fields take black text.
- Don't use rounded rectangles or pills for buttons or tags; everything structural is 0px radius.

## Responsive Behavior

The system is viewport-fluid by design, with all sizes in `vw`/`vh` so the poster composition holds at any 16:9 viewport without breakpoints; per the Fixed-Stage Policy, the generated deck renders at a fixed 1920×1080 stage scaled uniformly, and the `vw`/`vh` values are treated as design proportions only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (`fade-up`, `fade-in`, `slide-left`, `slide-right`, `scale-in`) with stagger delays via `data-delay="N"` mapped to discrete steps (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Elements with `[data-anim]` start at `opacity: 0` and animate on `.is-active`; re-visiting a slide replays the entrance.
- Shapes animate independently of text — give the dominant figure its own `data-anim` (scale-in for circles, slide-right for bars) so geometry lands on a delayed beat.

### Print Behavior
The template declares no `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. Because the system is flat ink on paper-like fields, printed export is visually faithful — verify only that full-bleed fields extend to the printed page edge.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Archivo Black) | Archivo Black | Noto Sans SC (思源黑体) | 900 (the heaviest weight is the only match for Archivo Black's mass) |
| Body / lead (Inter) | Inter | Noto Sans SC (思源黑体) | 400 |
| Sub-headline (Inter 600) | Inter | Noto Sans SC (思源黑体) | 700 |
| Label / kicker (Josefin Sans) | Josefin Sans | Noto Sans SC (思源黑体) | 500 |
| Numerals / index (Josefin Sans 700) | Josefin Sans | Noto Sans SC (思源黑体) | 900 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Archivo Black, Noto Sans SC, sans-serif"` (or the Inter / Josefin Sans equivalent). Latin glyphs render in the primary face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed sentences like `设计 01 — 品牌概念` render as one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo+Black&family=Inter:wght@400;500;600&family=Josefin+Sans:wght@400;600;700&family=Noto+Sans+SC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.1–1.2
- Letter-spacing: 0 on CJK (the −0.02em tight tracking of Archivo Black must be reset for Chinese runs)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `品牌概念 OK` not `品牌概念OK`)
- One font per sentence

### Aesthetic Notes for This System

Bauhaus's defining trait is **Archivo Black — a single ultra-heavy weight.** Noto Sans SC's 900 is the only weight that carries comparable visual mass, and even then a Chinese display headline at 900 reads slightly lighter than Archivo Black because Han strokes distribute weight differently. Use Noto Sans SC 900 for Chinese display and accept a ~10% size increase to match the poster's presence — or, better, reduce the Latin size by ~10% when the headline is mixed so the two scripts sit at the same perceived mass.

The uppercase rule and the −0.02em tracking do not transfer to CJK. In a mixed headline like `品牌概念 — NEW FORM`, the Latin segment is capped and tracked while the Chinese segment stays as written with letter-spacing 0. Set the tracking only on the Latin span (`span[lang]`) — do not apply `text-transform` or `letter-spacing` to the CJK run.

The Josefin Sans label voice (0.28em tracking) is a Latin-specific device. For Chinese kickers, drop the tracking to 0 and rely on the small size plus the graphite color; a tracked Chinese label looks broken because each character already carries its own full-width rhythm.

The outlined numeral technique (`-webkit-text-stroke`) works with Chinese numerals and even with single characters, but a 2px stroke on dense Han glyphs can make counters close up at 14vw. Widen the stroke to 3px for pure-CJK outline numerals and verify legibility in the rendered screenshot.

### Known CJK Gap

Archivo Black at 9vw is a very wide Latin headline; a pure-Chinese display at Noto Sans SC 900 is even wider per character. Long Chinese headlines will wrap sooner than their Latin equivalents. Reduce pure-Chinese display to ~7.8vw and keep headlines short (≤ 8 characters per line) or accept the two-line wrap as a poster moment — a wrapped poster headline is historically accurate.

## Iteration Guide

1. Any new slide background is `{colors.paper}` — or a full-bleed primary field (`{colors.red}`, `{colors.yellow}`, `{colors.blue}`) for high-contrast moments. Never introduce a new surface color.
2. Any new headline uses uppercase Archivo Black at weight 400 — display (9vw), h1 (5.5vw), or h2 (3.2vw) — with tight or negative tracking.
3. Any new body or lead uses Inter at `{typography.body}` or `{typography.lead}` size, weight 400, in `{colors.black}` (or `{colors.white}` on red/blue fields).
4. Any new label, kicker, or index uses Josefin Sans 600–700, uppercase, tracked ≥ 0.25em, in `{colors.graphite}` (labels) or `{colors.red}` (index numerals).
5. Any new section numeral is an outlined glyph: transparent fill with `-webkit-text-stroke: 2px {colors.black}` at 14vw.
6. Any new slide gets exactly one dominant geometric shape in a primary color, placed off-center; shapes may bleed off the frame.
7. Any new structural separation is a 5px black rule; any fine separation is a 1px black hairline.
8. Compose asymmetrically: content zone on one side, shape zone on the other. Never center, never mirror.
9. Text on `{colors.red}` and `{colors.blue}` fields is `{colors.white}`; text on `{colors.yellow}` and paper is `{colors.black}`.
10. If a slide needs a fourth hue, `{colors.cyan}` is the only permitted exception — use it once, never twice in a row.

## Known Gaps

- Archivo Black ships as a single weight (400); all display hierarchy must come from size and color-field contrast — there is no lighter display fallback.
- The outlined numeral relies on `-webkit-text-stroke`, which is not supported in all rendering engines (notably some older Firefox builds); the fallback is a solid-fill numeral, which visually collapses the section-break signature. Verify in the target browser.
- `{colors.yellow}` (#EAB308) is close to the luminance of `{colors.white}`; text on yellow fields must be black, and this rule is easy to miss during generation — always flip it explicitly.
- The clip-path triangle and the semicircle radius trick require modern CSS; older engines render a rectangle. Both shapes are optional per-slide, but verify any slide that uses them.
- The dot-grid pattern at 3px dots / 24px tile is tuned for 1920×1080; at the fixed stage it is stable, but it was originally designed in viewport units and should be re-verified after stage scaling.
- The 5px rule reads as a hard band on dense content slides; when a slide carries a table or a multi-column list, prefer the 1px hairline between rows to keep the poster air.

---

## Related

This is a standalone design system in the `html-showcase` template library. For other aesthetics in the same pack, see the `ticker-console`, `gallery-label`, `riso-print`, and `washi` design docs.
