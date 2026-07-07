# KOS-20 — Základní kostra: layout + audio init + kick

**Status:** Done (v1.0, PR #1)

## Popis

První verze `index.html` — kostra celé drum machine, na které bude stát všechno další.

Rozsah:
- HTML/CSS layout ve stylu 909: horní panel s knoby, spodní řada 16 step tlačítek, sekce Play/Stop + tempo
- `initAudio()` — Web Audio context, master gain (odemknutí contextu na první interakci)
- První syntetizovaný hlas: **kick** (`playKick()`) — sinus s pitch envelope + click transient, knoby TUNE / DECAY / LEVEL
- Tlačítko pro manuální trigger kicku (ověření zvuku ještě před sequencerem)

Technicky:
- Vše v jednom `index.html`, žádné závislosti
- Stavový objekt `S` (tempo, parametry nástrojů) připravit tak, aby šel později rozšířit o pattern a další hlasy
