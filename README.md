<img src="avatar.svg" alt="" width="96" align="right">

An assistant for engineering teams, built on [OpenRoutines](https://openroutines.dev).
It keeps the machinery of shipping healthy — the diagnosis, upkeep, and
sweeps nobody has time for: CI failures arrive pre-diagnosed, dependency
advisories get patched, long-running branches stay mergeable, and
shipped code gets swept for missing tests and accessibility failures.

Everything it does is visible where you already work: diagnosed tasks
and focused PRs on your repo, a weekly health digest in Discussions, and
a daily check-in in [Steady](https://runsteady.com) — where you can also
talk back: reply to its check-in and the ask becomes its task; assign it
a goal and its sweeps pursue the goal over time.

## The routines

| Routine | What it does |
|---|---|
| ci-doctor | Classifies failures on the default branch — flaky (re-run passed, boarded) or real (task filed with the diagnosis). Never guesses at fixes. |
| audit-watch | When the dependency scanners go red, establishes the truth from the advisories and opens a manifest-only bump PR; CI or a human regenerates the lock. |
| fresh-maker | Keeps PRs labeled `keep-fresh` current with their base, resolving conflicts the way the author would have; merge, never rebase. |
| a11y-sweep | Audits recently shipped frontend code for static WCAG failures. Mechanical fixes become PRs citing the criterion; judgment calls get flagged. |
| test-gaps | Writes the tests that shipping skipped, one focused PR per area — goal-aware, and safe unattended because a wrong test fails CI. |
| repo-health | Posts the week's engineering-health digest — CI trend, flaky board, advisory status, PR age — as a GitHub Discussion. |
| steady-check-in | The agent's own daily standup in Steady: what it did, what it will do, where it needs a human. |
| steady-inbox | The inbound half: answers comments, turns "go ahead" into its own tasks, tracks teammates' overlapping work, and keeps its goal board current. |

Each routine states its own boundary between what it fixes and what it
flags. The agent makes mechanical, verifiable changes itself and files a
task for anything that needs judgment — read any file in `routines/` to
see exactly what it may touch.

## Take it for a spin

Every working routine has a rehearsal scenario in `rehearsals/` — one
consistent fictional product with a week of CI failures, an advisory, a
conflicted branch, and shipped code missing tests. A fixtured rehearsal
strips all credentials and never writes anything, so this works before
any setup beyond the CLI and Docker:

```bash
openroutines routines run ci-doctor --rehearse
openroutines routines run audit-watch --rehearse
openroutines routines run test-gaps --rehearse
```

Each prints exactly what it would have done — the diagnosis it would
file, the PR it would open, the flag it would raise and why. Edit a
prompt, rehearse again, watch the judgment change. That's the
[write–rehearse–run loop](https://openroutines.dev/docs/local-development/)
you'll use for routines of your own.

## Setup

You need the [OpenRoutines CLI](https://openroutines.dev/docs/getting-started/)
and about ten minutes.

1. **Use this template** to create your agent's repository, and clone it.
2. `openroutines configure` — fills in the owner, timezone, and model,
   and generates the `master.key` that encrypts credentials (back it up;
   it stays out of git).
3. Set `repo` in `openroutines.yml` to your new repository's URL, then
   set the variables: your product repository and
   the workflow that runs your dependency scanners — and the same values
   in the trigger URLs of `routines/ci-doctor.md` and
   `routines/audit-watch.md`.
4. GitHub, as an App — so the agent's PRs, comments, and commits are its
   own, not yours, and each run gets a short-lived installation token
   instead of a long-lived personal one. Create a GitHub App
   ([Settings → Developer settings → GitHub Apps](https://github.com/settings/apps/new)):
   name it after your agent, deactivate the webhook, and grant
   repository permissions Contents, Issues, Pull requests, Discussions,
   and **Actions** (read and write — that's how ci-doctor re-runs a job
   to test flakiness). Install it on your product repo, then put the App
   ID in `openroutines.yml` and store the key:
   `openroutines credentials set github_app_private_key < your-app.private-key.pem`
5. Steady, so the agent can check in like a teammate — and take
   assignments: create an account for the agent, mint it a personal
   access token, then `openroutines credentials set steady_token`.
   Verify the wiring:
   `OPENROUTINES_LOG_LEVEL=warn openroutines routines run steady-verify --no-knowledge`
6. `openroutines check`, commit, and
   [deploy](https://openroutines.dev/docs/deploying/).

This is your teammate now — rename it in `openroutines.yml`, retune the
schedules, and edit the routine prompts like any other file in your
repo. Reply to its check-in ("go ahead and make that PR") and the next
relevant run picks it up; put it on a goal and its sweeps work toward it
week over week. Prefer the check-in in chat instead? Swap the plugin:
`openroutines plugin add steadyspacecorp/openroutines-plugins --path slack-report`
(or `--path discord-report`).

## Working on this agent

```bash
openroutines status                # what the agent has and still needs
openroutines sync                  # pull the latest knowledge; read the files under knowledge/
openroutines routines new <name>   # add a routine
openroutines routines run <name>   # real run; knowledge writes discarded (--write-knowledge settles)
openroutines check                 # validate everything; run it in CI
```

Deploying, updating, and everything else:
[OpenRoutines documentation](https://openroutines.dev).
