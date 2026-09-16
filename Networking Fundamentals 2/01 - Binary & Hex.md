# 🔢 Binary & Hex

> *"Networking looks complicated until you understand the numbers behind
> it."*

# 🎯 Learning Objectives

After this chapter, you will be able to:

-   Understand why number systems matter in networking.
-   Understand bits and bytes.
-   Understand how binary works.
-   Understand binary place values.
-   Convert simple decimal numbers to binary.
-   Understand hexadecimal (hex).
-   Understand why hex is useful in networking.

------------------------------------------------------------------------

# 🌐 Why Number Systems Matter in Networking?

When we work with networks, we see numbers everywhere:

-   IP addresses
-   MAC addresses
-   Subnet masks
-   IPv6 addresses
-   Network data

But computers store and process information using **bits: 0 and 1**.

Humans normally use **decimal (base 10)**, while computers use **binary
(base 2)**.

Hexadecimal (base 16) gives us a shorter way to write binary
information.

### 💡 Think of it like this

``` text
Decimal       → Easy for humans
Binary        → Used by computers
Hexadecimal   → Shorter way to write binary
```

For example:

``` text
Decimal:  10
Binary:  1010
Hex:      A
```

The value is the same. We are simply writing it in different number
systems.

------------------------------------------------------------------------

# 🟢 The Language of On and Off

Computers use electricity and electronic signals.

At a very basic level, we can think of two states:

``` text
ON  → 1
OFF → 0
```

These two values are called **binary digits**, or **bits**.

So binary uses only:

``` text
0 and 1
```

### 🌍 Simple Example

Imagine a light switch:

``` text
OFF → 0
ON  → 1
```

Now imagine having many switches together:

``` text
1 0 1 1 0 0 1 0
```

This is a binary number.

------------------------------------------------------------------------

# 💾 Bits and Bytes: The Building Blocks

## 🔹 What is a Bit?

A **bit** is the smallest unit of digital information.

It can have only two values:

``` text
0 or 1
```

Example:

``` text
1 bit → 1
```

------------------------------------------------------------------------

## 🔹 What is a Byte?

A **byte** is a group of **8 bits**.

``` text
1 byte = 8 bits
```

Example:

``` text
10110010
```

That is **8 bits = 1 byte**.

### 🧠 Easy Memory Trick

``` text
bit  → one 0 or 1
byte → eight bits
```

------------------------------------------------------------------------

# 🔢 How Binary Place Values Work

This is one of the most important ideas to understand.

In decimal, place values are based on powers of **10**.

For example:

``` text
345

3 × 100
4 × 10
5 × 1
```

So:

``` text
345 = 300 + 40 + 5
```

Binary works in the same way, but instead of powers of 10, it uses
powers of **2**.

For an 8-bit binary number:

``` text
128  64  32  16  8  4  2  1
```

These are the binary place values.

They come from:

``` text
2⁷ = 128
2⁶ = 64
2⁵ = 32
2⁴ = 16
2³ = 8
2² = 4
2¹ = 2
2⁰ = 1
```

### 💡 The Important Rule

Each position can be:

``` text
1 → use the value
0 → do not use the value
```

For example:

``` text
Binary:

1  0  1  0  0  0  0  1

128 64 32 16 8 4 2 1
```

We use the values where there is a `1`:

``` text
128 + 32 + 1 = 161
```

So:

``` text
10100001 = 161
```

------------------------------------------------------------------------

# 🧩 A Simple Way to Understand It

Think of each binary position as a switch.

``` text
128  64  32  16  8  4  2  1
 ↓    ↓    ↓   ↓   ↓  ↓  ↓  ↓
 1    0    1   0   0  0  0  1
```

The `1`s mean:

``` text
128 → ON
64  → OFF
32  → ON
16  → OFF
8   → OFF
4   → OFF
2   → OFF
1   → ON
```

Therefore:

``` text
128 + 32 + 1 = 161
```

------------------------------------------------------------------------

# 🔄 From Decimal to Binary

There are different ways to convert decimal to binary.

For networking, one easy method is:

> **Check the binary place values from left to right.**

Let's convert **173** to binary.

Our place values are:

``` text
128  64  32  16  8  4  2  1
```

### Step 1 --- Check 128

Can 128 fit into 173?

