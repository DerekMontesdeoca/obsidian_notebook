## Common `type` keywords

| Type       | Purpose                                         |
| ---------- | ----------------------------------------------- |
| `feat`     | Add a new feature                               |
| `fix`      | Fix a bug                                       |
| `docs`     | Documentation-only changes                      |
| `style`    | Code formatting, no code logic changes          |
| `refactor` | Code changes that neither fix nor add a feature |
| `perf`     | Improve performance                             |
| `test`     | Add or fix tests                                |
| `chore`    | Maintenance tasks (build, deps, etc.)           |
| `build`    | Changes to build system or external deps        |
| `ci`       | CI/CD config changes                            |

## Examples

```bash
feat(login): add JWT-based authentication

fix(api): handle null user ID on lookup 

docs(readme): clarify setup instructions 

style: remove trailing whitespace refactor: extract validation 
to separate module 

chore: bump dependencies
```

## Tips

- Use **imperative mood**: "add" not "added", "fix" not "fixed"
- Keep summary ≤ 50 chars
- Wrap body at 72 chars (if used)
- Use body to explain _why_, not just _what_
- Use footer for breaking changes or references