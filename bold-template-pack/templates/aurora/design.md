---
version: alpha
name: Aurora
description: A cinematic dark-field design system built for big single statements. Layered radial-gradient blobs in teal, violet, magenta, amber, and blue drift over a near-black canvas, and oversized Unbounded display type renders in white with a faint glow. One or two statements per slide, small mono kickers, 1px glass hairline dividers, and gradient-filled numerals — no cards, no panels, no clutter. The system is for brand launches, annual strategy moments, keynote opens and closes, and vision statements that need to land as luminous and confident.

colors:
  base-ink: "#0B0F1E"
  aurora-teal: "#2DD4BF"
  aurora-violet: "#8B5CF6"
  aurora-magenta: "#EC4899"
  aurora-amber: "#F59E0B"
  aurora-blue: "#3B82F6"
  text-white: "#FFFFFF"
  text-dim: "rgba(255,255,255,0.72)"

color-aliases:
  c-bg: base-ink
  c-bg-light: base-ink
  c-bg-cream: base-ink
  c-fg: text-white
  c-fg-light: text-white
  c-fg-2: text-dim
  c-fg-3: text-dim
  c-accent: aurora-teal
  c-border: text-white
  c-border-light: text-white

typography:
  display:
    fontFamily: "Unbounded, Noto Sans SC, system-ui, sans-serif"
    fontSize: 12vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: -0.02em
  h1:
    fontFamily: "Unbounded, Noto Sans SC, system-ui, sans-serif"
    fontSize: 6vw
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.01em
  h2:
    fontFamily: "Unbounded, Noto Sans SC, system-ui, sans-serif"
    fontSize: 3.4vw
    fontWeight: 600
    lineHeight: 1.2
  h3:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 2vw
    fontWeight: 400
    lineHeight: 1.3
  lead:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.6vw
    fontWeight: 300
    lineHeight: 1.6
  body:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.1vw
    fontWeight: 300
    lineHeight: 1.7
  caption:
    fontFamily: "Inter, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.85vw
    fontWeight: 300
    lineHeight: 1.55
  label:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.75vw
    fontWeight: 400
    letterSpacing: 0.2em
    textTransform: uppercase
  kicker:
    fontFamily: "JetBrains Mono, Noto Sans SC, monospace"
    fontSize: 0.72vw
    fontWeight: 400
    letterSpacing: 0.24em
    textTransform: uppercase
  stat-value:
    fontFamily: "Unbounded, Noto Sans SC, system-ui, sans-serif"
    fontSize: 5.5vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: -0.01em

spacing:
  pad-x: 7vw
  pad-y: 6vh
  gap-lg: 5vh
  gap-md: 3vh
  gap-sm: 1.5vh

canvas:
  width: 100vw
  height: 100vh

