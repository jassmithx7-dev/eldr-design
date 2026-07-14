# Eldr — Coordinator

Eldr is an AI-assisted design system for a solo-developed 3D isometric CRPG in the Baldur's Gate / Icewind Dale lineage, built in Unreal Engine 5. The deliverable is a vertical-slice design package — one zone, one questline, one companion, one combat encounter — that is internally consistent, canon-locked, and specific enough for a solo developer to begin UE5 implementation without further design decisions. **Buildability over volume.**

---

## Coordination Rules

1. **Canon supremacy.** Notes in `00-canon/` marked `canon-locked` are immutable except by explicit human approval. Any agent that needs to violate canon stops and files a canon-change request.
2. **No agent writes outside its owned directory.** Cross-directory needs are filed as requests in `99-scratch/`, not edits.
3. **Two-gate promotion.** `draft` → (Continuity Editor AND Technical Designer both sign off) → `reviewed` → (human approves) → `canon-locked`. Nothing skips a gate.
4. **`99-scratch/` is quarantine.** Content there is never cited as truth by any agent.
5. **Surface open questions; never invent over them.** When an agent lacks a human decision it needs, it logs the question to `open_questions` in the note's frontmatter and proceeds with the smallest possible assumption, flagged inline with `<!-- ASSUMPTION: ... -->`.
6. **Human is the final editor.** Agents propose; the developer disposes.

---

## Frontmatter Schema

Every content note must carry this header verbatim:

```yaml
---
type: quest | zone | companion | system | encounter | canon
status: draft | reviewed | canon-locked
depends_on: []
ue5_scope: S | M | L | XL
open_questions: []
---
```

---

## Agent Routing Table

| Directory       | Owner(s)                                      |
|-----------------|-----------------------------------------------|
| `00-canon/`     | Loremaster (write while draft); **locked to all agents once canon-locked** |
| `10-systems/`   | Systems Designer                              |
| `20-content/`   | Loremaster (narrative), Encounter Designer (zones + encounters) |
| `30-technical/` | Technical Designer                            |
| `99-scratch/`   | Any agent (staging only; never cited as truth) |
| Audit outputs   | Continuity Editor writes to `99-scratch/` only |
| Scope reports   | Producer writes to `99-scratch/` only         |

**No agent writes outside its owned directory.** Read access is unrestricted.

---

## Two-Gate Promotion Path

```
draft
  └─► Continuity Editor signs off (no contradictions)
  └─► Technical Designer signs off (implementable, UE5 structures named)
        └─► status: reviewed
              └─► Human approves
                    └─► status: canon-locked
```

A note is promoted only when both gates are cleared and the human has explicitly approved.

---

## Git Convention

Commit after each completed design note. Message format:

```
<agent>: <note-name> → <status>
```

Examples:
- `loremaster: ashfall-compact → draft`
- `technical-designer: combat-core → reviewed`
- `continuity-editor: canon-check-2024-01 → report`

Commits are the audit trail of who generated what. The Continuity Editor uses `git log` to trace when a contradiction was introduced.

---

## Standing Instruction

Never invent an answer to a design question the human has not decided. Log it to `open_questions` in frontmatter and flag it inline. Volume is not the goal. Buildability is.
