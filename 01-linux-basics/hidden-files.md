# Hidden Files & Directories

## Overview

In Linux, hidden files and directories are files whose names begin with a dot (`.`). These files are not displayed by default when using the `ls` command.

Hidden files are commonly used to store configuration settings, user preferences, and application-specific data.

---

# Why are Hidden Files Used?

Hidden files help keep configuration and system files separate from regular user files. They reduce clutter in directories while allowing applications to store settings safely.

Examples include:

* Shell configuration
* Git configuration
* SSH keys
* Application settings

---

# How to View Hidden Files

### List Hidden Files

```bash
ls -a
```

Displays all files, including hidden files.

Example:

```bash
$ ls -a

.  ..  .bashrc  .profile  Documents  Downloads
```

---

### List Hidden Files in Long Format

```bash
ls -la
```

Displays:

* File permissions
* Owner
* Group
* File size
* Last modified date

Example:

```bash
$ ls -la
```

---

# Common Hidden Files

| File         | Description                       |
| ------------ | --------------------------------- |
| `.bashrc`    | Bash shell configuration          |
| `.profile`   | User login configuration          |
| `.gitconfig` | Git user configuration            |
| `.gitignore` | Specifies files Git should ignore |
| `.ssh/`      | Stores SSH keys and configuration |
| `.vimrc`     | Vim editor configuration          |

---

# Understanding "." and ".."

| Symbol | Description       |
| ------ | ----------------- |
| `.`    | Current directory |
| `..`   | Parent directory  |

Examples:

```bash
cd .
```

Stay in the current directory.

```bash
cd ..
```

Move to the parent directory.

---

# Create a Hidden File

Simply start the filename with a dot.

```bash
touch .env
```

or

```bash
touch .config
```

Verify:

```bash
ls -a
```

---

# Rename a File to Hidden

```bash
mv notes.txt .notes.txt
```

The file becomes hidden because its name starts with a dot.

---

# Real-World DevOps Use Cases

* Store SSH keys in `.ssh/`
* Keep environment variables in `.env`
* Configure Git using `.gitconfig`
* Exclude files from version control using `.gitignore`
* Customize shell behavior with `.bashrc`

---

# Interview Questions

### How do you identify a hidden file in Linux?

A hidden file starts with a dot (`.`).

Example:

```text
.bashrc
```

---

### Which command displays hidden files?

```bash
ls -a
```

or

```bash
ls -la
```

---

### How do you create a hidden file?

```bash
touch .env
```

---

### What is the purpose of `.gitignore`?

It tells Git which files or directories should not be tracked.

---

# Key Takeaways

* Hidden files begin with a dot (`.`).
* They are mainly used for configuration and user settings.
* Use `ls -a` or `ls -la` to view hidden files.
* Files can be hidden simply by renaming them with a leading dot.
* Hidden files play an important role in Linux administration and DevOps workflows.
