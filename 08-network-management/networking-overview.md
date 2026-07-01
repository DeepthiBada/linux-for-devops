# Networking Overview

## Overview

A **computer network** is a collection of devices connected together to exchange data and communicate with each other.

These devices may include:

* Computers
* Servers
* Mobile devices
* Routers
* Switches
* Printers
* Cloud resources

Networking enables applications and users to communicate over local networks and the Internet.

---

# Why Do We Need Networking?

Networking allows devices to:

* Share files
* Access websites
* Communicate with servers
* Transfer data
* Connect to cloud services
* Access remote systems using SSH
* Use applications such as email, messaging, and video conferencing

Without networking, computers would operate independently without being able to exchange information.

---

# How Two Computers Communicate

Example:

```text
Laptop
(IP: 192.168.1.10)
        │
        ▼
Home Router / Switch
        │
        ▼
Internet
        │
        ▼
Web Server
(IP: 142.250.183.78)
```

When you open a website:

1. Your computer sends a request.
2. The request travels through the network.
3. The destination server receives the request.
4. The server processes it.
5. The server sends a response back to your computer.

---

# Basic Networking Components

| Component | Purpose                                                             |
| --------- | ------------------------------------------------------------------- |
| Computer  | Sends and receives data                                             |
| Router    | Connects different networks and forwards traffic                    |
| Switch    | Connects devices within the same local network (LAN)                |
| Modem     | Connects your local network to your Internet Service Provider (ISP) |
| Server    | Provides services such as websites, databases, or APIs              |
| Client    | Requests services from a server                                     |

---

# What is an IP Address?

An **IP (Internet Protocol) Address** is a unique identifier assigned to a device on a network.

It allows devices to locate and communicate with one another.

Example:

```text
192.168.1.100
```

Think of an IP address like a **house address**—it tells the network where to deliver data.

---

# Public IP vs Private IP

| Public IP                                      | Private IP                                  |
| ---------------------------------------------- | ------------------------------------------- |
| Accessible over the Internet                   | Used only within a local network            |
| Assigned by an Internet Service Provider (ISP) | Assigned by a router or local administrator |
| Globally unique                                | Can be reused in different private networks |

Examples:

Private IPs:

```text
192.168.1.10
10.0.0.25
172.16.5.8
```

Public IP:

```text
34.125.89.10
```

---

# IPv4 vs IPv6

## IPv4

Most commonly used addressing format.

Example:

```text
192.168.1.100
```

* 32-bit address
* Approximately 4.3 billion unique addresses

---

## IPv6

Introduced to overcome IPv4 address limitations.

Example:

```text
2001:db8::8a2e:370:7334
```

* 128-bit address
* Vastly larger address space

---

# What is a MAC Address?

A **MAC (Media Access Control) Address** is a unique hardware identifier assigned to a network interface.

Example:

```text
00:1A:2B:3C:4D:5E
```

Unlike an IP address, a MAC address identifies the network interface itself.

---

# What is a Hostname?

A **hostname** is a human-readable name assigned to a computer or server.

Example:

```text
web-server-01
db-server
jenkins-master
```

Hostnames are easier to remember than IP addresses.

---

# What is DNS?

**DNS (Domain Name System)** translates human-friendly domain names into IP addresses.

Example:

```text
google.com
        │
        ▼
142.250.183.78
```

Without DNS, users would need to remember IP addresses instead of domain names.

---

# What is a Port?

A **port** identifies a specific service or application running on a device.

A single server can run multiple services simultaneously, each listening on a different port.

Examples:

| Service    | Port |
| ---------- | ---: |
| SSH        |   22 |
| HTTP       |   80 |
| HTTPS      |  443 |
| MySQL      | 3306 |
| PostgreSQL | 5432 |
| Jenkins    | 8080 |

Think of an IP address as a building address and a port as the apartment number.

---

# What is a Protocol?

A **protocol** is a set of rules that define how devices communicate over a network.

Common protocols include:

* HTTP
* HTTPS
* SSH
* FTP
* SMTP
* DNS

---

# TCP vs UDP

| TCP                               | UDP                                         |
| --------------------------------- | ------------------------------------------- |
| Connection-oriented               | Connectionless                              |
| Reliable                          | Faster but less reliable                    |
| Guarantees delivery               | Does not guarantee delivery                 |
| Used for web browsing, SSH, email | Used for video streaming, VoIP, DNS queries |

---

# How a Website Opens

```text
User
  │
  ▼
Browser
  │
  ▼
DNS
(Find Server IP)
  │
  ▼
Internet
  │
  ▼
Web Server
  │
  ▼
Response
  │
  ▼
Browser Displays the Webpage
```

---

# Common Networking Commands

| Command    | Purpose                                 |
| ---------- | --------------------------------------- |
| `ip`       | Display network interface information   |
| `ping`     | Test network connectivity               |
| `ssh`      | Connect to a remote server              |
| `curl`     | Send HTTP requests                      |
| `wget`     | Download files                          |
| `ss`       | Display listening ports and connections |
| `nslookup` | Query DNS records                       |
| `dig`      | Perform detailed DNS lookups            |
| `hostname` | Display or set the system hostname      |

---

# Real-World DevOps Use Cases

* SSH into an AWS EC2 instance.
* Verify server connectivity using `ping`.
* Test REST APIs with `curl`.
* Check whether an application is listening on the correct port.
* Troubleshoot DNS resolution issues.
* Verify network configuration after deploying infrastructure.

---

# Best Practices

* Use meaningful hostnames for servers.
* Prefer HTTPS over HTTP for secure communication.
* Restrict access to unnecessary ports using firewalls or security groups.
* Verify DNS configuration before troubleshooting applications.
* Understand the difference between IP addresses, ports, and protocols.

---

# Interview Questions

### What is a network?

A network is a group of connected devices that communicate and exchange data.

---

### What is an IP address?

An IP address is a unique identifier assigned to a device so it can communicate on a network.

---

### What is the difference between a public IP and a private IP?

* A **public IP** is reachable over the Internet.
* A **private IP** is used within a local network.

---

### What is DNS?

DNS (Domain Name System) translates domain names into IP addresses.

---

### What is a port?

A port identifies a specific service or application running on a device.

---

### What is the difference between TCP and UDP?

* **TCP** is reliable and guarantees data delivery.
* **UDP** is faster but does not guarantee delivery.

---

### Why is networking important in DevOps?

Networking enables communication between applications, servers, containers, cloud resources, and services. It is essential for deploying, managing, and troubleshooting modern infrastructure.

---

# Key Takeaways

* Networking allows devices to communicate and exchange data.
* Every device on a network is identified by an IP address.
* DNS translates domain names into IP addresses.
* Ports identify individual services running on a device.
* Protocols define how devices communicate.
* TCP provides reliable communication, while UDP prioritizes speed.
* Strong networking fundamentals are essential for Linux administration, cloud computing, and DevOps.
