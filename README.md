# 🫘 Bean Hunt

A squishy 3D hide-and-seek party game that runs in your browser. It's a single `index.html` file: three.js and PeerJS load from a CDN.

## Play
- **Play vs bots**: works offline from the menu.
- **Host game**: you get a room code like `BEAN-4821` and an invite link (`…/?room=BEAN-4821`). Send either one to your friends.
- **Join game**: open the invite link (the code is filled in for you), or click *Join game* and type the code. Then pick a name, colour and hat and hit **Join**.
- In the lobby the host picks the number of bots, the bot difficulty and the rounds, then presses **Start**. Up to 8 beans per room.

Online play is peer-to-peer over WebRTC. The free public PeerJS broker only does matchmaking. The host's browser runs the game, so the host has to keep their tab open.

Controls: WASD to move, mouse to look, Space to jump, Shift to sprint, C to crouch. Hiders: Q to disguise, F to taunt. Seeker: E or click to tag, Q to sniff, F to dash.

### Notes
- If peer-to-peer is blocked by a very strict firewall or NAT (some office or school networks, some mobile carriers), joining can fail. You can add your own TURN server by setting `window.BEAN_HUNT_ICE = [{urls:'turn:your.server:3478', username:'…', credential:'…'}]` before the game script runs.
- Add `?debug` to the URL to expose the debug hooks (`window.__bh`, `window.__dbg`).
