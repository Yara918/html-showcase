---
version: alpha
name: Data Wall
description: A dense, annotation-first data canvas in the tradition of evidence-led financial-broadsheet charting. Small-multiple charts sit in a strict grid, every chart carries one mono callout that points at the key point, axes are 1px hairlines, and a single highlighted insight per slide is marked in red. Newsreader serif numerals give statistics an editorial gravity that a sans cannot; Inter carries body copy; JetBrains Mono carries every annotation, axis, and source note. The system is built to carry dense evidence without ever looking crowded.

colors:
  paper: "#FAF7F2"
  white: "#FFFFFF"
  ink: "#26221E"
  graphite: "#6E675E"
  graphite-light: "#A39B8F"
  accent-red: "#E63312"
  teal: "#1F7A74"
  gold: "#C99B3F"
  blue: "#2E5E8C"

color-aliases:
  c-bg: paper
  c-bg-light: white
  c-bg-cream: paper
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite-light
  c-accent: accent-red
  c-border: ink
  c-border-light: graphite-light

typography:
  display:
    fontFamily: "Newsreader, Noto Serif SC, Georgia, serif"
    fontSize: 7vw
    fontWeight: 500
    lineHeight: 1.0
    letterSpacing: -0.01em
  h1:
    fontFamily: "Newsreader, Noto Serif SC, Georgia, serif"
    fontSize: 4.6vw
    fontWeight: 600
    lineHeight: 1.05
    letterSpacing: -0.01em
  h2:
    fontFamily: "Newsreader, Noto Serif SC, Georgia, serif"
    fontSize: 3vw
    fontWeight: 600
    lineHeight: 1.15
  h3:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.9vw
    fontWeight: 600
    lineHeight: 1.25
  lead:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.5vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.7
  caption:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.8vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.7vw
    fontWeight: 400
    letterSpacing: 0.1em
    textTransform: uppercase
  stat-value:
    fontFamily: "Newsreader, Noto Serif SC, Georgia, serif"
    fontSize: 5vw
    fontWeight: 500
    lineHeight: 1.0
    letterSpacing: -0.01em
  annotation:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.78vw
    fontWeight: 400
    lineHeight: 1.5
  source-note:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.62vw
    fontWeight: 400
    lineHeight: 1.5
    letterSpacing: 0.05em
  axis-label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.66vw
    fontWeight: 400

spacing:
  pad-x: 5vw
  pad-y: 4.5vh
  gap-lg: 4vh
  gap-md: 2.2vh
  gap-sm: 1vh

canvas:
  width: 100vw
  height: 100vh

