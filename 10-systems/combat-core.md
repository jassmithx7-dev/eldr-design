---
type: system
status: draft
depends_on: ["[[world-rules]]", "[[design-pillars]]"]
ue5_scope: L
open_questions:
  - "Slice class names are Fighter, Thief, and Caster ([[class-list]]). Level-up choices inside a class are still unwritten."
  - "Full attribute stat block (STR/DEX/CON/INT/WIS/CHA modifiers, racial ceilings) — deserves its own attributes-core note; referenced here as needed"
  - "Arn is outside the Eld system entirely — his divinity is not Eld-based. He does not cast. Resolved."
  - "Enemy stat tables (HP ranges, Defense, Attack Bonus by tier) — resolved for Ashfall slice via [[enemy-tiers-ashfall]]"
  - "Spell domain and Eld cost per spell — deferred to Phase 2 per world-rules"
  - "Does the Stabilization DC scale with enemy level or stay flat? Currently flat DC 10 — flag for playtesting"
  - "Can a Caster use a spell as a Reaction (counterspell equivalent)? Excluded in Phase 1 — the targeting and Eld-cost edge cases require spell school rules that do not exist yet. Reserved for Phase 2 spell-interrupt design."
  - "Does a Reaction Window open if the telegraphed cast targets a non-party entity (e.g., an enemy buffing another enemy)? Currently assumed no window opens if no party member appears in the ability's target pool. Needs confirmation once enemy ability targeting types are fully specified."
  - "Terrain tag modifiers (elevated / choke / hazard / difficult) — numbers TBD; identity soft-locked under Combat Identity §2"
  - "Boss-only heavy-melee Brace/Dodge tell — deferred; not in soft-lock"
---

# Combat Core

*The mechanical skeleton of every fight in Eldr. All other combat systems — spell domain, enemy AI, itemization — bolt onto this frame.*

---

## Design Principle

The grimness is tonal, not punishing. Combat must feel dangerous without being a punishment system. Characters are professionals — they fight smart, cover each other, and sometimes lose ground. The party has worked together for twenty years. That history should be legible in how the system rewards coordination.

**The combat loop creates three primary decisions:**

1. **Positioning:** Where do I stand? Flanking, range bands, and AoE exposure all depend on placement. Moving costs your React if you spend it to attack.
2. **Action allocation:** Do I attack (deal damage now), use an ability (deal damage later or enable the party), or revive a downed ally (forfeit offense for survivability)?
3. **Threat prioritization:** Who do I hit? The Veteran's Read bonus rewards disciplined target focus. Enemies have morale thresholds. Killing the leader before morale breaks ends the fight faster.

---

## Combat Identity (soft-locked 2026-07-29)

Three layers. Do not replace the spine with a second combat fantasy mid-slice.

### 1. Spine — Company Doctrine
This note’s existing frame: turn-based grid, Act / React / Move, flanking, Veteran’s Read, morale, Rally Shout, Reaction Windows on telegraphed casts. Friendship reads as **coordination**, not combo cutscenes.

### 2. Ashfall taste — Hold the Line
Slice encounters should often feel like **buying time**, not only kill-all: dual-win Gate (clear wave **and** evac meter — already locked in quest/zone), choke points, reinforcement pressure. **Terrain tags** (elevated / choke / hazard / difficult) are an encounter layer on the grid — exact modifiers TBD; not a new action economy. **Momentum Track** (fight-wide win/lose dial) is **out** — HP, morale, and objectives already signal pressure.

### 3. Intent layer — casters + bosses
Steal full “see it coming” Intent only where magic / bosses demand an answer:
- **Soft-locked:** Cast telegraphs + Reaction Windows on **meaningful enemy casters** and **all bosses**. Ashfall minimum: **Binder Acolyte** + **Soulwright**.
- **Not soft-locked yet:** Heavy-melee Brace/Dodge tells (boss-only Intent spice — decide later).
- **Player casters:** Stay equal via Eld pool, Act-to-cast, Spell Check risk, Drift — enemy telegraphs do **not** buff player mages. Phase 1: no spell-as-Reaction (Counterspell reserved Phase 2).

**Balance intent:** Enemy magic is powerful but **answerable**. Fighters’ React matters as much as a Binder’s cast. Player casters match fighters on a good round; they do not clear packs alone for free.

---

## Attributes (Reference)

A full attributes note is pending. Combat math references six attributes with the following modifier formula:

**Modifier = floor((Score − 10) / 2)**

| Score | Modifier |
|-------|----------|
| 8     | −1       |
| 10    | 0        |
| 12    | +1       |
| 14    | +2       |
| 16    | +3       |
| 18    | +4       |

