# Filesystem Types

## Overview

A **filesystem** is the method used by an operating system to organize, store, retrieve, and manage files on a storage device.

Without a filesystem, a disk is simply a collection of raw storage blocks, and the operating system cannot efficiently store or locate files.

Every partition must be formatted with a filesystem before it can be used.

---

# Why Do We Need a Filesystem?

A filesystem helps the operating system:

* Store files and directories.
* Organize data efficiently.
* Track free and used disk space.
* Manage file permissions and ownership.
* Recover data after unexpected shutdowns (depending on the filesystem).
* Improve performance and reliability.

---

# How a Filesystem Works

```text id="fs01"
Application
      │
      ▼
Operating System
      │
      ▼
Filesystem
      │
      ▼
Disk
```

The filesystem acts as a bridge between the operating system and the storage device.

---

# Common Linux Filesystem Types

| Filesystem | Description                                                 | Common Usage                        |
| ---------- | ----------------------------------------------------------- | ----------------------------------- |
| **ext4**   | Most widely used Linux filesystem.                          | Ubuntu, Debian                      |
| **XFS**    | High-performance journaling filesystem.                     | RHEL, Rocky Linux, AlmaLinux        |
| **Btrfs**  | Modern filesystem with advanced features such as snapshots. | Some enterprise and desktop systems |
| **ext3**   | Older journaling filesystem.                                | Legacy Linux systems                |
| **ext2**   | Older filesystem without journaling.                        | USB drives, legacy systems          |
| **swap**   | Special filesystem used for swap space.                     | Virtual memory                      |

---

# ext4

## Overview

**ext4 (Fourth Extended Filesystem)** is the most widely used filesystem on Linux.

It is the default filesystem for many Debian-based distributions.

### Features

* Journaling support
* High reliability
* Good performance
* Supports large files and volumes
* Fast recovery after crashes

### Common Use Cases

* Ubuntu servers
* Debian systems
* AWS EC2 instances
* General-purpose Linux installations

---

# XFS

## Overview

**XFS** is a high-performance journaling filesystem designed for handling very large files and filesystems.

It is the default filesystem on modern RHEL-based distributions.

### Features

* Excellent performance
* Fast for large files
* Scales well with large storage volumes
* Supports online filesystem expansion

### Common Use Cases

* RHEL
* Rocky Linux
* AlmaLinux
* Enterprise servers
* Database servers
* Large storage systems

---

# Btrfs

## Overview

**Btrfs (B-tree File System)** is a modern Linux filesystem with advanced storage management features.

### Features

* Snapshots
* Compression
* Checksums for data integrity
* Copy-on-write (CoW)
* Subvolumes

### Common Use Cases

* Backup systems
* Development environments
* Snapshot-based recovery
* Advanced storage management

---

# ext3

## Overview

**ext3** is an older journaling filesystem.

It was widely used before ext4 became the standard.

### Features

* Journaling
* Stable and reliable
* Good compatibility

Today, ext4 is generally preferred for new installations.

---

# ext2

## Overview

**ext2** is an older Linux filesystem that does not support journaling.

### Features

* Simple design
* Low overhead
* No journaling

### Common Use Cases

* Small USB drives
* Embedded systems
* Legacy environments

---

# swap

Swap is not a general-purpose filesystem for storing user files.

It is a dedicated area used by the Linux kernel as **virtual memory** when physical RAM is insufficient.

---

# What is Journaling?

A **journal** is a log that records pending filesystem changes before they are written to disk.

This helps the filesystem recover more quickly after:

* Power failures
* System crashes
* Unexpected shutdowns

Without journaling:

```text id="fs02"
Power Failure
      │
      ▼
Possible File Corruption
```

With journaling:

```text id="fs03"
Power Failure
      │
      ▼
Journal
      │
      ▼
Filesystem Recovery
```

---

# Display Filesystem Information

List mounted filesystems:

```bash id="fs04"
df -Th
```

Example Output

```text id="fs05"
Filesystem     Type   Size Used Avail Mounted on
/dev/sda1      ext4    50G  20G   28G /
```

List block devices and filesystems:

```bash id="fs06"
lsblk -f
```

Display filesystem type for a partition:

```bash id="fs07"
blkid
```

---

# Filesystem Comparison

| Feature             | ext4      | XFS                                    | Btrfs |
| ------------------- | --------- | -------------------------------------- | ----- |
| Journaling          | ✅         | ✅                                      | ✅     |
| Snapshots           | ❌         | ❌                                      | ✅     |
| Compression         | ❌         | ❌                                      | ✅     |
| Performance         | Excellent | Excellent (especially for large files) | Good  |
| Default on Ubuntu   | ✅         | ❌                                      | ❌     |
| Default on RHEL 8/9 | ❌         | ✅                                      | ❌     |

---

# Real-World DevOps Use Cases

* Format new AWS EBS volumes with `ext4` or `XFS`.
* Identify the filesystem type before resizing a volume.
* Choose `XFS` for enterprise workloads with large files.
* Use `ext4` for general-purpose Linux servers.
* Verify mounted filesystems during server troubleshooting.

---

# Best Practices

* Use **ext4** for most general Linux workloads.
* Use **XFS** for enterprise systems and large storage environments.
* Use **Btrfs** when features like snapshots or compression are required.
* Prefer journaling filesystems for production servers.
* Verify the filesystem type before performing maintenance operations.

---

# Interview Questions

### What is a filesystem?

A filesystem is the structure used by an operating system to organize, store, and retrieve files on a storage device.

---

### Why do we format a partition?

Formatting creates a filesystem on the partition so the operating system can store and manage data.

---

### Which filesystem is commonly used on Ubuntu?

```text id="fs08"
ext4
```

---

### Which filesystem is the default on modern RHEL systems?

```text id="fs09"
XFS
```

---

### What is journaling?

Journaling records pending filesystem changes before they are written to disk, helping the filesystem recover more quickly after crashes or power failures.

---

### Which filesystem supports snapshots?

```text id="fs10"
Btrfs
```

---

# Key Takeaways

* A filesystem organizes how data is stored and retrieved on a storage device.
* Every partition must be formatted with a filesystem before use.
* **ext4** is the most common filesystem for Ubuntu and Debian systems.
* **XFS** is the default filesystem for modern RHEL-based distributions.
* **Btrfs** provides advanced features such as snapshots and compression.
* Journaling improves reliability by helping filesystems recover after unexpected shutdowns.
