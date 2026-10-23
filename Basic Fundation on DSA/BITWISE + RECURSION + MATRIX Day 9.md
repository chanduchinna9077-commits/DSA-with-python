# 🔵 DAY 9

## BITWISE + RECURSION + MATRIX

### Problems 81–90

```text
Even Using Bitwise
Count Set Bits
Single Number
Power of Two
Bit Operations
Recursive Factorial
Recursive String Reverse
Star Pattern
Matrix Transpose
Diagonal Sum
```

### 🎯 Skill

**Bit manipulation + recursion + 2D arrays**


# 🟠 CR2 — DAY 9: BITWISE + RECURSION + MATRIX

# SESSION 1 — Problems 81–83

You have completed **80/100**.

Day 9 changes the skill set slightly. We are not trying to become competitive programmers. We are learning the **small set of bitwise patterns that repeatedly appear in placement coding**, plus basic recursion.

## 🎯 Today's Problems

| #  | Problem                                | Difficulty      | LeetCode                     |
| -- | -------------------------------------- | --------------- | ---------------------------- |
| 81 | Check Even Using Bitwise AND           | 🟢 Basic        | ❌ No exact canonical LC      |
| 82 | Count Set Bits                         | 🟢 Basic        | 🔗 LC 191 — Number of 1 Bits |
| 83 | Single Non-Repeating Element Using XOR | 🟢 Basic–Medium | 🔗 LC 136 — Single Number    |

## 🧠 Today's Core Progression

```text
81 → Understand bitwise AND
        ↓
82 → Count 1-bits
        ↓
83 → XOR cancellation pattern
```

The most important thing today:

> **Do not memorize bitwise tricks blindly. Understand what each bit operation is actually doing.**

---

# 🔥 PROBLEM 81 — CHECK EVEN USING BITWISE AND

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode match.**

This is a fundamental bitwise placement problem.

The mathematical rule is:

```text
Even number → divisible by 2
Odd number  → not divisible by 2
```

But bitwise representation gives us a faster conceptual test.

### The key observation

Look at the **least significant bit (LSB)**.

For positive integers:

```text
Even → last bit = 0
Odd  → last bit = 1
```

Examples:

```text
2  = 10
4  = 100
6  = 110
8  = 1000
```

All end in:

```text
0
```

While:

```text
1 = 1
3 = 11
5 = 101
7 = 111
```

all end in:

```text
1
```

Therefore:

```text
n & 1
```

checks the last bit.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer, determine whether it is even using bitwise AND.

Example:

```text
Input:  14
Output: Even
```

Because:

```text
14 = 1110
 1 = 0001
-----------
     0000
```

Therefore:

```text
14 & 1 = 0
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of:

```text
1 = 0001
```

When we perform:

```text
n & 1
```

all higher bits are compared against `0`.

Only the final bit can survive.

### Example: 10

```text
10 = 1010
 1 = 0001
------------
     0000
```

So:

```text
10 & 1 = 0
```

Even.

### Example: 11

```text
11 = 1011
 1 = 0001
------------
     0001
```

So:

```text
11 & 1 = 1
```

Odd.

### The rule

```text
n & 1 == 0 → Even
n & 1 == 1 → Odd
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Take integer `n`.
2. Perform:

```text
n & 1
```

3. If the result is `0`, return even.
4. Otherwise return odd.

### Pseudocode

```text
if n & 1 == 0:
    return EVEN
else:
    return ODD
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def check_even(n):

    if (n & 1) == 0:
        return True

    return False


# Example
n = 14

if check_even(n):
    print("Even")
else:
    print("Odd")
```

Output:

```text
Even
```

### Short version

Once you understand the logic:

```python
def check_even(n):
    return (n & 1) == 0
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
class Main {

    public static boolean checkEven(int n) {

        return (n & 1) == 0;
    }

    public static void main(String[] args) {

        int n = 14;

        if (checkEven(n)) {
            System.out.println("Even");
        } else {
            System.out.println("Odd");
        }
    }
}
```

Output:

```text
Even
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
n = 14
```

Binary:

```text
14 = 1110
```

Binary representation of `1`:

```text
1 = 0001
```

AND:

```text
   1110
&  0001
--------
   0000
```

Therefore:

```text
14 & 1 = 0
```

Check:

```python
(14 & 1) == 0
```

becomes:

```text
0 == 0
```

True.

Therefore:

```text
14 is Even
```

---

### Another example — 17

```text
17 = 10001
 1 = 00001
------------
     00001
```

Therefore:

```text
17 & 1 = 1
```

So:

```text
17 is Odd
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses the same bitwise operation.

For:

```text
n = 17
```

```text
17 & 1
```

gives:

```text
1
```

Therefore:

```java
(17 & 1) == 0
```

is:

```text
false
```

So the number is odd.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

The operation:

```text
n & 1
```

uses a fixed number of machine-level bit operations.

Therefore in normal algorithmic analysis:

```text
Time = O(1)
Space = O(1)
```

### Final

```text
Time:  O(1)
Space: O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does `n & 1` tell us whether a number is even?

Because `1` has only the least significant bit set.

AND therefore extracts the least significant bit of `n`.

---

### Q2. What does an LSB of 0 mean?

For standard integer binary representation:

```text
LSB = 0 → even
LSB = 1 → odd
```

---

### Q3. Is `% 2` easier?

Yes.

```python
n % 2 == 0
```

is usually easier to read.

But interviewers may explicitly ask for a **bitwise solution**, where:

```python
n & 1
```

is the intended technique.

---

### Q4. Does this work for negative integers?

Yes, with standard two's-complement integer representation, the least significant bit still indicates parity.

For example:

```text
-4 → even
-5 → odd
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 Bitwise Parity Pattern

```text
EVEN?
  ↓
CHECK LAST BIT
  ↓
n & 1
```

Memorize:

```python
(n & 1) == 0
```

### Recognition trigger

> **"Check even/odd using bitwise"**

Immediately think:

```text
& 1
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using OR instead of AND

Wrong:

```python
n | 1
```

We need:

```python
n & 1
```

---

### ❌ Mistake 2 — Thinking `& 1` checks the entire number

It only extracts the **least significant bit**.

---

### ❌ Mistake 3 — Confusing `&` and `and`

These are completely different.

```python
&
```

is **bitwise AND**.

```python
and
```

is **logical AND**.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Check Even Using Bitwise AND
Exact LC → No exact canonical match
Pattern → Bitwise AND
Operation → n & 1
0 → Even
1 → Odd
Time → O(1)
Space → O(1)
```

### 🔥 Master Template

```python
if (n & 1) == 0:
    # even
else:
    # odd
```

---

# 🔥 PROBLEM 82 — COUNT SET BITS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### LeetCode Match

🔥 **LC 191 — Number of 1 Bits — Easy**

This is an actual LeetCode problem and a fundamental bitwise pattern.

### What is a set bit?

A **set bit** is a bit whose value is:

```text
1
```

Example:

```text
13 = 1101
```

There are three `1`s:

```text
1 1 0 1
↑ ↑   ↑
```

Therefore:

```text
Number of set bits = 3
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer, count how many `1`s exist in its binary representation.

Example:

```text
n = 13
```

Binary:

```text
1101
```

Answer:

```text
3
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

There are several methods.

### Method 1 — Convert to binary

```python
bin(n)
```

Then count `1`.

Easy to understand, but not the core bitwise interview technique.

### Method 2 — Check every bit

Repeatedly inspect the last bit:

```text
n & 1
```

then shift:

```text
n >> 1
```

### Method 3 — Brian Kernighan's algorithm

This is the important optimized pattern:

```text
n = n & (n - 1)
```

Every time we execute this, it removes **one set bit**.

Example:

```text
n = 12
```

Binary:

```text
1100
```

`n - 1`:

```text
1011
```

AND:

```text
  1100
& 1011
------
  1000
```

One `1` disappeared.

Do it again:

```text
1000
&
0111
=
0000
```

Two set bits existed.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Brian Kernighan's Algorithm

1. Set `count = 0`.
2. While `n != 0`:

   * Remove the lowest set bit:

```text
n = n & (n - 1)
```

* Increment `count`.

3. Return `count`.

### Pseudocode

```text
count = 0

while n != 0:

    n = n & (n - 1)

    count += 1

return count
```

### Why it works

Each iteration removes exactly **one `1` bit**.

Therefore:

```text
number of iterations
=
number of set bits
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def count_set_bits(n):

    count = 0

    while n != 0:

        # Remove the lowest set bit
        n = n & (n - 1)

        count += 1

    return count


# Example
n = 13

