# Linux User Management

## Overview

Linux is a multi-user operating system, which means multiple users can access and use the same system simultaneously.

Each user has a unique identity, home directory, permissions, and ownership of files. User management is an essential part of Linux system administration and DevOps because it helps control access to system resources securely.

---

# What is a User?

A **user** is an account that allows a person or application to log in and interact with the Linux operating system.

Each user has:

* A unique username
* A User ID (UID)
* A Home directory
* A Default shell
* One primary group
* Zero or more secondary groups

---

# Why Do We Need Users?

Linux uses user accounts to:

* Control access to files and directories
* Protect system resources
* Identify who is using the system
* Improve system security
* Allow multiple users to work independently

Example:

* A developer can access project files.
* A database administrator can manage databases.
* A normal user cannot modify critical system files.

---

# Types of Users in Linux

Linux has three main types of users.

## 1. Root User

The **root** user is the system administrator with unrestricted access to the system.

### Characteristics

* Username: `root`
* UID: `0`
* Can access all files and directories.
* Can create, modify, or delete any user.
* Can install or remove software.
* Can change system configurations.

Example Prompt

```text id="wkj9yr"
root@ubuntu:/#
```

> **Note:** Use the root account carefully because incorrect commands can affect the entire system.

---

## 2. System Users

System users are created automatically during the installation of Linux or applications.

They are mainly used to run services and background processes.

Examples:

```text id="fwjlwm"
daemon
www-data
mysql
sshd
nobody
```

Characteristics:

* Usually cannot log in interactively.
* Used by system services.
* Have low User IDs (distribution dependent).

---

## 3. Regular (Normal) Users

Regular users are created by administrators for daily work.

Examples:

```text id="cqg9mk"
deepthi
john
alice
```

Characteristics:

* Can access their own files.
* Have limited permissions.
* Cannot modify system files without elevated privileges.
* Can use `sudo` if granted permission.

Example Prompt

```text id="1v9nwa"
deepthi@ubuntu:~$
```

---

# User Information

Each Linux user has the following attributes:

| Attribute        | Description                        |
| ---------------- | ---------------------------------- |
| Username         | Name used to log in                |
| UID              | Unique User ID                     |
| Home Directory   | Default directory after login      |
| Shell            | Command interpreter (e.g., Bash)   |
| Primary Group    | Default group assigned to the user |
| Secondary Groups | Additional groups for permissions  |

---

# Important User Files

| File          | Purpose                         |
| ------------- | ------------------------------- |
| `/etc/passwd` | Stores user account information |
| `/etc/shadow` | Stores encrypted user passwords |
| `/etc/group`  | Stores group information        |

---

# Display Current User

### whoami

Displays the current logged-in user.

```bash id="jlwmc8"
whoami
```

Example

```text id="ytb94g"
deepthi
```

---

### id

Displays detailed information about the current user.

```bash id="zjlwmr"
id
```

Example

```text id="lm5qwg"
uid=1000(deepthi)
gid=1000(deepthi)
groups=1000(deepthi),27(sudo)
```

---

### who

Displays users currently logged into the system.

```bash id="t3xjqm"
who
```

---

### users

Displays the usernames of users currently logged in.

```bash id="vj4kbi"
users
```

---

# Real-World DevOps Use Cases

* Create separate user accounts for developers and administrators.
* Run applications using dedicated service accounts instead of the root user.
* Restrict access to production servers.
* Grant administrative privileges using `sudo` instead of sharing the root password.

---

# Interview Questions

### What is a user in Linux?

A user is an account that allows a person or application to access and use the Linux operating system.

---

### What are the different types of users in Linux?

* Root user
* System user
* Regular (normal) user

---

### What is the UID of the root user?

The UID of the root user is **0**.

---

### Why is Linux called a multi-user operating system?

Because multiple users can log in and use the system independently while maintaining separate accounts, permissions, and resources.

---

### Which file stores user account information?

```text id="jlwmju"
/etc/passwd
```

---

### Which file stores encrypted passwords?

```text id="e1h6kg"
/etc/shadow
```

---

# Key Takeaways

* Linux is a multi-user operating system.
* Every user has a unique username and User ID (UID).
* There are three main user types: Root, System, and Regular users.
* User accounts help secure the system by controlling access to resources.
* User information is stored in `/etc/passwd`, while encrypted passwords are stored in `/etc/shadow`.
