# Linux 101

> [!IMPORTANT]
> Work in progress

## Introduction

This course provides a practical introduction to Linux through hands-on exercises and real-world workflows.
Rather than focusing on graphical interfaces, we will primarily work in a **headless** environment—that is, interacting with Linux entirely through the command line.

Throughout the course, you will connect to a Linux machine using `ssh`.
The environment is preconfigured with all required tools to ensure everyone has a consistent learning experience.
Alternatively, you may use the provided Docker image [here](http://ghcr.io/canh25xp/dotfiles-debian)

By the end of this course, you should be comfortable navigating the Linux terminal, managing files and directories, working with remote systems, and using common command-line tools in your daily workflow.

## Prerequisite

- A keyboard
- A mouse (optional)
- A working computer with `ssh` client installed;
  ```
  ssh -V
  ```

## Table of Contents

- [Introduction to linux](/chapters/linux.md)
- Linux basic
  - [Basic Linux commands](/chapters/commands.md)
  - [Linux Filesystem Hierarchy Standard (FHS)](/chapters/FHS.md)
  - [Basic Bash](/chapters/bash.md)
- Productivity tools:
  - [`ssh`: working with remote systems](/chapters/ssh.md)
  - [Everything, everywhere, all at `git`](/chapters/git.md)
  - [From `p4` to `git`](/chapters/p4.md)
  - [Multitasking with `tmux`](/chapters/tmux.md)
  - [Android development with `termux` and `adb`](./chapters/android.md)
  - [Containerize with `podman` (`docker` alternative)](/chapters/docker.md)
- [Windows Subsystem for Linux](/chapters/wsl.md)

## Setup

To learn Linux, you must first get your self into one.

The easiest way is using `ssh`.

```bash
ssh -p <port> <username>@<ip>
```

Host: 107.98.150.183
Port: 10022

| Username     | Password    |
| ------------ | ----------- |
| cuong.nguyen | cuongnguyen |
| cuong.nm4    | cuongnm4    |
| doan.ng      | doanng      |
| duc.cuong    | duccuong    |
| giang.ngo    | giangngo    |
| haphong.ng   | haphongng   |
| khanh.pd     | khanhpd     |
| manhdung.ng  | manhdungng  |
| minhhoa.tr   | minhhoatr   |
| oanh.tt      | oanhtt      |
| tien.oanh    | tienoanh    |
| vancanh.ng   | vancanhng   |
| vu.pd        | vupd        |
| vuong.chinh  | vuongchinh  |
| yen.pt1      | yenpt1      |

For example:

```bash
ssh -p 10022 cuong.nguyen@107.98.150.183
ssh -p 10022 yen.pt1@107.98.150.183
```

Alternatively, Use your own computer:

```bash
docker run -it --rm ghcr.io/canh25xp/dotfiles-debian:latest
```

Or if you're using WSL:

```pwsh
curl.exe -LO http://107.98.150.183:6969/Archive/WSL/dotfiles-debian.tar.gz
wsl.exe --import Debian C:\Debian dotfiles-debian.tar.gz --version 2
wsl.exe -d Debian
```

> [!NOTE]
> if download from server `http://107.98.150.183:6969` is not working, use this instead:
>
> `curl -LO https://github.com/canh25xp/dotfiles/releases/latest/download/dotfiles-debian.tar.gz`

## References

- [the art of command line](https://github.com/jlevy/the-art-of-command-line)
- [101 linux commands](https://github.com/bobbyiliev/101-linux-commands)
- [introduction to linux](https://training.linuxfoundation.org/training/introduction-to-linux/)
