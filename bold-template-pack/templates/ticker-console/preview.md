# Ticker Console Preview Card

Use this small file for title-slide previews only. For final deck generation, read the full design doc listed below.

## Files

- Full design doc: `bold-template-pack/templates/ticker-console/design.md`
- Preview card: `bold-template-pack/templates/ticker-console/preview.md`

## Selection Metadata

- Slug: `ticker-console`
- Tagline: Vintage green-phosphor CRT: scanlines, uppercase mono type, blinking block cursor, system-log aesthetics.
- Mood: retro, technical, nocturnal, hacker
- Tone: direct, geeky, confident
- Formality: low-medium
- Density: medium
- Scheme: dark
- Best for: Tech updates, system-status walls, release logs, engineering-culture decks, internal dev talks (技术周报/系统状态/极客向内容/发布日志).
- Avoid for: Formal institutional or consumer-brand decks.

## Visual Snapshot

A nocturnal terminal system rendered as a vintage green-phosphor CRT. VT323 pixel-readout type and JetBrains Mono body carry every line of text; a scanline overlay, phosphor glow, and a blinking block cursor reproduce the hardware texture of an aging system console. The palette is one green phosphor family on a near-black screen, with exactly two signal colors — amber for warnings, red for errors — and nothing else.

Every slide is a full-bleed screen in near-black `{colors.screen}` under a 2px scanline grid, with the CRT vignette darkening the corners. Display text glows in phosphor green; log lines are bracketed `[HH:MM:SS]`, commands open with a bright `> ` prompt, and the last typed line carries a blinking block cursor. The system reads as a machine that has been left running for thirty years and is still printing the log.

## Preview Ingredients

- Palette: phosphor #4AF626; phosphor-bright #B8FFA8; phosphor-dim #1E5C2E; phosphor-faint #3B8F4E; screen #050B06; screen-edge #0A140C; screen-panel #09150B; amber #FFB000; red #FF3B30
- Typography: VT323; JetBrains Mono; Noto Sans SC (CJK); {typography.display.fontFamily}
- Signature move: Scanline overlay via `repeating-linear-gradient` (thin 2px lines, low opacity) plus a radial-gradient CRT vignette, on every slide ({components.scanline-overlay}).
- Signature move: Phosphor glow `text-shadow: 0 0 8px rgba(74,246,38,0.6), 0 0 24px rgba(74,246,38,0.25)` on display text only ({components.phosphor-glow}).
- Signature move: Blinking block cursor "▊" after the last typed line, blinking with `steps(1)` so it snaps like hardware ({components.cursor-block}).
- Signature move: Bracketed `[HH:MM:SS]` timestamps in dim phosphor mono ({components.timestamp}) and `> ` prompt prefixes in {colors.phosphor-bright}.
- Signature move: Uppercase Latin display in VT323 ({typography.display}), with {colors.amber} for WARN and {colors.red} for ERR and nothing else chromatic.

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
