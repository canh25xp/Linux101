# Basic Git Workflow for a Shared Repository

This document describes the most common workflow when multiple developers collaborate on the same Git repository.

## 1. Clone the Repository

Clone the repository to your local machine.

```sh
git clone <repo-url>
cd <repo-name>
```

Example:

```sh
git clone https://github.com/example/project.git
cd project
```

---

## 2. Update Your Local Repository

Before starting any work, make sure your local branch is up to date.

```sh
git pull origin main
```

This fetches new commits from the remote repository and merges them into your local branch.

---

## 3. Create a Feature Branch

Create a new branch for your work.

```sh
git switch -c feature/my-change
```

Examples:

```sh
git switch -c feature/add-login
git switch -c bugfix/fix-crash
```

Working on a separate branch keeps unfinished work isolated from the main branch.

---

## 4. Make Changes

Edit files, add new files, run tests, and verify everything works as expected.

Check what has changed:

```sh
git status
git diff
```

---

## 5. Stage Changes

Add the files you want to include in the next commit.

```sh
git add <file>
```

Or stage all modified files:

```sh
git add .
```

Verify staged changes:

```sh
git status
git diff --cached
```

---

## 6. Commit Changes

Create a commit describing your work.

```sh
git commit -m "Add login validation"
```

A commit should represent a logical unit of work.

---

## 7. Synchronize With Remote Changes

Other developers may have pushed changes while you were working.

Fetch the latest changes:

```sh
git fetch origin
```

Rebase your branch onto the latest main branch:

```sh
git rebase origin/main
```

Resolve conflicts if necessary.

---

## 8. Push Your Branch

Upload your branch to the remote repository.

```sh
git push -u origin feature/my-change
```

The `-u` option sets the upstream branch so future pushes can use:

```sh
git push
```

---

## 9. Create a Pull Request (PR)

Open a Pull Request (GitHub), Merge Request (GitLab), or equivalent review request.

The review process typically includes:

- Code review
- Automated testing
- Discussion and feedback
- Approval from teammates

---

## 10. Merge Into Main

After approval, merge the branch into the main branch.

Common merge strategies:

- Merge commit
- Squash merge
- Rebase merge

The exact method depends on team policy.

---

## 11. Update and Clean Up

Switch back to the main branch:

```sh
git switch main
```

Get the latest changes:

```sh
git pull origin main
```

Delete the local feature branch:

```sh
git branch -d feature/my-change
```

Delete the remote branch if it still exists:

```sh
git push origin --delete feature/my-change
```

---

# Workflow Summary

```text
git clone
    ↓
git pull
    ↓
git switch -c feature/my-change
    ↓
edit files
    ↓
git add
    ↓
git commit
    ↓
git fetch
git rebase origin/main
    ↓
git push
    ↓
Create Pull Request
    ↓
Code Review
    ↓
Merge
    ↓
git pull
    ↓
Delete feature branch
```

## Golden Rules

- Pull before starting work.
- Commit small, logical changes.
- Work on feature branches, not directly on `main`.
- Review changes before committing.
- Synchronize with the latest `main` before pushing.
- Never force-push shared branches unless the team explicitly allows it.
- Resolve conflicts carefully and test after resolving them.
