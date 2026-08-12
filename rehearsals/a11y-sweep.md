Work as if it is Wed 2026-08-05 09:30 (America/Los_Angeles), and as if
you are Engineering Assistant, the agent for acme/atlas — Atlas, a
route-planning SaaS (React frontend). $PRODUCT_REPO is acme/atlas. The
fixtures below replace every outside read and their formats are
authoritative: work from them, not from live systems or the knowledge
files on disk.

## Fixtures

Your ledger: last sweep Wed 2026-07-29; PRs through #347 audited.

`knowledge/tasks.md`:

````markdown
```
- [ ] `task-YYYYMMDD-<n>` what must be done — context. (raised by <routine> YYYY-MM-DD)
```

## Agent-owned

- [ ] `task-20260803-2` add accessible names to the dashboard map
  thumbnails — flagged 07-29, Priya replied "go ahead and make the PR".
  Thumbnails render in src/components/MapThumb.jsx. (raised by
  steady-inbox 2026-08-03)

## Human-owned
````

The goal board (steady-inbox ledger, refreshed 2026-08-03) lists
nothing a11y-specific. knowledge/context.md notes: paths under
`src/admin/` are internal-only tooling customers never see.

Merged PRs in acme/atlas since your last recorded run:

- **#348 "Tiered pricing for teams"** (merged 08-04) — backend only:
  `src/billing/tiers.js` and tests. No frontend files.
- **#351 "Route summary redesign"** (@tomas-r, merged 08-05) — touches
  `src/components/RouteSummary.jsx` and `src/styles/summary.css`. The
  component as merged:
  - a share button rendering only an SVG icon, no text, no `aria-label`
  - headings jump from `<h2>Route summary</h2>` to
    `<h4>Waypoints</h4>`; no h3 anywhere in the file
  - a `.summary-eta` timing label styled `color: #9aa0a6` on a white
    card background
- **#349 "Admin: bulk user import"** (merged 08-04) — touches only
  `src/admin/UserImport.jsx`.

`src/components/MapThumb.jsx` (for the task): renders
`<img src={thumbUrl(route)} />` in a loop, no `alt` attribute; the
route's name is available as `route.name`.

## Output

Print, and nothing else:

1. Each fix PR you would open: branch name, title, the changed JSX/CSS
   verbatim, and the PR body citing the criterion.
2. Anything you would flag for human review instead, worded as you
   would record it.
3. The ledger entries and every event line, verbatim.
4. Decision notes: anything you considered and decided against.
