# Blueprint Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/blueprint/design.md`
- Preview card: `bold-template-pack/templates/blueprint/preview.md`

## Selection Metadata

- Slug: `blueprint`
- Tagline: Drafting-table blueprint: deep blue field, white grid lines, technical lettering, and corner registration marks.
- Mood: technical, precise, constructive, retro-future
- Tone: exact, confident, engineered
- Formality: medium-high
- Density: medium
- Scheme: dark
- Best for: Project blueprints, planning roadmaps, technical architecture, go-to-market plans — any "this is how it's built" deck (方案图纸/规划蓝图/技术架构/路线图).
- Avoid for: Soft brand storytelling.

## Visual Snapshot

A drafting-table blueprint rendered as a design system — a deep blue field, white grid lines, technical lettering, and corner registration marks. JetBrains Mono carries every word like stencil drafting lettering, with Inter 600 reserved for sheet headers; amber pencil annotations provide the one warm human touch. The system presents anything that is "how it's built" — plans, roadmaps, architecture, go-to-market — as a drawing on the table, precise, confident, and engineered.

Every slide is a sheet on a drafting table: a deep blue field with a layered major/minor grid that never turns off, ✚ registration crosses at all four corners, plan lines drawn as 2px SVG strokes, dimension lines with arrowheads and mono measurements, dashed leader lines to labels, a bordered title block (PROJECT / SCALE / DATE / REV) bottom-right, and amber pencil annotations where the thinking happened. Lines carry the weight; fills stay at 6% white; there are no shadows — only light, line weight, and the grid.

## Preview Ingredients

- Palette: blueprint #123C7E; blueprint-deep #0E2F5E; panel-blue #15468F; line-white #EAF2FB; line-dim #9DB8DC; pencil #FFB800; accent-red #FF5A4E; vignette #0A2144
- Typography: JetBrains Mono; Inter; Noto Sans SC; {typography.label.fontFamily}
- Signature move: Layered grid background — major 1cm + minor 1mm via two repeating-linear-gradients in white at low opacity ({components.grid-layer}).
- Signature move: ✚ registration crosses at all four corners ({colors.line-dim} at 70% opacity).
- Signature move: Dimension lines with arrowheads and mono measurements (↔ 120.0) in {typography.dimension}.
- Signature move: Dashed leader lines (stroke-dasharray) to labels ({colors.line-dim}).
- Signature move: Bordered title block bottom-right (PROJECT / SCALE / DATE / REV) in {typography.field-value}; amber pencil annotations ({colors.pencil}) for emphasis.

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
