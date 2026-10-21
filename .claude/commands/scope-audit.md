# /scope-audit

Invokes the **Producer** to audit current scope against the vertical-slice target.

## What this command does

1. Reads all non-`99-scratch/` notes and the complexity ledger at `[[complexity-ledger]]`.
2. Identifies everything added since the last scope audit that was not in the approved vertical-slice scope.
3. Produces a cut list of features that can be removed without damaging the slice.
4. Reports total current implementation weight as a number (estimated weeks).
5. Writes the report to `99-scratch/scope-audit-<YYYY-MM-DD>.md`.

## Output

Three sections:
- **Creep inventory** — what crept in, named by file
- **Cut list** — what to remove, with one-line rationale per item
- **Total implementation weight** — sum of `ue5_scope` (Unity implementation weight) across all live notes, in estimated weeks

## Usage

```
/scope-audit
```

No arguments.

## When to run

- After any session that added new content, systems, or encounters.
- Before beginning a new phase.
- Any time you suspect the slice is growing beyond one developer's capacity.

---

*Subagent: producer*
*Output directory: 99-scratch/*
*Side effects: may add `status: CUT` to notes it marks for removal*
