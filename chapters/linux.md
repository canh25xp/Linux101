# Introduction to linux

## Unix vs Linux

| Aspect      | Unix                          | Linux                             |
| ----------- | ----------------------------- | --------------------------------- |
| Origin      | Created in 1969 at Bell Labs  | Created in 1991 by Linus Torvalds |
| Source Code | Original proprietary codebase | Written from scratch; Unix-like   |
| License     | Usually proprietary           | Open source (GPL)                 |
| Cost        | Often commercial              | Usually free                      |
| Examples    | AIX, HP-UX, Solaris           | Ubuntu, Debian, Fedora            |

Linux is a Free, Open-source alternative to Unix, Created by Linus Torvalds, hence the name, Linus's Unix.

Source code: [torvalds/Linux](https://github.com/torvalds/linux). Linux's [first commit](https://github.com/torvalds/linux/commit/1da177e4c3f41524e886b7f1b8a0c1fc7321cac2).

## Linux distribution (distro)

Linux it self is just a Kernel, it only become a complete Operating System when it packaged with system and libraries developed by third parties—such as GNU, Red Hat, and X.Org.
A distribution (aka distro) is just Linux with different "flavor".

![Linux distro map](https://github.com/codywohlers/linuxdistromap/blob/main/linuxdistros.dot.png)

- There are many thousands of Linux distributions: Ubuntu, Debian, Fedora, Arch, NixOS, Alpine, ...
- The most notable differences between these distro is:
  - The package manager their update/release policy: apt, pacman, yum, ...
  - The software that comes pre-installed with it.
  - The default desktop environment: Gnome, KDE, Cinnamon, ...

## Debian/Ubuntu

Ubuntu is by far the most popular distribution as of today.

|                     | Debian                                           | Ubuntu                                            |
| ------------------- | ------------------------------------------------ | ------------------------------------------------- |
| Maintainer          | Community-driven Debian Project                  | Developed by Canonical                            |
| First Release       | 1993                                             | 2004                                              |
| Release Cycle       | ~2 years (stable releases)                       | Every 6 months; LTS every 2 years                 |
| Support Period      | ~5 years (with LTS support)                      | 5 years standard LTS, optional extended support   |
| Package Source      | Debian repositories                              | Debian packages plus Ubuntu-specific packages     |
| Package Freshness   | Conservative, older but well-tested              | Newer software versions                           |
| Stability           | Extremely stable                                 | Stable, but less conservative than Debian         |
| Ease of Use         | Requires more manual setup                       | More beginner-friendly                            |
| Desktop Experience  | Multiple desktops available, less customized     | Polished desktop experience out of the box        |
| Hardware Support    | Good, but may require enabling non-free firmware | Generally better out-of-the-box hardware support  |
| Proprietary Drivers | Optional, less emphasized                        | Easier installation and management                |
| Commercial Support  | Community support                                | Commercial support available from Canonical       |
| Cloud Usage         | Popular for servers                              | Very popular for cloud and enterprise deployments |
| Default Audience    | Experienced users, servers                       | Beginners, desktop users, enterprises             |
| Documentation       | Excellent community documentation                | Extensive official and community documentation    |

Although Ubuntu is often recommended for beginner due to its simplicity and user friendly.
However, since we'll be using WSL, you won't notice much differences between these two.
So I would suggest you start with Debian

## Debian stable, testing, unstable and experimental

- **stable**: the current released version.
  As of 2026, that’s Debian 13 (`trixie`), released mid-2025.
  Stable gets security updates and very limited bugfix updates.
  Package versions are frozen at release; only Security Team-blessed exceptions move.
- **testing**: the next release in development.
  Currently this is `forky` (post `trixie` codename, will be Debian 14).
  Testing gets package updates from unstable after they sit ~10 days without serious bug reports.
  It's continuously usable but not “released.”
- **unstable**: aka `sid` the rolling track where everything lands first.
  Sid is always named Sid - it never releases.
  Packages flow from upstream > Debian developer uploads > unstable > testing > stable.
- **experimental**: opt-in archive for packages too risky for unstable (alpha software, packaging experiments, deliberately conflict-causing).
  Not pinned by default; you ask for individual packages.

To find current Debian version:

```sh
cat /etc/os-release
```

```sh
podman run --rm debian:latest cat /etc/os-release
podman run --rm debian:unstable cat /etc/os-release
```

- It is usually recommended to install Debian **stable** for personal computer, server, home lab, ...
- However, we'll accept the risk by using **unstable** since broken dependencies, bug, security vulnerability are often non-fatal in WSL.
  You can always just remove the old one and install a new fresh instance of Debian.

## References

- [Linux](https://en.wikipedia.org/wiki/Linux)
- [Linux kernel](https://en.wikipedia.org/wiki/Linux_kernel)
- [Unix-like](https://en.wikipedia.org/wiki/Unix-like)
- [Debian stable vs testing vs unstable](https://www.bigiron.cc/guides/debian-stable-vs-testing-vs-unstable-which-to-run-when)
- [Debian Release cycle](https://www.debian.org/releases/)
- [Debian vs Ubuntu](https://itsfoss.com/debian-vs-ubuntu/)
