# Eldr at a Glance

*One page of what's decided. Details live in the linked notes. Updated 2026-10-20.*

## Priorities
1. **How combat looks** — animation, spell and Eld effects. Grounded, never cartoonish.
2. **Story** — a distant second.
3. **Systems.**

Engine: **Unity** (locked). Summer was only tested, not adopted. → [[design-pillars]], [[engine]]

## The Game
- Grim, adult CRPG. Three acts: mountains, forest, coast. Slice 3–5 hrs; full game 15–20 hrs.
- A company of friends, aged 25–30, about ten years in arms. The bond is inherited, not earned.
- The protagonist (default **Ravn**) is a Captain of **the Line**, the army resisting the goddess Vela. Fixed human male; player picks Fighter, Thief or Caster.
- Dialogue is fully linear. No dialogue choices.
- → [[game-premise]], [[protagonist]], [[factions]], [[timeline]]

## Act 1 (the slice) — Ashfall Keep
- **Hold the Gate** (clear the wave *and* get civilians out) → **Reach the Shrine** → **Soulwright** boss.
- At the climax Bram and Fen are soul-trapped; Forn, the silent god of good suppressed inside Arn, breaks out and frees them. Arn says goodbye, his soul passes on, and Forn keeps his body.
- → [[quest-the-last-line]], [[enemy-roster-ashfall]]

## Party
| Who | Role | Acts |
|---|---|---|
| Arn | Paladin of Forn, healer, focal companion | 1 only |
| Bram | Goliath fighter | 1–3 |
| Fen | Halfling thief | 1–3 |
| Voryn | Eld-Weaver (caster) | 1–3 |
| Solen | Healer of Tyra | 2–3 |
| Dag | Camp craftsman, doesn't fight | all |

- **4 fight at a time**, chosen at camp or rest points. Story fights can fix the party; the Soulwright fight uses all five.

## Combat → [[combat-core]]
- **Menu-driven, turn-based.** No grid, no movement.
- **Visible timeline** shows who acts next; quick, normal and heavy actions change how soon you act again.
- **Your turn:** one action + one minor action (minor actions are instant).
- **Rows:** front and back. Back row deals and takes half melee damage.
- **No misses.** Armor reduces damage. Only status effects can be resisted.
- **Telegraphed enemy moves** show on the timeline; answer them with **interrupt skills** on your turn.
- **Company bond meter:** fills from teamwork; spent on **pair finishers** (authored pairs). May be cut after playtest.
- **Full HP and Eld restore after every fight.** Eld is a fixed pool per fight.
- **Downed, not dead.** Lose a fight → it restarts instantly.
- Enemies can flee when beaten down (morale).
- **Look and flow baseline:** the Unity prototype (`eldr-unity`, Bram and Arn vs raiders) — fights in place, run in, swing, run back. Its rules are being swapped for these one at a time; done so far: timeline, Eld pool with Bram's and Arn's kits, minor actions (2026-10-20).

## Eld (magic) → [[eld-magic]], [[world-rules]]
- Eld runs through everyone. Fighters and thieves use it by instinct; only a rare few can study spells.
- Two poles: **Forn** (preserve, heal, ward) and **Vela** (break, compel, drain). Using either moves your hidden **Drift**, which the world reacts to. No meter on screen.
- Fighters and thieves have 4 Eld abilities each (e.g. Bram's Bulwark and Break); casters use spells. → [[combat-core]] §12
- Arn has no Eld: his prayers (heal, revive, guard) are limited per fight. → [[party-kits-act1]]
- Proposed: melee Eld abilities get visible, grounded effects — amber for Forn, silver-blue for Vela.

## Named Items → [[combat-core]] §11
- One **item-ability slot** per character, beside 4–6 class skills.
- **Weapons:** an active ability (costs Eld, moves Drift, has its own showcase effect).
- **Armor:** a triggered effect (e.g. first time you drop below half HP).
- About 1–2 per character per act.

## Open — Needs Your Call
- How to source animation, and the budget.
- Bram's mid-fight join at Hold the Gate: five fight for that battle, or he replaces someone?
- Which finisher pairs, and whether finishers stay.
- Whether melee Eld abilities get visible effects (proposed rules in [[design-pillars]]).

## Next Up
1. Put the Unity project on GitHub (`eldr-unity`) and clear out the old grid projects.
2. Prototype: rows, then bond meter, then telegraphs.
3. Decide how to source animation.
4. Class-progression note (party stats by level) — the party numbers are placeholders until then.
5. Voryn's Act 1 spell list.