**Relevant to combat:**
- **STR** — melee attack bonus, melee damage bonus, carry capacity
- **DEX** — ranged attack bonus, ranged damage bonus, initiative, Defense cap (armor-dependent)
- **CON** — HP at level 1, HP per level, Stabilization Roll modifier
- **INT** — Eld pool size (casters)
- **WIS** — Perception, morale resistance (enemy-facing; also perception-based reactions)
- **CHA** — outside combat scope

<!-- ASSUMPTION: Standard array at character creation is 15, 14, 13, 12, 10, 8 (player distributes). This is not yet decided. -->

---

## 1. Turn Order and Initiative

Combat is turn-based. At the start of each encounter, every participant (all party members and all enemies) rolls initiative simultaneously.

**Initiative Roll: 1d20 + DEX modifier**

The initiative track is displayed as a persistent UI strip (horizontal, left-to-right, icons in order). Characters act highest-to-lowest. The track updates if characters are added mid-combat (summoned enemies, ambush reinforcements).

**Tiebreaking (in order):**
1. Higher DEX score wins
2. If DEX scores are equal: party members beat enemies
3. If two party members tie: player chooses order

**Design note:** Tiebreaking in the party's favor is a small readability gift, not a balance lever. It ensures predictable sequencing without extra UI complexity.

**Initiative is rolled once per encounter.** It does not re-roll each round. This keeps the track stable and readable, which is important for solo dev UI implementation.

---

## 2. Action Economy

Each character gets the following on their turn:

| Resource | Name | Description |
|----------|------|-------------|
| 1 | **Act** | The primary action: Attack, Use Ability, Cast Spell, Use Item (non-quick), Revive Ally, Interact (lever, lock, chest) |
| 1 | **React** | The secondary action: Use Quick Item (potion, grenade), Draw or Sheathe weapon, Dash (extra movement equal to Speed), or execute a Veteran's Shout (see Section 7) |
| 1 | **Move** | Move up to Speed tiles (see Section 3). Movement does not require spending Act or React. |

**Spend order:** Move, Act, and React can be used in any order on a character's turn. A character may split their movement (move, then attack, then move again using remaining tiles).

**Characters may choose to hold their Act** by selecting "Wait." They drop to the end of the current round's initiative track and can interrupt before the start of the next round with their held action. This is not a full reaction system — it is a tactical delay, not an interrupt.

**Characters who are Downed do not take turns.** They make Stabilization Rolls on their initiative tick instead (see Section 5).

---

## 3. Movement and Positioning

**Grid:** Square, 1.5 m per tile. Characters occupy 1 tile (1.5 m × 1.5 m). Large enemies occupy a 2×2 tile footprint (3.0 m × 3.0 m).

<!-- ASSUMPTION: 1.5 m tile size. This fits a human-scale character model at typical isometric camera angles without overcrowding a corridor or making an open field feel like a parking lot. Adjust in playtesting. -->

**Speed (tiles per Move action) by armor type:**

| Armor Class | Tiles | Example |
|-------------|-------|---------|
| Unarmored | 8 | Fen (Thief default) |
| Light (leather, padded) | 6 | Standard |
| Medium (chainmail, scale) | 5 | — |
| Heavy (plate, splint) | 4 | Bram (Fighter default) |

Speed can be modified by abilities, encumbrance, or terrain (difficult terrain costs 2 tiles of movement per tile entered).

**Flanking:** When two party members occupy tiles on opposite sides of the same enemy (180° ± 45°), both receive **+2 to attack rolls** against that enemy for the duration of that positioning. Flanking is broken as soon as either character moves.

**This system creates the decision:** Do I spend my Move to reach flanking position (costing tiles, possibly entering melee with a second enemy), or attack from a safe angle and forgo the bonus?

**Range bands:**

| Band | Distance | Notes |
|------|----------|-------|
| Melee | 1 tile (adjacent, including diagonal) | Melee weapons only |
| Short | 2–6 tiles | Bows, thrown weapons, short-range spells |
| Long | 7–16 tiles | Bows at disadvantage beyond Short; crossbows full damage |

Ranged attacks into melee (targeting an enemy who is adjacent to an ally) incur **−2 to attack roll** (friendly fire risk, not mechanical damage — the penalty models the careful shot, not an accident system).

---

## 4. Attack Resolution

### To-Hit

**Roll: 1d20 + Attack Bonus vs. Target Defense**

| Result | Outcome |
|--------|---------|
| Roll ≥ Defense | Hit — deal weapon damage |
| Roll < Defense | Miss — no damage |
| Natural 20 (unmodified d20 = 20) | Critical Hit — roll weapon damage die twice, add modifiers once |
| Natural 1 (unmodified d20 = 1) | Critical Miss — attack fails; attacker loses their React action next turn |

