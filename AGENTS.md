# AGENTS.md

This repo packages the `prs-reviews` agent skill. Agent skill that reviews GitHub PRs and posts a Requested Changes review with one inline comment per finding.

## Layout

- `skills/prs-reviews/SKILL.md`: the skill. Frontmatter holds `name` (equal to the folder name) and `description` (says when to use the skill).
- `README.md`: what the repo is and how to install it.
- `CHANGELOG.md`: notable changes, Keep a Changelog format.

## Rules for changes

- Write everything in EN-US. No em dashes or en dashes anywhere.
- Keep `SKILL.md` short and move long material to a `references/` folder.
- Do not add dependencies or tooling the skill does not need.
- Never commit secrets, tokens, personal data or machine-specific paths.
- Record every notable change under `## [Unreleased]` in `CHANGELOG.md` (Keep a Changelog format).
- Never push to `main`. Open a pull request. `main` needs one approval, and the repo owner can bypass it.
- Commit messages and PR titles use Conventional Commits with a scope, for example `fix(prs-reviews): tighten the trigger description`.

## Check before opening a PR

```bash
grep -rnE $'\xe2\x80\x94|\xe2\x80\x93' --exclude-dir=.git .   # em and en dashes: must print nothing
head -5 skills/*/SKILL.md                                       # frontmatter intact
```
