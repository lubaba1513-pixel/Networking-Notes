# 🌐 TCP/IP Model

> *"The OSI Model explains networking. TCP/IP is what the Internet actually uses."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Explain what the TCP/IP Model is.
- Understand why TCP/IP became the foundation of modern networking.
- Identify the four layers of the TCP/IP Model.
- Understand the main function of each layer.
- Compare the TCP/IP Model with the OSI Model.
- Understand when to use each model.
- Understand important similarities between TCP/IP and OSI.
- Understand how TCP/IP works in a real-world scenario.
- Differentiate between TCP and UDP.
- Understand how data moves through the TCP/IP layers.

---

# 🌍 Imagine This...

Imagine ordering a package online.

Different parts of the delivery system have different jobs:

- 🛒 **Application** = You place the order
- 📦 **Transport** = Makes sure the package is handled correctly
- 🗺️ **Internet** = Decides where the package should go
- 🛣️ **Network Access** = Physically moves the package

The **TCP/IP Model** works in a similar way.

It divides network communication into **four layers**, with each layer responsible for a different part of communication.

---

# 📖 What is TCP/IP?

**TCP/IP (Transmission Control Protocol / Internet Protocol)** is a suite of networking protocols used to communicate across networks, including the Internet.

The **TCP/IP Model** describes networking using **four layers**:

```text
┌──────────────────────────┐
│ 4. Application           │
├──────────────────────────┤
│ 3. Transport             │
├──────────────────────────┤
│ 2. Internet              │
├──────────────────────────┤
│ 1. Network Access        │
└──────────────────────────┘
```

Each layer has a specific role, and together they allow devices to communicate.

---

# ❓ Why Did TCP/IP Win?

You may wonder:

> If the OSI Model has 7 layers, why does the Internet mainly use TCP/IP?

TCP/IP became widely adopted because it was:

- 🌐 Practical for real-world networking
- 🔗 Designed for communication between different networks
- 🧩 Based on working protocols
- 📈 Easy to expand as networks grew
- 💻 Widely implemented on computers and network devices
- 🌍 Used as the foundation of the Internet

TCP/IP was developed and deployed before the OSI model became widely used as a reference model.

> 💡 **Simple idea:**  
> OSI became a great **reference and learning model**, while TCP/IP became the practical **protocol suite used to build the Internet**.

---

# 🧩 The 4 TCP/IP Layers

| Layer | Name | Main Function | Examples |
|------:|------|---------------|----------|
| **4** | Application | Provides network services to applications | HTTP, DNS, SSH, SMTP |
| **3** | Transport | End-to-end communication | TCP, UDP |
| **2** | Internet | IP addressing and routing | IPv4, IPv6, ICMP |
| **1** | Network Access | Local network communication and transmission | Ethernet, Wi-Fi, ARP |

> 💡 Some textbooks call the bottom layer **Network Interface**, **Link**, or **Network Access**. The idea is the same: it handles communication over the local network and physical medium.

---

# 4️⃣ Layer 4 — Application

The **Application Layer** provides network services that applications use to communicate.

It combines functions that are separated into **Application, Presentation, and Session** layers in the OSI Model.

### 🔑 Common Protocols

- HTTP / HTTPS
- DNS
- DHCP
- FTP
- SMTP
- SSH

### 🌍 Real-Life Example

When you open a website, your browser communicates with a web server using application-layer protocols such as **HTTP/HTTPS**.

```text
👤 User
   │
🌐 Browser
   │
   ▼
Application Layer
   │
HTTP / HTTPS
```

### 🧠 Remember

**Application = Network Services**

🛡️ **SOC Perspective:** SOC analysts often investigate DNS queries, HTTP/HTTPS traffic, email protocols, SSH activity, and suspicious application-level connections.

---

# 3️⃣ Layer 3 — Transport

The **Transport Layer** provides communication between applications running on different devices.

### 🔑 Main Functions

- End-to-end communication
- Segmentation
- Reassembly
- Reliability when using TCP
- Flow control
- Port numbers

### 🔑 Main Protocols

| Protocol | Main Idea |
|----------|-----------|
| **TCP** | Reliable, connection-oriented |
| **UDP** | Connectionless, low overhead |

### 🔢 Ports

Ports help identify the application or service involved in network communication.

Examples:

| Port | Common Service |
|------|----------------|
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |

### 📦 Data Units

- TCP → **Segment**
- UDP → **Datagram**

### 🧠 Remember

**Transport = TCP/UDP + Ports**

