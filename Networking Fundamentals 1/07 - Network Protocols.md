# 🌐 Network Protocols

> *"Protocols are the rules that allow devices to understand each other."*

---

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Explain what a network protocol is.
- Understand why protocols are needed.
- Understand how protocol standards help devices communicate.
- Explain what happens without protocols.
- Identify common application protocols.
- Understand how different protocols work together.
- Understand what a protocol header is.
- Explain why protocols are important in cybersecurity.

---

# 🌍 Imagine This...

Imagine two people trying to have a conversation.

One person speaks English, while the other speaks a completely different language.

Without a common language and agreed rules, communication becomes difficult.

Networks work the same way.

Computers need **agreed rules** to understand how data should be sent, received, and interpreted.

These rules are called **Network Protocols**.

---

# 📖 What is a Network Protocol?

A **network protocol** is a set of rules that defines how devices communicate over a network.

Protocols define things such as:

- How communication starts
- How data is formatted
- How data is transmitted
- How devices identify each other
- How errors are handled
- How communication ends

```text
💻 Device A
     │
     │  Protocol Rules
     ▼
🌐 Network
     │
     │  Protocol Rules
     ▼
💻 Device B
```

> 💡 **Simple Definition:**  
> A protocol is a **rulebook for network communication**.

---

# ❓ Why Do We Need Protocols?

Without protocols, devices would not have a common way to communicate.

Protocols help devices:

- 🤝 Understand each other
- 📦 Format data correctly
- 🗺️ Find destinations
- 🔄 Control data delivery
- 🛠️ Handle errors
- 🔒 Support secure communication
- 🌐 Communicate across different networks

### 🌍 Real-Life Example

When you visit a website, many protocols work together to make the communication possible.

```text
You
 │
 ▼
Browser
 │
 ├── DNS → Find the server
 │
 ├── TCP → Reliable transport
 │
 ├── IP → Deliver across networks
 │
 └── HTTP/HTTPS → Web communication
 │
 ▼
Web Server
```

---

# 📏 Protocols & Standards

Protocols work best when devices follow common **standards**.

A **standard** is an agreed specification that allows different systems and manufacturers to work together.

Organizations involved in networking standards include:

- **IETF** — Internet Engineering Task Force
- **IEEE** — Institute of Electrical and Electronics Engineers
- **ISO** — International Organization for Standardization

### 🌍 Why Standards Matter

Imagine buying a network device from one company and connecting it to a device from another company.

If both follow common standards:

```text
Company A Device
       │
       │  Common Standards
       ▼
Company B Device
```

They can communicate even though they were made by different manufacturers.

> 💡 **Protocol = Rules**  
> **Standard = Agreed specification**

---

# ❌ Without Protocols vs With Protocols

## Without Protocols

Imagine every device follows its own rules.

```text
💻 A
 │
 │ "I send data this way!"
 ▼
🌐 Network
 ▲
 │ "I understand it differently!"
 │
💻 B

❌ Communication fails
```

Problems could include:

- Different data formats
- No common addressing method
- No agreed communication process
- Difficult error handling
- Poor interoperability

---

## With Protocols

Devices follow the same communication rules.

```text
💻 A
 │
 │  Standard Protocol
 ▼
🌐 Network
 │
 │  Standard Protocol
 ▼
💻 B

✅ Communication works
```

### 🧠 Remember

**Protocols = Common Rules = Successful Communication**

---

# 🧩 Common Application Protocols

Application protocols provide services used by network applications.

| Protocol | Purpose | Default Port | Secure Version |
|----------|---------|--------------|----------------|
| **HTTP** | Web browsing | 80 | HTTPS (443) |
| **HTTPS** | Secure web browsing | 443 | — |
| **SMTP** | Sending email | 25 | SMTPS (465) |
| **IMAP** | Retrieving & synchronizing email | 143 | IMAPS (993) |
| **POP3** | Retrieving email | 110 | POP3S (995) |
| **FTP** | File transfer | 21 | SFTP (22) |
| **SSH** | Secure remote access | 22 | — |
| **DNS** | Name resolution | 53 | DNS over HTTPS/TLS |

