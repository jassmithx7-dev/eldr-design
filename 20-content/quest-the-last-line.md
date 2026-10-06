---
type: quest
status: draft
depends_on: ["[[zone-the-falling-gate]]", "[[companion-arn]]", "[[game-premise]]", "[[enemy-roster-ashfall]]", "[[relic-the-anchor]]", "[[party-web-ashfall]]", "[[opening-scene-outline]]"]
ue5_scope: M
open_questions:
  - "The notes do not say the breath Arn is gone, or whether Forn speaks. This scene uses the smallest version: the private line is the last thing Arn says, the body stays up, and Forn does not speak. Is that the moment?"
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

2. **Reach the Shrine**  
   The player pushes through the keep and learns that Vela's influence is not only military; it is ritual and spiritual. The shrine beneath the gate has been used to maintain the [[relic-the-anchor]] — a sealed vessel that is the true mechanism of Forn's thirty-year suppression. The shrine is not a discovery to be solved; it is evidence of something the player does not yet have the context to read.

3. **Confront the Source**  
   **End of Act 1 — the Soulwright.** Soul-trap: **Bram** and **Fen** caught (false wipe). **Voryn stays up and fighting** with player + Arn. Arn's stress breaks Forn's suppression; Forn shatters the trap once; Bram and Fen return. **Arn speaks a final conversation with the player**, then his soul passes and Forn holds the body. Full beat order locked in [[game-premise]]; boss kit in [[enemy-roster-ashfall]].

## Emotional Function

This quest should feel like a final stand that turns into sudden personal loss. The player should not understand Arn/Forn until the climax lands. No slow divine drip earlier in the quest.

---

## Party-web scene stubs

*Short placement stubs for [[party-web-ashfall]] checklist. Not full dialogue. Implement as Conversation / encounter hooks in [[slice-ashfall-unity-map]].*

### Stub 0 — Bram mid-fight join (Hold the Gate)
**When:** During the opening Gate combat, after the fight has started (not session-start roster).  
**What:** Bram arrives from the **Ironhold line** (delayed). Warm formal reunion beat — one line naming the delay, no lore dump, no long speech mid-fight. He becomes controllable after join trigger.  
**Also:** [[opening-scene-outline]] beat 4.

### Stub 1 — Fen ↔ Dag camp (grumble-play)
**When:** First camp / rest between Gate hold and Keep push (or immediately after Gate hybrid complete).  
**What:** Fen fills space; Dag complains while clearly playing along. Equal weird duo — neither in charge. Outsiders would only hear shell; company reads care.  
**Job:** Make camp feel inhabited before the keep gets worse.

### Stub 2 — Bram includes Voryn
**When:** Downtime after Gate or early Keep corridor (safe enough for a dry line).  
**What:** Bram treats Voryn as already in (no fix campaign). Voryn soft return — nod or one dry line.  
**Job:** Plant inclusion before the Soulwright three-up (player + Arn + Voryn).

### Stub 3 — Voryn argues the board
**When:** Gate or Keep decision beat (evac route, which corridor, whether to press shrine).  
**What:** Voryn predicts early and/or lays out options/costs until a better call or the player shuts it down. High-IQ competence, not “I’m smart” speech.  
**Job:** Decision friction that feels adult.

### Stub 4a — Fen EldSense (gatehouse shrine)
**When:** Opening contaminated gatehouse shrine — [[opening-scene-outline]] beat 5. The gate fight is over.  
**Who:** Ravn, Arn, Fen, Voryn, Bram. Dag is not in the gatehouse.  
**What:** Pose + “Wait.” / “Something’s wrong.” + portrait pulse (`Fen_EldSense`). No Eld lecture. No Arn hint.  
**Job:** First teach of the tell (1 of 2 Ashfall uses).  
**Not this room:** The old shrine under the keep (Reach the Shrine / the Anchor) is later. Passing this chapel does not complete that objective.

#### Scene

The gate fight is over. Ravn, Arn, Fen, Voryn, and Bram walk the gatehouse. Dag is not with them.

The passage is narrow stone. A chapel door stands open off it. Inside: a bench, a lamp still burning, an altar slab.

A soldier can see what is wrong. The lamp throws the slab’s shadow on the back wall, the way a lamp should. On the slab there is another dark — a film, thick, sitting against that light instead of with it. It is not soot. It does not flake. It is not a mark from the fight they just finished.

Fen has been talking.

**Fen:** Ravn, the bar on the door held. I said it would. Bram can—

He stops. He scans the chapel: the door, the corners, the slab. His hand goes toward his weapon.

**Fen:** Wait.

`Fen_EldSense`: alert pose, that one line, portrait pulse. He does not explain. He does not add a second sentence on his own.

