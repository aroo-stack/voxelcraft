# VoxelCraft

A Minecraft-style voxel sandbox that runs entirely in a **single HTML file** — no build step, no assets, no server. Just open it and play.

![gameplay](https://img.shields.io/badge/engine-three.js%20160-blue) ![size](https://img.shields.io/badge/size-~150KB-informational)

## Play

Open `minecraft.html` in any desktop browser (Chrome/Edge recommended). Click **Singleplayer**, create a world, go.

## Features

- **Infinite procedural terrain** — 8 biomes: Plains, Forest, Desert, Snowy Tundra, Snowy Forest, Taiga, Cherry Grove, and extreme Mountains (peaks to y=58)
- **Three dimensions** — Overworld, **Nether** (netherrack caverns, lava seas, glowstone, zombie piglins), and **the End** (end-stone island, obsidian pillars, Ender Dragon boss fight with health bar, Dragon Egg trophy)
- **Portals you build yourself** — Netherite frame + Flint & Steel → Nether; End Stone frame + Flint & Steel → the End
- **34 blocks** — ores by depth, sandstone, cacti, glowstone, wool, pumpkin, glass, bookshelf…
- **Practical blocks** — water & lava buckets, doors that open/close, walkable stairs with auto-step
- **Mobs** — pigs (day), zombies (night, chase & attack), zombified piglins (neutral → angry), with knockback, hurt-flash and drops-ready health
- **Survival & Creative** — hearts, fall/lava/mob damage, hunger-free regen; or G to toggle creative (no damage, mobs ignore you)
- **Commands** — `/` opens a console with autocomplete: `/tpbiome`, `/tp`, `/time`, `/gamemode`, `/end`, `/over`, `/seed`
- **Multi-world** — create/delete worlds, each with its own seed, game mode, spawn biome and edits; position saved on exit
- **Zero assets** — every texture, icon and sound is procedurally generated at boot (canvas + WebAudio)

## Controls

| | | | |
|---|---|---|---|
| **WASD** move | **Mouse** look | **L-click** break / attack | **R-click** place / light portal |
| **Space** jump / swim | **Shift** sprint | **F** toggle fly | **Middle-click** pick block |
| **1-9 / wheel** hotbar | **E** block inventory | **G** creative/survival | **/** command console |
| **F3** debug overlay | **Esc** pause | | |

## How it works (roughly)

- Chunked voxel world (16×64×16 chunks) with face-culled, ambient-occlusion-shaded greedy-ish meshing
- Seeded value-noise terrain: continents, hills, mountain amplification, 3D-noise caves & nether caverns
- DDA voxel raycasting for block targeting; axis-separated AABB physics with substepping
- Per-dimension world state, edits delta-saved to `localStorage` per world
- Procedural texture atlas (8×8 canvas), WebAudio-synthesized sound effects

## Save format

Worlds live in your browser's `localStorage` under `voxelcraft_worlds` (edits are stored as per-chunk deltas, so saves stay tiny). Clearing site data wipes worlds — export coming soon.
