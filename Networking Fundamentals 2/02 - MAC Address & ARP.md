# 🔗 MAC Addressing & ARP Process

> *"IP addresses help devices find each other, while MAC addresses help
> them communicate on the local network."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

-   Understand what a MAC address is.
-   Explain the format of a MAC address.
-   Understand the difference between MAC and IP addresses.
-   Understand where MAC addresses work.
-   Explain what ARP is and why it is needed.
-   Understand the ARP process step by step.
-   Understand the ARP message structure and ARP cache.
-   View ARP tables on Windows, Linux, and macOS.
-   Understand network changes, Gratuitous ARP, and Proxy ARP.
-   Troubleshoot common ARP problems.
-   Understand why MAC addresses and ARP matter to SOC analysts.

------------------------------------------------------------------------

# 🌍 Imagine This...

Imagine you live in an apartment building.

-   🏠 **IP Address** = Apartment number
-   👤 **MAC Address** = Unique identity of the device
-   📖 **ARP** = The local phonebook that helps find the device using an
    IP address

You may know **which apartment** you want to reach, but you still need
to know **which device** should receive the message.

That's where ARP helps.

------------------------------------------------------------------------

# 📖 What is a MAC Address?

**MAC** stands for **Media Access Control**.

A MAC address is a hardware-level address used to identify a network
interface on a local network.

It operates mainly at **Layer 2 --- Data Link Layer** of the OSI model.

Example:

``` text
00:1A:2B:3C:4D:5E
```

A device can have different MAC addresses for different network
interfaces.

``` text
💻 Laptop

Wi-Fi Adapter     → MAC Address A
Ethernet Adapter  → MAC Address B
```

------------------------------------------------------------------------

# 1️⃣ MAC Address = Local Network Interface Identity

Think of a MAC address as the **local identity** of a network interface.

When devices communicate on the same local network, Ethernet frames use
MAC addresses to identify:

-   Who sent the frame
-   Who should receive the frame

Example:

``` text
Computer A
IP: 192.168.1.10
MAC: 00:11:22:33:44:55

        ↓

Computer B
IP: 192.168.1.12
MAC: 00:AA:BB:CC:DD:EE
```

Computer A may know Computer B's IP address, but to send an Ethernet
frame locally, it needs Computer B's MAC address.

ARP helps discover it.

------------------------------------------------------------------------

# 2️⃣ MAC Address Format

A typical MAC address contains **48 bits (6 bytes)**.

It is usually written as six groups of hexadecimal numbers.

``` text
00:1A:2B:3C:4D:5E
```

Each group contains **2 hexadecimal digits**.

``` text
00 : 1A : 2B : 3C : 4D : 5E
│    │    │    │    │    │
2    2    2    2    2    2
hex  hex  hex  hex  hex  hex
```

Since:

``` text
1 Hex digit = 4 bits
```

Therefore:

``` text
12 Hex digits × 4 bits = 48 bits
```

Example:

``` text
A1:B2:C3:D4:E5:F6
```

contains:

``` text
6 bytes
48 bits
12 hexadecimal digits
```

------------------------------------------------------------------------

# 🧩 MAC Address Types

### 🟢 Unicast

A frame is sent to **one specific device**.

``` text
Computer A ─────────→ Computer B
```

### 🔵 Broadcast

A frame is sent to **all devices on the local network**.

The Ethernet broadcast MAC address is:

``` text
FF:FF:FF:FF:FF:FF
```

ARP Requests commonly use Ethernet broadcast because the sender does not
yet know the target MAC address.

``` text
             ┌──→ Device A
             │
Computer ────┼──→ Device B
             │
             └──→ Device C
```

### 🟣 Multicast

A frame is sent to a **specific group of devices**.

``` text
             ┌──→ Device A
             │
Sender ──────┼──→ Device C
             │
             └──→ Device E
```

------------------------------------------------------------------------

