# KOS-24 — Swing / shuffle

**Status:** Done (v1.4, PR #5)

## Popis

Groove — posun sudých 16tinových kroků, aby beat „houpal" místo robotické přesnosti.

Rozsah:
- Knob **SWING** v modulu Tempo (vedle BPM)
- Rozsah 50–75 % (0 = rovný beat, MPC-style maximum)
- Posouvá liché indexy kroků (offbeat 16tiny) o `(swing−50 %) × 2 × délka kroku`
- Vizuální kurzor zůstává synchronní se swingnutým audio časem
- Swing je součást stavu (`DEFAULT_PARAMS` → presety, `captureState`/`applyState`)
- Factory presetům nastavit vkusné výchozí hodnoty swingu

Technicky:
- Změna jen v `seqTick()`/`scheduleStep()` — offset se přičítá při plánování, grid `SEQ.nextTime` zůstává rovný
- Audio engine (hlasy) beze změny
