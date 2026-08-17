---
version: alpha
name: Washi (Sumi Ink & Paper)
description: A quiet system of Japanese minimalism — warm washi paper, sumi ink, and generous emptiness. Zen Old Mincho carries display and seal type; Zen Kaku Gothic New handles body copy; an enormous single character or a solid vermillion hanko seal provides the sole accent per slide. Extreme margins, thin 1px sumi rules, optional vertical text, and asymmetric balance make each slide a folio page rather than a presentation frame.

colors:
  washi-paper: "#F5F1E6"
  paper-light: "#FAF7EF"
  paper-deep: "#EDE6D6"
  sumi-ink: "#1F1D1A"
  graphite: "#7A746A"
  graphite-light: "#A39C90"
  vermillion: "#B3402A"
  moss: "#6B6B5C"
  gold: "#A98F5F"

color-aliases:
  c-bg: washi-paper
  c-bg-light: paper-light
  c-bg-cream: paper-deep
  c-fg: sumi-ink
  c-fg-light: sumi-ink
  c-fg-2: graphite
  c-fg-3: graphite-light
  c-accent: vermillion
  c-border: sumi-ink
  c-border-light: graphite-light

typography:
  display:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 8vw
    fontWeight: 700
    lineHeight: 1.1
  h1:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 4.5vw
    fontWeight: 700
    lineHeight: 1.25
  h2:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 2.8vw
    fontWeight: 700
    lineHeight: 1.35
  h3:
    fontFamily: "Zen Kaku Gothic New, Noto Sans SC, sans-serif"
    fontSize: 1.6vw
    fontWeight: 500
    lineHeight: 1.5
  lead:
    fontFamily: "Zen Kaku Gothic New, Noto Sans SC, sans-serif"
    fontSize: 1.35vw
    fontWeight: 300
    lineHeight: 1.8
  body:
    fontFamily: "Zen Kaku Gothic New, Noto Sans SC, sans-serif"
    fontSize: 1.02vw
    fontWeight: 300
    lineHeight: 1.9
  caption:
    fontFamily: "Zen Kaku Gothic New, Noto Sans SC, sans-serif"
    fontSize: 0.8vw
    fontWeight: 300
    lineHeight: 1.7
  label:
    fontFamily: "Zen Kaku Gothic New, Noto Sans SC, sans-serif"
    fontSize: 0.72vw
    fontWeight: 400
    letterSpacing: 0.25em
    textTransform: uppercase
  seal-char:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 3.2vw
    fontWeight: 700
    lineHeight: 1.0
  vertical-run:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 2.2vw
    fontWeight: 500
    lineHeight: 1.6
    writingMode: vertical-rl
  stat-value:
    fontFamily: "Zen Old Mincho, Noto Serif SC, serif"
    fontSize: 5vw
    fontWeight: 700
    lineHeight: 1.1

spacing:
  pad-x: 12vw
  pad-y: 10vh
  gap-lg: 7vh
  gap-md: 4vh
  gap-sm: 2vh

canvas:
  width: 100vw
  height: 100vh

