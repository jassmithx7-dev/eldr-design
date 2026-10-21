---
type: zone
status: draft
depends_on: ["[[game-premise]]", "[[enemy-roster-ashfall]]", "[[combat-core]]", "[[opening-scene-outline]]", "[[quest-the-last-line]]"]
ue5_scope: M
open_questions:
  - "Elevation tag modifier values (to-hit / Defense / movement) — [[combat-core]] still TBD. This note places height layers only; do not invent a bonus."
  - "EvacSafeTarget count and civilian spawn cadence — playtest ints. Do not invent the target. Quest Machine names already exist as a technical proposal; tune values are a human/Systems call."
  - "Can evac civilians be killed / downed, or are they invulnerable waypoint actors? Not decided. This note assumes invulnerable stall-on-occupancy (see ASSUMPTION below)."
  - "Hold-the-Gate defeat before Bram joins: all currently active party Downed, or a hardcoded five-body check? [[combat-core]] §9 says five. Gate starts with four."
  - "Hazard tag numbers (burning wreckage, etc.) — [[combat-core]] TBD. Visual fire only until Systems writes values."
---

# The Falling Gate

*The first vertical-slice zone — the outer gate of Ashfall Keep. One zone, three spaces. Not a second biome.*

## Overview

The Falling Gate is the outer gate of **Ashfall Keep**, a ruined frontier keep on the edge of the blighted lands — stone walls, collapsed sections, military construction with no pretension to grandeur. Half-ruined, half-defended, and already showing the strain of the war. Vela's forces have pushed close enough that this gate is now the last line of defense between the living settlements and the advancing darkness.

**Working presentation:** 3D isometric, Unity (C#), **fixed 3/4 camera**. Every volume below is authored so units, cover, and the evac lane read from that camera. If a prop hides a combatant from 3/4, cut the prop — do not invent a camera rail.

<!-- ASSUMPTION: Camera sits south-west of the courtyard, looking north-east into the gate mouth. Grid north = blighted approach. This matches a standard 3/4 read (near = evac / Varnstead staging; far = enemy field). Exact yaw/pitch numbers are a Technical/art call — do not lock a 16-bit pivot. -->

## Purpose in the Story

This zone is where the player first experiences the scale of the Line's exhaustion. The settlement is not glamorous; it is battered, frightened, and running out of time. The player must keep the gate standing long enough for civilians to evacuate and for the party to reach the old shrine beneath the keep.

## Spaces (one zone)

Three spaces, one keep. Do not add a forest, a second keep, or a second quest hub.

| Space | Job | Combat |
|-------|-----|--------|
| **Gate** | Opening retreat, [[encounter-hold-the-gate]], evac hybrid, Fen's first EldSense, Bram join | Authored Hold the Gate (this slice's combat encounter to thicken) |
| **Keep** | Reach the Shrine traversal | Diet already named in [[enemy-roster-ashfall]] ("Through the Keep"). **No new encounter note this pass** — paths only. |
| **Undercroft** | Shrine / [[relic-the-anchor]] evidence, Soulwright | Soulwright kit already lives on [[enemy-roster-ashfall]]. Do not rewrite it here. |

<!-- ASSUMPTION: These three spaces are regions of Ashfall Keep, not three zones. Scene packaging (additive vs merge) is Technical's problem; this note only locks spatial adjacency and what the player can see/do. -->

---

## Iso camera law (zone-wide)

1. **No closed roofs** over fight floors or the evac apron. Ruined — sky visible. A roof is a 3/4 occluder.
2. **Waist-high cover only** on camera-near tiles (≤ roughly a human waist). Tall crates on the near edge hide the party.
3. **Mass on camera-left (west):** the gatehouse block. **Open read on camera-right (east):** wall walk + Cinderbows silhouetted against sky/smoke.
4. **Merlons / crenels stay low** on the east wall. Full-height teeth hide elevated archers from 3/4.
5. **Gatehouse shrine** is open on the south (camera-facing) side — missing wall or collapsed vault — so the contaminated chapel reads as a dark recess, not a black box.
6. **Smoke and fire are backdrop**, north of the gate line. They must not be a particle wall through the combat grid.
7. **Large 2×2** (Gatebreaker) needs a visible breach mouth ≥ 3 tiles wide after Wave 3. Do not spawn a Large into a 2-tile alley — it will read as intersecting masonry from 3/4.

---

## Gate space — tile plan

**Footprint:** 20 tiles east–west × 24 tiles south–north. Square grid, **1.5 m / tile** ([[combat-core]] §3). ~30 m × 36 m.