components:
  aurora-bg:
    background: "{colors.base-ink}"
    description: "The near-black canvas. Every slide is #0B0F1E — a blue-tinted black that keeps the aurora stops luminous instead of neon-on-pure-black."
  orb:
    width: "46vw"
    height: "46vw"
    borderRadius: 50%
    background: "radial-gradient(circle at 40% 40%, rgba(45,212,191,0.55), rgba(139,92,246,0.25) 48%, transparent 72%)"
    filter: "blur(70px)"
    position: absolute
    description: "The aurora unit: a huge radial-gradient blob (55% opacity core fading to transparent at 72%) with 70px blur. 3–5 orbs per slide in teal, violet, magenta, amber, blue — the stops are the palette."
  glow-text:
    textShadow: "0 0 60px rgba(255,255,255,0.35), 0 0 140px rgba(139,92,246,0.25)"
    description: "The display glow: a tight white bloom plus a wide violet aura. Applied to display and h1 only — never to body copy."
  kicker:
    fontFamily: "{typography.kicker.fontFamily}"
    fontSize: "{typography.kicker.fontSize}"
    letterSpacing: 0.24em
    textTransform: uppercase
    color: "{colors.text-dim}"
    description: "Small mono kicker above a statement: 'BRAND LAUNCH — 2025'. Tracked wide, dim, and quiet — the whisper before the shout."
  glass-divider:
    width: "100%"
    height: 1px
    background: "rgba(255,255,255,0.2)"
    description: "1px glass hairline at 20% white. The only rule in the system — used once per slide to separate the statement from the meta line."
  gradient-num:
    fontFamily: "{typography.stat-value.fontFamily}"
    fontSize: "{typography.stat-value.fontSize}"
    fontWeight: 700
    background: "linear-gradient(120deg, {colors.aurora-teal}, {colors.aurora-violet} 45%, {colors.aurora-magenta} 80%, {colors.aurora-amber})"
    WebkitBackgroundClip: text
    backgroundClip: text
    color: transparent
    description: "Gradient-filled numerals via background-clip: text. For year marks (2025), scale figures, or the chapter numeral — the one place the aurora palette becomes type."
  statement:
    maxWidth: "72vw"
    description: "The statement block: a kicker, one display or h1 line (or two), and nothing else. One or two statements max per slide; the rest is the aurora."
  meta-line:
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.2em
    textTransform: uppercase
    color: "{colors.text-dim}"
    description: "The single mono meta line under the glass divider — page number, date, or a one-line note. One meta line per slide, never more."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Aurora is a **cinematic dark-field system** built on one commitment: the canvas is the message, and the canvas is aurora light on near-black. Layered radial-gradient blobs in teal, violet, magenta, amber, and blue drift over `#0B0F1E` — a blue-tinted black chosen so the stops glow like atmospheric light rather than neon paint — and onto that field the system places the smallest possible amount of type: one or two statements per slide, set in oversized Unbounded display type in white with a faint glow. The register is confident, aspirational, and expressive; the density is deliberately low; there are no cards, no panels, no charts, no bullet lists. When Aurora is chosen, the deck is committing to moments, not documents.

The typographic voice is **Unbounded for the statement, Inter for the whisper, JetBrains Mono for the code**. **Unbounded** at weights 600–800 is a display-only face — wide, high-contrast, unmistakably designed — the kind of letterform that reads as a brand mark before it reads as a word. It appears only in display, h1, h2, and the gradient numerals; it is never body copy. **Inter** at weights 300–400 carries the rare lead paragraph and any fine print, light enough to stay in the background. **JetBrains Mono** at weight 400 carries the kickers and meta lines in wide-tracked uppercase — the system's quiet operational voice, always dim (`rgba(255,255,255,0.72)`), always small, always the counterweight to the shouting display.

Color is **light, not ink**. The five aurora stops — teal `{colors.aurora-teal}`, violet `{colors.aurora-violet}`, magenta `{colors.aurora-magenta}`, amber `{colors.aurora-amber}`, blue `{colors.aurora-blue}` — exist in two forms only: as blurred background orbs (the atmosphere) and as the gradient fill of numerals (the one place light becomes type). Text at rest is always white or dim; no statement text is ever set in a stop color. This separation is the system's core discipline: the aurora glows *behind* the words and *inside* the numerals, but it never competes with the words as ink.

The system's restraint is its drama. Every slide answers the same three questions — what is the one statement, where does the aurora sit, what is the single meta line — and everything else is omitted. A 12vw display line with a faint glow over a violet-magenta field reads as a brand moment precisely because there is nothing else on the slide. When a deck needs density, Aurora is the wrong system; when it needs a launch, an opening, or a closing, Aurora is the reason the deck exists.

**Key Characteristics:**
- Near-black canvas `{colors.base-ink}` with 3–5 large blurred radial-gradient orbs in the five aurora stops.
- 10–13vw white Unbounded display type (default 12vw) with a two-layer glow (white bloom + violet aura).
- One or two statements max per slide; no cards, no panels, no charts.
- Small mono kickers at 0.24em tracking, dim white.
- Numerals set in gradient-filled text (teal → violet → magenta → amber).
- 1px glass hairline dividers at 20% white — the only rule in the system.
- Inter 300–400 for the rare lead or body moment; mono for all meta.
- Text at rest is white or dim; the aurora palette never paints statement text.

## Colors

### Palette

