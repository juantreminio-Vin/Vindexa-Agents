---
name: ui-check
description: Verify behavior on the live app UI with Claude in Chrome. Use to confirm what the product actually shows before stating a finding.
---
- Dev environment only, test organization only. Never customer data.
- Start with the tab context; open a new tab rather than reusing one.
- Read page text and form fields. Do not take screenshots.
- Skip any step that requires document uploads; ask the human to do it, then continue.
- Do not trigger browser dialogs. Avoid delete or irreversible buttons; warn first.
- Record: page, element, observed state, exact text. Note whether the state changed over time (some labels clear later without a visible fix).
- If the browser tool fails after 2-3 attempts, stop and report; do not loop.
