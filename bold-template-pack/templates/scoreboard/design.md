---
version: alpha
name: Scoreboard (LED Arena)
description: A stadium scoreboard rendered as a design system — a black arena panel, seven-segment-style LED numerals, team colors, and big KPI drama. Orbitron at weights 700–900 powers the glowing numeral clusters; JetBrains Mono uppercase handles every readout label. The system frames any us-vs-target story as a live contest: two clusters face off across a blinking VS, a ticker scrolls the status, and an amber line marks the period. It is dark, loud, and built for competition.

colors:
  board-black: "#0C0C0C"
  panel: "#1A1A1A"
  panel-soft: "#141414"
  panel-edge: "#262626"
  led-red: "#FF3B30"
  led-green: "#34C759"
  led-amber: "#FFB800"
  led-white: "#F2F2F0"
  dim: "#555555"

color-aliases:
  c-bg: board-black
  c-bg-light: panel
  c-bg-cream: panel-soft
  c-fg: led-white
  c-fg-light: led-white
  c-fg-2: dim
  c-fg-3: dim
  c-accent: led-red
  c-border: panel-edge
  c-border-light: dim

typography:
  display:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 8.5vw
    fontWeight: 900
    lineHeight: 0.95
    letterSpacing: -0.01em
  h1:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.5vw
    fontWeight: 800
    lineHeight: 1.05
    letterSpacing: 0.01em
  h2:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3vw
    fontWeight: 700
    lineHeight: 1.15
    letterSpacing: 0.02em
  h3:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.7vw
    fontWeight: 600
    lineHeight: 1.3
    letterSpacing: 0.1em
    textTransform: uppercase
  lead:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.3vw
    fontWeight: 500
    lineHeight: 1.6
    letterSpacing: 0.02em
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
    fontSize: 0.75vw
    fontWeight: 600
    letterSpacing: 0.14em
    textTransform: uppercase
  stat-value:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 7.5vw
    fontWeight: 800
    lineHeight: 1.0
    letterSpacing: 0.02em
  stat-value-sm:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3.8vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: 0.03em
  side-name:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.8vw
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: 0.08em
    textTransform: uppercase
  vs-mark:
    fontFamily: "Orbitron, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4vw
    fontWeight: 900
    lineHeight: 1.0
  ticker-text:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1vw
    fontWeight: 500
    lineHeight: 1.4
    letterSpacing: 0.06em
    textTransform: uppercase

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
  led-numeral:
    fontFamily: "{typography.stat-value.fontFamily}"
    color: "{colors.led-white}"
    textShadow: "0 0 12px currentColor, 0 0 32px currentColor"
    description: "Seven-segment-style LED numeral cluster. Glow is driven by currentColor, so red, green, amber, and white variants each glow in their own hue with zero extra CSS."
  score-panel:
    background: "{colors.panel}"
    border: "1px solid {colors.panel-edge}"
    borderRadius: 8px
    boxShadow: "inset 0 1px 0 rgba(255,255,255,0.05)"
    description: "Recessed module on the black stage. A hairline top highlight suggests a glass bezel; the panel reads as lit from within, not lit from above."
  vs-divider:
    color: "{colors.led-white}"
    animation: "blink 1.2s steps(2) infinite"
    description: "Center VS mark or colon between the two clusters. Blinks via @keyframes (50% opacity 0.15) — the arena's heartbeat between the two numbers."
  ticker-band:
    background: "{colors.panel-soft}"
    borderTop: "1px solid {colors.panel-edge}"
    overflow: hidden
    animation: "marquee 18s linear infinite"
    description: "Bottom status strip. The text is duplicated inside a flex run and translated -50% in a @keyframes loop for a seamless scroll."
  period-line:
    width: "100%"
    height: 3px
    background: "{colors.led-amber}"
    boxShadow: "0 0 10px {colors.led-amber}"
    description: "Amber period/warning line — the system's only glowing rule. Marks the current quarter, period, or countdown boundary."
  team-label:
    fontFamily: "{typography.side-name.fontFamily}"
    color: "{colors.led-white}"
    letterSpacing: "{typography.side-name.letterSpacing}"
    textTransform: uppercase
    description: "LED readout naming the side above each cluster — LEFT/RIGHT, TARGET/ACTUAL, or the team names."
  led-dots:
    width: 4px
    height: 4px
    borderRadius: 50%
    background: "{colors.dim}"
    description: "Small dim LED dots used as separators between panel modules — the hardware punctuation of the board."
  ghost-digits:
    content: "888"
    color: "{colors.dim}"
    opacity: 0.18
    fontSize: "{typography.stat-value.fontSize}"
    fontFamily: "{typography.stat-value.fontFamily}"
    description: "Ghost seven-segment '888' behind a live numeral, rendered as a ::before layer, suggesting the segment structure of a real LED display."
  kpi-chip:
    border: "1px solid {colors.panel-edge}"
    borderRadius: 4px
    padding: "0.3em 0.9em"
    color: "{colors.led-white}"
    background: "{colors.panel}"
    description: "Small bordered readout chip for supporting numbers — sub-KPIs, deltas, deltas-to-go — with a label above in {typography.label}."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Scoreboard (LED Arena) is a **contest system**: every slide is a scoreboard moment, and every scoreboard is a story with exactly two sides. The stage is a black arena — `{colors.board-black}` — with recessed panels, glowing numerals, a blinking center mark, and a scrolling ticker. The system's job is to make numbers feel live: KPIs become scores, targets become the away team, and a quarter review becomes a game you can't look away from. It is the loudest system in the library, and it is loud on purpose — it is built for KPI races, sales contests, campaign countdowns, and quarter showdowns, where the entire point of the room is the score.