**Attack Bonus = Base Attack Bonus (by level and class) + Attribute Modifier + Weapon Bonus**

- Melee attacks: attribute modifier is **STR**
- Ranged attacks: attribute modifier is **DEX**
- Finesse weapons (daggers, rapiers): attacker may use **STR or DEX**, whichever is higher

**Base Attack Bonus by class and level:**

| Level | Fighter | Thief | Caster |
|-------|---------|-------|--------|
| 1 | +1 | +1 | +0 |
| 2 | +2 | +2 | +1 |
| 3 | +3 | +3 | +1 |
| 4 | +4 | +3 | +2 |
| 5 | +5 | +4 | +2 |
| 6 | +6 | +5 | +3 |
| 7 | +7 | +5 | +3 |
| 8 | +8 | +6 | +4 |
| 9 | +9 | +6 | +4 |
| 10 | +10 | +7 | +5 |

<!-- Slice class list is Fighter, Thief, Caster. See [[class-list]]. Level-up options inside a class are still unwritten. -->

### Defense

**Defense = 10 + Armor Bonus + DEX modifier (capped by armor type)**

| Armor Type | Armor Bonus | DEX Cap | Defense Range (DEX −1 to +4) |
|------------|-------------|---------|-------------------------------|
| Unarmored | +0 | No cap | 9–14 |
| Light | +3 | +5 | 12–18 |
| Medium | +5 | +2 | 14–17 |
| Heavy | +8 | 0 | 18 |

Shields add **+2 Defense** and occupy the off-hand. A character holding a shield cannot use two-handed weapons.

### Weapon Damage Reference

| Weapon | Damage | Notes |
|--------|--------|-------|
| Dagger | 1d4 + DEX or STR | Finesse, concealable |
| Short sword | 1d6 + STR or DEX | Finesse |
| Longsword | 1d8 + STR | One-handed |
| Greatsword | 1d10 + STR | Two-handed; −2 Defense while equipped (guard is committed to offense) |
| Hand axe | 1d6 + STR | Can be thrown (Short range band) |
| War hammer | 1d8 + STR | +2 damage vs. Heavy armor (crush vs. rigid plate) |
| Short bow | 1d6 + DEX | Short and Long range |
| Crossbow | 1d8 + DEX | Long range full damage, no disadvantage beyond Short; reload costs React |
| Spear | 1d8 + STR | Reach: can attack from 2 tiles without moving into melee |

Dag's gear modification system can extend these baselines (e.g., +1 weapon bonus, added damage type, Eld-infused edge). Those enhancements are external to this note.

### Damage Reduction

Heavy armor provides **2 points of physical damage reduction** in addition to its Defense bonus. This applies after a hit is confirmed, reducing the damage roll by 2 (minimum 1 damage per hit).

No other armor tier provides damage reduction. The distinction makes heavy armor genuinely protective against many small hits, at the cost of speed and DEX bonus.

---

## 5. HP Model and the Downed State

### HP at Character Creation (Level 1)

**HP = Class Base + CON modifier (minimum 1)**

| Class | Base HP |
|-------|---------|
| Fighter | 12 |
| Thief | 8 |
| Caster | 6 |

**HP gained per level = Class Growth + CON modifier (minimum 1)**

| Class | Per-Level Growth |
|-------|-----------------|
| Fighter | 7 |
| Thief | 5 |
| Caster | 4 |

**Example:** Bram (Fighter, CON 14, modifier +2) at Level 1: 14 HP. At Level 5: 14 + (4 × 9) = 50 HP.

<!-- ASSUMPTION: Fixed HP growth (no roll). Solo dev: deterministic progression is easier to balance and eliminates a whole category of "my rolls were bad" complaints. -->

### Going Down

At 0 HP, a character is **Downed.** They are incapacitated: they cannot move, act, or react. They are not dead.

**Stabilization Roll:** On the downed character's initiative tick each round, they roll **1d20 + CON modifier vs. DC 10.**

| Outcome | Effect |
|---------|--------|
| Roll ≥ 10 (success) | Character **stabilizes** — stops rolling, remains unconscious at 1 HP. Will regain consciousness at end of combat. |
| Roll < 10 (failure) | Accumulate 1 failure. At **3 cumulative failures**, the character is **out for the encounter** — unconscious and unrevivable until combat ends. They survive. |

Characters do not die from combat failure. Death occurs only when the story demands it — authored in specific narrative moments, not generated by the stabilization system. A party member who reaches 3 failures wakes after the fight, shaken but present.

**Reviving Mid-Combat:** An adjacent conscious ally spends their **Act** to revive a downed or stabilized character. The revived character wakes with **1 HP + CON modifier** (minimum 1) and can act on their next initiative turn.

