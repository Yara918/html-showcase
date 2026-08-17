---
version: alpha
name: Blueprint (Drafting Table)
description: A drafting-table blueprint rendered as a design system — a deep blue field, white grid lines, technical lettering, and corner registration marks. JetBrains Mono carries every word like stencil drafting lettering, with Inter 600 reserved for sheet headers; amber pencil annotations provide the one warm human touch. The system presents anything that is "how it's built" — plans, roadmaps, architecture, go-to-market — as a drawing on the table, precise, confident, and engineered.

colors:
  blueprint: "#123C7E"
  blueprint-deep: "#0E2F5E"
  panel-blue: "#15468F"
  line-white: "#EAF2FB"
  line-dim: "#9DB8DC"
  pencil: "#FFB800"
  accent-red: "#FF5A4E"
  vignette: "#0A2144"

color-aliases:
  c-bg: blueprint
  c-bg-light: panel-blue
  c-bg-cream: blueprint-deep
  c-fg: line-white
  c-fg-light: line-white
  c-fg-2: line-dim
  c-fg-3: line-dim
  c-accent: pencil
  c-border: line-white
  c-border-light: line-dim

typography:
  display:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 7.5vw
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: 0.03em
    textTransform: uppercase
  h1:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4vw
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: 0.02em
    textTransform: uppercase
  h2:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 2.6vw
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: 0.02em
    textTransform: uppercase
  h3:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.7vw
    fontWeight: 500
    lineHeight: 1.3
    letterSpacing: 0.08em
    textTransform: uppercase
  lead:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.3vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.7
  caption:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.8vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.72vw
    fontWeight: 500
    letterSpacing: 0.14em
    textTransform: uppercase
  dimension:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.95vw
    fontWeight: 500
    lineHeight: 1.3
  field-value:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.1vw
    fontWeight: 500
    lineHeight: 1.3
    letterSpacing: 0.04em
    textTransform: uppercase
  callout-title:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.3vw
    fontWeight: 600
    lineHeight: 1.3
    letterSpacing: 0.08em
    textTransform: uppercase

spacing:
  pad-x: 5vw
  pad-y: 5vh
  gap-lg: 4vh
  gap-md: 2.4vh
  gap-sm: 1.2vh

canvas:
  width: 100vw
  height: 100vh

components:
  grid-layer:
    backgroundImage: "repeating-linear-gradient(to right, rgba(234,242,251,0.04) 0 1px, transparent 1px 4px), repeating-linear-gradient(to bottom, rgba(234,242,251,0.04) 0 1px, transparent 1px 4px), repeating-linear-gradient(to right, rgba(234,242,251,0.12) 0 1px, transparent 1px 40px), repeating-linear-gradient(to bottom, rgba(234,242,251,0.12) 0 1px, transparent 1px 40px)"
    description: "Layered drafting grid — minor lines every ~4px at 4% white, major lines every ~40px at 12% white — built from four repeating-linear-gradients on the slide background."
  registration-cross:
    width: 18px
    height: 18px
    backgroundImage: "linear-gradient({colors.line-dim} 0 1px, transparent 1px), linear-gradient(90deg, {colors.line-dim} 0 1px, transparent 1px)"
    backgroundPosition: "center center"
    opacity: 0.7
    description: "✚ registration cross at each of the four slide corners — a 1px vertical and horizontal bar crossing at center, inset ~2vw from the edges."
  title-block:
    border: "1px solid rgba(234,242,251,0.4)"
    display: grid
    gridTemplateColumns: "auto 1fr auto"
    background: "rgba(18,60,126,0.55)"
    description: "Bottom-right drafting title block with PROJECT / SCALE / DATE / REV fields, set in {typography.field-value} over a translucent blueprint fill."
  dimension-line:
    stroke: "{colors.line-white}"
    strokeWidth: 1px
    description: "SVG dimension line with arrowheads (a polygon marker) and a mono measurement label ('↔ 120.0') in {typography.dimension}, extending between extension lines."
  leader-line:
    stroke: "{colors.line-dim}"
    strokeWidth: 1px
    strokeDasharray: "4 3"
    fill: none
    description: "Dashed SVG leader from an annotation or node to its label — drafting's way of pointing without a heavy arrow."
  callout-box:
    border: "1px solid rgba(234,242,251,0.35)"
    background: "rgba(18,60,126,0.4)"
    padding: "{spacing.gap-md}"
    description: "Technical callout box with a {typography.callout-title} header and mono body — a bordered note that lives inside the drawing, not beside it."
  pencil-note:
    color: "{colors.pencil}"
    fontFamily: "{typography.body.fontFamily}"
    transform: "rotate(-1.5deg)"
    description: "Amber pencil annotation for human emphasis — a rotated note, a circled number, or a squiggled underline (SVG path) that marks 'an engineer looked at this.'"
  plan-line:
    stroke: "{colors.line-white}"
    strokeWidth: 2px
    description: "The 2px structural line of the plan itself — walls, blocks, architecture strokes. Heavier than grid and dimension lines, drawn as SVG."
  section-fill:
    fill: "rgba(234,242,251,0.06)"
    description: "Faint white fill for plan blocks and sections — suggests volume without breaking the flat drawing."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Blueprint (Drafting Table) is a **drawing system**: every slide is a sheet on a drafting table, and everything on it — the grid, the lines, the lettering, the title block — is drawn, not laid out. The founding idea is the architectural blueprint: a deep blue field (`{colors.blueprint}`) whose white lines read as light, a grid that is simultaneously the canvas and the content, and a discipline of lettering that treats text as annotation rather than design. The system is for anything that answers "this is how it's built" — project plans, planning roadmaps, technical architecture, go-to-market blueprints — where the confidence of the drawing is the message.

