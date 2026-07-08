# KOS-27 — Analog feel: humanizace hlasů + analog bus

**Status:** Done (body 4+5: v1.7, PR #8; body 1–3: v1.8, PR #9)

## Popis

Zvuk je stále moc „digitální" — dokonale se opakuje a má sterilní spektrum. Přiblížit se analogovému charakteru bez samplů. Čistě audio engine, žádné UI.

Rozsah:
- **Humanizace (drift) per úder** — při každém triggeru náhodně: ladění ±1–2 %, decay ±5 %, hlasitost ±pár %. Největší očekávaný efekt.
- **Envelope tvary** — decay přes `setTargetAtTime` (vybíjení kondenzátoru) místo `exponentialRampToValueAtTime`; attack 1–3 ms místo nulového (odstranit digitální „cvak")
- **Detuning hatů per úder** — šest obdélníků rozhodit o pár centů při každém úderu (pokaždé jiná interference, jako skutečný činel)
- **Analog bus na masteru** — lowpass ~13 kHz + highpass ~30 Hz (analogová šířka pásma) + velmi jemná soft saturace mixu („výstupní stupeň")
- **Paralelní komprese s knobem COMP** (nahrazuje sériový glue kompresor z KOS-25) — NY style: dry větev vždy 100 % (transienty netknuté), wet větev agresivně stlačená (threshold −24 dB, ratio 8:1, rychlý attack, release ~150 ms, fixní makeup gain); knob **COMP** v modulu Master přimíchává wet pod dry (0 = bez komprese, 1 = max glue). Parametr `compMix` v `DEFAULT_PARAMS` → jde do presetů i `captureState`/`applyState`; výchozí ~0.35, presetům nastavit vkusné hodnoty (boom bap víc, techno míň). Jediná UI změna tasku: 1 knob v Masteru.

Technicky:
- Drift jako malý helper (`drift(base, pct)`) volaný uvnitř `play*` funkcí
- Master řetězec: master gain → LP → HP → soft shaper → [dry + comp→wet] → destination
- Sequencer i zbytek UI beze změny; jediná UI změna = knob COMP v modulu Master
- Po implementaci poslechový A/B test proti v1.6 (záloha ve `versions/`)
