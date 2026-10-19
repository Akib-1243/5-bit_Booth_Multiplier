# 5-bit Booth Multiplier

A 5-bit signed multiplier based on **Booth's algorithm**. This project focuses on efficient multiplication of two 5-bit two's-complement numbers using arithmetic shift-and-add/subtract operations.

## Overview

Booth multiplication reduces the number of addition operations by encoding runs of 1s in the multiplier.
For 5-bit inputs:

- **Multiplicand (M):** 5-bit signed value
- **Multiplier (Q):** 5-bit signed value
- **Product (P):** 10-bit signed value

## Booth Algorithm (Radix-2)

Initialize:

- `A = 0` (accumulator)
- `Q = multiplier`
- `M = multiplicand`
- `Q-1 = 0`
- Iteration count = 5

For each iteration:

1. Check `(Q0, Q-1)`
   - `01` → `A = A + M`
   - `10` → `A = A - M`
   - `00` or `11` → no operation
2. Perform arithmetic right shift on the combined register `[A, Q, Q-1]`
3. Repeat until all 5 iterations are complete

Final product is the combined value of `[A, Q]` (10 bits).

## Example

Multiply `+7` by `-3` (5-bit two's complement):

- `M = 00111` (+7)
- `Q = 11101` (-3)
- Expected product: `-21`
- 10-bit result: `1111101011`

## Why Booth Multiplier?

- Efficient for signed multiplication
- Reduces additions/subtractions versus basic shift-add for many bit patterns
- Commonly used in digital design and computer architecture coursework

## Notes

- Inputs and internal operations should be treated as **signed two's-complement** values.
- Ensure arithmetic (sign-preserving) right shifts are used.
- Overflow beyond 10 bits is not represented in the final product.
