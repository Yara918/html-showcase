# Data Wall Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/data-wall/design.md`
- Preview card: `bold-template-pack/templates/data-wall/preview.md`

## Selection Metadata

- Slug: `data-wall`
- Tagline: A dense, annotation-first data canvas: small-multiple charts, hairline axes, and one highlighted insight per slide.
- Mood: analytical, dense, editorial, evidence-led
- Tone: rigorous, precise, calm, intelligent
- Formality: high
- Density: very high
- Scheme: light
- Best for: Data dashboards, analytics reviews, KPI deep-dives, experiment reports, market snapshots, annual reviews (运营看板/数据分析汇报/复盘/BI 报告).
- Avoid for: Keynote-style low-content talks — the system is built to carry dense evidence.

## Visual Snapshot

A dense, annotation-first data canvas on warm paper (`{colors.paper}`), set in Newsreader serif for display and stat numerals, Inter for body, and JetBrains Mono for every annotation, axis, legend, and source note. Small-multiple charts sit in a strict 3-column grid, each one carrying a single mono callout — a white chip with a 2px red left edge and a dashed ink leader line pointing at the key point.

The system's discipline is one highlighted insight per slide: red (`{colors.accent-red}`) marks exactly one series, one numeral, or one 64×2px rule, while teal, gold, and blue form a stable semantic series palette used only inside charts. Panels separate by 1px ink rules, axes are 1px hairlines, everything aligns to an 8px grid, and every chart is evidence with a mono source note — flat, square-cornered, and built to carry dense evidence without ever looking crowded.

## Preview Ingredients

- Palette: paper #FAF7F2; white #FFFFFF; ink #26221E; graphite #6E675E; graphite-light #A39B8F; accent-red #E63312; teal #1F7A74; gold #C99B3F; blue #2E5E8C
- Typography: Newsreader; Inter; JetBrains Mono; {typography.stat-value.fontFamily}
- Signature move: Big Newsreader serif stat numerals ({typography.stat-value.fontFamily} at 5vw, weight 500) — the editorial serif is the statistics voice.
- Signature move: Every chart carries exactly one mono callout — a white chip with a 2px {colors.accent-red} left edge and a dashed ink leader line to the key point.
- Signature move: Red is reserved for one highlighted insight per slide: one series, one numeral, or one {components.insight-rule} rule.
- Signature move: 1px hairline axes in {colors.graphite-light} with mono axis labels; all chart geometry as inline SVG.
- Signature move: Mono source notes at the bottom-left of every chart and slide, and panels separated by 1px rules — never shadows.

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
