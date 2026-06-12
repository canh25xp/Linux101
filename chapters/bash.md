# Bash

## Login shell & Interactive shell

### Login shell

```bash
shopt -q login_shell && echo Login || echo NotLogin
```

### Interactive shell

```bash
[[ $- == *i* ]] && echo Interactive || echo NotInteractive
```

### Example

```bash
printf "%s%s\n" $(shopt -q login_shell && echo L || echo l) $([[ $- == *i* ]] && echo I || echo i)
# Possible output
LI  # login + interactive
Li  # login + non-interactive
lI  # non-login + interactive
li  # non-login + non-interactive
```

```bash
docker run --rm debian bash -c 'printf "%s%s\n" $(shopt -q login_shell && echo L || echo l) $([[ $- == *i* ]] && echo I || echo i)'
li
docker run --rm debian printf "%s%s\n" $(shopt -q login_shell && echo L || echo l) $([[ $- == *i* ]] && echo I || echo i)
lI
```
