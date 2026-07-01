# vmstat Command

## Overview

The `vmstat` (**Virtual Memory Statistics**) command displays information about:

* Processes
* Memory
* Swap
* Disk I/O
* System activity
* CPU utilization

It provides a quick overview of the overall system performance and is commonly used for troubleshooting Linux servers.

---

# Why Use vmstat?

The `vmstat` command helps administrators to:

* Monitor memory usage
* Detect swap activity
* Analyze CPU utilization
* Identify disk I/O bottlenecks
* Troubleshoot performance issues
* Monitor running and blocked processes

---

# Syntax

```bash id="jlwm31"
vmstat [options]
```

---

# Display System Statistics

```bash id="jlwm32"
vmstat
```

Example Output

```text id="jlwm33"
procs -----------memory---------- ---swap-- -----io---- -system-- ------cpu------
 r  b swpd   free  buff  cache   si   so    bi    bo   in   cs us sy id wa st
 1  0    0 825000 43000 320000    0    0     2     5  120  220  5  2 92  1  0
```

---

# Understanding the Output

## Processes

| Column | Description                                          |
| ------ | ---------------------------------------------------- |
| `r`    | Number of runnable processes waiting for CPU time    |
| `b`    | Number of processes blocked, usually waiting for I/O |

### Interpretation

* High `r` → CPU may be overloaded.
* High `b` → Processes are waiting for disk or hardware operations.

---

## Memory

| Column  | Description                            |
| ------- | -------------------------------------- |
| `swpd`  | Amount of swap memory currently in use |
| `free`  | Completely unused physical RAM         |
| `buff`  | Memory used for disk buffers           |
| `cache` | Memory used for file caching           |

### Interpretation

* High `cache` is generally normal and improves performance.
* High `swpd` may indicate memory pressure.

---

## Swap

| Column | Description                                |
| ------ | ------------------------------------------ |
| `si`   | Swap In (memory read from swap to RAM)     |
| `so`   | Swap Out (memory written from RAM to swap) |

### Interpretation

```text id="jlwm34"
si = 0
so = 0
```

Ideal situation.

If `si` or `so` remain consistently high, the system may not have enough physical RAM.

---

## Disk I/O

| Column | Description                               |
| ------ | ----------------------------------------- |
| `bi`   | Blocks received from storage (disk reads) |
| `bo`   | Blocks sent to storage (disk writes)      |

### Interpretation

High values may indicate intensive disk activity.

---

## System

| Column | Description                           |
| ------ | ------------------------------------- |
| `in`   | Number of interrupts per second       |
| `cs`   | Number of context switches per second |

---

## CPU

| Column | Description                                          |
| ------ | ---------------------------------------------------- |
| `us`   | CPU time spent running user processes                |
| `sy`   | CPU time spent running kernel processes              |
| `id`   | CPU idle time                                        |
| `wa`   | CPU waiting for disk I/O                             |
| `st`   | CPU time stolen by the hypervisor (virtual machines) |

### Interpretation

High `id`

```text id="jlwm35"
Good
```

CPU has plenty of idle time.

High `wa`

```text id="’wini36"
Possible storage bottleneck
```

High `st`

```text id="’wini37"
Virtual machine may be waiting for CPU resources.
```

---

# Refresh Every 2 Seconds

```bash id="’wini38"
vmstat 2
```

Updates the statistics every **2 seconds**.

---

# Refresh Five Times

```bash id="’wini39"
vmstat 2 5
```

Meaning:

* Refresh every **2 seconds**
* Stop after **5 updates**

---

# Display Summary Statistics

```bash id="’wini40"
vmstat -s
```

Displays:

* Total memory
* Used memory
* Free memory
* Swap statistics
* CPU statistics

---

# Common vmstat Commands

| Command      | Description                             |
| ------------ | --------------------------------------- |
| `vmstat`     | Display system statistics               |
| `vmstat 2`   | Refresh every 2 seconds                 |
| `vmstat 2 5` | Display 5 updates at 2-second intervals |
| `vmstat -s`  | Display summary statistics              |

---

# Real-World DevOps Use Cases

* Identify servers experiencing memory pressure.
* Detect excessive swap usage.
* Investigate high disk I/O.
* Analyze CPU bottlenecks.
* Troubleshoot performance issues after deployments.
* Monitor EC2 instances and virtual machines.

---

# Best Practices

* Monitor `si` and `so` to identify swap activity.
* Check `wa` to detect disk I/O bottlenecks.
* A consistently high `r` value may indicate CPU contention.
* Use `vmstat` together with `free` and `top` for a complete view of system performance.

---

# Interview Questions

### What does the `vmstat` command display?

It displays information about processes, memory, swap, disk I/O, system activity, and CPU utilization.

---

### What does the `r` column represent?

The number of runnable processes waiting for CPU time.

---

### What do `si` and `so` represent?

* **si** → Swap In (data moved from swap to RAM)
* **so** → Swap Out (data moved from RAM to swap)

---

### Which column indicates CPU idle time?

```text id="’wini41"
id
```

---

### Which column indicates disk I/O wait?

```text id="’wini42"
wa
```

---

### Which command continuously displays system statistics every 2 seconds?

```bash id="’wini43"
vmstat 2
```

---

# Key Takeaways

* `vmstat` provides an overview of CPU, memory, swap, disk I/O, and processes.
* Use `vmstat` to quickly identify system bottlenecks.
* Monitor `si` and `so` for swap activity.
* High `wa` values often indicate storage-related performance issues.
* `vmstat` is one of the most useful commands for Linux performance troubleshooting and DevOps operations.
