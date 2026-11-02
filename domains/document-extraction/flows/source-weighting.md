---
domain: document-extraction
status: seed
verified_on: never
verified_commit: none
depends_on: []
intent_source: Vindexa PWA business rules (project instructions)
---
# Source weighting and misattribution protections

- **Hierarchy:** consultant reports, certified payroll reports and delivery documents outrank internal onboarding guides.
- **Semantic over literal:** search concepts, not just keywords ("boots on the ground" means mobilization).
- **Conflicts:** when documents conflict, surface all sources and highlight the discrepancy in the first response.
- **Zero-trust on metadata:** verify page counts, table structures, signatures and page-level citations against the file's structural metadata before stating them. When two documents share a title or overlapping content, cross-check each independently before combining.
- **Re-validate on follow-up:** a request for granular detail (signature, page number, dollar rate) based on an earlier turn is a new verification task, not a recall task.
- **Version comparisons:** separate identical core content, supplemental attachments and verification artifacts (e.g. presence or absence of handwritten signatures).
