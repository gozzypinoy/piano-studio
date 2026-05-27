# Beginner Music Studio

A standalone offline HTML app for beginner piano practice, song play-along, fretboard mapping, chords, and backing-band practice.

Open `index.html` directly in a browser. No server, build step, npm install, external assets, or network access are required.

## Quick Start

```bash
open index.html
```

Best browser: Chrome or Edge, especially if using Web MIDI.

## What Changed

The app is now unified in `index.html`. The previous iframe launcher has been replaced with one integrated runtime based on the Play-Along Academy engine, with Studio features ported into the same page.

The older source files are kept as references:

- `play-along-academy.html`
- `accompaniment-studio.html`

## Main Sections

- **Play**: piano, falling-note lane, note display, full scale picker, MIDI, recording, guitalele, and ukulele.
- **Songs**: unified song picker, Play-Along, Practice mode, falling notes, difficulty, personal bests, A/B loop, tempo ramp, chord backing, drums, bass, and strings.
- **Chords**: chord progressions, Roman numerals, strum/arpeggio playback, reset BPM, and optional accompaniment.
- **Band**: mixer, drum pads, step sequencer, presets, saved patterns, and custom backing toggle.
- **🎮 Game**: Guitar-Hero-style dedicated game mode. Bigger lane, per-pitch-class note colours, arcade HUD (score/combo/×2 multiplier/accuracy/shields/progress), hit-tier popups (PERFECT/GREAT/GOOD/MISS), end-of-song grade screen (S/A/B/C/D + stars + NEW BEST badge), Retry / Next / Quit. Includes a local song import (MIDI + JSON).
- **Progress**: achievements and local-data reset tools.

## Features

- 25-key piano from C4 to C6.
- Guitalele and ukulele fretboard mapping.
- Full scale picker: 12 roots across Major, Minor, Major Pentatonic, and Minor Pentatonic.
- Synthesia-style falling notes.
- Play-Along scoring with hit tiers, combo, shields, milestones, and summaries.
- Practice mode that waits for the correct note.
- Easy, Normal, and Hard difficulty with Hard unlock.
- Personal bests and achievement badges.
- Web MIDI input.
- Recording mode for custom songs.
- Chord progressions with Roman numeral analysis.
- Drum pads and 16-step sequencer.
- Bass, strings, drums, and mixer buses.
- Sticky global transport with Stop.
- LocalStorage persistence.

## Persistence

The app keeps compatibility with older keys and also writes newer namespaced keys:

- `pianoDiff`
- `pianoBest_<song>_<difficulty>`
- `pianoBadges`
- `pianoSettings`
- `customSongs`
- `piano-beginner.settings.v2`
- `piano-beginner.progress.v2`
- `piano-beginner.badges.v2`
- `piano-beginner.custom-songs.v2`
- `piano-beginner.drum-patterns.v1` (legacy binary patterns; auto-migrated on first load)
- `piano-beginner.drum-patterns.v2` (velocity-aware patterns: per-step 0/1/2/3 = off/soft/medium/loud)

Use the **Progress** tab to clear local app data.

## Copyright Notes

Traditional/public-domain learning songs and original style studies are included for educational use. Famous-song-derived entries have been renamed as study pieces and simplified into copyright-safer practice material.

## Importing songs (personal use)

The **Game** tab has an **⬆ Import song** button that loads a chart from your local disk. Two formats are supported:

- **JSON** matching the app's `SONGS` shape: `{ name, notes: [{ m, b }, ...], defaultBpm, level }`. Optional fields: `desc`, `chordRoots`, `chordBeats`, `patternKey`.
- **MIDI** (`.mid` / `.midi`). The parser reads Standard MIDI Files, picks the most in-range track (you can switch via a dropdown in the preview), transposes notes by octaves to fit the 25-key C4–C6 range when possible, and snaps note durations to a 16th-note grid.

Imported songs are stored only in this browser's `localStorage` under the existing `customSongs` namespace. They are not bundled with the repo and never enter git.

**Legal posture** (Australia): copyright law has no general "personal use" exemption, but using a transcribed chart on your own machine — not shared, not hosted, not monetised — carries effectively zero enforcement risk. The risk lives in distribution: don't commit copyrighted chart data, don't host it on a public URL, don't redistribute the resulting `.html`. To make this easy, the repo includes a `.gitignore` that excludes `private-songs/` and `.mid`/`.midi` files in this folder — keep raw MIDI source files there.

Royalty-free / public-domain sources that work well:

- **Public-domain composers** (Bach, Beethoven, Pachelbel, traditional folk): try [IMSLP](https://imslp.org) or [MuseScore](https://musescore.com) public-domain section.
- **Creative-Commons game / film music**: [Kevin MacLeod (incompetech.com)](https://incompetech.com) — CC-BY, attribution required for distribution but unrestricted for personal play.

To export a chart back to JSON (e.g. to share with yourself across machines), click the **↓** button on a song card in the Game picker.

## Archive

Original source files from before consolidation are preserved here:

```text
../archive/piano-beginner-originals-2026-05-24/
```
