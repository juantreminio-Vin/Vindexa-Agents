# Freshness stamps

Every flow file starts with frontmatter:

```yaml
---
domain: wage-determinations
status: seed | verified | stale
verified_on: 2026-11-01        # date a person or agent last checked it
verified_commit: <sha>         # vindexa-app develop commit it was checked against
depends_on:                    # code paths the flow relies on, for change detection
  - path/to/file-or-dir
intent_source: <regulation, spec, ticket or document name>
---
```

- `status: seed` means written from project rules, not yet checked against code or UI.
- A flow is **stale** when any `depends_on` path changed after `verified_commit`.
- Only a human-reviewed pull request may change `status` to `verified`. A freshness bump with no content change may be proposed automatically.

## Memory entries

One line each, in `memory.md`:

`- YYYY-MM-DD | source: <where it came from> | <correction, at its widest true scope> | status: unverified|verified`

Cap each file at about 40 lines. Dedupe before adding. Promote stable entries into flows and delete them from memory.
