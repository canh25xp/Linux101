# Tmux

## Why `tmux` ?

`tmux` is a terminal multiplexer.
It allows you to run multiple terminal sessions inside a single terminal window.

Benefits:

- Keep long-running processes alive even after disconnecting from SSH.
- Split the terminal into multiple panes.
- Open multiple windows inside a single session.
- Detach from a session and reattach later.
- Share a terminal session with another user.
- Improve productivity when working on remote servers.

A common workflow:

1. SSH into a server.
2. Start a `tmux` session.
3. Run editors, servers, builds, or monitoring tools.
4. Detach (`Ctrl+a d`) before disconnecting.
5. Reattach later (`tmux a`) and continue exactly where you left off.

## Using `tmux`

> [!NOTE]
> In the playground, `tmux` is configured as in [tmux.conf](https://github.com/canh25xp/LinuxPlayground/blob/main/dotfiles/.config/tmux/tmux.conf)
>
> So key binding might be different on other system

### Quick start

```sh
tmux # start a tmux session
Ctrl+a d # Detach
tmux a # Attach
```

### Panes, Windows, Sessions

`tmux` has three levels of organization:

```text
Session
├── Window 0
│   ├── Pane
│   └── Pane
├── Window 1
│   └── Pane
└── Window 2
    ├── Pane
    ├── Pane
    └── Pane
```

### Key binding

> [!NOTE]
> The following key bindings is **prefix** by `Ctrl + a`
>
> Keybinding is case sensitive. Meaning `a` is different than `A` (`Shift + a`)
>
> The list below is not completed. Use `?` (`<Prefix> ?`) for a full list of Keybindings.

| Key binding | Action                      |
| ----------- | --------------------------- |
| d           | Detach                      |
| c           | Create new window           |
| q           | Close current window        |
| h           | Select windows to the left  |
| l           | Select windows to the left  |
| \|          | New pane split vertically   |
| -           | New pane split horizontally |
| x           | Close current pane          |
| s           | Select session              |
| N           | New session                 |
| 0-9         | Select Windows 0-9          |
| ?           | See list of key bindings    |

The following commands does NOT need prefix

| Key binding | Action            |
| ----------- | ----------------- |
| h           | Select pane left  |
| j           | Select pane down  |
| k           | Select pane up    |
| l           | Select pane right |
