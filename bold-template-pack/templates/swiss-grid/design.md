---
version: alpha
name: Swiss Grid
description: An objective Swiss International Typography system built on a strict 12-column grid, a grotesque sans display voice (Archivo 700–800), and a single signal-red accent that is permitted exactly once per slide. Paper, ink, graphite, and 1px hairlines exist only to make the grid legible and the typography systematic. The aesthetic descends from International Typographic Style posters and annual-report grids — rational, editorial, modernist, and allergic to decoration.

colors:
  paper: "#F4F4F1"
  white: "#FFFFFF"
  ink: "#17171A"
  graphite: "#6E6E74"
  graphite-light: "#A3A3AA"
  signal-red: "#E63312"
  blue-gray: "#2E4A7A"

color-aliases:
  c-bg: paper
  c-bg-light: white
  c-bg-cream: paper
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite-light
  c-accent: signal-red
  c-border: ink
  c-border-light: graphite-light

typography:
  display:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 9vw
    fontWeight: 800
    lineHeight: 0.95
    letterSpacing: -0.03em
  h1:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 5.4vw
    fontWeight: 700
    lineHeight: 1.05
    letterSpacing: -0.02em
  h2:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3.4vw
    fontWeight: 700
    lineHeight: 1.15
    letterSpacing: -0.015em
  h3:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 2.1vw
    fontWeight: 600
    lineHeight: 1.25
  lead:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.6vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.1vw
    fontWeight: 400
    lineHeight: 1.7
  caption:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.85vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.72vw
    fontWeight: 400
    letterSpacing: 0.16em
    textTransform: uppercase
  index-num:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 6vw
    fontWeight: 800
    lineHeight: 1.0
    letterSpacing: -0.02em
  figure-caption:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.7vw
    fontWeight: 400
    letterSpacing: 0.08em
  stat-value:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.6vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: -0.02em

spacing:
  pad-x: 6vw
  pad-y: 5vh
  gap-lg: 4.5vh
  gap-md: 2.5vh
  gap-sm: 1.2vh

canvas:
  width: 100vw
  height: 100vh

