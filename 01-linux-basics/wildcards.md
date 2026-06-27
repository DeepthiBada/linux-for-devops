# Wildcards

## Overview

Wildcards are special characters used to match one or more files or directories based on patterns instead of specifying exact file names.

They help simplify file management tasks such as listing, copying, moving, and deleting multiple files.

---

# Common Wildcards

| Wildcard | Description                                   |
| -------- | --------------------------------------------- |
| `*`      | Matches zero or more characters               |
| `?`      | Matches exactly one character                 |
| `[]`     | Matches any one character within the brackets |

---

# 1. Asterisk (`*`)

## Description

The `*` wildcard matches **zero or more characters**.

It is the most commonly used wildcard in Linux.

### Examples

List all files:

```bash
ls *
```

List all text files:

```bash
ls *.txt
```

Copy all log files:

```bash
cp *.log backup/
```

Delete all temporary files:

```bash
rm *.tmp
```

Move all PDF files:

```bash
mv *.pdf Documents/
```

---

# 2. Question Mark (`?`)

## Description

The `?` wildcard matches **exactly one character**.

### Examples

Suppose the directory contains:

```text
file1.txt
file2.txt
file10.txt
```

Command:

```bash
ls file?.txt
```

Output:

```text
file1.txt
file2.txt
```

`file10.txt` is not matched because `10` consists of two characters.

---

# 3. Square Brackets (`[]`)

## Description

Square brackets match **any one character** from the specified set or range.

### Examples

Match files beginning with `a`, `b`, or `c`:

```bash
ls [abc]*
```

Output:

```text
apple.txt
banana.txt
cat.txt
```

Match files beginning with any digit:

```bash
ls [0-9]*
```

Match files beginning with letters A to Z:

```bash
ls [A-Za-z]*
```

---

# Combining Wildcards

Wildcards can be combined to create more flexible search patterns.

### Example 1

List all `.log` files that start with `app`:

```bash
ls app*.log
```

---

### Example 2

Copy all files beginning with `report`:

```bash
cp report* backup/
```

---

### Example 3

Delete all `.tmp` files:

```bash
rm *.tmp
```

---

# Real-World DevOps Use Cases

* Archive all log files:

```bash
tar -czf logs.tar.gz *.log
```

* Delete old temporary files:

```bash
rm *.tmp
```

* Copy configuration files:

```bash
cp *.conf backup/
```

* Move application logs:

```bash
mv *.log /var/log/archive/
```

* Find all shell scripts:

```bash
ls *.sh
```

---

# Best Practices

* Use `ls` first to verify which files match the wildcard pattern before using commands like `rm` or `mv`.
* Be cautious with commands such as:

```bash
rm *
```

This removes **all files** in the current directory.

* When deleting multiple files, consider using interactive mode:

```bash
rm -i *.log
```

This prompts for confirmation before deleting each file.

---

# Interview Questions

### What is a wildcard in Linux?

A wildcard is a special character used to match files or directories based on a pattern.

---

### What does `*` represent?

It matches zero or more characters.

Example:

```bash
ls *.txt
```

---

### What does `?` represent?

It matches exactly one character.

Example:

```bash
ls file?.txt
```

---

### What does `[]` represent?

It matches any one character from a specified set or range.

Example:

```bash
ls [abc]*
```

---

# Key Takeaways

* Wildcards simplify working with multiple files and directories.
* `*` matches zero or more characters.
* `?` matches exactly one character.
* `[]` matches one character from a set or range.
* Always verify wildcard matches before performing destructive operations like `rm` or `mv`.
