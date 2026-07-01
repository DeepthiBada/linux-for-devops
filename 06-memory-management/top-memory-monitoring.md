# Memory Monitoring Using top

## Overview

The `top` command is a real-time system monitoring tool that displays information about:

* CPU usage
* Memory usage
* Swap usage
* Running processes
* Process IDs (PID)
* System load

It is one of the first commands used by Linux administrators and DevOps engineers to identify performance issues and resource-intensive processes.

---

# Why Use top?

The `top` command helps to:

* Monitor memory usage in real time
* Identify processes consuming the most RAM
* Monitor CPU utilization
* Detect high system load
* Troubleshoot slow or unresponsive servers

---

# Syntax

```bash id="jlwm17"
top
```

---

# Sample Output

```text id="jlwm18"
top - 10:30:15 up 5 days,  2 users,  load average: 0.45, 0.38, 0.29

Tasks: 165 total, 1 running, 164 sleeping

%Cpu(s): 5.2 us, 1.0 sy, 93.8 id

MiB Mem : 7970 total, 2450 used, 1600 free, 3920 buff/cache

MiB Swap: 2048 total, 0 used, 2048 free

 PID USER     PR NI    VIRT    RES    SHR S %CPU %MEM TIME+ COMMAND
2541 java     20  0   2500M   820M   120M S 18.5 10.3 10:15 java
1985 nginx    20  0    120M    35M    12M S  2.0  0.4 00:30 nginx
```

---

# Understanding the Memory Section

```text id="jlwm19"
MiB Mem :

total
used
free
buff/cache
```

| Field          | Description                            |
| -------------- | -------------------------------------- |
| **total**      | Total installed RAM                    |
| **used**       | Memory currently in use                |
| **free**       | Completely unused memory               |
| **buff/cache** | Memory used for buffers and file cache |

---

# Understanding the Process Columns

| Column      | Description                                   |
| ----------- | --------------------------------------------- |
| **PID**     | Process ID                                    |
| **USER**    | Owner of the process                          |
| **PR**      | Process priority                              |
| **NI**      | Nice value                                    |
| **VIRT**    | Total virtual memory used by the process      |
| **RES**     | Physical RAM currently used (Resident Memory) |
| **SHR**     | Shared memory used by the process             |
| **S**       | Process state (R, S, D, T, Z)                 |
| **%CPU**    | CPU utilization                               |
| **%MEM**    | Percentage of RAM used                        |
| **TIME+**   | Total CPU time consumed                       |
| **COMMAND** | Process name                                  |

---

# Important Memory Columns

## VIRT (Virtual Memory)

Represents the total virtual memory allocated to the process.

It includes:

* Physical RAM
* Shared libraries
* Memory-mapped files
* Swapped memory
* Reserved memory

---

## RES (Resident Memory)

Represents the actual physical RAM currently occupied by the process.

This is the most useful value when checking how much memory a process is actively using.

---

## SHR (Shared Memory)

Represents memory shared with other processes.

Examples:

* Shared libraries
* Common system resources

---

## %MEM

Shows the percentage of total physical RAM used by the process.

Example:

```text id="jlwm20"
Java Process

RAM Used : 820 MB

%MEM : 10.3
```

---

# Sort Processes by Memory Usage

While `top` is running, press:

```text id="jlwm21"
M
```

This sorts processes by **memory usage** (highest first).

---

# Sort Processes by CPU Usage

Press:

```text id="’wini22"
P
```

---

# Kill a Process

Press:

```text id="’wini23"
k
```

Enter:

```text id="’wini24"
PID
```

Example:

```text id="’wini25"
2458
```

Then enter the signal number (default is **15** for `SIGTERM`).

---

# Useful Keyboard Shortcuts

| Key | Action               |
| --- | -------------------- |
| `M` | Sort by memory usage |
| `P` | Sort by CPU usage    |
| `k` | Kill a process       |
| `h` | Display help         |
| `q` | Quit `top`           |

---

# Alternative Commands

Display processes sorted by memory usage:

```bash id="’wini26"
ps aux --sort=-%mem
```

Display the top 10 memory-consuming processes:

```bash id="’wini27"
ps aux --sort=-%mem | head
```

---

# Real-World DevOps Use Cases

* Identify a Java application consuming excessive memory.
* Monitor memory usage after a deployment.
* Detect memory leaks in long-running applications.
* Investigate high swap usage.
* Find memory-intensive processes on EC2 instances or Linux servers.

---

# Best Practices

* Focus on the **RES** and **%MEM** columns when analyzing memory usage.
* Use `M` to quickly identify high-memory processes.
* Confirm process details before terminating them.
* Combine `top` with `free` and `vmstat` for comprehensive memory analysis.

---

# Interview Questions

### What does the `top` command do?

It provides a real-time view of system performance, including CPU, memory, swap usage, and running processes.

---

### Which key sorts processes by memory usage?

```text id="’wini28"
M
```

---

### What is the difference between **VIRT** and **RES**?

* **VIRT**: Total virtual memory allocated to the process.
* **RES**: Physical RAM currently used by the process.

---

### Which column shows the percentage of RAM used?

```text id="’wini29"
%MEM
```

---

### Which command lists processes sorted by memory usage?

```bash id="’wini30"
ps aux --sort=-%mem
```

---

# Key Takeaways

* `top` is a real-time monitoring tool for CPU, memory, and processes.
* Use **`M`** to sort processes by memory usage.
* **RES** shows actual physical RAM used by a process.
* **VIRT** represents total virtual memory allocated.
* **%MEM** indicates how much RAM a process is consuming.
* `top` is one of the most important commands for troubleshooting Linux performance issues.
