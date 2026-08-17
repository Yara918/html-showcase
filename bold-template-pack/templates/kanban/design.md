---
version: alpha
name: Kanban (Cork Wall)
description: A physical kanban wall rendered as a design system — cork-board texture, washi-tape column headers, and sticky notes in five colors, all set in handwriting type. Caveat carries every heading with energetic marker strokes; Patrick Hand handles note bodies with honest legibility. The system is deliberately imperfect: notes tilt ±1–2°, tape strips are translucent and slightly askew, and "done" notes fade — but the wall underneath is disciplined, so the chaos reads as teamwork, not clutter.

colors:
  cork: "#C9996B"
  cork-deep: "#A87C4E"
  whiteboard: "#F7F7F5"
  sticky-yellow: "#FFD166"
  sticky-pink: "#F4A7B9"
  sticky-green: "#A8D5A2"
  sticky-blue: "#9EC5FE"
  sticky-orange: "#FFB85C"
  ink: "#2A2A28"
  ink-soft: "#6E6E66"
  tape: "rgba(255,255,255,0.35)"

color-aliases:
  c-bg: cork
  c-bg-light: whiteboard
  c-bg-cream: whiteboard
  c-fg: ink
  c-fg-light: ink
  c-fg-2: ink-soft
  c-fg-3: ink-soft
  c-accent: sticky-yellow
  c-border: ink
  c-border-light: ink-soft

typography:
  display:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 9vw
    fontWeight: 700
    lineHeight: 0.95
    letterSpacing: 0.01em
  h1:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 5.5vw
    fontWeight: 700
    lineHeight: 1.05
  h2:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 3.6vw
    fontWeight: 600
    lineHeight: 1.15
  h3:
    fontFamily: "Patrick Hand, Noto Sans SC, cursive"
    fontSize: 1.9vw
    fontWeight: 400
    lineHeight: 1.3
  lead:
    fontFamily: "Patrick Hand, Noto Sans SC, cursive"
    fontSize: 1.5vw
    fontWeight: 400
    lineHeight: 1.55
  body:
    fontFamily: "Patrick Hand, Noto Sans SC, cursive"
    fontSize: 1.15vw
    fontWeight: 400
    lineHeight: 1.6
  caption:
    fontFamily: "Patrick Hand, Noto Sans SC, cursive"
    fontSize: 0.9vw
    fontWeight: 400
    lineHeight: 1.5
  label:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 1.2vw
    fontWeight: 600
    lineHeight: 1.2
  note-title:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 2.3vw
    fontWeight: 600
    lineHeight: 1.1
  note-body:
    fontFamily: "Patrick Hand, Noto Sans SC, cursive"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.5
  wip-num:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 1.5vw
    fontWeight: 700
    lineHeight: 1.0
  stat-value:
    fontFamily: "Caveat, Ma Shan Zheng, cursive"
    fontSize: 5.5vw
    fontWeight: 700
    lineHeight: 1.0

spacing:
  pad-x: 5vw
  pad-y: 5vh
  gap-lg: 4vh
  gap-md: 2.4vh
  gap-sm: 1.3vh

canvas:
  width: 100vw
  height: 100vh

