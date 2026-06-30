# User Management Commands

## Overview

Linux provides several commands to create, modify, delete, and manage user accounts. These commands help administrators securely manage system access and permissions.

---

# Common User Management Commands

| Command   | Description                                                                 |
| --------- | --------------------------------------------------------------------------- |
| `whoami`  | Displays the current logged-in user.                                        |
| `id`      | Displays user and group information.                                        |
| `who`     | Shows users currently logged into the system.                               |
| `users`   | Displays logged-in usernames.                                               |
| `useradd` | Creates a new user.                                                         |
| `adduser` | Interactive command to create a new user (available on many distributions). |
| `passwd`  | Creates or changes a user's password.                                       |
| `usermod` | Modifies an existing user account.                                          |
| `userdel` | Deletes a user account.                                                     |
| `su`      | Switches to another user.                                                   |
| `sudo`    | Executes a command with elevated privileges.                                |

---

# 1. whoami

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

# 2. id

### Description

Displays the user's UID, GID, and group memberships.

### Syntax

```bash
id
```

or

```bash
id <username>
```

### Example

```bash
id deepthi
```

Output

```text
uid=1000(deepthi)
gid=1000(deepthi)
groups=1000(deepthi),27(sudo)
```

---

# 3. who

### Description

Displays users currently logged into the system.

### Syntax

```bash
who
```

---

# 4. users

### Description

Displays the usernames of users currently logged in.

### Syntax

```bash
users
```

---

# 5. useradd

### Description

Creates a new user account.

### Syntax

```bash
useradd <username>
```

### Common Options

| Option | Description                       |
| ------ | --------------------------------- |
| `-m`   | Create the user's home directory. |
| `-s`   | Specify the login shell.          |
| `-u`   | Specify the User ID (UID).        |
| `-g`   | Specify the primary group.        |

### Examples

```bash
sudo useradd -m john
```

```bash
sudo useradd -m -s /bin/bash devops
```

---

# 6. adduser

### Description

Creates a new user interactively by prompting for additional information.

> **Note:** `adduser` is available on Debian-based distributions such as Ubuntu. On some distributions, only `useradd` is available.

### Syntax

```bash
sudo adduser john
```

---

# 7. passwd

### Description

Creates or changes a user's password.

### Syntax

```bash
passwd <username>
```

### Example

```bash
sudo passwd john
```

---

# 8. usermod

### Description

Modifies an existing user account.

### Common Options

| Option | Description                            |
| ------ | -------------------------------------- |
| `-aG`  | Add the user to a supplementary group. |
| `-l`   | Change the username.                   |
| `-d`   | Change the home directory.             |
| `-s`   | Change the login shell.                |

### Examples

Add a user to the Docker group:

```bash
sudo usermod -aG docker john
```

Change the login shell:

```bash
sudo usermod -s /bin/bash john
```

---

# 9. userdel

### Description

Deletes a user account.

### Syntax

```bash
userdel <username>
```

### Common Options

| Option | Description                                              |
| ------ | -------------------------------------------------------- |
| `-r`   | Delete the user's home directory along with the account. |

### Examples

Delete the user only:

```bash
sudo userdel john
```

Delete the user and home directory:

```bash
sudo userdel -r john
```

---

# 10. su

### Description

Switches to another user account.

### Syntax

```bash
su <username>
```

Switch to the root user:

```bash
su -
```

---

# 11. sudo

### Description

Executes a command with elevated (administrator) privileges.

### Syntax

```bash
sudo <command>
```

### Example

```bash
sudo apt update
```

---

# Real-World DevOps Use Cases

* Create user accounts for developers and administrators.
* Add users to the `docker` or `sudo` groups.
* Change user shells and home directories.
* Remove inactive user accounts.
* Use `sudo` instead of logging in directly as the root user.

---

# Interview Questions

### What is the difference between `useradd` and `adduser`?

* `useradd` is a low-level command that creates a user with minimal defaults.
* `adduser` is a user-friendly, interactive command available on many Debian-based systems.

---

### What is the purpose of `sudo`?

`sudo` allows a permitted user to execute commands with administrator (root) privileges.

---

### What does the `-m` option in `useradd` do?

It creates the user's home directory.

---

### What is the purpose of `usermod -aG`?

It adds an existing user to one or more supplementary groups without removing them from their current groups.

---

### Which command deletes a user and their home directory?

```bash
sudo userdel -r <username>
```

---

# Key Takeaways

* `useradd` and `adduser` are used to create user accounts.
* `passwd` sets or changes user passwords.
* `usermod` modifies existing user accounts.
* `userdel` removes user accounts.
* `su` switches between user accounts.
* `sudo` executes commands with elevated privileges.
* Proper user management is essential for Linux system administration and DevOps security.
