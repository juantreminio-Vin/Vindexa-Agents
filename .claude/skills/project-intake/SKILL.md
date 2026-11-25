---
name: project-intake
description: Set up a new project's working notes from the template. Use when the human names a new project to audit or test.
---
Everything goes in `local/` (gitignored), never in the tracked tree. Never store project data or links in tracked files.

1. Get the evidence folder from the human. Have `evidence-reader` walk the full tree (`parentId` searches) and read any README or inventory files first.
2. Copy `templates/project/` to `local/<slug>/`.
3. Fill `00_fact-sheet.md`. Every value gets a source and a status: Confirmed, Reported (stated but unconfirmed) or Conflicting (list the sources). Blank means not established.
4. Fill `01_source-manifest.md`: folder map with ids, key files with ids, counts per contractor and document type, data-quality notes. Page counts stay "unverified" until counted.
5. Start `02_findings-log.md` with any discrepancies seen while inventorying, labeled open observations, not violations.
6. Add a row to `local/_project-index.md`: slug, project name, evidence folder id, cutoff date.
7. Tell the human which values are Reported or Conflicting and need review.

If a lesson generalizes, route it through `capture-knowledge` without the project's identity.