print(count_set_bits(n))
```

Output:

```text
3
```

---

## 🔥 Understanding the critical line

```python
n = n & (n - 1)
```

This is not magic.

Take:

```text
n = 12
```

Binary:

```text
1100
```

Then:

```text
n - 1 = 1011
```

AND:

```text
1100
1011
----
1000
```

One set bit removed.

Again:

```text
1000
0111
----
0000
```

Another set bit removed.

Therefore:

```text
count = 2
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
class Main {

    public static int countSetBits(int n) {

        int count = 0;

        while (n != 0) {

            // Remove the lowest set bit
            n = n & (n - 1);

            count++;
        }

        return count;
    }

    public static void main(String[] args) {

        int n = 13;

        System.out.println(countSetBits(n));
    }
}
```

Output:

```text
3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
n = 13
```

Binary:

```text
1101
```

Initial:

```text
count = 0
```

---

### Iteration 1

```text
n     = 1101
n - 1 = 1100
```

AND:

```text
1101
1100
----
1100
```

New:

```text
n = 1100
count = 1
```

---

### Iteration 2

```text
n     = 1100
n - 1 = 1011
```

AND:

```text
1100
1011
----
1000
```

New:

```text
n = 1000
count = 2
```

---

### Iteration 3

```text
n     = 1000
n - 1 = 0111
```

AND:

```text
1000
0111
----
0000
```

New:

```text
n = 0000
count = 3
```

Loop ends.

Answer:

```text
3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
n = 13
```

Java performs:

```text
1101 → 1100 → 1000 → 0000
```

Count:

```text
1 → 2 → 3
```

Result:

```text
3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
k = number of set bits
```

The loop runs exactly `k` times.

Therefore:

```text
Time = O(k)
```

Since:

```text
k ≤ number of bits
```

for a fixed-width integer, this is extremely efficient.

For a general `w`-bit representation:

```text
O(k), where k ≤ w
```

Space:

```text
O(1)
```

### Final

```text
Time:  O(number of set bits)
Space: O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What does `n & (n - 1)` do?

It removes the **lowest set bit** from `n`.

---

### Q2. Why does `n - 1` change the bits?

Suppose:

```text
n = 1001000
```

The lowest `1` becomes `0`, and the zeros to its right become `1`.

Therefore:

```text
1001000
1000111
```

ANDing them removes that lowest `1`.

---

### Q3. What if `n = 0`?

There are no set bits.

```text
count = 0
```

The loop never executes.

---

### Q4. Is `bin(n).count("1")` valid?

For Python, yes for ordinary non-negative inputs:

```python
bin(n).count("1")
```

But for interviews, the bitwise algorithm demonstrates actual understanding of the underlying technique.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 Lowest Set Bit Removal

Memorize:

```text
n = n & (n - 1)
```

Meaning:

> **Remove one set bit.**

Therefore:

```text
while n != 0:
    n = n & (n - 1)
    count += 1
```

means:

> **Count how many set bits exist.**

### Recognition trigger

> "Count 1s in binary" → `n & (n - 1)`

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Writing

```python
n = n & n - 1
```

Although Python operator precedence may make this parse as intended, **don't write ambiguous bitwise expressions in interviews**.

Write:

```python
n = n & (n - 1)
```

Clearly.

---

### ❌ Mistake 2 — Confusing set bit with set data structure

Here:

```text
set bit = binary digit 1
```

It has nothing to do with Python `set`.

---

### ❌ Mistake 3 — Thinking it removes the highest set bit

It removes the **lowest/rightmost set bit**.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Count Set Bits
LeetCode → LC 191
Difficulty → Easy
Pattern → Bit Manipulation
Key operation → n & (n - 1)
Effect → Removes lowest set bit
Time → O(number of set bits)
Space → O(1)
```

### 🔥 Master Template

```python
count = 0

while n:
    n &= (n - 1)
    count += 1
```

---

# 🔥 PROBLEM 83 — SINGLE NON-REPEATING ELEMENT USING XOR

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### LeetCode Match

🔥 **LC 136 — Single Number — Easy**

This is one of the most important beginner bitwise problems.

### Problem

Every element appears exactly twice except one element.

Find the element that appears only once.

Example:

```text
[4, 1, 2, 1, 2]
```

Answer:

```text
4
```

### Senior Insight

This is a textbook XOR problem.

You need to know these three properties:

```text
x ^ x = 0
x ^ 0 = x
XOR is associative and commutative
```

Therefore:

```text
a ^ b ^ a
```

can be rearranged:

```text
a ^ a ^ b
```

which becomes:

```text
0 ^ b
```

which becomes:

```text
b
```

All pairs cancel.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array where every number appears twice except one number, find the single number.

Example:

```text
nums = [2, 2, 1]
```

Answer:

```text
1
```

Another:

```text
nums = [4, 1, 2, 1, 2]
```

Answer:

```text
4
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine XOR is an **automatic cancellation machine**.

```text
5 ^ 5 → 0
```

So every pair disappears.

Suppose:

```text
[4, 1, 2, 1, 2]
```

XOR everything:

```text
4 ^ 1 ^ 2 ^ 1 ^ 2
```

Rearrange:

```text
4 ^ (1 ^ 1) ^ (2 ^ 2)
```

Cancel pairs:

```text
4 ^ 0 ^ 0
```

Therefore:

```text
4
```

### No sorting.

### No HashMap.

### No extra array.

### No nested loops.

Just XOR.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Initialize:

```text
result = 0
```

2. Traverse every number.
3. XOR it with `result`.
4. Return `result`.

### Pseudocode

```text
result = 0

for x in nums:
    result = result XOR x

return result
```

Why initialize to `0`?

Because:

```text
0 ^ x = x
```

So zero doesn't affect the answer.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def single_number(nums):

    result = 0

    for num in nums:
        result ^= num

    return result


# Example
nums = [4, 1, 2, 1, 2]

print(single_number(nums))
```

Output:

```text
4
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
class Main {

    public static int singleNumber(int[] nums) {

        int result = 0;

        for (int num : nums) {

            result ^= num;
        }

        return result;
    }

    public static void main(String[] args) {

        int[] nums = {4, 1, 2, 1, 2};

        System.out.println(singleNumber(nums));
    }
}
```

Output:

```text
4
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [4, 1, 2, 1, 2]
```

Start:

```text
result = 0
```

---

### Step 1

```text
result = 0 ^ 4
       = 4
```

---

### Step 2

```text
result = 4 ^ 1
```

Binary:

```text
4 = 100
1 = 001
---------
    101
```

Therefore:

```text
result = 5
```

---

### Step 3

```text
result = 5 ^ 2
```

Binary:

```text
5 = 101
2 = 010
---------
    111
```

Therefore:

```text
result = 7
```

---

### Step 4

```text
result = 7 ^ 1
```

```text
7 = 111
1 = 001
---------
    110
```

Therefore:

```text
result = 6
```

---

### Step 5

```text
result = 6 ^ 2
```

```text
6 = 110
2 = 010
---------
    100
```

Therefore:

```text
result = 4
```

Final:

```text
4
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Exactly the same XOR chain:

```text
0
↓ XOR 4
4
↓ XOR 1
5
↓ XOR 2
7
↓ XOR 1
6
↓ XOR 2
4
```

Final:

```text
4
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We visit every element once.

For `n` elements:

```text
Time = O(n)
```

We only store one variable:

```text
result
```

Therefore:

```text
Space = O(1)
```

### Final

```text
Time:  O(n)
Space: O(1)
```

This is much better than using a frequency dictionary when the problem guarantees the exact pair structure.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does XOR solve this?

Because:

```text
x ^ x = 0
```

and:

```text
x ^ 0 = x
```

Every duplicate pair cancels.

---

### Q2. Why initialize `result = 0`?

Because:

```text
0 ^ x = x
```

So the initial value does not affect the final answer.

---

### Q3. Does XOR care about order?

No.

XOR is associative and commutative:

```text
a ^ b = b ^ a
```

and:

```text
(a ^ b) ^ c = a ^ (b ^ c)
```

Therefore we can conceptually group identical values together.

---

### Q4. What if one number appears three times?

Then this exact LC136 technique does **not** apply.

The guarantee:

```text
Every element appears twice except one
```

is essential.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 XOR Cancellation Pattern

Memorize:

```text
x ^ x = 0
x ^ 0 = x
```

Therefore:

```text
pairs disappear
single survives
```

### Master Template

```python
result = 0

for x in nums:
    result ^= x

return result
```

### Recognition trigger

> **"Every element appears twice except one"**

Immediately think:

```text
XOR
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using addition/subtraction

You don't need arithmetic tricks.

XOR directly matches the pair-cancellation property.

---

### ❌ Mistake 2 — Using a set

A set could find the unique value under some formulations, but the intended optimal bitwise solution is XOR with O(1) auxiliary space.

---

### ❌ Mistake 3 — Forgetting the problem guarantee

XOR works because every duplicate occurs exactly twice.

