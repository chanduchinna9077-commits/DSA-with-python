
# 🟡 12. BASIC BIT MANIPULATION — 10 Problems

Because you specifically asked for it earlier.

1. AND
2. OR
3. XOR
4. Check even/odd using bit
5. Check kth bit
6. Set kth bit
7. Clear kth bit
8. Toggle kth bit
9. Count set bits
10. Check power of 2


# 🟦 BASIC BIT MANIPULATION — LOCKED TOPGUN VERSION

We’ll treat **Basic Bit Manipulation** as a focused **10-problem pattern bank**, exactly like Arrays, Strings, Hashing, Searching, Stack, and Pattern Printing.

No advanced bit tricks, no competitive-programming garbage. The goal is to master the **basic operations and patterns that can appear in screening-level DSA**.

## 🔒 Locked Roadmap — 10 Problems

|  # | Problem                                                    | Core Pattern    |
| -: | ---------------------------------------------------------- | --------------- |
|  1 | Check Odd / Even                                           | `n & 1`         |
|  2 | Check / Set / Clear / Toggle a Bit                         | Bit masking     |
|  3 | Check if Number is Power of 2                              | `n & (n-1)`     |
|  4 | Count Set Bits                                             | Brian Kernighan |
|  5 | Find Number of Set Bits / Hamming Weight                   | Bit counting    |
|  6 | Find Unique Number                                         | XOR             |
|  7 | Find Missing Number                                        | XOR             |
|  8 | Swap Two Numbers Using XOR                                 | XOR             |
|  9 | Get Lowest Set Bit                                         | `n & -n`        |
| 10 | Generate / Check Binary Representation with Bit Operations | Shift + Mask    |

### Execution split

```text
Conversation 1 → Problems 1–4
Conversation 2 → Problems 5–8
Conversation 3 → Problems 9–10 + Complete Bit Mastery
```

And for **every problem**, we keep the same locked structure:

1. Problem Statement
2. Problem Theory
3. Pattern Being Tested
4. ELI10 Intuition
5. Example
6. Algorithm — Step-by-Step
7. Python using built-in methods
8. Python without built-in methods
9. Line-by-line explanation
10. Detailed dry run/table
11. Time Complexity
12. Space Complexity
13. Edge Cases
14. Common Mistakes/Traps
15. Pattern Recognition — **When you see X → think Y**

---

# 🧠 FIRST — WHAT IS BIT MANIPULATION?

A computer ultimately represents numbers using **bits**.

A bit can contain only:

```text
0
```

or

```text
1
```

For example:

```text
5
```

in binary is:

```text
101
```

because:

```text
1×4 + 0×2 + 1×1
= 5
```

---

# 🔥 THE 6 OPERATIONS YOU MUST KNOW

These are the foundation.

| Operator | Name        | Example  |
| -------- | ----------- | -------- |
| `&`      | AND         | `5 & 3`  |
| `\|`     | OR          | `5 \| 3` |
| `^`      | XOR         | `5 ^ 3`  |
| `~`      | NOT         | `~5`     |
| `<<`     | Left Shift  | `5 << 1` |
| `>>`     | Right Shift | `5 >> 1` |

---

# 1️⃣ AND — `&`

AND gives `1` only when **both bits are 1**.

```text
1 & 1 = 1
1 & 0 = 0
0 & 1 = 0
0 & 0 = 0
```

Example:

```text
5 = 101
3 = 011
---------
    001
```

Therefore:

```text
5 & 3 = 1
```

### ELI10

AND asks:

> "Are BOTH of you 1?"

---

# 2️⃣ OR — `|`

OR gives `1` when **at least one bit is 1**.

```text
1 | 1 = 1
1 | 0 = 1
0 | 1 = 1
0 | 0 = 0
```

Example:

```text
101
011
---
111
```

Therefore:

```text
5 | 3 = 7
```

---

# 3️⃣ XOR — `^`

XOR gives `1` when the bits are **different**.

```text
1 ^ 1 = 0
1 ^ 0 = 1
0 ^ 1 = 1
0 ^ 0 = 0
```

Example:

```text
101
011
---
110
```

Therefore:

```text
5 ^ 3 = 6
```

### 🔥 XOR properties

These are extremely important:

```text
x ^ x = 0
x ^ 0 = x
```

and XOR is:

```text
a ^ b ^ a = b
```

This is why XOR is useful for finding unique/missing numbers.

---

# 4️⃣ NOT — `~`

NOT flips bits:

```text
0 → 1
1 → 0
```

Python's `~` uses signed integer representation, so don't memorize it as simply "positive bits flip."

The important identity is:

```text
~n = -(n + 1)
```

Example:

```python
~5
```

gives:

```text
-6
```

For TopGun basic DSA, understand the operator but don't over-invest in Python's infinite-width integer representation.

---

# 5️⃣ LEFT SHIFT — `<<`

```python
n << k
```

moves bits left by `k`.

Example:

```text
5 = 101
```

```text
5 << 1
```

becomes:

```text
1010
```

which is:

```text
10
```

For non-overflowing positive integers:

```text
n << 1 ≈ n × 2
```

---

# 6️⃣ RIGHT SHIFT — `>>`

Example:

```text
10 = 1010
```

```text
10 >> 1
```

becomes:

```text
0101
```

which is:

```text
5
```

For non-negative integers:

```text
n >> 1 ≈ n // 2
```

---

# 🔥 THE MOST IMPORTANT BIT MENTAL MODEL

Think of a number as:

```text
[bit][bit][bit][bit][bit]
```

For example:

```text
13 = 1101
```

Positions:

```text
3   2   1   0
↓   ↓   ↓   ↓
1   1   0   1
```

Bit position `0` is the **rightmost bit**.

This is critical for almost every bit-manipulation problem.

---

# 🟦 PROBLEM 1 — CHECK ODD OR EVEN

## 1. Problem Statement

Given an integer `n`, determine whether it is:

```text
Odd
```

or

```text
Even
```

Example:

```text
7 → Odd
8 → Even
```

---

# 2. Problem Theory

Normally you might use:

```python
n % 2
```

But bit manipulation gives us a beautiful shortcut.

Look at binary:

```text
2 = 10
4 = 100
6 = 110
8 = 1000
```

All even numbers end in:

```text
0
```

Odd numbers:

```text
1 = 1
3 = 11
5 = 101
7 = 111
9 = 1001
```

All end in:

```text
1
```

So we can inspect the **last bit**.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
n & 1
```

If:

```text
n & 1 == 1
```

→ Odd.

If:

```text
n & 1 == 0
```

→ Even.

---

# 4. ELI10 Intuition

Imagine the last bit is a tiny switch:

```text
0 → even
1 → odd
```

We use:

```text
& 1
```

to look only at that switch.

Example:

```text
7 = 111
1 = 001
---------
    001
```

Result:

```text
1
```

So 7 is odd.

---

# 5. Example

```text
n = 10
```

Binary:

```text
1010
```

Perform:

```text
1010
0001
----
0000
```

Therefore:

```text
10 & 1 = 0
```

So:

```text
10 is even
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Take `n`.

### Step 2

Perform:

```text
n & 1
```

### Step 3

If result is `1`:

```text
Odd
```

Otherwise:

```text
Even
```

---

# 7. Python Solution — Using Built-in / Normal Method

```python
def check_even_odd(n):

    if n % 2 == 0:
        return "Even"
    else:
        return "Odd"


print(check_even_odd(7))
```

Output:

```text
Odd
```

---

# 8. Python Solution — Bit Manipulation

```python
def check_even_odd_bit(n):

    if n & 1:
        return "Odd"
    else:
        return "Even"


print(check_even_odd_bit(7))
```

Output:

```text
Odd
```

This is the version you need to recognize in a bit-manipulation question.

---

# 9. Line-by-Line Explanation

```python
if n & 1:
```

The expression:

```text
n & 1
```

checks the least significant bit.

If it is:

```text
1
```

the number is odd.

If it is:

```text
0
```

the number is even.

---

# 10. Detailed Dry Run

Take:

```text
n = 13
```

Binary:

