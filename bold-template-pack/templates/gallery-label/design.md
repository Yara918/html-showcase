---
version: alpha
name: Gallery Label (Museum Wall Label)
description: A curatorial system modeled on the museum wall label — quiet, elegant, and authoritative. Cormorant Garamond serif headlines sit in the upper-left third of a white gallery; Inter at weight 300 carries body copy; tiny uppercase tracked labels read like exhibition captions. Content occupies under half the canvas, a single thin brass frame borders cover slides, and restraint itself is the message.

colors:
  gallery-white: "#FAFAF7"
  paper: "#F3F1EC"
  paper-deep: "#E9E5DD"
  ink: "#1A1A18"
  graphite: "#6F6F6A"
  graphite-light: "#9C9C95"
  ink-faint: "#C9C9C2"
  brass: "#B08D57"

color-aliases:
  c-bg: gallery-white
  c-bg-light: gallery-white
  c-bg-cream: paper
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite-light
  c-accent: brass
  c-border: ink
  c-border-light: ink-faint

typography:
  display:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontSize: 7vw
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: 0
  h1:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontSize: 4.2vw
    fontWeight: 500
    lineHeight: 1.15
  h2:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontSize: 2.6vw
    fontWeight: 500
    lineHeight: 1.25
  h3:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.4vw
    fontWeight: 400
    lineHeight: 1.4
  lead:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.3vw
    fontWeight: 300
    lineHeight: 1.7
  body:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 1.02vw
    fontWeight: 300
    lineHeight: 1.8
  caption:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 0.85vw
    fontWeight: 300
    lineHeight: 1.6
  label:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 0.72vw
    fontWeight: 400
    letterSpacing: 0.2em
    textTransform: uppercase
  wall-label:
    fontFamily: "Inter, Noto Sans SC, sans-serif"
    fontSize: 0.62vw
    fontWeight: 400
    letterSpacing: 0.16em
    textTransform: uppercase
  stat-value:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontSize: 4vw
    fontWeight: 500
    lineHeight: 1.05
  drop-cap:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontSize: 3.4vw
    fontWeight: 600
    lineHeight: 0.85

spacing:
  pad-x: 10vw
  pad-y: 8vh
  gap-lg: 6vh
  gap-md: 4vh
  gap-sm: 2vh

canvas:
  width: 100vw
  height: 100vh

components:
  brass-frame:
    border: "1px solid {colors.brass}"
    inset: "3vh 3vw"
    description: "The single thin brass frame border, applied only to cover and closing slides, inset 3vh/3vw from the canvas edge."
  hairline-rule:
    width: "100%"
    height: 1px
    background: "{colors.ink-faint}"
    description: "The universal 1px separator in faint ink — the only divider the system admits."
  kicker:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.2em
    textTransform: uppercase
    color: "{colors.graphite-light}"
    description: "Tiny uppercase tracked eyebrow above a headline, in the quietest ink tone."
  wall-label-block:
    fontFamily: "{typography.wall-label.fontFamily}"
    fontSize: "{typography.wall-label.fontSize}"
    letterSpacing: 0.16em
    textTransform: uppercase
    color: "{colors.graphite}"
    description: "The signature museum wall label — artist / title / date / medium stacked on four lines, lowercase-free, tracked."
  plaque:
    background: "{colors.paper}"
    padding: "3vh 2.5vw"
    description: "An inset wall-label plaque in warm paper, holding the wall-label block; no border, no shadow — defined by tone alone."
  drop-cap:
    fontFamily: "{typography.drop-cap.fontFamily}"
    fontSize: "{typography.drop-cap.fontSize}"
    float: left
    lineHeight: 0.85
    marginRight: "0.4em"
    description: "A floated Cormorant Garamond drop cap opening long body passages — the system's only permitted typographic flourish."
  img-plate:
    border: "1px solid {colors.ink-faint}"
    background: "{colors.gallery-white}"
    description: "A white image plate with a 1px faint-ink hairline border; captions sit below in Inter 300 with a small tracked index."
  index-line:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.2em
    textTransform: uppercase
    color: "{colors.brass}"
    description: "A tiny brass index line (No. 01, Room 3) — the only sanctioned use of brass outside the cover frame."
  artwork-title:
    fontFamily: "Cormorant Garamond, Noto Serif SC, Georgia, serif"
    fontStyle: italic
    fontWeight: 500
    description: "Titles of artworks and quoted works inside body text, set in Cormorant italic — authentic gallery-catalog practice."
  page-mark:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.2em
    textTransform: uppercase
    color: "{colors.graphite-light}"
    description: "The bottom-right page mark in tiny tracked uppercase — the only chrome the system carries."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Gallery Label is a **curatorial system**, and its subject is not the content — it is the room the content hangs in. The design borrows the quiet authority of a museum wall: white walls, warm paper labels, one work per wall, and text that is small, precise, and unhurried. Every slide is a gallery wall at 1920×1080. The headline is the artwork; the tiny uppercase wall label beside it — artist, title, date, medium, tracked and muted — is the curatorial voice; and the empty wall around both is the point. A deck in this system does not *show* restraint, it *is* restraint, and that is what makes it persuasive for portfolio, aesthetic, and premium work.