If the input is:

```text
[2,2,2,3]
```

the simple XOR solution does not mean "find the unique frequency-1 value."

---

### ❌ Mistake 4 — Confusing XOR with OR

```text
^ → XOR
| → OR
& → AND
```

They have completely different behavior.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Single Non-Repeating Element
LeetCode → LC 136
Difficulty → Easy
Pattern → XOR cancellation
Key property → x ^ x = 0
Initial value → 0
Time → O(n)
Space → O(1)
```

### 🔥 Master Template

```python
result = 0

for x in nums:
    result ^= x

return result
```

---

# 🧠 DAY 9 — SESSION 1 MASTER PATTERN MAP

You now have **three fundamental bitwise patterns**.

```text
81 → EVEN / ODD
     ↓
     n & 1
     ↓
     CHECK LOWEST BIT
```

```text
82 → COUNT SET BITS
     ↓
     n & (n - 1)
     ↓
     REMOVE LOWEST 1-BIT
```

```text
83 → SINGLE NUMBER
     ↓
     XOR
     ↓
     DUPLICATES CANCEL
```

---

# 🔥 THE BITWISE DECISION TREE

```text
                 BITWISE
                    │
       ┌────────────┼────────────┐
       │            │            │
   Even/Odd      Count 1s     Single Number
       │            │            │
       ▼            ▼            ▼
     n & 1      n&(n-1)          XOR
       │            │            │
       ▼            ▼            ▼
  Last bit     Remove 1-bit   Pairs cancel
```

## Memorize these three lines

```python
# 81 — Parity
n & 1

# 82 — Remove lowest set bit
n &= (n - 1)

# 83 — XOR cancellation
result ^= x
```

These three lines are more important than memorizing the full programs.

---

# 🎯 SESSION 1 — FINAL MASTER TEST

## Problem 81

Without running the code, determine:

```text
n = 26
```

Binary:

```text
11010
```

What is:

```text
26 & 1
```

Is it even or odd?

---

## Problem 82

Count the set bits:

```text
n = 23
```

Binary:

```text
10111
```

Expected:

```text
4
```

---

## Problem 83

Find the single number:

```text
nums = [7, 3, 5, 3, 7]
```

Expected:

```text
5
```

---

# 🧪 🔥 SENIOR TRICK TEST

Identify the pattern **before writing code**.

### A.

> Determine whether `37` is even using bitwise operations.

```text
?
```

### B.

> Count the number of `1`s in the binary representation of `29`.

```text
?
```

### C.

> Every number occurs exactly twice except one. Find the single number.

```text
?
```

### D.

> Remove the lowest set bit from `n`.

```text
?
```

### E.

> Determine whether the least significant bit is set.

```text
?
```

### Expected recognition

```text
A → n & 1
B → n & (n - 1)
C → XOR
D → n & (n - 1)
E → n & 1
```

---

# 📈 CR2 PROGRESS

```text
DAY 1  ██████████ 10/10
DAY 2  ██████████ 20/20
DAY 3  ██████████ 30/30
DAY 4  ██████████ 40/40
DAY 5  ██████████ 50/50
DAY 6  ██████████ 60/60
DAY 7  ██████████ 70/70
DAY 8  ██████████ 80/80

DAY 9
Session 1 → 81–83 ✅
Session 2 → 84–86 ⏳
Session 3 → 87–90 ⏳

TOTAL → 83/100
```

## 🏆 TODAY'S MASTERY CHECK

You should now be able to explain these **without memorizing the answer**:

```text
n & 1
```

→ **extracts the lowest bit**

```text
n & (n - 1)
```

→ **removes the lowest set bit**

```text
a ^ a
```

→ **cancels to zero**

```text
0 ^ a
```

→ **remains a**

### 🔥 CR2 Rule

Don't just memorize:

```python
result ^= x
```

Know **why** it works.

That's what separates:

```text
🟡 Reproduced
```

from:

```text
🟠 Independent
```

and eventually:

```text
🔴 Mastered
```

**Day 9 Session 1 = Problems 81–83 complete.**

Would you like to try the three master-test questions first, or move straight to Day 9 Session 2?


# 🔥 CR2 — DAY 9 — SESSION 2

## Problems 84–86 | Bitwise + Recursion

**Locked execution preserved. No reduction. No mixing with the deeper DSA track.**

### 🎯 Session Scope

| #      | Problem                      | Exact LeetCode                  | Difficulty |
| ------ | ---------------------------- | ------------------------------- | ---------- |
| **84** | Power of Two                 | **LC 231 — Power of Two**       | Easy       |
| **85** | Set / Clear / Toggle Kth Bit | **No exact canonical LC match** | Basic      |
| **86** | Factorial Using Recursion    | **No exact canonical LC match** | Basic      |

---

# 🟦 PROBLEM 84 — POWER OF TWO

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### What are we really checking?

We need to determine whether a number can be written as:

```text
2^0 = 1
2^1 = 2
2^2 = 4
2^3 = 8
2^4 = 16
2^5 = 32
...
```

So valid powers of two look like:

```text
1
2
4
8
16
32
64
128
...
```

### 🔥 The important binary observation

Every positive power of 2 has **exactly one `1` bit**.

```text
1  → 0001
2  → 0010
4  → 0100
8  → 1000
16 → 10000
```

Now look at:

```text
n - 1
```

For a power of two:

```text
8  = 1000
7  = 0111
```

Therefore:

```text
1000
&
0111
----
0000
```

So:

```python
n & (n - 1) == 0
```

is the key test.

### ⚠️ Critical condition

`0` must be rejected.

Because:

```python
0 & (-1) == 0
```

but `0` is **not** a power of two.

Therefore:

```python
n > 0 and (n & (n - 1)) == 0
```

### 🎯 Senior pattern recognition

When you see:

> "Is this number a power of 2?"

Immediately think:

```text
positive + exactly one set bit
             ↓
      n & (n - 1)
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Problem

Given an integer `n`, determine whether it is a power of two.

### Examples

```text
Input: 16
Output: True
```

Because:

```text
16 = 2^4
```

---

```text
Input: 18
Output: False
```

Because:

```text
18 is not 2^k
```

---

```text
Input: 1
Output: True
```

Because:

```text
1 = 2^0
```

---

```text
Input: 0
Output: False
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Take:

```text
n = 16
```

Binary:

```text
16 = 10000
```

Then:

```text
15 = 01111
```

AND:

```text
  10000
& 01111
-------
  00000
```

Therefore:

```text
16 → Power of Two
```

Now:

```text
n = 18
```

Binary:

```text
18 = 10010
17 = 10001
```

AND:

```text
  10010
& 10001
-------
  10000
```

Result is not zero.

Therefore:

```text
18 → NOT Power of Two
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Algorithm

1. Receive `n`.
2. Check whether `n > 0`.
3. Calculate:

   ```text
   n & (n - 1)
   ```
4. If the result is `0`, return `True`.
5. Otherwise return `False`.

### Pseudocode

```text
IF n <= 0:
    return False

IF n & (n - 1) == 0:
    return True

return False
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_power_of_two(n):
    return n > 0 and (n & (n - 1)) == 0


# Test
print(is_power_of_two(16))
print(is_power_of_two(18))
print(is_power_of_two(1))
print(is_power_of_two(0))
```

### Output

```text
True
False
True
False
```

### 🧠 Line-by-line

```python
n > 0
```

Rejects:

```text
0
negative numbers
```

Then:

```python
n & (n - 1)
```

checks whether only one bit is set.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static boolean isPowerOfTwo(int n) {

        return n > 0 && (n & (n - 1)) == 0;
    }

    public static void main(String[] args) {

        System.out.println(isPowerOfTwo(16));
        System.out.println(isPowerOfTwo(18));
        System.out.println(isPowerOfTwo(1));
        System.out.println(isPowerOfTwo(0));
    }
}
```

### Output

```text
true
false
true
false
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

### Example 1

```text
n = 16
```

Binary:

```text
n     = 10000
n - 1 = 01111
```

Operation:

```text
  10000
& 01111
-------
  00000
```

Therefore:

```text
n > 0 → True
AND result == 0 → True

Answer = True
```

### Example 2

```text
n = 20
```

```text
20 = 10100
19 = 10011
```

```text
  10100
& 10011
-------
  10000
```

Result:

```text
10000 != 00000
```

Therefore:

```text
False
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses exactly the same bitwise operation:

```java
(n & (n - 1))
```

For:

```text
n = 8
```

```text
8  = 1000
7  = 0111
```

```text
1000
0111
----
0000
```

Result:

```text
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

The solution performs:

```text
constant number of operations
```

Therefore:

### Time

```text
O(1)
```

### Space

```text
O(1)
```

No loop.

No extra data structure.

### Interview answer

