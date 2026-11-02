---
name: bug-triage
description: Triage a suspected bug or finding with evidence. Use when the human reports unexpected behavior or asks whether something is a bug.
---
1. Restate the symptom and where it appears. Name the domain.
2. Run the live-first checks (`rules/live-first.md`): merged code and open PRs on `develop`, Linear search for the symptom, freshness of the relevant flow.
3. Find the source of intended behavior. If none exists, the result is an observation, not a bug.
4. Observe the live UI (`ui-check` skill) when behavior matters.
5. State at least two hypotheses and the evidence that eliminated the loser.
6. Apply `rules/verdicts.md`: status, numeric confidence, cited mechanism.
7. If it looks like a duplicate or already fixed, say so with the ticket and its status, and stop.
8. If it is a candidate bug, hand to `ticket-draft`. Never file.