The central composition is the **two-cluster face-off**. Two panels sit left and right; each carries a side name in LED readout (`{typography.side-name}`) above a giant numeral cluster (`{typography.stat-value}`), and between them a VS mark (`{typography.vs-mark}`) blinks at 1.2s. This is not decoration — it is the system's thesis about how to present comparison: don't put two numbers in a table and ask the audience to compare; put them in an arena and let the audience root. LEFT vs RIGHT, TARGET vs ACTUAL, 预算 vs 实绩 — the frame is always us-vs-target, and the drama is always the gap.

Light is the system's material. The stage is nearly black; everything visible is either a panel edge, a dim resting element, or an LED that glows. The glow is implemented as layered `text-shadow` on `currentColor` (`{components.led-numeral}`: `0 0 12px currentColor, 0 0 32px currentColor`), which means the LED hue and its glow can never disagree — change the color, the light changes with it. Dim elements (`{colors.dim}`) are the system's resting state: captions, dot separators, ghost digits, anything not currently shouting. A scoreboard that has no dim moments is just noise; the dim elements are what make the glowing elements feel like lights.

Typography is a two-voice digital stack. **Orbitron** (weights 700–900) is the numeral and display voice — squared, geometric, built for a screen that reads from across a room. Its wide forms and open counters carry the seven-segment illusion at 7.5vw. **JetBrains Mono** (weights 400–600) is the readout voice — every label, side name, ticker line, and caption is mono uppercase with 0.14em tracking, like a referee's log. There is no serif, no handwriting, no human warmth in the system; warmth is replaced by adrenaline.

**Density philosophy: medium, and everything has a role.** A scoreboard slide typically has the two clusters, a ticker, and one supporting row of chips — nothing more. The system resists the urge to fill the black with numbers; a second row of competing giants would break the face-off. Supporting numbers live in small `{components.kpi-chip}` readouts, deliberately quiet next to the giants. The black space is not emptiness; it is the arena.