**This system creates the decision:** Do I spend my Act to revive an ally now (giving up my attack, potentially preventing 3 more failures), or do I trust they'll stabilize and press the offensive? The wrong call in both directions costs the party.

### Healing in Combat

Potions are consumed via React (Quick Item). A standard healing potion restores **2d4 + 2 HP** (average 7). Potions cannot restore a downed character above 0 HP if they are used remotely — a character must be adjacent and conscious to administer a potion to someone at 0 HP (uses Act, not React, in that case).

<!-- ASSUMPTION: Healing magic exists in some form per the Phase 2 spell domain. Whether it restores HP or only stabilizes is deferred. world-rules flags this as an open question. -->

---

## 6. Eld and Class Abilities

The world is saturated with Eld. All classes have some sensitivity to it. What differs is how developed that sensitivity is and what the character does with it.

**Eld Pools:**

| Class | Eld Pool | Formula |
|-------|----------|---------|
| Caster | Large, scales with INT | 10 + (INT modifier × character level) |
| Fighter | Small, flat | 6 |
| Thief | Small, flat | 6 |

Eld does not regenerate mid-combat. Full restoration occurs at rest (camp/rest point).

**Casters:** Access to the full spell list across all nine schools. See [[eld-magic]] for casting rules, Spell Check, and school detail.

**Casting past 0 Eld (Casters only):** A caster who is at 0 Eld may still attempt to cast. Each Eld point short of the spell's cost deals **1d4 HP damage to the caster**. This is a hard choice, not an automatic failure.

**Fighters and Thieves:** Cannot cast spells. Their small Eld pool powers a set of class-specific combat abilities — instinctive Eld use developed through years of fieldwork rather than study. These abilities do not require a Spell Check. Eld is spent and the effect activates. Subsequent attack rolls still apply normally where relevant.

**All classes experience Drift.** Every Eld ability is pole-flavored. Using it moves the Drift Counter by +1 (Vela-pole) or −1 (Forn-pole), identical to spellcasting. The same thresholds, the same environmental cues, the same ending. See [[eld-magic]] — Drift mechanic.

---

### Fighter Eld Abilities

*Physical and instinctive. These are not spells — they are what a veteran learns to do with Eld without ever studying it.*

| Ability | Pole | Eld | Trigger | Effect |
|---------|------|-----|---------|--------|
| **Bulwark** | Forn | 2 | Your turn (Act) | An adjacent ally gains +3 Defense until the start of your next turn. You put yourself between them and the threat. |
| **Stand Firm** | Forn | 3 | Your turn (React) | Until the start of your next turn, you cannot be moved, knocked back, or knocked prone. You hold the position regardless of what hits you. |
| **Break** | Vela | 2 | Your turn; resolves on next melee hit | Your next melee hit reduces the target's Defense by 2 for 2 rounds. Something in their guard, their armor, or their footing gives. |
| **Execute** | Vela | 3 | Your turn; resolves on next melee hit | If the target is below half HP, your next attack this turn deals double weapon damage dice. You find the opening when they're already losing. |

*Decision created:* A Fighter's 6 Eld covers 2–3 ability uses per encounter. Bulwark and Stand Firm keep allies alive and positions held — Forn decisions, the work of someone who protects. Break and Execute end fights faster — Vela decisions, the work of someone who finishes things. Which you reach for more often is who you are becoming.

---

### Thief Eld Abilities

*About movement and exploitation. The Thief uses Eld without naming it — it is just what their body learned to do after long enough in the dark.*

| Ability | Pole | Eld | Trigger | Effect |
|---------|------|-----|---------|--------|
| **Fade** | Forn | 2 | Your turn (Move or React) | Move up to your Speed without provoking attacks of opportunity. You slip from the enemy's immediate awareness. They must spend their Act on their next turn to reacquire you; until then, they cannot target you. |
| **Mark** | Forn | 3 | Your turn (Act) | You read the target carefully. Until end of combat, your attacks against this target gain +1 to hit without requiring Veteran's Read. You have learned them. |
| **Expose** | Vela | 2 | Your turn (React) | You demonstrate a weakness in the target's position. Until the end of the target's next turn, all party members gain +1 to hit against them. |
| **Exploit** | Vela | 3 | Your turn; resolves on next attack | Your next attack this turn bypasses the target's armor damage reduction and any Defense bonus from a Shield. You find the crack and use it. |

*Decision created:* Fade and Mark are about patience — learning, preserving options, protecting the ability to act (Forn). Expose and Exploit are about taking — extracting advantage, using what you found against someone (Vela). A Thief who consistently Exploits is declaring something different from one who consistently Marks.

---