🛡️ **SOC Perspective:** Transport-layer information is useful for detecting port scans, suspicious connections, unusual ports, and some forms of malicious traffic.

---

# 2️⃣ Layer 2 — Internet

The **Internet Layer** is responsible for logical addressing and moving packets between networks.

### 🔑 Main Functions

- IP addressing
- Routing
- Packet forwarding

### 🔑 Examples

- IPv4
- IPv6
- ICMP

### 📦 Data Unit

**Packet**

### 🛠️ Common Devices

- Router
- Layer 3 Switch
- Layer 3 Firewall

### 🌍 Real-Life Example

A router examines destination IP information and forwards a packet toward its destination.

```text
💻
 │
 ▼
🌐 Router
 │
 ▼
🌐 Router
 │
 ▼
🖥️ Destination
```

### 🧠 Remember

**Internet = IP + Routing**

🛡️ **SOC Perspective:** IP addresses are important when investigating suspicious sources, destinations, scanning activity, and attack paths.

---

# 1️⃣ Layer 1 — Network Access

The **Network Access Layer** handles communication over the local network and the physical medium.

It combines functions associated with the **Data Link and Physical layers** of the OSI Model.

### 🔑 Main Functions

- Local network communication
- Frames
- MAC addressing
- Physical transmission
- Access to the network medium

### 🔑 Examples

- Ethernet
- Wi-Fi
- ARP

### 📦 Data Units

- **Frame**
- **Bits**

### 🛠️ Common Devices

- Switch
- Network Interface Card (NIC)
- Hub
- Repeater

### 🌍 Real-Life Example

Your laptop uses Wi-Fi or Ethernet to send data to the local network.

```text
💻 Laptop
    │
    │ Wi-Fi / Ethernet
    ▼
🔀 Switch / 📡 Access Point
```

### 🧠 Remember

**Network Access = Local Network + Transmission**

🛡️ **SOC Perspective:** Understanding the local network helps analysts investigate MAC addresses, ARP activity, rogue devices, and suspicious local traffic.

---

# 🔄 TCP/IP Model in Action

Imagine opening a website.

Your data moves down the TCP/IP layers before being transmitted.

```text
              SENDER
                │
                ▼
        4 ─ Application
        │   HTTP / HTTPS
        ▼
        3 ─ Transport
        │   TCP + Port 443
        ▼
        2 ─ Internet
        │   IP Address
        ▼
        1 ─ Network Access
        │   Wi-Fi / Ethernet
        ▼
             NETWORK
                │
                ▼
             RECEIVER
```

At the receiving device, the process happens in reverse.

```text
Network Access
      ↓
Internet
      ↓
Transport
      ↓
Application
```

---

# 📦 Encapsulation in TCP/IP

As data moves down the TCP/IP layers, each layer adds information needed for delivery.

```text
Application
     ↓
   DATA
     ↓
Transport
     ↓
SEGMENT / DATAGRAM
     ↓
Internet
     ↓
PACKET
     ↓
Network Access
     ↓
FRAME
     ↓
BITS
```

At the destination, the process is reversed.

This is called **decapsulation**.

### 🧠 Remember

**Data → Segment → Packet → Frame → Bits**

---

# 🔀 TCP/IP vs OSI

The two models are closely related, but they are not identical.

| OSI Model | TCP/IP Model |
|-----------|--------------|
| 7 layers | 4 layers |
| Reference model | Practical protocol model/suite |
| Application, Presentation, Session are separate | Combined into Application |
| Transport is separate | Transport is separate |
| Network is separate | Internet is separate |
| Data Link + Physical are separate | Combined into Network Access |

### 🔄 Layer Mapping

```text
OSI MODEL                 TCP/IP MODEL

7 ─ Application ─────┐
6 ─ Presentation ────┼──► 4 ─ Application
5 ─ Session ─────────┘

4 ─ Transport ─────────► 3 ─ Transport

3 ─ Network ───────────► 2 ─ Internet

2 ─ Data Link ───────┐
1 ─ Physical ─────────┴──► 1 ─ Network Access
```

> 💡 The mapping is approximate because the models organize networking concepts differently.

---

# ❓ When Should You Use Which Model?

## 📚 Use the OSI Model When...

- Learning networking concepts
- Studying for networking exams
- Troubleshooting by layer
- Explaining where a problem occurs
- Understanding how different networking functions relate to each other

## 🌐 Use TCP/IP When...

- Working with real-world networks
- Configuring network services
- Understanding Internet protocols
- Working with IP addresses, TCP, UDP, DNS, HTTP, etc.
- Analyzing actual network traffic