| Token | Value | Role |
|---|---|---|
| `{colors.base-ink}` | #0B0F1E | The canvas — blue-tinted near-black that makes the aurora stops luminous |
| `{colors.aurora-teal}` | #2DD4BF | Aurora stop — the cool light, usually the dominant upper orb |
| `{colors.aurora-violet}` | #8B5CF6 | Aurora stop — the atmospheric mid-light, also the glow aura color |
| `{colors.aurora-magenta}` | #EC4899 | Aurora stop — the hot light, usually a lower orb |
| `{colors.aurora-amber}` | #F59E0B | Aurora stop — the rare warm accent, one small orb or gradient tail |
| `{colors.aurora-blue}` | #3B82F6 | Aurora stop — the deep light, often blended under violet |
| `{colors.text-white}` | #FFFFFF | Every statement, headline, and numeral at rest |
| `{colors.text-dim}` | rgba(255,255,255,0.72) | Kickers, meta lines, lead text — the quiet voice |

### Defaults

- **Default background**: `{colors.base-ink}` on every slide. There is no light slide, no alternative canvas.
- **Default statement color**: `{colors.text-white}` — white, never a stop color, never dim. A statement in dim or in teal reads as a different system.
- **Default kicker / meta color**: `{colors.text-dim}` — the whisper voice.
- **Default aurora distribution**: 3–5 orbs per slide; teal and violet are the workhorses, magenta appears on roughly half of slides, amber is rare (once per deck is a reasonable budget), blue blends under violet.
- **Default glow**: the two-layer `{components.glow-text}` shadow on display and h1 only.
- **Default rule**: one 1px glass hairline (`rgba(255,255,255,0.2)`) per slide, separating the statement from the meta line.
- **Default numeral treatment**: `{components.gradient-num}` — the only place the aurora palette becomes type.

The system has no semantic colors. There is no green-for-ok, no red-for-alert; the stops are atmospheric and their arrangement is compositional, not informational.

## Typography

### Font Family

The system loads four faces: **Unbounded** (weights 600, 700, 800) carries display, h1, h2, and numerals; **Inter** (weights 300, 400) carries lead, body, and captions; **JetBrains Mono** (weight 400) carries kickers and meta lines in wide-tracked uppercase; **Noto Sans SC** is the CJK fallback for all three.

The emotional register is deliberate:

- Unbounded reads as **cinematic and unmistakably designed** — wide letterforms with hard contrast, the face of film titles and brand systems, not documents. At 12vw with a glow, a single word becomes a visual event.
- Inter at 300 reads as **almost weightless** — a lead paragraph on an Aurora slide should feel like a caption in a film, present but secondary.
- JetBrains Mono reads as **instrumental and technical** — kickers and meta lines are the system's control-room voice, dim and wide-tracked, telling you what moment you're in without competing with it.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 12vw | Unbounded | 700 | The statement — one line, one idea (10–13vw range) |
| `{typography.h1}` | 6vw | Unbounded | 600 | Secondary statement or two-line statement split |
| `{typography.stat-value}` | 5.5vw | Unbounded | 700 | Gradient-filled numeral — year, scale, chapter mark |
| `{typography.h2}` | 3.4vw | Unbounded | 600 | Section-mark headline (rare on this system) |
| `{typography.h3}` | 2vw | Inter | 400 | Sub-line under a statement, if any |
| `{typography.lead}` | 1.6vw | Inter | 300 | The single lead paragraph, if any |
| `{typography.body}` | 1.1vw | Inter | 300 | Rare body text |
| `{typography.caption}` | 0.85vw | Inter | 300 | Fine print |
| `{typography.label}` | 0.75vw | JetBrains Mono | 400 | Meta lines, mono chrome |
| `{typography.kicker}` | 0.72vw | JetBrains Mono | 400 | The whisper above the statement |

### Defaults

- **Default statement**: `{typography.display}` (12vw Unbounded 700) with the glow. One line if the phrase fits; two lines maximum.
- **Default kicker**: `{typography.kicker}` (0.72vw mono, 0.24em tracking, dim).
- **Default numeral**: `{typography.stat-value}` (5.5vw Unbounded 700) in gradient fill.
- **Default lead**: `{typography.lead}` (1.6vw Inter 300) — only when a single supporting sentence is genuinely needed.
- **Default meta line**: `{typography.label}` (0.75vw mono, 0.2em tracking, dim).

