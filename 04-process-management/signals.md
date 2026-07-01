# Linux Signals

## Overview

A **signal** is a software interrupt sent to a process to notify it that an event has occurred or to request it to perform a specific action.

Signals are used to control the behavior of running processes, such as stopping, terminating, pausing, or resuming them.

Linux uses signals for communication between the **kernel**, **users**, and **processes**.

---

# Why Do We Need Signals?

Signals help Linux manage running processes efficiently.

They are commonly used to:

* Stop a running process.
* Pause a process.
* Resume a paused process.
* Gracefully terminate applications.
* Forcefully kill unresponsive processes.
* Notify a process that an event has occurred.

---

# How Signals Work

```text id="7j9qxt"
User / Kernel / Process
          │
          ▼
      Sends Signal
          │
          ▼
     Running Process
          │
          ▼
 Process Responds to Signal
```

Example:

* You press **Ctrl + C**
* Linux sends **SIGINT** to the running process.
* The process receives the signal and terminates.

---

# Common Linux Signals

| Signal    | Number | Purpose                                                                |
| --------- | -----: | ---------------------------------------------------------------------- |
| `SIGHUP`  |      1 | Reload configuration or notify a process that the terminal has closed. |
| `SIGINT`  |      2 | Interrupt a running process (Ctrl + C).                                |
| `SIGKILL` |      9 | Forcefully terminate a process.                                        |
| `SIGTERM` |     15 | Gracefully terminate a process.                                        |
| `SIGSTOP` |     19 | Pause (stop) a process.                                                |
| `SIGCONT` |     18 | Resume a stopped process.                                              |

---

# 1. SIGTERM (15)

## Description

`SIGTERM` requests a process to terminate **gracefully**.

The process has an opportunity to:

* Save data
* Close files
* Release resources
* Shut down cleanly

### Example

```bash id="lgn9cs"
kill 2458
```

or

```bash id="uxhq9m"
kill -15 2458
```

> `kill` sends `SIGTERM` by default.

---

# 2. SIGKILL (9)

## Description

`SIGKILL` immediately terminates a process.

The process cannot ignore or handle this signal.

Use it only when a process does not respond to `SIGTERM`.

### Example

```bash id="a0zhzu"
kill -9 2458
```

> ⚠️ Since the process is terminated immediately, it cannot perform cleanup tasks or save its state.

---

# 3. SIGINT (2)

## Description

`SIGINT` interrupts a running foreground process.

It is commonly generated when the user presses:

```text id="v0iwxm"
Ctrl + C
```

Example:

```bash id="09r46n"
ping google.com
```

Press:

```text id="scc5yk"
Ctrl + C
```

The process stops gracefully.

---

# 4. SIGHUP (1)

## Description

Originally, `SIGHUP` indicated that a terminal session had ended.

Today, many applications interpret it as a signal to **reload their configuration** without stopping the process.

### Example

Reload an application after updating its configuration.

---

# 5. SIGSTOP (19)

## Description

`SIGSTOP` pauses a running process.

Unlike `SIGTERM`, the process is **not terminated**. It remains in memory until resumed.

### Example

```bash id="e21rrd"
kill -19 2458
```

or

```text id="6r87vf"
Ctrl + Z
```

The process enters the **Stopped (T)** state.

---

# 6. SIGCONT (18)

## Description

`SIGCONT` resumes a stopped process.

### Example

```bash id="m5rws5"
kill -18 2458
```

or

```bash id="k0slmn"
fg
```

or

```bash id="67gcmr"
bg
```

---

# View Available Signals

Display all supported signals:

```bash id="jlwm41"
kill -l
```

Example Output

```text id="jlwm42"
1) SIGHUP
2) SIGINT
9) SIGKILL
15) SIGTERM
18) SIGCONT
19) SIGSTOP
```

---

# Signal Comparison

| Signal    | Number | Can Process Handle It? | Common Use           |
| --------- | -----: | ---------------------- | -------------------- |
| `SIGHUP`  |      1 | Yes                    | Reload configuration |
| `SIGINT`  |      2 | Yes                    | Interrupt process    |
| `SIGKILL` |      9 | No                     | Forcefully terminate |
| `SIGTERM` |     15 | Yes                    | Graceful shutdown    |
| `SIGCONT` |     18 | Yes                    | Resume process       |
| `SIGSTOP` |     19 | No                     | Pause process        |

---

# Real-World DevOps Use Cases

* Stop an unresponsive application using `SIGKILL`.
* Gracefully restart services using `SIGTERM`.
* Reload Nginx or Apache configuration using `SIGHUP`.
* Pause a long-running job during troubleshooting.
* Resume a paused process after maintenance.

---

# Best Practices

* Always try `SIGTERM` before using `SIGKILL`.
* Use `SIGKILL` only when a process cannot be stopped gracefully.
* Use `SIGHUP` to reload configurations when supported by the application.
* Verify the PID before sending any signal.

---

# Interview Questions

### What is a Linux signal?

A signal is a software interrupt used to communicate with and control running processes.

---

### What is the difference between `SIGTERM` and `SIGKILL`?

* `SIGTERM` allows a process to shut down gracefully.
* `SIGKILL` immediately terminates a process without allowing cleanup.

---

### Which signal is sent when you press **Ctrl + C**?

```text id="jlwm43"
SIGINT (2)
```

---

### Which signal pauses a process?

```text id="’wini44"
SIGSTOP (19)
```

---

### Which signal resumes a stopped process?

```text id="jlwm45"
SIGCONT (18)
```

---

### Which command displays all available signals?

```bash id="jlwm46"
kill -l
```

---

# Key Takeaways

* Signals are software interrupts used to control running processes.
* `SIGTERM` gracefully terminates a process.
* `SIGKILL` forcefully terminates a process.
* `SIGINT` is generated by pressing **Ctrl + C**.
* `SIGSTOP` pauses a process, while `SIGCONT` resumes it.
* Understanding signals is essential for Linux administration, troubleshooting, and DevOps operations.
