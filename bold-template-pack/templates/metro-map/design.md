---
version: alpha
name: Metro Map (Beck Diagram)
description: A diagram-first system that borrows the visual grammar of Harry Beck's 1933 tube map — 45° lines, colored routes, and interchange nodes — to render processes, org structures, user journeys, roadmaps, and supply routes as rideable networks. Archivo at weights 500–700 supplies a single contemporary grotesque voice; color is reserved for route lines and nothing else. Every slide answers one question: where are we going, and what are the stops in between?

colors:
  cream: "#F7F3EA"
  cream-deep: "#EFE9DC"
  ink: "#1A1A18"
  graphite: "#8A847C"
  route-blue: "#1466B8"
  route-red: "#D64541"
  route-green: "#3A8F4E"
  route-gold: "#C99B3F"
  route-purple: "#7A4E9E"
  interchange-white: "#FFFFFF"

color-aliases:
  c-bg: cream
  c-bg-light: interchange-white
  c-bg-cream: cream-deep
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite
  c-accent: route-blue
  c-border: ink
  c-border-light: graphite

typography:
  display:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 8vw
    fontWeight: 700
    lineHeight: 0.98
    letterSpacing: -0.02em
  h1:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.6vw
    fontWeight: 700
    lineHeight: 1.05
    letterSpacing: -0.01em
  h2:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3vw
    fontWeight: 600
    lineHeight: 1.15
  h3:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.9vw
    fontWeight: 500
    lineHeight: 1.3
  lead:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.45vw
    fontWeight: 500
    lineHeight: 1.6
  body:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.05vw
    fontWeight: 500
    lineHeight: 1.7
  caption:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.8vw
    fontWeight: 500
    lineHeight: 1.55
  label:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.7vw
    fontWeight: 500
    letterSpacing: 0.12em
    textTransform: uppercase
  stat-value:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.5vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: -0.01em
  station-label:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.95vw
    fontWeight: 500
    lineHeight: 1.2
  route-title:
    fontFamily: "Archivo, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.3vw
    fontWeight: 700
    lineHeight: 1.15

spacing:
  pad-x: 6vw
  pad-y: 5.5vh
  gap-lg: 4.5vh
  gap-md: 2.5vh
  gap-sm: 1.2vh

canvas:
  width: 100vw
  height: 100vh

components:
  route-line:
    stroke: "{colors.route-blue}"
    strokeWidth: 3px
    strokeLinecap: round
    strokeLinejoin: round
    fill: none
    description: "SVG polyline built from horizontal, vertical, and 45° diagonal segments only. The route's color is the only chromatic signal it carries; stroke color rotates among the five route tokens."
  interchange-node:
    width: 14px
    height: 14px
    borderRadius: 50%
    background: "{colors.interchange-white}"
    border: "3px solid {colors.route-blue}"
    description: "White-filled circle with a colored ring — the signature node where routes cross. The ring color follows the primary route; the white fill is the only pure-white moment in the system."
  terminus-node:
    width: 20px
    height: 20px
    borderRadius: 50%
    background: "{colors.route-blue}"
    description: "Larger filled circle at the end of a route — the visual full-stop of a line. Never hollow, never ringed."
  station-dot:
    width: 8px
    height: 8px
    borderRadius: 50%
    background: "{colors.route-blue}"
    description: "Small filled circle marking an intermediate stop; carries a label. On monochrome slides the dot falls back to {colors.ink}."
  station-label:
    fontFamily: "{typography.station-label.fontFamily}"
    fontSize: "{typography.station-label.fontSize}"
    fontWeight: "{typography.station-label.fontWeight}"
    color: "{colors.ink}"
    description: "Label beside a station dot, rotated to match the segment angle when the line runs at 45°. Kept short — 1–3 words."
  route-legend:
    display: flex
    gap: 8px
    alignItems: center
    description: "Corner block pairing a 22×3px colored dash with the route name in {typography.route-title}. Defaults to the top-right corner; one legend per slide."
  journey-chip:
    background: "{colors.ink}"
    color: "{colors.cream}"
    borderRadius: 999px
    padding: "0.4em 1.2em"
    description: "Pill-shaped callout carrying a journey metaphor ('2 stops to launch') with the numeral set in {typography.stat-value}. The system's only pill shape."
  map-plate:
    background: "{colors.cream-deep}"
    border: "1px solid {colors.graphite}"
    padding: "{spacing.gap-md}"
    description: "The diagram surface — one step deeper than the slide background, the only bordered region on a content slide. Routes live inside it; chrome lives outside."
  step-node:
    width: 34px
    height: 34px
    borderRadius: 50%
    background: "{colors.interchange-white}"
    border: "2px solid {colors.ink}"
    color: "{colors.ink}"
    fontFamily: "{typography.h3.fontFamily}"
    fontWeight: 700
    description: "Numbered circle (01, 02, …) for process steps rendered as stations along a line. The numeral is Archivo 700, centered."
  spine-rule:
    width: "100%"
    height: 1px
    background: "{colors.ink}"
    opacity: 0.85
    description: "Chrome divider under the header and above the footer. On diagram slides the footer rule is replaced by the route-strip."
  route-strip:
    width: "100%"
    height: 3px
    background: "linear-gradient(90deg, {colors.route-blue} 0 33%, {colors.route-red} 33% 66%, {colors.route-gold} 66% 100%)"
    description: "Footer accent: a thin horizontal band of route colors acting as the page's 'line map'. Three colors maximum, matching the routes actually used on the slide."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Metro Map (Beck Diagram) is a **diagram-first system**: before there is a slide, there is a network. The founding idea is Harry Beck's 1933 map of the London Underground, which threw out geographic accuracy and kept only topology — lines that run horizontally, vertically, or at exactly 45°, nodes that say *change here*, and colors that identify a route the way a name identifies a person. Beck's insight was that commuters don't need geography, they need structure. This system applies the same contract to business content: a process is a line, a milestone is a terminus, a handoff is an interchange, and a roadmap is a network you can ride from end to end.

