# KOS-21 — 16-step sequencer

**Status:** Done (v1.1, PR #2)

## Popis

Srdce drum machine — krokový sekvencer nad Web Audio clockem.

Rozsah:
- 16 kroků × řádky nástrojů (zatím kick z KOS-20, připraveno na další hlasy)
- Lookahead scheduler (audio clock + krátký setTimeout tick, ne setInterval na krok)
- Play/Stop, tempo 40–240 BPM, vizuální běžící kurzor po krocích
- Zapínání/vypínání kroků klikem, stav v `S.pattern`

Technicky:
- Scheduler volá `play*()` funkce nástrojů s přesným `time` argumentem
- Swing/shuffle zatím ne — samostatný task později
