# chgrp Command (Change Group)

## Overview

The `chgrp` (change group) command is used to **change the group ownership** of a file or directory in Linux.

It is commonly used when multiple users need to share files through a common group.

Unlike `chown`, which changes the owner (and optionally the group), `chgrp` changes **only the group ownership**.

---

# Why Do We Use chgrp?

The `chgrp` command helps to:

* Assign files to a different group.
* Allow multiple users to access shared resources.
* Simplify permission management.
* Manage project directories shared among teams.
* Improve collaboration in multi-user environments.

---

# View Current Group Ownership

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
chgrp [options] <group_name> <file_or_directory>
```

Example

```bash
sudo chgrp developers report.txt
```

---

# Change Group Ownership of a File

```bash
sudo chgrp developers report.txt
```

Verify:

```bash
ls -l report.txt
```

Output

```text
-rw-r--r-- 1 john developers 2048 Jul 2 report.txt
```

---

# Change Group Ownership of a Directory

```bash
sudo chgrp developers project
```

---

# Change Group Ownership Recursively

Use the `-R` option to change the group for a directory and all of its contents.

```bash
sudo chgrp -R developers project/
```

---

# Common Options

| Option | Description                                       |
| ------ | ------------------------------------------------- |
| `-R`   | Change group ownership recursively.               |
| `-v`   | Display every group ownership change.             |
| `-c`   | Display only files whose group ownership changed. |

---

# Examples

### Change the group of a file

```bash
sudo chgrp developers report.txt
```

---

### Change the group of a directory

```bash
sudo chgrp developers project/
```

---

### Change group ownership recursively

```bash
sudo chgrp -R developers project/
```

---

# Verify Group Ownership

Before changing the group:

```bash
ls -l report.txt
```

Output

```text
-rw-r--r-- 1 john sales 2048 report.txt
```

Change the group:

```bash
sudo chgrp developers report.txt
```

Verify again:

```bash
ls -l report.txt
```

Output

```text
-rw-r--r-- 1 john developers 2048 report.txt
```

---

# Real-World DevOps Use Cases

* Assign project files to the **developers** group.
* Share deployment scripts among DevOps engineers.
* Configure shared application directories.
* Manage log directories accessed by multiple services.
* Change group ownership of mounted volumes in Linux servers.

---

# Best Practices

* Verify group ownership using `ls -l`.
* Use `-R` carefully when changing groups recursively.
* Ensure users belong to the target group before assigning group ownership.
* Combine `chgrp` with proper file permissions for secure collaboration.

---

# chgrp vs chown

| Command | Purpose                                                  |
| ------- | -------------------------------------------------------- |
| `chgrp` | Changes only the group ownership of a file or directory. |
| `chown` | Changes the owner and optionally the group ownership.    |

Example:

Change only the group:

```bash
sudo chgrp developers report.txt
```

Change owner and group:

```bash
sudo chown john:developers report.txt
```

---

# Interview Questions

### What does the `chgrp` command do?

It changes the group ownership of a file or directory.

---

### Which command changes only the group ownership?

```bash
chgrp
```

---

### Which option changes the group recursively?

```bash
-R
```

---

### How do you verify group ownership?

```bash
ls -l
```

---

### What is the difference between `chgrp` and `chown`?

* `chgrp` changes only the group ownership.
* `chown` changes the owner and can also change the group ownership.

---

# Key Takeaways

* `chgrp` changes the group ownership of files and directories.
* Use `-R` to change group ownership recursively.
* Verify changes using `ls -l`.
* `chgrp` is useful for managing shared resources in multi-user environments.
* Use `chgrp` when only the group needs to change, and `chown` when changing the owner or both owner and group.
