# KOS-25 — Sound design: odplechovatění hlasů + master glue

**Status:** In Progress

## Popis

Zvuk je moc „plechový" a sterilní. Čistě audio engine task (UI beze změny).

Rozsah:
- **Hi-haty** — bandpass + highpass místo syrových obdélníků přes samotný highpass; rychlý „cink" attack envelope
- **Kick** — waveshaper saturace (tanh) pro teplejší tělo, dvoufázový envelope (punch → sub tail)
- **Snare** — krátký „crack" transient (rána paličky), dvoufázový snappy envelope, o chlup silnější tělo
- **Master bus** — jemný DynamicsCompressor jako „glue" (threshold −12 dB, ratio 3:1)

Technicky:
- Drive curve sdílená (vytvoří se jednou v `initAudio`), WaveShaper node per hlas
- Řetězec: hlasy → master gain → kompresor → destination
- Sequencer, UI ani parametry knobů se nemění
