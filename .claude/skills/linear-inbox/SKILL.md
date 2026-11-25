---
name: linear-inbox
description: Walk the human's unread Linear notifications and handle them one by one. Use when the human asks to go through the Linear inbox.
---
1. `get_notifications` with `unreadOnly`.
2. Show a table: ticket, what happened, needs the human? (test / decide / FYI / already done).
3. Go one by one: explain in plain words (3-5 sentences, no code), offer to retest (`retest-fix`) or comment (`ticket-draft`).
4. `mark_notification` read only once an item is handled.
5. Finish with what was done and what's left.