components:
  ghost-kanji:
    color: "color-mix(in srgb, {colors.sumi-ink} 7%, {colors.washi-paper})"
    fontSize: "min(34vw, 56vh)"
    fontFamily: "{typography.display.fontFamily}"
    description: "An enormous single kanji/Chinese character at 6–8% ink opacity, placed behind the content — the system's signature background graphic."
  hanko-seal:
    width: "min(7vw, 10vh)"
    height: "min(7vw, 10vh)"
    background: "{colors.vermillion}"
    color: "{colors.paper-light}"
    borderRadius: 6px
    fontFamily: "{typography.seal-char.fontFamily}"
    fontSize: "{typography.seal-char.fontSize}"
    description: "The vermillion hanko seal — a solid square with a single white character, the system's sole strong accent."
  sumi-rule:
    width: "100%"
    height: 1px
    background: "{colors.sumi-ink}"
    description: "The thin 1px sumi rule, used sparingly under headlines and around foot zones."
  vertical-text:
    writingMode: vertical-rl
    fontFamily: "{typography.vertical-run.fontFamily}"
    fontSize: "{typography.vertical-run.fontSize}"
    description: "A vertical text run set with writing-mode: vertical-rl, reading top-to-bottom right-to-left, placed in the right margin."
  paper-texture:
    filter: "url(#washi-grain)"
    pointerEvents: none
    description: "Subtle washi texture via an inline SVG feTurbulence filter at low opacity, applied to the whole slide."
  moss-tag:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.2em
    textTransform: uppercase
    color: "{colors.moss}"
    description: "A quiet moss-green label tag for chapters and metadata — the system's neutral accent."
  gold-line:
    width: 36px
    height: 1px
    background: "{colors.gold}"
    description: "A rare 36px gold hairline, reserved for moments that need a whisper of warmth."
  index-mark:
    content: "・"
    color: "{colors.vermillion}"
    fontFamily: "{typography.body.fontFamily}"
    description: "A small vermillion nakaguro (・) used as the list marker — the Japanese middle dot replacing the Latin bullet."
  zen-quote:
    fontFamily: "{typography.h2.fontFamily}"
    fontSize: "{typography.h2.fontSize}"
    color: "{colors.graphite}"
    lineHeight: 1.5
    description: "A short serif reflection in graphite, set large with generous line height — the system's quote voice."
  folio-mark:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.25em
    color: "{colors.graphite-light}"
    description: "The folio page mark in the lower-left corner — page number and section, in the quietest ink."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Washi is a system of **Japanese minimalism in the wabi-sabi register** — a deck that behaves like a folio of washi paper brushed with sumi ink. The governing idea is *ma* (間): the meaningful emptiness between things. Every slide is 1920×1080 of warm paper `{colors.washi-paper}` with a small, precisely placed amount of content, an enormous faint character breathing behind it, and one deliberate accent. The system is not "minimalist" in the sense of clean corporate restraint — it is minimal in the Zen sense: everything that does not need to be there has been removed, and what remains carries weight.

The typographic voice is CJK-first, which is unusual in this library and deliberate. **Zen Old Mincho** — a Japanese serif with strong brush heritage — carries every display, headline, seal character, and vertical run. **Zen Kaku Gothic New** at weight 300 carries body copy with the quiet regularity of a kaku-gothic sans. Latin text is the guest in this system: it renders through the same faces (Zen Old Mincho includes Latin glyphs), and headlines are often better written in Chinese or Japanese characters, because the character itself is the graphic. A single character like 静 (stillness) or 美 (beauty) at 34vw behind the content is not decoration — it is the slide's meaning made visible.

The accent system is monastic. The vermillion hanko seal — a solid square with one white character — is the traditional Japanese signature, and it is the system's only strong accent. **One accent per slide, maximum.** It may be the hanko, or a moss-green label, or — very rarely — a 36px gold hairline, but never more than one. Vermillion `{colors.vermillion}` is the accent color of record; moss `{colors.moss}` is the quiet alternative; gold `{colors.gold}` is reserved for exceptional moments. Everything else is paper and ink.

**Density philosophy: low, almost severe.** The horizontal padding is 12vw — the most extreme in the library — and the canonical arrangement is content in the lower-left, emptiness in the upper-right. A slide with three text blocks has already failed. The system is for minimalist brand decks, annual reflections, cultural content, and traditional industries; its persuasive mechanism is the confidence of leaving space. Calm is the product.

