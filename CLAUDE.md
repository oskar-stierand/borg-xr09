# CLAUDE.md — Instructions for Claude Code

This file describes how to work on the BORG XR-09 project. Always read it before making any code change.

---

## Project

**BORG XR-09** is a single-file web drum machine ("Rhythm Composer") in `index.html`, inspired by the Roland TR-909 and similar instruments. No build, no dependencies, no Node.js — everything lives in one file.

All sounds are **synthesized with the Web Audio API** (no samples, no external files) — kick, snare, clap, hi-hats, toms etc. are built from oscillators and noise, just like in an analog/hybrid 909.

**Important:** This project is fully standalone. Do not touch the sister project `borg-xs20` (different folder, different repo) — at most it serves as inspiration for conventions.

Tasks are tracked in the **`tasks/`** folder — one file per task, named `kos-{number}.md` (e.g. `tasks/kos-20.md`). Numbering starts at **kos-20** (kos-1 through kos-18 belong to the XS-20 project; the format is Linear-importable and Oskar will bulk-upload the tasks later — do not change the structure).
Before starting any work, read the files with status `Todo` in `tasks/`.

---

## Working rules

### ✅ Always
- **Surgical changes** — only change what the task asks for. One task = one isolated change.
- **Syntax check** after every change: `node -e "new Function(js)"` on the JS block
- **Backup before changing** — copy the current `index.html` to `versions/index-vX.html`
- **Task update** — after finishing a task, set the status in `tasks/kos-XX.md` to `Done (vX.Y, PR #N)`
- **Changelog** — after finishing a task, add an entry for the new version to `CHANGELOG.md`
- **Show visual changes first** — demo locally, commit only after Oskar approves

### ❌ Never
- Don't run multiple visual rewrites at once
- Don't change the audio engine and the UI at the same time
- Don't rewrite whole functions when fixing 2–3 lines is enough

---

## Structure of `index.html` (as of v1.8)

```
<style>          ← all CSS
<body>           ← drum machine HTML structure
<script>
  // CONSTANTS & STATE      S object (tempo, banks A–D, params), DEFAULT_PARAMS,
  //                        INSTRUMENTS registry (8 voices — grid and sequencer are generated from it)
  // AUDIO ENGINE
  //   initAudio()          master → analog bus (HP/LP + saturation) + parallel compression (COMP)
  //   drift()              per-hit humanization (tuning, decay, level vary hit to hit)
  //   voices: playKick(), playSnare(), playClap(), playHat() (closed/open + choke), playTom()
  //           RC envelopes (setTargetAtTime) instead of digital ramps
  // SEQUENCER              lookahead scheduler on top of the Web Audio clock (not setInterval),
  //                        16 steps, swing (offbeat 16ths, 50–75%), accent
  // UI — KNOBS             KNOB_DEFS: tempo (40–240 BPM), masterVol, swing, compMix
  //                        + tune/tone/snappy/decay/level per instrument
  // UI — SEQUENCER GRID    8 instrument rows + ACCENT row, pattern banks A–D with copy
  // TRANSPORT              play/stop
  // PATTERNS & PRESETS     captureState()/applyState(), makePreset(),
  //                        9 factory presets (house, breakbeat, jungle, electro, techno,
  //                        boombap, ukgarage, dembow, liquiddnb)
  // BOOT                   DOMContentLoaded
```

Note: keep this sketch up to date so it matches reality.

---

## Testing

No automated tests. Manual checklist after every change:

- [ ] JS syntax check passes without errors
- [ ] The drum machine loads in Chrome without console errors
- [ ] Play/Stop works, the sequencer runs in tempo without drift
- [ ] Steps can be toggled on/off and trigger the right instruments
- [ ] Patterns/presets load correctly (applyState)
- [ ] Sound plays without artifacts (clicks, crackling)

---

## Git workflow

```bash
# Before each task
git checkout -b kos-XX-short-slug

# When done
git add index.html
git commit -m "KOS-XX: short description of what changed"
git push origin kos-XX-short-slug
# → open a Pull Request on GitHub (gh pr create)
```

Branch naming: `kos-{number}-{slug}` (same format as Linear `gitBranchName`).

---

## Language & communication

Conversation with Oskar happens **in Czech**. Everything in the repository is **in English**: code comments, docs (README, CHANGELOG), task files in `tasks/`, commit messages, and PR descriptions.
