---
domain: wage-determinations
status: seed
verified_on: never
verified_commit: none
depends_on: []
intent_source: Vindexa PWA business rules (project instructions); to be confirmed against code and UI
---
# State wage lookup

**Trigger:** a project needs the applicable wage for a classification.

**Rules (intent, not yet verified against code):**
- **Illinois (IDOL):** search the Highway classification first, then All. If neither exists, default to the Federal wage. The system must never trigger or recommend a conformance request for missing state wages in Illinois.
- **New York:** wages are localized by township (partial counties), based on project management data. Updates annually on July 1, plus mid-year exceptions that are not announced.
- **Address disambiguation:** where a region has several wage variations, use the exact project site address to show a single applicable row and prevent duplicate trade categories.
- **County field:** must be the real county, not the project's name (see memory).

**Open:** which code paths implement each rule, and what the UI shows. Verify before relying.
