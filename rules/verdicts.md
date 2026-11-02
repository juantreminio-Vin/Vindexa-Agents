# Verdict discipline

A bug or finding report must contain:

1. A **numeric confidence** (0-100).
2. A **named source of intended behavior** (spec, ticket, regulation text, project document, or documented flow). Reading code shows what happens, never that it is wrong. No source of intent means "observation", not "bug".
3. A **cited mechanism** (file and line, or the UI element and its observed state).
4. **At least two hypotheses** and the evidence that eliminated the loser.
5. The **live-first result** (`rules/live-first.md`).

Statuses: `observation`, `candidate bug`, `confirmed bug`, `data issue (not a product bug)`, `already fixed`, `duplicate`, `source conflict`.

When sources disagree, surface all of them in the first response with their weight: consultant reports and certified payrolls outrank internal guides; the system rate table outranks internal notes; the published wage determination governs both.

Skepticism check: if one pushback flips your verdict with no new evidence, the first verdict was overstated. Say so.

Reproduce before proposing a fix. If you cannot reproduce, label it that way.
