# Bauhaus Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/bauhaus/design.md`
- Preview card: `bold-template-pack/templates/bauhaus/preview.md`

## Selection Metadata

- Slug: `bauhaus`
- Tagline: Bauhaus poster language: primary-color circles and bars, geometric sans, strict asymmetric composition.
- Mood: geometric, bold, artful, playful-serious
- Tone: confident, graphic, modernist
- Formality: medium
- Density: medium
- Scheme: light
- Best for: Creative proposals, brand-concept decks, design pitches, cultural and art events, studio portfolios (创意方案/品牌概念/设计向提案/文化活动).
- Avoid for: Dense data documents or formal institutional decks.

## Visual Snapshot

A poster-language system in the Bauhaus tradition — primary-color circles, semicircles, triangles, and bars balanced against heavy geometric type on warm paper. Archivo Black carries every uppercase display headline; Inter handles body copy; Josefin Sans supplies a geometric voice for numerals and labels. Each slide is one strict asymmetric composition: content pushed to one side, a single dominant shape balancing the other.

Every slide is a 1920×1080 poster printed on warm paper `{colors.paper}`: one dominant geometric figure in a primary color (red, yellow, or blue) placed off-center, heavy uppercase Archivo Black headlines with tight tracking, 5px black rules, and huge outlined section numerals. Flat inks only — no shadows, no gradients — with the shape allowed to bleed off the frame like a real poster crop.

## Preview Ingredients

- Palette: paper #F2EFE9; paper-deep #E9E4D8; white #FFFFFF; black #141414; red #D0342C; yellow #EAB308; blue #1F4FA3; cyan #2AA7C9; graphite #5A5A55; graphite-light #8A8A82
- Typography: Archivo Black; Inter; Josefin Sans; Noto Sans SC (CJK); {typography.display.fontFamily}
- Signature move: One dominant geometric shape per slide — circle, semicircle, triangle, or bar — in a primary color, placed off-center ({components.shape-circle}).
- Signature move: Black 3–5px rules structuring headlines and foot bands ({components.rule-heavy}), with 1px hairlines for fine separation.
- Signature move: Uppercase tight-tracked display in Archivo Black ({typography.display}), sentence-case never.
- Signature move: Huge outlined section numerals via `-webkit-text-stroke: 2px {colors.black}` with transparent fill ({components.outlined-numeral}).
- Signature move: Strict asymmetric composition — content pushed to one side, the shape balancing the other; full-bleed color-field rectangles for high-contrast moments.

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