**Key Characteristics:**
- Warm washi paper (`{colors.washi-paper}`) on every slide; paper-light for inset plaques, paper-deep for reflection panels.
- An enormous single character at 6–8% ink opacity behind the content (`{components.ghost-kanji}`), or a solid vermillion hanko seal (`{components.hanko-seal}`) — each slide gets one of the two.
- Zen Old Mincho carries display, headlines, and vertical text; Zen Kaku Gothic New carries body.
- Extreme margins: 12vw horizontal, 10vh vertical.
- Thin 1px sumi rules only; no thicker borders.
- Optional vertical text runs (`writing-mode: vertical-rl`) in the right margin.
- Asymmetric balance: content lower-left, emptiness upper-right.
- Subtle washi paper texture via inline SVG feTurbulence.
- Exactly one accent per slide: vermillion, moss, or (rarely) gold.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.washi-paper}` | #F5F1E6 | Default surface — warm handmade-paper tone, the ground of every slide |
| `{colors.paper-light}` | #FAF7EF | Lighter washi for inset plaques and seal-text contrast |
| `{colors.paper-deep}` | #EDE6D6 | Deeper paper for reflection panels and quote strips |
| `{colors.sumi-ink}` | #1F1D1A | All primary text and rules — the black of brushed sumi ink |
| `{colors.graphite}` | #7A746A | Secondary text, quotes, metadata |
| `{colors.graphite-light}` | #A39C90 | Tertiary metadata, folio marks — barely-there ink |
| `{colors.vermillion}` | #B3402A | The seal accent — hanko, index marks, one accent per slide |
| `{colors.moss}` | #6B6B5C | The quiet accent — chapter tags, alternative labels |
| `{colors.gold}` | #A98F5F | The rare accent — a 36px hairline for exceptional moments only |

### Defaults

- **Default surface background**: `{colors.washi-paper}`. Slides never go dark; the paper is the light source.
- **Default headline color**: `{colors.sumi-ink}` — headlines are always brushed ink on paper.
- **Default body color**: `{colors.sumi-ink}` for primary copy; `{colors.graphite}` for secondary.
- **Default accent color**: `{colors.vermillion}` — used for the hanko, index marks, and any single accent moment.
- **Default border / rule color**: `{colors.sumi-ink}` — 1px only.
- **Default label color**: `{colors.graphite}`; tertiary metadata in `{colors.graphite-light}`.
- **Default quote color**: `{colors.graphite}` — reflections sit one step quieter than headlines.

### Semantic Notes

The system is paper-and-ink plus one accent. Warmth lives in the three paper tones — washi-paper (wall), paper-light (plaque), paper-deep (panel) — and in the warm sumi black. Vermillion is the emotional accent and appears once per slide: as the hanko, as a single index mark, or as a small rule end. Moss is the intellectual accent for chapter tags. Gold is exceptional — a 36px hairline, nothing more. If a slide needs more than one accent, it needs fewer accents, not more. The system's rule of one is absolute: a slide with a vermillion hanko and a moss tag and a gold line is three systems colliding.

## Typography

### Font Family

The system loads four faces: **Zen Old Mincho** (weights 400, 500, 700) for every display, headline, seal character, vertical run, and stat; **Zen Kaku Gothic New** (weights 300, 400, 500) for body, lead, caption, and label text; **Noto Serif SC** and **Noto Sans SC** as simplified-Chinese fallbacks (serif behind Mincho, sans behind Kaku Gothic).

The register is deliberately East Asian:
- Zen Old Mincho reads as **brush-carried, literary, calm** — a Japanese mincho with clear, classical stroke structure. At 700 it has the presence of ink pressed from a brush; at large sizes a single character becomes a graphic.
- Zen Kaku Gothic New reads as **modern, even, self-effacing** — the Japanese equivalent of a well-drawn sans for sustained reading, with a slightly rounded calm that suits the system.
- Noto Serif SC / Noto Sans SC are the simplified-Chinese fallbacks — see the CJK section for when to prefer them as primary faces.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 8vw | Zen Old Mincho | 700 | Cover headline — one or two characters are enough |
| `{typography.h1}` | 4.5vw | Zen Old Mincho | 700 | Chapter-opening headline |
| `{typography.h2}` | 2.8vw | Zen Old Mincho | 700 | Primary content-slide headline |
| `{typography.stat-value}` | 5vw | Zen Old Mincho | 700 | Large numerical figure |
| `{typography.vertical-run}` | 2.2vw | Zen Old Mincho | 500 | Vertical text in the right margin, top-to-bottom |
| `{typography.seal-char}` | 3.2vw | Zen Old Mincho | 700 | The single character inside the hanko seal |
| `{typography.h3}` | 1.6vw | Zen Kaku Gothic New | 500 | Sub-headline, region heading |
| `{typography.lead}` | 1.35vw | Zen Kaku Gothic New | 300 | Lead paragraph — generous line height |
| `{typography.body}` | 1.02vw | Zen Kaku Gothic New | 300 | Body paragraph |
| `{typography.caption}` | 0.8vw | Zen Kaku Gothic New | 300 | Caption, source note |
| `{typography.label}` | 0.72vw | Zen Kaku Gothic New | 400 | Kicker, chapter tag, folio mark — tracked 0.25em |

### Defaults

- **Default section headline**: `{typography.h2}` (2.8vw at weight 700). `{typography.h1}` is for chapter breaks; `{typography.display}` for covers.
- **Default cover display**: `{typography.display}` (8vw at weight 700).
- **Default body size**: `{typography.body}` (1.02vw at weight 300).
- **Default lead size**: `{typography.lead}` (1.35vw at weight 300).
- **Default label size**: `{typography.label}` (0.72vw at weight 400).
- **Default stat readout**: `{typography.stat-value}` (5vw at weight 700).

When unsure, the canonical composition is a `{typography.h2}` headline in the lower-left, one `{typography.body}` paragraph, a ghost character behind, and a hanko seal near the headline — with the upper-right left empty.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every slide carries one of the two character accents**: either an enormous faint background character (`{components.ghost-kanji}` at 6–8% opacity via `color-mix`) or a solid vermillion hanko seal (`{components.hanko-seal}`). Never both on the same slide.
- **The hanko seal is a solid vermillion square with a single white character** (`{colors.vermillion}` fill, `{colors.paper-light}` glyph, ~6px radius). One seal per slide maximum.
- **Headlines prefer single characters and short phrases.** A two-character display (`静寂`, `無為`) is ideal; a four-character phrase is the practical limit.
- **Vertical text runs use `writing-mode: vertical-rl`** and sit in the right margin; they read top-to-bottom, columns right-to-left.
- **Rules are 1px sumi ink and nothing else** — no thicker rules, no dashed rules.
- **List markers are the Japanese middle dot `・`** in vermillion (`{components.index-mark}`) — never round bullets.
- **Exactly one accent per slide** — vermillion, moss, or gold; never two.
- **The folio mark sits in the lower-left corner** in the quietest ink (`{components.folio-mark}`).
- **Body text is never bolded and never italicized** — weight 300 and 700 are the only two weights in the system's voice.

### Typography Principles

The rhythm of Washi is **heavy mincho + light kaku-gothic + vertical accents**. The contrast between 700-weight brush-like serif and 300-weight airy sans is the system's primary dynamic. Switching the display voice to a sans would flatten the brush character; bolding body text would break the calm. Underlines do not exist; emphasis comes from size, from the ink-density contrast (ghost vs. solid), and from the seal. Latin is rendered through the same faces — Zen Old Mincho's Latin is quiet and literary, which is exactly right for a system where English is the guest language.

## Layout

### Canvas System

The system targets a `100vw × 100vh` paper folio with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `ink-in`, `rise`) are available with stagger delays via `data-delay` attributes, and they animate slowly — the system's motion should feel like ink settling, not UI sliding.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 12vw | Slide horizontal padding — the most extreme in the library |
| `{spacing.pad-y}` | 10vh | Slide vertical padding |
| `{spacing.gap-lg}` | 7vh | Between major sections |
| `{spacing.gap-md}` | 4vh | Between related blocks |
| `{spacing.gap-sm}` | 2vh | Between tightly related elements |

### Asymmetric Balance

The canonical composition is **content in the lower-left, emptiness in the upper-right**. The content zone occupies roughly the lower-left 45% of the canvas; the upper-right 40% is intentionally empty — this is *ma*, the meaningful void. The ghost character breathes behind the empty quadrant; the hanko anchors the content corner; vertical text may run down the right margin when a slide needs an extra axis. Centered compositions exist but are rare and reserved for cover and closing slides, where a single character centered on the paper is a deliberate statement, not a default.

### Chrome Frame

The system's chrome is near-silent. Content slides carry a single **folio mark** in the lower-left corner — page number and section in `{colors.graphite-light}` tracked labels, separated from the body by nothing. A 1px sumi rule may separate the foot zone when a slide needs structure. Cover and closing slides carry no chrome at all — just the character, the seal, and the paper.

## Depth and Elevation

### No Shadows, Ink Density Only

The system uses **zero box-shadow, zero elevation, zero blur**. Depth is created through four ink-native mechanisms:

1. **Ink density layering** — the ghost character at 6–8% opacity sits *behind* solid text; the difference between faint ink and full ink is the system's entire depth vocabulary.
2. **Paper tone layering** — washi-paper (wall) → paper-light (plaque) → paper-deep (panel) are three steps of the same warm family; a panel reads as an object on the paper purely through its tone.
3. **The paper texture** — a subtle feTurbulence grain at low opacity gives the surface physical presence, the way real washi fiber catches light.
4. **Whitespace** — the empty upper-right quadrant is the deepest "space" in the system; the extreme 12vw gutter is its shadow.

### No Atmospheric Effects

There are no gradients, no glows, no glass, no noise beyond the paper grain. The ghost character is not a "watermark effect" — it is ink at low density, and it must never be rendered as an image, a blur, or an opacity-animated layer. If a moment needs presence, it gets more paper and fewer elements, never an effect.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every structural element — plaques, panels, image blocks |
| 6px | The hanko seal corners only (`{components.hanko-seal}`) — a real seal is a square with softened corners |
| 50% (circle) | None — circles do not appear in this system |
| 999px (pill) | None — pills do not exist |

The system is square-cornered. The 6px radius on the hanko is the only curved corner in the system, and it exists because real carved seals are never perfectly sharp.

### Border Weights

- **1px solid `{colors.sumi-ink}`** — the universal rule: under headlines, around foot zones, as the occasional frame on image blocks.
- There is no 2px+, no dashed border, no colored border. The gold hairline (`{components.gold-line}`) is a decorative 1px element, not a border weight.

### Decorative Element Types

**Ghost character** — `{components.ghost-kanji}`: a single character at `font-size: min(34vw, 56vh)`, colored `color-mix(in srgb, {colors.sumi-ink} 7%, {colors.washi-paper})` — 6–8% ink on paper. Positioned behind the content zone, usually bleeding into the empty upper-right quadrant.

**Hanko seal** — `{components.hanko-seal}`: a `min(7vw, 10vh)` square in `{colors.vermillion}` with a single white character in Zen Old Mincho 700 at `{typography.seal-char}` size, 6px radius. The traditional carved seal; the system's strongest accent.

**Sumi rule** — `{components.sumi-rule}`: `width: 100%; height: 1px; background: {colors.sumi-ink}`. The only structural divider; used sparingly.

**Vertical text** — `{components.vertical-text}`: a run set with `writing-mode: vertical-rl` in Zen Old Mincho 500, placed in the right margin. Chinese and Japanese both read naturally this way; Latin segments inside a vertical run should be rotated via `text-orientation: upright` or kept horizontal in a separate block.

**Paper texture** — `{components.paper-texture}`: an inline SVG `<filter id="washi-grain">` with `feTurbulence` at low baseFrequency, applied to a full-slide overlay at 3–5% opacity with `pointer-events: none`. The texture is subtle — it must be felt, not seen.

**Moss tag** — `{components.moss-tag}`: a tracked uppercase label in `{colors.moss}`, used for chapter tags and section metadata — the system's quiet accent.

**Gold line** — `{components.gold-line}`: a 36px × 1px `{colors.gold}` hairline, the rare accent for exceptional moments (an anniversary slide, a closing note). Once per deck at most.

**Index mark** — `{components.index-mark}`: the Japanese middle dot `・` in `{colors.vermillion}`, prepended to list items via a grid marker column — the replacement for the Latin bullet.

**Zen quote** — `{components.zen-quote}`: a short serif reflection in `{colors.graphite}` at `{typography.h2}` size with generous line height, sitting alone in the lower-left — the system's quote voice, unhurried and unadorned.

**Image block** — A paper-light rectangle with a 1px sumi border and zero radius; captions sit below in `{typography.caption}`. Photography in this system is framed like a hanging scroll — upright, quiet, uncropped by effects.

## Do's and Don'ts

### Do
- Keep the washi-paper ground (`{colors.washi-paper}`) on every slide; paper-light and paper-deep are the only surface variations.
- Give each slide one character accent: a faint ghost character at 6–8% ink, or a solid vermillion hanko — never both.
- Set headlines in Zen Old Mincho 700, preferring one or two characters.
- Keep body copy in Zen Kaku Gothic New 300 with generous line height (1.9).
- Leave the upper-right quadrant empty. *Ma* is the design.
- Use 1px sumi rules only, and sparingly.
- Use the vermillion `・` middle dot as the list marker.
- Use `writing-mode: vertical-rl` for vertical text in the right margin.
- Apply the subtle washi grain to every slide.
- Allow exactly one accent per slide: vermillion, moss, or gold.

### Don't
- Don't fill the canvas. The extreme 12vw margin and the empty quadrant are features, not wasted space.
- Don't use more than one accent per slide — a hanko plus a moss tag is three systems colliding.
- Don't use box-shadows, gradients, glows, or blur. Ink density and paper are the only depth.
- Don't render the ghost character as an image, a watermark, or a blurred layer — it is ink at 6–8% density.
- Don't bold or italicize body text; weight 300 and 700 are the only voices.
- Don't use round bullets — the `・` middle dot is the list marker.
- Don't use thick rules, dashed rules, or colored borders; 1px sumi is the only weight.
- Don't center content by default — lower-left content with upper-right emptiness is the canonical balance; centering is reserved for cover and closing slides.
- Don't use Latin-first typography for headlines when the content is Chinese or Japanese; the character itself is the graphic.

## Responsive Behavior

The system is viewport-fluid by design, with all sizes in `vw`/`vh` so the folio holds at any 16:9 viewport without breakpoints; per the Fixed-Stage Policy, the generated deck renders at a fixed 1920×1080 stage scaled uniformly, and the `vw`/`vh` values are treated as design proportions only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve — the easing is the slowest and softest in the library.
- Each slide can declare entrance animations on individual elements via `data-anim` (`fade-up`, `fade-in`, `ink-in`, `rise`) with stagger delays via `data-delay="N"` mapped to discrete steps (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Elements with `[data-anim]` start at `opacity: 0` and animate on `.is-active`; re-visiting a slide replays the entrance.
- Prefer `fade-in` and `ink-in` (a slow opacity rise) — nothing in this system should slide or bounce.

### Print Behavior
The template declares no `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. The paper tones and 1px rules print faithfully; verify only that the ghost character's `color-mix` density survives the rasterizer (some engines flatten it to a solid).

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin/JP face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Zen Old Mincho) | Zen Old Mincho | Noto Serif SC (思源宋体) | 700 |
| Body / lead (Zen Kaku Gothic New) | Zen Kaku Gothic New | Noto Sans SC (思源黑体) | 300 |
| Sub-headline (Zen Kaku Gothic New 500) | Zen Kaku Gothic New | Noto Sans SC (思源黑体) | 500 |
| Label / folio (Zen Kaku Gothic New 400) | Zen Kaku Gothic New | Noto Sans SC (思源黑体) | 400 |
| Seal character (Zen Old Mincho) | Zen Old Mincho | Noto Serif SC (思源宋体) | 700 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Zen Old Mincho, Noto Serif SC, serif"` or `"Zen Kaku Gothic New, Noto Sans SC, sans-serif"`. Japanese and Chinese glyphs render through the primary face or the fallback; Latin renders through the same stack. Mixed sentences like `静寂 · Quietude, 2024` render as one logical run with the correct script per segment.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Zen+Old+Mincho:wght@400;500;700&family=Zen+Kaku+Gothic+New:wght@300;400;500&family=Noto+Serif+SC:wght@400;500;700&family=Noto+Sans+SC:wght@300;400;500&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.85–1.95, display 1.15–1.3
- Letter-spacing: 0 on CJK (reset the 0.25em label tracking on Chinese/Japanese runs)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `静寂 Quietude` not `静寂Quietude`)
- One font per sentence

