# 3 ways to manipulate git history: `reset`, `revert`, `checkout`

- `reset` and `revert` are **Destructive**, meaning you should use them carefully to avoid losing your work.
- `revert` is **not destructive**. It is specifically designed to safely undo changes by creating a new commit.

Like most git operation, All 3 of them can be **undo** by `reflog`, but **not uncommitted changes that were overwritten or deleted**.

These commands can **NOT** be undo:

```sh
git reset --hard
git checkout foo.c
```

It will discard work tree changes (uncommitted files).

If you lucky, the editor might keep a backup of the changes somewhere.
Otherwise, your changes are lost forever.

A comparison table:

| Command        | Changes History?  | Creates New Commit? | Affects Branch Pointer? | Affects Index?  | Affects Working Tree? | Safe for Shared History? |
| -------------- | ----------------- | ------------------- | ----------------------- | --------------- | --------------------- | ------------------------ |
| `git reset`    | Yes               | No                  | Yes                     | Depends on mode | Depends on mode       | No                       |
| `git revert`   | No (adds history) | Yes                 | No                      | No              | No                    | Yes                      |
| `git checkout` | No                | No                  | Sometimes               | Sometimes       | Yes                   | Usually                  |

## `git reset`

Moves the current branch to another commit.

```sh
git reset --soft HEAD~1
```

```
A -- B -- C (main, HEAD)
```

becomes

```
A -- B (main, HEAD)
```

but the changes from `C` remain staged.

### Modes

| Mode                | Branch | Index | Working Tree |
| ------------------- | ------ | ----- | ------------ |
| `--soft`            | Reset  | Keep  | Keep         |
| `--mixed` (default) | Reset  | Reset | Keep         |
| `--hard`            | Reset  | Reset | Reset        |

Typical use:

```sh
git reset --soft HEAD~1
```

Undo the last commit but keep all changes staged.

```sh
git reset --hard HEAD~1
```

Completely remove the last commit and discard local changes.

---

## `git revert`

Creates a new commit that applies the inverse of an existing commit.

```sh
git revert <commit>
```

Before:

```
A -- B -- C (main, HEAD)
```

After:

```
A -- B -- C -- D (main, HEAD)
               ^
          revert of C
```

Nothing is removed from history.

Typical use:

```sh
git revert HEAD
```

Undo a bad commit that has already been pushed.

Advantages:

- Does not rewrite history.
- Safe for shared branches.
- Easy to understand and audit.

---

## `git checkout`

Historically used for many different operations.

### Switch branches

```sh
git checkout feature
```

Moves `HEAD` to another branch.

```
main:    A -- B
feature: A -- B -- C

HEAD -> feature
```

### Restore a file

```sh
git checkout HEAD -- foo.c
```

Replaces `foo.c` in the working tree with the version from `HEAD`.

This **discards uncommitted changes** in `foo.c`.

Modern Git prefers:

```sh
git switch feature
git restore foo.c
```

because they separate branch switching from file restoration.

---

## What can and cannot be recovered?

### Recoverable with `reflog`

```sh
git reset --hard HEAD~3
```

The commits still exist:

```sh
git reflog
git reset --hard <old-commit>
```

### Not recoverable with `reflog`

```sh
git checkout -- foo.c
git restore foo.c
git reset --hard
```

when the discarded changes were **never committed**.

Example:

```sh
echo "important work" >> foo.c
git checkout -- foo.c
```

The modified content existed only in the working tree, so Git never recorded it anywhere.

Recovery is only possible if:

- your editor kept backups,
- your filesystem has snapshots,
- or you manually saved a copy elsewhere.

Otherwise the changes are gone.

## Rule of thumb

| Goal                  | Command       |
| --------------------- | ------------- |
| Undo a commit locally | `git reset`   |
| Undo a pushed commit  | `git revert`  |
| Switch branches       | `git switch`  |
| Restore files         | `git restore` |
| Recover lost commits  | `git reflog`  |

A useful mental model:

- **`reset`** → move a branch.
- **`revert`** → add an opposite commit.
- **`checkout` / `switch`** → move `HEAD`.
- **`restore`** → replace files in the working tree.
