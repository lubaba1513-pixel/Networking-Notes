# 🌐 NAT

> *"NAT helps many private devices communicate with the Internet using public IP addresses."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what NAT is.
- Understand why NAT is needed.
- Understand how NAT works with a simple example.
- Learn the main types of NAT.
- Recognize where NAT is commonly used.
- Understand common beginner NAT problems.
- Understand how NAT connects with IP addresses and subnetting.
- Understand the security role and limits of NAT.

---

# 📖 What is NAT?

**NAT** stands for **Network Address Translation**.

NAT changes IP address information as traffic moves between networks.

A common use is translating:

```text
Private IP
   ↓
   NAT
   ↓
Public IP
```

This allows devices using private IPv4 addresses to communicate with the public Internet.

---

# ⚠️ The IPv4 Address Shortage Problem

IPv4 has a limited number of addresses.

But there are billions of devices that need network connectivity.

NAT helps by allowing many devices inside a private network to share public IPv4 addresses.

Example:

```text
💻 Laptop     192.168.1.10
📱 Phone      192.168.1.11
🖥️ PC         192.168.1.12
      │
      ↓
   📡 Router
      │
      ↓
Public IP: 203.0.113.5
      │
      ↓
   🌍 Internet
```

The devices use private IP addresses internally, while the router can use a public IP for Internet communication.

---

# 🔄 How NAT Works — Simple Example

Imagine your laptop wants to visit a website.

```text
Laptop
192.168.1.10
     │
     ↓
Router / NAT
     │
     ↓
203.0.113.5
     │
     ↓
Internet
     │
     ↓
Web Server
```

The NAT device keeps track of the connection so that returning traffic can be sent back to the correct internal device.

With PAT, it also uses **port numbers** to keep multiple connections separate.

### Simple Idea

```text
Private IP + Port
        ↓
       NAT
        ↓
Public IP + Port
```

---

# 🌍 Why NAT is Everywhere

You commonly encounter NAT in:

- 🏠 Home networks
- 🏢 Offices
- 🏫 Schools
- 🏥 Organizations
- ☁️ Some cloud/network environments

A typical home network looks like:

```text
💻 Laptop ─┐
📱 Phone  ─┼──→ 📡 Router/NAT ──→ 🌍 Internet
🖥️ PC     ─┘
```

One public IPv4 address can be shared by many private devices.

---

# 🔄 Types of NAT

There are three common types discussed in basic networking:

## 1️⃣ Static NAT

Static NAT creates a **fixed one-to-one mapping**.

```text
192.168.1.5
     ↓
203.0.113.10
```

The same private address is consistently mapped to the same public address.

### Common Use

- Servers
- Cameras
- Services that need a fixed mapping

```text
One Private IP
       ↓
One Public IP
```

---

## 2️⃣ Dynamic NAT

Dynamic NAT maps private addresses to addresses from a **public IP pool**.

Example:

```text
192.168.1.10 ─┐
192.168.1.11 ─┼──→ Public IP Pool
192.168.1.12 ─┘
```

Example public pool:

```text
203.0.113.20
203.0.113.21
203.0.113.22
203.0.113.23
```

The available public address is assigned from the pool.

```text
Many Private IPs
       ↓
Public IP Pool
       ↓
Temporary mappings
```

---

## 3️⃣ PAT

**PAT** stands for **Port Address Translation**.

It allows many private devices to share **one public IP address** by using different port numbers.

Example:

```text
192.168.1.100
       ↓
203.0.113.5:1000

192.168.1.101
       ↓
203.0.113.5:1001

192.168.1.102
       ↓
203.0.113.5:1002
```

The NAT device uses the port numbers to keep the connections separate.

```text
Many Private Devices
        ↓
   One Public IP
        ↓
   Different Ports
```

PAT is very common in home networks.

> PAT is also commonly called **NAT overload** or **NAPT**.

---

# 📊 NAT Types Comparison