components:
  panel:
    borderTop: "1px solid {colors.ink}"
    padding: "{spacing.gap-md} 0 0 0"
    description: "The atomic region of the canvas: a rule-topped block that holds one chart or one stat group. Panels are separated by 1px rules, never by shadows or fills."
  small-multiple:
    display: grid
    gridTemplateColumns: "repeat(3, 1fr)"
    columnGap: "{spacing.gap-md}"
    rowGap: "{spacing.gap-md}"
    description: "A strict grid of identical miniature charts sharing one scale. Each cell holds one small chart, a mono cell label, and its own inline annotation."
  chart-svg:
    display: block
    width: "100%"
    height: "auto"
    description: "All charts (bars, lines, donuts, sparklines) are inline SVG — never canvas, never images. 1px strokes with shape-rendering: crispEdges for bar and axis geometry."
  axis:
    stroke: "{colors.graphite-light}"
    strokeWidth: 1
    description: "Hairline axis geometry in graphite-light. Baselines and left axes are solid 1px; tick extensions use the same stroke at 50% opacity."
  axis-label:
    fontFamily: "{typography.axis-label.fontFamily}"
    fontSize: "{typography.axis-label.fontSize}"
    fill: "{colors.graphite}"
    description: "Mono axis labels (units, year ticks, series names) set in graphite. Never ink — axes are furniture, not content."
  leader-line:
    stroke: "{colors.ink}"
    strokeWidth: 1
    strokeDasharray: "2 2"
    description: "A 1px dashed ink leader line connecting a callout label to the exact point it annotates. The dash reads as 'this is a pointer,' not a chart element."
  callout:
    fontFamily: "{typography.annotation.fontFamily}"
    fontSize: "{typography.annotation.fontSize}"
    color: "{colors.ink}"
    background: "{colors.white}"
    padding: "0.35em 0.7em"
    borderLeft: "2px solid {colors.accent-red}"
    description: "The system's signature annotation: a white chip with a 2px red left edge, holding one mono sentence that states the chart's key point. Every chart carries exactly one callout."
  stat-cell:
    borderTop: "1px solid {colors.ink}"
    padding: "{spacing.gap-md} {spacing.gap-md} {spacing.gap-md} 0"
    description: "Rule-topped cell with a 5vw Newsreader stat numeral, an Inter label, and a mono source note. The red numeral is permitted only when it marks the slide's one highlighted insight."
  source-note:
    fontFamily: "{typography.source-note.fontFamily}"
    fontSize: "{typography.source-note.fontSize}"
    letterSpacing: 0.05em
    color: "{colors.graphite-light}"
    description: "Mono source note at the bottom-left of the slide or chart panel: 'SOURCE: Q3 SYSTEM TELEMETRY, EXPORTED 2025-10-01'. Every chart must carry one."
  legend:
    display: flex
    gap: "{spacing.gap-md}"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    description: "Mono legend row under a chart: 7px square swatches (borderRadius 0) followed by uppercase legend labels in graphite."
  legend-dot:
    width: 7px
    height: 7px
    background: "{colors.graphite}"
    description: "Square 7px legend swatch. Series color variants: graphite (default), {colors.teal}, {colors.gold}, {colors.blue}; the highlighted series is {colors.accent-red}."
  sparkline:
    width: "100%"
    height: "5.5vh"
    description: "Inline SVG line sparkline in a stat cell. The last point is emphasized with a 5px square marker; the red sparkline is allowed only for the one highlighted insight."
  donut:
    width: "min(20vw, 32vh)"
    height: "min(20vw, 32vh)"
    borderRadius: 50%
    description: "Donut ring via conic-gradient with a same-surface ::after cutout. Segments use the graphite/teal/gold/blue set; the single highlighted segment is red."
  bar-fill:
    width: "100%"
    background: "{colors.graphite}"
    description: "Bar geometry in graphite. The highlighted bar is {colors.accent-red}; secondary series may use {colors.teal} or {colors.gold} at reduced width (see Series Discipline)."
  table:
    borderTop: "1px solid {colors.ink}"
    borderCollapse: collapse
    description: "Dense data table with 1px ink horizontal rules and 1px graphite-light column rules. Header row is mono uppercase; the row holding the key metric may carry a red numeral."
  insight-rule:
    width: 64px
    height: 2px
    background: "{colors.accent-red}"
    description: "The 64×2px red rule under the slide's one highlighted insight — a headline, a stat numeral, or a callout. It is the only red decoration allowed outside charts."
  annotation-tag:
    fontFamily: "{typography.annotation.fontFamily}"
    fontSize: "{typography.annotation.fontSize}"
    color: "{colors.ink}"
    description: "Bare mono annotation text ('+18.4% YoY') placed directly beside a data point with a dashed leader line. No chip background — the chip is reserved for callouts."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Data Wall is an **annotation-first data canvas** in the tradition of evidence-led financial-broadsheet charting: dense small-multiple charts, hairline axes, serif statistics, and a single highlighted insight per slide. Where most presentation systems treat the chart as an illustration of a point, Data Wall treats the chart as the primary text — the slide is a document, the charts are its sentences, and the mono callouts are the paragraphs that tell you what to read first.

The system's core rule is **one insight per slide, marked once**. Every chart carries exactly one mono callout — a white chip with a 2px red left edge and a dashed ink leader line pointing at the key point. The slide's headline states the insight in one line; the callouts underneath it walk through the evidence; the red accent is reserved for the single highlighted series or the single highlighted numeral. If a slide has two red things, it has two insights, and it should be split into two slides. This discipline is what keeps a very-high-density canvas calm: the density is in the evidence, the clarity is in the annotation.

The typography is a **serif-for-numbers, sans-for-words, mono-for-metadata** hierarchy. **Newsreader** at weights 500–600 sets display, headlines, and stat numerals — a text serif with real stroke contrast, the same face class used by serious newspaper design, which is precisely why the statistics read as editorial rather than dashboard-y. **Inter** at weight 400 carries body and lead copy, quiet and invisible. **JetBrains Mono** carries every axis label, callout, annotation, legend, and source note — the chart's metadata voice, always present, always smaller than the data it describes. The CJK pair flips the display face to Noto Serif SC so Chinese statistics keep the same editorial serif gravity.

