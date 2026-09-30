# skills

A collection of reusable skills for coding agents. Each skill is a folder with a `SKILL.md` (instructions plus frontmatter) and, optionally, a `references/` folder with supporting material.

## Available skills

| Skill | Description |
| ----- | ----------- |
| [`conventional-commits`](skills/conventional-commits/SKILL.md) | Write commit messages following Conventional Commits v1.0.0: types, scopes, breaking changes, and SemVer mapping. |

## Installation

Skills are installed with the [`skills`](https://www.npmjs.com/package/skills) CLI. No global install is needed; run it through `npx`.

Replace `<owner>/skills` with this repository's GitHub path.

### Install all skills

```sh
npx skills add <owner>/skills
```

### Install a single skill

```sh
npx skills add <owner>/skills --skill conventional-commits
```

## License

MIT. See [LICENSE](LICENSE).
