---
version: alpha
name: Ticker Console (Green Phosphor CRT)
description: A nocturnal terminal system rendered as a vintage green-phosphor CRT. VT323 pixel-readout type and JetBrains Mono body carry every line of text; a scanline overlay, phosphor glow, and a blinking block cursor reproduce the hardware texture of an aging system console. The palette is one green phosphor family on a near-black screen, with exactly two signal colors — amber for warnings, red for errors — and nothing else.

colors:
  phosphor: "#4AF626"
  phosphor-bright: "#B8FFA8"
  phosphor-dim: "#1E5C2E"
  phosphor-faint: "#3B8F4E"
  screen: "#050B06"
  screen-edge: "#0A140C"
  screen-panel: "#09150B"
  amber: "#FFB000"
  red: "#FF3B30"

color-aliases:
  c-bg: screen
  c-bg-light: screen-edge
  c-bg-cream: screen-panel
  c-fg: phosphor
  c-fg-light: phosphor-bright
  c-fg-2: phosphor-dim
  c-fg-3: phosphor-faint
  c-accent: phosphor
  c-border: phosphor-dim
  c-border-light: phosphor-faint

typography:
  display:
    fontFamily: "VT323, Noto Sans SC, monospace"
    fontSize: 8vw
    fontWeight: 400
    lineHeight: 0.95
    letterSpacing: 0.02em
  h1:
    fontFamily: "VT323, Noto Sans SC, monospace"
    fontSize: 4.5vw
    fontWeight: 400
    lineHeight: 1.05
    letterSpacing: 0.02em
  h2:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 2.1vw
    fontWeight: 500
    lineHeight: 1.25
  h3:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.45vw
    fontWeight: 400
    lineHeight: 1.35
  lead:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.28vw
    fontWeight: 400
    lineHeight: 1.6
  body:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 1.05vw
    fontWeight: 400
    lineHeight: 1.7
  caption:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.82vw
    fontWeight: 400
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.72vw
    fontWeight: 400
    letterSpacing: 0.1em
    textTransform: uppercase
  stat-value:
    fontFamily: "VT323, Noto Sans SC, monospace"
    fontSize: 6vw
    fontWeight: 400
    lineHeight: 1.0
    letterSpacing: 0.02em
  ticker:
    fontFamily: "VT323, Noto Sans SC, monospace"
    fontSize: 2.6vw
    fontWeight: 400
    letterSpacing: 0.12em
    textTransform: uppercase
  boot-log:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.9vw
    fontWeight: 400
    lineHeight: 1.5

spacing:
  pad-x: 6vw
  pad-y: 5vh
  gap-lg: 5vh
  gap-md: 3vh
  gap-sm: 1.5vh

canvas:
  width: 100vw
  height: 100vh

