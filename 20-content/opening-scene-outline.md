---
type: quest
status: draft
depends_on: ["[[game-premise]]", "[[zone-the-falling-gate]]"]
ue5_scope: S
inspired_by: ["anatomy-of-story", "moral-argument"]
open_questions: []
---

# Opening Scene Outline

*The first scene of the vertical slice.*

## Purpose

The opening should establish three things immediately:

1. The world is already losing ground.
2. The player is a tired, experienced leader.
3. The party is a group of old friends carrying history into a war they did not start.

## Scene Summary

The player arrives at the Falling Gate mid-retreat. The resistance is already falling back, covering the final evacuation of **Varnstead**. The outer walls are damaged, the streets crowded with frightened civilians. The party's job is not to win — it is to hold long enough for the retreat not to collapse into panic.

## Key Beats

1. **The world is already in retreat.**  
   The player sees smoke, broken barricades, and people carrying what little they can save. **Scripted** in `Conv_AshfallOpening` below.

2. **The player is recognized as the one who holds the line.**  
   People look to them for orders, not because they are glamorous, but because they have survived long enough to be trusted. **Scripted** in `Conv_AshfallOpening` below.

3. **Arn is present as the steady companion.**  
   He does not speak like a hero. He speaks like someone who has been there before and knows what it costs. **Scripted** in `Conv_AshfallOpening` below. After-hold practical bark lives on [[companion-arn]] — not this conversation.

4. **Bram joins mid-fight — not on the starting roster.**  
   He was **delayed from the Ironhold line** (oath/Hold front — not Ashfall renamed). He arrives into the Gate battle as a reunion (~20-year bond), not a stranger recruit. Warmth + formal edge; no long reunion speech mid-fight. One beat can name Ironhold delay without a lore dump. **Spoken line:** [[quest-the-last-line]] stub 0. Not part of `Conv_AshfallOpening`.

5. **The first sign of the supernatural appears.**  
   A shrine or chapel inside the gatehouse is contaminated by strange shadow or residue. The danger is no longer just soldiers and sieges. **Fen EldSense fires here** (pose + “Wait.” / “Something’s wrong.” + portrait pulse) — first teach of the alarm. He does not explain Eld. **Spoken package:** [[quest-the-last-line]] stub 4a. Not part of `Conv_AshfallOpening`.

6. **The scene ends with urgency, not clarity.**  
   The gate holds for now, but the party realizes that the enemy is not merely advancing; it is changing the world itself. **Still a stub.** Do not script this pass.

---

## Conversation cards — `Conv_AshfallOpening`

**Asset:** `Conv_AshfallOpening` (Dialogue System). Already named in [[slice-ashfall-unity-map]].  
**When:** Gate bootstrap / load, **before Wave 1**. Play once.  
**Form:** Linear cards. No player menu. No CHA. No social gate. No class callout. Companions address **Captain** — never a personal name.  
**Speakers on stage:** CAPTAIN (`PC_Protagonist`), ARN (`PC_Arn`), FEN (`PC_Fen`), VORYN (`PC_Voryn`). **Bram absent.**  
**On end:** hand the Gate to Hold-the-Gate combat. Do not start Wave 1 under this conversation.

STAGE lines are director text (camera / blocking). They are not spoken.

| # | Beat | Speaker | Line |
|---|------|---------|------|
| 1 | 1 | STAGE | Smoke on the north approach. Broken barricades. People from **Varnstead** crossing the south apron with what they can carry. The company is already in the courtyard. Bram is not among them. |
| 2 | 1 | FEN | They're still coming through. |
| 3 | 1 | VORYN | Withdrawal. Not a stand they asked for. |
| 4 | 1 | ARN | Then we make it one long enough. |
| 5 | 2 | FEN | They're waiting on you. |
| 6 | 2 | CAPTAIN | Mouth first. We don't let this become a run. |
| 7 | 3 | ARN | You take the line. I'll watch who's still outside. |
| 8 | 3 | CAPTAIN | Same as last time. |
| 9 | 3 | ARN | Same as every time. People first. |
| 10 | 3 | FEN | Bram's late. |
| 11 | 3 | ARN | He'll walk in when he can. |
| 12 | 3 | CAPTAIN | Work. |

**Do not add here:** shrine / Eld lecture (stub 4a), Ironhold dump (stub 0), postern board-argue (stub 3), after-hold Arn, Reach the Shrine, Soulwright, goodbye.

## Tone

The opening should feel exhausted, practical, and haunted. It should not feel like a triumphant beginning. It should feel like the last time anyone still believes they can hold something together.
