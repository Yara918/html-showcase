# Scoreboard Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/scoreboard/design.md`
- Preview card: `bold-template-pack/templates/scoreboard/preview.md`

## Selection Metadata

- Slug: `scoreboard`
- Tagline: A stadium scoreboard: seven-segment LED numerals, black panel, team colors, big KPI drama.
- Mood: competitive, bold, energetic, celebratory
- Tone: direct, punchy, high-energy
- Formality: low-medium
- Density: medium
- Scheme: dark
- Best for: KPI races, goal competitions, sales-contest walls, campaign countdowns, quarter showdowns — any us-vs-target framing (KPI 冲刺/目标竞赛/大促倒计时/季度对决).
- Avoid for: Quiet formal documents.

## Visual Snapshot

A stadium scoreboard rendered as a design system — a black arena panel, seven-segment-style LED numerals, team colors, and big KPI drama. Orbitron at weights 700–900 powers the glowing numeral clusters; JetBrains Mono uppercase handles every readout label. The system frames any us-vs-target story as a live contest: two clusters face off across a blinking VS, a ticker scrolls the status, and an amber line marks the period. It is dark, loud, and built for competition.

Every content slide is a scoreboard moment: two recessed panels on a near-black stage, each carrying a side name in LED readout above a giant glowing numeral, divided by a blinking center mark, with a scrolling ticker across the bottom. Light is the material — numerals glow in their own hue via layered text-shadow on currentColor, dim elements rest at #555555, and the amber period line marks time and risk. Two sides, one arena, and the gap between the numbers is the story.

## Preview Ingredients

- Palette: board-black #0C0C0C; panel #1A1A1A; panel-soft #141414; panel-edge #262626; led-red #FF3B30; led-green #34C759; led-amber #FFB800; led-white #F2F2F0; dim #555555
- Typography: Orbitron; JetBrains Mono; Noto Sans SC; {typography.label.fontFamily}
- Signature move: Two big seven-segment-style LED numeral clusters (LEFT vs RIGHT, or TARGET vs ACTUAL) with glow — text-shadow 0 0 12px currentColor ({colors.led-white}).
- Signature move: Side names as LED text above each cluster ({typography.side-name}, JetBrains Mono uppercase).
- Signature move: A center VS/colon with blinking animation ({components.vs-divider}).
- Signature move: A bottom ticker band with scrolling status ({colors.panel-soft} background, {typography.ticker-text}).
- Signature move: Amber period/warning line ({colors.led-amber}) — LEDs glow against the black panel.

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