When unsure, the canonical Aurora slide is: kicker, one 12vw display statement, one 1px glass divider, one meta line. Nothing else.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Every statement is white `{colors.text-white}` Unbounded with the two-layer glow.** Dim, gradient, or stop-colored statement text is a different system.
- **Kickers and meta lines are JetBrains Mono uppercase at 0.2–0.24em tracking in `{colors.text-dim}`.** Mono in sentence case does not exist here.
- **Numerals are gradient-filled** (`background: linear-gradient(120deg, teal, violet 45%, magenta 80%, amber); background-clip: text; color: transparent`). A numeral in plain white reads as a missed opportunity.
- **One or two statements max per slide.** Three statements is a different system.
- **One glass hairline divider per slide** — `rgba(255,255,255,0.2)`, 1px. No other rules exist.
- **The aurora palette never paints text at rest.** Stops live in orbs and gradient numerals only.
- **No cards, no panels, no borders around content.** Type floats on the field.

### Typography Principles

The rhythm of Aurora is **12vw Unbounded statement + dim mono whisper**. Switching the statement to Inter reads as a different system. Setting the kicker in Unbounded reads as a different system. The glow is part of the type: `text-shadow: 0 0 60px rgba(255,255,255,0.35), 0 0 140px rgba(139,92,246,0.25)` gives display a bloom that white-on-black alone lacks — but it must never be applied to body copy, where it would smear legibility. Italics are not used. Bold exists only as the display weight. Emphasis is achieved by making a thing bigger and letting the aurora sit behind it, never by color or decoration on the text itself.

## Layout

### Canvas System

The system targets the fixed 1920×1080 stage model described in the Fixed-Stage Policy above, expressed in the source as fluid `100vw × 100vh` proportions with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.8s with a slow cinematic ease — Aurora moves like a film cut, not a presentation advance.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 7vw | Slide horizontal padding — statements never touch the edges |
| `{spacing.pad-y}` | 6vh | Slide vertical padding |
| `{spacing.gap-lg}` | 5vh | Between statement block and the glass divider |
| `{spacing.gap-md}` | 3vh | Between kicker and statement, and divider and meta line |
| `{spacing.gap-sm}` | 1.5vh | Tight groupings |

Statements are left-anchored at `{spacing.pad-x}` and capped at 72vw (`{components.statement}`) so a 12vw line leaves the right third of the canvas to the aurora. A centered statement is permitted only for a single short display line on a title or closing slide — and never for body or meta.

### Chrome Frame

There is no chrome band. The only recurring furniture is the **meta line** (`{components.meta-line}`): a single dim mono line under the glass divider, holding the page number, a date, or a one-line note. One meta line per slide, bottom area, left-aligned. Title slides may drop the meta line entirely; closing slides usually keep only the page number.

## Depth and Elevation

### The Aurora as Depth

Depth in Aurora is **atmospheric, not architectural**. There are three layers and no more:

1. **The base canvas** — `{colors.base-ink}` at the back.
2. **The orbs** — 3–5 radial-gradient blobs (`{components.orb}`, 46vw, 55% core opacity fading to transparent at 72%, `filter: blur(70px)`) sitting on the canvas. They overlap and blend at their blurred edges; the field reads as continuous light, not discrete circles.
3. **The type layer** — statements, kickers, numerals, and the meta line on top, with the glow shadow as the type's own light.

### Glow as Elevation

The two-layer `text-shadow` is the system's only elevation tool: a tight white bloom (60px, 35%) plus a wide violet aura (140px, 25%). It lifts display type off the field the way a drop shadow lifts a panel in a light system — but here the light source is the type itself.

### No Architectural Depth

There are no panels, no cards, no borders, no drop shadows on shapes (the only shadow is the glow on type), no gradients on shapes (orbs are radial light, not fills). Nothing on an Aurora slide is elevated except the words.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 50% (circle) | Orbs — though blurred to invisibility as discrete shapes |
| 0px / 999px | None — no cards, no pills, no buttons, no cornered surfaces at all |

Aurora has **no structural shapes**. The only geometry on a slide is type, the glass divider, and the orbs. Any card, pill, tile, or button is a foreign object and must not be introduced.

### Border Weights

- **1px rgba(255,255,255,0.2)** — the single glass hairline divider. It is the only border-like element in the system.

### Decorative Element Types

**Aurora orbs** — `{components.orb}`: 46vw radial-gradient circles in the five stops, `filter: blur(70px)`, positioned absolutely with hand-placed coordinates per slide (e.g., teal upper-left at 55% opacity, violet right-center at 40%, magenta lower-right at 45%, amber small at 30%). The orb arrangement is the composition.

