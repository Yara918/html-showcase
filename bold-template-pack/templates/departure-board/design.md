---
version: alpha
name: Departure Board (Split-Flap)
description: A mechanical split-flap display system in the airport-board tradition: a black board, amber characters on black flaps, and tabular departure rows that read like live operational equipment. Every character sits in its own flap cell with a top-and-bottom flap-line divider, a blinking STATUS column animates between NOW and BOARDING states, a live HH:MM:SS clock runs in the top bar, and 1px flap-line rules separate the rows. The register is utilitarian, kinetic, alert, and precise — built for project dispatch boards, operations command screens, launch countdowns, and any live-status wall.

colors:
  board-black: "#0A0A0A"
  panel-charcoal: "#151515"
  flap-dark: "#232323"
  flap-line: "#3A3A3A"
  amber: "#FF9F1C"
  white: "#F5F5F0"
  dim: "#8A8A85"
  alert-red: "#FF4B3E"

color-aliases:
  c-bg: board-black
  c-bg-light: panel-charcoal
  c-bg-cream: flap-dark
  c-fg: white
  c-fg-light: white
  c-fg-2: amber
  c-fg-3: dim
  c-accent: amber
  c-border: flap-line
  c-border-light: flap-line

typography:
  display:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.5vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: 0.02em
  h1:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3vw
    fontWeight: 700
    lineHeight: 1.1
  h2:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 2vw
    fontWeight: 600
    lineHeight: 1.2
  h3:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.6vw
    fontWeight: 600
    lineHeight: 1.25
  row:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.5vw
    fontWeight: 600
    lineHeight: 1.9
    letterSpacing: 0.04em
  row-large:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 2.4vw
    fontWeight: 700
    lineHeight: 1.6
    letterSpacing: 0.04em
  label:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.8vw
    fontWeight: 600
    letterSpacing: 0.12em
    textTransform: uppercase
  caption:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.75vw
    fontWeight: 400
    lineHeight: 1.5
  clock:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 2.2vw
    fontWeight: 600
    lineHeight: 1.0
    letterSpacing: 0.08em
  lead:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.2vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1vw
    fontWeight: 400
    lineHeight: 1.7

spacing:
  pad-x: 5vw
  pad-y: 4vh
  gap-lg: 4vh
  gap-md: 2vh
  gap-sm: 1vh

canvas:
  width: 100vw
  height: 100vh