**Key Characteristics:**
- Black stage (`{colors.board-black}`) with recessed panels (`{components.score-panel}`) edged in `{colors.panel-edge}`.
- Two giant seven-segment-style LED numeral clusters (LEFT vs RIGHT, or TARGET vs ACTUAL) with `text-shadow: 0 0 12px currentColor` glow (`{components.led-numeral}`).
- Side names in LED readout above each cluster (`{typography.side-name}`).
- A center VS mark (`{typography.vs-mark}`) with a 1.2s steps blink (`{components.vs-divider}`).
- A bottom ticker band with a seamless marquee scroll (`{components.ticker-band}`).
- An amber period/warning line (`{components.period-line}`) — the system's only glowing rule.
- Orbitron 700–900 for numerals and display; JetBrains Mono uppercase for every readout label.
- Dim `{colors.dim}` resting elements — ghost digits, dot separators, captions — give the glow its meaning.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.board-black}` | #0C0C0C | The arena. Default stage background — near-black, never pure black, so panels can sit on it. |
| `{colors.panel}` | #1A1A1A | Recessed panel surface for clusters, chips, and ticker modules. |
| `{colors.panel-soft}` | #141414 | Deeper panel tone for the ticker band and secondary modules — one step darker than panel. |
| `{colors.panel-edge}` | #262626 | Panel borders and hairlines. The system's only structural line color. |
| `{colors.led-red}` | #FF3B30 | The left contestant / the hot side. Default accent (`c-accent`); the system's first LED hue. |
| `{colors.led-green}` | #34C759 | The right contestant / the healthy side. Use for actuals, delivery, on-track numbers. |
| `{colors.led-amber}` | #FFB800 | The warning voice — period lines, countdowns, at-risk numbers, neutral emphasis. |
| `{colors.led-white}` | #F2F2F0 | Default numeral and label color. The quiet LED that still glows. |
| `{colors.dim}` | #555555 | Resting elements — captions, dot separators, ghost digits, anything not currently shouting. |

### Defaults

- **Default stage background**: `{colors.board-black}`. Every slide is the arena; panels (`{colors.panel}`) sit on it, never replace it.
- **Default numeral color**: `{colors.led-white}`. Reached for first; switch to `{colors.led-red}` or `{colors.led-green}` only when the slide's story is a side-by-side contest.
- **Default accent**: `{colors.led-red}` — the left side, the hot side, the side the room is betting on.
- **Default label color**: `{colors.led-white}` for side names and live readouts; `{colors.dim}` for captions and resting chrome.
- **Default border**: `{colors.panel-edge}` (1px). The system never uses a brighter border.
- **Default warning**: `{colors.led-amber}` — period lines and at-risk numbers only.
- **Default glow**: `text-shadow: 0 0 12px currentColor, 0 0 32px currentColor` on every live numeral.
- **Default count of glowing hues per slide**: two — plus white. A slide with red, green, amber, and white all glowing simultaneously stops being a scoreboard and becomes a slot machine.

### Semantic Roles

The LED hues are **data semantics, not decoration**. Red is the hot side (the challenger, the target, the gap that hurts); green is the healthy side (the actual, the delivered, the on-track number); amber is the warning voice (period boundaries, countdowns, at-risk KPIs); white is the neutral voice (labels, default numerals, ticker text). Assign the red/green sides once per deck (LEFT always red, RIGHT always green) and keep the polarity stable across slides — flipping sides mid-deck reads as the scoreboard glitching. Amber never represents a contestant; it represents time and risk. Dim is not a hue — it is the off state of an LED that will light up later.

## Typography

### Font Family

The system loads exactly three families: **Orbitron** (weights 500–900; the system uses 700–900) for numerals, display, and the VS mark; **JetBrains Mono** (weights 400–600) for every readout label, side name, ticker line, and caption; **Noto Sans SC** as the CJK fallback. There is no humanist voice anywhere — the system is built of electronics and referee logs.

The emotional register of each face is fixed:
- **Orbitron 800–900** — the score. Squared, wide, geometric; designed to be read from the back of a room. It carries the seven-segment illusion without actually being a seven-segment font.
- **Orbitron 700** — secondary numerals and display support.
- **JetBrains Mono 600** — readout labels and side names, uppercase, tracked 0.08–0.14em. The referee's log.
- **JetBrains Mono 400–500** — body, lead, ticker, captions. Still mono; the arena speaks in one register of machine text.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 8.5vw | Orbitron | 900 | Cover or opening display — the marquee title |
| `{typography.stat-value}` | 7.5vw | Orbitron | 800 | Giant LED numeral cluster — the score itself |
| `{typography.h1}` | 4.5vw | Orbitron | 800 | Chapter-opening or section-break headline |
| `{typography.vs-mark}` | 4vw | Orbitron | 900 | The center VS mark |
| `{typography.stat-value-sm}` | 3.8vw | Orbitron | 700 | Secondary clusters and big supporting numbers |
| `{typography.h2}` | 3vw | Orbitron | 700 | Primary content-slide headline |
| `{typography.side-name}` | 1.8vw | JetBrains Mono | 600 | LED readout naming each side — uppercase, 0.08em tracking |
| `{typography.h3}` | 1.7vw | JetBrains Mono | 600 | Panel header — uppercase, 0.1em tracking |
| `{typography.lead}` | 1.3vw | JetBrains Mono | 500 | Lead paragraph or single supporting block |
| `{typography.ticker-text}` | 1vw | JetBrains Mono | 500 | Ticker band line — uppercase, 0.06em tracking |
| `{typography.body}` | 1.05vw | JetBrains Mono | 400 | Body copy inside panels |
| `{typography.caption}` | 0.8vw | JetBrains Mono | 400 | Source notes, resting chrome |
| `{typography.label}` | 0.75vw | JetBrains Mono | 600 | Chip labels, kickers — uppercase, 0.14em tracking |

### Defaults

- **Default section headline**: `{typography.h2}` (3vw Orbitron 700). Reserve `{typography.h1}` for chapter breaks.
- **Default opening / cover display**: `{typography.display}` (8.5vw Orbitron 900).
- **Default numeral size**: `{typography.stat-value}` (7.5vw Orbitron 800) for the two cluster giants; `{typography.stat-value-sm}` (3.8vw) for secondary numbers.
- **Default label size**: `{typography.label}` (0.75vw); **default side-name size**: `{typography.side-name}` (1.8vw).
- **Default weight for any display element**: 800 (display and numerals) or 900 (marquee titles). **Default weight for labels and readouts**: 600. **Default weight for body**: 400.
- **Default tracking**: 0.02em on numerals (Orbitron's wide forms need a touch of air), 0.08–0.14em on readout labels, 0.06em on ticker text.

When unsure, the canonical slide is two `{components.score-panel}`s, each with a `{typography.side-name}` readout and a `{typography.stat-value}` numeral, divided by the blinking `{components.vs-divider}`, with the `{components.ticker-band}` across the bottom and one `{components.period-line}` above it.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Two giant seven-segment-style LED numeral clusters** (LEFT vs RIGHT, or TARGET vs ACTUAL) with glow — `text-shadow: 0 0 12px currentColor, 0 0 32px currentColor` (`{components.led-numeral}`). The clusters are the slide's center of gravity; nothing competes with them.
- **Side names as LED text above each cluster** (`{typography.side-name}`) — JetBrains Mono 600, uppercase, 0.08em tracking, `{colors.led-white}`.
- **A center VS mark with a blinking animation** (`{components.vs-divider}`) — 1.2s `steps(2)` blink to 15% opacity. The colon variant blinks on the colon only.
- **A bottom ticker band with scrolling status** (`{components.ticker-band}`) — duplicated text translated −50% in a linear loop, 18s per pass.
- **An amber period/warning line** (`{components.period-line}`) — 3px `{colors.led-amber}` with a 10px glow. One per slide, marking the current period.
- **LEDs glow against the black panel** — every live numeral glows in its own hue via currentColor; dim `{colors.dim}` elements (ghost digits `{components.ghost-digits}`, dot separators `{components.led-dots}`, captions) provide the contrast that makes glow read as light.

### Typography Principles

The rhythm of Scoreboard is **giant Orbitron numerals + mono uppercase readouts + dim resting text**. Setting a numeral in JetBrains Mono reads as a different system (a terminal, not a scoreboard); setting a label in Orbitron reads as a different system; introducing a serif anywhere reads as a different product. Numerals are always Arabic — no spelled-out numbers, ever. Uppercase is the default for every readout; only numeral clusters and the VS mark break the uppercase register. Underline and bold-in-body do not exist; emphasis is light (glow), size (scale), or hue (LED color).

## Layout

### Canvas System

The source template targets a fluid `100vw × 100vh` viewport with all sizes in `vw`/`vh`; under the Fixed-Stage Policy these translate directly into 1920×1080 stage coordinates. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `reveal-right`, `reveal-left`, `scale-in`) run per slide with stagger delays via `data-delay` attributes; numeral clusters have a dedicated `power-on` entrance (see Responsive Behavior).

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding — the arena edge |
| `{spacing.pad-y}` | 5vh | Slide vertical padding — room above the ticker |
| `{spacing.gap-lg}` | 4.5vh | Between the cluster row and the ticker, and between header and stage |
| `{spacing.gap-md}` | 2.5vh | Between a side name and its numeral, between panels |
| `{spacing.gap-sm}` | 1.2vh | Between a chip label and its value, between ticker dots |

### Chrome Frame

Most content slides carry an **arena header** and the **ticker foot**. The header is a `flex space-between` row of two `{typography.label}` readouts (e.g. "ARENA 01 — KPI CONTEST" left, "QUARTER 3" right) separated from the stage by a 1px `{colors.panel-edge}` rule and a `{components.led-dots}` separator row. The foot is the full-width `{components.ticker-band}` — a scrolling status strip that every content slide owns; on cover and closing slides the ticker pauses or is replaced by a static caption. Cover, chapter-break, and closing slides suppress the header but keep the stage black.

The **stage** is the area between header and ticker: two `{components.score-panel}`s face off across the center `{components.vs-divider}`, with the `{components.period-line}` marking the current period above the ticker and a row of `{components.kpi-chip}` readouts below the clusters when supporting numbers are needed.

## Depth and Elevation

### Light Is the Elevation System

There are no drop shadows on the black stage — depth is light. The system's elevation vocabulary is:

1. **LED glow** — layered `text-shadow` on `currentColor` (`{components.led-numeral}`: `0 0 12px currentColor, 0 0 32px currentColor`). The glow is the system's only "shadow," and it points outward: light comes from the numerals.
2. **Recessed panels** — `{components.score-panel}` uses `background: {colors.panel}`, a 1px `{colors.panel-edge}` border, and a hairline `inset 0 1px 0 rgba(255,255,255,0.05)` top highlight. The panel reads as a lit glass module set into the black, not a card floating above it.
3. **Tone steps, not shadows** — separation between stage, panel, and panel-soft comes from lightness steps (#0C0C0C → #1A1A1A → #141414), never from shadows.

### No Atmospheric Gradients

No radial ambient glow behind the stage, no gradient washes, no vignette. The arena is honestly black; every light in the scene belongs to a numeral, a line, or a label. The only sanctioned "gradient-like" effect is the ghost `888` layer (`{components.ghost-digits}`) at 18% opacity, which suggests segment structure without blending anything.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Ghost digits, LED text, numerals — electronics are square |
| 4px | KPI chips — small, machined, slightly eased |
| 8px | Score panels — the module's single soft edge |
| 50% (circle) | LED dot separators (`{components.led-dots}`) |
| 999px (pill) | None — pills read as UI, not hardware |

The system is dominantly square; the 8px panel radius and 4px chip radius are the only easing, and they read as machined bezels, not rounded UI.

### Border Weights

- **1px solid `{colors.panel-edge}`** — the universal structural weight: panel borders, chip borders, header rule, ticker top rule.
- **3px solid `{colors.led-amber}`** — the period line (`{components.period-line}`), the only non-1px line in the system.
- **No other borders.** Brighter or thicker borders would out-shout the panels.

### Decorative Element Types

**LED numeral cluster** — The signature element (`{components.led-numeral}`): Orbitron 800 at `{typography.stat-value}` size, colored `{colors.led-white}` (or red/green), with `text-shadow: 0 0 12px currentColor, 0 0 32px currentColor`. Optionally backed by a ghost `888` layer (`{components.ghost-digits}`) via `::before` at 18% dim opacity.

**Score panel** — The recessed module (`{components.score-panel}`): `{colors.panel}` background, 1px `{colors.panel-edge}` border, 8px radius, `inset 0 1px 0 rgba(255,255,255,0.05)` highlight. Holds the side name and numeral cluster.

**VS divider** — The blinking center mark (`{components.vs-divider}`): Orbitron 900 `{typography.vs-mark}` at 4vw, `@keyframes blink { 0%, 100% { opacity: 1 } 50% { opacity: 0.15 } }`, 1.2s `steps(2)` infinite. A colon variant is used on single-number countdown slides.

**Side name** — The readout above each cluster (`{components.team-label}`): JetBrains Mono 600, uppercase, 0.08em tracking, `{colors.led-white}`.

**Ticker band** — The scrolling foot (`{components.ticker-band}`): `{colors.panel-soft}` background, 1px `{colors.panel-edge}` top border, text in `{typography.ticker-text}`; the text run is duplicated and translated `-50%` in an 18s linear `@keyframes marquee` loop.

**Period line** — The amber boundary (`{components.period-line}`): full-width 3px `{colors.led-amber}` with `box-shadow: 0 0 10px {colors.led-amber}`. Marks quarters, periods, or countdown boundaries; one per slide.

**KPI chip** — A small readout module (`{components.kpi-chip}`): 1px `{colors.panel-edge}` border, 4px radius, `{colors.panel}` background, with a `{typography.label}` caption above the value. Supporting numbers live here — deliberately small next to the giants.

**LED dot separator** — 4px dim circles (`{components.led-dots}`) in a row, used between header items and panel modules. The board's hardware punctuation.

**Ghost digits** — A dim `888` layer (`{components.ghost-digits}`) behind a live numeral, suggesting the seven segments of a real LED display.

## Do's and Don'ts

### Do
- Build every content slide around the two-cluster face-off: two panels, two side names, two giant numerals, one blinking center mark.
- Give every live numeral the layered glow (`text-shadow: 0 0 12px currentColor, 0 0 32px currentColor`) so hue and light never disagree.
- Keep the stage black (`{colors.board-black}`) and let panels, not fills, define regions.
- Use `{colors.led-red}` for the left side and `{colors.led-green}` for the right side, and keep that polarity stable across the deck.
- Use `{colors.led-amber}` for period lines, countdowns, and at-risk numbers — time and risk, never a contestant.
- Set every label, side name, and readout in JetBrains Mono uppercase with 0.08–0.14em tracking.
- Put a scrolling ticker on content slides; it is the board's heartbeat.
- Keep supporting numbers in small `{components.kpi-chip}` readouts so the giants stay giant.
- Use dim `{colors.dim}` elements (captions, dots, ghost digits) as the resting state that makes glow read as light.
- Use Arabic numerals everywhere — never spelled-out numbers.

### Don't
- Don't use more than two glowing contestant hues plus white per slide. Red + green + amber + white simultaneously is a slot machine.
- Don't drop the center mark — the VS (or colon) is what makes it a contest, not a dashboard.
- Don't put text on the numeral scale; the numerals are the only 7.5vw voice.
- Don't use drop shadows on the stage — depth is light (glow) and tone steps, never shadows.
- Don't introduce a serif, handwriting, or non-mono humanist face. The arena speaks Orbitron and JetBrains Mono.
- Don't spell out numbers or use mixed-case labels; uppercase readouts and Arabic numerals are the contract.
- Don't add a third giant element — a second row of clusters breaks the face-off.
- Don't make the ticker static; if there is nothing to scroll, shorten the text or drop the band.
- Don't use amber for a contestant side; amber is time and risk.
- Don't light everything — without dim resting elements the glow has no meaning.

## Responsive Behavior

The source template is viewport-fluid by design; under the Fixed-Stage Policy those `vw`/`vh` proportions become fixed 1920×1080 stage coordinates, and the stage scales as one unit. Do not add breakpoints or reflow content for mobile — letterbox or pillarbox instead.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (fade-up, fade-in, reveal-right, reveal-left, scale-in) with stagger delays via `data-delay="N"` where N maps to a discrete delay step (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Numeral clusters use a dedicated `power-on` entrance: two quick opacity flickers (0 → 0.2 → 0 → 1 over ~0.5s) followed by a glow settle, timed so the cluster "lights up" rather than fades in. Apply it to the two clusters simultaneously — the contest starts together.
- The VS divider and ticker animations run continuously once the slide is active; honor `prefers-reduced-motion` by pausing the blink and marquee (see Known Gaps).
- Elements with `[data-anim]` start invisible (opacity:0) and animate on `.is-active` — re-visiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. LED glow (`text-shadow`) and the marquee do not print — verify exported PDFs still distinguish numerals from labels (they will, via size and weight, but the drama is lost on paper; note this in the delivery message).

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / numerals (Orbitron 800–900) | Orbitron | Noto Sans SC (思源黑体) | 900 (heaviest available — CJK must match the LED mass) |
| Side name / readout (JetBrains Mono 600) | JetBrains Mono | Noto Sans SC (思源黑体) | 600 (no uppercase, tracking 0 — see Aesthetic Notes) |
| Body / lead (JetBrains Mono 400–500) | JetBrains Mono | Noto Sans SC (思源黑体) | 400 or 500 |
| Ticker / captions (JetBrains Mono 500) | JetBrains Mono | Noto Sans SC (思源黑体) | 400 or 500 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"Orbitron, Noto Sans SC, system-ui, sans-serif"` or `"JetBrains Mono, Noto Sans SC, monospace"`. Latin glyphs render in Orbitron / JetBrains Mono; CJK glyphs fall through to Noto Sans SC. No per-language class needed. Mixed lines like `目标 120 万，实际 98 万` render in one run with the correct face per script — and keep all numerals Arabic (Orbitron), which is the scoreboard convention.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Orbitron:wght@500;600;700;800;900&family=JetBrains+Mono:wght@400;500;600&family=Noto+Sans+SC:wght@400;500;700;900&display=swap" rel="stylesheet">
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

