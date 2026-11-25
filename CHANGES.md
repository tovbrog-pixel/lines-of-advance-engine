# Engine changes

Tov Binyamin Brog

## 25 November 2026: one engine for both games

- **Base:** France 1944's engine at 01917bd. It carries fixes A1 to A6 (reserve and lane rules, sister orders, attach stock, reserve area), advance pacing by the rear quarter of the leading battalions, the tutorial panel, label and hover fixes, fix 8 from Sarn Corridor and the Granville rule (an army objective no route reaches is set aside for ten days).
- **Added from Sarn Corridor, each off unless a game sets it:** battalion weight (`bns`), deployment variants, H-hour, the intel module, Sarn division templates, step timers (`S.TT`), `supplyMin`, the built-up radius `t[4]`.
- **New settings:** `game.json` read into `GAMECFG` for the game's name and wording; `squareAxis: 'all'` for square corps axes. Sarn Corridor needs that axis: on Tov's 22 Jun replay, divisions turned back 14 times in 200 hours without it and 2 times with it.
