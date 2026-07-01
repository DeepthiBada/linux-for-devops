# TCP vs UDP

## Overview

**TCP (Transmission Control Protocol)** and **UDP (User Datagram Protocol)** are transport layer protocols in the **TCP/IP networking model**.

They define **how data is transmitted between devices** over a network.

Although both are used to send data, they are designed for different purposes:

* **TCP** focuses on **reliability and accuracy**.
* **UDP** focuses on **speed and low latency**.

---

# Why Do We Need TCP and UDP?

Different applications have different networking requirements.

For example:

* Online banking requires reliable data delivery.
* A live video stream prioritizes speed over perfect accuracy.

Instead of using one protocol for every situation, networking provides:

* **TCP** for reliable communication.
* **UDP** for fast communication.

---

# What is TCP?

**TCP (Transmission Control Protocol)** is a **connection-oriented** protocol.

Before transmitting data, TCP establishes a connection between the sender and receiver.

It guarantees:

* Reliable delivery
* Correct packet order
* Error checking
* Retransmission of lost packets

---

# How TCP Works

```text
Client
   │
   │  SYN
   ▼
Server
   ▲
   │ SYN + ACK
   │
Client
   │
   │ ACK
   ▼
Connection Established
```

This process is called the **TCP Three-Way Handshake**.

After the connection is established, data transfer begins.

---

# Features of TCP

* Connection-oriented
* Reliable communication
* Error detection
* Packet retransmission
* Ordered delivery
* Flow control
* Congestion control

---

# Common TCP Applications

| Application | Port |
| ----------- | ---: |
| HTTP        |   80 |
| HTTPS       |  443 |
| SSH         |   22 |
| FTP         |   21 |
| SMTP        |   25 |
| MySQL       | 3306 |
| PostgreSQL  | 5432 |

---

# What is UDP?

**UDP (User Datagram Protocol)** is a **connectionless** protocol.

It sends data directly without establishing a connection.

UDP does **not** guarantee:

* Delivery
* Packet order
* Retransmission

Because of this, UDP is much faster than TCP.

---

# How UDP Works

```text
Client
   │
   ▼
Data Packet
   │
   ▼
Server
```

There is no handshake before sending data.

---

# Features of UDP

* Connectionless
* Fast transmission
* Low latency
* No retransmission
* No guaranteed delivery
* No packet ordering
* Lower overhead

---

# Common UDP Applications

| Application     |    Port |
| --------------- | ------: |
| DNS             |      53 |
| DHCP            | 67 / 68 |
| NTP             |     123 |
| VoIP            |  Varies |
| Video Streaming |  Varies |
| Online Gaming   |  Varies |

---

# TCP Three-Way Handshake

Before data transfer, TCP establishes a connection.

### Step 1

Client sends:

```text
SYN
```

### Step 2

Server replies:

```text
SYN + ACK
```

### Step 3

Client sends:

```text
ACK
```

Now both devices are ready to exchange data.

---

# TCP Connection Termination

TCP closes a connection using a **Four-Way Handshake**.

```text
Client
   │
   │ FIN
   ▼
Server
   ▲
   │ ACK
   │
Server
   │ FIN
   ▼
Client
   ▲
   │ ACK
```

This ensures that both sides finish transmitting data before the connection is closed.

---

# TCP vs UDP

| Feature         | TCP                    | UDP                     |
| --------------- | ---------------------- | ----------------------- |
| Connection      | Connection-oriented    | Connectionless          |
| Reliability     | Guaranteed             | Not guaranteed          |
| Packet Ordering | Guaranteed             | Not guaranteed          |
| Speed           | Slower                 | Faster                  |
| Error Recovery  | Yes                    | No                      |
| Handshake       | Yes                    | No                      |
| Overhead        | Higher                 | Lower                   |
| Best For        | Reliable communication | Real-time communication |

---

# Real-World Examples

### TCP Example

Downloading a file:

```text
Client
   │
Download PDF
   │
   ▼
Server
```

Every byte must arrive correctly.

Missing packets are retransmitted automatically.

---

### UDP Example

Video call:

```text
Client
   │
Voice & Video
   │
   ▼
Server
```

If one packet is lost, the conversation continues.

A small glitch is preferable to waiting for retransmissions.

---

# Which Protocol Should You Choose?

Use **TCP** when:

* Data accuracy is important.
* Every packet must arrive.
* Applications cannot tolerate missing data.

Examples:

* Banking applications
* File transfers
* Email
* SSH
* Database connections

---

Use **UDP** when:

* Speed is more important than perfect reliability.
* Low latency is required.
* Small packet loss is acceptable.

Examples:

* Live streaming
* Voice calls
* Online gaming
* DNS lookups

---

# Real-World DevOps Use Cases

* SSH uses **TCP** because remote administration requires reliable communication.
* Web applications use **HTTP/HTTPS over TCP**.
* Kubernetes API communication uses **TCP**.
* DNS queries typically use **UDP** for fast name resolution (with TCP used in specific cases such as large responses or zone transfers).
* Video conferencing applications often use **UDP** to minimize latency.

---

# Best Practices

* Choose TCP when reliability is critical.
* Choose UDP when low latency is more important than guaranteed delivery.
* Understand the transport protocol used by the applications you manage.
* Remember that many production systems use both protocols depending on the service.

---

# Interview Questions

### What is TCP?

TCP (Transmission Control Protocol) is a connection-oriented transport protocol that provides reliable and ordered data delivery.

---

### What is UDP?

UDP (User Datagram Protocol) is a connectionless transport protocol that prioritizes speed over guaranteed delivery.

---

### Which protocol uses the Three-Way Handshake?

```text
TCP
```

---

### Which protocol is faster?

```text
UDP
```

---

### Which protocol guarantees packet delivery?

```text
TCP
```

---

### Which protocol is used by SSH?

```text
TCP
```

---

### Which protocol is commonly used for DNS queries?

```text
UDP
```

---

### Why is UDP preferred for video streaming?

Because it minimizes latency. Occasional packet loss is generally less disruptive than waiting for retransmissions.

---

# Key Takeaways

* TCP and UDP are transport layer protocols.
* TCP is connection-oriented, reliable, and guarantees ordered delivery.
* UDP is connectionless, faster, and optimized for low-latency communication.
* TCP uses a Three-Way Handshake to establish a connection.
* UDP sends data without establishing a connection.
* Choose the protocol based on the application's requirements for reliability versus speed.
