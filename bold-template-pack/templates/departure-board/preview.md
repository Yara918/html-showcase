# Departure Board Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/departure-board/design.md`
- Preview card: `bold-template-pack/templates/departure-board/preview.md`

## Selection Metadata

- Slug: `departure-board`
- Tagline: A Solari split-flap board: black panel, orange-on-black characters, destination rows, and a live clock.
- Mood: utilitarian, kinetic, alert, precise
- Tone: direct, operational, energetic
- Formality: medium
- Density: high
- Scheme: dark
- Best for: Project dispatch boards, operations command screens, launch countdowns, sprint boards, event schedules — any live-status wall (项目调度/运营大屏/倒计时/进度直播).
- Avoid for: Soft corporate narratives — the board voice is mechanical and loud.

## Visual Snapshot

A mechanical split-flap display in the airport-board tradition: a charcoal board frame with a 1px flap-line border, a 6px black bezel, and a deep inner shadow hangs on a black wall (`{colors.board-black}`). Every row character sits in its own dark flap cell (`{colors.flap-dark}`) with top/bottom flap-line seams, set in amber JetBrains Mono; TIME / CODE / DESTINATION / GATE / STATUS columns are a fixed tabular grid with a dim Archivo small-cap header band.

The board runs live equipment: a blinking STATUS cell (`NOW`, `BOARDING`) animates via a steps() CSS animation, a live HH:MM:SS clock with tabular numerals sits in the header band, and 1px flap-line rules separate the rows. Amber on black is the whole display; white is reserved for titles, dim for metadata, and alert red (`{colors.alert-red}`) for stopped states — steady, never blinking. The register is utilitarian, kinetic, alert, and precise: a status wall, not a document.

## Preview Ingredients

- Palette: board-black #0A0A0A; panel-charcoal #151515; flap-dark #232323; flap-line #3A3A3A; amber #FF9F1C; white #F5F5F0; dim #8A8A85; alert-red #FF4B3E
- Typography: JetBrains Mono; Archivo; {typography.row.fontFamily}
- Signature move: Every character sits in its own flap cell ({components.flap-cell}) with a top/bottom flap-line seam ({components.flap-divider}) — a 1px {colors.flap-line} gradient fading right.
- Signature move: Tabular departure rows in five fixed columns (TIME / CODE / DESTINATION / GATE / STATUS) with a dim Archivo small-cap header band and 1px flap-line row separators.
- Signature move: A blinking STATUS cell ({components.status-cell}) — amber `NOW`/`BOARDING` via a steps() CSS animation; alert red never blinks.
- Signature move: A live HH:MM:SS clock ({components.clock}) with tabular numerals in the header band, amber on black.
- Signature move: The board frame ({components.board-frame}) — charcoal panel, 1px border, 6px black bezel, deep inner shadow — the whole slide is one lit appliance.

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
