---
type: encounter
status: draft
depends_on: ["[[zone-the-falling-gate]]", "[[enemy-roster-ashfall]]", "[[enemy-tiers-ashfall]]", "[[combat-core]]", "[[quest-the-last-line]]", "[[opening-scene-outline]]"]
ue5_scope: M
open_questions:
  - "EvacSafeTarget (how many civilians count as 'enough') and spawn cadence — playtest. Do not invent the int."
  - "Civilian lethality — invulnerable waypoint actors vs killable. Zone and this note assume invulnerable stall-on-occupancy."
  - "Gatebreaker breach: authored Wave 3 (this note's assumption) vs fail-state if evac stalls. Do not implement both."
  - "Defeat before Bram joins: all currently active party Downed, or hardcoded five? [[combat-core]] §9 says five; Gate starts with four."
  - "Elevation modifier values — place Cinderbows on Layer 1; no invented +to-hit. [[combat-core]] / [[enemy-tiers-ashfall]] already say Phase 1 elevation is staging."
  - "Levy pack sizes — starting counts below. [[enemy-tiers-ashfall]] already flags playtest if packs feel like busywork."
---

# Hold the Gate

*The vertical-slice combat encounter. Ashfall Keep, Falling Gate. One fight. Diet already named on [[enemy-roster-ashfall]].*

## Tactic (one sentence)

This encounter teaches the player to **hold a choke and split attention** between a priority elite (Chain Sergeant) and a live evac lane — then punishes clustering when the Gatebreaker takes the authored breach.

## Why this fight exists

[[combat-core]] Combat Identity §2: Ashfall should feel like **buying time**, not only kill-all. [[quest-the-last-line]] already locks the hybrid: **wave clear AND evac meter**. This note fills the missing wave / tile / AI / join decisions so a solo Unity implementer can block the grid without inventing a second encounter.

Soulwright stays thicker on [[enemy-roster-ashfall]]. Do not duplicate it here. Do not add Unpassed, Binder Acolyte, or Ash-Hound to this fight.

---

## Arena

**Grid:** square, 1.5 m / tile ([[combat-core]] §3).
**Footprint:** 20×24 tiles. Origin, bands, cover, choke, stair, shrine, and postern: [[zone-the-falling-gate]] § Gate space — tile plan.
**Orientation:** north = blighted approach (enemy spawn). South = evac apron / Varnstead staging (camera-near).
**Camera:** fixed 3/4, south-west looking north-east. If a prop hides a unit from that view, cut the prop.

**`EncounterTrigger`:** `encounterId = HoldTheGate`. Bounds = full 20×24. `lockCameraOnStart = true` (no rail — lock the existing 3/4).

**CombatGrid layers:**

| Layer | Use |
|-------|-----|
| 0 | Apron, courtyard, gate line, approach, west gatehouse |
| 1 | East wall walk `(17–18, 8–18)` |

Stair `(17–18, 6–8)` is the only Layer 0↔1 connection.

<!-- ASSUMPTION: 20×24 is a starting block-out. Playtest may shrink the approach band (y=19–23) if the first walk-in feels like empty parking lot. Do not grow the grid this pass. -->

---

## Starting roster (player)

| Slot | Active at combat start? |
|------|-------------------------|
| Protagonist | Yes |
| [[companion-arn]] | Yes |
| [[companion-fen]] | Yes |
| [[companion-voryn]] | Yes |
| [[companion-bram]] | **No** — mid-fight join |
| Dag | Never (camp NPC) |

**Start tiles (Layer 0), facing north:**

| Who | Tile |
|-----|------|
| Arn | `(8,8)` — toward the choke. He is the body on the line. |
| Protagonist | `(10,8)` |
| Fen | `(8,6)` |
| Voryn | `(10,6)` |

Formation is two-wide so flanking later is a choice, not a spawn gift.

---

## Enemy diet (already named)

Levy + Cinderbow; **one** Chain Sergeant as spike; **one** Gatebreaker if the wall "breaks." Stats: [[enemy-tiers-ashfall]]. Do not duplicate HP here.

