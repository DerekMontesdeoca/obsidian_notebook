$ introduces parameter expansion, command sutitution and arithmetic expansion. Parameter name may be enclosed in braces like so: `${MYVAR}` to avoid having characters that follow the variable be interpreted as part of thename: `${f}_today`.

# Useful parameter expansions

```bash
# The typical var || default
${var:-default}
# This is more like (var = var || default)
${var:=default}
# Fail if var is unset.
${var:?error message}
# When using the above expansion by itself, add : (noop command) to avoid having it be interpreted as a command. lke so:
: ${var:? error message}
```