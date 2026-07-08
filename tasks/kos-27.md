# KOS-27 — Analog feel: humanizace hlasů + analog bus

**Status:** Todo

## Popis

Zvuk je stále moc „digitální" — dokonale se opakuje a má sterilní spektrum. Přiblížit se analogovému charakteru bez samplů. Čistě audio engine, žádné UI.

Rozsah:
- **Humanizace (drift) per úder** — při každém triggeru náhodně: ladění ±1–2 %, decay ±5 %, hlasitost ±pár %. Největší očekávaný efekt.
- **Envelope tvary** — decay přes `setTargetAtTime` (vybíjení kondenzátoru) místo `exponentialRampToValueAtTime`; attack 1–3 ms místo nulového (odstranit digitální „cvak")
- **Detuning hatů per úder** — šest obdélníků rozhodit o pár centů při každém úderu (pokaždé jiná interference, jako skutečný činel)
- **Analog bus na masteru** — lowpass ~13 kHz + highpass ~30 Hz (analogová šířka pásma) + velmi jemná soft saturace mixu („výstupní stupeň")

Technicky:
- Drift jako malý helper (`drift(base, pct)`) volaný uvnitř `play*` funkcí
- Master řetězec: master gain → LP → HP → soft shaper → kompresor → destination
- Sequencer, UI ani parametry knobů se nemění
- Po implementaci poslechový A/B test proti v1.6 (záloha ve `versions/`)
