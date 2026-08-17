---
version: alpha
name: Glass Panel
description: A frosted-glass design system: translucent panels float over a soft four-stop gradient field, and depth comes from blur, not from borders or ink weight. Sora display type, Inter body, and Space Grotesk labels sit on panels of rgba(255,255,255,0.55) glass with 1px white borders, 24px corner radii, and layered soft shadows. The register is calm, modern, airy, and premium — a screen-native aesthetic built for product walkthroughs, solution pitches, and onboarding explainers.

colors:
  field-blue: "#EAF2FF"
  field-violet: "#F3EEFF"
  field-pink: "#FFF0F2"
  field-mint: "#EAFCF4"
  glass-white: "rgba(255,255,255,0.55)"
  glass-border: "rgba(255,255,255,0.65)"
  ink: "#1E2430"
  graphite: "#5B6472"
  accent-indigo: "#4F46E5"
  accent-violet: "#8B5CF6"
  accent-cyan: "#06B6D4"

color-aliases:
  c-bg: field-blue
  c-bg-light: field-mint
  c-bg-cream: field-pink
  c-fg: ink
  c-fg-light: ink
  c-fg-2: graphite
  c-fg-3: graphite
  c-accent: accent-indigo
  c-border: glass-border
  c-border-light: glass-border

typography:
  display:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 6.5vw
    fontWeight: 700
    lineHeight: 1.05
    letterSpacing: -0.02em
  h1:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.2vw
    fontWeight: 600
    lineHeight: 1.1
    letterSpacing: -0.015em
  h2:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 2.8vw
    fontWeight: 600
    lineHeight: 1.2
  h3:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 1.8vw
    fontWeight: 600
    lineHeight: 1.3
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
    fontFamily: "Space Grotesk, Noto Sans SC, system-ui, sans-serif"
    fontSize: 0.75vw
    fontWeight: 500
    letterSpacing: 0.08em
    textTransform: uppercase
  stat-value:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.2vw
    fontWeight: 700
    lineHeight: 1.0
    letterSpacing: -0.02em
  hero-phrase:
    fontFamily: "Sora, Noto Sans SC, system-ui, sans-serif"
    fontSize: 4.8vw
    fontWeight: 700
    lineHeight: 1.08
    letterSpacing: -0.02em

spacing:
  pad-x: 6vw
  pad-y: 5vh
  gap-lg: 4.5vh
  gap-md: 2.5vh
  gap-sm: 1.4vh

canvas:
  width: 100vw
  height: 100vh

