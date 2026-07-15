# KOS-21 — 16-step sequencer

**Status:** Done (v1.1, PR #2)

## Description

The heart of the drum machine — a step sequencer on top of the Web Audio clock.

Scope:
- 16 steps × instrument rows (just the kick from KOS-20 for now, prepared for more voices)
- Lookahead scheduler (audio clock + a short setTimeout tick, not setInterval per step)
- Play/Stop, tempo 40–240 BPM, visual running cursor across the steps
- Toggle steps on/off by clicking, state kept in `S.pattern`

Technical notes:
- The scheduler calls the instruments' `play*()` functions with an exact `time` argument
- No swing/shuffle yet — separate task later