``` text
173 ≥ 128 → YES
```

So write `1`.

Subtract:

``` text
173 - 128 = 45
```

### Step 2 --- Check 64

Can 64 fit into 45?

``` text
45 ≥ 64 → NO
```

Write `0`.

The remainder stays:

``` text
45
```

### Step 3 --- Check 32

``` text
45 ≥ 32 → YES
```

Write `1`.

``` text
45 - 32 = 13
```

### Step 4 --- Check 16

``` text
13 ≥ 16 → NO
```

Write `0`.

Remainder:

``` text
13
```

### Step 5 --- Check 8

``` text
13 ≥ 8 → YES
```

Write `1`.

``` text
13 - 8 = 5
```

### Step 6 --- Check 4

``` text
5 ≥ 4 → YES
```

Write `1`.

``` text
5 - 4 = 1
```

### Step 7 --- Check 2

``` text
1 ≥ 2 → NO
```

Write `0`.

### Step 8 --- Check 1

``` text
1 ≥ 1 → YES
```

Write `1`.

``` text
1 - 1 = 0
```

Now collect the bits:

``` text
128 64 32 16 8 4 2 1
 1   0  1  0  1 1 0 1
```

Therefore:

``` text
173 = 10101101
```

### 🧠 Remember

``` text
YES → 1 → subtract
NO  → 0 → leave the remainder
```

------------------------------------------------------------------------

# 🔁 Binary Back to Decimal

Now let's do the opposite.

Convert:

``` text
10101101
```

to decimal.

Write the place values:

``` text
128  64  32  16  8  4  2  1
 1    0   1   0  1  1  0  1
```

Take only the values with `1`:

``` text
128 + 32 + 8 + 4 + 1
```

Add them:

``` text
128 + 32 = 160
160 + 8  = 168
168 + 4  = 172
172 + 1  = 173
```

So:

``` text
10101101 = 173
```

### 🔄 Therefore

``` text
Decimal → Binary
173     → 10101101

Binary → Decimal
10101101 → 173
```

------------------------------------------------------------------------

# 🧠 Quick Binary Reference

For an 8-bit number:

``` text
128  64  32  16  8  4  2  1
```

Some useful values:

    Decimal Binary
  --------- ------------
          0 `00000000`
          1 `00000001`
          2 `00000010`
          4 `00000100`
          8 `00001000`
         10 `00001010`
         15 `00001111`
         16 `00010000`
         32 `00100000`
         64 `01000000`
        128 `10000000`
        255 `11111111`

### 💡 Important Networking Fact

An IPv4 address has **4 parts**, called **octets**.

Each octet contains **8 bits**.

``` text
IPv4:

192 . 168 . 1 . 10
 ↓     ↓    ↓    ↓
8-bit 8-bit 8-bit 8-bit
```

Therefore, each IPv4 octet can have a value from:

``` text
0 → 255
```

You will use this knowledge later when learning **IP addressing and
subnetting**.

------------------------------------------------------------------------

# 🟣 Hexadecimal System

**Hexadecimal**, usually called **hex**, is a number system with **16
symbols**.

Decimal uses:

``` text
0 1 2 3 4 5 6 7 8 9
```

Hex uses:

``` text
0 1 2 3 4 5 6 7 8 9 A B C D E F
```

The letters represent values from 10 to 15:

  Hex     Decimal
  ----- ---------
  `0`           0
  `1`           1
  `2`           2
  `3`           3
  `4`           4
  `5`           5
  `6`           6
  `7`           7
  `8`           8
  `9`           9
  `A`          10
  `B`          11
  `C`          12
  `D`          13
  `E`          14
  `F`          15

### 🧠 Easy Memory Trick

After `9`, hex does not start again.

It continues:

``` text
9 → A → B → C → D → E → F
```

So:

``` text
A = 10
B = 11
C = 12
D = 13
E = 14
F = 15
```

------------------------------------------------------------------------

# 🤔 Why Do We Need Hex?

Binary can become very long.

For example:

``` text
Binary:
10100001
```

Hex can write the same value as:

``` text
A1
```

Much shorter!

That's why hex is useful for things such as:

-   MAC addresses
-   IPv6 addresses
-   Packet/data representations
-   Memory and debugging information

------------------------------------------------------------------------

