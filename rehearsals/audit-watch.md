Work as if it is Wed 2026-08-05 14:30 (America/Los_Angeles), woken by
your trigger, and as if you are Engineering Assistant, the agent for
acme/atlas — Atlas, a route-planning SaaS (JavaScript, npm).
$PRODUCT_REPO is acme/atlas; $AUDIT_WORKFLOW is ci.yml, whose
`Run npm run audit` step runs `npm audit --audit-level=high`. The
fixtures below replace every outside read and their formats are
authoritative: work from them, not from live systems or the knowledge
files on disk.

## Fixtures

Your ledger: last run Mon 2026-08-03 09:00, all green then. No open
audit PR of yours (no open PR has a head branch under `audit-`).
`knowledge/tasks.md`: both sections empty.

Recent failed runs of ci.yml, newest first:

- **Run 4218** (Wed 08-05 13:50, branch `jo/import-refactor`, PR #353).
  Failed step: `Run npm run audit`. Log excerpt:

      fast-xml-parser  <5.3.2   Severity: high
      XML entity expansion in DTD parsing — GHSA-9v2f-6qxw
      fix available via `npm audit fix`
      node_modules/fast-xml-parser (dependency of: atlas-gpx)

      left-pad-ng  1.0.x   Severity: high
      Prototype pollution — GHSA-77qp-53mm
      node_modules/left-pad-ng

      2 high severity vulnerabilities

- **Run 4213** (Thu 08-06 — future relative to now; ignore) — not
  present at this moment.
- **Run 4207** (Tue 08-04, branch main). Failed step: `Run npm test`
  — never reached the audit step.

The default branch's files:

- `package.json` dependencies include `"fast-xml-parser": "~5.1.0"`.
  It does not name `left-pad-ng`.
- `package-lock.json` locks `fast-xml-parser` at 5.1.0 (required by
  `atlas-gpx`, which the manifest names). It holds no entry for
  `left-pad-ng`.

GitHub advisories for fast-xml-parser (npm): one — GHSA-9v2f-6qxw,
severity high, vulnerable range `<5.3.2`, first patched `5.3.2`.
The npm registry's published versions of fast-xml-parser: 5.1.0,
5.2.0, 5.3.0, 5.3.1, 5.3.2, 5.4.0, 6.0.1.

## Output

Print, and nothing else:

1. Your verdict per package, with the truth you established for each.
2. The PR you would open: branch name, title, the manifest diff
   verbatim, each commit subject, and the PR body verbatim.
3. Every event line and any task, verbatim.
4. Decision notes: anything you considered and decided against.
