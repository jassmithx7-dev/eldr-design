---
type: system
status: draft
depends_on: ["[[combat-core]]", "[[enemy-roster-ashfall]]"]
ue5_scope: M
inspired_by: ["challenge-skill-balance"]
open_questions:
  - "Playtest: Settled Levy pack size before gate fights feel like busywork (boredom) rather than war pressure"
  - "Playtest: Chain Sergeant aura radius (3 tiles) vs. isometric readability — tighten to 2 if players miss the link"
  - "Playtest: Unpassed HP 36 may over-sponge at party Level 2; if average clear >5 rounds solo, drop to 30"
  - "Playtest: Ritual N = 6 interrupt windows before meter completion under baseline pacing — confirm Phase 1 length 8–12 rounds"
  - "Playtest: Soulwright HP 180 vs. meter clock — if party routinely 0-HPs him before meter ~70, raise HP or lower meter gain"
  - "Binder Acolyte morale: assumed none (Bound-touched). Confirm with Loremaster if Host body should still check morale"
---

# Enemy Tiers — Ashfall Keep (Act 1 Slice)

*Concrete combat stats for the eight roster enemies in [[enemy-roster-ashfall]]. Resolution uses [[combat-core]]: **1d20 + Attack Bonus vs Defense**.*

<!-- ASSUMPTION: Party is roughly Level 2–3 for the vertical slice; Bram/Fen example stats in combat-core §10. -->

**Baseline anchor:** Ashfall Mercenaries worked example = Settled Levy → Defense 14, HP 20, Attack +2, 1d6+1.

**Party reference (L2, from [[combat-core]] §10):**
- Bram: Defense 18 (heavy), Attack ~+4 (+6 flanked), HP ~23
- Fen: Defense 16 (light), Attack ~+5, HP 17

Hit chance vs Levy Defense 14: Fen ~60%, Bram flanked ~65%. Pack fights stay in the flow channel — readable pressure, not brick walls — then escalate complexity (aura, interrupt, Large footprint) without inventing new resolution rules.

---

## Quick Table

| Enemy | Tier | Size | HP | Def | Atk | Damage | Spd | WIS | Morale |
|-------|------|------|----|-----|-----|--------|-----|-----|--------|
| Settled Levy | Trash | Med | 20 | 14 | +2 | 1d6+1 | 5 | +0 | Yes |
| Cinderbow | Skirmisher | Med | 14 | 13 | +3 | 1d6+2 | 6 | +0 | Yes |
| Chain Sergeant | Elite | Med | 32 | 16 | +4 | 1d8+2 | 5 | +1 | Alone only |
| Unpassed | Bound | Med | 36 | 13 | +2 | 1d8+1 | 3 | — | No |
| Binder Acolyte | Ritualist | Med | 18 | 12 | +1 | 1d4+1 / casts | 5 | — | No |
| Gatebreaker | Siege | Large 2×2 | 55 | 15 | +4 | 2d6+2 | 4 | — | No (beast) |
| Ash-Hound | Hunter | Large 2×2 | 40 | 14 | +5 | 1d8+3 | 7 | — | No |
| Soulwright | Boss | Large 2×2 | 180 | 16 | +5 | 1d10+3 / rites | 4 | — | No |

---

## 1. Settled Levy — Tier: Trash

| Stat | Value |
|------|-------|
| Size | Medium (1×1) |
| HP | 20 |
| Defense | 14 |
| Attack Bonus | +2 |
| Damage | 1d6+1 (spear; avg 4.5) |
| Speed | 5 tiles |
| WIS | +0 (score 10) |
| Morale | Yes — check at ≤5 HP (25% of 20). DC = 12 + party level ([[combat-core]] §9) |

**Special:** Spear reach optional in later polish (attack from 2 tiles). Slice ships as adjacent melee. Shield baked into Defense 14 (not a separate +2 stack).

**Decision created:** Focus-fire one Levy to corpse vs. spread damage to trip multiple morale checks at once.

---

## 2. Cinderbow — Tier: Skirmisher

| Stat | Value |
|------|-------|
| Size | Medium (1×1) |
| HP | 14 |
| Defense | 13 |
| Attack Bonus | +3 |
| Damage | 1d6+2 (short bow; avg 5.5) |
| Speed | 6 tiles |
| WIS | +0 |
| Morale | Yes — check at ≤3 HP (25% of 14, floor 3) |