Color is a **disciplined semantic set**. Paper (`{colors.paper}`) is the warm off-white surface; ink (`{colors.ink}`) is text and structural rules; graphite and graphite-light are secondary and tertiary text plus default chart series. The chromatic set — red (`{colors.accent-red}`), teal (`{colors.teal}`), gold (`{colors.gold}`), blue (`{colors.blue}`) — is used only inside charts, with three disciplines: red highlights exactly one series or numeral per slide; teal, gold, and blue are reserved for semantically distinct series and repeat consistently across the deck (the same series carries the same color on every slide); every chromatic use is captioned in mono.

Depth comes from **1px rules and the 8px grid**, not from elevation. Panels are separated by 1px ink top rules; axes are 1px graphite-light hairlines; there are no shadows, no rounded corners except the donut, no gradients except the donut's conic fill, no 3D. The canvas is an evidence desk: flat, legible, and honest about its own structure.

**Key Characteristics:**
- Small-multiple charts in a strict 3-column grid sharing one scale.
- Every chart carries exactly one mono callout with a dashed leader line to the key point.
- 1px hairline axes in graphite-light; inline SVG for all chart geometry.
- Big Newsreader serif stat numerals — the editorial serif is the statistics voice.
- Mono source notes at the bottom-left of every chart and slide.
- Red is reserved for the single highlighted insight — one series or one numeral per slide.
- Everything aligns to an 8px grid; panels separate by 1px rules, never shadows.
- A restrained semantic chart palette: red, teal, gold, blue — each repeatable, each captioned.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.paper}` | #FAF7F2 | Default surface. Warm off-white with a hint of bone — reads as print stock, not as screen white |
| `{colors.white}` | #FFFFFF | Callout chips, figure wells, inset stat fields |
| `{colors.ink}` | #26221E | Headlines, body text, structural rules, leader lines, stat numerals |
| `{colors.graphite}` | #6E675E | Secondary text, axis labels, default chart series |
| `{colors.graphite-light}` | #A39B8F | Tertiary metadata, source notes, hairline axes and tick extensions |
| `{colors.accent-red}` | #E63312 | The highlighted insight: one series, one numeral, one callout edge, or the 64×2px insight rule |
| `{colors.teal}` | #1F7A74 | Semantic chart series color — e.g., the comparison cohort or the secondary market |
| `{colors.gold}` | #C99B3F | Semantic chart series color — e.g., revenue share or the target band |
| `{colors.blue}` | #2E5E8C | Semantic chart series color — e.g., a neutral third series or regional aggregate |

### Defaults

- **Default surface background**: `{colors.paper}`. Slides are never pure white and never dark.
- **Default headline color**: `{colors.ink}`. Headlines never render in a chromatic color.
- **Default stat numeral color**: `{colors.ink}` — except the single highlighted numeral, which may be `{colors.accent-red}`.
- **Default body text color**: `{colors.ink}`; muted lead and secondary text use `{colors.graphite}`.
- **Default annotation / callout color**: `{colors.ink}` text on a `{colors.white}` chip with a 2px red left edge.
- **Default axis and source-note color**: `{colors.graphite-light}` for hairlines and sources; `{colors.graphite}` for axis labels.
- **Default border / divider color**: `{colors.ink}` for panel rules; `{colors.graphite-light}` for column rules and axes.
- **Default chart series colors**: graphite for the baseline series; red for the one highlighted series; teal, gold, blue for semantically distinct series. Chart color assignments are stable across the deck.

### Series Discipline

- Red highlights **one** series or numeral per slide. Two red marks on a slide means two insights — split the slide.
- Teal, gold, and blue are semantic, not decorative: the same series keeps the same color on every slide it appears on, so a reader can track one series across the deck.
- No chromatic color is ever used for text, borders, or chrome. Chromatic colors exist inside charts and nowhere else.

## Typography

### Font Family

The system loads four Latin faces plus CJK fallbacks: **Newsreader** (weights 500, 600) carries display, headlines, and stat numerals; **Inter** (weights 400, 500) carries body, lead, and caption copy; **JetBrains Mono** (weight 400) carries every annotation, axis label, legend, callout, and source note; **Noto Serif SC** is the CJK fallback for Newsreader; **Noto Sans SC** is the CJK fallback for Inter and JetBrains Mono.

The emotional register is deliberate:

- Newsreader reads as **editorial, unhurried, and weighty** — a text serif with high-contrast strokes that makes a number like 12,480 feel reported rather than displayed. It is the system's evidence voice.
- Inter reads as **neutral to the point of invisibility** at 400 — body copy must never compete with the data.
- JetBrains Mono reads as **instrument, not voice** — annotations and axes are the chart's footnote apparatus, always present, always quieter than the data.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 7vw | Newsreader | 500 | Title-slide or insight-headline display |
| `{typography.stat-value}` | 5vw | Newsreader | 500 | Big serif stat numeral inside a stat cell |
| `{typography.h1}` | 4.6vw | Newsreader | 600 | Chapter or single-insight headline |
| `{typography.h2}` | 3vw | Newsreader | 600 | Primary content-slide headline |
| `{typography.h3}` | 1.9vw | Inter | 600 | Panel title, small-multiple group label |
| `{typography.lead}` | 1.5vw | Inter | 400 | Lead paragraph under a headline |
| `{typography.body}` | 1.05vw | Inter | 400 | Body paragraph |
| `{typography.caption}` | 0.8vw | Inter | 400 | Image caption, fine print |
| `{typography.label}` | 0.7vw | JetBrains Mono | 400 | Legend labels, panel keys, column headers |
| `{typography.annotation}` | 0.78vw | JetBrains Mono | 400 | Callouts and inline annotations |
| `{typography.axis-label}` | 0.66vw | JetBrains Mono | 400 | Axis ticks and series names inside charts |
| `{typography.source-note}` | 0.62vw | JetBrains Mono | 400 | Source notes, export stamps |

### Defaults

- **Default insight headline**: `{typography.h1}` (4.6vw Newsreader 600) — one line, states the slide's single insight.
- **Default panel headline**: `{typography.h3}` (1.9vw Inter 600) for panels and small-multiple groups.
- **Default stat numeral**: `{typography.stat-value}` (5vw Newsreader 500).
- **Default annotation size**: `{typography.annotation}` (0.78vw mono).
- **Default body size**: `{typography.body}` (1.05vw Inter 400).

When unsure, the canonical structure is: `{typography.h1}` insight line at top-left, a `{typography.lead}` evidence paragraph under it, then the chart panel with its `{typography.annotation}` callout and `{typography.source-note}`.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every chart carries exactly one mono callout** with a 2px red left edge and a dashed ink leader line to the key point. A chart without a callout is an unfinished chart.
- **Every chart and stat cell carries a mono source note** at its foot or the slide's bottom-left.
- **Big numbers are always Newsreader serif.** A stat numeral in Inter or a sans reads as a different system.
- **All chart geometry is inline SVG** with 1px strokes (`shape-rendering: crispEdges` for bars and axes); never canvas, never raster images.
- **Axes are 1px hairlines in `{colors.graphite-light}`** with mono axis labels in `{colors.graphite}`.
- **Red marks exactly one insight per slide** — one series, one numeral, or the 64×2px insight rule under the headline.
- **All panels separate by 1px ink rules** — no shadows, no fills, no rounded panels.
- **Everything aligns to the 8px grid** — panel heights, chart heights, gaps, and padding are all multiples of 8px on the 1920×1080 stage.

### Typography Principles

The rhythm of Data Wall is **Newsreader serif numerals + Inter body + dense mono annotation**. Switching stat numerals to a sans reads as a different system. Setting annotations in a readable serif or sans at body size reads as a different system — annotations must stay mono and small so the data stays primary. Bold is not used inside body text; the weight contrast lives between the serif display scale and the sans body scale. Italic is not used at all. The serif face's italic (Newsreader does have one) is never used — data text must not slant.

## Layout

### Canvas System

The system targets the fixed 1920×1080 stage model described in the Fixed-Stage Policy above, expressed in the source as fluid `100vw × 100vh` proportions. All sizes are `vw`/`vh` design proportions translated onto the stage. The deck is a horizontal flex strip with slide-to-slide transitions at 0.4s with a gentle ease-out — fast enough to keep a data review moving, slow enough to let the eye settle on each evidence panel.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 5vw | Slide horizontal padding |
| `{spacing.pad-y}` | 4.5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4vh | Between major regions (headline block → chart panel) |
| `{spacing.gap-md}` | 2.2vh | Between related elements; small-multiple gutters |
| `{spacing.gap-sm}` | 1vh | Between tightly related elements (numeral under label) |

All values are rounded to the 8px grid on the 1920×1080 stage (5vw ≈ 96px, 2.2vh ≈ 24px, 1vh ≈ 11px → 8px). Panel heights and chart heights are computed in 8px multiples.

### Chrome Frame

Content slides carry a **chrome header** and **chrome foot**. The header is a `flex space-between` row of two mono labels (left: panel key such as `PANEL 02 / REVENUE`; right: deck code such as `SHEET 07/24`), separated from the body by a 1px ink rule. The foot holds the slide title on the left and the source note (`{components.source-note}`) on the bottom-left, with the page number at bottom-right. Title slides and closing slides suppress the chrome; they carry the source note and page number only.

## Depth and Elevation

### No Shadows, Hairline Rules Only

Data Wall uses **zero box-shadow declarations**. Depth is created through three mechanisms:

1. **1px ink panel rules** (`{components.panel}`) — every panel is a rule-topped block; the rule count on a slide is a direct measure of how many regions it holds.
2. **1px graphite-light chart axes** — charts float on paper with hairline geometry; the axis is the chart's only frame.
3. **The 8px grid and whitespace rhythm** — consistent 8px multiples make dense panels read as organized; the air between panels is a designed value.

### No Atmospheric Effects

There are no gradients outside the donut's conic fill, no glows, no grain, no blur, no opacity layers beyond the 50%-opacity tick extensions. No 3D, no extruded bars, no perspective. The flatness is a claim: the evidence is presented, not dramatized.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every panel, stat cell, table, legend swatch, marker, and callout corner |
| 50% (circle) | Donut chart only |
| 999px (pill) | None — pills do not exist |

Data Wall is **square-cornered without exception** outside the donut. Rounded cards would import a product-dashboard aesthetic that the system explicitly avoids.

### Border Weights

- **1px solid `{colors.ink}`** — panel rules, stat-cell tops, table horizontals, leader lines are dashed-ink variant.
- **1px solid `{colors.graphite-light}`** — chart axes, tick extensions (at 50% opacity), table column rules.
- **2px solid `{colors.accent-red}`** — the callout's left edge and the 64×2px insight rule. This is the only red border in the system.

### Decorative Element Types

**Mono callout with leader line** — `{components.callout}`: a white chip (0.35em × 0.7em padding) with a 2px red left edge, containing one mono sentence like `Q3 RAMP +18.4% — THE ONLY COHORT ABOVE TARGET`. A 1px dashed ink leader line (`{components.leader-line}`, `stroke-dasharray: 2 2`) connects the chip to the exact point it annotates. Every chart carries one.

**Bare annotation** — `{components.annotation-tag}`: mono text like `+18.4% YoY` placed directly beside a data point with a dashed leader line and no chip. Used for in-chart value labels; the chip is reserved for the full-sentence callout.

**Small multiples** — `{components.small-multiple}`: a strict 3-column grid of identical miniature charts sharing one scale, each with a mono cell label (`JAN`, `FEB`, …) and its own callout. Small multiples are the system's way of showing a trend across many slices without a wall of text.

**Inline SVG charts** — `{components.chart-svg}`: bars, lines, donuts, and sparklines rendered as inline SVG with 1px strokes. Bars use `shape-rendering: crispEdges`; line charts use `vector-effect: non-scaling-stroke` so hairlines stay 1px at any scale.

**Hairline axes** — `{components.axis}`: 1px graphite-light baselines and left axes with mono tick labels (`{components.axis-label}`). Tick extensions run at 50% opacity.

**Big serif stat cell** — `{components.stat-cell}`: rule-topped cell with a 5vw Newsreader numeral, an Inter label, and a mono source note. The numeral is ink; the single highlighted numeral may be red.

**Sparkline in a stat cell** — `{components.sparkline}`: an inline SVG line at 5.5vh height with a 5px square end marker; used under stat numerals to show trajectory without a full chart.

**Donut chart** — `{components.donut}`: `min(20vw, 32vh)` circle with a conic-gradient ring and a same-surface `::after` cutout; segments follow the semantic palette with one red segment allowed.

**Dense data table** — `{components.table}`: 1px ink horizontals, 1px graphite-light column rules, mono uppercase header, red numeral permitted on the key-metric row only.

**Legend** — `{components.legend}`: a mono uppercase row with 7px square swatches; series colors repeat the semantic set.

**64×2px insight rule** — `{components.insight-rule}`: the red rule under the slide's one highlighted insight (headline, numeral, or callout). It is the slide's red punctuation and counts as its single red mark.

## Do's and Don'ts

### Do
- Give every chart exactly one mono callout with a dashed leader line to the key point.
- Give every chart and stat cell a mono source note.
- Use Newsreader serif for all display, headlines, and stat numerals — the serif is the evidence voice.
- Use inline SVG for all chart geometry with 1px strokes.
- Reserve red for exactly one highlighted insight per slide.
- Keep semantic series colors (teal, gold, blue) stable across the deck and captioned.
- Separate panels with 1px ink rules; align everything to the 8px grid.
- Use mono annotations, axis labels, legends, and source notes at their token sizes.
- Keep the headline to one line stating the slide's single insight.

### Don't
- Don't show a chart without its callout — an unannotated chart is unfinished evidence.
- Don't use more than one red mark per slide. Two reds = two insights = two slides.
- Don't set stat numerals in a sans face. Numbers are always Newsreader.
- Don't use canvas, raster images, or 3D for charts — inline SVG only.
- Don't use shadows, rounded panels, or pills. Flat, square, hairline.
- Don't use chromatic colors for text, borders, or chrome. Color lives inside charts only.
- Don't center charts or stat cells. Everything is left-anchored on the grid.
- Don't use italic anywhere, including Newsreader's italic. Data text does not slant.
- Don't hide the source note. A chart without a source is an unverifiable claim.
- Don't let annotations exceed one or two lines — a callout that needs a paragraph is a slide that needs its own panel.

## Responsive Behavior

The source template is viewport-fluid by design (all sizes in `vw`/`vh`), but per the Fixed-Stage Policy the `html-showcase` output is a fixed 1920×1080 stage scaled uniformly to the viewport — no reflow, no breakpoints, letterboxing or pillarboxing only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions at 0.4s with a gentle `cubic-bezier(0.25, 0.6, 0.3, 1)` ease-out.
- Entrance animations are minimal: `fade-up` (10px, 0.45s) for text blocks and `rule-grow` (scaleX from 0 to 1, 0.6s, transform-origin left) for the insight rule. Both run on slide entrance via `data-anim` with staggered `data-delay` steps; charts themselves never animate (see Known Gaps).
- Elements with `[data-anim]` start at opacity 0 and animate on `.is-active`; revisiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export captures only the active slide; multi-slide export requires manual navigation per slide. Printed output should use `color-adjust: exact` guidance in the generated deck so the semantic series colors survive PDF export.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline / stat numerals (Newsreader 500–600) | Newsreader | Noto Serif SC (思源宋体) | 600 (display), 500 (numerals) |
| Panel titles / sub-headlines (Inter 600) | Inter | Noto Sans SC (思源黑体) | 600 |
| Body / lead (Inter 400) | Inter | Noto Sans SC (思源黑体) | 400 |
| Annotation / axis / source (JetBrains Mono) | JetBrains Mono | Noto Sans SC | 400 (do not force monospace on CJK; see Aesthetic Notes) |
| Numerals inside Chinese text | Newsreader | Noto Serif SC | 500 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"Newsreader, Noto Serif SC, Georgia, serif"` (or the Inter / JetBrains Mono equivalents). Latin glyphs render in the Latin face; CJK glyphs automatically fall through to the CJK face. No per-language class is needed. Mixed sentences like `Q3 留存率 +18.4% YoY` render in one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Newsreader:opsz,wght@6..72,500;6..72,600&family=Inter:wght@400;500&family=JetBrains+Mono:wght@400&family=Noto+Sans+SC:wght@300;400;500;700;900&family=Noto+Serif+SC:wght@400;500;600;700&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK (the serif's -0.01em display tracking does not transfer)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `Q3 留存率` not `Q3留存率`)
- One font per sentence
- Numerals adjacent to Chinese stay Latin-proportional (Newsreader); do not force full-width numerals

### Aesthetic Notes for This System

Data Wall's defining trait is **Newsreader serif statistics**: high-contrast text-serif strokes that make numbers read as reported facts. Noto Serif SC is the correct CJK partner — its 宋体 structure has the same editorial gravity and ink contrast, so a Chinese headline like `季度营收创三年新高` beside a Newsreader numeral holds together. Set Chinese display in Noto Serif SC 600 and Chinese stat labels in 500; do not drop to lighter weights, which read as anemic at 5vw sizes.

The mono annotation voice does not transfer to CJK — Chinese has no monospace tradition in this register and forcing it looks broken. **Set Chinese annotations, axis labels, and source notes in Noto Sans SC 400, mixed case, letter-spacing 0.** The "instrument" register is carried by size (0.62–0.78vw), color (graphite), and the mono treatment of any Latin tokens inside the string (series codes, dates, percentages stay in JetBrains Mono). A pure-Latin source line (`SOURCE: Q3 SYSTEM TELEMETRY`) stays fully mono as designed.

The dashed leader line and callout chip work unchanged in CJK — they are geometry, not glyphs. Chinese callout text at 0.78vw is legible but dense; prefer callouts that mix a short Chinese claim with Latin figures (`Q3 爬坡 +18.4% — 达标队列`).

### Known CJK Gap

Chinese glyphs are roughly square and consume ~15–20% more horizontal space than Latin at the same point size. The dense 3-column small-multiple grid, tuned for Latin axis labels, will wrap Chinese cell labels to two lines. Reduce small-multiple cell labels to `{typography.caption}` size or shorten them to two-character keys (`一月` → `1月`) when the deck is Chinese. The 5vw Newsreader stat numerals are pure Latin digits and behave identically; the risk is in labels, not numbers. The 8px-grid rule applies unchanged, but panel heights should add one 8px step when a Chinese panel title wraps.

## Iteration Guide

1. Any new slide states exactly one insight in its `{typography.h1}` headline. If the slide needs two insights, split it.
2. Any new chart is inline SVG with 1px hairline axes in `{colors.graphite-light}` and mono axis labels in `{colors.graphite}`.
3. Any new chart carries exactly one mono callout (white chip, 2px red left edge, dashed ink leader) and one mono source note.
4. Any new stat numeral uses `{typography.stat-value}` (Newsreader 500). One numeral per slide may be `{colors.accent-red}` as the highlighted insight.
5. Any new series color comes from the semantic set (teal, gold, blue) or is the single red highlight; the same series keeps the same color on every slide.
6. Any new panel is a rule-topped block (`{components.panel}`) aligned to the 8px grid. No shadows, no fills, no rounded corners.
7. Any new legend uses 7px square swatches and mono uppercase labels.
8. Any new table uses 1px ink horizontals, 1px graphite-light columns, and a mono uppercase header.
9. Keep chrome to two mono labels per band; title and closing slides suppress chrome.
10. Verify every chromatic element on the slide is captioned, and verify exactly one red mark exists per slide.
11. When in doubt, add a source note and an annotation — Data Wall is over-evidenced by design, never under-annotated.

## Known Gaps

- Charts are static inline SVG with hand-computed values; there is no data-binding layer. Bars, lines, and donut segments must be regenerated when the underlying data changes.
- Entrance animations are text-only by design; charts appear instantly with their slide. An animated draw-in would require per-path SVG animation wiring that the source does not provide.
- The callout chip's 2px red left edge is the only red border; a slide where the highlighted series, the callout edge, and a red numeral all appear would break the one-red rule. The generator must choose one red carrier per slide.
- The donut's same-surface `::after` cutout assumes the paper background; a white figure well under a donut needs the cutout restyled to the well color.
- The semantic series palette (teal, gold, blue) has no documented ordering; decks with more than four series must reuse colors, which can confuse cross-slide tracking — cap series at four per slide.
- The source template is named "Data Wall" in the library; any historical names in source comments refer to the same system.
- The 0.62vw source-note size is near the legibility floor on a scaled-down projector view; verify source notes are readable at the actual projection resolution, not just on the 1920×1080 stage.
