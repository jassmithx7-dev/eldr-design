# Eldr

An AI-assisted design system for a solo-developed 3D isometric CRPG (Baldur's Gate / Icewind Dale lineage, Unreal Engine 5). This repository is an Obsidian vault and a game design document — not a software project.

The goal is a **vertical-slice design package**: one zone, one questline, one companion, one combat encounter. Internally consistent. Canon-locked. Specific enough to open UE5 and start building.

---

## Directory Structure

| Directory | Purpose |
|-----------|---------|
| `00-canon/` | **Single source of truth.** World rules, factions, timeline, glossary. Canon-locked notes here are immutable without human approval. |
| `10-systems/` | Game mechanics — combat math, attributes, progression, skill checks, itemization. |
| `20-content/` | Zones, quests, companions, encounters. |
| `30-technical/` | UE5 implementation mapping. Every reviewed design note has a counterpart here. |
| `99-scratch/` | Unvetted staging area. Never cited as truth. Not versioned. |
| `.claude/agents/` | Subagent definitions (Loremaster, Systems Designer, Encounter Designer, Technical Designer, Continuity Editor, Producer). |
| `.claude/commands/` | Slash commands for common workflows. |

**Start reading in `00-canon/`.** Everything else depends on it.

---

## Slash Commands

### `/canon-check`
Runs a full-vault contradiction audit via the Continuity Editor. Output is a report in `99-scratch/` — findings only, no edits. Run this before locking any note.

### `/scope-audit`
Invokes the Producer to report scope creep, generate a cut list, and state total implementation weight as a number. Run this after any session that added content.

### `/new-quest <premise>`
Runs the full pipeline for one quest: Loremaster drafts → Systems Designer specs mechanics → Encounter Designer builds encounters → Technical Designer maps to UE5 → Continuity Editor audits → Producer scopes.

Example:
```
/new-quest The player must recover a stolen relic before it is used to break the treaty between two rival factions.
```

---

## Promotion Path

No note advances status without clearing both gates:

```
draft → [Continuity Editor + Technical Designer sign off] → reviewed → [human approves] → canon-locked
```

---

## Source of Truth

`00-canon/` is the single source of truth. When any other note contradicts a canon-locked note in `00-canon/`, the canon note wins and the conflict must be resolved by the human before work continues.
