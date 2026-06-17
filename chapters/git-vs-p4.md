# `git` vs `p4`

## Core Differences

| Aspect             | Git                                                          | Perforce (P4)                                               |
| ------------------ | ------------------------------------------------------------ | ----------------------------------------------------------- |
| Architecture       | Distributed Version Control System (DVCS)                    | Centralized Version Control System (CVCS)                   |
| Repository Model   | Every clone contains the full repository history             | Files and history are stored on a central server            |
| Offline Work       | Full functionality offline (commit, branch, log, diff, etc.) | Most operations require server access                       |
| Performance        | Very fast for local operations                               | Fast for large centralized repositories                     |
| Branching          | Lightweight and cheap                                        | More heavyweight, typically managed through streams         |
| Merging            | Common workflow; powerful merge tools                        | Supported, but branching/merging is usually more controlled |
| Commits            | Local commits, then push to remote                           | Changes are submitted directly to the server                |
| History Storage    | Entire history on every client                               | History stored primarily on the server                      |
| Collaboration      | Peer-to-peer capable; multiple remotes supported             | Central server is the source of truth                       |
| Access Control     | Usually repository-level through hosting platforms           | Fine-grained permissions built into the server              |
| Large Binary Files | Not ideal by default (often use `git lfs`)                   | Designed to handle large binary assets efficiently          |
| Scalability        | Excellent for source code repositories                       | Excellent for very large repositories and binary assets     |
| Source code        | Yes                                                          | Proprietary (free tiers available)                          |

## Commands Differences

| Task               | Git                         | P4                            |
| ------------------ | --------------------------- | ----------------------------- |
| Clone repository   | `git clone`                 | `p4 client` + `p4 sync`       |
| Check status       | `git status`                | `p4 opened`, `p4 diff`        |
| Get latest changes | `git pull`                  | `p4 sync`                     |
| Create change      | `git commit`                | `p4 submit`                   |
| View history       | `git log`                   | `p4 filelog`, `p4 changes`    |
| Compare changes    | `git diff`                  | `p4 diff`                     |
| Create branch      | `git branch`                | `p4 integrate` / Streams      |
| Merge branch       | `git merge`                 | `p4 integrate` + `p4 resolve` |
| Revert changes     | `git restore`, `git revert` | `p4 revert`                   |
| Tag release        | `git tag`                   | Labels (`p4 label`)           |

## References

- [Git vs. Perforce P4](https://www.perforce.com/blog/vcs/git-vs-perforce-how-choose-and-when-use-both)
- [p4 vs git branching](https://stackoverflow.com/questions/23208128/perforce-branching-vs-git-branching)
