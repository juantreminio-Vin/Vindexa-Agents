---
domain: fringe-payroll
status: seed
verified_on: never
verified_commit: none
depends_on: []
intent_source: Vindexa PWA business rules (project instructions) and consultant-benchmark notes; to be confirmed against code and UI
---
# Fringe handling

**Rules (intent, not yet verified against code):**
- A fringe benefit statement with no effective date is assumed to apply for the whole project duration. The start date on the matching "Authorization for Payroll Deduction" form sets the baseline timeline.
- Employer fringe contributions must be verified as bona fide before they credit against the required fringe, to avoid false underpayment warnings on certified payroll reports.
- Compliance compares the total package (base plus fringe). Paid fringe comes from the payroll; required fringe comes from the wage determination.
- Fringe arrives in several structurally different forms: separate hourly component columns that must be summed; columns omitted entirely; labeled values in a PDF; monthly dollar contributions that must be annualized to dollars per hour; attestation only (corroborating, no per-hour value). Never assume a single "fringe" column.
- A contractor's weekly payroll can be split across several files by labor agreement. These are different workers, not duplicates; the week's truth is the union. A signed PDF often twins a spreadsheet, so dedupe those.

**Open:** which of these the extractor handles today. Verify.
