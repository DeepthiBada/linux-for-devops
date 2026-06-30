# Numeric Permissions (Octal Permissions)

## Overview

Linux allows file permissions to be assigned using **numeric (octal) values**. Instead of using symbols (`rwx`), permissions can be represented by numbers.

Numeric permissions provide a quick and efficient way to assign permissions using the `chmod` command.

---

# Permission Values

Each permission has a numeric value.

| Permission | Symbol | Value |
| ---------- | ------ | ----: |
| Read       | `r`    |     4 |
| Write      | `w`    |     2 |
| Execute    | `x`    |     1 |

---

# Calculating Numeric Permissions

Permissions are calculated by adding the values together.

| Permission | Calculation | Numeric Value |
| ---------- | ----------- | ------------: |
| `rwx`      | 4 + 2 + 1   |             7 |
| `rw-`      | 4 + 2       |             6 |
| `r-x`      | 4 + 1       |             5 |
| `r--`      | 4           |             4 |
| `-wx`      | 2 + 1       |             3 |
| `-w-`      | 2           |             2 |
| `--x`      | 1           |             1 |
| `---`      | 0           |             0 |

---

# Permission Structure

Linux permissions are assigned to three categories:

* **Owner (User)**
* **Group**
* **Others**

Example:

```text id="jlwm15"
chmod 754 file.txt
```

Breakdown:

```text id="jlwm16"
7      5      4
│      │      │
│      │      └── Others
│      └───────── Group
└──────────────── Owner
```

| Category | Value | Permission |
| -------- | ----: | ---------- |
| Owner    |     7 | `rwx`      |
| Group    |     5 | `r-x`      |
| Others   |     4 | `r--`      |

---

# Common Numeric Permissions

## 777

```text id="jlwm17"
rwxrwxrwx
```

* Owner: Read, Write, Execute
* Group: Read, Write, Execute
* Others: Read, Write, Execute

```bash id="jlwm18"
chmod 777 file.txt
```

> ⚠️ Not recommended for production because everyone has full access.

---

## 755

```text id="jlwm19"
rwxr-xr-x
```

* Owner: Read, Write, Execute
* Group: Read, Execute
* Others: Read, Execute

```bash id="jlwm20"
chmod 755 script.sh
```

**Common Use:** Executable scripts and application directories.

---

## 750

```text id="jlwm21"
rwxr-x---
```

Owner has full access, the group can read and execute, and others have no permissions.

---

## 700

```text id="jlwm22"
rwx------
```

Only the owner has full access.

**Common Use:** Private scripts and sensitive files.

---

## 644

```text id="jlwm23"
rw-r--r--
```

* Owner: Read, Write
* Group: Read
* Others: Read

```bash id="’wini24"
chmod 644 file.txt
```

**Common Use:** Configuration files, text files, documentation.

---

## 640

```text id="jlwm25"
rw-r-----
```

Owner can read/write, the group can read, and others have no access.

---

## 600

```text id="jlwm26"
rw-------
```

Only the owner can read and write.

**Common Use:** SSH private keys, passwords, and confidential files.

---

## 400

```text id="jlwm27"
r--------
```

Read-only access for the owner.

---

# Visual Representation

```text id="jlwm28"
Permission    Numeric

rwx  = 7
rw-  = 6
r-x  = 5
r--  = 4
-wx  = 3
-w-  = 2
--x  = 1
---  = 0
```

---

# Examples

Make a script executable:

```bash id="’wini29"
chmod 755 deploy.sh
```

Secure a private key:

```bash id="’wini30"
chmod 600 id_rsa
```

Give full access to the owner only:

```bash id="’wini31"
chmod 700 backup.sh
```

Set read-only permissions:

```bash id="’wini32"
chmod 444 notes.txt
```

---

# Real-World DevOps Use Cases

* `755` for executable scripts and application directories.
* `644` for configuration files that should not be executable.
* `600` for SSH private keys and secret files.
* `700` for backup or deployment scripts containing sensitive information.
* `750` for shared project directories where only group members need access.

---

# Best Practices

* Use the **least privilege** principle.
* Avoid `777` unless absolutely necessary.
* Keep SSH private keys at `600`.
* Use `755` for scripts that need to be executed.
* Use `644` for most configuration and text files.

---

# Interview Questions

### Why is `rwx` equal to `7`?

Because:

* Read = 4
* Write = 2
* Execute = 1

Total:

```text id="’wini33"
4 + 2 + 1 = 7
```

---

### What does `755` mean?

* Owner → Read, Write, Execute
* Group → Read, Execute
* Others → Read, Execute

---

### Which permission is recommended for SSH private keys?

```text id="’wini34"
600
```

---

### Why is `777` considered unsafe?

Because every user has full read, write, and execute permissions, increasing the risk of accidental or unauthorized modifications.

---

### Which permission is commonly used for text files?

```text id="’wini35"
644
```

---

# Key Takeaways

* Numeric permissions are based on the values: Read = 4, Write = 2, Execute = 1.
* Permissions are assigned separately to the Owner, Group, and Others.
* Common permissions include `755`, `700`, `644`, and `600`.
* Use the principle of least privilege to keep systems secure.
* Understanding numeric permissions is essential for Linux administration and DevOps.
