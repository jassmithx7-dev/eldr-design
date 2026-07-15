---
type: canon
status: canon-locked
depends_on: []
ue5_scope: S
open_questions: []
---

# Engine Decision: Unity

**Engine: Unity (C#)**

This is a settled human decision. It is canon-locked without a draft phase.

---

## Rationale

This is a walkable, turn-based, writing-driven party CRPG in the Baldur's Gate lineage — a less massive BG2. A party CRPG is approximately 80% systems: branching reactive dialogue, quest state, inventory, party management, and save/load that captures all of it.

Unity has a mature, genre-proven CRPG systems ecosystem that Godot and UE5 do not match for this specific genre. The Pixel Crushers Dialogue System + Quest Machine stack has shipped acclaimed writing-driven RPGs (Disco Elysium, Citizen Sleeper, Suzerain, Lake, and others). These tools exist, are maintained, and are designed for exactly this problem.

Environment assets (towns, dungeons, props) are available for any engine via asset packs and AI generation, so environment tooling was not a deciding factor. Systems tooling was.

UE5's strengths — high-fidelity rendering, GAS, C++ — are mismatched to a text-and-tactics game and carry a complexity tax this project does not want to pay.

---

## Assumed Stack

- **Language:** C#
- **Data layer:** ScriptableObjects (stats, items, abilities, classes, factions)
- **Dialogue and conversation:** Pixel Crushers Dialogue System for Unity
- **Quest state:** Pixel Crushers Quest Machine
- **Save/load:** Dialogue System's built-in save/load (covers world state, quest state, party state)
- **Combat:** Turn-based, implemented in C# — not a real-time ability system

---

## Known Tradeoff Accepted

Unity uses binary scene and prefab formats that do not diff or merge cleanly in git. Design content stays in this text vault. Game project files will be a separate binary-tracked concern. This is accepted and will not be relitigated.