Fen does not use Eld abilities — her sensitivity is characterization only (see [[companion-fen]]). Bram does not use Eld. Arn does not use Eld (his divinity is not Eld-based — see [[companion-arn]]). Voryn is an Eld-Weaver with the full caster pool.

---

## 7. The Party Bond — Veteran's Read

The party has worked together for approximately twenty years. The mechanical expression of this is not a special system — it is a persistent passive and one triggered ability that costs nothing to implement beyond a flag and a modifier lookup.

### Passive: Veteran's Read

When a character makes an attack against an enemy that **another party member also attacked during the previous round**, the attacking character gains **+1 to hit** on that attack.

*Implementation note: track last-attacker-ID per enemy entity. If any party member ≠ current attacker hit this enemy in round N−1, set +1 to-hit flag for current attacker this round.*

"We've run this pattern a hundred times." The bonus is small enough that it rewards discipline without mandating it, and it expires each round, so it requires repeated coordination rather than a one-time setup.

### Triggered: Rally Shout

Once per combat per character, as a **React**, any conscious party member who witnesses a companion go down (within 6 tiles, line of sight) may shout. The downed companion's next Stabilization Roll is made with **+4 bonus**.

This does not require a special ability slot, talent, or level unlock. It is available to every character from level 1 because twenty years of working together means you know what to say.

**This system creates the decision:** Do I spend my React on Rally Shout now (protecting my downed ally from dying on their next roll), or save my React for a potion, a weapon switch, or a Dash? The decision has weight because React is also the resource for other useful actions.

---

## 8. Dag's Gear and the Party

Dag is not a playable party member — he is the camp craftsman, an NPC. He does not enter combat.

**One mechanical consequence worth designing:** Gear modifications that Dag applies may carry a condition: if the modified character is Downed, high-maintenance enhancements deactivate until the character recovers. The reasoning is that the modification requires upkeep — which an unconscious character cannot perform. This is a mild texture, not a punishment system. Deferred to the gear-modification system note when that note is written.

---

## 9. Encounter End Conditions

### Victory

The encounter ends in **victory** when all enemies are eliminated (dead, routed, or surrendered).

**Enemy Morale:** Humanoid enemies who fall below **25% of their starting HP** make a Morale Check on their next turn: **1d20 + WIS modifier vs. DC 12 + party level.** On a failure, the enemy routes (flees the encounter area; counts as eliminated for victory purposes). Beasts and undead do not check morale.

*The morale threshold creates a decision: focus fire on one enemy to kill it quickly, or spread damage across multiple enemies to trigger multiple simultaneous morale checks?*

### Defeat

All five party members are simultaneously Downed or out for the encounter. The encounter ends in defeat.

**Consequence of defeat:** The game returns to the last rest point. No permadeath. No persistent injury. No character can die from combat mechanics — death is a story event, authored deliberately, never generated by a stabilization roll. Loss has weight through writing: the party's dialogue after a close call, the acknowledgment of what almost happened. The grimness lives there.

### Special Conditions

Some encounters end on a condition that is not "kill everything": protect a location, survive N rounds, reach a trigger zone, eliminate a named leader. These are per-encounter overlays on the core loop, not changes to the loop itself. They are authored in encounter notes, not here.

---

## 10. Worked Combat Example (Level 2)

**Setup:** Bram (Fighter/Blade, L2, STR 14, CON 14, heavy armor) and Fen (Thief, L2, DEX 16, light armor) vs. two Ashfall Mercenaries (Defense 14, HP 20, Attack +2, 1d6+1 damage).

**Initiative:**
- Fen rolls 1d20+3 = 15 (acts first)
- Mercenary A rolls 1d20 = 12
- Bram rolls 1d20+0 = 9
- Mercenary B rolls 1d20 = 7

**Round 1:**
- *Fen's turn:* Moves 2 tiles (flanking position on Mercenary A alongside Bram). Attacks Mercenary A: 1d20 + 1 (level) + 3 (DEX) = 1d20+4 vs Defense 14. Rolls 11+4 = 15. **Hit.** Damage: 1d6+3 = 5. Mercenary A at 15/20 HP.
- *Mercenary A:* Attacks Bram: 1d20+2 vs Defense 18 (heavy plate). Rolls 8+2 = 10. **Miss.**
- *Bram's turn:* Flanking bonus applies (+2) because Fen is on opposite side. Attacks Mercenary A: 1d20 + 2 (level) + 2 (STR) + 2 (flanking) = 1d20+6 vs Defense 14. Rolls 7+6 = 13. **Miss.** (needs 14+, bad luck). Bram has not used React. Uses React to Dash toward Mercenary B (3 tiles, positioning for Round 2).
- *Mercenary B:* Attacks Fen: 1d20+2 vs Defense 16 (light armor, DEX +3). Rolls 14+2 = 16. **Hit.** Damage: 1d6+1 = 5. Fen at 12/17 HP.

