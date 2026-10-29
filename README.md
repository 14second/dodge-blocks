# Dodge the Falling Blocks 🚀

A tiny arcade survival game — you're a little ship at the bottom of the screen, blocks rain down faster and faster, and your only job is to not be there when they land.

**Play it:** https://14second.github.io/dodge-blocks/ — or open `index.html` in any browser. That's it. No build, no install, no dependencies.

## How to play

- **← / →** or **A / D** — steer · **drag / touch** — steer on mobile
- **Space** — start / restart · **R** — restart · **M** — mute
- Score = 10 points per second survived + 5 per block dodged. Best score saves in your browser.

Add `?demo=1` to the URL to watch the ship play itself.

## How it's built

One self-contained `index.html` (~450 lines). Everything is drawn on a `<canvas>` with plain JavaScript:

| Part | Where |
|---|---|
| Game loop (fixed 120 Hz timestep) | `frame()` / `update()` at the bottom |
| Difficulty ramp (fall speed + spawn rate) | `CONFIG` + the ramp lines in `update()` |
| Forgiving collisions (hitboxes shrunk ~15%) | the collision block in `update()` |
| The ship (vector-drawn, tilt, flame) | `drawShip()` |
| Blocks / background / particles | `drawBlock()`, `drawPuffs()` |
| Sound (synthesized, no audio files) | `beep()` / `sfx` |
| Autopilot demo mode | `demoSteer()` — a potential-field dodger |

## Tweak the feel

All tuning lives in the `CONFIG` block at the top of the script:

- `startFall` / `maxFall` / `fallAccel` — how fast blocks fall, and how quickly it ramps
- `startGap` / `minGap` / `gapShrink` — how often blocks spawn
- `blockMin` / `blockMax` — block sizes
- `shipSpeed` — steering speed

Hitboxes are deliberately forgiving (shrunk ~15% in the collision check) — near-misses feel good.

## Deploy

It's a static file. Drop it on GitHub Pages, Netlify, or any static host and share the link.
