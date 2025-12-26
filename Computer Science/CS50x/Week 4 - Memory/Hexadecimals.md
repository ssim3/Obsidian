# Hexadecimal (Base 16) — CS50 Week 4

## What is Hexadecimal?
- A **number system** that uses base 16 instead of base 10.
- Digits: `0–9` plus `A–F`  
  - `A = 10`, `B = 11`, `C = 12`, `D = 13`, `E = 14`, `F = 15`

## Why Use Hexadecimal?
- Computers store everything in **binary (base 2)**, which is hard to read.
- Hexadecimal provides a **shorthand for binary**:
  - **4 binary bits = 1 hex digit**
- Easier to represent:
  - Memory addresses
  - Colors (e.g., `#FF0000`)
  - Machine code & ASCII

## Conversions
- **Decimal → Hex**: Divide by 16, note remainders.
- **Binary → Hex**: Group into 4-bit chunks.
  - Example: `10101100 (binary)`  
    → `1010 1100`  
    → `A C`  
    → `0xAC (hex)`

## Notation
- Hex values often prefixed with `0x`
  - Example: `0xFF = 255 (decimal)`

## Key Idea
- Hexadecimal is just a **different representation** of the same values.
- It is **human-friendly binary** since each hex digit maps exactly to 4 bits.

## Conversion Table (0–15)

| Decimal | Binary | Hex |
|---------|--------|-----|
| 0       | 0000   | 0   |
| 1       | 0001   | 1   |
| 2       | 0010   | 2   |
| 3       | 0011   | 3   |
| 4       | 0100   | 4   |
| 5       | 0101   | 5   |
| 6       | 0110   | 6   |
| 7       | 0111   | 7   |
| 8       | 1000   | 8   |
| 9       | 1001   | 9   |
| 10      | 1010   | A   |
| 11      | 1011   | B   |
| 12      | 1100   | C   |
| 13      | 1101   | D   |
| 14      | 1110   | E   |
| 15      | 1111   | F   |
