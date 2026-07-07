# KOS-22 — Zbytek bicí sady (snare, clap, hi-hats, tomy)

**Status:** Done (v1.2, PR #3)

## Popis

Doplnit syntetizované hlasy do plné 909 sady.

Rozsah:
- **Snare** — tón (dva rozladěné oscilátory) + noise burst, knoby TUNE / TONE / SNAPPY / DECAY / LEVEL
- **Clap** — filtrovaný šum s vícenásobným retrigger envelope (typický 909 „flam")
- **Closed / Open hi-hat** — filtrovaný šum/metalický mix, open hat ukončí closed (choke group)
- **Low / Mid / High tom** — laděný sinus s pitch envelope
- Každý hlas: vlastní řádek v sequenceru + knoby

Technicky:
- Žádné samply — vše z oscilátorů a šumového bufferu
- Neměnit scheduler z KOS-21, jen registrovat nové hlasy