**Round 2:** Veteran's Read kicks in — Fen attacked Mercenary A last round, so Bram gets +1 to hit vs. Mercenary A this round as well. Mercenary A is at 75% HP — above morale threshold. The fight continues.

---

## 11. Complexity Assessment

**Estimated implementation scope: Large (L)**

Core components and rough Unity task breakdown:

| Component | Complexity | Notes |
|-----------|------------|-------|
| Grid manager (1.5m tiles, occupancy, pathfinding) | High | A* on square grid; Unity has nav mesh alternatives but grid is more predictable for CRPG |
| Initiative tracker + UI strip | Medium | Sort on combat start; update on change |
| Action economy state machine (Act/React/Move tracking per turn) | Medium | Per-character state; straightforward FSM |
| Attack resolution (d20, hit/miss, damage, critical) | Low | Pure math; simplest component here |
| HP + Downed state + Stabilization Roll | Medium | Per-character state, death tracker |
| Flanking detection | Low | Tile adjacency check, 180° calculation |
| Veteran's Read (last-attacker-per-enemy flag) | Low | One int per enemy entity |
| Rally Shout (React expenditure + Stabilization modifier) | Low | Flag + modifier; once-per-combat constraint |
| Morale checks (HP threshold, WIS roll) | Low | Triggered on damage; exit behavior is flee pathfinding |
| Eld pool + casting-past-zero | Low | Resource bar; damage on overdraw |
| Dag's gear offline on downed | Low | Boolean flag per modified item |
| Enemy AI (action selection, target priority) | High | Largest unknown; basic priority AI is achievable; tactical AI is not |
| Reactions — `REACTION_WINDOW` FSM state | Medium | One new TurnManager state; on/off React tracking per character per round; sequential party prompt loop with event callbacks; cast ring decal + CASTING banner VFX + initiative strip highlight; no new resource, draws on existing React bool |

**The enemy AI is the risk.** Everything else is bounded. A basic priority-based AI (attack nearest target, use abilities at threshold HP, morale check on low HP) is implementable in 1–2 weeks. A sophisticated tactical AI is not. **Recommendation:** ship with deterministic priority AI for the vertical slice; post-launch behavior tree if the game ships.

**Total estimate for vertical slice implementation (one zone, one encounter type): 4–6 weeks** for an experienced Unity/C# solo developer. This is over the 2-week per-system guideline.

**Simpler alternative:** Reduce to a pure point-and-click ARPG (no grid, no turns). **Rejected.** Turn-based + grid is locked per [[design-pillars]], and it is the correct call — real-time ARPG requires enemy AI that is tactically interesting at all times, which is harder, not easier. The grid and turns mean enemy AI only needs to produce one decision per turn, which is achievable solo.

**Phased implementation path to stay in budget:**
- **Phase 1A (2 weeks):** Grid manager, initiative, action economy, attack resolution, HP/downed. Playable skeleton — two fighters punching each other. No abilities, no spells, no morale.
- **Phase 1B (1 week):** Flanking, Veteran's Read, Rally Shout, morale checks, Dag's gear flag. Full party bond mechanics.
- **Phase 1C (1 week):** Eld pool, potion React, basic enemy AI. Encounter-complete.
- **Phase 1D (1 week):** Reaction Window (`REACTION_WINDOW` FSM state, cast ring VFX, initiative strip highlight, off-turn React expenditure). Requires Phase 1A FSM as prerequisite. Soulwright tutorial encounter gates this phase.
- **Phase 2:** Spell domain, enemy ability set, encounter-specific overlays, caster spell-as-Reaction (counterspell design).

---

## 12. Reactions

*An off-turn interruption system. Narrow by design. One trigger. Binary choice. The Soulwright teaches it.*

**This system creates the decision:** When an enemy begins casting, do you spend your React now — disrupting, damaging, or shielding — and forfeit the React you would use on your own turn? Or do you hold it and let the cast land?

---

### 12.1 Trigger — Telegraphed Cast

A **telegraphed cast** is an enemy ability whose data asset (`EnemyAbilityDataSO`) carries the designer-set flag `bTelegraphsCast = true`. This flag is authored at design time, not computed at runtime. The same ability asset shared across multiple enemy types propagates the flag to all of them.

Only abilities with `bTelegraphsCast = true` pause the enemy turn and open the Reaction Window. The following are explicitly excluded:

