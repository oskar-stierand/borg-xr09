# BORG XR-09 — Rhythm Composer

Jednoduchá, ale legendární webová drum machine inspirovaná Rolandem TR-909.

- **Single-file** — celý nástroj žije v `index.html`, žádný build, žádné závislosti
- **Plně syntetizované zvuky** — Web Audio API, žádné samply
- **8 hlasů** — kick, snare, clap, closed/open hi-hat (s choke), 3 tomy
- **16-step sequencer** — lookahead scheduler nad audio clockem, swing 50–75 %, řádek accent
- **Pattern banky A–D** s kopírováním + 9 factory presetů (house, breakbeat, jungle, electro, techno, boom bap, UK garage, dembow, liquid DnB)
- **Analog feel** — per-hit humanizace (drift ladění/decay/hlasitosti), RC obálky, analog bus se saturací a paralelní kompresí (knob COMP)
- Sesterský projekt syntezátoru [BORG XS-20](https://github.com/oskar-stierand/borg-xs20)

## Spuštění

Otevři `index.html` v Chrome. To je vše.

## Vývoj

Tasky jsou ve složce `tasks/` (jeden `.md` soubor na task), pracovní postup popisuje `CLAUDE.md`, historie verzí je v `CHANGELOG.md`. Zálohy jednotlivých verzí leží ve `versions/`.
