# Absolute vs Relative Paths

## Overview

A **path** specifies the location of a file or directory in the Linux file system.

Linux supports two types of paths:

* **Absolute Path**
* **Relative Path**

Understanding the difference between them is essential for navigating the file system and writing shell scripts.

---

# Absolute Path

## Definition

An **absolute path** is the complete path to a file or directory starting from the **root directory (`/`)**.

It always begins with a forward slash (`/`) and points to the same location regardless of your current working directory.

### Syntax

```text
/path/to/file
```

### Example

```text
/home/deepthi/Documents/report.txt
```

```bash
cat /home/deepthi/Documents/report.txt
```

### Characteristics

* Starts with `/`
* Independent of the current directory
* Always points to the same location
* Preferred in scripts for consistency

---

# Relative Path

## Definition

A **relative path** specifies the location of a file or directory relative to your **current working directory**.

It does **not** start with `/`.

### Example

Current directory:

```text
/home/deepthi
```

Access a file in the Documents folder:

```bash
cat Documents/report.txt
```

Here, `Documents/report.txt` is a relative path because it depends on the current directory.

---

# Special Path Symbols

| Symbol | Description                        |
| ------ | ---------------------------------- |
| `.`    | Current directory                  |
| `..`   | Parent directory                   |
| `~`    | Home directory of the current user |
| `/`    | Root directory                     |

### Examples

Go to the current directory:

```bash
cd .
```

Move to the parent directory:

```bash
cd ..
```

Go to the home directory:

```bash
cd ~
```

Go to the root directory:

```bash
cd /
```

---

# Absolute vs Relative Path

| Absolute Path                                    | Relative Path                            |
| ------------------------------------------------ | ---------------------------------------- |
| Starts with `/`                                  | Does not start with `/`                  |
| Begins from the root directory                   | Begins from the current directory        |
| Always points to the same location               | Depends on the current working directory |
| Commonly used in scripts and configuration files | Convenient for daily navigation          |

---

# Example Scenario

Suppose the following directory structure exists:

```text
/home/deepthi/
├── Documents/
│   └── report.txt
└── Downloads/
```

Current directory:

```text
/home/deepthi
```

Using an absolute path:

```bash
cat /home/deepthi/Documents/report.txt
```

Using a relative path:

```bash
cat Documents/report.txt
```

Both commands access the same file.

---

# Real-World DevOps Use Cases

* Use **absolute paths** in shell scripts, cron jobs, and automation to ensure files are always found correctly.
* Use **relative paths** while working within project directories to simplify commands.
* Deployment scripts often use absolute paths for configuration files and log locations.

---

# Interview Questions

### What is an absolute path?

An absolute path is the complete path to a file or directory starting from the root directory (`/`).

---

### What is a relative path?

A relative path is the path to a file or directory based on the current working directory.

---

### Which path is preferred in shell scripts?

Absolute paths are generally preferred because they work regardless of the current directory.

---

### What do the following symbols represent?

| Symbol | Meaning           |
| ------ | ----------------- |
| `.`    | Current directory |
| `..`   | Parent directory  |
| `~`    | Home directory    |
| `/`    | Root directory    |

---

# Key Takeaways

* A path identifies the location of a file or directory.
* Absolute paths always start with `/` and are independent of the current location.
* Relative paths depend on the current working directory.
* `.` represents the current directory, `..` the parent directory, `~` the home directory, and `/` the root directory.
* Understanding paths is essential for Linux administration, shell scripting, and DevOps automation.