The system is deliberately **diagram-first rather than prose-first**. The default content slide is a map plate (`{components.map-plate}`) holding a route network; text appears as station labels, legend entries, and chrome — never as a paragraph that has to carry the slide alone. When a slide needs explanation, the explanation is attached to the diagram (a label, a callout, a journey chip), not floated beside it as a wall of words. This is the discipline that separates a real diagram system from a presentation that happens to contain a chart.

Color is the system's scarcest resource and its loudest voice. The cream paper (`{colors.cream}`), ink (`{colors.ink}`), and graphite (`{colors.graphite}`) handle everything structural; the five route colors are reserved exclusively for route lines, node rings, and legend dashes. The rule is hard: **never more than three route colors on a slide**, and never use a route color for text. When color appears, it means *a line runs here* — nothing else is allowed to say that. The economy is what keeps a dense network diagram legible; a slide with five routes and colored text reads as a fruit salad, not a map.

Typography follows the same single-voice discipline. **Archivo** at weights 500, 600, and 700 carries every word on the slide — display, body, labels, station names. There is no serif, no mono, no handwriting; the diagram is the ornament and the type must stay out of its way. Archivo's contemporary grotesque construction keeps the system urban and current, closer to a modern wayfinding system than to a retro transit poster. Headlines are set tight (`-0.01em` to `-0.02em`) and mixed case; only chrome labels go uppercase with 0.12em tracking, mirroring the station-name typography of real transit maps.

The system's signature move is the **journey metaphor**: distance in a process is measured in stops, not steps. "2 stops to launch", "one transfer at design review", "you are here" — these phrases turn abstract process diagrams into something people can feel themselves moving through. The metaphor engine is supported by the `{components.journey-chip}` and the stat-value numeral; it is optional but strongly encouraged, because it is the moment the diagram stops being a chart and becomes a ride.

