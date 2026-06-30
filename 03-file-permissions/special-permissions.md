# Special Permissions

## Overview

In addition to the standard **Read (r)**, **Write (w)**, and **Execute (x)** permissions, Linux provides three **special permissions** that offer more advanced access control.

These permissions are:

* **SUID (Set User ID)**
* **SGID (Set Group ID)**
* **Sticky Bit**

They are commonly used to improve security, enable controlled access, and support collaboration in multi-user environments.

---

# Types of Special Permissions

| Permission | Symbol | Numeric Value | Purpose                                                                                  |
| ---------- | ------ | ------------: | ---------------------------------------------------------------------------------------- |
| SUID       | `s`    |             4 | Run a file with the owner's privileges                                                   |
| SGID       | `s`    |             2 | Run a file with the group's privileges or inherit the group for new files in a directory |
| Sticky Bit | `t`    |             1 | Restrict file deletion in shared directories                                             |

---

# 1. SUID (Set User ID)

## What is SUID?

SUID allows a user to execute a file with the **permissions of the file owner**, rather than the permissions of the user running the file.

It is mainly used with executable files.

---

## How to Set SUID

```bash
chmod u+s <file>
```

or

```bash
chmod 4755 <file>
```

---

## View SUID

```bash
ls -l
```

Example

```text
-rwsr-xr-x
```

Notice the **`s`** in the owner's execute position.

---

## Real-World Example

The `passwd` command allows users to change their own passwords.

```bash
passwd
```

Although a regular user cannot modify system files directly, the `passwd` program runs with the **root user's privileges** because it has the SUID bit set.

---

# 2. SGID (Set Group ID)

## What is SGID?

SGID has two common uses:

### On Executable Files

The program runs with the **group permissions** of the file instead of the user's group.

### On Directories

New files and subdirectories inherit the **directory's group ownership**, making collaboration easier.

---

## How to Set SGID

```bash
chmod g+s <directory>
```

or

```bash
chmod 2755 <directory>
```

---

## View SGID

```bash
ls -l
```

Example

```text
drwxr-sr-x
```

Notice the **`s`** in the group's execute position.

---

## Real-World Example

A shared project directory belongs to the **developers** group.

When SGID is set, every new file created inside the directory automatically belongs to the **developers** group, regardless of the creator's primary group.

---

# 3. Sticky Bit

## What is Sticky Bit?

The Sticky Bit prevents users from deleting or renaming files owned by other users in a shared directory.

Only the following users can delete a file:

* File owner
* Directory owner
* Root user

---

## How to Set Sticky Bit

```bash
chmod +t <directory>
```

or

```bash
chmod 1777 <directory>
```

---

## View Sticky Bit

```bash
ls -l
```

Example

```text
drwxrwxrwt
```

Notice the **`t`** in the others' execute position.

---

## Real-World Example

The `/tmp` directory is writable by all users.

Without the Sticky Bit, any user could delete another user's temporary files.

The Sticky Bit ensures users can delete **only their own files**.

---

# Numeric Representation

Special permissions are represented by an additional leading digit.

| Numeric Value | Meaning    |
| ------------: | ---------- |
|             4 | SUID       |
|             2 | SGID       |
|             1 | Sticky Bit |

Examples:

| Permission               | Numeric |
| ------------------------ | ------: |
| SUID                     |  `4755` |
| SGID                     |  `2755` |
| Sticky Bit               |  `1777` |
| SUID + SGID              |  `6755` |
| SUID + SGID + Sticky Bit |  `7755` |

---

# Verify Special Permissions

```bash
ls -l
```

Examples

```text
-rwsr-xr-x
```

SUID

```text
drwxr-sr-x
```

SGID

```text
drwxrwxrwt
```

Sticky Bit

---

# Real-World DevOps Use Cases

* Allow users to change passwords securely using SUID-enabled programs.
* Use SGID on shared project directories so new files inherit the correct group.
* Protect shared directories like `/tmp` with the Sticky Bit.
* Secure collaboration on shared application and deployment directories.

---

# Best Practices

* Use SUID only on trusted executables.
* Avoid setting SUID on custom scripts or unnecessary programs.
* Use SGID for team collaboration directories.
* Always use the Sticky Bit on world-writable shared directories.
* Regularly audit systems for unnecessary special permissions.

---

# Interview Questions

### What are the three special permissions in Linux?

* SUID
* SGID
* Sticky Bit

---

### What is SUID?

SUID allows a program to run with the permissions of the file owner.

---

### What is SGID?

SGID allows a program to run with the permissions of the file's group. On directories, it ensures new files inherit the directory's group ownership.

---

### What is the purpose of the Sticky Bit?

It prevents users from deleting or renaming files they do not own in a shared directory.

---

### How can you identify special permissions?

Use:

```bash
ls -l
```

Look for:

* `s` in the owner's execute position → SUID
* `s` in the group's execute position → SGID
* `t` in the others' execute position → Sticky Bit

---

# Key Takeaways

* Linux provides three special permissions: **SUID**, **SGID**, and **Sticky Bit**.
* SUID executes a program with the owner's privileges.
* SGID executes a program with the group's privileges and enables group inheritance on directories.
* Sticky Bit protects files in shared directories from being deleted by other users.
* These permissions are widely used to improve security and collaboration in Linux systems.
