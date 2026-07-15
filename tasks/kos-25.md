# KOS-25 — Sound design: de-tinning the voices + master glue

**Status:** Done (v1.5, PR #6)

## Description

The sound is too "tinny" and sterile. Pure audio engine task (UI unchanged).

Scope:
- **Hi-hats** — bandpass + highpass instead of raw squares through a single highpass; fast "ting" attack envelope
- **Kick** — waveshaper saturation (tanh) for a warmer body, two-phase envelope (punch → sub tail)
- **Snare** — short "crack" transient (stick hit), two-phase snappy envelope, slightly stronger body
- **Master bus** — gentle DynamicsCompressor as "glue" (threshold −12 dB, ratio 3:1)

Technical notes:
- Shared drive curve (created once in `initAudio`), WaveShaper node per voice
- Chain: voices → master gain → compressor → destination
- Sequencer, UI, and knob params unchanged
