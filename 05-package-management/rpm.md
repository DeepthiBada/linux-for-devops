# RPM (RPM Package Manager)

## Overview

**RPM (RPM Package Manager)** is a low-level package management tool used in **RHEL**, **CentOS**, **Rocky Linux**, **AlmaLinux**, and **Fedora**.

It is used to install, query, verify, upgrade, and remove **`.rpm`** packages.

Unlike **YUM** or **DNF**, RPM **does not automatically resolve package dependencies**.

---

# What is an RPM Package?

An **RPM package** is a software package used by RPM-based Linux distributions.

An RPM package contains:

* Application files
* Executable binaries
* Configuration files
* Documentation
* Metadata
* Version information

Example:

```text
nginx-1.24.0-1.x86_64.rpm
```

---

# Why Use RPM?

RPM allows administrators to:

* Install local `.rpm` packages.
* Upgrade installed software.
* Remove packages.
* Verify package integrity.
* Query package information.
* List installed files belonging to a package.

---

# Syntax

```bash
rpm [options] <package.rpm>
```

---

# Install an RPM Package

```bash
sudo rpm -ivh package.rpm
```

### Options

| Option | Description                             |
| ------ | --------------------------------------- |
| `-i`   | Install package                         |
| `-v`   | Verbose output                          |
| `-h`   | Display progress using hash (`#`) marks |

Example

```bash
sudo rpm -ivh nginx.rpm
```

---

# Upgrade an RPM Package

```bash
sudo rpm -Uvh package.rpm
```

Example

```bash
sudo rpm -Uvh nginx.rpm
```

The package is upgraded if already installed.

If it is not installed, RPM installs it.

---

# Remove a Package

```bash
sudo rpm -e <package_name>
```

Example

```bash
sudo rpm -e nginx
```

> **Note:** Use the package name, not the `.rpm` filename.

---

# Query Installed Packages

List all installed RPM packages.

```bash
rpm -qa
```

Search for a package.

```bash
rpm -qa | grep nginx
```

---

# Display Package Information

```bash
rpm -qi <package_name>
```

Example

```bash
rpm -qi nginx
```

Displays:

* Package name
* Version
* Release
* Architecture
* Installation date
* Description

---

# List Files Installed by a Package

```bash
rpm -ql <package_name>
```

Example

```bash
rpm -ql nginx
```

---

# Verify an Installed Package

```bash
rpm -V <package_name>
```

Example

```bash
rpm -V nginx
```

This verifies that installed package files have not been modified or corrupted.

---

# Display Package Dependencies

```bash
rpm -qpR package.rpm
```

Shows the dependencies required by a package **before** installation.

---

# Common RPM Commands

| Command    | Description                       |
| ---------- | --------------------------------- |
| `rpm -ivh` | Install a package                 |
| `rpm -Uvh` | Upgrade a package                 |
| `rpm -e`   | Remove a package                  |
| `rpm -qa`  | List all installed packages       |
| `rpm -qi`  | Display package information       |
| `rpm -ql`  | List files installed by a package |
| `rpm -V`   | Verify package integrity          |
| `rpm -qpR` | Display package dependencies      |

---

# Typical Workflow

Install a local package

```bash
sudo rpm -ivh nginx.rpm
```

Verify installation

```bash
rpm -qi nginx
```

List installed files

```bash
rpm -ql nginx
```

Remove the package

```bash
sudo rpm -e nginx
```

---

# Real-World DevOps Use Cases

* Install locally downloaded RPM packages.
* Verify package integrity after deployment.
* Audit installed software on production servers.
* Inspect package contents before installation.
* Troubleshoot package installation issues.

---

# Best Practices

* Use `dnf` or `yum` for installing software from repositories because they automatically resolve dependencies.
* Use `rpm` when working with local `.rpm` files.
* Verify package integrity before deploying software.
* Confirm package dependencies before installation.

---

# RPM vs YUM vs DNF

| Feature                | RPM     | YUM     | DNF     |
| ---------------------- | ------- | ------- | ------- |
| Package Type           | `.rpm`  | `.rpm`  | `.rpm`  |
| Install Local Packages | ✅       | ✅       | ✅       |
| Dependency Resolution  | ❌ No    | ✅ Yes   | ✅ Yes   |
| Repository Support     | ❌ No    | ✅ Yes   | ✅ Yes   |
| Updates                | Limited | ✅ Yes   | ✅ Yes   |
| Package Verification   | ✅ Yes   | Limited | Limited |

---

# Interview Questions

### What is RPM?

RPM (RPM Package Manager) is a low-level package management tool used to install, query, verify, upgrade, and remove `.rpm` packages.

---

### Does RPM resolve dependencies automatically?

No. RPM does not automatically resolve dependencies. Package managers such as **YUM** and **DNF** handle dependency resolution.

---

### Which command installs an RPM package?

```bash
sudo rpm -ivh package.rpm
```

---

### Which command lists all installed RPM packages?

```bash
rpm -qa
```

---

### Which command displays package information?

```bash
rpm -qi <package_name>
```

---

### Which command verifies package integrity?

```bash
rpm -V <package_name>
```

---

### What is the difference between RPM and DNF?

* **RPM** is a low-level package management tool.
* **DNF** is a high-level package manager that uses RPM underneath and automatically resolves dependencies.

---

# Key Takeaways

* RPM is the package management tool for `.rpm` packages.
* It is commonly used on RHEL, Rocky Linux, AlmaLinux, Fedora, and related distributions.
* RPM installs, removes, queries, verifies, and upgrades packages.
* RPM does not automatically resolve dependencies.
* DNF and YUM are built on top of RPM and provide dependency management and repository support.
