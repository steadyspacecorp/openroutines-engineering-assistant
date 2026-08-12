Work as if it is Fri 2026-08-07 08:00 (America/Los_Angeles), and as if
you are Engineering Assistant, the agent for acme/atlas — Atlas, a
route-planning SaaS (JavaScript, npm, CI in `ci.yml`). $PRODUCT_REPO is
acme/atlas. The fixtures below replace every outside read and their
formats are authoritative: work from them, not from live systems or the
knowledge files on disk.

## Fixtures

Your ledger: last run Thu 2026-08-06 08:00; runs through 4210 diagnosed.
The flaky board:

```markdown
## Flaky board

- test/integration/route-share.test.js "shows shared route to viewer" —
  2 confirmations (07-22, 07-29), both timing: viewer poll races the
  share write. Re-runs passed.
```

`knowledge/tasks.md`: `## Agent-owned` and `## Human-owned` both empty.

Failed workflow runs on acme/atlas, branch main, since your cursor:

- **Run 4213** (`ci.yml`, Thu 08-06 15:12, commit `d4e5f6a` "Fix typos
  in README and importer docs"). Failed step: `Run npm test`. Log tail:

      ✕ route-share › shows shared route to viewer (timeout 5000ms)
      expected share banner, received loading spinner

  The commit touches only `README.md` and `docs/importing.md`.
- **Run 4221** (`ci.yml`, Fri 08-07 06:40, commit `8a9b0c1` "Add
  vehicle profiles to route costing", author @jo-medina). Failed step:
  `Run npm test`. Log tail:

      ✕ costing › vehicle-profile › applies axle weight to toll roads
      TypeError: Cannot read properties of undefined (reading 'axleWeight')
        at costForSegment (src/costing/vehicle-profile.js:41)

  The commit adds `src/costing/vehicle-profile.js` and its test file.

Re-run results, if you choose to re-run: run 4213's failed jobs pass on
re-run; run 4221's fail identically.

## Output

Print, and nothing else:

1. Your verdict per run, with what you did about it: the re-runs you
   issued, the flaky-board update verbatim, and any Human-owned task
   verbatim.
2. Every event line you would record, verbatim.
3. Decision notes: anything you considered and decided against.
