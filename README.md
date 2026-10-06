# 🫘 Bean Hunt

A squishy 3D hide-and-seek party game that runs in your browser. It's a single `index.html` file: three.js and PeerJS load from a CDN.

## Play
- **Play vs bots**: works offline from the menu.
- **Host game**: you get a room code like `BEAN-4821` and an invite link (`…/?room=BEAN-4821`). Send either one to your friends.
- **Join game**: open the invite link (the code is filled in for you), or click *Join game* and type the code. Then pick a name, colour and hat and hit **Join**.
- In the lobby the host picks the **map**, the number of bots, the bot difficulty and the rounds, then presses **Start**. Up to 8 beans per room.

## Maps
- **Walled City** (default): a dense, tall Attack-on-Titan-style town inside a 22 m stone wall. It has timber and stone houses 3–7 floors tall, a clock tower, narrow alleys, bridges between rooftops, balconies, chimneys, water towers, rooftop gardens and crates, and arcades around a fountain plaza. Many of the best hiding spots are up high.
- **Backyard**: the original cosy garden and house.

## ODM gear (grappling hooks)
Every bean wears ODM gear with two hooks.
- **Left click / right click** fires the left / right hook at whatever you're aiming at. Hold the button to stay attached and release it to let go; your momentum carries on. **G** also fires the left hook.
- The reticle glows cyan when a surface is within range (60 m). Otherwise it shows "too far".
- **Space** while hooked uses gas to reel you in hard. **Shift** in mid-air gives a gas thrust in the direction you're looking.
- The gas meter refills while you're on the ground.
- Swing on one hook to get pendulum arcs, or use both hooks to zip between towers.
- Bots use their gear too. Hiders zip up to rooftops, and the seeker grapples up to check high spots.

Online play is peer-to-peer over WebRTC. The free public PeerJS broker only does matchmaking. The host's browser runs the game, so the host has to keep their tab open.

Controls: WASD to move, mouse to look, Space to jump, Shift to sprint, C to crouch. Left/right click (or G) for the hooks, Space while hooked to reel in with gas, Shift in mid-air for gas thrust. Hiders: Q to disguise, F to taunt. Seeker: **E** to tag (mouse clicks are now the hooks), Q to sniff, F to dash.

### Notes
- If peer-to-peer is blocked by a very strict firewall or NAT (some office or school networks, some mobile carriers), joining can fail. You can add your own TURN server by setting `window.BEAN_HUNT_ICE = [{urls:'turn:your.server:3478', username:'…', credential:'…'}]` before the game script runs.
- Add `?debug` to the URL to expose the debug hooks (`window.__bh`, `window.__dbg`).
