# SATURNO MOVEMENT STUDIO — CLAUDE.md

## What This Is
"The Ableton of Movement" — a DAW-style workout composition tool where exercises are instruments, sets are bars, reps are beats, and BPM controls both music AND training tempo.

## Repo
- Path: ~/dev/saturno-movement-studio/
- GitHub: gabosaturno11/saturno-movement-studio
- Part of: Saturno Bonus ecosystem (linked from vault page)
- Ship deadline: Tuesday March 4, 2026

## Architecture
Single-file HTML app (index.html, ~1,400 lines). No build step. No framework.

### Structure
```
saturno-movement-studio/
  index.html          <- THE APP (everything in one file)
  assets/
    planet-logo.png   <- Favicon + logo (23KB)
    planet-logo.svg   <- SVG version (2.7KB)
  docs/
    MOVEMENT_COMPOSITION_ENGINE.md   <- BPM -> training mode theory
    SATURNO_UNIFIED_THEORY.md        <- 7-layer architecture spec
    README_MVP_HUB.md               <- Original product vision
  CLAUDE.md           <- THIS FILE
```

### Key Concepts
- **Movement Families as Instruments**: Push=Percussion, Pull=Bass, Legs=Rhythm, Core=Harmony, Skills=Lead, Flow=Ambient
- **BPM Training Modes**: 40-80=Slow Strength, 80-120=Standard, 120-160=Flow State, 160+=Explosive
- **Faders**: Intensity, Volume (exercise count), Density (rest ratio), Rest
- **Knobs**: Strength-Mobility, Power-Control, Static-Dynamic
- **Tempo Linking**: BPM changes -> music playback rate + exercise tempo per rep

### Exercise Database
58 exercises from Victory Belt CC movement matrix:
- 7 patterns: Horizontal Push (9), Horizontal Pull (6), Downward Press (6), Vertical Pull (9), Overhead Press (6), Knee-Dominant (7), Hip-Dominant (4)
- Plus: Core (6), Mobility (7)
- 3 stages per exercise (progression difficulty)
- 6 disciplines: Calisthenics, Power-Free, Bodybuilding, Street Lifting, Hand-Balancing, Freestyle, Mobility

### Presets (8 total)
- Monk Mode (65 BPM), Beast Mode (140 BPM), Flow Ritual (100 BPM), Skill Ascension (75 BPM)
- Upper Day (100 BPM), Lower Day (90 BPM), Push/Pull/Legs (110 BPM), Full Body (105 BPM)

### Music
4 ASTRA tracks from Vercel Blob CDN:
- Celestial Reverie, Blue Phoenix, Veil of Truth, Astral Shadows
- Music track in timeline with dropdown selector
- BPM-to-playback-rate linking (120 BPM = 1.0x)

## Design Constraints
- Dark theme: cosmic blue palette (#050711 base)
- Sora font (no JetBrains Mono, no Inter)
- No transition:all (use specific properties)
- No emojis in code
- var/function (not const/let/arrow) for compatibility
- localStorage wrapped in try-catch
- prefers-reduced-motion supported

## Source References
- ~/dev/saturno-bonus/tools/saturno-movement-studio/ (original 4,548-line version)
- /tmp/saturno-movement-daw/ (232-line prototype, the one that "played music")
- ~/dev/victory-belt-cc/data/movement_matrix.json (72 exercises, 264 transfer edges)
- /Volumes/G-DRIVE ArmorATD/CONSOLIDATION_FEB10/01_TITAN_FORGE_CANONICAL/titan-forge/movement-studio.html (236-line prototype)
- /tmp/saturno-hub/ (content manager, different purpose)
