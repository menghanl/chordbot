# ChordBot — Chord Relationship Graph

## Chords

| Symbol | Name | Formula |
|--------|------|---------|
| Major | Major Triad | 1, 3, 5 |
| m | Minor | 1, b3, 5 |
| maj7 | Major 7th | 1, 3, 5, 7 |
| 7 | Dominant 7th | 1, 3, 5, b7 |
| m7 | Minor 7th | 1, b3, 5, b7 |
| m7b5 (ø7) | Half-diminished | 1, b3, b5, b7 |
| dim7 (°7) | Diminished 7th | 1, b3, b5, bb7 |

## Scales

| Name | Formula |
|------|---------|
| Major (Ionian) | 1, 2, 3, 4, 5, 6, 7 |
| Minor (Aeolian) | 1, 2, b3, 4, 5, b6, b7 |
| Dorian | 1, 2, b3, 4, 5, 6, b7 |
| Mixolydian | 1, 2, 3, 4, 5, 6, b7 |

## Relationships

Each edge describes the modification to go from parent to child.

```
Major (1, 3, 5)
├─[b3]──→ Minor (1, b3, 5)
│            └─[+b7]──→ Minor 7th (1, b3, 5, b7)
│                          ├── Minor Scale
│                          ├── Dorian Scale
│                          └─[b5]──→ Half-dim / m7b5 (1, b3, b5, b7)
│                                      └─[bb7]──→ Dim7 (1, b3, b5, bb7)
├─[+7]──→ Major 7th (1, 3, 5, 7)
│            └── Major Scale
└─[+b7]─→ Dominant 7th (1, 3, 5, b7)
             ├── Mixolydian Scale
             └─[b3]──→ Minor 7th (same node as above)
```

### Edge List

| From | To | Modification |
|------|----|--------------|
| Major | Minor | flatten 3rd → b3 |
| Major | Major 7th | add natural 7th (+7) |
| Major | Dominant 7th | add flat 7th (+b7) |
| Minor | Minor 7th | add flat 7th (+b7) |
| Dominant 7th | Minor 7th | flatten 3rd → b3 |
| Minor 7th | Half-diminished | flatten 5th → b5 |
| Half-diminished | Diminished 7th | flatten b7 → bb7 |

### Chord → Scale Links

| Chord | Scale |
|-------|-------|
| Major 7th | Major (Ionian) |
| Minor 7th | Minor (Aeolian) |
| Minor 7th | Dorian |
| Dominant 7th | Mixolydian |

## Library

**svguitar** — vanilla JS, SVG chord diagrams, no build tools.
- GitHub: https://github.com/omnibrain/svguitar
- CDN: `https://unpkg.com/svguitar@latest/dist/svguitar.umd.js`
- Supports: fingers, barres, open/muted strings, titles, position markers

## E-Shape Barre Chord Voicings

All E-shape chords have the root on the 6th (low E) string.
Fret numbers are relative to barre position N.
Strings numbered 6 (low E) to 1 (high E).

Barre at fret N on all 6 strings gives intervals: 1, 4, b7, b3, 5, 1

### Major — E shape

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+2  N+2  N+1   N    N
Interval: 1    5    1    3    5    1
Barre: strings 1-6 at fret N
```

Arpeggio (1, 3, 5) — all chord tones in the position box:
```
Fret:  N-1   N   N+1   N+2
  6:        [1]
  5:  [3]               [5]
  4:                     [1]
  3:              [3]
  2:        [5]
  1:        [1]
```

### Major 7th — E shape

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+2  N+1  N+1   N    N
Interval: 1    5    7    3    5    1
Barre: strings 1-6 at fret N
Diff from Major: string 4 drops from N+2 to N+1 (7th instead of root)
```

Arpeggio (1, 3, 5, 7) — all chord tones in the position box:
```
Fret:  N-1   N   N+1   N+2
  6:        [1]
  5:  [3]               [5]
  4:              [7]   [1]
  3:              [3]
  2:        [5]
  1:  [7]  [1]
```

### Major Scale (Ionian) — E shape

Scale pattern (1, 2, 3, 4, 5, 6, 7):
```
Fret:  N-1   N   N+1   N+2
  6:        [1]         [2]
  5:  [3]  [4]          [5]
  4:  [6]        [7]   [1]
  3:  [2]        [3]   [4]
  2:        [5]         [6]
  1:  [7]  [1]          [2]
```

### Dominant 7th — E shape (future)

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+2   N   N+1   N    N
Interval: 1    5   b7    3    5    1
Barre: strings 1-6 at fret N
Diff from Major: string 4 drops from N+2 to N (b7 instead of root)
```

### Minor — E shape (future)

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+2  N+2   N    N    N
Interval: 1    5    1   b3    5    1
Barre: strings 1-6 at fret N
Diff from Major: string 3 drops from N+1 to N (flatten 3rd)
```

### Minor 7th — E shape (future)

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+2   N    N    N    N
Interval: 1    5   b7   b3    5    1
Barre: strings 1-6 at fret N
Diff from Major: string 4 to N (b7), string 3 to N (b3)
```

### Half-diminished (m7b5) — E shape (future)

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+1   N    N    x    x
Interval: 1   b5   b7   b3
Strings 2 and 1 muted
Diff from Minor 7th: string 5 drops from N+2 to N+1 (b5)
```

### Diminished 7th — E shape (future)

Chord:
```
String:  6    5    4    3    2    1
Fret:    N   N+1  N-1   N    x    x
Interval: 1   b5  bb7   b3
Strings 2 and 1 muted
Diff from Half-dim: string 4 drops from N to N-1 (bb7)
```
