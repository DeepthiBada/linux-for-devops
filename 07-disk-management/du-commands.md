# du Command (Disk Usage)

## Overview

The `du` (**Disk Usage**) command displays the amount of disk space used by files and directories.

Unlike the `df` command, which reports usage for an entire filesystem, `du` helps identify **which files or directories are consuming disk space**.

It is one of the most commonly used commands for troubleshooting storage issues on Linux systems.

---

# Why Use the du Command?

The `du` command helps administrators to:

* Find large directories.
* Identify files consuming excessive storage.
* Troubleshoot "Disk Full" issues.
* Analyze storage usage.
* Monitor application log directories.

---

# Syntax

```bash
du [options] <file_or_directory>
```

---

# Display Directory Size

```bash
du
```

Displays the disk usage of the current directory and its subdirectories.

---

# Display Human-Readable Output

```bash
du -h
```

Example Output

```text
4.0K    ./docs
8.0K    ./scripts
120M    ./logs
130M    .
```

The `-h` option displays sizes in KB, MB, GB, or TB.

---

# Display Summary Only

Instead of displaying every subdirectory:

```bash
du -sh
```

Example Output

```text
2.5G    .
```

Options:

* `-s` → Summary only
* `-h` → Human-readable

---

# Check a Specific Directory

```bash
du -sh /var/log
```

Example Output

```text
3.8G    /var/log
```

---

# Display All Directories Under Root

```bash
sudo du -sh /*
```

Example Output

```text
1.2G    /boot
2.5G    /etc
18G     /home
40G     /var
```

This command is very useful for identifying which top-level directory is consuming the most disk space.

---

# Display Maximum Directory Sizes

```bash
du -h --max-depth=1
```

Example Output

```text
600M    ./logs
150M    ./images
2.0G    ./backup
```

The `--max-depth` option limits how many directory levels are displayed.

---

# Find the Largest Directories

```bash
du -sh * | sort -hr
```

Example Output

```text
18G     backup
6.4G    logs
2.3G    images
```

Options:

* `sort -h` → Sort human-readable sizes.
* `-r` → Reverse order (largest first).

---

# Find the Largest Files

```bash
find . -type f -exec du -h {} + | sort -hr | head
```

This displays the largest files in the current directory.

---

# Common du Options

| Command                | Description                          |
| ---------------------- | ------------------------------------ |
| `du`                   | Display directory usage              |
| `du -h`                | Human-readable output                |
| `du -sh`               | Display summary only                 |
| `du -sh /var/log`      | Display size of a specific directory |
| `du -h --max-depth=1`  | Show one directory level             |
| `du -sh * \| sort -hr` | Sort directories by size             |

---

# Typical Workflow

Check filesystem usage

```bash
df -h
```

Identify large directories

```bash
sudo du -sh /*
```

Check a specific directory

```bash
du -sh /var/log
```

Find the largest directories

```bash
du -sh * | sort -hr
```

---

# du vs df

| du                                     | df                                      |
| -------------------------------------- | --------------------------------------- |
| Displays file and directory sizes      | Displays filesystem usage               |
| Helps identify what is consuming space | Helps identify which filesystem is full |
| Works on directories and files         | Works on mounted filesystems            |

---

# Real-World DevOps Use Cases

* Identify large log directories.
* Analyze application storage usage.
* Troubleshoot "Disk Full" alerts.
* Find old backup files consuming storage.
* Monitor log growth after deployments.

---

# Best Practices

* Use `du -sh` for a quick directory summary.
* Combine `du` with `sort` to identify the largest directories.
* Use `sudo` when checking system directories to avoid permission issues.
* Start with top-level directories before investigating subdirectories.
* Use `df` first to identify the affected filesystem, then `du` to locate the source of the usage.

---

# Interview Questions

### What does the `du` command do?

It displays the amount of disk space used by files and directories.

---

### Which option displays human-readable output?

```bash
du -h
```

---

### Which command displays only the total size of a directory?

```bash
du -sh
```

---

### How do you check the size of `/var/log`?

```bash
du -sh /var/log
```

---

### What is the difference between `du` and `df`?

* `du` reports the size of files and directories.
* `df` reports disk usage for mounted filesystems.

---

### How do you list directories from largest to smallest?

```bash
du -sh * | sort -hr
```

---

# Key Takeaways

* `du` displays the disk usage of files and directories.
* Use `du -sh` for a concise summary.
* Use `du -sh * | sort -hr` to identify the largest directories.
* Use `df` to determine which filesystem is full, then use `du` to find what is consuming the space.
* `du` is one of the most valuable commands for troubleshooting Linux storage issues.
