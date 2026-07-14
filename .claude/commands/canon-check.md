# /canon-check

Invokes the **Continuity Editor** to run a full-vault contradiction audit.

## What this command does

1. Reads every non-`99-scratch/` note in the vault.
2. Checks for: proper-noun consistency against `[[glossary]]`, timeline coherence, faction-motivation consistency, mechanical terminology matching `10-systems/`, and tonal drift from `[[world-rules]]`.
3. Writes a report to `99-scratch/canon-check-<YYYY-MM-DD>.md`.
4. Prints a summary of open items (BLOCKER / MAJOR / MINOR counts).

## Output

The report is a Markdown file in `99-scratch/`. It is not edits. The Continuity Editor reports contradictions and proposes resolution options — it does not resolve them.

## Usage

```
/canon-check
```

No arguments. Scope is always the full vault.

## When to run

- On demand, any time you want a consistency check.
- Mandatory before promoting any note to `canon-locked`.
- After any session that added or modified content in `00-canon/`.

---

*Subagent: continuity-editor*
*Output directory: 99-scratch/*
*Side effects: none — read-only except for the audit report*
