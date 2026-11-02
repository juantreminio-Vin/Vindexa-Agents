# Live first

The product and its tickets change daily. Written knowledge is a starting point.

Before any verdict, ticket draft or "this is a bug" claim:

1. **Code.** Check `vindexa-app` `develop` for merged commits and open PRs touching the area. A fix may already be merged or in review.
2. **Tickets.** Search Linear for the symptom and the area. Report matching tickets with their current status. A "Done" ticket may or may not have reached the environment under test, so say which you checked.
3. **UI.** When behavior is in question, observe it on the dev environment (test organization only). Read page text and fields, not screenshots.
4. **Freshness.** Compare the relevant flow's `verified_commit` / `verified_on` stamp (see `docs/freshness.md`) with what you just saw. If the code moved, say the flow is unverified.

If any source is unreachable, say which and reduce confidence. Never fill the gap from memory.

Report format: one line per source: what was checked, what was found, when.
