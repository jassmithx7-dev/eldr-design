---
type: system
status: draft
depends_on: ["[[world-rules]]", "[[combat-core]]"]
ue5_scope: M
open_questions:
  - "Spell acquisition mechanism — do Casters begin with all 14 spells, or unlock them through leveling / found texts / Pale Circle access? Depends on class-progression note (not yet written)."
  - "Enemy stat tables must include WIS modifier for Spell Defense calculation. Defer to encounter-design note."
  - "Does Fen's Eld sensitivity provide any mechanical advantage for detecting magic, traps, or hidden workings? Characterization note deferred to companion note. Current ruling: no mechanical effect — narrative only."
  - "Range extension on select spells for acts 2-3. All spells are currently capped at Short range (2-6 tiles) as a vertical-slice constraint. Review after playtest."
  - "Does the Pale Circle teach all five disciplines, or are some disciplines considered heterodox / suppressed? Loremaster question — affects Voryn characterization and faction worldbuilding."
---

# Eld Magic

*The mechanical specification for all Eld-based spellcasting in Eldr. Covers spell disciplines, the full curated spell list, casting procedure in combat, and mechanical expression of the bodily cost. The Eld resource skeleton (pool formula, overdraw rule, rest restoration) is established in [[combat-core]] and is not duplicated here.*

---

## Design Principle

Magic is a trade. The caster studied for years and gave up physical development to do it. Every spell they throw is a decision against a limited resource that does not come back until the party rests. The decision the entire system creates is:

**Do I spend Eld now, knowing I cannot recover it until we camp — and knowing that casting past empty costs me HP?**

This maps directly to the lore: magic is expensive, cumulative, and practitioners who rely on it end up damaged. A sensible caster treats their pool like a professional treats expensive materials: uses them when the leverage is right, not because the option is available.

---

## Eld Resource (Reference)

This note does not re-specify the Eld pool. See [[combat-core]] §6 for the authoritative rule. Summary for reference only:

- **Eld Pool = 10 (Caster base) + (INT modifier × character level)**
- Non-casters: 0 Eld. Cannot cast. Period.
- Full restoration at rest only. No mid-combat regeneration.
- Casting past 0 Eld: each Eld point short of the spell's cost deals **1d4 HP** to the caster after the spell resolves.

**Representative pool sizes:**

| Level | INT 14 (mod +2) | INT 16 (mod +3) | INT 18 (mod +4) |
|-------|-----------------|-----------------|-----------------|
| 1     | 12              | 13              | 14              |
| 5     | 20              | 25              | 30              |
| 10    | 30              | 40              | 50              |

---

## The Five Disciplines

Practitioners and institutions (including the Pale Circle) organize Eld workings into five named disciplines. These are not schools with formal barriers — they are descriptive categories that emerged from centuries of practice. A caster who has studied broadly may work in all five. A specialist may favor one.

| Discipline | What it Does |
|------------|-------------|
| **Drive** | Kinetic force — push, hold, displace |
| **Char** | Thermal energy — burning, heat-denial, ignition |
| **Veil** | Perceptual manipulation — darkness, silence, visual distortion |
| **Knit** | Biological repair — flesh, tissue, stabilization |
| **Wrench** | Direct bodily disruption — pain, involuntary failure, stun |

There are 14 spells in the vertical slice, distributed 3 / 3 / 3 / 2 / 3 across the disciplines. This is a curated list. New spells are not added without deliberate design — each one requires implementation, VFX, and balance testing.

---

## Casting in Combat

### Action and Cost

Casting a spell spends the caster's **Act** action. It costs the listed Eld. The caster may move before or after casting (normal Move rules apply).

Eld is paid whether the spell succeeds or fails.

### Targeting

Spells fall into three target types:

| Target Type | Resolution | Examples |
|-------------|-----------|---------|
| **Targeted — enemy** | Requires a Spell Check (see below) | Scald, Shove, Seize |
| **Targeted — area** | Automatic — no roll. Effect applies to all creatures in radius. | Scorch, Dusk, Hush |
| **Targeted — self or ally** | Automatic — no roll. | Brace, Suture, Set, Haze |

Line of sight is required for all spells. The target tile (or center point of an area) must be visible to the caster. Casting through total darkness or solid walls is not possible.