**Key Characteristics:**
- Cream paper background (`{colors.cream}`) on every slide; the diagram plate is one step deeper (`{colors.cream-deep}`).
- Route networks are SVG polylines with only horizontal, vertical, and 45° segments (`{components.route-line}`). No curves, no arbitrary angles, no 30° or 60° compromises.
- 2–3 colored routes maximum per slide (`{colors.route-blue}`, `{colors.route-red}`, `{colors.route-green}` are the default trio).
- Interchange nodes are white-filled circles with colored rings (`{components.interchange-node}`); terminus stations are larger filled circles (`{components.terminus-node}`).
- A route legend sits in one corner — a colored dash plus the route name in `{typography.route-title}` (`{components.route-legend}`).
- Process steps render as stations along a line (`{components.step-node}`), and journey metaphors like "2 stops to launch" appear in `{components.journey-chip}`.
- Archivo at weights 500–700 is the only typeface family; labels are uppercase with 0.12em tracking.
- The footer carries a 3px route-color strip (`{components.route-strip}`) instead of a plain rule — the page's own line map.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.cream}` | #F7F3EA | Default slide surface. Warm paper tone, never pure white — the canvas for every slide. |
| `{colors.cream-deep}` | #EFE9DC | Map-plate surface. One step deeper than the cream; defines the diagram region on a content slide. |
| `{colors.ink}` | #1A1A18 | Primary text, chrome rules, step-node rings, journey-chip fill. A very dark warm black. |
| `{colors.graphite}` | #8A847C | Secondary text, plate border, muted chrome. The only "quiet" tone — steps back from ink. |
| `{colors.route-blue}` | #1466B8 | Primary route color. Default accent (`c-accent`); the first route reached for. |
| `{colors.route-red}` | #D64541 | Second route color. Use for the "hot" line — risks, change, exceptions. |
| `{colors.route-green}` | #3A8F4E | Third route color. Use for the "healthy" line — approvals, delivery, stable flow. |
| `{colors.route-gold}` | #C99B3F | Fourth route color. Use for the "money" line — revenue, cost, ROI. |
| `{colors.route-purple}` | #7A4E9E | Fifth route color. Use only when a slide genuinely needs a fourth or fifth distinction. |
| `{colors.interchange-white}` | #FFFFFF | Interchange-node fill only. The single pure-white moment in the system; never used as a surface. |

### Defaults

- **Default surface background**: `{colors.cream}`. The system is single-surface by default; the map plate (`{colors.cream-deep}`) is the only sanctioned variant surface.
- **Default primary headline color**: `{colors.ink}`. Headlines never appear in a route color.
- **Default body text color**: `{colors.ink}` for primary copy; `{colors.graphite}` for secondary, captions, and plate borders.
- **Default label color**: `{colors.graphite}` for chrome labels; route-color text does not exist.
- **Default border / divider color**: `{colors.ink}` for chrome rules; `{colors.graphite}` for the plate border.
- **Default route color**: `{colors.route-blue}` — the primary line. Reached for first, used on the majority of slides.
- **Default route trio**: `{colors.route-blue}` + `{colors.route-red}` + `{colors.route-green}`. Gold and purple are fourth and fifth choices, not defaults.
- **Default rule weight**: 1px for chrome; 3px for route strokes.

### Semantic Roles

The five route colors are **content colors, not decoration**. They mean *a line runs here*. Never use them for: body text, headlines, backgrounds, button fills, or chart bars. The cream/ink/graphite trio carries all structure; the route tokens carry all meaning. Blue is the default line; red is the exception line (risk, change, escalation); green is the healthy line (approvals, delivery); gold is the money line (revenue, cost); purple is the overflow line for a rare fourth distinction. Because routes are hue-distinguished, keep each route's geometry distinct too — a route that shares a segment with another route must diverge at an interchange node, never fade into it.

## Typography

### Font Family

The system loads exactly two families: **Archivo** (weights 500, 600, 700) for every Latin text moment, and **Noto Sans SC** as the CJK fallback. There is no second Latin family. The reasoning is the same as the color rule: the diagram is the ornament, so type must be a single, quiet, contemporary voice. Archivo is a geometric grotesque with a strong vertical feel — its squared, upright construction echoes the 45° geometry of the map itself without competing with it. Weights below 500 are not loaded; the system never whispers, it annotates.

