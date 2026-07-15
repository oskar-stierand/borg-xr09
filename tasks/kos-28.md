# KOS-28 — Translate the repository to English

**Status:** Done (v1.9, PR #10)

## Description

The public repo should be entirely in English; development communication with Oskar stays in Czech.

Scope:
- Translate README.md, CHANGELOG.md, and CLAUDE.md to English
- Translate all task files in `tasks/` (kos-20 through kos-27)
- Translate all code comments in `index.html` (comments only — no behavior changes)
- Add a language policy section to CLAUDE.md: repo content in English, conversation in Czech
- Going forward, new task files and changelog entries are written in English

Technical notes:
- The instrument UI was already in English (BASS DRUM, SNARE, …) — no UI changes
- Commit messages were already in English by convention
