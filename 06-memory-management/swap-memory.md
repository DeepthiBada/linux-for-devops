# Swap Memory

## Overview

**Swap Memory** is a reserved area on a disk (SSD or HDD) that Linux uses as an extension of **physical RAM** when available memory becomes low.

Swap helps prevent applications from crashing when RAM is exhausted, but because it resides on disk, it is **much slower than RAM**.

The Linux kernel automatically decides when to use swap based on system memory usage and configuration.

---

# Why Do We Need Swap?

Swap provides several benefits:

* Prevents applications from crashing when RAM is full.
* Supports systems running many applications simultaneously.
* Allows inactive memory pages to be moved out of RAM.
* Provides additional memory during temporary spikes in usage.
* Can support features such as **hibernation** (on systems configured for it).

---

# How Swap Works

```text id="jlwm44"
Application
      │
      ▼
Physical RAM
      │
      │ (RAM becomes full)
      ▼
Linux Kernel
      │
      ▼
Move Less-Used Memory Pages
      │
      ▼
Swap Space (Disk)
```

The kernel moves **less frequently used memory pages** from RAM to swap, freeing RAM for active applications.

---

# RAM vs Swap

| RAM                | Swap                  |
| ------------------ | --------------------- |
| Physical memory    | Disk space            |
| Very fast          | Much slower than RAM  |
| Used first         | Used only when needed |
| Volatile           | Stored on disk        |
| Better performance | Lower performance     |

---

# Types of Swap

Linux supports two types of swap.

## 1. Swap Partition

A dedicated disk partition reserved for swap.

Example:

```text id="jlwm45"
/dev/sda2
```

### Advantages

* Slightly better performance
* Common on traditional Linux installations

---

## 2. Swap File

A regular file on the filesystem that is used as swap.

Example:

```text id="jlwm46"
/swapfile
```

### Advantages

* Easy to create
* Easy to resize
* Common on cloud servers and virtual machines

---

# Check Swap Usage

## Display Memory and Swap

```bash id="’wini47"
free -h
```

Example Output

```text id="’wini48"
               total   used   free
Mem:            8.0G   2.5G   1.8G
Swap:           2.0G   256M   1.8G
```

---

## Display Active Swap Areas

```bash id="’wini49"
swapon --show
```

Example Output

```text id="’wini50"
NAME       TYPE  SIZE  USED PRIO
/swapfile  file   2G   256M   -2
```

---

## Display Swap Information

```bash id="’wini51"
cat /proc/swaps
```

---

# Enable Swap

Enable an existing swap area.

```bash id="’wini52"
sudo swapon /swapfile
```

Enable all swap devices listed in `/etc/fstab`.

```bash id="’wini53"
sudo swapon -a
```

---

# Disable Swap

Disable a specific swap area.

```bash id="’wini54"
sudo swapoff /swapfile
```

Disable all swap.

```bash id="’wini55"
sudo swapoff -a
```

---

# Swappiness

Linux uses the **swappiness** value to determine how aggressively it should move memory pages from RAM to swap.

Display the current value:

```bash id="’wini56"
cat /proc/sys/vm/swappiness
```

Example Output

```text id="’wini57"
60
```

Typical values:

| Value | Behavior                               |
| ----: | -------------------------------------- |
|   `0` | Avoid swap unless absolutely necessary |
|  `10` | Prefer RAM, use swap only when needed  |
|  `60` | Common Linux default                   |
| `100` | Use swap more aggressively             |

Temporarily change the value:

```bash id="’wini58"
sudo sysctl vm.swappiness=10
```

> **Note:** This change is temporary and lasts until the next reboot unless configured persistently.

---

# When is High Swap Usage a Problem?

High swap usage may indicate:

* Insufficient physical RAM
* Memory-intensive applications
* Memory leaks
* Poor application tuning
* Excessive multitasking

Heavy swap activity can make the system slow because reading from and writing to disk is much slower than accessing RAM.

---

# Common Swap Commands

| Command                       | Description                |
| ----------------------------- | -------------------------- |
| `free -h`                     | Display RAM and swap usage |
| `swapon --show`               | Display active swap areas  |
| `cat /proc/swaps`             | Show configured swap       |
| `swapon -a`                   | Enable all swap devices    |
| `swapoff -a`                  | Disable all swap devices   |
| `cat /proc/sys/vm/swappiness` | Display swappiness value   |

---

# Real-World DevOps Use Cases

* Monitor swap usage on production servers.
* Troubleshoot application slowdowns caused by memory pressure.
* Configure swap on cloud virtual machines.
* Analyze memory utilization during deployments.
* Investigate Out Of Memory (OOM) events.

---

# Best Practices

* Use swap as a safety mechanism, not as a replacement for RAM.
* Monitor swap usage regularly.
* Investigate continuously high swap usage.
* Increase physical RAM if swap usage remains consistently high.
* Tune the **swappiness** value based on workload requirements.

---

# Interview Questions

### What is swap memory?

Swap is disk space that Linux uses as an extension of physical RAM when available memory becomes low.

---

### Is swap faster than RAM?

No. Swap is much slower because it is stored on a disk rather than in physical memory.

---

### What is the difference between a swap partition and a swap file?

* **Swap Partition:** A dedicated disk partition reserved for swap.
* **Swap File:** A regular file on the filesystem that is used as swap.

---

### Which command displays current swap usage?

```bash id="’wini59"
free -h
```

or

```bash id="’wini60"
swapon --show
```

---

### What is swappiness?

Swappiness is a Linux kernel parameter that controls how aggressively the kernel moves memory pages from RAM to swap.

---

### Should a server continuously use swap?

Not usually. Occasional swap usage is normal, but sustained heavy swap usage often indicates memory pressure or insufficient RAM and should be investigated.

---

# Key Takeaways

* Swap is disk space used as an extension of RAM.
* Linux uses swap only when additional memory is needed.
* Swap is much slower than physical RAM.
* Linux supports both swap partitions and swap files.
* Monitor swap usage with `free -h` and `swapon --show`.
* High swap usage may indicate memory shortages or application issues.
