---
type: system
status: draft
depends_on: ["[[world-rules]]", "[[combat-core]]", "[[design-pillars]]"]
ue5_scope: M
open_questions:
  - "Voryn's authored Drift schedule (starting counter value, per-act increment) — flagged inline; confirm in companion note."
  - "Spell acquisition mechanism — does the protagonist caster begin with all 18 vertical-slice spells, or unlock them through level-up / found texts / Pale Circle access? Depends on class-progression note (not yet written)."
  - "Enemy stat blocks must include WIS modifier for Spell Defense. Defer to encounter-design note."
  - "Are Divination spells available at character creation for a Forn-affinity caster, or are they taught by an NPC contact? They have no combat value and must be introduced at a narratively appropriate moment."
  - "Does Fen's Eld sensitivity give any mechanical advantage specifically against Illusion spells? Characterization question — deferred to companion note. Current ruling: no mechanical effect."
  - "Range extension on select spells (Elemental school) for acts 2–3. All spells currently capped at Short range (2–6 tiles) as vertical-slice constraint. Review after playtest."
---

# Eld Magic

*The mechanical specification for all Eld-based spellcasting in Eldr. Covers the two-pole structure, the nine schools, the full vertical-slice spell list, casting procedure in combat, affinity at creation, the Drift mechanic, and the bodily cost. The Eld resource skeleton (pool formula, overdraw rule, rest restoration) is established in [[combat-core]] §6 and is not duplicated here.*

---

## Design Principle

Magic is a trade, and the pole you work in is a declaration. The caster studied for years and gave up physical development to do it. Every spell they throw is a decision against a finite resource. The pole system adds a second layer: casting shapes you, and the world notices before you do.

**The system creates two interlocking decisions:**

1. **Do I spend Eld now, knowing I cannot recover it until we camp — and knowing that casting past empty costs me HP?** (The resource decision, from [[combat-core]].)
2. **Which school do I reach for? Every choice toward one pole is a choice away from the other, and the world is watching what I'm becoming.** (The alignment decision, from this note.)

A caster who only ever heals and wards is becoming something. A caster who only ever compels and drains is becoming something else. The drift mechanic means neither is cost-free.

---

## Eld Resource (Reference Only)

This note does not re-specify the Eld pool. See [[combat-core]] §6 for the authoritative rule. Summary for reference:

- **Eld Pool = 10 (Caster base) + (INT modifier × character level)**
- Non-casters: 0 Eld, cannot cast.
- Full restoration at rest only. No mid-combat regeneration.
- Casting past 0 Eld: each Eld point short of the spell's cost deals **1d4 HP** to the caster after the spell resolves.

**Representative pool sizes:**

| Level | INT 14 (mod +2) | INT 16 (mod +3) | INT 18 (mod +4) |
|-------|-----------------|-----------------|-----------------|
| 1     | 12              | 13              | 14              |
| 5     | 20              | 25              | 30              |
| 10    | 30              | 40              | 50              |

---

## The Two-Pole Structure

Eld is uniformly present in the world. It has no will. What differs is how a caster reaches for it and what shape they force it into.

Practitioners and scholars have named two opposing tendencies in how that shaping happens:

**Forn's Pole** — named by the Pale Circle for a theorist whose work described magic that preserves the existing state of things. Forn workings hold the world in place: they mend tissue, seal thresholds, reinforce what is, and read what has been. Forn magic is not gentle — a Warding that seals a door is an act of force. But its orientation is toward the intact, the whole, the lasting.

**Vela's Pole** — named for the same tradition's counter-argument. Vela workings break, compel, consume, and pass. They act on the world by moving through it destructively, even productively: draining vitality to empower the caster, compelling a target to stop, reading the cold logic of death and ending. Vela magic is not evil — a Necromancer who speaks with the recently dead to close a family's grief is not corrupt. But its orientation is toward entropy, change, and passage.

**Neutral (Raw Eld)** — the three schools that do not align with either tendency. Elemental, Alteration, and Illusion work raw Eld into natural force, physical change, and perceptual manipulation. They are not morally neutral — fire burns friends and enemies alike — but they do not pull the caster toward either pole. A caster who works exclusively in Neutral schools experiences no Drift.

**No worship is required.** Alignment is not granted by gods and not revoked by heresy. How you draw and shape Eld determines what you are becoming. The Pale Circle categorizes and teaches all nine schools. Whether they judge a practitioner for their choices is a factional question, not a mechanical one.

---

## Casting in Combat

### Action and Cost

Casting a spell spends the caster's **Act** action. It costs the listed Eld. The caster may move before or after casting. Eld is paid whether the spell hits or misses.

### Targeting

| Target Type | Resolution | Examples |
|-------------|-----------|---------|
| **Targeted — enemy** | Requires a Spell Check | Fear, Chain Lightning, Vampiric Touch |
| **Targeted — area** | Automatic — no roll; effect applies to all creatures in radius | Thunderwave, Glyph of Warding |
| **Targeted — self or ally** | Automatic — no roll | Shield, Cure Wounds, Blur |

Line of sight is required for all spells. Casting through total darkness or solid walls is not possible.

All spells in the vertical slice have **Short range: 2–6 tiles.** The caster must be within 6 tiles of the target or the center point of an area effect.

### Spell Check

For spells that target an enemy, roll:

**1d20 + INT modifier vs. Spell Defense (10 + target WIS modifier)**

| Result | Outcome |
|--------|---------|
| Roll ≥ Spell Defense | Hit — apply spell effect in full |
| Roll < Spell Defense | Miss — spell fizzles; Eld cost is still paid |
| Natural 20 | Critical — apply effect and deal an additional 1d6 damage if the spell deals damage; non-damage control spells extend duration by 1 round |
| Natural 1 | Fumble — spell fails; Eld cost paid; caster loses React on their next turn |

