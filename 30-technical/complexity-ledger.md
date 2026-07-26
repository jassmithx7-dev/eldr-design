---
type: system
status: draft
depends_on: []
ue5_scope: S
open_questions: []
---

# Complexity Ledger

*Maintained by the Technical Designer. Every reviewed feature gets an entry. The Producer reads this file.*

*Scale: S = days, M = 1 week, L = 2 weeks, XL = 2+ weeks (requires written justification).*

---

## Ledger

| Feature | Source Note | Unity Scope | Est. Weeks | Signed Off | Notes |
|---|---|---|---|---|---|
| The Anchor (relic prop + climax VFX) | [[relic-the-anchor]] | S | 0.5 | Yes — [[tech-anchor]] | Code is trivial (~half day): two SerializeField references + one event callback added to `SoulwrightBossFightController`. Remaining time is art-dependent: ShaderGraph animated material (inner-light shimmer) and `AnchorShatterVFX` particle system. Both need an art brief before scene integration. No new systems. No paid assets. Mordrek Thread (Act 2 implications) deferred — zero Act 1 implementation cost. |
| Enemy Roster — Ashfall Keep | [[enemy-roster-ashfall]] | L | 2.0 | No — BLOCKED (5 blockers) | 7 `EnemyDataSO` ScriptableObjects + `EnemyAIController` MonoBehaviours are implementable. Blockers: (1) Chain Sergeant aura requires `CombatModifierBus` or proximity scan — not in `combat-core.md`; (2) Ritual meter UI is an unscoped new system (`RitualMeterController` + HUD canvas element); (3) "Interrupt" mechanic is ambiguous — Wait action vs. true mid-turn hook; (4) Large 2×2 flanking geometry undefined in `combat-core.md`; (5) Elevation mechanic undefined. `SoulwrightBossFightController` outcome lock and Drift-colored goodbye (Dialogue System) are implementable once blockers clear. See [[technical-batch-check-01]] in 99-scratch. |
| Zone — The Falling Gate | [[zone-the-falling-gate]] | M | 1.5 | No — BLOCKED (3 blockers) | Note is structurally thin. Blockers: (1) Keep aesthetic open question unresolved — gates art direction and geometry; (2) Inherits elevation system blocker from enemy-roster; (3) Missing scene structure (how many Unity scenes, encounter trigger zones, transition colliders). Cannot begin Unity scene authoring until resolved. 1.5 weeks estimate assumes single scene with 3 encounter areas once blockers clear. |
| Opening Scene Outline | [[opening-scene-outline]] | S | 0.5 | No — BLOCKED (2 design decisions) | Technically low-risk. Maps to Dialogue System conversations + waypoint-mover civilian Prefabs + shrine VFX prop (same category as AnchorShatterVFX). Blocked on: (1) Settlement name — required before any Dialogue System conversation text is authored; (2) Scene structure (battle/retreat/council first) — gates Dialogue System conversation order and tutorial sequencing. Additional flag: civilian crowd scope (authored waypoints vs. NavMeshAgent crowd) must be decided. |
| Quest — The Last Line | [[quest-the-last-line]] | M | 1.0 | No — NEAR PASS (1 dependency) | Quest Machine `QuestAsset` structure is clear: 3 objectives (`HoldTheGate`, `ReachTheShrine`, `ConfrontTheSource`). All completion conditions are defined or derivable from existing flags. Drift-colored goodbye maps to Dialogue System `Conv_ArnGoodbye` with 3 branches on `DriftCounter` Lua condition. Recommendation: model `Soulwright_TrapFired`, `Arn_GoodbyeDone`, `Forn_Emerged` as Quest Machine objective states (serialised free by Pixel Crushers save system). Blocked only by `enemy-roster-ashfall` sign-off (dependency). Minor flag: objective 0→1 transition trigger not specified. |
| Reactions mechanic | [[combat-core]] | M | 1.0 | No — pending Technical Designer sign-off | New `REACTION_WINDOW` state on `TurnManager` FSM. No new resource — draws on existing per-character `bReactionAvailable` bool (React resource). Core tasks: (1) `bInReactionWindow` guard + FSM state branch; (2) `OnReactionWindowPrompt` / `OnReactionResponseReceived` event pair + UI prompt; (3) cast ring ground decal (shader/VFX — shared art brief with any existing decal system); (4) CASTING banner on enemy model + initiative strip portrait; (5) initiative strip highlight for eligible party members. Caster spell-as-Reaction excluded (Phase 2). Depends on Phase 1A action economy FSM being complete. Soulwright encounter tutorial scripting is a separate task in [[encounter-soulwright]], not counted here. |

---

*Running totals (vertical slice):*

| Scope bucket | Count | Est. weeks |
|---|---|---|
| S | 2 | 1.0 |
| M | 3 | 3.5 |
| L | 1 | 2.0 |
| XL | 0 | — |
| **Total** | **6** | **6.5** |

*Note: 4 of the 5 entries above are not yet signed off. Weeks are forward estimates; actual totals will firm once blockers resolve. The combat-core system (already scoped at L, 4–6 weeks in its own note) is not double-counted here — these entries cover content and encounter layers that sit on top of the core loop.*
