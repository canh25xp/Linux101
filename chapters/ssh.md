# Secure Shell (SSH)

## What is ssh ?

- **SSH** in it self is a protocol, it provides cryptographic network protocol for operating network services securely over an unsecured network.
- Application that implement ssh protocol including:
  - `ssh` (provided by `openssh-client` package) and `sshd` (provided by `openssh-server` package)
  - `dropbear`

## What does it do ?

- Remote connection.
- Files transfer
- Port forwarding
- Key Signing (git commit, ...)

## How to use it ?

### Quick start

```bash
ssh -p <port> <username>@<ip>
```

For example

```bash
ssh -p 10022 vancanh.ng@107.98.150.183
```

> [!NOTE]
> By default `ssh` uses port **22**.
> So you can skip `-p 22` if the ssh server is running at port 22.

### Public and private keys

1. Generate a key with optional email
   ```bash
   ssh-keygen -t ed25519 -C "vancanh.ng@samsung.com"
   ```
   You will be ask key key name and password.
   You can keep everything as default or change it as you like.
2. Check Generated keys
   ```bash
   ls ~/.ssh
   ```
   You should see your private key `id_ed25519` and public key `id_ed25519.pub`
3. Copy **public key** to the server
   ```bash
   ssh-copy-id -p 10022 vancanh.ng@107.98.150.183
   ```
4. Connect using **private key**.
   ```bash
   ssh -p 10022 vancanh.ng@107.98.150.183
   ```
   Now you should not be ask for the server password.

### SSH config

1. Edit `~/.ssh/config` file
   ```bash
   nvim ~/.ssh/config
   ```
2. Add host.
   ```
   Host playground
     HostName 107.98.150.183
     User vancanh.ng
     Port 10022
   ```
   > [!NOTE]
   > Change **playground** to what ever you like
3. Connect to host
   ```bash
   ssh playground
   ```
