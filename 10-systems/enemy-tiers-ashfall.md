---
type: system
status: draft
depends_on: ["[[combat-core]]", "[[enemy-roster-ashfall]]"]
ue5_scope: M
inspired_by: ["challenge-skill-balance", "turn-economy-design"]
open_questions:
  - "Playtest: Settled Levy pack size before gate fights feel like busywork rather than war pressure."
  - "Playtest: Unpassed HP 36 may over-sponge at party level 2. If an average clear takes more than 5 party turns on it alone, drop to 30."
  - "Playtest: Soulwright HP 180 vs the ritual meter. If the party routinely reaches 0 HP before the meter passes about 70, raise HP or lower meter gain."
  - "Binder Acolyte morale: assumed none (Bound-touched). Confirm with Loremaster if a Host body should still flee."
  - "Party stats (HP, armor, attributes per level) depend on the class-progression note, not yet written. The party reference below is a placeholder."
---

# Enemy Tiers — Ashfall Keep (Act 1 Slice)

*Rewritten 2026-10-19 for menu combat ([[combat-core]]): no misses, armor reduces damage, a visible timeline, front and back rows, interrupt skills. Replaces the d20 version (attack bonus, Defense, grid size, terrain).*

**All numbers are first-pass values (TUNE).**

---

## Party Reference (placeholder, level 2)

| Character | Hit with | Damage per hit vs armor 0 | Armor | HP |
|---|---|---|---|---|
| Bram | Longsword 5 + STR 2 | 7 | Heavy + shield: 4 | ~24 |
| Fen | Short sword 4 + DEX 3 | 7 | Light: 1 | ~17 |
| Arn | Longsword 5 + STR 1 | 6 | Medium + shield: 3 | ~22 |
| Voryn | Spells (see [[eld-magic]]) | 5–9 | None: 0 | ~12 |

A Settled Levy (armor 2) takes about 5 per hit, so 4 hits to drop. A pack of four Levies is roughly two rounds of party turns.

---

## Quick Table

| Enemy | Tier | Row | HP | Armor | Damage | Speed | WIS | Morale |
|---|---|---|---|---|---|---|---|---|
| Settled Levy | Trash | Front | 20 | 2 | 5 | Normal | +0 | Yes |
| Cinderbow | Skirmisher | Back | 14 | 1 | 6 (ranged) | Quick | +0 | Yes |
| Chain Sergeant | Elite | Front | 32 | 3 | 7 | Normal | +1 | Only if alone |
| Unpassed | Bound | Front | 36 | 1 | 6 | Slow | — | No |
| Binder Acolyte | Ritualist | Back | 18 | 0 | 3 / casts | Normal | — | No |
| Gatebreaker | Siege, Large | Front only | 55 | 3 | 10 | Heavy | — | No |
| Ash-Hound | Hunter, Large | Front only | 40 | 2 | 8 | Quick | — | No |
| Soulwright | Boss, Large | Front only | 180 | 3 | 9 / rites | Normal | — | No |

**Speed** sets the delay of each enemy's normal action on the timeline: Quick 70, Normal 100, Slow 120, Heavy 140.

**Damage** is the hit before the target's armor. Enemy hits always land.

**Large** enemies stand only in the front row, can't be moved between rows, and fill the frame. They are expensive to model and animate; use them as punctuation.

**Morale:** a humanoid with morale below 25% HP flees on its turn with a 40% chance (TUNE). Fleeing counts as defeated.

---

## 1. Settled Levy — Trash

- Spear and shield. Front row.
- **Decision created:** finish one Levy, or spread damage to push several under 25% so more of them break and flee.

## 2. Cinderbow — Skirmisher

- Short bow from the back row. Quick, so it acts often.
- Prefers the softest target it can see (lowest armor).
- **Decision created:** spend actions reaching the back row (ranged attacks, spells), or tank the chip damage while you clear the front.

## 3. Chain Sergeant — Elite

- **Command aura:** while alive, every Settled Levy deals +1 damage. Ends the instant he falls or flees.
- Flees only if no Levy or Cinderbow is left and he is below 25% HP.
- **Decision created:** kill the sergeant to weaken the whole pack, or clear Levies first and take the extra damage.

## 4. Unpassed — Bound

- Slow, durable, never flees. Hollowed strike.
- First appearance gets a short horror beat (staging, not a mechanic).
- **Decision created:** commit damage into a target that won't break, or deal with the faster threats first and let it lumber.

