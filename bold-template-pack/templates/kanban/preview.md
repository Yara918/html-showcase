# Kanban Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/kanban/design.md`
- Preview card: `bold-template-pack/templates/kanban/preview.md`

## Selection Metadata

- Slug: `kanban`
- Tagline: A physical kanban wall: cork-board texture, washi-tape columns, sticky notes, handwritten energy.
- Mood: casual, tactile, collaborative, warm
- Tone: friendly, honest, energetic
- Formality: low
- Density: medium-high
- Scheme: light
- Best for: Project boards, ops daily standups, sprint reviews, team retrospectives, work-in-progress walls, activity recaps (项目进度/运营日常/团队协作/复盘).
- Avoid for: Formal client-facing or high-authority decks.

## Visual Snapshot

A physical kanban wall rendered as a design system — cork-board texture, washi-tape column headers, and sticky notes in five colors, all set in handwriting type. Caveat carries every heading with energetic marker strokes; Patrick Hand handles note bodies with honest legibility. The system is deliberately imperfect: notes tilt ±1–2°, tape strips are translucent and slightly askew, and "done" notes fade — but the wall underneath is disciplined, so the chaos reads as teamwork, not clutter.

Every slide is a wall in progress: cork (or whiteboard) as the surface, tape-labeled columns with circular WIP-limit badges, stacks of tilted sticky notes with soft shadows, arrow connectors showing flow, and faded notes remembering what already moved on. Controlled imperfection is the point — nothing is perfectly aligned, but everything stays inside a fixed vocabulary of rotation, color, and shadow, so the energy reads as human and the structure reads as trustworthy.

## Preview Ingredients

- Palette: cork #C9996B; cork-deep #A87C4E; whiteboard #F7F7F5; sticky-yellow #FFD166; sticky-pink #F4A7B9; sticky-green #A8D5A2; sticky-blue #9EC5FE; sticky-orange #FFB85C; ink #2A2A28; ink-soft #6E6E66; tape rgba(255,255,255,0.35)
- Typography: Caveat; Patrick Hand; Ma Shan Zheng; Noto Sans SC; {typography.label.fontFamily}
- Signature move: Column headers as washi-tape strips ({colors.tape}) with slight rotation and a small shadow.
- Signature move: Sticky notes at ±1-2deg rotation with soft shadows; default note color {colors.sticky-yellow}, titles in {typography.note-title}.
- Signature move: WIP-limit badges as small circles ({colors.ink} fill, {typography.wip-num} numeral).
- Signature move: Cork background with a repeating radial-dot pattern ({components.cork-dot-texture}), plus a whiteboard dot-grid alternative.
- Signature move: "Done" notes slightly faded (opacity 0.55, saturate 0.7); arrow connectors between columns.

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
