# Eldr — Control Panel

**Start here:** [[Eldr-at-a-glance]] — one page of everything decided.

---

## Status Board

```dataview
TABLE type, status, ue5_scope
FROM "00-canon" OR "10-systems" OR "20-content" OR "30-technical"
WHERE file.name != ".gitkeep"
SORT status ASC, file.name ASC
GROUP BY status
```

---

## Blocked on Me

*Notes with open questions that require a human decision.*

```dataview
TABLE open_questions
FROM "10-systems" OR "20-content" OR "30-technical" OR "00-canon"
WHERE open_questions AND length(open_questions) > 0
SORT file.mtime DESC
```

---

## Complexity Ledger

*All notes with a scope rating (`ue5_scope` — Unity implementation weight).*

```dataview
TABLE type, ue5_scope, status
FROM "10-systems" OR "20-content" OR "30-technical"
WHERE ue5_scope
SORT ue5_scope ASC, file.name ASC
```

**Scope counts:**

```dataview
TABLE length(rows) AS "Note Count"
FROM "10-systems" OR "20-content" OR "30-technical"
WHERE ue5_scope
GROUP BY ue5_scope AS "Weight"
SORT ue5_scope ASC
```

---

## Canon

```dataview
TABLE status
FROM "00-canon"
WHERE file.name != ".gitkeep"
SORT status ASC, file.name ASC
```

---

## Recently Touched

```dataview
TABLE file.mtime AS "Modified", status, type
FROM "00-canon" OR "10-systems" OR "20-content" OR "30-technical"
WHERE file.name != ".gitkeep"
SORT file.mtime DESC
LIMIT 10
```
