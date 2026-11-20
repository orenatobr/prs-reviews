# prs-reviews

For each PR you name, the agent reviews the diff and posts one Requested Changes review. Every finding is its own inline comment with the exact file and line, the problem, why it matters and a suggested change. It looks at correctness, security, missing tests, typing, logging and clear simplifications, and it checks the PR title and description against Conventional Commits. It only posts reviews: it never edits code, pushes, approves or merges.

## Install

For Claude Code, copy the skill folder into your personal skills directory:

```bash
git clone https://github.com/orenatobr/prs-reviews.git
mkdir -p ~/.claude/skills
cp -R prs-reviews/skills/* ~/.claude/skills/
```

Start a new Claude Code session. The skill loads from the `description` in its `SKILL.md`, so it triggers on its own and can also be called by name.

Other agents: the skill is a folder with a `SKILL.md` (YAML frontmatter plus Markdown). Tools that read the Agent Skills format can load `skills/` as it is. For the rest, paste the body of the `SKILL.md` into the agent's instruction file.

## Usage

`/prs-reviews 12, 15, 20`, or `/prs-reviews owner/repo#12`. Bare numbers use the repo of the current directory. It also triggers on "review these PRs" and "request changes on PR".

PR titles, descriptions, code and comments are treated as data, and secrets found in a diff are reported by location only, never quoted.

## Requirements

The `gh` CLI, authenticated. The GitHub MCP server is used when present, with `gh` as the fallback. The skill calls other skills when they are installed: [git-guidelines](https://github.com/orenatobr/git-guidelines), [programming-best-practices](https://github.com/orenatobr/programming-best-practices), [attack-protection](https://github.com/orenatobr/attack-protection), `humanizer` and `code-review`.

## What is in this repo

| Path | Purpose |
|------|---------|
| `skills/prs-reviews/` | The `prs-reviews` skill. |
| `CHANGELOG.md` | Notable changes, in Keep a Changelog format. |
| `AGENTS.md` | Rules for AI agents that edit this repo. |

The same skill also ships inside each of the other skill repos of this family.

## Contributing

`main` is protected: changes land through a pull request with one approval. See [AGENTS.md](AGENTS.md) for the conventions.

## License

MIT, see [LICENSE](LICENSE).