components:
  gradient-field:
    background: "radial-gradient(60% 55% at 15% 18%, {colors.field-blue}, transparent 70%), radial-gradient(55% 50% at 85% 20%, {colors.field-violet}, transparent 70%), radial-gradient(50% 50% at 80% 85%, {colors.field-pink}, transparent 70%), radial-gradient(55% 55% at 12% 88%, {colors.field-mint}, transparent 72%)"
    description: "The slide background: four large soft radial-gradient fields (blue, violet, pink, mint) laid over each other so no two slides read identically. No stops, no hard edges — the field is atmosphere."
  orb:
    width: "34vw"
    height: "34vw"
    borderRadius: 50%
    background: "radial-gradient(circle at 35% 35%, rgba(79,70,229,0.28), rgba(139,92,246,0.12) 55%, transparent 72%)"
    filter: "blur(40px)"
    description: "A large soft color orb drifting behind the panels. Orbs are pure light — radial gradient, heavy blur, never a solid disk. 2–3 per slide, positioned under panel gaps so blur shows through."
  glass-panel:
    background: "{colors.glass-white}"
    border: "1px solid {colors.glass-border}"
    borderRadius: 24px
    backdropFilter: "blur(18px)"
    WebkitBackdropFilter: "blur(18px)"
    boxShadow: "0 24px 48px -12px rgba(30,36,48,0.18), 0 8px 20px -8px rgba(30,36,48,0.10), inset 0 1px 0 rgba(255,255,255,0.6)"
    padding: "{spacing.gap-lg} {spacing.gap-md}"
    description: "The system's core surface: a 55%-white frosted panel with a 1px white border, 18–24px backdrop blur, and a three-layer shadow (soft drop, near drop, inner top highlight). Panels float; they never touch."
  glass-pill:
    background: "rgba(255,255,255,0.5)"
    border: "1px solid {colors.glass-border}"
    borderRadius: 999px
    padding: "0.4em 1.1em"
    fontFamily: "{typography.label.fontFamily}"
    fontSize: "{typography.label.fontSize}"
    letterSpacing: 0.08em
    textTransform: uppercase
    color: "{colors.graphite}"
    description: "Frosted pill badge for category labels, versions, and step numbers. The only pill shape in the system — pills are badges, never panels."
  stat-chip:
    background: "rgba(255,255,255,0.42)"
    border: "1px solid rgba(255,255,255,0.5)"
    borderRadius: 20px
    padding: "1.2vh 1.2vw"
    backdropFilter: "blur(12px)"
    description: "Frosted stat chip holding a Sora stat-value numeral and a small label. Chips sit on panels or directly on the gradient field; the lower blur (12px) keeps the numeral crisp."
  gradient-text:
    background: "linear-gradient(100deg, {colors.accent-indigo}, {colors.accent-violet} 55%, {colors.accent-cyan})"
    WebkitBackgroundClip: text
    backgroundClip: text
    color: "transparent"
    description: "Gradient-filled text via background-clip: text. Reserved for one hero phrase per slide — a key word, a product name, or a short claim. Never full sentences, never body copy."
  divider:
    height: 1px
    background: "rgba(255,255,255,0.6)"
    description: "1px white-glass divider at 60% opacity, used inside panels to separate a header band from content. Dividers are white light, not ink."
  icon-tile:
    width: "4.2vw"
    height: "4.2vw"
    borderRadius: 14px
    background: "rgba(255,255,255,0.6)"
    border: "1px solid rgba(255,255,255,0.7)"
    display: grid
    placeItems: center
    description: "Small frosted square tile holding an inline SVG icon. Tiles are the system's substitute for illustration — light-filled squares, 14px radius, 1px white border."
  glass-card:
    background: "rgba(255,255,255,0.5)"
    border: "1px solid {colors.glass-border}"
    borderRadius: 24px
    backdropFilter: "blur(20px)"
    padding: "3vh 2vw"
    description: "A taller glass panel variant for feature cards: a Sora h3 title, an Inter body block, and a small mono-free label row at the foot. Three cards in a row is the canonical arrangement."
  hero-phrase:
    fontFamily: "{typography.hero-phrase.fontFamily}"
    fontSize: "{typography.hero-phrase.fontSize}"
    fontWeight: 700
    letterSpacing: -0.02em
    description: "The one big phrase on a hero slide. The first key word is wrapped in a gradient-text span; the rest stays {colors.ink}."
---

## Fixed-Stage Policy

When this design system is used by the `html-showcase` skill, generate the final deck as a **fixed 1920×1080 stage** that scales uniformly to the browser viewport. The deck should preserve a 16:9 slide canvas on every screen, including phones; it may letterbox or pillarbox, but it should not reflow slide content for mobile.

This policy has higher priority than any source-template responsive behavior described later in this file. If a later section says the original template is viewport-fluid, treat that as source history only, not as the target generation model for `html-showcase`.

This policy applies even if the source template was originally implemented with viewport-fluid CSS such as `100vw`, `100vh`, `vw`, `vh`, or `clamp()`. Treat those values as design proportions to translate into 1920×1080 stage coordinates, not as live responsive rules in the generated deck.

Use `deck-stage.js` or an equivalent inline stage scaler for final output: render each slide at 1920×1080, scale the whole stage with one transform, and verify rendered screenshots for both text overflow and panel overlap.

## Overview