```text
13 = 1101
```

Perform:

```text
1101
0001
----
0001
```

Result:

```text
1
```

Therefore:

```text
13 → Odd
```

### Another example

```text
n = 12
```

```text
1100
0001
----
0000
```

Therefore:

```text
12 → Even
```

---

# 11. Time Complexity

Bit operation:

```text
O(1)
```

for normal machine-word integers.

---

# 12. Space Complexity

```text
O(1)
```

---

# 13. Edge Cases

```text
0 → Even
```

Negative numbers also work:

```text
-3 → Odd
-4 → Even
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake

Using:

```python
n & 2
```

to check odd/even.

Wrong.

The least significant bit is:

```text
bit 0
```

and its mask is:

```text
0001
```

Therefore:

```python
n & 1
```

---

# 15. Pattern Recognition

When you see:

> "Check odd/even using bit manipulation"

Immediately think:

```text
n & 1
```

### 🔥 Trigger

```text
Odd / Even
↓
Last bit
↓
AND with 1
```

---

# 🟦 PROBLEM 2 — SET / CLEAR / TOGGLE / CHECK A BIT

This is one of the most important **basic bit-mask patterns**.

---

# 1. Problem Statement

Given:

```text
number n
bit position k
```

perform basic operations on bit `k`:

1. Check bit
2. Set bit
3. Clear bit
4. Toggle bit

---

# 2. Problem Theory

Suppose:

```text
n = 10
```

Binary:

```text
1010
```

Bit positions:

```text
3 2 1 0
1 0 1 0
```

Suppose we want to manipulate:

```text
bit 1
```

We create a mask:

```text
1 << 1
```

which is:

```text
0010
```

This mask lets us target exactly bit 1.

---

# 3. Pattern Being Tested

### 🔥 Bit Masking

The universal mask:

```text
1 << k
```

means:

> Create a number whose kth bit is 1.

---

# 4. ELI10 Intuition

Imagine a row of switches:

```text
0 0 0 0
```

We want to touch only switch #2.

We create:

```text
0 0 1 0
```

That's:

```text
1 << 2
```

Then use different operations to manipulate that switch.

---

# 5. Example

Let:

```text
n = 10
```

Binary:

```text
1010
```

Take:

```text
k = 1
```

Mask:

```text
1 << 1 = 0010
```

---

# 6. Algorithm — Step-by-Step

## A. Check bit

Use:

```text
n & (1 << k)
```

If non-zero:

```text
bit = 1
```

Otherwise:

```text
bit = 0
```

---

## B. Set bit

Use:

```text
n | (1 << k)
```

Setting means:

```text
0 → 1
1 → 1
```

---

## C. Clear bit

Use:

```text
n & ~(1 << k)
```

Clearing means:

```text
1 → 0
0 → 0
```

---

## D. Toggle bit

Use:

```text
n ^ (1 << k)
```

Toggle means:

```text
0 → 1
1 → 0
```

---

# 7. Python — Normal / Built-in Equivalent

For checking:

```python
def check_bit_normal(n, k):
    return (n // (2 ** k)) % 2
```

For basic understanding, this extracts the kth bit mathematically.

---

# 8. Python — Bit Manipulation

```python
def check_bit(n, k):

    mask = 1 << k

    if n & mask:
        return 1
    else:
        return 0


def set_bit(n, k):

    return n | (1 << k)


def clear_bit(n, k):

    return n & ~(1 << k)


def toggle_bit(n, k):

    return n ^ (1 << k)
```

---

# 9. Line-by-Line Explanation

### Mask

```python
mask = 1 << k
```

If:

```text
k = 2
```

then:

```text
1 << 2 = 0100
```

---

### Check

```python
n & mask
```

AND allows us to inspect only bit `k`.

---

### Set

```python
n | mask
```

OR forces that bit to `1`.

---

### Clear

```python
n & ~mask
```

The inverted mask has:

```text
0
```

at position `k`.

AND therefore forces that bit to `0`.

---

### Toggle

```python
n ^ mask
```

XOR flips that bit.

---

# 10. Detailed Dry Run

Take:

```text
n = 10
```

Binary:

```text
1010
```

and:

```text
k = 1
```

Mask:

```text
0010
```

## Check

```text
1010
0010
----
0010
```

Non-zero:

```text
bit 1 = 1
```

---

## Set

```text
1010
0010
----
1010
```

Already 1, so unchanged.

---

## Clear

```text
mask       = 0010
~mask      = ...1101
```

Effectively:

```text
1010
↓
1000
```

So:

```text
clear bit 1 → 8
```

---

## Toggle

```text
1010
0010
----
1000
```

Result:

```text
8
```

---

# 11. Time Complexity

Each operation is constant-time for fixed-width machine integers:

```text
O(1)
```

---

# 12. Space Complexity

```text
O(1)
```

---

# 13. Edge Cases

### Setting an already-set bit

No change.

```text
1 | 1 = 1
```

### Clearing an already-clear bit

No change.

```text
0 & 0 = 0
```

### Toggling

Always flips:

```text
0 ↔ 1
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```text
1 << k
```

incorrectly.

Remember:

```text
k = 0 → 0001
k = 1 → 0010
k = 2 → 0100
k = 3 → 1000
```

---

### ❌ Mistake 2

Confusing set and toggle.

```text
SET
→ force 1
→ OR
```

```text
TOGGLE
→ flip
→ XOR
```

---

# 15. Pattern Recognition

When you see:

```text
set bit
clear bit
toggle bit
check kth bit
```

Immediately think:

```text
MASK = 1 << k
```

Then:

```text
Check  → &
Set    → |
Clear  → & ~
Toggle → ^
```

### 🔥 Memorize:

```text
CHECK  → &
SET    → |
CLEAR  → & ~
TOGGLE → ^
```

---

# 🟦 PROBLEM 3 — CHECK WHETHER A NUMBER IS A POWER OF 2

## 1. Problem Statement

Given an integer `n`, determine whether it is a power of `2`.

Examples:

```text
1   → True
2   → True
4   → True
8   → True
16  → True
10  → False
12  → False
```

---

# 2. Problem Theory

Look at powers of two in binary:

```text
1  = 0001
2  = 0010
4  = 0100
8  = 1000
16 = 10000
```

A power of two has:

> **Exactly one set bit.**

For example:

```text
8 = 1000
```

Only one `1`.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
n & (n - 1)
```

For a positive power of two:

```text
n & (n - 1) == 0
```

---

# 4. ELI10 Intuition

Take:

```text
8 = 1000
```

Subtract one:

```text
7 = 0111
```

Now:

```text
1000
0111
----
0000
```

Everything cancels.

But consider:

```text
10 = 1010
```

`10 - 1`:

```text
9 = 1001
```

AND:

```text
1010
1001
----
1000
```

Not zero.

Therefore 10 isn't a power of two.

---

# 5. Example

```text
n = 16
```

Binary:

```text
10000
```

`n - 1`:

```text
01111
```

AND:

```text
10000
01111
-----
00000
```

Therefore:

```text
16 is power of 2
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Check:

```text
n > 0
```

because:

```text
0
```

is not a power of 2.

### Step 2

Calculate:

```text
n & (n - 1)
```

### Step 3

If result is `0`:

```text
Power of 2
```

Otherwise:

```text
Not a power of 2
```

---

# 7. Python — Normal Method

```python
def is_power_of_two_normal(n):

    if n <= 0:
        return False

    while n % 2 == 0:
        n //= 2

    return n == 1
```

---

# 8. Python — Bit Manipulation

```python
def is_power_of_two(n):

    return n > 0 and (n & (n - 1)) == 0


print(is_power_of_two(16))
print(is_power_of_two(10))
```

Output:

```text
True
False
```

---

# 9. Line-by-Line Explanation

```python
n > 0
```

Eliminates:

```text
0
negative numbers
```

Then:

```python
n & (n - 1)
```

removes the lowest set bit.

For a number with only one set bit, nothing remains.

Therefore:

```text
result = 0
```

---

# 10. Detailed Dry Run

### `n = 8`

```text
8     = 1000
7     = 0111
--------------
AND   = 0000
```

True.

### `n = 12`

```text
12    = 1100
11    = 1011
--------------
AND   = 1000
```

Not zero.

False.

---

# 11. Time Complexity

```text
O(1)
```

for fixed-width integers.

---

# 12. Space Complexity

```text
O(1)
```

---

# 13. Edge Cases

```text
1 → True
```

Because:

```text
2⁰ = 1
```

```text
0 → False
```

```text
-8 → False
```

---

# 14. Common Mistakes / Traps

### ❌ Forgetting `n > 0`

If you only write:

```python
(n & (n - 1)) == 0
```

then `0` incorrectly satisfies the expression.

Correct:

```python
n > 0 and (n & (n - 1)) == 0
```

---

# 15. Pattern Recognition

When you see:

> "Power of 2"

Immediately think:

```text
n > 0
AND
n & (n-1) == 0
```

### 🔥 Golden identity

```text
n & (n - 1)
```

removes the **lowest set bit**.

This identity will appear again in Problem 4.

---

# 🟦 PROBLEM 4 — COUNT SET BITS

## 1. Problem Statement

Given an integer `n`, count how many `1`s are present in its binary representation.

This is also called:

```text
Number of Set Bits
```

or:

```text
Hamming Weight
```

Example:

```text
n = 13
```

Binary:

```text
1101
```

There are:

```text
3
```

set bits.

Answer:

```text
3
```

---

# 2. Problem Theory

A **set bit** is simply a bit whose value is:

```text
1
```

Example:

```text
13 = 1101
```

Positions:

```text
3 2 1 0
1 1 0 1
```

There are three `1`s.

---

# 3. Pattern Being Tested

There are two common methods.

### Method 1 — Check every bit

```text
n & 1
n >> 1
n & 1
...
```

### Method 2 — Brian Kernighan's Algorithm

Use:

```text
n = n & (n - 1)
```

Each operation removes one set bit.

Therefore:

> Number of iterations = number of set bits.

This is the more important interview pattern.

---

# 4. ELI10 Intuition

Imagine every `1` is a light.

```text
1101
```

has three lights on.

The trick:

```text
n & (n - 1)
```

turns off the **rightmost light that is currently ON**.

So:

```text
1101
↓
1100
↓
1000
↓
0000
```

We performed the operation three times.

Therefore:

```text
3 set bits
```

---

# 5. Example

```text
n = 13
```

Binary:

```text
1101
```

### First operation

```text
1101
1100
----
1100
```

Count = 1.

### Second

```text
1100
1011
----
1000
```

Count = 2.

### Third

```text
1000
0111
----
0000
```

Count = 3.

Done.

---

# 6. Algorithm — Step-by-Step

### Step 1

Set:

```text
count = 0
```

### Step 2

While:

```text
n != 0
```

### Step 3

Remove lowest set bit:

```text
n = n & (n - 1)
```

### Step 4

Increment:

```text
count += 1
```

### Step 5

Return count.

---

# 7. Python — Normal Method

```python
def count_set_bits_normal(n):

    count = 0

    while n > 0:

        if n % 2 == 1:
            count += 1

        n //= 2

    return count
```

This repeatedly examines the last bit.

---

# 8. Python — Bit Manipulation

```python
def count_set_bits(n):

    count = 0

    while n:

        n = n & (n - 1)

        count += 1

    return count


print(count_set_bits(13))
```

Output:

```text
3
```

---

# 9. Line-by-Line Explanation

```python
count = 0
```

No set bits counted yet.

---

```python
while n:
```

Continue while there are still set bits.

---

```python
n = n & (n - 1)
```

This removes exactly one set bit.

---

```python
count += 1
```

Because one set bit was removed.

---

```python
return count
```

Number of removals = number of original set bits.

---

# 10. Detailed Dry Run

Input:

```text
n = 13
```

Binary:

```text
1101
```

| Iteration | `n` before | `n & (n-1)` | Count |
| --------: | ---------- | ----------- | ----: |
|         1 | `1101`     | `1100`      |     1 |
|         2 | `1100`     | `1000`      |     2 |
|         3 | `1000`     | `0000`      |     3 |

Stop.

Answer:

```text
3
```

---

# 11. Time Complexity

This is a very important detail.

The loop runs once for every **set bit**, not every bit position.

If there are `k` set bits:

```text
Time = O(k)
```

Since:

```text
k ≤ number of bits
```

for a fixed-width integer, this is effectively very efficient.

---

# 12. Space Complexity

```text
O(1)
```

---

# 13. Edge Cases

### `n = 0`

```text
0
```

contains zero set bits.

Answer:

```text
0
```

### `n = 1`

```text
1
```

Answer:

```text
1
```

### `n = 15`

```text
1111
```

Answer:

```text
4
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Thinking:

```text
n & (n-1)
```

always gives zero.

No.

It gives zero **only when the number has exactly one set bit**.

Otherwise it removes one set bit and leaves the others.

---

### ❌ Mistake 2

Confusing:

```text
lowest set bit
```

with:

```text
total set bits
```

`n & (n-1)` removes one set bit.

Repeatedly applying it counts all set bits.

---

# 15. Pattern Recognition

When you see:

> "Count number of 1s in binary"

Think:

```text
Brian Kernighan
↓
n = n & (n-1)
↓
count++
```

### 🔥 Golden pattern

```text
n & (n-1)
```

means:

> **Remove the lowest set bit.**

---

# 🟢 BASIC BIT MANIPULATION — CONVERSATION 1 COMPLETE

We have completed the first four fundamental patterns:

```text
1. Odd / Even
   ↓
   n & 1

2. Check / Set / Clear / Toggle Bit
   ↓
   1 << k
   ↓
   &, |, &~, ^

3. Power of 2
   ↓
   n > 0
   ↓
   n & (n-1) == 0

4. Count Set Bits
   ↓
   n = n & (n-1)
   ↓
   count++
```

## 🔥 The four identities to memorize

```text
ODD / EVEN
→ n & 1
```

```text
BIT MASK
→ 1 << k
```

```text
POWER OF 2
→ n & (n-1) == 0
```

```text
REMOVE LOWEST SET BIT
→ n & (n-1)
```

### Current Progress

```text
BASIC BIT MANIPULATION

Problem 1  Odd / Even                    ✅
Problem 2  Check / Set / Clear / Toggle  ✅
Problem 3  Power of 2                    ✅
Problem 4  Count Set Bits                ✅

Progress: 4/10
```

**Next locked section: Problems 5–8 → Hamming Weight refinement, Unique Number using XOR, Missing Number using XOR, and XOR Swap.**


# 🟦 BASIC BIT MANIPULATION — CONVERSATION 2

## Problems 5–8 — Locked TopGun Version

We continue directly from **4/10**.

```text
1. Odd / Even                         ✅
2. Check / Set / Clear / Toggle Bit   ✅
3. Power of 2                         ✅
4. Count Set Bits                     ✅
5. Hamming Weight                     🔵
6. Unique Number using XOR            🔵
7. Missing Number using XOR           🔵
8. Swap Two Numbers using XOR         🔵
9. Lowest Set Bit                     🔵
10. Binary Representation             🔵
```

---

# 🔵 PROBLEM 5 — HAMMING WEIGHT

## 1. Problem Statement

Given a positive integer `n`, return the number of `1` bits in its binary representation.

This is commonly called:

> **Hamming Weight**

### Example

```text
n = 11
```

Binary:

```text
1011
```

There are three `1`s.

Therefore:

```text
Output = 3
```

---

# 2. Problem Theory

You already learned **Count Set Bits** in Problem 4.

So why is Hamming Weight here?

Because in interviews and coding platforms, the same fundamental operation can appear under different wording:

```text
Number of 1 bits
Count set bits
Hamming weight
Population count
Number of set bits
```

They are fundamentally the same pattern.

### Important distinction

There are two common approaches.

### Approach 1 — Examine every bit

```text
check last bit
shift right
check next bit
...
```

### Approach 2 — Remove one set bit at a time

```text
n = n & (n - 1)
```

The second approach is the important optimized pattern.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
Hamming Weight
        ↓
Count 1-bits
        ↓
n & (n - 1)
```

Every application of:

```text
n & (n - 1)
```

removes exactly **one** set bit.

Therefore:

```text
number of operations = number of 1s
```

---

# 4. ELI10 Intuition

Imagine binary digits are light switches.

```text
101101
```

There are four lights turned ON:

```text
1 0 1 1 0 1
↑   ↑ ↑   ↑
```

Our trick:

```text
n & (n - 1)
```

turns off the **rightmost ON switch**.

So:

```text
101101
↓
101100
↓
101000
↓
100000
↓
000000
```

We needed four operations.

Therefore:

```text
Hamming Weight = 4
```

---

# 5. Example

Take:

```text
n = 11
```

Binary:

```text
1011
```

Apply:

```text
1011
1010
----
1010
```

Count = 1.

Again:

```text
1010
1001
----
1000
```

Count = 2.

Again:

```text
1000
0111
----
0000
```

Count = 3.

Therefore:

```text
Hamming Weight = 3
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Create:

```python
count = 0
```

### Step 2

While `n` is not zero:

```python
while n:
```

### Step 3

Remove the lowest set bit:

```python
n = n & (n - 1)
```

### Step 4

Increment count:

```python
count += 1
```

### Step 5

Return count.

---

# 7. Python Solution — Using Built-in Method

Python provides a direct binary conversion approach:

```python
def hamming_weight_builtin(n):
    return bin(n).count("1")


print(hamming_weight_builtin(11))
```

Output:

```text
3
```

This is useful, but for a **bit-manipulation interview**, you should understand the manual bit operation.

---

# 8. Python Solution — Without Built-in Bit Counting

```python
def hamming_weight(n):

    count = 0

    while n:

        n = n & (n - 1)

        count += 1

    return count


print(hamming_weight(11))
```

Output:

```text
3
```

---

# 9. Line-by-Line Explanation

```python
count = 0
```

No `1` bits counted yet.

---

```python
while n:
```

Continue while at least one set bit remains.

---

```python
n = n & (n - 1)
```

This removes the lowest set bit.

This is the **core operation**.

---

```python
count += 1
```

One set bit was removed, so increase the count.

---

```python
return count
```

Return the total number of set bits.

---

# 10. Detailed Dry Run

Take:

```text
n = 22
```

Binary:

```text
10110
```

Set bits:

```text
1 0 1 1 0
↑   ↑ ↑
```

There are 3.

| Iteration | `n` before | `n - 1` | Result  | Count |
| --------: | ---------- | ------- | ------- | ----: |
|         1 | `10110`    | `10101` | `10100` |     1 |
|         2 | `10100`    | `10011` | `10000` |     2 |
|         3 | `10000`    | `01111` | `00000` |     3 |

Final:

```text
3
```

---

# 11. Time Complexity

If the number contains `k` set bits:

```text
Time = O(k)
```

Since every iteration removes exactly one `1`.

---

# 12. Space Complexity

```text
O(1)
```

---

# 13. Edge Cases

### `n = 0`

```text
binary = 0
```

Answer:

```text
0
```

### `n = 1`

```text
binary = 1
```

Answer:

```text
1
```

### `n = 7`

```text
111
```

Answer:

```text
3
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Thinking:

```text
n & (n - 1)
```

counts bits automatically.

No.

It **removes one bit**.

You need:

```python
count += 1
```

for every removal.

---

### ❌ Mistake 2

Confusing:

```text
n & 1
```

with:

```text
n & (n - 1)
```

Remember:

```text
n & 1
→ inspect last bit
```

```text
n & (n - 1)
→ remove lowest set bit
```

---

# 15. Pattern Recognition

When you see:

```text
Hamming Weight
Population Count
Count 1s
Number of Set Bits
```

Immediately think:

```text
n & (n - 1)
```

---

# 🔵 PROBLEM 6 — FIND THE UNIQUE NUMBER USING XOR

## 1. Problem Statement

Given an array where:

* every number appears exactly twice
* except one number that appears once

find the number that appears only once.

### Example

```text
[4, 1, 2, 1, 2]
```

Output:

```text
4
```

---

# 2. Problem Theory

A normal frequency dictionary could solve this.

But XOR gives a much cleaner solution.

The critical XOR identities are:

```text
x ^ x = 0
```

and:

```text
x ^ 0 = x
```

Therefore:

```text
4 ^ 1 ^ 2 ^ 1 ^ 2
```

can be rearranged as:

```text
4 ^ (1 ^ 1) ^ (2 ^ 2)
```

which becomes:

```text
4 ^ 0 ^ 0
```

which becomes:

```text
4
```

All pairs cancel.

Only the unique number survives.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
Duplicates appear twice
+
One unique
↓
XOR
```

Template:

```python
result = 0

for x in arr:
    result ^= x

return result
```

---

# 4. ELI10 Intuition

Imagine every number has a twin.

```text
1 → twin 1
2 → twin 2
4 → no twin
```

XOR makes twins disappear:

```text
1 ^ 1 = 0
2 ^ 2 = 0
```

The number without a twin survives.

---

# 5. Example

```text
[4, 1, 2, 1, 2]
```

Process:

```text
0 ^ 4 = 4
4 ^ 1 = 5
5 ^ 2 = 7
7 ^ 1 = 6
6 ^ 2 = 4
```

Answer:

```text
4
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Initialize:

```python
result = 0
```

### Step 2

Visit every number.

### Step 3

XOR it with `result`.

### Step 4

Return `result`.

Why does this work?

Because:

```text
a ^ a = 0
```

and:

```text
0 ^ unique = unique
```

---

# 7. Python Solution — Using Built-in / Normal Method

A dictionary solution:

```python
def find_unique_normal(arr):

    frequency = {}

    for x in arr:
        frequency[x] = frequency.get(x, 0) + 1

    for x in arr:
        if frequency[x] == 1:
            return x


arr = [4, 1, 2, 1, 2]

print(find_unique_normal(arr))
```

Output:

```text
4
```

---

# 8. Python Solution — XOR

```python
def find_unique(arr):

    result = 0

    for x in arr:
        result ^= x

    return result


arr = [4, 1, 2, 1, 2]

print(find_unique(arr))
```

Output:

```text
4
```

---

# 9. Line-by-Line Explanation

```python
result = 0
```

XOR has:

```text
0 ^ x = x
```

so zero is the perfect starting value.

---

```python
for x in arr:
```

Visit every element.

---

```python
result ^= x
```

Equivalent to:

```python
result = result ^ x
```

Pairs eventually cancel.

---

```python
return result
```

The only surviving number is the unique number.

---

# 10. Detailed Dry Run

Input:

```text
[4, 1, 2, 1, 2]
```

| Step | Value | XOR Calculation | Result |
| ---: | ----: | --------------- | -----: |
|    0 |     — | `0`             |      0 |
|    1 |     4 | `0 ^ 4`         |      4 |
|    2 |     1 | `4 ^ 1`         |      5 |
|    3 |     2 | `5 ^ 2`         |      7 |
|    4 |     1 | `7 ^ 1`         |      6 |
|    5 |     2 | `6 ^ 2`         |      4 |

Final:

```text
4
```

---

# 11. Time Complexity

Every element is visited once:

```text
O(n)
```

---

# 12. Space Complexity

No dictionary or additional array:

```text
O(1)
```

---

# 13. Edge Cases

### One element

```text
[7]
```

Answer:

```text
7
```

### Unique number at beginning

```text
[5, 2, 2, 3, 3]
```

Answer:

```text
5
```

### Unique number at end

```text
[2, 3, 2, 3, 5]
```

Answer:

```text
5
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Starting with:

```python
result = 1
```

Wrong.

Use:

```python
result = 0
```

because:

```text
0 ^ x = x
```

---

### ❌ Mistake 2

Using this pattern when numbers don't satisfy the condition.

The XOR solution requires:

> Every duplicate appears exactly twice and exactly one number appears once.

If there are multiple unique numbers, this simple solution does not directly solve the problem.

---

# 15. Pattern Recognition

When you see:

> Every number appears twice except one.

Think:

```text
XOR
```

Immediately recall:

```text
x ^ x = 0
x ^ 0 = x
```

---

# 🔵 PROBLEM 7 — FIND THE MISSING NUMBER USING XOR

## 1. Problem Statement

Given an array containing `n` distinct numbers from:

```text
0 → n
```

with exactly one number missing, find the missing number.

### Example

```text
Input:
[3, 0, 1]

Output:
2
```

Because the complete range is:

```text
0, 1, 2, 3
```

and `2` is missing.

---

# 2. Problem Theory

There are several ways to solve this.

### Mathematical method

Use:

```text
sum(0...n) - sum(array)
```

But XOR provides another elegant solution.

We know:

```text
x ^ x = 0
```

So if we XOR:

```text
all numbers from 0 to n
```

and:

```text
all numbers in the array
```

every number that exists in both places cancels.

Only the missing number remains.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
Complete range
+
Array
+
Exactly one missing
↓
XOR cancellation
```

---

# 4. ELI10 Intuition

Imagine two lists.

Complete list:

```text
0 1 2 3
```

Actual list:

```text
0 1 3
```

XOR them:

```text
0 ^ 1 ^ 2 ^ 3
^
0 ^ 1 ^ 3
```

The matching numbers disappear:

```text
0 ^ 0 = 0
1 ^ 1 = 0
3 ^ 3 = 0
```

Only:

```text
2
```

remains.

---

# 5. Example

```text
[3, 0, 1]
```

Expected:

```text
0,1,2,3
```

Missing:

```text
2
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Start:

```python
missing = 0
```

### Step 2

XOR every index.

### Step 3

XOR every array value.

### Step 4

Matching numbers cancel.

### Step 5

Return the remaining value.

A convenient implementation is:

```python
missing = len(arr)

for i in range(len(arr)):
    missing ^= i
    missing ^= arr[i]
```

---

# 7. Python Solution — Normal Method

Using arithmetic:

```python
def missing_number_normal(arr):

    n = len(arr)

    expected_sum = n * (n + 1) // 2

    actual_sum = 0

    for x in arr:
        actual_sum += x

    return expected_sum - actual_sum


print(missing_number_normal([3, 0, 1]))
```

Output:

```text
2
```

---

# 8. Python Solution — XOR

```python
def missing_number(arr):

    n = len(arr)

    missing = n

    for i in range(n):
        missing ^= i
        missing ^= arr[i]

    return missing


arr = [3, 0, 1]

print(missing_number(arr))
```

Output:

```text
2
```

---

# 9. Line-by-Line Explanation

```python
n = len(arr)
```

If:

```text
arr = [3,0,1]
```

then:

```text
n = 3
```

The complete range is:

```text
0,1,2,3
```

---

```python
missing = n
```

Start with `3`.

---

```python
for i in range(n):
```

Process:

```text
i = 0,1,2
```

---

```python
missing ^= i
```

XOR with every index.

---

```python
missing ^= arr[i]
```

XOR with every array value.

Eventually all existing numbers cancel.

---

# 10. Detailed Dry Run

Input:

```text
[3, 0, 1]
```

Start:

```text
missing = 3
```

### `i = 0`

```text
3 ^ 0 ^ 3
```

```text
3 ^ 0 = 3
3 ^ 3 = 0
```

Result:

```text
0
```

### `i = 1`

```text
0 ^ 1 ^ 0
```

Result:

```text
1
```

### `i = 2`

```text
1 ^ 2 ^ 1
```

First:

```text
1 ^ 2 = 3
```

Then:

```text
3 ^ 1 = 2
```

Final:

```text
2
```

### Dry Run Table

|   `i` | `arr[i]` | Calculation | `missing` |
| ----: | -------: | ----------- | --------: |
| Start |        — | —           |         3 |
|     0 |        3 | `3 ^ 0 ^ 3` |         0 |
|     1 |        0 | `0 ^ 1 ^ 0` |         1 |
|     2 |        1 | `1 ^ 2 ^ 1` |         2 |

---

# 11. Time Complexity

We visit each element once:

```text
O(n)
```

---

# 12. Space Complexity

Only one variable:

```text
O(1)
```

---

# 13. Edge Cases

### Missing `0`

```text
[1, 2, 3]
```

Answer:

```text
0
```

### Missing `n`

```text
[0, 1, 2]
```

Answer:

```text
3
```

### One element

```text
[0]
```

Answer:

```text
1
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Assuming XOR works for an arbitrary unsorted array with duplicates.

The required condition is:

```text
0 → n
distinct
exactly one missing
```

---

### ❌ Mistake 2

Forgetting that `n = len(arr)`.

If array has length 3:

```text
complete range = 0,1,2,3
```

---

# 15. Pattern Recognition

When you see:

> Numbers from `0` to `n`, exactly one missing.

Think:

```text
XOR
```

Template:

```python
missing = n

for i in range(n):
    missing ^= i
    missing ^= arr[i]
```

---

# 🔵 PROBLEM 8 — SWAP TWO NUMBERS USING XOR

## 1. Problem Statement

Swap two integer variables without using a temporary third variable.

Example:

```text
a = 5
b = 9
```

After swapping:

```text
a = 9
b = 5
```

---

# 2. Problem Theory

Normally:

```python
temp = a
a = b
b = temp
```

This is perfectly fine in real Python.

But bit manipulation introduces a classic XOR trick:

```text
a = a ^ b
b = a ^ b
a = a ^ b
```

The trick works because XOR is reversible.

---

# 3. Pattern Being Tested

### 🔥 Pattern

```text
XOR swap
```

The three-step pattern:

```text
a = a ^ b
b = a ^ b
a = a ^ b
```

---

# 4. ELI10 Intuition

Suppose:

```text
a = A
b = B
```

After:

```text
a = A ^ B
```

Now `a` remembers a combination of both values.

Then:

```text
b = (A ^ B) ^ B
```

Since:

```text
B ^ B = 0
```

we get:

```text
b = A
```

Then:

```text
a = (A ^ B) ^ A
```

which gives:

```text
a = B
```

They have swapped.

---

# 5. Example

Take:

```text
a = 5
b = 9
```

Binary:

```text
5 = 0101
9 = 1001
```

### Step 1

```text
a = a ^ b
```

```text
0101
1001
----
1100
```

So:

```text
a = 12
b = 9
```

### Step 2

```text
b = a ^ b
```

```text
1100
1001
----
0101
```

So:

```text
b = 5
```

### Step 3

```text
a = a ^ b
```

```text
1100
0101
----
1001
```

So:

```text
a = 9
```

Final:

```text
a = 9
b = 5
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Combine both values:

```text
a = a ^ b
```

### Step 2

Recover original `a` into `b`:

```text
b = a ^ b
```

### Step 3

Recover original `b` into `a`:

```text
a = a ^ b
```

Done.

---

# 7. Python Solution — Normal Method

```python
def swap_normal(a, b):

    temp = a
    a = b
    b = temp

    return a, b


print(swap_normal(5, 9))
```

Output:

```text
(9, 5)
```

---

# 8. Python Solution — XOR

```python
def swap_xor(a, b):

    a = a ^ b
    b = a ^ b
    a = a ^ b

    return a, b


print(swap_xor(5, 9))
```

Output:

```text
(9, 5)
```

---

# 9. Line-by-Line Explanation

### First line

```python
a = a ^ b
```

Now `a` contains:

```text
original_a ^ original_b
```

---

### Second line

```python
b = a ^ b
```

Substitute:

```text
b = (A ^ B) ^ B
```

Because:

```text
B ^ B = 0
```

we get:

```text
b = A
```

---

### Third line

```python
a = a ^ b
```

Now:

```text
a = (A ^ B) ^ A
```

Since:

```text
A ^ A = 0
```

we get:

```text
a = B
```

Swap complete.

---

# 10. Detailed Dry Run

Input:

```text
a = 5
b = 9
```

Binary:

```text
a = 0101
b = 1001
```

| Step        | `a` | `b` |
| ----------- | --: | --: |
| Initial     |   5 |   9 |
| `a = a ^ b` |  12 |   9 |
| `b = a ^ b` |  12 |   5 |
| `a = a ^ b` |   9 |   5 |

Final:

```text
a = 9
b = 5
```

---

# 11. Time Complexity

Three XOR operations:

```text
O(1)
```

---

# 12. Space Complexity

No additional variable:

```text
O(1)
```

---

# 13. Edge Cases

### Same values

```text
a = 5
b = 5
```

Result:

```text
5, 5
```

### Zero

```text
a = 0
b = 7
```

Result:

```text
7, 0
```

---

# 14. Common Mistakes / Traps

## ⚠️ Important real-world note

In Python, XOR swap is **not recommended as the normal way to swap values**.

Python already provides:

```python
a, b = b, a
```

which is clearer and idiomatic.

For this **Bit Manipulation topic**, however, the XOR swap is valuable because it tests whether you understand XOR's properties.

---

### ❌ Mistake 1

Changing the order.

The exact sequence matters:

```text
a = a ^ b
b = a ^ b
a = a ^ b
```

---

### ❌ Mistake 2

Trying XOR swap when `a` and `b` refer to the same storage location in lower-level languages.

That can cause issues in certain implementations.

For basic Python screening, this is mainly a conceptual XOR exercise.

---

# 15. Pattern Recognition

When you see:

> Swap two integers without a temporary variable using bit manipulation.

Think:

```text
XOR SWAP
```

```text
a ^= b
b ^= a
a ^= b
```

---

# 🧠 CONVERSATION 2 — BIT MANIPULATION MASTER MAP

We have now completed Problems 5–8.

|     # | Problem                      | Pattern               |
| ----: | ---------------------------- | --------------------- |
|     1 | Odd / Even                   | `n & 1`               |
|     2 | Check / Set / Clear / Toggle | Bit Mask              |
|     3 | Power of 2                   | `n & (n-1)`           |
|     4 | Count Set Bits               | Kernighan             |
| **5** | **Hamming Weight**           | **Count `1` bits**    |
| **6** | **Unique Number**            | **XOR Cancellation**  |
| **7** | **Missing Number**           | **XOR Cancellation**  |
| **8** | **XOR Swap**                 | **XOR Reversibility** |
|     9 | Lowest Set Bit               | `n & -n`              |
|    10 | Binary Representation        | Shift + Mask          |

---

# 🔥 THE XOR RULES YOU MUST MEMORIZE

These four rules are the foundation:

```text
x ^ x = 0
```

```text
x ^ 0 = x
```

```text
a ^ b = b ^ a
```

```text
(a ^ b) ^ c = a ^ (b ^ c)
```

Therefore, XOR can:

```text
cancel duplicates
recover missing values
preserve unique values
reverse information
```

---

# 🧠 BIT PATTERN RECOGNITION

## If you see:

### "Odd or even"

```text
→ n & 1
```

### "kth bit"

```text
→ 1 << k
```

### "Set kth bit"

```text
→ n | (1 << k)
```

### "Clear kth bit"

```text
→ n & ~(1 << k)
```

### "Toggle kth bit"

```text
→ n ^ (1 << k)
```

### "Power of 2"

```text
→ n > 0
→ n & (n-1) == 0
```

### "Count set bits"

```text
→ n & (n-1)
```

### "Every element twice except one"

```text
→ XOR
```

### "0 to n with one missing"

```text
→ XOR
```

### "Swap using bit manipulation"

```text
→ XOR
```

---

# 🚨 TOPGUN SCREENING TRAPS

## Trap 1 — Confusing XOR and OR

```text
OR:
1 | 1 = 1
```

but:

```text
XOR:
1 ^ 1 = 0
```

For cancellation problems:

```text
→ XOR
```

---

## Trap 2 — Forgetting the `n > 0` condition

Power of 2:

```python
n > 0 and (n & (n - 1)) == 0
```

Not simply:

```python
(n & (n - 1)) == 0
```

---

## Trap 3 — Confusing `n & 1` with `n & (n-1)`

```text
n & 1
→ inspect lowest bit
```

```text
n & (n-1)
→ remove lowest set bit
```

---

## Trap 4 — Misunderstanding XOR unique-number condition

Simple XOR works when:

```text
every duplicate appears exactly twice
AND
one element appears once
```

---

## Trap 5 — Missing number range

The XOR missing-number pattern assumes:

```text
0,1,2,...,n
```

with exactly one missing.

---

# 🏆 BIT MANIPULATION MASTER FORMULA CARD

```text
┌────────────────────────────────────┐
│ BASIC BIT MANIPULATION             │
├────────────────────────────────────┤
│ Last bit        → n & 1            │
│ kth-bit mask    → 1 << k           │
│ Check bit       → n & mask         │
│ Set bit         → n | mask         │
│ Clear bit       → n & ~mask        │
│ Toggle bit      → n ^ mask         │
│ Remove low bit  → n & (n-1)        │
│ Power of 2      → n & (n-1) == 0   │
│ Count 1-bits    → repeat removal   │
│ Unique element  → XOR              │
│ Missing number  → XOR              │
│ XOR swap        → 3 XOR operations │
└────────────────────────────────────┘
```

---

# 🟢 CURRENT PROGRESS

```text
BASIC BIT MANIPULATION

Problem 1  Odd / Even                    ✅
Problem 2  Check / Set / Clear / Toggle  ✅
Problem 3  Power of 2                    ✅
Problem 4  Count Set Bits                ✅
Problem 5  Hamming Weight                ✅
Problem 6  Unique Number using XOR       ✅
Problem 7  Missing Number using XOR      ✅
Problem 8  XOR Swap                      ✅
-------------------------------------------
Progress: 8/10
```

### Next locked section

```text
CONVERSATION 3

Problem 9
→ Find Lowest Set Bit
→ n & -n

Problem 10
→ Generate / Check Binary Representation
→ Shift + Mask

Then:

→ Complete Bit Manipulation Mastery
→ Full Pattern Recognition Map
→ Master Templates
→ TopGun Screening Traps
→ Mini Test
→ 10/10 completion
```

Would you like to continue with Problems 9–10, or would a short practice quiz on Problems 5–8 be more useful first?

# 🔵 BASIC BIT MANIPULATION — PROBLEMS 9–10

## Final 2 Problems → Topic Completion

We are continuing **exactly with the locked execution format**. These last two problems complete the remaining core bit patterns:

* **Problem 9 → Lowest Set Bit**
* **Problem 10 → Binary Representation using Shift + Mask**

---

# 🟦 PROBLEM 9 — Find the Lowest Set Bit

## 1. 🧩 Problem Statement

Given a positive integer `n`, find the **value of its lowest set bit**.

A **set bit** is a bit whose value is `1`.

The **lowest set bit** means the **rightmost `1`** in the binary representation.

### Example

```text
n = 12
```

Binary:

```text
12 = 1100
```

The rightmost `1` is:

```text
1100
  ↑
```

Its place value is:

```text
0100 = 4
```

### Output

```text
4
```

---

# 2. 📚 Problem Theory

The key bit-manipulation identity is:

```text
n & (-n)
```

This isolates the **lowest set bit**.

### Example

```text
n = 12
```

Binary:

```text
12 = 1100
```

The result is:

```text
0100
```

Therefore:

```text
12 & -12 = 4
```

---

# 3. 🎯 Pattern Being Tested

### Main Pattern

> **Lowest Set Bit Isolation**

### Formula

```python
n & -n
```

This is one of the most important bit tricks.

---

# 4. 🧒 ELI10 Intuition

Imagine the binary number has several lights turned ON.

```text
1100
```

There are two ON lights:

```text
1 1 0 0
↑ ↑
```

We only want the **last ON light**.

The trick:

```python
n & -n
```

magically turns everything except that last ON bit into `0`.

So:

```text
1100
```

becomes:

```text
0100
```

which is:

```text
4
```

---

# 5. 🔍 Example

Take:

```text
n = 40
```

Binary:

```text
40 = 101000
```

Lowest set bit:

```text
101000
   ↑
```

Its value is:

```text
001000 = 8
```

Therefore:

```python
40 & -40
```

gives:

```text
8
```

---

# 6. 🧠 Why Does `n & -n` Work?

This is based on **two's complement** representation.

For a positive number `n`:

```text
-n = ~n + 1
```

Take:

```text
n = 12
```

Binary:

```text
00001100
```

Invert:

```text
11110011
```

Add 1:

```text
11110100
```

So:

```text
-12 = 11110100
```

Now AND:

```text
  00001100
& 11110100
-----------
  00000100
```

Result:

```text
4
```

Everything except the lowest `1` disappears.

---

# 7. 🔹 Algorithm — Step-by-Step

### Bit Manipulation Algorithm

```text
Step 1 → Take positive integer n.
Step 2 → Compute -n.
Step 3 → Perform n & (-n).
Step 4 → The result is the lowest set bit value.
```

### Example

```text
n = 12

12 & -12
   ↓
4
```

---

# 8. 🐍 Python Solution — Using Normal/Mathematical Method

Before learning the bit trick, we can solve it by checking bits from right to left.

```python
def lowest_set_bit_normal(n):
    position = 0

    while n > 0:
        if n % 2 == 1:
            return 2 ** position

        n = n // 2
        position += 1

    return 0
```

### Test

```python
print(lowest_set_bit_normal(12))
```

Output:

```text
4
```

---

# 9. 🐍 Python Solution — Bit Manipulation

```python
def lowest_set_bit(n):
    return n & -n
```

### Test

```python
print(lowest_set_bit(12))
```

Output:

```text
4
```

---

# 10. 🔬 Line-by-Line Explanation

```python
def lowest_set_bit(n):
```

Defines the function.

---

```python
return n & -n
```

Three things happen:

### `-n`

Find the two's-complement negative value.

### `&`

Performs bitwise AND.

### Result

Only the lowest set bit survives.

---

# 11. 🧪 Detailed Dry Run

Let's use:

```text
n = 12
```

### Step 1

```text
12 = 1100
```

### Step 2

Find `-12`.

```text
  00001100
```

Invert:

```text
  11110011
```

Add 1:

```text
  11110100
```

Therefore:

```text
-12 = 11110100
```

### Step 3

AND them:

```text
  00001100
& 11110100
-----------
  00000100
```

### Step 4

Convert back:

```text
00000100 = 4
```

### Final answer

```text
4
```

---

# 12. ⏱️ Time Complexity

```python
n & -n
```

is a constant number of bit operations.

### Time

```text
O(1)
```

### Space

```text
O(1)
```

---

# 13. ⚠️ Edge Cases

### Case 1 — `n = 1`

```text
1 = 0001
```

```python
1 & -1
```

Result:

```text
1
```

---

### Case 2 — `n = 8`

```text
1000
```

Lowest set bit:

```text
1000 = 8
```

---

### Case 3 — Power of 2

Every positive power of 2 contains exactly one set bit.

```text
8  → 1000 → 8
16 → 10000 → 16
32 → 100000 → 32
```

Therefore:

```python
n & -n == n
```

for positive powers of two.

---

### Case 4 — `n = 0`

```text
0 & -0 = 0
```

So:

```python
lowest_set_bit(0)
```

returns:

```text
0
```

---

# 14. 🚨 Common Mistakes / Traps

### Trap 1 — Confusing value with position

For:

```text
n = 12 = 1100
```

Lowest set bit **position** is:

```text
2
```

if counting from position `0`.

But lowest set bit **value** is:

```text
4
```

The formula:

```python
n & -n
```

returns:

```text
4
```

not `2`.

---

### Trap 2 — Forgetting that Python uses arbitrary-size integers

Python does not have the same fixed-width integer representation as C/C++.

But the identity:

```python
n & -n
```

still works correctly for positive integers.

---

# 15. 🧠 Pattern Recognition

## When you see:

> "Find the lowest/rightmost set bit"

Immediately think:

```python
n & -n
```

### Mental shortcut

```text
Lowest set bit → n & -n
```

---

# 🟩 PROBLEM 10 — Generate Binary Representation Using Bit Operations

## 1. 🧩 Problem Statement

Given a non-negative integer `n`, return its **binary representation** using bit operations.

### Example

```text
Input:
13
```

Binary:

```text
1101
```

Output:

```text
"1101"
```

This problem specifically teaches:

* Right shift `>>`
* AND `&`
* Extracting the last bit
* Reconstructing binary representation

---

# 2. 📚 Problem Theory

To extract the **rightmost bit**, use:

```python
n & 1
```

Why?

Because:

```text
1 = 0001
```

ANDing with `1` checks only the final bit.

### Example

```text
13 = 1101
```

```text
1101
0001
----
0001
```

Result:

```text
1
```

So the last bit is `1`.

---

## Then remove the last bit

Use:

```python
n >> 1
```

For:

```text
1101
```

right shift:

```text
0110
```

which is:

```text
6
```

So:

```text
n & 1 → extract last bit
n >> 1 → remove last bit
```

This is the core pattern.

---

# 3. 🎯 Pattern Being Tested

### Main Patterns

```text
Bit Masking
+
Right Shift
+
Binary Construction
```

Key operations:

```python
n & 1
n >> 1
```

---

# 4. 🧒 ELI10 Intuition

Imagine binary digits are passengers sitting in a row:

```text
1 1 0 1
```

We repeatedly ask:

> "Is the last passenger 0 or 1?"

Use:

```python
n & 1
```

Then we remove that passenger:

```python
n >> 1
```

Repeat until nothing remains.

For:

```text
1101
```

we discover:

```text
1
0
1
1
```

Notice something important:

**We discover the bits from right to left.**

Therefore:

```text
1 → 0 → 1 → 1
```

must eventually be reversed:

```text
1 1 0 1
```

---

# 5. 🔍 Example

Input:

```text
n = 13
```

Binary:

```text
1101
```

Process:

```text
13 → last bit 1
13 >> 1 = 6

6 → last bit 0
6 >> 1 = 3

3 → last bit 1
3 >> 1 = 1

1 → last bit 1
1 >> 1 = 0
```

Collected:

```text
1 0 1 1
```

Reverse:

```text
1 1 0 1
```

Answer:

```text
1101
```

---

# 6. 🧠 Algorithm — Step-by-Step

```text
Step 1 → If n == 0, return "0".

Step 2 → Create an empty collection called bits.

Step 3 → While n > 0:
            a. Extract last bit using n & 1.
            b. Store that bit.
            c. Remove last bit using n >> 1.

Step 4 → The bits are currently reversed.

Step 5 → Reverse them.

Step 6 → Join them into a binary string.

Step 7 → Return the result.
```

---

# 7. 🐍 Python Solution — Using Built-in Method

Python already provides binary conversion:

```python
def binary_builtin(n):
    return bin(n)[2:]
```

### Test

```python
print(binary_builtin(13))
```

Output:

```text
1101
```

### Why `[2:]`?

Python gives:

```python
bin(13)
```

as:

```text
'0b1101'
```

The:

```text
0b
```

means:

> "This is a binary number."

We remove it:

```python
[2:]
```

giving:

```text
1101
```

---

# 8. 🐍 Python Solution — Without `bin()`

```python
def binary_manual(n):
    if n == 0:
        return "0"

    bits = []

    while n > 0:
        bit = n & 1
        bits.append(str(bit))
        n = n >> 1

    bits.reverse()

    return "".join(bits)
```

### Test

```python
print(binary_manual(13))
```

Output:

```text
1101
```

---

# 9. 🔬 Line-by-Line Explanation

```python
def binary_manual(n):
```

Creates the function.

---

```python
if n == 0:
    return "0"
```

Special case.

Without this, the loop would never execute.

---

```python
bits = []
```

Stores extracted bits.

---

```python
while n > 0:
```

Continue until every bit has been processed.

---

```python
bit = n & 1
```

Extract the rightmost bit.

Example:

```text
1101 & 0001
------------
0001
```

So:

```text
bit = 1
```

---

```python
bits.append(str(bit))
```

Store the bit.

We use strings because the final answer must be:

```text
"1101"
```

---

```python
n = n >> 1
```

Remove the rightmost bit.

Example:

```text
1101 >> 1
= 0110
```

---

```python
bits.reverse()
```

The bits were collected backward.

For `13`:

```text
[1, 0, 1, 1]
```

Reverse:

```text
[1, 1, 0, 1]
```

---

```python
return "".join(bits)
```

Convert:

```text
['1', '1', '0', '1']
```

into:

```text
"1101"
```

---

# 10. 🧪 Detailed Dry Run

Input:

```text
n = 13
```

Binary:

```text
1101
```

### Iteration 1

Current:

```text
n = 13
1101
```

Extract:

```text
1101 & 0001 = 1
```

Store:

```text
bits = [1]
```

Shift:

```text
1101 >> 1 = 0110
```

So:

```text
n = 6
```

---

### Iteration 2

```text
n = 6
0110
```

Extract:

```text
0110 & 0001 = 0
```

Store:

```text
bits = [1, 0]
```

Shift:

```text
0110 >> 1 = 0011
```

So:

```text
n = 3
```

---

### Iteration 3

```text
n = 3
0011
```

Extract:

```text
0011 & 0001 = 1
```

Store:

```text
bits = [1, 0, 1]
```

Shift:

```text
0011 >> 1 = 0001
```

So:

```text
n = 1
```

---

### Iteration 4

```text
n = 1
0001
```

Extract:

```text
0001 & 0001 = 1
```

Store:

```text
bits = [1, 0, 1, 1]
```

Shift:

```text
0001 >> 1 = 0000
```

So:

```text
n = 0
```

Loop stops.

---

### Before Reverse

```text
[1, 0, 1, 1]
```

### After Reverse

```text
[1, 1, 0, 1]
```

### Final

```text
"1101"
```

---

# 11. ⏱️ Time Complexity

For an integer with `k` binary bits:

```text
O(k)
```

Since:

```text
k = log₂(n) + 1
```

we can also write:

```text
O(log n)
```

### Space

We store the binary representation:

```text
O(k)
```

Therefore:

```text
Space = O(log n)
```

---

# 12. ⚠️ Edge Cases

### Case 1

```text
n = 0
```

Output:

```text
0
```

---

### Case 2

```text
n = 1
```

Output:

```text
1
```

---

### Case 3

```text
n = 8
```

Binary:

```text
1000
```

Output:

```text
1000
```

---

### Case 4

```text
n = 15
```

Binary:

```text
1111
```

Output:

```text
1111
```

---

# 13. 🚨 Common Mistakes / Traps

### Trap 1 — Forgetting `n & 1`

To extract the last bit:

```python
n & 1
```

not:

```python
n % 2
```

when specifically practicing bit manipulation.

---

### Trap 2 — Forgetting the right shift

You need:

```python
n >>= 1
```

to move to the next bit.

Otherwise:

```python
while n > 0:
```

never ends.

---

### Trap 3 — Wrong bit order

Bits are discovered:

```text
right → left
```

but binary representation is written:

```text
left → right
```

So you must reverse the collected bits.

---

### Trap 4 — Forgetting zero

If:

```python
n = 0
```

the loop does not execute.

Therefore:

```python
if n == 0:
    return "0"
```

is required.

---

# 14. 🧠 Pattern Recognition

When you see:

> "Extract the last/rightmost bit"

Think:

```python
n & 1
```

When you see:

> "Remove the last bit"

Think:

```python
n >> 1
```

When you see:

> "Process every binary bit"

Think:

```python
while n:
    bit = n & 1
    n >>= 1
```

This is a **core bit-manipulation template**.

---

# 🟨 15. 🔥 BIT MANIPULATION MASTER PATTERN MAP

You have now completed all 10 selected basic bit patterns.

| Problem | Pattern           | Core Trick             |
| ------- | ----------------- | ---------------------- |
| 1       | Odd / Even        | `n & 1`                |
| 2       | Check Bit         | `n & (1 << k)`         |
| 2       | Set Bit           | `n \| (1 << k)`        |
| 2       | Clear Bit         | `n & ~(1 << k)`        |
| 2       | Toggle Bit        | `n ^ (1 << k)`         |
| 3       | Power of 2        | `n & (n-1)`            |
| 4       | Count Set Bits    | `n & (n-1)` repeatedly |
| 5       | Hamming Weight    | Count `1` bits         |
| 6       | Unique Number     | XOR                    |
| 7       | Missing Number    | XOR                    |
| 8       | XOR Swap          | `a ^ b`                |
| 9       | Lowest Set Bit    | `n & -n`               |
| 10      | Binary Processing | `n & 1`, `n >> 1`      |

---

# 🧠 THE 10 BIT PATTERNS YOU MUST REMEMBER

## Pattern 1 — Odd / Even

```python
n & 1
```

```text
1 → Odd
0 → Even
```

---

## Pattern 2 — K-th Bit

```python
mask = 1 << k
```

Then:

```text
Check  → n & mask
Set    → n | mask
Clear  → n & ~mask
Toggle → n ^ mask
```

---

## Pattern 3 — Power of 2

```python
n > 0 and (n & (n - 1)) == 0
```

---

## Pattern 4 — Remove Lowest Set Bit

```python
n = n & (n - 1)
```

---

## Pattern 5 — Count Set Bits

```python
count = 0

while n:
    n = n & (n - 1)
    count += 1
```

---

## Pattern 6 — Unique Number

```python
result = 0

for x in arr:
    result ^= x
```

---

## Pattern 7 — Missing Number

```python
missing = n

for i in range(n):
    missing ^= i
    missing ^= arr[i]
```

---

## Pattern 8 — XOR Swap

```python
a ^= b
b ^= a
a ^= b
```

Conceptual bit trick; in Python production code, prefer:

```python
a, b = b, a
```

---

## Pattern 9 — Lowest Set Bit

```python
n & -n
```

### Memorize:

> **Lowest set bit → `n & -n`**

---

## Pattern 10 — Process Binary Bits

```python
while n:
    bit = n & 1
    n >>= 1
```

### Memorize:

> **Read last bit → `& 1`**
> **Remove last bit → `>> 1`**

---

# 🏆 BASIC BIT MANIPULATION — FINAL STATUS

### Problems

```text
1  → Odd / Even                         ✅
2  → Check / Set / Clear / Toggle      ✅
3  → Power of 2                         ✅
4  → Count Set Bits                     ✅
5  → Hamming Weight                     ✅
6  → Unique Number                      ✅
7  → Missing Number                     ✅
8  → XOR Swap                           ✅
9  → Lowest Set Bit                     ✅
10 → Binary Representation              ✅
```

# 🟢 BIT MANIPULATION: 10 / 10 COMPLETE

Your current selected problem-bank progress is now:

```text
Arrays              10/10 ✅
Strings             10/10 ✅
Hashing             10/10 ✅
Searching           10/10 ✅
Recursion           10/10 ✅
2D Arrays / Matrix  10/10 ✅
Stack               10/10 ✅
Pattern Printing    10/10 ✅
Bit Manipulation    10/10 ✅
────────────────────────────
TOTAL               90/90 ✅
```

**Important:** this is **90/90 across the 9 topics you've completed in the current problem bank**. Your broader 12-topic basic DSA track still has **Sorting, Queue/Deque, and Linked List** remaining.

### 🔥 Final Bit Recognition Rule

If TopGun gives you a basic bit problem, first ask:

```text
Is it about...
        ↓
Last bit?              → n & 1
K-th bit?              → 1 << k
Power of 2?            → n & (n-1)
Count 1s?              → n & (n-1)
Unique element?        → XOR
Missing element?       → XOR
Lowest 1 bit?          → n & -n
Process binary bits?   → & 1 + >> 1
```

This is the **screening-level bit manipulation core** you should be able to recognize immediately.

Would you like a short mixed quiz covering all 10 bit-manipulation patterns, or should we move on to Sorting next?



Would you like to continue with Problems 5–8 next?