> "I use the property that a positive power of two has exactly one set bit. Applying `n & (n-1)` removes the lowest set bit, so the result is zero exactly when only one bit was set."

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does `n & (n-1)` work?

Because subtracting `1` from a number flips its lowest set bit from `1` to `0` and turns all lower zero/affected bits into `1`.

For:

```text
1000
0111
```

the AND becomes:

```text
0000
```

for a number containing only one set bit.

---

### Q2. Why do we need `n > 0`?

Because:

```text
0
```

is not a power of two.

---

### Q3. Is `1` a power of two?

Yes.

```text
1 = 2^0
```

---

### Q4. What is the time complexity?

```text
O(1)
```

because there is no loop.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

| Problem Type          | Pattern                    |
| --------------------- | -------------------------- |
| Even/odd              | `n & 1`                    |
| Remove lowest set bit | `n & (n-1)`                |
| Count set bits        | Repeated `n & (n-1)`       |
| Power of two          | `n > 0 and n & (n-1) == 0` |
| Single number         | XOR                        |

### 🔥 Bitwise mini-template

```text
Parity?
    ↓
n & 1

Power of 2?
    ↓
n > 0 AND n & (n-1) == 0

Remove lowest 1?
    ↓
n & (n-1)

Count 1s?
    ↓
repeat n & (n-1)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

```python
n & (n - 1) == 0
```

without considering `n <= 0`.

Use:

```python
n > 0 and (n & (n - 1)) == 0
```

---

### ❌ Mistake 2

Thinking:

```text
All even numbers are powers of 2.
```

Wrong.

```text
6 → even
10 → even
12 → even
18 → even
```

but none are powers of two.

---

### ❌ Mistake 3

Confusing:

```python
&
```

with:

```python
and
```

`&` → bitwise AND

`and` → logical AND

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
POWER OF TWO
     ↓
Positive?
     ↓
Exactly one set bit?
     ↓
n & (n-1) == 0
```

### 🔥 Memorize this:

```python
return n > 0 and (n & (n - 1)) == 0
```

### Exact LeetCode Match

**LC 231 — Power of Two — Easy** ✅

---

# 🟦 PROBLEM 85 — SET / CLEAR / TOGGLE KTH BIT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem is about **directly manipulating one bit** of a number.

Suppose:

```text
n = 10
```

Binary:

```text
1010
```

We want to manipulate the **k-th bit**.

The most important tool is:

```text
1 << k
```

This creates a **bit mask** with exactly one `1`.

For:

```text
k = 2
```

```text
1 << 2
```

gives:

```text
0100
```

That mask allows us to target only bit 2.

### Three operations

```text
SET
CLEAR
TOGGLE
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Assume **0-based indexing from the right**.

Example:

```text
n = 10

Binary:
1010
 ↑↑↑↑
 3 2 1 0
```

So:

```text
bit 0 = 0
bit 1 = 1
bit 2 = 0
bit 3 = 1
```

We need to perform:

### SET kth bit

Make kth bit:

```text
0 → 1
1 → 1
```

### CLEAR kth bit

Make kth bit:

```text
0 → 0
1 → 0
```

### TOGGLE kth bit

Flip:

```text
0 → 1
1 → 0
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

## 1️⃣ SET

Use:

```text
n | (1 << k)
```

Why?

OR with `1`:

```text
0 | 1 = 1
1 | 1 = 1
```

Therefore the targeted bit becomes `1`.

---

## 2️⃣ CLEAR

Use:

```text
n & ~(1 << k)
```

Why?

The mask:

```text
1 << k
```

has a `1` at position k.

NOT changes it into `0` at position k.

Then AND with `0` forces that bit to zero.

---

## 3️⃣ TOGGLE

Use:

```text
n ^ (1 << k)
```

XOR has:

```text
0 ^ 1 = 1
1 ^ 1 = 0
```

Therefore it flips the bit.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### SET

1. Create mask:

   ```text
   mask = 1 << k
   ```
2. OR with number:

   ```text
   n | mask
   ```
3. Return result.

### CLEAR

1. Create mask:

   ```text
   mask = 1 << k
   ```
2. Invert mask:

   ```text
   ~mask
   ```
3. AND with number:

   ```text
   n & ~mask
   ```

### TOGGLE

1. Create mask:

   ```text
   mask = 1 << k
   ```
2. XOR:

   ```text
   n ^ mask
   ```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def set_bit(n, k):
    return n | (1 << k)


def clear_bit(n, k):
    return n & ~(1 << k)


def toggle_bit(n, k):
    return n ^ (1 << k)


# Example
n = 10
k = 1

print("Original:", n)
print("Set:", set_bit(n, k))
print("Clear:", clear_bit(n, k))
print("Toggle:", toggle_bit(n, k))
```

### Output

```text
Original: 10
Set: 10
Clear: 8
Toggle: 8
```

Why SET remains 10?

```text
10 = 1010
k=1 → bit 1 already equals 1

