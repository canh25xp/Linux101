# 3 way to manipulate git history: `reset`, `revert`, `checkout`

All of them are **Destructive commands**, meaning you should use them carefully to avoid losing your work.

Like most git operation, All 3 of them can be **undo** by `reflog`

These commands can **NOT** be undo:

```sh
git reset --hard
git checkout foo.c
```

It will discard work tree changes (uncommitted files)

If you messed up something, [ohshitgit](https://ohshitgit.com/) might be able to rescue.
