# Metro Map Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/metro-map/design.md`
- Preview card: `bold-template-pack/templates/metro-map/preview.md`

## Selection Metadata

- Slug: `metro-map`
- Tagline: Tube-map diagram language: 45° lines, colored routes, and interchange nodes for process and org maps.
- Mood: diagrammatic, structured, clean, urban
- Tone: clear, systematic, contemporary
- Formality: medium
- Density: medium
- Scheme: light
- Best for: Process flows, org structures, user journeys, roadmap stages, supply-chain routes — any content that is a set of nodes and connections (流程梳理/组织架构/路径规划/节点图).
- Avoid for: Narrative prose decks — this is a diagram-first system.

## Visual Snapshot

A diagram-first system that borrows the visual grammar of Harry Beck's 1933 tube map — 45° lines, colored routes, and interchange nodes — to render processes, org structures, user journeys, roadmaps, and supply routes as rideable networks. Archivo at weights 500–700 supplies a single contemporary grotesque voice; color is reserved for route lines and nothing else. Every slide answers one question: where are we going, and what are the stops in between?

The default content slide is a cream-deep map plate holding an SVG route network whose lines run only horizontally, vertically, or at 45°. Interchange nodes are white-filled circles with colored rings, terminuses are larger filled circles, process steps render as numbered stations, and a route legend anchors a corner. The system's signature flourish is the journey metaphor — "2 stops to launch" — which turns abstract process diagrams into something an audience feels itself moving through.

## Preview Ingredients

- Palette: cream #F7F3EA; cream-deep #EFE9DC; ink #1A1A18; graphite #8A847C; route-blue #1466B8; route-red #D64541; route-green #3A8F4E; route-gold #C99B3F; route-purple #7A4E9E; interchange-white #FFFFFF
- Typography: Archivo; Noto Sans SC; {typography.label.fontFamily}
- Signature move: Line networks drawn as SVG polylines with only horizontal, vertical and 45° segments — never curves, never arbitrary angles ({colors.route-blue}).
- Signature move: Interchange nodes = white-filled circles with colored rings ({colors.interchange-white} fill, route-colored border); terminus stations are larger filled circles.
- Signature move: 2-3 colored route lines max per slide; process steps render as numbered stations along a line.
- Signature move: A route legend in one corner pairing a colored dash with the route name in {typography.route-title}.
- Signature move: Journey metaphors like "2 stops to launch" set in {typography.stat-value} inside an ink-filled pill chip.

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
