# 📚 OSI Model

> *"Seven layers, one goal: moving data from one device to another."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Explain what the OSI Model is.
- Understand why the OSI Model was created.
- Identify all seven OSI layers.
- Understand the main function of each layer.
- Identify common protocols and network devices at different layers.
- Understand data units, encapsulation, and decapsulation.
- Understand how data travels from sender to receiver.
- Use the OSI Model for network troubleshooting.
- Explain why the OSI Model is important in cybersecurity.

---

# 🌍 Imagine This...

Imagine sending a package to your friend.

Different people handle different parts of the delivery — preparing the package, adding the address, transporting it, and finally delivering it.

Networking works the same way.

The **OSI Model** divides network communication into **7 layers**, and each layer has a specific job.

---

# 📖 What is the OSI Model?

**OSI (Open Systems Interconnection)** is a conceptual model that explains how devices communicate over a network.

It divides network communication into **seven layers**.

Each layer performs a different task and works with the layers above and below it.

---

# ❓ Why is the OSI Model Important?

The OSI Model helps us:

- 🌐 Understand network communication
- 🔧 Troubleshoot network problems
- 🧩 Understand networking protocols
- 📚 Learn networking more easily
- 🛡️ Investigate cybersecurity incidents

> 💡 The OSI Model is a **reference model**. Real-world protocols do not always fit perfectly into only one layer.

---

# 🧩 The 7 OSI Layers

| Layer | Name | Main Function | Examples | Common Devices |
|------:|------|---------------|----------|----------------|
| **7** | Application | Network services | HTTP, DNS, SSH | Proxy, WAF |
| **6** | Presentation | Format, encryption, compression | TLS, JPEG, ASCII | Usually none |
| **5** | Session | Manage communication sessions | RPC, NetBIOS, SIP | Usually none |
| **4** | Transport | End-to-end delivery & ports | TCP, UDP | Firewall, Load Balancer |
| **3** | Network | IP addressing & routing | IPv4, IPv6, ICMP | Router, L3 Switch |
| **2** | Data Link | MAC addressing & frames | Ethernet, Wi-Fi | Switch, Bridge, NIC |
| **1** | Physical | Signals, cables & bits | Ethernet cable, Fiber, Radio | Hub, Repeater |

---

# 7️⃣ Layer 7 — Application

The **Application Layer** provides network services that applications use to communicate.

It is the layer closest to the user.

### 🔑 Common Protocols

- HTTP / HTTPS
- DNS
- FTP
- SMTP
- SSH
- DHCP

### 🛠️ Common Devices

- Proxy Server
- Web Server
- WAF
- Application Gateway

### 🌍 Real-Life Example

When you open a website, your browser uses application-level protocols such as **HTTP/HTTPS** to communicate with the web server.

### 🧠 Remember

**Application = Network Services**

🛡️ **SOC Perspective:** SOC analysts investigate HTTP requests, DNS queries, suspicious URLs, SSH activity, and other application-level traffic.

---

# 6️⃣ Layer 6 — Presentation

The **Presentation Layer** prepares data so different systems can understand it.

### 🔑 Main Functions

- Data translation
- Encryption / decryption
- Compression / decompression

### 🔑 Examples

- TLS
- JPEG
- PNG
- ASCII
- Unicode

### 🌍 Real-Life Example

Think of a translator converting information from one language or format into another.

### 🧠 Remember

**Presentation = Format the Data**

🛡️ **SOC Perspective:** Useful when dealing with encrypted, encoded, or compressed data.

> 💡 In modern networking, these functions are often handled by applications and protocols rather than a separate Layer 6 component.

---

# 5️⃣ Layer 5 — Session

The **Session Layer** manages communication sessions between applications.

### 🔑 Main Functions

- Start a session
- Maintain a session
- Manage communication
- End a session

### 🔑 Examples

- RPC
- NetBIOS
- SIP

### 🌍 Real-Life Example

Think of a phone call:

**Start → Communicate → End**

### 🧠 Remember

**Session = Manage Communication**

