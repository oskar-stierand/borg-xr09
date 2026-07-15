# KOS-23 — Accent, patterns and presets

**Status:** Done (v1.3, PR #4)

## Description

Turn the "toy" into an instrument — dynamics and saving.

Scope:
- **Accent** row — an accented step raises the velocity of all instruments on that step (like on the 909)
- Pattern switching (A/B/C/D), pattern copy
- `captureState()` / `applyState()` — save and load the entire state (pattern + instrument params + tempo)
- A few factory presets (classic 4-on-the-floor, breakbeat, electro)

Technical notes:
- Preset format as a plain JS object, forward-compatible with JSON export/import