### 🧠 Easy Rule

> **OSI = Understand & Troubleshoot**  
> **TCP/IP = Build & Communicate**

---

# 🤝 Important Similarities

Both models:

- 🌐 Explain network communication.
- 🧩 Divide networking into layers.
- 🔄 Describe how data moves between devices.
- 📦 Help organize networking concepts.
- 🛠️ Help with troubleshooting.
- 🛡️ Help security professionals understand network traffic.

The main difference is **how they organize these functions**.

---

# ⚔️ TCP vs UDP

TCP and UDP are both **Transport Layer protocols**, but they work differently.

| Feature | TCP | UDP |
|---------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable delivery | No delivery guarantee |
| Ordering | Maintains order | No ordering guarantee |
| Retransmission | Yes | No |
| Speed / Overhead | More overhead | Lower overhead |
| Common Uses | Web, SSH, email | DNS, streaming, VoIP, gaming |

### 🧠 Simple Analogy

Imagine sending five messages to a friend.

**TCP** is like sending them with confirmation:

```text
📤 1 → 📥 Received
📤 2 → 📥 Received
📤 3 → ❌ Lost
       ↳ 🔄 Resend
📤 4 → 📥 Received
📤 5 → 📥 Received
```

**UDP** sends them without waiting for confirmation:

```text
📤 1 → 📥
📤 2 → 📥
📤 3 → ❌
📤 4 → 📥
📤 5 → 📥
```

> 💡 TCP is useful when accurate, ordered delivery matters. UDP is useful when low overhead and speed are more important than guaranteed delivery.

---

# 🌍 Real-Life Scenario — Watching a Video

Imagine watching an online video.

```text
💻 Your Device
     │
     ▼
4️⃣ Application
   Video Service
     │
     ▼
3️⃣ Transport
   TCP / UDP
     │
     ▼
2️⃣ Internet
   IP Routing
     │
     ▼
1️⃣ Network Access
   Wi-Fi / Ethernet
     │
     ▼
🌐 Internet
     │
     ▼
🖥️ Server
```

Every layer performs a different job to move the data from the server to your device.

---

# 🛡️ Why SOC Analysts Should Learn TCP/IP

TCP/IP is extremely important for SOC analysts because real network traffic is built around TCP/IP protocols.

Understanding it helps analysts:

- 🔍 Analyze packets and network traffic
- 🌐 Investigate IP addresses
- 🔢 Analyze ports
- 🚨 Detect suspicious connections
- 🧩 Understand protocols
- 🛠️ Troubleshoot network problems
- 🛡️ Investigate network-based attacks

### Example SOC Alert

```text
Source IP:        192.168.1.50
Destination IP:   10.0.0.20
Protocol:         TCP
Destination Port: 443
```

An analyst can understand:

```text
Internet Layer  → Source & Destination IP
Transport Layer → TCP + Port 443
Application     → HTTPS traffic
```

---

# ⚡ Quick Revision

| TCP/IP Layer | Main Idea | Examples |
|--------------|-----------|----------|
| **4 — Application** | Network Services | HTTP, DNS, SSH |
| **3 — Transport** | End-to-End Communication | TCP, UDP |
| **2 — Internet** | IP + Routing | IPv4, IPv6, ICMP |
| **1 — Network Access** | Local Network + Transmission | Ethernet, Wi-Fi |

---

# 🧠 Remember Like This

### TCP/IP Layers — Top to Bottom

**A T I N**

> **Application → Transport → Internet → Network Access**

```text
4 — Application
3 — Transport
2 — Internet
1 — Network Access
```

### ⭐ Data Unit Chain

```text
DATA
  ↓
SEGMENT / DATAGRAM
  ↓
PACKET
  ↓
FRAME
  ↓
BITS
```

### ⭐ OSI vs TCP/IP

```text
OSI                         TCP/IP

Application ───────┐
Presentation ──────┼──────► Application
Session ───────────┘

Transport ─────────────────► Transport

Network ───────────────────► Internet

Data Link ────────┐
Physical ─────────┴───────► Network Access
```

> 🧠 **OSI = 7 layers for understanding**  
> **TCP/IP = 4 layers used in practical networking**

---

# 📚 What's Next?

Excellent work! 🎉 You now understand the **TCP/IP Model**, its four layers, how it compares with OSI, and the difference between TCP and UDP.

> **Remember:** OSI helps you understand networking as a layered concept, while TCP/IP represents the protocol architecture that forms the foundation of modern Internet communication.

➡️ **Next Chapter:** 🔌 Network Protocols