The typographic voice is a high/low pairing that real galleries use. **Cormorant Garamond** — a high-contrast display serif with the air of engraved plate text — carries every headline, stat, and drop cap. It is warm, literary, and slightly old-fashioned in the best way. **Inter at weight 300** carries body copy at a size and weight that says "this is not trying to impress you; read it slowly." The two voices never trade roles: a headline in Inter would read as a brochure, a paragraph in Cormorant would read as a menu. Between them, a third voice does the administrative work: tiny uppercase Inter labels tracked at 0.16–0.2em, styled exactly like a museum wall label. This third voice is the system's signature — the deck literally prints its own captions.

Color is nearly absent, on purpose. The canvas is `{colors.gallery-white}` — white with the faintest warmth, never a hard `#FFFFFF` screen white. Paper tones (`{colors.paper}`, `{colors.paper-deep}`) appear only as label plaques and inset strips. Ink `{colors.ink}` is a soft near-black for text; graphite carries secondary copy; `{colors.ink-faint}` renders the 1px hairlines. The single warm accent is **brass** `{colors.brass}` — a restrained, patina-able gold that appears exactly twice per deck at most: the thin frame border on cover and closing slides, and a tiny index line. Everything else is silence.

**Density philosophy: low, by constitution.** Content occupies under 50% of the canvas. The 10vw horizontal padding is among the most generous in the library, and slides that fill more than half their area with text have failed the brief. This is not wasted space; it is the museum's negative space, and it does the persuasive work. The system is designed for portfolio showcases, brand books, product-aesthetic decks, and high-end pitches — precisely the decks where a client's trust is won by what you choose not to say.

