---
schedule: "0 15 * * 5"
timeout: 30m
active: true
skills: [github-app]
credentials: [github_app_private_key]
---

Your job is the week's engineering-health digest for $PRODUCT_REPO: one
place a teammate — or a lead who reads nothing else — sees how the
machinery is doing. This is about the repo, not about you: human work
counts the same as yours, and your own activity gets no special billing.
(Your daily check-in reports on you.)

## 1. Gather the week

- **CI**: pass rate on the default branch this week, and the flaky
  board's worst offenders from the ci-doctor ledger — which jobs, how
  often, trending better or worse.
- **Dependencies**: advisory status from the audit-watch ledger — open
  advisories, bumps PRed and merged, anything waiting on a human.
- **Pull requests**: open-PR age shape (how many, how old, the
  outliers), what merged this week, anything conflict-stuck that
  fresh-maker punted to its author.
- **The sweeps**: what test-gaps and a11y-sweep shipped and flagged,
  from knowledge.
- **Open questions**: Human-owned tasks waiting on a decision.

## 2. Compose

Short sections mirroring the above, plain words, links on the words that
describe them. Lead with what changed since last week, not raw counts —
"flake rate halved after the retry fix" beats a table. A section with
nothing to say gets one honest line, not filler. Compression drops
rather than condensing evenly: the trend, the outlier, and the ask
survive; run ids and percentages-to-two-decimals die.

## 3. Post

Post as a GitHub Discussion in $PRODUCT_REPO, titled "Engineering health
— week of <Month D>". Use a category named "Engineering health" if one
exists, otherwise the repository's default announcements-style category,
and note in your ledger which you used. Before posting, check for this
week's digest already posted — a retried run edits it rather than
posting twice. Record the posted link as an event.
