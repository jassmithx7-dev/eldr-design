---
type: system
status: draft
depends_on:
  - "[[slice-ashfall-unity-map]]"
  - "[[combat-core]]"
  - "[[zone-the-falling-gate]]"
  - "[[quest-the-last-line]]"
  - "[[enemy-roster-ashfall]]"
  - "[[tech-anchor]]"
ue5_scope: S
open_questions: []
---

# Complexity Ledger

*Maintained by the Technical Designer. Every reviewed feature gets an entry. The Producer reads this file.*

*Scale: S = days, M = ~1 week, L = ~2 weeks, XL = 2+ weeks (requires written justification in the technical note).*

*Slice map: [[slice-ashfall-unity-map]].*

---

## Ledger

| Feature | Source Note | Unity Scope | Est. Weeks | Signed Off | Notes |
|---|---|---|---|---|---|
| Combat core slice | [[combat-core]] | L | 4–6 | No | Phase 1A–1D: `TurnManager`, `CombatGrid`, action economy, attack/HP/Downed, flanking, Veteran's Read, morale, Eld pool, basic AI, `REACTION_WINDOW`. XL-by-weeks justified in combat-core §11 (phased path). Vertical-slice playable skeleton; no invented enemy HP here. |
| Ashfall zone | [[zone-the-falling-gate]] · [[slice-ashfall-unity-map]] | M | 1.5 | No | Bootstrap + 3 additive regions (`Ashfall_Gate` / `_Keep` / `_Undercroft`), `EncounterTrigger`s, `RegionTransitionTrigger`s. Blocked on elevation modifier values + art direction; scene structure answered in tech map. |
| Last Line quest + dialogue | [[quest-the-last-line]] · [[opening-scene-outline]] | M | 1.0 | No | Quest Machine `Quest_TheLastLine` (Hold → Shrine → Confront + climax counters). DS: `Conv_AshfallOpening`, `Conv_ArnGoodbye` (3 Drift branches), `Conv_Soulwright_VO`. Hold→Shrine: hybrid (wave clear AND `EvacSafeCount`) locked. |
| Soulwright boss + outcome lock | [[enemy-roster-ashfall]] · [[game-premise]] | L | 2.0 | No | `SoulwrightBossController` phase machine, `RitualMeterController` + `RitualMeterConfig`, lethal clamp, flags `Soulwright_TrapFired` / `Forn_Emerged` / `Arn_GoodbyeDone`, EncounterVictory gated. Ritual N open. Depends on combat core + Reactions. |
| Enemy SO set | [[enemy-roster-ashfall]] | M | 1.0 | No | Eight `EnemyDefinition` assets + shared `EnemyAbilityDataSO` refs; `EnemyUnit` prefab variants. Stats fields empty until Systems Designer fills — no invented HP. Chain Sergeant aura + Large 2×2 flanking need combat-core wiring. |

### Also tracked (prior sign-offs / adjacent)

| Feature | Source Note | Unity Scope | Est. Weeks | Signed Off | Notes |
|---|---|---|---|---|---|
| The Anchor (prop + climax VFX) | [[relic-the-anchor]] | S | 0.5 | Yes — [[tech-anchor]] | Two SerializeFields + callback on boss controller; art-dependent ShaderGraph + `AnchorShatterVFX`. |
| Reactions mechanic | [[combat-core]] §12 | M | 1.0 | No | Counted inside combat-core Phase 1D above; row kept so Producer can see the FSM slice separately. |
| Fen EldSense HUD / pose / bark | [[companion-fen]] · [[slice-ashfall-unity-map]] | S | 0.25 | No | Flag `Fen_EldSense` + alert pose (stop/scan/hand-to-weapon) + instinct bark + portrait pulse; two Ashfall setters (shrine open + Soulwright P1→2). No mute chip; no Eld lecture. Pose cost assumes reuse of existing alert anim — see tech-map ASSUMPTION. Not a full companion-status system. |

---

## Running totals (vertical slice — primary five)

| Scope bucket | Count | Est. weeks (mid) |
|---|---|---|
| S | 0 | — |
| M | 3 | 3.5 |
| L | 2 | 6.5 (combat uses 5 mid of 4–6) |
| XL | 0* | — |
| **Primary five** | **5** | **~10** |

\*Combat core is scoped L in frontmatter but estimates 4–6 weeks; justification lives in [[combat-core]] §11. Do not double-count Reactions or Anchor into the primary five total.

*Anchor (+0.5) and Fen EldSense HUD/pose/bark (+0.25) sit outside the primary five. Weeks firm when open_questions on [[slice-ashfall-unity-map]] close.*
