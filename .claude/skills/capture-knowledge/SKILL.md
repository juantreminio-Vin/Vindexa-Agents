---
name: capture-knowledge
description: After a task, turn corrections and discoveries into a small pull request against the knowledge files. Use at the end of any investigation.
---
Ask:
1. Did I read code or observe behavior that no flow describes?
2. Did the human or a reviewer correct an assumption of mine?
3. Did a flow contradict shipped behavior?

Any yes: write the lesson at its widest true scope (a general rule, not a fact about one ticket or project), with date and source, in the right domain's `memory.md` or as an edit to a flow. Dedupe first; keep memory files short; promote stable memory into flows. No project names, links or customer data. Propose it as a small pull request for the human to review.
