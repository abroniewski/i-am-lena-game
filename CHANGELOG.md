# Changelog

## 0.1.0 — 2026-11-10

iPad playable after name entry; mid-mission progress survives refresh.

### Added
- Mid-mission progress is saved on this device (mission counters, Oskar’s Pizza ingredients, paintings, balloons), so a refresh does not wipe what you already collected

### Fixed
- Game no longer dies on older iPad Safari (`canvas.roundRect` missing), which left a blank sky-blue screen after the name gate
- Name gate stays up with a loading state until the house finishes booting, instead of flashing empty sky
- Three.js / cannon load via relative module paths (more reliable than an import map on some iPads)
- GRAB / JUMP / SHELL labels stay centred on iPad Safari (default button padding no longer shifts them)