**Special:** Prefers Short/Long range bands. Attacks into melee (ally adjacent to target) take the normal −2 ([[combat-core]] §3). Elevation is encounter staging, not a flat +to-hit in Phase 1.

**Decision created:** Spend Move/Dash to collapse range on the bow line now, or tank chip damage while finishing melee packs.

---

## 3. Chain Sergeant — Tier: Elite

| Stat | Value |
|------|-------|
| Size | Medium (1×1) |
| HP | 32 |
| Defense | 16 |
| Attack Bonus | +4 |
| Damage | 1d8+2 (longsword; avg 6.5) |
| Speed | 5 tiles |
| WIS | +1 (score 12) |
| Morale | Only if **alone** (no living Settled Levy or Cinderbow in the encounter) **and** ≤8 HP (25% of 32). Otherwise holds. |

**Special — Command Aura:** While the Chain Sergeant is alive, all Settled Levy within **3 tiles** gain **+1 Attack Bonus**. Aura ends instantly on death/route. Does not buff Cinderbows, Bound, or beasts.

**Decision created:** Kill the sergeant to collapse pack accuracy, or clear Levies first and eat the +1 while you do it.

---

## 4. Unpassed — Tier: Bound

| Stat | Value |
|------|-------|
| Size | Medium (1×1) |
| HP | 36 |
| Defense | 13 |
| Attack Bonus | +2 |
| Damage | 1d8+1 (hollowed strike; avg 5.5) |
| Speed | 3 tiles |
| WIS | — (no morale) |
| Morale | No (Bound) |

**Special:** Slow sponge. On its Act, if it moved this turn, it may only attack (no React Dash). Visual soul-horror telegraph on first engagement (staging — not a Reaction Window unless Encounter Designer flags a specific ability `bTelegraphsCast`).

**Decision created:** Commit focus fire through a high-HP target that will not route, or kite/slow-walk it while removing soft threats.

---

## 5. Binder Acolyte — Tier: Ritualist

| Stat | Value |
|------|-------|
| Size | Medium (1×1) |
| HP | 18 |
| Defense | 12 |
| Attack Bonus | +1 (melee fallback) |
| Damage | Melee 1d4+1 (avg 3.5); primary threat is casts |
| Speed | 5 tiles |
| WIS | — |
| Morale | No |

<!-- ASSUMPTION: Binder Acolyte is Bound-touched enough to skip morale checks. If Loremaster rules Host body → morale applies, use WIS +0 and 25% threshold (≤4 HP). -->

**Special — kit (Phase 1 numbers):**

| Ability | Telegraph? | Effect |
|---------|------------|--------|
| **Soften** | Yes (`bTelegraphsCast`) | One party member: **−2 Defense** until end of that target's next turn |
| **Rite Feed** | Yes (`bTelegraphsCast`) | 1d6 Eld-burn damage (avg 3.5) to one party member in Short range; if used in Undercroft lead-in fights that share a ritual prop, **+2** to any active ritual meter (0 if none) |
| Melee prod | No | 1d4+1 |

Teaches the Reaction Window before Soulwright ([[combat-core]] §12).

**Decision created:** Spend React to interrupt Soften/Rite Feed now, or hold React for potions/Dash and accept the debuff.

---

## 6. Gatebreaker — Tier: Siege

| Stat | Value |
|------|-------|
| Size | **Large (2×2)** |
| HP | 55 |
| Defense | 15 |
| Attack Bonus | +4 |
| Damage | 2d6+2 (avg 9) |
| Speed | 4 tiles |
| WIS | — |
| Morale | No (beast) |

**Special:** Occupies 2×2. **Breach:** on a confirmed melee hit against a Medium or smaller target, knock that target **1 tile** directly away (blocked tiles = no knockback, still full damage). Rare: 0–1 per gate encounter.

**Decision created:** Spread formation / leave escape tiles vs. cluster for focus fire and eat knockback into bad ground.

---

## 7. Ash-Hound — Tier: Hunter

| Stat | Value |
|------|-------|
| Size | **Large (2×2)** |
| HP | 40 |
| Defense | 14 |
| Attack Bonus | +5 |
| Damage | 1d8+3 (avg 7.5) |
| Speed | 7 tiles |
| WIS | — |
| Morale | No (beast / Bound-touched) |

**Special:** Occupies 2×2. **Hunt AI:** priority target = conscious party member with lowest current HP; ties favor Unarmored/Light over Heavy. Optional spice — not required every fight; never in Soulwright room.

