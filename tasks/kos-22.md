# KOS-22 — Rest of the drum kit (snare, clap, hi-hats, toms)

**Status:** Done (v1.2, PR #3)

## Description

Add the remaining synthesized voices to complete the 909 kit.

Scope:
- **Snare** — tone (two detuned oscillators) + noise burst, TUNE / TONE / SNAPPY / DECAY / LEVEL knobs
- **Clap** — filtered noise with a multiple-retrigger envelope (the typical 909 "flam")
- **Closed / Open hi-hat** — filtered noise/metallic mix, closed hat chokes the open hat (choke group)
- **Low / Mid / High tom** — tuned sine with a pitch envelope
- Each voice: its own sequencer row + knobs

Technical notes:
- No samples — everything from oscillators and a noise buffer
- Don't change the KOS-21 scheduler, just register the new voices
