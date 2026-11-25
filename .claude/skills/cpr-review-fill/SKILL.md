---
name: cpr-review-fill
description: Fill the flagged "couldn't read" fields on a CPR review page (Check the reading) from the signed PDF. Use when the human gives a CPR review URL and the signed PDF. Stops before saving so the human reviews.
---
Runs in the main session, not in `ui-reader`: it types into the app and needs the human's yes. Values come from `evidence-reader`; never type a value it did not cite. Browser rules: `.claude/skills/ui-check`.

The AI reader sometimes leaves fields blank (usually one worker's fringe set, sometimes the Project, sometimes a whole pay row) even though the PDF prints them.

## Before touching the page
1. Confirm the project name and id in the URL and the week ending on the page.
2. Read the right-hand "N things to check" list (worker, field). Record it.
3. Send `evidence-reader` the PDF and the list. The signed PDF governs; the Excel only cross-checks. Fringe rates change week to week and differ by worker, so every flagged worker is read from this PDF.
4. Show the human the values with their PDF page or line. Missing values are reported as missing. Type nothing until the human says to.

## Entering values: refs, not screenshots
1. Load `browser_batch` and `find` in one ToolSearch call.
2. One `find` for the card's pencil buttons ("Edit Name", "Edit Straight hours", "Edit Fringe · Health"). These refs hold for the session; re-find only after a reload.
3. Per field, one `browser_batch`: click the previous field's Save ref, click this field's pencil ref, `type` the value (the box is already focused), then `find` "Save button inside the open inline editor (not the header)". The inline Save ref changes every time; find it every time. Ignore the header Save.
4. After the last Save, verify once with `get_page_text`: every field, the "Changed by you" / "Entered by you" tags, the flagged count.
5. Screenshot only when something is unclear (unknown input, a freeze, a dialog).

All inputs are plain text boxes (including Name, Classification, Apprentice as `Yes`). Leave fields the PDF leaves blank empty.

## Fallback: coordinates
- Use the "Type it" button or pencil on the card, click the box, type, press the Save next to it. Enter does not save.
- Layout shifts after every save. Zoom or screenshot before each click; never reuse coordinates.
- The page can freeze for seconds after a Save. Wait, call `tabs_context_mcp`, look again. Don't click blind.

## Traps
- **Never press "It's right" on a blank card.** It confirms the blank. If it happens, open the pencil, type the value, Save.
- **"Changed by you" is a draft.** Nothing is kept until "Continue to save"; leaving the page discards every edit. Never call a field saved because of that tag.
- The footer count ("Check the N flagged items to continue") should drop with each field. Watch it.
- Stop after the last field. "Continue to save", "Something's off", "Not right?", uploads, replacements and marking final are the human's. Both flag links leave the review in Needs review; they do not re-read the document.

## Reading the PDF
- IDOL form day columns run Mon to Sun; the app's pay period runs Thu to Wed. Map by the header.
- The apprentice percentage printed under the row checks out: percentage x journeyworker base = hourly wage.
- Check hours x rate = gross before typing.
- Identify workers by name, hours and net pay; two workers can share hours and rate.

## A worker printed at two rates in one week
The form can print one apprentice twice (a step from 70% to 75%). The app keeps one row per rate; the reader may drop both rows.
- Never type a blended or highest rate on one row.
- Row 1 goes in the existing card. Row 2 goes in a new card from "+ Add a worker the read missed": same name, SSN last 4, classification and apprentice flags; that row's hours, rates, fringe, gross, net and days.
- The added card shows "added by you" and the worker count rises by one. The reader's flag "the pay row was not joined" may stay; it does not clear by itself.
- Not yet proven that the added card joins the same worker. After the human saves, the CPR page should read N workers with N+1 rows and a Multi-rate chip. If it reads N+1 workers, say so and stop.

## Report
One line per field typed: worker, field, value, PDF source. Then the remaining flagged count and anything still needing a decision. A repeat of the unread-fringe pattern goes to `capture-knowledge` (week and pattern, no worker names) for the reader ticket.
