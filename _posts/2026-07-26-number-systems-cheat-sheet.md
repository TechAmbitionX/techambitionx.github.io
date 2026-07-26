---
title: "Number Systems Cheat Sheet: Binary, Octal, Decimal, HEX Techniques"
date: "2026-07-26"
categories: [Computer Science, Fundamentals]
tags: [binary, decimal, octal, hexadecimal, number-systems, conversions, cheat-sheet]
description: A reference guide for conversion between Binary, Octal, Decimal, and Hexadecimal—including fractions and arithmetic tricks.
math: true
mermaid: false
image: 
  path: https://github.com/user-attachments/assets/dd354d74-4acf-42d1-a460-2fe7b6bc8430
  alt: "Number Systems Post Thumbnail"

---

# Number Systems Quick Cheat Sheet & Conversions

Look, I can't claim that you'd become ultra prox max Number Systems Master by reading this article, but you should open your eyes, and brain, and open a notebook or something so you can practice. If you've got an exam tomorrow, and this stuff is included in exam, you might want to check it!

---

## 1. Quick Base Reference Table (0–15)

Memorize (or reference) these fundamental equivalences—they make binary, octal, and hex shortcuts almost instantaneous:

| Decimal (Base 10) | Binary (Base 2) | Octal (Base 8) | Hexadecimal (Base 16) |
| :---: | :---: | :---: | :---: |
| **0** | `0000₂` | `0₈` | **0₁₆** |
| **1** | `0001₂` | `1₈` | **1₁₆** |
| **2** | `0010₂` | `2₈` | **2₁₆** |
| **3** | `0011₂` | `3₈` | **3₁₆** |
| **4** | `0100₂` | `4₈` | **4₁₆** |
| **5** | `0101₂` | `5₈` | **5₁₆** |
| **6** | `0110₂` | `6₈` | **6₁₆** |
| **7** | `0111₂` | `7₈` | **7₁₆** |
| **8** | `1000₂` | `10₈` | **8₁₆** |
| **9** | `1001₂` | `11₈` | **9₁₆** |
| **10** | `1010₂` | `12₈` | **A₁₆** |
| **11** | `1011₂` | `13₈` | **B₁₆** |
| **12** | `1100₂` | `14₈` | **C₁₆** |
| **13** | `1101₂` | `15₈` | **D₁₆** |
| **14** | `1110₂` | `16₈` | **E₁₆** |
| **15** | `1111₂` | `17₈` | **F₁₆** |

---

## 🔄 2. Complete Inter-System Conversions (All 12 Combinations)

To convert smoothly between any base, pick your starting base below and follow the direct rule.

```
       ┌──────────┐
  ┌───>│ Decimal  │<───┐
  │    └────┬─────┘    │
  │         │          │
  v         v          v
┌───┐    ┌──────┐    ┌───┐
│Oct│<-->│Binary│<-->│Hex│
└───┘    └──────┘    └───┘
```

---

### A. Conversions FROM Binary (Base 2)

#### 1. Binary ➔ Octal (Group by 3s)
* **The Trick:** Group bits into sets of **3** from **right to left**. Pad with leading zeros on the left if needed.
* **Example:** Convert `101110₂` to Octal.
  * Grouping: `101` | `110`
  * Math (Weights 4-2-1): $(4+0+1)$ | $(4+2+0) \rightarrow 5$ | $6$
  * **Result:** `56₈`

#### 2. Binary ➔ Hexadecimal (Group by 4s)
* **The Trick:** Group bits into sets of **4** from **right to left**. Use weights **8-4-2-1**.
* **Example:** Convert `11010110₂` to Hex.
  * Grouping: `1101` | `0110`
  * Math: $(8+4+0+1) = 13 \text{ (D)}$ | $(0+4+2+0) = 6$
  * **Result:** `D6₁₆`

#### 3. Binary ➔ Decimal (Positional Expansion)
* **The Trick:** Multiply each bit by $2^\text{position}$ (starting at index 0 from the right).
* **Example:** Convert `1101₂` to Decimal.
  * $1(2^3) + 1(2^2) + 0(2^1) + 1(2^0) = 8 + 4 + 0 + 1$
  * **Result:** `13₁₀`

---

### B. Conversions FROM Decimal (Base 10)

#### 4. Decimal ➔ Binary (Successive Division by 2)
* **The Trick:** Repeatedly divide by 2. Read remainders **from bottom to top (last remainder is MSB)**.
* **Example:** Convert `25₁₀` to Binary.

```
2 │ 25
2 │ 12    1
2 │  6    0
2 │  3    0
2 │  1    1
     0    1
```

Read remainders **bottom → top**: `1 1 0 0 1`

> **Fast Alternative:** Subtract the largest power of 2 that fits!  
> $25 = 16 + 8 + 1 \rightarrow (2^4 + 2^3 + 2^0) \rightarrow$ `11001₂`.
{: .prompt-tip }