Glass Panel is a **frosted-glass system in the glassmorphism tradition**, built on a single material premise: surfaces are translucent, depth comes from blur, and light does the separating that ink does elsewhere. Panels of `rgba(255,255,255,0.55)` glass float over a soft four-stop gradient field — blue, violet, pink, mint — and everything about the system is tuned to keep that float believable: 1px white borders catch the light, 18–24px backdrop blur softens whatever drifts behind, and layered soft shadows give each panel just enough gravity to read as a real object hovering over the field.

The system is **screen-native by conviction**. Glass reads as a screen material — you can't print frosted blur, and you don't want to. This is why the brief's avoid-list is explicit: dense formal documents and print-like editorial belong to other templates; Glass Panel is for product walkthroughs, solution pitches, team and culture decks, and onboarding explainers — anything that wants a modern premium SaaS feel, where the deck itself should feel like the product it describes.

The typographic voice is a **two-weight Sora + Inter + Space Grotesk** stack. **Sora** at 600–700 carries display, headlines, and stat values — a geometric sans with a slight tech-modern personality, wide and friendly at large sizes, the voice of a polished product screen rather than a newspaper. **Inter** at 400 carries body copy, calm and neutral so the panels stay the protagonists. **Space Grotesk** at 500 carries labels in small caps — a quirky-but-clean geometric grotesque whose distinctive letterforms give the chrome a designed, not default, feel. The CJK fallback for all three is Noto Sans SC.

Color is **field-first and accent-light**. The gradient field (four pastel radial stops at 70–100% transparency) is the only background; panels are translucent white; ink (`{colors.ink}`) is a deep blue-slate for text; graphite handles secondary copy. The three accents — indigo (`{colors.accent-indigo}`), violet (`{colors.accent-violet}`), cyan (`{colors.accent-cyan}`) — exist in two places only: the gradient-text hero phrase and the orbs behind the panels. Accents never paint text at rest, never fill a button, never become a chart palette; they are light phenomena, not ink.

Density is deliberately **low-to-medium**. Glass needs air to blur; a slide where panels cover 80% of the field reads as fog, not glass. The system's rhythm is one large statement panel, two or three smaller feature cards, or a hero phrase with one frosted stat chip row — always with visible field between panels, always with orbs leaking through the gaps. When a deck needs a denser moment, it gets more panels, never more ink weight.

**Key Characteristics:**
- Frosted panels: `{colors.glass-white}` fill, 1px `{colors.glass-border}` border, `backdrop-filter: blur(18–24px)`, 24px corner radius, layered soft shadows with an inset top highlight.
- The background is a soft four-stop radial gradient field; 2–3 large blurred orbs drift behind panels.
- 24px corner radius is the structural default; 999px pills are badges only.
- Glass pill badges and frosted stat chips are the system's small surfaces.
- One hero phrase per slide can use gradient text (`background-clip: text`).
- Sora 600–700 display, Inter 400 body, Space Grotesk 500 labels.
- Dividers are 1px white glass at 60% — light, not ink.
- Density is low-medium: panels float with visible field between them.

## Colors

### Palette

| Token | Value | Role |
|---|---|---|
| `{colors.field-blue}` | #EAF2FF | First gradient field stop — cool blue light, usually the upper-left field |
| `{colors.field-violet}` | #F3EEFF | Second gradient field stop — lavender light, usually upper-right |
| `{colors.field-pink}` | #FFF0F2 | Third gradient field stop — blush light, usually lower-right |
| `{colors.field-mint}` | #EAFCF4 | Fourth gradient field stop — mint light, usually lower-left |
| `{colors.glass-white}` | rgba(255,255,255,0.55) | The panel fill — translucent white is the material, not a color |
| `{colors.glass-border}` | rgba(255,255,255,0.65) | The 1px panel border — catches light, defines the panel edge |
| `{colors.ink}` | #1E2430 | Text, headings, stat values — a deep blue-slate, never pure black |
| `{colors.graphite}` | #5B6472 | Secondary text, pill labels, captions |
| `{colors.accent-indigo}` | #4F46E5 | Gradient-text start, orb core, one accent moment per slide |
| `{colors.accent-violet}` | #8B5CF6 | Gradient-text mid, orb color |
| `{colors.accent-cyan}` | #06B6D4 | Gradient-text end, small accent details |