**Key Characteristics:**
- Gallery-white surface (`{colors.gallery-white}`) on every slide; paper tones only for plaques and inset strips.
- Large Cormorant Garamond serif headline in the upper-left third of the canvas.
- Content occupies under 50% of the canvas — the empty wall is a design element.
- Tiny uppercase tracked labels everywhere: kickers, wall labels, index lines, page marks.
- Thin 1px separators in `{colors.ink-faint}`; no other border weight exists in the system.
- A single thin brass frame (`{components.brass-frame}`) borders cover and closing slides only.
- Drop caps open long body passages — the only permitted typographic flourish.
- Artwork titles inside body text are set in Cormorant italic, following gallery-catalog convention.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.gallery-white}` | #FAFAF7 | Default surface — white with the faintest warmth, never a cold screen white |
| `{colors.paper}` | #F3F1EC | Wall-label plaques and inset strips |
| `{colors.paper-deep}` | #E9E5DD | Deepest paper tone for quote strips and section-break panels |
| `{colors.ink}` | #1A1A18 | All primary text — a soft near-black with a trace of warmth |
| `{colors.graphite}` | #6F6F6A | Secondary text, wall-label copy |
| `{colors.graphite-light}` | #9C9C95 | Tertiary metadata, kickers, page marks |
| `{colors.ink-faint}` | #C9C9C2 | The 1px hairline separators — barely-there ink |
| `{colors.brass}` | #B08D57 | The single warm accent: cover frame and index lines only |

### Defaults

- **Default surface background**: `{colors.gallery-white}`. There is exactly one wall color; slides never go dark.
- **Default headline color**: `{colors.ink}` — serif headlines always in the soft near-black.
- **Default body color**: `{colors.ink}` for primary copy; `{colors.graphite}` for wall labels and secondary text.
- **Default kicker / metadata color**: `{colors.graphite-light}` — the quietest legible ink.
- **Default separator color**: `{colors.ink-faint}` — hairlines are meant to be felt, not seen.
- **Default accent color**: `{colors.brass}` — reserved for the cover frame and a tiny index line; nothing else.
- **Default surface for inset labels**: `{colors.paper}` — plaques are defined by tone, not border.

### Semantic Notes

The system is monochrome-plus-one. Warm white, warm paper, and warm ink form a single tonal family; graphite and ink-faint are its shadows. Brass is the entire chromatic vocabulary, and it is rationed: the frame on cover and closing slides, and optionally one index line per content slide. If a slide needs more warmth, the answer is a paper plaque or a paper-deep panel — never more brass and never a new hue. The gallery-white surface must stay warm: a neutral or blue-tinted white would make the paper plaques look dirty instead of deliberate.

## Typography

### Font Family

The system loads three faces: **Cormorant Garamond** (weights 500, 600, plus italics) for every display, headline, stat, drop cap, and in-text artwork title; **Inter** (weights 300, 400) for every body, lead, caption, label, and wall label; and **Noto Serif SC** plus **Noto Sans SC** as the CJK fallbacks (serif behind Cormorant, sans behind Inter).

The emotional register is deliberate:
- Cormorant Garamond reads as **engraved, literary, unhurried** — the serif of exhibition catalogs and plate books. Its high stroke contrast gives headlines a quiet drama that heavier sans faces cannot.
- Inter at 300 reads as **institutional, precise, self-effacing** — the type of gallery wall text: legible at small sizes, never decorative, never loud.
- The tracked uppercase label voice (Inter 400) reads as **curatorial metadata** — the artist's name card, the caption, the accession number.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 7vw | Cormorant Garamond | 600 | Cover headline — large, warm, slightly engraved |
| `{typography.h1}` | 4.2vw | Cormorant Garamond | 500 | Chapter or section-break headline |
| `{typography.h2}` | 2.6vw | Cormorant Garamond | 500 | Primary content-slide headline |
| `{typography.stat-value}` | 4vw | Cormorant Garamond | 500 | Large numerical figure in a stat block |
| `{typography.drop-cap}` | 3.4vw | Cormorant Garamond | 600 | Floated opening letter of a long body passage |
| `{typography.h3}` | 1.4vw | Inter | 400 | Sub-headline, region heading |
| `{typography.lead}` | 1.3vw | Inter | 300 | Lead paragraph under a headline |
| `{typography.body}` | 1.02vw | Inter | 300 | Body paragraph |
| `{typography.caption}` | 0.85vw | Inter | 300 | Image caption, source note |
| `{typography.label}` | 0.72vw | Inter | 400 | Kicker, index line, page mark — uppercase, tracked 0.2em |
| `{typography.wall-label}` | 0.62vw | Inter | 400 | The museum wall label block — uppercase, tracked 0.16em |

### Defaults

- **Default section headline**: `{typography.h2}` (2.6vw at weight 500). `{typography.h1}` is for chapter breaks; `{typography.display}` for covers.
- **Default cover display**: `{typography.display}` (7vw at weight 600).
- **Default body size**: `{typography.body}` (1.02vw at weight 300).
- **Default lead size**: `{typography.lead}` (1.3vw at weight 300).
- **Default label size**: `{typography.label}` (0.72vw, tracked 0.2em).
- **Default stat readout**: `{typography.stat-value}` (4vw at weight 500).

When unsure, the canonical pairing is a Cormorant `{typography.h2}` headline in the upper-left third, one `{typography.lead}` paragraph beneath it, and a `{typography.wall-label}` block in a corner — with the rest of the canvas empty.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every label — kicker, wall label, index line, page mark — is Inter 400, uppercase, tracked at least 0.16em** (labels 0.2em, wall labels 0.16em). The tracked small-caps voice is the system's signature; it appears on nearly every slide.
- **The wall label is always structured as artist / title / date / medium** — four stacked uppercase lines in `{colors.graphite}`, following the museum format, not a single running caption.
- **Headlines live in the upper-left third of the canvas.** The serif voice never centers, never sits at the bottom, never shares the wall with a second headline.
- **Content occupies under 50% of the canvas.** A slide that crosses the half-line is over-filled; cut copy or split the slide.
- **Artwork titles inside body text are Cormorant italic** (`{components.artwork-title}`) — the gallery-catalog convention; never quoted, never underlined, never bolded.
- **Drop caps open any body passage longer than four lines** (`{components.drop-cap}`), floated left with a 0.4em margin.
- **Every separator is a 1px line in `{colors.ink-faint}`.** No thicker rules, no colored rules, no dashed rules.
- **Brass appears exactly twice per deck maximum**: the cover-frame border and one index line per content slide.
- **Body text is never bolded** — emphasis inside a paragraph comes from the Cormorant italic switch or from isolation through whitespace.

### Typography Principles

The rhythm of Gallery Label is **large warm serif + weight-300 sans + tiny tracked caps**. The serif carries emotion, the sans carries information, the caps carry metadata — three voices, three jobs, no overlap. Switching the display voice to a geometric sans reads as a different system. Bolding body text breaks the self-effacing register. Italic is reserved for artwork titles (Cormorant) and is not used for emphasis anywhere else. There is no underline in the system.

## Layout

### Canvas System

The system targets a `100vw × 100vh` gallery wall with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `fade-left`, `rise`) are available with stagger delays via `data-delay` attributes, and they run slowly — the system's animations are the quietest in the library.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 10vw | Slide horizontal padding — among the most generous in the library |
| `{spacing.pad-y}` | 8vh | Slide vertical padding |
| `{spacing.gap-lg}` | 6vh | Between major sections |
| `{spacing.gap-md}` | 4vh | Between related blocks |
| `{spacing.gap-sm}` | 2vh | Between tightly related elements (wall label lines, caption and image) |

### Chrome Frame

The system's chrome is nearly invisible. Content slides carry a single **page mark** in the bottom-right corner: a tiny tracked uppercase label (`{colors.graphite-light}`) showing the section name and page number — `EXHIBITION · 03`. A 1px `{colors.ink-faint}` hairline may separate it from the slide body, but only when the slide already uses a hairline elsewhere. Cover, quote, and closing slides suppress even the page mark. There is no top header; the headline is the header, and the wall label does the metadata work.

### The 50% Rule

Content — headline, body, labels, plates — must fit inside a region that occupies less than half of the canvas area. The canonical placement is a compact block in the lower-left quadrant plus the headline in the upper-left third, or a single centered-in-the-upper-half plate with a wall label below it. The remaining wall is empty on purpose. If a layout idea requires more than half the canvas, it is the wrong layout for this system.

## Depth and Elevation

### Flat Wall, No Elevation

The system uses **zero box-shadow, zero gradient, zero blur, zero elevation**. A gallery wall is flat, and so is this system. Depth is created through three mechanisms:

1. **Tonal layering** — gallery-white (wall), paper (plaque), paper-deep (inset panel) are three steps of the same warm family; a plaque reads as "an object on the wall" purely through its tone, with no border and no shadow.
2. **Hairline separators** — 1px `{colors.ink-faint}` lines divide caption from plate, label from body; the faintness keeps them from adding visual weight.
3. **Whitespace** — the empty wall is the dominant depth cue. The 10vw gutter and the sub-50% content rule are the system's real "shadows."

### No Atmospheric Effects

There are no gradients, no glows, no grain, no textures of any kind — even the paper tones are flat fills. The brass frame is a 1px border, not a metallic gradient; it must never be faked with a gold gradient. If a moment needs presence, it gets more white space or a paper-deep panel, never an effect.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every element — plates, plaques, panels, buttons, stat blocks |
| 50% (circle) | None — circles do not appear in this system |
| 999px (pill) | None — pills do not exist |

The system is entirely square-cornered. Even the paper plaques are 0px rectangles; a rounded plaque would read as a modern UI card and break the museum fiction.

### Border Weights

- **1px solid `{colors.ink-faint}`** — the universal hairline: image plates, section separators, caption rules.
- **1px solid `{colors.brass}`** — the cover/closing frame only (`{components.brass-frame}`).
- There is no 2px+, no dashed border, no colored structural border. The brass frame is the only non-faint border in the system, and it appears on exactly two slides.

### Decorative Element Types

**Brass frame** — `{components.brass-frame}`: a 1px brass border inset 3vh/3vw from the canvas edge, applied to the cover and closing slides. The frame is thin on purpose — it is a gallery molding, not a picture border.

**Hairline separator** — `{components.hairline-rule}`: `width: 100%; height: 1px; background: {colors.ink-faint}`. The only divider in the system; used between caption and plate, above foot zones, and between wall-label lines when a block needs structure.

**Kicker** — `{components.kicker}`: Inter 400 uppercase tracked 0.2em in `{colors.graphite-light}`, placed above a headline. Barely-there by design.

**Wall label block** — `{components.wall-label-block}`: the signature element. Four stacked uppercase lines — artist, title, date, medium — in `{colors.graphite}` at `{typography.wall-label}` size, tracked 0.16em. Sits on a `{components.plaque}` paper surface or directly on the wall beside the headline.

**Drop cap** — `{components.drop-cap}`: Cormorant Garamond 600 at 3.4vw, `float: left; line-height: 0.85; margin-right: 0.4em`, opening long body passages. The system's only flourish, and it must be Cormorant — never Inter, never a sans drop cap.

**Image plate** — `{components.img-plate}`: a gallery-white rectangle with a 1px `{colors.ink-faint}` border, captioned below in `{typography.caption}` Inter 300 with an optional small tracked index. Plates hang on the wall like framed works.

**Artwork title** — `{components.artwork-title}`: Cormorant italic for work titles inside body text, matching catalog convention; the italic is the only inline emphasis in the system.

**Page mark** — `{components.page-mark}`: the bottom-right tracked uppercase label — `EXHIBITION · 03` — the system's only chrome.

## Do's and Don'ts

### Do
- Keep the gallery-white surface (`{colors.gallery-white}`) on every slide. One wall color, always.
- Set every headline in Cormorant Garamond in the upper-left third, in `{colors.ink}`.
- Keep content under 50% of the canvas. The empty wall is the design.
- Use tiny uppercase tracked labels (0.16–0.2em) for every kicker, wall label, index line, and page mark.
- Format wall labels as artist / title / date / medium on four stacked lines.
- Use the 1px `{colors.ink-faint}` hairline as the only structural divider.
- Set artwork titles in Cormorant italic inside body text.
- Use the brass frame on cover and closing slides only, and brass index lines sparingly.
- Use a Cormorant drop cap for any body passage longer than four lines.

### Don't
- Don't fill the canvas. Content over 50% of the area is a failed slide for this system.
- Don't introduce a second accent color. Brass is the entire chromatic vocabulary.
- Don't use a dark background, a gradient, a shadow, or any texture. The wall is flat and warm.
- Don't bold body text or use Inter for headlines — the serif/sans roles are fixed.
- Don't set wall labels in sentence case or without tracking. The tracked caps voice is the signature.
- Don't put the headline anywhere but the upper-left third — no centered serif, no bottom-anchored serif.
- Don't use rounded corners on plaques, plates, or buttons. Everything is 0px.
- Don't fake the brass frame with a gold gradient; it is a 1px border.
- Don't use a circle or any geometric shape as decoration — this system has no shapes, only objects (plates, plaques, frames).
- Don't underline links; mark them with `{colors.ink}` + Cormorant italic if they are titles, or leave them as plain text.

## Responsive Behavior

The system is viewport-fluid by design, with all sizes in `vw`/`vh` so the wall composition holds at any 16:9 viewport without breakpoints; per the Fixed-Stage Policy, the generated deck renders at a fixed 1920×1080 stage scaled uniformly, and the `vw`/`vh` values are treated as design proportions only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve — the easing is deliberately slow and soft.
- Each slide can declare entrance animations on individual elements via `data-anim` (`fade-up`, `fade-in`, `fade-left`, `rise`) with stagger delays via `data-delay="N"` mapped to discrete steps (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Elements with `[data-anim]` start at `opacity: 0` and animate on `.is-active`; re-visiting a slide replays the entrance.
- Prefer `fade-in` and `rise` over slide animations — the wall should never feel mechanical.

### Print Behavior
The template declares no `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. Because the system is flat warm-white with 1px hairlines, printed output is faithful — verify that the brass frame and hairlines survive the print rasterizer at their 1px weight.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Cormorant 600) | Cormorant Garamond | Noto Serif SC (思源宋体) | 700 |
| Chapter / content headline (Cormorant 500) | Cormorant Garamond | Noto Serif SC (思源宋体) | 600 |
| Body / lead (Inter 300) | Inter | Noto Sans SC (思源黑体) | 300 |
| Caption / metadata (Inter 300) | Inter | Noto Sans SC (思源黑体) | 300 |
| Label / wall label (Inter 400 caps) | Inter | Noto Sans SC (思源黑体) | 400 |
| Artwork title (Cormorant italic) | Cormorant Garamond italic | Noto Serif SC (思源宋体) | 600 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Cormorant Garamond, Noto Serif SC, Georgia, serif"` or `"Inter, Noto Sans SC, sans-serif"`. Latin glyphs render in the primary face; CJK glyphs automatically fall through to Noto Serif SC / Noto Sans SC. No per-language class is needed. Mixed sentences like `《夜航》 · Night Voyage, 1962` render as one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:ital,wght@0,400;0,500;0,600;1,400;1,500&family=Inter:wght@300;400&family=Noto+Serif+SC:wght@400;500;600;700&family=Noto+Sans+SC:wght@300;400&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.8–1.9, display 1.15–1.25
- Letter-spacing: 0 on CJK (reset the 0.16–0.2em tracking on Chinese label runs)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `《夜航》 Night Voyage` not `《夜航》Night Voyage`)
- One font per sentence