components:
  scanline-overlay:
    background: "repeating-linear-gradient(0deg, transparent 0 2px, rgba(0, 0, 0, 0.18) 2px 4px)"
    pointerEvents: none
    description: "The system's signature hardware texture: a repeating-linear-gradient of 2px transparent / 2px dark bands laid over the entire slide with pointer-events: none."
  vignette:
    background: "radial-gradient(ellipse at center, transparent 55%, rgba(0, 0, 0, 0.55) 100%)"
    pointerEvents: none
    description: "CRT corner falloff — a radial-gradient that darkens the four edges of the screen, simulating the curved-glass vignette of a real monitor."
  phosphor-glow:
    textShadow: "0 0 8px rgba(74, 246, 38, 0.6), 0 0 24px rgba(74, 246, 38, 0.25)"
    description: "Two-layer phosphor text-shadow — a tight 8px bloom plus a wide 24px halo in translucent green. Reserved for display, h1, and stat-value only."
  cursor-block:
    content: "▊"
    color: "{colors.phosphor}"
    animation: "blink 1.1s steps(1) infinite"
    description: "A blinking solid block cursor ('▊') emitted by ::after on the active typed line; the animation uses steps(1) so it snaps on and off like hardware, never fades."
  prompt-prefix:
    content: "> "
    color: "{colors.phosphor-bright}"
    fontFamily: "{typography.body.fontFamily}"
    description: "The '> ' prompt prefix that opens every command or action line; rendered bright phosphor so input reads louder than output."
  timestamp:
    color: "{colors.phosphor-dim}"
    fontFamily: "{typography.label.fontFamily}"
    description: "A bracketed [HH:MM:SS] timestamp in dim phosphor mono that precedes every log line and status entry."
  status-pill:
    border: "1px solid {colors.phosphor-dim}"
    padding: "0.25em 0.7em"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    textTransform: uppercase
    description: "Bordered mono uppercase pill for status words; filled variants use amber for WARN and red for ERR — the only two fill colors that exist."
  terminal-window:
    background: "{colors.screen-panel}"
    border: "1px solid {colors.phosphor-dim}"
    borderRadius: 4px
    description: "A bordered panel styled as a terminal window with a title bar carrying three 8px square LED dots in phosphor-dim."
  progress-bar:
    background: "{colors.screen-panel}"
    border: "1px solid {colors.phosphor-dim}"
    description: "Segmented block progress bar made of 8px squares; the filled segments are phosphor-bright and the track has no rounded corners."
  boot-sequence:
    fontFamily: "{typography.boot-log.fontFamily}"
    color: "{colors.phosphor-dim}"
    description: "Dim mono boot lines that narrate startup, one line per row, each led by a bracketed timestamp."
  ticker-marquee:
    background: "{colors.screen-edge}"
    fontFamily: "{typography.ticker.fontFamily}"
    color: "{colors.phosphor}"
    description: "A full-width scrolling ticker band of uppercase VT323 text tracked at 0.12em, animating horizontally on a loop."
  signal-dot:
    width: 8px
    height: 8px
    borderRadius: 2px
    background: "{colors.phosphor}"
    description: "A small square status indicator; the amber and red variants carry the only chromatic status signal in the system."
  blocky-bar:
    background: "{colors.phosphor}"
    description: "Vertical bar chart column with square corners and a 1px transparent gap between columns; the highlighted bar is phosphor-bright."
  img-placeholder:
    border: "1px solid {colors.phosphor-dim}"
    background: "{colors.screen-panel}"
    color: "{colors.phosphor-faint}"
    fontFamily: "{typography.label.fontFamily}"
    description: "A bordered panel showing a dim mono label such as [IMG NOT FOUND] until real imagery is dropped in."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Ticker Console treats the deck as a piece of surviving hardware: a green-phosphor CRT that has been left running in a machine room for thirty years and is still printing the system log. The design premise is not "retro styling applied to a presentation" but a strict material fiction — every slide is a screen state, every headline is a readout, every paragraph is a log entry, and the browser is the glass. That fiction is what makes the system coherent: once you accept that the slide is a terminal, the uppercase headlines, the bracketed `[HH:MM:SS]` timestamps, the blinking block cursor, and the `> ` prompt prefixes stop being decoration and become the only honest typography available.

The color system is one phosphor family plus two signal colors. Green is the state of normal operation, and it exists in four brightness steps: bright `{colors.phosphor-bright}` for highlights and active input, `{colors.phosphor}` for primary text, `{colors.phosphor-dim}` for secondary text and borders, and `{colors.phosphor-faint}` for metadata that should barely register. Amber means WARN, red means ERR, and nothing else is ever colored. There is no blue, no purple, no white. A slide that introduces a fourth hue has broken the machine's illusion — real consoles don't get new colors, they get new brightness levels.

Depth works the way a real CRT works: not through shadows, but through brightness layers and screen curvature. The background is near-black `{colors.screen}`; inset panels sit one step lighter at `{colors.screen-panel}`; the bezel chrome and ticker band sit at `{colors.screen-edge}`. A 1px `{colors.phosphor-dim}` border separates windows, exactly like a terminal's text-mode window borders. The two "effects" in the system — scanlines and the corner vignette — are not decoration but hardware simulation: the raster lines and the curved-glass falloff that every phosphor display physically had. They apply to every slide without exception.

