# 🌐 IP Addresses

> *"IP addresses give devices a logical identity and help data find its way across networks."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what an IP address is.
- Understand the basic structure of an IP address.
- Explain what IP addresses do.
- Understand how devices get IP addresses.
- Differentiate between IPv4 and IPv6.
- Understand public and private IP addresses.
- Know common private IPv4 ranges.
- Understand how routers use IP addresses.

---

# 📖 What is an IP Address?

An **IP address** is a logical address assigned to a device or network interface.

It helps identify a device on a network and allows data to be sent to the correct destination.

Example IPv4 address:

```text
192.168.1.10
```

Think of it like a **digital address** for a device.

---

## Basic Structure of IP Addresses

### IPv4

IPv4 uses **32 bits** divided into four parts called **octets**.

```text
192 . 168 . 1 . 10
 ↓     ↓    ↓    ↓
 8     8    8    8 bits
```

Each octet can contain a value from:

```text
0 → 255
```

Example:

```text
192.168.1.10
```

### IPv6

IPv6 uses **128 bits** and is written using hexadecimal numbers.

Example:

```text
2001:db8::1
```

---

## What IP Addresses Do

IP addresses mainly help with:

- **Identification** — identify a device/interface on a network.
- **Location** — indicate where a device/network is logically located.
- **Routing** — help routers decide where to forward packets.

Simple idea:

```text
Source IP
   ↓
Network
   ↓
Destination IP
   ↓
Correct Destination
```

---

## How Devices Get IP Addresses

A device can receive an IP address in different ways.

### 🟢 DHCP

**DHCP** can automatically provide network settings.

```text
Device
   ↓
DHCP
   ↓
IP Address
Subnet Mask
Default Gateway
DNS Server
```

### 🔵 Static Configuration

An IP address can also be configured manually.

Example:

```text
IP Address: 192.168.1.20
```

---

# 🔄 IPv4 vs IPv6

IPv4 and IPv6 are two versions of the Internet Protocol.

| Feature | IPv4 | IPv6 |
|---|---|---|
| Address Size | 32 bits | 128 bits |
| Format | Decimal | Hexadecimal |
| Example | `192.168.1.10` | `2001:db8::1` |
| Number of Addresses | About 4.3 billion | Extremely large address space |
| Broadcast | Supported | No broadcast; uses multicast/other mechanisms |

---

## Why Do We Need IPv6?

The main reason is **IPv4 address exhaustion**.

The number of devices connected to networks has grown greatly, while IPv4 has a limited address space.

IPv6 provides a much larger address space:

```text
IPv4 → 32 bits
IPv6 → 128 bits
```

This allows networks to support a huge number of unique addresses.

---

# 🌍 Public vs Private IP Addresses

IPv4 addresses can be used in different ways.

### 🟢 Private IP Address

Private IP addresses are used inside local/private networks.

Example:

```text
192.168.1.10
```

A private IP is **not directly routable on the public Internet**.

### 🔵 Public IP Address

A public IP address is used for communication across the public Internet.

Example:

```text
203.0.113.10
```

> `203.0.113.0/24` is a documentation range used for examples, not a normal public address assignment.

---

## Why Do We Need Both Systems?

Private addresses allow devices inside a local network to communicate without requiring a unique public IPv4 address for every device.

Example:

```text
💻 Laptop       192.168.1.10
📱 Phone        192.168.1.11
🖥️ PC           192.168.1.12
       │
       ↓
    Router
       │
       ↓
🌍 Public Internet
```

The router commonly uses **NAT** to allow private IPv4 devices to communicate with the Internet using a public IPv4 address.

---

## Common Private IPv4 Address Ranges

There are three main private IPv4 ranges:

| Range | Example |
|---|---|
| `10.0.0.0/8` | `10.0.0.5` |
| `172.16.0.0/12` | `172.16.5.10` |
| `192.168.0.0/16` | `192.168.1.10` |

These ranges are reserved for private networks.

---

## 🛡️ Security Benefit

Private IP addresses can reduce direct exposure of internal devices to the public Internet.

For example:

```text
Internet
   ↓
Public IP
   ↓
Router / Firewall
   ↓
Private Network
   ↓
Internal Devices
```

However:

> **Private IP addresses are not a complete security solution.**

Firewalls, access controls, authentication, encryption, monitoring, and other security controls are still important.

---

# 🛣️ How Routers Read IP Addresses

Routers examine the **destination IP address** of a packet.

They use their routing table to decide where to forward it.

Example:

```text
Laptop
192.168.1.10
      │
      │ Destination:
      │ 8.8.8.8
      ↓
   Router
      │
      │ Checks routing table
      ↓
   Internet
```

The router does not need to know the entire path in advance.

It uses its routing information to choose the next hop/interface for the packet.

### 🧠 Simple Idea

```text
Destination IP
      ↓
Routing Table
      ↓
Next Hop / Interface
      ↓
Packet Forwarded
```

---

# 🌍 Real-Life Scenario

You open a website on your laptop.

Your laptop might have:

```text
Private IP:
192.168.1.10
```

Your router has a public-facing address and connects your local network to the Internet.

```text
💻 Laptop
192.168.1.10
      ↓
📡 Router
      ↓
🌍 Internet
      ↓
🌐 Web Server
```

The IP addresses help the network deliver packets toward the correct destination.

---

# 🛡️ Why SOC Analysts Should Learn This

IP addresses are everywhere in cybersecurity.

SOC analysts may use IP addresses to:

- Identify source and destination devices.
- Investigate network connections.
- Analyze firewall and SIEM logs.
- Identify internal vs external traffic.
- Investigate suspicious communication.
- Understand network routing.

Example log:

```text
Source IP:      192.168.1.10
Destination IP: 203.0.113.50
Port:           443
Protocol:       TCP
```

A SOC analyst can use this information to understand the connection.

---

# ⚡ Quick Revision

| Concept | Simple Meaning |
|---|---|
| IP Address | Logical address used for network communication |
| IPv4 | 32-bit address |
| IPv6 | 128-bit address |
| Private IP | Used inside private networks |
| Public IP | Used for communication across the public Internet |
| DHCP | Automatically provides IP configuration |
| Static IP | Manually configured IP |
| NAT | Translates private/public IPv4 addresses |
| Router | Uses destination IP and routing information to forward packets |

---

# 🧠 Remember Like This

```text
MAC = Local identity

IP = Logical address

ARP = Finds MAC from IPv4

Router = Uses IP to forward packets
```

> **"MAC helps locally, IP helps across networks, and routers use IP addresses to move packets toward their destination."**

---

# 📚 What's Next?

➡️ **04 - DHCP**

Next, we will learn how devices automatically receive:

- IP addresses
- Subnet masks
- Default gateways
- DNS server information