1010
OR
0010
----
1010
```

So:

```text
10 → 10
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static int setBit(int n, int k) {
        return n | (1 << k);
    }

    static int clearBit(int n, int k) {
        return n & ~(1 << k);
    }

    static int toggleBit(int n, int k) {
        return n ^ (1 << k);
    }

    public static void main(String[] args) {

        int n = 10;
        int k = 1;

        System.out.println("Original: " + n);
        System.out.println("Set: " + setBit(n, k));
        System.out.println("Clear: " + clearBit(n, k));
        System.out.println("Toggle: " + toggleBit(n, k));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
n = 10
k = 1
```

Binary:

```text
n = 1010
```

### SET

Mask:

```text
1 << 1 = 0010
```

Operation:

```text
  1010
| 0010
------
  1010
```

Result:

```text
10
```

---

### CLEAR

Mask:

```text
0010
```

NOT mask:

```text
...1101
```

For the relevant bits:

```text
1010
1101
----
1000
```

Result:

```text
8
```

---

### TOGGLE

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

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs the same bitwise operations.

For:

```text
n = 12
k = 2
```

Binary:

```text
12 = 1100
```

Bit 2:

```text
1100
  ↑
```

Mask:

```text
1 << 2 = 0100
```

### SET

```text
1100
0100
----
1100
```

Result:

```text
12
```

### CLEAR

```text
1100
1011
----
1000
```

Result:

```text
8
```

### TOGGLE

```text
1100
0100
----
1000
```

Result:

```text
8
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Each operation performs a constant number of bitwise operations.

Therefore:

### Time

```text
O(1)
```

### Space

```text
O(1)
```

No loops.

No additional data structures.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. How do you set the kth bit?

```python
n | (1 << k)
```

---

### Q2. How do you clear the kth bit?

```python
n & ~(1 << k)
```

---

### Q3. How do you toggle the kth bit?

```python
n ^ (1 << k)
```

---

### Q4. Why do we use `1 << k`?

It creates a mask where only bit `k` is set.

Example:

```text
k = 3

0001 << 3
=
1000
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

| Operation      | Formula         |
| -------------- | --------------- |
| Check kth bit  | `(n >> k) & 1`  |
| Set kth bit    | `n \| (1 << k)` |
| Clear kth bit  | `n & ~(1 << k)` |
| Toggle kth bit | `n ^ (1 << k)`  |

### 🔥 Master this table.

This is the actual reusable bitwise pattern.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Forgetting zero-based indexing

Usually:

```text
rightmost bit = bit 0
```

not bit 1.

---

### ❌ Mistake 2 — Using arithmetic instead of a mask

Don't manually calculate:

```text
2^k
```

Think:

```python
1 << k
```

---

### ❌ Mistake 3 — Confusing SET and TOGGLE

SET:

```text
0 → 1
1 → 1
```

TOGGLE:

```text
0 → 1
1 → 0
```

---

### ❌ Mistake 4 — Confusing CLEAR and TOGGLE

CLEAR always produces:

```text
0
```

TOGGLE flips the current state.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Memorize:

```python
mask = 1 << k

SET:
n | mask

CLEAR:
n & ~mask

TOGGLE:
n ^ mask
```

### Exact LeetCode Match

**No exact canonical LeetCode problem for this exact three-operation placement exercise.**

---

# 🟦 PROBLEM 86 — FACTORIAL USING RECURSION

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Factorial is:

```text
n! = n × (n-1) × (n-2) × ... × 1
```

Examples:

```text
5! = 5 × 4 × 3 × 2 × 1
   = 120
```

The recursive definition is:

```text
n! = n × (n-1)!
```

Eventually:

```text
1! = 1
0! = 1
```

That final condition is called the **base case**.

### 🔥 The recursive thinking pattern

Every recursive function needs:

```text
BASE CASE
+
SMALLER SUBPROBLEM
```

For factorial:

```text
factorial(n)
    ↓
n × factorial(n-1)
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Problem

Calculate:

```text
n!
```

using recursion.

### Example

```text
Input:
5

Output:
120
```

Because:

```text
5!
= 5 × 4!
= 5 × 4 × 3!
= 5 × 4 × 3 × 2!
= 5 × 4 × 3 × 2 × 1!
= 120
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine asking:

> "What is 5 factorial?"

Instead of solving everything immediately:

```text
5! = 5 × 4!
```

Then:

```text
4! = 4 × 3!
```

Then:

```text
3! = 3 × 2!
```

Then:

```text
2! = 2 × 1!
```

Then:

```text
1! = 1
```

Now the recursion returns upward.

```text
1! = 1
2! = 2 × 1 = 2
3! = 3 × 2 = 6
4! = 4 × 6 = 24
5! = 5 × 24 = 120
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Define `factorial(n)`.
2. Check whether `n <= 1`.
3. If yes, return `1`.
4. Otherwise return:

   ```text
   n * factorial(n-1)
   ```
5. Recursive calls continue until the base case.
6. Results return backward through the call stack.

### Pseudocode

```text
factorial(n):

    if n <= 1:
        return 1

    return n * factorial(n - 1)
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def factorial(n):

    # Base case
    if n <= 1:
        return 1

    # Recursive case
    return n * factorial(n - 1)


# Test
print(factorial(5))
print(factorial(0))
```

### Output

```text
120
1
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static long factorial(int n) {

        // Base case
        if (n <= 1) {
            return 1;
        }

        // Recursive case
        return n * factorial(n - 1);
    }

    public static void main(String[] args) {

        System.out.println(factorial(5));
        System.out.println(factorial(0));
    }
}
```

### Output

```text
120
1
```

### Why `long`?

Factorials grow extremely quickly.

Using `long` provides a larger integer range than Java `int`.

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Let's calculate:

```text
factorial(5)
```

### Call phase

```text
factorial(5)
↓
5 × factorial(4)

factorial(4)
↓
4 × factorial(3)

factorial(3)
↓
3 × factorial(2)

factorial(2)
↓
2 × factorial(1)

factorial(1)
↓
1
```

Now recursion returns.

### Return phase

```text
factorial(1) = 1

factorial(2)
= 2 × 1
= 2

factorial(3)
= 3 × 2
= 6

factorial(4)
= 4 × 6
= 24

factorial(5)
= 5 × 24
= 120
```

### Call-stack view

| Call           |        Waiting for |
| -------------- | -----------------: |
| `factorial(5)` | `5 × factorial(4)` |
| `factorial(4)` | `4 × factorial(3)` |
| `factorial(3)` | `3 × factorial(2)` |
| `factorial(2)` | `2 × factorial(1)` |
| `factorial(1)` |                `1` |

Then:

```text
↑ 1
↑ 2
↑ 6
↑ 24
↑ 120
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
factorial(4)
```

Call stack:

```text
factorial(4)
→ factorial(3)
→ factorial(2)
→ factorial(1)
```

Base case:

```text
factorial(1) = 1
```

Return:

```text
factorial(2) = 2
factorial(3) = 6
factorial(4) = 24
```

Final answer:

```text
24
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For:

```text
factorial(n)
```

we make one recursive call for each value:

```text
n
n-1
n-2
...
1
```

So there are approximately `n` function calls.

### Time

```text
O(n)
```

### Space

The recursion stack contains approximately `n` active calls:

```text
O(n)
```

### Important interview distinction

The algorithm does not create an explicit array or list, but recursion itself consumes stack memory.

Therefore:

```text
Time  = O(n)
Space = O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the base case?

```python
if n <= 1:
    return 1
```

It stops infinite recursion.

---

### Q2. What happens without the base case?

The function keeps calling itself:

```text
factorial(5)
factorial(4)
factorial(3)
...
```

Eventually it causes a recursion/stack overflow.

---

### Q3. Why is `0! = 1`?

It is defined mathematically as `1`, and it also makes factorial's recursive relationship work consistently.

---

### Q4. What is the space complexity?

```text
O(n)
```

because of the recursion call stack.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recursive template

```python
def function(problem):

    if base_case:
        return answer

    return current_work + function(smaller_problem)
```

For factorial:

```python
def factorial(n):

    if n <= 1:
        return 1

    return n * factorial(n - 1)
```

### 🔥 Recognition trigger

When the problem says:

> "Solve using recursion"

Ask:

```text
1. What is the smallest case?
2. What is the recursive relationship?
3. Does each call move toward the base case?
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — No base case

```python
def factorial(n):
    return n * factorial(n - 1)
```

Wrong.

---

### ❌ Mistake 2 — Wrong recursive direction

```python
factorial(n + 1)
```

moves away from the base case.

Correct:

```python
factorial(n - 1)
```

---

### ❌ Mistake 3 — Incorrect base case

```python
if n == 0:
    return 0
```

Wrong.

Correct:

```python
if n <= 1:
    return 1
```

---

### ❌ Mistake 4 — Forgetting recursion uses stack memory

Even without an explicit data structure:

```text
O(n)
```

stack space is used.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Core formula

```text
n! = n × (n-1)!
```

### Base case

```python
if n <= 1:
    return 1
```

### Recursive case

```python
return n * factorial(n - 1)
```

### Complexity

```text
Time  → O(n)
Space → O(n)
```

### Exact LeetCode Match

**No exact canonical LeetCode match for this basic recursion exercise.**

---

# 🧠 DAY 9 — SESSION 2 MASTER PATTERN MAP

You now have:

```text
81 → Parity
     n & 1

82 → Count Set Bits
     n & (n-1)

83 → Single Number
     XOR

84 → Power of Two
     n > 0 AND n & (n-1) == 0

85 → Bit Manipulation
     SET    → n | (1 << k)
     CLEAR  → n & ~(1 << k)
     TOGGLE → n ^ (1 << k)

86 → Recursion
     BASE CASE
     +
     SMALLER SUBPROBLEM
```

# 🔥 THE 6 FORMULAS YOU MUST KNOW

```python
# 1. Check even
n & 1 == 0

# 2. Remove lowest set bit
n & (n - 1)

# 3. Power of two
n > 0 and (n & (n - 1)) == 0

# 4. Set kth bit
n | (1 << k)

# 5. Clear kth bit
n & ~(1 << k)

# 6. Toggle kth bit
n ^ (1 << k)
```

---

# 🧪 SESSION 2 — NO-SOLUTION MASTER TEST

**Do these independently. Do NOT look back at the solutions.**

## Test 1 — Power of Two

Write a Python function:

```text
is_power_of_two(n)
```

Test:

```text
1
2
8
16
18
0
```

Expected:

```text
True
True
True
True
False
False
```

---

## Test 2 — Set Bit

Given:

```text
n = 8
k = 1
```

Binary:

```text
1000
```

Set bit `1`.

Expected:

```text
1010
```

Decimal:

```text
10
```

---

## Test 3 — Clear Bit

Given:

```text
n = 14
k = 2
```

```text
14 = 1110
```

Clear bit 2.

Expected:

```text
1010
```

Decimal:

```text
10
```

---

## Test 4 — Toggle Bit

Given:

```text
n = 10
k = 1
```

```text
1010
```

Toggle bit 1.

Expected:

```text
1000
```

Decimal:

```text
8
```

---

## Test 5 — Recursion

Write:

```python
factorial(n)
```

for:

```text
0
1
3
5
7
```

Expected:

```text
1
1
6
120
5040
```

---

# 🎯 SESSION 2 MASTERY CHECK

Before moving to Session 3:

### 🟢 Understood

You can explain the idea.

### 🟡 Reproduced

You can rewrite the code after seeing the pattern.

### 🟠 Independent

You can solve the master tests without looking.

### 🔴 Mastered

You can solve them **and explain why the formula works**, identify the pattern from a new question, and handle edge cases.

**Target for CR2: 🔴 Mastered.**

---

# 📊 CR2 PROGRESS

```text
DAY 1  → 10/10 ✅
DAY 2  → 20/20 ✅
DAY 3  → 30/30 ✅
DAY 4  → 40/40 ✅
DAY 5  → 50/50 ✅
DAY 6  → 60/60 ✅
DAY 7  → 70/70 ✅
DAY 8  → 80/80 ✅

DAY 9
Session 1 → 81–83 ✅
Session 2 → 84–86 ✅
Session 3 → 87–90 ⏳

TOTAL → 86/100
REMAINING → 14
```

**Do not move to Session 3 until you can reproduce Problems 84–86 independently.**

Would you like to start with the Session 2 master test, or should I give you a fresh locked execution for Problems 84–86?


# 🔥 CR2 — DAY 9 — SESSION 3

## Problems 87–90 | Recursion + Matrix Fundamentals

**LOCKED EXECUTION PRESERVED.**
No reduction. No mixing with the deeper DSA track.
This completes **Day 9 → 90/100**.

---

# 📌 SESSION 3 SCOPE

| #      | Problem                        | Exact LeetCode Match                                             | Difficulty |
| ------ | ------------------------------ | ---------------------------------------------------------------- | ---------- |
| **87** | Reverse String Using Recursion | No exact canonical LC match for this exact recursive formulation | Basic      |
| **88** | Right-Angled Star Pattern      | No exact LC match                                                | Basic      |
| **89** | Transpose Matrix               | No exact canonical LC match for this exact placement formulation | Basic      |
| **90** | Main Diagonal Sum              | No exact canonical LC match for this basic formulation           | Basic      |

---

# 🟦 PROBLEM 87 — REVERSE STRING USING RECURSION

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The goal is simple:

```text
Input:
"hello"

Output:
"olleh"
```

But the important part is:

> **We must use recursion.**

The key recursive idea is:

```text
reverse("hello")
```

Instead of trying to reverse everything at once:

```text
"hello"
↓
"o" + reverse("hell")
```

Then:

```text
reverse("hell")
↓
"l" + reverse("hel")
```

Eventually:

```text
reverse("h")
↓
"h"
```

### 🔥 Pattern

For recursive string reversal:

```text
last character
+
reverse(remaining string)
```

### Senior recognition

Whenever recursion asks you to reverse something, think:

```text
Take one character
+
Solve the smaller string
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, reverse it using recursion.

### Example

```text
Input:
"python"

Output:
"nohtyp"
```

### Base case

A string with:

```text
0 or 1 character
```

is already reversed.

Therefore:

```python
if len(s) <= 1:
    return s
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Consider:

```text
"CAT"
```

The last character is:

```text
T
```

Remaining:

```text
"CA"
```

Therefore:

```text
reverse("CAT")
=
"T" + reverse("CA")
```

Then:

```text
reverse("CA")
=
"A" + reverse("C")
```

And:

```text
reverse("C")
=
"C"
```

Return upward:

```text
C
AC
TAC
```

Final:

```text
TAC
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Receive string `s`.
2. Check if its length is `0` or `1`.
3. If yes, return `s`.
4. Take the last character:

   ```text
   s[-1]
   ```
5. Recursively reverse everything except the last character:

   ```text
   s[:-1]
   ```
6. Put the last character before the reversed smaller string.
7. Return the result.

### Pseudocode

```text
reverse(s):

    if length(s) <= 1:
        return s

    return s[last] + reverse(s without last character)
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def reverse_string(s):

    # Base case
    if len(s) <= 1:
        return s

    # Recursive case:
    # Put the last character first,
    # then reverse the remaining string.
    return s[-1] + reverse_string(s[:-1])


# Test
print(reverse_string("hello"))
print(reverse_string("python"))
print(reverse_string("a"))
print(reverse_string(""))
```

### Output

```text
olleh
nohtyp
a

```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static String reverseString(String s) {

        // Base case
        if (s.length() <= 1) {
            return s;
        }

        // Last character + reverse remaining string
        return s.charAt(s.length() - 1)
                + reverseString(s.substring(0, s.length() - 1));
    }

    public static void main(String[] args) {

        System.out.println(reverseString("hello"));
        System.out.println(reverseString("python"));
        System.out.println(reverseString("a"));
        System.out.println(reverseString(""));
    }
}
```

### Output

```text
olleh
nohtyp
a

