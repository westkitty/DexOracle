# Audio Role Map — Nana Cheese Oracle

## Uploaded song stems

Source archive: `Happy Mother's Day! Stems (102BPM).zip`

| Runtime stage | Production files | Rendered source layers |
| --- | --- | --- |
| 0 | `assets/audio/music-stage-0.ogg`, `.mp3` | Synth |
| 1 | `assets/audio/music-stage-1.ogg`, `.mp3` | Synth + Percussion |
| 2 | `assets/audio/music-stage-2.ogg`, `.mp3` | Synth + Percussion + Bass |
| 3 | `assets/audio/music-stage-3.ogg`, `.mp3` | Synth + Percussion + Bass + Drums |
| 4 | `assets/audio/music-stage-4.ogg`, `.mp3` | Synth + Percussion + Bass + Drums + Guitar |
| 5 | `assets/audio/music-stage-5.ogg`, `.mp3` | Synth + Percussion + Bass + Drums + Guitar + Backing Vocals |
| 6 | `assets/audio/music-stage-6.ogg`, `.mp3` | Synth + Percussion + Bass + Drums + Guitar + Backing Vocals + Lead Vocals |
| 7 | `assets/audio/music-stage-7.ogg`, `.mp3` | Full mix: Synth + Percussion + Bass + Drums + Guitar + Backing Vocals + Lead Vocals + Other |

All song stages were rendered to the same 57.740354-second duration. Runtime playback starts all stage mixes together after the first user gesture, keeps them looping, and crossfades volume so new stems enter without restarting the song.

## Ambience and SFX

| Role | Production files | Notes |
| --- | --- | --- |
| Beach ambience | `assets/audio/beach-ambience.ogg`, `.mp3` | Procedural low-volume surf and distant bird bed, generated locally for clean redistribution. |
| Cheese coin | `assets/audio/sfx-cheese-coin.ogg`, `.mp3` | Small generated chime when a fortune dispenses. |
| Power-up | `assets/audio/sfx-power-up.ogg`, `.mp3` | Generated wake cue. |
| Dexter stamp | `assets/audio/sfx-dexter-stamp.ogg`, `.mp3` | Generated low stamp thunk on unlock. |

See `assets/audio/AUDIO_MANIFEST.md` for the compact runtime manifest.