components:
  grid-12:
    display: grid
    gridTemplateColumns: "repeat(12, 1fr)"
    columnGap: "{spacing.gap-md}"
    description: "The system's backbone: a strict 12-column grid with a 2.5vh gutter. Every content slide is a direct child of this grid; no element is allowed to break out of its column span."
  col-rule:
    width: 1px
    background: "{colors.graphite-light}"
    opacity: 0.4
    description: "Visible hairline column rule. On title slides the 12 columns are drawn as 1px vertical lines at 40% graphite-light so the grid itself is on display."
  rule:
    width: "100%"
    height: 1px
    background: "{colors.ink}"
    description: "Full-width 1px solid ink rule. The only sanctioned full-bleed divider: under chrome headers, above foot bands, between content regions."
  rule-short:
    width: 44px
    height: 2px
    background: "{colors.signal-red}"
    description: "The signature 44×2px signal-red punctuation rule. May appear under a kicker, beside an index numeral, or as the underline of one headline span. This counts as the slide's single red element when present."
  kicker:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.16em
    textTransform: uppercase
    color: "{colors.graphite}"
    description: "Mono uppercase eyebrow above a headline, tracked at 0.16em. Reads as the slide's filing code, not its voice."
  index-num:
    fontFamily: "{typography.index-num.fontFamily}"
    fontSize: "{typography.index-num.fontSize}"
    fontWeight: 800
    color: "{colors.graphite}"
    lineHeight: 1.0
    description: "Oversized graphite index numeral (01, 02, 03…) marking chapter position. Set at 6vw in Archivo 800; the strongest non-accent graphic in the system."
  tag:
    border: "1px solid {colors.ink}"
    padding: "0.25em 0.7em"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.12em
    textTransform: uppercase
    description: "Square-cornered 1px-ink bordered inline tag for version codes, status labels, or process-step keys."
  cell:
    borderTop: "1px solid {colors.ink}"
    padding: "{spacing.gap-md} {spacing.gap-md} {spacing.gap-md} 0"
    description: "Rule-topped grid cell holding a stat-value numeral, an Inter label, and an optional mono source line. Three cells across a row is the canonical arrangement."
  stat-cell:
    borderTop: "1px solid {colors.ink}"
    padding: "{spacing.gap-md} {spacing.gap-md} {spacing.gap-md} 0"
    description: "A cell variant for KPI moments: 4.6vw Archivo-700 numeral in ink, Inter label below, mono note at the foot."
  table:
    borderTop: "1px solid {colors.ink}"
    borderCollapse: collapse
    description: "Data table with 1px ink column rules and 1px horizontal rules between rows. No zebra striping, no row fills."
  bar-fill:
    width: "100%"
    background: "{colors.graphite}"
    description: "Vertical bar in solid graphite. The highlighted bar swaps to {colors.signal-red} — the single allowed red series."
  img-placeholder:
    border: "1px solid {colors.ink}"
    background: "{colors.white}"
    aspectRatio: "1 / 1"
    display: grid
    placeItems: center
    fontFamily: "{typography.figure-caption.fontFamily}"
    fontSize: "{typography.figure-caption.fontSize}"
    color: "{colors.graphite-light}"
    description: "Square white void with a 1px ink border and a centered mono label such as 'FIG. 03'. Holds photography or a real figure until it arrives."
  figure-caption:
    fontFamily: "{typography.figure-caption.fontFamily}"
    fontSize: "{typography.figure-caption.fontSize}"
    letterSpacing: 0.08em
    color: "{colors.graphite-light}"
    description: "Mono figure-caption label ('FIG. 03 — Q3 FULFILLMENT BY REGION') set directly under a chart or image. Objective captions, never decorative flourishes."
  bullet-marker:
    content: "—"
    color: "{colors.graphite}"
    fontFamily: "{typography.label.fontFamily}"
    description: "Em-dash in graphite via JetBrains Mono, prepended in a 1.2em grid marker column. The only list mark in the system."
  timeline-spine:
    width: 1px
    background: "{colors.ink}"
    description: "1px vertical ink rule anchoring a timeline. Each entry carries a 7px square marker (borderRadius 0) aligned to the spine."
  donut:
    width: "min(22vw, 36vh)"
    height: "min(22vw, 36vh)"
    borderRadius: 50%
    description: "Donut rendered as a conic-gradient ring with a same-surface circular ::after cutout. Ring segments are graphite; one segment may be signal-red."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Swiss Grid is an **objective typographic system** in the tradition of International Typographic Style: the grid is the voice, the grotesque sans is the instrument, and a single signal-red accent is the only moment the system allows itself to raise its voice. It is built for content that must read as rational, structured, and trustworthy — operations reviews, methodology decks, KPI definitions, quarterly reports, policy explanations — anything where the reader should trust the structure before they trust the argument.

The system is a **12-column grid first and a visual style second**. Every content slide is laid out as a direct child of a `grid-template-columns: repeat(12, 1fr)` container with a fixed gutter; no element is permitted to break out of its column span. On title slides the columns themselves are drawn as visible 1px hairlines at 40% graphite-light, so the machinery of the layout is literally on display — the grid is not a hidden tool but a declared part of the design. This is the single most distinctive move in the system: other templates hide their scaffolding, Swiss Grid exhibits it.

The typographic voice is a three-face hierarchy with strictly separated jobs. **Archivo** at weights 700–800 is the display instrument — a grotesque sans with a straight, slightly squared construction that reads in the neo-grotesque tradition without copying any single historical face. It carries display, headlines, and numerals. **Inter** at weight 400 is the body instrument — neutral, quietly humanist, and long-form legible, so dense methodology text stays calm. **JetBrains Mono** at weight 400 is the metadata instrument: every kicker, tag, axis label, figure caption, footer, and index annotation is mono, uppercase, and tracked at 0.12–0.16em. Uppercase belongs to the mono voice exclusively; display and body text are always mixed case.

Color is rationed like a budget. Paper (`{colors.paper}`) is the default surface; white (`{colors.white}`) marks inset surfaces such as image placeholders and panel fields. Ink (`{colors.ink}`) is every text moment, border, and divider. Graphite and graphite-light step text back in two measured stages. **Signal red appears exactly once per slide** — as a kicker, an index numeral, an underline, or a single chart series — and nowhere else; two red elements on one slide is a design error. A rare blue-gray (`{colors.blue-gray}`) is reserved for semantic second-series distinctions in charts and must be justified in a figure caption when used.