### Aesthetic Notes for This System

Gallery Label's defining trait is **Cormorant Garamond — a high-contrast, engraved-style display serif.** The correct Chinese counterpart is Noto Serif SC, which carries the same classical, printed-book warmth. Set Chinese display in Noto Serif SC 700 against Cormorant 600; the serif voice survives the script switch better than any sans substitution would. For body text, Inter 300 pairs with Noto Sans SC 300 — the light, self-effacing register carries across scripts.

The tracked uppercase label voice does not transfer to CJK. Chinese has no case, and letter-spacing on Chinese runs breaks their natural full-width rhythm. **Set Chinese labels in Noto Sans SC 400 with letter-spacing 0** — the curatorial voice in Chinese is carried by the small size and the graphite color, not by tracking. If a label is pure Latin (an artist name, a date), keep the tracking as designed.

Noto Serif SC has no italic. **Chinese artwork titles cannot be italicized** — follow the Chinese catalog convention instead and wrap work titles in full-width book-title marks 《》, which is the authentic typographic signal for a work title in Chinese. Do not fake italic with `font-style: italic` on a Chinese run; the auto-slant renders broken.

The drop cap is a Latin-specific flourish. A Chinese drop cap at the same size would overbalance the opening line; use the drop cap on Latin passages only, or skip it for pure-Chinese body text.

