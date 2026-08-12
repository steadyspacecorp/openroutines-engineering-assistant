Work as if it is Fri 2026-08-07 15:00 (America/Los_Angeles), and as if
you are Engineering Assistant, the agent for acme/atlas — Atlas, a
route-planning SaaS. $PRODUCT_REPO is acme/atlas. The fixtures below
replace every outside read and their formats are authoritative: work
from them, not from live systems or the knowledge files on disk.

## Fixtures

The week in acme/atlas (Mon 08-03 → Fri 08-07):

- **CI, default branch**: 47 runs, 41 passed (87%; last week 74%).
  The ci-doctor ledger's flaky board: `route-share › shows shared route
  to viewer`, 3 confirmations (07-22, 07-29, 08-06), all timing.
  One real break: vehicle-profile costing (`8a9b0c1`, Fri morning) —
  diagnosed, Human-owned task open, unclaimed.
- **Dependencies** (audit-watch ledger): fast-xml-parser bumped for
  GHSA-9v2f-6qxw — PR #356 open since Wed, waiting on lockfile
  regeneration and review. Nothing else outstanding.
- **Pull requests**: 12 open; median age 3 days; the outlier is
  [#341 "Offline map bundles"](https://github.com/acme/atlas/pull/341)
  (34 days, `keep-fresh`) — brought current this morning, two conflicts
  resolved toward main's tile-store rename, author reviewing the
  resolution. Merged this week: 9, including the route summary redesign
  and tiered pricing.
- **Sweeps** (knowledge): a11y-sweep opened two PRs (share-button name,
  heading order — merged Thu; map-thumb alt text — open) and flagged
  the `.summary-eta` contrast for a human. test-gaps opened
  [#357 "Tests for pricing tiers"](https://github.com/acme/atlas/pull/357)
  (open) and flagged the last-day proration mismatch against
  docs/pricing.md.
- **Open Human-owned tasks**: the vehicle-profile break (unclaimed);
  the contrast decision; the proration mismatch (code vs.
  docs/pricing.md).

The goal board notes involvement in "Q3 reliability: flake rate under
2%" and "Billing revamp ships safely".

Discussion categories in acme/atlas: "Announcements", "General", "Q&A".
No "Engineering health" category; no prior digest exists.

## Output

Print, and nothing else:

1. The Discussion you would post: category, title, and full body,
   verbatim.
2. The event line recording it, verbatim.
3. Decision notes: what you left out of the digest and why.
