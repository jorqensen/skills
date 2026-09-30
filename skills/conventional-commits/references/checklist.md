# Conventional Commits — Validation Checklist

Before finalizing a commit message:

- [ ] Starts with a type (`feat`, `fix`, `docs`, `refactor`, ...).
- [ ] Optional scope is a single noun in parentheses directly after the type, e.g. `(parser)`.
- [ ] `!` (if any) sits immediately before the colon.
- [ ] Colon followed by exactly one space, then the description.
- [ ] Description is imperative, present tense, concise, no trailing period.
- [ ] Header line ideally ≤ 72 characters.
- [ ] One blank line between header and body; one blank line between body and footers.
- [ ] Footers use `Token: value` or `Token #value`; tokens use `-` instead of spaces.
- [ ] Breaking changes are marked with `!` and/or an uppercase `BREAKING CHANGE:` footer.
- [ ] The commit contains one logical change (one type). Otherwise, split it.

## Header regex (single line)

```
^(feat|fix|docs|style|refactor|perf|test|build|ci|chore|revert)(\([a-z0-9._/-]+\))?!?: .+$
```

Adjust the type list to match the project. The spec itself allows any noun as a type.

## SemVer quick reference

- Contains `BREAKING CHANGE:` footer or `!` → **MAJOR**
- Otherwise `feat` → **MINOR**
- Otherwise `fix` → **PATCH**
- Anything else → no version bump by default