All spells in the vertical slice have **Short range: 2–6 tiles.** The caster must be within 6 tiles of the target or the center point of an area effect.

<!-- ASSUMPTION: Short range only for vertical slice. Long-range variants of select spells (Char domain, 7–12 tiles) deferred to range-extension review in open_questions. -->

### Spell Check

For spells that target an enemy, roll:

**1d20 + INT modifier vs. Spell Defense (10 + target WIS modifier)**

| Result | Outcome |
|--------|---------|
| Roll ≥ Spell Defense | Hit — apply spell effect in full |
| Roll < Spell Defense | Miss — spell fizzles; Eld cost is still paid |
| Natural 20 | Critical — apply effect and deal an additional 1d6 damage if the spell deals damage. Non-damage control spells extend duration by 1 round on a Critical. |
| Natural 1 | Fumble — spell fails; Eld cost paid; caster loses React on their next turn (concentration broken) |

**Why Spell Defense uses WIS:** Mental fortitude, alertness, and awareness of one's physical state determine how well a target resists magical disruption. A high-WIS warrior who knows danger is coming is harder to seize or wrench than an oblivious one. Armor does not protect against force displacement or thermal energy — evasion and willpower do.

**Representative Spell Defense values for context:**

| WIS Score | Spell Defense |
|-----------|--------------|
| 8         | 9            |
| 10        | 10           |
| 12        | 11           |
| 14        | 12           |
| 16        | 13           |

At level 1, a caster with INT 16 (+3) hits SD 10 on a 7+: 70% chance. SD 12 on a 9+: 60% chance. These are meaningful but not punishing — the caster is a professional.

### Casting While Adjacent to an Enemy

A caster adjacent to a conscious enemy may still cast, but suffers **−2 to Spell Check rolls** (not Eld cost, not to-hit — only the spell check). Area spells and ally/self-targeted spells are unaffected — those do not require a roll.

This creates real danger for mages caught in melee: they are lightly armored, their spell accuracy degrades, and the overdraw risk is omnipresent. The counter is correct positioning — mages should not be in melee range without deliberate tactical reason.

**This system creates the decision:** Do I cast from my current position (−2, risky) or spend my Move to disengage first (costs tiles, might not be possible)?

---

## Spell List

### Drive — Kinetic Force

**Shove**
- **Eld cost:** 3
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- A concentrated burst of kinetic force strikes the target. On a hit, the target is pushed **3 tiles directly away** from the caster in a straight line. If the path is blocked by a wall or another unit, the pushed target stops at the obstruction and takes **1d6 impact damage**; any unit they collide with also takes **1d4 impact damage**.
- *Decision created:* Push a dangerous melee threat off a companion, or push a ranged enemy into a wall for bonus damage? Direction matters — the caster must be positioned correctly for the desired push angle.

**Brace**
- **Eld cost:** 2
- **Target:** Self (automatic)
- **Range:** Self only
- The caster hardens a kinetic shell around their body. Gain **+4 Defense** and **immunity to forced movement** (knockback, shoves, Heave) until the start of the caster's next turn. Does not require concentration.
- *Decision created:* Spend 2 Eld to survive a turn in melee while still being able to cast next round, or trust their low base Defense and hope enemies miss?

**Heave**
- **Eld cost:** 5
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- The target is lifted off the ground and held suspended for **1 full round**. While suspended: they cannot move, cannot attack, cannot use abilities. At the start of the caster's next turn, the effect ends: the target falls, taking **1d8 fall damage** and landing prone (costs 2 movement tiles to stand from prone).
- *Decision created:* Burn 5 Eld to completely remove the most dangerous enemy from a round, or spend it on two cheaper spells? Heave is the most expensive control spell in the game.

---

### Char — Thermal Energy

**Scald**
- **Eld cost:** 4
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- A mass of concentrated thermal energy strikes the target for **2d6 fire damage**. If the hit is confirmed (i.e., Spell Check succeeds), the target is **ignited**: they take an additional **1d4 fire damage** at the start of their next turn. The ignition extinguishes after one tick.
- *Decision created:* Spend 4 Eld for 2d6 + follow-up burn (strong single-target damage), or spread Eld across cheaper options?

