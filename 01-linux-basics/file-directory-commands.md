# File & Directory Commands

## Overview

File and directory management commands are used to create, copy, move, rename, and delete files and directories in Linux. These are some of the most frequently used commands by Linux administrators and DevOps engineers.

---

# Common File & Directory Commands

| Command | Description                                                       |
| ------- | ----------------------------------------------------------------- |
| `touch` | Create an empty file or update the timestamp of an existing file. |
| `mkdir` | Create a new directory.                                           |
| `rmdir` | Remove an empty directory.                                        |
| `cp`    | Copy files and directories.                                       |
| `mv`    | Move or rename files and directories.                             |
| `rm`    | Delete files and directories.                                     |

---

# 1. touch

## Description

Creates a new empty file. If the file already exists, it updates the file's timestamp.

### Syntax

```bash
touch <filename>
```

### Examples

```bash
touch notes.txt
touch app.log
```

---

# 2. mkdir

## Description

Creates a new directory.

### Syntax

```bash
mkdir <directory_name>
```

### Common Options

| Option | Description                                     |
| ------ | ----------------------------------------------- |
| `-p`   | Creates parent directories if they don't exist. |

### Examples

```bash
mkdir project

mkdir project/docs

mkdir -p project/src/java
```

---

# 3. cp

## Description

Copies files or directories from one location to another.

### Syntax

```bash
cp [options] <source> <destination>
```

### Common Options

| Option | Description                               |
| ------ | ----------------------------------------- |
| `-r`   | Copy directories recursively.             |
| `-i`   | Prompt before overwriting.                |
| `-v`   | Display copied files.                     |
| `-p`   | Preserve file permissions and timestamps. |

### Examples

```bash
cp file1.txt backup.txt

cp file1.txt Documents/

cp -r project backup/

cp -iv file.txt backup/
```

---

# 4. mv

## Description

Moves files or directories to a new location. It is also used to rename files and directories.

### Syntax

```bash
mv [options] <source> <destination>
```

### Common Options

| Option | Description                      |
| ------ | -------------------------------- |
| `-i`   | Prompt before overwriting.       |
| `-v`   | Display moved files.             |
| `-n`   | Do not overwrite existing files. |

### Examples

```bash
mv file1.txt file2.txt

mv report.txt Documents/

mv project backup/

mv oldname.txt newname.txt
```

---

# 5. rm

## Description

Deletes files and directories.

> ⚠️ Be careful! Files deleted using `rm` cannot be recovered from the Recycle Bin.

### Syntax

```bash
rm [options] <file>
```

### Common Options

| Option | Description                          |
| ------ | ------------------------------------ |
| `-r`   | Delete directories recursively.      |
| `-f`   | Force deletion without confirmation. |
| `-i`   | Ask before deleting.                 |
| `-v`   | Display deleted files.               |

### Examples

```bash
rm file.txt

rm -i file.txt

rm -rf project/

rm -rv project/
```

---

# 6. rmdir

## Description

Removes an empty directory.

### Syntax

```bash
rmdir <directory_name>
```

### Example

```bash
rmdir test
```

> Note: `rmdir` works only if the directory is empty. Use `rm -r` to remove a directory containing files.

---

# Real-World DevOps Use Cases

* Create configuration files using `touch`.
* Create project folders using `mkdir`.
* Copy configuration files before making changes using `cp`.
* Rename log files using `mv`.
* Delete temporary files using `rm`.
* Remove unused empty directories using `rmdir`.

---

# Interview Questions

### What is the difference between `cp` and `mv`?

* `cp` creates a copy while keeping the original file.
* `mv` moves the file or renames it without creating a duplicate.

---

### What is the difference between `rm` and `rmdir`?

* `rm` removes files and directories (with `-r`).
* `rmdir` removes only empty directories.

---

### Which command is used to rename a file?

```bash
mv oldname.txt newname.txt
```

---

### How do you copy an entire directory?

```bash
cp -r project backup/
```

---

## Key Takeaways

* Use `touch` to create files.
* Use `mkdir` to create directories.
* Use `cp` to copy files or directories.
* Use `mv` to move or rename files.
* Use `rm` to delete files and directories.
* Use `rmdir` only for empty directories.
