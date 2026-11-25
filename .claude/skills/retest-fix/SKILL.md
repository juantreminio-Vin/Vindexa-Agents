---
name: retest-fix
description: Retest a fixed Linear ticket on the dev app and report pass or fail per step. Use when a ticket moves to review or done, or the human asks to retest one.
---
1. Read the ticket's last comments for the dev's test steps and the PR. Have `live-checker` confirm the PR is merged on `develop`.
2. Run the steps through `ui-reader` in the test organization.
3. Report pass or fail per step in plain words with exact numbers.
4. **Pass:** offer a short comment ("Retested on dev, <project>, passes: ...") and closing the ticket.
5. **Fail:** draft a full comment on the same ticket (steps, URLs, numbers, expected vs actual, screenshots as backup).
6. New asks go in their own ticket (`ticket-draft`), not into a comment on a ticket that will close.

Comments and status changes are drafts until the human approves each one (`rules/approvals.md`).