**Density philosophy: medium, but disciplined.** Terminals are dense by nature — that is their charm — yet a real CRT was dim and slightly blurry, so dense screens only stay legible because of a strict brightness hierarchy. Body and log text stay in dim phosphor; only the active line, the headline, and the cursor sit at full brightness. Every log entry is terse. If a slide needs more than a screenful of text, cut it — a terminal scrolls, a slide does not.

**Key Characteristics:**
- Every slide is a full-bleed screen in `{colors.screen}` with the scanline overlay and vignette applied; the hardware texture is never optional.
- VT323 carries all display, headline, stat, and ticker text; JetBrains Mono carries every body, log, label, and chrome element.
- Every Latin headline is uppercase. Body copy is terse sentence case, like real log output.
- `{components.timestamp}` brackets — `[HH:MM:SS]` in dim phosphor — lead every log line, boot line, and status entry.
- `{components.prompt-prefix}` — `> ` in bright phosphor — opens every command or action line.
- `{components.cursor-block}` — a blinking `▊` — sits after the last typed line of each interactive-looking slide.
- Status words are pills: green for OK, `{colors.amber}` for WARN, `{colors.red}` for ERR. Nothing else is ever amber or red.
- The `{components.ticker-marquee}` band at the bottom of content slides scrolls a continuous uppercase message.

## Colors

### Palette

| Token | Hex | Role |
|---|---|---|
| `{colors.phosphor}` | #4AF626 | Primary text and the system's identity color — the green of a lit P1 phosphor |
| `{colors.phosphor-bright}` | #B8FFA8 | Highlight text, prompt prefixes, active selection, filled progress segments |
| `{colors.phosphor-dim}` | #1E5C2E | Secondary text, timestamps, boot lines, all 1px borders |
| `{colors.phosphor-faint}` | #3B8F4E | Tertiary metadata, placeholders, disabled states — barely-there green |
| `{colors.screen}` | #050B06 | Default background — near-black with a green cast, never pure black |
| `{colors.screen-edge}` | #0A140C | Bezel chrome: ticker band, bottom status bar, outer frame |
| `{colors.screen-panel}` | #09150B | Inset surface: terminal windows, panels, chart tracks |
| `{colors.amber}` | #FFB000 | WARN only. Warning banners, warning pills, warning icon |
| `{colors.red}` | #FF3B30 | ERR only. Error banners, error pills, failed-state icons |

### Defaults

- **Default surface background**: `{colors.screen}`. Every slide is a full-bleed screen; there is no "card on a page" layout.
- **Default primary text color**: `{colors.phosphor}`. Headlines and primary copy are always full-brightness phosphor green.
- **Default body text color**: `{colors.phosphor}` for active lines; `{colors.phosphor-dim}` for log and secondary copy. Dim is the resting state of body text, brightness is the emphasis.
- **Default label / metadata color**: `{colors.phosphor-faint}` — chrome labels and placeholder text sit at the lowest brightness step.
- **Default border color**: `{colors.phosphor-dim}` — every window border, every rule, every panel edge.
- **Default accent color**: `{colors.phosphor}` — the accent is brightness, not hue.
- **Default warning color**: `{colors.amber}` — reserved for WARN.
- **Default error color**: `{colors.red}` — reserved for ERR.

### Semantic Notes

The green family carries the whole informational hierarchy through brightness: bright > primary > dim > faint. Amber and red are the only two chromatic exceptions in the entire system and they are semantically locked — amber may only mark a warning, red may only mark an error. A slide that uses amber for a decorative highlight has misused the system. Note also that `{colors.screen}` is a green-tinted near-black, not neutral `#000`; keep that cast — it is what makes the whole screen read as a lit phosphor tube rather than a dark web page.

