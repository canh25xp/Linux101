# Quick start with `p4`

## Installation

### Download binary from [the official perforce file server](https://filehost.perforce.com/perforce)

Download the binary for your system and put it in `$PATH`:

- [p4 (Linux)](https://filehost.perforce.com/perforce/r26.1/bin.linux26x86_64/p4)
- [`p4.exe` (Windows)](https://filehost.perforce.com/perforce/r26.1/bin.ntx64/p4.exe)

### Install from the package manager

#### Windows

There's no separated `p4` cli installation on `winget`, but you can install `Perforce.P4V` which has `p4.exe` included.

```sh
Winget install --id Perforce.P4V
```

#### Linux

First add Perforce repository to apt source lists

```sh
curl -fsSL https://package.perforce.com/perforce.pubkey | gpg --dearmor | sudo tee /usr/share/keyrings/perforce.gpg >/dev/null
echo "deb [signed-by=/usr/share/keyrings/perforce.gpg] https://package.perforce.com/apt/ubuntu noble release" | sudo tee /etc/apt/sources.list.d/perforce.list >/dev/null
sudo apt update && sudo apt install -y p4-cli
```

> [!NOTE]
> Replace **noble** replace with your Ubuntu distribution: precise, trusty, xenial, bionic, focal, jammy or, noble.
>
> On Debian, just use **noble** is fine.

## Post Installation

### 1. Check executable

```sh
p4 -V
```

Sample output:

```text
Perforce - The Fast Software Configuration Management System.
Copyright 1995-2026 Perforce Software.  All rights reserved.
This product includes software developed by the OpenSSL Project
for use in the OpenSSL Toolkit (http://www.openssl.org/)
Version of OpenSSL Libraries: OpenSSL 3.5.7 9 Jun 2026
See 'p4 help [ -l ] legal' for additional license information on
these licenses and others.
Extensions/scripting support built-in.
Parallel sync threading built-in.
Rev. P4/LINUX26X86_64/2026.1/2972966 (2026/06/10).
```

### 2. Set environment

First check if any p4 environment variable is set.
If you setup on a new computer, this should return nothing.

```sh
p4 set
```

> [!NOTE]
> Run `p4 help env` to see a full list of supported Perforce environment variables.

You need to setup at least `P4USER` and `P4PORT` to be able to connect to the Perforce server.

```sh
p4 set P4USER=vancanh.ng
p4 set P4PORT=107.113.53.156:1716
```

Use `p4 set` with no arguments again to check if environment is properly setup.

> [!NOTE]
> There's 3 location to store p4 environment with 1 additional exception for Windows:
>
> - Command line global options
> - Config file
> - Registry (Windows only)
> - Enviro file
> - Environments

### 3. Check connection

```sh
p4 info
```

Sample output

```text
User name: vancanh.ng
Client name: vancanh-ng02
Client host: vancanh-ng02
Client unknown.
Current directory: /home/vancanh-ng/projects/Linux101
Peer address: 165.213.202.46:3908
Client address: 107.98.39.128
Server address: P4-AVENGERS:1669
Server root: /p4root/db
Server date: 2026/06/29 13:08:32 +0900 KST
Server uptime: 1036:28:57
Server version: P4D/LINUX26X86_64/2023.2/2723144 (2025/02/19)
ServerID: p4m_sds
Server services: standard
Broker address: P4-AVENGERS:1736
Broker version: P4BROKER/LINUX26X86_64/2025.2/2907753
Proxy address: Proxy-Replica:1716
Proxy version: P4P/LINUX26X86_64/2016.2/1598668 (2017/12/08)
Server license: ELECTRONICS DIVISION CO.,LTD. 10800 users (support ends 2027/06/01) (expires 2027/06/01)
Server license-ip: 165.213.202.46:1669
Case Handling: sensitive
```

## References

- [p4 set](https://help.perforce.com/helix-core/server-apps/cmdref/current/Content/CmdRef/p4_set.html)
- [Environment and registry variables](https://help.perforce.com/helix-core/server-apps/cmdref/current/Content/CmdRef/envars.html)
- [P4CONFIG](https://help.perforce.com/helix-core/server-apps/cmdref/current/Content/CmdRef/P4CONFIG.html)
- [P4ENVIRO](https://help.perforce.com/helix-core/server-apps/cmdref/current/Content/CmdRef/P4ENVIRO.html)
