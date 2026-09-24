![Reload Bench](og-image.png)

# Reload Bench

A browser-based sound design tool for game developers. It synthesizes weapon foley from scratch (reload sequences,
single gunshots and bullet impacts) and exports the results as WAV files ready to drop into a game engine.

**Try it:** https://joonas98.github.io/reload-bench/

Every sound is generated in the visitor's browser with the Web Audio API. There are no recorded samples and nothing is
uploaded anywhere, so everything you export is yours to use.

## Features

### Reload: step sequence
- Eight weapon platforms: pistol, rifle, SMG, pump shotgun, revolver, bolt action, LMG and energy rifle.
- Each reload is a sequence of steps (mag out, mag in, bolt back and so on) with a timing marker for the frame the
  sound should sync to. Markers can be dragged on the waveform or typed in, steps can be added, removed or muted, and
  the clip length can be changed with the steps following along.
- Shape controls for weight, metal, grit and room, plus tone variation and optional timing drift between takes.

### Shot: single fire
- Presets from pistol and SMG to sniper, pump shotgun and energy rifle.
- Layers for crack, blast, punch, mechanics and casing drop, placed indoors, outdoors or in an urban space, with an
  optional suppressor and adjustable caliber, distance and reverb tail.
- The shot starts 12 ms into the clip so it plays the instant a game triggers it.

### Impact: bullet hits
- Eight surfaces: flesh, body armor, wood, dirt, rock, metal, glass and water.
- Layers for snap, body, wet, tear, debris, crunch and ricochet, with force, distance, environment and a headshot
  option.
- The hit lands 5 ms into the clip.

### Export
- **Export this take** downloads the current sound as a single WAV.
- **Export 6 takes / variations** downloads a ZIP of six variations to use as round-robin sounds, so repeated reloads,
  shots and hits never sound identical in-game.
- Files are 44.1 kHz, 16-bit stereo, trimmed to the clip length and peak-normalized.

### Shortcuts
| Key | Action |
|---|---|
| `Space` | Play |
| `V` | New take |
| `Shift` + drag | Fine adjustment |

## How it works

The whole app is a single `index.html` with inline CSS and JavaScript and no dependencies. Each layer is synthesized
sample by sample in JavaScript into audio buffers, then mixed and rendered with an `OfflineAudioContext`, including a
generated impulse response for the room or environment reverb. Randomness comes from a seeded generator: the take number
shown in the app is the seed, so the same take with the same settings always produces the same sound. WAV encoding and
the ZIP archive for batch exports are written by hand in JavaScript, so no libraries are needed.

## Run your own copy

The easiest way to use Reload Bench is the [live version](https://joonas98.github.io/reload-bench/). If you'd rather
use it offline or host a copy yourself, download this repository. Everything is in a single `index.html` with no build
step or dependencies.

- **Offline:** open `index.html` in any modern browser. Without an internet connection the fonts fall back to system
  fonts; everything else works the same.
- **On your own site:** upload the files as they are to any static host, such as GitHub Pages, Netlify, Cloudflare
  Pages or itch.io (as an HTML project).