## Typography

### Font Family

The system loads three faces: **VT323** (weight 400 only) for every display, headline, stat, and ticker moment; **JetBrains Mono** (weights 400, 500) for every body, log, label, and chrome element; and **Noto Sans SC** as the CJK fallback behind both.

The division is strict and physical. VT323 is a bitmap-flavored pixel font that replicates the blocky readouts of early terminals — it is the voice of the *machine announcing something*. JetBrains Mono is a contemporary, carefully drawn monospace built for sustained reading — it is the voice of the *log text you actually read*. A body paragraph in VT323 would be unreadable at length; a headline in JetBrains Mono would lose the readout character of the system entirely.

- VT323 reads as **hardware, readout, alphanumeric display** — counters, titles, ticker text, boot banners.
- JetBrains Mono reads as **log, ledger, documentation** — body copy, lists, tables, labels, timestamps.
- Noto Sans SC is the Chinese fallback; it is never used for Latin (see the CJK section — VT323 must never render Chinese).

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 8vw | VT323 | 400 | Cover or boot-screen hero readout — large, bright, glowing |
| `{typography.h1}` | 4.5vw | VT323 | 400 | Chapter or section-break headline |
| `{typography.h2}` | 2.1vw | JetBrains Mono | 500 | Content-slide headline — the only weight-500 moment in the system |
| `{typography.stat-value}` | 6vw | VT323 | 400 | Large numerical readout inside a stat block |
| `{typography.ticker}` | 2.6vw | VT323 | 400 | Scrolling ticker band text, uppercase, tracked 0.12em |
| `{typography.h3}` | 1.45vw | JetBrains Mono | 400 | Sub-headline, window title, panel heading |
| `{typography.lead}` | 1.28vw | JetBrains Mono | 400 | Lead paragraph or a large log entry |
| `{typography.body}` | 1.05vw | JetBrains Mono | 400 | Body paragraph, log lines, table content |
| `{typography.boot-log}` | 0.9vw | JetBrains Mono | 400 | Dim boot-sequence lines and dense system output |
| `{typography.caption}` | 0.82vw | JetBrains Mono | 400 | Source note, fine print, axis labels |
| `{typography.label}` | 0.72vw | JetBrains Mono | 400 | Kicker, chrome label, status word, timestamp — uppercase, tracked 0.1em |

### Defaults

- **Default section headline**: `{typography.h2}` (2.1vw at weight 500). This is the standard content-slide headline; `{typography.h1}` is reserved for chapter breaks and boot screens.
- **Default cover display**: `{typography.display}` (8vw at weight 400).
- **Default body size**: `{typography.body}` (1.05vw at weight 400).
- **Default label / chrome size**: `{typography.label}` (0.72vw).
- **Default stat readout**: `{typography.stat-value}` (6vw at weight 400).

When unsure, the canonical pairing is `{typography.h2}` for the headline plus one terse paragraph at `{typography.body}` — and, if the slide claims interactivity, a blinking cursor after the last line.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every Latin display, h1, h2, ticker, and label element is uppercase.** VT323 at sentence case reads as a broken font; headlines and labels are always caps.
- **Every timestamp is bracketed and dim**: `[HH:MM:SS]` in JetBrains Mono colored `{colors.phosphor-dim}`, placed before the line it annotates.
- **Every prompt or command line begins with `> `** in `{colors.phosphor-bright}` via `::before`.
- **The active typed line carries the blinking block cursor** (`{components.cursor-block}`) via `::after` — one cursor per slide maximum, always on the last interactive-looking line.
- **Status words are uppercase pills**: `OK` in green, `WARN` in `{colors.amber}`, `ERR` in `{colors.red}`. These are the only pill colors.
- **The phosphor glow applies only to display, h1, and stat-value text.** Body and log text never glow — a glowing paragraph is illegible on a real tube.
- **No italics anywhere.** A CRT terminal does not italicize; emphasis is done with brightness (bright text) or with `[WARN]`-style prefixes.
- **No underlines.** Links and key terms are marked with `{colors.phosphor-bright}` color, never an underline.
- **List markers are terminal-style**: `-`, `*`, or `[x]` in mono — never round bullets, never checks.

