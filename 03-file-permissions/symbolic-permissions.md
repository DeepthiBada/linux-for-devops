# Symbolic Permissions

## Overview

In Linux, permissions can also be modified using **symbolic notation** instead of numeric values.

Symbolic permissions provide a flexible way to **add**, **remove**, or **assign** permissions to specific users or groups without changing other existing permissions.

---

# Symbolic Permission Components

A symbolic permission consists of three parts:

```text
[User Category][Operator][Permission]
```

Example:

```bash
chmod u+x script.sh
```

Breakdown:

| Component | Meaning            |
| --------- | ------------------ |
| `u`       | User (Owner)       |
| `+`       | Add permission     |
| `x`       | Execute permission |

---

# User Categories

| Symbol | Description                 |
| ------ | --------------------------- |
| `u`    | User (Owner)                |
| `g`    | Group                       |
| `o`    | Others                      |
| `a`    | All (User + Group + Others) |

---

# Operators

| Operator | Description                                       |
| -------- | ------------------------------------------------- |
| `+`      | Add permission                                    |
| `-`      | Remove permission                                 |
| `=`      | Assign permission (replaces existing permissions) |

---

# Permission Symbols

| Symbol | Permission |
| ------ | ---------- |
| `r`    | Read       |
| `w`    | Write      |
| `x`    | Execute    |

---

# Using the '+' Operator

The `+` operator adds permissions without affecting existing permissions.

### Add execute permission for the owner

```bash
chmod u+x script.sh
```

### Add write permission for the group

```bash
chmod g+w project.txt
```

### Add read permission for others

```bash
chmod o+r notes.txt
```

### Add execute permission for everyone

```bash
chmod a+x deploy.sh
```

---

# Using the '-' Operator

The `-` operator removes permissions.

### Remove write permission from the owner

```bash
chmod u-w report.txt
```

### Remove execute permission from the group

```bash
chmod g-x app.sh
```

### Remove read permission from others

```bash
chmod o-r confidential.txt
```

### Remove execute permission for everyone

```bash
chmod a-x script.sh
```

---

# Using the '=' Operator

The `=` operator replaces the existing permissions with the specified permissions.

### Give the owner only read and write permissions

```bash
chmod u=rw file.txt
```

### Give the group only read permission

```bash
chmod g=r file.txt
```

### Remove all permissions from others

```bash
chmod o= file.txt
```

---

# Combining Multiple Changes

You can modify multiple user categories in a single command.

### Example 1

```bash
chmod u+rwx,g+rx,o-r file.txt
```

Meaning:

* Owner → Add Read, Write, Execute
* Group → Add Read and Execute
* Others → Remove Read

---

### Example 2

```bash
chmod u=rw,g=r,o= file.txt
```

Meaning:

* Owner → Read and Write
* Group → Read only
* Others → No permissions

---

# View Permissions

Before changing permissions:

```bash
ls -l file.txt
```

After changing permissions:

```bash
chmod u+x file.txt
ls -l file.txt
```

Example Output

```text
-rwxr--r--
```

---

# Real-World DevOps Use Cases

* Make deployment scripts executable.

```bash
chmod +x deploy.sh
```

* Remove write permission from configuration files.

```bash
chmod g-w application.conf
```

* Grant execute permission to all users for maintenance scripts.

```bash
chmod a+x cleanup.sh
```

* Restrict access to sensitive files.

```bash
chmod o-r secrets.txt
```

---

# Best Practices

* Grant only the permissions that are required.
* Use symbolic mode when making small permission changes.
* Verify permission changes using `ls -l`.
* Avoid granting unnecessary permissions to **Others**.

---

# Symbolic vs Numeric Permissions

| Symbolic | Numeric                                           | Description                            |
| -------- | ------------------------------------------------- | -------------------------------------- |
| `u+x`    | `chmod 755` *(depending on existing permissions)* | Add execute permission to the owner    |
| `g-w`    | N/A                                               | Remove write permission from the group |
| `o+r`    | N/A                                               | Add read permission to others          |
| `a+x`    | N/A                                               | Add execute permission to everyone     |

> **Note:** Symbolic mode modifies only the specified permissions, while numeric mode sets all permissions for Owner, Group, and Others.

---

# Interview Questions

### What are symbolic permissions?

Symbolic permissions use letters (`u`, `g`, `o`, `a`, `r`, `w`, `x`) and operators (`+`, `-`, `=`) to modify file permissions.

---

### What does the following command do?

```bash
chmod u+x script.sh
```

Adds execute permission to the file owner.

---

### What is the difference between `+` and `=`?

* `+` adds permissions without affecting existing ones.
* `=` replaces the existing permissions with the specified permissions.

---

### What does `chmod a+r file.txt` do?

It grants read permission to the owner, group, and others.

---

### When should symbolic permissions be used?

Use symbolic permissions when you want to add, remove, or modify specific permissions without changing the entire permission set.

---

# Key Takeaways

* Symbolic permissions modify permissions using letters and operators.
* `u`, `g`, `o`, and `a` represent different user categories.
* `+` adds permissions, `-` removes permissions, and `=` replaces permissions.
* Symbolic mode is ideal for making targeted permission changes.
* Use `ls -l` to verify permission changes after running `chmod`.
