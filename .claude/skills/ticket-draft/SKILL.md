---
name: ticket-draft
description: Draft a Linear ticket or comment from a verified finding. Use after bug-triage; produces an editable draft only.
---
Preconditions: live-first checks done and recorded; duplicate and already-fixed check done (state which tickets were checked and their status).

Draft contains: title, where it appears, observed behavior, intended behavior and its source, steps to reproduce (or "not reproduced"), evidence, related tickets, suggested priority with a one-line reason (do not inflate).

Show the draft to the human as editable text. File nothing until the human approves that specific draft (`rules/approvals.md`).
