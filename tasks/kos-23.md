# KOS-23 — Accent, patterny a presety

**Status:** Done (v1.3, PR #4)

## Popis

Z „hračky" udělat nástroj — dynamika a ukládání.

Rozsah:
- **Accent** řádek — akcentovaný krok zvýší velocity všech nástrojů na daném kroku (jako na 909)
- Přepínání patternů (A/B/C/D), kopírování patternu
- `captureState()` / `applyState()` — uložení a načtení celého stavu (pattern + parametry nástrojů + tempo)
- Pár factory presetů (klasický 4-on-the-floor, breakbeat, electro)

Technicky:
- Formát presetů jako prostý JS objekt, kompatibilní do budoucna s export/import JSON