### Aesthetic Notes for This System

Washi is the **CJK-native system of this library** — Chinese and Japanese are not fallbacks here, they are the intended primary scripts. Zen Old Mincho is a Japanese face with JIS-oriented glyph coverage; for simplified-Chinese decks, prefer **Noto Serif SC 700** as the display face to get mainland-standard glyph forms (e.g. 门 vs. 門), and keep Zen Old Mincho for Japanese or traditional-Chinese content. The ghost character technique is at its best with a single ideograph — one character is a graphic, and its meaning is the slide's message.

Vertical writing (`writing-mode: vertical-rl`) is native to Chinese and Japanese and works beautifully for headline accents, but **Latin text inside a vertical run should be avoided** — set `text-orientation: upright` for short Latin labels, or keep Latin in a separate horizontal block. The hanko seal reads authentically with either script: a single Chinese character (印, 静, 真) in white on vermillion.

The uppercase label tracking (0.25em) applies to Latin labels only; Chinese and Japanese labels are set with letter-spacing 0 and rely on the small size and graphite color for their quiet voice.

### Known CJK Gap

The extreme 12vw horizontal padding is tuned for the generous rhythm of CJK, but a *long* Chinese paragraph still consumes more width than its Latin equivalent at the same size. Keep body blocks to ≤ 18 characters per line and prefer lead-size (1.35vw) over body-size for Chinese passages, which read more calmly at the larger size. The ghost character at `min(34vw, 56vh)` is safe at 1920×1080, but on very dense slides verify it does not collide with the vertical text run in the right margin. Zen Old Mincho's Latin is literary but light; for decks with heavy English content, consider pairing with a Latin serif (see the gallery-label system) rather than forcing English through Mincho at small sizes.

