# KOS-27 — Analog feel: voice humanization + analog bus

**Status:** Done (items 4+5: v1.7, PR #8; items 1–3: v1.8, PR #9)

## Description

The sound is still too "digital" — it repeats perfectly and has a sterile spectrum. Get closer to an analog character without samples. Pure audio engine, no UI.

Scope:
- **Per-hit humanization (drift)** — on every trigger, randomize: tuning ±1–2%, decay ±5%, level ±a few %. Biggest expected effect.
- **Envelope shapes** — decay via `setTargetAtTime` (capacitor discharge) instead of `exponentialRampToValueAtTime`; attack 1–3 ms instead of zero (remove the digital "click")
- **Per-hit hat detuning** — scatter the six squares by a few cents on every hit (different interference every time, like a real cymbal)
- **Analog bus on the master** — lowpass ~13 kHz + highpass ~30 Hz (analog bandwidth) + very subtle soft saturation of the mix ("output stage")
- **Parallel compression with a COMP knob** (replaces the serial glue compressor from KOS-25) — NY style: dry branch always at 100% (transients untouched), wet branch heavily squashed (threshold −24 dB, ratio 8:1, fast attack, release ~150 ms, fixed makeup gain); the **COMP** knob in the Master module blends the wet under the dry (0 = no compression, 1 = max glue). The `compMix` param in `DEFAULT_PARAMS` → goes into presets and `captureState`/`applyState`; default ~0.35, give presets tasteful values (boom bap more, techno less). The only UI change of this task: 1 knob in Master.

Technical notes:
- Drift as a small helper (`drift(base, pct)`) called inside the `play*` functions
- Master chain: master gain → LP → HP → soft shaper → [dry + comp→wet] → destination
- Sequencer and the rest of the UI unchanged; the only UI change = the COMP knob in the Master module
- After implementation, listening A/B test against v1.6 (snapshot in `versions/`)
