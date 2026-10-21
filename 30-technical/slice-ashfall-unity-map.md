---
type: system
status: draft
depends_on:
  - "[[zone-the-falling-gate]]"
  - "[[quest-the-last-line]]"
  - "[[enemy-roster-ashfall]]"
  - "[[combat-core]]"
  - "[[relic-the-anchor]]"
  - "[[companion-arn]]"
  - "[[companion-fen]]"
  - "[[opening-scene-outline]]"
  - "[[game-premise]]"
  - "[[engine]]"
  - "[[tech-anchor]]"
  - "[[enemy-tiers-ashfall]]"
ue5_scope: L
open_questions:
  - "Elevation modifier — combat-core must specify the mechanical value before CombatGrid.GetElevationModifier is wired. Zone geometry can still place height layers."
  - "Evac meter target count / civilian spawn rate — tune in playtest; Quest Machine counter name `EvacSafeCount` vs `EvacSafeTarget`."
---

# Technical Map — Ashfall Vertical Slice

*Unity + Pixel Crushers mapping for Ashfall Keep / The Falling Gate / The Last Line / Soulwright / Arn goodbye / The Anchor.*
*Answers the zone open question on scene structure (this note only — `20-content/` untouched).*

---

## Scene approach (zone open question — answered)

**Decision: additive multi-scene regions.** **Human-confirmed 2026-07-26** (do not merge Gate+Keep without a new decision).

| Scene | Role |
|-------|------|
| `Bootstrap_Persistent` | Always loaded. Managers (`TurnManager`, Quest Machine / Dialogue System GameObjects, save system, audio listeners), `PartyRoot`, camera rig, HUD canvases. Never unloaded mid-slice. |
| `Ashfall_Gate` (additive) | Outer gatehouse, walls, civilian evacuation staging, Hold the Gate encounters. |
| `Ashfall_Keep` (additive) | Interior routes, streets, keep approaches, Reach the Shrine traversal fights. |
| `Ashfall_Undercroft` (additive) | Shrine / Anchor prop, lead-in trash outside boss room, Soulwright boss room. |

**Region transitions:** `RegionTransitionTrigger` (BoxCollider, `isTrigger`) on each portal. On enter → unload previous additive region (optional async) → load next → teleport `PartyRoot` to named `SpawnPoint_*`. Quest Machine conditions may gate transitions (e.g. no Undercroft exit until climax flags — see Outcome Lock).

**EncounterTriggers** live as child objects inside the region scene that owns the fight space — not in Bootstrap.

<!-- ASSUMPTION: One bootstrap + three additive region scenes is the slice default. If solo art budget forces a merge, collapse Gate+Keep into one additive scene first; keep Undercroft separate so the climax can unload siege geometry. Logged in open_questions. -->

**Why not one mega-scene:** Undercroft climax + outcome lock + save mid-quest are cleaner with a region id; Gate siege art does not need to stay resident during the boss. Bootstrap keeps Pixel Crushers + party across loads.

---

## Prefabs + components

### Party