```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
s = "CAT"
```

### Call 1

```text
reverse("CAT")
```

Last character:

```text
T
```

Remaining:

```text
CA
```

So:

```text
T + reverse("CA")
```

---

### Call 2

```text
reverse("CA")
```

Last character:

```text
A
```

Remaining:

```text
C
```

So:

```text
A + reverse("C")
```

---

### Call 3

```text
reverse("C")
```

Length = 1.

Base case:

```text
"C"
```

---

### Return phase

```text
reverse("C")
= "C"
```

Then:

```text
reverse("CA")
= "A" + "C"
= "AC"
```

Then:

```text
reverse("CAT")
= "T" + "AC"
= "TAC"
```

### Call-stack table

| Call             | Action                |
| ---------------- | --------------------- |
| `reverse("CAT")` | `"T" + reverse("CA")` |
| `reverse("CA")`  | `"A" + reverse("C")`  |
| `reverse("C")`   | Base case → `"C"`     |
| Return           | `"AC"`                |
| Return           | `"TAC"`               |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
reverseString("ABC")
```

Calls:

```text
reverseString("ABC")
→ "C" + reverseString("AB")

reverseString("AB")
→ "B" + reverseString("A")

reverseString("A")
→ "A"
```

Returning:

```text
"A"
"BA"
"CBA"
```

Final:

```text
CBA
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

There are approximately `n` recursive calls.

Each call creates a smaller string using:

```python
s[:-1]
```

Creating/copying strings costs additional work.

For this simple Python implementation, the practical time complexity is:

```text
O(n²)
```

because the copied strings have lengths approximately:

```text
n + (n-1) + (n-2) + ... + 1
```

which is:

```text
O(n²)
```

Recursion depth:

```text
O(n)
```

So auxiliary stack space is:

```text
O(n)
```

### Important

This is a **recursion-learning exercise**, not the production-optimal way to reverse a large string.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the base case?

```python
if len(s) <= 1:
    return s
```

---

### Q2. Why do we use `s[-1]`?

It gives the last character.

Example:

```text
"HELLO"[-1] = "O"
```

---

### Q3. What does `s[:-1]` mean?

Everything except the last character.

```text
"HELLO"[:-1]
→ "HELL"
```

---

### Q4. What is the space complexity?

Recursion depth is `O(n)`.

So:

```text
O(n)
```

stack space.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recursive reversal template

```python
def reverse_string(s):

    if len(s) <= 1:
        return s

    return s[-1] + reverse_string(s[:-1])
```

### Recognition

```text
Reverse using recursion
        ↓
Take one element
        ↓
Solve smaller problem
        ↓
Combine
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Forgetting the base case.

### ❌ Mistake 2

Using:

```python
s[1:]
```

and then placing the first character incorrectly.

### ❌ Mistake 3

Calling:

```python
reverse_string(s)
```

again instead of:

```python
reverse_string(s[:-1])
```

This never reduces the problem.

### ❌ Mistake 4

Assuming recursive code is automatically faster.

Recursion is a **problem-solving technique**, not automatically an optimization.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Core idea

```text
reverse(s)
=
last character
+
reverse(smaller string)
```

### Template

```python
if len(s) <= 1:
    return s

return s[-1] + reverse(s[:-1])
```

### Complexity

```text
Time  → O(n²) for this slicing-based implementation
Space → O(n)
```

### Exact LeetCode Match

**No exact canonical LeetCode match for this exact recursive placement exercise.**

---

# 🟦 PROBLEM 88 — RIGHT-ANGLED STAR PATTERN

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a basic **nested-loop pattern problem**.

Given:

```text
n = 5
```

we want:

```text
*
**
***
****
*****
```

The important observation:

> Row `i` contains exactly `i` stars.

So:

```text
Row 1 → 1 star
Row 2 → 2 stars
Row 3 → 3 stars
Row 4 → 4 stars
Row 5 → 5 stars
```

### 🔥 Pattern recognition

When you see:

> Print a pattern with rows and columns.

Immediately think:

```text
Outer loop → rows
Inner loop → items inside each row
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given `n`, print a right-angled triangle of stars.

### Example

Input:

```text
5
```

Output:

```text
*
**
***
****
*****
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

For every row:

```text
row = 1
→ print 1 star

row = 2
→ print 2 stars

row = 3
→ print 3 stars
```

Therefore:

```text
for row in range(1, n + 1):
    print(row stars)
```

In Python, the easiest implementation is:

```python
"*" * row
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Read `n`.
2. Start row from `1`.
3. Continue until row `n`.
4. For each row, generate exactly `row` stars.
5. Print the row.
6. Continue to the next row.

### Pseudocode

```text
FOR row = 1 to n:
    PRINT "*" repeated row times
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def right_triangle(n):

    for row in range(1, n + 1):
        print("*" * row)


# Test
right_triangle(5)
```

### Output

```text
*
**
***
****
*****
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static void rightTriangle(int n) {

        for (int row = 1; row <= n; row++) {

            for (int col = 1; col <= row; col++) {
                System.out.print("*");
            }

            System.out.println();
        }
    }

    public static void main(String[] args) {

        rightTriangle(5);
    }
}
```

### Output

