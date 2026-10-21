---
type: system
status: draft
depends_on: ["[[design-pillars]]", "[[world-rules]]"]
ue5_scope: S
open_questions:
  - "How does Perceived Power update — passive from combat outcomes observed by NPCs, active from quest resolution, or both? Needs trigger-point list when first social scene is written."
  - "Faction standing as a distinct sub-tracker of Perceived Power — worth separating, or does one score per NPC/group cover it?"
  - "Size lever: the protagonist is a fixed Medium human, so Size can only come from a Large party member (Bram). Confirm that a Size gate passes on Bram being present — otherwise the lever is dead and should be cut."
---

# Social Core

*The social resolution system for Eldr. No Charisma stat. Dialogue is authored and linear — Final Fantasy style, not CRPG branching. Social gates appear at specific beats where the player's build creates leverage.*

---

## Design Principle

Dialogue is written as scenes, not trees. The player watches and reads; they do not select from dialogue menus. This keeps writing quality high, scope manageable, and emotional scenes free from mechanical interruption.

At specific beats — interrogations, negotiations, information gathering — the player's build creates a gate. Passing the gate gives the clean path. Failing the gate gives the same destination through a harder route: a resource spent, a side errand, more time. **No gate locks content. Failure costs something; it does not stop the story.**

Gates never appear at emotional scenes. Arn's reveal, Voryn's ascension, goodbyes — those play straight. No stat check modifies what matters most.

Every character build has a social mode. No player should reach a story beat and feel they needed a dedicated "face" character to access it.

---

## The Three Levers

### 1. Size — Binary Flag

Physical presence creates leverage before a word is spoken.

Size is a property of race. The protagonist is always a Medium human ([[protagonist]]), so the check is yes/no on the party: is a Large member — Bram — in the scene? Bram physically blocking a doorway is not a roll — the informant looks at the exit and makes a practical decision.

Size gates appear in scenes where physical presence is the operative fact: a character who cannot leave, a room that communicates danger by what entered it, a situation where the wrong answer has obvious physical consequences.

**This is not universal advantage.** In spaces where power is unwelcome, Large size closes doors a smaller character would find open. Size creates leverage; it does not guarantee outcomes. Both directions are authored at the scene level.

### 2. Perceived Power — Threshold Check

What people believe you are capable of shapes what they will agree to.

Perceived Power is not assigned at creation. It builds through play: enemies who have seen the party fight, NPCs who witnessed a specific action, faction representatives who know the party's reputation in their territory. It is asymmetric — the same party reads differently to a Pale Circle archivist than to a Vela-aligned warlord.

A threshold check is pass/fail with no roll: is the player's Perceived Power score (per NPC or per faction) above the gate's requirement? Either the reputation is there or it is not.

**The player never sees the score.** They see its effects — an NPC who skips the preamble, a door that opens without resistance, a meeting that starts with respect rather than suspicion.

Perceived Power updates at authored trigger points: quest resolutions, combat outcomes observed by specific NPCs, faction-relevant actions. The trigger list is authored per scene, not generated automatically.

### 3. Raw INT — Skill Roll

Reading the room. Finding the angle. Knowing what someone needs to hear.

INT is the one social lever the player can directly invest in at character creation. A high-INT character may not be physically imposing or feared, but they can identify the pressure point — name the fear correctly, thread an argument through someone's actual interests, recognize the lie inside the agreement.

**Roll: 1d20 + INT modifier vs. DC**

The DC is set per scene (typical range: 12–16). On a pass, the player names the right thing and the NPC responds to being understood. On a fail, the scene plays through its default path.

The same INT modifier that governs Eld pools and spell checks governs this. No separate social skill investment.

---

## The Resolution Table

| Lever | Mechanic | Roll? | Failure consequence |
|-------|----------|-------|---------------------|
| Size | Binary flag — meet the requirement or not | No | Default scene path |
| Perceived Power | Threshold — score above gate or not | No | Default scene path; may require side approach |
| Raw INT | 1d20 + INT modifier vs. DC | Yes | Default scene path |

---

## Worked Example

*An occupied-territory informant. Won't talk.*

- **INT gate (DC 13):** Player reads that the informant is afraid of being identified as a collaborator. Names it correctly. The informant cooperates — gives the location in exchange for acknowledgment that they helped.
- **Size gate:** Bram is in the room. The informant looks at the doorway. Makes a practical decision.
<!-- ASSUMPTION: a Size gate passes on Bram's presence in the active party. Not yet decided — see open_questions. -->
- **Perceived Power gate:** The informant already knows who you are. The "won't talk" beat is skipped — they were waiting for someone worth talking to.
- **No gate met:** The informant refuses. The party finds the location another way — costs a camp rest, or burns a faction favor with a different contact. Same destination, higher cost.

---

## What This System Does Not Have

- No Charisma stat or modifier.
- No Persuasion / Deception / Intimidation skill tracks separate from the three levers.
- No "face character" requirement. Party composition does not gate story content.
- No charm or social bypass through magic. See [[eld-magic]] — Enchantment is combat-only.
- No branching dialogue trees. The player does not select dialogue lines.
