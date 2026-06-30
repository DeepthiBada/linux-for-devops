# Linux File Permissions

## Overview

Linux is a multi-user operating system where multiple users can access the same system. To protect files and directories from unauthorized access, Linux uses a **permission model**.

Permissions determine **who can read, modify, or execute a file or directory**.

Proper permission management is essential for system security and is a fundamental concept in Linux administration and DevOps.

---

# Why Do We Need File Permissions?

File permissions help:

* Protect sensitive data.
* Prevent unauthorized access.
* Control who can modify files.
* Improve system security.
* Allow secure collaboration between users and groups.

---

# Permission Types

Linux has three basic permissions.

| Permission | Symbol | Description                                              |
| ---------- | ------ | -------------------------------------------------------- |
| Read       | `r`    | View the contents of a file or list a directory.         |
| Write      | `w`    | Modify a file or create/delete files inside a directory. |
| Execute    | `x`    | Run a file as a program or access a directory.           |

---

# Permission Categories

Permissions are assigned to three categories.

| Category     | Description                          |
| ------------ | ------------------------------------ |
| Owner (User) | The user who owns the file.          |
| Group        | Users belonging to the file's group. |
| Others       | All other users on the system.       |

---

# Viewing File Permissions

Use the following command:

```bash
ls -l
```

Example Output

```text
-rwxr-xr--
```

Let's break it down.

```text
-rwxr-xr--

│
├── -
├── rwx
├── r-x
└── r--
```

| Section | Meaning            |
| ------- | ------------------ |
| `-`     | File type          |
| `rwx`   | Owner permissions  |
| `r-x`   | Group permissions  |
| `r--`   | Others permissions |

---

# Understanding the First Character

The first character represents the file type.

| Symbol | Meaning          |
| ------ | ---------------- |
| `-`    | Regular file     |
| `d`    | Directory        |
| `l`    | Symbolic link    |
| `c`    | Character device |
| `b`    | Block device     |

Example:

```text
-rwxr-xr--
```

Regular file

```text
drwxr-xr-x
```

Directory

---

# Understanding Read, Write and Execute

## Read (`r`)

For files:

* View file contents.
* Open and read files.

For directories:

* List the contents of the directory.

---

## Write (`w`)

For files:

* Modify file contents.

For directories:

* Create files.
* Delete files.
* Rename files.

---

## Execute (`x`)

For files:

* Execute the file as a program or script.

For directories:

* Enter the directory using the `cd` command.
* Access files inside the directory.

---

# Permission Example

```text
-rwxr-x---
```

| User Type | Permission           |
| --------- | -------------------- |
| Owner     | Read, Write, Execute |
| Group     | Read, Execute        |
| Others    | No permissions       |

---

# Display Detailed Permissions

```bash
ls -l
```

Example

```text
-rwxr-xr-- 1 deepthi developers 2048 Jul 2 script.sh
```

| Field        | Description          |
| ------------ | -------------------- |
| `-rwxr-xr--` | File permissions     |
| `1`          | Number of hard links |
| `deepthi`    | Owner                |
| `developers` | Group                |
| `2048`       | File size (bytes)    |
| `Jul 2`      | Last modified date   |
| `script.sh`  | File name            |

---

# Real-World DevOps Use Cases

* Restrict access to configuration files.
* Allow only application owners to modify deployment scripts.
* Grant execute permission to shell scripts.
* Secure SSH keys by limiting file permissions.
* Control access to shared project directories.

---

# Interview Questions

### What are the three basic Linux permissions?

* Read (`r`)
* Write (`w`)
* Execute (`x`)

---

### What are the three permission categories?

* Owner
* Group
* Others

---

### Which command displays file permissions?

```bash
ls -l
```

---

### What does the first character in `ls -l` output represent?

It indicates the file type (regular file, directory, symbolic link, etc.).

---

### What is the difference between write permission on a file and a directory?

* On a **file**, write permission allows modification of its contents.
* On a **directory**, write permission allows creating, deleting, or renaming files within that directory.

---

# Key Takeaways

* Linux uses file permissions to control access to files and directories.
* Permissions are assigned to the Owner, Group, and Others.
* The three permission types are Read (`r`), Write (`w`), and Execute (`x`).
* Use `ls -l` to view file permissions.
* Proper permission management is essential for Linux security and DevOps administration.
