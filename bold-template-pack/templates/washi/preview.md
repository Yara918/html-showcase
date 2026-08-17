# Washi Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/washi/design.md`
- Preview card: `bold-template-pack/templates/washi/preview.md`

## Selection Metadata

- Slug: `washi`
- Tagline: Quiet Japanese minimalism: warm paper, ink brush strokes, generous emptiness, and vertical rhythm.
- Mood: serene, minimal, deliberate, natural
- Tone: calm, refined, understated
- Formality: high
- Density: low
- Scheme: light
- Best for: Minimalist brand decks, annual reflections, cultural content, traditional industries — anything wanting calm and breathing room (极简品牌/年度复盘/文化内容/东方审美向).
- Avoid for: Urgent, data-heavy, or loud operational walls.

## Visual Snapshot

A quiet system of Japanese minimalism — warm washi paper, sumi ink, and generous emptiness. Zen Old Mincho carries display and seal type; Zen Kaku Gothic New handles body copy; an enormous single character or a solid vermillion hanko seal provides the sole accent per slide. Extreme margins, thin 1px sumi rules, optional vertical text, and asymmetric balance make each slide a folio page rather than a presentation frame.

Every slide is a folio of warm washi paper `{colors.washi-paper}` at 1920×1080: content in the lower-left, emptiness in the upper-right, an enormous single character breathing behind at 6–8% ink opacity (or a solid vermillion hanko seal), Zen Old Mincho 700 headlines, weight-300 Kaku Gothic body, 1px sumi rules, and a subtle feTurbulence paper grain. One accent per slide — vermillion, moss, or a rare gold hairline — and nothing else.

## Preview Ingredients

- Palette: washi-paper #F5F1E6; paper-light #FAF7EF; paper-deep #EDE6D6; sumi-ink #1F1D1A; graphite #7A746A; graphite-light #A39C90; vermillion #B3402A; moss #6B6B5C; gold #A98F5F
- Typography: Zen Old Mincho; Zen Kaku Gothic New; Noto Serif SC / Noto Sans SC (CJK); {typography.display.fontFamily}
- Signature move: An enormous single kanji/Chinese character as a faint background graphic — `color-mix(in srgb, {colors.sumi-ink} 7%, {colors.washi-paper})` at 6–8% opacity ({components.ghost-kanji}).
- Signature move: A solid vermillion hanko seal — a square with a single white character in {colors.vermillion} ({components.hanko-seal}).
- Signature move: Optional vertical text runs with `writing-mode: vertical-rl` in the right margin ({components.vertical-text}).
- Signature move: Extreme margins (12vw) with asymmetric balance — content lower-left, emptiness upper-right — and thin 1px sumi rules ({components.sumi-rule}).
- Signature move: Subtle washi paper texture via inline SVG feTurbulence ({components.paper-texture}), and exactly one accent per slide.

## International / CJK Preview Note

- If the preview uses Chinese or other CJK text, keep CJK letter-spacing at 0, loosen line-height, and avoid uppercase transforms on CJK runs.
- Use the full `design.md` CJK section after selection for exact font pairings and script-specific adjustments.

## Preview Rules

- Build exactly one title slide at 1920x1080 inside the fixed-stage model.
- Preserve the palette, type roles, surface rhythm, and decorative vocabulary described above.
- Use the user's real title/subtitle/context; do not copy demo slide content.
- The rendered preview must look like a real first slide, not a template-selection card.
- Never place internal workflow text on the slide: no `preview`, `generated from`, `preview.md`, `template`, `preset`, `style option`, `Option A/B/C`, file names, paths, or source-doc labels.
- Never place the template name or slug on the slide itself; mention it only in the chat message.
- Never place user requirement notes such as desired vibe, audience, or internal-use labels on the slide unless the user explicitly wants those exact words in the deck.
- Use only real deck content for visible chrome: deck title, real section title, date, author, company, page number, or genuine content phrases from the user material.
- Do not read `template.html` for preview generation.
- Do not read other templates' `design.md` files.
- After the user picks this template for the full deck, read the full design doc before generating final slides.
