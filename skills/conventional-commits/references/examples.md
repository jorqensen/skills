# Conventional Commits — Examples

## Valid examples

### Description only

```
docs: correct spelling of CHANGELOG
```

### With scope

```
feat(lang): add Polish language
```

### With body and multiple footers

```
fix: prevent racing of requests

Introduce a request id and a reference to latest request. Dismiss
incoming responses other than from latest request.

Remove timeouts which were used to mitigate the racing issue but are
obsolete now.

Reviewed-by: Z
Refs: #123
```

### Breaking change with `!`

```
feat!: send an email to the customer when a product is shipped
```

### Breaking change with scope and `!`

```
feat(api)!: send an email to the customer when a product is shipped
```

### Breaking change with `!` and footer

```
chore!: drop support for Node 6

BREAKING CHANGE: use JavaScript features not available in Node 6.
```

### Breaking change footer only

```
feat: allow provided config object to extend other configs

BREAKING CHANGE: `extends` key in config file is now used for extending other config files
```

### Revert

```
revert: let us never again speak of the noodle incident

Refs: 676104e, a215868
```

### Other common types

```
build(deps): bump lodash from 4.17.20 to 4.17.21
ci: run tests on Node 20
perf(db): cache prepared statements
refactor(auth): extract token validation into helper
style: apply prettier formatting
test(cart): cover empty cart checkout
```

### Closing an issue

```
fix(login): handle expired session cookie

Redirect to the login page instead of throwing a 500 when the session
cookie has expired.

Closes: #482
```

## Invalid examples and fixes

| Bad | Problem | Better |
| --- | --- | --- |
| `Fixed the bug` | No type | `fix: handle null user in profile page` |
| `fix : handle null` | Space before colon | `fix: handle null user` |
| `fix:handle null` | Missing space after colon | `fix: handle null user` |
| `feat: Added dark mode.` | Past tense, capitalised, trailing period | `feat: add dark mode` |
| `update stuff` | No type, vague | `refactor(ui): simplify button styles` |
| `feat(): add login` | Empty scope | `feat: add login` or `feat(auth): add login` |
| `feat(auth, ui): add login` | Multiple scopes; spec expects a single noun | Split commits or pick one scope |
| `fix: bug\nBody right after` | No blank line before body | Insert one blank line |
| `breaking change: drop v1` | Not a type; wrong token | `feat!: drop v1 API` |
| `feat: x\n\nBreaking change: y` | `BREAKING CHANGE` must be uppercase | `BREAKING CHANGE: y` |
| `feat: add search and fix cache bug` | Two types in one commit | Two commits: `feat: add search`, `fix: invalidate stale cache` |

## Choosing between similar types

- Adds behavior users can observe → `feat`.
- Corrects behavior that was wrong → `fix`.
- Restructures with no behavior change → `refactor`.
- Faster or lighter with the same behavior → `perf`.
- Only comments/README/docs → `docs`.
- Dependency bumps, build scripts → `build`. Pipeline config → `ci`.
- Housekeeping that fits nowhere else (e.g. `.gitignore`) → `chore`.