#### 5. Decimal ➔ Octal (Successive Division by 8)
* **Example:** Convert `175₁₀` to Octal.
  * $175 \div 8 = 21$, remainder **7**
  * $21 \div 8 = 2$, remainder **5**
  * $2 \div 8 = 0$, remainder **2**
  * **Result:** Read upwards $\rightarrow$ `257₈`

#### 6. Decimal ➔ Hexadecimal (Successive Division by 16)
* **Example:** Convert `438₁₀` to Hex.
  * $438 \div 16 = 27$, remainder **6**
  * $27 \div 16 = 1$, remainder **11 (B)**
  * $1 \div 16 = 0$, remainder **1**
  * **Result:** Read upwards $\rightarrow$ `1B6₁₆`

---

### C. Conversions FROM Octal (Base 8)

#### 7. Octal ➔ Binary (3-Bit Expansion)
* **The Trick:** Expand every single octal digit into its **3-bit binary code**.
* **Example:** Convert `72₈` to Binary.
  * $7 \rightarrow$ `111`
  * $2 \rightarrow$ `010`
  * **Result:** `111010₂`

#### 8. Octal ➔ Hexadecimal (Bridge via Binary)
* **Golden Rule:** **Never go through Decimal!** Use Binary as your middle step.
* **Example:** Convert `175₈` to Hex.
  1. Octal to Binary: $1 \to 001$, $7 \to 111$, $5 \to 101 \rightarrow$ `001111101₂`
  2. Regroup into 4-bit sets (right to left): `0011` | `1101`
  3. Map 4-bit sets to Hex: `0011` = **3**, `1101` = **D**
  * **Result:** `3D₁₆`

#### 9. Octal ➔ Decimal (Positional Expansion)
* **Example:** Convert `357₈` to Decimal.
  * $3(8^2) + 5(8^1) + 7(8^0) = 3(64) + 5(8) + 7(1) = 192 + 40 + 7$
  * **Result:** `239₁₀`

---

### D. Conversions FROM Hexadecimal (Base 16)

#### 10. Hex ➔ Binary (4-Bit Expansion)
* **The Trick:** Expand each hex character into a **4-bit binary block**.
* **Example:** Convert `3F₁₆` to Binary.
  * $3 \rightarrow$ `0011`
  * $\text{F (15)} \rightarrow$ `1111`
  * **Result:** `00111111₂`

#### 11. Hex ➔ Octal (Bridge via Binary)
* **The Trick:** Expand Hex to 4-bit Binary, then regroup into 3-bit blocks for Octal.
* **Example:** Convert `A5₁₆` to Octal.
  1. Hex to Binary: $\text{A (10)} \to 1010$, $5 \to 0101 \rightarrow$ `10100101₂`
  2. Regroup by 3s (right to left): `010` | `100` | `101`
  3. Convert to Octal: `010` = **2**, `100` = **4**, `101` = **5**
  * **Result:** `245₈`

#### 12. Hex ➔ Decimal (Positional Expansion)
* **Example:** Convert `2A3₁₆` to Decimal.
  * $2(16^2) + \text{A}(16^1) + 3(16^0) = 2(256) + 10(16) + 3(1)$
  * $512 + 160 + 3$
  * **Result:** `675₁₀`

---

## 3. Handling Fractional Numbers

Converting numbers with radix points (fractions) follows systematic positional rules.

---

### A. Non-Decimal Fractions ➔ Decimal (Positional Expansion)

Positions to the **right** of the point use negative powers ($Base^{-1}, Base^{-2}, Base^{-3}, \dots$).

#### 1. Binary Fraction ➔ Decimal
* **Weights:** $2^{-1} = 0.5$, $2^{-2} = 0.25$, $2^{-3} = 0.125$, $2^{-4} = 0.0625$
* **Example:** Convert `0.1011₂` to Decimal.

$$
0.1011_2 = 1(2^{-1}) + 0(2^{-2}) + 1(2^{-3}) + 1(2^{-4}) = 0.5 + 0 + 0.125 + 0.0625 = \mathbf{0.6875_{10}}
$$

#### 2. Octal Fraction ➔ Decimal
* **Weights:** $8^{-1} = 0.125$, $8^{-2} = 0.015625$, $8^{-3} = 0.001953125$
* **Example:** Convert `0.34₈` to Decimal.

$$
0.34_8 = 3(8^{-1}) + 4(8^{-2}) = 3(0.125) + 4(0.015625) = 0.375 + 0.0625 = \mathbf{0.4375_{10}}
$$

#### 3. Hexadecimal Fraction ➔ Decimal
* **Weights:** $16^{-1} = 0.0625$, $16^{-2} = 0.00390625$
* **Example:** Convert `0.A4₁₆` to Decimal.

$$
0.\text{A}4_{16} = 10(16^{-1}) + 4(16^{-2}) = 10(0.0625) + 4(0.00390625) = 0.625 + 0.015625 = \mathbf{0.640625_{10}}
$$

---

### B. Decimal Fractions ➔ Other Bases (Repeated Multiplication)

Multiply the fractional part by the **target base**. The integer part of each result becomes the next digit — keep multiplying the *remaining* fractional part until it hits zero (or you have enough digits).