# 3️⃣ MAC vs IP

  -----------------------------------------------------------------------
  Feature                 MAC Address             IP Address
  ----------------------- ----------------------- -----------------------
  Main Layer              Layer 2                 Layer 3

  Purpose                 Local network           Logical addressing and
                          identification          routing

  Format                  Hexadecimal             IPv4 / IPv6

  Example                 `00:1A:2B:3C:4D:5E`     `192.168.1.10`

  Used by                 Ethernet / Wi-Fi        IP

  Scope                   Mainly local network    Can work across
                                                  networks

  Changes                 Can change when         Can change with network
                          interface or            configuration
                          configuration changes   
  -----------------------------------------------------------------------

### 🧠 Easy Way to Remember

``` text
MAC = Who are you on this local network?

IP = Where are you on the network?
```

------------------------------------------------------------------------

# 4️⃣ Where MAC Addresses Work

MAC addresses are mainly used on the **local network**.

``` text
Laptop
  │
  ↓
Switch
  │
  ↓
Router
  │
  ↓
Internet
```

When your laptop sends data to the router, the local Ethernet/Wi-Fi
communication uses MAC addresses.

When packets travel through multiple networks, routers use **IP
addresses** to make routing decisions.

### Important

A MAC address is generally **not used to route packets across the
Internet**.

Routers forward packets based primarily on the **destination IP
address**.

------------------------------------------------------------------------

# 📖 What is ARP?

**ARP** stands for:

> **Address Resolution Protocol**

ARP is used in IPv4 networks to discover the **MAC address associated
with an IP address on the local network**.

In simple words:

``` text
IP Address → MAC Address
```

Example:

``` text
I know:

192.168.1.12

But I need:

00:1C:2D:3E:4F:6A
```

ARP helps find that MAC address.

------------------------------------------------------------------------

# 1️⃣ ARP = The Network Phonebook

You know:

``` text
IP = 192.168.1.12
```

But you need:

``` text
MAC = 00:1C:2D:3E:4F:6A
```

So the device asks:

> "Who has 192.168.1.12?"

The device using that IP responds:

> "That's me. My MAC address is 00:1C:2D:3E:4F:6A."

Now the sender can communicate with it on the local network.

------------------------------------------------------------------------

# 2️⃣ How ARP Works --- Step by Step

Suppose:

``` text
Computer A
IP: 192.168.1.10
MAC: AA:AA:AA:AA:AA:AA

Computer B
IP: 192.168.1.12
MAC: BB:BB:BB:BB:BB:BB
```

## Step 1 --- Check ARP Cache

Computer A first checks whether it already knows the MAC address.

``` text
192.168.1.12 → BB:BB:BB:BB:BB:BB
```

If the entry exists, it can use it.

If not, it continues.

## Step 2 --- Send ARP Request

Computer A asks:

``` text
"Who has 192.168.1.12?"
```

The request is sent as a **broadcast** on the local network.

``` text
             ┌──→ Computer C
             │
Computer A ──┼──→ Computer B
             │
             └──→ Computer D
```

All devices receive the request, but only the device using
`192.168.1.12` needs to respond.

## Step 3 --- ARP Reply

Computer B sends an ARP Reply:

``` text
"192.168.1.12 is at
BB:BB:BB:BB:BB:BB"
```

The reply is normally sent directly to Computer A's MAC address.

## Step 4 --- Store the Information

Computer A stores:

``` text
192.168.1.12
      ↓
BB:BB:BB:BB:BB:BB
```

## Step 5 --- Send the Data

Now Computer A can create an Ethernet frame using Computer B's MAC
address.

``` text
Application Data
       ↓
TCP/UDP
       ↓
IP Packet
       ↓
Ethernet Frame
       ↓
Destination MAC
BB:BB:BB:BB:BB:BB
```

------------------------------------------------------------------------

# 🔄 Complete ARP Flow

``` text
Computer A
192.168.1.10
     │
     │ ARP Request
     │ "Who has 192.168.1.12?"
     │
     ├─────────────────────────→ Broadcast
     │
     │              Computer B
     │              192.168.1.12
     │              MAC: BB:BB:BB:BB:BB:BB
     │
     │ ARP Reply
     │ "192.168.1.12 is at BB:BB:BB:BB:BB:BB"
     │
     ←─────────────────────────
     │
     ↓
ARP Cache Updated
     │
     ↓
Data Communication
```