### Typography Principles

The rhythm of Ticker Console is **VT323 readouts + JetBrains Mono logs + brightness hierarchy**. Switching body text to a proportional sans (Inter, Helvetica) reads as a different system — the mono width is what makes the log fiction hold. Putting VT323 at body size reads as broken. Setting a headline in a heavier sans reads as a web banner, not a console. Every face has exactly one job.

## Layout

### Canvas System

The system targets a full-bleed `100vw × 100vh` screen. There is no page, no card, no rounded app shell — the slide *is* the glass. All sizes are `vw`/`vh`; the deck is a horizontal flex strip with slide-to-slide transitions at 0.9s with a smooth easing curve. Entrance animations (`fade-up`, `fade-in`, `boot-in`, `scan-reveal`) are available with stagger delays via `data-delay` attributes and run on each slide entrance.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding — tighter than the editorial templates, like a real console margin |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 5vh | Between major content sections and windows |
| `{spacing.gap-md}` | 3vh | Between related blocks within a window |
| `{spacing.gap-sm}` | 1.5vh | Between tightly related elements (a label and its value, a log line and its timestamp) |

### Chrome Frame

Content slides carry a **top status bar** and a **bottom status bar**. Each is a `flex space-between` row of two mono labels separated from the slide body by a 1px `{colors.phosphor-dim}` rule. The top bar shows a system identifier on the left and a live `[HH:MM:SS]` clock on the right. The bottom bar shows a build/version tag on the left and `PAGE n/m` on the right. Cover, boot, and closing slide types suppress the chrome entirely — they are "full-screen" moments. The `{components.ticker-marquee}` band sits directly above the bottom status bar on content slides.

### Window System

Content is organized into `{components.terminal-window}` panels: bordered rectangles in `{colors.screen-panel}` with a title bar (window name in mono uppercase + three 8px LED dots on the right). A slide typically holds one large window or a 2-column grid of two windows; three-window rows are allowed only for tight stat layouts. Windows never overlap and never float — they tile inside the 6vw gutter.

## Depth and Elevation

### No Shadows, Brightness Layers Only

The system uses **zero box-shadow elevation** on any structural element. The only shadows that exist are the phosphor text-glow (`{components.phosphor-glow}`) and the CRT vignette (`{components.vignette}`) — both are hardware simulations with a physical justification, not decoration. Depth is created through three mechanisms:

1. **Brightness layering** — the screen steps from `{colors.screen}` (background) to `{colors.screen-panel}` (inset windows) to `{colors.screen-edge}` (bezel chrome). A panel is "closer" because it is lighter, exactly like a real tube.
2. **1px `{colors.phosphor-dim}` borders** — every window, panel, chart track, and status bar is separated by a hairline green border.
3. **The scanline overlay** — `repeating-linear-gradient(0deg, transparent 0 2px, rgba(0,0,0,0.18) 2px 4px)` fixed over the whole slide at a z-index above content with `pointer-events: none`. It flattens the image like glass and is the single strongest depth cue in the system.

### No Atmospheric Effects

There are no gradients other than the two hardware textures (scanlines, vignette), no blur, no grain, no glassmorphism. The glow `text-shadow` is applied sparingly — display text only — and never stacked with other effects. A slide should never look "designed with filters"; it should look like a screen.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 0px | Every structural element — windows, panels, buttons, progress bars, chart columns, images |
| 4px | Terminal-window outer corners only (`{components.terminal-window}`) |
| 2px | Signal dots and LED indicators (`{components.signal-dot}`) |
| 999px (pill) | None — pills do not exist in a text-mode terminal |