components:
  board-frame:
    background: "{colors.panel-charcoal}"
    border: "1px solid {colors.flap-line}"
    borderRadius: 12px
    padding: "{spacing.gap-md} {spacing.gap-md} {spacing.gap-lg} {spacing.gap-md}"
    boxShadow: "0 0 0 6px {colors.board-black}, inset 0 0 40px rgba(0,0,0,0.6)"
    description: "The board's physical frame: a charcoal panel with a 1px flap-line border, a 12px radius, an outer black bezel (0 0 0 6px), and a deep inner shadow that makes the board read as a lit appliance."
  header-band:
    display: flex
    justifyContent: space-between
    alignItems: baseline
    borderBottom: "1px solid {colors.flap-line}"
    paddingBottom: "{spacing.gap-sm}"
    description: "The top band of the board: the board title (Archivo 700) on the left, the live clock and date on the right, separated from the rows by a 1px flap-line rule."
  column-header:
    display: grid
    gridTemplateColumns: "10ch 8ch 1fr 8ch 14ch"
    columnGap: "{spacing.gap-md}"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.12em
    textTransform: uppercase
    color: "{colors.dim}"
    description: "The column header row: TIME / CODE / DESTINATION / GATE / STATUS in Archivo 600 small caps, dim — the equipment's own labeling."
  row:
    display: grid
    gridTemplateColumns: "10ch 8ch 1fr 8ch 14ch"
    columnGap: "{spacing.gap-md}"
    borderTop: "1px solid {colors.flap-line}"
    padding: "{spacing.gap-sm} 0"
    description: "A departure row: five grid columns holding flap-cell runs. Rows separate by 1px flap-line rules; row content is amber on flap-dark."
  flap-cell:
    display: inline-grid
    placeItems: center
    minWidth: "1.2em"
    height: "1.5em"
    background: "{colors.flap-dark}"
    color: "{colors.amber}"
    fontFamily: "{typography.row.fontFamily}"
    fontSize: "{typography.row.fontSize}"
    fontWeight: 600
    position: relative
    description: "One character in its own flap cell: a dark flap (#232323) with amber type, the top and bottom edges cut by flap-line dividers (see flap-divider). Characters never share a cell."
  flap-divider:
    content: '""'
    position: absolute
    left: 0
    right: 0
    height: 1px
    background: "linear-gradient(90deg, {colors.flap-line}, rgba(58,58,58,0.2) 60%, transparent)"
    description: "The split-flap seam: a 1px flap-line gradient across the top and bottom of every flap cell (::before top, ::after bottom), fading out toward the right so the board reads as lit from the left."
  status-cell:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.14em
    textTransform: uppercase
    color: "{colors.amber}"
    animation: "status-blink 1.2s steps(2, jump-none) infinite"
    description: "The live STATUS cell: amber uppercase state text ('NOW', 'BOARDING') blinking via a steps() CSS animation (opacity 1↔0.25, 1.2s). The only animated cell on the board."
  status-cancelled:
    color: "{colors.alert-red}"
    animation: none
    description: "The CANCELLED / DELAYED state: alert red, steady — red never blinks. Red on this board means stopped, not live."
  clock:
    fontFamily: "{typography.clock.fontFamily}"
    fontSize: "{typography.clock.fontSize}"
    fontWeight: 600
    letterSpacing: 0.08em
    color: "{colors.amber}"
    fontVariantNumeric: "tabular-nums"
    description: "The live HH:MM:SS clock in the header band, amber on black with tabular numerals so the digits never shift width."
  ticker:
    fontFamily: "{typography.caption.fontFamily}"
    fontSize: "{typography.caption.fontSize}"
    color: "{colors.dim}"
    letterSpacing: 0.1em
    textTransform: uppercase
    description: "A dim mono ticker line under the board (e.g., 'NEXT UPDATE 14:32 — ALL SYSTEMS NOMINAL'), carrying operational context without touching the rows."
  alert-line:
    background: "{colors.alert-red}"
    color: "{colors.white}"
    fontWeight: 700
    description: "A full-width alert band variant of the row for critical items — red fill, white mono type, used at most once per board."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Departure Board is a **mechanical split-flap display system** in the airport-board tradition: a black board, amber characters on black flaps, tabular departure rows, and a live clock — the whole slide designed to read as operational equipment rather than a document. Where other templates make arguments, this system runs a status wall: project dispatch boards, operations command screens, launch countdowns, sprint boards, and event schedules. The register is utilitarian, kinetic, alert, and precise — the mechanical voice of a board that has no time for decoration because it has live information to show.

The material premise is the **flap**. Every character on the board sits in its own cell — a dark flap (`{colors.flap-dark}`) holding a single amber glyph — with a top-and-bottom seam cut by a 1px flap-line gradient. The seams are the texture of the system: hundreds of fine horizontal rules across the board are what make a slide read as a mechanical display rather than a table with orange text. Characters never share a cell, so a destination like `SHANGHAI` is a run of eight individual flaps; the row reads as a strip of machine-set type. The flap cells are built with `display: inline-grid; place-items: center` and a fixed `1.5em` height so every character on every row sits on the same optical line.

The rows are **tabular equipment**. Each departure row is a five-column grid — TIME / CODE / DESTINATION / GATE / STATUS — with fixed column widths in `ch` units (`10ch 8ch 1fr 8ch 14ch`) so every row aligns perfectly, the way a real board's mechanically fixed column positions align. The column header band is Archivo 600 small caps in dim; rows are JetBrains Mono 600 at 1.5vw with 0.04em tracking. Row separators are 1px flap-line rules; there is no zebra striping, no row fill, no hover highlight — a live board does not decorate its rows.

