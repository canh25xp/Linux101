# File Hierarchy Standard (FHS)

## The root `/` directory

```
/
├── bin -> usr/bin
├── boot
├── dev
├── etc
├── home
├── lib -> usr/lib
├── lib64 -> usr/lib64
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin -> usr/sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

| Path     | Content                                                                   |
| -------- | ------------------------------------------------------------------------- |
| `/bin`   | Binaries (User)                                                           |
| `/boot`  | Static boot loader files                                                  |
| `/dev`   | Devices: representing hardware and virtual devices attached to the system |
| `/etc`   | System specific configs                                                   |
| `/home`  | User homes                                                                |
| `/lib`   | Shared libraries and kernel modules                                       |
| `/lib64` | Shared libraries and kernel modules (64-bit)                              |
| `/media` | Mountpoint for external drives                                            |
| `/mnt`   | Mountpoint for internal drives                                            |
| `/opt`   | Optional: is intended for add-on software packages                        |
| `/proc`  | Running processes                                                         |
| `/root`  | Root's home                                                               |
| `/run`   | PID files of running processes                                            |
| `/sbin`  | Binaries (System/root)                                                    |
| `/sys`   | Pseudo file system                                                        |
| `/usr`   | 3rd party software                                                        |
| `/var`   | Varying files (e.g. Logs, Caches)                                         |

## The home `~` directory