Scoreboard's Latin voice is **Orbitron** — a squared, geometric digital face whose wide forms carry the seven-segment illusion. **Noto Sans SC has no seven-segment analogue**, and Chinese glyphs cannot be made to look like segments. The honest move: set Chinese numerals and display in **Noto Sans SC 900** (the heaviest available) and let the **LED glow do the digital work** — `text-shadow: 0 0 12px currentColor` reads as "powered" on any glyph, Chinese included. Keep Chinese display headlines short (2–6 characters, e.g. 目标冲刺, 季度对决); a long Chinese headline at display size breaks the marquee register.

Side names and labels are JetBrains Mono uppercase with 0.08–0.14em tracking — **CJK has no uppercase and should not be tracked.** Set Chinese side names in Noto Sans SC 600, mixed case, letter-spacing 0, at `{typography.side-name}` size; the "readout" voice comes from the size and the LED color, not from tracking. A pure-Latin side name (e.g. "TARGET") can stay in JetBrains Mono uppercase as designed.

The VS center mark is a sports convention that survives translation: keep "VS" in Latin (Orbitron 900) even in fully Chinese decks, or swap to 对 for a more local register — pick once and stay consistent. The ticker in Chinese scrolls fine but reads denser; set Chinese ticker text at `{typography.ticker-text}` size with a slower pass (22s) and keep each ticker item short. Arabic numerals (Orbitron 800) stay the score voice inside Chinese sentences — 比分 98:120 是 the arena's universal language.