components:
  tape-header:
    background: "{colors.tape}"
    padding: "0.35em 1.2em"
    transform: "rotate(-2deg)"
    boxShadow: "0 2px 6px rgba(0,0,0,0.12)"
    borderRadius: 2px
    description: "Column header rendered as a washi-tape strip — translucent white at 35%, slightly rotated, with a small shadow. Reads as taped-on, not painted-on."
  sticky-note:
    background: "{colors.sticky-yellow}"
    borderRadius: 3px
    boxShadow: "0 6px 14px rgba(0,0,0,0.18)"
    padding: "1em 1.1em"
    description: "The workhorse surface. A colored rectangle with a soft drop shadow and a ±1–2° rotation; carries a Caveat title and a Patrick Hand body."
  sticky-fold:
    background: "linear-gradient(to bottom, rgba(0,0,0,0.07), transparent 20%)"
    description: "Faint darker gummed edge at the top of a sticky note via a pseudo-element, echoing the adhesive strip of a real note."
  wip-badge:
    width: 24px
    height: 24px
    borderRadius: 50%
    background: "{colors.ink}"
    color: "{colors.whiteboard}"
    fontFamily: "{typography.wip-num.fontFamily}"
    fontSize: "{typography.wip-num.fontSize}"
    description: "Small circular badge showing the column's work-in-progress limit. The number is Caveat 700 on ink; the circle is the column's discipline meter."
  cork-dot-texture:
    backgroundImage: "radial-gradient(circle, rgba(0,0,0,0.05) 1.5px, transparent 1.5px)"
    backgroundSize: "26px 26px"
    description: "Repeating radial-dot pattern over the cork base that gives the wall its tactile grain. Cheap, uniform, and never photorealistic."
  whiteboard-grid:
    backgroundImage: "radial-gradient(circle, rgba(42,42,40,0.12) 1px, transparent 1px)"
    backgroundSize: "22px 22px"
    description: "Dot-grid alternative for the whiteboard surface — the 'clean' variant for planning slides that need less texture."
  board-column:
    background: "rgba(255,255,255,0.12)"
    borderRadius: 6px
    padding: "{spacing.gap-md}"
    description: "A column panel on the cork wall — a barely-lighter zone holding a tape header, a WIP badge, and a stack of sticky notes."
  arrow-connector:
    content: "→"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: 2.5vw
    color: "{colors.ink}"
    opacity: 0.6
    description: "Handwritten-style arrow between columns, drawn as an inline SVG path with a polygon arrowhead at 55% ink opacity — the wall's flow direction."
  done-note:
    opacity: 0.55
    filter: "saturate(0.7)"
    description: "Completed sticky notes fade to 55% opacity and lose saturation — the wall's memory of what already moved on."
  pushpin:
    width: 10px
    height: 10px
    borderRadius: 50%
    background: "radial-gradient(circle at 35% 30%, #FFE9D6, #D64541 65%)"
    boxShadow: "0 2px 3px rgba(0,0,0,0.3)"
    description: "Tiny pushpin rendered as a radial-gradient sphere with a highlight, pinned at a note's top corner for extra physicality."
  divider-line:
    height: 1px
    background: "{colors.ink}"
    opacity: 0.15
    description: "Faint ink hairline inside a note or panel separating blocks — the only straight line allowed inside an otherwise tilted world."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Kanban (Cork Wall) is a **physical-wall system**: every slide is a wall in progress, with columns, sticky notes, tape, pins, and arrows — the honest working surface of a team that is mid-flow, not a finished report. The aesthetic starts from the real kanban board: cork where you pin things, tape where you label things, notes where you commit things. The system's job is to make project status, sprints, standups, and retrospectives feel *alive* — as if the team just stepped away from the wall and the audience is reading the state of the work.

The key design decision is **controlled imperfection**. Nothing on the wall is perfectly aligned: tape strips sit at −2°, notes tilt between +1° and +2° or −1° and −2°, pushpins sit at slightly different heights, and handwriting never typesets. But the imperfection is a fixed vocabulary, not randomness — rotation stays inside ±2°, the note palette has exactly five colors, the column structure is a disciplined grid underneath the wobble. This is what separates the system from "messy": the audience reads the energy as human, and the structure as trustworthy. A board where every note is straight and every tape strip is level would read as a fake photo of a real wall; a board where notes rotate 15° randomly would read as a mess.

The palette splits into three roles. **The wall** — cork (`{colors.cork}`) as the default surface, whiteboard (`{colors.whiteboard}`) as the clean alternative, with `{colors.cork-deep}` for footers and depth. **The ink** — `{colors.ink}` for handwriting and structure, `{colors.ink-soft}` for secondary notes. **The notes** — five sticky colors that are the system's accent system: yellow is the default voice (the system's `c-accent`), and pink, green, blue, and orange carry category meaning (blockers, done-adjacent, people, metrics — assign once per deck and stay consistent). The tape token (`{colors.tape}`) is the only translucent color in the palette — white at 35% opacity — and it never carries text at full contrast.

