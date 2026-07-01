# Disk Partitions

## Overview

A **partition** is a logical section of a physical disk.

Partitioning divides a single storage device into multiple independent sections, allowing each partition to have its own filesystem and purpose.

For example, a single 500 GB disk can be divided into separate partitions for the operating system, user data, backups, or swap space.

---

# Why Do We Need Partitions?

Partitions help administrators to:

* Organize data efficiently.
* Separate the operating system from user data.
* Improve data management.
* Install multiple operating systems on the same disk.
* Simplify backups and recovery.
* Allocate storage for different applications.

---

# How Partitioning Works

Example:

```text id="pt01"
Physical Disk (500 GB)
│
├── Partition 1 (100 GB)
│      Operating System
│
├── Partition 2 (250 GB)
│      User Data
│
└── Partition 3 (150 GB)
       Backups
```

Each partition behaves like an independent storage device.

---

# Partition Naming in Linux

Linux identifies partitions under the `/dev` directory.

Example (SATA/SCSI disks):

```text id="pt02"
/dev/sda      → Physical Disk
/dev/sda1     → Partition 1
/dev/sda2     → Partition 2
/dev/sda3     → Partition 3
```

Example (NVMe SSD):

```text id="pt03"
/dev/nvme0n1      → Physical Disk
/dev/nvme0n1p1    → Partition 1
/dev/nvme0n1p2    → Partition 2
```

---

# Types of Partitions

Traditional MBR-partitioned disks support three partition types.

## 1. Primary Partition

A **primary partition** is a standard partition that can store data or an operating system.

Characteristics:

* Can contain a filesystem.
* Can be bootable.
* MBR supports up to **4 primary partitions**.

---

## 2. Extended Partition

An **extended partition** is a special partition that acts as a container for logical partitions.

Characteristics:

* Only one extended partition is allowed on an MBR disk.
* It cannot directly store files.
* It exists only to hold logical partitions.

---

## 3. Logical Partition

Logical partitions are created inside an extended partition.

Characteristics:

* Used when more than four partitions are needed on an MBR disk.
* Behave like normal partitions.
* Can store files and filesystems.

---

# Primary vs Extended vs Logical

```text id="pt04"
MBR Disk

├── Primary Partition
├── Primary Partition
├── Primary Partition
└── Extended Partition
      │
      ├── Logical Partition
      ├── Logical Partition
      └── Logical Partition
```

---

# MBR (Master Boot Record)

## Overview

MBR is the older partitioning scheme used by many legacy systems.

### Characteristics

* Supports disks up to **2 TB**
* Maximum **4 primary partitions**
* Widely supported by older BIOS systems

---

# GPT (GUID Partition Table)

## Overview

GPT is the modern partitioning scheme used by most current systems.

### Characteristics

* Supports disks larger than **2 TB**
* Supports up to **128 partitions** by default on many Linux systems
* Used with **UEFI** firmware
* Includes redundant partition table information for improved reliability

---

# MBR vs GPT

| Feature            | MBR                    | GPT                                 |
| ------------------ | ---------------------- | ----------------------------------- |
| Maximum Disk Size  | 2 TB                   | Greater than 2 TB                   |
| Maximum Partitions | 4 Primary              | Typically 128                       |
| Firmware           | BIOS                   | UEFI                                |
| Reliability        | Single partition table | Primary and backup partition tables |

---

# Partition Workflow

Before a disk can be used, it typically goes through the following steps:

```text id="pt05"
Disk
 │
 ▼
Partition
 │
 ▼
Create Filesystem
 │
 ▼
Mount
 │
 ▼
Store Files
```

---

# Display Disk Partitions

Display block devices:

```bash id="pt06"
lsblk
```

Display partition information:

```bash id="pt07"
sudo fdisk -l
```

Display filesystem information:

```bash id="pt08"
df -Th
```

---

# Real-World DevOps Use Cases

* Partition a new disk attached to an AWS EC2 instance.
* Create separate partitions for application data and logs.
* Inspect storage layout before expanding a volume.
* Verify partition information during server provisioning.
* Prepare disks before formatting and mounting.

---

# Best Practices

* Use **GPT** for modern systems and large disks.
* Separate operating system files from application or user data when practical.
* Verify partition layouts before modifying disks.
* Back up important data before repartitioning.
* Leave sufficient free space for future growth.

---

# Interview Questions

### What is a partition?

A partition is a logical division of a physical disk that can be formatted with its own filesystem.

---

### Why do we partition disks?

Partitioning helps organize data, separate workloads, simplify backups, and support multiple operating systems.

---

### What is the difference between a physical disk and a partition?

* A **physical disk** is the actual storage device.
* A **partition** is a logical section of that storage device.

---

### What is the difference between MBR and GPT?

| MBR                          | GPT                                     |
| ---------------------------- | --------------------------------------- |
| Supports disks up to 2 TB    | Supports disks larger than 2 TB         |
| Maximum 4 primary partitions | Typically supports up to 128 partitions |
| Used with BIOS               | Used with UEFI                          |

---

### Which partitioning scheme is recommended for modern Linux servers?

```text id="pt09"
GPT
```

---

### Which command displays disk partitions?

```bash id="pt10"
lsblk
```

or

```bash id="pt11"
sudo fdisk -l
```

---

# Key Takeaways

* A partition is a logical section of a physical disk.
* Each partition can have its own filesystem.
* MBR is the legacy partitioning scheme, while GPT is the modern standard.
* GPT supports larger disks, more partitions, and improved reliability.
* Partitions must typically be formatted and mounted before they can store files.
