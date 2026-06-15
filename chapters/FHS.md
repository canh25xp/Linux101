# File Hierarchy Standard (FHS)

## The root `/` directory

```
/
├── bin -> usr/bin         Binaries (User)
├── boot                   Static boot loader files
├── dev                    Devices: representing hardware and virtual devices attached to the system
├── etc                    System specific configs
├── home                   User homes
├── lib -> usr/lib         Shared libraries and kernel modules
├── lib64 -> usr/lib64     Shared libraries and kernel modules (64-bit)
├── media                  Mountpoint for external drives
├── mnt                    Mountpoint for internal drives
├── opt                    Optional: is intended for add-on software packages
├── proc                   Running processes
├── root                   Root's home
├── run                    PID files of running processes
├── sbin -> usr/sbin       Binaries (System/root)
├── srv                    Network mount
├── sys                    Pseudo file system
├── tmp                    Temporary files,
├── usr                    3rd party software
└── var                    Varying files (e.g. Logs, Caches)
```

## The home `~` directory

```
.
├── .bash_history         Commands history
├── .bash_logout          Run on bash log out
├── .bash_profile         Run on bash log in
├── .bashrc               Run on bash interactive shell
├── .cache                Caches
├── .config               Application configuration files
└── .local                User-specific application data and binaries
    ├── bin               User-specific binaries
    ├── lib               User-specific libraries
    ├── opt               User-specific optional software
    ├── share             User-specific application persistant data (usually portable)
    └── state             User-specific User-specific state information (usually not portable)
```
