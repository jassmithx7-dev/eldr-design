---
type: canon
status: draft
depends_on: ["[[world-rules]]", "[[design-pillars]]", "[[combat-core]]"]
ue5_scope: M
open_questions:
  - "Ironhold — what is it? Mentioned as the Mountain-Hold alliance anchor. Needs a faction/location entry before this note can be promoted to reviewed."
  - "Half-Orc shares the Large size tier. They have no canon note yet. Flag for consistency when that note is written."
  - "Specific HP bonus and reach values for Large characters — deferred to attributes-core note (not yet written)."
  - "Animation budget for Large characters: the narrow-door crouch/squeeze animation is confirmed as intended. Solo dev cost assessment needed before implementation commitment."
---

# Goliath

*A Large race. The people who stay and hold the line.*

---

## Size

Goliaths are **Large**. In game terms this means:

- **Combat footprint:** 2×2 tiles (per [[combat-core]] §3 — large enemies already use this footprint; Goliath player characters use the same)
- **Melee reach:** 2 tiles (can attack from adjacent or one tile gap without moving into contact)
- **HP bonus:** above standard for their class — specific values deferred to attributes-core
- **Easier to hit:** Large characters have a lower Defense cap than Medium or Small characters at equivalent armor — they present more surface area
- **Narrow spaces:** Goliaths cannot move freely through standard doorways and tight corridors. A Goliath entering a Small or Medium-scale space ducks, turns, or presses through. This has a dedicated animation — not a mechanical penalty, but a legible world fact that the character and environment acknowledge

The tradeoff is built in. A Goliath is harder to kill and harder to ignore, and easier to land a blow on.

---

## Stats

Large size sets **high STR and CON floors and ceilings** — a Goliath's minimum starting STR and CON are higher than a Medium race's, and their maximum is higher. The exact values belong in the attributes-core note.

**Sex modifier applies** per [[world-rules]]: male Goliaths have higher STR and DEX floors and ceilings than female Goliaths.

Goliaths do **not** have a special relationship to Eld. They are not more or less likely to have sensitivity than other races. Magic is not their domain.

---

## Culture — The Mountain-Hold

Goliaths in the world of Eldr are associated primarily with the **Mountain-Hold** tradition: a long-standing compact among the northern passes and high corridors that predates the current war. The ethos is oath-bound, disciplined, and rooted in the idea that some positions must simply be held regardless of whether holding them wins anything.

**The Mountain-Hold disposition:**

- They stay. When a line is designated, a Mountain-Hold Goliath does not reconsider the designation.
- They are allied with **Ironhold** — a fortification, faction, or territorial claim in the north that has not yet been fully defined. The relationship is old and specific, not general goodwill toward any given army.
- They have an internal code around obligation: you honor what you committed to, you do not commit to things you cannot honor, and the two rules exist in permanent tension.

**What they are not:**

This is not the whole of Goliath culture. Two other tendencies exist and are acknowledged:

- **Wildland Goliaths** — untethered from any compact, unallied. Some humans use "Goliath" as a synonym for "raider" because of these groups. Mountain-Hold Goliaths find this offensive.
- **Stoneblood** — an older tradition, associated with Goliaths who carry memory of a time before the current political division of the passes. Rare. Viewed as either keepers of something important or as people who live in the past, depending on who is doing the viewing.

The Mountain-Hold is the dominant Goliath social identity in the world of the vertical slice. It is not the only one.

---

## Social Presence

Per [[design-pillars]] — social resolution uses Size, Perceived Power, and Raw INT. No CHA.

A Goliath's size is social leverage before they speak. They **command presence** in rooms where presence matters. Intimidation is not a stat they roll — it is an ambient fact about being Large in a world built for Medium creatures.

This cuts both ways. In spaces where power is unwelcome, a Goliath's size is legible before their intentions are. They cannot blend. They cannot be underestimated. Both are true at once.

---

## Bram

Bram is a Goliath. His companion note has not yet been written, but his characterization (pure goodness, warmth, loyal protector) fits naturally within the Mountain-Hold tradition — the person who stays not because they are commanded to but because leaving would not occur to them.

<!-- ASSUMPTION: Bram is Mountain-Hold-aligned by disposition if not by formal oath. Confirm in companion note when written. -->

---

## Implementation Notes

**The narrow-door animation** is a deliberate design choice, not a convenience. A Goliath moving through a standard-scale interior should acknowledge the scale difference — crouch, turn sideways, press through — with a short transitional animation. This is a solo-dev art commitment, not an engineering one. It should be scoped when Bram's companion note and the first interior zone are in active development.

**Grid footprint:** The 2×2 tile system for large enemies already exists in [[combat-core]]. Extending it to a player character requires the UI and camera systems to handle a player-controlled large unit — pathfinding, selection highlight, and follow-cam adjustments. This is the main engineering delta over the existing enemy implementation.