**Glow display statement** — `{components.glow-text}` + `{typography.display}`: one white Unbounded line at 10–13vw with the two-layer glow, left-anchored, capped at 72vw.

**Mono kicker** — `{components.kicker}`: 0.72vw JetBrains Mono uppercase at 0.24em tracking, dim white, sitting `{spacing.gap-md}` above the statement.

**Gradient numeral** — `{components.gradient-num}`: 5.5vw Unbounded 700 filled with the teal → violet → magenta → amber linear gradient via `background-clip: text`. Used for years (`2025`), scale figures, and chapter numerals.

**Glass hairline divider** — `{components.glass-divider}`: the 1px 20%-white rule between statement and meta line. One per slide.

**Meta line** — `{components.meta-line}`: the single dim mono line under the divider — page number, date, or note.

## Do's and Don'ts

### Do
- Keep the near-black canvas (`{colors.base-ink}`) on every slide.
- Build the aurora from 3–5 blurred radial-gradient orbs in the five stops; let them overlap and blend.
- Set the statement in Unbounded 700 at 10–13vw, white, with the two-layer glow.
- Use exactly one or two statements per slide.
- Set kickers and meta lines in JetBrains Mono uppercase at 0.2–0.24em tracking, dim white.
- Fill numerals with the aurora gradient via `background-clip: text`.
- Use one 1px glass hairline divider per slide.
- Leave the right third of the canvas to the aurora.
- Keep text at rest white or dim — never stop-colored.

### Don't
- Don't add cards, panels, pills, buttons, or charts. Aurora has no shapes and no containers.
- Don't set statement text in a stop color, in dim, or in a gradient. Statements are white.
- Don't use more than two statements per slide, and never use body copy as a statement.
- Don't use more than one meta line or more than one divider per slide.
- Don't apply the glow to body copy, kickers, or meta — the glow is display-only.
- Don't use hard-edged orbs, solid-color disks, or unblurred gradients — the aurora must read as atmospheric light.
- Don't use a light slide, a second canvas color, or a frame/border around the stage.
- Don't use serif type, italics, underlines, or bullet lists. None of them exist here.
- Don't set a numeral in plain white when a gradient numeral is the signature treatment.
- Don't center statements except a single short title/closing line.

## Responsive Behavior

