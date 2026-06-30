# Group Management Commands

## Overview

Linux provides several commands to create, modify, view, and delete groups. Groups simplify permission management by allowing administrators to assign permissions to multiple users at once.

---

# Common Group Management Commands

| Command    | Description                                        |
| ---------- | -------------------------------------------------- |
| `groups`   | Displays the groups a user belongs to.             |
| `groupadd` | Creates a new group.                               |
| `groupmod` | Modifies an existing group.                        |
| `groupdel` | Deletes a group.                                   |
| `gpasswd`  | Manages group members and passwords.               |
| `newgrp`   | Changes the current primary group for the session. |

---

# 1. groups

## Description

Displays the groups that a user belongs to.

### Syntax

```bash id="u5f9a1"
groups
```

or

```bash id="7vpk02"
groups <username>
```

### Example

```bash id="0gwg67"
groups deepthi
```

Example Output

```text id="9sv5xw"
deepthi : deepthi sudo docker developers
```

---

# 2. groupadd

## Description

Creates a new group.

### Syntax

```bash id="4xy0rm"
groupadd <group_name>
```

### Common Options

| Option | Description                 |
| ------ | --------------------------- |
| `-g`   | Specify the Group ID (GID). |

### Examples

Create a group:

```bash id="bdmfdl"
sudo groupadd developers
```

Create a group with a specific GID:

```bash id="chv6z7"
sudo groupadd -g 1050 developers
```

---

# 3. groupmod

## Description

Modifies an existing group.

### Common Options

| Option | Description                |
| ------ | -------------------------- |
| `-n`   | Rename the group.          |
| `-g`   | Change the Group ID (GID). |

### Examples

Rename a group:

```bash id="h7v0vh"
sudo groupmod -n devops developers
```

Change the Group ID:

```bash id="xdlmzc"
sudo groupmod -g 1100 devops
```

---

# 4. groupdel

## Description

Deletes an existing group.

### Syntax

```bash id="tlnq8g"
groupdel <group_name>
```

### Example

```bash id="3huw6x"
sudo groupdel developers
```

> **Note:** A group cannot be deleted if it is the primary group of an existing user.

---

# 5. gpasswd

## Description

Manages group membership and group passwords.

### Common Options

| Option | Description                 |
| ------ | --------------------------- |
| `-a`   | Add a user to a group.      |
| `-d`   | Remove a user from a group. |

### Examples

Add a user to a group:

```bash id="c4jey8"
sudo gpasswd -a john developers
```

Remove a user from a group:

```bash id="d7ykmd"
sudo gpasswd -d john developers
```

---

# 6. newgrp

## Description

Temporarily changes the current primary group for the active session.

### Syntax

```bash id="mx0l3t"
newgrp <group_name>
```

### Example

```bash id="p5w5up"
newgrp developers
```

This starts a new shell with the specified group as the current primary group.

---

# Useful Files

Linux stores group information in:

```text id="vjlwm1"
/etc/group
```

Example:

```text id="jlwmd2"
developers:x:1001:john,deepthi
```

---

# Real-World DevOps Use Cases

* Create a **developers** group to share project files.
* Add users to the **docker** group so they can run Docker commands without using `sudo`.
* Add administrators to the **sudo** group for elevated privileges.
* Organize users into application-specific groups for controlled access.

---

# Interview Questions

### Which command creates a new group?

```bash id="jlwmh3"
groupadd
```

---

### Which command displays the groups a user belongs to?

```bash id="jlwmk4"
groups
```

---

### Which command renames a group?

```bash id="jlwmn5"
groupmod -n
```

---

### Which command deletes a group?

```bash id="jlwmp6"
groupdel
```

---

### Which command adds a user to a group?

Using `gpasswd`:

```bash id="jlwmq7"
sudo gpasswd -a john developers
```

Or using `usermod`:

```bash id="jlwmr8"
sudo usermod -aG developers john
```

> **Note:** In practice, `usermod -aG` is more commonly used to add users to supplementary groups.

---

### What is the purpose of the `newgrp` command?

`newgrp` starts a new shell with a different primary group for the current session.

---

# Key Takeaways

* `groupadd` creates a new group.
* `groupmod` modifies an existing group.
* `groupdel` deletes a group.
* `groups` displays group membership.
* `gpasswd` manages users within groups.
* `newgrp` changes the current primary group for a session.
* Group management simplifies permission administration and improves security in Linux systems.
