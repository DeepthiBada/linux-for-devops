# Process Management Commands

## Overview

Linux provides several commands to monitor, search, manage, and terminate running processes.

These commands are essential for Linux administrators and DevOps engineers when troubleshooting applications, monitoring server performance, and managing system resources.

---

# Process Management Commands

| Command   | Description                                       |
| --------- | ------------------------------------------------- |
| `ps`      | Display running processes.                        |
| `top`     | Display real-time system and process information. |
| `htop`    | Interactive process viewer (if installed).        |
| `pstree`  | Display processes in a tree structure.            |
| `pgrep`   | Find processes by name.                           |
| `pidof`   | Display the Process ID (PID) of a program.        |
| `kill`    | Terminate a process using its PID.                |
| `killall` | Terminate all processes with the same name.       |
| `pkill`   | Terminate processes by name or pattern.           |
| `nice`    | Start a process with a specified priority.        |
| `renice`  | Change the priority of a running process.         |

---

# Viewing Processes

## ps

Displays information about running processes.

### Syntax

```bash
ps
```

Useful Examples

Display all running processes

```bash
ps -ef
```

Display processes for the current user

```bash
ps -u $USER
```

Display custom output

```bash
ps -eo pid,ppid,user,%cpu,%mem,cmd
```

---

## top

Displays real-time information about:

* CPU usage
* Memory usage
* Running processes
* Process IDs
* Load average

### Syntax

```bash
top
```

Useful Keys

| Key | Action               |
| --- | -------------------- |
| `P` | Sort by CPU usage    |
| `M` | Sort by Memory usage |
| `k` | Kill a process       |
| `q` | Quit                 |

---

## htop

An interactive version of `top`.

### Syntax

```bash
htop
```

Features

* User-friendly interface
* Mouse support
* Easy process search
* Color-coded resource usage

> Note: `htop` may need to be installed separately.

---

## pstree

Displays processes in a parent-child tree structure.

### Syntax

```bash
pstree
```

Example

```bash
pstree -p
```

Shows process names along with their PIDs.

---

# Finding Processes

## pgrep

Finds processes based on their name.

### Syntax

```bash
pgrep <process_name>
```

Example

```bash
pgrep nginx
```

---

## pidof

Displays the Process ID of a running program.

### Syntax

```bash
pidof <process_name>
```

Example

```bash
pidof sshd
```

---

# Managing Processes

## kill

Terminates a process using its Process ID (PID).

### Syntax

```bash
kill <PID>
```

Example

```bash
kill 2458
```

Force kill

```bash
kill -9 2458
```

> Use `kill -9` only when a process does not terminate gracefully.

---

## killall

Terminates all processes with the specified name.

### Syntax

```bash
killall <process_name>
```

Example

```bash
killall firefox
```

---

## pkill

Terminates processes by name or pattern.

### Syntax

```bash
pkill <process_name>
```

Example

```bash
pkill java
```

Unlike `kill`, you do not need to specify the PID.

---

# Process Priority

## nice

Starts a process with a specified priority.

### Syntax

```bash
nice -n <priority> <command>
```

Example

```bash
nice -n 10 python app.py
```

The **nice value** ranges from:

```text
-20  (Highest Priority)

  0  (Default)

 19  (Lowest Priority)
```

---

## renice

Changes the priority of an already running process.

### Syntax

```bash
renice <priority> -p <PID>
```

Example

```bash
sudo renice 5 -p 2458
```

---

# Verify Running Processes

List all Java processes

```bash
ps -ef | grep java
```

Find the PID of nginx

```bash
pidof nginx
```

Display the process tree

```bash
pstree
```

Monitor the server

```bash
top
```

---

# Real-World DevOps Use Cases

* Check whether an application is running.
* Find the PID of a Java or Nginx process.
* Monitor CPU and memory usage during deployments.
* Stop unresponsive applications.
* Adjust process priority for background jobs.
* Troubleshoot high CPU utilization on production servers.

---

# Best Practices

* Use `ps` to inspect processes.
* Use `top` or `htop` for real-time monitoring.
* Prefer `kill` before using `kill -9`.
* Verify the correct PID before terminating a process.
* Avoid killing critical system processes.

---

# Interview Questions

### Which command displays all running processes?

```bash
ps -ef
```

---

### What is the difference between `ps` and `top`?

* `ps` displays a snapshot of running processes.
* `top` displays real-time process information.

---

### What is the difference between `kill`, `killall`, and `pkill`?

| Command   | Description                                       |
| --------- | ------------------------------------------------- |
| `kill`    | Terminates a process using its PID.               |
| `killall` | Terminates all processes with the specified name. |
| `pkill`   | Terminates processes by name or pattern.          |

---

### Which command displays the process hierarchy?

```bash
pstree
```

---

### Which command finds the PID of a process?

```bash
pgrep <process_name>
```

or

```bash
pidof <process_name>
```

---

### Which command changes the priority of a running process?

```bash
renice
```

### Difference between 'ps -ef' and 'ps aux'?

ps -ef : shows current processes running

ps aux : shows current processes running along with mem and cpu utilization

---

# Key Takeaways

* `ps` displays process information.
* `top` and `htop` provide real-time system monitoring.
* `pgrep` and `pidof` help locate running processes.
* `kill`, `killall`, and `pkill` terminate processes.
* `nice` and `renice` manage process priorities.
* Process management is a fundamental Linux skill for system administrators and DevOps engineers.
