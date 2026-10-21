---
type: system
status: draft
depends_on: ["[[world-rules]]", "[[design-pillars]]", "[[eld-magic]]"]
ue5_scope: L
inspired_by: ["turn-based-dead-air", "turn-economy-design", "design-doc-turn-based-combat"]
open_questions:
  - "Can overdrawing Eld Down the user? Prototype assumes no: HP stops at 1."
  - "Hold the Gate: Bram joins mid-fight while protagonist, Arn, Fen and Voryn are already fighting. Does he make a fifth for that fight (story exception), or replace someone? Proposed: story exception — five for that fight."
  - "Bond finisher list: which pairs, and how many in the slice? Proposed slice set: protagonist + Arn, Bram + Fen, Bram + Voryn. Finishers may be removed entirely after playtest (human, 2026-10-19)."
  - "All numbers in this note are first-pass tuning values, marked TUNE. They need a playtest, not a debate."
  - "Class-progression note (party HP, armor and attributes by level) is not written; party numbers in [[enemy-tiers-ashfall]] and [[party-kits-act1]] are placeholders."
---

# Combat Core

*Rewritten 2026-10-19. Replaces the grid-tactics version (d20 to-hit, flanking, movement, Reaction Windows). Decisions from the 2026-10-19 combat-loop interview.*

*Priority order from [[design-pillars]]: how combat looks comes first. This system exists to give the animation and effects good moments to play — and to keep the waits between those moments short.*

---

## Decided (2026-10-19)

| Topic | Decision |
|---|---|
| Combat form | Menu-driven, turn-based. No grid, no free movement. |
| Turn order | **Visible timeline.** Units act one at a time in speed order; the next several turns are shown. |
| Party meter | **Company bond.** Coordinated actions fill it; it is spent on **authored pair finishers**. |
| Resources | **Full restore after every fight.** Eld is a fixed pool per fight. |
| Position | **Front row and back row.** |
| Hit resolution | **No misses.** Attacks always land; armor reduces damage. Only status effects can be resisted. |
| Turn actions | **One action plus one minor action.** |
| Answering telegraphs | **Interrupt skills**, used on your own turn before the telegraphed move fires. |
| Finishers | **Authored pairs** with shared history. |
| Party size | **4 active** of the 5-person company, chosen at camp or rest points. Story fights may fix the party; the Soulwright climax fights with all five. |

**Kept from the old version (converted in section 12):** class Eld abilities. **Also kept:** Downed instead of death; no permadeath; enemy morale; class Eld abilities and Drift ([[eld-magic]]); casting past 0 Eld costs HP; the Soulwright ritual meter and objective fights like Hold the Gate.

**Dropped:** the grid, flanking, range bands, movement speed, Large 2×2 footprints, Veteran's Read (folded into the bond meter), Rally Shout (folded into the bond meter), the off-turn Reaction Window, d20 to-hit.

---

## 1. The Timeline

Every combatant has a marker on a timeline track. When a marker reaches the end, that unit acts. The track shows the next **6 turns** in order, including enemies.

**Speed.** Each action has a **delay** that sets how soon the unit acts again:

| Action weight | Delay (TUNE) | Examples |
|---|---|---|
| Quick | 70 | Light attack, minor skills, Guard |
| Normal | 100 | Standard attack, most skills and spells |
| Heavy | 140 | Big skills, finishers, heavy weapons |

A unit's DEX shortens all its delays: **delay × (1 − DEX modifier × 0.04)** (TUNE). Turn order at the start of a fight comes from DEX, with a small random spread so fights don't open identically.

**The decision it creates:** a fast weak move now, or a slow strong one that lets enemies act first.

**Telegraphs live on the timeline.** When an enemy begins a telegraphed move, its marker shows the move's icon and the turn it will fire. The player can see what is coming and how many party turns remain to answer it.

---

## 2. A Turn

On its turn a character gets:

- **One action:** attack, skill, spell, item, or Defend.
- **One minor action:** change row, use a quick item, or a minor skill marked *minor*.