The system's defining material is the **layered grid**. The slide background is not a flat blue — it is two grid systems stacked: minor lines every ~4px at 4% white and major lines every ~40px at 12% white, both drawn with `repeating-linear-gradient` (`{components.grid-layer}`). The grid is never optional and never decorative; it is the drawing surface, and it does two jobs at once: it gives the eye a scale to read measurements against, and it quietly says "this was made with instruments." A blueprint without the grid is just a dark blue slide; with it, every line the content draws is visibly *on* the paper.

Everything in the system is a **line before it is a shape**. Walls and architecture strokes are 2px `{colors.line-white}` SVG paths (`{components.plan-line}`); dimensions are 1px lines with arrowheads and mono measurements (`{components.dimension-line}`); annotations reach their labels along dashed leaders (`{components.leader-line}`); regions fill with 6% white (`{components.section-fill}`) — enough to suggest volume, never enough to read as a colored panel. The system's restraint on fills is absolute: on a blueprint, weight means line weight, not fill. When the eye needs a moment of emphasis, the system reaches for the one warm color it allows: amber pencil (`{colors.pencil}`).

**Typography is drafting lettering.** JetBrains Mono at weights 400–600 carries every word on the sheet — headers, labels, bodies, dimensions, title-block fields — because drafting lettering was always stencil-like and monospaced, uniform strokes drawn with a lettering guide. Inter 600 is reserved for sheet-level headers only (display, h1, h2), where a slightly softer grotesque reads as the sheet's title rather than its annotation. There is no serif, no handwriting in the drawing itself — but the amber pencil note (`{components.pencil-note}`), rotated −1.5° and drawn by hand, is the system's permission slip for a human to exist inside the machine. That one warm, imperfect element is what keeps the system from feeling cold: the blueprint is perfect, and the pencil is where the thinking happened.

**Retro-future, not retro.** The system borrows the drafting table but does not pretend to be 1962. The grid is rendered in CSS gradients, the dimension markers are SVG, the lettering is a contemporary mono — the aesthetic is *how a future engineering culture would keep drafting as its metaphor*, which is why it fits product plans and go-to-market blueprints as naturally as it fits architecture.

