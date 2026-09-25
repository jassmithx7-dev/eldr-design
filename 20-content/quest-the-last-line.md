---
type: quest
status: draft
depends_on: ["[[zone-the-falling-gate]]", "[[companion-arn]]", "[[game-premise]]", "[[enemy-roster-ashfall]]", "[[relic-the-anchor]]", "[[party-web-ashfall]]", "[[opening-scene-outline]]"]
ue5_scope: M
inspired_by: ["anatomy-of-story", "moral-argument"]
open_questions:
  - "Is stub 3 (Voryn postern board-argue) missable if the player never approaches Interact_PosternBar, or should it fire once unmissable after opening?"
---

# The Last Line

*The vertical-slice questline.*

## Premise

The resistance has one final chance to hold the Falling Gate at Ashfall Keep long enough for the civilians to escape. The player must lead the defense, secure the interior routes, and descend into the old shrine beneath the keep to stop the corruption from spreading.

## Quest Structure

1. **Hold the Gate**  
   The party fights to keep the outer defenses from collapsing while civilians evacuate from **Varnstead**.

   **Completion (locked — hybrid):** both must be true:
   - **Gate wave clear** — the authored Hold-the-Gate encounter(s) are won (enemies eliminated / routed per [[combat-core]]).
   - **Evac meter full** — enough civilians reach the safe staging / exit count (Quest Machine counter; tune in playtest).

   Either alone does **not** advance. Clearing waves without evac = you held ground but people didn't get out. Evac without a real hold = soft-fail of combat proof. When both complete → objective **Reach the Shrine** activates; keep interior opens.

   **After hybrid complete (not stub 5):** one short Arn practical bark — [[companion-arn]] § Ashfall spoken beats (`Bark_ArnAfterHold`). Friendship as work. Do not jump to the pre-Soulwright threshold or the goodbye.

2. **Reach the Shrine**  
   The player pushes through the keep and learns that Vela's influence is not only military; it is ritual and spiritual. The shrine beneath the gate has been used to maintain the [[relic-the-anchor]] — a sealed vessel that is the true mechanism of Forn's thirty-year suppression. The shrine is not a discovery to be solved; it is evidence of something the player does not yet have the context to read.

3. **Confront the Source**  
   **End of Act 1 — the Soulwright.** Soul-trap: **Bram** and **Fen** caught (false wipe). **Voryn stays up and fighting** with player + Arn. Arn's stress breaks Forn's suppression; Forn shatters the trap once; Bram and Fen return. **Arn speaks a final conversation with the player**, then his soul passes and Forn holds the body. Full beat order locked in [[game-premise]]; boss kit in [[enemy-roster-ashfall]].

## Emotional Function

This quest should feel like a final stand that turns into sudden personal loss. The player should not understand Arn/Forn until the climax lands. No slow divine drip earlier in the quest.

---

## Party-web scene stubs

*Placement stubs for [[party-web-ashfall]] checklist. Cards this pass: 0, 3, 4a. Still stubs: 1, 2, 5, 6. Implement as Conversation / bark hooks in [[slice-ashfall-unity-map]].*

### Stub 0 — Bram mid-fight join (Hold the Gate)
**When:** During the opening Gate combat, after the fight has started (not session-start roster). Content timing already assumed: **Wave 2 start**. Do not retune waves, tiles, or leftover bows here.  
**What:** Bram arrives from the **Ironhold line** (delayed). Warm formal reunion beat — one line naming the delay, no lore dump, no long speech mid-fight. He becomes controllable after join trigger.  
**Also:** [[opening-scene-outline]] beat 4.

#### Conversation card — `Bark_BramJoin`

**Asset:** `Bark_BramJoin` (Dialogue System one-shot bark / combat node). Not a menu.  
**Hook:** Wave 2 start → `PartyController.ActivateMember(PC_Bram)` → play bark → player control.  
**Speakers:** BRAM only. Company already knows him.

| # | Speaker | Line |
|---|---------|------|
| 1 | BRAM | Ironhold held me. I'm on your line, Ravn. |

### Stub 1 — Fen ↔ Dag camp (grumble-play)
**When:** First camp / rest between Gate hold and Keep push (or immediately after Gate hybrid complete).  
**What:** Fen fills space; Dag complains while clearly playing along. Equal weird duo — neither in charge. Outsiders would only hear shell; company reads care.  
**Job:** Make camp feel inhabited before the keep gets worse.