**Scorch**
- **Eld cost:** 5
- **Target:** Area — ground point (automatic, no Spell Check)
- **Range:** Short (target center point 2–6 tiles away)
- **Radius:** 3-tile radius from center point
- A thermal detonation erupts from the target point. All creatures in the radius take **1d6 fire damage**. No Spell Check — the area effect is automatic. Catches allies in the radius as well; do not target adjacent to the party.
- *Decision created:* Spend 5 Eld for guaranteed area damage with no roll, or spend 4 Eld on Scald for higher single-target damage that might miss? Against three clustered enemies, Scorch is more efficient. Against one, Scald wins.

**Leach**
- **Eld cost:** 3
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- The caster strips thermal energy from the target, dealing **1d6 cold damage** and reducing the target's **Speed by 3 tiles** until the end of their next turn.
- *Decision created:* Spend 3 Eld to slow a fast, kiting enemy (locking them into range of melee allies), or save it for damage? Speed reduction does not deal much damage — it enables the party to do their jobs.

---

### Veil — Perceptual Manipulation

**Dusk**
- **Eld cost:** 3
- **Target:** Area — ground point (automatic, no Spell Check)
- **Range:** Short (target center point 2–6 tiles away)
- **Radius:** 4-tile radius from center point
- All mundane light sources (torches, lanterns) within the radius are extinguished. The area fills with magical shadow. Duration: until the end of the caster's next turn. All creatures within the area (ally and enemy) suffer **−4 to attack rolls** due to impaired visibility.
- *Decision created:* Blanket an enemy cluster in darkness (hurts them more than the party if the party is outside the radius), or save 3 Eld for a targeted spell? Requires careful positioning — Dusk is party-hostile if placed poorly.
- *Out-of-combat use:* Blind a guard post, traverse a lit corridor without being seen, create ambush conditions.

**Haze**
- **Eld cost:** 2
- **Target:** Single ally (automatic)
- **Range:** Short (2–6 tiles)
- The caster wraps a target ally in visual distortion. Attackers targeting that ally suffer **−2 to attack rolls** until the start of the caster's next turn. Does not stack with other Haze effects on the same target.
- *Decision created:* Spend 2 Eld to protect a companion who is about to be attacked, or spend it on offense? 2 Eld is the cheapest spell available — this is the "protect the wounded ally" button.

**Hush**
- **Eld cost:** 3
- **Target:** Area — ground point (automatic, no Spell Check)
- **Range:** Short (target center point 2–6 tiles away)
- **Radius:** 2-tile radius from center point
- No sound enters or exits the area. Duration: until the end of the caster's next turn. Creatures within the area cannot use abilities that require shouting or vocal projection — including [[combat-core]] §7 **Rally Shout**. Eld casting does not require a verbal component and is unaffected.
- *Decision created:* Silence an enemy caster or a tactically positioned enemy before they Rally Shout or use a shout-based ability, knowing the area is small and requires accurate placement?
- *Out-of-combat use:* Approach a guarded position without sound. Eavesdrop on a conversation without the party's own sounds betraying them.

<!-- ASSUMPTION: Eld casting is mental/somatic, not verbal. Hush therefore does not block a caster's own spells. This must be stated explicitly to prevent player confusion. If any spells are later designed to require verbal components, update this note. -->

---

### Knit — Biological Repair

**Suture**
- **Eld cost:** 4
- **Target:** Single ally (automatic)
- **Range:** Short (2–6 tiles)
- Accelerate biological repair in a target ally, restoring **2d4 + 2 HP** (average 7). Cannot restore above maximum HP. Cannot be used on a Downed target — use Set instead.
- *Decision created:* Spend 4 Eld to remotely heal an ally (no adjacency, no potion consumed), or let them use a potion from their own React? Suture heals from range at the cost of the caster's Act; a potion heals the same amount via the target's own React. Suture is strictly better when the target is out of potions, or when they need their React for something else.
- **Answers world-rules open question:** Healing magic exists. Its cost is 4 Eld and an Act — comparable in output to a potion but different in action economy.

