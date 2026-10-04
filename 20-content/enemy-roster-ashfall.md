---
type: encounter
status: draft
depends_on: ["[[game-premise]]", "[[zone-the-falling-gate]]", "[[combat-core]]", "[[pantheon]]", "[[enemy-tiers-ashfall]]"]
ue5_scope: M
inspired_by: ["challenge-skill-balance", "eight-elements-of-enjoyment", "paradox-of-control-flow"]
open_questions:
  - "Playtest retune only — baseline numbers live in [[enemy-tiers-ashfall]] (Ritual N = 6 starting assumption)"
---

# Enemy Roster — Ashfall Keep (Act 1 Slice)

*Slice-only. Not a world bestiary. Families: **Settled Host** (living Vela army) + **the Bound** (soul-war) + a few **large** threats. ~7 types + 1 boss.*

**Design rule:** Gate fights feel like a war. Shrine fights feel like the world being overwritten. Boss bridges both and runs the soul-trap (see [[game-premise]]).

**Morale reminder ([[combat-core]]):** Humanoid Settled Host check morale. Bound and beasts do not.

**Combat numbers:** [[enemy-tiers-ashfall]] (HP / Defense / Attack / damage / Ritual N). Do not duplicate stats here — retune in the systems note.

---

## Families

### Settled Host (living)
Vela's frontier army. People who chose (or were pressured into) her settlement. They break. They shout. They can flee.

### The Bound (soul-war)
Souls denied Mordrek's passage — hollowed, caged, or worn as tools. No morale. Horror pressure in the keep and shrine.

### Large threats
Few. Expensive to author and animate. Use as punctuation, not spam.

---

## Roster

| # | Name | Family | Size | Where | Role |
|---|------|--------|------|-------|------|
| 1 | **Settled Levy** | Host | Medium | Gate, streets | Melee trash. Spears/shields. Morale. *(Maps to "Ashfall Mercenaries" placeholder in [[combat-core]] worked example.)* |
| 2 | **Cinderbow** | Host | Medium | Gate walls, courtyards | Ranged. Harass from elevation. Morale. |
| 3 | **Chain Sergeant** | Host | Medium | Gate elite packs | Elite melee. Buffs nearby Levy (one-line aura: +1 to hit while sergeant up). Morale at lower HP only if alone. |
| 4 | **Unpassed** | Bound | Medium | Keep interior, shrine approaches | Hollowed melee. No morale. Slow, hard to put down, telegraphs soul-horror. |
| 5 | **Binder Acolyte** | Bound / Host hybrid | Medium | Shrine, undercroft | Support caster. Softens party / feeds the trap ritual. Priority interrupt target. |
| 6 | **Gatebreaker** | Large (living beast) | Large (2×2) | Gate breach moments | Living warbeast under Settled handlers. Siege brute; cracks formations. No morale (beast). Rare — 0–1 per gate encounter. |
| 7 | **Ash-Hound** | Large / Bound-touched | Large (2×2) | Keep depths, optional | Fast warbeast. Flanks and hunts isolated soft targets. Optional spice, not required every fight. |
| 8 | **Soulwright** | Bound + Host | Large (2×2) solo | Undercroft | Act 1 end boss. **Large solo** — no adds during the boss fight itself. Ritual specialist who built the trap under Ashfall. Runs the **soul-trap**; catches Bram & Fen. Must feel like total loss until Forn breaks it. |

---

## Encounter Diet (how to use them)

1. **Hold the Gate** — Levy + Cinderbow; one Chain Sergeant as spike; one Gatebreaker if the wall "breaks."
2. **Through the Keep** — mix Levy remnants with Unpassed; introduce Binder Acolyte once.
3. **Undercroft approach** — Binder Acolyte + Unpassed as the lead-in fight(s). Ash-Hound optional earlier, not in the boss room.
4. **Soulwright** — Large solo. No adds in the boss fight. Soul-trap beat plays here.

**Reuse budget:** These 7 + Soulwright cover the whole slice. Do not invent Act 2 forest fauna here. Full-game enemy ceiling: ≤25 kits (4–6 new per later act) — see [[design-pillars]].

---

## Gatebreaker

Living warbeast driven by Settled Host handlers (not a Bound flesh hulk). **Beast:** no morale check. Large 2×2. Use as a gate-breach spike, not a trash spam unit.

## Soulwright (Act 1 End Boss)

Ritual specialist — less army captain, more shrine horror. Built the soul-trap beneath Ashfall Keep. Speaks like a craftsman of the dead, not a ranting cultist.

**Size / staging:** **Large (2×2) solo.** Lead-in trash stays outside the boss room; the Soulwright fight has no adds.

**Must:** fight the party; run a Vela-grade soul-trap; survive long enough for the false wipe (Bram & Fen); get interrupted by Forn's one shatter-act (Soulwright may die, flee, or collapse — authored).

<!-- ASSUMPTION: Not Vela herself and not a lesser god on the field — intermediary / champion only. -->

### Flow design law

