# /new-quest

Runs the full pipeline for one new quest, passing through all agent roles in order.

## Usage

```
/new-quest <one-line quest premise>
```

**Example:**
```
/new-quest The player must recover a stolen relic before it is used to break the treaty between two rival factions.
```

## Pipeline

The command runs these steps in sequence. Each step must complete before the next begins.

### Step 1 — Loremaster: narrative draft
- Writes the quest note to `20-content/quests/<slug>.md`
- Includes: quest hook, 3–5 beats, key NPCs, dialogue summary, player choices and consequences, world-state changes
- Status: `draft`
- Adds any new proper nouns to `[[glossary]]`

### Step 2 — Systems Designer: mechanics assessment
- Reviews the quest for any new mechanics or skill-check types it requires
- If new systems are needed: writes system note(s) to `10-systems/`
- If existing systems are sufficient: writes a one-paragraph confirmation in `30-technical/` (no new file needed)
- Each new system note must include concrete numbers and name the player decision it creates

### Step 3 — Encounter Designer: encounter build
- For each combat or traversal encounter in the quest, writes an encounter note to `20-content/encounters/<slug>-<encounter-name>.md`
- Each encounter specifies: arena footprint, enemy roster + counts, terrain features, win/loss conditions, tactic taught/punished

### Step 4 — Technical Designer: UE5 mapping + sign-off
- For each new note (quest, system, encounter), writes a technical mapping note to `30-technical/`
- Names actual UE5 constructs; updates the complexity ledger
- Signs off on each note by adding `tech_signoff: [[technical-note]]` to its frontmatter
- Notes that cannot be signed off are flagged with `ue5_scope: BLOCKED` and a blocking reason

### Step 5 — Continuity Editor: contradiction audit
- Audits the new notes against the full vault
- Writes report to `99-scratch/canon-check-<YYYY-MM-DD>-<quest-slug>.md`
- Any BLOCKER findings halt promotion until resolved

### Step 6 — Producer: scope check
- Reviews all new notes against current vertical-slice scope
- Adds any out-of-scope elements to the cut list
- Reports new total implementation weight

## Output

At the end of the pipeline, the command prints:
- List of all notes created
- Any open questions logged across all agents
- Any BLOCKER contradictions from the Continuity Editor
- Any scope concerns from the Producer
- Current total implementation weight

Notes are promoted to `reviewed` only after both Technical Designer sign-off and a clean Continuity Editor report. Human approval is required for `canon-locked`.

---

*Subagents: loremaster → systems-designer → encounter-designer → technical-designer → continuity-editor → producer*
*Sequential — each step depends on the previous*
