# df Command (Disk Filesystem)

## Overview

The `df` (**Disk Filesystem**) command displays information about **disk space usage** for mounted filesystems.

It helps administrators determine:

* Total disk space
* Used disk space
* Available disk space
* Filesystem type
* Mount points
* Disk usage percentage

The `df` command is commonly used to monitor storage utilization and identify filesystems that are running out of space.

---

# Why Use the df Command?

The `df` command helps administrators to:

* Monitor disk usage.
* Check available storage space.
* Identify full filesystems.
* Verify mounted filesystems.
* Troubleshoot "No space left on device" errors.

---

# Syntax

```bash id="df01"
df [options]
```

---

# Display Disk Usage

```bash id="df02"
df
```

Example Output

```text id="df03"
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1       52428800 20971520  28835840   43% /
```

---

# Understanding the Output

| Column         | Description                               |
| -------------- | ----------------------------------------- |
| **Filesystem** | Storage device or filesystem name         |
| **1K-blocks**  | Total filesystem size in 1 KB blocks      |
| **Used**       | Disk space currently in use               |
| **Available**  | Free disk space available                 |
| **Use%**       | Percentage of disk space used             |
| **Mounted on** | Directory where the filesystem is mounted |

---

# Display Human-Readable Output

```bash id="df04"
df -h
```

Example Output

```text id="df05"
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  43% /
```

The `-h` option displays sizes in KB, MB, GB, or TB, making the output easier to read.

---

# Display Filesystem Types

```bash id="df06"
df -Th
```

Example Output

```text id="df07"
Filesystem     Type  Size Used Avail Use% Mounted on
/dev/sda1      ext4   50G  20G   28G  43% /
```

The `-T` option displays the filesystem type.

---

# Display Disk Usage for a Specific Filesystem

```bash id="df08"
df -h /
```

Example Output

```text id="df09"
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1        50G   20G   28G  43% /
```

---

# Display Inode Usage

Filesystems also have a limited number of **inodes**.

Check inode usage with:

```bash id="df10"
df -i
```

Example Output

```text id="df11"
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/dev/sda1      3276800 120000 3156800    4% /
```

---

# What is an Inode?

An **inode** is a data structure that stores metadata about a file, such as:

* File owner
* Permissions
* File size
* Timestamps
* File location on disk

Each file consumes one inode.

A filesystem can run out of **inodes** even if disk space is still available.

---

# Common df Options

| Command   | Description                                       |
| --------- | ------------------------------------------------- |
| `df`      | Display filesystem usage                          |
| `df -h`   | Human-readable output                             |
| `df -T`   | Display filesystem types                          |
| `df -Th`  | Display filesystem types in human-readable format |
| `df -i`   | Display inode usage                               |
| `df -h /` | Display usage for the root filesystem             |

---

# Typical Workflow

Display all mounted filesystems

```bash id="df12"
df -h
```

Display filesystem types

```bash id="df13"
df -Th
```

Check inode usage

```bash id="df14"
df -i
```

Check the root filesystem

```bash id="df15"
df -h /
```

---

# df vs du

| df                                     | du                                                        |
| -------------------------------------- | --------------------------------------------------------- |
| Shows filesystem usage                 | Shows directory or file usage                             |
| Reports total and available disk space | Reports the size of files and directories                 |
| Used to identify full filesystems      | Used to identify which directories consume the most space |

Example:

```bash id="df16"
df -h
```

Displays:

```text id="df17"
Filesystem usage
```

```bash id="df18"
du -sh /var/log
```

Displays:

```text id="df19"
Directory size
```

---

# Real-World DevOps Use Cases

* Check disk space before deployments.
* Investigate "Disk Full" alerts.
* Verify mounted EBS volumes on AWS EC2.
* Monitor storage utilization on production servers.
* Check inode usage when applications cannot create new files.

---

# Best Practices

* Use `df -h` for readable output.
* Monitor filesystems regularly to prevent outages.
* Investigate filesystems with high **Use%** values.
* Check inode usage with `df -i` if disk space appears available but file creation fails.
* Use `du` to identify directories consuming excessive disk space.

---

# Interview Questions

### What does the `df` command do?

It displays disk space usage information for mounted filesystems.

---

### Which option displays human-readable output?

```bash id="df20"
df -h
```

---

### Which option displays filesystem types?

```bash id="df21"
df -T
```

or

```bash id="df22"
df -Th
```

---

### What is an inode?

An inode is a data structure that stores metadata about a file, including ownership, permissions, timestamps, and the location of the file's data.

---

### What is the difference between `df` and `du`?

* `df` displays filesystem-level disk usage.
* `du` displays the size of files and directories.

---

### Why might a filesystem report "No space left on device" even when `df` shows free space?

Because the filesystem may have exhausted its available **inodes**, preventing the creation of new files.

---

# Key Takeaways

* `df` displays disk usage for mounted filesystems.
* Use `df -h` for human-readable output.
* Use `df -Th` to display filesystem types.
* Use `df -i` to check inode usage.
* `df` reports filesystem usage, while `du` reports directory and file usage.
* Monitoring disk space and inode usage is essential for maintaining healthy Linux systems.
