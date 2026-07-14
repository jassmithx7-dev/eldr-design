# AI-Assisted CRPG Design System — Project Prompt

> **How to use this file:** Place it at the root of your CRPG repo/vault as `PROJECT_BRIEF.md`. Open the folder in Cursor or Claude Code and give the agent this instruction: *"Read PROJECT_BRIEF.md and execute Phase 0."*

---

## Objective

Build a **role-based AI design system inside Obsidian + Claude Code** that produces a coherent, implementable game bible for a solo-developed 3D isometric CRPG (Baldur's Gate / Icewind Dale lineage, Unreal Engine 5).

The deliverable is **game design content**, not a software platform. There is no orchestration server, no web UI, no custom API layer. The tooling is Claude Code's native subagent system operating on a Markdown vault.

**Definition of done:** a vertical-slice design package (one zone, one questline, one companion, one combat encounter) that is internally consistent, canon-locked, and specific enough that a solo developer can begin UE5 implementation without further design decisions.

---

## Non-Goals (do not build these)

- Multi-agent orchestration framework or message bus
- Web interface, dashboard, or progress tracker
- OpenAI API integration or any external API layer
- Flask/React/Replit anything
- A tabletop RPG module
- A complete, exhaustive game bible for the whole game

Anything that is not design content for the vertical slice is out of scope. If a task does not directly produce or validate slice content, do not do it.

---

## Architecture

```
crpg-vault/
├── CLAUDE.md                    # Coordinator: canon rules, agent routing, scope guard
├── PROJECT_BRIEF.md             # This file
├── .claude/
│   ├── agents/
│   │   ├── loremaster.md
│   │   ├── systems-designer.md
│   │   ├── encounter-designer.md
│   │   ├── technical-designer.md
│   │   ├── continuity-editor.md
│   │   └── producer.md
│   └── commands/
│       ├── canon-check.md       # Run continuity audit across vault
│       ├── new-quest.md         # Full quest pipeline, all roles
│       └── scope-audit.md       # Producer reviews slice for creep
├── 00-canon/                    # LOCKED. Single source of truth.
│   ├── world-rules.md           # Magic, cosmology, physics — what CAN happen
│   ├── factions.md
│   ├── timeline.md
│   └── glossary.md              # Every proper noun, defined once
├── 10-systems/                  # Mechanics, stats, progression
├── 20-content/                  # Zones, quests, companions, encounters
├── 30-technical/                # UE5 implementation mapping
└── 99-scratch/                  # Unvetted output. Never referenced as truth.
```

**Data flow:** All inter-role communication happens as Markdown files in the vault with YAML frontmatter. Obsidian wikilinks are the dependency graph. There is no JSON protocol — the vault *is* the protocol.

**Frontmatter schema (every content note):**
```yaml
---
type: quest | zone | companion | system | encounter | canon
status: draft | reviewed | canon-locked
depends_on: [[world-rules]], [[faction-name]]
ue5_scope: <estimated implementation weight: S | M | L | XL>
open_questions: []
---
```

---

## Agent Roles

Each role is a Claude Code subagent with an isolated context. Define each in `.claude/agents/<name>.md`.

### 1. Loremaster
**Owns:** `00-canon/`, narrative content in `20-content/`
**Produces:** world rules, factions, timeline, characters, quest narratives, dialogue
**Hard constraints:**
- May never contradict a `canon-locked` note. If new fiction requires changing canon, it must **stop and file a canon-change request**, not silently diverge.
- Every new proper noun goes in `glossary.md` on first use.
- Narrative must be expressible through CRPG verbs: dialogue, combat, exploration, skill checks, world state. **No cutscene-dependent storytelling.** If the emotional beat only works as a cinematic, it doesn't work.

### 2. Systems Designer
**Owns:** `10-systems/`
**Produces:** combat math, attributes, classes, progression curves, skill checks, itemization, economy
**Hard constraints:**
- Every mechanic ships with **concrete numbers**, not adjectives. "Balanced sword" is a failure; "1d8+STR, 1.2s wind-up, 15% armor pen" is a deliverable.
- Every mechanic names the **player decision it creates.** A system that doesn't produce an interesting choice is cut.
- Solo-dev complexity budget: if a system needs more than ~2 weeks of implementation, it must be justified against a simpler alternative.

### 3. Encounter Designer
**Owns:** encounter and zone-layout notes in `20-content/`
**Produces:** isometric zone layouts, enemy compositions, spatial/tactical setups, environmental interactions, pacing
**Hard constraints:**
- Design for a **fixed isometric camera**. Verticality, sightlines, and cover must read from a 3/4 top-down view. Note explicitly when something won't.
- Every combat encounter specifies: arena footprint, enemy roster + counts, terrain features, win/loss conditions, and the tactic it is meant to teach or punish.
- Every zone specifies at least two traversal paths and one non-combat solution.

### 4. Technical Designer
**Owns:** `30-technical/`
**Produces:** the mapping from design → UE5 structures
**Hard constraints:**
- **No design note is `reviewed` until this agent has signed off on implementability.** This is the gate that prevents an unbuildable bible.
- Output names actual UE5 constructs: Data Assets, Gameplay Ability System (attributes, effects, abilities, tags), Behavior Trees, Data Tables, Blueprint vs. C++ boundary, save-state serialization.
- Flags anything requiring engine-level work, custom tooling, or third-party plugins.
- Maintains a running **complexity ledger**: implementation weight per feature, so the Producer can see cost.

### 5. Continuity Editor
**Owns:** cross-cutting audits. Owns nothing exclusively; reads everything.
**Produces:** contradiction reports, canon-drift alerts, glossary enforcement, tonal consistency passes
**Hard constraints:**
- Runs on demand via `/canon-check` and mandatory before any note is promoted to `canon-locked`.
- **Reports contradictions, does not silently resolve them.** Resolution is a human decision — surface the conflict, name both sources, propose options.
- Checks: proper-noun consistency, timeline coherence, faction-motivation consistency, mechanical terminology matching `10-systems/`, tonal drift.

### 6. Producer
**Owns:** scope. Owns the right to say no.
**Produces:** scope audits, cut lists, cost/benefit on features
**Hard constraints:**
- Adversarial by design. Assumes every proposed feature is scope creep until proven otherwise.
- On every `/scope-audit`: lists what has crept in since last audit, what can be cut without damaging the slice, and what the current total implementation weight is.
- Has explicit authority to mark any note `CUT` with a one-line rationale.
- **Never adds content. Ever.**

---

## Coordination Rules (put in `CLAUDE.md`)

1. **Canon supremacy.** `00-canon/` notes marked `canon-locked` are immutable except by explicit human approval. Any agent that needs to violate canon stops and asks.
2. **No agent writes outside its owned directory.** Cross-directory needs are filed as requests, not edits.
3. **The two-gate promotion path.** `draft` → (Continuity Editor + Technical Designer both sign off) → `reviewed` → (human approves) → `canon-locked`. Nothing skips a gate.
4. **`99-scratch/` is quarantine.** Content there is never cited as truth by any agent.
5. **Open questions are surfaced, never invented over.** If an agent lacks a decision it needs, it writes it to `open_questions` in frontmatter and proceeds with the smallest possible assumption, flagged inline.
6. **Human is the final editor.** Agents propose; the developer disposes.

---

## Execution Phases

### Phase 0 — Scaffold
Create the vault structure, `CLAUDE.md`, and the six agent definition files. Populate `00-canon/world-rules.md` with a skeleton and stop. **Ask the developer the foundational questions** (setting, tone, magic model, party size, real-time-with-pause vs. turn-based, the one thing this CRPG does that others don't) before generating any fiction. Do not guess these.

### Phase 1 — Canon Foundation
Loremaster drafts world rules, 2–3 factions, glossary. Continuity Editor audits. Human locks. **Nothing else starts until canon is locked.**

### Phase 2 — Systems Spine
Systems Designer produces combat core + progression + skill-check resolution. Technical Designer maps to GAS and produces first complexity ledger entry. Producer audits.

### Phase 3 — Vertical Slice
One zone. One questline (3–5 beats). One companion (with arc + reactivity hooks). One signature combat encounter. All roles in pipeline. Full two-gate promotion on every note.

### Phase 4 — Validation
Continuity Editor runs full-vault `/canon-check`. Producer runs `/scope-audit` and reports total implementation weight. Technical Designer produces a UE5 implementation order-of-work.

---

## Success Criteria

The system works if:

- [ ] A `/canon-check` across the full vault returns **zero unresolved contradictions**.
- [ ] Every `reviewed` note has a Technical Designer sign-off naming its UE5 structures.
- [ ] The vertical slice's total implementation weight is **known and stated as a number**, not a vibe.
- [ ] The developer can open UE5 and start building without asking a single "but what does X do?" question.
- [ ] The Producer has cut at least one thing. If it hasn't, it isn't working.

It fails if it produces a large volume of beautiful, unimplementable, mutually contradictory lore. **Volume is not the goal. Buildability is.**