```text
*
**
***
****
*****
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

For:

```text
n = 5
```

| Row | Number of stars | Output  |
| --: | --------------: | ------- |
|   1 |               1 | `*`     |
|   2 |               2 | `**`    |
|   3 |               3 | `***`   |
|   4 |               4 | `****`  |
|   5 |               5 | `*****` |

Final:

```text
*
**
***
****
*****
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
n = 3
```

### Outer loop

```text
row = 1
```

Inner loop:

```text
col = 1
```

Print:

```text
*
```

---

`row = 2`

```text
col = 1 → *
col = 2 → *
```

Print:

```text
**
```

---

`row = 3`

```text
col = 1 → *
col = 2 → *
col = 3 → *
```

Print:

```text
***
```

Final:

```text
*
**
***
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Number of stars printed:

```text
1 + 2 + 3 + ... + n
```

This equals:

```text
n(n+1)/2
```

Therefore:

```text
O(n²)
```

time.

Auxiliary space:

```text
O(1)
```

excluding the output itself.

### Why not O(n)?

Because the total number of printed characters is quadratic.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why are there two loops in Java?

Outer loop controls:

```text
rows
```

Inner loop controls:

```text
stars per row
```

---

### Q2. How many stars are printed for `n=5`?

```text
1+2+3+4+5 = 15
```

---

### Q3. Can Python solve it without an inner loop?

Yes:

```python
print("*" * row)
```

---

### Q4. What is the time complexity?

```text
O(n²)
```

because the number of printed stars is approximately `n²/2`.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Pattern

```text
Row i → i stars
```

General structure:

```python
for row in range(1, n + 1):
    print("*" * row)
```

### Nested-loop mental model

```text
Outer loop
   ↓
ROW

Inner loop
   ↓
CONTENT OF ROW
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Printing all stars on one line:

```python
print("*" * n)
```

That produces only one row.

---

### ❌ Mistake 2

Using:

```text
n stars
```

for every row.

The number must increase.

---

### ❌ Mistake 3

Off-by-one:

```python
range(1, n)
```

prints only `n-1` rows.

Correct:

```python
range(1, n + 1)
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Outer loop → rows
Inner logic → stars
Row i → i stars
```

Python:

```python
for row in range(1, n + 1):
    print("*" * row)
```

Complexity:

```text
Time  → O(n²)
Space → O(1) auxiliary
```

### Exact LeetCode Match

**No exact LeetCode match.**

---

# 🟦 PROBLEM 89 — TRANSPOSE MATRIX

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The transpose of a matrix changes:

```text
rows → columns
columns → rows
```

Example:

```text
1 2 3
4 5 6
```

Transpose:

```text
1 4
2 5
3 6
```

### Core rule

```text
original[i][j]
        ↓
transpose[j][i]
```

That is the entire concept.

### 🔥 Recognition trigger

Whenever you see:

> "Transpose a matrix"

think:

```text
swap row index and column index
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an `m × n` matrix, return its transpose.

Example:

```text
Input:

1 2 3
4 5 6
```

Output:

```text
1 4
2 5
3 6
```

Notice:

```text
2 rows × 3 columns
```

becomes:

```text
3 rows × 2 columns
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Original:

```text
      columns
       0 1 2
row 0  1 2 3
row 1  4 5 6
```

Coordinates:

```text
(0,0) → 1
(0,1) → 2
(0,2) → 3

(1,0) → 4
(1,1) → 5
(1,2) → 6
```

Transpose means:

```text
(i,j) → (j,i)
```

Therefore:

```text
(0,0) → (0,0)
(0,1) → (1,0)
(0,2) → (2,0)

(1,0) → (0,1)
(1,1) → (1,1)
(1,2) → (2,1)
```

Result:

```text
1 4
2 5
3 6
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

For an `m × n` matrix:

1. Determine number of rows `m`.
2. Determine number of columns `n`.
3. Create a result matrix of size:

   ```text
   n × m
   ```
4. Visit every original cell `(i,j)`.
5. Put:

   ```text
   matrix[i][j]
   ```

   into:

   ```text
   result[j][i]
   ```
6. Return result.

### Pseudocode

```text
rows = m
columns = n

create result[columns][rows]

for i:
    for j:
        result[j][i] = matrix[i][j]
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def transpose_matrix(matrix):

    rows = len(matrix)
    cols = len(matrix[0])

    # Create transpose matrix
    result = [[0] * rows for _ in range(cols)]

    for i in range(rows):
        for j in range(cols):
            result[j][i] = matrix[i][j]

    return result


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

print(transpose_matrix(matrix))
```

### Output

```text
[[1, 4], [2, 5], [3, 6]]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static int[][] transposeMatrix(int[][] matrix) {

        int rows = matrix.length;
        int cols = matrix[0].length;

        int[][] result = new int[cols][rows];

        for (int i = 0; i < rows; i++) {

            for (int j = 0; j < cols; j++) {

                result[j][i] = matrix[i][j];
            }
        }

        return result;
    }

    static void printMatrix(int[][] matrix) {

        for (int[] row : matrix) {

            for (int value : row) {
                System.out.print(value + " ");
            }

            System.out.println();
        }
    }

    public static void main(String[] args) {

        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6}
        };

        int[][] result = transposeMatrix(matrix);

        printMatrix(result);
    }
}
```

### Output

```text
1 4
2 5
3 6
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
1 2 3
4 5 6
```

Dimensions:

```text
rows = 2
cols = 3
```

Create:

```text
result = 3 × 2
```

Initially:

```text
0 0
0 0
0 0
```

### `i=0, j=0`

```text
matrix[0][0] = 1
```

Place:

```text
result[0][0] = 1
```

---

### `i=0, j=1`

```text
matrix[0][1] = 2
```

Place:

```text
result[1][0] = 2
```

---

### `i=0, j=2`

```text
matrix[0][2] = 3
```

Place:

```text
result[2][0] = 3
```

Current:

```text
1 0
2 0
3 0
```

---

### `i=1, j=0`

```text
matrix[1][0] = 4
```

Place:

```text
result[0][1] = 4
```

---

### `i=1, j=1`

```text
matrix[1][1] = 5
```

Place:

```text
result[1][1] = 5
```

---

### `i=1, j=2`

```text
matrix[1][2] = 6
```

Place:

```text
result[2][1] = 6
```

Final:

```text
1 4
2 5
3 6
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
1 2
3 4
5 6
```

Original dimensions:

```text
3 × 2
```

Result dimensions:

```text
2 × 3
```

Mapping:

```text
matrix[0][0] → result[0][0]
matrix[0][1] → result[1][0]

matrix[1][0] → result[0][1]
matrix[1][1] → result[1][1]

matrix[2][0] → result[0][2]
matrix[2][1] → result[1][2]
```

Result:

```text
1 3 5
2 4 6
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Suppose matrix dimensions are:

```text
m × n
```

There are:

```text
m × n
```

elements.

Every element is visited once.

Therefore:

### Time

```text
O(m × n)
```

### Auxiliary/output space

The result contains:

```text
n × m
```

elements.

Therefore:

```text
O(m × n)
```

space.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What happens to dimensions?

```text
m × n
```

becomes:

```text
n × m
```

---

### Q2. What is the key index transformation?

```text
(i, j) → (j, i)
```

---

### Q3. Can every rectangular matrix be transposed?

Yes.

The dimensions simply swap.

---

### Q4. Can we transpose a square matrix in-place?

Yes, for a square matrix, by swapping:

```text
matrix[i][j]
```

with:

```text
matrix[j][i]
```

for one side of the diagonal.

But for this CR2 problem, the clean general solution uses a new matrix.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Matrix transformation template

```text
Original:
matrix[i][j]

Transpose:
result[j][i]
```

### Recognition

```text
Transpose
    ↓
Swap indexes
    ↓
(i,j) → (j,i)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Creating result with the same dimensions for a rectangular matrix.

Wrong:

```text
2 × 3 → 2 × 3
```

Correct:

```text
2 × 3 → 3 × 2
```

---

### ❌ Mistake 2

Writing:

```python
result[i][j] = matrix[i][j]
```

That copies the matrix.

Transpose requires:

```python
result[j][i] = matrix[i][j]
```

---

### ❌ Mistake 3

Confusing transpose with reversing rows.

Transpose is:

```text
rows ↔ columns
```

not:

```text
reverse each row
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### One formula:

```text
matrix[i][j]
     ↓
result[j][i]
```

Dimensions:

```text
m × n → n × m
```

Complexity:

```text
Time  → O(mn)
Space → O(mn)
```

### Exact LeetCode Match

**No exact canonical LeetCode match for this basic standalone formulation.**

---

# 🟦 PROBLEM 90 — MAIN DIAGONAL SUM

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The **main diagonal** of a square matrix runs:

```text
top-left → bottom-right
```

Example:

```text
1 2 3
4 5 6
7 8 9
```

Main diagonal:

```text
1
   5
      9
