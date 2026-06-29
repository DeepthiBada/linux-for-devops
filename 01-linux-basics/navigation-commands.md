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

# Understanding the Linux Command Prompt

When you open a Linux terminal, you will see a command prompt similar to the following:

```text
root@ubuntu-dev:/#
```

Each part of the prompt has a specific meaning.

| Part         | Description                                                         |
| ------------ | ------------------------------------------------------------------- |
| `root`       | The currently logged-in user.                                       |
| `ubuntu-dev` | The hostname (computer or server name).                             |
| `:`          | Separator between the hostname and the current working directory.   |
| `/`          | Current working directory. Here, `/` represents the root directory. |
| `#`          | Indicates you are logged in as the **root (administrator)** user.   |

---

## Prompt Breakdown

```text
root@ubuntu-dev:/#
│      │          │ │
│      │          │ └── Root user prompt (`#`)
│      │          └──── Current working directory (`/`)
│      └─────────────── Hostname (System Name)
└────────────────────── Logged-in User
```

---

## User Prompt vs Root Prompt

### Root User

```text
root@ubuntu-dev:/#
```

* Logged in as the **root (administrator)** user.
* Has full access to the system.
* Prompt ends with `#`.

---

### Normal User

```text
deepthi@ubuntu-dev:~$
```

* Logged in as a regular user.
* Has limited permissions.
* Prompt ends with `$`.

---

## Symbols Used in the Prompt

| Symbol | Meaning                                       |
| ------ | --------------------------------------------- |
| `@`    | Separates the username and hostname.          |
| `:`    | Separates the hostname and current directory. |
| `/`    | Root directory.                               |
| `~`    | Home directory of the current user.           |
| `$`    | Normal user prompt.                           |
| `#`    | Root (administrator) user prompt.             |

---

## Examples

Current directory is the root directory:

```text
root@ubuntu-dev:/#
```

Current directory is the home directory:

```text
deepthi@ubuntu-dev:~$
```

Current directory is `/var/log`:

```text
deepthi@ubuntu-dev:/var/log$
```

---

## Interview Question

### What is the difference between `$` and `#` in the Linux prompt?

* `$` indicates a **regular (non-root)** user.
* `#` indicates the **root (administrator)** user with full system privileges.
