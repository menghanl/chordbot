# ShapeRoll

Guitar fretboard practice tool. Pick notes from chord shapes on the fretboard, generate random sequences to practice.

## Features

- Interactive fretboard — click to select/deselect notes
- Presets for E-shape chords and arpeggios (Major, Maj7, Major Scale)
- Random note sequence generator with configurable bar count
- Jianpu (numbered notation) with octave dots
- String labels on each note
- Seeded PRNG — same seed produces the same sequence across refreshes
- Light/dark theme with localStorage persistence
- PWA — installable, works offline
- Responsive — desktop sidebar, tablet/phone stacked layout

## Usage

Open `index.html` in a browser, or visit the GitHub Pages deployment.

1. Pick a preset or click notes on the fretboard
2. Click **Generate** to roll a new random sequence
3. Practice the generated notes on your guitar

## Deploy

Static HTML/JS — no build step. Push to GitHub and enable Pages, or open `index.html` directly.

## Tech

Single `index.html` with embedded CSS and JS. No frameworks, no dependencies.
