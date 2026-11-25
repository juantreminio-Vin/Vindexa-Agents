# Dev app map

How to reach pages on the dev app (`https://dev.vindexa.ai`) by URL instead of clicking. Used by `ui-reader` through `.claude/skills/ui-check`.

Last checked: 2026-11 (migrated from the chat navigation skill). Re-verify the unverified tabs on first use and update this file through `capture-knowledge`.

## Verified URLs
- Project: `/projects/<projectId>?tab=overview | contractors | payroll | setup`. The setup wizard is `?tab=setup`; `/projects/<id>/setup` is a 404.
- Contractor on a project: `/projects/<projectId>/contractors/<contractorId>?tab=overview | payroll | apprenticeship`.
- Issue: `/issues/<issueId>`.
- Worker: `/workers/<workerId>?project=<projectId>`.
- CPR page: `/projects/<projectId>/payroll/<cprId>`; the review wizard adds `/review`.

## Seen but not yet tried as `?tab=` values
Project: `issues`, `wage-rates`, `workers`, `documents`, `apprenticeship`, `reports`, `audit-log`, `settings`. Contractor: `wages`, `workers`, `sampling`, `documents`. If one 404s, `find` the tab link and read its `href`.

## Ids
Never hardcode ids. Take them from the page: `find` returns a link's `href` (contractor rows, the week's CPR row).

## Moves, cheapest first
| Need | Do |
|---|---|
| A page with a known URL | `navigate` + `get_page_text` in one batch |
| Several known pages | one batch with all navigates and reads |
| A page known only by its link text | `find` the link, read the `href`, navigate to it |
| A collapsed section | `find` the header ("<Name> · 1/4 complete"), click its ref, wait 1 s, `get_page_text` |
| One button or field | `find` with a specific description |
| Something visual | one zoomed screenshot of the region |
| A huge page (Workers tab, long tables) | `find` or `read_page` with `ref_id`; don't read it whole |

## Clicking
- Click by `ref` from `find` (`computer`, `left_click`, `ref`), not by coordinates. Refs hold for one page load; re-`find` after any reload.
- After a click that loads data, wait 1-2 s before reading. A click that only expands a section needs 1 s.
- If a click lands somewhere unexpected, call `tabs_context_mcp` and re-read the URL before the next step.
