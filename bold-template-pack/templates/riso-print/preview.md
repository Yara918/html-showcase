# Riso Print Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/riso-print/design.md`
- Preview card: `bold-template-pack/templates/riso-print/preview.md`

## Selection Metadata

- Slug: `riso-print`
- Tagline: Risograph printing: 2-3 ink colors, coarse halftone, misregistration offsets, and paper grain.
- Mood: tactile, handmade, vibrant, zine
- Tone: playful, direct, artful, indie
- Formality: low-medium
- Density: medium-high
- Scheme: light
- Best for: Event posters, cultural and community content, zine-style reports, social-campaign recaps, creative-operations showcases (活动海报/文化内容/社群运营/创意活动).
- Avoid for: Formal corporate documents or dense financial data.

## Visual Snapshot

A tactile print-shop system modeled on Risograph printing — two or three flat ink colors per slide, coarse halftone dots, misregistered offset type, and paper grain. Anton condensed heavy display and Archivo body carry the zine voice; "+" registration marks, rotated collage cards, and ink fields make every slide read as a freshly printed sheet. Flat inks only, no shadows, no gradients — the paper is the texture.

Every slide is a fresh riso sheet on cream paper `{colors.paper}`: an enormous Anton headline with a misregistration ghost offset 2–4px in a second ink, coarse halftone dots filling the texture areas, "+" registration marks in the corners, and paper grain from an SVG feTurbulence filter over everything. Stamps, slightly rotated zine cards, and index numerals complete a composition that looks pulled off a stencil duplicator, not rendered on a screen.

## Preview Ingredients

- Palette: paper #FBF7EE; paper-deep #F3EDDD; riso-red #E8472F; riso-blue #2266CC; riso-yellow #FFCD00; riso-green #008A72; ink #2A2723; graphite #8A847A
- Typography: Anton; Archivo; Noto Sans SC (CJK); {typography.display.fontFamily}
- Signature move: Misregistration — the display headline duplicated and offset 2–4px in another ink color with `mix-blend-multiply` or layered `text-shadow` ({components.misreg-headline}).
- Signature move: Coarse halftone dot pattern for image areas — 2.5px dots on a 7px grid via a tiled radial-gradient ({components.halftone-panel}).
- Signature move: Paper grain via an inline SVG feTurbulence noise filter at low opacity ({components.grain-overlay}).
- Signature move: Max 2–3 ink colors per slide ({colors.riso-red}, {colors.riso-blue}, {colors.riso-yellow}, {colors.riso-green}) — flat inks, no shadows.
- Signature move: "+" registration marks in the corners ({components.registration-mark}) and zine collage compositions with slight rotation ({components.zine-card}).

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