------------------------------------------------------------------------

# 3️⃣ ARP Message Structure

ARP messages contain information needed for address resolution.

  --------------------------------------------------------------------------
  Field                   Purpose                 Example
  ----------------------- ----------------------- --------------------------
  Hardware Type           Type of hardware        `1` for Ethernet

  Protocol Type           Network protocol        `0x0800` for IPv4

  Hardware Size           Length of MAC address   `6 bytes`

  Protocol Size           Length of IPv4 address  `4 bytes`

  Operation               Request or Reply        `1 = Request, 2 = Reply`

  Sender MAC              MAC of sender           `00:1A:2B:3C:4D:5E`

  Sender IP               IP of sender            `192.168.1.10`

  Target MAC              MAC being asked for     `00:00:00:00:00:00` in a
                                                  typical request

  Target IP               IP being asked about    `192.168.1.12`
  --------------------------------------------------------------------------

### 🧠 Important

In a typical ARP Request, the target MAC is unknown:

``` text
00:00:00:00:00:00
```

The target IP is the IP address being searched for.

------------------------------------------------------------------------

# 4️⃣ The ARP Cache

The **ARP cache** is a temporary table that stores recently learned:

``` text
IP Address ↔ MAC Address
```

Example:

``` text
IP Address       MAC Address             Type

192.168.1.1      00:11:22:33:44:55       dynamic
192.168.1.12     00:1C:2D:3E:4F:6A       dynamic
192.168.1.15     AA:BB:CC:DD:EE:FF       dynamic
```

This avoids sending an ARP Request every time the same local device is
contacted.

## Dynamic ARP Entry

Learned automatically through ARP.

``` text
192.168.1.12 → 00:1C:2D:3E:4F:6A
```

Dynamic entries can expire.

## Static ARP Entry

Manually configured IP-to-MAC mapping.

Static entries can be useful in specific network configurations, but
they require manual management.

------------------------------------------------------------------------

# 5️⃣ Viewing ARP Tables

  Operating System   Command                  What You'll See
  ------------------ ------------------------ --------------------------------
  Windows            `arp -a`                 IP addresses and MAC addresses
  Linux              `arp -n` or `ip neigh`   IP-to-MAC mappings
  macOS              `arp -a`                 Similar ARP information

### Windows

``` cmd
arp -a
```

Example:

``` text
192.168.1.1    00-11-22-33-44-55    dynamic
192.168.1.12   00-1c-2d-3e-4f-6a    dynamic
192.168.1.15   aa-bb-cc-dd-ee-ff    dynamic
```

### Linux

``` bash
ip neigh
```

Example:

``` text
192.168.1.1 dev eth0 lladdr 00:11:22:33:44:55 REACHABLE
192.168.1.12 dev eth0 lladdr 00:1c:2d:3e:4f:6a REACHABLE
```

------------------------------------------------------------------------

# 👀 What an ARP Table Tells You

An ARP table can show:

``` text
IP Address
     ↓
MAC Address
     ↓
Interface
     ↓
Entry State
```

For example:

``` text
192.168.1.12
      ↓
00:1C:2D:3E:4F:6A
      ↓
eth0
      ↓
REACHABLE
```

This helps you understand local IP-to-MAC relationships your system has
recently learned.

------------------------------------------------------------------------

# 6️⃣ Network Changes and ARP

Networks can change.

For example:

``` text
Yesterday:

192.168.1.12 → MAC A

Today:

192.168.1.12 → MAC B
```

This can happen because:

-   A device was replaced.
-   A network interface changed.
-   A device reconnected.
-   DHCP assigned a different IP.
-   An ARP cache entry expired.
-   Network configuration changed.

The device may need to update its ARP information.

``` text
Network changes
      ↓
ARP information may change
      ↓
Cache gets updated
```

------------------------------------------------------------------------

