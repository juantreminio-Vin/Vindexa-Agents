---
name: source-inventory
description: Keep a file-by-file source checklist when rebuilding a project in the app from its Drive folder or comparing it with a reference project. Use before calling a phase done, saying a file doesn't exist, or explaining a difference between projects.
---
Why: on a past rebuild, roster letters and a dozen payroll files for two of three payroll streams sat in the shared Drive the whole time and were never uploaded. A phase was marked done with one stream filed, an open item fell off the plan, and one search using the app's word ("roster letter") instead of the file names ("Davis Bacon Ltr", "DOL Certification") was taken as proof the document didn't exist. Each rule closes one of those gaps.

## Rules
1. **Inventory first.** The Drive inventory is the checklist. Every customer-side file gets one status: uploaded, duplicate, out of scope (with reason), or to do. A phase is done only when every file in its scope has a status.
2. **"Done" says what was checked.** For payroll: every stream for every week, plus workers and hours per contractor matched against the reference project.
3. **"Not found" says where and how you searched.** Search by the file-name patterns in the project's document map and by folder listing, not only by the app's vocabulary. One empty search proves nothing.
4. **Inputs before outputs.** When a figure differs from the reference project, first diff the two document lists and the workers and hours per contractor. Only then look at engine logic.
5. **Open items carry forward.** A new plan lists every open item from earlier notes, dashboards, upload guides and the parking lot, or closes it in writing.
6. **Standing rules.** Customer-side files only; label each file customer-side, consultant-origin or origin unknown. The human does every upload and data-changing click. Never modify the shared Drive; give links, don't download folders. If the reference project has a file ours lacks, the reference copy may be used, and each use is logged in the comparison report (what, which file, from where, why).

## Procedure
**A. Drive inventory** (start of a session and before closing any phase). Through `evidence-reader`:
1. Folder tree from the project's document map in `local/<slug>/`, or walk it with `parentId` searches.
2. List files with `search_files` on several `parentId`s per call (`excludeContentSnippets: true`, `pageSize: 100`). Parse large results in Python, never by eye.
3. Write a CSV to `local/<slug>/`: path, title, size, created date, link, origin label, duplicate-of (same title and size). Skip the consultant results folder except as an answer key.

**B. What each project in the app holds.** Through `ui-reader`:
1. Documents tab is paginated (25 per page). Collect every row in one read-only pass, waiting for the first row to change between pages.
2. Normalize names: lower case, collapse spaces, drop a trailing " (1)", cut at " — week ending" and " · pp.".
3. Weeks, workers and hours per contractor from the Apprenticeship tab's contractor table.

**C. Compare.**
1. Each Drive file: in ours, in the reference only, or in neither.
2. Group by what it feeds: payroll per stream and week, fringe, apprenticeship proof (DOL certs, Davis-Bacon letters, ETA-671s, standards, registration), wage rates, CBAs, conformance requests, paystubs.
3. Flag any week where a stream is missing; confirm with workers and hours per contractor.
4. Spot-check three "missing" files on the Documents tab before reporting.

**D. Record.** A "Source inventory" section in the running notes: counts, missing files by purpose, the phase checklist status (reopen any phase with files still to do). The comparison report says which differences come from missing inputs. Give the human the CSV and, when uploads are needed, the Drive links grouped by upload spot, in the order that moves the numbers most.

## Report
One line per check: expected, found, how checked (Drive crawl, Documents tab, Apprenticeship tab, file opened). Name matches stay "by file name" until the file is opened or seen in the app.