**Key Characteristics:**
- Deep blue field (`{colors.blueprint}`) with a layered major/minor grid (`{components.grid-layer}`) on every slide — the grid never turns off.
- ✚ registration crosses (`{components.registration-cross}`) at all four corners, inset ~2vw — every sheet is registered to the table.
- JetBrains Mono lettering for everything; Inter 600 for sheet headers only.
- A bordered title block bottom-right (`{components.title-block}`) — PROJECT / SCALE / DATE / REV — on every content slide.
- Dimension lines with arrowheads and mono measurements ("↔ 120.0") and dashed leader lines (`stroke-dasharray: 4 3`) to labels.
- Technical callout boxes (`{components.callout-box}`) — bordered notes inside the drawing.
- Amber pencil annotations (`{colors.pencil}`) for emphasis — the one warm human touch; `{colors.accent-red}` is the rare danger mark.
- Lines before shapes: 2px plan strokes, 1px dimension/leader lines, 6% section fills, and no drop shadows anywhere.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.blueprint}` | #123C7E | Default sheet field. The blueprint blue — deep enough for white lines to read as light. |
| `{colors.blueprint-deep}` | #0E2F5E | Deeper blue for reverse moments and edge vignettes — the sheet's shadow side. |
| `{colors.panel-blue}` | #15468F | Lighter panel tone for inset regions and callout bases (`c-bg-light`). |
| `{colors.line-white}` | #EAF2FB | Primary drawing ink — plan lines, text, dimensions, borders. Cool white, slightly blue. |
| `{colors.line-dim}` | #9DB8DC | Secondary line — leaders, extension lines, registration crosses, muted labels. |
| `{colors.pencil}` | #FFB800 | Amber pencil annotation — the system's accent (`c-accent`) and only warm color. |
| `{colors.accent-red}` | #FF5A4E | Rare marking — errors, danger, non-negotiable callouts. One red moment per slide maximum. |
| `{colors.vignette}` | #0A2144 | Deep edge tone for the optional vignette — the lamp-lit drafting table's shadow. |

### Defaults

- **Default sheet background**: `{colors.blueprint}` with the full grid layer. The grid is part of the background, not an overlay you may remove.
- **Default text color**: `{colors.line-white}` for primary text; `{colors.line-dim}` for leaders, extension lines, and muted labels.
- **Default headline color**: `{colors.line-white}`. Headlines never appear in pencil or red.
- **Default accent**: `{colors.pencil}` — used for annotations and emphasis only, never for structure.
- **Default border**: `{colors.line-white}` at 35–40% opacity (via `rgba(234,242,251,…)`); the full-value white border is reserved for plan lines.
- **Default plan stroke**: 2px `{colors.line-white}`; **default dimension/leader stroke**: 1px `{colors.line-white}` / `{colors.line-dim}`.
- **Default section fill**: `rgba(234,242,251,0.06)` — barely-there volume.
- **Default red usage**: one `{colors.accent-red}` element per slide, and only for danger or non-negotiable marks.

### Semantic Roles

The palette is a **drawing-ink system**: line-white is the primary ink, line-dim is the secondary ink, pencil is the human ink, and accent-red is the alarm ink. Blue tones are the paper (field, deep, panel); they never carry text on their own. Pencil is the system's accent because it is the one color that exists *outside* the drawing — it is what an engineer adds on top, so it is the natural home for emphasis, callouts, and "look here" moments. Red is for things that must not be missed — a red X, a red circled number — and its rarity is its power; a slide with three red marks stops reading as a drawing and starts reading as a warning. Line-white and line-dim carry all structure; nothing structural is ever pencil or red.

## Typography

### Font Family

The system loads exactly three families: **JetBrains Mono** (weights 400, 500, 600) for every word on the sheet except sheet headers; **Inter** (weights 400, 600; the system uses 600) for display, h1, and h2; **Noto Sans SC** as the CJK fallback for both. The mono-first decision is the system's identity: drafting lettering was lettering-guide stenciled, uniform and monospaced, so a mono face *is* the correct translation of the source material — not a stylistic joke. JetBrains Mono's industrial, machine-era construction also carries the retro-future register: it is a machine face, comfortable on a drafting table and equally comfortable in a developer's terminal.

The emotional register of each face is fixed:
- **JetBrains Mono 600** — callout titles, label weight, emphasis. The strongest stencil voice.
- **JetBrains Mono 500** — dimensions, field values, labels, h3. The working annotation voice.
- **JetBrains Mono 400** — body, lead, captions. The quiet, mechanical text.
- **Inter 600** — sheet headers only. A slight human ease at the top of the sheet; everything below is machine lettering.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 7.5vw | Inter | 600 | Cover or opening sheet title — uppercase, 0.03em tracking |
| `{typography.h1}` | 4vw | Inter | 600 | Chapter-opening or section-break headline |
| `{typography.h2}` | 2.6vw | Inter | 600 | Primary content-slide headline |
| `{typography.h3}` | 1.7vw | JetBrains Mono | 500 | Panel and region headers — uppercase, 0.08em tracking |
| `{typography.callout-title}` | 1.3vw | JetBrains Mono | 600 | Callout-box header — uppercase, 0.08em tracking |
| `{typography.lead}` | 1.3vw | JetBrains Mono | 400 | Lead paragraph or single supporting block |
| `{typography.field-value}` | 1.1vw | JetBrains Mono | 500 | Title-block values (PROJECT / SCALE / DATE / REV) — uppercase, 0.04em |
| `{typography.body}` | 1.05vw | JetBrains Mono | 400 | Body copy inside callouts and annotations |
| `{typography.dimension}` | 0.95vw | JetBrains Mono | 500 | Measurement labels ("↔ 120.0") |
| `{typography.caption}` | 0.8vw | JetBrains Mono | 400 | Source notes, sheet notes, fine print |
| `{typography.label}` | 0.72vw | JetBrains Mono | 500 | Chrome label, kicker — uppercase, 0.14em tracking |

### Defaults

- **Default section headline**: `{typography.h2}` (2.6vw Inter 600). Reserve `{typography.h1}` for chapter breaks.
- **Default opening / cover display**: `{typography.display}` (7.5vw Inter 600).
- **Default body size**: `{typography.body}` (1.05vw JetBrains Mono 400).
- **Default label size**: `{typography.label}` (0.72vw); **default dimension size**: `{typography.dimension}` (0.95vw).
- **Default weight for sheet headers**: 600 (Inter). **Default weight for all lettering**: 400–600 (JetBrains Mono).
- **Default tracking**: 0.02–0.03em on sheet headers, 0.04em on field values, 0.08–0.14em on uppercase mono labels, 0 on body.

When unsure, the canonical pairing is `{typography.h2}` (Inter 600, uppercase) + one `{typography.lead}` block in JetBrains Mono 400, with a callout box and a title block. The contrast between the soft sans header and the machine mono body is deliberate: the sheet is titled by a hand, annotated by a machine.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **The layered grid is always on** (`{components.grid-layer}`): minor ~4px lines at 4% white and major ~40px lines at 12% white via four `repeating-linear-gradient`s. No slide exists without it.
- **✚ registration crosses sit at all four corners** (`{components.registration-cross}`), inset ~2vw, at 70% `{colors.line-dim}` opacity. Every sheet is registered.
- **Dimension lines carry arrowheads and mono measurements** (`{components.dimension-line}`) — SVG line + polygon arrowhead marker + "↔ 120.0" in `{typography.dimension}`.
- **Annotations reach their labels along dashed leader lines** (`{components.leader-line}`) — `stroke: {colors.line-dim}; stroke-dasharray: 4 3`.
- **Every content slide carries a bordered title block bottom-right** (`{components.title-block}`) with PROJECT / SCALE / DATE / REV in `{typography.field-value}`.
- **Explanations live in technical callout boxes** (`{components.callout-box}`) — bordered, mono-headed, inside the drawing.
- **Emphasis is amber pencil** (`{colors.pencil}`) — rotated annotations, circled numbers, squiggled underlines (`{components.pencil-note}`). Red (`{colors.accent-red}`) marks danger only, one moment per slide.
- **Lettering is JetBrains Mono** for everything except sheet headers; sheet headers are Inter 600 uppercase. No other faces exist.

### Typography Principles

The rhythm of Blueprint is **sans sheet header + mono machine lettering + one pencil moment**. Setting body text in Inter reads as a different system (a tech deck, not a drawing); setting a header in JetBrains Mono reads as a different system (all-annotation, no title). Uppercase is the default for headers, labels, field values, and callout titles; body and lead stay sentence-case for reading. Underline exists only as the pencil squiggle; bold exists only as mono 600. Every measurement, version, date, and coordinate is set in `{typography.dimension}` or `{typography.field-value}` — numbers are lettered, never typeset loose.

## Layout

### Canvas System

The source template targets a fluid `100vw × 100vh` viewport with all sizes in `vw`/`vh`; under the Fixed-Stage Policy these translate directly into 1920×1080 stage coordinates. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `reveal-right`, `reveal-left`, `scale-in`) run per slide with stagger delays via `data-delay` attributes; plan lines may additionally draw in via `stroke-dashoffset` (see Responsive Behavior).

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 5vw | Slide horizontal padding — the sheet margin; registration crosses sit inside it |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4vh | Between the header strip, the drawing area, and the title block |
| `{spacing.gap-md}` | 2.4vh | Between plan blocks, callouts, and label clusters |
| `{spacing.gap-sm}` | 1.2vh | Between a leader-line label and its element, between field rows |

### Chrome Frame

Most content slides carry a **drafting header strip** and the **title block**. The header is a `flex space-between` row of two `{typography.label}` readouts — left: "PROJECT — <name> // REV C", right: "SHEET 03 OF 08" — separated from the body by a 1px `rgba(234,242,251,0.35)` rule. The bottom-right corner of every content slide carries the `{components.title-block}`: a bordered, translucent-blue grid with PROJECT / SCALE / DATE / REV fields in `{typography.field-value}`. The title block is not optional chrome — it is the sheet's identity, and removing it makes the slide an orphan drawing. Cover, chapter-break, and closing slides suppress the header and title block but keep the grid and registration crosses.

The **drawing area** sits between header and title block: the plan (SVG lines and blocks), its dimension and leader lines, its callout boxes, and its pencil annotations. Nothing in the drawing area is filled more than 6% white — volume is line and section-fill, never a colored panel.

## Depth and Elevation

### No Shadows; Depth Is Line Weight and Light

The system uses **zero box-shadow declarations**. Depth comes from three drafting-specific mechanisms:

1. **Line-weight contrast** — 2px plan strokes against 1px dimension/leader lines against the faint grid. In drafting, heavier line = closer to the viewer; the plan is the closest thing on the sheet.
2. **Grid density** — the major/minor grid gives every element a scale and a "depth of field": content drawn over the grid reads as sitting on the paper; the grid itself reads as the paper.
3. **The optional vignette** — a very subtle radial gradient of `{colors.vignette}` at the sheet edges (`radial-gradient(ellipse at center, transparent 60%, rgba(10,33,68,0.55) 100%)`) suggesting the lamp-lit drafting table. Optional and faint; it must never read as a dark frame.

### The One Translucent Surface

The only non-flat surfaces are the translucent fills of the title block (`rgba(18,60,126,0.55)`) and callout boxes (`rgba(18,60,126,0.4)`) — both are "paper under the plan," slightly deeper blueprint that lets the grid show through. No glows, no blurs, no grain. The amber pencil is flat — a pencil does not glow.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Everything structural — title block, callout boxes, plan blocks, labels. Drawings are square. |
| 50% (circle) | Registration-cross target dots and any plan circles drawn as geometry |
| 999px (pill) | None — pills are UI, not drafting |

The system is entirely square-cornered. A rounded callout box would read as a modern dashboard card; on a blueprint, boxes are drawn with a straightedge.

### Border Weights

- **1px solid `rgba(234,242,251,0.35)`** — title-block and callout-box borders, header rules.
- **1px solid `{colors.line-white}`** — dimension lines and extension lines.
- **1px dashed `{colors.line-dim}`** — leader lines (`stroke-dasharray: 4 3`), drawn as SVG, never as CSS borders.
- **2px solid `{colors.line-white}`** — plan lines: walls, blocks, architecture strokes (`{components.plan-line}`).
- **18px ✚** — registration-cross size (two crossing 1px bars).

### Decorative Element Types

**Layered grid** — The background (`{components.grid-layer}`): four `repeating-linear-gradient`s — minor vertical/horizontal every ~4px at 4% white, major vertical/horizontal every ~40px at 12% white. Rendered once on the slide root; content sits above it, never replaces it.

**Registration cross** — An 18px ✚ (`{components.registration-cross}`) at each of the four corners, inset ~2vw, built from two 1px `{colors.line-dim}` gradient bars (`background-image: linear-gradient(… 0 1px, transparent 1px), linear-gradient(90deg, …)`) at 70% opacity. The sheet declares itself registered to the table.

**Title block** — The bottom-right identity block (`{components.title-block}`): a `grid` of field rows (PROJECT / SCALE / DATE / REV), 1px `rgba(234,242,251,0.4)` border, `rgba(18,60,126,0.55)` fill, values in `{typography.field-value}` (JetBrains Mono 500, uppercase, 0.04em).

**Dimension line** — An SVG construction (`{components.dimension-line}`): a 1px `{colors.line-white}` line with a polygon arrowhead marker at each end, a mono measurement ("↔ 120.0") in `{typography.dimension}` above the line, and thin extension lines running to the measured points.

**Leader line** — A dashed SVG path (`{components.leader-line}`): `stroke: {colors.line-dim}; stroke-width: 1px; stroke-dasharray: 4 3; fill: none`, from an annotation or node to its label. The system's pointing device — a leader never carries an arrowhead heavier than a dot.

**Callout box** — A bordered note inside the drawing (`{components.callout-box}`): 1px `rgba(234,242,251,0.35)` border, `rgba(18,60,126,0.4)` fill, a `{typography.callout-title}` header (JetBrains Mono 600, uppercase, 0.08em) and mono body. Sits on the grid; the grid shows through its translucent fill.

**Pencil note** — The human moment (`{components.pencil-note}`): `{colors.pencil}` text, `transform: rotate(-1.5deg)`, in `{typography.body}` — a rotated annotation, a circled number (SVG ellipse + mono numeral), or a squiggled underline (a small SVG path with two tight S-curves under a word). One or two per slide; the pencil is where the thinking happened.

**Plan line** — The structural stroke (`{components.plan-line}`): 2px `{colors.line-white}` SVG paths for walls, blocks, and architecture; regions optionally carry `{components.section-fill}` at `rgba(234,242,251,0.06)`.

## Do's and Don'ts

### Do
- Keep the layered grid on every slide — minor lines at 4% white, major lines at 12% white. The grid is the paper.
- Put a ✚ registration cross in all four corners, inset ~2vw, at 70% `{colors.line-dim}` opacity.
- Letter everything in JetBrains Mono; sheet headers only in Inter 600 uppercase.
- Carry a bordered title block (PROJECT / SCALE / DATE / REV) bottom-right on every content slide.
- Draw dimensions as 1px lines with arrowheads and mono measurements ("↔ 120.0") in `{typography.dimension}`.
- Reach labels along dashed leader lines (`stroke-dasharray: 4 3`, `{colors.line-dim}`).
- Put explanations in technical callout boxes inside the drawing.
- Emphasize with amber pencil (`{colors.pencil}`) — rotated annotations, circled numbers, squiggled underlines. One or two per slide.
- Use `{colors.accent-red}` for danger marks only — one red moment per slide maximum.
- Draw weight with lines (2px plan vs 1px dimension), not with fills; section fills stay at 6% white.

### Don't
- Don't remove or flatten the grid. A blueprint without the grid is just a dark blue slide.
- Don't use drop shadows, glows, or blur anywhere. Depth is line weight, grid density, and the optional faint vignette.
- Don't set body or annotation text in Inter — mono lettering is the contract; sans is for sheet headers only.
- Don't round any corner. Drawings are square; a rounded callout reads as a dashboard card.
- Don't use filled colored panels — volume is 2px lines and 6% section fills, never a colored rectangle.
- Don't use pencil for structure or borders; pencil is the human layer, added on top of the machine drawing.
- Don't use more than one red mark per slide; red is alarm ink and its rarity is its power.
- Don't letter measurements in anything but `{typography.dimension}` — numbers are part of the drawing language.
- Don't let the vignette read as a dark frame; it must stay a faint lamp-light falloff.
- Don't ship a content slide without its title block; the sheet needs its identity.

## Responsive Behavior

The source template is viewport-fluid by design; under the Fixed-Stage Policy those `vw`/`vh` proportions become fixed 1920×1080 stage coordinates, and the stage scales as one unit. Do not add breakpoints or reflow content for mobile — letterbox or pillarbox instead.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (fade-up, fade-in, reveal-right, reveal-left, scale-in) with stagger delays via `data-delay="N"` where N maps to a discrete delay step (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Plan lines and dimension lines may draw in on entrance via `stroke-dasharray`/`stroke-dashoffset` animation (set the dash to the path length, animate offset from length to 0 over ~1s). Use at most one drawing line per slide — the effect is strongest as a single drafting moment.
- The title block and callout boxes fade up after the plan resolves, so the sheet "finishes drawing" before it is annotated.
- Elements with `[data-anim]` start invisible (opacity:0) and animate on `.is-active` — re-visiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. Blueprint is the most print-friendly system in the library — its flat colors, hairline rules, and mono lettering survive PDF export well; verify that the 4% minor grid still prints (some pipelines drop sub-5% opacity layers) and that `stroke-dasharray` leaders render as dashes on the PDF.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Sheet header (Inter 600) | Inter | Noto Sans SC (思源黑体) | 600 or 700 (no uppercase, tracking 0 — see Aesthetic Notes) |
| Body / lead (JetBrains Mono 400) | JetBrains Mono | Noto Sans SC (思源黑体) | 400 or 500 |
| Label / callout title (JetBrains Mono 500–600) | JetBrains Mono | Noto Sans SC (思源黑体) | 500 or 600 |
| Dimension / field value (JetBrains Mono 500) | JetBrains Mono | Noto Sans SC (思源黑体) | 500 (measurements stay Latin — see below) |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"JetBrains Mono, Noto Sans SC, monospace"` or `"Inter, Noto Sans SC, system-ui, sans-serif"`. Latin glyphs render in JetBrains Mono / Inter; CJK glyphs fall through to Noto Sans SC. No per-language class needed. Mixed lines like `方案 REV C — 已评审` render in one run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500;600&family=Inter:wght@400;600&family=Noto+Sans+SC:wght@400;500;700&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.1–1.2
- Letter-spacing: 0 on CJK
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `使用 AI` not `使用AI`)
- One font per sentence

