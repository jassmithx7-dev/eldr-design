---
type: system
status: draft
depends_on: ["[[relic-the-anchor]]", "[[quest-the-last-line]]", "[[enemy-roster-ashfall]]", "[[game-premise]]"]
ue5_scope: S
open_questions:
  - "AnchorProp ShaderGraph material spec — needs an art brief before Unity scene authoring begins. Inner-light animated effect using scrolling subsurface noise. No blocker."
  - "relic-the-anchor.md type: canon in 20-content/ — schema ambiguity. Loremaster to confirm final home (00-canon/ vs 20-content/) before promotion gate clears."
---

# Technical Note — The Anchor

*Sign-off note for [[relic-the-anchor]] two-gate promotion review.*
*Full scratch analysis: [[technical-anchor-check]]*

---

## Implementability Verdict

**Implementable. Sign-off granted.**

The Anchor is a narrative prop with a single scripted event callback. It requires no new C# systems, no new Pixel Crushers assets, no paid tooling, and no engine-level work. All implementation slots into structures already defined by `enemy-roster-ashfall.md` (Phase 3 authored sequence) and the existing save/load architecture.

Estimated implementation: **2–4 days** (art-dependent). Code work is less than half a day.

---

## Unity Structure Mapping

### Prefabs

**`AnchorProp` Prefab**
- `GameObject`: static scene object placed in the Ashfall Keep shrine (undercroft)
- `MeshRenderer`: custom dark sphere mesh (artist-authored; not a Unity primitive)
- `Material`: ShaderGraph animated material — scrolling subsurface noise that suggests interior movement without resolving to a shape; emission intensity low; no specular highlights (the note specifies "not reflective")
- No `Collider` component — the Anchor is not raycast-targetable
- No `Interactable` component — no UI prompt, no player verb
- No `Rigidbody` — static prop
- Child optional: `AnchorShimmer` (ambient `ParticleSystem`) — extremely subtle, low-emission; adds presence without drawing player attention to the prop as a gameplay object

**`AnchorShatterVFX` Prefab**
- `ParticleSystem`: burst mode, one-shot, sphere fragments + energy dissipation; duration ~2 seconds, no loop
- `AudioSource`: single audio clip (shatter + dissipation tone), play on awake, no loop
- Self-destructs via `ParticleSystemStopAction.Destroy` after clip completes
- This Prefab is **pre-placed in the shrine scene** as inactive, or **instantiated** at the AnchorProp's world position when triggered — either approach works; pre-placement is simpler for a single-scene shrine

### C# Classes

**`SoulwrightBossFightController` (MonoBehaviour)**
This class is already scoped under `enemy-roster-ashfall.md` as the turn-based phase manager for the Act 1 boss. It owns the outcome lock state machine (`Soulwright_TrapFired`, `Arn_GoodbyeDone`, `Forn_Emerged`).

Anchor-specific additions to this class:
```
[SerializeField] private GameObject anchorProp;
[SerializeField] private GameObject anchorShatterVFX;

// Called when Forn_Emerged flag sets (Phase 3 start)
private void OnFornEmerged()
{
    if (anchorProp != null) anchorProp.SetActive(false);
    if (anchorShatterVFX != null) anchorShatterVFX.SetActive(true); // or Instantiate
}
```

This is a two-line addition to an existing class. The Anchor has no independent controller.

### ScriptableObjects

**None.** The Anchor has no game data — no stats, no item definition, no ability, no faction relationship. It is a prop and a VFX trigger. A ScriptableObject would add complexity with no benefit.

### Pixel Crushers Integration

**None direct.** The Anchor's shattering is triggered downstream of the Phase 3 authored sequence, which is driven by the `SoulwrightBossFightController` state machine. That state machine may surface signals to Pixel Crushers Dialogue System (to begin the Arn farewell conversation) and Quest Machine (to set `Forn_Emerged`), but the Anchor itself has no Dialogue System conversation and no Quest Machine objective. It is a visual callback to a state change owned elsewhere.

### Save/Load

**Nothing to register.** The Anchor is destroyed at the climax and the shrine is not revisited within the slice. No `Saver` component is needed on the AnchorProp. If the undercroft scene is ever re-entered post-climax (out-of-scope for Act 1), the AnchorProp would simply be absent by default (inactive/despawned state serialized in scene state — standard Unity scene management).

---

## Flags Carried Forward

1. **Art brief required before scene integration.** The ShaderGraph material ("something shifts inside when it catches light but never resolves") and the `AnchorShatterVFX` particle system both need explicit art direction. Implementation is blocked on these assets, not on code.

2. **Frontmatter type ambiguity in source note.** `relic-the-anchor.md` is `type: canon` in `20-content/`. This is a schema concern for the Loremaster / Continuity Editor, not a technical blocker.

3. **Mordrek Thread is deferred.** The shrine's role as evidence for Act 2 (Mordrek's stolen souls) requires no Act 1 code. No flag, no saver, no Quest Machine objective needed in the slice. This is a reminder for Act 2 design intake.

4. **No real-time combat assumption present.** The Anchor's climax moment is a scripted authored callback within the turn-based Phase 3 sequence. Turn-based integrity confirmed.

---

## Complexity Ledger Entry

See `[[complexity-ledger]]` — entry: `relic-the-anchor`, scope S, 2–4 days.