**Origin:** `(0,0)` = south-west corner (camera-near, Varnstead staging). `+x` = east. `+y` = north (blight / enemy approach).

**Combat grid bounds for Hold the Gate:** the full 20×24. Evac apron and shrine alcove stay in-bounds so Interact and civilian waypoints run during the fight.

### Bands (south → north)

| y | Name | Elevation layer | Tag (identity only — modifiers TBD) |
|---|------|-----------------|-------------------------------------|
| 0–5 | **Evac apron** | 0 | — |
| 6–14 | **Courtyard** | 0 | cover / some **difficult** rubble |
| 15–18 | **Gate line** | 0 | **choke** on the mouth; rubble **difficult** on the cheeks |
| 19–23 | **Approach** | 0 | enemy spawn; smoke backdrop beyond y=23 |
| 8–18, x=16–19 | **East wall walk** | **1** | **elevated** — staging / LOS only until Systems writes a number |
| 6–16, x=0–5 | **West gatehouse** | 0 | shrine alcove + postern Interact |

<!-- ASSUMPTION: Elevation layer 1 is a second floor (~3 m). Stair tiles at the south-east (see below) are the only legal Layer-0 ↔ Layer-1 move. No jump. No fall damage invented. Cinderbow elevation is staging (range/LOS), not a flat +to-hit — already stated on [[enemy-tiers-ashfall]]. -->

### Choke and breach (do not invent destruction)

- **Gate mouth (Waves 1–2):** walkable choke at **x=8–11, y=16–18** (4 tiles wide). Tag: **choke**.
- **Cheeks:** masonry at x=6–7 and x=12–15 on y=16–18. Solid. Not player-destructible.
- **Authored breach (Wave 3):** disable the east cheek blocker on **x=12–14, y=16–17** (prop swap / collider off). Gatebreaker (2×2) enters through that gap. This is the roster's "if the wall breaks" — an authored beat, not a physics system and not a fail-state.

<!-- ASSUMPTION: The wall "breaks" as Wave 3 starts, always, even if the player is winning. The keep is already falling ([[opening-scene-outline]]). A fail-triggered Gatebreaker would punish play that already has a hybrid win; cheaper and truer to "world already losing" is authored pressure. If Jason wants breach-on-fail instead, that is an open human call — do not implement both. -->

### Stair (wall access)

- **SE stair:** tiles `(17–18, 6–8)`, Layer 0 → 1. Two tiles wide so a Medium can pass a Medium. Melee collapse path onto Cinderbows.
- Wall walk walkable tiles: `(17–18, 8–18)` Layer 1.

### Cover and rubble (Layer 0)

Waist-high only. Suggested barricade tiles (crates / cart beds / torn pavise):

`(6,8)`, `(9,9)`, `(12,8)`, `(7,12)`, `(11,12)`, `(14,11)`

**Difficult rubble** (2 Move per tile entered — already in [[combat-core]] §3; not a new tag number):

`(7,15)`, `(12,15)`, `(8,14)`, `(13,7)`

**Hazard:** a burning wagon visual at `(15,10)` — **no mechanical hazard** until Systems writes the hazard modifier. Do not deal fire damage from this note.

### Interactables (Gate)

| Id | Tile | Act | Result |
|----|------|-----|--------|
| `Interact_PosternBar` | `(2,7)` | Interact | Opens **second evac lane** (west postern). Non-combat solution for evac pressure. Does **not** complete Hold the Gate by itself. |
| `Volume_GatehouseShrine` | `(1–4, 11–14)` | Enter (no Interact) | Sets `Fen_EldSense` (first Ashfall teach). Contaminated chapel — residue only. **Not** [[relic-the-anchor]]. No loot. No puzzle. |

The Anchor stays undercroft. Do not place a second sphere here.

### Evac hybrid (spatial only)

Locked by [[quest-the-last-line]]: Hold the Gate completes only when **both** are true — wave clear **and** evac meter full. Either alone does not open the keep.

**Lanes (waypoint actors, not combatants):**

1. **Main lane (always open):** spawn `(3,0)` → `(4,3)` → `(5,5)` → safe sink `(2,1)` (south-west apron / Varnstead staging).
2. **Postern lane (after Interact):** spawn `(0,9)` → `(1,7)` → `(2,4)` → same safe sink `(2,1)`.

**Stall rule:** if a lane tile is occupied by a living enemy, the next civilian on that lane **pauses**. They resume when the tile is empty. Party members do not stall civilians.

<!-- ASSUMPTION: Civilians cannot be killed or downed. Evac is space/time pressure, not a body-count minigame. No civilian HP bar. If Jason wants lethal civilians, that is a new system — log it, do not add it here. -->

