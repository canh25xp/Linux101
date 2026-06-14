# Bash

## Bash files

- **~/.bash_profile**: Executed only for **login shells**
- **~/.bashrc**: Executed for every **interactive shell**

See `man bash` for a full list of bash related files.

### What goes in `~/.bash_profile`

Things that should run **once when you log in**:

- Environment variables (`PATH`, `EDITOR`, `PAGER`, ...)
- Session-wide configuration
- Starting agents (ssh-agent, gpg-agent)
- Variables needed by GUI applications
- Commands that are expensive and should not run for every shell

### What goes in `~/.bashrc`

Things that should be available in **every interactive shell**:

- Aliases
- Shell options
- Prompt (`PS1`)
- Completion
- Functions
- Key bindings
- Interactive tools (`fzf`, `zoxide`, `starship`, etc.)

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
bash -c 'printf "%s%s\n" $(shopt -q login_shell && echo L || echo l) $([[ $- == *i* ]] && echo I || echo i)'
li
printf "%s%s\n" $(shopt -q login_shell && echo L || echo l) $([[ $- == *i* ]] && echo I || echo i)
lI
```