Typography is **handwriting first, everywhere**. **Caveat** (weights 600–700) carries display, headings, note titles, and labels — its bouncy, marker-drawn energy is the voice of someone writing on a wall. **Patrick Hand** (weight 400) carries note bodies, leads, and captions — it is the legible "note text" face, less stylized than Caveat, closer to how a real hand writes a card. There is no serif, no mono, no sans in the system; a sans-serif slide would immediately read as a different product. The CJK pairing — Ma Shan Zheng for display, Noto Sans SC for body — preserves the handwriting contract across scripts (see the CJK section).

**Density philosophy: medium-high, but breathing.** A kanban wall is naturally dense — four columns, each with three to six notes. The system handles density because notes are small, tilted, and shadowed — the eye groups them as a cluster, not a wall of text. The discipline: every note carries a short Caveat title plus at most three lines of Patrick Hand body; a note that needs more than that is a card that should have been split. Empty wall space is not a flaw — a wall with one column of notes and a big "today" arrow reads as a team's focus, which is a story worth telling.

**Key Characteristics:**
- Cork background (`{colors.cork}`) with a repeating radial-dot texture (`{components.cork-dot-texture}`) as the default surface; whiteboard dot-grid (`{components.whiteboard-grid}`) is the clean alternative.
- Column headers are washi-tape strips (`{components.tape-header}`): translucent white, ~−2° rotation, small shadow.
- Sticky notes (`{components.sticky-note}`) tilt ±1–2° with soft shadows and a faint gummed top edge (`{components.sticky-fold}`).
- WIP-limit badges (`{components.wip-badge}`) — small ink circles with Caveat-700 numerals.
- Handwritten typography: Caveat 600–700 for headings and titles, Patrick Hand 400 for notes and body.
- Arrow connectors (`{components.arrow-connector}`) between columns show flow; completed notes fade (`{components.done-note}`).
- Pushpins (`{components.pushpin}`), tape, and slight rotations make every slide feel physically assembled.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.cork}` | #C9996B | Default wall surface. Warm cork tan; the base for the default scheme. |
| `{colors.cork-deep}` | #A87C4E | Deeper cork for footers, page strips, and depth accents on the cork wall. |
| `{colors.whiteboard}` | #F7F7F5 | Whiteboard surface — the clean alternative for planning slides. Also the light text color inside ink badges. |
| `{colors.sticky-yellow}` | #FFD166 | Default sticky note (`c-accent`). The system's first voice for any note. |
| `{colors.sticky-pink}` | #F4A7B9 | Note color for blockers, risks, and "attention" content. |
| `{colors.sticky-green}` | #A8D5A2 | Note color for healthy flow, approvals, and done-adjacent content. |
| `{colors.sticky-blue}` | #9EC5FE | Note color for people, ownership, and collaboration content. |
| `{colors.sticky-orange}` | #FFB85C | Note color for metrics, numbers, and standup highlights. |
| `{colors.ink}` | #2A2A28 | Handwriting ink — all text on notes and walls, badge fills, arrows. A warm near-black. |
| `{colors.ink-soft}` | #6E6E66 | Secondary handwriting — captions, source notes, muted card text. |
| `{colors.tape}` | rgba(255,255,255,0.35) | Washi tape — the only translucent token. Never used as a text color; only as a strip surface. |

### Defaults

- **Default surface background**: `{colors.cork}` with the radial-dot texture. The wall is the default; whiteboard is an explicit alternative, never a fallback.
- **Default note color**: `{colors.sticky-yellow}`. Reach for yellow first; assign the other four colors a meaning once per deck and keep it.
- **Default headline color**: `{colors.ink}` (on cork and whiteboard alike).
- **Default body text color**: `{colors.ink}` for primary note text; `{colors.ink-soft}` for captions and secondary notes.
- **Default tape surface**: `{colors.tape}` — text on tape renders in `{colors.ink}` at normal contrast.
- **Default border / divider**: `{colors.ink}` at low opacity (hairlines inside notes at 15%).
- **Default badge**: ink circle with `{colors.whiteboard}` numeral.
- **Default rotation**: −2° for tape headers; ±1–2° for notes (pick per note, never 0° for more than one note in a row, never beyond 2°).

### Semantic Roles

The five sticky colors are **category semantics, not decoration**: yellow is the default voice; pink is attention (blockers, risks); green is healthy flow (approvals, shipped-adjacent); blue is people (owners, collaborators); orange is metrics (numbers, counts). Assign each color one meaning at deck start and use it consistently across slides — a color that means "blocker" on slide two and "metric" on slide five destroys the wall's legibility. Sticky colors are note *backgrounds* only; they are never used for text, borders, or fills of non-note elements. The tape token is the only white-family surface and stays translucent everywhere; a solid white tape strip reads as a sticker, not washi tape.

## Typography

### Font Family

The system loads exactly four faces: **Caveat** (weights 600, 700) for display, headings, note titles, and labels; **Patrick Hand** (weight 400) for note bodies, leads, and captions; **Ma Shan Zheng** (weight 400) as the CJK display fallback; **Noto Sans SC** as the CJK body fallback. There is deliberately no Latin sans, serif, or mono — the handwriting contract is the system's identity.

The emotional register of each face is fixed:
- **Caveat 600–700** — marker energy. Its bouncy baseline and confident strokes say "written on the wall, recently." Used for anything that should feel like a heading.
- **Patrick Hand 400** — legible note hand. More regular than Caveat, closer to a real quick card note; used where the audience must actually read at speed.
- **Ma Shan Zheng 400** — the Chinese display voice. A brush-script handwriting that matches Caveat's energy in register (see CJK section for the trade-off).
- **Noto Sans SC 400/500/700** — the Chinese body voice. Legibility over style for note text.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 9vw | Caveat | 700 | Cover or opening display — big marker headline |
| `{typography.h1}` | 5.5vw | Caveat | 700 | Chapter-opening or section-break headline |
| `{typography.h2}` | 3.6vw | Caveat | 600 | Primary content-slide headline |
| `{typography.stat-value}` | 5.5vw | Caveat | 700 | Big numeral on metric slides |
| `{typography.note-title}` | 2.3vw | Caveat | 600 | Sticky-note title — the wall's per-note headline |
| `{typography.h3}` | 1.9vw | Patrick Hand | 400 | Sub-headline, section labels inside panels |
| `{typography.label}` | 1.2vw | Caveat | 600 | Tape-header text, chrome labels, board names |
| `{typography.lead}` | 1.5vw | Patrick Hand | 400 | Lead paragraph or single supporting block |
| `{typography.wip-num}` | 1.5vw | Caveat | 700 | WIP-limit badge numeral |
| `{typography.body}` | 1.15vw | Patrick Hand | 400 | Body copy, note secondary text |
| `{typography.note-body}` | 1.05vw | Patrick Hand | 400 | Sticky-note body text (≤ 3 lines) |
| `{typography.caption}` | 0.9vw | Patrick Hand | 400 | Source notes, page notes, fine print |

### Defaults

- **Default section headline**: `{typography.h2}` (3.6vw Caveat 600). Reserve `{typography.h1}` for chapter breaks.
- **Default opening / cover display**: `{typography.display}` (9vw Caveat 700).
- **Default note title**: `{typography.note-title}` (2.3vw Caveat 600); **default note body**: `{typography.note-body}` (1.05vw Patrick Hand 400).
- **Default label / tape text**: `{typography.label}` (1.2vw Caveat 600).
- **Default body size**: `{typography.body}` (1.15vw Patrick Hand 400).
- **Default weight for display**: 700; **default weight for body**: 400. Caveat 400 and 500 exist but are not loaded — the system writes with a marker, not a pencil.

When unsure, the canonical moment is a `{typography.note-title}` headline on a yellow `{colors.sticky-yellow}` note with two lines of `{typography.note-body}` underneath. If it needs more presence, scale the note, don't change the face.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every column header is a washi-tape strip** (`{components.tape-header}`): `{colors.tape}` background, ~−2° rotation, small shadow, rounded 2px corners. No column header exists without tape.
- **Every sticky note has a ±1–2° rotation and a soft shadow** (`{components.sticky-note}`). Notes in the same column should alternate tilt direction (one +, next −) so the stack reads as pinned, not stacked.
- **Every column shows a WIP limit** as a small circle (`{components.wip-badge}`) — ink fill, `{colors.whiteboard}` numeral in Caveat 700.
- **The default surface is cork with the repeating radial-dot texture** (`{components.cork-dot-texture}`). The whiteboard dot-grid (`{components.whiteboard-grid}`) is the explicit clean alternative for planning slides.
- **Note typography is always handwritten**: Caveat for titles, Patrick Hand for bodies. Never a sans or serif inside a note.
- **Flow between columns is shown with an arrow connector** (`{components.arrow-connector}`), drawn as an inline SVG at ~55–60% ink opacity.
- **Completed notes fade** (`{components.done-note}`): opacity 0.55, `filter: saturate(0.7)` — the wall keeps its history but lets it recede.
- **Every slide is physically assembled**: tape, pins, slight rotations. A slide with zero rotation and zero tape reads as a different system.

### Typography Principles

The rhythm of Kanban is **Caveat energy + Patrick Hand legibility + physical assembly**. Switching a heading to a sans-serif reads as a different system; setting a note body in Caveat (too stylized for a paragraph) reads as a mistake; straightening every element to 0° reads as a screenshot of a wall rather than a wall. Rotation is a type-level decision: it lives on the *containers* (notes, tape) and never on the *text runs* themselves — a rotated text block inside an already-rotated note compounds to illegibility. Keep one rotation per container.

## Layout

### Canvas System

The source template targets a fluid `100vw × 100vh` viewport with all sizes in `vw`/`vh`; under the Fixed-Stage Policy these translate directly into 1920×1080 stage coordinates. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `reveal-right`, `reveal-left`, `scale-in`) run per slide with stagger delays via `data-delay` attributes; sticky notes have a dedicated `pin-in` entrance (see Responsive Behavior).

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 5vw | Slide horizontal padding — the wall extends toward the edges, tighter than editorial systems |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4vh | Between columns, and between chrome and the board |
| `{spacing.gap-md}` | 2.4vh | Between notes within a column, between a tape header and its first note |
| `{spacing.gap-sm}` | 1.3vh | Between a note title and its body, between a dash and a label |

### Chrome Frame

Most content slides carry a **wall header** and **wall foot**. The header is a `flex space-between` row: a large tape label (`{components.tape-header}`) with the deck/board title in `{typography.label}` on the left, and a smaller handwritten page note ("board 03 / 12") on the right. The foot is a `{colors.cork-deep}` strip (or a thin ink hairline on whiteboard slides) carrying a page note in `{typography.caption}`. Cover, chapter-break, and closing slides suppress chrome entirely.

The **board area** is a horizontal flex of `{components.board-column}` panels. Three to four columns is the canonical arrangement; each column holds a tape header, a WIP badge, a stack of sticky notes, and (optionally) an arrow connector on its right edge. Columns never scroll — the wall shows the state of the work, not a scrollable backlog.

## Depth and Elevation

### Soft Shadows Are the Elevation System

Unlike the flat editorial templates, this system uses **box-shadow deliberately** — but only in two places, with two strengths:

1. **Sticky notes** — `0 6px 14px rgba(0,0,0,0.18)` (`{components.sticky-note}`). Soft, diffuse, slightly warm-feeling; the note sits *on* the wall, not hovering above it. Never a tight hard shadow — that would read as a UI card, not a paper note.
2. **Tape strips and pushpins** — `0 2px 6px rgba(0,0,0,0.12)` for tape, `0 2px 3px rgba(0,0,0,0.3)` for pins (`{components.tape-header}`, `{components.pushpin}`). Small and tight — these elements are close to the surface.

### No Gradients (Almost), Texture Instead

The only sanctioned gradients are the radial-gradient of the pushpin sphere (a highlight sphere, not a blend) and the `{components.sticky-fold}` top edge (a 20% fade to transparent). Depth comes primarily from **texture** — the cork radial-dot pattern and the whiteboard dot-grid — plus the layered shadows above. No glows, no blur, no grain overlays, no gradient washes. The wall must feel physical: light falls on it from one direction, and everything casts a shadow consistent with that direction.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 2px | Tape strips — a barely-soft edge, as if cut by scissors |
| 3px | Sticky notes — the tiny corner rounding of real paper notes |
| 6px | Board columns — a soft zone on the wall, the least "paper" shape |
| 50% (circle) | WIP badges and pushpins |
| 999px (pill) | None — pills read as UI chips, not wall elements |

The system is softly rounded at paper scale and no sharper. Note corners are 3px, not 0px — a 0px note looks cut with a laser, and this wall is cut with hands.

### Border Weights

- **0px** — sticky notes have no border. A bordered note reads as a card from a design tool, not paper on a wall.
- **1px at 15% opacity** — the only hairline, `{colors.ink}` at 15%, used inside notes and panels (`{components.divider-line}`). One straight line per note maximum.
- **No other borders.** Tape strips, columns, and badges are borderless; separation comes from surface contrast and shadow.

### Decorative Element Types

**Washi-tape header** — A translucent white strip (`{components.tape-header}`) at `rgba(255,255,255,0.35)` with `border-radius: 2px`, `transform: rotate(-2deg)`, and a small shadow. Text on tape is `{colors.ink}` in `{typography.label}` (Caveat 600). The strip is the column's identity; two strips never share the same rotation angle.

**Sticky note** — A colored rectangle (`{components.sticky-note}`) at one of the five sticky colors, `border-radius: 3px`, `box-shadow: 0 6px 14px rgba(0,0,0,0.18)`, rotated ±1–2°. Contains a `{typography.note-title}` (Caveat 600) and up to three lines of `{typography.note-body}` (Patrick Hand 400). The top edge carries the `{components.sticky-fold}` gummed hint via `::before` with a `linear-gradient(to bottom, rgba(0,0,0,0.07), transparent 20%)`.

**WIP badge** — A 24px ink circle (`{components.wip-badge}`) with a `{colors.whiteboard}` numeral in Caveat 700 (`{typography.wip-num}`). Sits at the top of the column, above or beside the tape header. The badge is the wall's discipline meter: a column at its limit visibly declares it.

**Cork texture** — The default wall texture (`{components.cork-dot-texture}`): `background-image: radial-gradient(circle, rgba(0,0,0,0.05) 1.5px, transparent 1.5px); background-size: 26px 26px`, layered over `{colors.cork}`. Uniform, faint, never photorealistic — it suggests cork without pretending to be a photograph of it.

**Whiteboard dot-grid** — The clean alternative (`{components.whiteboard-grid}`): `radial-gradient(circle, rgba(42,42,40,0.12) 1px, transparent 1px)` at `22px 22px` over `{colors.whiteboard}`. Used for planning slides, roadmaps, and anything that needs less texture.

**Arrow connector** — An inline SVG (`{components.arrow-connector}`) between columns: a stroked path with a polygon arrowhead at ~55% ink opacity, sized ~2.5vw. One arrow per column pair; the arrow is the wall's statement of flow direction.

**Pushpin** — A 10px sphere (`{components.pushpin}`) at a note's top corner, `background: radial-gradient(circle at 35% 30%, #FFE9D6, #D64541 65%)`, `box-shadow: 0 2px 3px rgba(0,0,0,0.3)`. Pins are decorative extras, one or two per slide, never on every note — a pinned-everything wall looks upholstered.

**Done note** — A faded sticky note (`{components.done-note}`): `opacity: 0.55; filter: saturate(0.7)`. The wall's memory; completed work recedes but stays visible.

**Board column** — A `{colors.cork}`-overlaid lighter zone (`{components.board-column}`) at `rgba(255,255,255,0.12)`, `border-radius: 6px`, holding the column's tape header, WIP badge, notes, and arrow.

## Do's and Don'ts

### Do
- Use the cork wall (`{colors.cork}` + `{components.cork-dot-texture}`) as the default surface; switch to the whiteboard (`{colors.whiteboard}` + `{components.whiteboard-grid}`) only when a slide needs to feel clean and planned.
- Render every column header as a washi-tape strip (`{components.tape-header}`) — translucent, rotated, shadowed.
- Give every sticky note a ±1–2° rotation and the soft 0 6px 14px shadow. Alternate tilt direction within a column.
- Show a WIP limit on every column as a `{components.wip-badge}` circle.
- Write note titles in Caveat 600 and note bodies in Patrick Hand 400 — never a sans or serif inside a note.
- Keep note bodies to three lines maximum. A note that needs more is a card that should be split.
- Use the five sticky colors as category semantics and keep each color's meaning consistent across the deck.
- Fade completed notes (`{components.done-note}`) — the wall keeps its history but lets it recede.
- Connect columns with arrow connectors; let the wall tell the flow story.
- Add one or two pushpins per slide for physicality — never pin everything.

### Don't
- Don't make everything straight. A wall with zero rotation reads as a screenshot; every tape strip and note should tilt slightly (within ±2°).
- Don't rotate text runs independently of their container — one rotation per container, or the note becomes illegible.
- Don't use sticky colors for text, borders, or non-note fills. They are note backgrounds only.
- Don't use a sans, serif, or mono typeface anywhere. Handwriting is the contract.
- Don't put a border on a sticky note; paper notes on a wall don't have outlines.
- Don't use hard, tight shadows (e.g. 0 2px 4px) on notes — that's UI-card lighting, not wall lighting.
- Don't exceed 5 note colors in a deck, and don't let one color mean two things.
- Don't use the tape color for text; tape is a surface, and text on tape is ink.
- Don't build a scrollable backlog column. The wall shows the state of the work, not a list to scroll.
- Don't use pills, sharp 0px corners on notes, or photorealistic cork textures. The wall is suggested, not photographed.

## Responsive Behavior

The source template is viewport-fluid by design; under the Fixed-Stage Policy those `vw`/`vh` proportions become fixed 1920×1080 stage coordinates, and the stage scales as one unit. Do not add breakpoints or reflow content for mobile — letterbox or pillarbox instead.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (fade-up, fade-in, reveal-right, reveal-left, scale-in) with stagger delays via `data-delay="N"` where N maps to a discrete delay step (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Sticky notes use a dedicated `pin-in` entrance: `transform: scale(0.85) rotate(0deg)` → final rotation, with opacity 0 → 1 over ~0.35s — the note lands on the wall. Apply it to notes within a column with a left-to-right stagger (0.08s per note).
- Tape headers fade up (fade-up) rather than pin-in — tape is applied, not thrown.
- Elements with `[data-anim]` start invisible (opacity:0) and animate on `.is-active` — re-visiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. Note that `filter: saturate(0.7)` on done notes and the translucent tape may flatten in some print pipelines — verify the printed wall still distinguishes done from active.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Caveat 700) | Caveat | Ma Shan Zheng (马善政) | 400 (only weight; see Aesthetic Notes) |
| Note title (Caveat 600) | Caveat | Ma Shan Zheng (马善政) | 400 |
| Body / notes (Patrick Hand 400) | Patrick Hand | Noto Sans SC (思源黑体) | 400 |
| Label / tape text (Caveat 600) | Caveat | Ma Shan Zheng (马善政) | 400 |
| Caption / fine print (Patrick Hand 400) | Patrick Hand | Noto Sans SC (思源黑体) | 400 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Caveat, Ma Shan Zheng, cursive"` (display) or `"Patrick Hand, Noto Sans SC, cursive"` (body). Latin glyphs render in Caveat / Patrick Hand; CJK glyphs fall through to Ma Shan Zheng / Noto Sans SC automatically. No per-language class needed. Mixed lines like `本周目标：ship the onboarding flow` render in one run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Caveat:wght@600;700&family=Patrick+Hand&family=Ma+Shan+Zheng&family=Noto+Sans+SC:wght@400;500;700&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.7–1.8, display 1.2–1.3
- Letter-spacing: 0 on CJK
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `使用 AI` not `使用AI`)
- One font per sentence

