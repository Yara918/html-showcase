# Swiss Grid Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/swiss-grid/design.md`
- Preview card: `bold-template-pack/templates/swiss-grid/preview.md`

## Selection Metadata

- Slug: `swiss-grid`
- Tagline: Objective Swiss International Typography: a strict 12-column grid, grotesque sans, and a single signal-red accent.
- Mood: objective, precise, editorial, modernist
- Tone: clear, confident, neutral, systematic
- Formality: high
- Density: medium-high
- Scheme: light
- Best for: Operations reviews, process documentation, methodology decks, KPI definitions, quarterly reports, policy and standard explanations — anything that should read as rational, structured and trustworthy (运营周报/数据汇报/方法论/制度说明).
- Avoid for: Playful, warm, or story-led decks — the objective grid voice refuses decoration.

## Visual Snapshot

An objective Swiss International Typography system on cool paper (`{colors.paper}`), set in Archivo 700–800 display with tight negative tracking, Inter 400 body, and JetBrains Mono uppercase metadata. The layout is a strict 12-column grid with visible 1px hairline column rules on title slides — the grid itself is the ornament, drawn in 40% graphite-light so the machinery of the layout is on display.

The palette is rationed: paper, white, ink, two graphites, and a single signal-red accent (`{colors.signal-red}`) that appears exactly once per slide — as a kicker, an oversized index numeral, a short 44×2px underline rule, or one highlighted chart series. There are no shadows, no gradients, no rounded corners; separation comes from 1px ink hairlines and deliberate empty grid columns. The register is rational, editorial, and modernist: structure first, decoration refused.

## Preview Ingredients

- Palette: paper #F4F4F1; white #FFFFFF; ink #17171A; graphite #6E6E74; graphite-light #A3A3AA; signal-red #E63312; blue-gray #2E4A7A
- Typography: Archivo; Inter; JetBrains Mono; {typography.label.fontFamily}
- Signature move: A strict 12-column grid with visible hairline column rules on the title slide — the grid is drawn as 1px vertical lines at 40% {colors.graphite-light}.
- Signature move: Exactly one signal-red element per slide ({colors.signal-red}), used as a kicker, index numeral, 44×2px underline, or one chart series — never more.
- Signature move: Oversized graphite index numerals ({typography.index-num.fontFamily} at 6vw, weight 800) as the strongest non-accent graphic.
- Signature move: JetBrains Mono uppercase with 0.16em tracking for every kicker, tag, and figure caption; all text left-aligned and ragged-right.
- Signature move: Zero shadows, zero gradients, zero rounded corners — 1–2px hairlines and whitespace carry all separation.

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