| # | Name | Count (slice start) | Size | AI role |
|---|------|---------------------|------|---------|
| 1 | Settled Levy | 9 across three waves (4+3+2) | Medium | **Aggressor** — close to nearest conscious party member; prefer occupying choke tiles `(8–11, 16–18)` if empty |
| 2 | Cinderbow | 2 (one per of Waves 1–2) | Medium | **Ranged** — hold Layer 1 wall tiles; do not voluntarily drop to Layer 0; prefer Short/Long; skip Dash into melee unless a party member is adjacent |
| 3 | Chain Sergeant | 1 (Wave 2 only) | Medium | **Support / aggressor** — stay within 3 tiles of ≥1 living Levy (aura); if no Levy left, close on the nearest party member in the courtyard |
| 4 | Gatebreaker | 1 (Wave 3 only) | Large 2×2 | **Siege aggressor** — enter through the authored breach; melee nearest cluster (≥2 party members within 2 tiles of each other), else nearest party member; use Breach knockback ([[enemy-tiers-ashfall]]) to shove toward the **evac apron** (south), not north off the map |

No Binder. No Unpassed. No Ash-Hound. No telegraphed casts in this fight — Reaction Window is taught later (Binder / Soulwright). Do not add a fake telegraph to the Sergeant.

**Morale:** Levy and Cinderbow check per [[combat-core]] §9. Sergeant only if alone. Gatebreaker never (beast). Routed = eliminated for wave-clear.

---

## Waves

**`EnemyWaveDefinition[]` — three waves, sequential.**

<!-- ASSUMPTION: Wave N+1 starts at the beginning of the next round after Wave N is fully eliminated or routed. No wall-clock timer. No overlap spawn. Pressure escalates by composition (sergeant, then Large), not by stacking two waves on the same tiles. Overlap would be a second AI problem the slice does not need. -->

**Wave-clear (half of the hybrid):** Waves 1–3 are all eliminated or routed.

### Wave 1 — Teach the choke

**Spawn when:** `EncounterTrigger` start (after `Conv_AshfallOpening` ends).

| Unit | Tile | Layer | Facing |
|------|------|-------|--------|
| Levy | `(8,21)` | 0 | south |
| Levy | `(9,22)` | 0 | south |
| Levy | `(10,21)` | 0 | south |
| Levy | `(11,22)` | 0 | south |
| Cinderbow | `(18,16)` | 1 | west |

**Job:** player learns the 4-tile mouth and that the wall is a ranged problem. Evac main lane is already live (see Evac). Four-person party. No elite yet.

### Wave 2 — Sergeant spike + Bram

**Spawn when:** Wave 1 cleared.

| Unit | Tile | Layer | Facing |
|------|------|-------|--------|
| Levy | `(8,20)` | 0 | south |
| Levy | `(10,21)` | 0 | south |
| Levy | `(11,20)` | 0 | south |
| Chain Sergeant | `(9,21)` | 0 | south |
| Cinderbow | `(18,12)` | 1 | west |

**Bram join (content-owned timing):** at **Wave 2 start**, same initiative insertion as a mid-combat add ([[combat-core]] §1).

| Who | Spawn tile | Facing |
|-----|------------|--------|
| Bram | `(4,5)` (friendly apron, **not** through the enemy gate) | north |

One reunion bark — [[quest-the-last-line]] stub 0 / [[opening-scene-outline]] beat 4. No lore dump. Then he is controllable.

<!-- ASSUMPTION: Bram joins on Wave 2 start, not on a round timer and not on evac count. The opening only requires "after the fight has started." Wave 2 is the first moment the line needs a fifth body. -->