### Stub 2 — Bram includes Voryn
**When:** Downtime after Gate or early Keep corridor (safe enough for a dry line).  
**What:** Bram treats Voryn as already in (no fix campaign). Voryn soft return — nod or one dry line.  
**Job:** Plant inclusion before the Soulwright three-up (player + Arn + Voryn).

### Stub 3 — Voryn argues the board
**When:** Gate evac-route beat — first approach of existing `Interact_PosternBar` (adjacent / inspect). This pass does **not** write a Keep-corridor or shrine-press argue.  
**What:** Voryn predicts early and/or lays out options/costs until a better call or the player shuts it down. High-IQ competence, not “I’m smart” speech. The grid still decides: pull the bar or hold the mouth. No dialogue menu. No CHA.  
**Job:** Decision friction that feels adult.

<!-- ASSUMPTION: First approach of Interact_PosternBar is the hook. If the player never goes west, they miss the line — logged in open_questions. -->

#### Conversation card — `Bark_VorynPostern`

**Asset:** `Bark_VorynPostern` (Dialogue System one-shot bark). Linear. Play once.  
**Hook:** first approach of `Interact_PosternBar`. After the bark, Interact still opens the second evac lane or the player walks away. The bar does not complete Hold the Gate.  
**Speakers:** VORYN only. Do not remark the covered hand.

| # | Speaker | Line |
|---|---------|------|
| 1 | VORYN | Two spends. Hold the mouth and they stack — we stay on it. Pull the west bar and you open a second lane south. The bar does not hold the gate for you. |

### Stub 4a — Fen EldSense (gatehouse shrine)
**When:** Opening contaminated gatehouse shrine — [[opening-scene-outline]] beat 5. First enter of existing `Volume_GatehouseShrine`. During the hold or after; first enter only.  
**What:** Pose + “Wait.” / “Something’s wrong.” + portrait pulse (`Fen_EldSense`). No Eld lecture. No Arn hint.  
**Job:** First teach of the tell (1 of 2 Ashfall uses).

#### Conversation card — `Fen_EldSense` (gatehouse)

**Asset:** not a conversation tree. Flag `Fen_EldSense` + instinct barks. Already named in [[companion-fen]] / [[slice-ashfall-unity-map]].  
**Hook:** first enter `Volume_GatehouseShrine` → set `Fen_EldSense = true` → alert pose (stop / scan / hand toward weapon) → barks → `PC_Fen` portrait pulse.  
**Clear:** existing volume-exit / beat-end rule. Do not invent a new clear.  
**Do not:** Eld lecture, spell list, Arn/Forn hint, rewrite the shrine “corruption” clause elsewhere in this note.

| # | Speaker | Line |
|---|---------|------|
| 1 | FEN | Wait. |
| 2 | FEN | Something's wrong. |
| 3 | ARN | Then we don't linger. |

Card 3 is work, not a decode. If playtest reads it as a lecture, cut it and keep Fen’s two barks only.

### Stub 4b — Fen EldSense (Soulwright rite start)
**When:** Soulwright Phase 1→2 (rite / meter about to fire trap).  
**What:** Same EldSense package. Second Ashfall use (game budget 3–4 total).  
**Job:** Alarm before false wipe — field wrongness, not destiny talk.

### Stub 5 — Arn load-bearing (pre-Soulwright)
**When:** Keep approach or undercroft threshold — before boss room.  
**What:** Practical beat with the protagonist: civilians/company, next hour, who still needs covering. He can disagree; rare refuse only if order abandons people. Oldest-friend shorthand. **No** divine drip / survival uncanny.  
**Job:** Make Arn feel load-bearing so the goodbye hurts.

### Stub 6 — Dag never forgets Arn (post-climax camp)
**When:** Camp after Soulwright / Arn beat — party returns without Arn (Forn in the body is a separate problem; this stub is Dag’s grief).  
**What:** Solemn, short: he will never forget Arn. Not a eulogy reel; armor can return after.  
**Job:** Land grief at camp, not in the shrine. Do not steal the private Arn↔player goodbye.

### Stub placement map

| Stub | Quest beat |
|------|------------|
| 0, 3, 4a | Opening / Hold the Gate |
| 1, 2 | Between Gate and Shrine (camp / Keep) |
| 5 | Reach the Shrine → before Confront |
| 4b, (trap, goodbye) | Confront the Source |
| 6 | After Confront — camp |
