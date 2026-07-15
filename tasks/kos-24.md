# KOS-24 — Swing / shuffle

**Status:** Done (v1.4, PR #5)

## Description

Groove — shifting the even 16th steps so the beat "swings" instead of being robotically precise.

Scope:
- **SWING** knob in the Tempo module (next to BPM)
- Range 50–75% (0 = straight beat, MPC-style maximum)
- Shifts odd step indices (offbeat 16ths) by `(swing−50%) × 2 × step length`
- The visual cursor stays in sync with the swung audio time
- Swing is part of the state (`DEFAULT_PARAMS` → presets, `captureState`/`applyState`)
- Give the factory presets tasteful default swing values

Technical notes:
- Change only in `seqTick()`/`scheduleStep()` — the offset is added when scheduling, the `SEQ.nextTime` grid stays straight
- Audio engine (voices) unchanged
