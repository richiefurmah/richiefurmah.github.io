# Dragonreach — a first-person open-world RPG

A high-fantasy, first-person open-world action RPG built with HTML5 + Three.js (WebGL).
Lives under `/game/` so it is fully isolated from the rest of the site.

## Milestone 1 — Foundation & Player ✅
- Decoupled camera + first-person controller (yaw/pitch rig, gravity, jump, sprint)
- Procedurally generated mountainous open-plain world (seeded value-noise heightfield)
- Placeholder inventory screen driven by an authoritative `GameState`

### Run it
Everything is one self-contained file — no build step.

- **Live (GitHub Pages):** `https://<your-domain>/game/`
- **Local:** serve the repo root over HTTP and open `/game/index.html`:
  ```bash
  cd richiefurmah.github.io
  python3 -m http.server 8000
  # then visit http://localhost:8000/game/
  ```
  (Opening the file with `file://` will fail — ES modules require an HTTP origin.)

### Controls
| Key | Action |
| --- | --- |
| `W` `A` `S` `D` / Arrows | Move |
| Mouse | Look |
| `Shift` | Sprint |
| `Space` | Jump |
| `I` | Toggle inventory |
| `Esc` | Release cursor |

## Architecture notes
- **`GameState` is the single source of truth.** Every system reads/writes it; nothing keeps
  a private copy of shared state. This is the seam a future server authority plugs into
  (GitHub Pages is static hosting, so true server authority is deferred).
- **One shared height field** feeds both terrain rendering and player collision, so what you
  see is exactly what you stand on.
- **All assets are procedural** (terrain, boulders, conifers, sky, lighting) — no external art.

## Roadmap
- Milestone 2 — Combat & Magic (light/heavy attacks, blocking, fireballs, health/stamina)
- Milestone 3 — World, NPCs & Quests (radiant "Kill the Bandit" quest, journal, enemy AI)
