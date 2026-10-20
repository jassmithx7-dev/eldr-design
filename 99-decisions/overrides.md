---
type: ledger
status: live
---

# Override Ledger

Every time the human overrides a Skeptic [OBJECT], it is logged here.

This is not a record of shame. It is a decision audit trail. When something goes wrong in six months, this file is how you find the decision that caused it. Overrides are allowed. Overrides are recorded.

**Trigger word:** "override" — nothing else counts. Not impatience, not repetition, not rephrasing.

---

## Override — 2026-07-13
**Request:** Gender-based stat caps — average male has higher strength/speed ceiling than average female, consistent across races.
**Skeptic verdict:** [CONCERN] NECESSITY — race-based caps already provide the variation needed; gender caps add a second player-facing asymmetry that has caused friction in modern CRPGs.
**Human reason:** "This game will keep with what has been known for all time — the average male will be stronger/faster than the average female."
**Four-test result:** CANON [pass] | TONE [pass] | SCOPE [pass] | NECESSITY [concern]

---

## Foundational Decision — 2026-07-14
**Decision:** Target engine switched from UE5 (original brief assumption) to Unity.
**Type:** Not a Skeptic override — a foundational planning decision made with research. Logged here because it invalidates prior UE5-specific content and the paper trail matters.
**Four-test result:** N/A — this was not a content request; it was an engine selection.
**Reasoning:** Full rationale in [[engine]]. Summary: Unity's Pixel Crushers stack (Dialogue System + Quest Machine) is genre-proven for writing-driven CRPGs; UE5's strengths (rendering, GAS, C++) are mismatched to a text-and-tactics game. Systems tooling was the deciding factor, not environment tooling.

---

## Override — 2026-07-21
**Request:** Arn/Forn metaphysics and vertical-slice unmasking beat — Johnny/V model (Forn suppressed under Arn; Arn never aware); soul-trap false wipe (option 5) triggers Forn to break the trap once under stress; Arn gets a final conversation with the player; Arn's soul passes to a named rest-place (name TBD); Forn keeps the body as a stranger. Possible Arn return at game end left open.
**Skeptic verdict:** [OBJECT] CANON — prior lock "Arn is Forn / same person" forbids Arn's soul in heaven while Forn remains in the world.
**Human reason:** Explicit `override`. Model is Cyberpunk-like (Johnny taking V): Arn is a real unaware soul; Forn taking over sends Arn to the world's heaven; surprise for the player; no slow divine drip.
**Four-test result:** CANON [override — metaphysics rewritten] | TONE [pass — loss, not upgrade] | SCOPE [pass — one authored climax beat] | NECESSITY [pass — defines the slice hinge]

---

## Override — 2026-07-27
**Request:** Replace Fen's Eld-silence tell with spider-sense style Eld-wrongness alert (body language + instinct bark + portrait pulse). Triggers remain gatehouse shrine + Soulwright rite start.
**Skeptic verdict:** [CONCERN] NECESSITY (soft TONE) — silence-as-alarm was the individuating war-adult twist on Tas chatter; full spider-sense bark + pulse risks generic scout-tingle. Cheaper alt: keep silence identity, pulse + body language, optional one-word "Wait."
**Human reason:** Explicit `override`. Silence did not feel right; wants spider-sense readability (A+D package).
**Four-test result:** CANON [pass] | TONE [concern — override] | SCOPE [pass — retitle existing HUD work] | NECESSITY [concern — override]

---

## Foundational Decisions — 2026-10-10
**Type:** Not Skeptic overrides — human decisions from a canon interview, made to resolve contradictions blocking the lock of `world-rules`, `design-pillars`, `game-premise`, `factions` and `timeline`. Logged here because they rewrite earlier draft canon and the paper trail matters. No note changed status; everything touched is still `draft`.

