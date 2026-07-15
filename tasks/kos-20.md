# KOS-20 — Basic skeleton: layout + audio init + kick

**Status:** Done (v1.0, PR #1)

## Description

First version of `index.html` — the skeleton of the whole drum machine that everything else will build on.

Scope:
- HTML/CSS layout in 909 style: top panel with knobs, bottom row of 16 step buttons, Play/Stop + tempo section
- `initAudio()` — Web Audio context, master gain (unlock the context on first interaction)
- First synthesized voice: **kick** (`playKick()`) — sine with a pitch envelope + click transient, TUNE / DECAY / LEVEL knobs
- Manual kick trigger button (to verify the sound before the sequencer exists)

Technical notes:
- Everything in a single `index.html`, no dependencies
- Design the state object `S` (tempo, instrument params) so it can later be extended with a pattern and more voices
