# Project Bible — The Nana Cheese Oracle

## Current State Summary

The Nana Cheese Oracle has been rebuilt as a full-screen local/offline web artifact. The boardwalk and fortune machine are the interface. All primary controls are diegetic scene hotspots, not side panels or dashboard controls.

## Artifact Registry

- `index.html` — full-screen interactive Oracle, all CSS/interaction logic embedded except fortune data.
- `assets/data/fortunes.js` — 100 editable fortune objects, weighted by category in runtime logic.
- `assets/img/ocean-poster.jpg` — ocean fallback still.
- `assets/img/machine-off-curtain.jpg` — dormant machine fallback still.
- `assets/img/machine-on-dexter.jpg` — active Dexter fallback still.
- `assets/video/ocean-loop.mp4` — trimmed forward/reverse ocean ping-pong loop.
- `assets/video/boardwalk-approach.mp4` — trimmed one-shot approach transition.
- `assets/video/machine-wake.mp4` — trimmed wake/reveal clip with unrelated ocean frame removed.
- `assets/video/machine-idle.mp4` — trimmed forward/reverse active Dexter idle ping-pong loop.
- `assets/video/machine-consult.mp4` — trimmed consult/glow one-shot.
- `README.md` — local usage and editing notes.
- `dev-notes/ASSET_ROLE_MAP.md` — production asset role map and processing notes.

## Chronological Ledger

### Entry 001 — 2026-05-10 — Full-screen rebuild and package

- Interpreted the correction brief as mandatory: no external control panel, no side dashboard, no separate menu. The machine and boardwalk must contain the interaction model.
- Inspected the uploaded asset archive and previous fixed zip.
- Confirmed available source roles: ocean loop, approach clip, dormant machine still, wake clip, active idle clip, consult/glow clips, active and dormant stills.
- Generated contact sheets for source stills and videos to visually audit asset content.
- Selected production assets matching the prior role map while correcting the interface model.
- Processed video with ffmpeg:
  - Ocean was trimmed and rendered as a forward/reverse ping-pong loop.
  - Idle Dexter was cut to a calmer scan and rendered as a forward/reverse ping-pong loop.
  - Approach was trimmed to end cleanly on the dormant machine.
  - Wake was trimmed to remove the unrelated initial ocean frame.
  - Consult was trimmed to a compact glow beat; the printed ticket is rendered with CSS for readability and alignment.
- Rebuilt the page as a fixed full-viewport scene with a single image layer, a single video layer, blurred backplate support for vertical media, small callout hotspots, in-world energy bulbs, a physical ticket slip, and a machine-area approval stamp.
- Implemented the state machine: OCEAN -> APPROACH -> MACHINE_OFF -> WAKING -> READY -> CONSULTING -> DISPENSING -> READY/UNLOCKED.
- Added reduced-motion fallbacks, `aria-live` status, real button hotspots, keyboard-focus styling, and a secondary reset affordance.
- Created a downloadable package zip at `/mnt/data/nana-cheese-oracle-fullscreen.zip`.

## Open Questions

- Hotspot coordinates are tuned to the provided vertical art and common desktop/mobile viewports. Final human visual testing in the target browser/device is still recommended, because exact object-fit composition differs slightly by browser and viewport.
- Headless Chromium screenshot capture in the container did not complete reliably, apparently due container/headless environment issues rather than project syntax. Static JavaScript syntax checks and asset path checks were performed.

### Entry 002 — 2026-05-10 — Stem-integrated audio, consult variants, and transition polish

- Integrated the uploaded `Happy Mother's Day! Stems (102BPM).zip` as staged song power levels.
- Rendered eight synchronized stage mixes from the stems:
  - Stage 0: synth.
  - Stage 1: synth + percussion.
  - Stage 2: adds bass.
  - Stage 3: adds drums.
  - Stage 4: adds guitar.
  - Stage 5: adds backing vocals.
  - Stage 6: adds lead vocals.
  - Stage 7: adds other/full mix.
- Implemented a runtime audio engine that starts after the first user gesture, keeps all music stages looping from the same origin, and crossfades between stages as Nana Cheese Energy increases.
- Added low-volume beach ambience as a locally generated procedural surf / distant-bird bed to avoid third-party redistribution problems while satisfying the requested waves/seagulls atmosphere.
- Added generated local SFX for cheese coin, wake power-up, and Dexter stamp.
- Added a transparent `Sound On/Off` in-scene corner control.
- Reprocessed six consult video variants from the original source archive and placed them under `assets/video/consult/`.
- Updated runtime consult selection to use weighted non-immediate-repeat variants so Dexter does not repeat the same crystal-ball-touch animation every consult.
- Added localized flash transitions and subtle camera motion variants (`push`, `drift-left`, `drift-right`, `settle`, `consult-close`) to soften clip joins and make the machine feel less static.
- Reduced UI overlay opacity for plaques, labels, gauge, ticket, reset, and sound controls so the artwork remains more visible.
- Added `dev-notes/AUDIO_ROLE_MAP.md` and `dev-notes/VIDEO_VARIANTS.md`.

## Open Questions Update

- The audio loop is rendered to a common exact OGG duration and a common MP3 fallback duration; native browser loop behavior should be acceptable, but the final subjective seam should still be listened to on the intended browser/device. Browser audio engines are rude little gremlins.
- External beach ambience sourcing was not embedded. A procedural ambience bed was generated locally instead, keeping the package offline and redistribution-clean.

### Entry 003 — 2026-05-11 — GitHub Pages deployment package and mobile hardening

- Prepared the full-screen audio build as a repository-root GitHub Pages site for `westkitty/DexOracle`.
- Added/verified `.github/workflows/deploy-pages.yml` using the official Pages artifact/deploy flow.
- Added `.nojekyll` so GitHub Pages serves the static assets without Jekyll processing.
- Added `404.html` as a copy of `index.html` so project-site fallback routes keep the Oracle visible.
- Hardened mobile behavior: viewport safe-area support, coarse-pointer tap targets, phone-specific hotspot placement, smaller transparent controls, bottom-anchored readable fortune ticket, and portrait media filling the screen instead of shrinking into a letterboxed card.
- Local validation confirmed 100 fortunes, 30/30/40 category split, all local asset references present, workflow file present, and mobile CSS checks present.
- Push to GitHub could not be completed from this container because DNS resolution for `github.com` fails and the available GitHub connector exposes read/search tools only, despite showing admin/push permissions on the repository.
