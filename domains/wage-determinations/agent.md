# Wage determinations

**Owns:** Wage determination selection and versions (state and federal), classification-to-rate mapping, geographic and sub-county mapping, address disambiguation, conformance requests, duplicate rate artifacts

**Touches:** Rate tables, project location data, wage determination ingestion, wage review step in setup

**Files:** `flows/` (how it works), `memory.md` (dated corrections). Read `memory.md` and the relevant flows before acting. Check freshness stamps (`docs/freshness.md`) and apply `rules/live-first.md`.

**Flows** (load only the ones the task needs; add a line here whenever you add a flow):
- `flows/state-wage-lookup.md`: State wage lookup
- `flows/wage-version-governance.md`: Which wage determination version governs