## 5. Binder Acolyte — Ritualist

Back row. Teaches telegraphs and interrupts before the Soulwright.

| Ability | Telegraphed | Fires | Effect |
|---|---|---|---|
| **Soften** | Yes | Its next turn | One party member's armor −2 for 2 of their turns. |
| **Rite Feed** | Yes | Its next turn | 6 Eld-burn damage, ignores armor. In undercroft fights that share a ritual prop, +2 to the ritual meter. |
| Prod | No | — | 3 damage. |

- **Decision created:** use this turn to interrupt (Break, Exploit, Counterspell, Arn's Shield Bash), or press damage and take the debuff.

## 6. Gatebreaker — Siege (Large)

- Living warbeast. Heavy, slow, hits hard.
- **Breach:** each hit on a front-row character pushes them to the back row. They can step forward again with a minor action. Stand Firm prevents it.
- 0–1 per gate fight.
- **Decision created:** keep your fighters forward (Stand Firm, re-stepping) or accept a reshuffled line.

## 7. Ash-Hound — Hunter (Large)

- Fast. **Leaps:** ignores rows and always attacks the conscious party member with the lowest current HP.
- Optional encounter spice; never in the Soulwright fight.
- **Decision created:** guard the soft target (Bulwark, Arn's Stand Between), or race to kill the hound.

## 8. Soulwright — Boss (Large, solo)

- **HP 180** is the skill channel. **The ritual meter is the clock** ([[enemy-roster-ashfall]]).
- **Outcome lock:** reaching 0 HP before the trap forces Phase 2; it never gives a victory ([[enemy-roster-ashfall]]).

### Ritual meter

| Parameter | Value |
|---|---|
| Meter max | 100 → Phase 2 (the soul-trap fires) |
| Gain per Soulwright turn | +8 |
| Turtle punish | +4 more if no rite was interrupted since its last turn |
| Successful interrupt on a rite | −12 (floor 0) and the rite is pushed back on the timeline |
| Telegraph cadence | A rite every 1–2 of its turns; the first by its second turn |

Under normal play the meter fills in about 8–11 Soulwright turns.

<!-- ASSUMPTION: Under the old rules an interrupt (−12) outpaced gain (+8) and could stall the meter forever. Now that interrupts are skills that cost the actor's turn and Eld, a party that interrupts every rite deals far less damage and burns its Eld pool. Check in playtest that the meter can't be stalled indefinitely; if it can, cap interrupts per rite or lower the interrupt reduction to −8. -->

### Kit

| Move | Telegraphed | Fires | Effect |
|---|---|---|---|
| **Rite Pulse** | Yes | 1 turn after shown | 7 damage to every front-row party member, ignores armor. |
| **Claim** | Yes | Its next turn | Marks one party member for 2 of its turns: the Soulwright's hits on them deal +4. Cleared by Lesser Restoration or an item. |
| **Settle the Floor** | No | Instant | The front row's next actions are delayed +20 (the floor drags at them). |
| Strike | No | — | 9 damage. |

- **Decision created:** spend turns interrupting rites to slow the clock, or deal damage — knowing the meter, not HP, decides when Phase 2 fires.

---

## Tier → Player Choice

| Tier | Enemy | What you choose |
|---|---|---|
| Trash | Settled Levy | Kill one, or break several |
| Skirmisher | Cinderbow | Reach the back row, or take the chip damage |
| Elite | Chain Sergeant | Sergeant first, or trash first |
| Bound | Unpassed | Commit to the sponge, or kite around it |
| Ritualist | Binder Acolyte | Interrupt now, or press damage |
| Siege | Gatebreaker | Hold the line, or accept the reshuffle |
| Hunter | Ash-Hound | Guard the weak, or race it |
| Boss | Soulwright | Slow the clock, or deal damage |

---

## Complexity

| Piece | Estimate | Notes |
|---|---|---|
| Stat blocks on enemy data assets | 2 days | Numbers only |
| Sergeant aura | 0.5 day | Flag check |
| Gatebreaker Breach (row push) | 0.5 day | Row change |
| Ash-Hound leap targeting | 0.5 day | Lowest-HP sort |
| Telegraph + interrupt hooks per enemy | 2 days | Uses the combat-core telegraph system |
| Ritual meter | 2 days | Already scoped under the boss controller |

About 1–1.5 weeks on top of [[combat-core]].