### Aesthetic Notes for This System

Blueprint's Latin voice is **stencil drafting lettering** — JetBrains Mono, uniform and machine-drawn. Noto Sans SC is the correct Chinese pairing because Chinese characters are themselves uniform and machine-adjacent at body sizes; the "lettering guide" feel survives in Noto Sans SC 500 far better than it would in a serif. The bigger question is **uppercase**: the system's sheet headers, labels, field values, and callout titles are all uppercase with tracking — and **CJK has no uppercase and should not be tracked**. Chinese headers in Noto Sans SC 600, mixed case, letter-spacing 0, keep the register through size and weight instead. Keep the *field names* of the title block (PROJECT / SCALE / DATE / REV) in Latin uppercase even on fully Chinese sheets — that is the drafting convention, and it reads as authentic rather than untranslated; the *values* can be Chinese (项目名, 1:50, 2025-06, Rev B).

Measurements are the system's one strictly Latin rule: **dimension labels stay in Latin digits and units** ("↔ 120.0") even in Chinese decks, because a blueprint's measurements are its universal language; Chinese unit words (米, 万) may follow in Noto Sans SC 500. The amber pencil annotation translates beautifully — 手写体 emphasis works in Chinese with a brush or pen note; use Noto Sans SC 500 at `{typography.body}` size with the −1.5° rotation, and keep it to one or two characters more than a Latin note would allow (Chinese is denser).

