# DRIFTWAVE — neon street racing

A 3D arcade street racer that runs entirely from a single `index.html`.

## Play

Double-click `index.html` (or open it in Chrome, Edge, Firefox or Safari). An internet
connection is needed the first time so the browser can fetch three.js from the jsDelivr CDN.

**Controls:** W/↑ accelerate · S/↓ brake & reverse · A/D or ←/→ steer · hold Space while
turning to drift, release to boost · R reset · M mute · Esc pause · ` (backquote) live tuning panel

Enter your driver name, pick **Solo Race** (or press Enter) and race 5 AI cars over 3 laps.

## Tuning

Every handling value lives in the `CONFIG` object at the top of the script in `index.html`.
Press ` in game to edit them live, then copy the values you like back into the file.
You can also poke them from the browser console, e.g. `__dw.CONFIG.car.driftGrip = 2.5`.

## Status

- [x] Milestone 1 — handling model, chase cam, test arena
- [x] Milestone 2 — track and city
- [x] Milestone 3 — AI, laps, positions, race flow, HUD
- [x] Milestone 4 — drift boost
- [x] Milestone 5 — audio
- [ ] Milestone 6 — online multiplayer
- [ ] Milestone 7 — polish