Color is **amber on black, with one red exception**. The board reads amber (`{colors.amber}`) on flap-dark and board-black; white (`{colors.white}`) appears only in titles and the alert band's type; dim (`{colors.dim}`) is the metadata voice. Alert red (`{colors.alert-red}`) is reserved for stopped states — CANCELLED and DELAYED — and it never blinks. The blinking status cell (`NOW`, `BOARDING`, `LIVE`) animates via a `steps(2)` CSS animation, flipping between full amber and 25% opacity like a real flap board's mechanical flicker. The system's liveliness budget is exactly one blinking cell per board.

The live clock in the header band (`HH:MM:SS`, tabular numerals) is the system's heartbeat — it makes every deck feel live even when the content is static, and it is the single most reliable way to sell the "operations screen" illusion. Typography is Archivo for the board's labels and JetBrains Mono for the data: the board is equipment, so the data is set in the typeface of equipment — monospaced, tabular, mechanical.

**Key Characteristics:**
- The board frame: charcoal panel, 1px flap-line border, 12px radius, outer black bezel, deep inner shadow — a lit appliance.
- Every character sits in its own flap cell with top/bottom flap-line seams (`{components.flap-divider}`).
- Tabular rows in five fixed columns (TIME / CODE / DESTINATION / GATE / STATUS) with a dim Archivo small-cap header band.
- A blinking STATUS cell (`NOW`, `BOARDING`) via a steps() CSS animation; alert red never blinks.
- A live HH:MM:SS clock with tabular numerals in the header band.
- Amber on black; white for titles and alert type; dim for metadata; red for stopped states only.
- 1px flap-line row separators; no fills, no zebra, no hover states.
- One blinking cell per board; one alert band at most.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.board-black}` | #0A0A0A | The stage background — the wall the board hangs on |
| `{colors.panel-charcoal}` | #151515 | The board's frame and header area — one step up from the wall |
| `{colors.flap-dark}` | #232323 | Every flap cell — the character's mechanical surface |
| `{colors.flap-line}` | #3A3A3A | Seams, row separators, borders — the board's hardware lines |
| `{colors.amber}` | #FF9F1C | All board data — the display color, the system's accent |
| `{colors.white}` | #F5F5F0 | Board titles, alert-band type, high-emphasis labels |
| `{colors.dim}` | #8A8A85 | Column headers, ticker lines, metadata — the quiet voice |
| `{colors.alert-red}` | #FF4B3E | CANCELLED / DELAYED states and the alert band — stopped, never blinking |

### Defaults

- **Default stage background**: `{colors.board-black}`. The wall is always black.
- **Default board surface**: `{colors.panel-charcoal}` with a 1px `{colors.flap-line}` border and the inner shadow.
- **Default flap cell**: `{colors.flap-dark}` background, `{colors.amber}` type, 1px flap-line seams top and bottom.
- **Default row text**: `{colors.amber}` at `{typography.row}` (JetBrains Mono 600).
- **Default header text**: `{colors.dim}` at `{typography.label}` (Archivo 600 small caps).
- **Default title text**: `{colors.white}` at `{typography.display}` (Archivo 700).
- **Default clock**: `{colors.amber}` with tabular numerals.
- **Default status states**: NOW / BOARDING / LIVE blink amber; CANCELLED / DELAYED are steady `{colors.alert-red}`.
- **Default separator**: 1px `{colors.flap-line}` — rows, header underline, frame border.

There is no semantic color beyond red-for-stopped. Green does not exist (a real board has no green); success states are expressed as `BOARDING` or `LIVE` in blinking amber, never as a color change.

## Typography

### Font Family

The system loads four faces: **Archivo** (weights 600, 700) carries board titles, section headlines, and all column labels in small caps; **JetBrains Mono** (weights 400, 600, 700) carries every row, clock, ticker, and data string; **Noto Sans SC** is the CJK fallback for both.

The emotional register is deliberate:

- Archivo reads as **signage** — the same squared grotesque confidence as airport wayfinding, condensed into board titles and labels.
- JetBrains Mono reads as **equipment** — monospaced, mechanical, and unambiguous. On a real split-flap board every character occupies the same width because the flaps are the same width; monospace is the typographic translation of that physical constraint.
- The pairing is strict: labels in Archivo small caps, data in JetBrains Mono. A row set in Archivo reads as a poster, not a board.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 4.5vw | Archivo | 700 | Board title in the header band |
| `{typography.row-large}` | 2.4vw | JetBrains Mono | 700 | Hero row — the single headline item on a board |
| `{typography.clock}` | 2.2vw | JetBrains Mono | 600 | The live HH:MM:SS clock |
| `{typography.h1}` | 3vw | Archivo | 700 | Section-break headline on a board slide |
| `{typography.row}` | 1.5vw | JetBrains Mono | 600 | Standard departure row characters |
| `{typography.h2}` | 2vw | Archivo | 600 | Panel headline |
| `{typography.h3}` | 1.6vw | Archivo | 600 | Sub-headline, group label |
| `{typography.lead}` | 1.2vw | JetBrains Mono | 400 | Operational note under the board |
| `{typography.body}` | 1vw | JetBrains Mono | 400 | Rare body text |
| `{typography.label}` | 0.8vw | Archivo | 600 | Column headers, section labels — small caps, 0.12em |
| `{typography.caption}` | 0.75vw | JetBrains Mono | 400 | Ticker lines, source stamps |

### Defaults

- **Default board title**: `{typography.display}` (4.5vw Archivo 700) in white.
- **Default row data**: `{typography.row}` (1.5vw JetBrains Mono 600, 0.04em tracking) in amber on flap cells.
- **Default clock**: `{typography.clock}` (2.2vw JetBrains Mono 600) in amber, tabular.
- **Default column header**: `{typography.label}` (0.8vw Archivo 600 small caps) in dim.
- **Default ticker**: `{typography.caption}` (0.75vw JetBrains Mono 400) in dim.

When unsure, the canonical board is: header band (title + clock), column header row, 6–10 departure rows, one dim ticker line. Rows dominate; everything else is equipment.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every character on a row sits in its own flap cell** (`{components.flap-cell}`) with the top/bottom flap-line seams. Row text is never set as a plain string on the board surface.
- **Rows are tabular grids** with the fixed five-column template (`10ch 8ch 1fr 8ch 14ch`) and 1px flap-line separators. No fills, no zebra, no hover.
- **The STATUS cell is the only animated cell** — `animation: status-blink 1.2s steps(2, jump-none) infinite` flipping opacity 1 ↔ 0.25. One blinking cell per board.
- **Alert red never blinks.** CANCELLED / DELAYED are steady red; blinking red does not exist.
- **The clock uses `font-variant-numeric: tabular-nums`** so digits never shift width.
- **All data strings are JetBrains Mono with 0.04em tracking**; all labels are Archivo 600 small caps with 0.12em tracking.
- **The board frame is always present**: `{components.board-frame}` with its bezel and inner shadow. Board content never floats on the raw black wall.

### Typography Principles

The rhythm of Departure Board is **Archivo signage + JetBrains Mono equipment**. Setting a row in Archivo reads as a different system. Setting a column header in mono reads as a different system. The 0.04em row tracking is mechanical, not editorial — it spaces characters the way a flap board spaces flaps. Monospace is non-negotiable for data because it reproduces the physical constraint of equal-width flaps; tabular numerals on the clock extend that same logic to the time display. Italics do not exist; weight contrast lives between the mono 600 rows and the mono 700 hero row, and between Archivo 700 titles and Archivo 600 labels.

## Layout

### Canvas System

The system targets the fixed 1920×1080 stage model described in the Fixed-Stage Policy above, expressed in the source as fluid `100vw × 100vh` proportions with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.5s with a sharp mechanical ease — the board flips like a flap, quickly and without grace.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 5vw | Slide horizontal padding — the wall margin around the board |
| `{spacing.pad-y}` | 4vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4vh | Between board and ticker, between sections |
| `{spacing.gap-md}` | 2vh | Inside the board: between header band and rows, between groups |
| `{spacing.gap-sm}` | 1vh | Between tightly related elements; row padding |

The board itself occupies most of the stage: `{spacing.pad-x}` wall margins, the frame at `{spacing.gap-md}` padding, the header band at the top, then the column header row and 6–10 departure rows at `{spacing.gap-sm}` vertical rhythm. Column widths are `ch`-based so the grid is driven by character width, not by percentages — this is what makes the tabular alignment hold across any destination length.

### Chrome Frame

The board **is** the chrome. There is no slide header or footer outside the board; the header band inside the frame holds the title (left) and the live clock plus date (right), and the dim ticker line sits below the frame. Title slides may show a single hero row (`{typography.row-large}`) instead of a full table, with the board title promoted to the header band and the clock still running.

## Depth and Elevation

### The Board as an Appliance

Depth comes from **one object with real materiality**, not from layered surfaces. The `{components.board-frame}` does all the work: a charcoal panel lifted off the black wall by a 1px flap-line border and a 6px black bezel (`box-shadow: 0 0 0 6px board-black`), with a deep inset shadow (`inset 0 0 40px rgba(0,0,0,0.6)`) that darkens the board's edges like a lit display recessed into a housing. The board reads as a physical object on a wall; nothing else on the slide is elevated.

### Flap Texture as Depth

The flap seams are a texture of depth: every cell's top and bottom 1px flap-line gradient (fading toward the right, suggesting light from the left) creates hundreds of fine horizontal rules that separate the character plane from the flap surface. The board's apparent "rows of flaps" depth is entirely this seam texture — no 3D, no perspective, no shadows per cell.

### No Other Elevation

There are no cards on the wall, no floating elements, no drop shadows on rows, no hover lifts. Content is either inside the board or on the wall — nothing hovers.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 12px | The board frame only |
| 0px | Everything else — flap cells, rows, header band, ticker |
| 999px (pill) | None — a real board has no pills |

The single 12px frame radius is the only soft edge; it mirrors the slight rounding of a physical display housing. All internal geometry is square.

### Border Weights

- **1px solid `{colors.flap-line}`** — the frame border, the header underline, row separators, and every flap seam.
- **6px solid `{colors.board-black}`** — the bezel ring via `box-shadow: 0 0 0 6px`, not a real border, so it never consumes layout space.
- No heavier borders, no dashed lines, no colored borders except the flap-line's gradient fade.

### Decorative Element Types

**Board frame** — `{components.board-frame}`: the charcoal housing with the bezel and inner shadow. The system's one object.

**Header band** — `{components.header-band}`: title (left) + clock and date (right), underlined by a 1px flap-line rule.

**Column header row** — `{components.column-header}`: TIME / CODE / DESTINATION / GATE / STATUS in dim Archivo small caps, matching the row grid exactly.

**Departure row** — `{components.row}`: five-column grid, 1px flap-line top rule, `{spacing.gap-sm}` vertical padding. Each cell in the TIME, CODE, DESTINATION, and GATE columns is a run of flap cells.

**Flap cell** — `{components.flap-cell}`: `display: inline-grid; place-items: center; min-width: 1.2em; height: 1.5em`, flap-dark fill, amber glyph, with the `::before`/`::after` flap seams (`{components.flap-divider}`, a 1px flap-line gradient fading right).

**Status cell** — `{components.status-cell}`: amber uppercase state text with the steps() blink animation; `{components.status-cancelled}` is the steady red variant.

**Live clock** — `{components.clock}`: 2.2vw amber mono, tabular numerals, driven by a JS interval in the generated deck (the source ships the CSS; the ticking is wired at generation).

**Ticker** — `{components.ticker}`: a dim mono uppercase line under the board carrying operational context ('NEXT UPDATE 14:32 — ALL SYSTEMS NOMINAL').

**Alert band** — `{components.alert-line}`: a full-width red row with white bold mono type for critical items; used at most once per board.

## Do's and Don'ts

### Do
- Put every board inside the `{components.board-frame}` — bezel, 12px radius, inner shadow. Board content never floats on the raw wall.
- Set every row character in its own flap cell with top/bottom flap-line seams.
- Use the fixed five-column row grid (`10ch 8ch 1fr 8ch 14ch`) for both rows and the column header.
- Keep one blinking STATUS cell per board; blink amber, `steps(2)`, 1.2s.
- Run the live HH:MM:SS clock with tabular numerals in the header band.
- Set data in JetBrains Mono with 0.04em tracking; set labels in Archivo small caps with 0.12em tracking.
- Separate rows with 1px flap-line rules; never fill, stripe, or hover rows.
- Use alert red for stopped states only — steady, never blinking.
- Keep the dim ticker line under the board.

### Don't
- Don't set row text as plain strings without flap cells — the seams are the system's texture.
- Don't blink red, and don't blink more than one cell per board.
- Don't use green, blue, or any color outside the eight-token palette.
- Don't fill rows, zebra-stripe, or add hover states — a live board has no interaction styling.
- Don't put content outside the board unless it is the ticker or a headline above the frame.
- Don't use proportional fonts for data rows or the clock. Mono is mechanical.
- Don't round anything except the 12px frame radius.
- Don't add cards, charts, icons, or progress bars inside the board — the board shows rows and nothing else.
- Don't use italics or underlines; the board's typography is flat and mechanical.
- Don't let a row wrap — long destinations are truncated or abbreviated; the grid columns are fixed.

## Responsive Behavior

The source template is viewport-fluid by design (all sizes in `vw`/`vh`), but per the Fixed-Stage Policy the `html-showcase` output is a fixed 1920×1080 stage scaled uniformly to the viewport — no reflow, no breakpoints, letterboxing or pillarboxing only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions at 0.5s with a sharp `cubic-bezier(0.2, 0.8, 0.2, 1)` ease — mechanical, like a flap.
- Entrance animations are two: `flap-down` (the row's cells flip in via a 0.25s translateY/opacity with staggered `data-delay`) and `fade-in` (0.3s) for the clock and ticker. Rows animate in sequence, top to bottom, like a board updating.
- The status blink and the clock run continuously; entrance animations run per slide via `data-anim` on `.is-active`.
- The clock should pause when the deck is idle-hidden if the presenter environment throttles background tabs (see Known Gaps).

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export captures only the active slide; multi-slide export requires manual navigation per slide. The clock renders as the time of export (static), and the blinking status cell should be pinned to its visible state in print CSS if the generated deck adds one.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Board title / headlines (Archivo 700) | Archivo | Noto Sans SC (思源黑体) | 700 |
| Labels / column headers (Archivo 600) | Archivo | Noto Sans SC (思源黑体) | 600 |
| Row data (JetBrains Mono 600–700) | JetBrains Mono | Noto Sans SC | 600 (rows), 700 (hero rows) |
| Clock / ticker / caption (JetBrains Mono 400–600) | JetBrains Mono | Noto Sans SC | 500–600 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"JetBrains Mono, Noto Sans SC, monospace"` (or the Archivo equivalent). Latin glyphs render in the Latin face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed rows like `上海 SHA 14:32` render in one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo:wght@600;700&family=JetBrains+Mono:wght@400;600;700&family=Noto+Sans+SC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK (the 0.04em row tracking does not transfer)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `上海 SHA 14:32` not `上海SHA14:32`)
- One font per sentence

