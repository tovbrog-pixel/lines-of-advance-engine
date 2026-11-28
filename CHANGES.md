# Engine changes

Tov Binyamin Brog

## 27 November 2026: France 1944's changes since the merge (France commits 01917bd to 32851bd)

- **Arrivals (fault):** a division forming a road or rail column is no longer landed again at its first beach (`arrivals` skips `F.transit`). Every game with arrivals and strategic moves is affected.
- **Corps review (fault):** no crash when a relieved formation has no position.
- **Army AI, pocket bonus:** only for an objective with own ground at eight points on a ring round it.
- **Army AI, mission axis (setting `armyAI.axis`):** an objective ahead on the army's axis scores higher, one behind lower. Off without the setting.
- **Army AI, reach:** a corps that finds no objective within reach looks as far as it must; before, it kept its last order. On by default; `armyAI.far: false` keeps the old rule. In France a corps sat on a taken objective for up to 355 hours.
- **Phase lines (settings `nat`, `west`, `east`):** a line can bind listed nationalities only and can close the ground west or east of a north-south line, for a boundary between armies.
- **Fortresses (formation flag `fortress`, scenario list `forts`):** a fortress garrison does not take the three-kilometre fall-back, and its shaken units fall back on the centre of the works. Inside prepared works a unit of the owning side is dug in to the fort's strength (at most 1.5) within the hour while the objective is held.
- **Theater commander, rule 9 (setting `coverPts`):** an important objective of his own left empty with the enemy near gets a division. Off without the setting.
- **Checks:** Sarn Corridor's regression suite matches its baseline with these changes. France 1944: command tests pass; Exercise Cumberland on five seeds, Blue wins all five (60-20, 50-30, 80-0, 50-30, 70-10); a 96-hour Overlord run completes. France's regression fingerprints change on eight scenarios because France had not yet taken the square axis and coherence changes of 25 November; they are re-recorded in France.
- **Not checked:** Sarn Corridor's own campaign scenario with computer armies, where the reach change applies.

## 25 November 2026: concentration (scenario setting `concentrate`)

- **Corps and army orders:** with `sc.concentrate`, a line much wider than the attack needs (over 1.5 times) is attacked at its decisive point: the most valuable enemy-held objective within 6 km of the line, else straight ahead of the commander. Two children go in abreast (three when there are five or more), each on about the frontage its battalions need. A corps sends the others after them in second echelon; an army leaves its other corps to hold and screen their present sectors. The order note names who attacks and toward what.
- **Computer armies:** with `sc.concentrate`, an army attacks with its three best-placed corps at a time.
- **Off by default:** France 1944 is unchanged; Sarn Corridor turns it on.

## 25 November 2026: coherence fixes from Tov's Sarn Corridor game

Found with the coherence checker (sarn-corridor `tools/coherence.js`) on Tov's 22 Jun save, 200 hours.
- **Halts at the bound end:** a division halted to wait for a lagging neighbour goes on once that neighbour has gained under 2 km in 6 hours (`DOCTRINE.alignMaxH`, `alignGainKm`), and the corps reports it. The 8th Infantry Division had waited 156 hours; the longest halt is now 17 hours.
- **Rear battalions close up during a halt:** a battalion over 3 km from its division's centre and heading nearer keeps moving while the division halts.
- **Retreated battalions rally:** a battalion that fell back over 6 km from its division and is clear of the enemy makes for a point 2 km behind the division's centre. Cut-off battalions fell from 364 to 86 per 100 hours.
- **Refused orders stand:** when a commander refuses because the division is disorganised or out of ammunition or fuel, the order stands and he tries again each hour. Divisions standing refused fell from 581 to 50 division-hours per 100 hours.
- **Effect on France 1944:** every regression scenario changes. Exercise Cumberland on five seeds: Blue wins all five (60-20, 50-30, 80-0, 50-30, 70-10), Carthage at hour 7.5 to 9. Command tests pass. Overlord, 168 hours, seeds 7 and 8: same objectives on seed 7, Caen taken on seed 8, losses within 4.

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
