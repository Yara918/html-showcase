# Gallery Label Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/gallery-label/design.md`
- Preview card: `bold-template-pack/templates/gallery-label/preview.md`

## Selection Metadata

- Slug: `gallery-label`
- Tagline: White-gallery restraint: small-caps serif labels, generous margins, and art-caption typography.
- Mood: quiet, elegant, curatorial, premium
- Tone: refined, unhurried, authoritative-quiet
- Formality: high
- Density: low
- Scheme: light
- Best for: Portfolio showcases, product aesthetics, brand books, luxury and premium pitches, art-direction reviews — any deck where restraint is the message (作品展示/产品美学/品牌画册/高定提案).
- Avoid for: Dense operational data or energetic launches.

## Visual Snapshot

A curatorial system modeled on the museum wall label — quiet, elegant, and authoritative. Cormorant Garamond serif headlines sit in the upper-left third of a white gallery; Inter at weight 300 carries body copy; tiny uppercase tracked labels read like exhibition captions. Content occupies under half the canvas, a single thin brass frame borders cover slides, and restraint itself is the message.

Every slide is a gallery wall in warm gallery-white `{colors.gallery-white}`: a large Cormorant serif headline in the upper-left third, body text in featherweight Inter 300, and a four-line uppercase wall label — artist / title / date / medium — tracked and muted in graphite. Paper plaques, 1px faint-ink hairlines, and a single thin brass frame on the cover complete a system where the empty wall does the persuading.

## Preview Ingredients

- Palette: gallery-white #FAFAF7; paper #F3F1EC; paper-deep #E9E5DD; ink #1A1A18; graphite #6F6F6A; graphite-light #9C9C95; ink-faint #C9C9C2; brass #B08D57
- Typography: Cormorant Garamond; Inter; Noto Serif SC / Noto Sans SC (CJK); {typography.display.fontFamily}
- Signature move: Tiny uppercase tracked wall labels (artist / title / date / medium on four stacked lines) styled like museum captions ({components.wall-label-block}).
- Signature move: Large serif headline in the upper-left third ({typography.display}, Cormorant Garamond 600).
- Signature move: Content occupies under 50% of the canvas — the empty gallery wall is the design.
- Signature move: Thin 1px separators in {colors.ink-faint}, and a single thin brass frame border on cover slides ({components.brass-frame}).
- Signature move: Cormorant drop caps opening long text passages ({components.drop-cap}) and italic artwork titles inside body copy.

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