> 💡 Ports shown above are common/default ports. Actual deployments can use different ports.

---

# 🔑 HTTP & HTTPS

## HTTP

**HTTP (Hypertext Transfer Protocol)** is used for communication between web browsers and web servers.

```text
💻 Browser
    │
    │ HTTP
    ▼
🌐 Web Server
```

HTTP commonly uses **Port 80**.

---

## HTTPS

**HTTPS (HTTP Secure)** protects HTTP communication using **TLS**.

```text
💻 Browser
    │
    │ HTTPS 🔒
    ▼
🌐 Web Server
```

HTTPS commonly uses **Port 443**.

### 🛡️ SOC Perspective

SOC analysts monitor web traffic for:

- Suspicious URLs
- Malicious requests
- Unusual destinations
- Web attacks
- Abnormal HTTPS connections

---

# 📧 Email Protocols

Different protocols are used for different email tasks.

### SMTP

**SMTP (Simple Mail Transfer Protocol)** is mainly used to **send email**.

### IMAP

**IMAP (Internet Message Access Protocol)** is used to access and synchronize email stored on a mail server.

### POP3

**POP3 (Post Office Protocol 3)** is used to retrieve email, traditionally by downloading messages from the server.

```text
📧 Send Email
     │
     ▼
   SMTP
     │
     ▼
📨 Mail Server
     │
     ├── IMAP → Access & synchronize
     │
     └── POP3 → Retrieve messages
```

---

# 📁 FTP & SFTP

### FTP

**FTP (File Transfer Protocol)** is used to transfer files.

It commonly uses:

- Port 21 — Control connection
- Port 20 — Data connection in traditional active-mode FTP

### SFTP

**SFTP (SSH File Transfer Protocol)** provides file transfer through an SSH connection and commonly uses **Port 22**.

```text
💻 Client
   │
   ├── FTP ────► 📁 Server
   │
   └── SFTP 🔒 ► 📁 Server
```

> 💡 FTP itself does not provide encryption. SFTP is a different protocol built over SSH.

---

# 🔐 SSH

**SSH (Secure Shell)** provides secure remote access to systems.

It is commonly used by:

- System administrators
- Network administrators
- Security professionals
- DevOps engineers

SSH commonly uses **Port 22**.

```text
💻 Admin
   │
   │ SSH 🔒
   ▼
🖥️ Remote Server
```

🛡️ **SOC Perspective:** Analysts may investigate unusual SSH logins, repeated authentication failures, and unexpected remote access.

---

# 🌐 DNS

**DNS (Domain Name System)** translates domain names into IP addresses.

For example:

```text
www.example.com
        │
        ▼
       DNS
        │
        ▼
   IP Address
```

DNS commonly uses **Port 53** over UDP or TCP.

### 🧠 Remember

**DNS = Name → IP**

🛡️ **SOC Perspective:** DNS is especially important for detecting suspicious domains, command-and-control activity, DNS tunneling, and DGA-related activity.

---

# 🤝 How Protocols Work Together

A single network communication can involve **multiple protocols**.

Imagine opening a website.

```text
👤 User
   │
   ▼
🌐 Browser
   │
   │ HTTPS
   ▼
🔢 DNS
   │
   │ Find IP address
   ▼
📍 IP
   │
   ▼
🚚 TCP
   │
   ▼
🔌 Ethernet / Wi-Fi
   │
   ▼
🌐 Network
   │
   ▼
🖥️ Web Server
```

Each protocol performs a different job.

### Example

When visiting a website:

1. **DNS** helps find the server's IP address.
2. **TCP** provides reliable transport when TCP is used.
3. **IP** handles addressing and routing.
4. **Ethernet/Wi-Fi** moves data across the local network.
5. **HTTPS** handles secure web communication.

> 💡 Protocols don't work alone. They **work together as a stack**.

---

# 🧱 Protocol Stack

A **protocol stack** is a group of protocols that work together to provide network communication.

For a typical HTTPS connection:

```text
┌─────────────────────┐
│ HTTPS               │ ← Web communication
├─────────────────────┤
│ TLS                 │ ← Security
├─────────────────────┤
│ TCP                 │ ← Transport
├─────────────────────┤
│ IP                  │ ← Addressing & Routing
├─────────────────────┤
│ Ethernet / Wi-Fi    │ ← Local Network
└─────────────────────┘
```

