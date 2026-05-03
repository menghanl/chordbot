# ChordBot — Future Ideas

## Rewrite to Svelte + Vite
- Migrate from single-file vanilla HTML/JS to Svelte components
- Vite for dev server + build
- GitHub Actions for auto-deploy to Pages
- Plan saved in session — component breakdown, file structure, migration steps all mapped out

## Formula-based fretboard (replace hand-picked presets)
- Define chords/scales by semitone formula only (e.g. Major Arp = [0, 4, 7])
- Compute ALL positions where chord tones appear across the full fretboard
- Highlight shape zones (E, A, D, G, C) as colored regions
- No more hand-picked per-shape preset data — eliminates wrong-note bugs
- Shapes become just "which fret region to focus on"
- Zone filter: only select notes within N frets of a shape's root
- Makes adding D, G, C shapes trivial

## More CAGED shapes
- Add D, G, C shape root positions and zone highlights
- Depends on formula-based fretboard (above) to avoid hand-picking explosion

## Multi-exercise mode
- Show multiple generated outputs at once (e.g. Maj7 16 bars + Maj9 16 bars)
- Each exercise: own preset selection, own note pool, own output
- Fretboard scrolls to whichever exercise is focused
- Option A: shared fretboard that follows focus
- Option B: each exercise has its own fretboard (collapsible)

## Tab-style output
- Replace interval cards with guitar tablature rendering
- 6-line tab showing string + fret numbers
- More natural for guitar players reading the generated practice

## Audio playback
- Play generated sequences using Web Audio API or tone.js
- Metronome click track
- Adjustable BPM

## A-shape preset corrections
- User noted they'll fix remaining wrong A-shape notes as they find them
- Current presets were verified systematically but may still have issues