Depth is achieved entirely through **1px hairlines and whitespace**. There are no shadows, no gradients, no rounded corners (0px everywhere), no textures, no elevation. Regions are separated by rules, never by fills or lifts; a region that needs more weight gets more padding, not more ink. The emotional register is the opposite of decorative: the system's beauty is in alignment, in the beat of the column grid, and in the discipline of leaving large areas of paper untouched.

**Key Characteristics:**
- A strict 12-column grid with a 2.5vh gutter; no element breaks out of its column span.
- Visible hairline column rules on title slides — the grid as ornament.
- Archivo 700–800 for display, Inter 400 for body, JetBrains Mono 400 uppercase for every label.
- Exactly one signal-red element per slide, always `{colors.signal-red}`.
- Left-aligned, ragged-right text throughout; centered text is a rare, deliberate exception.
- 1–2px hairlines are the only decoration; zero shadows, zero gradients, zero rounded corners.
- Oversized graphite index numerals (01/02/03) as the system's strongest non-accent graphic.
- Objective figure-caption labels in mono: "FIG. 03 — Q3 FULFILLMENT BY REGION".
- Square image placeholders with mono labels, never rounded.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.paper}` | #F4F4F1 | Default surface. A cool, slightly gray warm-white — reads as paper, not as screen white |
| `{colors.white}` | #FFFFFF | Inset surfaces: image placeholders, panel fields, figure wells |
| `{colors.ink}` | #17171A | Every text moment, every border, every divider, every shape fill that isn't paper or white |
| `{colors.graphite}` | #6E6E74 | Secondary text: leads, labels under numerals, list markers |
| `{colors.graphite-light}` | #A3A3AA | Tertiary metadata: figure captions, source notes, dormant hairlines, placeholder labels |
| `{colors.signal-red}` | #E63312 | The single accent. One element per slide: kicker, numeral, underline, or one chart series |
| `{colors.blue-gray}` | #2E4A7A | Rare secondary for a second data series or a semantic distinction; always explained by a caption |

### Defaults

- **Default surface background**: `{colors.paper}`. Slides are never pure white and never dark.
- **Default primary headline color**: `{colors.ink}`. Headlines never render in graphite or red.
- **Default body text color**: `{colors.ink}`; muted lead paragraphs use `{colors.graphite}`.
- **Default kicker / label color**: `{colors.graphite}` — labels are metadata, not emphasis.
- **Default border / divider color**: `{colors.ink}` for structural rules; `{colors.graphite-light}` at 40% opacity for dormant hairlines such as title-slide column rules.
- **Default rule weight**: 1px. The 2px rule-short is the only thicker rule, and it is reserved for the red signature punctuation.
- **Default accent color**: `{colors.signal-red}` — permitted exactly once per slide.
- **Default chart series colors**: graphite for all series; signal-red for the single highlighted series; blue-gray only when a second series is semantically required.

The system has no warm/cool pairing and no semantic color traffic light (no green for success, no yellow for warning). Emphasis comes from size, weight, and the one red element — never from a palette of functional colors.

## Typography

### Font Family

The system loads three Latin faces plus the CJK fallbacks: **Archivo** (weights 600, 700, 800) carries all display, headline, and numeral moments; **Inter** (weights 400, 500) carries body, lead, and caption copy; **JetBrains Mono** (weight 400) carries every label, kicker, tag, axis, figure caption, and footer; **Noto Sans SC** is the CJK fallback for all three.

The emotional register is deliberate:

- Archivo reads as **engineered, slightly squared, and confident** at 800. Its tight negative tracking (-0.02em to -0.03em) makes display type feel machined rather than drawn — the voice of a specification sheet, not a brochure.
- Inter reads as **neutral and almost invisible** at 400. Body text should be felt as information, not as typography.
- JetBrains Mono reads as **indexical and archival**. Mono uppercase at 0.16em tracking is the system's filing-cabinet voice: it tells the reader "this is a code, a date, a reference — not a sentence."

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 9vw | Archivo | 800 | Title-slide hero display — the largest Archivo in the system |
| `{typography.h1}` | 5.4vw | Archivo | 700 | Chapter or section-break headline |
| `{typography.h2}` | 3.4vw | Archivo | 700 | Primary content-slide headline |
| `{typography.stat-value}` | 4.6vw | Archivo | 700 | KPI numeral inside a stat cell |
| `{typography.index-num}` | 6vw | Archivo | 800 | Oversized graphite index numeral (01/02/03) |
| `{typography.h3}` | 2.1vw | Archivo | 600 | Sub-headline, region heading, flow-step title |
| `{typography.lead}` | 1.6vw | Inter | 400 | Lead paragraph under a headline |
| `{typography.body}` | 1.1vw | Inter | 400 | Body paragraph |
| `{typography.caption}` | 0.85vw | Inter | 400 | Image caption, source note, fine print |
| `{typography.label}` | 0.72vw | JetBrains Mono | 400 | Kicker, tag, axis label, footer, version code |
| `{typography.figure-caption}` | 0.7vw | JetBrains Mono | 400 | Figure captions under charts and images |

### Defaults

- **Default content-slide headline**: `{typography.h2}` (3.4vw at weight 700). `{typography.h1}` is for chapter breaks, not standard content slides.
- **Default title-slide display**: `{typography.display}` (9vw at weight 800).
- **Default body size**: `{typography.body}` (1.1vw at weight 400).
- **Default label / kicker size**: `{typography.label}` (0.72vw).
- **Default numeral size**: `{typography.stat-value}` (4.6vw at weight 700) for in-cell KPIs.

When unsure, the canonical pairing is `{typography.h2}` for the headline, one `{typography.lead}` paragraph for the supporting block, and a `{typography.label}` kicker above — all left-aligned on the grid.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every display, h1, h2, h3, and body element is mixed case.** Uppercase is reserved exclusively for JetBrains Mono labels. An uppercase Archivo headline reads as a different system.
- **Every label, kicker, tag, axis, footer, and figure caption uses JetBrains Mono uppercase with at least 0.12em tracking** (kickers at 0.16em). Mono in sentence case does not exist here.
- **All text is left-aligned and ragged-right.** Centered text is permitted only for a single short display line on a title slide, and never for body copy.
- **Exactly one signal-red element per slide.** If a kicker is red, the numeral, underline, and chart highlight on that slide must be ink or graphite.
- **Display type uses negative letter-spacing**: -0.03em at `{typography.display}`, -0.02em at h1 and stat-value. The tight tracking is the display signature.
- **Headlines are `{colors.ink}`; the index numeral is `{colors.graphite}`; labels are `{colors.graphite}` or `{colors.graphite-light}`.** Red never substitutes for a text color at rest — red only marks one element.
- **The bullet-list marker is an em-dash in graphite via JetBrains Mono.** Never a dot, never a check, never an arrow.

### Typography Principles

The rhythm of Swiss Grid is **tightly tracked Archivo display + invisible Inter body + uppercase tracked mono metadata**. Switching Archivo to weight 400 for a headline reads as a different system. Setting a label in Inter rather than mono reads as a different system. Adding italics or underlines to body copy reads as a different system — emphasis is achieved through size and position on the grid, not through slant or line decoration. Bold is not used inside body text; the weight contrast lives only between the display scale and the body scale.

## Layout

### Canvas System

The system targets the fixed 1920×1080 stage model described in the Fixed-Stage Policy above, expressed in the source as fluid `100vw × 100vh` proportions with all sizes in `vw`/`vh`. All 12-column spans, padding, and type sizes are design proportions to be translated onto the 1920×1080 stage. The deck is a horizontal flex strip with slide-to-slide transitions at 0.35s with a sharp ease-out curve — Swiss Grid moves quickly and without ceremony.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding — the content edge on both sides |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4.5vh | Between major content regions |
| `{spacing.gap-md}` | 2.5vh | Between related elements, and the grid column gutter |
| `{spacing.gap-sm}` | 1.2vh | Between tightly related elements (label under numeral) |

The 12-column grid uses `{spacing.gap-md}` (2.5vh) as its fixed column gutter. Common spans: full-width statements span all 12 columns; a headline + lead pair spans 8 columns left-aligned with 4 columns of deliberate emptiness; three stat cells span 4 columns each; a two-column data spread spans 6 and 6.

### Chrome Frame

Most content slides carry a **chrome header** and **chrome foot**. The header is a `flex space-between` row of two mono labels (left: section code such as `SEC. 02 / PROCESS`; right: slide code such as `SHEET 07/24`), separated from the slide body by a 1px ink rule. The foot is a matching row (left: page title; right: date) above a 1px rule. Title slides, chapter breaks, and closing slides suppress the chrome entirely and instead carry the oversize index numeral (`{components.index-num}`) in the lower-left corner at `{spacing.pad-x}` from the edge — the numeral is the chrome on those slides.

## Depth and Elevation

### No Shadows, Hairline Rules Only

The system uses **zero box-shadow declarations** on any structural element. Depth is created through three mechanisms:

1. **1px hairline rules in solid `{colors.ink}`** — under chrome headers, above foot bands, between stat cells, across chart baselines, along timeline spines. The rule is the separator; there is no other kind.
2. **The 44×2px signal-red rule** (`{components.rule-short}`) — the only thicker rule, used as punctuation under a kicker or beside an index numeral, and counting as the slide's one red element.
3. **Whitespace and grid position** — the primary depth signal is what a region is *not* filled with. An empty 4-column gutter next to an 8-column text block creates the hierarchy that other systems fake with shadows.

### No Atmospheric Effects

There are no gradients, no glows, no grain, no blur, no opacity layers beyond the 40%-opacity dormant hairlines. Even the donut chart's center is a same-surface cutout, not a tonal change. Elevation does not exist; adjacency and alignment do.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every structural element — image placeholders, tags, stat cells, tables, chart areas, timeline markers |
| 50% (circle) | Donut chart only |
| 999px (pill) | None — pills do not exist in this system |

Swiss Grid is **square-cornered without exception**. A rounded corner anywhere (cards, buttons, images) reads as another design system entirely.

### Border Weights

- **1px solid `{colors.ink}`** — the universal structural weight: dividers, chrome rules, cell tops, table rules, image-placeholder borders, chart axes.
- **2px solid `{colors.signal-red}`** — used only on the signature rule-short (44px long) as the slide's red punctuation.
- **1px solid `{colors.graphite-light}` at 40% opacity** — dormant hairlines: title-slide column rules and axis tick extensions.

There is no dashed border, no double border, no colored structural border. The only color that ever appears in a border is signal-red on the rule-short.

### Decorative Element Types

**Visible column rules** — On title slides, the 12-column grid is drawn as 1px vertical lines (`{components.col-rule}`) at 40% graphite-light spanning the full content height. The grid is the ornament; no other decoration is permitted on those slides.

**44×2px signal-red rule** — `{components.rule-short}`: a short red bar used under a kicker, beside an index numeral, or as a headline underline via `background: linear-gradient({colors.signal-red}, {colors.signal-red}) no-repeat 0 100% / 44px 2px` on an inline span. It is the system's only red punctuation and its only 2px element.

**Mono kicker** — A graphite JetBrains Mono uppercase eyebrow (`{components.kicker}`) above a headline, tracked at 0.16em. The kicker may optionally be signal-red when it is the slide's one red element.

**Oversized index numeral** — `{components.index-num}`: 6vw Archivo-800 graphite numerals (01, 02, 03…) marking chapter position, typically in the lower-left corner of title and chapter slides. This is the strongest non-accent graphic the system permits.

**Bordered tag** — A square-cornered 1px-ink bordered inline element (`{components.tag}`) with 0.25em × 0.7em padding containing a mono uppercase string — version codes, process-step keys, status labels.

**Stat cell** — A vertical region with a 1px ink top rule (`{components.stat-cell}`), holding a 4.6vw Archivo-700 numeral, an Inter label, and an optional mono source line. Three cells in a row is canonical; the red numeral is allowed only when it is the slide's single red element.

**Square image placeholder** — A 1px-ink-bordered white square (`{components.img-placeholder}`) with `aspect-ratio: 1 / 1` and a centered mono label like `FIG. 03`, plus a mono figure caption below (`{components.figure-caption}`).

**Figure caption** — Mono caption text under charts and images: `FIG. 03 — Q3 FULFILLMENT BY REGION`. Captions are objective and terse; they state what the figure shows and never editorialize.

**Bullet em-dash** — A `—` in JetBrains Mono colored `{colors.graphite}`, prepended via a CSS grid marker column (`grid-template-columns: 1.2em 1fr`).

**Timeline spine** — A 1px vertical ink rule (`{components.timeline-spine}`) with 7px **square** markers (borderRadius 0) per entry. The square marker is a deliberate anti-organic choice: timelines in this system are process diagrams, not flowing stories.

**Donut chart** — A `min(22vw, 36vh)` circle with a conic-gradient ring and a same-surface `::after` cutout. Segments are graphite; one segment may be signal-red as the slide's single accent.

**Vertical bar chart** — Graphite bars at full opacity with a highlighted signal-red bar when the slide's one red element is the highlight. The chart carries a 1px ink baseline and, on dense slides, 1px graphite-light tick extensions with mono axis labels.

**Table** — `{components.table}`: 1px ink column rules and 1px horizontal rules between rows, no zebra striping, no row fills. The header row is mono uppercase labels on ink text.

## Do's and Don'ts

### Do
- Lay every content slide out on the 12-column grid; keep every element inside its declared column span.
- Use the paper background (`{colors.paper}`) on every slide. The single-surface canvas is the foundation.
- Use Archivo at weight 700–800 for all display moments with negative letter-spacing. The machined tight tracking is the display signature.
- Use exactly one signal-red element per slide — kicker, numeral, underline, or one chart series. Never more.
- Set every label, kicker, tag, axis, and footer in JetBrains Mono uppercase with at least 0.12em tracking.
- Keep all text left-aligned and ragged-right.
- Separate regions with 1px ink rules and whitespace. A rule or padding replaces every shadow, every fill change.
- Draw the visible column hairlines on title slides — that is the system's signature ornament.
- Use mono figure captions under every chart and image.
- Leave paper empty. A 4-column gutter of nothing is a designed element.

### Don't
- Don't add a second accent color. Red is the only accent; blue-gray appears only as a justified second chart series.
- Don't use two red elements on one slide. The one-red rule is the system's central discipline.
- Don't round any corner. 0px everywhere; the donut is the only circle.
- Don't use box-shadow, gradients, or backdrop blur anywhere. The system has no elevation and no atmosphere.
- Don't set display or body type in uppercase. Uppercase belongs to mono labels only.
- Don't center body text or multi-line blocks. Centering is a rare title-slide exception.
- Don't set labels in Inter or body copy in mono. The three faces have non-overlapping jobs.
- Don't use bold inside body paragraphs, italics, or underlines (other than the red rule-short). Emphasis comes from size and grid position.
- Don't replace the em-dash bullet marker with dots, checks, arrows, or numerals.
- Don't zebra-stripe tables or fill cells. Ink rules and whitespace carry all the structure.
- Don't crowd the chrome: headers and foots hold exactly two mono labels each.

## Responsive Behavior

The source template is viewport-fluid by design (all sizes in `vw`/`vh`), but per the Fixed-Stage Policy the `html-showcase` output is a fixed 1920×1080 stage scaled uniformly to the viewport — no reflow, no breakpoints, letterboxing or pillarboxing only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions at 0.35s with a sharp `cubic-bezier(0.2, 0.8, 0.2, 1)` ease-out — fast, mechanical, no lingering.
- Entrance animations are minimal and only two are permitted: `fade-up` (12px, 0.4s) for text blocks and `rule-grow` (scaleX from 0 to 1, 0.5s, transform-origin left) for the red rule-short. Both run on slide entrance via `data-anim` with staggered `data-delay` steps.
- Elements with `[data-anim]` start at opacity 0 and animate on `.is-active`; revisiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export captures only the active slide; multi-slide export requires manual navigation per slide.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Archivo 800) | Archivo | Noto Sans SC (思源黑体) | 900 (see Aesthetic Notes) |
| Headline / sub-headline (Archivo 700/600) | Archivo | Noto Sans SC (思源黑体) | 700 |
| Body / lead (Inter 400) | Inter | Noto Sans SC (思源黑体) | 400 |
| Label / mono chrome (JetBrains Mono) | JetBrains Mono | Noto Sans SC | 400 (do not force monospace on CJK; see Aesthetic Notes) |
| Numerals (Archivo 700/800) | Archivo | Noto Sans SC | 900 for 6vw index numerals, 700 elsewhere |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"Archivo, Noto Sans SC, system-ui, sans-serif"` (or the Inter / JetBrains Mono equivalents). Latin glyphs render in the Latin face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed sentences like `流程 12-step SLA 定义` render in one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo:wght@600;700;800&family=Inter:wght@400;500&family=JetBrains+Mono:wght@400&family=Noto+Sans+SC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK (the -0.02em to -0.03em display tracking does not transfer)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `使用 AI 分析` not `使用AI分析`)
- One font per sentence

