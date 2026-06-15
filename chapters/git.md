# Version control with `git`

## Useful git config

### Alias

```gitconfig
[alias]
  ff = merge --ff-only origin/HEAD
  s = status --verbose
  a = add
  aa = add --all
  au = add --update
  b = branch --verbose
  c = commit --verbose
  ca = commit --all --verbose
  cm = commit --amend --verbose
  d = diff
  ds = diff --stat
  dc = diff --cached
  e = edit
  r = remote --verbose
  nuke = "!git reset --hard HEAD && git clean -fd"
  logs = log --pretty=format:"%C(yellow)%h\\ %ad%Cred%d\\ %Creset%s%Cblue\\ [%cn]" --decorate --date=short
  graph = log --graph --all --oneline --decorate
  list = ls-tree --full-tree --name-only -r HEAD
  fzf = "!git ls-files | fzf | xargs -r ${EDITOR:-nvim}"
  alias = "!git config -l | grep alias | cut -c 7-"
  diff-file-last-commit = "!f() { \
    project_root_dir=$(git rev-parse --show-toplevel); \
    echo finding full file path of $1 in $project_root_dir; \
    filepath=$(find $project_root_dir -type f -name $1); \
    echo full file path $filepath; \
    last_modified_commit_hash=$(git rev-list -1 HEAD $filepath); \
    echo last commit file modified $last_modified_commit_hash; \
    git difftool $last_modified_commit_hash^ $filepath; \
  }; f"
  hide = update-index --assume-unchanged
  unhide = update-index --no-assume-unchanged
  unhide-all = ! git ls-files -v | grep '^[a-z]' | cut -c3- | xargs git unhide --
  hiddens = ! git ls-files -v | grep '^[a-z]' | cut -c3-
  edit = !$EDITOR $(git status --porcelain | awk '$1 ~ /^M|A|U/ {print $2}')
```
