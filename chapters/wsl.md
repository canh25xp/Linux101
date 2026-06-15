# Windows Subsystem for Linux (WSL)

## Installation

This guide does NOT contain how to install the WSL it self (`wsl.exe`), it assumed you already has `wsl.exe` install.
Check `wsl` installation with:

```pwsh
wsl --version
```

Refer to [How to install Linux on Windows with WSL](`https://learn.microsoft.com/en-us/windows/wsl/install`) for that.

This guide only instruct you to install a **distro** on WSL.

### Install from Microsoft's official repo

```pwsh
wsl --list --online
```

Currently, these are the official distro support by Microsoft.

| NAME                         | FRIENDLY NAME                |
| ---------------------------- | ---------------------------- |
| AlmaLinux-8                  | AlmaLinux OS 8               |
| AlmaLinux-9                  | AlmaLinux OS 9               |
| AlmaLinux-Kitten-10          | AlmaLinux OS Kitten 10       |
| AlmaLinux-10                 | AlmaLinux OS 10              |
| Debian                       | Debian GNU/Linux             |
| FedoraLinux-44               | Fedora Linux 44              |
| FedoraLinux-43               | Fedora Linux 43              |
| SUSE-Linux-Enterprise-15-SP7 | SUSE Linux Enterprise 15 SP7 |
| SUSE-Linux-Enterprise-16.0   | SUSE Linux Enterprise 16.0   |
| Ubuntu                       | Ubuntu                       |
| Ubuntu-26.04                 | Ubuntu 26.04 LTS             |
| Ubuntu-24.04                 | Ubuntu 24.04 LTS             |
| Ubuntu-22.04                 | Ubuntu 22.04 LTS             |
| archlinux                    | Arch Linux                   |
| eLxr                         | eLxr 12.12.0.0 GNU/Linux     |
| kali-linux                   | Kali Linux Rolling           |
| openSUSE-Tumbleweed          | openSUSE Tumbleweed          |
| openSUSE-Leap-16.0           | openSUSE Leap 16.0           |
| OracleLinux_7_9              | Oracle Linux 7.9             |
| OracleLinux_8_10             | Oracle Linux 8.10            |
| OracleLinux_9_5              | Oracle Linux 9.5             |
| SUSE-Linux-Enterprise-15-SP6 | SUSE Linux Enterprise 15 SP6 |

Pick a distro, for example **Debian**:

```pwsh
wsl --install Debian
```

Launch it:

```pwsh
wsl -d Debian
```

### Install from a `tar` file

Unofficial repo for WSL tar files: [wsl-distro-tars](https://github.com/mvaisakh/wsl-distro-tars)

Although these file does NOT come from official Microsoft repo, they are extracted directly from official Docker Image.

```pwsh
curl.exe -LO https://github.com/mvaisakh/wsl-distro-tars/releases/download/100620260342/debian.unstable-100620260344.tar
wsl.exe --import Debian C:\Debian debian.unstable-100620260344.tar --version 2
wsl.exe -d Debian
```

## References

- [Windows Subsystem for Linux Documentation](https://learn.microsoft.com/en-us/windows/wsl/)