**Presentation rule for minor actions:** they resolve **instantly with no staged animation** — a short gesture at most. Only the main action gets a staged beat. This keeps "action plus minor" from doubling the wait. *(Concern noted 2026-10-19: two actions per turn means longer turns. This rule is the mitigation.)*

**Defend:** take 50% less damage until your next turn (TUNE); quick delay.

---

## 3. Rows

Each side has a **front row** and a **back row**.

| Row | Deals melee | Takes melee | Notes |
|---|---|---|---|
| Front | Full | Full | Can be targeted by everything. |
| Back | Melee attacks from the back row deal 50% (TUNE) | 50% (TUNE) | Ranged attacks and spells are unaffected by row. |

- If a side's front row is empty, the back row becomes the front row.
- Changing row is a minor action.
- Bram and Arn are built to stand forward; Voryn and a caster protagonist to stand back.

**The decision it creates:** who stands in front this fight, and when to pull someone back.

---

## 4. Damage

Attacks always land.

**Damage = (weapon or skill base + attribute bonus) × variance (0.9–1.1) − target armor**, minimum 1 (TUNE).

| Attribute | Used for |
|---|---|
| STR | Melee damage |
| DEX | Ranged damage, timeline speed |
| CON | HP |
| INT | Eld pool, spell power |
| WIS | Status resistance, enemy morale |

There is no Charisma ([[design-pillars]]).

**Weapon bases** (TUNE — the average of the old dice, so enemy HP from the old notes still roughly holds):

| Weapon | Base | Weight | Notes |
|---|---|---|---|
| Dagger | 3 + STR or DEX | Quick | |
| Short sword | 4 + STR or DEX | Quick | |
| Longsword | 5 + STR | Normal | |
| War hammer | 5 + STR | Normal | +2 vs Heavy armor |
| Spear | 5 + STR | Normal | Full damage from the back row |
| Greatsword | 6 + STR | Heavy | |
| Short bow | 4 + DEX | Normal | Ranged — row doesn't matter |
| Crossbow | 5 + DEX | Heavy | Ranged |

The attribute bonus is the modifier: floor((score − 10) / 2).

**Armor** (damage subtracted from each hit, TUNE):

| Armor | Reduction | Delay effect |
|---|---|---|
| None | 0 | Quick actions 10% faster |
| Light | 1 | — |
| Medium | 2 | — |
| Heavy | 3 | All delays +10% |
| Shield | +1 | — |

**Status effects** (Fear, Command, Enfeeble and similar) can be resisted: **resist chance = target WIS-based value vs. caster INT-based value** (formula TUNE). Damage spells always land.

**Criticals:** a 5% chance (TUNE) for 1.5× damage, shown with a distinct impact frame.

---

## 5. Eld in Combat

- Each character has an **Eld pool for the fight**. It does not refill during the fight and is full again at the start of the next.
- Casters have a large pool; Fighters and Thieves a small one for their class abilities ([[eld-magic]], [[world-rules]] — two tiers).
- **Casting past 0 Eld** is still allowed: each missing point costs 1d4 HP (kept from the old version).
- Every Eld use moves the Drift Counter as in [[eld-magic]].

---

## 6. The Company Bond Meter

One shared meter, 0–100. It is the mechanical form of a ten-year friendship.

**Fills from coordination** (all TUNE):

| Event | Bond |
|---|---|
| Attacking a target an ally hit since your last turn | +8 |
| Taking or blocking a hit meant for an ally (Guard, Bulwark) | +12 |
| Interrupting a telegraphed move | +20 |
| An ally goes Downed (the company rallies) | +10 |
| Finishing an enemy an ally set up (debuffed or staggered) | +10 |

**Spent on pair finishers.** A finisher costs **100** (TUNE) and needs both members of the pair active and conscious.

It uses the turn of whichever partner acts first; the other partner keeps their turn. The meter is the limit. Finishers may be cut entirely after playtest.

**Finishers are authored pairs** with history behind them — each is a hand-made showcase animation. The pair list is open (see open_questions); the slice needs few.