### Defaults

- **Default surface**: the `{components.gradient-field}` — never a flat color, never white. The field is the canvas.
- **Default panel fill**: `{colors.glass-white}` (55% white) with a 1px `{colors.glass-border}` border and 18–24px backdrop blur.
- **Default headline color**: `{colors.ink}` on glass. Headlines never sit directly on the raw field (see Typography Principles).
- **Default body text color**: `{colors.ink}`; secondary copy uses `{colors.graphite}`.
- **Default label color**: `{colors.graphite}` in Space Grotesk small caps.
- **Default divider color**: `rgba(255,255,255,0.6)` — white light, never ink.
- **Default accent usage**: one gradient-text phrase per slide; accent colors otherwise live only in orbs and small icon details.
- **Default radius**: 24px for panels and cards, 14px for icon tiles, 999px for pills, 20px for stat chips.

The system has no semantic color traffic (no green-for-ok, no red-for-warn). Accent colors are atmospheric, not informational; if a slide needs a semantic mark, it uses a pill badge with text, not a colored dot.

## Typography

### Font Family

The system loads four faces: **Sora** (weights 600, 700) carries display, headlines, and stat values; **Inter** (weight 400) carries body, lead, and captions; **Space Grotesk** (weight 500) carries labels, pills, and chrome in small caps; **Noto Sans SC** is the CJK fallback for all three.

The emotional register is deliberate:

- Sora reads as **modern, friendly, and slightly engineered** — wide geometric forms with confident apertures, the voice of a premium product screen. At 700 with -0.02em tracking it carries a hero phrase without shouting.
- Inter reads as **quiet and professional** at 400 — body copy on glass should disappear into legibility.
- Space Grotesk reads as **designed-but-relaxed** — its unusual letterforms (open a, distinctive g) make labels feel art-directed without becoming decorative. It is the system's small detail voice.

### Type Scale

| Token | Size | Family | Weight | Use |
|---|---|---|---|---|
| `{typography.display}` | 6.5vw | Sora | 700 | Title-slide display — set on a hero panel, never bare field |
| `{typography.hero-phrase}` | 4.8vw | Sora | 700 | One big phrase with a gradient-text key word |
| `{typography.h1}` | 4.2vw | Sora | 600 | Section-break headline on a panel |
| `{typography.stat-value}` | 4.2vw | Sora | 700 | Stat numeral inside a frosted stat chip |
| `{typography.h2}` | 2.8vw | Sora | 600 | Content-slide headline |
| `{typography.h3}` | 1.8vw | Sora | 600 | Feature-card title |
| `{typography.lead}` | 1.5vw | Inter | 400 | Lead paragraph |
| `{typography.body}` | 1.05vw | Inter | 400 | Body paragraph |
| `{typography.caption}` | 0.8vw | Inter | 400 | Caption, fine print |
| `{typography.label}` | 0.75vw | Space Grotesk | 500 | Pill label, chip label, chrome |

### Defaults

- **Default content-slide headline**: `{typography.h2}` (2.8vw Sora 600).
- **Default title-slide display**: `{typography.display}` (6.5vw Sora 700) — always inside a hero panel.
- **Default body size**: `{typography.body}` (1.05vw Inter 400).
- **Default label size**: `{typography.label}` (0.75vw Space Grotesk 500).
- **Default stat value**: `{typography.stat-value}` (4.2vw Sora 700) inside a `{components.stat-chip}`.

When unsure, the canonical pairing is a glass panel holding `{typography.h2}` + one `{typography.lead}` paragraph, with a `{typography.label}` pill above the headline.

### Signature Treatments

These treatments are **non-optional whenever the corresponding element type is used**:

- **Headlines and body text always sit on glass** — a panel, a card, or a chip — never directly on the raw gradient field. Bare text on the field is the system's most common failure mode (see Do's and Don'ts).
- **Every panel is frosted**: `backdrop-filter: blur(18–24px)` with a `-webkit-` prefix, a 1px `{colors.glass-border}` border, and the three-layer shadow (outer drop, near drop, inset top highlight).
- **Gradient text is used exactly once per slide**, on one hero phrase (`background: linear-gradient(100deg, indigo, violet 55%, cyan); -webkit-background-clip: text; color: transparent`). Never on full sentences, body copy, or labels.
- **Pills are badges**: the 999px radius is reserved for `{components.glass-pill}` labels and chips, never for panels or cards.
- **Stat values are Sora 700** inside frosted `{components.stat-chip}` surfaces.
- **Labels are Space Grotesk 500 in small caps** with 0.08em tracking — never Sora, never Inter.
- **Dividers are white light**: 1px `rgba(255,255,255,0.6)`, not ink.
- **Orbs are blurred light**: radial gradient + `filter: blur(40px)`, 2–3 per slide, positioned to peek through panel gaps.

### Typography Principles

The rhythm of Glass Panel is **Sora on glass + Inter body + Space Grotesk small caps**. Switching display to a serif reads as a different system. Setting labels in Sora reads as a different system. The glass material is part of the typography: type on a 55%-white panel over a pastel field has a soft luminance that flat-color systems don't — headlines should be ink-dark enough (`{colors.ink}`) to hold their edge against the frosted background. Bold is not used inside body text; weight contrast lives between the display scale and the body scale. Italics are not used.

## Layout

### Canvas System

The system targets the fixed 1920×1080 stage model described in the Fixed-Stage Policy above, expressed in the source as fluid `100vw × 100vh` proportions with all sizes in `vw`/`vh`. The deck is a horizontal flex strip with slide-to-slide transitions at 0.6s with a soft ease — slower than the grid systems, because glass needs a moment to settle.

### Padding and Gap Scale

| Token | Value | Use |
|---|---|---|
| `{spacing.pad-x}` | 6vw | Slide horizontal padding |
| `{spacing.pad-y}` | 5vh | Slide vertical padding |
| `{spacing.gap-lg}` | 4.5vh | Between major regions (hero panel → card row) |
| `{spacing.gap-md}` | 2.5vh | Between related elements; card-row gaps |
| `{spacing.gap-sm}` | 1.4vh | Between tightly related elements (label under numeral) |

The canonical hero slide stacks: pill badge, display headline (both on the hero panel), then a row of 2–3 stat chips *below* the panel — chips float on the field, half overlapping the panel's bottom edge, so the blur interaction between panel and chip is visible. Feature slides use a 3-column card row with `{spacing.gap-md}` gutters and visible field in the gaps.

### Chrome Frame

Content slides carry a **floating chrome**: a single glass pill in the top-left holding the deck code (e.g., `PRODUCT / 04`) and a text label in the top-right (page number). There is no rule band, no header bar — the chrome floats on the field the same way panels do. Title, hero, and closing slides suppress the top-right page number. The bottom-left may carry a small `{typography.caption}` date line directly on the field, in `{colors.graphite}`.

## Depth and Elevation

### The Layered Shadow

The system's elevation language is the **three-layer glass shadow** on every panel:

1. **Outer drop**: `0 24px 48px -12px rgba(30,36,48,0.18)` — the wide soft shadow that lifts the panel off the field.
2. **Near drop**: `0 8px 20px -8px rgba(30,36,48,0.10)` — the tight shadow that anchors the panel's edge.
3. **Inset top highlight**: `inset 0 1px 0 rgba(255,255,255,0.6)` — the light-catching top edge that makes the glass read as a material.

### Blur as Depth

`backdrop-filter: blur(18–24px)` on panels and `blur(12px)` on stat chips is the primary depth signal — it is the only thing that proves the panel is in front of the field. Orbs (`filter: blur(40px)`) sit *behind* panels, so their edges soften under the glass; panels never sit in front of a hard-edged orb. Stacking: field → orbs → panels → chips → text.