### Aesthetic Notes for This System

Swiss Grid's display voice is **Archivo 800 with tight negative tracking** — wide, squared, machined letterforms that fill a 9vw display line with presence. Noto Sans SC at 900 is the closest CJK analogue for that presence; at 700 the Chinese display reads slightly lighter than its Archivo neighbor. For 6vw index numerals, set Chinese numerals (or Chinese section titles set beside them) at Noto Sans SC 900 to keep the weight balance.

The uppercase mono voice does not transfer to CJK — Chinese has no uppercase. **Set Chinese labels in Noto Sans SC 400, mixed case, with letter-spacing reset to 0.** The "filing code" register is carried by size, color (graphite), and the mono treatment of any Latin tokens inside the label (version codes, dates stay in JetBrains Mono uppercase). If a label is pure Latin (a code, a date, an axis tick), keep it in JetBrains Mono uppercase exactly as designed.

The em-dash bullet marker (`—`) works perfectly in Chinese — the Chinese em-dash is also `—`. Keep the marker as-is.

The visible 1px column hairlines on title slides behave identically in CJK decks — they are geometry, not glyphs. But because Chinese glyphs are wider, long Chinese titles can collide with the last column rule at the 9vw display size; see the Known CJK Gap.

### Known CJK Gap

Chinese characters are roughly square and consume ~15–20% more horizontal space than Latin at the same point size. A 9vw Archivo display line ("Objective Review") may wrap to two lines at 9vw in Noto Sans SC. Reduce display and h1 sizes by ~15% when the line is pure Chinese (Archivo 9vw → Noto Sans SC 7.6vw), or plan the title-slide grid span for two lines (8 columns instead of 12). The red one-per-slide rule applies unchanged — signal red reads as strong and intentional in Chinese business culture, and the single-element discipline is even more important with denser glyphs.