### Aesthetic Notes for This System

Kanban's Latin voice is **Caveat** — a marker-drawn script with a bouncy baseline and energetic strokes. The natural Chinese pairing is **Ma Shan Zheng**, a brush-script handwriting. Two honest caveats: Ma Shan Zheng is a *brush* face (calligraphic, with stroke-width variation) while Caveat is a *marker* face (uniform strokes), so the energy matches but the material differs — Chinese display headlines will read slightly more calligraphic, which is acceptable and even warm. And Ma Shan Zheng has only weight 400; it cannot deliver Caveat 700's bold presence. For a heavier Chinese display, set the Ma Shan Zheng text with `font-weight: 700` on a Noto Sans SC fallback *or* accept the single weight and compensate with size (Ma Shan Zheng at 5vw reads bolder than its weight suggests because of its brush contrast).

Chinese **note bodies** are the system's translation heart. Patrick Hand was tuned for Latin's narrow glyphs; Chinese characters are square and roughly double the width per character. Keep Chinese note bodies to **two lines maximum** (the three-line Latin budget becomes two in Chinese), and keep note titles to **2–6 characters**. The sticky-note discipline — short title, short body — is exactly right for Chinese; a Chinese note that needs a paragraph is a card that should be split.

Caveat and Patrick Hand have no CJK glyphs, and their bouncy baselines do not survive mixed-script lines at small sizes. **Keep notes single-script:** a note is either Chinese or Latin, never a long mixed run. Chrome labels in Chinese (tape text) render in Ma Shan Zheng at `{typography.label}` size; there is no uppercase and no tracking — the "tape" voice comes from the strip itself, not the letters. The `{components.wip-badge}` numeral stays Arabic (Caveat 700) even on Chinese walls — "3" in a circle is a universal reading.

