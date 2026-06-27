# Help Commands

## Overview

Linux provides several built-in commands to help users understand how commands work, locate executables, and access documentation.

These commands are useful for learning Linux, troubleshooting issues, and exploring available command options.

---

# Common Help Commands

| Command   | Description                                                   |
| --------- | ------------------------------------------------------------- |
| `man`     | Displays the manual page for a command.                       |
| `--help`  | Shows a brief help message with available options.            |
| `whatis`  | Displays a one-line description of a command.                 |
| `which`   | Shows the path of an executable command.                      |
| `whereis` | Locates the executable, source, and manual page of a command. |
| `type`    | Identifies how the shell interprets a command.                |
| `info`    | Displays detailed GNU documentation for commands.             |

---

# 1. man

## Description

Displays the manual page for a command, including its syntax, options, and examples.

### Syntax

```bash
man <command>
```

### Examples

```bash
man ls
man cp
man mkdir
```

### Useful Navigation

| Key   | Action                   |
| ----- | ------------------------ |
| ↑ / ↓ | Scroll line by line      |
| Space | Next page                |
| b     | Previous page            |
| /     | Search within the manual |
| n     | Next search result       |
| q     | Quit the manual          |

---

# 2. --help

## Description

Displays a quick summary of a command and its available options.

### Syntax

```bash
<command> --help
```

### Examples

```bash
ls --help
cp --help
rm --help
```

This command is useful when you need a quick reference without opening the full manual.

---

# 3. whatis

## Description

Displays a short, one-line description of a command.

### Syntax

```bash
whatis <command>
```

### Examples

```bash
whatis ls
whatis cp
whatis grep
```

Example Output

```text
ls (1) - list directory contents
```

---

# 4. which

## Description

Displays the location of an executable command.

### Syntax

```bash
which <command>
```

### Examples

```bash
which python
which git
which ssh
```

Example Output

```text
/usr/bin/python
```

---

# 5. whereis

## Description

Displays the executable, source code, and manual page location of a command.

### Syntax

```bash
whereis <command>
```

### Examples

```bash
whereis python
whereis git
```

Example Output

```text
python:
/usr/bin/python
/usr/share/man/man1/python.1.gz
```

---

# 6. type

## Description

Identifies how the shell interprets a command.

It tells whether a command is:

* Built-in
* Alias
* Function
* External executable

### Syntax

```bash
type <command>
```

### Examples

```bash
type cd
type ls
type pwd
```

Example Output

```text
cd is a shell builtin
```

---

# 7. info

## Description

Displays detailed GNU documentation for supported commands.

It provides more comprehensive documentation than the `man` command for many GNU utilities.

### Syntax

```bash
info <command>
```

### Example

```bash
info ls
```

---

# Comparison of Help Commands

| Command   | Purpose                                        |
| --------- | ---------------------------------------------- |
| `man`     | Complete manual page                           |
| `--help`  | Quick usage guide                              |
| `whatis`  | One-line description                           |
| `which`   | Shows executable location                      |
| `whereis` | Shows executable, source, and manual locations |
| `type`    | Identifies command type                        |
| `info`    | Detailed GNU documentation                     |

---

# Real-World DevOps Use Cases

* Use `man` to learn command options while working on Linux servers.
* Use `which` to verify which version of a command is being executed.
* Use `whereis` when troubleshooting missing binaries or documentation.
* Use `type` to determine whether a command is a shell built-in or an external executable.
* Use `--help` for a quick reminder of command syntax during daily administration tasks.

---

# Interview Questions

### What is the difference between `man` and `--help`?

* `man` provides complete documentation, including descriptions, options, and examples.
* `--help` displays a concise summary of usage and available options.

---

### What is the purpose of the `which` command?

It displays the path of the executable that will be run when a command is executed.

Example:

```bash
which git
```

---

### What is the difference between `which` and `whereis`?

* `which` returns the executable path only.
* `whereis` returns the executable, source files, and manual page locations.

---

### Why is the `type` command useful?

It helps determine whether a command is a shell built-in, alias, function, or executable.

---

# Key Takeaways

* Linux provides multiple commands to access documentation and locate executables.
* Use `man` for detailed documentation and `--help` for quick command syntax.
* Use `which` and `whereis` to locate commands.
* Use `type` to identify how the shell interprets a command.
* Learning these commands improves productivity and makes troubleshooting easier.