## Iteration Guide

1. Any new slide background is `{colors.paper}`. Never introduce a dark or chromatic surface.
2. Any new headline uses Archivo in mixed case at weight 700 (h2) or 800 (display/h1), with negative letter-spacing per the token.
3. Any new label, kicker, tag, or metadata uses JetBrains Mono uppercase with at least 0.12em tracking in `{colors.graphite}`.
4. Any new structural divider is a 1px solid ink rule. Use `{components.rule}` for region separation and `{components.rule-short}` (red, 44×2px) for the signature punctuation.
5. Any new accent moment uses `{colors.signal-red}` — and verify it is the only red element on the slide. If a second red appears, demote one to ink or graphite.
6. Any new chart series defaults to graphite; highlight one series in signal-red; use `{colors.blue-gray}` only when a semantic second series is required and caption it.
7. Any new bullet list uses the em-dash in graphite via JetBrains Mono.
8. Any new figure gets a mono caption (`FIG. NN — DESCRIPTION`) and, if it is a placeholder, the square 1px-ink bordered form.
9. Any new data table uses 1px ink rules with no zebra striping and a mono uppercase header row.
10. Keep the chrome to two mono labels per band, and let title/chapter slides carry the oversize index numeral instead of chrome.
11. When in doubt about hierarchy, add whitespace, not ink: empty grid columns are a feature.
12. Never introduce shadows, gradients, rounded corners, or a second accent color — those are other systems.