## Iteration Guide

1. Any new slide background is `{colors.washi-paper}`; paper-light and paper-deep are the only surface variations, for plaques and panels.
2. Any new headline uses Zen Old Mincho 700 (or Noto Serif SC 700 for simplified Chinese) — display (8vw), h1 (4.5vw), or h2 (2.8vw) — preferring one or two characters.
3. Any new body or lead uses Zen Kaku Gothic New (or Noto Sans SC) at weight 300 in `{colors.sumi-ink}`.
4. Any new label or folio mark is `{typography.label}` size, tracked 0.25em for Latin, letter-spacing 0 for CJK.
5. Give each slide exactly one character accent: a ghost character at 6–8% ink, or a vermillion hanko — never both, never neither.
6. Any new structural separation is a 1px `{colors.sumi-ink}` rule, used sparingly.
7. Any new list uses the vermillion `・` middle dot as its marker.
8. Keep the upper-right quadrant empty; content lives lower-left. Centering is reserved for cover and closing slides.
9. Allow exactly one accent per slide — vermillion (default), moss (chapters), or gold (exceptional, once per deck).
10. Apply the washi grain overlay to every slide at 3–5% opacity.

## Known Gaps

- Zen Old Mincho is a Japanese face: its Han glyph forms are JIS-oriented, so simplified-Chinese decks should swap the display face to Noto Serif SC 700 (the fallback) for correct glyph shapes — a decision that must be made per deck, not per token.
- The ghost character's `color-mix` density (7% ink) is tuned for bright projectors; on low-contrast projection it can disappear entirely — verify in the rendered screenshot and raise to 9–10% if needed.
- The hanko seal at `min(7vw, 10vh)` is sized for 1920×1080; at the fixed stage it is stable, but it was originally designed in viewport units and should be re-verified after stage scaling.
- `writing-mode: vertical-rl` is well supported in modern engines, but mixed Latin/CJK vertical runs need `text-orientation` handling; older engines render Latin segments sideways — check any slide that uses vertical text.
- The one-accent rule is a design constraint, not a CSS rule; nothing enforces it mechanically, so it must be checked per slide during generation.
- The paper-grain feTurbulence filter is dropped by some PDF rasterizers; printed export may lose the washi texture even though the slide looks correct on screen.

---

## Related

This is a standalone design system in the `html-showcase` template library. For other aesthetics in the same pack, see the `ticker-console`, `bauhaus`, `gallery-label`, and `riso-print` design docs.