<!-- ASSUMPTION: EvacSafeCount increments by 1 when a civilian reaches the safe sink. EvacSafeTarget is an unset playtest int (same counter the hybrid already names). Spawn cadence is unset — do not invent a per-round rate in this note. Encounter note lists the smallest wiring assumption for implementers. -->

**Defeat overlay:** party wipe per [[combat-core]] §9 (return to last rest). Evac stall is **not** a wipe. Failed evac after a wave clear = quest does not advance (hybrid). Do not add a timeout defeat.

### Two Gate reads from 3/4

- **Floor read:** choke in the middle-distance; party in the near courtyard; civilians drifting through the near-left apron.
- **Wall read:** Cinderbows on the far-right walk, heads above the ruined merlons, not behind the gatehouse mass.

---

## Traversal paths (zone requirement)

**At least two distinct paths Keep-ward, after Hold completes:**

| Path | Route | Cost |
|------|-------|------|
| **A — Ground hall** | Shrine landing → east-west barrel vault → north stair-head to Undercroft | Shorter. Diet: Levy remnants + Unpassed (roster). Choke corridors. |
| **B — Mural walk** | Shrine landing → west mural stair → wall passage → same stair-head | Longer. Elevated Layer 1. Fewer bodies, worse 3/4 if you hang banners — **no hanging banners**. |

Both paths share the **shrine landing** (west gatehouse chapel). They split *after* `Volume_GatehouseShrine`. First EldSense is on the shared landing — not missable, not a UI lecture.

**Non-combat solution (required):** `Interact_PosternBar` at the Gate — spend Act, open the second evac lane. A second keep-side non-combat: `Interact_KeepWinch` on Path B's mural stair (jammed windlass). Spending Act opens Path B without a fight. Path A remains the combat default. Neither Interact skips the Soulwright or the hybrid Hold.

<!-- ASSUMPTION: Keep winch is a one-shot Interact, not a skill check and not a social gate. [[design-pillars]] social gates are authored elsewhere. If Loremaster wants Voryn's board-argue (quest stub 3) to *be* the evac-route / which-corridor beat, they own the words — this note only places the Interact. -->

### Keep / Undercroft (path stubs only)

Do not thicken Soulwright here. Do not invent a second combat encounter note this pass.

- **Keep footprint (working):** ~16×20 tiles, interior, two corridors as Path A / Path B above. Narrow. 3/4: no complete vault roofs; broken vaults + light wells.
- **Undercroft:** descent on the shared stair-head. Shrine chamber holds the Anchor **prop** (see canon-locked relic note). Boss room is Large 2×2 solo — leave a ≥6×8 clear floor. Lead-in trash stays **outside** the boss door (roster lock).
- Region exit Gate→Keep: blocked until Hold hybrid completes **and** shrine volume has been entered once.
- Region exit Keep→Undercroft: after Reach the Shrine traversal (quest). Not designed as a new fight here.
- Undercroft exit after climax: Technical / quest flags. Not this note.

---

## Key Features

- A collapsing outer gatehouse with limited defensive positions (choke + east wall + authored Wave 3 breach).
- A chapel or shrine that has become a site of strange power (gatehouse landing — Fen EldSense; **not** the Anchor).
- Narrow interior routes that make the battle feel urgent and spatially constrained (Keep Path A / B).
- A final descent into the old undercroft where the party confronts the first true sign of opposition at the source — Soulwright + Anchor evidence, already authored elsewhere.

## Encounter Intent

The zone should feel like a desperate holding action. The enemies are not just monsters; they are the pressure of a world already being overwritten. Enemy types for this zone: [[enemy-roster-ashfall]].

**Gate combat (the thin one, now specified):** [[encounter-hold-the-gate]] — Levy + Cinderbow; one Chain Sergeant; one Gatebreaker on the authored break. Hybrid win.

**Tactic the Gate teaches (one sentence):** Hold a choke and split attention between a priority elite and a live evac lane; then survive a Large footprint that punishes clustering.

Party start (Gate): protagonist, [[companion-arn]], [[companion-fen]], [[companion-voryn]]. [[companion-bram]] is **not** on the starting roster — he joins mid-Hold (see encounter note). Dag is camp only.

---

## What this note does not decide

- Elevation / hazard **numbers**
- EvacSafeTarget and spawn cadence
- Whether civilians can die
- Whether defeat counts four or five bodies before Bram
- Soulwright arena pedagogy (already thicker on the roster)
- Art pack / texture direction
- A 16-bit or FF camera pivot
