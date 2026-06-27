# Linux File System

## What is the Linux File System?

The Linux file system is a hierarchical directory structure used to organize and manage files and directories. Unlike Windows, Linux stores everything under a single root directory (`/`).

> **Key Point:** In Linux, everything is treated as a file, including hardware devices, disks, and processes.

---

# Linux File System Hierarchy

```
/
├── bin
├── boot
├── dev
├── etc
├── home
├── lib
├── media
├── mnt
├── opt
├── proc
├── root
├── run
├── sbin
├── srv
├── sys
├── tmp
├── usr
└── var
```

---

# Important Directories

## /

* Root directory of the Linux file system.
* Every file and directory starts from here.

Example:

```bash
cd /
```

---

## /home

* Contains personal directories for normal users.
* Stores user documents, downloads, and personal files.

Example:

```
/home/deepthi
```

---

## /root

* Home directory of the root (administrator) user.
* Accessible only by the root user or users with elevated privileges.

---

## /bin

* Contains essential user commands.
* Commands are available to all users.

Examples:

```
ls
cp
mv
cat
pwd
echo
```

---

## /sbin

* Contains system administration commands.
* Primarily used by the root user.

Examples:

```
fdisk
reboot
shutdown
mount
```

---

## /etc

* Stores system-wide configuration files.
* One of the most frequently accessed directories by system administrators.

Examples:

```
/etc/passwd
/etc/hosts
/etc/ssh/
/etc/fstab
```

---

## /var

* Stores files that change frequently.

Contains:

* Log files
* Mail
* Cache
* Spool files

Examples:

```
/var/log/
/var/cache/
/var/spool/
```

---

## /tmp

* Stores temporary files.
* Files may be deleted automatically after a reboot.

---

## /usr

* Contains user applications, libraries, and documentation.
* Usually the largest directory on a Linux system.

Examples:

```
/usr/bin
/usr/lib
/usr/share
```

---

## /boot

* Contains files required to boot the operating system.

Examples:

* Linux kernel
* GRUB bootloader

---

## /dev

* Contains device files.
* Hardware devices are represented as files.

Examples:

```
/dev/sda
/dev/null
/dev/tty
```

---

## /proc

* Virtual file system containing process and kernel information.
* Files are generated dynamically by the kernel.

Examples:

```
/proc/cpuinfo
/proc/meminfo
/proc/version
```

---

## /opt

* Used for installing optional or third-party software.

Example:

```
/opt/google
```

---

## /media

* Automatically mounts removable devices.

Examples:

* USB drives
* DVDs

---

## /mnt

* Used for manually mounting file systems.

Example:

```bash
mount /dev/sdb1 /mnt
```

---

# Linux File System Characteristics

* Hierarchical directory structure
* Case-sensitive file names
* Everything is treated as a file
* Supports multiple users
* Secure permission model
* Supports symbolic and hard links

---

# Quick Summary

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/`       | Root directory                 |
| `/home`   | User home directories          |
| `/root`   | Root user's home               |
| `/bin`    | Essential user commands        |
| `/sbin`   | System administration commands |
| `/etc`    | Configuration files            |
| `/var`    | Logs and variable data         |
| `/tmp`    | Temporary files                |
| `/usr`    | Applications and libraries     |
| `/boot`   | Boot files                     |
| `/dev`    | Device files                   |
| `/proc`   | Process and kernel information |
| `/opt`    | Optional software              |
| `/media`  | Removable media                |
| `/mnt`    | Temporary mount point          |

---

# Interview Questions

### 1. What is the root directory in Linux?

The root directory (`/`) is the top-level directory from which all other directories originate.

---

### 2. What is the difference between `/home` and `/root`?

* `/home` contains home directories for regular users.
* `/root` is the home directory of the root (administrator) user.

---

### 3. Where are Linux log files stored?

Most system and application logs are stored in:

```
/var/log
```

---

### 4. Which directory contains configuration files?

```
/etc
```

---

### 5. What is stored in `/proc`?

Runtime information about processes and the Linux kernel.

---

# Real-World DevOps Use Cases

* Check application logs in `/var/log` during troubleshooting.
* Update configuration files in `/etc`.
* Store deployment scripts under `/opt`.
* Verify disk mounts using `/mnt`.
* Monitor system resources using files in `/proc`.
* Access user application files in `/home`.

---

# Key Takeaways

* Linux follows a single hierarchical directory structure.
* Everything begins at the root directory (`/`).
* Understanding the purpose of major directories is essential for system administration and DevOps.
* Knowing where configuration files, logs, binaries, and user data are stored makes troubleshooting and server management much easier.