### Known CJK Gap

The uppercase + tracking system is a **Latin-only property**. Chinese headers lose the all-caps drafting look entirely; compensate with Noto Sans SC 600–700 and the short-phrase discipline (2–6 characters per header). Chinese body text in a mono-first system also loses the "monospaced" feel — Noto Sans SC is proportional, so a Chinese callout reads as a normal text box rather than lettering; the border and the grid showing through the translucent fill carry the drafting cue instead. Chinese field values in the title block may overflow the field row at `{typography.field-value}` size — allow the value column to wrap or widen the block. And the 4px minor grid, tuned for Latin optical rhythm, is invisible *under* dense Chinese text; when a slide is text-heavy, verify the major grid (12% white) still reads around the content.

## Iteration Guide

1. Any new slide keeps the layered grid (`{components.grid-layer}`) on the root background — minor 4px at 4% white, major 40px at 12% white. Never flatten it.
2. Any new slide keeps ✚ registration crosses at all four corners, inset ~2vw, at 70% `{colors.line-dim}` opacity.
3. Any new sheet header uses Inter 600 uppercase — display 7.5vw, h1 4vw, h2 2.6vw. Never a mono sheet header.
4. Any new label, callout title, or field value uses JetBrains Mono 500–600 uppercase with 0.08–0.14em tracking; any new body or lead uses JetBrains Mono 400 sentence-case.
5. Any new content slide carries the title block bottom-right (PROJECT / SCALE / DATE / REV) in `{typography.field-value}`.
6. Any new plan element is an SVG line: 2px `{colors.line-white}` for structure, 1px for dimensions, 1px dashed (`4 3`) `{colors.line-dim}` for leaders.
7. Any new dimension carries arrowheads and a mono measurement in `{typography.dimension}`; any new annotation reaches its label along a dashed leader.
8. Any new explanation goes in a callout box (`{components.callout-box}`) — 1px `rgba(234,242,251,0.35)` border, `rgba(18,60,126,0.4)` fill, mono header.
9. Any new emphasis uses amber pencil (`{components.pencil-note}`) — rotated note, circled number, squiggle underline; `{colors.accent-red}` only for danger, one moment per slide.
10. Any new region fill stays at `rgba(234,242,251,0.06)` or below. If a region needs more presence, draw a heavier line — never a brighter fill.

