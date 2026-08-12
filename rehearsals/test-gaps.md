Work as if it is Thu 2026-08-06 10:00 (America/Los_Angeles), and as if
you are Engineering Assistant, the agent for acme/atlas — Atlas, a
route-planning SaaS (JavaScript, Jest). $PRODUCT_REPO is acme/atlas.
The fixtures below replace every outside read and their formats are
authoritative: work from them, not from live systems or the knowledge
files on disk.

## Fixtures

Your ledger: last run Tue 2026-08-04 10:00; merged PRs through #347
judged. `knowledge/tasks.md`: both sections empty.

The goal board (steady-inbox ledger, refreshed 2026-08-03):

```markdown
## Goal board (refreshed 2026-08-03)

- Billing revamp ships safely — tiered pricing and proration land with
  test coverage to match; owner Priya Nair; involvement: contributor;
  due 2026-09-15; on track; latest: tiers merged behind flag (08-04)
- Q3 reliability: flake rate under 2% — owner Priya Nair; involvement:
  contributor; due 2026-09-30; on track; latest: retry helper shipped
  (07-31)
```

knowledge/context.md: "Jo — owns the gpx-importer test backfill, in
flight this week (08-05). Firm."

Merged PRs in acme/atlas since your cursor:

- **#348 "Tiered pricing for teams"** (@jo-medina, merged 08-04). Adds
  `src/billing/tiers.js` — `tierFor(seatCount)` (boundary thresholds at
  5, 25, 100), `prorate(change, daysLeft, cycleLength)` (upgrades
  charge immediately, downgrades credit next cycle, zero-day edge), and
  `applyTierChange()` wiring both. No test files in the diff. The
  existing suite has `test/billing/invoice.test.js` using a
  `buildTeam()` helper from `test/support/factories.js`.
- **#350 "Extract costing constants"** (merged 08-05) — moves constants
  into `src/costing/constants.js`; `test/costing/` passes unchanged and
  covers every moved value.
- **#344 "GPX importer hardening"** (merged 08-03) — importer edge
  cases, no tests in the diff.

Open PRs: **#355 "gpx importer: test backfill"** (@jo-medina, open,
adds `test/import/gpx.test.js`).

Existing tests relevant to #348: none reference `tiers.js` or
`prorate`. The pricing behavior in `tiers.js` matches the tier table in
`docs/pricing.md`, except: `prorate` returns a negative charge for a
downgrade on the final day of a cycle, where `docs/pricing.md` says
downgrades never produce a charge or credit inside the last day.

## Output

Print, and nothing else:

1. Where you chose to work and where you stood down, tied to the goal
   board and context.
2. The test PR you would open: branch name, title, the test file
   verbatim, and the PR body naming what's covered and what you left
   uncovered and why.
3. Anything you would flag rather than test, worded as you would record
   it.
4. Every event line and ledger update, verbatim.