**Decision created:** Body-block / Bulwark the soft target the hound wants, or leave Fen/casters exposed to delete the hound faster.

---

## 8. Soulwright — Tier: Boss

| Stat | Value |
|------|-------|
| Size | **Large (2×2) solo** (no adds) |
| HP | 180 |
| Defense | 16 |
| Attack Bonus | +5 |
| Damage | Melee 1d10+3 (avg 8.5); rites below |
| Speed | 4 tiles |
| WIS | — |
| Morale | No |

**HP role:** High enough that Phase 1 lasts a real fight (~8–12 rounds of party DPS at L2–3) without routinely racing to 0 HP first. **The ritual meter is the real clock** — HP is the skill channel; the meter is the authored pressure ([[enemy-roster-ashfall]] Phase 1–2).

**Outcome lock:** 0 HP before trap → force Phase 2; does not grant EncounterVictory (roster rule). Stats here do not override that.

### Ritual meter (soft escalate)

| Parameter | Value |
|-----------|-------|
| Meter max | 100 → fire Phase 2 (soul-trap) |
| Base gain | **+8** at end of each Soulwright turn |
| Turtle punish | **+4** additional if **no** party member spent a Reaction in a Soulwright telegraph this round |
| Successful interrupt | Party Reaction that **hits** the Soulwright during a telegraph: **−12** meter (floor 0) |
| Telegraph cadence | Rite Pulse or Claim every **1–2** rounds (guaranteed window by round 2 — [[combat-core]] §12.5) |

Under baseline play (mix of hits and passes), meter completes in roughly **8–11 Soulwright turns**.

### Ritual N

<!-- ASSUMPTION: Ritual N = 6 — design target for telegraphed interrupt windows that open during Phase 1 before the meter completes under baseline pacing. Playtest: if Phase 1 feels short, raise N toward 8 and/or lower base gain to +6; if long/boring, drop N toward 4 and/or raise base gain to +10. -->

**Ritual N = 6** (starting interrupt-window count for slice tuning).

### Boss kit (combat numbers; pedagogy in encounter note)

| Move | Telegraph? | Effect |
|------|------------|--------|
| **Rite Pulse** | Yes | AoE, radius 2 tiles from Soulwright: 2d6 (avg 7) to each party member in area; Reaction Window opens |
| **Claim** | Yes | Mark one PC for 2 rounds: Soulwright attacks against that PC gain **+2** to hit; cleanse = existing item/Eld answers only (no new cleanse system) |
| **Settle the Floor** | No (aura/terrain) | On Act, choose 3 tiles within 4: those tiles become difficult terrain (2 Move per tile) for 2 rounds |
| Melee | No | 1d10+3 |

**Decision created:** Spend React on rite interrupts (slow the meter) vs. hold React for survival tools — knowing the meter, not HP, decides when Phase 2 fires.

---

## Tier → Player Choice Map

| Tier | Enemy | What you choose differently |
|------|-------|-----------------------------|
| Trash | Settled Levy | Kill vs. morale-break packing |
| Skirmisher | Cinderbow | Collapse range vs. eat chip |
| Elite | Chain Sergeant | Sergeant first vs. trash first |
| Bound | Unpassed | Commit sponge vs. kite around it |
| Ritualist | Binder Acolyte | Interrupt now vs. save React |
| Siege | Gatebreaker | Spread for space vs. cluster for DPS |
| Hunter | Ash-Hound | Protect soft targets vs. race the kill |
| Boss | Soulwright | Interrupt the rite clock vs. raw DPS |

---

## Complexity Assessment

**ue5_scope: M** — eight stat blocks + one aura + one knockback + ritual meter config. No new resolution math beyond [[combat-core]].

| Piece | Estimate | Notes |
|-------|----------|-------|
| Stat blocks on existing enemy data assets | 2–3 days | Numbers only |
| Sergeant aura + Levy query | 1 day | Radius check |
| Gatebreaker knockback | 1 day | Grid push |
| Ritual meter controller | 2–3 days | Already scoped under roster/boss tech |
| Hunt AI priority | 0.5 day | Lowest-HP sort |

**Simpler alternative:** Flat HP/Damage only, no aura/knockback/meter escalate. **Rejected for slice** — aura and interrupt are the teach→test spine into Soulwright; cutting them collapses Act 1 into generic trash fights.

**Total for this note's mechanics on top of combat-core:** ~1–1.5 weeks — inside the solo budget if combat-core Phase 1A–1D already exists.