### Aesthetic Notes for This System

Departure Board's defining trait is **amber JetBrains Mono on flap-dark cells**. Noto Sans SC is the CJK fallback, and because Chinese characters are square, they occupy a full flap cell with no optical adjustment needed — a Chinese destination is naturally a run of square cells, which is exactly how a real split-flap board renders CJK. Set Chinese row data in Noto Sans SC 600 (700 for hero rows); do not try to force monospace metrics on CJK, which Noto Sans SC cannot deliver.

The small-cap Archivo labels do not transfer to CJK — Chinese has no case. **Set Chinese column headers in Noto Sans SC 600, mixed case, letter-spacing 0.** The signage register is carried by the dim color, the size, and the header-band position, not by the typeface's caps. Pure-Latin column headers (`TIME`, `GATE`) stay Archivo small caps as designed.

The blink animation applies unchanged to Chinese status text (`现在`, `登机中`) — the CSS animation is script-agnostic. Alert red on Chinese text reads the same as on Latin; the color discipline (red = stopped, never blinking) carries across scripts.

### Known CJK Gap

Chinese glyphs are square and wider than Latin; a flap cell set to `min-width: 1.2em` fits a Chinese character at the same size, but the fixed `ch`-based row grid (TIME `10ch`, CODE `8ch`, etc.) was tuned for Latin strings. Chinese destination rows are fine (the DESTINATION column is `1fr`), but a Chinese label in a fixed `ch` column (e.g., a Chinese status in the `14ch` STATUS column) may overflow. Shorten Chinese status strings to two characters (`现在`, `登机`) or widen the STATUS column to `16ch` when the deck is Chinese. The 1.5em flap-cell height should step to 1.6em for CJK so square glyphs don't clip the seams.