The emotional register of each weight is fixed:
- **Archivo 700** — display, h1, route names, journey numerals. Confident, diagrammatic, unemotional.
- **Archivo 600** — h2. The workhorse heading weight.
- **Archivo 500** — h3, lead, body, captions, labels, station names. The annotation voice — everything attached to the diagram.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 8vw | Archivo | 700 | Cover or opening display — tight, authoritative |
| `{typography.h1}` | 4.6vw | Archivo | 700 | Chapter-opening or section-break headline |
| `{typography.h2}` | 3vw | Archivo | 600 | Primary content-slide headline |
| `{typography.stat-value}` | 4.5vw | Archivo | 700 | Journey-metaphor numeral ("2" in "2 stops to launch") |
| `{typography.h3}` | 1.9vw | Archivo | 500 | Sub-headline, step-node numeral, legend heading |
| `{typography.lead}` | 1.45vw | Archivo | 500 | Lead paragraph or single supporting block |
| `{typography.body}` | 1.05vw | Archivo | 500 | Body copy inside callouts and notes |
| `{typography.route-title}` | 1.3vw | Archivo | 700 | Route names inside the legend |
| `{typography.station-label}` | 0.95vw | Archivo | 500 | Station labels along a route |
| `{typography.caption}` | 0.8vw | Archivo | 500 | Source notes, fine print, diagram footnotes |
| `{typography.label}` | 0.7vw | Archivo | 500 | Chrome label, sheet number, kicker — uppercase, 0.12em tracking |

### Defaults

- **Default section headline**: `{typography.h2}` (3vw at weight 600). Reserve `{typography.h1}` for chapter breaks and covers.
- **Default opening / cover display**: `{typography.display}` (8vw at weight 700).
- **Default body size**: `{typography.body}` (1.05vw at weight 500).
- **Default lead size**: `{typography.lead}` (1.45vw) when a paragraph is the single supporting block.
- **Default label size**: `{typography.label}` (0.7vw).
- **Default weight for any display element**: 700. **Default weight for body and labels**: 500.
- **Default tracking**: `-0.01em` to `-0.02em` on display and h1; `0.12em` on chrome labels; 0 on station labels.

When unsure, the canonical pairing is `{typography.h2}` (600) + one `{typography.lead}` (500) block, with a route legend in the corner. The narrow weight gap between heading and body is correct — Metro Map does not need heavy contrast because the diagram provides the visual drama.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every route network is an SVG polyline using only horizontal, vertical, and 45° segments.** No curves, no arcs, no arbitrary angles. This is the system's founding rule.
- **Maximum three route colors per slide.** A fourth route requires a design decision, not a color token.
- **Every interchange node is a white-filled circle with a colored ring** (`{components.interchange-node}`). Never a filled interchange, never a square interchange.
- **Every terminus is a larger filled circle** in the route color (`{components.terminus-node}`). Never hollow, never ringed.
- **Every diagram slide carries a route legend** (`{components.route-legend}`) in one corner — default top-right — pairing a colored dash with the route name.
- **Station dots carry labels** (`{components.station-label}`), rotated to match 45° segments. Labels are 1–3 words; longer text becomes a callout.
- **Process steps render as numbered stations** (`{components.step-node}`) along a line, not as free-floating boxes.
- **Chrome labels are Archivo 500 uppercase with at least 0.12em tracking.** Sentence-case chrome does not exist here.
- **Journey metaphors** ("2 stops to launch") are encouraged and always set with the numeral in `{typography.stat-value}` inside `{components.journey-chip}`.
- **Route colors never touch text.** The route tokens are line colors; ink and graphite are text colors.

### Typography Principles

The rhythm of Metro Map is **one family, three weights, tight headlines, tracked chrome**. Introducing a second Latin family (a serif, a mono) reads as a different system. Setting a body paragraph in Archivo 400 or 300 reads as a different system. The type must be quiet enough that a 45° route line is the loudest thing on the slide. Underline is not used. Bold is not used inside body text — emphasis comes from the diagram (a node, a route, a chip), not from weight.

## Layout

### Canvas System

The source template targets a fluid `100vw × 100vh` viewport with all sizes in `vw`/`vh`; under the Fixed-Stage Policy these translate directly into 1920×1080 stage coordinates. The deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `reveal-right`, `reveal-left`, `scale-in`) run per slide with stagger delays via `data-delay` attributes; route polylines may additionally draw in via `stroke-dashoffset` (see Responsive Behavior).

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding — tighter than the editorial templates because the diagram needs room, not air |
| `{spacing.pad-y}` | 5.5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4.5vh | Between the diagram plate and chrome, or between major sections |
| `{spacing.gap-md}` | 2.5vh | Between related elements inside a plate or panel |
| `{spacing.gap-sm}` | 1.2vh | Between tightly related elements (station dot and its label, dash and route name) |

