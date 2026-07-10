# CLAUDE.md — Instrukce pro Claude Code

Tento soubor popisuje jak pracovat s projektem BORG XR-09. Přečti ho vždy před jakoukoliv změnou kódu.

---

## Projekt

**BORG XR-09** je single-file webová drum machine („Rhythm Composer") v `index.html`, inspirovaná Rolandem TR-909 a podobnými nástroji. Žádný build, žádné závislosti, žádný Node.js — vše je v jednom souboru.

Všechny zvuky jsou **syntetizované ve Web Audio API** (žádné samply, žádné externí soubory) — kick, snare, clap, hi-hats, tomy atd. vznikají z oscilátorů a šumu, stejně jako v analogové/hybridní 909.

**Důležité:** Tento projekt je zcela samostatný. Nesahej na sesterský projekt `borg-xs20` (jiná složka, jiné repo) — slouží nanejvýš jako inspirace pro konvence.

Tasky jsou vedeny ve složce **`tasks/`** — jeden soubor na task, pojmenovaný `kos-{číslo}.md` (např. `tasks/kos-20.md`). Číslování začíná na **kos-20** (kos-1 až kos-18 patří projektu XS-20; formát je Linear-importovatelný a Oskar tasky později hromadně nahraje — strukturu neměnit).
Před každou prací načti soubory se statusem `Todo` z `tasks/`.

---

## Zásady práce s kódem

### ✅ Vždy
- **Chirurgické změny** — měň jen to co je v tasku. Jeden task = jedna izolovaná změna.
- **Syntax check** po každé změně: `node -e "new Function(js)"` na JS blok
- **Záloha před změnou** — zkopíruj aktuální `index.html` do `versions/index-vX.html`
- **Task update** — po dokončení tasku přepiš v `tasks/kos-XX.md` status na `Done (vX.Y, PR #N)`
- **Changelog** — po dokončení tasku přidej záznam nové verze do `CHANGELOG.md`
- **Vizuální změny nejdřív ukázat** — lokálně předvést, commit až po Oskarově schválení

### ❌ Nikdy
- Nespouštěj více vizuálních přepisů najednou
- Neměň audio engine a UI zároveň
- Nepřepisuj celé funkce pokud stačí opravit 2–3 řádky

---

## Struktura souboru `index.html` (stav v1.8)

```
<style>          ← veškerý CSS
<body>           ← HTML struktura drum machine
<script>
  // CONSTANTS & STATE      S objekt (tempo, banky A–D, params), DEFAULT_PARAMS,
  //                        registr INSTRUMENTS (8 hlasů — grid i sequencer se generují odsud)
  // AUDIO ENGINE
  //   initAudio()          master → analog bus (HP/LP + saturace) + paralelní komprese (COMP)
  //   drift()              per-hit humanizace (ladění, decay, hlasitost se úder od úderu liší)
  //   hlasy: playKick(), playSnare(), playClap(), playHat() (closed/open + choke), playTom()
  //          RC obálky (setTargetAtTime) místo digitálních ramp
  // SEQUENCER              lookahead scheduler nad Web Audio clockem (ne setInterval),
  //                        16 kroků, swing (offbeat 16tiny, 50–75 %), accent
  // UI — KNOBS             KNOB_DEFS: tempo (40–240 BPM), masterVol, swing, compMix
  //                        + tune/tone/snappy/decay/level per nástroj
  // UI — SEQUENCER GRID    8 řádků nástrojů + řádek ACCENT, pattern banky A–D s kopírováním
  // TRANSPORT              play/stop
  // PATTERNY & PRESETY     captureState()/applyState(), makePreset(),
  //                        9 factory presetů (house, breakbeat, jungle, electro, techno,
  //                        boombap, ukgarage, dembow, liquiddnb)
  // BOOT                   DOMContentLoaded
```

Poznámka: tento nákres průběžně aktualizuj, aby odpovídal realitě.

---

## Testování

Žádné automatické testy. Manuální checklist po každé změně:

- [ ] JS syntax check projde bez chyb
- [ ] Drum machine se načte v Chrome bez console errors
- [ ] Play/Stop funguje, sequencer běží v tempu bez driftu
- [ ] Kroky jdou zapínat/vypínat a hrají správné nástroje
- [ ] Patterny/presety se správně načítají (applyState)
- [ ] Zvuk hraje bez artefaktů (kliky, praskání)

---

## Git workflow

```bash
# Před každým taskem
git checkout -b kos-XX-kratky-popis

# Po dokončení
git add index.html
git commit -m "KOS-XX: stručný popis co bylo změněno"
git push origin kos-XX-kratky-popis
# → otevřít Pull Request na GitHubu (gh pr create)
```

Branch naming: `kos-{číslo}-{slug}` (stejný formát jako Linear `gitBranchName`).

---

## Komunikace

Projekt je vyvíjen česky. Commit messages jsou anglicky (konvence).
