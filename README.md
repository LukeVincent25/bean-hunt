# 🫘 Bean Hunt

A squishy 3D hide-and-seek party game that runs in your browser. It's a single `index.html` file: three.js and PeerJS load from a CDN.

## Play
- **Play vs bots**: works offline from the menu.
- **Host game**: you get a room code like `BEAN-4821` and an invite link (`…/?room=BEAN-4821`). Send either one to your friends.
- **Join game**: open the invite link (the code is filled in for you), or click *Join game* and type the code. Then pick a name, colour and hat and hit **Join**.
- In the lobby the host picks the **map**, the number of bots, the bot difficulty and the rounds, then presses **Start**. Up to 8 beans per room.

## Infection tag (default rules)
Roulette picks the starting seeker. When a hider is **tagged**, they immediately become a seeker (red glow, sniff/dash/tag) and help hunt the rest — not a ghost. The round ends when all hiders are converted, or when time runs out (survivors get the survival bonus). Tagging scores **+100**, with a small **+25 chain** bonus for follow-up conversions. All seekers share a sweep bonus if everyone is converted.

## Maps
- **Walled City** (default): a huge Attack-on-Titan-style town (~2× the original footprint, ~4× the area) inside a **46 m** stone wall. Timber and stone houses rise **5–12 floors**, with a taller clock tower, a raised castle district, multi-level bridges, balconies, chimneys, water towers and rooftop gardens. ~700 hiding spots, most of them up high. Hide time 40s / seek 150s.
- **Backyard**: the cosy garden and house, moderately bigger fence (~±48 m). Hide 28s / seek 110s.

## Giant beans (Titans)
Toggle **Giant beans** on/off and set the count in the menu or lobby (default on: 4 in the city, 2 in the backyard).
- Huge lumbering beans (~14–18 m) roam, notice nearby players, and try to **grab** them.
- If grabbed: mash **Space** to wriggle free within ~4 seconds. Fail and you get **yeeted** across the map (hiders are briefly revealed to the seeker).
- Zip into a giant's **nape** (back of the neck) at high speed on your hooks to **stun** it for ~10s and score +150. Grapples can attach to giants too.
- Host simulates giants in multiplayer; grab / nape / wriggle go through the host.

## ODM gear (grappling hooks)
Every bean wears ODM gear with two hooks.
- **Left click / right click** fires the left / right hook at whatever you're aiming at. Hold the button to stay attached and release it to let go; your momentum carries on. **G** also fires the left hook.
- The reticle glows cyan when a surface is within range (60 m). Otherwise it shows "too far".
- **Space** while hooked uses gas to reel you in hard. **Shift** in mid-air gives a gas thrust in the direction you're looking.
- The gas meter refills while you're on the ground.
- Swing on one hook to get pendulum arcs, or use both hooks to zip between towers.
- Bots use their gear too. Hiders zip up to rooftops, and the seeker grapples up to check high spots.

Online play is peer-to-peer over WebRTC. The free public PeerJS broker only does matchmaking. The host's browser runs the game, so the host has to keep their tab open.

Controls: WASD to move, mouse to look, Space to jump, Shift to sprint, C to crouch. Left/right click (or G) for the hooks, Space while hooked to reel in with gas, Shift in mid-air for gas thrust. Mash Space if a giant grabs you; nape-hit giants while grappling fast to stun them. Hiders: Q to disguise, F to taunt. Seekers: **E** to tag (recruits them!), Q to sniff, F to dash.

## Race mode
Pick **Race** on the menu or in the lobby (alongside Hide & Seek).
- Host (or solo) chooses **laps** (1 / 3 / 5) and an optional **track seed**. The same seed always builds the same procedural course for every peer.
- Tracks include hills, jumps, bridges/tunnels, boost pads, checkpoints and a start/finish gate. Optional ODM grapples can cut corners.
- Countdown → race. **Shift** boosts (meter refills). HUD shows place, lap, and boost. Finish order becomes the scoreboard.
- Online: host-authoritative sync (~20 Hz) of positions + race state. Solo: race against bots.

## Soundtrack
Original procedural music (Web Audio only — no sampled tracks). Martial drums, tense low strings/brass, aeolian ostinatos and choir-like pads that intensify from the menu → hiding → seeking, and surge when a giant chases you. Mute with **M**.

### Notes
- If peer-to-peer is blocked by a very strict firewall or NAT (some office or school networks, some mobile carriers), joining can fail. You can add your own TURN server by setting `window.BEAN_HUNT_ICE = [{urls:'turn:your.server:3478', username:'…', credential:'…'}]` before the game script runs.
- Add `?debug` to the URL to expose the debug hooks (`window.__bh`, `window.__dbg`).

## Race mode v2 — karts, drifts & items
- **Controls:** W/S gas/brake · A/D steer · **Shift (or Space) + steer = drift** (blue → orange → purple sparks, release for a mini-turbo) · Space in the air = trick (landing boost) · **E / left-click = item** · R / middle-click = reset camera · Backspace = respawn · hold W right at GO = rocket start.
- **Items:** 🍮 Jelly Boost, 🍌 Banana-bean Peel, 🎯 Homing Bean, 🛡️ Bean Shield, 👹 Giant Stampede, 🪝 Grapple Yank. Racers further back get better items.
- **Tracks:** seeded, 5 themes (Rooftop City, Candy Land, Desert Canyon, Lava Peaks, Snowy Pass), banked turns, half-pipes, gap jumps, boost pads, sometimes a shortcut plank. If you fall off you respawn at the last checkpoint.
- **Juice:** chase camera with speed FOV, speed lines, place callouts, a final-lap banner and faster music, photo-finish slow-mo, a podium with bouncing beans, and a ghost of your best lap in single player.
- **Bots:** Speedy / Drifter / Bully / Steady / Chaos personalities; they drift and use items.
- **Camera settings** (⚙️ or Esc): sensitivity, invert-Y and distance, saved on this device.