**The decision it creates:** play for coordination to build the meter, or for raw damage now.

---

## 7. Answering Telegraphs — Interrupt Skills

Some skills carry the **Interrupt** tag (for example a shield bash, a quick shot, Counterspell). Used on a target that has a telegraphed move pending, an interrupt:

- **cancels** the move if the target is a regular enemy, or
- **pushes it back** on the timeline (+50 delay, TUNE) and weakens it if the target is a boss or elite.

Interrupts are used on the character's own turn, before the move fires. The timeline shows how many turns remain. There is no off-turn reaction prompt.

**The decision it creates:** spend this turn stopping the threat, or deal damage and take the hit.

The Soulwright ritual meter works the same way: successful interrupts on its rites slow the meter ([[enemy-roster-ashfall]]).

---

## 8. Downed, Defeat, Morale

- At 0 HP a character is **Downed**: no turns, still targetable by revive effects.
- **Revive:** a skill or item brings them back at 25% HP (TUNE).
- Characters cannot die from combat. Death is a story event only ([[design-pillars]]).
- **Defeat:** all active party members Downed. **The fight restarts instantly** from its first turn with the party at full strength (decided 2026-10-19). An option to return to the last rest point is offered on the same screen.
- **Victory** comes when all enemies are defeated, routed or surrendered, or when the fight's own objective is met (survive N turns, protect a point, fill the evac counter).
- **Morale:** humanoid enemies below 25% HP may flee on their turn. Beasts and the Bound never do.
- After every fight: **full HP and Eld restore**. There is nothing to grind and nothing to ration between fights.

---

## 9. Presentation Rules

How combat looks is the first priority. These rules exist so it looks good *and* stays quick ([[design-pillars]]; Atlas: turn-based dead air).

| Beat | Time budget (TUNE) | Staging |
|---|---|---|
| Menu input | Instant | Menus never wait on animation. The player can choose the next command while the previous action finishes. |
| Basic attack | ≤ 1.5 s | Animation and impact; no camera move. |
| Skill / spell / Eld ability | ≤ 2.5 s | Short camera push-in, effect, impact, brief hit-stop. |
| Named-item ability | ≤ 3 s | As above, with the item's own effect. |
| Pair finisher | ≤ 6 s | Full authored sequence. The showcase moment. |
| Enemy basic action | ≤ 1.5 s | No camera move. |
| Minor action | ≤ 0.5 s | Gesture only. |

- **Overlap:** damage numbers, HP changes and status icons play *during* the animation, never after it.
- **No text that repeats what the animation just showed.**
- **Settings:** battle speed (1×, 1.5×, 2×) and a toggle to shorten repeat finishers. A patch, not the design — the budgets above are the design.
- Eld effects follow the proposed rules in [[design-pillars]] Combat Presentation (grounded, short, colour by pole).

---

## 10. Implementation (Unity)

| Component | Complexity | Notes |
|---|---|---|
| Timeline + turn manager | Medium | Ordered list by remaining delay; projected next 6 turns for the UI. |
| Action resolution (damage, status, revive) | Low | No grid, no to-hit roll. |
| Rows | Low | Two lists per side and a multiplier. |
| Bond meter + finisher triggers | Low | One shared value; pair availability check. |
| Interrupts + telegraph markers | Medium | Pending-move state per enemy; cancel or delay. |
| Enemy AI | Medium | One decision per turn from a priority list; bosses scripted. |
| Combat UI (timeline bar, menus, rows) | Medium | Main UI cost of the system. |
| Presentation sequencer (camera beats, hit-stop, overlap) | Medium–High | Where most of the polish time goes; matches priority 1. |

**Estimate:** about 4–5 weeks for the system and UI, before animation and effects content. Animation and effects are the larger cost and are budgeted separately (see [[design-pillars]] open questions).

**Cheaper than the old version:** no grid pathfinding, flanking geometry, movement, Large footprints or Reaction Window state machine.