### No Ink Elevation

There are no solid fills, no borders heavier than 1px, no ink shadows, no outlines. A panel never separates from the field by darkness — only by blur, light border, and shadow.

## Shapes and Treatment

### Border Radius

| Value | Use |
|---|---|
| 24px | Panels and glass cards — the structural default |
| 20px | Frosted stat chips |
| 14px | Icon tiles |
| 999px (pill) | Glass pill badges only — never panels or cards |
| 50% (circle) | Orbs (blurred light, not visible disks) |

The 24px radius is the system's signature soft edge; it is what makes glass read as friendly rather than clinical. The hierarchy 24 → 20 → 14 → pill keeps every surface shape-coded by its role.

### Border Weights

- **1px solid `{colors.glass-border}`** (65% white) — every panel, card, and pill border.
- **1px solid rgba(255,255,255,0.5)** — stat-chip borders (slightly fainter, smaller surface).
- **1px solid rgba(255,255,255,0.7)** — icon-tile borders (slightly brighter, decorative surface).
- No ink borders exist anywhere. If a slide needs a strong separator, it gets a white-glass divider, not an ink rule.

### Decorative Element Types

**Gradient field** — `{components.gradient-field}`: four radial-gradient stops (blue, violet, pink, mint) at 70–100% transparency over the slide. Stop positions vary slightly per slide so the atmosphere shifts.

**Soft orbs** — `{components.orb}`: 34vw radial-gradient circles (indigo core fading to violet at 55% and transparent at 72%) with `filter: blur(40px)`. 2–3 per slide, tucked under panel edges so blur shows through panel gaps.

**Glass panel** — `{components.glass-panel}`: the core surface. 55%-white fill, 1px white border, 24px radius, 18–24px backdrop blur, three-layer shadow, `{spacing.gap-lg}` × `{spacing.gap-md}` padding.

**Glass pill badge** — `{components.glass-pill}`: 999px-radius frosted label with a Space Grotesk small-cap string. Used for category labels, step numbers (`STEP 01`), and version codes.

**Frosted stat chip** — `{components.stat-chip}`: 20px-radius, 42%-white fill, 12px blur chip holding a Sora stat numeral and a small label. Chips float on the field and may half-overlap panel edges.

**Gradient-text hero phrase** — `{components.gradient-text}` + `{components.hero-phrase}`: one phrase per slide where a key word is gradient-filled via `background-clip: text`. The gradient runs indigo → violet → cyan at 100deg.

**Icon tile** — `{components.icon-tile}`: 4.2vw frosted square with a 14px radius and a 1px white border, holding an inline SVG icon. The system's substitute for illustration.

**White-glass divider** — `{components.divider}`: 1px at 60% white, used inside panels to separate a title band from content.

**Feature card row** — `{components.glass-card}`: three 24px-radius glass cards in a row, each with a Sora h3 title, an Inter body block, and a label row at the foot.

## Do's and Don'ts

### Do
- Keep the gradient field as the background on every slide; the field is the canvas.
- Put every headline and body block on glass — a panel, a card, or a chip. Bare text on the field is a failure.
- Frost every panel with `backdrop-filter: blur(18–24px)` (with `-webkit-` prefix), a 1px white border, and the three-layer shadow.
- Use the 24px radius for panels, 20px for stat chips, 14px for icon tiles, 999px for pills.
- Use exactly one gradient-text phrase per slide, on a hero key word.
- Set labels in Space Grotesk 500 small caps with 0.08em tracking.
- Keep orbs blurred (`blur(40px)`), few (2–3), and positioned behind panel edges.
- Use white-glass dividers (1px, 60% white) for separation inside panels.
- Let field show between panels — glass needs air to blur.