| Action type | Telegraph? | Reason |
|---|---|---|
| Standard melee attack | No | Intent is legible; no design value in pausing |
| Ranged attack (non-cast) | No | Same as above |
| Movement | No | Pausing for movement creates too many repositioning edge cases |
| Passive aura activation | No | Not a discrete action; no decision point |
| Telegraphed cast (`bTelegraphsCast = true`) | **Yes** | Opens Reaction Window |

**Isometric UI — three simultaneous layers:**

1. **Cast Ring.** A pulsing circular ground decal appears around the casting enemy. Color: amber (#E8A020). Radius: equal to the ability's effect area for AoE; 1 tile for single-target abilities. Pulse: 1 full pulse per 0.6 seconds. If the ability is targeted (single-target or directed AoE), a directional arrow indicator extends from the caster toward the intended target. The ring persists for the entire Reaction Window and disappears when the window closes.

2. **CASTING banner.** A floating text label reading "CASTING" appears above the casting enemy's model and on their initiative strip portrait. Uses the same font and scale as the combat log. Duration: entire Reaction Window.

3. **Initiative strip highlight.** All party member portraits with `bReactionAvailable == true` gain a 2 px yellow border (#FFD700). Portraits with `bReactionAvailable == false` drop to 50% opacity. This communicates at a glance who can still act.

---

### 12.2 Window — Duration, Order, and Closure

The Reaction Window is a **complete pause** of the enemy's turn. Real-world time is unlimited — this is a turn-based CRPG and the player may deliberate freely.

**Sequencing within the window:**

Party members are prompted in **initiative order, highest to lowest**, but only if `bReactionAvailable == true`. Each prompted character makes a single binary choice:

- **Spend Reaction** → select a valid Reaction action from §12.3 and resolve it immediately before the next character is prompted.
- **Pass** → no action taken; `bReactionAvailable` is not consumed (the player chose not to spend it, not that they couldn't).

Characters with `bReactionAvailable == false` are skipped automatically with no prompt.

**Closure:** When every eligible party member has responded (Spend or Pass), the window closes. The `bInReactionWindow` flag on `TurnManager` clears to `false`. The enemy's telegraphed cast then resolves in full, applying its normal effect.

**If no party members have `bReactionAvailable == true`:** The window does not open. The cast ring and banner appear for 0.4 seconds as visual feedback, then the cast resolves immediately. No pause occurs.

**No Reaction-on-Reaction:** If any Reaction action triggers an effect that would itself carry `bTelegraphsCast = true`, that inner telegraph is suppressed for the duration of the window. The `TurnManager` checks `bInReactionWindow` before evaluating any cast telegraph flag. This check costs one boolean read. No Reaction Window can nest inside another Reaction Window.

---

### 12.3 Valid Reaction Actions

Conservative list. Complexity is the enemy of a solo dev shipping anything.

| Reaction action | Details | Range constraint |
|---|---|---|
| **Standard Attack** | One weapon attack (melee or ranged) against any valid target within the equipped weapon's current range band. Normal to-hit and damage resolution. No flanking bonus — flanking requires a Move action, and Move is not available as a Reaction. | Equipped weapon range band |
| **Eld Ability (React-typed only)** | Any class Eld ability whose Trigger column in §6 lists "React." Current qualifying abilities: Fighter — **Stand Firm**; Thief — **Fade**, **Expose**. Casters have no React-typed Eld abilities in the current list. Eld cost applies normally. Drift counter moves normally. | Per ability definition |
| **Quick Item** | Use a potion or throwable on self or an adjacent ally (1 tile adjacent). Identical rules to Quick Item on own turn. | Self or 1-tile adjacent |

**Not valid as a Reaction:**

| Action | Excluded reason |
|---|---|
| Move | Repositioning before a cast resolves requires re-evaluating AoE targeting geometry mid-window — a disproportionate FSM complexity cost for Phase 1 |
| Act-typed Eld abilities (Bulwark, Break, Execute, Mark, Exploit) | These are Act actions; their economy belongs on the character's own turn |
| Spell (full cast list) | Casters spend Act to cast; Phase 2 will design a caster interrupt (counterspell equivalent) once spell school targeting rules exist |
| Revive Ally | Requires adjacency check, HP restoration, and FSM interaction with the downed state — too many edge cases for off-turn execution |
| Interact (lever, lock, chest) | Not combat-relevant in this context |

<!-- ASSUMPTION: Casters are excluded from using their spell list as a Reaction. This is the highest-value exclusion — a counterspell/interrupt-cast ability is the natural Phase 2 extension, but it requires spell school targeting rules that do not yet exist. Logged to open_questions. -->

---

### 12.4 Economy — Reactions Draw on the Existing React Resource

The Reaction is **not a new resource.** There is no separate Reaction token, counter, or pool. The existing `React` resource (§2) is the sole economy.

**Core rule:** Each character has 1 React per round. That single React covers both their off-turn Reaction Window use and their on-turn React actions. They are the same resource.

**Consumption rules:**

| Situation | Result |
|---|---|
| You spend your React on your own turn (potion, weapon draw, Dash, Rally Shout, Stand Firm via own turn) | `bReactionAvailable == false`. You cannot respond if a Reaction Window opens later this round. |
| You spend your Reaction in a cast window | React is consumed. When your own turn arrives this round, you have no React. |
| You Pass in a cast window | React is preserved. You may still spend it on your own turn. |
| You have not taken your turn yet and a window opens | You may spend your Reaction in the window, consuming your React before your turn arrives. |

**Refresh:** React restores at the start of each new round, when the initiative tracker loops. It does not restore mid-round when a character's individual tick completes.

**Interaction with Wait:** A character who has used Wait (held Act, dropped to end of round) retains their Reaction independently. Spending their Reaction in a cast window does not cancel or consume their held Act. The held Act resolves normally on their deferred initiative tick.

**No double-spend:** A character may spend their Reaction only once per Reaction Window. A window contains exactly one telegraphed cast (the condition that opened it), so there is no scenario where two Reaction spends would be solicited from the same character in one window.

---

### 12.5 Enemy Participation

An enemy entity participates in the Reaction system if and only if at least one entry in its `EnemyAbilityDataSO` array has `bTelegraphsCast = true`. The flag lives on the **ability asset**, not on the enemy entity. One ability asset with the flag propagates it to every enemy that holds a reference to that asset. No runtime computation determines participation.

**Enemy types and the flag:**

- **Cast-capable humanoids** (mages, channelers, summoners, ritual specialists): All abilities that are magical in nature receive `bTelegraphsCast = true`. Standard melee or ranged attacks on the same enemy do not.
- **Beasts:** No abilities expected to carry the flag in Act 1. Flag remains available for future creature design.
- **Standard soldiers / mercenaries:** No casting; flag not applicable.
- **Bosses:** At least one ability per boss encounter that carries `bTelegraphsCast = true` — the Reaction system must be exercised in every boss fight.

**Soulwright (Act 1 Boss):** The Soulwright is the designed tutorial for this system. At minimum two of the Soulwright's abilities carry `bTelegraphsCast = true`. The encounter is authored to guarantee a Reaction Window fires within the first two rounds of combat, allowing the player to learn the mechanic before it delivers full damage. Tutorial scripting — including first-time UI callouts and the guaranteed early window — is deferred to [[encounter-soulwright]]. This note specifies the mechanic; the encounter note specifies the pedagogy.

---

### 12.6 TurnManager FSM — State: REACTION_WINDOW

The `TurnManager` finite state machine gains one new state: **`REACTION_WINDOW`**.

**Branch description:** While in `ENEMY_ACTING`, if the enemy's selected ability resolves `bTelegraphsCast == true` and `bInReactionWindow == false`, `TurnManager` transitions to `REACTION_WINDOW` before executing the ability. On entry, it sets `bInReactionWindow = true` and iterates over all `CombatantController` entries in descending initiative order. For each entry where `bReactionAvailable == true` and `IsPlayerControlled == true`, the manager raises `OnReactionWindowPrompt(CombatantController)` and suspends the iterator, awaiting `OnReactionResponseReceived(CombatantController, ReactionChoice)`. `ReactionChoice` is a two-variant discriminated union: `Spend(ActionData)` or `Pass`. On `Spend`, the manager immediately invokes the normal action resolution pipeline for the chosen `ActionData`, then advances the iterator. On `Pass`, the iterator advances without consuming React. When the iterator is exhausted, `TurnManager` sets `bInReactionWindow = false`, transitions back to `ENEMY_ACTING`, and the telegraphed ability executes. The `bInReactionWindow` guard prevents any nested `REACTION_WINDOW` entry for the duration. The Technical Designer owns all implementation details; this paragraph names the architecture.

---

### 12.7 Relationship to Wait

Wait (§2) and Reactions are independent systems that share the React resource but do not otherwise interact.

| Axis | Wait | Reaction |
|---|---|---|
| What it holds | Act (primary action) | React (secondary action) |
| When it triggers | Player-initiated, own turn | System-initiated, enemy's turn |
| Condition | Player chooses to delay | Enemy uses `bTelegraphsCast` ability |
| Interaction | A character on Wait still has their Reaction unless already spent | Spending a Reaction does not cancel a held Act |

The §2 note "This is not a full reaction system — it is a tactical delay, not an interrupt" remains accurate. Wait is a turn-delay. Reactions are off-turn interrupts. They are not the same thing and do not conflict.