### Chrome Frame

Most content slides carry a **chrome header** and **chrome foot**, each a `flex space-between` row of two Archivo-500 uppercase labels separated from the body by a 1px solid ink rule. The header left carries the deck title ("METRO DECK — LINE 01"), the header right carries the sheet number ("SHEET 03/12"). The foot replaces the plain rule with the 3px `{components.route-strip}` band, with a small caption beneath it. Cover, chapter-break, and closing slides suppress chrome entirely.

The **map plate** (`{components.map-plate}`) is the content stage: a cream-deep region with a 1px graphite border holding the route network. Chrome never enters the plate; the plate never leaves the page body.

## Depth and Elevation

### Flat Paper, No Elevation

The system uses **zero box-shadow declarations** on structural elements. Depth is created through three mechanisms:

1. **1px hairline rules in `{colors.ink}` and `{colors.graphite}`** — chrome rules, plate border, spine rules. The rule is the separator.
2. **The cream-deep plate fill** — the diagram region is distinguished by being one step darker than the slide surface, not by a shadow.
3. **The route network's own geometry** — lines crossing, nodes opening, the legend anchoring a corner. The diagram is its own depth.

### No Atmospheric Effects

There are no gradients in the body — the only gradient in the system is the decorative `{components.route-strip}` footer band, and it is a sequence of flat color stops, not a blend. No glows, no blurs, no grain, no textures. The map must read as printed wayfinding: crisp, flat, and honest about its geometry.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Map plate, chrome rules, panels, callout boxes — the system is square by default |
| 50% (circle) | Station dots, interchange nodes, terminus nodes, step nodes — every node is a true circle |
| 999px (pill) | Journey chip only |

The system is square-cornered except for circles and the single journey chip. Rounded rectangles (6px, 12px) do not exist — a rounded map reads as a dashboard, not a map.

### Border Weights

- **1px solid `{colors.ink}`** — chrome rules, spine rules, dividers.
- **1px solid `{colors.graphite}`** — map-plate border.
- **2px solid `{colors.ink}`** — step-node ring.
- **3px** — route-line stroke (`{components.route-line}`) and interchange-node ring.
- **22×3px** — the legend dash (width × height, in the route color).

There is no dashed border in the system; dashed lines are reserved for leader lines in callout layouts, drawn as SVG `stroke-dasharray`, never as CSS borders.

### Decorative Element Types

**Route line** — An SVG polyline (`{components.route-line}`) stroked at 3px with round caps and joins, filled `none`, built from only horizontal, vertical, and 45° segments. Coordinates are hand-authored; the 45° discipline means every diagonal changes x and y by equal pixel deltas.

**Interchange node** — A 14px white circle with a 3px route-colored ring (`{components.interchange-node}`). The white fill is `{colors.interchange-white}` — the system's single pure-white moment.

**Terminus node** — A 20px filled circle in the route color (`{components.terminus-node}`). The line ends here; nothing extends past a terminus.

**Station dot + label** — An 8px filled circle (`{components.station-dot}`) in the route color (or ink on monochrome slides) with an Archivo-500 label (`{components.station-label}`) beside it, rotated to match 45° segments via `transform: rotate(45deg)` on the label wrapper.

**Numbered step node** — A 34px white circle with a 2px ink ring (`{components.step-node}`) containing an Archivo-700 numeral. Rendered as a flex-centered circle; used for process steps, roadmap stages, and numbered org layers.

**Route legend** — A corner block (`{components.route-legend}`) with a 22×3px colored dash and the route name in `{typography.route-title}` (Archivo 700). Defaults to the top-right corner; one legend per slide, listing only the routes present.

**Journey chip** — An ink-filled pill (`{components.journey-chip}`) with cream text, `border-radius: 999px`, padding `0.4em 1.2em`, carrying a metaphor numeral in `{typography.stat-value}` (Archivo 700, 4.5vw) plus a phrase in Archivo 500. The system's only pill.

**Map plate** — The cream-deep diagram surface (`{components.map-plate}`) with a 1px graphite border and `{spacing.gap-md}` internal padding. All routes and nodes live inside it.

**Route strip (footer)** — A 3px full-width band (`{components.route-strip}`) built from a `linear-gradient(90deg, …)` of up to three flat route-color stops, mirroring the routes on the slide. The footer is the page's line map.