## Known Gaps

- The title-slide column hairlines are drawn at 40% graphite-light and can become invisible on low-contrast projectors; there is no toggle token for boosting them to full opacity, so a presentation-critical title slide may need a one-off opacity bump in the generated deck.
- The 2.5vh grid gutter is a single fixed value; there is no wide/narrow gutter variant for data-dense spreads, so very dense tables must be handled inside their column span (smaller type, tighter row rules) rather than by widening the gutter.
- The `rule-short` underline technique (`background: linear-gradient(...) no-repeat 0 100% / 44px 2px`) requires the underlined span to be `display: inline`; a multi-line headline needs the background positioned on the last line, which CSS alone cannot target — the red underline should stay on single-line headlines.
- The donut chart uses a same-surface `::after` cutout; if a slide background differs from paper (e.g., a white figure well), the cutout must be restyled to match the well, not the page.
- Bars and donut segments are static (inline `style="height: XX%"` or conic-gradient percentages) — there is no data-binding layer; values are computed manually.
- The animation system requires `.is-active` to be applied for entrances to play; without navigation-engine wiring, `[data-anim]` elements remain at opacity 0.
- The source names the system "Swiss Grid" in the template library; any historical names in source comments refer to the same system.
- Blue-gray exists as a token but has no dedicated component; every use must be hand-built and captioned, which makes misuse easy to introduce silently.