The system is square-cornered. The 4px radius on terminal windows is the only soft edge and it exists to keep the window from reading as a sharp box inside a scanline texture. Everything else is 0px — a progress bar with rounded corners instantly reads as a modern web UI and breaks the fiction.

### Border Weights

- **1px solid `{colors.phosphor-dim}`** — the universal structural weight: window borders, chrome rules, chart tracks, table separators.
- **2px solid `{colors.phosphor-dim}`** — reserved for the *active* or *focused* window, the single place in the system where one panel is marked as current.
- There is no 3px+, no dashed border, no colored border. Selection and focus are signaled by border weight or by `{colors.phosphor-bright}` text, never by a new color.

### Decorative Element Types

**Scanline overlay** — A full-slide `repeating-linear-gradient(0deg, transparent 0 2px, rgba(0,0,0,0.18) 2px 4px)` at `position: fixed; inset: 0; pointer-events: none`. The single most important texture in the system; every slide carries it.

**CRT vignette** — A `radial-gradient(ellipse at center, transparent 55%, rgba(0,0,0,0.55) 100%)` overlaying the slide edges. Sits above the scanlines, below the chrome.

**Phosphor glow** — `text-shadow: 0 0 8px rgba(74,246,38,0.6), 0 0 24px rgba(74,246,38,0.25)` on display, h1, and stat-value text only. The wide 24px halo gives the "lit tube" bloom; the tight 8px layer keeps glyph edges crisp.

**Blinking block cursor** — A `::after` with `content: "▊"` and `animation: blink 1.1s steps(1) infinite`, where the keyframes toggle `opacity` between 1 and 0. The `steps(1)` timing is non-negotiable — a fading cursor is a web cursor, not a terminal cursor.

**Prompt prefix** — A `::before` with `content: "> "` in `{colors.phosphor-bright}`. Precedes command lines; the bright green marks the place where a human operator acts.

**Bracketed timestamp** — A `<span class="ts">[HH:MM:SS]</span>` in `{colors.phosphor-dim}` mono, inserted before log lines. The bracket glyphs are literal characters, not CSS borders.

**Status pill** — An inline-bordered label (`{components.status-pill}`) with uppercase mono text. Default: 1px `{colors.phosphor-dim}` border, `{colors.phosphor}` text. WARN variant: `{colors.amber}` fill with `{colors.screen}` text. ERR variant: `{colors.red}` fill with `{colors.screen}` text.

**Segmented progress bar** — A track in `{colors.screen-panel}` with a 1px `{colors.phosphor-dim}` border; the fill is a row of 8px `{colors.phosphor-bright}` squares with 2px gaps, built with `repeating-linear-gradient` or a flex row of spans. No rounding, no smooth gradient fill.

**Boot sequence** — A stacked block of `{components.boot-sequence}` lines, each `[HH:MM:SS] INIT OK`-shaped, in dim phosphor. Used on boot/cover-adjacent slides to narrate startup.

**Ticker marquee** — `{components.ticker-marquee}`: a full-width band in `{colors.screen-edge}` with uppercase VT323 text at `{typography.ticker}` size, scrolling via a `translateX` keyframe loop inside an `overflow: hidden` container.

**Signal dots** — Three 8px squares in the terminal-window title bar (red, amber, green — mimicking real console LEDs) plus single status dots in legends.

**Blocky bar chart** — Columns of `{components.blocky-bar}` with square corners and 1px transparent gaps, `{colors.phosphor}` fill, highlighted column in `{colors.phosphor-bright}`. The chart has a 1px `{colors.phosphor-dim}` baseline.

**Image placeholder** — A `{colors.screen-panel}` panel with a 1px `{colors.phosphor-dim}` border and a dim mono label like `[IMG NOT FOUND]` centered. Used until real imagery is dropped in.

## Do's and Don'ts