### Known CJK Gap

Cormorant Garamond's numerals and headlines are narrow compared with Chinese characters. A pure-Chinese display headline will be noticeably wider per character; reduce display size by ~12–15% (Cormorant 7vw → Noto Serif SC 6vw) for pure-Chinese headlines and keep them to ≤ 8 characters per line. Also, the 50%-of-canvas content rule was tuned for Latin's horizontal economy; Chinese text carries more characters per line, so a bilingual slide may need either a longer wrap or a smaller body size (1.02vw → 0.95vw) to stay inside the half-canvas budget.

## Iteration Guide

1. Any new slide background is `{colors.gallery-white}`. Slides never go dark; paper tones are for plaques and panels only.
2. Any new headline is Cormorant Garamond in `{colors.ink}`, placed in the upper-left third — display (7vw, 600), h1 (4.2vw, 500), or h2 (2.6vw, 500).
3. Any new body or lead is Inter 300 in `{colors.ink}`, never bolded.
4. Any new label — kicker, wall label, index line, page mark — is Inter 400 uppercase tracked ≥ 0.16em; wall labels are formatted artist / title / date / medium.
5. Any new artwork title inside body text is Cormorant italic; in Chinese, wrap it in 《》 instead.
6. Any new structural separation is a 1px `{colors.ink-faint}` hairline. No other divider exists.
7. Any new plaque is a `{colors.paper}` rectangle at 0px radius, defined by tone, never by border or shadow.
8. Keep every slide under the 50% content rule. When in doubt, cut copy — the empty wall does the persuading.
9. Use brass exactly twice per deck maximum: the cover-frame border and one index line per content slide.
10. Any body passage longer than four lines opens with a Cormorant drop cap.

## Known Gaps

- The brass frame and brass index lines are the system's only chromatic moments; if a deck has more than two brass uses, it has drifted out of the system — the rule is easy to violate during generation.
- Cormorant Garamond has no weight below 300 and no true black; the display hierarchy relies on size (7vw → 2.6vw), and very large sizes can expose its high stroke contrast on low-DPI projectors — verify in the rendered screenshot.
- The 50%-of-canvas content rule is a design constraint, not a CSS rule; nothing enforces it mechanically, so it must be checked per slide during generation.
- The drop cap relies on `float: left`, which is stable but interacts with `[data-anim]` entrance animations — the floated cap should animate with `fade-in` only, or it can jump during the entrance.
- Inter weight 300 at 1.02vw is a deliberately light reading voice; on dense bilingual slides it may fall below comfortable contrast against `{colors.gallery-white}` — raise to weight 400 only when a slide is unusually text-heavy, and document that choice.
- The system assumes artwork photography will be provided as image plates; there is no illustration system — a deck without photography leans entirely on typography and whitespace, which is correct but demanding.

---

## Related

This is a standalone design system in the `html-showcase` template library. For other aesthetics in the same pack, see the `ticker-console`, `bauhaus`, `riso-print`, and `washi` design docs.
