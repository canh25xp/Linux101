# Tmux

## Why `tmux` ?

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

### Key binding

> [!NOTE]
> The following key bindings is **prefix** by `Ctrl + a`
>
> Keybinding is case sensitive. Meaning `a` is different than `A` (`Shift + a`)
>
> The list below is not completed. Use `?` (`<Prefix> ?`) for a full list of Keybindings.

| Key binding | Action                     |
| ----------- | -------------------------- |
| d           | Detach                     |
| c           | Create new windows         |
| x           | Close current windows      |
| s           | Select session             |
| N           | New session                |
| 0-9         | Select Windows 0-9         |
| \|          | Split vertically           |
| -           | Split horizontally         |
| h           | Select windows to the left |
| l           | Select windows to the left |
| ?           | See list of key bindings   |

The following commands does NOT need prefix

| Key binding | Action            |
| ----------- | ----------------- |
| h           | Select pane left  |
| j           | Select pane down  |
| k           | Select pane up    |
| l           | Select pane right |
