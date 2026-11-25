---
name: ticket-draft
description: Recommend file, comment or skip for a verified finding, then draft the Linear ticket or comment. Use after bug-triage; produces an editable draft and files only on the human's go.
---
Preconditions: `live-checker` lines recorded; `verdict-reviewer` returned `holds` (or the draft states its weakening).

## 1. Recommend first
Say in a few lines which and why: **file** a new ticket, **comment** on an existing one (VIN-x), **skip** (by design; explain), or **for Andres** (a data or product question, not a ticket).

## 2. Draft
The text stands on its own: steps, URLs, project and contractor names, exact on-screen wording, exact numbers. Screenshots are backup, never the description.

Title: `<Screen>: <what goes wrong>` in plain words.

```
**User goal:** what the user is trying to do.
**Where:** menu path + project (org) + contractor/week, and a direct URL to the exact spot.
**Current behavior:** what happens, with steps and exact on-screen text.
**Expected behavior:** what should happen, and its source.
**Suggestion:** optional; offer options when it's the team's call.
**How to reproduce:** if the original state is gone, how a dev gets it back (sample file, test project, or function + input).
**Note:** code pointers, related tickets, what was NOT verified.
Screenshots (backup): one line per image saying what it shows.
```

Label: Bug, Feature or Improvement. Team: Vindexa. Link related tickets with `relatedTo`. Owner: `docs/owners.md`, confirmed by the last commit author `live-checker` reported. Don't cc anyone unless asked.

**Priority** (don't inflate; the human can override): Low for UX, wording, nice-to-haves. Medium when work is blocked or a real document can't be processed. High only when compliance numbers come out wrong.

Side findings go at the end as a separate list, not into the ticket.

## 3. Wait, then file
Show the draft. File only after the human's go for that draft (`rules/approvals.md`). Confirm in one line with the ticket id.

**Filing (Linear):** `save_issue` (team, assignee by email or user id via `list_users`, priority 1-4, labels, `relatedTo`).

**Attachments,** one at a time, within 60 s:
1. `prepare_attachment_upload` (issue, filename, contentType, exact size from `stat -c %s`).
2. `curl -X PUT --data-binary @file` with every signed header verbatim. Expect 200.
3. `create_attachment_from_upload`.
4. Append `![alt](assetUrl)` (images) or `[name](assetUrl)` (files) to the description with `save_issue`, patch op `append`.
Images in a comment: `prepare_file_upload` + PUT, then the markdown in `save_comment`. If the PUT gets a 403 from a proxy, network egress is off; tell the human.

## Observation logs
When the human shares a log, go item by item. After each decision, update that row's Linear column ("Filed: VIN-x", "Commented on VIN-x", "Not filed: <reason>", "For Andres") and keep the intro paragraph current.
