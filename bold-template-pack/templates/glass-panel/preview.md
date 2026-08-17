# Glass Panel Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/glass-panel/design.md`
- Preview card: `bold-template-pack/templates/glass-panel/preview.md`

## Selection Metadata

- Slug: `glass-panel`
- Tagline: Frosted-glass panels floating over a soft gradient field: calm, modern, depth through blur.
- Mood: modern, calm, airy, premium
- Tone: friendly, polished, contemporary
- Formality: medium
- Density: low-medium
- Scheme: light
- Best for: Product walkthroughs, solution pitches, team and culture decks, onboarding explainers — anything wanting a modern premium SaaS feel (产品介绍/方案演示/团队介绍).
- Avoid for: Dense formal documents or print-like editorial — glass panels read as screen-native.

## Visual Snapshot

A frosted-glass system: translucent panels of `{colors.glass-white}` float over a soft four-stop gradient field (blue, violet, pink, mint), and depth comes from blur, not ink. Every panel carries a 1px white border, `backdrop-filter: blur(18–24px)`, a 24px corner radius, and a three-layer shadow with an inset top highlight; large blurred orbs drift behind the panels so light leaks through the gaps.

Sora 600–700 display, Inter 400 body, and Space Grotesk 500 small-cap labels sit on the glass; a single hero phrase per slide may carry gradient text (`background-clip: text`) in indigo → violet → cyan. Glass pill badges and frosted stat chips are the small surfaces, white-glass dividers replace ink rules, and headlines never sit on the raw field. The register is calm, modern, airy, and premium — screen-native by conviction.

## Preview Ingredients

- Palette: field-blue #EAF2FF; field-violet #F3EEFF; field-pink #FFF0F2; field-mint #EAFCF4; glass-white rgba(255,255,255,0.55); glass-border rgba(255,255,255,0.65); ink #1E2430; graphite #5B6472; accent-indigo #4F46E5; accent-violet #8B5CF6; accent-cyan #06B6D4
- Typography: Sora; Inter; Space Grotesk; {typography.hero-phrase.fontFamily}
- Signature move: Frosted-glass panels ({colors.glass-white} fill, 1px {colors.glass-border} border, backdrop-filter blur 18–24px) with 24px corner radius and three-layer soft shadows.
- Signature move: A soft four-stop radial gradient field with 2–3 large blurred orbs ({components.orb}) drifting behind the panels.
- Signature move: One hero phrase per slide with gradient text ({components.gradient-text}, background-clip: text) in indigo → violet → cyan.
- Signature move: Glass pill badges ({components.glass-pill}) and frosted stat chips ({components.stat-chip}) as the system's small surfaces.
- Signature move: White-glass dividers at 60% white replace ink rules — separation is light, never ink.

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
