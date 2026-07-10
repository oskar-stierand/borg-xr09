# Changelog — BORG XR-09

Všechny významné změny projektu. Verze odpovídají zálohám ve `versions/index-vX.Y.html`.

## v1.8 — 2026-07-08 (KOS-27 část 2, PR #9)
- Per-hit humanizace `drift()` — ladění, decay a hlasitost každého úderu se nepatrně liší
- Analogové RC obálky (`setTargetAtTime`) místo lineárních digitálních ramp — žádné cvaky
- Detune oscilátorů hi-hatů — pár centů jinak při každém úderu

## v1.7 — 2026-07-08 (KOS-27 část 1, PR #8)
- Analog bus na masteru: HP/LP filtry (šířka pásma analogového řetězce) + jemná saturace výstupního stupně
- Paralelní (NY) komprese s knobem **COMP** — dry vždy 100 %, agresivně stlačená wet větev se přimíchává

## v1.6 — 2026-07-08 (KOS-26, PR #7)
- Pět nových factory presetů: techno, boom bap, UK garage, dembow, liquid DnB (celkem 9)

## v1.5 — 2026-07-08 (KOS-25, PR #6)
- Sound design: bandpass hi-hatů, saturace kicku, crack snaru
- Master glue kompresor (v v1.7 nahrazen paralelní kompresí)

## v1.4 — 2026-07-08 (KOS-24, PR #5)
- Swing/shuffle 50–75 % (posun offbeat 16tin), živý knob, defaulty v presetech

## v1.3 — 2026-07-08 (KOS-23, PR #4)
- Řádek ACCENT
- Pattern banky A–D s kopírováním
- `captureState()`/`applyState()` + factory presety (house, breakbeat, jungle, electro)

## v1.2 — 2026-07-07 (KOS-22, PR #3)
- Kompletní bicí sada: snare, clap, closed/open hi-hat (s choke), 3 tomy
- Grid 8 nástrojů × 16 kroků

## v1.1 — 2026-07-07 (KOS-21, PR #2)
- 16-step sequencer: lookahead scheduler nad Web Audio clockem, transport, kurzor kroku

## v1.0 — 2026-07-07 (KOS-20, PR #1)
- Základní kostra: layout ve stylu TR-909, inicializace audia, syntetizovaný kick
