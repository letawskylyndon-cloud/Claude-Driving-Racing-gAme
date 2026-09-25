# DRIFTWAVE — neon street racing

A 3D arcade street racer that runs entirely from a single `index.html`.

## Play

Double-click `index.html` (or open it in Chrome, Edge, Firefox or Safari). An internet
connection is needed so the browser can fetch three.js (and, for online play, PeerJS) from
the jsDelivr CDN.

**Controls:** W/↑ accelerate · S/↓ brake & reverse · A/D or ←/→ steer · hold Space while
turning to drift, release to boost · R reset · M mute · Esc pause (online: menu, the race keeps
running) · ` (backquote) live tuning panel

Enter your driver name, pick **Solo Race** (or press Enter) and race 5 AI cars over 3 laps.

## Online with friends (up to 4 players)

1. One player picks **Host Online**. A 5-character room code appears in the lobby
   (codes never use O, 0, I, 1 or L, so they're easy to read out).
2. Friends pick **Join Online** and type the code.
3. Everyone gets their own neon color; AI cars fill the rest of the 6-car grid. Only the
   host can start the race, and after the results the host can start a **Rematch**.

Connections go peer-to-peer (WebRTC) and are matched through the free public PeerJS server.
Some strict networks (school, office, public Wi-Fi) block direct connections — if joining
times out, try another network or a phone hotspot. Solo racing never needs the server.

**Testing online on your own:** open `index.html` in **two browser windows** side by side
(not two tabs — browsers pause background tabs). Host in one, join from the other. Only the
focused window receives keyboard input, and you may want to press M in one of them.

## Tuning

Every handling value lives in the `CONFIG` object at the top of the script in `index.html`.
Press ` in game to edit them live, then copy the values you like back into the file.
You can also poke them from the browser console, e.g. `__dw.CONFIG.car.driftGrip = 2.5`.

The ones worth trying first:

| Value | What it changes |
| --- | --- |
| `car.grip` / `car.driftGrip` | how planted the car is / how wide and floaty drifts are |
| `car.driftYawRate`, `car.driftKick` | how hard the car rotates when drifting and when a drift starts |
| `car.steerRate`, `car.steerSpeedFalloff` | turn-in at low speed and how much steering calms down at speed |
| `car.topSpeed`, `car.accel` | pace and punch |
| `car.boostTierTimes`, `car.boostStrength` | how long to drift for each boost tier and how big the boosts are |
| `car.wallScrape`, `car.wallGripLoss` | how much a wall hit costs you |
| `camera.distance`, `camera.driftSwing`, `camera.fovSpeed` | chase cam feel |
| `ai.difficulty`, `ai.rubberBand` | opponent pace and how much they bunch up around you |
| `race.laps` | race length |
| `render.maxPixelRatio`, `render.bloomStrength` | performance vs sharpness, and neon glow |

## Status

- [x] Milestone 1 — handling model, chase cam, test arena
- [x] Milestone 2 — track and city
- [x] Milestone 3 — AI, laps, positions, race flow, HUD
- [x] Milestone 4 — drift boost
- [x] Milestone 5 — audio
- [x] Milestone 6 — online multiplayer
- [x] Milestone 7 — polish
