# SATURNO MOVEMENT STUDIO — CLAUDE.md

## What This Is
"The Ableton of Movement" — a DAW-style workout composition tool where exercises are instruments, sets are bars, reps are beats, and BPM controls both music AND training tempo.

## Repo
- Path: ~/dev/saturno-movement-studio/
- GitHub: gabosaturno11/saturno-movement-studio
- Part of: Saturno Bonus ecosystem (linked from vault page)
- Ship deadline: Tuesday March 4, 2026

## Architecture
Single-file HTML app (index.html, ~8,400 lines). No build step. No framework.

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

## Design Lock V3.0 — "Endel x Craft x Logic Pro"
- Dark theme: cosmic blue palette (#050711 base)
- Sora font (no JetBrains Mono, no Inter)
- No transition:all (use specific properties)
- No emojis in code
- var/function (not const/let/arrow) for compatibility
- localStorage wrapped in try-catch
- prefers-reduced-motion supported
- **UNBOXED**: No pill borders on display elements (tags, badges, nav buttons)
- **Text hierarchy** over box styling: color + weight + size = visual structure
- **Gradient lock**: --gradient-cosmic, --gradient-titan, --glow-cyan CSS vars

### Features (Batches 1-159)
- Multi-track timeline (Push, Pull, Core, Legs, Skills, Music)
- 58 exercises with drag-and-drop from library to timeline
- Solo/Mute tracks, clip resize, clip drag, multi-select
- Copy/paste/duplicate clips (Cmd+C/V/D)
- Split clips at playhead (B key)
- Undo/redo with 30-step history
- 8 presets (Monk Mode to Full Body)
- Random workout generator
- BPM modes with music playback rate linking (120 BPM = 1.0x)
- Tap tempo (T key, rolling 8-tap average)
- Knobs (Strength-Mobility, Power-Control, Static-Dynamic)
- Faders (Intensity, Volume, Density, Rest)
- VU meters per family
- Right-click context menu with 18+ actions (includes Stage Up/Down, Reset Fades)
- **Workout Summary panel** (SUMMARY button): fullscreen overlay, A1/B1/C1 indexing, unboxed params, interactive progression chains
- **Exercise notes**: Craft-style annotations per clip (textarea in inspector)
- **Clip color picker**: 7 colors in context menu (Ableton-style)
- Print worksheet: Craft-minimalist design with notes, RPE, est. duration
- Session save/load/auto-save with debounce (includes markers + workout name + recent exercises)
- Save as named workout, load saved workouts (up to 20)
- JSON export/import (includes markers, fades, custom colors)
- Command palette (Cmd+K, 41 commands)
- Keyboard shortcuts panel (?, 35 shortcuts)
- Video reference panel (VID) with drag-drop loading
- Music player with 4 ASTRA tracks + track selector dropdown + time display
- Focus mode (F key)
- Zoom (6 levels: 50%-200%, Cmd+/-, wheel, slider, FIT)
- Auto-scroll during playback (FOLLOW button, synced with settings)
- Footer stats (clips, duration, bars, session timer, family balance)
- Header breadcrumb with workout name
- **Inline prompt modal** (replaces native prompt() for rename/save)
- **Craft-style tooltips** (data-tip on ALL interactive elements — 100% coverage)
- **Multi-select action bar** (Copy/Dup/Quantize/Delete when 2+ clips selected)
- **Inspector quick actions** (DUP/SPLIT/DEL buttons below notes)
- **Inspector progression chain** (S1/S2/S3 pills, click to swap exercise in-place)
- **Metronome downbeat accents** (1500Hz downbeat, 1000Hz offbeat, volume-aware)
- **Beat dot animation** (cyan dots pulse on beat during playback)
- **Time signature support** (4/4, 3/4, 6/8, 5/4, 7/8 — affects metronome, dots, ruler)
- **Marker persistence** (session save/load, undo/redo, JSON export/import)
- **Toast slide animation** (slide-up entrance with blur backdrop)
- **Recently used exercises** panel (last 5 with drag-drop, persists in session)
- **Marquee rubber-band selection** on timeline
- **Clip hover micro-interactions** (1px lift, brightness boost, drag lift effect)
- **Clip fade handles** (drag to set fade in/out, visual gradient overlay, persists)
- **Grid-aware snap** (gridRes setting affects SNAP_SIZE via BPM calculation)
- **Auto-save debounce** (300ms, Cmd+S bypasses for immediate save)
- **Escape deselects** (clips deselected before stopping playback)
- **Shuffled footer hints** (Fisher-Yates randomization, feels organic)
- **Draggable loop region** (Option+drag ruler to set, handles to resize, body to move)
- **Loop persistence** (save/load, undo/redo, export/import — full round-trip)
- **Library collapse memory** (localStorage persists which categories are open/closed)
- **Clip overlap flash warning** (pulse animation + toast when new overlaps detected)
- **Arrow key clip resize** (Alt+Arrow to resize, Up/Down to move between tracks)
- **Command palette** (Cmd+K, 44 commands including Move Up/Down, Delete Selected)
- **Keyboard shortcuts panel** (?, 38 shortcuts including Alt+Arrow, ruler loop drag)
- **Auto-scroll to selected clip** (timeline scrolls to show clip when selected)
- **Clip duration display** (shows seconds on clip: "3x8 15s", updates on resize)
- **Zoom follows cursor** (mouse wheel zoom centers on cursor position)
- **Double-click ruler markers** (dblclick ruler to add marker at position)
- **Playhead return-to-start** (stop returns to play start, double-stop to zero)
- **Clip-to-clip edge snapping** (magnetic snap to sibling clip edges, 6px threshold)
- **Colored waveforms** (family color used in all resize/split operations)
- **Gradient clip name mask** (CSS mask-image fade instead of hard ellipsis)
- **Minimap loop region** (blue overlay + marker dots in minimap overview)
- **Sorted Tab cycling** (Tab cycles clips in track-then-position order)
- **Empty state keyboard hints** (P/G/Cmd+K/? badges shown when no clips)
- **Snap badge grid resolution** (SNAP badge shows "SNAP 4B" when active)
- **Tap tempo feedback** (BPM + tap count in toast)
- **Clip grouping** (Cmd+G to group, Cmd+Shift+G to ungroup, grouped clips move together)
- **Alt+drag duplicate** (Alt+drag clips to create copies in-place)
- **Ruler drag-to-scrub** (mousedown+drag on ruler scrubs playhead in real-time)
- **RPE-scaled waveforms** (waveform amplitude scales with RPE for visual "loudness")
- **Estimated workout time** (footer shows est. time from sets x reps x tempo + rest)
- **Workout intensity score** (0-100 score in footer: volume + RPE + diversity)
- **Mute/solo aware playback** (muted tracks skip progress animation)
- **Record-mode quick-add** (R then 2-6 drops exercise at playhead on family track)
- **Track state persistence** (solo/mute/collapsed persist in session save/load)
- **Clip tooltips** (data-tip on clips with exercise name, family, stage, discipline)
- **Superset detection** (cross-track overlaps show purple "SS" badge + footer count)
- **Browser title sync** (document.title updates with workout name)
- **Library stage filter** (S1/S2/S3/All buttons to filter by exercise difficulty)
- **Library discipline filter** (dropdown to filter by Calisthenics/Power-Free/etc.)
- **Copy workout as text** (COPY TEXT button in summary, clipboard-ready plain text)
- **Minimap seek** (click minimap to jump playhead)
- **Workout share via URL** (#share= base64 encoded, clipboard copy)
- **Playback speed control** (0.5x-2x, transport button, SPEED_STEPS cycle)
- **BPM mode ambient tint** (subtle box-shadow on timeline from mode color)
- **Settings persistence** (snap, grid res, SFX, metro vol, auto-scroll, playback speed, zoom, time sig)
- **Playhead time persistence** (survives page reload)
- **Auto-inspect during playback** (inspector follows clip under playhead)
- **Knob persistence** (knob positions saved/restored in session)
- **Clear all markers** (command palette, with undo)
- **Reverse track clip order** (mirrors positions on active track)
- **Faders + knobs in export/import** (JSON round-trip)
- **Workout difficulty badge** (Beginner/Intermediate/Advanced in footer)
- **Knob double-click reset** (reset to 50% center)
- **Fader double-click reset** (reset to 50%)
- **Undo/redo count toast** ("Undo (3 left)" feedback)
- **Reset all faders/knobs** (command palette actions)
- **Clip lock system** (Cmd+L, context menu, visual lock indicator, persists all 6 state paths)
- **Humanize clips** (random position jitter for organic feel)
- **Export CSV** (tabular spreadsheet export)
- **Invert selection** (Cmd+I toggles selected/unselected)
- **RPE shortcuts** (Shift+Up/Down adjusts RPE on selected clip)
- **Select track clips** (Cmd+Shift+A selects only active track clips)
- **Spread clips evenly** (distributes clips with equal gaps on active track)
- **Session timer persistence** (cumulative timer survives page reload)
- **Print discipline/stage** (print worksheet shows discipline + stage per exercise)
- **Nudge sets/reps** ([ ] for sets, Shift+[ ] for reps on selected clip)
- **Nudge tempo/rest** (, . for tempo, Shift+, . for rest on selected clip)
- **updateClipInfo helper** (syncs clip label when params change via keyboard)
- **Alt+Up/Down duplicate to track** (copies clip to adjacent track preserving all props)
- **Collapse track keyboard** (C key toggles active track collapse)
- **Marker navigation** (N / Shift+N jumps playhead to next/prev marker)
- **Home/End jump** (Home to start, End to last clip end)
- **Stage up/down keyboard** (PgUp/PgDn swaps exercise to next/prev progression stage)
- **Clear track clips** (clears only active track, command palette)
- **Auto-name workout** (generates name from dominant family + mode + count)
- **Summary discipline stats** (shows est. minutes + discipline tags in summary panel)
- **Copy text improvements** (includes exercise count + est. duration in header)
- **CSV color/lock columns** (Color + Locked columns in CSV export)
- **Session creation date** (tracked across save/load/export/import)
- **Print creation date** (shows "Created" date in print meta bar)
- **Arrow scrub playhead** (Left/Right scrubs by beat when no clip selected, Shift=bar)
- **Paste at playhead** (Cmd+Shift+V pastes clips aligned to current playhead position)
- **Command palette** (Cmd+K, 70+ commands including paste-at-playhead, auto-name)
- **Keyboard shortcuts panel** (?, 55+ shortcuts including []/,. nudge, PgUp/PgDn)

## Source References
- ~/dev/saturno-bonus/tools/saturno-movement-studio/ (original 4,548-line version)
- /tmp/saturno-movement-daw/ (232-line prototype, the one that "played music")
- ~/dev/victory-belt-cc/data/movement_matrix.json (72 exercises, 264 transfer edges)
- /Volumes/G-DRIVE ArmorATD/CONSOLIDATION_FEB10/01_TITAN_FORGE_CANONICAL/titan-forge/movement-studio.html (236-line prototype)
- /tmp/saturno-hub/ (content manager, different purpose)