### Don't
- Don't place text directly on the raw gradient field. Without glass behind it, type loses the system's depth contract.
- Don't use ink borders, ink dividers, or ink shadows. Separation is white light and blur.
- Don't use the pill radius for panels or cards — pills are badges only.
- Don't gradient-fill more than one phrase per slide, and never gradient-fill body copy or labels.
- Don't use accent colors as text color at rest, as button fills, or as a chart palette. Accents are light phenomena.
- Don't stack more than three panels deep, and don't let panels cover more than ~70% of the field — a fogged slide reads as broken glass.
- Don't use heavy blur on stat chips — 12px keeps numerals crisp; 18–24px is for panels.
- Don't use serif display type, italic, or bold body emphasis. The three-face stack is fixed.
- Don't use hard-edged orbs or solid-color disks — orbs are blurred light only.

## Responsive Behavior

The source template is viewport-fluid by design (all sizes in `vw`/`vh`), but per the Fixed-Stage Policy the `html-showcase` output is a fixed 1920×1080 stage scaled uniformly to the viewport — no reflow, no breakpoints, letterboxing or pillarboxing only.

### Presenter Behavior
- Standard keyboard navigation: arrows, space, Home, End.
- Touch swipe for mobile.
- Mouse wheel with debounce to prevent multi-skip.
- Slide-to-slide transitions at 0.6s with a soft `cubic-bezier(0.3, 0.7, 0.3, 1)` ease.
- Entrance animations are soft and few: `fade-up` (14px, 0.6s) for panels and `blur-in` (opacity 0→1 with `filter: blur(6px)` → `blur(0)`, 0.7s) for the hero phrase and stat chips. Both run on slide entrance via `data-anim` with staggered `data-delay` steps.
- Elements with `[data-anim]` start at opacity 0 and animate on `.is-active`; revisiting a slide replays the entrance.
- The gradient field and orbs are static per slide; they do not animate, so the blur budget stays stable on low-end projectors.

### Print Behavior
The template does not declare a `@media print` rule. Browser-driven PDF export captures only the active slide; multi-slide export requires manual navigation per slide. Note that printed or rasterized PDF export flattens `backdrop-filter` — panels will render with their `rgba(255,255,255,0.55)` fill but lose the blur interaction, so a print review of this template always looks flatter than the live deck.

## CJK & International Content

### Recommended Chinese Pairing

| Role | Latin face | Chinese face | Weight |
|---|---|---|---|
| Display / headline / stat (Sora 600–700) | Sora | Noto Sans SC (思源黑体) | 700 (display), 600 (headlines) |
| Body / lead (Inter 400) | Inter | Noto Sans SC (思源黑体) | 400 |
| Label / pill / chrome (Space Grotesk 500) | Space Grotesk | Noto Sans SC | 500 |
| Numerals inside Chinese text | Sora | Noto Sans SC | 700 for stat chips, 600 elsewhere |

### Mixed-Content Strategy

Strategy A — same `font-family` stack, Latin-first fallback. Each typographic token already lists `"Sora, Noto Sans SC, system-ui, sans-serif"` (or the Inter / Space Grotesk equivalents). Latin glyphs render in the Latin face; CJK glyphs automatically fall through to Noto Sans SC. No per-language class is needed. Mixed sentences like `产品已接入 200+ 客户` render in one logical run with the correct face per script.

