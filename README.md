# Linux 101

> [!IMPORTANT]
> Work in progress

## Introduction

This course provides a practical introduction to Linux through hands-on exercises and real-world workflows.
Rather than focusing on graphical interfaces, we will primarily work in a **headless** environment—that is, interacting with Linux entirely through the command line.

Throughout the course, you will connect to a Linux machine using `ssh`.
The environment is preconfigured with all required tools to ensure everyone has a consistent learning experience.
Alternatively, you may use the provided Docker image:

```bash
ghcr.io/canh25xp/dotfiles-debian
```

By the end of this course, you should be comfortable navigating the Linux terminal, managing files and directories, working with remote systems, and using common command-line tools in your daily workflow.

## Prerequisite

- A keyboard
- A mouse (optional)
- A working computer with `ssh` client installed;
  ```
  ssh -V
  ```

## Table of Contents

- Introduction to linux
  - A brief history of Linux
  - Linux distribution (distro)
    - Debian / Ubuntu
- Linux basic
  - Basic Linux commands
  - Linux Filesystem Hierarchy Standard (FHS)
    - Everything is a file.
  - Bash basic
- Productivity tools:
  - `ssh`: working with remote systems.
  - Everything, everywhere, all at `git`
    - `git` tips and tricks.
    - `git` good and bad practices.
    - Dotfiles management with `chezmoi`
    - Password management with `pass`
  - From `p4` to `git`
  - Multitasking with `tmux`
  - Android development with `termux` and `adb`
  - Containerize with `podman` (`docker` alternative)

## Chapters

TODO

### Setup

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
curl.exe -LO http://107.98.150.183:6969/Archive/WSL/dotfile-debian.tar.gz
wsl.exe --import Debian C:\WSL\Debian dotfiles-debian.tar.gz --version 2
wsl.exe -d Debian
```

> [!NOTE]
> if download from server `http://107.98.150.183:6969` is not working, use this instead:
>
> `curl.exe -LO https://github.com/canh25xp/dotfiles/releases/download/v0.1.0/dotfiles-debian.tar.gz`

## References

- [the art of command line](https://github.com/jlevy/the-art-of-command-line)
- [101 linux commands](https://github.com/bobbyiliev/101-linux-commands)
- [introduction to linux](https://training.linuxfoundation.org/training/introduction-to-linux/)