### Do
- Apply the scanline overlay and the vignette to every slide. The hardware texture is the system's identity, not an optional filter.
- Keep every headline, label, ticker, and status word uppercase in Latin text.
- Lead log lines, boot lines, and status entries with bracketed `[HH:MM:SS]` timestamps in `{colors.phosphor-dim}`.
- Open command lines with `> ` in `{colors.phosphor-bright}`.
- Put the blinking block cursor after the last typed line of an interactive-looking slide — one cursor per slide.
- Use brightness as the hierarchy tool: bright for active, primary for standard, dim for secondary, faint for metadata.
- Use `{colors.amber}` for warnings and `{colors.red}` for errors, and for nothing else.
- Keep body copy in JetBrains Mono at `{typography.body}` size. Terse log-style sentences read best.
- Use the 4px radius on terminal windows and 0px everywhere else.

### Don't
- Don't introduce a fourth hue. Blue, purple, orange, pink do not exist here; the accent is brightness.
- Don't render body text in VT323 — it is unreadable at length.
- Don't apply the phosphor glow to body or log text. Glowing paragraphs are illegible.
- Don't italicize anything. Terminals don't have italics; use brightness or `[WARN]` prefixes instead.
- Don't use drop shadows, rounded progress bars, or glassmorphism. They read as a modern web app, not a console.
- Don't use round bullets — list markers are `-`, `*`, or `[x]` in mono.
- Don't put amber or red on decorative elements — those colors are semantically locked to WARN and ERR.
- Don't add underlines; emphasis is bright green text.
- Don't let a slide exceed a screenful of text. A terminal scrolls; a slide does not — cut lines until it fits.
- Don't fake vendor logos or product names in the chrome. The system identifier in the top bar should be the deck's own title or a generic label.

## Responsive Behavior

The system is viewport-fluid by design, with all sizes in `vw`/`vh` so the composition renders at any 16:9 viewport without breakpoints; per the Fixed-Stage Policy, the generated deck renders at a fixed 1920×1080 stage scaled uniformly, and the `vw`/`vh` values are treated as design proportions only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions animate over 0.9s with a smooth easing curve.
- Each slide can declare entrance animations on individual elements via `data-anim` (`fade-up`, `fade-in`, `boot-in`, `scan-reveal`) with stagger delays via `data-delay="N"` mapped to discrete steps (0s, 0.08s, 0.18s, 0.3s, 0.44s, 0.6s, 0.78s, 0.96s).
- Elements with `[data-anim]` start at `opacity: 0` and animate on `.is-active`; re-visiting a slide replays the entrance.
- The ticker marquee runs continuously and is not tied to slide activation.

### Print Behavior
The template declares no `@media print` rule. Browser-driven PDF export will capture only the active slide; multi-slide export requires manual navigation per slide. Note that the scanline overlay and vignette are dark overlays — exporting to PDF will carry them unless they are suppressed for the export pass.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline (VT323) | VT323 | Noto Sans SC (思源黑体) | 700 (VT323 has no CJK glyphs; see Aesthetic Notes) |
| Body / lead / log (JetBrains Mono) | JetBrains Mono | Noto Sans SC (思源黑体) | 400 |
| Labels / status / chrome (JetBrains Mono) | JetBrains Mono | Noto Sans SC (思源黑体) | 500 |
| Ticker / readouts (VT323) | VT323 | Noto Sans SC (思源黑体) | 700 |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token lists `"VT323, Noto Sans SC, monospace"` or `"JetBrains Mono, Noto Sans SC, monospace"`. Latin glyphs render in the mono face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed sentences like `系统状态 OK · uptime 99.9%` render as one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=VT323&family=JetBrains+Mono:wght@400;500&family=Noto+Sans+SC:wght@300;400;500;700&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `系统状态 OK` not `系统状态OK`)
- One font per sentence

### Aesthetic Notes for This System

