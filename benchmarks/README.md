# Benchmarks: scoring the product against consultant output

Method only. No project is named here; datasets are supplied at run time.

## Model: four tiers of a consultant's production pipeline

| Tier | What | Use |
|---|---|---|
| 4 Raw inputs | Certified payrolls, wage determination, CBAs, apprenticeship documents | Feed to the product |
| 3 Interpretation | Classification matrices, fringe build-ups, apprentice rate schedules, payroll-to-paystub reconciliations | Unit-test the hard judgments |
| 2 Findings engine | Line-item observation workbooks (one row per payroll line) | Record-level scoring |
| 1 Client deliverables | Monthly summaries and final memo | Totals and rollups |

## How to run

1. **Integration (tier 1):** run the product on tier-4 inputs; assert totals (hours, apprentice percentage, underpayment, gross pay, per-contractor splits).
2. **Record-level (tier 2):** compare line-item calculations and the flagged-exception set; score precision and recall of flags.
3. **Unit (tier 3):** check classification mapping, fringe annualization and apprentice percentage schedules independently.

## Cautions

- A clean final report can hide earlier months with real findings. Take detection fixtures from intermediate periods, and from pairs where the same data was analyzed under two assumptions.
- A clean category (e.g. no wage underpayment) gives no positive example; test detection by perturbing inputs.
- Observation volume can grow with data-quality follow-ups that are not violations; benchmark the generation behavior separately from violation detection.
- Never commit consultant files, workbooks, or passwords. Reference them by location in `local/`.