Phase 1 must feel like **exercising control in a difficult situation** (skills Act 1 already taught, at higher complexity). Phase 2 is an **authored anxiety spike**, not a failed DPS check. Phase 3 is story — not a second mastery test.

Do not introduce brand-new combat mechanics in the boss room. Remix: interrupt, focus fire, flanking, Eld utility, space control (Gatebreaker lessons).

### Fight phases

#### Phase 1 — Flow channel (bulk of the fight)

**Clear goal:** Break the Soulwright / interrupt the rite before it completes.

**Immediate feedback (required):**
- Visible **ritual meter** or glowing glyph cycle
- Loud telegraphs every 1–2 rounds
- Player always knows if they are winning the rite race

**Kit (draft — numbers TBD):**

| Move | What it does | Skill it tests |
|------|----------------|----------------|
| **Rite Pulse** | Telegraphed AOE; dodge/position or interrupt | Positioning + interrupt timing |
| **Claim** | Marks one PC; focus-fire or existing cleanse/item answer | Priority target discipline |
| **Settle the Floor** | Tiles become bad ground | Space control learned at the gate |
| Soft pressure | Escalating rite if the party turtles | Punishes boredom / stalling |

**Tuning target:** First clear feels tight; retry feels fair (same threshold, readable tells). Fight stays solvable — no soft-lock patterns.

#### Phase 2 — Anxiety spike (authored, short)

**Trigger (locked): ritual meter fills.** The trap is a rite race, not an HP threshold. Interrupts slow the meter; they do not permanently prevent it. When the meter completes → soul-trap fires. (Exact interrupt-window count N — tune in playtest.)

- **Bram** and **Fen** are caught (false wipe — not deleted from roster)
- Still standing: **player, Arn, Voryn**
- Must **not** read as “you played wrong”
- Frame as **objective danger** (Vela-grade rite was always the plan) — UI and/or one VO line makes that clear
- Party of three remains able to act; no soft-lock
- **0 HP still forces this phase** if the meter somehow never completed (outcome lock) — but normal play reaches Phase 2 via the meter

#### Phase 3 — Story handoff (not a mastery test)

1. Arn’s stress breaks suppression → **Forn** shatters the trap / immediate threat **once**
2. Bram and Fen return shaken
3. **Arn ↔ player** one private line. The old Drift-colored last-words rule is replaced. The line does not change with Drift.
4. Arn’s soul passes to **Lumen**; **Forn** holds the body
5. Soulwright collapse / flee / death is **authored after** the Arn beat — not a free combat win that skips story

Full beat order: [[game-premise]].

### Outcome lock (anti-cheese / narrative gate)

**Hard rule:** The Act 1 climax outcome is a **quest state machine**, not “boss HP hit 0 → victory screen.” Mods, one-shots, or broken damage cannot skip Arn’s loss.

| Player action | What the game does |
|---------------|--------------------|
| Ritual **meter completes** | Fire Phase 2 (normal path). |
| Soulwright reaches **0 HP before** Phase 2 | **Do not end the encounter.** Treat 0 HP as a **forced gate into Phase 2** (soul-trap). Same Bram/Fen false wipe, same Forn shatter, same Arn → Lumen beat. Cheese cannot skip the meter path's outcome. |
| Soulwright reaches 0 HP **during** Phase 2 | Ignore lethal as “kill win.” Keep trap sequence running until Phase 3 completes. |
| Soulwright reaches 0 HP **after** Arn beat (Phase 3 done) | Allow authored collapse / corpse / flee — encounter may end. |
| Player tries to leave / soft-lock | Encounter bounds + quest flags block progress until climax flags are set. |

**Implementation intent (Unity / Quest Machine):**
- Flags e.g. `Soulwright_TrapFired`, `Arn_GoodbyeDone`, `Forn_Emerged` gate zone exit and quest completion
- Boss entity: `OnLethalDamage` → if `!TrapFired`, clamp HP to 1 (or 0 with invuln shell), fire trap cutscene/sequence, **do not** call EncounterVictory
- EncounterVictory only after `Arn_GoodbyeDone` (or equivalent)

**Honest limit:** Determined modders can always break a single-player game. This design stops **casual cheese and accidental skips**, and keeps legitimate play on one spine. It is not a DRM fantasy.

**Feedback:** If 0 HP triggers early Phase 2, show the rite completing / trap detonating — never a “Victory” banner before Arn’s goodbye.

### Act 1 teach → Soulwright test

| Taught earlier in slice | Paid off on Soulwright |
|-------------------------|-------------------------|
| Interrupt Binder Acolyte | Interrupt Rite Pulse / ritual casts |
| Focus Chain Sergeant | Focus Claim mark / priority windows |
| Flanking ([[combat-core]]) | Damage windows on Large footprint |
| Eld utility (displace, deny Act) | Real answers, not flavor |
| Gatebreaker space pressure | Settle the Floor |

---

## What This Is Not

- Not a three-biome monster manual
- Not random dungeon ecology
- Not Forn as a controllable combat summon
- Not permadeath via Bound erasure (false wipe only — see [[game-premise]])