**Why Spell Defense uses WIS:** Mental fortitude and self-awareness determine how well a target resists magical disruption. Armor does not protect against compulsion or vitality drain — evasion and willpower do.

**Representative Spell Defense values:**

| WIS Score | Spell Defense |
|-----------|--------------|
| 8         | 9            |
| 10        | 10           |
| 12        | 11           |
| 14        | 12           |
| 16        | 13           |

At level 1, a caster with INT 16 (+3) hits SD 10 on a 7+: 70% chance. SD 12 on a 9+: 60% chance.

### Casting While Adjacent to an Enemy

A caster adjacent to a conscious enemy may cast, but suffers **−2 to Spell Check rolls.** Area spells and ally/self-targeted spells are unaffected — those do not require a roll.

**This system creates the decision:** Do I cast from my current position (−2, risky) or spend my Move to disengage first (costs tiles, may not be possible)?

---

## The Nine Schools

### FORN'S POLE — Preserves, Mends, Holds

---

#### Healing

**What it does:** Accelerates biological repair. Closes wounds, arrests disease, pulls a dying person back from the threshold. Eld is directed into the target's own body to do what the body would do if given time it doesn't have.

**Hard prohibition:** Healing cannot raise the dead. A body that has crossed into death is outside Forn's reach — the Eld finds nothing to work with. This is not a rule imposed by the Pale Circle. It is a property of how the school functions. [[world-rules]] makes this permanent canon.

---

