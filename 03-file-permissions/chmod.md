# chmod Command

## Overview

The `chmod` (change mode) command is used to **modify the permissions of files and directories** in Linux.

It allows administrators and users to control who can **read**, **write**, or **execute** a file or directory.

---

# Why Do We Use chmod?

The `chmod` command helps to:

* Secure sensitive files.
* Allow or restrict access to files and directories.
* Make scripts executable.
* Prevent unauthorized modifications.
* Manage file permissions efficiently.

---

# Syntax

```bash id="rw2gmp"
chmod [options] <permissions> <file_or_directory>
```

Example

```bash id="4zh7if"
chmod 755 script.sh
```

---

# Permission Symbols

| Symbol | Permission |
| ------ | ---------- |
| `r`    | Read       |
| `w`    | Write      |
| `x`    | Execute    |

---

# User Categories

| Symbol | Meaning                     |
| ------ | --------------------------- |
| `u`    | User (Owner)                |
| `g`    | Group                       |
| `o`    | Others                      |
| `a`    | All (User + Group + Others) |

---

# Symbolic Mode

In symbolic mode, permissions are added (`+`), removed (`-`), or assigned (`=`).

## Syntax

```bash id="ukl39h"
chmod [ugoa][+-=][rwx] file
```

### Examples

Add execute permission to the owner:

```bash id="yx73p1"
chmod u+x script.sh
```

Remove write permission from the group:

```bash id="8f6c5q"
chmod g-w report.txt
```

Give read permission to others:

```bash id="c9zt2b"
chmod o+r notes.txt
```

Give execute permission to everyone:

```bash id="0bpnt8"
chmod a+x script.sh
```

Assign read and write permissions to the owner only:

```bash id="63r3c9"
chmod u=rw file.txt
```

---

# Numeric (Octal) Mode

Each permission has a numeric value.

| Permission    | Value |
| ------------- | ----: |
| Read (`r`)    |     4 |
| Write (`w`)   |     2 |
| Execute (`x`) |     1 |

Permissions are added together.

| Permission | Value |
| ---------- | ----: |
| `rwx`      |     7 |
| `rw-`      |     6 |
| `r-x`      |     5 |
| `r--`      |     4 |
| `---`      |     0 |

### Examples

```bash id="jlwm01"
chmod 755 script.sh
```

```bash id="jlwm02"
chmod 644 file.txt
```

```bash id="jlwm03"
chmod 700 private.sh
```

> Numeric permissions are covered in detail in **numeric-permissions.md**.

---

# Common chmod Examples

Make a script executable:

```bash id="jlwm04"
chmod +x deploy.sh
```

Remove execute permission:

```bash id="jlwm05"
chmod -x deploy.sh
```

Give full permissions to the owner only:

```bash id="jlwm06"
chmod 700 secrets.txt
```

Give read permission to everyone:

```bash id="jlwm07"
chmod a+r file.txt
```

Change permissions recursively:

```bash id="jlwm08"
chmod -R 755 project/
```

---

# Common Options

| Option | Description                                                        |
| ------ | ------------------------------------------------------------------ |
| `-R`   | Change permissions recursively for directories and their contents. |
| `-v`   | Display every permission change.                                   |
| `-c`   | Display only files whose permissions were changed.                 |

---

# Verify Permissions

Before changing permissions:

```bash id="jlwm09"
ls -l file.txt
```

After changing permissions:

```bash id="jlwm10"
chmod 755 file.txt
ls -l file.txt
```

Example Output

```text id="jlwm11"
-rwxr-xr-x
```

---

# Real-World DevOps Use Cases

* Make deployment scripts executable.
* Secure SSH private keys.
* Restrict access to configuration files.
* Set permissions for application directories.
* Apply permissions recursively during deployments.

---

# Best Practices

* Grant only the permissions that are required.
* Avoid using `777` unless absolutely necessary.
* Verify permissions using `ls -l` before and after changes.
* Use recursive permission changes (`-R`) with caution.

---

# Interview Questions

### What does the `chmod` command do?

It changes the permissions of files and directories.

---

### What is the difference between symbolic and numeric mode?

* **Symbolic mode** uses letters (`u`, `g`, `o`, `a`, `r`, `w`, `x`) to add, remove, or assign permissions.
* **Numeric mode** uses numbers (such as `755` or `644`) to set permissions.

---

### What does the following command do?

```bash id="jlwm12"
chmod u+x script.sh
```

Adds execute permission for the file owner.

---

### Which command makes a shell script executable?

```bash id="jlwm13"
chmod +x script.sh
```

---

### Which command changes permissions recursively?

```bash id="jlwm14"
chmod -R 755 project/
```

---

# Key Takeaways

* `chmod` changes file and directory permissions.
* Permissions can be modified using symbolic or numeric mode.
* Always verify permission changes using `ls -l`.
* Follow the principle of least privilege by granting only the permissions required.
* Proper use of `chmod` is essential for Linux security and DevOps administration.