### Known CJK Gap

The ±1–2° rotation and short-label discipline were tuned for Latin. Chinese characters are square and dense, so rotated Chinese text is significantly harder to read than rotated Latin — keep Chinese notes at gentler tilts (≤1.5°) and never rotate a Chinese tape header beyond −2°. Because Ma Shan Zheng lacks a bold weight, Chinese display headlines cannot match Caveat 700's visual mass without scaling up; verify rendered screenshots for overflow when a Chinese display wraps. And the two-line Chinese note budget means a wall that was five notes deep in Latin may need six or seven notes in Chinese — plan column heights accordingly.

## Iteration Guide

1. Any new slide background is `{colors.cork}` with the radial-dot texture (`{components.cork-dot-texture}`), or explicitly `{colors.whiteboard}` with the dot-grid for clean planning slides. Never introduce a third surface.
2. Any new column has a tape header (`{components.tape-header}`) at ~−2° rotation, a WIP badge (`{components.wip-badge}`), and notes in a stack with alternating ±1–2° tilts.
3. Any new sticky note uses one of the five sticky colors, `border-radius: 3px`, the soft `0 6px 14px rgba(0,0,0,0.18)` shadow, a Caveat 600 title, and ≤3 lines of Patrick Hand 400 body.
4. Any new category of note picks one sticky color and keeps it consistent deck-wide. Yellow is the default; don't invent a sixth color.
5. Any new headline uses Caveat 700 (display/h1) or 600 (h2), mixed case, never uppercase, never a sans face.
6. Any new chrome label (tape text, board names) uses Caveat 600 in `{typography.label}` size on a tape strip.
7. Any new connector between columns is an inline SVG arrow at ~55–60% ink opacity. Don't draw arrows with Unicode glyphs at body size.
8. Any new "done" moment fades its note (`{components.done-note}`): opacity 0.55, saturate 0.7. Don't delete finished work from the wall.
9. If a slide needs to explain the wall, add a tape-labeled annotation or a pushpinned callout note — don't add a prose column.
10. Rotations live on containers, not text runs; verify each note stays legible at its tilt before shipping.

## Known Gaps

- `{colors.tape}` is an rgba token — over a non-standard surface it changes apparent lightness. If a slide deviates from cork/whiteboard, recheck tape legibility; the token is tuned for those two surfaces only.
- `filter: saturate(0.7)` on done notes requires a modern browser and may flatten in print pipelines; the fade is visual, not structural — a done note is identified by its position in the final column too.
- Rotation via `transform` on flex children can clip inside overflow-hidden parents; verify columns use visible overflow or the tilts get cut off at panel edges.
- Patrick Hand and Ma Shan Zheng each have a single weight — the system cannot express bold emphasis in those faces. Emphasis is done with size (Caveat title), color (note color), or the WIP badge, never font-weight.
- The cork dot pattern at 26px spacing was tuned for 1920×1080; if the stage scales to an unusual aspect, the dot density changes with it (acceptable, since the pattern is decorative).
- Handwriting faces render inconsistently across platforms until the web fonts load; the deck should gate slide reveal on `document.fonts.ready` to avoid a flash of fallback cursive.
- The board-column stack assumes notes stay uniform in height; a single tall note (3-line body + long title) can create a visual hole in the column rhythm — keep note sizes within the budget above.
