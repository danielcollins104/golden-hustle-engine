# Golden Hustle — Street Royale · ENGINE v3 (Phaser 3)

v3 rebuilds the slot on **Phaser 3.80** (WebGL): reel strips are sprite
containers with geometry masks, spins are tween-driven with cubic ease-out,
win frames/anticipation borders are generated textures, and your art loads
from real files (`assets/symbols/*.png`) — no more base64 bloat.

The DOM layer keeps the proven chrome: HUD, menus, paytable, jackpot wheel,
and all three bonus games. Game math lives in `js/engine.js` (pure, no
rendering). All tuning stays in `js/config.js` (same CFG template as v2).

## Run
Serve the folder over HTTP (CDN needed for Phaser):
  npx serve .        # or: python3 -m http.server
Then open the page. GitHub Pages works out of the box.

## Structure
  index.html        chrome + overlays + CDN/module scripts
  js/config.js      ★ the template — edit everything here
  js/engine.js      strips, RNG planning, evaluation, suspense detection
  js/audio.js       synth SFX, schemes, music bed, haptics
  js/game.js        Phaser scenes + spin flow + DOM UI wiring
  assets/symbols/   the 10 owned symbol tiles

## Fixes over v2
- Reel strips: 3×strip+3 tiles — the v2 DOM renderer could overrun its
  strip on long spins; the engine layout mathematically cannot.
