# Engine changes

Tov Binyamin Brog

## 25 November 2026: square axis for corps orders in both games

- **Corps orders:** a corps now takes its axis of advance square to the objective line, as armies already did. On Tov's 22 Jun Sarn Corridor replay, divisions turned back 2 times in 200 hours, against 14 with the old axis from the corps centre to the objective.
- **Tutorial:** the 1st Armored Division starts at 24, 34, behind II Corps, where step 7 says it waits (before: 15, 29.5, west of the corps). From the old spot, Ames sent it to wait 16 km west of Carthage.
- **Exercise Cumberland on five seeds** (79, 7, 11, 23, 101), Hale's plan as written: Blue wins all five, 70-10, 80-0, 70-10, 50-30 and 80-0. Before: 50-30, 50-30, 80-0, 80-0 and 60-20. Carthage now falls at hour 8 to 10 (6.5 to 7.5 before).
- **Regression:** only `tutorial-tn` changes. Overlord, computer against computer, gives identical results over 168 hours on seeds 7 and 8, because the computer's corps lines are already square to their approach.
- **Command tests:** all pass. In two of the jumbled cases the corps keeps a different division in reserve.

## 25 November 2026: one engine for both games

- **Base:** France 1944's engine at 01917bd. It carries fixes A1 to A6 (reserve and lane rules, sister orders, attach stock, reserve area), advance pacing by the rear quarter of the leading battalions, the tutorial panel, label and hover fixes, fix 8 from Sarn Corridor and the Granville rule (an army objective no route reaches is set aside for ten days).
- **Added from Sarn Corridor, each off unless a game sets it:** battalion weight (`bns`), deployment variants, H-hour, the intel module, Sarn division templates, step timers (`S.TT`), `supplyMin`, the built-up radius `t[4]`.
- **New setting:** `game.json` read into `GAMECFG` for the game's name and wording.