🛡️ **SOC Perspective:** Understanding sessions helps analysts investigate unexpected connections and session-related attacks.

> 💡 Modern TCP/IP networking often combines Session Layer functions with other layers.

---

# 4️⃣ Layer 4 — Transport

The **Transport Layer** provides **end-to-end communication** between devices.

### 🔑 Main Functions

- Segmentation
- Reassembly
- Reliability
- Flow control
- Port numbers

### 🔑 Main Protocols

| Protocol | Main Idea |
|----------|-----------|
| **TCP** | Reliable, connection-oriented |
| **UDP** | Faster, connectionless |

### 📦 Data Unit

- TCP → **Segment**
- UDP → **Datagram**

### 🔢 Common Ports

| Port | Service |
|------|---------|
| 22 | SSH |
| 25 | SMTP |
| 53 | DNS |
| 80 | HTTP |
| 443 | HTTPS |

### 🧠 Remember

**Transport = TCP/UDP + Ports**

🛡️ **SOC Perspective:** Layer 4 is important for detecting port scans, suspicious connections, unusual ports, and malicious traffic.

---

# 3️⃣ Layer 3 — Network

The **Network Layer** handles communication between different networks.

### 🔑 Main Functions

- Logical addressing
- Routing
- Packet forwarding
- Path selection

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

A router uses IP addresses to decide where packets should go.

### 🧠 Remember

**Network = IP + Routing**

🛡️ **SOC Perspective:** IP addresses help analysts investigate suspicious sources, destinations, and attack paths.

---

# 2️⃣ Layer 2 — Data Link

The **Data Link Layer** handles communication between devices on the **same local network**.

### 🔑 Main Functions

- MAC addressing
- Framing
- Local delivery
- Error detection

### 🔑 Examples

- Ethernet
- Wi-Fi (802.11)
- PPP

### 📦 Data Unit

**Frame**

### 🏷️ MAC Address

A MAC address identifies a network interface on a local network.

```text
00:1A:2B:3C:4D:5E
```

### 🛠️ Common Devices

- Switch
- Bridge
- Network Interface Card (NIC)

### 🌍 Real-Life Example

A switch uses MAC addresses to forward frames to the appropriate device on the local network.

### 🧠 Remember

**Data Link = MAC + Frames**

🛡️ **SOC Perspective:** Useful for investigating MAC spoofing, ARP attacks, rogue devices, and local network activity.

---

# 1️⃣ Layer 1 — Physical

The **Physical Layer** is responsible for physically transmitting data.

### 🔑 Main Functions

- Electrical signals
- Light signals
- Radio signals
- Cables
- Connectors
- Bits

### 📦 Data Unit

**Bits**

```text
101101001011010
```

### 🛠️ Common Devices

- Hub
- Repeater
- Transceiver
- Cables
- Connectors

### 🌍 Real-Life Example

Bits are transmitted as electrical, light, or radio signals.

### 🧠 Remember

**Physical = Signals + Bits**

🛡️ **SOC Perspective:** Helps understand link failures, physical connectivity problems, and unauthorized physical connections.

---

# 🔄 How Data Travels Through the OSI Model

When sending data, it moves **from Layer 7 down to Layer 1**.

When receiving data, it moves **from Layer 1 up to Layer 7**.

```text
              SENDER
                │
                ▼
        7 ─ Application
                ↓
        6 ─ Presentation
                ↓
        5 ─ Session
                ↓
        4 ─ Transport
                ↓
        3 ─ Network
                ↓
        2 ─ Data Link
                ↓
        1 ─ Physical
                │
             NETWORK
                │
                ▼
        1 ─ Physical
                ↓
        2 ─ Data Link
                ↓
        3 ─ Network
                ↓
        4 ─ Transport
                ↓
        5 ─ Session
                ↓
        6 ─ Presentation
                ↓
        7 ─ Application
                │
                ▼
             RECEIVER
```

---

# 📦 Data Encapsulation & Decapsulation

As data moves down the OSI layers, each layer can add its own information.

This process is called **encapsulation**.

