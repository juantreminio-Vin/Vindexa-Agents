---
name: project-audit
description: Run or continue a prevailing wage and apprenticeship audit for one named project without mixing evidence between projects. Use when the human names a project to audit or asks a question about a project's evidence.
---
Project files live in `local/` (gitignored): `local/_project-index.md` (slug, evidence folder id) and `local/<slug>/00_fact-sheet.md`, `01_source-manifest.md`, `02_findings-log.md`. New project: `project-intake` first.

## 1. Lock the project
- One project per task. If it isn't named, ask; don't guess from context.
- Read its index row and the three files.
- Open with one line: project, evidence folder, export or review cutoff date, number of open findings.

## 2. Scope
- Evidence is read by `evidence-reader`, scoped to that project's folder tree. Never cite a file from another project's folder.
- The manifest and fact sheet are indexes, not evidence. Every granular value (rate, hours, signature, page, date) comes from the source file, re-opened on each follow-up that asks for detail. Never answer from conversation memory.

## 3. Answer format
Answer / Summary · Evidence · Calculations · Gaps and Conflicts · EPC Clarification Required · Recommended Next Step.

Cite as `[exact filename.ext — page/sheet/row/cell]`. Statuses: Verified / Reported / Calculated / Conflicting / Not found / Inaccessible. A gap is not a violation.

## 4. Keep the project files current
When a variable is established, a finding confirmed or resolved, or a new discrepancy found, draft the exact edit (next F-number, status, cited evidence, EPC question). Show it; write it to `local/<slug>/` only after the human approves. Never delete a finding; close it with a resolution line and its source.

## 5. Generalize lessons
A lesson that holds beyond this project goes through `capture-knowledge`, without the project's name, links or data.
