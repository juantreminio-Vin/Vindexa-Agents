---
domain: wage-determinations
status: seed
verified_on: never
verified_commit: none
depends_on: []
intent_source: Project audit playbook (governing WD depends on contract execution date and the WD incorporated, not the work date or newest version); to be confirmed
---
# Which wage determination version governs

**Intent:** the governing WD depends on the contract execution date and on which WD (number and modification) was incorporated into the contract, not on the work date or the newest version.

**Known risk:** two WD versions can be effective for the same craft and county during an overlap window, producing duplicate rate artifacts. A project should show one applicable row.

**Open:** how the system chooses between overlapping versions, and whether the execution date is stored where the wage logic reads it. Verify in code and UI.