| Type | Mapping | Public IPs Needed | Common Use |
|---|---|---|---|
| **Static NAT** | One-to-one, fixed | Usually one per mapping | Servers, cameras |
| **Dynamic NAT** | Many-to-many from a pool | A public IP pool | Organizations |
| **PAT** | Many-to-one using ports | Often one | Home networks |

### 🧠 Easy Memory

```text
Static NAT  → Fixed
Dynamic NAT → Pool
PAT         → Ports
```

---

# 🌐 Where You Encounter NAT

### 🏠 Home Network

Most home routers commonly use PAT.

```text
Laptop ─┐
Phone  ─┼→ Router/NAT → Internet
Tablet ─┘
```

### 🏢 Office Network

An organization may use NAT to allow many internal devices to access external networks.

### 🖥️ Servers

Static NAT can be used when a private server needs a consistent public mapping.

---

# ⚠️ Common NAT Issues for Beginners

| Issue | What Happens | Simple Explanation | What to Do |
|---|---|---|---|
| **Double NAT** | Remote access or gaming may have problems | Two routers are performing NAT | Check whether two routers are doing NAT; one may need bridge/AP mode |
| **Strict NAT** | Games may show NAT warnings or have connection problems | NAT/router configuration is restricting connections | Check router/game settings; port forwarding may sometimes be needed |
| **No Internet on some devices** | Some devices work while others do not | NAT or router configuration may have a problem | Restart the router and check its configuration |
| **VPN problems** | A VPN may have connection problems | NAT/router configuration can sometimes interfere with VPN traffic | Check VPN and router settings |

> NAT problems can have different causes, so these are simple troubleshooting starting points rather than guaranteed fixes.

---

# 🔗 How NAT Connects to What You've Learned

NAT connects several NF2 concepts together.

```text
IP Addresses
     ↓
Private IPs
     ↓
Subnetting
     ↓
Local Network
     ↓
NAT / PAT
     ↓
Public Internet
```

### Example

You learned that:

```text
192.168.1.10
```

is a private IPv4 address.

Your router can use NAT/PAT to allow that device to communicate with an Internet service.

```text
Private IP
192.168.1.10:5000
       ↓
     NAT/PAT
       ↓
Public IP
203.0.113.5:1000
       ↓
    Internet
```

---

# 🛡️ Security with NAT

NAT can provide a **basic layer of network separation** because internal private addresses are not directly exposed as public addresses.

For example:

```text
🌍 Internet
      ↓
 Public IP
      ↓
 📡 Router / NAT
      ↓
Private Network
      ↓
Internal Devices
```

However:

> **NAT is not a replacement for a firewall.**

Good network security also uses:

- 🔥 Firewalls
- 🔐 Authentication
- 🔑 Access controls
- 🔒 Encryption
- 📊 Monitoring
- 🛡️ Network segmentation

### SOC Perspective

SOC analysts may see NAT-related information in logs and need to understand that:

```text
Public IP
    ↓
NAT Translation
    ↓
Private Device
```

When investigating an incident, NAT logs can help identify which internal device was associated with a public connection at a particular time.

---

# ⚡ Quick Revision

| Concept | Simple Meaning |
|---|---|
| **NAT** | Translates IP addresses between networks |
| **Private IP** | Used inside private networks |
| **Public IP** | Used for public Internet communication |
| **Static NAT** | Fixed one-to-one mapping |
| **Dynamic NAT** | Uses a pool of public IPs |
| **PAT** | Many devices share a public IP using ports |
| **Double NAT** | Two devices are performing NAT |
| **Port Forwarding** | Allows selected incoming traffic to reach an internal device |
| **Firewall** | Controls traffic; NAT is not a firewall |

---

# 🧠 Remember Like This

```text
NAT = Changes addresses

Static NAT  = One → One
Dynamic NAT = Many → Pool
PAT         = Many → One + Ports
```

> **"NAT helps private networks communicate with the public Internet while conserving IPv4 addresses."**

---

# 📚 What's Next?

➡️ **08 - Encryption**

Next, we will learn how **encryption protects data from being read by unauthorized people**.
