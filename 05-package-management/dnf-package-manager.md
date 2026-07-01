# DNF Package Manager

## Overview

**DNF (Dandified YUM)** is the modern package manager for **Fedora**, **RHEL 8/9**, **Rocky Linux**, and **AlmaLinux**.

It replaces YUM while maintaining a similar command syntax. DNF provides improved dependency resolution, better performance, lower memory usage, and enhanced package management features.

---

# Why DNF Replaced YUM?

DNF was introduced to overcome some limitations of YUM.

Benefits of DNF:

* Faster dependency resolution
* Better performance
* Lower memory consumption
* Improved package management
* Enhanced repository handling
* Better error reporting

> **Note:** On many modern RHEL-based systems, the `yum` command is still available and internally redirects to DNF for compatibility.

---

# Supported Linux Distributions

| Distribution | Package Manager | Package Format |
| ------------ | --------------- | -------------- |
| Fedora       | DNF             | `.rpm`         |
| RHEL 8 / 9   | DNF             | `.rpm`         |
| Rocky Linux  | DNF             | `.rpm`         |
| AlmaLinux    | DNF             | `.rpm`         |

---

# Check DNF Version

```bash
dnf --version
```

---

# Display Enabled Repositories

```bash
dnf repolist
```

Displays all configured repositories.

---

# Install a Package

```bash
sudo dnf install <package_name>
```

Example

```bash
sudo dnf install git
```

Install multiple packages

```bash
sudo dnf install git curl wget
```

---

# Update Installed Packages

Update all packages

```bash
sudo dnf upgrade
```

Update a specific package

```bash
sudo dnf upgrade git
```

---

# Remove a Package

```bash
sudo dnf remove <package_name>
```

Example

```bash
sudo dnf remove nginx
```

---

# Search for a Package

```bash
dnf search <package_name>
```

Example

```bash
dnf search docker
```

---

# Display Package Information

```bash
dnf info <package_name>
```

Example

```bash
dnf info nginx
```

---

# List Installed Packages

```bash
dnf list installed
```

Search within installed packages

```bash
dnf list installed | grep git
```

---

# List Available Packages

```bash
dnf list available
```

---

# Check for Available Updates

```bash
dnf check-update
```

Displays available package updates without installing them.

---

# Clean Cached Packages

```bash
sudo dnf clean all
```

Rebuild the cache

```bash
sudo dnf makecache
```

---

# Display Package History

One useful feature of DNF is package history.

```bash
dnf history
```

This displays:

* Installed packages
* Removed packages
* Updated packages
* Transaction history

---

# Common DNF Commands

| Command              | Description                         |
| -------------------- | ----------------------------------- |
| `dnf install`        | Install a package                   |
| `dnf upgrade`        | Upgrade installed packages          |
| `dnf remove`         | Remove a package                    |
| `dnf search`         | Search for packages                 |
| `dnf info`           | Display package information         |
| `dnf repolist`       | Display repositories                |
| `dnf list installed` | List installed packages             |
| `dnf check-update`   | Show available updates              |
| `dnf clean all`      | Clear package cache                 |
| `dnf history`        | Display package transaction history |

---

# Typical Workflow

Update repository metadata

```bash
sudo dnf makecache
```

Search for Git

```bash
dnf search git
```

Install Git

```bash
sudo dnf install git
```

Verify installation

```bash
git --version
```

---

# Real-World DevOps Use Cases

* Install Docker on Rocky Linux servers.
* Install Nginx on RHEL 9.
* Apply security updates during maintenance windows.
* Review package installation history for troubleshooting.
* Configure new cloud instances with required software.

---

# Best Practices

* Keep package metadata up to date.
* Upgrade systems regularly.
* Clean cached packages periodically.
* Verify repositories before installing software.
* Use package history to troubleshoot installation issues.

---

# DNF vs YUM

| Feature               | DNF                                | YUM                  |
| --------------------- | ---------------------------------- | -------------------- |
| Package Format        | `.rpm`                             | `.rpm`               |
| Dependency Resolution | Improved                           | Good                 |
| Performance           | Faster                             | Slower               |
| Memory Usage          | Lower                              | Higher               |
| Transaction History   | Yes                                | Limited              |
| Used In               | Fedora, RHEL 8/9, Rocky, AlmaLinux | Older RHEL, CentOS 7 |

---

# DNF vs APT

| Feature           | DNF                            | APT            |
| ----------------- | ------------------------------ | -------------- |
| Package Format    | `.rpm`                         | `.deb`         |
| Operating Systems | Fedora, RHEL, Rocky, AlmaLinux | Ubuntu, Debian |
| Install Package   | `dnf install`                  | `apt install`  |
| Update Packages   | `dnf upgrade`                  | `apt upgrade`  |
| Remove Package    | `dnf remove`                   | `apt remove`   |
| Search Package    | `dnf search`                   | `apt search`   |

---

# Interview Questions

### What is DNF?

DNF (Dandified YUM) is the modern package manager for Fedora and RHEL-based Linux distributions.

---

### Why was DNF introduced?

To provide better dependency resolution, improved performance, lower memory usage, and enhanced package management compared to YUM.

---

### Which package format does DNF use?

```text
.rpm
```

---

### Which command installs a package?

```bash
sudo dnf install git
```

---

### Which command shows package transaction history?

```bash
dnf history
```

---

### Is the `yum` command still available on modern RHEL systems?

Yes. On many RHEL 8/9 systems, `yum` is available as a compatibility command that internally uses DNF.

---

# Key Takeaways

* DNF is the modern replacement for YUM.
* It manages `.rpm` packages.
* DNF offers better dependency resolution and performance.
* It supports package installation, upgrades, removal, repository management, and transaction history.
* DNF is the default package manager for Fedora, RHEL 8/9, Rocky Linux, and AlmaLinux.
