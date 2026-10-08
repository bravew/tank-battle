# Tank Battle 3D

A classic Battle City–style tank battle game rebuilt as a 3D top-down web game with three.js. A single self-contained `index.html` — no build step, just open and play.

**Play it live:** https://bravew.github.io/tank-battle/

## Gameplay

- Defend the eagle base at the bottom of the map; destroy every enemy tank to clear the level.
- 3 levels with different map layouts; enemy count, speed and firepower scale up per level.
- Brick walls are destructible by bullets; steel walls are indestructible.
- Power-ups drop from destroyed enemies: star (firepower up), helmet (temporary invincibility), clock (freeze all enemies for a few seconds).
- Game over if your lives run out or the eagle base is hit. Clear level 3 for the victory screen.

## Controls

| Key | Action |
|---|---|
| WASD / Arrow keys | Move tank |
| Space / J | Fire |
| P | Pause |
| M | Mute sound |
| Enter | Start / restart / next level |

The HUD shows lives, power-up status, level, remaining enemies and score. All sound effects (fire, explosion, hit, pickup) are synthesized with WebAudio — no audio assets needed.

## Tech

- three.js 0.160.0 loaded from CDN via import map, game logic in an inline `<script type="module">`
- Tanks, walls and the eagle base are all assembled from three.js geometry — no model files
- One file, ~34 KB, zero build tooling

## How this project was created

This game was built end-to-end by an AI agent workflow — no hand-written code:

1. **Muse** (Meta's personal AI agent) acted as the orchestrator: it scaffolded the project, delegated the build, smoke-tested the result and published it here.
2. **Pi** (`@earendil-works/pi-coding-agent`, the coding-agent CLI from pi.dev) did the actual development — it wrote the complete game in one pass from a detailed spec prompt.
3. **Ant-Ling Ling-3.1-flash** was the model behind pi, wired up as a custom OpenAI-compatible provider (`https://api.ant-ling.com/v1`) in pi's `models.json`, with `compat.supportsDeveloperRole: false` and a full `thinkingLevelMap`, running at the `high` thinking level.

The model's API key lives in the developer's shell environment (`LING_API_KEY` exported from `~/.bashrc`) and is read lazily by the pi config — it is **never committed to this repository**. If you fork this project and rebuild it with pi, bring your own key.

## Run locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

Internet access is required on first load (three.js comes from a CDN).

## Deploy

Any static host works. This repo is deployed with GitHub Pages from the `main` branch (`/` root).