# 🔗 The Magic Connection: 1 Hex Digit = 4 Bits

This is the most useful thing to remember about hex.

One hex digit represents exactly **4 binary bits**.

For example:

``` text
A = 1010
```

And:

``` text
F = 1111
```

Here is the complete mapping:

  Hex     Decimal Binary
  ----- --------- --------
  `0`           0 `0000`
  `1`           1 `0001`
  `2`           2 `0010`
  `3`           3 `0011`
  `4`           4 `0100`
  `5`           5 `0101`
  `6`           6 `0110`
  `7`           7 `0111`
  `8`           8 `1000`
  `9`           9 `1001`
  `A`          10 `1010`
  `B`          11 `1011`
  `C`          12 `1100`
  `D`          13 `1101`
  `E`          14 `1110`
  `F`          15 `1111`

### ⭐ The Golden Rule

``` text
1 hex digit = 4 bits
2 hex digits = 8 bits = 1 byte
```

For example:

``` text
A1
```

Split it:

``` text
A → 1010
1 → 0001
```

Therefore:

``` text
A1 = 10100001
```

------------------------------------------------------------------------

# 🌍 Real Networking Example: MAC Address

A MAC address commonly looks like:

``` text
A1:B2:C3:DD:EE:FF
```

Each pair is two hex digits:

``` text
A1 : B2 : C3 : DD : EE : FF
```

Each pair represents **one byte (8 bits)**.

For example:

``` text
A1
```

means:

``` text
A = 1010
1 = 0001

A1 = 10100001
```

So hex makes a long binary sequence much easier for humans to read.

------------------------------------------------------------------------

# 🔄 Binary ↔ Hex

## Binary → Hex

Take:

``` text
11010010
```

Split it into groups of 4:

``` text
1101 0010
```

Convert each group:

``` text
1101 = D
0010 = 2
```

Therefore:

``` text
11010010 = D2
```

------------------------------------------------------------------------

## Hex → Binary

Take:

``` text
F0
```

Convert each hex digit separately:

``` text
F = 1111
0 = 0000
```

Therefore:

``` text
F0 = 11110000
```

### 🧠 Remember

> **Binary → group into 4**\
> **Each group → one hex digit**

------------------------------------------------------------------------

# 🛡️ Why This Matters for Cybersecurity

As a SOC analyst or cybersecurity learner, you will see binary and
hexadecimal in many places.

For example:

-   IP addresses and subnet masks use binary concepts.
-   MAC addresses are commonly written in hex.
-   IPv6 addresses use hexadecimal.
-   Packet data may be displayed in hex.
-   Security tools may show raw data in hexadecimal.

You don't need to memorize everything at once.

The most important things to remember are:

``` text
Binary → 0 and 1
1 byte → 8 bits

8-bit place values:
128 64 32 16 8 4 2 1

Hex → 0-9 and A-F
1 hex digit → 4 bits
2 hex digits → 1 byte
```

------------------------------------------------------------------------

# ⚡ Quick Revision

### Binary

``` text
Base: 2
Symbols: 0, 1
Used for: computer data and network calculations
```

### Decimal

``` text
Base: 10
Symbols: 0-9
Used for: human-readable numbers and IPv4 addresses
```

### Hexadecimal

``` text
Base: 16
Symbols: 0-9, A-F
Used for: MAC addresses, IPv6, and compact binary representation
```

### Most Important Relationships

``` text
1 bit   = 0 or 1
8 bits  = 1 byte
4 bits  = 1 hex digit
2 hex digits = 1 byte
```

------------------------------------------------------------------------

# 🧠 Remember It Like This

``` text
                 NUMBER SYSTEMS
                       │
          ┌────────────┼────────────┐
          ↓            ↓            ↓
       Decimal       Binary        Hex
        Base 10      Base 2       Base 16
       0-9           0-1          0-F
          │            │            │
       Humans       Computers    Shorter binary
```

And remember:

> **Binary is made of bits. Hex is a shorter way to write groups of
> binary bits.**

------------------------------------------------------------------------

# 📚 What's Next?

Now that you understand binary and hexadecimal, the next networking
topics can build on these ideas:

**IP Addressing → Subnet Masks → Subnetting**

That's where binary starts becoming really useful in networking.