The source template is viewport-fluid by design (all sizes in `vw`/`vh`), but per the Fixed-Stage Policy the `html-showcase` output is a fixed 1920×1080 stage scaled uniformly to the viewport — no reflow, no breakpoints, letterboxing or pillarboxing only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions at 0.8s with a slow cinematic `cubic-bezier(0.3, 0.5, 0.3, 1)` ease.
- Entrance animations are cinematic and few: `glow-in` (opacity 0→1 with `filter: blur(8px)` → `blur(0)`, 0.9s) for statements, and `fade-up` (16px, 0.7s) for kickers and meta. Both run on slide entrance via `data-anim` with staggered `data-delay` steps.
- Elements with `[data-anim]` start at opacity 0 and animate on `.is-active`; revisiting a slide replays the entrance.
- Orbs are static per slide; they do not drift (see Known Gaps).

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export captures only the active slide; multi-slide export requires manual navigation per slide. The glow and the blurred orbs partially flatten in PDF rasterization — printed Aurora reads darker and flatter than the live deck, which is acceptable for a cinema system but should be flagged in delivery notes.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / statement (Unbounded 700) | Unbounded | Noto Sans SC (思源黑体) | 900 (see Aesthetic Notes) |
| Secondary statement / h2 (Unbounded 600) | Unbounded | Noto Sans SC (思源黑体) | 700 |
| Lead / body (Inter 300–400) | Inter | Noto Sans SC (思源黑体) | 400 (body), 300 (lead) |
| Kicker / meta (JetBrains Mono) | JetBrains Mono | Noto Sans SC | 400 (do not force monospace on CJK; see Aesthetic Notes) |
| Numerals (Unbounded 700) | Unbounded | Noto Sans SC | 900 for 5.5vw gradient numerals |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"Unbounded, Noto Sans SC, system-ui, sans-serif"` (or the Inter / JetBrains Mono equivalents). Latin glyphs render in the Latin face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed statements like `迈向 2025 的新篇章` render in one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Unbounded:wght@600;700;800&family=Inter:wght@300;400&family=JetBrains+Mono:wght@400&family=Noto+Sans+SC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK (the -0.02em display tracking does not transfer)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `迈向 2025` not `迈向2025`)
- One font per sentence

### Aesthetic Notes for This System

Aurora's defining trait is **12vw Unbounded white display with a glow**. Noto Sans SC 900 is the only weight that can carry that statement register — Unbounded's wide, high-contrast forms have enormous visual mass, and Chinese glyphs need the heaviest available weight (900) to hold the same presence on a 12vw line. Do not set Chinese statements below 700; lighter weights read as anemic against the aurora.

The wide-tracked mono kicker does not transfer to CJK — Chinese has no uppercase and no monospace tradition in this register. **Set Chinese kickers and meta lines in Noto Sans SC 500, mixed case, letter-spacing 0.** The whisper register is carried by the dim color and small size. Pure-Latin kickers (`BRAND LAUNCH — 2025`) stay fully mono as designed.

Gradient numerals via `background-clip: text` work with Chinese characters, but stroke-dense glyphs break up the teal→violet→magenta→amber sweep. **Keep gradient fill on Latin digits and short Latin words only**; a Chinese character set in the aurora gradient reads as muddy. Chinese statements stay white; the gradient belongs to numbers.

The glow shadow applies unchanged to CJK display — `text-shadow` is script-agnostic. But because Chinese glyphs are denser, the white bloom (60px at 35%) can pool inside tight strokes; prefer the tighter bloom (`0 0 40px rgba(255,255,255,0.3)`) for pure-Chinese statements.

### Known CJK Gap

Chinese characters are square and ~15–20% wider than Latin at the same point size, and the statement cap is 72vw. A 12vw Unbounded English statement ("We Build The Future") may need only 40vw, but a six-character Chinese statement at 12vw Noto Sans SC 900 already exceeds the cap and wraps — which breaks the one-line statement contract. Reduce Chinese display to 9–10vw (12vw → 9.5vw) or shorten to four characters when the statement must sit on one line. The gradient numeral treatment is unaffected (digits are Latin). The dim kicker at 0.24em tracking cannot apply to Chinese — reset to 0 and rely on size and color.

## Iteration Guide

1. Any new slide starts from the near-black canvas (`{colors.base-ink}`).
2. Any new slide gets 3–5 aurora orbs (`{components.orb}`) in the five stops — teal and violet dominant, magenta on half the slides, amber rare, blue under violet. Hand-place them so no orb's bright core sits under the statement.
3. Any new statement is white Unbounded 700 at 10–13vw with the glow (`{components.glow-text}`), capped at 72vw, left-anchored. One or two statements max.
4. Any new kicker is JetBrains Mono uppercase at 0.24em tracking in `{colors.text-dim}`.
5. Any new numeral is gradient-filled (`{components.gradient-num}`) — teal → violet → magenta → amber.
6. Any new divider is the 1px `rgba(255,255,255,0.2)` glass hairline — one per slide.
7. Any new meta is one dim mono line under the divider.
8. Keep text at rest white or dim; verify no statement text carries a stop color.
9. Verify no cards, panels, pills, buttons, or charts were introduced.
10. When in doubt, remove an element: Aurora is a system that gets better with less.

## Known Gaps

- Orbs are static per slide with hand-placed coordinates; the source provides no drift or parallax animation, so a "living aurora" requires JS that the template does not ship.
- The `background-clip: text` gradient numeral needs the `-webkit-` prefix in most engines and silently degrades to solid color where unsupported — the generated deck should keep the prefix and accept a flat fallback.
- The glow is a fixed two-layer shadow; there is no intensity token for adjusting glow on projector vs. screen, so a low-contrast projector may need a one-off shadow reduction in the generated deck.
- The 12vw display default sits at the top of the 10–13vw range; longer statements must be hand-fitted (reduced size or two lines), and the 72vw cap is a design rule, not an enforced mechanism.
- The amber stop has no dedicated component and no frequency rule enforcement; it is easy to overuse amber and shift the field from cool-luminous to warm-garish.
- The source template is named "Aurora" in the library; any historical names in source comments refer to the same system.
- Print and PDF export flatten orbs and glow (see Responsive Behavior); the printed artifact is darker and flatter than the live deck by design, but delivery notes should state this.
