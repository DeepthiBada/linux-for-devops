# OOM Killer (Out Of Memory Killer)

## Overview

The **Out Of Memory (OOM) Killer** is a feature of the Linux kernel that protects the system when it runs out of available memory.

When both **RAM** and **Swap** are exhausted, the kernel selects one or more processes and terminates them to free memory, helping the system remain operational.

Without the OOM Killer, the system could become completely unresponsive.

---

# Why Do We Need the OOM Killer?

The OOM Killer helps Linux to:

* Prevent the system from freezing.
* Recover memory when RAM is exhausted.
* Keep the operating system responsive.
* Protect critical system processes.
* Automatically recover from severe memory shortages.

---

# When Does the OOM Killer Run?

The OOM Killer is triggered when:

* Physical RAM is nearly exhausted.
* Swap space is fully utilized or unavailable.
* The kernel cannot allocate additional memory.

Example:

```text id="oom01"
RAM = 16 GB

Used RAM = 16 GB

Swap = 2 GB

Used Swap = 2 GB

Application requests more memory
            │
            ▼
Linux Kernel
            │
            ▼
OOM Killer Activated
```

---

# How the OOM Killer Works

```text id="oom02"
Application Requests Memory
           │
           ▼
Linux Kernel
           │
           ▼
Enough Memory Available?
      │             │
     Yes            No
      │             │
      ▼             ▼
Allocate RAM    Trigger OOM Killer
                      │
                      ▼
          Select Process to Terminate
                      │
                      ▼
             Free Memory
```

---

# How Does Linux Choose a Process?

The kernel assigns each process an **OOM Score**, which indicates how suitable it is for termination during an out-of-memory event.

Generally, processes that consume large amounts of memory are more likely to receive a higher score.

The kernel also considers:

* Amount of memory used
* Process priority
* Process importance
* System configuration

> **Note:** The kernel's decision is based on multiple factors. High memory usage is important, but it is **not** the only criterion.

---

# Check OOM Score

Every running process has an OOM score.

Display the score:

```bash id="oom03"
cat /proc/<PID>/oom_score
```

Example

```bash id="oom04"
cat /proc/2458/oom_score
```

Higher values indicate the process is **more likely** to be selected by the OOM Killer.

---

# Adjust OOM Preference

Linux allows you to influence how likely a process is to be selected.

Display the adjustment value:

```bash id="oom05"
cat /proc/<PID>/oom_score_adj
```

Example

```bash id="oom06"
cat /proc/2458/oom_score_adj
```

Typical values range from:

```text id="oom07"
-1000   → Strongly protect the process

0       → Default

1000    → Highest chance of being killed
```

Applications such as databases or critical services may be configured with lower values to reduce the chance of termination.

---

# Check OOM Events

## Using dmesg

```bash id="oom08"
dmesg | grep -i oom
```

Example Output

```text id="oom09"
Out of memory: Killed process 2458 (java)
```

---

## Using journalctl

```bash id="oom10"
journalctl -k | grep -i oom
```

or

```bash id="oom11"
journalctl | grep -i "Out of memory"
```

These commands help identify when and why the OOM Killer terminated a process.

---

# Monitor Memory Before OOM

Useful commands:

Check memory usage

```bash id="oom12"
free -h
```

Monitor running processes

```bash id="oom13"
top
```

Sort processes by memory usage

```bash id="oom14"
ps aux --sort=-%mem
```

---

# Example Scenario

A Java application gradually consumes more memory due to a memory leak.

```text id="oom15"
Java Application
        │
        ▼
RAM Usage Increases
        │
        ▼
Swap Starts Being Used
        │
        ▼
RAM + Swap Become Full
        │
        ▼
OOM Killer Terminates Java Process
```

Result:

```text id="oom16"
Killed
```

The application stops unexpectedly, but the operating system continues running.

---

# How to Prevent OOM Events

* Add more physical RAM.
* Investigate and fix memory leaks.
* Increase swap space if appropriate.
* Optimize application memory usage.
* Monitor memory usage continuously.
* Configure application memory limits (for example, JVM heap size or container memory limits).

---

# Common Commands

| Command                         | Description                          |
| ------------------------------- | ------------------------------------ |
| `free -h`                       | Display RAM and swap usage           |
| `top`                           | Monitor running processes            |
| `ps aux --sort=-%mem`           | Show processes using the most memory |
| `cat /proc/<PID>/oom_score`     | Display a process's OOM score        |
| `cat /proc/<PID>/oom_score_adj` | Display OOM adjustment value         |
| `dmesg \| grep -i oom`          | Display recent OOM events            |
| `journalctl -k \| grep -i oom`  | Search kernel logs for OOM events    |

---

# Real-World DevOps Use Cases

* Investigate why a Java application suddenly exited.
* Troubleshoot Kubernetes Pods terminated due to memory limits.
* Diagnose Docker containers that stop because of memory exhaustion.
* Analyze EC2 instances experiencing high memory pressure.
* Review OOM events after production incidents.

---

# Best Practices

* Monitor memory usage proactively.
* Investigate recurring OOM events rather than simply restarting applications.
* Tune application memory settings based on workload.
* Configure appropriate memory limits for containers.
* Ensure critical services have adequate resources.

---

# Interview Questions

### What is the OOM Killer?

The OOM (Out Of Memory) Killer is a Linux kernel mechanism that terminates one or more processes when the system runs out of available memory.

---

### When does the OOM Killer run?

It runs when the kernel cannot allocate more memory because available RAM and swap are exhausted.

---

### Does the OOM Killer always terminate the process using the most memory?

Not necessarily. The kernel considers several factors, including the process's OOM score, memory usage, priority, and system configuration.

---

### How do you check whether the OOM Killer terminated a process?

```bash id="oom17"
dmesg | grep -i oom
```

or

```bash id="oom18"
journalctl -k | grep -i oom
```

---

### How do you display a process's OOM score?

```bash id="oom19"
cat /proc/<PID>/oom_score
```

---

### How can you reduce the chance of OOM events?

* Increase available memory.
* Fix memory leaks.
* Optimize application memory usage.
* Monitor memory consumption.
* Configure appropriate swap and application memory limits.

---

# Key Takeaways

* The OOM Killer protects Linux systems when memory is exhausted.
* It is triggered when the kernel cannot allocate additional memory.
* The kernel uses an OOM score and other factors to decide which process to terminate.
* Use `dmesg` and `journalctl` to investigate OOM events.
* Prevent recurring OOM issues by monitoring memory, tuning applications, and providing adequate system resources.
