# Basic Git Concepts

## Working Directory, Staging Area, and Repository

Git tracks changes through three main areas:

```text
Working Directory  -->  Staging Area  -->  Repository
      (edit)            git add          git commit
```

### Working Directory

The **working directory** (or working tree) contains the files you are currently editing.

```sh
echo "Hello" > hello.txt
```

At this point:

- File exists on disk.
- Git sees it as modified or untracked.
- The change is **not staged** and **not committed**.

Check status:

```sh
git status
```

### Staging Area (Index)

The **staging area** (also called the **index**) is where you prepare the exact changes that will go into the next commit.

```sh
git add hello.txt
```

Now:

- Working directory contains the file.
- Staging area contains a snapshot of the file.
- Repository is unchanged.

Think of the staging area as a **draft of the next commit**.

You can selectively stage changes:

```sh
git add file1.c
git add file2.c
```

or interactively:

```sh
git add -p
```

### Repository

The **repository** (`.git` directory) stores the complete history of commits.

```sh
git commit -m "Add hello.txt"
```

Now the staged snapshot becomes a permanent commit in the repository.

```text
Working Directory
        |
        v
   Staging Area
        |
        v
    Commit History
```

---

## HEAD

`HEAD` is a special reference that indicates **what commit you currently have checked out**.

Normally:

```text
HEAD
 |
 v
main
 |
 v
a1b2c3d
```

Meaning:

- `HEAD` points to branch `main`
- `main` points to commit `a1b2c3d`

Check it:

```sh
git rev-parse HEAD
```

### Moving HEAD

When switching branches:

```sh
git switch feature
```

```text
HEAD
 |
 v
feature
 |
 v
e4f5g6h
```

When checking out a specific commit:

```sh
git checkout a1b2c3d
```

```text
HEAD
 |
 v
a1b2c3d
```

This is called a **detached HEAD** state because `HEAD` points directly to a commit instead of a branch.

---

## References (Refs)

A **reference** (ref) is simply a named pointer to an object, usually a commit.

Common refs:

| Ref             | Purpose                |
| --------------- | ---------------------- |
| `main`          | Branch reference       |
| `feature/login` | Branch reference       |
| `v1.0`          | Tag reference          |
| `HEAD`          | Current checkout       |
| `origin/main`   | Remote-tracking branch |

Example:

```text
main ----------+
               |
feature -------+----> a1b2c3d
               |
v1.0 ----------+
```

All refs ultimately point to commits.

### Branches Are References

A branch is just a movable reference:

```text
main -> A
```

After a new commit:

```text
main -> B
```

Git simply moves the branch pointer forward.

### Tags Are References

Tags also point to commits:

```sh
git tag v1.0
```

```text
v1.0 -> a1b2c3d
```

Unlike branches, tags normally do not move.

### Remote-Tracking References

When you fetch:

```sh
git fetch origin
```

Git updates refs such as:

```text
origin/main
origin/develop
```

These represent Git's last known state of the remote repository.

---

## Useful Mental Model

```text
                refs
                 |
                 v
HEAD --> main --> Commit C
                   |
                   v
                Commit B
                   |
                   v
                Commit A


Working Directory
        |
        v
Staging Area (Index)
        |
        v
      HEAD
```

- **Working Directory** = files you are editing.
- **Staging Area (Index)** = snapshot for the next commit.
- **Repository** = commit history stored in `.git`.
- **HEAD** = current checkout position.
- **References (Refs)** = named pointers to commits (branches, tags, remote branches).

### Related Commands

```sh
git status          # Inspect working tree and staging area
git add             # Working Directory -> Staging Area
git restore         # Discard working tree changes
git restore --staged # Unstage changes
git commit          # Staging Area -> Repository

git switch          # Move HEAD to another branch
git checkout        # Older command for switching/checking out

git branch          # List branch refs
git tag             # List tag refs
git show-ref        # List all refs
git rev-parse HEAD  # Resolve HEAD to a commit
```

**Reference:**

- [Working Directory, Staging, Repository](https://unwiredlearning.com/blog/git-staging-workflow)