Ravn can look at the slab. Ravn can look at Arn.

If Ravn looks to Arn, Arn looks at the slab, then at Ravn. He does not name the film. He does not look to Fen for a meaning. He does not tell Ravn what to make of it.

**Arn:** Ravn. We keep moving.

If Ravn presses Fen:

**Ravn:** Fen.
**Fen:** Something’s wrong.

That is the same beat, not a lecture. Nothing after it.

Voryn looks at the film once. He does not brief. Bram sees Fen coiled. He does not ask the room to teach him.

**Bram:** With you, Ravn.

They go on. The chapel stays behind them.

<!-- ASSUMPTION: The film on the slab is the visible contamination from [[opening-scene-outline]] beat 5 (shadow or residue a soldier can see). It is not named in dialogue. -->

### Lower court — the stuck family
**When:** After the gatehouse chapel. The company is in the lower court.  
**Who:** Ravn leads. Arn stands with him by choice. Fen is in the hall; he does not stop them here. Voryn and Bram are with them. Dag is not in the court.  
**Choice:** Physical. Ravn drops the bar, or he goes through the doorway. No talk menu.  
**Remembered fact (one):** the adult who can still work lives, or does not. No second flag.

#### Scene

The chapel is behind them. The lower court is the stone yard under the gatehouse. A hall runs across it. A room stands open off that hall. The bar is up in its brackets, not dropped.

A family is in the room. They cannot get out. One adult cannot move. One adult can still work. Children are in there with them. Settled Levy are in the room too — the same living soldiers from [[enemy-roster-ashfall]], not a new kind. They stand between the family and the door.

Ravn can see what the open door costs. If he leaves it open, those levy come out into the hall behind the company. If he drops the bar, what is in that room stays behind the bar. It does not come out into the hall. He does not spend the company on this room before the way down. The company stays intact. The hall stays clear.

Going through gets the family out of that room. It also means taking the fight.

Arn wants them out because they are stuck. He does not grade Ravn.

**Arn:** Ravn. They're stuck. Leave the bar up.

**If Ravn goes through**

Ravn goes through the doorway to them. He does not drop the bar.

The room is a short fight with the Settled Levy inside it. No numbers are set here.

Arn is with the adult who cannot move. That adult cannot be brought through the door. They do not come out. When the fight is done, the adult who can still work comes out, and the children who can walk come out with that adult. Arn comes out with Ravn.

The company has taken the fight. The people who could leave are with them.

**If Ravn drops the bar**

Ravn takes the bar and drops it into the brackets. The door shuts. The way is sealed.

The family does not come out. The levy stay in the room. They do not come into the hall behind the company. The company does not fight this room. The hall behind them is clear.

Arn stays beside Ravn. He does not say Ravn was wrong. He does not say he will leave.

#### The fire again

**When:** After the lower court. The company is back at Dag's fire.  
**Who:** Ravn is the player. Arn stands beside him. Fen and Dag are the ones talking. Bram and Voryn are in the room.  
**Flag:** The one fact from the court. The adult who can still work got out, or Ravn barred the way.

The company comes back to the back room. The fire is going. This is the same room as Stub 1. It does not replace that sitting. Fen and Dag are still the ones a person hears first.

Fen is on his feet.

**Fen:** Ravn. Dag kept your end of the bench. I told him you'd be back.

**Dag:** I kept the bench clear. Sit down.

Fen sits. He does not stop talking.

**Fen:** You see, Dag? Ravn's back.

**Dag:** I see him. Let me work.

Dag stays at the bench. He still does the real repairs. The court does not change that.

Arn stands beside Ravn. Bram is in the room. Voryn is in the room. They do not take the talk from Fen and Dag.

**If the adult who can still work got out**

That adult is at the fire. The children who walked out are with them.

The adult puts one ordinary thing in Ravn's hand. Food, or a little oil, or a spare strap. One thing.

Arn sees it. He does not make a speech about it.

**If Ravn barred the way**

Their place at the fire is empty.

Arn does not grade Ravn. He does not say he will leave.

**Arn:** Ravn. Their sister is already through with the carts. She will ask for them.

Bram can say what the door did.

**Bram:** Ravn. The door held. Nothing followed us up.

No one hands Ravn anything.

#### Act 2 camp

That same fact is still the only one later: if the adult lives, that same person is at the Act 2 camp selling ordinary supplies; if the adult does not live, that seller is not there. No shop, no prices, no inventory. Dag still does the real repairs either way. Missing this person does not lock Ravn out of gear that matters.

