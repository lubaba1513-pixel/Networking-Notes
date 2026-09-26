# 🌐 DNS

> *"DNS is like the Internet's phonebook: it turns names people understand into addresses computers use."*

# 🎯 Learning Objectives

After completing this chapter, you will be able to:

- Understand what DNS is.
- Explain why DNS is important.
- Understand how a DNS lookup works.
- Differentiate between recursive and iterative queries.
- Understand DNS caching and TTL.
- Recognize common DNS record types.
- Know when different DNS records are used.

---

# 📖 What is DNS?

**DNS** stands for **Domain Name System**.

DNS translates human-friendly domain names into IP addresses.

Example:

```text
www.example.com
       ↓
   DNS Lookup
       ↓
93.184.216.34
```

Instead of remembering an IP address, we can use a domain name.

---

# ❓ Why DNS Matters

Without DNS, we would often need to remember IP addresses to reach websites and services.

DNS makes the Internet easier to use.

It helps:

- 🌐 Find websites.
- 📧 Find mail servers.
- 🔗 Connect services using domain names.
- 🛡️ Investigate network activity in cybersecurity.

Simple idea:

```text
Domain Name
     ↓
    DNS
     ↓
 IP Address
     ↓
 Website / Service
```

---

# 🔎 DNS Lookup Process

When you enter a website name, your device needs to find its IP address.

A simplified lookup looks like this:

```text
1. 💻 Your Device
       ↓
2. 🔎 DNS Resolver
       ↓
3. 🌳 Root DNS Server
       ↓
4. 🌐 TLD DNS Server
       ↓
5. 🏠 Authoritative DNS Server
       ↓
6. 📍 IP Address
       ↓
7. 💻 Your Device
```

### Simple Example

You enter:

```text
www.example.com
```

DNS helps find the IP address for that domain.

Your browser can then connect to the server using the IP address.

> **Note:** Caching can make the process much shorter because the answer may already be stored by a DNS resolver or device.

---

# 🔄 Recursive vs Iterative Queries

DNS queries can work in different ways.

| Query Type | Who Makes It | Who Answers | Simple Meaning |
|---|---|---|---|
| **Recursive** | Your device/client asks a resolver | Resolver provides the final answer | "Find the answer for me." |
| **Iterative** | DNS resolver/server | Server may provide an answer or referral | "I don't have it; ask this server." |

### 🟢 Recursive

```text
💻 Client
   ↓
"Find www.example.com for me."
   ↓
🔎 DNS Resolver
   ↓
Final Answer
```

The client expects the resolver to find the answer.

### 🔵 Iterative

```text
DNS Server
   ↓
"I don't have the final answer."
   ↓
"Ask this other DNS server."
```

The querying DNS server follows referrals until it finds the needed information.

---

# ⚡ DNS Caching and TTL

DNS does not need to look up every domain from the beginning every time.

DNS responses can be **cached**.

A cache stores a DNS answer for a period of time.

## What is TTL?

**TTL** stands for **Time To Live**.

It tells DNS caches how long a DNS record can be kept before it should be queried again.

Example:

```text
DNS Record
    ↓
TTL = 3600 seconds
    ↓
Cache for about 1 hour
```

### Why Caching Helps

- ⚡ Faster DNS lookups
- 🌐 Less DNS traffic
- 🔄 Fewer repeated queries

---

# 📋 DNS Record Types

DNS uses different **record types** for different purposes.

| Record Type | Purpose | Example |
|---|---|---|
| **A** | Maps a domain to an IPv4 address | `example.com → 192.0.2.1` |
| **AAAA** | Maps a domain to an IPv6 address | `example.com → 2001:db8::1` |
| **CNAME** | Creates an alias for another domain name | `www.example.com → example.com` |
| **MX** | Specifies mail servers | `example.com → mail.example.com` |
| **TXT** | Stores text information | Verification, SPF information |
| **NS** | Specifies authoritative name servers | `example.com → ns1.example.com` |

---

# 🧩 When to Use Which Record Type?

Think of the records like this:

```text
A      → IPv4 address
AAAA   → IPv6 address
CNAME  → Alias
MX     → Email
TXT    → Text / verification
NS     → Name Server
```

### Example

If you want:

- 🌐 A website to point to an IPv4 address → **A**
- 🌐 A website to point to an IPv6 address → **AAAA**
- 🔗 One domain name to act as an alias for another → **CNAME**
- 📧 Email to reach the correct mail server → **MX**
- 📝 Domain verification or SPF information → **TXT**
- 🏠 To identify authoritative DNS servers → **NS**

---

# 🌍 Real-Life Scenario

You type:

```text
www.example.com
```

Your device asks a DNS resolver for the address.

```text
💻 Device
   ↓
🔎 DNS Resolver
   ↓
📍 IP Address
   ↓
🌐 Web Server
```

The browser can then connect to the web server.

If the resolver already has the answer in its cache, it may return it without performing a new full lookup.

---

# 🛡️ Why SOC Analysts Should Learn DNS

DNS is very important in cybersecurity because network activity often contains DNS requests.

SOC analysts may investigate:

- Suspicious domains
- Unusual DNS requests
- Large numbers of DNS queries
- Failed/NXDOMAIN queries
- DNS tunneling indicators
- Connections to known malicious domains

Example:

```text
Client → DNS Resolver
        ↓
suspicious-domain.example
```

DNS logs can provide useful evidence during an investigation.

---

# ⚡ Quick Revision

| Concept | Simple Meaning |
|---|---|
| **DNS** | Translates domain names to IP addresses |
| **Resolver** | Helps find DNS answers |
| **Recursive Query** | Resolver finds the final answer |
| **Iterative Query** | Server gives an answer or referral |
| **Cache** | Temporarily stores DNS answers |
| **TTL** | How long a cached record can be kept |
| **A** | IPv4 address |
| **AAAA** | IPv6 address |
| **CNAME** | Alias |
| **MX** | Mail server |
| **TXT** | Text/verification information |
| **NS** | Name server |

---

# 🧠 Remember Like This

```text
DNS = Internet Phonebook

A      = IPv4
AAAA   = IPv6
CNAME  = Alias
MX     = Mail
TXT    = Text
NS     = Name Server

TTL = How long the DNS answer can stay in cache
```

> **"Humans use names. Networks use IP addresses. DNS connects the two."**

---

# 📚 What's Next?

➡️ **06 - Subnetting**

Next, we will learn how a network can be divided into smaller networks called **subnets**.
