---
name: ui-check
description: Verify behavior on the live Vindexa dev app with Claude in Chrome, reading with the cheapest reliable method. Run it through the ui-reader subagent.
---
Run this through the `ui-reader` subagent (Haiku) so page text never enters the lead's context. Where pages are and how to reach them: `docs/app-map.md`.

## Scope
- Dev environment only. Writes happen only in the test organization (Meridian Infrastructure Partners), never on Juan's or Andres's projects unless asked. Never customer data.
- Uploads are the human's. Skip that step, say so, continue after.
- Any save, confirm, approve, mark final, invite, delete or settings change needs the human's yes for that action. Never use a read to work around it.
- Do not trigger browser dialogs.

## Tabs
- Load every Chrome tool you need in one ToolSearch call. Call `tabs_context_mcp` once at the start; never reuse a tab id from an earlier session.
- One tab per task. Reuse an open dev app tab only if it is not on a review or setup flow (`/review`, `?tab=setup`) and holds no unsaved input. Otherwise open one tab, reuse it for every page, close it when done.

## Read ladder (stop at the first rung that answers)
1. Not in the app? Linear, Drive and the repo through their own tools, never the browser.
2. `get_page_text`: the default for statuses, labels, counts, dates, names, tables.
3. `find`, or `read_page` with `filter: interactive` or a `ref_id`: one control or field and whether it is enabled.
4. `read_network_requests` filtered to the page's data call: exact numbers the text truncates. Read only; never replay requests or call Server Actions.
5. One zoomed screenshot: only when the answer is visual (colour, strike-through, chips, a PDF preview, whether a dialog appeared) or the text disagrees with what the human describes.

Batch `navigate` + `get_page_text` in one `browser_batch` (every item needs an explicit `tabId`).

## Accuracy (overrides saving tokens)
- After every navigation, confirm the project name and id in the URL and the breadcrumb. Two projects have near-identical names. A login redirect or a 404 reads as an empty page.
- Name what you expect, then look for exactly that. Absence of an error is not success.
- Reload before re-checking after the human changes something.
- Read both the checklist and the detail panel; report both if they disagree.
- Open collapsed sections before saying something is empty.
- Truncated or odd text: go up one rung, don't infer.
- Note whether a state changed over time (some labels clear later without a visible fix).
- The project's Audit Log tab shows what was actually saved and when (UTC). Use it for "I clicked and nothing happened".
- `form_input` on a checkbox can change the box without changing app state. Use real clicks and confirm the button label changed.
- Two or three failures on the same step: stop and report. Do not loop.

## Record
One line per element: `page | element | expected | observed state | exact text | method (if above page text) | changed over time?`