**Cure Wounds**
- **Eld cost:** 4 (affinity: 3)
- **Target:** Single conscious ally (automatic)
- **Range:** Short (2–6 tiles)
- Accelerate tissue repair in a living ally. Restore **2d4 + 2 HP** (average 7). Cannot be used on a Downed (0 HP) target — use Spare the Dying instead. Cannot restore above maximum HP.
- *Decision created:* Spend 4 Eld to remotely heal an ally (no adjacency, no potion consumed, uses caster's Act), or let the target use their own React to drink a potion (same HP, different action economy)? Cure Wounds is strictly better when the target is out of potions or needs their React for something else.

---

**Spare the Dying**
- **Eld cost:** 3 (affinity: 2)
- **Target:** Single Downed ally (automatic)
- **Range:** Short (2–6 tiles)
- Stabilize a Downed ally at range without physical contact. The target passes their next Stabilization Roll automatically: they stabilize, stop accumulating failures, and regain consciousness at 1 HP at end of combat. Does **not** restore HP or return the ally to combat readiness. Compare with physical revival (adjacent, Act): that restores 1 HP + CON modifier and returns the ally to their next initiative turn.
- *Decision created:* Use Spare the Dying (3 Eld, no adjacency, stops the failure clock, ally stays down) or close distance and spend the Act to physically revive them (ally returns to combat but requires movement to reach)?

---

**Lesser Restoration**
- **Eld cost:** 5 (affinity: 4)
- **Target:** Single conscious ally (automatic)
- **Range:** Short (2–6 tiles)
- Remove one active negative status effect from the target (Fear, Command, Ray of Enfeeblement's STR reduction, Burning, any poison applied between encounters). In combat, additionally restores **1d4 HP** as the body rebounds from the cleared condition. Between encounters: removes disease and long-duration afflictions. Cannot restore wounds — use Cure Wounds for HP restoration.
- *Decision created:* Spend 5 Eld to remove a status that is costing an ally their actions or accuracy — worth it if the ally was Commanded or Frightened; overkill if they only had a minor debuff.

---

#### Warding

**What it does:** Forces Eld into barriers, seals, and countermeasures. Warding works by making a thing harder to change — a body harder to hit, a threshold harder to cross, a magical working harder to sustain.

**No prohibition specific to Warding.** The school does what it says. Note: Counterspell can prevent an enemy from casting but does not allow the caster to "interrogate" the enemy's magic or steal their spells.

---

**Shield**
- **Eld cost:** 2 (affinity: 1)
- **Target:** Self or single ally (automatic)
- **Range:** Short (2–6 tiles) for ally; Self if targeting self
- Harden an Eld barrier around the target. Gain **+4 Defense** and **immunity to forced movement** (knockback, displacement) until the start of the caster's next turn.
- *Decision created:* Spend 2 Eld on the cheapest defensive option to survive a turn in heavy fire — or use that Eld offensively and trust Defense to hold?

---

**Counterspell**
- **Eld cost:** 4 (affinity: 3)
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- On a hit: the target cannot use any magical ability, spell, or Eld-based effect on their next turn. They retain Move and physical attacks. On their next turn, the block expires automatically.
- *Decision created:* Spend 4 Eld to remove a dangerous enemy caster from the magical board for one turn, or deal damage instead? Counterspell has zero value against non-casting enemies — it is a targeted counter, not a general-purpose option.

---

**Glyph of Warding**
- **Eld cost:** 3 (affinity: 2)
- **Target:** Ground point (automatic, no Spell Check required to place)
- **Range:** Short (2–6 tiles from target center point)
- Inscribe a Warding glyph on the ground at the target tile. The glyph is invisible to enemies with WIS 10 or below; enemies with WIS 12+ may notice it (no mechanical effect — they can still walk into it). The first enemy to enter the glyph tile takes **−2 to all rolls** for 2 rounds. The glyph expires after triggering once or at end of combat.
- *Out-of-combat use:* Leave at a chokepoint before a rest; if the area is disturbed while the party sleeps, the disturbing creature takes the debuff and the noise may alert the party (implementation: scripted trigger, not passive detection roll).
- *Decision created:* Spend 3 Eld now to set a trap that pays off later — gamble on enemy routing or predictable pathing, or save it for certain-value combat spending?

---

#### Divination

**What it does:** Reads what has been. Divination accesses the emotional and experiential residue that Eld-sensitive people leave in places and objects. It reads the past, reads the emotional truth inside a living person, and cuts through deliberate deception — not because it reads minds, but because it reads what the body already knows.

**Hard prohibitions (both from [[world-rules]] and explicit design intent):**

- **Retrospective only.** Divination cannot predict the future, locate hidden objects, or reveal the position of people the caster has not already seen. "Where is the hidden lever?" is not a Divination question. "What was felt when the lever was last used?" is.
- **Cannot shortcut exploration.** Divination cannot replace investigation, searching, or dialogue. If an answer is meant to be found by looking, Divination cannot find it instead. This is a hard design prohibition, not a lore limitation — it is enforced at the content level. No Divination spell can return map-relevant information like locations, exits, or item positions.
- **Cannot expose the full truth.** Divination surfaces emotional impression, not deposition testimony. It tells the caster what was *felt*, not what was *done* in granular detail.

All Divination spells are **out-of-combat only.** They have no combat application. Eld spent on Divination is Eld the caster does not have in the next fight — that trade is the cost.

---

**Psychometry**
- **Eld cost:** 2 (affinity: 1)
- **Target:** Location or held object (automatic)
- **Range:** Touch (caster must physically contact the location or object)
- The caster reads the emotional residue of the location or object. Surfaces one recent emotional truth: what was *felt* here, not what was *done*. A bloodstained floor might return grief, not a description of the killing. A locked box might return anxiety, not its contents. The impression is approximately 7 days deep — older events fade.
- *What this replaces:* Investigation rolls that would otherwise be "did I notice anything?" Psychometry adds color and implication, not answers.

---

**Past Sight**
- **Eld cost:** 3 (affinity: 2)
- **Target:** Location or held object associated with a specific event (automatic)
- **Range:** Touch
- More focused than Psychometry. The caster perceives a fragmented, third-person visual impression of the most emotionally charged event associated with the target within the past 30 days. The impression is 5–10 seconds of subjective experience, not a full scene. It does not reveal dialogue content, names, or locations — only action fragments and felt weight. The caster cannot ask follow-up questions.
- *Canonical limitation flagged inline:* <!-- ASSUMPTION: Past Sight surfaces one event chosen by encounter scripting, not player-queried freeform recall. Implementation requires authored impression text per significant object/location. This is a content budget item. -->

---

**Discern Lies**
- **Eld cost:** 4 (affinity: 3)
- **Target:** Single NPC (out-of-combat, narrative context only)
- **Range:** Direct eye contact — effectively adjacent
- Spell Check required: 1d20 + INT modifier vs. Spell Defense (10 + target WIS modifier). On a hit: the caster reads whether the target is concealing something and what emotional category it falls into — shame, fear, grief, anger, or determination. Returns the category, not the secret. "They're hiding something out of fear" is a Discern Lies result. "They killed the merchant" is not.
- **Hard prohibition:** Discern Lies does not bypass social interaction. It adds information to a conversation; it does not replace the conversation. A frightened person concealing something still needs to be persuaded, pressured, or trusted into disclosure. Magic cannot solve a problem the player could solve by being a better person. This is a [[world-rules]] rule and a design pillar for the Enchantment school as well — stated here because Discern Lies is the closest Forn equivalent.
- *Decision created:* Spend 4 Eld and an out-of-combat Spell Check to narrow your read on an NPC before a high-stakes conversation — useful when you genuinely cannot tell if someone is lying or merely scared.

---

### VELA'S POLE — Breaks, Compels, Consumes

---

#### Enchantment

**What it does:** Works on the mind and will. Fear as a status effect. Compulsion as action denial. Enchantment operates in combat to strip options from enemies.

**Hard prohibitions:**

- **Combat only.** Command cannot be used outside of combat. It does not function in social scenes, cannot be used to bypass NPC dialogue, and cannot make an NPC do something outside a fight. This prohibition is absolute and enforced at the content scripting level.
- **No social charm or bypass.** The [[world-rules]] prohibition on "magic cannot solve a problem the player could have solved by being a better person" applies here in its fullest form. Enchantment does not make NPCs agreeable, reveal information, or open locked social paths.
- **Dream invasion is NPC-only.** Vela can invade the player's dreams as a story event (authored, specific). The player caster cannot use dream invasion on NPCs. This ability does not exist in the player's spell list.

---

**Fear**
- **Eld cost:** 3 (affinity: 2)
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- On a hit: the target is **Frightened** for 1 round. A Frightened target suffers **−2 to attack rolls** and cannot willingly move closer to the caster. They can still attack from range, defend themselves, or retreat. The status expires at the start of the target's next turn.
- *Decision created:* Push a dangerous melee threat out of close range for one round — but if it misses, 3 Eld is gone for nothing. Worth more against a single powerful melee enemy than against a group.

---

**Command**
- **Eld cost:** 5 (affinity: 4)
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- **Combat only.** On a hit: the target loses their **Act action** on their next turn. They retain Move and React. The compulsion is involuntary muscular arrest — not mind control. The target knows what happened. On the target's next turn, the effect ends automatically.
- *Decision created:* Spend 5 Eld to remove the most dangerous action from an enemy's next turn. Is this target's Act worth 5 Eld? The answer scales with how lethal the denied action would have been.

---

**Dispel Magic**
- **Eld cost:** 4 (affinity: 3)
- **Target:** Single enemy caster (Spell Check)
- **Range:** Short (2–6 tiles)
- **Only useful against enemies with Eld pools.** On a hit: the target's next spell costs **+4 Eld** above its normal cost. If they lack the Eld, they cannot cast (or can overdraw at the usual HP cost). The disruption expires after their next attempted cast or at end of their turn, whichever comes first.
- *Decision created:* Spend 4 Eld to potentially brick a dangerous enemy caster's next spell — but only if you know they're about to cast. Wasted against a non-caster or a caster who decides to move instead.

---

#### Necromancy

**What it does:** Works with the cold logic of finality — vitality drain, passage, and decay. Necromancy understands death as a state to be engaged with, not reversed.

**Hard prohibitions:**

- **No undead armies.** Necromancy cannot animate corpses for combat use in the vertical slice. The school is about passage and the residue of ending — not about conscripting the dead. [[world-rules]] prohibits raising the dead outright; Necromancy does not approach that limit.
- **Speak with Dead does not compel.** Speaking with the recently dead surfaces voluntary impression, not interrogated testimony. The dead have no obligation to answer fully or truthfully.

---

**Vampiric Touch**
- **Eld cost:** 4 (affinity: 3)
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- Drain vitality from a living target, dealing **1d6 + INT modifier necrotic damage** (bypasses armor damage reduction — the drain is biological, not physical). The caster recovers **HP equal to half the damage dealt** (round down, minimum 1 HP recovered). Does not restore Eld.
- *Decision created:* Vampiric Touch functions as the only offensive spell that also heals the caster. It is weaker in raw damage than Fireball or Chain Lightning. Worth casting when the caster is at low HP and a kill is not the priority — spend 4 Eld, deal 5–8 damage, and recover 2–4 HP. The trade is worse than Cure Wounds for healing but comes from the caster's own action rather than needing an ally's.

---

**Speak with Dead**
- **Eld cost:** 2 (affinity: 1)
- **Target:** A corpse not more than 24 hours dead (automatic)
- **Range:** Touch
- **Out-of-combat only.** Briefly speak with the recently dead. The dead can answer up to **3 questions**, responses limited to yes/no or a brief sensory impression. They are not compelled to answer fully. They cannot lie, but they can choose not to answer. They do not know anything they did not know in life. After 3 questions, the channel closes and cannot be reopened with that corpse.
- *Design note:* Speak with Dead is an encounter-design tool, not a general investigation bypass. Authors must assume the player will use it on significant corpses and write appropriate responses. A corpse that "doesn't know" anything is a missed opportunity.

---

**Ray of Enfeeblement**
- **Eld cost:** 3 (affinity: 2)
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- Briefly age living tissue at the target site. Deals **1d4 necrotic damage** (bypasses armor DR) and reduces the target's **STR by 2** for 2 rounds. An Enfeebled enemy with STR 12 temporarily has STR 10, reducing their melee damage output by the difference in modifier (in this case, from +1 to 0 — a −1 damage penalty per hit).
- *Decision created:* Low direct damage, but STR reduction debuffs the hardest-hitting melee enemies precisely when they're dangerous. Ray of Enfeeblement a boss-tier enemy before they reach the party's frontline.

---

### NEUTRAL POLE — Raw Eld, Neither Alignment

---

#### Elemental

**What it does:** Translates Eld into natural force — fire, water, lightning, earth, wind. The oldest and most legible school. No alignment effect. Elemental damage has no metaphysical implication; fire burns because it burns.

**No prohibitions beyond targeting rules.** Area Elemental spells affect allies. That is not a bug.

---

**Fireball**
- **Eld cost:** 4
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- Strike a target with concentrated fire. Deals **2d6 fire damage**. If the Spell Check hits, the target is **Burning**: takes **1d4 fire damage** at the start of their next turn (one tick, then extinguishes).
- *Decision created:* Spend 4 Eld for 2d6 + potential follow-up burn (strong single-target damage output) or split the Eld across cheaper options? Fireball is the reliable damage spell for a single threatening enemy.

---

**Thunderwave**
- **Eld cost:** 3
- **Target:** Area — ground point (automatic, no Spell Check)
- **Range:** Short (target center point 2–6 tiles)
- **Radius:** 3 tiles from center point
- A burst of force knocks all creatures in the radius **2 tiles directly away** from the center point. Deals no damage. Extinguishes all Burning effects on creatures in the radius (including allies — this can be useful). Allies are affected by the knockback equally; aim carefully.
- *Decision created:* Spend 3 Eld for guaranteed displacement with no roll — repositions enemies and allies alike. High skill-expression tool: used well, it breaks enemy formations; used carelessly, it sends an ally into worse ground.

---

**Chain Lightning**
- **Eld cost:** 5
- **Target:** Single primary enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- Strike the primary target with lightning for **1d8 lightning damage**. If the primary hit succeeds, lightning chains automatically to the nearest other creature within 2 tiles of the primary target — ally or enemy — for **1d4 lightning damage** (no Spell Check for the chain; it is automatic). If no creature is within 2 tiles, the chain does not fire.
- *Decision created:* Spend 5 Eld for the highest-damage single-target spell in the list — but only if the primary target is isolated. If an ally is within 2 tiles of the target, Chain Lightning will chain to them. Positioning the party correctly before casting is a genuine tactical requirement.

---

#### Alteration

**What it does:** Reshapes the physical — speeds a body, thickens skin, empowers a weapon's edge. Alteration does not align with either pole because it works on the material level, not the vital or spiritual level.

**No prohibitions specific to Alteration.** These are enhancement tools; their morality is in their use.

---

**Magic Weapon**
- **Eld cost:** 2
- **Target:** Single ally (including self) carrying a melee or ranged weapon (automatic)
- **Range:** Short (2–6 tiles) for ally; Self if targeting self
- Charge the target's weapon with Eld energy. The **next attack** made with that weapon deals **+1d6 bonus damage** regardless of whether the hit roll confirms (the Eld charge discharges on the next swing, hit or miss). Expires after 1 attack or end of combat, whichever comes first.
- *Decision created:* Spend 2 Eld to boost a high-damage ally's next hit — efficient when Bram is about to swing against a near-dead enemy, or when a crit-fishing build needs that extra die.

---

**Stoneskin**
- **Eld cost:** 3
- **Target:** Self (automatic)
- **Range:** Self only
- The caster's skin and muscle densify against incoming force. Gain **damage reduction 3** (reduce all incoming physical damage by 3, minimum 1 damage per hit) until the start of the caster's next turn. Does not require a Spell Check. Can be cast while adjacent to an enemy — it is auto-targeted and does not trigger the −2 melee casting penalty.
- *Decision created:* A caster caught in melee can spend 3 Eld to absorb multiple hits this round (DR 3 is significant against 1d6 enemies), buying time to disengage next turn — or they can cast an attack spell at −2 to Spell Check and try to end the problem.

---

**Haste**
- **Eld cost:** 4
- **Target:** Single ally (automatic)
- **Range:** Short (2–6 tiles)
- Target gains **+4 Speed tiles** and **+1 to attack rolls** for 1 round. The speed bonus applies to their next Move action; the attack bonus applies to any attacks made on their current or next turn (whichever is relevant depending on initiative order).
- *Decision created:* Spend 4 Eld to make a melee ally faster and more accurate for one round — high value when Bram needs to cross difficult terrain to engage a priority target, but wasteful if the ally was already in position.

---

#### Illusion

**What it does:** Works light, shadow, and perception — concealment, misdirection, and sound. Illusion is the stealth school. It does not deal damage. Its value is in creating tactical and exploratory options that would otherwise not exist.

**Prohibitions:**
- Illusion does not grant invisibility in the true sense — it creates perceptual difficulty, not absolute concealment. A creature actively searching in a small space will eventually find a Blurred caster. Illusion is a tool for initiative and surprise, not an "I win" exploration button.
- Phantasmal Force cannot be sustained beyond one round. It is a one-shot distraction, not a persistent decoy.

---

**Blur**
- **Eld cost:** 3
- **Target:** Self (automatic)
- **Range:** Self only
- The caster becomes visually indistinct — shapes and edges blur, color reads ambiguously. Attackers targeting the caster suffer **−3 to attack rolls** until the start of the caster's next turn. In combat, this does not make the caster invisible — the penalty applies to aimed strikes, not to area effects. Out of combat: while moving at half speed, the caster is treated as **Hidden** for stealth approach purposes (does not negate sound; does not work in open, well-lit ground without other cover).
- *Decision created:* Spend 3 Eld to make the caster significantly harder to hit for one round — or spend those Eld on offense and accept the low Defense of an unarmored mage? Blur is the "I'm about to be hit a lot and cannot disengage" button.

---

**Minor Illusion**
- **Eld cost:** 2
- **Target:** Ground point (automatic)
- **Range:** Short (2–6 tiles)
- Generate a convincing sound impression at the target location — footsteps, a voice, a weapon clash, a door opening. In combat: enemy units that have not yet confirmed a target spend their Move redirecting toward the illusion point for 1 round. Enemy units already engaged ignore it. Out of combat: draw a guard patrol, break a sentry's attention, create an opening to move.
- *Decision created:* Cheapest manipulation option in the Illusion school. Highly situational — wasted against already-engaged enemies, but potent against unalerted enemies or in stealth approaches.

---

**Phantasmal Force**
- **Eld cost:** 4
- **Target:** Single enemy (Spell Check)
- **Range:** Short (2–6 tiles)
- On a hit: the target perceives a threatening figure immediately adjacent to them (an illusion drawn from the target's own fear, not a specific shape the caster chooses). The target wastes their **Act** striking at the illusion on their next turn. At the end of that turn, they see through it automatically — the effect is one round only. On a miss, the target sees through the illusion immediately and the Eld is spent for nothing.
- *Decision created:* Spend 4 Eld and a Spell Check to remove a high-threat enemy's Act from the next round — same effect category as Command (5 Eld), but cheaper and going through INT vs WIS rather than through the Vela-pole cost of Command. The trade: Phantasmal Force has no other effect and requires a hit. Command guarantees a harder result at higher Eld cost and advances Drift toward Vela. *Using Phantasmal Force instead of Command against a frightening enemy is itself a Drift decision.*

---

## Spell Reference Table

| Spell | School | Pole | Eld (base / affinity) | Target | Roll? | Effect Summary |
|-------|--------|------|-----------------------|--------|-------|----------------|
| Cure Wounds | Healing | Forn | 4 / 3 | Ally | Auto | 2d4+2 HP; conscious targets only |
| Spare the Dying | Healing | Forn | 3 / 2 | Downed ally | Auto | Remote stabilize; stops failure clock |
| Lesser Restoration | Healing | Forn | 5 / 4 | Ally | Auto | Remove 1 status; +1d4 HP in combat |
| Shield | Warding | Forn | 2 / 1 | Self or ally | Auto | +4 Defense; knockback immunity; 1 round |
| Counterspell | Warding | Forn | 4 / 3 | Enemy caster | Spell Check | Block magical abilities for 1 round |
| Glyph of Warding | Warding | Forn | 3 / 2 | Ground point | Auto (place) | Trap tile: −2 all rolls for 2 rounds on first trigger |
| Psychometry | Divination | Forn | 2 / 1 | Location/object | Auto | Emotional residue; 7-day window; out of combat |
| Past Sight | Divination | Forn | 3 / 2 | Location/object | Auto | Fragmented visual impression; 30-day window; out of combat |
| Discern Lies | Divination | Forn | 4 / 3 | NPC | Spell Check | Emotional category of concealment; out of combat |
| Fear | Enchantment | Vela | 3 / 2 | Enemy | Spell Check | Frightened: −2 attacks, cannot close; 1 round |
| Command | Enchantment | Vela | 5 / 4 | Enemy | Spell Check | Lose Act next turn; combat only |
| Dispel Magic | Enchantment | Vela | 4 / 3 | Enemy caster | Spell Check | +4 Eld cost on target's next spell |
| Vampiric Touch | Necromancy | Vela | 4 / 3 | Enemy | Spell Check | 1d6+INT necrotic (bypasses DR); caster recovers half as HP |
| Speak with Dead | Necromancy | Vela | 2 / 1 | Corpse (≤24h) | Auto | 3-question conversation; out of combat |
| Ray of Enfeeblement | Necromancy | Vela | 3 / 2 | Enemy | Spell Check | 1d4 necrotic (bypasses DR); STR −2 for 2 rounds |
| Fireball | Elemental | Neutral | 4 | Enemy | Spell Check | 2d6 fire; Burning: 1d4 next turn |
| Thunderwave | Elemental | Neutral | 3 | Area | Auto | Knockback 2 tiles, 3-tile radius; extinguishes Burning |
| Chain Lightning | Elemental | Neutral | 5 | Enemy | Spell Check | 1d8 lightning; auto-chains 1d4 to nearest creature within 2 tiles |
| Magic Weapon | Alteration | Neutral | 2 | Ally weapon | Auto | Next attack +1d6 damage (discharges on swing) |
| Stoneskin | Alteration | Neutral | 3 | Self | Auto | DR 3 vs physical; 1 round; castable in melee |
| Haste | Alteration | Neutral | 4 | Ally | Auto | +4 Speed tiles, +1 attack rolls; 1 round |
| Blur | Illusion | Neutral | 3 | Self | Auto | Attackers −3 to hit; Hidden out of combat at half speed |
| Minor Illusion | Illusion | Neutral | 2 | Ground point | Auto | Sound decoy; redirect unengaged enemies 1 round |
| Phantasmal Force | Illusion | Neutral | 4 | Enemy | Spell Check | Target wastes Act on illusion; 1 round |

**Total spells: 24.** Vertical-slice implementation target: **18 spells** (all combat spells + Minor Illusion for stealth + Speak with Dead for narrative; defer Past Sight, Psychometry, and Discern Lies until act 2 content requires them).

---

## Affinity at Creation

At character creation, a caster picks one of three affinities: **Forn**, **Vela**, or **Neutral**. This represents where their natural sensitivity and early study invested — not a wall between them and other schools, but a well where they draw more easily.

### Mechanical Effects of Affinity

**Affinity-pole schools** (the 3–4 schools that belong to your chosen pole, or the 3 Neutral schools if Neutral):

| Benefit | Value |
|---------|-------|
| Eld cost reduction | −1 Eld per spell (minimum 1) |
| Spell Check bonus | +2 to Spell Check rolls |

**Opposite-pole schools** (schools belonging to the pole you did not choose):

| Penalty | Value |
|---------|-------|
| Eld cost increase | +1 Eld per spell |
| Spell Check bonus | none (no bonus, no penalty beyond cost) |

**Neutral affinity** receives cost reduction and +2 Spell Check for Elemental, Alteration, and Illusion. No cost change applies to Forn or Vela schools for a Neutral-affinity caster. Neutral affinity also confers **Drift resistance**: the Neutral caster's Drift Counter changes at half the normal rate (each Forn/Vela cast contributes ±0.5, rounded to nearest integer at the end of each encounter).

**Affinity is not a hard ceiling.** A Forn-affinity caster can learn Necromancy and pay +1 Eld per cast with no Spell Check penalty beyond the base. The cost is resource and, over time, alignment.

**Example:** A Forn-affinity caster with INT 16 (+3) casting Cure Wounds costs 3 Eld (affinity discount). The same caster casting Counterspell against an enemy: 1d20 +3 +2 (affinity) = 1d20+5 vs SD. The same caster casting Command: costs 6 Eld (base 5 + opposite-pole +1), no Spell Check bonus, and advances the Drift Counter by +1.

---

## The Drift Mechanic

### What Drift Is

Drift is the accumulation of pole-aligned casting choices. It is not a morality score. It is not a reputation. It is what the caster is becoming, expressed through how the world around them reads them before they understand it themselves.

**There is no UI meter. There is no alignment track the player watches.** The Drift Counter is an internal integer. The player learns where they are from the world's behavior — not from a display.

### The Counter

**Drift Counter:** an internal integer, range [−30, +30].

- **Starting values based on affinity:**
  - Forn affinity: −10 (already anchored toward Forn)
  - Neutral affinity: 0 (true center)
  - Vela affinity: +10 (already anchored toward Vela)

- **Per-cast changes:**
  - Cast from a Forn school: −1
  - Cast from a Vela school: +1
  - Cast from a Neutral school: no change
  - Neutral-affinity caster: each Forn/Vela cast contributes ±0.5 (round to nearest integer at encounter end)

- **Threshold events:** environmental cue fires when the counter **crosses** one of the following thresholds. Each threshold fires once in each direction.

| Threshold | Direction | Name |
|-----------|-----------|------|
| −10 | Forn | First Forn signal |
| −20 | Forn | Second Forn signal |
| −30 | Forn | Full Forn alignment |
| +10 | Vela | First Vela signal |
| +20 | Vela | Second Vela signal |
| +30 | Vela | Full Vela alignment |

A counter that oscillates across a threshold (crosses −10, comes back above, crosses −10 again) fires the cue event only on the **first crossing** in each direction. Re-crossing a threshold in the same direction fires no event.

### What "Sustained Use" Means in Practice

In a typical combat encounter, a caster throws 3–5 spells. An encounter-heavy run of 30 encounters produces 90–150 total casts. "Sustained use" of a single pole means the player is consistently choosing that pole's tools.

- A Forn-affinity caster (starting at −10) who casts exclusively Vela spells hits the first Vela signal (+10) after 20 net Vela casts. With 3–4 Vela casts per encounter, this registers around encounter 6–7. A full Vela flip requires +40 net Vela casts from starting position — achievable only by sustained, consistent Vela use with minimal Forn counter-casting.
- A Neutral-affinity caster who mixes freely will rarely approach a threshold. A Neutral caster who commits to one pole will drift slowly (half rate), reaching the first signal around 20+ net casts.

### Environmental Cues — What They Look Like

These are authored scene-level observations, not system pop-ups. They fire at threshold-crossing moments through ambient dialogue, environmental detail, or brief NPC reaction. **No text says "alignment shift registered."**

**Moving toward Vela (positive thresholds):**

- **+10 (First Vela signal):** An NPC who knows the caster mentions, unprompted, that they seem cold lately. In the same zone, a dog that approached the party before now keeps its distance from specifically the caster. A Forn-aligned healer NPC, if present, pauses before accepting the caster's hand for a greeting.
- **+20 (Second Vela signal):** Small plants in the caster's immediate vicinity — potted herbs at an inn, a patch of flowers near a camp — wilt within a day's proximity and recover after the party moves on. Eld manifestations (spell VFX) run slightly cooler in hue — the warm amber of Forn-adjacent work shifts toward silver-blue. A mortician NPC in a town remarks the caster has "the look." This lands as a compliment or an insult depending on that NPC's faction.
- **+30 (Full Vela alignment):** The caster's Eld-light is definitively cold — ice-blue, visible to anyone watching carefully. Forn-aligned constructs or creatures (if present in encounter design) treat the caster as a threat on sight. A Pale Circle archivist, if the party has access to one, pulls a sealed record away from the caster's line of sight without explanation.

**Moving toward Forn (negative thresholds):**

- **−10 (First Forn signal):** A wound the caster caused on an enemy in the previous encounter closes visibly faster than it should when the party passes the body. A sick NPC who was near the caster's spell-work the previous day reports feeling slightly better, without connection to the caster. A Vela-affiliated NPC comments the caster has been "soft lately."
- **−20 (Second Forn signal):** A child in a settlement approaches the caster without prompting and asks to see their hands — not afraid, drawn. A creature that would normally flee from humans holds its ground near the caster. Eld manifestations shift warmer — amber, or faint gold where there was none.
- **−30 (Full Forn alignment):** The caster's presence in places associated with recent death produces a stillness — not supernatural, but noted by companions in ambient dialogue. Things don't feel like they're decaying as fast. A Vela-affiliated NPC calls the caster by a Forn-tradition honorific as a mild insult that doesn't quite land that way.

### Voryn

Voryn's Drift Counter is **authored, not player-driven.** His counter advances independently of what the player caster does. He is the example of what the system reveals before the narrative confirms it.

<!-- ASSUMPTION: Voryn starts at +5 (slightly Vela-adjacent). His counter advances by +2 per completed act (scripted, not cast-tracked). By Act 2 start his counter reads +7; by Act 3 start, +9 — approaching but not yet crossing the first Vela threshold from the authored side. The threshold-cross event fires as a story beat, not a stat update. This schedule requires confirmation in the companion note when written. -->

The environmental cues around Voryn fire on the authored schedule. The player who is paying attention notices them before the story names them. The player who is not notices the story confirmation and finds it earned rather than sudden. Both readings are valid.

**Voryn's cues for the writer:** At Act 2, dogs and small animals avoid him. At Act 3, a Pale Circle contact who knew him before the game begins treats him with visible unease. Neither cue names what is happening.

### Design Note: No UI Meter

This is a firm constraint, not a placeholder. Showing the player a meter converts a system about how the world reads you into a system about how you manage a bar. The entire point is that the player learns what they are becoming from the world's behavior, not from a display. Any implementation that shows the Drift Counter value — in any form, as any UI element — is incorrect.

If a developer needs to debug drift behavior, the counter is exposed in a debug panel behind a flag. It does not exist in the shipped UI.

---

## Bodily Cost

The long-term bodily degradation of Eld use is a **narrative fact**, not a mechanical track. See [[world-rules]] — old practitioners are visibly damaged; sensible people do not rely on magic; the cost is real and cumulative.

**What is implemented mechanically:**

1. **Acute overdraw** — 1d4 HP per Eld point short of a spell's cost. In [[combat-core]] §6. Not duplicated here. This is the bodily cost made immediate and legible in combat.
2. **Nothing else.** No persistent degradation meter. No casting scar track. No stat that erodes over sessions.

**How the narrative carries it instead:**

- Veteran caster NPCs (including Voryn) are assigned **low CON scores** in their stat blocks — the consequence of a career in the craft. A caster who has thrown spells for thirty years has CON 8 (modifier −1): fragile HP and poor Stabilization Rolls. No new system required. Stat assignment at encounter design does the work.
- Dialogue and description handle the rest. Voryn's marked hand. The way senior Pale Circle members move as if something hurts. These are writing deliverables, not mechanical systems.

**Why this is the right call for solo dev:** A persistent degradation track requires a new UI element, a persistent save variable per caster, balance testing against the main stat lines, and conditional dialogue for threshold states. The output tells the player what the writing already tells them. Cut it.

---

## Eld Sensitivity in Non-Casters

**Fen (Thief):** Has Eld sensitivity and does not cast. This is characterization only — no mechanical system attached. Sensitivity means Fen perceives Eld the way a person with perfect pitch perceives musical notes: he notices it, it is part of his world, he has never learned what to do with it. No detection bonus, no magical resistance, no passive trap-sensing. If his sensitivity is used narratively (recognizing a caster's recent presence, noticing an active warding), that is a scripted dialogue moment in the encounter or narrative design, not a passive roll.

<!-- ASSUMPTION: No mechanical effect for Fen's sensitivity. If the companion note decides otherwise, that note overrides this ruling. -->

**Bram and Arn:** No sensitivity, no casting. Arn's divine nature is not Eld-based — see [[world-rules]].

---

## Implementation Assessment

**Scope: M (Medium) — estimated 2–3 weeks for an experienced Unity C# developer with the vertical-slice constraint applied (18 spells, not 24).**

### Core Data Structure

Each spell is a data record (ScriptableObject):
- Name, school, pole, Eld cost base, Eld cost affinity, target type, range, requires Spell Check (bool), effect type, effect parameters, out-of-combat only (bool), Drift contribution (+1 / −1 / 0)

The nine schools are a categorization enum — they drive UI organization and affinity lookup but not separate code paths. All spells use the same resolution pipeline.

### Resolution Branches

Two branches:
1. **Spell Check required:** roll 1d20 + INT + affinity bonus vs SD; apply hit/miss/crit/fumble table
2. **Automatic:** effect applies on cast; no roll

Effect primitives:

| Primitive | New? | Notes |
|-----------|------|-------|
| Deal damage (fire/lightning/necrotic/cold/kinetic) | Existing | Source type for DR bypass logic |
| Apply stat modifier (Defense, Speed, STR, attack roll) with duration | Existing | |
| Apply state (Frightened, Commanded, Burning, Counterspelled, Enfeebled) | New states | Frightened, Counterspelled, Enfeebled are new; Commanded = old Stagger renamed |
| Restore HP (ally) | Existing | |
| HP recovery for caster (Vampiric Touch) | New | Half damage dealt, rounded down |
| Knockback (Thunderwave — area knockback) | Existing | Thunderwave adds area version |
| Out-of-combat narrative hook (Psychometry, Past Sight, Discern Lies, Speak with Dead) | New | Trigger scripted scene via SpellCast event; no combat code path |

### Drift System

| Component | Complexity | Notes |
|-----------|-----------|-------|
| Drift Counter per caster entity (int) | Low | One int on caster stat block |
| Per-cast counter update | Low | On spell resolution, check school pole, increment |
| Threshold detection and event fire | Low | Threshold table lookup; fire authored scene event |
| Authored cue events (6 thresholds × 3–5 observations each) | Medium | Content, not code — writing and scripting deliverable |
| Voryn authored counter schedule | Low | 3 scripted counter increments at act transitions |

### Full Component Table

| Component | Complexity | Notes |
|-----------|-----------|-------|
| Spell data structure (18–24 records) | Low | ScriptableObjects; define once |
| Affinity lookup at cast time | Low | Flag on caster entity; modifier table |
| Spell Check resolution | Low | Same pipeline as attack rolls |
| Spell Defense stat (10 + WIS mod) | Low | One additional field on enemy stat block |
| Combat spell effect application (15 combat spells) | Medium | ~10 use existing primitives; 5 add new states |
| Area effect detection (Thunderwave, Glyph of Warding) | Low | Radius query on grid; reuse existing AoE |
| Casting melee penalty (−2 Spell Check) | Low | Adjacency check; reuse flanking detection |
| Out-of-combat spell hooks (Psychometry, Past Sight, Discern Lies, Speak with Dead) | Medium | Scene event system; authored response text per location |
| Drift Counter + threshold events | Low | Integer + threshold table |
| Spell selection UI (hotbar by school) | Medium | New UI; 9 school tabs or flat list with school icons |
| VFX per spell (pole-aligned hue shift on Drift) | Out of scope | Artist deliverable; engineer hooks for hue parameter |

### Vertical-Slice Constraint

**Ship 18 spells** in the vertical slice:
- All 9 combat-applicable Forn/Vela spells (Cure Wounds, Spare the Dying, Lesser Restoration, Shield, Counterspell, Glyph of Warding, Fear, Command, Dispel Magic — minus Divination's 3 out-of-combat spells)
- All 3 Necromancy spells (Vampiric Touch, Ray of Enfeeblement in combat; Speak with Dead for the one scripted narrative use)
- All 9 Neutral spells (Fireball, Thunderwave, Chain Lightning, Magic Weapon, Stoneskin, Haste, Blur, Minor Illusion, Phantasmal Force)
- Defer Psychometry, Past Sight, Discern Lies until the narrative structure of Acts 2–3 requires them; the out-of-combat hook system can be stubbed in Act 1 with authored "nothing to read here" results

**The decision this system creates, stated explicitly:**

*Every spell a caster throws is a resource decision and a declaration about what they are becoming. The two are never separable. A caster who reaches for Command instead of Phantasmal Force because it is more reliable is also drifting. A caster who defaults to Cure Wounds because it feels safe is also choosing. The system does not punish either choice — it witnesses them.*
