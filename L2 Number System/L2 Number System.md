---
title: Number Systems & Data Representation
markmap:
  colorFreezeLevel: 2
---

# Number Systems & Data Representation

## Number Systems
- **Binary (Base 2)**
  - Bits and Bytes
  - Notation: suffix B, prefix 0b
- **Hexadecimal (Base 16)**
  - Compact form for Binary
  - Symbols: 0-9, A-F
  - Notation: suffix H, prefix 0x
- **Conversions**
  - Decimal to Binary/Hex
  - Binary to Hex (Grouping 4 bits)

## Integer Representation (整数表示)
- **Unsigned Integers**
  - Range: 0 to $2^n - 1$
- **Signed Integers**
  - **Original Code (Sign-Magnitude)**
    - Sign bit: 0 positive, 1 negative
    - Two zeros issue
  - **Inverse Code (Ones Complement)**
    - Negative: Sign bit unchanged, flip others
  - **Complement Code (Twos Complement)**
    - Standard for arithmetic
    - Calculation: Inverse Code + 1
    - Subtraction by addition
  - **Offset Binary (Excess-N)**
    - Used in Floating Point Exponents


## Decimal/Real Representation (小数/实数表示)
- **Fixed Point**
  - Implicit decimal point
  - Limited precision
- **Offset Binary**
  - $[X]_{offset} = X + offset$ (offset = $2^{n-1}$)
  - 相当于补码符号位取反
- **Floating Point (IEEE 754)**
  - Scientific Notation: $F \times r^E$
  - ==**Single Precision (32-bit)**==
    - Sign: 1 bit
    - Exponent: 8 bits (Offset Binary = $X + 2^{n-1} - 1$ = $X + 2^7 - 1$ =  $X + 127$ ) 
    - Fraction: 23 bits (Original Code)
    - Range:
      - $X=(-1)^S \times 1.F \times 2^e = (-1)^S \times 1.F \times 2^{E-127}$
      - Positive number: $ 2^{-126}\times(1+0)$ ~ $ 2^{127}\times(1+1-2^{-23})$
      - Negative number: $ -2^{127}\times(1+1-2^{-23})$ ~ $ -2^{126}\times(1+0)$
  - **Double Precision (64-bit)**
    - Exponent: 11 bits
    - Fraction: 52 bits

## Coding Schemes
- ==**BCD (Binary Coded Decimal)**==
  - ==8421 Code (Natural)==
  - ==2421 Code (1111-2=7,互补)==
  - ==Excess-3 Code (+0011)==
- **Alphanumeric**
  - ASCII (7-bit standard)
  - Chinese (GB2312-80/QW/IN)
  - **Unicode (Universal Set)**
    - represent all the symbols used in any language
    - UTF-8 (Variable length 1-4 bytes)
    - UTF-16 (2 or 4 bytes)
- **Gray Code**
  - ==Adjacent numbers differ by 1 bit==

## Error Control
- **Concepts**
  - Bit flips (Noise)
  - Hamming Distance ==(Diff bits count)==:minimum number of errors
- **Types of Error Detection**
  - **Detection Only**
    - Parity Check
      - Odd Parity
      - Even Parity
      - Improved:Horizontal/Vertical
  - **Correction**
    - **Hamming Code (SEC)**
      - Redundant bits at powers of 2
      - ==Formula: $2^P \ge n + P + 1$==
  - **CRC (Cyclic Redundancy Check)**
    - Modulo-2 Division
    - XOR Operation (no carry)