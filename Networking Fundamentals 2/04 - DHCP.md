# 🌐 DHCP

> *"DHCP automatically gives devices the network settings they need to communicate."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what DHCP is.
- Explain what DHCP stands for.
- Understand what information DHCP provides.
- Understand where DHCP is used.
- Explain the DORA process.
- Understand what a DHCP lease is.

---

# 📖 What is DHCP?

It is a network protocol that automatically provides devices with the network settings they need to communicate.

Instead of entering network settings manually on every device, DHCP can provide them automatically.

---

## What Does DHCP Stand For?

```text
D = Dynamic
H = Host
C = Configuration
P = Protocol
```

**Dynamic Host Configuration Protocol**

---

## What Does DHCP Actually Do?

When a device connects to a network, the DHCP server can provide several important network settings, including:

| Information | Simple Meaning |
|---|---|
| **IP Address** | The device's address on the network |
| **Subnet Mask** | Shows which network/segment the device belongs to |
| **Default Gateway** | The router used to reach other networks |
| **DNS Server** | Helps translate website names into IP addresses |

Example:

```text
💻 Device
   ↓
DHCP Server
   ↓
IP Address       → 192.168.1.20
Subnet Mask      → 255.255.255.0
Default Gateway  → 192.168.1.1
DNS Server       → 192.168.1.1
```

---

## Where is DHCP Used?

DHCP is commonly used in:

- 🏠 Home networks
- 🏢 Offices
- 🏫 Schools
- 🏥 Organizations
- 🌐 Enterprise networks

For example, when your laptop or phone connects to Wi-Fi, it can use DHCP to receive its network configuration automatically.

---

# 🔄 Manual vs DHCP

There are two common ways to configure network settings.

| Method | How It Works | Main Issue |
|---|---|---|
| **Manual (Static)** | A person enters the settings on each device | Time-consuming and can cause configuration mistakes |
| **DHCP (Dynamic)** | A DHCP server automatically assigns and manages settings | Requires a working DHCP service |

### Manual Configuration

```text
Person
  ↓
Enters IP
Subnet Mask
Gateway
DNS
  ↓
Device
```

### DHCP Configuration

```text
Device
  ↓
DHCP Server
  ↓
IP + Subnet Mask + Gateway + DNS
  ↓
Device is ready
```

DHCP makes managing many devices much easier.

---

# 🔄 The DORA Process

DHCP uses a four-step conversation called **DORA**:

```text
D → Discover
O → Offer
R → Request
A → Acknowledge
```

---

## 1️⃣ Discover

The device looks for a DHCP server.

The device is basically saying:

> **"Hello! Is there a DHCP server here? I need an IP address."**

```text
💻 Device
    │
    │ DHCP Discover
    ↓
🌐 DHCP Server
```

---

## 2️⃣ Offer

The DHCP server responds with an available configuration.

It may offer:

- IP address
- Subnet mask
- Default gateway
- DNS server
- Lease information

The server is basically saying:

> **"I have an IP address for you. Here are the details."**

```text
💻 Device
    ↑
    │ DHCP Offer
    │
🌐 DHCP Server
```

---

## 3️⃣ Request

The device requests the offered IP configuration.

The device is basically saying:

> **"I'd like to use that IP address you offered me."**

```text
💻 Device
    │
    │ DHCP Request
    ↓
🌐 DHCP Server
```

---

## 4️⃣ Acknowledge

The DHCP server confirms the assignment.

The server is basically saying:

> **"Confirmed! This configuration is now assigned to you."**

```text
💻 Device
    ↑
    │ DHCP ACK
    │
🌐 DHCP Server
```

---

# 🏨 DORA — Real-World Analogy

Think of checking into a hotel.

| DHCP Step | Hotel Example |
|---|---|
| **Discover** | Guest asks for a room |
| **Offer** | Manager offers an available room |
| **Request** | Guest accepts that room |
| **Acknowledge** | Manager confirms the booking and gives the key |

So remember:

```text
Discover → Offer → Request → Acknowledge
```

---

# ⏳ What is a Lease?

A **DHCP lease** is the period of time for which a DHCP server allows a device to use an assigned IP address.

The IP address is not necessarily assigned to the device forever.

Example:

```text
IP Address: 192.168.1.20
Lease Time: 8 hours
```

Before the lease expires, the device can communicate with the DHCP server to renew its lease.

If the device leaves the network, the address can eventually become available for another device.

### 🧠 Simple Example

Imagine a parking space:

```text
🚗 Device
   ↓
🅿️ IP Address
   ↓
⏳ Lease Time
```

The device gets to use the address for a period of time.

---

# 🌍 Real-Life Scenario

You connect your laptop to your home Wi-Fi.

```text
💻 Laptop
    │
    │ DORA
    ↓
📡 Router / DHCP Server
    │
    ↓
IP:       192.168.1.20
Mask:     255.255.255.0
Gateway:  192.168.1.1
DNS:      192.168.1.1
```

Now your laptop has the network information it needs to communicate with devices on the local network and reach other networks.

---

# 🛡️ Why SOC Analysts Should Learn This

DHCP information can be useful during network investigations.

A SOC analyst may investigate:

- Which device received an IP address.
- When an IP address was assigned.
- DHCP configuration problems.
- Unexpected DHCP activity.
- Devices receiving unusual network settings.

DHCP logs can help connect a device's identity with an IP address at a particular time.

---

# ⚡ Quick Revision

| Concept | Simple Meaning |
|---|---|
| **DHCP** | Automatically provides network configuration |
| **IP Address** | Device's network address |
| **Subnet Mask** | Identifies the network/segment |
| **Default Gateway** | Router used to reach other networks |
| **DNS Server** | Translates domain names into IP addresses |
| **DORA** | Discover → Offer → Request → Acknowledge |
| **Lease** | Temporary period for using an assigned IP |

---

# 🧠 Remember Like This

```text
DHCP = Automatic Network Configuration

D → Discover
O → Offer
R → Request
A → Acknowledge

Lease = Temporary use of an IP address
```

> **"DHCP saves you from manually configuring every device on the network."**

---

# 📚 What's Next?

➡️ **05 - DNS**

Next, we will learn how DNS translates human-friendly domain names such as:

```text
google.com
```

into IP addresses that networks can use.
