# chown Command (Change Owner)

## Overview

The `chown` (change owner) command is used to **change the owner of a file or directory** in Linux.

It can also change the **group ownership** of a file or directory.

The `chown` command is commonly used by system administrators to assign ownership after creating users, deploying applications, or copying files.

---

# Why Do We Use chown?

The `chown` command helps to:

* Assign ownership of files and directories.
* Transfer ownership to another user.
* Change the owner and group simultaneously.
* Manage access in multi-user environments.
* Ensure applications have the correct file ownership.

---

# View Current Ownership

Use the following command to display the current owner and group.

```bash
ls -l
```

Example Output

```text
-rw-r--r-- 1 john developers 2048 Jul 2 report.txt
```

Explanation

| Field | Value        |
| ----- | ------------ |
| Owner | `john`       |
| Group | `developers` |

---

# Syntax

```bash
chown [options] owner file
```

Change both owner and group:

```bash
chown owner:group file
```

---

# Change File Owner

Change the owner of a file.

```bash
sudo chown deepthi report.txt
```

Verify:

```bash
ls -l report.txt
```

---

# Change Directory Owner

```bash
sudo chown deepthi project
```

---

# Change Owner and Group

```bash
sudo chown deepthi:developers report.txt
```

This changes:

* Owner → `deepthi`
* Group → `developers`

---

# Change Only the Group

You can also change only the group using `chown`.

```bash
sudo chown :developers report.txt
```

> **Note:** Although this works, using the `chgrp` command is generally clearer when only the group needs to be changed.

---

# Change Ownership Recursively

Use the `-R` option to change ownership for a directory and all of its files and subdirectories.

```bash
sudo chown -R deepthi:developers project/
```

---

# Common Options

| Option | Description                                 |
| ------ | ------------------------------------------- |
| `-R`   | Change ownership recursively.               |
| `-v`   | Display every ownership change.             |
| `-c`   | Display only files whose ownership changed. |

---

# Examples

### Change file owner

```bash
sudo chown john report.txt
```

---

### Change owner and group

```bash
sudo chown john:developers report.txt
```

---

### Change ownership recursively

```bash
sudo chown -R john:developers project/
```

---

### Display ownership before and after

Before

```bash
ls -l report.txt
```

Output

```text
-rw-r--r-- 1 root root 1024 report.txt
```

Change ownership

```bash
sudo chown john:developers report.txt
```

After

```bash
ls -l report.txt
```

Output

```text
-rw-r--r-- 1 john developers 1024 report.txt
```

---

# Real-World DevOps Use Cases

* Assign ownership of application files after deployment.
* Change ownership of web application directories.
* Set ownership for log directories.
* Assign uploaded files to the correct application user.
* Configure ownership for Docker volumes and mounted directories.

---

# Best Practices

* Verify ownership using `ls -l` before making changes.
* Use `sudo` when changing ownership of system files.
* Use the `-R` option carefully, as it changes ownership for all files and subdirectories.
* Avoid changing ownership of critical system files unless necessary.

---

# Interview Questions

### What does the `chown` command do?

It changes the owner of a file or directory.

---

### Which command changes both the owner and group?

```bash
sudo chown john:developers file.txt
```

---

### Which option changes ownership recursively?

```bash
-R
```

---

### How do you verify file ownership?

```bash
ls -l
```

---

### What is the difference between `chmod` and `chown`?

| Command | Purpose                                                              |
| ------- | -------------------------------------------------------------------- |
| `chmod` | Changes file or directory permissions.                               |
| `chown` | Changes the owner (and optionally the group) of a file or directory. |

---

# Key Takeaways

* `chown` changes the owner of files and directories.
* It can also change the associated group.
* Use `-R` to apply ownership changes recursively.
* Verify ownership changes with `ls -l`.
* Proper ownership management is essential for Linux security and application deployment.
