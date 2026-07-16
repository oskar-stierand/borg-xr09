# Changelog — BORG XR-09

All notable changes to the project. Versions correspond to snapshots in `versions/index-vX.Y.html`.

## v1.11 — 2026-07-16 (KOS-32, PR #12)
- README hero screenshot under the title: the jungle (amen break) factory preset
- Fixed a Czech UI label missed by the translation — the grid header `click a track name to trigger` (the diacritics were HTML-entity-encoded `&aacute;`, so the earlier raw-diacritic scan didn't catch it)

## v1.10 — 2026-07-15 (KOS-30, PR #11)
- Finished the English translation: six Czech CSS section comments missed by KOS-28 (comments only, no behavior changes)

## v1.9 — 2026-07-15 (KOS-28, PR #10)
- Translated the entire repository to English (README, CHANGELOG, CLAUDE.md, task files, code comments in `index.html`)
- No behavior changes — `index.html` edits are comments only

## v1.8 — 2026-07-08 (KOS-27 part 2, PR #9)
- Per-hit humanization `drift()` — tuning, decay, and level of every hit vary slightly
- Analog RC envelopes (`setTargetAtTime`) instead of linear digital ramps — no clicks
- Hi-hat oscillator detune — a few cents different on every hit

## v1.7 — 2026-07-08 (KOS-27 part 1, PR #8)
- Analog bus on the master: HP/LP filters (analog chain bandwidth) + subtle output-stage saturation
- Parallel (NY) compression with a **COMP** knob — dry always at 100%, heavily squashed wet branch blended in

## v1.6 — 2026-07-08 (KOS-26, PR #7)
- Five new factory presets: techno, boom bap, UK garage, dembow, liquid DnB (9 total)

## v1.5 — 2026-07-08 (KOS-25, PR #6)
- Sound design: hi-hat bandpass, kick saturation, snare crack
- Master glue compressor (replaced by parallel compression in v1.7)

## v1.4 — 2026-07-08 (KOS-24, PR #5)
- Swing/shuffle 50–75% (offbeat 16th shift), live knob, preset defaults

## v1.3 — 2026-07-08 (KOS-23, PR #4)
- ACCENT row
- Pattern banks A–D with copy
- `captureState()`/`applyState()` + factory presets (house, breakbeat, jungle, electro)

## v1.2 — 2026-07-07 (KOS-22, PR #3)
- Full drum kit: snare, clap, closed/open hi-hat (with choke), 3 toms
- 8 instruments × 16 steps grid

## v1.1 — 2026-07-07 (KOS-21, PR #2)
- 16-step sequencer: lookahead scheduler on top of the Web Audio clock, transport, step cursor

## v1.0 — 2026-07-07 (KOS-20, PR #1)
- Basic skeleton: TR-909-style layout, audio init, synthesized kick
