# 🔌 Network Ports

> *"IP addresses identify devices; ports identify the services communicating on those devices."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Explain what a network port is.
- Understand why ports are needed.
- Understand the three port categories.
- Identify common port numbers and their services.
- Understand how ports work with IP addresses and protocols.
- Understand common port states.
- Check listening and active ports on Windows.
- Check listening and active ports on Linux.
- Interpret a simple port-checking result.
- Understand why ports are important in cybersecurity.

---

# 🌍 Imagine This...

Imagine an apartment building.

The **building address** tells you which building to visit.

But the building has many doors, each leading to a different service or room.

```text
🏢 Building
IP Address
    │
    ├── 🚪 Port 22  → SSH
    ├── 🚪 Port 53  → DNS
    ├── 🚪 Port 80  → HTTP
    └── 🚪 Port 443 → HTTPS
```

In networking:

- **IP Address** → Identifies the device
- **Port Number** → Identifies the service/application endpoint
- **Protocol** → Defines how communication works

> 🧠 **Easy Trick:**  
> **IP = Which device?**  
> **Port = Which service?**  
> **Protocol = What communication rules?**

---

# 📖 What is a Network Port?

A **network port** is a logical number used to identify a communication endpoint for a service or application.

Port numbers range from:

**0 → 65535**

A port works together with an **IP address** and a **transport protocol** such as TCP or UDP.

```text
192.168.1.10:443
      │       │
      │       └── Port
      │
      └── IP Address
```

This can be understood as:

```text
Device: 192.168.1.10
Port:   443
Protocol: TCP
Service: HTTPS
```

---

# ❓ Why Do We Need Ports?

A single computer can run many network services at the same time.

For example:

```text
                 💻 Server
                    │
       ┌────────────┼────────────┐
       │            │            │
     :22          :80          :443
      │             │             │
     SSH           HTTP         HTTPS
```

Without ports, the operating system would have difficulty determining **which application should receive incoming transport-layer traffic**.

Ports allow multiple applications and services to use the same IP address.

---

# 🧩 Port Categories

Port numbers are divided into three main ranges.

| Category | Range | Common Use |
|----------|-------|------------|
| **Well-Known Ports** | 0–1023 | Common system and network services |
| **Registered Ports** | 1024–49151 | Applications and services |
| **Dynamic / Private Ports** | 49152–65535 | Temporary client-side connections |

### 1️⃣ Well-Known Ports

These are commonly associated with widely used services.

Examples:

```text
22  → SSH
25  → SMTP
53  → DNS
80  → HTTP
443 → HTTPS
```

### 2️⃣ Registered Ports

These are commonly used by applications and services that are registered with IANA.

They are in the range:

**1024–49151**

### 3️⃣ Dynamic / Private Ports

These are commonly used temporarily by client applications for outgoing connections.

Range:

**49152–65535**

Example:

```text
Client
192.168.1.10:51524
       │
       │
       ▼
Server
93.184.216.34:443
```

Here, `51524` can be a temporary client-side port, while `443` is the server's destination port.

---

# 🔢 Common Port Numbers

| Port | Protocol | Service | Description |
|------|----------|---------|-------------|
| **20/21** | FTP | File Transfer | File transfer (data/control) |
| **22** | SSH | Secure Shell | Secure remote access |
| **23** | Telnet | Telnet | Unsecure remote access |
| **25** | SMTP | Simple Mail Transfer | Email sending |
| **53** | DNS | Domain Name System | Converts names to IPs |
| **80** | HTTP | Hypertext Transfer | Regular web traffic |
| **110** | POP3 | Post Office Protocol | Email retrieval |
| **143** | IMAP | Internet Message Access | Email retrieval |
| **443** | HTTPS | HTTP Secure | Encrypted web traffic |
| **3389** | RDP | Remote Desktop Protocol | Windows remote access |

