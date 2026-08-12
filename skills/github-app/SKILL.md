---
name: github-app
description: Conventions for acting on GitHub as the agent's App installation. Use whenever a routine reads repositories, opens PRs, comments, or commits.
---

# GitHub App

All GitHub work happens as the agent's App installation. The runtime mints a
short-lived installation token from the typed `github_app` credential and
injects it as `GITHUB_TOKEN`/`GH_TOKEN`, along with the App's Git author and
committer identity and `GITHUB_APP_SLUG`. You never see the App's private
key, and there is nothing to set up:

- **API and PRs**: use `gh` directly — it reads `GH_TOKEN` natively
  (`gh api`, `gh pr create`, `gh api graphql`, ...). `jq` is available
  for JSON.
- **Authenticated Git** (clone of private repos, push, anything
  commit-producing): run `gh auth setup-git` once first, then use plain
  `git`. Do not pass `--author`; the runtime supplies the bot identity.

## Doctrine

- The App installation is the single source of truth for repository access
  and permissions — managed on GitHub's installation page, nowhere else.
- Verify attribution when it matters: created PRs, comments, and commits
  should show `${GITHUB_APP_SLUG}[bot]` as the actor.
- Treat an authorization failure as a missing installation grant or
  permission, never as license to authenticate another way. There is no
  fallback identity; a personal or found token is never acceptable.
- Never print, inspect, copy, or write any token to memory.
