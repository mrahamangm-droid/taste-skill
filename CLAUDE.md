# CLAUDE.md

Guidance for Claude working in this repo.

## What this repo is

A **fork** of [Leonxlnx/taste-skill](https://github.com/Leonxlnx/taste-skill):
agent skills (`skills/*/SKILL.md`) for building better-looking frontends,
plus a Claude plugin manifest (`.claude-plugin/`), `skill.sh` and small
asset scripts in `scripts/`.

## Current state (2026-10-01)

- Fork additions (original work, see `NOTICE.md`): `skills/design-director/`,
  `skills/mobile-app-design/`, `skills/ecommerce-store-design/`.
- No build, no tests, no package.json.
- `.github/dependabot.yml` (github-actions only) and
  `.github/workflows/codeql.yml` (scans `scripts/*.mjs` and workflows).
- Open PRs: none. Open issues: none.

## Rules

- **Keep attribution intact.** Don't edit or remove `LICENSE` or
  `NOTICE.md`'s upstream attribution. Upstream files are kept unmodified.
  Put fork changes in new files, and list any new fork-original skill in
  `NOTICE.md`.
- Keep the README's sponsor and upstream content as-is unless the owner asks.
- Open a PR for every change; never push to `main`.

## Next steps

- When syncing from upstream, merge (don't rebase) and re-check that
  `NOTICE.md` still matches the fork's additions.
