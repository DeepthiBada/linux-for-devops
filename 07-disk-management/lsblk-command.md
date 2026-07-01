# lsblk Command (List Block Devices)

## Overview

The `lsblk` (**List Block Devices**) command displays information about **block storage devices** connected to a Linux system.

It provides a tree-like view of:

* Disks
* Partitions
* Filesystems
* Mount points
* Storage device sizes

The `lsblk` command is commonly used to inspect storage devices before partitioning, formatting, or mounting them.

---

# What is a Block Device?

A **block device** is a storage device that reads and writes data in fixed-size blocks.

Examples include:

* Hard Disk Drives (HDD)
* Solid State Drives (SSD)
* NVMe SSDs
* USB Flash Drives
* External Hard Drives

Linux represents these devices under the `/dev` directory.

Examples:

```text id="ls01"
/dev/sda
/dev/sdb
/dev/nvme0n1
```

---

# Why Use lsblk?

The `lsblk` command helps administrators to:

* View connected disks.
* Display partitions.
* Check filesystem types.
* Verify mount points.
* Inspect storage layouts.
* Confirm that newly attached disks are detected.

---

# Syntax

```bash id="ls02"
lsblk [options]
```

---

# Display Block Devices

```bash id="ls03"
lsblk
```

Example Output

```text id="ls04"
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
sda           8:0    0   50G  0 disk
├─sda1        8:1    0   49G  0 part /
└─sda2        8:2    0    1G  0 part [SWAP]

sdb           8:16   0  100G  0 disk

nvme0n1     259:0    0  500G  0 disk
└─nvme0n1p1 259:1    0  500G  0 part /data
```

---

# Understanding the Output

| Column         | Description                               |
| -------------- | ----------------------------------------- |
| **NAME**       | Device or partition name                  |
| **MAJ:MIN**    | Major and minor device numbers            |
| **RM**         | Removable device (1 = Yes, 0 = No)        |
| **SIZE**       | Device or partition size                  |
| **RO**         | Read-only status                          |
| **TYPE**       | Device type (`disk`, `part`, `lvm`, etc.) |
| **MOUNTPOINT** | Directory where the filesystem is mounted |

---

# Display Filesystem Information

```bash id="ls05"
lsblk -f
```

Example Output

```text id="ls06"
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda
├─sda1 ext4         1f2b3c4d-5678-90ab-cdef-123456789abc /
└─sda2 swap         9abc1234-def5-6789-abcd-ef1234567890 [SWAP]
```

The `-f` option displays:

* Filesystem type
* UUID
* Label
* Mount point

---

# Display Device Sizes Only

```bash id="ls07"
lsblk -b
```

Displays sizes in bytes.

---

# Display Specific Columns

```bash id="ls08"
lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT
```

Example Output

```text id="ls09"
NAME         SIZE FSTYPE MOUNTPOINT
sda           50G
├─sda1        49G ext4   /
└─sda2         1G swap   [SWAP]
```

---

# Display All Block Devices

```bash id="ls10"
lsblk -a
```

Includes empty or hidden devices.

---

# Typical Workflow After Attaching a New Disk

Step 1: Verify the new disk

```bash id="ls11"
lsblk
```

Example:

```text id="ls12"
sda    50G
sdb   100G
```

Here, `/dev/sdb` is the newly attached disk.

Step 2: Create a partition (using `fdisk` or `parted`).

Step 3: Create a filesystem.

Step 4: Mount the filesystem.

Step 5: Verify the mount.

```bash id="ls13"
lsblk -f
```

---

# Common lsblk Commands

| Command                                | Description                    |
| -------------------------------------- | ------------------------------ |
| `lsblk`                                | Display block devices          |
| `lsblk -f`                             | Display filesystem information |
| `lsblk -b`                             | Display sizes in bytes         |
| `lsblk -a`                             | Display all devices            |
| `lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT` | Display selected columns       |

---

# lsblk vs df

| lsblk                         | df                             |
| ----------------------------- | ------------------------------ |
| Displays disks and partitions | Displays filesystem usage      |
| Shows storage layout          | Shows available and used space |
| Useful before mounting        | Useful after mounting          |

---

# Real-World DevOps Use Cases

* Verify a newly attached AWS EBS volume.
* Inspect storage devices before partitioning.
* Confirm filesystem types.
* Verify mount points after mounting a disk.
* Audit storage layouts on production servers.

---

# Best Practices

* Run `lsblk` after attaching a new disk to verify that Linux has detected it.
* Use `lsblk -f` to check filesystem types and mount points.
* Verify device names carefully before formatting or partitioning.
* Combine `lsblk` with `df`, `blkid`, and `fdisk` for complete storage information.

---

# Interview Questions

### What does the `lsblk` command do?

It displays information about block storage devices, including disks, partitions, filesystems, and mount points.

---

### Which option displays filesystem information?

```bash id="ls14"
lsblk -f
```

---

### Which column displays the mount point?

```text id="ls15"
MOUNTPOINT
```

---

### Which command displays only selected columns?

```bash id="ls16"
lsblk -o NAME,SIZE,FSTYPE,MOUNTPOINT
```

---

### What is the difference between `lsblk` and `df`?

* `lsblk` displays storage devices and partitions.
* `df` displays disk usage for mounted filesystems.

---

### What should you do after attaching a new disk to a Linux server?

1. Verify the disk using `lsblk`.
2. Create a partition.
3. Create a filesystem.
4. Mount the filesystem.
5. Verify the mount.

---

# Key Takeaways

* `lsblk` displays block devices connected to the system.
* It provides a tree view of disks and partitions.
* Use `lsblk -f` to display filesystem types and mount points.
* `lsblk` is commonly used before partitioning, formatting, or mounting storage devices.
* It is one of the first commands used after attaching new storage to Linux servers or cloud instances.
