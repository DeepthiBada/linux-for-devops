# Disk Management Overview

## Overview

Disk management is the process of organizing, storing, and managing data on storage devices such as **Hard Disk Drives (HDDs)** and **Solid State Drives (SSDs)**.

Linux provides tools to:

* Detect storage devices
* Create partitions
* Format filesystems
* Mount storage devices
* Monitor disk usage
* Manage available storage space

Proper disk management ensures efficient storage utilization, system performance, and data reliability.

---

# What is a Disk?

A **disk** is a storage device used to permanently store data.

Unlike RAM, data stored on a disk remains available even after the system is powered off.

Common examples include:

* Hard Disk Drive (HDD)
* Solid State Drive (SSD)
* NVMe SSD
* USB Flash Drive
* External Hard Drive

---

# Types of Storage Devices

| Storage Device | Description                                                |
| -------------- | ---------------------------------------------------------- |
| HDD            | Mechanical storage using spinning magnetic disks.          |
| SSD            | Flash-based storage with no moving parts. Faster than HDD. |
| NVMe SSD       | High-speed SSD connected through the PCIe interface.       |
| USB Drive      | Portable removable storage device.                         |

---

# HDD vs SSD vs NVMe SSD

| Feature      | HDD   | SSD      | NVMe SSD  |
| ------------ | ----- | -------- | --------- |
| Speed        | Slow  | Fast     | Very Fast |
| Moving Parts | Yes   | No       | No        |
| Noise        | Yes   | No       | No        |
| Durability   | Lower | Higher   | Higher    |
| Cost         | Lower | Moderate | Higher    |

---

# How Linux Identifies Disks

Linux represents storage devices as files under the `/dev` directory.

Examples:

```text
/dev/sda
/dev/sdb
/dev/nvme0n1
```

Example:

```text
/dev/sda
│
├── sda1
├── sda2
└── sda3
```

Where:

* `sda` → Disk
* `sda1` → Partition 1
* `sda2` → Partition 2
* `sda3` → Partition 3

For NVMe drives:

```text
/dev/nvme0n1
│
├── nvme0n1p1
└── nvme0n1p2
```

---

# What is a Partition?

A **partition** is a logical division of a physical disk.

Partitions allow one disk to be divided into multiple independent storage areas.

Example:

```text
500 GB Disk

│
├── Partition 1 (100 GB)
├── Partition 2 (200 GB)
└── Partition 3 (200 GB)
```

Each partition can have its own filesystem.

---

# What is a Filesystem?

A **filesystem** defines how data is stored, organized, and retrieved on a storage device.

Without a filesystem, the operating system cannot efficiently store or access files.

Common Linux filesystems:

* ext4
* XFS
* Btrfs

---

# What is Mounting?

Before Linux can use a storage device, it must be **mounted**.

Mounting connects a filesystem to a directory in the Linux directory tree.

Example:

```text
Disk
 │
 ▼
Filesystem
 │
 ▼
Mount Point (/data)
 │
 ▼
Users Access Files
```

---

# Disk Management Workflow

```text
Disk
 │
 ▼
Partition
 │
 ▼
Filesystem
 │
 ▼
Mount
 │
 ▼
Store Files
```

---

# Common Disk Management Commands

| Command  | Purpose                      |
| -------- | ---------------------------- |
| `lsblk`  | Display disks and partitions |
| `df`     | Display filesystem usage     |
| `du`     | Display directory size       |
| `fdisk`  | Create and manage partitions |
| `mount`  | Mount a filesystem           |
| `umount` | Unmount a filesystem         |

---

# Real-World DevOps Use Cases

* Check available disk space before deployments.
* Identify disks attached to cloud instances.
* Mount additional EBS volumes on AWS EC2.
* Investigate "Disk Full" errors.
* Monitor storage usage on production servers.

---

# Best Practices

* Monitor disk usage regularly.
* Separate application data from the operating system when possible.
* Remove unnecessary files to free disk space.
* Verify available space before large deployments or backups.
* Use appropriate filesystems based on workload requirements.

---

# Interview Questions

### What is disk management?

Disk management is the process of organizing, monitoring, partitioning, formatting, and managing storage devices.

---

### What is the difference between RAM and a disk?

| RAM                     | Disk                                   |
| ----------------------- | -------------------------------------- |
| Temporary (volatile)    | Permanent (non-volatile)               |
| Very fast               | Slower than RAM                        |
| Stores running programs | Stores files and operating system data |

---

### What is a partition?

A partition is a logical division of a physical disk that allows separate storage areas on the same device.

---

### What is a filesystem?

A filesystem is the structure used by the operating system to store and organize files on a storage device.

---

### Why do we mount a filesystem?

A filesystem must be mounted so that Linux can access and use the data stored on it.

---

# Key Takeaways

* A disk is a permanent storage device.
* Linux identifies storage devices under the `/dev` directory.
* Partitions divide a physical disk into logical sections.
* A filesystem organizes how data is stored and retrieved.
* Filesystems must be mounted before they can be accessed.
* Disk management is a core Linux administration skill used in server management and DevOps.