Each layer provides services to the layer above it.

---

# 🧾 What is a Protocol Header?

A **protocol header** is control information added to data by a protocol.

Headers contain information needed to process and deliver the data.

Different protocols have different headers.

### Example

A simplified packet might look like:

```text
┌─────────────────────┐
│ Ethernet Header     │
├─────────────────────┤
│ IP Header           │
├─────────────────────┤
│ TCP Header          │
├─────────────────────┤
│ Application Data    │
└─────────────────────┘
```

Each header provides information for its corresponding protocol.

---

# 🔍 What Can Headers Contain?

Depending on the protocol, headers may contain information such as:

### Ethernet Header

- Source MAC address
- Destination MAC address
- EtherType

### IP Header

- Source IP address
- Destination IP address
- Protocol information

### TCP Header

- Source port
- Destination port
- Sequence number
- Acknowledgment information
- Control flags

### 🧠 Remember

**Headers = Information needed to handle the data**

---

# 📦 Encapsulation with Protocol Headers

As data moves through the protocol stack, headers are added.

```text
Application Data
      ↓
   + TCP Header
      ↓
   + IP Header
      ↓
+ Ethernet Header
      ↓
   Network
```

At the receiving device, the headers are processed and removed as the data moves upward.

This is part of **decapsulation**.

---

# 🔄 Protocols Across the TCP/IP Model

Protocols can be associated with different layers of the TCP/IP Model.

| TCP/IP Layer | Examples |
|--------------|----------|
| **Application** | HTTP, HTTPS, DNS, SMTP, IMAP, POP3, FTP, SSH |
| **Transport** | TCP, UDP |
| **Internet** | IPv4, IPv6, ICMP |
| **Network Access** | Ethernet, Wi-Fi, ARP |

```text
4 ─ Application
    │
    ├── HTTP / HTTPS
    ├── DNS
    ├── SMTP
    └── SSH
    │
3 ─ Transport
    │
    ├── TCP
    └── UDP
    │
2 ─ Internet
    │
    ├── IPv4 / IPv6
    └── ICMP
    │
1 ─ Network Access
    │
    ├── Ethernet
    └── Wi-Fi
```

---

# 🛡️ Why SOC Analysts Should Learn Network Protocols

Protocols are extremely important in cybersecurity because network attacks often appear as **unusual protocol behavior**.

Understanding protocols helps SOC analysts:

- 🔍 Analyze network traffic
- 🚨 Identify suspicious connections
- 🌐 Investigate DNS activity
- 🔢 Analyze ports
- 📦 Understand packet contents
- 🧩 Recognize abnormal protocol behavior
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
IP       → Where the traffic is going
TCP      → How it is transported
Port 443 → HTTPS service
```

---

# ⚡ Quick Revision

| Concept | Remember |
|---------|----------|
| Protocol | Rules for communication |
| Standard | Agreed specification |
| HTTP | Web communication |
| HTTPS | Secure web communication |
| SMTP | Send email |
| IMAP | Access & synchronize email |
| POP3 | Retrieve email |
| FTP | File transfer |
| SFTP | Secure file transfer over SSH |
| SSH | Secure remote access |
| DNS | Name → IP |
| Header | Control information added by a protocol |

---

# 🧠 Remember Like This

### Protocol = Rulebook

```text
💻 Device A
     │
     │ Follow the rules
     ▼
🌐 Network
     │
     │ Follow the rules
     ▼
💻 Device B
```

### Website Communication

> **DNS → Find**  
> **TCP → Transport**  
> **IP → Route**  
> **HTTPS → Communicate Securely**  
> **Ethernet/Wi-Fi → Connect Locally**

### Protocol Header

> **Header = Information needed to handle the data**

---

# 📚 What's Next?

Excellent work! 🎉 You now understand what network protocols are, why standards matter, how common protocols work together, and how protocol headers help deliver data.

> **Remember:** Networks work because devices follow common rules and protocols work together as a stack.

➡️ **Next Chapter:** 🔢 IP Addressing