### Loading

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Sora:wght@600;700&family=Inter:wght@400&family=Space+Grotesk:wght@500&family=Noto+Sans+SC:wght@300;400;500;700;900&display=swap" rel="stylesheet">
```

### Universal CJK Adjustments

- Line-height: body 1.75–1.85, display 1.15–1.25
- Letter-spacing: 0 on CJK (the -0.02em display tracking does not transfer)
- Text-transform: no uppercase on CJK
- Full-width punctuation （，。：；！？「」（））
- No period on display headlines (Chinese typography convention)
- Pangu spacing 盘古之白 (space between CJK and Latin: `接入 200+ 客户` not `接入200+客户`)
- One font per sentence

### Aesthetic Notes for This System

Glass Panel's defining trait is **Sora 700 display on frosted glass**. Noto Sans SC 700 is a strong CJK partner — its even stroke weight holds up under the 55%-white panel fill, where lighter CJK weights can feel washed out by the frosted backdrop. For hero phrases and display, use Noto Sans SC 700 (or 900 for a single emphasized display word); for headlines, 600. Avoid weights below 500 on glass: the blur over a pastel field eats the thin-stroke contrast that CJK glyphs need.

Space Grotesk's small-caps labels do not transfer to CJK — Chinese has no case. **Set Chinese pill labels and chrome in Noto Sans SC 500, mixed case, letter-spacing 0.** The "designed detail" register is carried by the pill's frosted surface and the small size, not by the typeface's quirks. If a pill is pure Latin (a version code like `V2.4`), keep Space Grotesk small caps as designed.

Gradient text (`background-clip: text`) works with CJK glyphs, but Chinese characters are stroke-dense and the indigo→violet→cyan sweep reads busier on them. **Limit gradient text to short phrases (2–4 characters) or a single key word**, and prefer gradient on Latin product names over Chinese claims. The frosted stat chips and pill badges behave identically in CJK.

### Known CJK Gap

Chinese characters are roughly square and ~15–20% wider than Latin at the same point size, and glass panels have fixed padding budgets. A 6.5vw Sora display line that fits a panel may wrap in Noto Sans SC at the same size. Reduce display and hero-phrase sizes by ~12% (6.5vw → 5.7vw) for pure-Chinese lines, or plan the hero panel taller for two lines. Panel padding should also step up one `{spacing.gap-sm}` when Chinese text is expected, because CJK line-height 1.75–1.85 consumes more vertical space than the 1.6 lead default. The `blur-in` entrance animation is unaffected — geometry, not glyphs.

## Iteration Guide

1. Any new slide starts from the gradient field (`{components.gradient-field}`) with 2–3 orbs behind the panel layer.
2. Any new headline goes on a glass panel (`{components.glass-panel}`) — never bare on the field.
3. Any new panel uses `{colors.glass-white}` fill, a 1px `{colors.glass-border}` border, 24px radius, 18–24px backdrop blur, and the three-layer shadow.
4. Any new label or badge is a glass pill (`{components.glass-pill}`) in Space Grotesk 500 small caps.
5. Any new stat uses `{typography.stat-value}` (Sora 700) inside a frosted stat chip (`{components.stat-chip}`, 20px radius, 12px blur).
6. Any new hero moment uses `{typography.hero-phrase}` with one gradient-text key word (`{components.gradient-text}`) — and verify it is the only gradient text on the slide.
7. Any new divider inside a panel is 1px white glass at 60% opacity.
8. Any new icon sits in a 14px-radius frosted icon tile.
9. Keep chrome to one floating pill top-left and a page number top-right.
10. Verify no panel covers more than ~70% of the field and no text sits on raw field.
11. When in doubt, add air, not ink: glass is a material that needs visible field to blur.

## Known Gaps

- `backdrop-filter` requires a modern browser and degrades silently: in older browsers or some rasterization paths, panels render as flat 55%-white rectangles with no blur. The generated deck should keep the `-webkit-` prefix and accept the flattened fallback; there is no graceful mid-ground.
- Orbs are static per slide with hand-placed positions; there is no animation or parallax layer, so a "drifting light" effect requires JS the source does not provide.
- The gradient-field stop positions are baked into the CSS; varying them per slide means duplicating the background declaration, which the source does not parameterize.
- The one-gradient-text-per-slide rule is a design discipline, not an enforced mechanism — the generator must remember to demote additional gradient spans to plain ink.
- The 55%-white panel fill assumes the four pastel field stops; on a slide where the field was replaced with a flat color, panels may read too gray. Do not replace the field.
- Stat chips half-overlapping panel edges rely on the chip's own backdrop blur; on low-end hardware the double-blur (panel + chip) can be expensive — keep chip counts to 3 per slide.
- The source template is named "Glass Panel" in the library; any historical names in source comments refer to the same system.
- Print and PDF export flatten all blur (see Responsive Behavior); a client reviewing a PDF will see a flatter system than the live deck, which should be flagged in the delivery notes.
