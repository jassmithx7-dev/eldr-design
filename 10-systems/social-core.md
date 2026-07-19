---
type: system
status: draft
depends_on: ["[[design-pillars]]", "[[world-rules]]"]
ue5_scope: M
open_questions:
  - "What is the full resolution mechanic? (roll-based vs. threshold-based vs. scripted pass/fail with stat modifier)"
  - "How does perceived power update? (passive from combat outcomes, active from quest resolution, both?)"
  - "Does size create automatic pass conditions on certain checks, or just a bonus?"
  - "How does this interact with Fen's small size and Dag's dwarf stature — are they penalized on presence checks, and if so how?"
  - "Faction standing as a social lever — how is it tracked and displayed (or not displayed)?"
---

# Social Core

*The social resolution system for Eldr. No Charisma stat. Social outcomes are determined by three levers: Size, Perceived Power, and Raw INT.*

---

## Design Principle

Every character build has a social mode. No player should reach a story beat and feel they needed a dedicated "face" character to access it. A Goliath Fighter and a small-framed caster with high INT both have leverage — different kinds, equally real.

The intent is the opposite of Baldur's Gate 3's CHA model, where social content is gated behind a single stat that must be prioritized at character creation. Here, your class and build determine *how* you navigate social scenes, not *whether* you can.

---

## The Three Levers

### 1. Size

Physical presence is leverage before a word is spoken.

A Large character (Goliath, Half-Orc) commands different assumptions than a Medium or Small character entering the same room. This is not universal advantage — a Goliath in a space where they are perceived as a threat may close doors that a smaller character would find open. Size creates leverage; it does not guarantee outcomes.

**Implementation:** Size tier is a property of the character's race. Its social weight is expressed through authored scene beats and modifier values on presence-type checks, not through a separate "intimidation stat."

### 2. Perceived Power

What people believe you are capable of shapes what they will agree to.

Perceived power is not a number the player assigns at creation. It is built through play: enemies who have seen the party fight, NPCs who have witnessed a specific action, faction representatives who know the party's reputation in their territory. It is asymmetric — the same party reads differently to a Pale Circle archivist than to a Vela-aligned warlord.

**Implementation:** Tracked per-NPC or per-faction as a hidden modifier. Updated by authored trigger points (quest resolutions, combat outcomes observed by specific characters, faction-relevant actions). The player never sees the number — they see its effects in how NPCs respond.

### 3. Raw INT

The smart read. Finding the angle, knowing what someone needs to hear, recognizing a lie, threading an argument through someone's actual interests rather than their stated position.

INT is the only social lever the player can directly invest in at character creation. A high-INT character may not be large or feared, but they can read a room and find the pressure point.

**Implementation:** INT modifier applies to social checks where comprehension, argument construction, or deception-detection is the operative skill. The same modifier used for Eld pools and spell checks.

---

## What This System Does Not Have

- No Charisma stat or modifier.
- No Persuasion / Deception / Intimidation skill tracks separate from the three levers above.
- No "face character" requirement. Party composition should not gate story content.
- No charm or social bypass through magic. See [[eld-magic]] — Enchantment prohibition is absolute.

---

## Full Design

Deferred. This stub establishes the three-lever direction and the no-CHA commitment. The full system (resolution mechanics, how checks are called, how perceived power updates, how faction standing integrates) is Phase 2 design work.
