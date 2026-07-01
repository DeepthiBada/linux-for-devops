# APT Package Manager

## Overview

**APT (Advanced Package Tool)** is the default package manager for **Ubuntu**, **Debian**, and other Debian-based Linux distributions.

It simplifies software management by automatically handling:

* Package installation
* Package updates
* Package upgrades
* Package removal
* Dependency management

APT downloads packages from configured software repositories and installs them along with any required dependencies.

---

# Why Use APT?

APT helps administrators and developers to:

* Install software quickly
* Keep the system updated
* Manage software dependencies automatically
* Remove unused packages
* Search for available packages
* Display package information

---

# Check APT Version

```bash
apt --version
```

Example Output

```text
apt 2.4.11 (Ubuntu)
```

---

# Update Package Index

Downloads the latest package information from configured repositories.

```bash
sudo apt update
```

> **Note:** `apt update` updates the package list only. It does **not** install or upgrade software.

---

# Upgrade Installed Packages

Upgrades all installed packages to the latest available versions.

```bash
sudo apt upgrade
```

Example

```bash
sudo apt update
sudo apt upgrade
```

---

# Full System Upgrade

Performs a complete system upgrade, including installing or removing packages if required to satisfy dependencies.

```bash
sudo apt full-upgrade
```

---

# Install a Package

Install a software package.

```bash
sudo apt install <package_name>
```

Example

```bash
sudo apt install git
```

Install multiple packages

```bash
sudo apt install git curl wget
```

---

# Remove a Package

Remove an installed package while keeping its configuration files.

```bash
sudo apt remove <package_name>
```

Example

```bash
sudo apt remove nginx
```

---

# Completely Remove a Package

Removes both the package and its configuration files.

```bash
sudo apt purge <package_name>
```

Example

```bash
sudo apt purge nginx
```

---

# Remove Unused Dependencies

Remove packages that were installed automatically but are no longer required.

```bash
sudo apt autoremove
```

---

# Clean Downloaded Package Cache

Delete downloaded package files to free disk space.

```bash
sudo apt clean
```

Remove only obsolete package files.

```bash
sudo apt autoclean
```

---

# Search for a Package

Search repositories for available packages.

```bash
apt search <package_name>
```

Example

```bash
apt search docker
```

---

# Display Package Information

View details about a package.

```bash
apt show <package_name>
```

Example

```bash
apt show nginx
```

---

# List Installed Packages

Display all installed packages.

```bash
apt list --installed
```

List a specific package.

```bash
apt list --installed | grep git
```

---

# Common APT Commands

| Command                | Description                             |
| ---------------------- | --------------------------------------- |
| `apt update`           | Update package index                    |
| `apt upgrade`          | Upgrade installed packages              |
| `apt full-upgrade`     | Perform a complete system upgrade       |
| `apt install`          | Install packages                        |
| `apt remove`           | Remove packages                         |
| `apt purge`            | Remove packages and configuration files |
| `apt autoremove`       | Remove unused dependencies              |
| `apt clean`            | Clear downloaded package cache          |
| `apt search`           | Search for packages                     |
| `apt show`             | Display package information             |
| `apt list --installed` | List installed packages                 |

---

# Typical Workflow

Update package information

```bash
sudo apt update
```

Upgrade installed packages

```bash
sudo apt upgrade
```

Install Git

```bash
sudo apt install git
```

Verify installation

```bash
git --version
```

---

# Real-World DevOps Use Cases

* Install Git on a new Ubuntu server.
* Install Docker Engine on an EC2 instance.
* Install Nginx for hosting web applications.
* Apply security updates before production deployments.
* Remove unused packages to reduce disk usage.
* Keep development and production servers updated.

---

# Best Practices

* Run `sudo apt update` before installing new software.
* Regularly install security updates using `sudo apt upgrade`.
* Use `apt autoremove` to clean unnecessary packages.
* Use `apt purge` when removing software completely.
* Verify package names using `apt search` before installation.

---

# Interview Questions

### What is APT?

APT (Advanced Package Tool) is the package manager used in Ubuntu and Debian-based Linux distributions.

---

### What is the difference between `apt update` and `apt upgrade`?

* `apt update` refreshes the package index.
* `apt upgrade` installs newer versions of installed packages.

---

### What is the difference between `remove` and `purge`?

* `remove` deletes the package but keeps configuration files.
* `purge` removes both the package and its configuration files.

---

### Which command removes unused dependencies?

```bash
sudo apt autoremove
```

---

### Which command searches for available packages?

```bash
apt search <package_name>
```

---

### Which command displays detailed information about a package?

```bash
apt show <package_name>
```

---

# Key Takeaways

* APT is the default package manager for Ubuntu and Debian-based systems.
* Use `apt update` to refresh package information.
* Use `apt upgrade` to install available updates.
* Use `apt install` to install software.
* Use `apt remove` or `apt purge` to uninstall software.
* Use `apt autoremove` to clean unused dependencies.
* APT automatically resolves and installs required dependencies, making software management simple and reliable.
