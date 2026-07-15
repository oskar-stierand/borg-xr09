# KOS-30 — Finish the English translation: CSS section comments

**Status:** Done (v1.10, PR #11)

## Description

Follow-up to KOS-28: six Czech CSS section comments in `index.html` were missed during the translation (ŠASI, HORNÍ BRANDING, PANEL S MODULY, KNOBY, PATTERN & PRESETY, TEMPO DISPLEJ). Found by a diacritics scan while checking that both repos are fully English.

## Solution

- Translated the six CSS section comments (CHASSIS, TOP BRANDING, MODULE PANEL, KNOBS, PATTERN & PRESETS, TEMPO DISPLAY) — comments only, no behavior changes
- Verified: zero Czech diacritics left anywhere in `index.html` and `*.md` (historical snapshots in `versions/` intentionally untouched)