**Chrome label** — Archivo 500 uppercase with 0.12em tracking, colored `{colors.graphite}`. Used for deck titles, sheet numbers, kickers, and legend headings.

## Do's and Don'ts

### Do
- Put a diagram on every content slide. The default slide is a map plate with a route network; prose-only slides are the exception, not the rule.
- Build every route as an SVG polyline with only horizontal, vertical, and 45° segments. The 45° discipline is the system's identity.
- Limit each slide to 2–3 route colors, drawn from `{colors.route-blue}`, `{colors.route-red}`, `{colors.route-green}` first.
- Use the interchange node (white fill + colored ring) whenever two routes meet or a process handoff happens.
- End every line with a terminus — a larger filled circle in the route color.
- Add a route legend to every diagram slide, top-right by default.
- Render process steps as numbered stations along a line, not as floating boxes.
- Keep the cream surface, ink text, and graphite secondary text on every slide. Color means a line runs here.
- Use journey metaphors ("2 stops to launch") with the numeral in `{typography.stat-value}`.
- Keep station labels to 1–3 words and rotate them to match 45° segments.

### Don't
- Don't use curves, arcs, or arbitrary angles in a route network. A curved line is a different design system.
- Don't use more than three route colors per slide. The palette has five tokens for cross-deck variety, not per-slide variety.
- Don't color text with a route color. Route tokens are line colors; ink and graphite are text colors.
- Don't fill an interchange node — interchanges are white with a colored ring.
- Don't make a terminus hollow or ringed — terminuses are filled.
- Don't use rounded rectangles for plates, panels, or callouts. Square corners are the structural default.
- Don't introduce a second Latin typeface. Archivo carries everything; a serif or mono breaks the single-voice discipline.
- Don't float paragraphs beside the diagram as a wall of text. Attach explanations to the network — labels, legends, chips.
- Don't drop the route legend. One legend per diagram slide, always.
- Don't use box-shadow on any element. The system is flat paper.
- Don't use the route-strip gradient with colors that don't appear on the slide — the footer is a line map, not a decoration.

## Responsive Behavior

