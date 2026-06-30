# Linux Processes

## Overview

A **process** is an instance of a program that is currently being executed by the operating system.

When you run a command or start an application, Linux creates a process to execute it.

For example:

* Running the `ls` command creates a process.
* Opening Google Chrome creates one or more processes.
* Starting an application server creates a process.

Every running program in Linux is a process.

---

# Program vs Process

A **program** is a set of instructions stored on the disk.

A **process** is a program that is currently running in memory.

### Example

```text
Program (Stored on Disk)
        │
        ▼
Execute Program
        │
        ▼
Process (Running in Memory)
```

Example:

* `/usr/bin/python` → Program
* Running `python app.py` → Process

---

# Process Lifecycle

A process goes through different stages during its execution.

```text
New
 │
 ▼
Ready
 │
 ▼
Running
 │
 ├───────────────┐
 ▼               │
Waiting          │
 │               │
 └──────► Ready ◄┘
 │
 ▼
Terminated
```

### Process States

| State              | Description                                                     |
| ------------------ | --------------------------------------------------------------- |
| New                | Process is being created.                                       |
| Ready              | Process is waiting for CPU time.                                |
| Running            | Process is currently executing.                                 |
| Waiting (Sleeping) | Process is waiting for an event such as user input or disk I/O. |
| Terminated         | Process has finished execution.                                 |

---

# Process ID (PID)

Every process in Linux has a unique **Process ID (PID)** assigned by the operating system.

The PID is used to:

* Identify a process
* Monitor a process
* Stop a process
* Manage a process

Example:

```text
PID 1256 → nginx
PID 2148 → java
PID 3502 → ssh
```

---

# Parent Process ID (PPID)

Every process (except the first system process) is started by another process called its **parent process**.

The parent process is identified using the **Parent Process ID (PPID)**.

Example:

```text
systemd (PID 1)
        │
        ├── sshd
        │      └── bash
        │             └── python
        │
        └── nginx
```

---

# What is PID 1?

The first process started by the Linux kernel is called **init** or **systemd** (on most modern Linux distributions).

It has:

```text
PID = 1
```

Responsibilities include:

* Starting system services
* Managing system startup
* Acting as the parent of orphaned processes

---

# Daemon Processes

A **daemon** is a background process that runs continuously without direct user interaction.

Daemon processes usually provide system or application services.

Examples:

* `sshd` – SSH server
* `cron` – Task scheduler
* `systemd` – System manager
* `nginx` – Web server
* `mysqld` – Database server

---

# Foreground and Background Processes

## Foreground Process

A foreground process runs in the terminal and occupies it until the process finishes.

Example:

```bash
ping google.com
```

You cannot use the same terminal for another command until the process stops or is interrupted.

---

## Background Process

A background process runs independently, allowing you to continue using the terminal.

Example:

```bash
ping google.com &
```

The `&` symbol starts the process in the background.

---

# Process Hierarchy

Linux organizes processes in a tree structure.

```text
systemd (PID 1)
│
├── sshd
│     └── bash
│            └── python
│
├── cron
│
├── nginx
│
└── docker
      └── container process
```

Each child process is created by a parent process.

---

# Why Process Management is Important

Process management helps administrators:

* Monitor running applications
* Identify high CPU or memory usage
* Stop unresponsive applications
* Troubleshoot system performance
* Manage background services

---

# Real-World DevOps Use Cases

* Check whether an application is running.
* Monitor Java application processes.
* Restart unresponsive services.
* Investigate high CPU or memory usage.
* Identify processes consuming excessive resources.

---

# Interview Questions

### What is a process?

A process is an instance of a program that is currently executing.

---

### What is the difference between a program and a process?

* A **program** is stored on disk.
* A **process** is a running instance of a program in memory.

---

### What is a PID?

A **Process ID (PID)** is a unique number assigned to every running process.

---

### What is a PPID?

A **Parent Process ID (PPID)** identifies the process that created the current process.

---

### What is a daemon process?

A daemon is a background process that provides system or application services without direct user interaction.

---

### What is PID 1?

PID 1 is the first process started by the Linux kernel (typically `systemd` on modern Linux systems). It manages system startup and other system processes.

---

# Key Takeaways

* A process is a running instance of a program.
* Every process has a unique Process ID (PID).
* Every process (except PID 1) has a Parent Process ID (PPID).
* Linux organizes processes in a hierarchical tree structure.
* Daemon processes run in the background to provide system services.
* Process management is essential for monitoring, troubleshooting, and maintaining Linux systems.
