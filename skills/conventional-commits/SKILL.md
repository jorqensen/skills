---
name: conventional-commits
description: Write git commit messages following the Conventional Commits v1.0.0 specification. Use when creating, reviewing, or rewriting commit messages, or when asked about commit message format, types, scopes, breaking changes, or semantic versioning of commits.
---

# Conventional Commits v1.0.0

A lightweight convention for commit messages that yields an explicit history, enables automated changelogs, and maps directly onto Semantic Versioning.

## Format

```
<type>[optional scope][!]: <description>

[optional body]

[optional footer(s)]
```

## Rules

The key words MUST, SHOULD, MAY follow RFC 2119.

1. Commits MUST be prefixed with a **type** (noun such as `feat` or `fix`), followed by an optional scope, an optional `!`, and a REQUIRED colon and space.
2. `feat` MUST be used when a commit adds a new feature to the application or library.
3. `fix` MUST be used when a commit represents a bug fix.
4. A **scope** MAY follow the type. It is a noun describing a section of the codebase, in parentheses: `fix(parser):`.
5. A **description** MUST immediately follow the colon and space. It is a short summary of the change.
6. A longer **body** MAY follow the description, separated by one blank line. It is free-form and may span multiple paragraphs.
7. One or more **footers** MAY follow the body, separated by one blank line. Each footer is a word token, then either `: ` or ` #`, then a string value (git trailer format).
8. A footer token MUST use `-` in place of whitespace (e.g. `Acked-by`). The exception is `BREAKING CHANGE`.
9. A footer value MAY contain spaces and newlines; parsing ends when the next valid footer token/separator pair is seen.
10. **Breaking changes** MUST be indicated in the type/scope prefix with `!`, or as a footer entry, or both.
11. As a footer, a breaking change MUST be `BREAKING CHANGE: <description>`.
12. If `!` is used, the `BREAKING CHANGE:` footer MAY be omitted, and the commit description SHALL describe the breaking change.
13. Types other than `feat` and `fix` MAY be used (e.g. `docs: update ref docs`).
14. Units of information MUST NOT be treated as case sensitive, except `BREAKING CHANGE`, which MUST be uppercase.
15. `BREAKING-CHANGE` MUST be synonymous with `BREAKING CHANGE` when used as a footer token.

## Semantic Versioning mapping

| Commit                                   | SemVer bump |
| ---------------------------------------- | ----------- |
| `fix`                                    | PATCH       |
| `feat`                                   | MINOR       |
| Any type with `!` or `BREAKING CHANGE:`  | MAJOR       |

## Types

Only `feat` and `fix` are defined by the spec. The following are common additional types (from the Angular convention) and are widely used:

| Type       | Use for                                                   |
| ---------- | --------------------------------------------------------- |
| `feat`     | A new feature                                             |
| `fix`      | A bug fix                                                 |
| `docs`     | Documentation-only changes                                |
| `style`    | Formatting, whitespace; no code meaning change            |
| `refactor` | Code change that neither fixes a bug nor adds a feature   |
| `perf`     | A change that improves performance                        |
| `test`     | Adding or correcting tests                                |
| `build`    | Build system or external dependencies                     |
| `ci`       | CI configuration and scripts                              |
| `chore`    | Other changes that don't modify src or test files         |
| `revert`   | Reverts a previous commit                                 |

If the project defines its own types or scopes, follow the project's.

## Writing guidance

- Use the imperative, present tense: "add", not "added" or "adds".
- Keep the description short (aim for ≤ 72 characters for the whole first line), lowercase start, no trailing period.
- Pick the single most fitting type. If a commit spans multiple types, split it into multiple commits.
- Use the body to explain **what and why**, not how.
- Put issue references and metadata in footers (`Refs: #123`, `Closes: #45`, `Reviewed-by: Z`).
- Mark breaking changes explicitly and describe the migration path.

## Examples

```
docs: correct spelling of CHANGELOG
```

```
feat(lang): add Polish language
```

```
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```

```
feat!: send an email to the customer when a product is shipped
```

```
feat(api)!: send an email to the customer when a product is shipped
```

```
chore!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```

More examples, including bad ones and a checklist, are in the `references/` folder:

- [references/specification.md](references/specification.md) — the full spec, rules and FAQ
- [references/examples.md](references/examples.md) — good and bad commit messages with explanations
- [references/checklist.md](references/checklist.md) — quick validation checklist and regex

## Workflow

1. Inspect the staged changes (`git diff --staged`).
2. Choose the type (and scope, following existing project history via `git log`).
3. Write a concise imperative description.
4. Add a body and footers only when they add value.
5. Add `!` and/or a `BREAKING CHANGE:` footer if the public API/behavior breaks.
6. Verify against [references/checklist.md](references/checklist.md).
