# Disk Partitioning and Mounting

## Overview

Before a new storage device can be used in Linux, it typically goes through the following steps:

1. Detect the disk.
2. Create a partition.
3. Create a filesystem.
4. Mount the filesystem.
5. Configure automatic mounting after reboot.

This is one of the most common storage administration tasks performed by Linux administrators and DevOps engineers.

---

# Complete Workflow

```text
New Disk
   │
   ▼
lsblk
   │
   ▼
fdisk
(Create Partition)
   │
   ▼
mkfs
(Create Filesystem)
   │
   ▼
mount
(Mount Filesystem)
   │
   ▼
Verify
(df -h / lsblk -f)
   │
   ▼
/etc/fstab
(Persistent Mount)
```

---

# Step 1: Verify the New Disk

Display all connected storage devices.

```bash
lsblk
```

Example Output

```text
NAME   SIZE TYPE MOUNTPOINT
sda     50G disk
├─sda1  49G part /
└─sda2   1G part [SWAP]

sdb    100G disk
```

In this example:

```text
/dev/sdb
```

is the new disk.

---

# Step 2: Create a Partition Using fdisk

Start fdisk.

```bash
sudo fdisk /dev/sdb
```

Common interactive commands:

| Command | Description             |
| ------- | ----------------------- |
| `m`     | Display help            |
| `p`     | Display partition table |
| `n`     | Create a new partition  |
| `d`     | Delete a partition      |
| `w`     | Write changes and exit  |
| `q`     | Quit without saving     |

Example:

```text
Command (m for help): n
Partition type: primary
Partition number: 1
First sector: Enter
Last sector: Enter

Command (m for help): w
```

After saving:

```text
/dev/sdb1
```

is created.

---

# Step 3: Create a Filesystem

A partition cannot store files until it has a filesystem.

Create an ext4 filesystem:

```bash
sudo mkfs.ext4 /dev/sdb1
```

Create an XFS filesystem:

```bash
sudo mkfs.xfs /dev/sdb1
```

---

# Step 4: Create a Mount Point

A mount point is a directory where the filesystem will be attached.

Example:

```bash
sudo mkdir /data
```

---

# Step 5: Mount the Filesystem

Mount the partition.

```bash
sudo mount /dev/sdb1 /data
```

Now the storage is accessible through:

```text
/data
```

---

# Step 6: Verify the Mount

Display mounted filesystems.

```bash
df -h
```

or

```bash
lsblk -f
```

Example:

```text
Filesystem      Size Used Avail Mounted on
/dev/sdb1       100G   1G   99G /data
```

---

# Unmount a Filesystem

Before removing a disk or performing maintenance, unmount it.

```bash
sudo umount /data
```

or

```bash
sudo umount /dev/sdb1
```

> **Note:** Ensure no process is using the filesystem before unmounting it.

---

# Why Do We Need /etc/fstab?

By default, manually mounted filesystems are **not mounted automatically after a reboot**.

The `/etc/fstab` file defines which filesystems should be mounted automatically during system startup.

---

# View fstab

```bash
cat /etc/fstab
```

Example Output

```text
UUID=8b7c9f4d-1234-5678-abcd-123456789abc /data ext4 defaults 0 2
```

---

# Understanding fstab Fields

| Field          | Description                             |
| -------------- | --------------------------------------- |
| Device or UUID | Storage device to mount                 |
| Mount Point    | Directory where it will be mounted      |
| Filesystem     | Filesystem type (ext4, xfs, etc.)       |
| Mount Options  | Mount options (for example, `defaults`) |
| Dump           | Backup option (usually `0`)             |
| Pass           | Filesystem check order during boot      |

---

# Why Use UUID Instead of Device Names?

Device names such as `/dev/sdb1` can change after a reboot or when new disks are added.

UUIDs are unique and remain consistent.

Display UUIDs:

```bash
blkid
```

Example:

```text
/dev/sdb1: UUID="8b7c9f4d-1234-5678-abcd-123456789abc" TYPE="ext4"
```

Example `fstab` entry:

```text
UUID=8b7c9f4d-1234-5678-abcd-123456789abc /data ext4 defaults 0 2
```

---

# Test fstab Before Rebooting

Always verify your `fstab` configuration.

```bash
sudo mount -a
```

If no errors are displayed, the configuration is likely correct.

---

# Common Commands

| Command                      | Description                          |
| ---------------------------- | ------------------------------------ |
| `lsblk`                      | Display block devices                |
| `sudo fdisk /dev/sdb`        | Partition a disk                     |
| `sudo mkfs.ext4 /dev/sdb1`   | Create an ext4 filesystem            |
| `sudo mkdir /data`           | Create a mount point                 |
| `sudo mount /dev/sdb1 /data` | Mount a filesystem                   |
| `sudo umount /data`          | Unmount a filesystem                 |
| `df -h`                      | Verify mounted filesystems           |
| `lsblk -f`                   | Display filesystems and mount points |
| `blkid`                      | Display UUID information             |
| `cat /etc/fstab`             | View automatic mount configuration   |
| `sudo mount -a`              | Test `fstab` entries                 |

---

# Real-World DevOps Use Cases

* Attach and configure a new AWS EBS volume.
* Add storage for application logs.
* Mount additional storage for databases.
* Configure persistent storage after server reboots.
* Verify storage during infrastructure provisioning.

---

# Best Practices

* Verify the correct disk using `lsblk` before partitioning.
* Back up important data before modifying partitions.
* Use UUIDs in `/etc/fstab` instead of device names.
* Test `fstab` with `sudo mount -a` before rebooting.
* Unmount filesystems before removing disks or performing maintenance.

---

# Interview Questions

### What is the purpose of `fdisk`?

`fdisk` is used to create, delete, and manage disk partitions.

---

### What is the difference between `mount` and `umount`?

* `mount` makes a filesystem accessible.
* `umount` safely detaches the filesystem from the directory tree.

---

### Why is a filesystem required after partitioning?

A partition must be formatted with a filesystem before it can store files.

---

### What is `/etc/fstab`?

`/etc/fstab` is a configuration file that defines which filesystems are mounted automatically during system startup.

---

### Why should UUIDs be used in `fstab`?

UUIDs remain consistent even if device names change after a reboot or when new disks are added.

---

### Which command tests `fstab` without rebooting?

```bash
sudo mount -a
```

---

# Key Takeaways

* Verify new disks using `lsblk`.
* Use `fdisk` to create partitions.
* Format partitions with a filesystem using `mkfs`.
* Mount filesystems using `mount`.
* Use `umount` before removing storage devices.
* Configure persistent mounts using `/etc/fstab`.
* Prefer UUIDs over device names in `/etc/fstab`.
* Test `fstab` with `sudo mount -a` before restarting the system.