**Job:** teach **focus the sergeant vs. clear aura-fed Levy** (Veteran's Read + flanking pay here). Second Cinderbow keeps the wall relevant so collapsing onto the sergeant is a real trade.

### Wave 3 — Authored break

**Spawn when:** Wave 2 cleared. **On this wave's start:** disable east-cheek blocker `(12–14, 16–17)` (prop swap / collider off). Do not play a physics collapse.

| Unit | Tiles (2×2 origin = south-west cell) | Layer | Facing |
|------|--------------------------------------|-------|--------|
| Gatebreaker | origin `(12,17)` occupying `(12–13, 17–18)` | 0 | south |
| Levy (handler) | `(8,20)` | 0 | south |
| Levy (handler) | `(10,20)` | 0 | south |

If a Wave 1–2 Cinderbow is still alive (player ignored the wall), it stays. Do not spawn a third bow.

**Job:** pay off space control. 2×2 + knockback toward the apron. Clustering in the choke for focus fire is the punished line. Stand Firm (Bram, if the protagonist is a Fighter) / spreading is the answer. This is the Gate lesson Soulwright later remixes as Settle the Floor — do not invent a new knockback rule.

<!-- ASSUMPTION: Breach is authored Wave 3, always, including when the player is ahead on evac. The world is already losing. A fail-only Gatebreaker would read as "you played wrong" — rejected for this note unless Jason overrides. -->

---

## Evac hybrid (encounter overlay)

Locked: **both** must be true to complete Hold the Gate and open Keep ([[quest-the-last-line]]):

1. **Gate wave clear** — Waves 1–3 eliminated / routed.
2. **Evac meter full** — `EvacSafeCount >= EvacSafeTarget`.

### What the implementer can wire without a target int

| Piece | Spec |
|-------|------|
| Actors | `CivilianEvacWaypoint` movers. **Not** `CombatantController`. No initiative. No HP. |
| Main lane | Always open. Path: `(3,0)` → `(4,3)` → `(5,5)` → sink `(2,1)`. |
| Postern lane | Closed until `Interact_PosternBar` `(2,7)` succeeds (Act). Path: `(0,9)` → `(1,7)` → `(2,4)` → sink `(2,1)`. |
| Stall | Living **enemy** occupancy on the next lane tile → that civilian pauses. Party occupancy does not stall. |
| Increment | +1 `EvacSafeCount` on sink arrival. Then despawn or idle off-grid. |
| HUD | Existing quest objective / counter. **No second fight-wide meter.** Momentum Track is out ([[combat-core]] §2). |
| Target | `EvacSafeTarget` is a serialized int. **Unset in this note.** |

<!-- ASSUMPTION (smallest wiring so block-out can run): spawn **one** civilian on the main lane at combat start, and **one** additional main-lane civilian at the start of each new combat round, until `EvacSafeCount + in-flight civilians == EvacSafeTarget`. Postern lane, once open, takes the next spawned civilian instead of main (faster sink — reward for the Act). The target int itself is still a human/playtest call. If that cadence fights the hybrid, retune the int or the cadence — do not add civilian death to "fix" it. -->

**Postern is the non-combat solution** for evac pressure. It does not skip waves. It does not skip the shrine landing.

**Soft-fail (already locked):** waves without evac = held ground, people still outside. Evac without wave clear = no combat proof. Quest does not advance. Keep portal stays shut.

---

## Win / loss

| Result | When | What happens |
|--------|------|----------------|
| **Encounter victory** | Waves 1–3 clear **and** `EvacSafeCount >= EvacSafeTarget` | `EncounterTrigger.onEncounterEnd` victory. Quest objective `HoldTheGate` complete. `ReachTheShrine` can activate. Keep portal still waits on shrine volume (zone). |
| **Still in combat** | One half of the hybrid is true, the other is not | Stay in `TurnManager` combat (if enemies remain) **or** remain in the locked grid with evac still running (if waves are done but the meter is not). Do not show Victory. Do not open Keep. |
| **Defeat** | All **currently active** party members Downed or out for the encounter | Last rest ([[combat-core]] §9). No permadeath. No civilian-wipe defeat. |

<!-- ASSUMPTION: Defeat checks the active roster (4 before Bram, 5 after), not a hardcoded five-body test. Combat-core's "all five" is the full-party rule; Gate start is a four-body exception until the join. Systems/Technical must confirm — logged in open_questions. -->

---

## Iso readability (encounter-specific)

- Cinderbows stand on **camera-right** Layer 1. Their silhouettes must clear the merlons.
- Gatebreaker 2×2 must be **fully visible** in the breach — no half-clip through the east tower.
- Evac civilians travel the **near-left** apron so the meter has a visible cause, not a hidden off-screen increment.
- Sergeant aura (3 tiles) should use a **ground decal**, not a tall column, or 3/4 will hide courtyard units behind the VFX.
- Initiative strip is already [[combat-core]] §1. Do not add a second timeline UI.

**Will not read from 3/4 (do not build):** closed gatehouse roof; full-height crenellation; hanging Keep banners on Path B; particle wall on the approach; civilian column marching through the camera-near tall cart.

---

## Terrain features (encounter use)

| Feature | Tiles | Combat use |
|---------|-------|------------|
| Waist-high barricades | zone list | Soft cover **read**; no invented cover bonus until terrain-tag numbers exist. They still block the *look* of an empty parking lot and suggest hold points. |
| Difficult rubble | zone list | 2 Move / tile (already in combat-core). Slows Levy into the choke; slows party collapse onto the wall stair. |
| Choke mouth | `(8–11, 16–18)` | Where Levy want to stand. Flanking is awkward on purpose. |
| East wall + stair | zone | Cinderbow nest; Fen / a Dasher can collapse range. |
| Authored breach | `(12–14, 16–17)` | Wave 3 only. Large entry. |
| Postern bar | `(2,7)` | Act Interact. Second evac lane. |
| Burning wagon | `(15,10)` | Visual only. **No hazard damage.** |
| Shrine volume | `(1–4, 11–14)` | Not a combat interact. EldSense is a **post-hold shared landing** requirement to leave for Keep (zone). Entering during combat is allowed and still sets the flag. |

<!-- ASSUMPTION: Barricades do not grant a Defense bonus until Systems writes the cover/elevated/choke numbers. They are occupancy + read. Standing behind one does not invent +2 Defense. -->

---

## Bram join (implementation hook)

Owned here so Technical does not guess the beat:

1. Wave 2 start.
2. `PartyController.ActivateMember(PC_Bram)` at `(4,5)`.
3. `TurnManager` inserts Bram on the next safe initiative seat (already in combat-core: adds update the track).
4. Set `BramJoined` if a quest/save flag is needed.
5. One short bark; then player control.

Not an Ironhold recruit flow. Not session-start.

---

## Opening beats this fight must not steal

- World-already-losing, tired captain, Arn practical — `Conv_AshfallOpening` **before** Wave 1 ([[opening-scene-outline]] 1–3).
- Fen EldSense — shrine volume, pose + instinct bark + portrait pulse. No Eld lecture. No Arn hint. First of two Ashfall uses.
- No divine drip. No Anchor interact. No second zone.

Voryn may argue the board on postern vs. hold-the-mouth (quest stub 3). **Loremaster owns the line.** This note only makes both options real on the grid.

---

## Teach → later test (do not expand the kit)

| Taught here | Paid later |
|-------------|------------|
| Focus Chain Sergeant vs. trash | Focus Claim / priority windows (Soulwright) |
| Flanking in a bad choke | Damage windows on Large footprint |
| Leave space / eat knockback | Settle the Floor |
| Evac + kill (split attention) | Buying-time identity, not a second meter |

Interrupt / Reaction Window is **not** taught here. First telegraphed cast is Binder Acolyte (keep / undercroft approach), then Soulwright.

---

## What a Unity implementer can do tomorrow

- Block 20×24, Layer 0/1, stair, waist-high props, choke colliders.
- Place `EncounterTrigger` + three `EnemyWaveDefinition`s with the spawn tables above.
- Hook Wave 3 masonry disable.
- Hook Bram at Wave 2 start.
- Hook postern Interact → enable second waypoint path.
- Hook evac increment on sink; expose `EvacSafeTarget` as an inspector int.
- Victory gate = waves done **and** counter ≥ target.

## What they cannot do without a human call

- Set the **real** `EvacSafeTarget` / spawn cadence as design truth (inspector stub only).
- Apply elevation or hazard **numbers**.
- Kill civilians (not approved).
- Treat Wave 3 as a fail-state (not approved).
- Hardcode defeat to five bodies at session start (conflicts with four-person start — needs Systems/Technical confirm).
- Build Through-the-Keep or Soulwright arenas from this note (not in scope).