**Set**
- **Eld cost:** 3
- **Target:** Downed ally (automatic)
- **Range:** Short (2–6 tiles)
- The caster stabilizes a Downed ally at range without physical contact. The target immediately counts as having passed a Stabilization Roll: they stabilize, stop accumulating failures, and will regain consciousness at 1 HP at end of combat. Does **not** grant 1 HP + CON modifier revival or restore combat capability. Compare with physical revival (adjacent, Act): that restores HP and combat readiness. Set only stops the clock.
- *Decision created:* Use Set (3 Eld, no adjacency, stops the clock but ally stays down) or spend the Act to physically revive the ally (adjacency required, ally returns to combat)?

---

### Wrench — Direct Bodily Disruption

**Seize**
- **Eld cost:** 4
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- The caster locks the target's musculature. On a hit: target's **Speed is reduced to 0** (cannot move) and suffers **−2 to attack rolls** for 1 round. On the target's next turn, the effect ends.
- *Decision created:* Spend 4 Eld to lock down a mobile enemy for one round, enabling melee allies to close — or let the enemy kite and spend the Eld on a damage spell?

**Rack**
- **Eld cost:** 3
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- A cascade of involuntary pain disrupts the target's body. On a hit: deals **1d4 damage** (this damage bypasses armor damage reduction — the disruption is internal) and the target's **next attack roll is made with disadvantage** (roll 1d20 twice, take the lower result).
- *Decision created:* Low damage but a guaranteed debuff if the Spell Check succeeds. Use Rack when a companion is about to be attacked and you want to reduce the incoming hit chance, not when you need damage output.

**Stagger**
- **Eld cost:** 6
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- The most expensive spell in the vertical slice. The caster delivers a direct neural disruption so overwhelming the target **loses their Act action on their next turn**. They retain Move and React. Eld cost is spent whether or not the Spell Check succeeds.
- *Decision created:* Is this enemy worth 6 Eld to remove from the board for one turn? At level 1 with a 13-Eld pool, casting Stagger leaves 7 Eld — enough for two or three more spells. At level 5 with 25 Eld, it's more sustainable. The spell's value scales with how dangerous the removed action would have been — and a miss at 6 Eld is painful.

---

## Spell Reference Table

| Spell | Domain | Eld | Target | Roll? | Effect Summary |
|-------|--------|-----|--------|-------|----------------|
| Shove | Drive | 3 | Enemy | Spell Check | Knockback 3 tiles; 1d6 impact on collision |
| Brace | Drive | 2 | Self | Auto | +4 Defense, knockback immunity, 1 round |
| Heave | Drive | 5 | Enemy | Spell Check | Suspended 1 round; 1d8 fall + prone on drop |
| Scald | Char | 4 | Enemy | Spell Check | 2d6 fire damage + 1d4 burn next turn |
| Scorch | Char | 5 | Area | Auto (no roll) | 1d6 fire damage, 3-tile radius |
| Leach | Char | 3 | Enemy | Spell Check | 1d6 cold damage + Speed −3 tiles, 1 round |
| Dusk | Veil | 3 | Area | Auto (no roll) | Extinguish lights; −4 attack rolls in area, 1 round |
| Haze | Veil | 2 | Ally | Auto | Attackers −2 to hit that ally, 1 round |
| Hush | Veil | 3 | Area | Auto (no roll) | Silence zone; blocks shout abilities, 1 round |
| Suture | Knit | 4 | Ally | Auto | Restore 2d4+2 HP; range revive not included |
| Set | Knit | 3 | Downed ally | Auto | Remote stabilize; stops failure clock, no HP |
| Seize | Wrench | 4 | Enemy | Spell Check | Speed 0, −2 attacks, 1 round |
| Rack | Wrench | 3 | Enemy | Spell Check | 1d4 damage (bypasses DR) + next attack disadvantage |
| Stagger | Wrench | 6 | Enemy | Spell Check | Target loses Act on next turn |

**Total spells: 14.** This is the complete vertical-slice spell list.

---

## Bodily Cost: Mechanical Expression

The long-term bodily degradation of Eld use is a **narrative fact**, not a mechanical track. See [[world-rules]] — old practitioners are visibly damaged; sensible people do not rely on magic; the cost is real and cumulative.

**What is implemented mechanically:**

1. **Acute overdraw** — 1d4 HP per Eld point short. Already in [[combat-core]] §6. Not duplicated here. This is the mechanical expression of the bodily cost made immediate and legible in combat.