| # | Topic | Decision |
|---|-------|----------|
| 1 | Ages | The company is 25–30. The intent is adults, not coming-of-age; "worn down young" is rejected. Arn is 30, so "thirty years ago" stands. Replaces "two decades, aware they are aging". |
| 2 | Eld sensitivity | Two tiers: Eld runs through everyone; only a rare few perceive it consciously and can study spells. |
| 3 | Forn | A known god who has gone silent. Not forgotten. |
| 4 | Race and sex stat ceilings | World fact, no mechanical system. |
| 5 | Company tenure | About ten years in arms. Arn since birth. |
| 6 | Dialogue | Fully linear. The player never selects lines. |
| 7 | Gods on screen | Gods walk the land, bounded to the three neutrals (Valdrek, Mordrek, Morrven), once each, Acts 2–3. |
| 8 | Arn | A paladin of Forn. |
| 9 | Forn's other faithful | Their prayers still work, weakly. Arn is one paladin among many. |
| 10 | The resistance | One organized army with a command structure. |
| 11 | War length | 15 to 20 years. |
| 12 | Command at Ashfall | The protagonist is the ranking officer. |
| 13 | Army name | The Line. |

**Concerns raised before the human decided (logged, not blocking):**
- #7 — TONE / SCOPE [concern]: on-screen gods pull against the FRAMING RISK in [[game-premise]] and the human-scale stakes line in [[world-rules]]. Human bounded it to three scenes.
- #8 — CANON [concern]: answered prayers to a silent god conflict with "no divine drip". Resolved by #9. Residual risk: the player hears "Forn" beside "Arn" all through Act 1.

**Left open by the human:** the single figure for the war's length; whether Arn may return at the ending; the era and the ancient event; what answers Forn's faithful; the Pale Circle's stance; whether a Size gate passes on Bram's presence.

---

## Override — 2026-10-19
**Request:** Reorder the project's priorities: (1) how combat looks — animation, spell and Eld effects — above all else; (2) story, a distant second; (3) systems. Combat visuals grounded, never cartoonish. Possibly make Eld visible on melee characters. Add named weapons (and potentially armor) with special abilities or spells.
**Skeptic verdict:** [OBJECT] CANON / SCOPE — reverses the founding differentiator in [[design-pillars]] ("achievable solo because it is carried by writing, not by assets, scope, or spectacle"). Animation and VFX are the most expensive, most specialist work for a solo developer; making them first priority raises cost and changes the engine evaluation (favours real-time 3D with a deep VFX asset supply; weakest for pre-rendered sprites).
**Human reason:** Explicit `override`. After watching a lot of gameplay from comparable RPGs, concluded that the way combat looks is the number-one thing to get right.
**Four-test result:** CANON [override — differentiator rewritten] | TONE [pass — grounded, not cartoonish] | SCOPE [object — override] | NECESSITY [pass — sets the quality bar]

---

## Foundational Decisions — 2026-10-19 (combat loop)
**Type:** Not Skeptic overrides — human decisions from a combat-loop interview. Logged because they replace the grid-tactics [[combat-core]].

| Topic | Decision |
|---|---|
| Combat form | Menu-driven, turn-based; no grid |
| Turn order | Visible timeline |
| Party meter | Company bond, spent on finishers |
| Resources | Full restore after every fight; Eld is a fixed pool per fight |
| Position | Front and back rows |
| Hit resolution | No misses; armor reduces damage |
| Turn actions | One action plus one minor action |
| Telegraphs | Answered with interrupt skills on the player's own turn |
| Finishers | Authored pairs |

**Concern raised (not blocking):** one action plus a minor action lengthens turns, which works against the presentation-first priority. Mitigation written into combat-core: minor actions resolve instantly with no staged animation.

**Left open:** active party size (human leaning toward 4, not locked); defeat handling; the finisher pair list; whether named-item abilities take a skill slot.

**Follow-up decisions, 2026-10-19:**
- Defeat: the fight restarts instantly at full strength; return to last rest point offered on the same screen.
- Finishers use only the acting partner's turn; the bond meter is the limit. May be cut after playtest.
- Named items: one item-ability slot per character beside 4–6 class skills; weapons give active Eld abilities; armor gives triggered effects; about 1–2 per character per act.
- Party size: 4 active of 5, chosen at camp or rest points; story fights may fix the party; the Soulwright climax fights with all five.

