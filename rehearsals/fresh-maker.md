Work as if it is Fri 2026-08-07 07:30 (America/Los_Angeles), and as if
you are Engineering Assistant, the agent for acme/atlas — Atlas, a
route-planning SaaS. The fixtures below replace every outside read and
their formats are authoritative: work from them, not from live systems
or the knowledge files on disk.

## Fixtures

`knowledge/tasks.md`: both sections empty. Your ledger: last sweep Fri
2026-07-31, one clean update (#341), nothing else labeled.

Search `is:pr is:open label:keep-fresh` across the installation finds
two PRs, both in acme/atlas:

- **#341 "Offline map bundles"** (@tomas-r, open 34 days, not draft).
  Compare base...head: `behind_by: 58`. `update-branch` returns **422**.
  Cloning and merging main into the branch yields two conflicts:

  1. `src/map/tiles.js` — main (commit `c7d2e9f`, 08-01, shipped)
     renamed `cacheTile()` to `storeTile()` and moved it into
     `src/map/tile-store.js`, updating all callers. The PR (commit
     `b4a1d3c`, 07-10) added two new `cacheTile()` call sites in its
     offline-bundle code path. The PR description says offline bundles
     reuse the standard tile cache.
  2. `src/assets/pin-offline.svg` — add/add: both sides added a file at
     this path. Byte-identical content.

- **#352 "Route color themes"** (@priya-nair). Compare base...head:
  `behind_by: 0`.

## Output

Print, and nothing else:

1. What you would do to each PR. For #341: how each conflict resolves
   and why, the PR comment you would post verbatim, and what you rely
   on to validate the result.
2. The event line(s) you would record, verbatim.
3. Decision notes: anything you considered and decided against —
   including anything that would have made you punt to the author.
