---
name: status-refresh
description: Refresh the status of a list of observations or findings against Linear and the app repo. Use before reviewing a findings or observations log.
---
For each row, `live-checker` finds its Linear ticket (or searches for it), reads the current status, and checks `develop` for a merged fix or open PR. Batch several rows per brief. Report per row: previous status, current status, evidence (ticket, commit or PR), and whether the fix has reached the environment under test.

Rows with no ticket get the duplicate check from `ticket-draft`. Change nothing in Linear; return a table of proposed status updates for the human.
