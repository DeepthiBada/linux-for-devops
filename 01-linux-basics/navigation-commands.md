# Navigation Commands

## Overview

Navigation commands are used to move through the Linux file system, identify your current location, list directory contents, and determine the current logged-in user.

These commands are essential for working efficiently from the Linux terminal.

---

## Common Navigation Commands

| Command  | Description                             |
| -------- | --------------------------------------- |
| `pwd`    | Displays the current working directory. |
| `whoami` | Displays the current logged-in user.    |
| `ls`     | Lists files and directories.            |
| `cd`     | Changes the current directory.          |

---

## 1. pwd

### Description

Displays the absolute path of the current working directory.

### Syntax

```bash
pwd
```

### Example

```bash
$ pwd
/home/deepthi/linux-devops-lab
```

---

## 2. whoami

### Description

Displays the username of the currently logged-in user.

### Syntax

```bash
whoami
```

### Example

```bash
$ whoami
deepthi
```

---

## 3. ls

### Description

Lists the contents of a directory.

### Syntax

```bash
ls [options] [directory]
```

### Common Options

| Option | Description                         |
| ------ | ----------------------------------- |
| `-l`   | Long listing format                 |
| `-a`   | Show hidden files                   |
| `-la`  | Long listing including hidden files |
| `-h`   | Human-readable file sizes           |

### Examples

```bash
ls

ls -l

ls -la

ls /home
```

---

## 4. cd

### Description

Changes the current working directory.

### Syntax

```bash
cd <directory>
```

### Examples

```bash
cd Documents

cd ..

cd ~

cd /

cd /home/deepthi
```

---

## Real-World Use Cases

* Use `pwd` to verify your current location before executing commands.
* Use `whoami` to confirm the active user, especially when working with multiple accounts.
* Use `ls -la` to inspect directory contents, including hidden files.
* Use `cd` to navigate between project directories.

---

## Interview Questions

### What is the difference between `pwd` and `ls`?

* `pwd` displays the current directory path.
* `ls` lists the files and directories inside the current directory.

### What does `cd ..` do?

Moves to the parent directory.

### How do you go to your home directory?

```bash
cd ~
```

or simply

```bash
cd
```