#### 1. Decimal Fraction ➔ Binary

Convert `0.625₁₀` to Binary:

| Step | Multiplication | Digit Extracted | Remaining Fraction |
| :---: | :---: | :---: | :---: |
| 1 | 0.625 × 2 = 1.25 | **1** | 0.25 |
| 2 | 0.25 × 2 = 0.50 | **0** | 0.50 |
| 3 | 0.50 × 2 = 1.00 | **1** | 0.00 (Stop) |

**Result:** Read top-to-bottom → `0.101₂`

#### 2. Decimal Fraction ➔ Octal

Convert `0.4375₁₀` to Octal:

| Step | Multiplication | Digit Extracted | Remaining Fraction |
| :---: | :---: | :---: | :---: |
| 1 | 0.4375 × 8 = 3.50 | **3** | 0.50 |
| 2 | 0.50 × 8 = 4.00 | **4** | 0.00 (Stop) |

**Result:** Read top-to-bottom → `0.34₈`

#### 3. Decimal Fraction ➔ Hexadecimal

Convert `0.640625₁₀` to Hex:

| Step | Multiplication | Digit Extracted | Remaining Fraction |
| :---: | :---: | :---: | :---: |
| 1 | 0.640625 × 16 = 10.25 | **A (10)** | 0.25 |
| 2 | 0.25 × 16 = 4.00 | **4** | 0.00 (Stop) |

**Result:** Read top-to-bottom → `0.A4₁₆`

---

### C. Inter-Base Fractional Shortcuts (Binary Bridge)

> **Crucial Rule for Fractional Grouping:** Group digits **left-to-right** starting directly from the decimal point. Append trailing zeros on the right end to fill out incomplete groups.
{: .prompt-warning }

#### 1. Binary Fraction ➔ Octal & Hex

**Binary to Octal** (group by 3s, left-to-right):

| Binary | Grouped | Octal Digits | Result |
| :---: | :---: | :---: | :---: |
| `0.1011₂` | `101` \| `100` (padded with `00`) | 5, 4 | `0.54₈` |

**Binary to Hex** (group by 4s, left-to-right):

| Binary | Grouped | Hex Digit | Result |
| :---: | :---: | :---: | :---: |
| `0.1011₂` | `1011` | B (11) | `0.B₁₆` |

#### 2. Octal Fraction ↔ Hexadecimal Fraction

Always convert through Binary using bit expansion.

**Example:** Convert `0.34₈` to Hex.
1. Expand each digit to 3-bit binary: $3 \to 011$, $4 \to 100 \rightarrow$ `0.011100₂`
2. Regroup into 4-bit blocks left-to-right: `0111` | `0000`
3. Map 4-bit blocks to Hex: `0111` = **7**

**Result:** `0.7₁₆`

---

## 4. Quick Arithmetic Rules

### Binary Addition
* $0 + 0 = 0$
* $0 + 1 = 1$
* $1 + 1 = 0$ *(Carry 1)*
* $1 + 1 + 1 = 1$ *(Carry 1)*

### Binary Subtraction (2's Complement Shortcut)
Instead of borrowing across multiple zeros, convert $A - B$ into $A + (\text{2's complement of } B)$:

1. **1's Complement:** Invert all bits of $B$ ($0 \to 1, 1 \to 0$).
2. **2's Complement:** Add `1` to 1's Complement.
3. **Add $A + \text{2's Complement}$**, then discard the overflow bit on the far left.

* **Example:** Calculate `1101₂ - 0100₂` ($13 - 4 = 9$):
  1. 1's Complement of `0100₂` = `1011₂`
  2. 2's Complement = `1011₂ + 1` = `1100₂`
  3. Add: `1101₂ + 1100₂` = `110101₂`
  4. Drop left bit $\rightarrow$ `1001₂` ($9_{10}$)

### Hexadecimal Addition
Add digits like normal decimal numbers. If the sum is **16 or greater**, subtract **16** and carry **1** to the next column.

* **Example:** `8B₁₆ + 4A₁₆`
  * Right Column: $\text{B (11)} + \text{A (10)} = 21$.
    * Since $21 \ge 16$: $21 - 16 = \mathbf{5}$ (Carry **1**).
  * Left Column: $8 + 4 + 1 \text{ (carry)} = 13 \rightarrow \mathbf{D}$.
  * **Result:** `D5₁₆`

---

## Key Takeaways

1. **Base 2 (Binary):** Core logic language. 3-bit blocks map to Octal; 4-bit blocks map to Hex.
2. **Base 8 (Octal):** $2^3 = 8$. Useful for unix file permissions (`chmod 755`).
3. **Base 16 (Hex):** $2^4 = 16$. Great for condensed binary views (bytes, color codes, memory addresses).
4. **Octal ↔ Hex:** Skip decimal entirely. Route through Binary blocks instead.

---

### Disclaimer
If you find any issues or typos in this article, please feel free to reach out or leave a message!

(btw, there was some pain making this whole article, markdown issue!)