> 💡 **Security Tip:** Telnet is an insecure legacy protocol. Modern environments generally use secure alternatives such as SSH.

---

# 🔄 How Do Ports Work?

When an application communicates over TCP or UDP, the operating system uses port numbers to identify the communication endpoint.

A simplified connection looks like:

```text
Client                              Server

💻                                      🖥️
IP: 192.168.1.10                       IP: 10.0.0.20
Port: 51524                            Port: 443
   │                                      │
   │──── TCP ────────────────────────────►│
   │                                      │
   │          HTTPS Service               │
```

The combination of:

```text
IP Address + Transport Protocol + Port
```

helps identify a network endpoint.

A connection is commonly described using both the **source** and **destination** information.

```text
Source                          Destination

192.168.1.10:51524 ─────────► 10.0.0.20:443
        │                              │
     Client                         Server
```

---

# 🧠 Source Port vs Destination Port

### Source Port

Usually identifies the temporary port used by the client application.

### Destination Port

Usually identifies the service the client wants to reach.

Example:

```text
192.168.1.10:51524
        │
        │  Request
        ▼
10.0.0.20:443
```

Here:

- `51524` → Source port
- `443` → Destination port

---

# 🚦 Common Port States

A port can be in different states depending on what is happening with the connection.

| State | Meaning |
|-------|---------|
| **LISTENING** | A service is waiting for incoming connections |
| **ESTABLISHED** | A connection is currently active |
| **TIME_WAIT** | A recently closed TCP connection is being kept temporarily |
| **CLOSE_WAIT** | The remote side closed the connection, but the local application has not fully closed it |
| **SYN_SENT** | A TCP connection request has been sent and is awaiting a response |

### ⭐ Most Important

```text
LISTENING
   ↓
Service is waiting for connections

ESTABLISHED
   ↓
Connection is active
```

> 💡 UDP does not establish a TCP-style connection, so tools may show UDP sockets differently from TCP connections.

---

# 🔍 Checking Your Ports

You can check ports on your **own computer** to see which services are listening or which connections are active.

---

# 🪟 Check Ports on Windows

## Method 1 — netstat

Open **Command Prompt** and run:

```text
netstat -ano
```

This displays network connections and listening ports.

Example:

```text
Proto  Local Address      Foreign Address      State
TCP    0.0.0.0:443        0.0.0.0:0            LISTENING
TCP    192.168.1.10:51524 93.184.216.34:443    ESTABLISHED
```

### Useful options

```text
netstat -an
```

Shows addresses and ports without resolving names.

```text
netstat -ano
```

Also shows the **PID (Process ID)** associated with the connection.

You can then identify the process with:

```text
tasklist /FI "PID eq 1234"
```

Replace `1234` with the PID you found.

---

## Method 2 — PowerShell

Open PowerShell and run:

```text
Get-NetTCPConnection
```

To see listening TCP connections:

```text
Get-NetTCPConnection -State Listen
```

---

# 🐧 Check Ports on Linux

Open a terminal and run:

```text
ss -tuln
```

This shows listening TCP and UDP sockets.

### Useful command

```text
ss -tulpn
```

This can also show the process information when permitted.

Example:

```text
Netid  State   Local Address:Port
tcp    LISTEN  0.0.0.0:22
tcp    LISTEN  0.0.0.0:80
tcp    LISTEN  0.0.0.0:443
```

This tells you that services are listening on:

```text
22  → SSH
80  → HTTP
443 → HTTPS
```

> 💡 You may need appropriate permissions to see process details for some services.

---

# 🧪 Example — Understanding a Port Result

Suppose your computer shows:

```text
TCP    0.0.0.0:22      0.0.0.0:0      LISTENING
TCP    0.0.0.0:80      0.0.0.0:0      LISTENING
TCP    0.0.0.0:443     0.0.0.0:0      LISTENING
```

You can interpret it as:

| Port | State | Meaning |
|------|-------|---------|
| **22** | LISTENING | SSH service is accepting connections |
| **80** | LISTENING | HTTP service is accepting connections |
| **443** | LISTENING | HTTPS service is accepting connections |

> ⚠️ A listening port is **not automatically malicious**. The important question is whether the service is expected, properly secured, and intentionally exposed.

---

# 🌍 Real-World Scenario

Imagine a company has a web server.

```text
                 🖥️ Web Server
                 10.0.0.20
                      │
          ┌───────────┼───────────┐
          │           │           │
        :22         :80         :443
         │            │            │
        SSH          HTTP        HTTPS
```

A user visits the company's website:

```text
Client
192.168.1.50:52000
       │
       │ TCP
       ▼
Server
10.0.0.20:443
       │
       ▼
     HTTPS
```

The server uses **port 443** for HTTPS traffic.

At the same time, administrators may use **port 22** for SSH.

Different services can therefore operate on the same server while using different ports.

---

# 🛡️ Why SOC Analysts Should Learn Network Ports

Ports are extremely useful when investigating network activity.

A SOC analyst may see an alert such as:

```text
Source IP:        192.168.1.50
Destination IP:   10.0.0.20
Protocol:         TCP
Destination Port: 22
```

The analyst can understand:

```text
TCP + Port 22
       ↓
Possible SSH communication
```

Analysts can then ask:

- Is SSH expected on this system?
- Is the source device authorized?
- Was the connection successful?
- Are there repeated connection attempts?
- Is the service exposed where it should be?

### 🚨 Security Perspective

Unexpected or unusual port activity can be a useful **investigation signal**.

For example:

```text
Many connection attempts
        ↓
      Port 22
        ↓
Possible SSH scanning / brute-force activity
        ↓
Investigate logs + source IP + authentication events
```

> 💡 **Important:** A port number alone does not prove what application is running. Services can use non-standard ports, so analysts should correlate ports with other evidence.

---

# ⚡ Quick Revision

| Concept | Remember |
|---------|----------|
| Port | Logical communication endpoint |
| Range | 0–65535 |
| Well-Known | 0–1023 |
| Registered | 1024–49151 |
| Dynamic / Private | 49152–65535 |
| LISTENING | Waiting for connections |
| ESTABLISHED | Active connection |
| Source Port | Usually client-side temporary port |
| Destination Port | Usually identifies the target service |
| Port 22 | SSH |
| Port 53 | DNS |
| Port 80 | HTTP |
| Port 443 | HTTPS |
| Port 3389 | RDP |

---

# 🧠 Remember Like This

```text
🌐 IP Address
      ↓
   Which device?
      ↓
🔢 Port
      ↓
   Which service?
      ↓
📡 Protocol
      ↓
   How do they communicate?
```

### ⭐ Port Categories

```text
0 ───────── 1023 ───────── 49151 ───────── 65535
│              │              │
│ Well-Known   │ Registered   │ Dynamic/Private
```

### ⭐ Most Important Ports

> **22 → SSH**  
> **53 → DNS**  
> **80 → HTTP**  
> **443 → HTTPS**  
> **3389 → RDP**

---

# 📚 What's Next?

🎉 **Congratulations!**

You have now completed **Networking Fundamentals 1**!

You started with the basics of networking and progressed through:

```text
🌐 Network Overview
        ↓
🔗 Network Topologies
        ↓
🔌 Network Cabling
        ↓
🛠️ Network Devices
        ↓
📚 OSI Model
        ↓
🌐 TCP/IP Model
        ↓
📡 Network Protocols
        ↓
🔢 Network Ports
```

You now have a strong foundation for understanding how devices communicate and how network activity can be analyzed from a cybersecurity perspective.

> **Remember:** Understanding networking is one of the most important foundations for becoming a strong cybersecurity professional.

➡️ **Next:** 🚀 **Networking Fundamentals 2**
