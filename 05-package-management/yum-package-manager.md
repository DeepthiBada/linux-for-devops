# YUM Package Manager

## Overview

**YUM (Yellowdog Updater Modified)** is the traditional package manager used in **Red Hat Enterprise Linux (RHEL)**, **CentOS 7**, and other RPM-based Linux distributions.

YUM simplifies software management by downloading packages from repositories and automatically resolving dependencies.

Although modern RHEL-based distributions now use **DNF**, YUM is still widely used and commonly discussed in Linux administration and DevOps environments.

---

# Why Use YUM?

YUM helps administrators to:

* Install software packages
* Update installed software
* Remove packages
* Manage dependencies
* Search for packages
* Display package information

---

# Check YUM Version

```bash
yum --version
```

---

# Check Configured Repositories

```bash
yum repolist
```

Displays all enabled software repositories.

---

# Install a Package

```bash
sudo yum install <package_name>
```

Example

```bash
sudo yum install git
```

Install multiple packages

```bash
sudo yum install git wget curl
```

---

# Update Installed Packages

Update all installed packages

```bash
sudo yum update
```

Update a specific package

```bash
sudo yum update git
```

---

# Remove a Package

```bash
sudo yum remove <package_name>
```

Example

```bash
sudo yum remove nginx
```

---

# Search for a Package

```bash
yum search <package_name>
```

Example

```bash
yum search docker
```

---

# Display Package Information

```bash
yum info <package_name>
```

Example

```bash
yum info nginx
```

---

# List Installed Packages

```bash
yum list installed
```

Display information about an installed package

```bash
yum list installed | grep git
```

---

# List Available Packages

```bash
yum list available
```

---

# Check for Updates

```bash
yum check-update
```

Shows available updates without installing them.

---

# Clean YUM Cache

Remove downloaded metadata and cached packages.

```bash
sudo yum clean all
```

Rebuild the package cache.

```bash
sudo yum makecache
```

---

# Common YUM Commands

| Command              | Description                    |
| -------------------- | ------------------------------ |
| `yum install`        | Install a package              |
| `yum update`         | Update installed packages      |
| `yum remove`         | Remove a package               |
| `yum search`         | Search for a package           |
| `yum info`           | Display package information    |
| `yum list installed` | List installed packages        |
| `yum repolist`       | Display enabled repositories   |
| `yum check-update`   | Show available updates         |
| `yum clean all`      | Clear package cache            |
| `yum makecache`      | Rebuild package metadata cache |

---

# Typical Workflow

Display repositories

```bash
yum repolist
```

Search for Git

```bash
yum search git
```

Install Git

```bash
sudo yum install git
```

Verify installation

```bash
git --version
```

---

# Real-World DevOps Use Cases

* Install Git on RHEL servers.
* Install Docker on CentOS.
* Install Nginx on production servers.
* Update security patches.
* Verify configured repositories.
* Remove unused software from servers.

---

# Best Practices

* Check repositories before installing software.
* Keep systems updated regularly.
* Remove unused packages to reduce system size.
* Clean the package cache periodically.
* Verify installations after package updates.

---

# YUM vs APT

| Feature           | YUM           | APT            |
| ----------------- | ------------- | -------------- |
| Package Format    | `.rpm`        | `.deb`         |
| Operating Systems | RHEL, CentOS  | Ubuntu, Debian |
| Install Package   | `yum install` | `apt install`  |
| Update Packages   | `yum update`  | `apt upgrade`  |
| Remove Package    | `yum remove`  | `apt remove`   |
| Search Package    | `yum search`  | `apt search`   |

---

# Interview Questions

### What is YUM?

YUM (Yellowdog Updater Modified) is a package manager used on RHEL and CentOS systems to install, update, and remove software packages.

---

### Which package format does YUM use?

```text
.rpm
```

---

### Which command installs a package?

```bash
sudo yum install git
```

---

### Which command updates all installed packages?

```bash
sudo yum update
```

---

### Which command displays enabled repositories?

```bash
yum repolist
```

---

### Which command searches for a package?

```bash
yum search docker
```

---

# Key Takeaways

* YUM is the traditional package manager for RHEL and CentOS.
* It uses `.rpm` packages.
* YUM automatically resolves package dependencies.
* It supports package installation, updates, removal, and repository management.
* Understanding YUM is valuable because many enterprise Linux environments still use it or reference its commands.