**Prototype baseline (decided 2026-10-20).** The Unity prototype in the `eldr-unity` project (`Assets/EldrTest/Battle`) is the baseline for how combat looks and flows: fights start where the party meets the enemy, sides line up facing each other, melee attackers run in, swing, turn and run back, with hit-stop and battle lighting. Its *rules* are not canon. They are replaced with this note's rules one at a time: timeline, Eld pool (replaces TP) with Bram's §12 Fighter abilities and Arn's prayers, minor actions (all done 2026-10-20), then rows, bond meter (replaces Coordination and Rally), telegraphs and interrupts, instant restart on defeat.

- In the prototype, a unit's Speed stands in for the DEX modifier in the delay formula: delay × (1 − (Speed − 8) × 0.04). <!-- ASSUMPTION: Speed 8 = no modifier, until attributes exist. -->
- Overdrawing Eld costs 1d4 HP per missing point but can't drop the user below 1 HP. <!-- ASSUMPTION: §5 doesn't say whether overdraw can Down you. -->
- Damage and heal amounts in the prototype use its own scale (Attack × power) until the class-progression note sets real stats; flat values (2 less per hit, armor −2) are this note's.
- The run-in and run-back are staging, not movement; position on the field still has no rules effect. They must fit the §9 budgets — the basic-attack budget (≤ 1.5 s) has not yet been measured against the run-in.

---

## 11. Named-Item Abilities

*(Decided 2026-10-19.)* Named weapons and armor carry abilities ([[design-pillars]] Itemization).

- **A separate item slot.** Each character's menu has their class skills (4–6) plus **one item-ability slot**, filled by their equipped named weapon. Equipping a named item never costs a class skill, and the menu stays the same size.
- **Weapons give an active ability**, paid from the Eld pool, pole-flavoured, moving Drift like any Eld use. It is a showcase beat (≤ 3 s, section 9) with its own hand-made effect.
- **Armor gives a triggered effect**, not a menu option: it fires on a condition (first time the wearer drops below half HP, when guarding an ally, when interrupted). No extra menu entries, still a visible moment.
- **Limit by effects work, not rules:** each named item needs its own animation and effect, so the real cap is the effects budget. 1–2 named items per character per act.

---

## 12. Class Eld Abilities (converted 2026-10-19)

Fighters and Thieves spend their small Eld pool (6 per fight) on these. Every use moves Drift ([[eld-magic]]). Converted from the grid version: "Defense" became damage reduction, "to hit" became damage, movement became rows. Visible effects follow the proposed rules in [[design-pillars]] Combat Presentation.

### Fighter

| Ability | Pole | Eld | Type | Effect |
|---|---|---|---|---|
| **Bulwark** | Forn | 2 | Action, quick | Guard one ally until your next turn: hits aimed at them hit you instead, and you take 2 less from each. Fills bond when it triggers. |
| **Stand Firm** | Forn | 3 | Minor | Until your next turn: you can't be pushed out of the front row, and you take 2 less from each hit. |
| **Break** | Vela | 2 | Action, normal, **Interrupt** | Heavy strike: normal damage, target's armor −2 for 2 of its turns. Interrupts a telegraphed move. |
| **Execute** | Vela | 3 | Action, heavy | If the target is below half HP, double damage. |

### Thief

| Ability | Pole | Eld | Type | Effect |
|---|---|---|---|---|
| **Fade** | Forn | 2 | Minor | Enemies can't target you until your next turn, unless every other party member is Downed. |
| **Mark** | Forn | 3 | Action, quick | Your attacks against this target deal +2 for the rest of the fight. |
| **Expose** | Vela | 2 | Minor | Until the target's next turn, the whole party deals +2 to it. |
| **Exploit** | Vela | 3 | Action, normal, **Interrupt** | An attack that ignores armor. Interrupts a telegraphed move. |

**The decision these create:** Forn abilities protect and prepare; Vela abilities end things faster. Which you reach for is who you are becoming.

**Who uses them:** Bram (Fighter set), Fen (Thief set), and a Fighter or Thief protagonist. Voryn and a Caster protagonist use spells ([[eld-magic]]). Arn has his own kit with no Eld ([[party-kits-act1]]).