```text
Application
     ↓
   DATA
     ↓
Transport
     ↓
SEGMENT / DATAGRAM
     ↓
Network
     ↓
PACKET
     ↓
Data Link
     ↓
FRAME
     ↓
Physical
     ↓
BITS
```

At the receiving device, the information is processed in reverse.

This is called **decapsulation**.

### 🧠 Remember

**Data → Segment → Packet → Frame → Bits**

---

# 🌍 Real-Life Example — Opening a Website

Imagine you open a website on your laptop.

```text
💻 Laptop
   │
   ▼
7️⃣ Application
   Browser / HTTP(S)
   │
   ▼
6️⃣ Presentation
   Encryption / Formatting
   │
   ▼
5️⃣ Session
   Communication Session
   │
   ▼
4️⃣ Transport
   TCP/UDP + Ports
   │
   ▼
3️⃣ Network
   IP + Routing
   │
   ▼
2️⃣ Data Link
   MAC + Frames
   │
   ▼
1️⃣ Physical
   Wi-Fi / Cable / Signals
   │
   ▼
🌐 Internet
   │
   ▼
🖥️ Web Server
```

Each layer performs its own job to help the data reach its destination.

---

# 🔧 OSI Model for Troubleshooting

The OSI Model helps you identify **where a network problem may be occurring**.

```text
❌ No cable / signal
        ↓
Layer 1 — Physical

❌ Local network problem
        ↓
Layer 2 — Data Link

❌ IP / routing problem
        ↓
Layer 3 — Network

❌ Port / TCP / UDP problem
        ↓
Layer 4 — Transport

❌ Session problem
        ↓
Layer 5 — Session

❌ Encryption / formatting problem
        ↓
Layer 6 — Presentation

❌ Application / service problem
        ↓
Layer 7 — Application
```

> 💡 The OSI Model helps you narrow down **where to investigate** instead of randomly checking the entire network.

---

# 🛡️ Why SOC Analysts Should Learn the OSI Model

Understanding the OSI Model helps SOC analysts:

- 🔍 Analyze network traffic
- 🚨 Investigate attacks
- 🌐 Analyze IP addresses
- 🔢 Analyze ports and protocols
- 🧩 Understand attack paths
- 🛠️ Troubleshoot network problems
- 🛡️ Respond to security incidents

### Example SOC Alert

```text
Source IP:        192.168.1.50
Destination IP:   10.0.0.20
Protocol:         TCP
Destination Port: 443
```

An analyst can connect this information to:

```text
Layer 3 → IP addresses
Layer 4 → TCP + Port 443
Layer 7 → Web / HTTPS traffic
```

---

# ⚡ Quick Revision

| Layer | Name | Remember |
|------:|------|----------|
| **7** | Application | Network Services |
| **6** | Presentation | Format & Encryption |
| **5** | Session | Manage Sessions |
| **4** | Transport | TCP/UDP + Ports |
| **3** | Network | IP + Routing |
| **2** | Data Link | MAC + Frames |
| **1** | Physical | Bits + Signals |

---

# 🧠 Remember Like This

### Top → Bottom

**A P S T N D P**

> **All People Seem To Need Data Processing**

```text
7 — Application
6 — Presentation
5 — Session
4 — Transport
3 — Network
2 — Data Link
1 — Physical
```

### ⭐ Data Unit Chain

```text
DATA
  ↓
SEGMENT
  ↓
PACKET
  ↓
FRAME
  ↓
BITS
```

> 🧠 **Application → Services**  
> **Presentation → Format**  
> **Session → Sessions**  
> **Transport → TCP/UDP + Ports**  
> **Network → IP + Routing**  
> **Data Link → MAC + Frames**  
> **Physical → Bits + Signals**

---

# 📚 What's Next?

Excellent work! 🎉 You now understand the **7 layers of the OSI Model**, how data travels through them, and how the model helps with networking, troubleshooting, and cybersecurity.

> **Remember:** The OSI Model is a map that helps you understand **how network communication works and where problems can occur.**

➡️ **Next Chapter:** 🌐 TCP/IP Model
