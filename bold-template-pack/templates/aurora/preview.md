# Aurora Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/aurora/design.md`
- Preview card: `bold-template-pack/templates/aurora/preview.md`

## Selection Metadata

- Slug: `aurora`
- Tagline: Full-bleed aurora gradients with oversized white display type: cinematic brand moments.
- Mood: cinematic, bold, luminous, premium
- Tone: confident, aspirational, expressive
- Formality: medium-low
- Density: low
- Scheme: dark
- Best for: Brand launches, annual strategy moments, keynote opens and closes, vision statements, product reveals (品牌发布/年度战略/开场与收尾).
- Avoid for: Dense data or formal documents — the canvas commits to big single statements.

## Visual Snapshot

A cinematic dark-field system: layered radial-gradient blobs in teal, violet, magenta, amber, and blue drift over a near-black canvas (`{colors.base-ink}`), and oversized Unbounded display type renders in white with a faint two-layer glow. One or two statements max per slide, a small dim mono kicker above, a 1px glass hairline divider below, and one gradient-filled numeral per moment — no cards, no panels, no charts.

The discipline is restraint: text at rest is always white or dim (`{colors.text-dim}`), the aurora palette lives only in blurred orbs and gradient numerals, and every slide answers three questions — the statement, the aurora arrangement, the single meta line. The register is confident, aspirational, and luminous; the system is built for launches, openings, closings, and vision moments where the canvas is the message.

## Preview Ingredients

- Palette: base-ink #0B0F1E; aurora-teal #2DD4BF; aurora-violet #8B5CF6; aurora-magenta #EC4899; aurora-amber #F59E0B; aurora-blue #3B82F6; text-white #FFFFFF; text-dim rgba(255,255,255,0.72)
- Typography: Unbounded; Inter; JetBrains Mono; {typography.display.fontFamily}
- Signature move: A near-black canvas ({colors.base-ink}) with 3–5 blurred radial-gradient orbs (46vw, blur 70px) in the five aurora stops — the aurora is the composition.
- Signature move: Oversized white Unbounded display at 10–13vw with a two-layer glow ({components.glow-text} — white bloom plus violet aura).
- Signature move: Numerals filled with the aurora gradient ({components.gradient-num}) via background-clip: text — teal → violet → magenta → amber.
- Signature move: Small dim mono kickers ({typography.kicker.fontFamily} at 0.24em tracking) and one 1px glass hairline divider at 20% white per slide.
- Signature move: One or two statements max per slide — no cards, no panels, no charts; text at rest is always white or dim.

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
