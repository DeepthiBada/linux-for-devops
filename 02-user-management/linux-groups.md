# Linux Groups

## Overview

A **group** is a collection of users that share the same access permissions to files, directories, and system resources.

Instead of assigning permissions to individual users one by one, Linux allows administrators to assign permissions to a group. Any user who belongs to that group automatically inherits those permissions.

---

# Why Do We Need Groups?

Groups make user management easier and improve security.

Benefits of using groups:

* Simplify permission management
* Share files among multiple users
* Reduce administrative effort
* Improve system security
* Organize users based on roles

### Example

Suppose a company has a Development team with 20 developers.

Instead of assigning file permissions to each developer individually, create a group called **developers** and add all developers to that group.

Now, any file owned by the **developers** group can be accessed by all members of the group.

---

# Types of Groups

Linux supports two types of groups.

## 1. Primary Group

Every user has one **primary group**.

* Assigned when the user is created.
* Used as the default group for files created by the user.

Example:

```text id="z9pk0n"
User: deepthi
Primary Group: deepthi
```

Any new file created by **deepthi** will belong to the **deepthi** group by default.

---

## 2. Secondary (Supplementary) Groups

A user can belong to multiple secondary groups.

These groups provide additional permissions.

Example:

```text id="d1qx7m"
User: deepthi

Primary Group:
deepthi

Secondary Groups:
developers
docker
sudo
```

This allows the user to access resources assigned to those groups.

---

# Group Information

Each group has:

* Group Name
* Group ID (GID)
* Members

Example:

| Group Name | GID  | Members       |
| ---------- | ---- | ------------- |
| developers | 1001 | deepthi, john |
| docker     | 999  | deepthi       |
| sudo       | 27   | deepthi       |

---

# Group Information File

Linux stores group information in:

```text id="s7me1u"
/etc/group
```

Example entry:

```text id="5mkjcs"
developers:x:1001:deepthi,john
```

Explanation:

| Field        | Meaning              |
| ------------ | -------------------- |
| developers   | Group name           |
| x            | Password placeholder |
| 1001         | Group ID (GID)       |
| deepthi,john | Members of the group |

---

# View Group Information

### Display Current User's Groups

```bash id="cn1l2v"
groups
```

Example Output

```text id="ysdrtb"
deepthi sudo docker developers
```

---

### Display User and Group Information

```bash id="y5m4dn"
id
```

Example Output

```text id="f3w1bq"
uid=1000(deepthi)
gid=1000(deepthi)
groups=1000(deepthi),27(sudo),999(docker)
```

---

# Real-World DevOps Use Cases

* Add developers to a **developers** group to share project files.
* Add administrators to the **sudo** group to grant administrative privileges.
* Add users to the **docker** group so they can run Docker commands without switching to the root user.
* Control access to shared application directories through group ownership.

---

# Interview Questions

### What is a group in Linux?

A group is a collection of users who share the same permissions to files, directories, or system resources.

---

### Why are groups used?

Groups simplify permission management by allowing administrators to assign permissions to multiple users at once.

---

### What is the difference between a primary group and a secondary group?

* **Primary Group:** Default group assigned to a user. New files created by the user belong to this group.
* **Secondary Group:** Additional groups that provide extra permissions.

---

### Which file stores group information?

```text id="0tntqq"
/etc/group
```

---

### Can a user belong to multiple groups?

Yes. A user can have one primary group and multiple secondary (supplementary) groups.

---

# Key Takeaways

* A group is a collection of users with shared permissions.
* Every user has one primary group.
* A user can belong to multiple secondary groups.
* Group information is stored in `/etc/group`.
* Groups simplify permission management and improve system security.
* Groups are widely used in Linux administration and DevOps environments.
