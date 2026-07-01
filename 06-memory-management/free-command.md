# free Command

## Overview

The `free` command displays information about **system memory (RAM)** and **swap memory**.

It provides a quick summary of:

* Total memory
* Used memory
* Free memory
* Shared memory
* Buffer/Cache memory
* Available memory
* Swap usage

The `free` command is commonly used to monitor memory usage and troubleshoot performance issues on Linux systems.

---

# Why Use the free Command?

The `free` command helps administrators to:

* Check available RAM
* Monitor memory usage
* Verify swap usage
* Troubleshoot memory-related issues
* Monitor server health

---

# Syntax

```bash id="jlwm01"
free [options]
```

---

# Display Memory Information

```bash id="jlwm02"
free
```

Example Output

```text id="jlwm03"
               total        used        free      shared  buff/cache   available
Mem:         8059276     2523148     1658720      154720      3877408      5062480
Swap:        2097148           0     2097148
```

---

# Understanding the Output

| Column         | Description                                                                                    |
| -------------- | ---------------------------------------------------------------------------------------------- |
| **total**      | Total installed physical memory (RAM).                                                         |
| **used**       | Memory currently being used by processes, the kernel, and system resources.                    |
| **free**       | Memory that is completely unused.                                                              |
| **shared**     | Memory shared between processes (commonly used with shared memory and temporary file systems). |
| **buff/cache** | Memory used for disk buffers and file cache to improve performance.                            |
| **available**  | Memory that can be allocated to new applications without significant performance impact.       |

---

# Memory Layout

```text id="jlwm04"
Total RAM
│
├── Used Memory
├── Free Memory
├── Buffers / Cache
└── Available Memory
```

Linux uses unused RAM for **buffers** and **cache** to improve system performance.

If an application needs more memory, the kernel can reclaim this cached memory automatically.

---

# Display Human-Readable Output

```bash id="jlwm05"
free -h
```

Example Output

```text id="jlwm06"
               total   used   free  shared  buff/cache  available
Mem:            7.7G   2.4G   1.6G    151M      3.7G        4.9G
Swap:           2.0G     0B   2.0G
```

The `-h` option displays values in KB, MB, or GB, making the output easier to read.

---

# Display Memory in Megabytes

```bash id="jlwm07"
free -m
```

Example

```text id="’wini08"
Mem:  7970  2430  1610 ...
```

---

# Display Memory in Gigabytes

```bash id="’wini09"
free -g
```

---

# Display Memory in Bytes

```bash id="’wini10"
free -b
```

---

# Refresh Memory Information Continuously

```bash id="’wini11"
free -s 2
```

This refreshes the output every **2 seconds**.

Press **Ctrl + C** to stop.

---

# Understanding Swap

Example Output

```text id="’wini12"
Swap:
total   2.0G
used    512M
free    1.5G
```

| Field     | Meaning                     |
| --------- | --------------------------- |
| **total** | Total swap space available. |
| **used**  | Swap currently in use.      |
| **free**  | Remaining swap space.       |

High swap usage may indicate that the system is running low on available RAM.

---

# Which Memory Value Should You Check?

Many beginners focus on the **free** column.

Instead, the most useful value is:

```text id="’wini13"
available
```

Why?

* **Free** = Memory that is completely unused.
* **Available** = Memory that can be used immediately, including reclaimable cache.

A low **free** value is not necessarily a problem if the **available** memory is still healthy.

---

# Common free Command Options

| Command     | Description                     |
| ----------- | ------------------------------- |
| `free`      | Display memory information.     |
| `free -h`   | Human-readable output.          |
| `free -m`   | Display memory in MB.           |
| `free -g`   | Display memory in GB.           |
| `free -b`   | Display memory in bytes.        |
| `free -s 2` | Refresh output every 2 seconds. |

---

# Real-World DevOps Use Cases

* Check memory usage on production servers.
* Monitor swap usage after deploying applications.
* Verify available RAM before starting memory-intensive jobs.
* Troubleshoot high memory consumption.
* Monitor EC2 instances and Linux virtual machines.

---

# Best Practices

* Prefer `free -h` for readability.
* Monitor the **available** column instead of only the **free** column.
* Investigate high swap usage if applications become slow.
* Combine `free` with `top`, `htop`, or `vmstat` for deeper analysis.

---

# Interview Questions

### What does the `free` command do?

It displays information about physical memory (RAM) and swap memory.

---

### Which option displays memory in a human-readable format?

```bash id="’wini14"
free -h
```

---

### What is the difference between **free** and **available** memory?

* **Free** is completely unused RAM.
* **Available** is the amount of memory that can be allocated to new applications without significant performance impact.

---

### What does the `buff/cache` column represent?

It represents memory used for file caching and disk buffers to improve system performance.

---

### Which column is most useful when checking if a system has enough memory?

```text id="’wini15"
available
```

---

### How do you continuously monitor memory usage?

```bash id="’wini16"
free -s 2
```

---

# Key Takeaways

* The `free` command provides a summary of RAM and swap usage.
* Use `free -h` for human-readable output.
* Focus on the **available** column rather than only the **free** column.
* Linux uses unused RAM for caching and buffering to improve performance.
* The `free` command is one of the first tools used to troubleshoot memory issues on Linux systems.