## Known Gaps

- The `repeating-linear-gradient` grid at 4px minor spacing renders slightly differently across browsers (sub-pixel rounding); verify the major grid lines at 40px remain visually dominant in the target renderer. The grid is decorative but load-bearing — do not "fix" it by removing a layer.
- The vignette (`{colors.vignette}`) is optional and must stay faint; on projectors with low contrast it can read as a dark frame — if so, drop it rather than lighten it.
- `stroke-dashoffset` draw-in animation requires the path length known in advance; on multi-segment plan lines it can glitch mid-animation — test on the final polyline before shipping.
- The title block's `rgba(18,60,126,0.55)` fill assumes the slide is `{colors.blueprint}`; on the rare `{colors.blueprint-deep}` reverse slide the block's translucency changes apparent tone — verify legibility of `{typography.field-value}` against it.
- JetBrains Mono has no italic and no heavy weight; emphasis inside body text cannot use mono-bold — use the pencil layer instead, which is the system's intended emphasis mechanism anyway.
- Chinese headers cannot take uppercase/tracking (see CJK section), so a Chinese deck loses the all-caps drafting register on headers; the register is carried by the title block's Latin field names and the mono body — mention this trade-off when delivering a Chinese blueprint deck.
- The system is drawing-first; photographic or illustrative content has no natural home on the sheet. Place images only as plan-area voids with a dimension line and a label, never as full-bleed art.