Ticker Console's defining trait is **VT323 — a pixel font with no CJK coverage.** Never render Chinese in VT323: its bitmap logic was designed around Latin counters and reads as visibly broken on Han characters. Chinese display text goes in **Noto Sans SC 700**, which at large sizes delivers the same blocky, confident "readout" presence that VT323 gives Latin — weight is the only way to match a pixel font's visual mass with a CJK face. For body and log text, Noto Sans SC 400 against JetBrains Mono 400 is the correct match; the log fiction is carried by the terse line structure and the mono-matching even rhythm, not by actual monospace.

The uppercase rule does not transfer to CJK — Chinese has no case, so "uppercase" in a mixed headline means the Latin segments are capped while the Chinese segments stay as written. The `[HH:MM:SS]` timestamp and the `> ` prompt are pure Latin and stay in JetBrains Mono even when the line around them is Chinese.

The blinking block cursor works identically with CJK — the `▊` block is script-agnostic and sits naturally after a Chinese sentence. Keep it.

### Known CJK Gap

Green-on-black at full saturation is the most contrast-heavy surface in the library, and Noto Sans SC glyphs are denser than mono Latin glyphs — the combination can push dim green Chinese text below comfortable readability. When body copy is Chinese, use `{colors.phosphor}` at weight 400 rather than `{colors.phosphor-dim}`. Chinese display headlines are also wider per character: reduce headline sizes by ~12% (VT323 8vw → Noto Sans SC 7vw) when the headline is pure Chinese, or accept an extra wrap as part of the log rhythm.

## Iteration Guide

1. Any new slide background is `{colors.screen}`, always with the scanline overlay and vignette applied on top.
2. Any new headline uses VT323 in uppercase at weight 400 — display (8vw), h1 (4.5vw), or stat-value (6vw). Never use a heavier weight; VT323 has only one.
3. Any new content headline uses `{typography.h2}` (JetBrains Mono, weight 500) — the single weight-500 moment in the system.
4. Any new body, list, or log text uses JetBrains Mono at `{typography.body}` size in `{colors.phosphor}` (active) or `{colors.phosphor-dim}` (resting).
5. Any new timestamp is `[HH:MM:SS]` in `{colors.phosphor-dim}`; any new command line is prefixed with `> ` in `{colors.phosphor-bright}`.
6. Any new status uses the pill vocabulary: `OK` green, `WARN` `{colors.amber}`, `ERR` `{colors.red}` — never another color.
7. Any new structural separation is a 1px solid `{colors.phosphor-dim}` rule; the active window may use 2px.
8. Any new panel is a `{components.terminal-window}` with a title bar and three LED dots; panels tile inside the 6vw gutter and never overlap.
9. Add the blinking block cursor to at most one line per slide — the last interactive-looking line.
10. If a slide runs long, cut lines. A terminal scrolls; a slide does not.

## Known Gaps

- VT323 has exactly one weight (400); all display hierarchy must come from size, brightness, and glow — never from faux-bold.
- The scanline overlay and vignette are dark overlays stacked above content; both need `pointer-events: none`, and both will appear in PDF export unless suppressed.
- The blinking cursor's `steps(1)` animation is time-based: a static screenshot captures it at an arbitrary on/off phase. Acceptable, but verify the cursor isn't invisible in the rendered preview.
- The `{colors.screen}` green-tinted near-black is easy to "correct" to neutral black during generation; doing so silently removes the tube glow that makes the palette coherent.
- JetBrains Mono weight 500 is the only semi-bold moment; if the font fails to load, the browser substitutes a heavier mono and the h2 hierarchy jumps — keep the loading `<link>` in the document head.
- The ticker marquee loops via CSS animation only; there is no data-binding layer, so the message is hard-coded per deck.
- The window title-bar LED dots are decorative and sit flush against the window's top border; on dense three-window layouts, verify they do not collide with window titles.

---

## Related

This is a standalone design system in the `html-showcase` template library. For other aesthetics in the same pack, see the `bauhaus`, `gallery-label`, `riso-print`, and `washi` design docs.
