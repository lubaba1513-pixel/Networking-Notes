# 🧩 Subnetting

> *"Subnetting means dividing one big network into smaller, more manageable networks."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what subnetting means.
- Understand why subnetting is useful.
- Understand what a subnet mask does.
- Read the basic 1s and 0s rule.
- Recognize common subnet masks.
- Understand the basic idea of the AND operation.
- Understand CIDR notation.
- Perform a very simple subnet calculation.

---

# 📖 What is Subnetting?

**Subnetting** means dividing one network into smaller networks called **subnets**.

Think of a large building:

```text
🏢 One Large Building
        ↓
 ┌──────┼──────┐
 ↓      ↓      ↓
HR     IT    Finance
```

Instead of putting everyone into one large network, we can divide the network into smaller sections.

### Simple Example

```text
One Network
192.168.1.0/24

        ↓ Subnetting

Subnet 1 → 192.168.1.0/26
Subnet 2 → 192.168.1.64/26
Subnet 3 → 192.168.1.128/26
Subnet 4 → 192.168.1.192/26
```

You do **not** need to memorize the calculation yet. The important idea is:

> **Subnetting = splitting a network into smaller networks.**

---

# ❓ Why Does Subnetting Matter?

Subnetting can help with:

- 🧩 Organizing large networks
- 🚦 Reducing unnecessary network traffic
- 🔐 Separating groups of devices
- 📊 Using IP addresses more efficiently
- 🛡️ Improving network management and security

Example:

```text
Company Network
       ↓
 ┌─────┼─────┐
 ↓     ↓     ↓
 HR    IT   Finance
```

Each department can have its own subnet.

---

# 🧮 What is a Subnet Mask?

A **subnet mask** tells us which part of an IPv4 address represents the:

- **Network portion**
- **Host portion**

Example:

```text
IP Address:  192.168.1.10
Mask:        255.255.255.0
```

Think of it like a street address:

```text
Network portion = Street / neighborhood
Host portion    = House number
```

So:

```text
192.168.1.10
```

with:

```text
255.255.255.0
```

means:

```text
Network → 192.168.1
Host    → 10
```

---

## How It Works: The 1s and 0s Rule

A subnet mask is made from **1s and 0s** in binary.

### The simple rule:

So, In a subnet mask:
```text
1 = Network portion
0 = Host portion
```

Example:

```text
Subnet Mask:
255.255.255.0

Binary:
11111111.11111111.11111111.00000000
```

Therefore:

```text
11111111.11111111.11111111 | 00000000
<------ Network -----------> | <- Host ->
```

That gives us:

```text
Network = 24 bits
Host    = 8 bits
```

This is why:

```text
255.255.255.0 = /24
```

---

# 📋 Common Subnet Masks

These are useful to recognize:

| Subnet Mask | CIDR | Network Bits | Host Bits |
|---|---:|---:|---:|
| `255.0.0.0` | `/8` | 8 | 24 |
| `255.255.0.0` | `/16` | 16 | 16 |
| `255.255.255.0` | `/24` | 24 | 8 |
| `255.255.255.128` | `/25` | 25 | 7 |
| `255.255.255.192` | `/26` | 26 | 6 |

For now, focus especially on:

```text
/24 = 255.255.255.0
```

---

# 🔢 The "AND" Operation

Don't worry — this sounds harder than it is.

A basic **AND operation** compares the IP address with the subnet mask **bit by bit**.

The simple rule is:

```text
1 AND 1 = 1

Everything else = 0
```

Example:

```text
IP:   11000000
Mask: 11111111
      --------
      11000000
```

Another example:

```text
IP:   00001010
Mask: 00000000
      --------
      00000000
```

The result helps us find the **network address**.

### Easy Way to Remember

```text
IP Address
    +
Subnet Mask
    ↓
  AND
    ↓
Network Address
```

You do not need to perform large binary calculations yet. First understand what the AND operation is used for.

---

# 📝 What is CIDR Notation?

**CIDR** stands for **Classless Inter-Domain Routing**.

CIDR gives us a shorter way to write an IP address and subnet mask.

Instead of:

```text
192.168.1.10
255.255.255.0
```

we can write:

```text
192.168.1.10/24
```

The `/24` means:

```text
24 bits = Network portion
8 bits  = Host portion
```

Because IPv4 has 32 bits:

```text
32 - 24 = 8 host bits
```

### Remember

```text
/24 → 24 network bits
/25 → 25 network bits
/26 → 26 network bits
```

As the CIDR number increases, **more bits are used for the network** and fewer are available for hosts.

---

# 🧮 Simple Subnet Calculation

Let's use a very simple example:

```text
IP Address: 192.168.1.10/24
```

### Step 1 — Look at `/24`

```text
/24 = 24 network bits
```

So there are:

```text
32 - 24 = 8 host bits
```

### Step 2 — Find the subnet mask

```text
/24 = 255.255.255.0
```

### Step 3 — Find the network address

The last 8 bits are the host portion.

Our IP is:

```text
192.168.1.10
```

The network address is:

```text
192.168.1.0
```

So:

```text
IP Address:     192.168.1.10
Subnet Mask:    255.255.255.0
Network:        192.168.1.0
```

### 🧠 Think of It Like This

```text
192.168.1.10
^^^^^^^^^^^  ^^^
 Network     Host
```

For `/24`:

```text
192.168.1 | .10
 Network  | Host
```

---

# 🔍 Another Easy Example

```text
IP:   192.168.1.25/24
```

Because `/24` means the first three octets are the network portion:

```text
Network → 192.168.1
Host    → 25
```

Therefore:

```text
Network Address = 192.168.1.0
```

Both of these devices:

```text
192.168.1.10/24
192.168.1.25/24
```

belong to the same network:

```text
192.168.1.0/24
```

---

# 🛡️ Why SOC Analysts Should Learn Subnetting

Subnetting helps SOC analysts understand **where devices belong in a network**.

For example:

```text
192.168.1.10
        ↓
192.168.1.0/24
        ↓
Local Network
```

It can help when:

- Reading firewall logs
- Investigating network traffic
- Understanding IP ranges
- Identifying internal networks
- Investigating suspicious communication

---

# ⚡ Quick Revision

| Concept | Simple Meaning |
|---|---|
| **Subnetting** | Dividing a network into smaller networks |
| **Subnet** | A smaller network |
| **Subnet Mask** | Separates network and host portions |
| **1 in Mask** | Network portion |
| **0 in Mask** | Host portion |
| **AND** | Helps calculate the network address |
| **CIDR** | Short notation such as `/24` |
| `/24` | 24 network bits + 8 host bits |

---

# 🧠 Remember Like This

```text
Subnetting = Split a big network

Subnet Mask = Shows network vs host

1 = Network
0 = Host

CIDR /24 = 24 network bits

AND = Helps find the network address
```

> **"Subnetting is simply dividing a big network into smaller, organized networks."**

---

# 📚 What's Next?

➡️ **07 - NAT**

Next, we will learn how **NAT (Network Address Translation)** allows private networks to communicate with the public Internet.