2. **Nothing else.** No persistent degradation meter. No "casting scar" track. No separate stat that erodes over time.

**How the narrative carries it instead:**

- Veteran caster NPCs (including Voryn) are assigned **low CON scores** in their stat blocks — the consequence of a career in the craft expressed as a low HP value. A caster who has thrown spells for thirty years has a CON of 8 (modifier −1). No new system required — stat assignment at encounter design time does the work.
- Dialogue and character description handle the rest. Voryn's marked hand, the visible aging of the senior Pale Circle members, the way practitioners move as if something hurts — these are writing deliverables, not mechanical systems.

**Why this is the right call for solo dev:** A persistent degradation track would require: a new UI element, a persistent save variable per caster, balance testing against the main stat lines, and writing conditional dialogue for threshold states. The output would be a system that tells the player what the writing already tells them. The implementation cost is not recovered in player experience. Cut it.

---

## Eld Sensitivity in Non-Casters

### Fen (Thief)

Fen has Eld sensitivity and does not cast. This is **characterization only** — there is no mechanical system attached to it.

What sensitivity means for a non-caster: Fen perceives Eld the way a person with perfect pitch perceives musical notes — she notices it, it is part of her experience of the world, and she has never learned what to do with it. The perception does not grant detection abilities, trap-sensing, or magical resistance in the mechanical sense.

If Fen's sensitivity is used to detect active spellwork nearby or recognize a practitioner, that is a scripted dialogue moment in the encounter design or narrative — not a passive skill roll with a number attached.

<!-- ASSUMPTION: No mechanical detection bonus for Fen from Eld sensitivity. If the companion note decides otherwise, that note overrides this. -->

### Dag (Fighter) and Arn

No sensitivity, no casting. No note required beyond confirming the absence.

---

## Implementation Assessment

**Scope: M (Medium) — estimated 2 weeks for an experienced Unity C# developer.**

The system is data-driven. Each spell is a data record (ScriptableObject or equivalent):
- Name, domain, Eld cost, target type, range, effect type, effect parameters

The resolution code has two branches (Spell Check / Auto) and the effect application is a small number of shared primitives:
- Deal damage (with source type: fire, cold, kinetic, bodily)
- Apply stat modifier (Defense, Speed, attack roll, with duration in rounds)
- Apply state (suspended, prone, silenced, stabilized)
- Restore HP

Most spells combine one or two primitives. No spell requires custom physics, animation rigs, or a new resolution subsystem. Scorch and Dusk require radius detection (already needed for AoE and flanking — reuse that code).

| Component | Complexity | Notes |
|-----------|-----------|-------|
| Spell data structure (14 records) | Low | ScriptableObjects; define once |
| Spell Check resolution | Low | Same pipeline as attack rolls; INT modifier instead of STR/DEX |
| Spell Defense stat (10 + WIS mod) | Low | One additional field on enemy stat block |
| Targeted spell effect application (12 spells) | Medium | ~8 use existing primitives; 4 add new states (suspended, prone, silenced) |
| Area effect detection (Scorch, Dusk, Hush) | Low | Radius query on grid; share with existing AoE detection |
| Casting melee penalty (−2 Spell Check) | Low | Adjacency check, already exists for flanking |
| Spell selection UI (hotbar) | Medium | New UI component; bind to Act action |
| VFX per spell | Out of scope | Artist deliverable; engineer hooks only |

**Simpler alternative:** Reduce to 7 spells (one per discipline × 1 + two bonus) and cut the Veil and Knit disciplines entirely. **Rejected.** Healing and perceptual spells create different problem-solving options that the party needs to feel like a professional outfit. Fourteen spells at this level of mechanical simplicity is buildable within the 2-week estimate. The VFX is the actual risk, and that is an art budget question.

**The decision this system creates, stated explicitly:**

*Every combat, a caster decides: what is the right tool for this moment, and is it worth the Eld I will not get back?* Force control versus area damage versus targeted disruption versus supporting the party. The five disciplines ensure different enemy configurations call for different answers. The finite pool and rest-gated restoration mean every cast matters. The overdraw rule means "out of Eld" is never the end — it is a harder choice with a harder cost.
