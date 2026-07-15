# KOS-26 — More factory presets

**Status:** Done (v1.6, PR #7)

## Description

Expand the factory preset selection with more genres.

Candidates:
- **Techno** — straight 4/4, offbeat open hats, minimal
- **Hip-hop (boom bap)** — ~90 BPM, heavy swing, kick/snare bounce
- **UK Garage / 2-step** — shuffle, skipped kicks
- **Reggaeton (dembow)** — 4/4 kick + snare on the "a" beats
- **Liquid DnB** — ~172 BPM, two-step (kick on 1 and 3&, snare on 2 and 4), rolling ghost snares, subtle swing (Technimatic / Alix Perez style)

Technical notes:
- Data only, in `FACTORY` + `<option>` in the select — engine unchanged
- After KOS-25, revisit the params of existing presets (voices sound different now)