**`PartyRoot` Prefab** (persists in Bootstrap)
- `PartyController` (C#) — roster order, active formation, join/activate API
- Child slots: `PC_Protagonist`, `PC_Arn`, `PC_Fen`, `PC_Voryn`, `PC_Bram`
- **Session start (active):** Protagonist, Arn, Fen, Voryn. **Dag = camp NPC only** — not a `PartyRoot` combat slot.
- **`PC_Bram`:** slot may exist on `PartyRoot` but **inactive / not spawned** at session start. Bram is **not** on the starting active roster. He joins mid-fight during the opening Falling Gate encounter (reunion, ~10 years known — not stranger recruit). Activate via join trigger (below).
- Each **active** party member child:
  - `CombatantController` — HP runtime, Act/React/Move flags, `bReactionAvailable`, Downed/Stabilization
  - `CharacterDefinition` ref (ScriptableObject) — class, attributes (no HP invented here)
  - `Animator` + isometric facing helper
  - Capsule/Box collider for selection + grid occupancy proxy
  - Dialogue System `BarkOnIdle` optional (out of slice scope unless needed)

#### Bram Gate join (mid-fight)

**Locked:** Bram joins during the opening Hold-the-Gate / Falling Gate encounter — not at bootstrap, not as a frame-zero party member.

**Smallest hook (pick one owner; do not invent a parallel join system):**
1. Gate `EncounterTrigger` (`encounterId` = Hold / Falling Gate) fires a mid-wave or timed `UnityEvent` / C# callback → `PartyController.ActivateMember(PC_Bram)` (spawn or enable slot) → `TurnManager` inserts Bram onto `CombatGrid` on next safe initiative seat.
2. Optionally gate that callback with a Quest Machine message/objective flag (e.g. `BramJoined`) and/or a short Dialogue System reunion bark/conversation node **during combat** — then same `ActivateMember` call.

<!-- ASSUMPTION: Exact beat timing (which wave / which round) is owned by content ([[zone-the-falling-gate]] / encounter notes). Technical default: EncounterTrigger UnityEvent → PartyController.ActivateMember; QM counter `BramJoined` set for save/journal if needed. Not an Ironhold recruit flow — Ashfall only. -->

#### Fen EldSense UI lock ([[companion-fen]])

**Locked (Ashfall only — these two triggers):**
1. Contaminated gatehouse shrine (opening beat) — first teach.
2. Soulwright rite starting (Phase 1→2).

**Not triggers:** Binder casts in general; Unpassed-first as a required beat.

**Flag (single):** `Fen_EldSense` (bool). Thin CompanionStatus slot — **do not** invent a general companion-status framework; this is one named flag + pose / bark / HUD bind for the slice.

**Display (spider-sense style — body + bark + pulse; NOT mute chip):**
1. **Body language** on `PC_Fen`: stop mid-action → scan → hand to weapon (Animator alert / pose).
2. **Instinct bark** (short, non-explanatory): e.g. `"Wait."` / `"Something's wrong."` via Dialogue System bark or `BarkOnIdle` one-shot — not a conversation tree.
3. **UI:** `PC_Fen` party-portrait pulse while the flag is true.

**Do not use:** mute status chip text such as `Fen — still`, or portrait desaturate-as-silence.

**Wire:**
| Trigger | Setter |
|---------|--------|
| Gatehouse shrine opening beat | Opening beat / zone trigger (same beat that owns the contaminated shrine) → set `Fen_EldSense = true` → play Fen alert pose + instinct bark + portrait pulse |
| Soulwright Phase 1→2 | `SoulwrightBossController` on ritual-meter complete / lethal gate into Phase 2 → set `Fen_EldSense = true` → same pose / bark / pulse |

**Clear:** unset when leaving the wrongness zone / after the beat ends (pose returns; pulse stops).

<!-- ASSUMPTION: Clear = leave shrine trigger volume (opening) or end of Phase-2 start beat / leave Undercroft wrongness volume (rite). Exact clear timing owned by content beat end; technical default is volume-exit or beat-complete UnityEvent → flag false. -->

<!-- ASSUMPTION: Fen alert pose reuses an existing companion alert / stop-scan anim already on the party Animator controller. If a dedicated hand-to-weapon clip must be authored, cost stays S unless art blocks; do not invent a companion-status animation framework. -->

**Hard locks:** No Fen Dialogue System line explaining Eld (barks are instinct only — no lecture). No Arn / Forn divine hint from this tell. Characterization / pose / bark / HUD only — not a combat ability, not a quest objective that names Forn.

**HUD / pose binder:** `CompanionStatusHudBinder` (or Fen portrait pulse on existing party HUD) reads `Fen_EldSense` only; drives portrait pulse + optional Animator trigger on `PC_Fen`. Pure C# + UI + Animator; optional Dialogue System Lua mirror `Variable["Fen_EldSense"]` if bark sequencing needs it — not a conversation condition for Eld lore.

### Encounter

**`EncounterTrigger` Prefab**
- `BoxCollider` (`isTrigger`)
- `EncounterTrigger` (C#) fields:
  - `string encounterId`
  - `EnemyWaveDefinition[] waves` (refs to spawn groups)
  - `CombatGridBounds gridBounds` (or scene `CombatGrid` ref)
  - `bool lockCameraOnStart`
  - `UnityEvent onEncounterStart` / `onEncounterEnd`
- On party enter (once, unless `retriggerable`): loads combatants onto `CombatGrid`, hands control to `TurnManager`

**`EnemyUnit` Prefab** (instanced from roster)
- `CombatantController`
- `EnemyAIController` — priority AI (nearest / focus mark / interrupt targets)
- `EnemyDefinition` SO reference
- `NavProxy` or grid mover (turn-based tile steps — not real-time chase)
- Optional `AuraEmitter` (Chain Sergeant +1 to hit while alive — proximity scan or `CombatModifierBus`)

**`SoulwrightBoss` Prefab** (Undercroft only)
- Extends `EnemyUnit` footprint Large 2×2
- `SoulwrightBossController` (phase machine — see Combat C#)
- `RitualMeterController` (or scene-owned singleton driven by boss)
- No add spawner in boss room (design lock)

### Props (from [[tech-anchor]])

- `AnchorProp` — shrine static mesh; no interact
- `AnchorShatterVFX` — one-shot particles; fired when `Forn_Emerged`

### Region helpers

- `RegionTransitionTrigger` — load/unload additive scenes
- `SpawnPoint_Gate` / `SpawnPoint_Keep` / `SpawnPoint_Undercroft`
- `CivilianEvacWaypoint` Prefabs (opening) — waypoint movers; not combatants

---

## ScriptableObjects

### `EnemyDefinition` : ScriptableObject

One asset per roster row (8). **Do not invent HP / Defense / Attack numbers** — leave numeric fields blank or placeholder-zero until Systems Designer fills them.

| Asset name | Key fields |
|------------|------------|
| `EnemyDef_SettledLevy` | `displayName`, `family` (Host), `size` (Medium), `moraleEnabled` (true), `abilityRefs[]`, `aiProfile`, `prefab`, `hp` / `defense` / `attackBonus` *(TBD)* |
| `EnemyDef_Cinderbow` | as above; `preferredRangeBand` = Short/Long; elevation-prefer AI hint |
| `EnemyDef_ChainSergeant` | `auraToHitBonus` = 1; `auraRadiusTiles`; `moraleOnlyWhenAlone` |
| `EnemyDef_Unpassed` | `moraleEnabled` = false; Bound family |
| `EnemyDef_BinderAcolyte` | ability with `bTelegraphsCast` = true; interrupt priority weight |
| `EnemyDef_Gatebreaker` | `size` = Large2x2; `moraleEnabled` = false (beast) |
| `EnemyDef_AshHound` | Large2x2; optional-encounter flag |
| `EnemyDef_Soulwright` | Large2x2; boss kit ability refs (Rite Pulse, Claim, Settle the Floor); `bIsBoss` |

Shared ability assets: `EnemyAbilityDataSO` with `bTelegraphsCast`, effect refs — owned by combat data, referenced by definitions.

### `RitualMeterConfig` : ScriptableObject

| Field | Purpose |
|-------|---------|
| `interruptWindowsToTrap` (int N) | Successful interrupt windows needed to delay / race — **open_questions** |
| `meterGainPerRound` | Soft pressure if party turtles |
| `interruptMeterDelta` | How much an interrupt slows the meter |
| `uiColor` / `glyphPrefab` | HUD / floor glyph |
| `forcePhase2OnLethal` | bool — outcome lock path when 0 HP before trap |

### Quest-related data

Quest state lives primarily in **Quest Machine** (below). Optional thin SO:

**`QuestSliceBootstrapSO`** (optional)
- `questAsset` → `Quest_TheLastLine`
- `openingConversation` title
- `regionSceneNames[]`

No duplicate quest counters in custom SOs if Quest Machine already owns them.

---

## Quest Machine

**QuestAsset:** `Quest_TheLastLine`

| Node / counter | Purpose |
|----------------|---------|
| Objective `HoldTheGate` | Active at slice start after opening dialogue. **Complete only when BOTH:** (1) Gate encounter victory (`EncounterTrigger` Hold wave cleared) AND (2) `EvacSafeCount >= EvacSafeTarget` (civilian waypoints / QM counter). Human-locked hybrid 2026-07-26 — see [[quest-the-last-line]]. |
| Objective `ReachTheShrine` | Activates on Hold complete. Region transition Gate→Keep unlocks. Complete when party enters Undercroft shrine approach / clears lead-in. |
| Counter / condition `KeepInteriorCleared` (optional sub) | Tracks keep fights if needed for journal text. |
| Objective `ConfrontTheSoulwright` | Active in boss room. **Does not complete on boss 0 HP.** |
| Quest counter `Soulwright_TrapFired` (0/1) | Set when Phase 2 starts (meter complete or lethal gate). |
| Quest counter `Forn_Emerged` (0/1) | Set when Forn shatter beat starts. |
| Quest counter `Arn_GoodbyeDone` (0/1) | Set when `Conv_ArnGoodbye` ends successfully. |
| Success condition | `Arn_GoodbyeDone == 1` (and authored Soulwright collapse). Then allow EncounterVictory + quest success. |

Quest Machine actions wire to C# via Quest Machine's message / Lua / UnityEvent hooks:
- Start encounter by id
- Load additive region
- Set Dialogue System Lua variables mirroring counters for conversation conditions

---

## Dialogue System

| Conversation asset | When | Notes |
|--------------------|------|-------|
| `Conv_AshfallOpening` | Bootstrap / Gate load, before first combat | Opening beats from [[opening-scene-outline]]; speakers from **starting active party** (Protagonist, Arn, Fen, Voryn). **Bram absent** — he is not present from frame zero; reunion join is mid-Gate fight (see Party / Bram Gate join). No divine drip. |
| `Conv_ArnGoodbye` | Phase 3 after Forn shatter + Bram/Fen return | **Three Drift variants** — same structure, different last words. Branch on Lua `Variable["DriftCounter"]` (or equivalent) into Forn-lean / neutral / Vela-lean leaves. Sets `Arn_GoodbyeDone` on conversation end. |
| `Conv_Soulwright_VO` | Boss Phase 1–2 barks | Craftsman-of-the-dead lines; one VO clarifying Phase 2 as objective danger (not player failure). Sequenced Sequence/`ShowAlert` or bark nodes — not a free-roam chat. |
| Optional `Conv_KeepBeat` | Mid-keep | Only if writing needs a short ritual/spiritual reveal; not required for quest machine structure. |

**Lua / conditions (examples):**
- `Variable["DriftCounter"] <= -X` → Forn-lean goodbye
- `Variable["DriftCounter"] >= X` → Vela-lean goodbye
- else → neutral
- Exact Drift thresholds: owned by [[eld-magic]] / social — do not invent here; conversation uses whatever variable combat already writes.

<!-- ASSUMPTION: DriftCounter is already maintained by Eld casting systems as a Dialogue System Lua variable (or synced into one before Conv_ArnGoodbye). If not, SoulwrightBossController syncs it once before starting the conversation. -->

---

## Outcome lock

| Flag | Owner | Meaning |
|------|-------|---------|
| `Soulwright_TrapFired` | Quest Machine counter + `SoulwrightBossController` | Phase 2 has begun |
| `Arn_GoodbyeDone` | Quest Machine + Dialogue System conversation end | Climax talk finished |
| `Forn_Emerged` | Quest Machine + boss controller | Trap shattered; Anchor VFX; body handoff path |

**`OnLethalDamage` behavior** (`SoulwrightBossController`):
1. If `!Soulwright_TrapFired` → clamp HP to 1 (or 0 + invuln shell); **do not** call `EncounterVictory`; force Phase 2 (same as meter complete).
2. If trap fired and Phase 2 running → ignore lethal as kill-win; keep sequence.
3. If `Arn_GoodbyeDone` → allow authored collapse / flee / corpse; then victory.

**EncounterVictory gated:** `TurnManager.EndEncounter(Victory)` only when `Arn_GoodbyeDone` (Quest Machine / C# flag check). Zone exit / soft-lock: `RegionTransitionTrigger` blocked until climax flags set.

UI: never show Victory banner before Arn goodbye. Early 0 HP → rite-complete / trap feedback only.

---

## Turn-based combat C# classes

| Class | Responsibility |
|-------|----------------|
| `TurnManager` | FSM: `IDLE` → `COMBAT_START` → `PLAYER_TURN` / `ENEMY_ACTING` → `REACTION_WINDOW` → … → `ENCOUNTER_END`. Initiative strip; Act/React/Move; **gates victory** on climax flags for Soulwright encounter. Pure C#. |
| `CombatGrid` | Square grid (1.5 m/tile per combat-core), occupancy, Large 2×2 footprints, pathfinding, flanking queries, elevation layer ids (modifier value TBD). Pure C#. |
| `RitualMeterController` | Reads `RitualMeterConfig`; advances meter; applies interrupt deltas; raises `OnRitualMeterComplete` → boss Phase 2. HUD binder. Pure C# + UI. |
| `SoulwrightBossController` | Phase machine: `Phase1_Flow` → `Phase2_Anxiety` → `Phase3_StoryHandoff` → `PostClimax`. Owns outcome lock, lethal clamp, Dialogue System start for `Conv_ArnGoodbye` / VO, Quest Machine counter sets, Anchor shatter callback (`[[tech-anchor]]`), sets `Fen_EldSense` on Phase 1→2 (see Fen EldSense UI lock). Pure C#; hooks Pixel Crushers API for dialogue/quest. |
| `CombatantController` | Per-unit runtime state |
| `EnemyAIController` | Priority AI for non-boss units |
| `EncounterTrigger` | World → combat bridge |
| `RegionTransitionTrigger` | Additive scene flow |

**C# vs data vs Pixel Crushers boundary:**
- **Pure C#:** turn loop, grid, attack math, ritual meter, boss phase machine, outcome lock
- **ScriptableObject-driven:** `EnemyDefinition`, `RitualMeterConfig`, `EnemyAbilityDataSO`, character defs
- **Pixel Crushers API:** conversations, quest objectives/counters, default save/load registration

**No real-time combat assumption.** Ritual meter advances on turn/round boundaries and interrupt windows, not wall-clock DPS.

<!-- ASSUMPTION: Class name `SoulwrightBossController` is canonical. [[tech-anchor]] earlier used `SoulwrightBossFightController` — treat as the same component; rename on implementation. -->

---

## Save / load

**Default:** Dialogue System built-in save/load (+ Quest Machine state via the Pixel Crushers stack).

| What | How |
|------|-----|
| Quest objectives + counters (`Soulwright_TrapFired`, `Arn_GoodbyeDone`, `Forn_Emerged`) | Quest Machine — covered by PC save |
| Dialogue / Drift Lua variables | Dialogue System savers |
| Current additive region + spawn | Custom `RegionStateSaver` : `Saver` — stores `activeRegionSceneName`, spawn id |
| Party composition / positions on grid | `PartyStateSaver` : `Saver` — or Dialogue System persistent data if already used for party; must persist whether `PC_Bram` is active (`BramJoined`) so mid-slice loads do not drop him back to inactive; persist `Fen_EldSense` if save can occur while the tell is active |
| Combat mid-fight | **Out of scope for slice v1** — do not offer save during active `TurnManager` combat; force save at rest / region transition / pre-boss door |
| Anchor prop | No saver (destroyed at climax; scene default absent post-flag) |

Reconstruct at load: load Bootstrap → apply Quest/Dialogue state → load additive region from saver → place party at spawn → do **not** resume mid-turn combat.

---

## Paid assets assumed

| Asset | Status |
|-------|--------|
| Pixel Crushers **Dialogue System for Unity** | Assumed |
| Pixel Crushers **Quest Machine** | Assumed |
| Other paid packs | **None required** for this map |

Flag later if grid pathfinding or isometric camera packs are purchased — not required to implement the structures above.

---

## Complexity

`ue5_scope: L` (~2 weeks for this *mapping layer*: scenes, triggers, QM/DS wiring, boss controller + outcome lock, SO stubs). Does **not** include full [[combat-core]] Phase 1A–1D (tracked separately in [[complexity-ledger]]).

---

## Sign-off status

This note is **`draft`**. It is the technical map for the slice; promotion of content notes to `reviewed` still requires explicit `tech_signoff` links after blockers in open_questions clear (elevation modifier; evac tune values).