## Iteration Guide

1. Any new board slide opens with the frame (`{components.board-frame}`) on the black wall.
2. Any new header band holds the title (white Archivo 700) and the live clock + date (amber mono) under a 1px flap-line rule.
3. Any new column header row uses `{components.column-header}` — dim Archivo small caps in the five-column grid.
4. Any new departure row uses `{components.row}` with the fixed five-column template and 1px flap-line top rules; every character goes in its own `{components.flap-cell}`.
5. Any new status uses `{components.status-cell}` (blinking amber) or `{components.status-cancelled}` (steady red) — never blinking red, never a second blink.
6. Any new clock uses `{typography.clock}` with tabular numerals; wire the ticking JS at generation.
7. Any new ticker line is dim mono uppercase under the frame.
8. Any new alert uses `{components.alert-line}` — at most one per board.
9. Keep data in JetBrains Mono 0.04em, labels in Archivo 0.12em small caps, and colors inside the eight-token palette.
10. Verify rows do not wrap and the board shows 6–10 rows of live-looking data.
11. When in doubt, add a row, not a widget: the board's power is the table itself.

## Known Gaps

- The source ships the flap, row, and blink CSS, but the **live clock and the status updates require generation-time JS** (an interval writing `HH:MM:SS` and cycling status text). The generated deck must wire this; a static deck shows the clock frozen at export time.
- The `steps(2, jump-none)` blink animation and the `-webkit-backdrop-filter`-free flap gradients are straightforward CSS, but the flap-cell seams depend on `::before`/`::after` — cells built as plain text without pseudo-elements lose the seams entirely.
- The `ch`-based column grid is tuned for Latin; long destinations must be truncated or abbreviated by the generator (real boards truncate; there is no auto-shrink).
- The status vocabulary is open-ended (NOW, BOARDING, LIVE, CANCELLED, DELAYED); there is no enforced state list, so a generator could invent a state outside the amber-blink / red-steady contract.
- The board shows rows only; there is no component for KPIs, charts, or timelines inside the board — a deck needing those must place them outside the frame, which weakens the appliance illusion.
- The 6px bezel is a `box-shadow`, so print and PDF export render it as a soft ring rather than a crisp housing edge.
- The source template is named "Departure Board (Split-Flap)" in the library; any historical names in source comments refer to the same system.
- Background-tab throttling can freeze the clock's JS interval in some browsers; the generated deck should use a `setInterval` with a drift-compensating timestamp (or accept up to a one-second stall) and note it in delivery docs.
