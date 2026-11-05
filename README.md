# DRIFTWAVE — neon street racing

A 3D arcade street racer that runs entirely from a single `index.html`.

## Play

Double-click `index.html` (or open it in Chrome, Edge, Firefox or Safari). An internet
connection is needed so the browser can fetch three.js (and, for online play, PeerJS) from
the jsDelivr CDN.

**Controls:** W/↑ accelerate · S/↓ brake & reverse · A/D or ←/→ steer · hold Space while
turning to drift, release to boost · R reset · M mute · Esc pause (online: menu, the race keeps
running) · ` (backquote) live tuning panel

Enter your driver name, pick a track with the ◀ ▶ arrows, then **Solo Race** (or press Enter)
and race 5 AI cars over 3 laps.

**Tracks:** each has its own street layout, sky and neon colors. Your best lap on each one is
saved as a track record in this browser.

| Track | Character |
| --- | --- |
| NEON CIRCUIT | long straights, square corners and two fast sweepers (2.0 km, night) |
| SUNSET STRIP | flat-out sweepers and a long U-turn at the far end (2.6 km, dusk) |
| MIDNIGHT GRID | a technical zig-zag through the downtown blocks (2.3 km, deep blue under a moon) |

**Garage:** on the title screen, **GARAGE** lets you pick a body (VECTOR, BRUISER or PHANTOM),
a paint color and an underglow color, which also colors your drift trails. It's looks only:
every body has the same size and handling. Your car is saved for next time.

**Slow laptop?** Graphics are set to **AUTO** by default. The game starts from a guess based
on your graphics chip, then steps down through HIGH → MEDIUM → LOW → POTATO whenever the frame
rate can't keep up, and remembers the result for next time. The lower presets render at a lower
resolution, skip anti-aliasing, compute the neon glow at lower resolution and use fewer
particles. You can also pick a preset yourself with the **GRAPHICS** button on the title screen
or in the pause menu; cycling back to AUTO re-runs the calibration.

## Online with friends (up to 4 players)

1. One player picks **Host Online**. A 5-character room code appears in the lobby
   (codes never use O, 0, I, 1 or L, so they're easy to read out).
2. Friends pick **Join Online** and type the code.
3. Everyone races the car from their own garage; AI cars fill the rest of the 6-car grid.
   The host picks the track in the lobby (friends see it switch), only the host can start
   the race, and after the results the host can start a **Rematch**.

Everyone needs the same version of `index.html`: a friend with an older copy is told the room
runs a different version.

Connections go peer-to-peer (WebRTC) and are matched through the free public PeerJS server.
Solo racing never needs the server. If friends on other networks can't join, see below.

**Testing online on your own:** open `index.html` in **two browser windows** side by side
(not two tabs — browsers pause background tabs). Host in one, join from the other. Only the
focused window receives keyboard input, and you may want to press M in one of them.

### Friends on other networks can't join? Set up a relay

Two windows on one computer always connect, because nothing sits between them. Two computers
have to reach each other through their routers and firewalls, and some networks block that:
school, office and public Wi-Fi often do, and so do some home routers. The join screen then says
the computers couldn't connect, and the host's lobby says a friend couldn't connect.

PeerJS used to run a free backup relay for this case, but it has been shut down. The fix is a
**relay (TURN) server**, which passes the race traffic between you. Some providers have free plans
(as listed in November 2026; plans change, so check their sites):

| Provider | Free plan | Notes |
| --- | --- | --- |
| [Metered](https://www.metered.ca/tools/openrelay/) | 20 GB a month | Runs on ports 80 and 443 (including TLS), so it gets through strict networks |
| [ExpressTURN](https://www.expressturn.com/) | 1000 GB a month | Port 3478 only, which strict networks may block |

Both need a free account. A race uses only a few MB per friend, so a free plan covers a lot of racing.

1. Sign up and find your TURN details: a server address (starting with `turn:` or `turns:`),
   a username and a password. If the provider shows a ready-made `iceServers` list, you can paste
   the whole list into the SERVER box and the game picks out the rest.
2. On the **host's** computer, press **RELAY** (on the title screen, the join screen or in the
   lobby), paste the details and press **SAVE & TEST**. It should say **RELAY WORKS**. The host
   can do this while waiting in the lobby; friends then join again with the same code.
3. Usually only the host needs a relay. If a friend still can't join, they set up the same
   details on their computer too.

The details are saved in that browser only. Anyone you give them to can use your plan's data, so
don't post them publicly. To build them into the copy of `index.html` you send your friends,
fill in `net.relay` in `CONFIG` instead. If you just want to race right away, both computers on
the same phone hotspot often connect without a relay.

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
| `render.quality` | default graphics preset: `'auto'`, or `'HIGH'` / `'MEDIUM'` / `'LOW'` / `'POTATO'` |
| `render.maxPixelRatio`, `render.bloomStrength` | sharpness on the HIGH preset, and neon glow |
| `net.relay` | a relay (TURN) server built into your copy of the file (normally set in game with RELAY) |

## Status

- [x] Milestone 1 — handling model, chase cam, test arena
- [x] Milestone 2 — track and city
- [x] Milestone 3 — AI, laps, positions, race flow, HUD
- [x] Milestone 4 — drift boost
- [x] Milestone 5 — audio
- [x] Milestone 6 — online multiplayer
- [x] Milestone 7 — polish
- [x] Low-end laptop performance (graphics presets)
- [x] More tracks and car customization
- [x] Relay (TURN) support for networks that block direct connections