```

So:

```text
1 + 5 + 9 = 15
```

### 🔥 Key observation

For a square matrix:

```text
row index = column index
```

Therefore the main diagonal cells are:

```text
matrix[0][0]
matrix[1][1]
matrix[2][2]
...
matrix[n-1][n-1]
```

So:

```python
matrix[i][i]
```

is the key pattern.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a square matrix, calculate the sum of the main diagonal.

### Example

```text
1 2 3
4 5 6
7 8 9
```

Main diagonal:

```text
1 + 5 + 9
```

Answer:

```text
15
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine drawing a line from:

```text
top-left
```

to:

```text
bottom-right
```

The selected coordinates are:

```text
(0,0)
(1,1)
(2,2)
...
```

Notice:

```text
row == column
```

Therefore:

```python
sum += matrix[i][i]
```

That's the entire core idea.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Get matrix size `n`.
2. Initialize `total = 0`.
3. Loop `i` from `0` to `n-1`.
4. Add:

   ```text
   matrix[i][i]
   ```
5. Return `total`.

### Pseudocode

```text
total = 0

for i = 0 to n-1:
    total += matrix[i][i]

return total
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def main_diagonal_sum(matrix):

    total = 0

    for i in range(len(matrix)):
        total += matrix[i][i]

    return total


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(main_diagonal_sum(matrix))
```

### Output

```text
15
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static int mainDiagonalSum(int[][] matrix) {

        int total = 0;

        for (int i = 0; i < matrix.length; i++) {

            total += matrix[i][i];
        }

        return total;
    }

    public static void main(String[] args) {

        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println(mainDiagonalSum(matrix));
    }
}
```

### Output

```text
15
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
1 2 3
4 5 6
7 8 9
```

Start:

```text
total = 0
```

### `i = 0`

```text
matrix[0][0] = 1
```

```text
total = 0 + 1 = 1
```

---

### `i = 1`

```text
matrix[1][1] = 5
```

```text
total = 1 + 5 = 6
```

---

### `i = 2`

```text
matrix[2][2] = 9
```

```text
total = 6 + 9 = 15
```

Final:

```text
15
```

### Trace table

| `i` | `matrix[i][i]` | `total` |
| --: | -------------: | ------: |
|   0 |              1 |       1 |
|   1 |              5 |       6 |
|   2 |              9 |      15 |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
5 2 1
7 3 8
4 6 9
```

Diagonal elements:

```text
matrix[0][0] = 5
matrix[1][1] = 3
matrix[2][2] = 9
```

Sum:

```text
5 + 3 + 9 = 17
```

Output:

```text
17
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For an `n × n` matrix, we visit exactly `n` diagonal elements.

Therefore:

### Time

```text
O(n)
```

### Space

```text
O(1)
```

No extra matrix or data structure is created.

### Important comparison

A full matrix traversal would take:

```text
O(n²)
```

But we only need:

```text
n
```

diagonal elements.

Therefore:

```text
O(n)
```

is sufficient.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What identifies a main-diagonal element?

```text
row index == column index
```

Therefore:

```python
matrix[i][i]
```

---

### Q2. What is the complexity?

```text
O(n)
```

because only `n` diagonal elements are visited.

---

### Q3. Is this valid for a rectangular matrix?

The **main diagonal** can technically be defined up to `min(rows, columns)`, but this CR2 problem assumes a square matrix.

---

### Q4. What is the difference between main and secondary diagonal?

Main diagonal:

```text
(i, i)
```

Secondary diagonal in an `n × n` matrix:

```text
(i, n - 1 - i)
```

Example:

```text
1 2 3
4 5 6
7 8 9
```

Secondary:

```text
3 + 5 + 7
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Main diagonal

```python
matrix[i][i]
```

### Secondary diagonal

```python
matrix[i][n - 1 - i]
```

### 🔥 Recognition

If the problem says:

> "top-left to bottom-right"

think:

```text
[i][i]
```

If it says:

> "top-right to bottom-left"

think:

```text
[i][n-1-i]
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
matrix[i][i + 1]
```

That is not the main diagonal.

---

### ❌ Mistake 2

Using nested loops.

You don't need:

```python
for i:
    for j:
```

because the column is always equal to the row.

---

### ❌ Mistake 3

Confusing main diagonal with secondary diagonal.

Remember:

```text
Main:
[i][i]

Secondary:
[i][n-1-i]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Core formula

```python
matrix[i][i]
```

### Algorithm

```text
total = 0

for i:
    total += matrix[i][i]
```

### Complexity

```text
Time  → O(n)
Space → O(1)
```

### Exact LeetCode Match

**No exact canonical LeetCode match for this basic standalone formulation.**

---

# 🧠 DAY 9 — SESSION 3 MASTER PATTERN MAP

You have now completed:

```text
87 → Recursive String Reversal
     last character + reverse(smaller string)

88 → Star Pattern
     outer loop = rows
     row i = i stars

89 → Matrix Transpose
     (i,j) → (j,i)

90 → Main Diagonal
     matrix[i][i]
```

---

# 🔥 DAY 9 — COMPLETE PATTERN MAP

```text
81 → EVEN
     n & 1

82 → COUNT SET BITS
     n & (n-1)

83 → SINGLE NUMBER
     XOR

84 → POWER OF TWO
     n > 0
     AND
     n & (n-1) == 0

85 → BIT MANIPULATION

     SET
     n | (1 << k)

     CLEAR
     n & ~(1 << k)

     TOGGLE
     n ^ (1 << k)

86 → RECURSION
     BASE CASE
     +
     SMALLER PROBLEM

87 → RECURSIVE REVERSE
     s[-1] + reverse(s[:-1])

88 → PATTERN
     row i → i stars

89 → TRANSPOSE
     result[j][i] = matrix[i][j]

90 → MAIN DIAGONAL
     matrix[i][i]
```

---

# 🧪 DAY 9 — FINAL NO-SOLUTION MASTER TEST

**Do not look at the solutions above while solving.**

## Test 87 — Recursive Reverse

Write:

```python
reverse_string(s)
```

for:

```text
"HELLO"
```

Expected:

```text
"OLLEH"
```

Also test:

```text
""
"A"
"AB"
```

---

## Test 88 — Pattern

For:

```text
n = 6
```

produce:

```text
*
**
***
****
*****
******
```

**Do it without looking at the code.**

---

## Test 89 — Transpose

Given:

```text
1 2 3 4
5 6 7 8
```

Produce:

```text
1 5
2 6
3 7
4 8
```

### Mental test

Identify:

```text
matrix[0][2]
```

Where does it go after transpose?

Answer:

```text
result[2][0]
```

---

## Test 90 — Main Diagonal

Given:

```text
10 20 30
40 50 60
70 80 90
```

Calculate the main diagonal sum.

Expected:

```text
150
```

Because:

```text
10 + 50 + 90 = 150
```

---

# 🧠 DAY 9 — FINAL MIXED RECOGNITION TEST

Identify the correct pattern **before writing code**.

### A.

> "Determine whether 64 is a power of two."

```text
Your pattern:
?
```

### B.

> "Turn bit 3 ON."

```text
Your pattern:
?
```

### C.

> "Reverse a string using recursion."

```text
Your pattern:
?
```

### D.

> "Print 5 rows where row i has i stars."

```text
Your pattern:
?
```

### E.

> "Convert rows into columns."

```text
Your pattern:
?
```

### F.

> "Add elements from top-left to bottom-right."

```text
Your pattern:
?
```

### Correct recognition

```text
A → n & (n-1)
B → n | (1 << k)
C → recursion + smaller string
D → nested/pattern loop
E → (i,j) → (j,i)
F → matrix[i][i]
```

---

# 📊 CR2 PROGRESS — DAY 9 COMPLETE

```text
DAY 1  → 10/10 ✅
DAY 2  → 20/20 ✅
DAY 3  → 30/30 ✅
DAY 4  → 40/40 ✅
DAY 5  → 50/50 ✅
DAY 6  → 60/60 ✅
DAY 7  → 70/70 ✅
DAY 8  → 80/80 ✅
DAY 9  → 90/90 ✅

━━━━━━━━━━━━━━━━━━━━━━
TOTAL   → 90/100
REMAIN  → 10
━━━━━━━━━━━━━━━━━━━━━━
```

## 🔴 DAY 9 TARGET

Do **not** consider Day 9 truly mastered merely because you read the solutions.

You should be able to reproduce from memory:

```text
n & 1
n & (n-1)
n ^ x

n | (1 << k)
n & ~(1 << k)
n ^ (1 << k)

recursive base case
recursive smaller problem

matrix[i][j] → matrix[j][i]
matrix[i][i]
```

**Day 9 = 90/100 complete.**

**Next locked syllabus: Day 10 — Final Mixed Placement Challenge, Problems 91–100.**

Would you like to attempt the Day 9 final mixed recognition test first, or jump straight into Day 10?
