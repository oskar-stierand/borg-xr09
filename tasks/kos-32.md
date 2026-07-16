# KOS-32 — README hero screenshot (+ fix missed Czech UI label)

**Status:** Done (v1.11, PR #12)

## Description

Add a single preview image to the README, right under the app title (no gallery — one image, capturing a nice pattern). Same recipe as KOS-31 in borg-xs20.

While preparing the shot, a Czech UI label surfaced that the translation (KOS-28/30) had missed.

## Solution

- `docs/screenshots/borg-xr09.png` — the **jungle** (amen break) factory preset loaded: BPM 165, the step grid lit with kick/snare/hi-hat hits and the accent row
- Embedded in README.md directly below the `# BORG XR-09` title
- **Fixed:** the grid header `Pattern — 16 Steps · click a track name to trigger` was still Czech (`klik na název nástroje = trig`). The diacritics were HTML-entity-encoded (`n&aacute;zev`), so the raw-diacritic scans in KOS-28/30 missed it. Same label also fixed in borg-studio (KOS-48).
- Reproducible capture: headless Chrome (`--headless=new`, `--force-device-scale-factor=1`, `--virtual-time-budget`) loads a scratchpad copy of `index.html` whose boot script calls `applyState(FACTORY['jungle'])` (the app has no URL state), then cropped to `#machine` with `sips`. The committed `index.html` is untouched by the capture harness.

## Notes for future screenshots

- XR-09 has no `?patch` URL state — inject a post-boot `applyState(FACTORY['<preset>'])` into a temp copy for a deterministic headless shot
- At window 1800×952 the `#machine` frame is x=360 y=97, 1080×758