<!-- ASSUMPTION: The soldiers in the room are Settled Levy already on the Ashfall roster. How many is not set here. The through path is this short fight, not a second hard-walk version. -->
<!-- ASSUMPTION: On the through path, the adult who cannot move does not leave the room. Only the adult who can still work, and the children who can walk, get out. The person Arn says will ask is unnamed — the sister already through with the carts. -->
<!-- ASSUMPTION: "The lower court" is the yard just after the gatehouse chapel. [[zone-the-falling-gate]] does not name that yard yet. -->

### Stub 4b — Fen EldSense (Soulwright rite start)
**When:** Soulwright Phase 1→2 (rite / meter about to fire trap).  
**What:** Same EldSense package. Second Ashfall use (game budget 3–4 total).  
**Job:** Alarm before false wipe — field wrongness, not destiny talk.

### Stub 5 — the way down
**When:** After the second fire. The company leaves Dag's fire and walks toward the old shrine under the keep. Before the boss room.  
**Who:** Ravn leads. Arn stands beside him by choice. Fen, Bram, and Voryn walk with them. Dag stays at the fire.  
**What:** The next hour. Who still needs covering on the way down. Arn disagrees once. He still comes.  
**Not this walk:** The Soulwright fight. Arn's goodbye. The lower court. The family.  
**Job:** Make Arn feel load-bearing so the goodbye hurts.

#### Scene

The fire is behind them. Dag stays at the bench. He does not come.

**Dag:** Go on. I'll keep the fire.

The stair is stone. It is narrow. It goes down toward the old shrine under the keep.

Ravn leads. Arn walks beside him. Fen, Bram, and Voryn are on the stair with them.

**Fen:** Ravn, I've got the back.

He takes the rear.

**Bram:** Ravn. I'll hold the turn.

**Voryn:** Ravn. I'll call the corners.

**Arn:** Ravn. Leave one of us here. Dag is alone at the fire.

**Ravn:** No. Five of us go down. Dag holds the fire.

Arn comes. He does not say it again. He takes his place beside Ravn.

**Ravn:** Same stair back up.
**Arn:** On your left.

They keep walking.

<!-- ASSUMPTION: The way down is the keep stair from Dag's fire toward the old undercroft shrine. [[zone-the-falling-gate]] names the descent and does not name this stair. -->

### Arn's goodbye

**When:** End of Act 1, under the keep, after the Soulwright is destroyed.  
**Who:** Arn and Ravn. Voryn and Bram are in the room. They do not take the goodbye. Fen is in the quiet. Dag is still at the fire.  
**Not this scene:** The fight. Class or combat rules. Anyone explaining the gods. Any hint that Arn comes back.

#### Scene

The Soulwright is destroyed. That trap is ended. What it held can pass. The war is not over. No one says this.

Bram is back on his feet. Fen is back on his feet. Voryn is with them. They do not come into the goodbye.

Arn is still beside Ravn. He is still Arn.

**Arn:** Ravn. Get them up the stair.

**Arn:** On your left.

The second line is for Ravn. The others do not take it.

Then Arn is gone. The body stays on its feet. Arn's soul is not in it. Forn has the body. Forn does not speak. No one names him.

Fen is on his feet. He has not sat down.

The line from the fire is still open.

Ravn. Fen still hasn't settled down.

No one answers it.

Voryn and Bram stay in the room. They do not fill the quiet. Dag is still at the fire.

<!-- ASSUMPTION: The notes lock the order — the trap breaks, Arn speaks, then his soul is not in the body and Forn holds it — and do not lock the breath it happens on, or whether Forn speaks. Smallest version: the private line is the last thing Arn says; the body stays up; Forn does not speak and no one names him. -->
<!-- ASSUMPTION: The unanswered line is the one Arn does not finish at Dag's fire: "Ravn. Fen still hasn't settled down." That sitting is not in this branch's earlier scenes. Dag stays at the fire, as on the way down, so he is not in this room. -->

### Stub 6 — Dag never forgets Arn (post-climax camp)
**When:** Camp after Soulwright / Arn beat — party returns without Arn (Forn in the body is a separate problem; this stub is Dag’s grief).  
**What:** Solemn, short: he will never forget Arn. Not a eulogy reel; armor can return after.  
**Job:** Land grief at camp, not in the shrine. Do not steal the private Arn↔player goodbye.

### Stub placement map

| Stub | Quest beat |
|------|------------|
| 0, 4a | Opening / Hold the Gate |
| Lower court, the fire again | After the gatehouse chapel; then back at Dag's fire |
| 1, 2, 3 | Between Gate and Shrine (camp / Keep) |
| 5 — the way down | After the second fire, before Confront |
| 4b, Arn's goodbye | Confront the Source |
| 6 | After Confront — camp |