### Known CJK Gap

Orbitron and JetBrains Mono are Latin-only faces, so every Chinese moment lands on Noto Sans SC, which has no digital/segment styling and no uppercase. The seven-segment illusion and the uppercase readout register are **Latin-only properties**; Chinese slides compensate with weight (900), glow, and short phrasing. Also, the ghost `888` layer (`{components.ghost-digits}`) is meaningless behind Chinese numerals — suppress it on Chinese-only clusters. And the 7.5vw cluster size tuned for Orbitron's narrow width will read wider in Noto Sans SC 900; verify overflow when a Chinese side name is longer than 4 characters.

## Iteration Guide

1. Any new slide background is `{colors.board-black}`. Never introduce a lighter stage; the arena is black.
2. Any new contest slide has exactly two clusters: left in `{colors.led-red}` (or white for neutral), right in `{colors.led-green}` (or white), separated by the blinking `{components.vs-divider}`. Keep side polarity stable across the deck.
3. Any new numeral uses Orbitron — 800 at `{typography.stat-value}` (7.5vw) for giants, 700 at `{typography.stat-value-sm}` (3.8vw) for secondary — with the layered `currentColor` glow.
4. Any new label, side name, or readout uses JetBrains Mono uppercase: 600 at `{typography.side-name}` (1.8vw) for side names, 600 at `{typography.label}` (0.75vw) for chip captions, 500 at `{typography.ticker-text}` (1vw) for the ticker.
5. Any new period or countdown boundary is the amber `{components.period-line}` (3px, 10px glow). One per slide.
6. Any new supporting number goes in a `{components.kpi-chip}` — small, bordered, quiet. Never a second row of giants.
7. Any new dim element (caption, dot, ghost digit) uses `{colors.dim}`; dim is the resting state of every LED.
8. Any new content slide carries the ticker band; cover and closing slides may drop it.
9. Glow is always `text-shadow: 0 0 12px currentColor, 0 0 32px currentColor` on `currentColor` — never a hard-coded shadow color, so hue and light cannot disagree.
10. If a slide needs more than two contestant hues plus white, it is not a scoreboard slide — split the content.

## Known Gaps

- The seven-segment look is an *illusion* created by Orbitron's squared geometry plus the ghost `888` layer — the numerals are not true segment displays. Do not attempt real segment rendering; the effect is deliberately approximate.
- `text-shadow` glow does not print and can be clipped by overflow-hidden ancestors on some renderers; verify the cluster's parent allows glow bleed.
- The marquee requires duplicated text for a seamless loop; if the text is short enough to fit without scrolling, the loop shows a visible seam — either lengthen the item list or pause the animation.
- The blink and marquee animations ignore `prefers-reduced-motion` in the base template; add a media query to pause them for motion-sensitive viewers.
- Orbitron at 7.5vw with 0.02em tracking is wide; on slides where the cluster must sit beside a side name of 8+ characters, the numeral may need a size step down (to `{typography.stat-value-sm}`) to avoid overflow.
- JetBrains Mono 600 uppercase tracking (0.14em) at `{typography.label}` size is nearly unreadable below 0.7vw — do not shrink labels to fit; drop the text instead.
- The red/green polarity is a convention held by discipline, not by the template — nothing enforces "left is red"; keep a style note at the top of the deck's CSS so later editors don't flip sides mid-deck.
