# DPKG (Debian Package)

## Overview

**DPKG (Debian Package)** is the low-level package management tool used in **Debian**, **Ubuntu**, **Linux Mint**, and other Debian-based Linux distributions.

It is used to install, remove, query, verify, and manage **`.deb`** packages.

Unlike **APT**, DPKG **does not automatically resolve package dependencies**.

---

# What is a DEB Package?

A **DEB package** is the standard software package format used in Debian-based Linux distributions.

A `.deb` package typically contains:

* Application files
* Executable binaries
* Configuration files
* Documentation
* Libraries
* Package metadata

Example:

```text
google-chrome-stable_current_amd64.deb
```

---

# Why Use DPKG?

DPKG allows administrators to:

* Install local `.deb` packages
* Remove installed packages
* Upgrade packages
* Display package information
* Verify installed packages
* List files installed by a package

---

# Syntax

```bash
dpkg [options] <package.deb>
```

---

# Install a DEB Package

```bash
sudo dpkg -i <package.deb>
```

Example

```bash
sudo dpkg -i google-chrome-stable_current_amd64.deb
```

> **Note:** If dependency errors occur, install the missing dependencies using:

```bash
sudo apt install -f
```

---

# Remove a Package

Remove the package but keep its configuration files.

```bash
sudo dpkg -r <package_name>
```

Example

```bash
sudo dpkg -r google-chrome-stable
```

---

# Completely Remove a Package

Remove both the package and its configuration files.

```bash
sudo dpkg -P <package_name>
```

Example

```bash
sudo dpkg -P google-chrome-stable
```

---

# List Installed Packages

Display all installed packages.

```bash
dpkg -l
```

Search for a package.

```bash
dpkg -l | grep nginx
```

---

# Display Package Information

```bash
dpkg -s <package_name>
```

Example

```bash
dpkg -s nginx
```

Displays:

* Package name
* Version
* Architecture
* Status
* Description

---

# List Files Installed by a Package

```bash
dpkg -L <package_name>
```

Example

```bash
dpkg -L nginx
```

---

# Find Which Package Owns a File

```bash
dpkg -S <file_path>
```

Example

```bash
dpkg -S /usr/bin/git
```

This command identifies the package that installed the specified file.

---

# Display Package Contents

View the contents of a `.deb` package without installing it.

```bash
dpkg -c <package.deb>
```

Example

```bash
dpkg -c google-chrome-stable_current_amd64.deb
```

---

# Common DPKG Commands

| Command   | Description                             |
| --------- | --------------------------------------- |
| `dpkg -i` | Install a `.deb` package                |
| `dpkg -r` | Remove a package                        |
| `dpkg -P` | Purge a package and configuration files |
| `dpkg -l` | List installed packages                 |
| `dpkg -s` | Display package information             |
| `dpkg -L` | List files installed by a package       |
| `dpkg -S` | Find which package owns a file          |
| `dpkg -c` | Display package contents                |

---

# Typical Workflow

Install a local package

```bash
sudo dpkg -i package.deb
```

Fix missing dependencies (if required)

```bash
sudo apt install -f
```

Verify installation

```bash
dpkg -l | grep package-name
```

Display package information

```bash
dpkg -s package-name
```

---

# Real-World DevOps Use Cases

* Install software downloaded from a vendor's website.
* Install local `.deb` packages on Ubuntu servers.
* Verify installed packages during troubleshooting.
* Identify which package installed a specific file.
* Audit software installed on production systems.

---

# Best Practices

* Use **APT** when installing software from repositories because it automatically resolves dependencies.
* Use **DPKG** for installing local `.deb` files.
* Verify package installation after deployment.
* Run `sudo apt install -f` if dependency issues occur after using `dpkg -i`.

---

# DPKG vs APT

| Feature                | DPKG    | APT    |
| ---------------------- | ------- | ------ |
| Package Format         | `.deb`  | `.deb` |
| Install Local Packages | ✅       | ✅      |
| Dependency Resolution  | ❌ No    | ✅ Yes  |
| Repository Support     | ❌ No    | ✅ Yes  |
| Search Packages        | Limited | ✅ Yes  |
| Update Packages        | ❌ No    | ✅ Yes  |

---

# DPKG vs RPM

| Feature               | DPKG           | RPM                 |
| --------------------- | -------------- | ------------------- |
| Package Format        | `.deb`         | `.rpm`              |
| Linux Family          | Debian, Ubuntu | RHEL, Rocky, Fedora |
| Install Package       | `dpkg -i`      | `rpm -ivh`          |
| Remove Package        | `dpkg -r`      | `rpm -e`            |
| Dependency Resolution | ❌ No           | ❌ No                |

---

# Interview Questions

### What is DPKG?

DPKG is the low-level package management tool used to manage `.deb` packages on Debian-based Linux distributions.

---

### Does DPKG automatically resolve dependencies?

No. DPKG installs packages but does not resolve dependencies automatically.

---

### Which command installs a `.deb` package?

```bash
sudo dpkg -i package.deb
```

---

### How do you fix dependency issues after using `dpkg -i`?

```bash
sudo apt install -f
```

---

### Which command lists all installed packages?

```bash
dpkg -l
```

---

### Which command identifies the package that owns a file?

```bash
dpkg -S /path/to/file
```

---

### What is the difference between DPKG and APT?

* **DPKG** is a low-level tool for managing local `.deb` packages.
* **APT** is a high-level package manager that uses DPKG underneath and automatically handles dependencies and repositories.

---

# Key Takeaways

* DPKG is the low-level package management tool for Debian-based systems.
* It manages `.deb` packages.
* DPKG installs, removes, queries, and inspects packages.
* It does not automatically resolve dependencies.
* APT is built on top of DPKG and provides dependency management, repository support, and software updates.