The source template is viewport-fluid by design; under the Fixed-Stage Policy those `vw`/`vh` proportions become fixed 1920×1080 stage coordinates, and the stage scales as one unit. Do not add breakpoints or reflow content for mobile — letterbox or pillarbox instead.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (fade-up, fade-in, reveal-right, reveal-left, scale-in) with stagger delays via `data-delay="N"` where N maps to a discrete delay step (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Route polylines may additionally draw in on entrance via `stroke-dasharray`/`stroke-dashoffset` animation (set the dash to the path length, animate offset from length to 0 over ~1.2s). Use at most one drawing line per slide — the effect is strongest as a single moment.
- Elements with `[data-anim]` start invisible (opacity:0) and animate on `.is-active` — re-visiting a slide replays the entrance.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (Archivo 700) | Archivo | Noto Sans SC (思源黑体) | 700 or 900 (match the visual mass of Archivo 700) |
| Body / lead (Archivo 500) | Archivo | Noto Sans SC (思源黑体) | 400 or 500 |
| Chrome label (Archivo 500 uppercase) | Archivo | Noto Sans SC (思源黑体) | 500 (no uppercase, tracking 0 — see Aesthetic Notes) |
| Station label / legend (Archivo 500 / 700) | Archivo | Noto Sans SC (思源黑体) | 500 (stations), 700 (route names) |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"Archivo, Noto Sans SC, system-ui, sans-serif"`. Latin glyphs render in Archivo; CJK glyphs automatically fall through to Noto Sans SC. No per-language class needed. Mixed sentences like `流程还有 2 站就到发布` render in one logical run with the correct face per script — and keep numerals in Arabic (Archivo), which is the transit-map convention.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Archivo:wght@500;600;700&family=Noto+Sans+SC:wght@400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `使用 AI` not `使用AI`)
- One font per sentence

### Aesthetic Notes for This System

Metro Map's Latin voice is Archivo 700 display — a squared, upright geometric grotesque that echoes the 45° map geometry. **Noto Sans SC 700 matches that presence well**; for a heavier, poster-like Chinese display use 900. The tighter the Chinese headline (2–6 characters), the closer it lands to a station-name sign — which is exactly the system's register.

Chinese **station labels** are the system's biggest CJK translation challenge. Archivo-500 station labels were tuned for Latin's narrow glyphs; Chinese characters are square and roughly double the width at the same point size. Keep Chinese station labels to **2–4 characters** (e.g. 设计评审 not 设计方案与评审委员会) and drop the rotation on 45° segments when the label would collide with the line — a horizontal label is acceptable when rotation breaks legibility.

Chrome labels are Archivo 500 uppercase with 0.12em tracking; **CJK has no uppercase and should not be tracked.** Set Chinese chrome in Noto Sans SC 500, mixed case, letter-spacing 0. The "signage" voice in Chinese comes from the short phrasing and the graphite color, not from tracking.

Route names in the legend work fine in Chinese (`{colors.route-blue}` → 主干线). The `{components.journey-chip}` metaphor translates directly: `距发布还有 2 站` reads naturally in Chinese and preserves the transit joke. Keep the numeral in Archivo `{typography.stat-value}` even inside a Chinese sentence.

### Known CJK Gap

The 45° label rotation and the short-label discipline were tuned for Latin. Chinese station labels consume ~2× the horizontal space per character, so dense networks (6+ stations on one line) will collide in Chinese. Reduce station-label size by ~15% (0.95vw → 0.8vw) on Chinese-only diagrams, drop rotation on diagonals, or increase the plate's vertical padding to give labels room to wrap. Long Chinese route names (4+ characters) may need the legend dash and name to stack vertically — allow `{components.route-legend}` to wrap its text block.

## Iteration Guide

1. Any new slide background is `{colors.cream}`; any new diagram surface is the map plate (`{colors.cream-deep}` with a 1px `{colors.graphite}` border). Never introduce a dark or chromatic background.
2. Any new route is an SVG polyline with only horizontal, vertical, and 45° segments, stroked 3px round. Verify every diagonal changes x and y by equal pixel deltas.
3. Any new route color comes from the five route tokens, and the slide total stays at 2–3 routes. Default trio: blue, red, green.
4. Any new node is a true circle: 8px station dot, 14px interchange (white fill + 3px colored ring), 20px terminus (filled), 34px numbered step node.
5. Any new diagram slide carries a route legend in the top-right corner: 22×3px colored dash + route name in `{typography.route-title}`.
6. Any new headline uses Archivo mixed case — 700 for h1/display, 600 for h2. Never uppercase a headline.
7. Any new label, kicker, or chrome text uses Archivo 500 uppercase with 0.12em tracking, colored `{colors.graphite}`.
8. Any new callout uses a square-cornered bordered box; any new emphasis uses a journey chip — never a shadow, never a colored fill.
9. If a slide needs to explain a diagram, attach the explanation (label, leader line, chip) to the diagram. Don't add a prose column.
10. The footer route-strip mirrors the routes actually on the slide — update its `linear-gradient` stops whenever the slide's routes change.
11. Route colors never touch text. If text needs emphasis, change its weight or size, never its hue.

## Known Gaps

- Route polylines are hand-authored SVG `d`/`points` data — there is no data-binding layer that turns a node list into coordinates. Build coordinates manually; the 45° discipline means the math is simple but not automated.
- Label collision on dense networks (6+ stations per line) requires manual offsetting. The system has no automatic collision solver; place labels by hand and verify with a rendered screenshot.
- The route legend position is fixed at top-right by convention; slides with content in that corner must move it manually (bottom-left is the sanctioned alternative).
- The system is hue-distinguished for routes. On grayscale projectors or for color-blind viewers, the blue/red/green trio compresses; add route numerals to the legend (e.g. "1 — 主干线") as a fallback that costs nothing.
- The route-strip footer gradient must be hand-updated per slide to match its routes; it is decorative and easy to forget during iteration.
- `stroke-dashoffset` draw-in animation requires the path length known in advance (getTotalLength or a hard-coded value); on complex multi-segment lines it can glitch mid-animation — test on the final polyline before shipping.
- The system is deliberately diagram-first; content that is genuinely prose (a narrative paragraph, a long quote) has no natural home. That is a feature, not a bug — but it means prose-heavy requests should be steered to a different template.