# 7️⃣ Gratuitous ARP

**Gratuitous ARP (GARP)** is an ARP message sent by a device to announce
or confirm its own IP-to-MAC mapping.

It can be useful when:

-   A device changes network state.
-   A device wants other devices to update their ARP information.
-   Redundant systems need to announce a changed address.

Simple example:

``` text
Device:

"My IP is 192.168.1.10
and my MAC is AA:AA:AA:AA:AA:AA."
```

------------------------------------------------------------------------

# 8️⃣ Proxy ARP --- Simplified

**Proxy ARP** occurs when a device, usually a router, responds to an ARP
Request on behalf of another device.

Instead of:

``` text
Computer A → Computer B
```

the router may respond:

``` text
Computer A → Router
```

The router then handles communication toward the destination.

``` text
Computer A
    │
    │ ARP Request
    ↓
Router
    │
    │ forwards traffic
    ↓
Computer B
```

Proxy ARP can be useful in certain network designs, but it can also make
troubleshooting more complicated.

------------------------------------------------------------------------

# ⚠️ ARP Limitations

ARP was designed for address resolution, not strong security.

Important limitations include:

-   ARP does not provide strong authentication.
-   Devices generally trust ARP information they receive.
-   Incorrect ARP information can cause communication problems.
-   ARP is used with IPv4.

For IPv6, **Neighbor Discovery Protocol (NDP)** is used instead of ARP.

------------------------------------------------------------------------

# 9️⃣ Common ARP Issues & Troubleshooting

## 🟠 Problem 1 --- Device Cannot Reach Another Local Device

Possible causes:

-   Incorrect IP configuration
-   Incorrect subnet
-   Device is offline
-   Network interface problem
-   Incorrect ARP information

Check:

``` cmd
arp -a
```

or:

``` bash
ip neigh
```

------------------------------------------------------------------------

## 🟠 Problem 2 --- Unexpected MAC Address

Example:

``` text
192.168.1.12 → unexpected MAC address
```

Possible causes include:

-   Network changes
-   Stale cache information
-   Duplicate IP address
-   Configuration problems
-   Suspicious ARP activity

Investigate the device and network configuration before assuming
malicious activity.

------------------------------------------------------------------------

## 🟠 Problem 3 --- Duplicate IP Address

Two devices should not normally use the same IP address.

``` text
Device A → 192.168.1.20
Device B → 192.168.1.20
```

This can create unstable communication and changing ARP mappings.

------------------------------------------------------------------------

# 🛡️ ARP and Cybersecurity

ARP is important for SOC analysts because it provides information about
**local network relationships**.

A SOC analyst may investigate:

-   Unexpected IP-to-MAC mappings
-   Unknown devices
-   Duplicate IP addresses
-   Sudden ARP changes
-   Unusual ARP traffic
-   Communication problems caused by incorrect ARP information

## ⚠️ ARP Spoofing

ARP spoofing is a security issue where false ARP information is
introduced into a local network.

It can cause devices to associate an IP address with an incorrect MAC
address.

Conceptually:

``` text
Correct:

192.168.1.1 → Router MAC


Unexpected:

192.168.1.1 → Unexpected MAC
```

This can potentially redirect or disrupt local network traffic.

### 🛡️ Defensive Awareness

Organizations can use measures such as:

-   ARP monitoring
-   Network segmentation
-   Switch security features
-   Static ARP entries where appropriate
-   Encryption such as HTTPS
-   Network monitoring and alerting

------------------------------------------------------------------------

# 🔄 MAC + ARP + IP Working Together

These three concepts work together during local communication.

``` text
              APPLICATION
                   ↓
                TCP/UDP
                   ↓
               IP Address
                   ↓
        "Where is the device?"
                   ↓
                  ARP
                   ↓
        "What is its MAC address?"
                   ↓
             MAC Address
                   ↓
           Ethernet Frame
                   ↓
              Local Network
```

### Example

Computer A wants to communicate with:

``` text
Destination IP:
192.168.1.12
```

It checks its ARP cache:

``` text
192.168.1.12
      ↓
00:1C:2D:3E:4F:6A
```

Now it can create a frame:

``` text
Source MAC:
AA:AA:AA:AA:AA:AA

Destination MAC:
00:1C:2D:3E:4F:6A
```

The IP packet inside the frame still contains:

``` text
Destination IP:
192.168.1.12
```

------------------------------------------------------------------------

# 🌍 Real-Life Scenario

Imagine you open a website from your laptop.

Your laptop needs to communicate with your local router first.

``` text
💻 Laptop
IP: 192.168.1.10
MAC: AA:AA:AA:AA:AA:AA

        ↓

📡 Router
IP: 192.168.1.1
MAC: BB:BB:BB:BB:BB:BB
```

Your laptop already knows the router's IP:

``` text
192.168.1.1
```

But it needs the router's MAC address for local Ethernet/Wi-Fi
communication.

So it checks its ARP cache.

If the MAC is unknown:

``` text
Laptop
   │
   │ "Who has 192.168.1.1?"
   ↓
Broadcast
   │
   ↓
Router
   │
   │ "192.168.1.1 is at BB:BB:BB:BB:BB:BB"
   ↓
Laptop
```

The laptop stores the result and can then send the Ethernet/Wi-Fi frame
to the router.

------------------------------------------------------------------------

# 🛠️ Simple Troubleshooting Flow

``` text
Can I reach the device?
        │
       NO
        ↓
Check IP configuration
        ↓
Check subnet
        ↓
Check ARP table
        ↓
Is the MAC address present?
      /         YES      NO
     ↓        ↓
Check MAC    ARP resolution
and network  problem
     │
     ↓
Check device/interface
```

------------------------------------------------------------------------

# 🛡️ Why SOC Analysts Should Learn This

Understanding MAC addresses and ARP helps SOC analysts:

-   Identify local devices.
-   Understand IP-to-MAC relationships.
-   Investigate unknown devices.
-   Recognize unexpected ARP changes.
-   Troubleshoot local communication problems.
-   Investigate possible ARP-related security events.
-   Understand network traffic at Layer 2.

------------------------------------------------------------------------

# ⚡ Quick Revision

  Concept         Simple Meaning
  --------------- ------------------------------------------------------------
  MAC Address     Local hardware/interface identity
  MAC Size        48 bits / 6 bytes
  IP Address      Logical network address
  ARP             Finds MAC address for an IPv4 address on the local network
  ARP Request     "Who has this IP?"
  ARP Reply       "That IP is at this MAC."
  ARP Cache       Stores recently learned IP-to-MAC mappings
  Broadcast MAC   `FF:FF:FF:FF:FF:FF`
  GARP            Announces or confirms a device's own IP/MAC mapping
  Proxy ARP       A device responds to ARP on behalf of another device
  IPv6            Uses NDP instead of ARP

------------------------------------------------------------------------

# 🧠 Remember Like This

``` text
IP = WHERE?

MAC = WHO?

ARP = HOW DO I FIND THE MAC?
```

> **"IP tells me where the device is, MAC identifies it locally, and ARP
> connects the two."**

------------------------------------------------------------------------

# 📚 What's Next?

Next, we move from **local device identification** to **logical
addressing**.

➡️ **03 - IP Addresses**

We will learn:

-   IPv4
-   IPv6
-   Public vs Private IPs
-   Network vs Host portions
-   Static vs Dynamic IPs
-   Special IP addresses
-   How IP addresses are used for routing
-   Why IP addresses matter in cybersecurity

------------------------------------------------------------------------

# 🏁 Chapter Summary

``` text
MAC Address
     ↓
Identifies a network interface locally
     ↓
IP Address
     ↓
Provides logical addressing
     ↓
ARP
     ↓
Finds the MAC address associated with an IPv4 address
     ↓
ARP Cache
     ↓
Stores the learned IP ↔ MAC mapping
     ↓
Ethernet/Wi-Fi Communication
```

> **MAC identifies. IP addresses. ARP resolves.**
