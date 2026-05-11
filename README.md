# The Nana Cheese Oracle — Full-Screen Audio Build

Open `index.html` in a browser. No server, internet connection, libraries, fonts, or build tools are required.

## What this version does

This version keeps the Oracle as a full-screen diegetic boardwalk attraction. The boardwalk and machine remain the interface. No side panel, no dashboard, no detached control card. The visible UI is intentionally transparent and anchored to the scene.

Interaction flow:

1. Ocean / boardwalk opening loop.
2. Tap the boardwalk callout to approach the machine.
3. Tap the coin-slot callout to wake Dexter.
4. Tap the crystal-ball / machine callout to consult Dexter.
5. A different consult animation is selected each time, avoiding the same repeated crystal-ball touch.
6. A ticket dispenses from the machine area.
7. Nana Cheese Energy lights one bulb per consultation.
8. Each energy step crossfades to a richer song stage rendered from the uploaded stems.
9. Seven consultations unlock the Official Dexter Approval Stamp.
10. Consulting remains available after unlock.
11. Reset returns to the ocean opening without stopping the looped audio bed.

## Audio behavior

Browsers require a user gesture before audio can play. Sound starts on the first scene interaction or when the small `Sound On` control is pressed.

Audio assets live in `assets/audio/`.

- `music-stage-0` through `music-stage-7` are rendered from the uploaded `Happy Mother's Day! Stems (102BPM).zip`.
- Stage 0 starts with synth.
- Each Nana Cheese Energy step adds another piece: percussion, bass, drums, guitar, backing vocals, lead vocals, then the final other layer.
- All music stages share the same loop length so the song can run continuously while the app crossfades between stage mixes.
- `beach-ambience` is a low-volume procedural waves / distant bird bed generated locally for clean redistribution.
- Small generated interaction sounds are included for the imaginary cheese coin, power-up, and Dexter stamp.
- OGG is used first, with MP3 fallback for browsers that need it.

## Video behavior

The core state videos remain:

- `assets/video/ocean-loop.mp4`
- `assets/video/boardwalk-approach.mp4`
- `assets/video/machine-wake.mp4`
- `assets/video/machine-idle.mp4`

Consulting now has multiple variants in `assets/video/consult/`:

- `machine-consult-glow.mp4`
- `machine-consult-bulbs.mp4`
- `machine-consult-ticket.mp4`
- `machine-consult-stare.mp4`
- `machine-consult-orbit.mp4`
- `machine-consult-closeup.mp4`

The runtime picks a weighted non-immediate-repeat variant and adds small camera nudges plus localized flash transitions between clips.

## Editing fortunes

Fortunes live in `assets/data/fortunes.js` as an easy-to-edit array of 100 objects.

## Accessibility notes

- Hotspots are real buttons.
- The sound toggle and reset are real buttons.
- The energy bulbs expose `role="meter"`.
- Status and fortunes update an `aria-live` region.
- The build respects `prefers-reduced-motion` by using still fallbacks instead of long video transitions.
## GitHub Pages deployment

This repository is prepared for GitHub Pages with `.github/workflows/deploy-pages.yml`. The workflow uploads the static root as a Pages artifact and deploys it from `main`. Expected project URL after Pages is enabled and the workflow completes:

`https://westkitty.github.io/DexOracle/`

Mobile is a first-class target: the viewport uses `viewport-fit=cover`, coarse-pointer tap targets are enlarged, phone breakpoints reposition hotspots and the ticket, and portrait media is allowed to fill the screen instead of shrinking into a tiny card.

