---
type: canon
status: draft
depends_on: ["[[world-rules]]"]
ue5_scope: S
open_questions: []
---

# Design Pillars

*Foundational human decisions that constrain all agents. These are the decisions before the decisions — they shape what is possible in every downstream note.*

---

## The Name

**Eldr** is the name of the world. It is also the project title. Do not invent an etymology or explain the name in-fiction — it is the name, not a word with a meaning characters would reference.

---

## The Differentiator

A grim, adult CRPG about a company of long-time friends — adults aged 25 to 30, about ten years in arms together — doing dangerous work in a war they grew up inside. The party bond is **inherited, not earned in-game**.

The point of their age is maturity, not weariness. This is not a coming-of-age story and nobody in it is finding themselves. They are not "worn down young" either: they are competent adults. *(Decided 2026-10-10 — replaces the earlier "two decades, aware they are aging" framing.)*

This is achievable solo because it is carried by writing, not by assets, scope, or spectacle. It is difficult for a studio because it denies players the recruit-and-befriend fantasy that testing rewards.

---

## Rarity and Missability

**Rare and missable content is intentional and welcome.**

- Authored events that fire **few times** (or once) are preferred over always-on reminders.
- Players **may miss** optional color, tells, environmental reads, and some side beats. That is a feature — replay and attention are rewarded; the game does not have to guarantee every observation.
- Agents must **not** “fix” rarity into unmissable tutorials, constant UI chips, or spam triggers unless the human explicitly asks for guaranteed readability on that beat.
- **Exception:** critical story hinges stay unmissable (e.g. Arn unmasking / Soulwright climax, Voryn ascension). Emotional spine ≠ optional Easter egg.
- Example already in force: Fen EldSense is **3–4 beats game-wide** — sparse on purpose ([[companion-fen]]).

---

## Structure

- **Three acts only.** Locked. See [[world-rules]].
- **No chapter system** (reject BG2's 7-chapter / dual-sandbox model). Acts are the only structural spine.
- Lineage inspiration (BG / IWD) does not mean matching their content volume or chapter count.

## Target Playtime

Locked solo-scope budgets (main path unless noted):

| Deliverable | Hours | Notes |
|-------------|-------|--------|
| **Vertical slice** | **3–5** | Ashfall Keep / The Last Line / Soulwright / Arn unmasking. Proof of combat + writing + loss beat. |
| **Full game** | **15–20** | ~5–7 hours per act. Dense, not wide. |
| **Ceiling with side content** | **≤25** | Cap biome side content; no Athkatla-scale hubs. |

Reject BG2-length (50–100+ hr) as a target. If a design pushes past the ceiling, cut content — do not expand the budget.

## Enemy Variety Budget

Locked solo-scope limits (unique combat **kits**, not palette swaps):

| Scope | Count |
|-------|--------|
| **Act 1 / vertical slice** | **7 + Soulwright** (see [[enemy-roster-ashfall]]) — do not expand without cutting something |
| **Acts 2 and 3 each** | **+4–6 new kits** + 1 act boss |
| **Full game** | **~18–22** typical; **hard ceiling ≤25** including bosses |

Rules:
- Reskins / one-stat variants of an existing kit do **not** count as new types.
- Large (2×2) enemies are expensive — prefer ≤1 new Large kit per act.
- If a note needs a new mesh **and** new AI, it consumes budget; cut elsewhere or reject.

## Quest Budget

Locked solo-scope limits:

| Scope | Main | Side | Total |
|-------|------|------|-------|
| **Vertical slice** | **1** — [[quest-the-last-line]] | **0–1** keep-local (optional) | **1–2** |
| **Full game** | **3** (one continuous spine, one major questline per act) | **6–9** | **9–12** |
| **Per act (full)** | 1 main (~4–6 hr) | **2–3** sides (~30–75 min each) | — |

**Side content ceiling:** ≤ ~5 hours of the full playtime budget.

**No fetch quests.** Reject “go get item / walk back” loops with no meaningful decision. Preferred side types: hold/under-fire, investigation with cost, moral/tactical choice with lasting consequence, companion pressure, social gates, clear-with-consequence.

**Spine rule:** Side quests feed the main war/friendship story (party, locals, faction leverage, evidence). They do not open an Athkatla-scale second sandbox. If a side quest has no important function in the overall story, cut it.

## Protagonist

- **Age:** 25–30. An adult — not a teenager, not coming of age.
- **Competence:** earned through years of work, not innate talent or bloodline.
- **Character creation:** fully player-authored — class, stats, build. Classic CRPG character creation in the Baldur's Gate / Icewind Dale lineage.

---

## Party Structure

- **Party size:** 5 controllable characters (protagonist + 4 companions).
- **Combat paradigm:** turn-based. Locked.

---

## Companions

**Active party (playable, full combat kits, full arcs):**

| Character | Class | Acts |
|-----------|-------|------|
| Arn | Paladin of Forn (divine, non-Eld) | Act 1 only — replaced by Solen at Act 2 |
| Fen | Shadow (Thief) | Acts 1–3 |
| Bram | Blade (Fighter, Goliath) | Acts 1–3 |
| Voryn | Eld-Weaver | Acts 1–3 — ascends at ending |
| Solen | Devotee (Healer) | Acts 2–3 |

**Story NPCs (no combat kit required):**

| Character | Role |
|-----------|------|
| Dag | Camp craftsman — gear modification, upgrades. Present throughout. |
| Forn | Brief NPC presence after Arn's mask slips. Not playable. |

- **Classes:** fixed. Companions are pre-authored people with histories. Their class is characterization, not a build slot.
- **Relationship to protagonist:** the company has been in arms together for about ten years; the protagonist has known Arn since birth, and the others joined in the company's first years. The friendship predates the game. There is shorthand, old debts, arguments nobody reopens, affection that is already load-bearing. Solen is the exception — she joins at Act 2.
- **Shared history in dialogue:** must remain class-agnostic. References the relationship, never the protagonist's build.
- **Vertical slice focal companion:** Arn. Other party members are present but his arc is the one built end-to-end in the slice.

---

## Social System

No Charisma stat. CHA does not exist as a player-assigned attribute in Eldr.

Social resolution draws on three levers instead:

- **Size** — physical presence as leverage. A Goliath commands a room without speaking. A Small character in the same scene does not. The protagonist is a fixed human (Medium), so Size leverage is never part of the player's build — see the open question in [[social-core]].
- **Perceived power** — reputation, demonstrated ability, faction standing, visible combat capability. What people *think* you can do shapes what they will agree to.
- **Raw INT** — the smart read. Reading the room, finding the angle, knowing what someone needs to hear. Intelligence as social tool.

The intent: every character build has a social mode. A high-INT caster negotiates differently than a physically imposing Fighter, but neither is locked out of the story. No player should feel they needed a "face" character to experience the game fully.

**Dialogue is authored and linear — Final Fantasy style, not CRPG branching.** The player does not select from dialogue menus. Social gates appear at specific beats (interrogations, negotiations, information gathering) where the player's build creates leverage. Passing a gate gives the clean path; failing costs something (time, a resource, a harder route) but never locks content. Emotional scenes — the Arn reveal, Voryn's ascension — play straight with no gates.

Full mechanics in `10-systems/social-core.md`.

---

## Systems Posture

Not a hardcore sim.

- Downed at 0 HP, revivable.
- No permadeath. Characters cannot die from combat mechanics. Death is a story event — authored deliberately in specific narrative moments, never generated by the combat system.
- No persistent injury system.

Classic CRPG resolution. The grimness is tonal and narrative — it lives in the writing. Mechanical punishment is not the register.
