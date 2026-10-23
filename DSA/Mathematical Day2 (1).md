

# 🔵 DAY 2

## MATHEMATICAL LOGIC

### Problems 11–20

```text
Happy Number
Strong Number
Fibonacci
Nth Fibonacci
Factors
Perfect Square
Factorial
Power
Decimal → Binary
Binary → Decimal
```

### 🎯 Skill

**Mathematical reasoning + implementation**


# 🔥 DAY 2 — SESSION 1

## Mathematical Logic — Problems 11–13

We continue with the **exact locked depth**. No reduction.

### 🎯 Today's Session

| #  | Problem          | Core Pattern                                           | LeetCode              |
| -- | ---------------- | ------------------------------------------------------ | --------------------- |
| 11 | Happy Number     | Repeated digit-square transformation + cycle detection | LC 202 — Easy         |
| 12 | Strong Number    | Factorial of each digit + accumulation                 | No exact canonical LC |
| 13 | Fibonacci Series | Iterative recurrence                                   | LC 509 — Easy         |

### Session Goal

These 3 problems introduce an important progression:

```text
Happy Number
    ↓
Repeated transformation + cycle

Strong Number
    ↓
Digit extraction + factorial

Fibonacci
    ↓
Previous states → next state
```

---

# 🔥 PROBLEM 11 — HAPPY NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact Definition

A number is called a **Happy Number** if repeatedly replacing the number by the sum of the squares of its digits eventually reaches:

```text
1
```

Example:

```text
19
```

First:

```text
1² + 9²
= 1 + 81
= 82
```

Then:

```text
8² + 2²
= 64 + 4
= 68
```

Then:

```text
6² + 8²
= 36 + 64
= 100
```

Then:

```text
1² + 0² + 0²
= 1
```

Therefore:

```text
19 → Happy Number
```

### LeetCode Match

🔥 **LC 202 — Happy Number**

Difficulty: **Easy**

---

## 🚨 Senior Insight: This Is NOT Just a Digit Problem

At first glance, it looks like:

```text
extract digits
→ square digits
→ sum
```

But there is a second layer:

```text
new number
    ↓
new number
    ↓
new number
    ↓
...
```

What if it never reaches `1`?

It can enter a **cycle**.

For example, an unhappy number eventually repeats a previous value.

Therefore the real problem is:

```text
Repeated transformation
+
Cycle detection
```

That is the important interview pattern.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
n = 19
```

Repeatedly calculate:

```text
sum of squares of digits
```

If the process reaches:

```text
1
```

return:

```text
True
```

Otherwise, if a number repeats, return:

```text
False
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine each number is a node:

```text
19 → 82 → 68 → 100 → 1
```

For an unhappy number, eventually you get something like:

```text
2 → 4 → 16 → 37 → ... → 2
                         ↑    |
                         └────┘
```

Once you see the same number again, you know:

> "I've entered a cycle. I'll never reach 1."

So we need to remember numbers we've already seen.

Use:

```python
seen = set()
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Create an empty set `seen`.
2. While `n != 1`:

   * If `n` is already in `seen`, a cycle exists.
   * Return `False`.
   * Add `n` to `seen`.
   * Calculate the sum of squares of its digits.
   * Replace `n` with that sum.
3. If `n == 1`, return `True`.

### Digit-square helper

For:

```text
82
```

we calculate:

```text
8² + 2²
= 64 + 4
= 68
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def sum_of_square_digits(n):
    total = 0

    while n > 0:
        digit = n % 10
        total += digit * digit
        n //= 10

    return total


def is_happy(n):

    seen = set()

    while n != 1:

        if n in seen:
            return False

        seen.add(n)

        n = sum_of_square_digits(n)

    return True


n = int(input("Enter a number: "))

if is_happy(n):
    print("Happy Number")
else:
    print("Not a Happy Number")
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {

    static int sumOfSquareDigits(int n) {

        int total = 0;

        while (n > 0) {

            int digit = n % 10;

            total += digit * digit;

            n /= 10;
        }

        return total;
    }

    static boolean isHappy(int n) {

        Set<Integer> seen = new HashSet<>();

        while (n != 1) {

            if (seen.contains(n)) {
                return false;
            }

            seen.add(n);

            n = sumOfSquareDigits(n);
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (isHappy(n)) {
            System.out.println("Happy Number");
        } else {
            System.out.println("Not a Happy Number");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
19
```

Initial:

```text
n = 19
seen = {}
```

### Iteration 1

Is `19` in `seen`?

```text
No
```

Add:

```text
seen = {19}
```

Calculate:

```text
19
↓
1² + 9²
↓
1 + 81
↓
82
```

Now:

```text
n = 82
```

---

### Iteration 2

`82` already seen?

```text
No
```

Add:

```text
seen = {19, 82}
```

Calculate:

```text
8² + 2²
= 64 + 4
= 68
```

Now:

```text
n = 68
```

---

### Iteration 3

Add:

```text
seen = {19, 82, 68}
```

Calculate:

```text
6² + 8²
= 36 + 64
= 100
```

---

### Iteration 4

Add:

```text
seen = {19, 82, 68, 100}
```

Calculate:

```text
1² + 0² + 0²
= 1
```

Now:

```text
n = 1
```

Loop ends.

```text
return True
```

Output:

```text
Happy Number
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs exactly the same transformation:

```text
19
 ↓
82
 ↓
68
 ↓
100
 ↓
1
```

At every step, the `HashSet` records previously visited values.

Since `1` is reached:

```text
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let `k` be the number of transformation steps until either:

```text
1
```

or a repeated value is detected.

Each transformation processes the digits of the current number.

For ordinary integer-sized inputs, the number quickly becomes small.

### Time

General form:

```text
O(k × d)
```

where:

* `k` = number of transformations
* `d` = digits processed per transformation

For fixed-width integers, this is effectively very small.

### Space

The `seen` set stores previously encountered values:

```text
O(k)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we need a set?

Because the process may enter a cycle.

The set lets us detect:

```python
if n in seen:
```

in approximately:

```text
O(1)
```

average lookup time.

---

### Q2. What happens if we don't use cycle detection?

The program could run forever for an unhappy number.

We need a stopping condition other than `n == 1`.

---

### Q3. Can we solve Happy Number without extra space?

Yes.

A more advanced approach uses **Floyd's Cycle Detection**:

```text
slow pointer
fast pointer
```

But for a basic placement round, the `set` solution is clearer and easier to implement correctly.

---

### Q4. What is the important pattern?

Not merely digit extraction.

The bigger pattern is:

```text
Repeated transformation
+
Cycle detection
```

This pattern appears in many problems beyond Happy Number.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Pattern:

```text
number
 ↓
transform(number)
 ↓
new number
 ↓
transform(number)
 ↓
...
```

Whenever you see:

> "Repeat an operation until..."

ask:

### 🚨 Senior question:

> **Can this process enter a cycle?**

If yes:

```text
Set
or
Floyd's Cycle Detection
```

may be useful.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Only checking whether the current number is `1`.

❌ Forgetting cycle detection.

❌ Using `n % 10` but forgetting:

```python
n //= 10
```

❌ Modifying the original input when you still need it later.

❌ Assuming every repeated transformation must eventually reach `1`.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Memorize:

```text
Happy Number
     ↓
Square every digit
     ↓
Sum
     ↓
Repeat
     ↓
1 → Happy
cycle → Not Happy
```

The key senior-level pattern:

```text
Repeated transformation → Cycle Detection
```

---

# 🔥 PROBLEM 12 — STRONG NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A **Strong Number** is a number whose value equals the sum of the factorials of its digits.

Example:

```text
145
```

Calculate:

```text
1! + 4! + 5!
```

```text
1 + 24 + 120
= 145
```

Therefore:

```text
145 → Strong Number
```

There is **no exact canonical LeetCode problem** for this basic standalone definition.

---

## 🧠 Recognition

This is another combination problem.

We already know:

```text
Digit extraction
```

Now combine it with:

```text
Factorial
```

So:

```text
Strong Number
      ↓
Extract digit
      ↓
Factorial(digit)
      ↓
Add
      ↓
Compare with original
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text
145
```

Digits:

```text
1, 4, 5
```

Factorials:

```text
1! = 1
4! = 24
5! = 120
```

Sum:

```text
1 + 24 + 120 = 145
```

Therefore:

```text
Strong Number
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

The biggest observation:

### Digits are only 0–9.

Therefore factorials are tiny and bounded.

We can either calculate factorial each time:

```python
factorial(digit)
```

or precompute:

```text
0! = 1
1! = 1
2! = 2
...
9! = 362880
```

For beginner placement coding, calculating factorial using a helper is perfectly understandable.

For repeated queries, a lookup table is even faster.

### Senior practical choice

For **one number**:

```text
factorial helper
```

is clean.

For **many numbers**:

```text
precomputed factorials
```

is better.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Store original number.
2. Set `total = 0`.
3. Extract the last digit.
4. Calculate its factorial.
5. Add factorial to `total`.
6. Remove the digit.
7. Repeat until number becomes zero.
8. Compare `total` with original.
9. Equal → Strong Number.
10. Otherwise → Not Strong.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def factorial(n):

    result = 1

    for i in range(2, n + 1):
        result *= i

    return result


def is_strong(n):

    if n < 0:
        return False

    original = n
    total = 0

    if n == 0:
        total = factorial(0)

    while n > 0:

        digit = n % 10

        total += factorial(digit)

        n //= 10

    return total == original


n = int(input("Enter a number: "))

if is_strong(n):
    print("Strong Number")
else:
    print("Not a Strong Number")
```

### Example

```text
Input:
145

Output:
Strong Number
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static int factorial(int n) {

        int result = 1;

        for (int i = 2; i <= n; i++) {
            result *= i;
        }

        return result;
    }

    static boolean isStrong(int n) {

        if (n < 0) {
            return false;
        }

        int original = n;
        int total = 0;

        if (n == 0) {
            total = factorial(0);
        }

        while (n > 0) {

            int digit = n % 10;

            total += factorial(digit);

            n /= 10;
        }

        return total == original;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (isStrong(n)) {
            System.out.println("Strong Number");
        } else {
            System.out.println("Not a Strong Number");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
145
```

Initial:

```text
original = 145
total = 0
n = 145
```

### Iteration 1

Extract:

```text
145 % 10 = 5
```

Calculate:

```text
5! = 120
```

Add:

```text
total = 120
```

Remove digit:

```text
145 // 10 = 14
```

---

### Iteration 2

Extract:

```text
14 % 10 = 4
```

Calculate:

```text
4! = 24
```

Add:

```text
total = 120 + 24
      = 144
```

Remove:

```text
14 // 10 = 1
```

---

### Iteration 3

Extract:

```text
1 % 10 = 1
```

Calculate:

```text
1! = 1
```

Add:

```text
total = 144 + 1
      = 145
```

Remove:

```text
1 // 10 = 0
```

Loop ends.

Compare:

```text
total == original

145 == 145
```

Therefore:

```text
Strong Number
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same sequence:

```text
145
 ↓
5 → 5! = 120
 ↓
4 → 4! = 24
 ↓
1 → 1! = 1
```

Total:

```text
120 + 24 + 1
= 145
```

Therefore:

```text
Strong Number
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
d = number of digits
```

Each digit's factorial requires at most 9 multiplication steps.

Because digit ≤ 9:

```text
9! 
```

is a constant-sized calculation.

Therefore:

### Time

```text
O(d)
```

More formally:

```text
O(d × 9) = O(d)
```

### Space

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is factorial computation effectively constant time here?

Because we're calculating factorials of **digits**, and a decimal digit can only be:

```text
0 to 9
```

So the maximum is:

```text
9!
```

---

### Q2. Can factorials be precomputed?

Yes.

For example:

```python
factorials = [1, 1, 2, 6, 24, 120, 720, 5040, 40320, 362880]
```

Then:

```python
total += factorials[digit]
```

gives constant-time factorial lookup.

---

### Q3. Why preserve the original number?

Because `n` is destroyed through:

```python
n //= 10
```

We need the original for comparison.

---

### Q4. What is the main coding pattern?

```text
Digit extraction
+
factorial
+
accumulation
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is another variation of the Day 1 digit skeleton:

```python
while n > 0:

    digit = n % 10

    # special processing

    n //= 10
```

Here:

```python
total += factorial(digit)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Calculating factorial of the entire number instead of each digit.

Wrong:

```text
145!
```

Correct:

```text
1! + 4! + 5!
```

❌ Forgetting `0! = 1`.

❌ Forgetting to preserve original.

❌ Forgetting `n //= 10`.

❌ Confusing Strong Number with Armstrong Number.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Strong Number
      ↓
Extract digit
      ↓
Factorial(digit)
      ↓
Add
      ↓
Compare with original
```

Example:

```text
145
↓
1! + 4! + 5!
↓
1 + 24 + 120
↓
145
```

---

# 🔥 PROBLEM 13 — FIBONACCI SERIES

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

The Fibonacci sequence is a sequence where every number is the sum of the previous two numbers.

Starting with:

```text
0, 1
```

we get:

```text
0
1
1
2
3
5
8
13
21
34
...
```

The recurrence is:

```text
F(n) = F(n-1) + F(n-2)
```

### LeetCode Match

🔥 **LC 509 — Fibonacci Number**

Difficulty: **Easy**

---

## 🚨 Important Distinction

Our Day 2 Problem #13 is:

> **Print Fibonacci Series**

while LC 509 asks:

> **Find the nth Fibonacci number**

They are related, but not exactly the same task.

So we should not falsely call them identical.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
n = 7
```

Print the first 7 Fibonacci numbers:

```text
0 1 1 2 3 5 8
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We only need two previous values:

```text
a = previous
b = current
```

Then:

```text
next = a + b
```

Shift:

```text
a = b
b = next
```

Example:

```text
a = 0
b = 1
```

Next:

```text
0 + 1 = 1
```

Shift:

```text
a = 1
b = 1
```

Next:

```text
1 + 1 = 2
```

Shift:

```text
a = 1
b = 2
```

And continue.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

To print the first `n` terms:

1. Handle `n <= 0`.
2. Set:

```text
a = 0
b = 1
```

3. Repeat `n` times:

   * print `a`
   * calculate `next = a + b`
   * move `a = b`
   * move `b = next`

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def fibonacci_series(n):

    if n <= 0:
        return []

    a = 0
    b = 1

    result = []

    for _ in range(n):

        result.append(a)

        a, b = b, a + b

    return result


n = int(input("Enter number of terms: "))

series = fibonacci_series(n)

print("Fibonacci Series:")

for number in series:
    print(number, end=" ")
```

### Example

```text
Input:
7

Output:
Fibonacci Series:
0 1 1 2 3 5 8
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n <= 0) {
            System.out.println("Invalid number of terms");
            sc.close();
            return;
        }

        long a = 0;
        long b = 1;

        for (int i = 0; i < n; i++) {

            System.out.print(a + " ");

            long next = a + b;

            a = b;
            b = next;
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
n = 7
```

Initial:

```text
a = 0
b = 1
```

### Iteration 1

Print:

```text
0
```

Calculate:

```text
next = 0 + 1 = 1
```

Update:

```text
a = 1
b = 1
```

---

### Iteration 2

Print:

```text
1
```

Calculate:

```text
next = 1 + 1 = 2
```

Update:

```text
a = 1
b = 2
```

---

### Iteration 3

Print:

```text
1
```

Calculate:

```text
next = 1 + 2 = 3
```

Update:

```text
a = 2
b = 3
```

---

### Iteration 4

Print:

```text
2
```

Next:

```text
2 + 3 = 5
```

---

### Iteration 5

Print:

```text
3
```

Next:

```text
3 + 5 = 8
```

---

### Iteration 6

Print:

```text
5
```

Next:

```text
5 + 8 = 13
```

---

### Iteration 7

Print:

```text
8
```

Final output:

```text
0 1 1 2 3 5 8
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java maintains:

```text
a → current Fibonacci number
b → next Fibonacci number
```

State table:

| Iteration |  a |  b | Printed |
| --------: | -: | -: | ------: |
|         1 |  0 |  1 |       0 |
|         2 |  1 |  1 |       1 |
|         3 |  1 |  2 |       1 |
|         4 |  2 |  3 |       2 |
|         5 |  3 |  5 |       3 |
|         6 |  5 |  8 |       5 |
|         7 |  8 | 13 |       8 |

Output:

```text
0 1 1 2 3 5 8
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We generate exactly `n` terms.

### Time

```text
O(n)
```

because the loop executes `n` times.

### Auxiliary Space

The algorithm itself only needs:

```text
a
b
next
```

Therefore:

```text
O(1)
```

However, our Python implementation stores the output in a list:

```python
result = []
```

So its total output-storage space is:

```text
O(n)
```

### Important interview distinction

If we print directly:

```text
O(1)
```

auxiliary space.

If we store all terms:

```text
O(n)
```

additional storage.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the Fibonacci recurrence?

```text
F(n) = F(n-1) + F(n-2)
```

with:

```text
F(0) = 0
F(1) = 1
```

---

### Q2. Why is iterative Fibonacci preferred over naive recursion?

Naive recursion repeatedly recalculates the same values.

Its time complexity is approximately:

```text
O(2^n)
```

The iterative solution is:

```text
O(n)
```

with:

```text
O(1)
```

auxiliary space.

---

### Q3. Can Fibonacci be calculated in O(log n)?

Yes.

For finding a single nth Fibonacci number, advanced methods such as **matrix exponentiation** or **fast doubling** can achieve:

```text
O(log n)
```

But that is unnecessary for this basic placement problem of printing the series.

---

### Q4. Why use two variables?

Because the next Fibonacci number only depends on the previous two:

```text
previous
current
```

We don't need the entire history.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

The key pattern is:

```text
Previous State
+
Current State
↓
Next State
```

This appears everywhere in dynamic programming and iterative algorithms.

For Fibonacci:

```text
a = previous
b = current

next = a + b

a = b
b = next
```

### 🔥 Recognition rule

Whenever you see:

> "Each new value depends on the previous one/two values"

think:

```text
State variables
→ update
→ repeat
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Starting with:

```text
1 1 2 3...
```

when the problem expects:

```text
0 1 1 2...
```

❌ Updating `a` before calculating `next`.

Wrong:

```python
a = b
next = a + b
```

Correct:

```python
next = a + b
a = b
b = next
```

❌ Using naive recursion unnecessarily.

❌ Confusing "first n terms" with "nth term."

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Memorize this:

```text
a = 0
b = 1

repeat:

    print(a)

    next = a + b

    a = b
    b = next
```

That's the fundamental iterative Fibonacci template.

---

# 🧠 DAY 2 — SESSION 1 MASTER PATTERN

These three problems look unrelated, but there are three very important patterns.

## 1️⃣ Happy Number

```text
Transform
   ↓
Transform
   ↓
Transform
   ↓
Cycle?
```

Pattern:

**Repeated Transformation + Cycle Detection**

---

## 2️⃣ Strong Number

```text
Extract digit
     ↓
Factorial
     ↓
Accumulate
```

Pattern:

**Digit Extraction + Mathematical Function**

---

## 3️⃣ Fibonacci

```text
Previous + Current
        ↓
       Next
        ↓
     Update
```

Pattern:

**State Transition / Iterative Recurrence**

---

# 🔥 DAY 2 — SESSION 1 — QUICK MEMORY CARD

```text
╔════════════════════════════════════════════╗
║ HAPPY NUMBER                               ║
║                                            ║
║ digit² + digit² + ...                      ║
║ repeat                                     ║
║ 1 → Happy                                  ║
║ repeat → cycle → Not Happy                 ║
╠════════════════════════════════════════════╣
║ STRONG NUMBER                              ║
║                                            ║
║ digit! + digit! + ...                      ║
║ compare with original                      ║
╠════════════════════════════════════════════╣
║ FIBONACCI                                  ║
║                                            ║
║ a = 0                                      ║
║ b = 1                                      ║
║ next = a + b                               ║
║ a = b                                      ║
║ b = next                                    ║
╚════════════════════════════════════════════╝
```

---

# 📊 DAY 2 — SESSION 1 COMPLETION

| Problem              | Status      |
| -------------------- | ----------- |
| 11. Happy Number     | ✅ Completed |
| 12. Strong Number    | ✅ Completed |
| 13. Fibonacci Series | ✅ Completed |

### Current CR2 Progress

```text
DAY 1 → 10/10 ✅
DAY 2 → 3/10 ✅

TOTAL → 13/100
```

But **13/100 read is not 13/100 mastered**.

Your real target remains:

```text
🟢 Understand
    ↓
🟡 Reproduce
    ↓
🟠 Independent
    ↓
🔴 Master
```

---

# 🧪 SESSION 1 — INDEPENDENT PRACTICE

Do these without looking at the solutions.

### 🟢 Basic

**Q1. Happy Number**

```text
n = 19
```

Determine whether it is happy.

---

**Q2. Strong Number**

```text
n = 145
```

Determine whether it is strong.

---

**Q3. Fibonacci**

Print the first:

```text
10
```

Fibonacci terms.

Expected:

```text
0 1 1 2 3 5 8 13 21 34
```

---

# 🟡 REPRODUCTION DRILL

Write from memory:

```text
1. Happy Number
2. Strong Number
3. Fibonacci Series
```

Rules:

* No copy-paste.
* Run them.
* Intentionally test an edge case.
* Fix your own bug if one appears.

---

# 🟠 SENIOR VARIATION DRILL

### Challenge 1

Instead of printing Fibonacci series, find:

```text
F(10)
```

Expected:

```text
55
```

This connects directly to **LC 509**.

### Challenge 2

Check:

```text
n = 2
```

for Happy Number.

### Challenge 3

Check:

```text
n = 123
```

for Strong Number.

Don't memorize the answer. **Calculate it.**

---

## 🚨 DO NOT MOVE ON YET

Before Day 2 Session 2, you should be able to write these three skeletons without seeing the solution:

```text
Happy:
Repeated transformation + set

Strong:
%10 + factorial + //10

Fibonacci:
a,b → next → shift
```

**Day 2 Session 2 = Problems 14–16: Nth Fibonacci Number → Find All Factors → Perfect Square.**

Would you like to solve the three practice questions first, or should I give you a short quiz on Happy Number, Strong Number, and Fibonacci?

# 🔥 DAY 2 — SESSION 2

## Mathematical Logic — Problems 14–16

We continue with the **exact locked CR2 format and full content depth**. No shortcuts, no reduced explanations.

### 🎯 Session 2

| #  | Problem                      | Core Pattern                           | LeetCode              |
| -- | ---------------------------- | -------------------------------------- | --------------------- |
| 14 | Nth Fibonacci Number         | Iterative state transition             | LC 509 — Easy         |
| 15 | Find All Factors of a Number | Divisor pairs + √n optimization        | No exact canonical LC |
| 16 | Check Perfect Square         | Binary Search / Mathematical reasoning | LC 367 — Easy         |

---

# 🔥 PROBLEM 14 — NTH FIBONACCI NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem looks similar to Problem 13, but there is an important difference.

### Problem 13

> Print the first `n` Fibonacci numbers.

### Problem 14

> Return the **nth Fibonacci number**.

Example:

```text
Fibonacci:

Index:  0  1  2  3  4  5  6
Value:  0  1  1  2  3  5  8
```

Therefore:

```text
F(6) = 8
```

### LeetCode Match

🔥 **LC 509 — Fibonacci Number**

Difficulty: **Easy**

---

## 🚨 Senior Insight

The obvious recursive solution is:

```python
def fib(n):
    if n <= 1:
        return n

    return fib(n - 1) + fib(n - 2)
```

It is mathematically beautiful but computationally inefficient because it repeatedly calculates the same values.

For example:

```text
fib(5)
├── fib(4)
│   ├── fib(3)
│   └── fib(2)
└── fib(3)
    ├── fib(2)
    └── fib(1)
```

`fib(3)` gets calculated multiple times.

### Better approach

Maintain only two values:

```text
previous
current
```

Then:

```text
next = previous + current
```

This gives:

```text
Time = O(n)
Space = O(1)
```

For a placement coding round, this is the clean solution you should reach immediately.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
n = 7
```

We need:

```text
F(7)
```

Sequence:

```text
F(0) = 0
F(1) = 1
F(2) = 1
F(3) = 2
F(4) = 3
F(5) = 5
F(6) = 8
F(7) = 13
```

Output:

```text
13
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Start:

```text
a = 0
b = 1
```

Here:

```text
a = F(0)
b = F(1)
```

To move forward:

```text
next = a + b
```

Then shift:

```text
a = b
b = next
```

For `n = 7`:

```text
0 → 1 → 1 → 2 → 3 → 5 → 8 → 13
```

The important idea is:

> **We don't need the whole Fibonacci array. We only need the previous two values.**

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Algorithm

1. If `n <= 1`, return `n`.
2. Set:

   ```text
   a = 0
   b = 1
   ```
3. Repeat from `2` through `n`.
4. Calculate:

   ```text
   next = a + b
   ```
5. Shift:

   ```text
   a = b
   b = next
   ```
6. Return `b`.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def fibonacci(n):

    if n <= 1:
        return n

    a = 0
    b = 1

    for _ in range(2, n + 1):

        next_value = a + b

        a = b
        b = next_value

    return b


n = int(input("Enter n: "))

print("Fibonacci number =", fibonacci(n))
```

### Example

```text
Input:
7

Output:
Fibonacci number = 13
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static long fibonacci(int n) {

        if (n <= 1) {
            return n;
        }

        long a = 0;
        long b = 1;

        for (int i = 2; i <= n; i++) {

            long next = a + b;

            a = b;
            b = next;
        }

        return b;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        System.out.println("Fibonacci number = " + fibonacci(n));

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
n = 7
```

Initial:

```text
a = 0
b = 1
```

We start from `i = 2`.

### Iteration 1

```text
i = 2

next = 0 + 1
     = 1
```

Update:

```text
a = 1
b = 1
```

Therefore:

```text
F(2) = 1
```

---

### Iteration 2

```text
i = 3

next = 1 + 1
     = 2
```

Update:

```text
a = 1
b = 2
```

Therefore:

```text
F(3) = 2
```

---

### Iteration 3

```text
i = 4

next = 1 + 2
     = 3
```

```text
a = 2
b = 3
```

---

### Iteration 4

```text
i = 5

next = 2 + 3
     = 5
```

```text
a = 3
b = 5
```

---

### Iteration 5

```text
i = 6

next = 3 + 5
     = 8
```

```text
a = 5
b = 8
```

---

### Iteration 6

```text
i = 7

next = 5 + 8
     = 13
```

```text
a = 8
b = 13
```

Loop ends.

Return:

```text
13
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

State table:

|       i |  a |  b | next |
| ------: | -: | -: | ---: |
| Initial |  0 |  1 |    — |
|       2 |  1 |  1 |    1 |
|       3 |  1 |  2 |    2 |
|       4 |  2 |  3 |    3 |
|       5 |  3 |  5 |    5 |
|       6 |  5 |  8 |    8 |
|       7 |  8 | 13 |   13 |

Final:

```text
F(7) = 13
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

The loop executes approximately `n` times.

### Time

```text
O(n)
```

### Auxiliary Space

Only `a`, `b`, and `next_value` are used:

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is recursive Fibonacci inefficient?

Because it repeatedly calculates the same Fibonacci values.

Naive recursion has exponential time complexity:

```text
O(2^n)
```

approximately.

---

### Q2. Can we solve Fibonacci in O(log n)?

Yes.

Using:

* Matrix exponentiation
* Fast doubling

we can calculate the nth Fibonacci number in:

```text
O(log n)
```

But for normal placement constraints, iterative `O(n)` is simpler and often sufficient.

---

### Q3. Why is the space O(1)?

We don't store:

```text
F(0), F(1), F(2), ..., F(n)
```

We only store two previous values.

---

### Q4. What is the difference between Problem 13 and Problem 14?

Problem 13:

```text
Print first n terms
```

Problem 14:

```text
Return F(n)
```

Same mathematical sequence, different output requirement.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Pattern:

```text
previous
current
   ↓
next = previous + current
   ↓
shift states
```

This is an important **state-transition pattern**.

Don't think:

> "Fibonacci = memorize code."

Think:

> "Next state depends on the previous two states."

That's the reusable concept.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Off-by-one indexing.

Remember:

```text
F(0) = 0
F(1) = 1
```

❌ Returning `a` instead of `b`.

❌ Running the loop the wrong number of times.

❌ Using recursion unnecessarily.

❌ Confusing nth term with first n terms.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
F(0) = 0
F(1) = 1

a = 0
b = 1

repeat:

    next = a + b
    a = b
    b = next

return b
```

🔥 **Core pattern: Two-State Iteration**

---

# 🔥 PROBLEM 15 — FIND ALL FACTORS OF A NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A **factor/divisor** of a number `n` is a number that divides `n` exactly.

Example:

```text
n = 24
```

Factors:

```text
1, 2, 3, 4, 6, 8, 12, 24
```

Because:

```text
24 % factor == 0
```

---

## 🚨 Senior Insight

A beginner solution:

```python
for i in range(1, n + 1):
    if n % i == 0:
        print(i)
```

Complexity:

```text
O(n)
```

It works, but it is unnecessarily slow.

### The key mathematical observation:

Factors come in pairs.

For:

```text
24
```

we have:

```text
1 × 24
2 × 12
3 × 8
4 × 6
```

Once we reach:

```text
sqrt(24)
```

the pairs have been discovered.

Therefore:

```text
i * i <= n
```

is enough.

This gives:

```text
O(sqrt(n))
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text
24
```

Output:

```text
1 2 3 4 6 8 12 24
```

We need all positive factors.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Suppose:

```text
n = 36
```

Check:

```text
i = 1
```

Since:

```text
36 % 1 == 0
```

we have:

```text
1 and 36
```

Next:

```text
i = 2
```

gives:

```text
2 and 18
```

Next:

```text
i = 3
```

gives:

```text
3 and 12
```

Next:

```text
i = 4
```

gives:

```text
4 and 9
```

Next:

```text
i = 5
```

not a factor.

Next:

```text
i = 6
```

gives:

```text
6 and 6
```

This is the square-root boundary.

### Important duplicate issue

For perfect squares:

```text
i == n // i
```

So don't add the same factor twice.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Read `n`.
2. Create an empty list.
3. Start `i = 1`.
4. While:

   ```text
   i * i <= n
   ```
5. If:

   ```text
   n % i == 0
   ```

   then:

   * add `i`
   * calculate `n // i`
   * add paired factor if different.
6. Increment `i`.
7. Sort the factors.
8. Print them.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def find_factors(n):

    factors = []

    i = 1

    while i * i <= n:

        if n % i == 0:

            factors.append(i)

            paired_factor = n // i

            if paired_factor != i:
                factors.append(paired_factor)

        i += 1

    factors.sort()

    return factors


n = int(input("Enter a number: "))

if n <= 0:
    print("Enter a positive number.")
else:
    factors = find_factors(n)

    print("Factors:", *factors)
```

### Example

```text
Input:
24

Output:
Factors: 1 2 3 4 6 8 12 24
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
import java.util.Scanner;

public class Main {

    static List<Integer> findFactors(int n) {

        List<Integer> factors = new ArrayList<>();

        for (int i = 1; i * i <= n; i++) {

            if (n % i == 0) {

                factors.add(i);

                int pairedFactor = n / i;

                if (pairedFactor != i) {
                    factors.add(pairedFactor);
                }
            }
        }

        Collections.sort(factors);

        return factors;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n <= 0) {
            System.out.println("Enter a positive number.");
        } else {

            List<Integer> factors = findFactors(n);

            System.out.println("Factors:");

            for (int factor : factors) {
                System.out.print(factor + " ");
            }
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
n = 24
```

Initial:

```text
factors = []
i = 1
```

### i = 1

```text
1 × 1 <= 24
```

Check:

```text
24 % 1 == 0
```

Yes.

Pair:

```text
24 // 1 = 24
```

Add:

```text
1, 24
```

Current:

```text
[1, 24]
```

---

### i = 2

```text
24 % 2 == 0
```

Pair:

```text
24 // 2 = 12
```

Add:

```text
2, 12
```

Current:

```text
[1, 24, 2, 12]
```

---

### i = 3

```text
24 % 3 == 0
```

Pair:

```text
24 // 3 = 8
```

Current:

```text
[1, 24, 2, 12, 3, 8]
```

---

### i = 4

```text
24 % 4 == 0
```

Pair:

```text
24 // 4 = 6
```

Current:

```text
[1, 24, 2, 12, 3, 8, 4, 6]
```

---

### i = 5

```text
24 % 5 != 0
```

Nothing added.

---

### Stop

Next:

```text
i = 5
```

and:

```text
5 × 5 > 24
```

So stop.

Sort:

```text
[1, 2, 3, 4, 6, 8, 12, 24]
```

Final output:

```text
1 2 3 4 6 8 12 24
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For `36`:

|  i | Divides? | Pair  |
| -: | -------- | ----- |
|  1 | Yes      | 1, 36 |
|  2 | Yes      | 2, 18 |
|  3 | Yes      | 3, 12 |
|  4 | Yes      | 4, 9  |
|  5 | No       | —     |
|  6 | Yes      | 6, 6  |

Since:

```text
6 == 36 / 6
```

we add `6` only once.

Final:

```text
1 2 3 4 6 9 12 18 36
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We test only:

```text
1 ... sqrt(n)
```

Therefore:

### Search time

```text
O(sqrt(n))
```

Sorting the factors takes:

```text
O(k log k)
```

where `k` is the number of factors.

So the complete implementation is:

```text
O(sqrt(n) + k log k)
```

If the interviewer only cares about the divisor-search technique:

```text
O(sqrt(n))
```

is the important answer.

### Space

We must store the factors:

```text
O(k)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why only iterate to sqrt(n)?

Because every divisor below `sqrt(n)` has a corresponding divisor above `sqrt(n)`.

Example:

```text
24 = 3 × 8
```

Finding `3` automatically gives `8`.

---

### Q2. Why do we sort?

Because when using divisor pairs, factors are discovered in an unsorted order:

```text
1,24,2,12,3,8,4,6
```

Sorting gives:

```text
1,2,3,4,6,8,12,24
```

---

### Q3. What is the duplicate issue?

For perfect squares:

```text
36 = 6 × 6
```

We must not add `6` twice.

---

### Q4. Can we print factors without sorting?

Yes.

We could collect the small factors and print them in ascending order, then print the paired factors in reverse order.

That can avoid sorting.

But the list + sort approach is easier to understand and write correctly in a basic placement round.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Whenever you see:

> "Find divisors/factors"

immediately think:

```text
i * i <= n
```

Then:

```text
n % i == 0
```

Then:

```text
i
n // i
```

🔥 This same optimization was used in **Perfect Number**.

You should now recognize the connection.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Looping to `n`.

❌ Forgetting paired divisor.

❌ Adding square-root divisor twice.

❌ Forgetting to sort when sorted output is required.

❌ Using:

```text
i * i < n
```

instead of:

```text
i * i <= n
```

and accidentally missing the square-root factor.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Find factors
      ↓
i = 1
      ↓
i*i <= n
      ↓
n % i == 0
      ↓
add i
add n//i
      ↓
avoid duplicate for perfect square
```

🔥 **Core pattern: Divisor Pairs + √n**

---

# 🔥 PROBLEM 16 — CHECK PERFECT SQUARE

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A number is a **perfect square** if it can be written as:

```text
x × x
```

for an integer `x`.

Examples:

```text
1 = 1 × 1
4 = 2 × 2
9 = 3 × 3
16 = 4 × 4
25 = 5 × 5
```

But:

```text
20
```

is not a perfect square.

---

### LeetCode Match

🔥 **LC 367 — Valid Perfect Square**

Difficulty: **Easy**

---

## 🚨 Senior Insight

A beginner might do:

```python
import math

root = math.sqrt(num)

return root == int(root)
```

This is short, but in an interview it may not demonstrate the search pattern they're testing.

A more interview-worthy solution is:

### Binary Search

Search for an integer:

```text
mid
```

such that:

```text
mid * mid == num
```

This turns the problem into a **binary search on the answer**.

That pattern is extremely useful for your broader DSA preparation.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
num = 16
```

We need to determine whether some integer satisfies:

```text
x² = 16
```

Since:

```text
4 × 4 = 16
```

return:

```text
True
```

For:

```text
num = 14
```

there is no integer whose square is `14`.

Return:

```text
False
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Suppose:

```text
num = 36
```

Possible square roots are ordered:

```text
1 2 3 4 5 6
```

If we test the middle:

```text
mid = 3
```

Then:

```text
3 × 3 = 9
```

Since:

```text
9 < 36
```

we need a **larger** number.

So:

```text
left = mid + 1
```

If instead:

```text
mid × mid > num
```

we need a smaller number:

```text
right = mid - 1
```

This is classic binary search.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. If `num < 0`, return false.
2. If `num` is `0` or `1`, return true.
3. Set:

   ```text
   left = 1
   right = num // 2
   ```
4. Calculate:

   ```text
   mid = left + (right - left) // 2
   ```
5. Calculate:

   ```text
   square = mid * mid
   ```
6. If:

   ```text
   square == num
   ```

   return true.
7. If:

   ```text
   square < num
   ```

   search right:

   ```text
   left = mid + 1
   ```
8. Otherwise:

   ```text
   right = mid - 1
   ```
9. If search ends, return false.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_perfect_square(num):

    if num < 0:
        return False

    if num == 0 or num == 1:
        return True

    left = 1
    right = num // 2

    while left <= right:

        mid = left + (right - left) // 2

        square = mid * mid

        if square == num:
            return True

        elif square < num:
            left = mid + 1

        else:
            right = mid - 1

    return False


num = int(input("Enter a number: "))

if is_perfect_square(num):
    print("Perfect Square")
else:
    print("Not a Perfect Square")
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static boolean isPerfectSquare(long num) {

        if (num < 0) {
            return false;
        }

        if (num == 0 || num == 1) {
            return true;
        }

        long left = 1;
        long right = num / 2;

        while (left <= right) {

            long mid = left + (right - left) / 2;

            long square = mid * mid;

            if (square == num) {
                return true;
            }

            if (square < num) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }

        return false;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        long num = sc.nextLong();

        if (isPerfectSquare(num)) {
            System.out.println("Perfect Square");
        } else {
            System.out.println("Not a Perfect Square");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
num = 16
```

Initial:

```text
left = 1
right = 8
```

### Iteration 1

Calculate:

```text
mid = 1 + (8 - 1) // 2
    = 1 + 3
    = 4
```

Now:

```text
4 × 4 = 16
```

Therefore:

```text
square == num
16 == 16
```

Return:

```text
True
```

Output:

```text
Perfect Square
```

---

## 🔬 More Important Dry Run — NOT Perfect Square

Input:

```text
num = 20
```

Initial:

```text
left = 1
right = 10
```

### Iteration 1

```text
mid = 5
5² = 25
```

Since:

```text
25 > 20
```

move left:

```text
right = 4
```

---

### Iteration 2

```text
left = 1
right = 4

mid = 2
```

Square:

```text
2² = 4
```

Since:

```text
4 < 20
```

move right:

```text
left = 3
```

---

### Iteration 3

```text
left = 3
right = 4

mid = 3
```

Square:

```text
3² = 9
```

Since:

```text
9 < 20
```

move right:

```text
left = 4
```

---

### Iteration 4

```text
left = 4
right = 4

mid = 4
```

Square:

```text
16
```

Still:

```text
16 < 20
```

Move:

```text
left = 5
```

Now:

```text
left = 5
right = 4
```

Loop ends.

No square found.

Return:

```text
False
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For `20`:

```text
mid = 5
5² = 25 → too large
        ↓
mid = 2
2² = 4 → too small
        ↓
mid = 3
3² = 9 → too small
        ↓
mid = 4
4² = 16 → too small
        ↓
search exhausted
```

Result:

```text
Not a Perfect Square
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Binary search repeatedly halves the search range.

Therefore:

### Time

```text
O(log n)
```

### Space

```text
O(1)
```

This is substantially better than checking every possible integer from `1` to `n`.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can binary search be used?

Because:

```text
1² < 2² < 3² < 4² < ...
```

Squares of positive integers are monotonically increasing.

That makes binary search valid.

---

### Q2. Why set `right = num // 2`?

For `num > 1`, its square root is always less than or equal to `num // 2` for the relevant search range.

For example:

```text
sqrt(16) = 4
16 // 2 = 8
```

So the root is safely inside the range.

---

### Q3. Why use `left + (right-left)//2`?

It is a standard overflow-safe binary-search midpoint calculation:

```text
mid = left + (right-left)//2
```

instead of:

```text
mid = (left+right)//2
```

In Python integer overflow isn't normally an issue, but this is a strong cross-language habit, especially in Java/C++.

---

### Q4. Could we use `sqrt()`?

Yes.

For a basic placement program:

```python
math.isqrt(num) ** 2 == num
```

is extremely clean in Python.

But binary search teaches a reusable interview pattern:

```text
Search for an answer in a monotonic range.
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This problem is extremely important for your DSA roadmap.

### Recognition:

If you see:

> "Find whether there exists an integer `x` such that `f(x) == target`"

and `f(x)` is monotonic:

```text
x increases
↓
f(x) increases
```

consider:

```text
Binary Search
```

Here:

```text
x → x²
```

is monotonic for positive `x`.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Using binary search without recognizing monotonicity.

❌ Forgetting `0` and `1`.

❌ Using floating-point comparison carelessly.

❌ Overflow in fixed-width languages when using `mid * mid`.

In Java/C++ with large values, use a wider type or compare:

```text
mid <= num / mid
```

when appropriate.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Perfect Square?
       ↓
Search for x
       ↓
x*x == num
       ↓
x² < num → right half
x² > num → left half
       ↓
Binary Search
```

🔥 **Core pattern: Binary Search on Answer**

---

# 🧠 DAY 2 — SESSION 2 MASTER PATTERN

These three problems teach three different levels of thinking.

### 14 — Nth Fibonacci

```text
Previous State
      ↓
Current State
      ↓
Next State
```

**Pattern: Two-State Iteration**

---

### 15 — Factors

```text
Divisor
   ↓
Paired Divisor
   ↓
sqrt(n)
```

**Pattern: Divisor Pair Optimization**

---

### 16 — Perfect Square

```text
Search Space
     ↓
mid²
     ↓
too small → right
too large → left
```

**Pattern: Binary Search**

---

# 🔥 DAY 2 — SESSION 2 MEMORY CARD

```text
╔════════════════════════════════════════════╗
║ NTH FIBONACCI                              ║
║                                            ║
║ a = 0                                      ║
║ b = 1                                      ║
║ next = a + b                               ║
║ shift states                               ║
║ return b                                   ║
╠════════════════════════════════════════════╣
║ ALL FACTORS                                ║
║                                            ║
║ i*i <= n                                   ║
║ n % i == 0                                 ║
║ pair = n//i                                ║
║ avoid duplicate square-root factor         ║
╠════════════════════════════════════════════╣
║ PERFECT SQUARE                             ║
║                                            ║
║ Binary Search                              ║
║ mid² == n → YES                            ║
║ mid² < n → right                           ║
║ mid² > n → left                            ║
╚════════════════════════════════════════════╝
```

---

# 📊 DAY 2 — SESSION 2 COMPLETION

| Problem                  | Status |
| ------------------------ | ------ |
| 14. Nth Fibonacci Number | ✅      |
| 15. Find All Factors     | ✅      |
| 16. Check Perfect Square | ✅      |

### CR2 Progress

```text
Day 1       → 10/10
Day 2 S1    → 3/3
Day 2 S2    → 3/3

TOTAL       → 16/100
```

Again:

```text
16 read ≠ 16 mastered
```

Your target remains:

```text
🟢 Understand
      ↓
🟡 Reproduce
      ↓
🟠 Independent
      ↓
🔴 Master
```

---

# 🧪 SESSION 2 — INDEPENDENT PRACTICE

Do these **without looking at the solutions**.

### 🟢 Basic

**Q1.**

```text
Find F(10)
```

Expected:

```text
55
```

---

**Q2.**

Find all factors of:

```text
36
```

Expected:

```text
1 2 3 4 6 9 12 18 36
```

---

**Q3.**

Check:

```text
49
```

Is it a perfect square?

---

### 🟡 Reproduction Drill

Write from memory:

```text
1. nth Fibonacci
2. all factors
3. perfect square using binary search
```

No copy-paste.

---

# 🟠 SENIOR VARIATION DRILL

### Challenge 1

Check:

```text
n = 0
```

for nth Fibonacci.

### Challenge 2

Find factors of:

```text
100
```

### Challenge 3

Check whether:

```text
num = 99
```

is a perfect square.

### Challenge 4 — Recognition Test 🔥

You are given:

```text
n = 144
```

Without coding yet, identify which of these statements are true:

```text
F(144) ?
Factors of 144?
Is 144 a perfect square?
```

Then decide **which algorithm/pattern** each question requires.

---

# 🚨 MOST IMPORTANT TAKEAWAY

Today's biggest upgrade is not Fibonacci.

It is **pattern recognition**:

```text
"Previous two values?"
        ↓
Two-State Iteration


"Find divisors?"
        ↓
sqrt(n) + divisor pairs


"Find integer x where x² = target?"
        ↓
Binary Search
```

That recognition skill is what eventually lets you solve placement questions **without memorizing 100 programs**.

Would you like to try the three independent-practice questions first, or move on to Day 2 Session 3?


# 🔥 DAY 2 — SESSION 3

## Mathematical Logic — Problems 17–20

We are finishing **Day 2** now.

And yes — **same locked content depth**. No reduction.

### 🎯 Session 3

| #  | Problem           | Core Pattern             | LeetCode              |
| -- | ----------------- | ------------------------ | --------------------- |
| 17 | Factorial         | Iterative multiplication | No exact canonical LC |
| 18 | Power of a Number | Fast Exponentiation      | LC 50 — Medium        |
| 19 | Decimal → Binary  | Base conversion          | No exact LC           |
| 20 | Binary → Decimal  | Base conversion          | No exact LC           |

---

# 🔥 PROBLEM 17 — FACTORIAL

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact Definition

The factorial of a non-negative integer `n` is:

```text id="u3y7mj"
n! = n × (n-1) × (n-2) × ... × 2 × 1
```

Example:

```text id="m6s8qb"
5! = 5 × 4 × 3 × 2 × 1
   = 120
```

Special case:

```text id="u8xq1c"
0! = 1
```

This is extremely important.

---

## 🚨 Senior Insight

There are two natural solutions.

### Recursive

```python id="k6n5zq"
factorial(n) = n * factorial(n-1)
```

### Iterative

```python id="4k1yq7"
result = 1

for i in range(2, n + 1):
    result *= i
```

For placement coding, the **iterative solution is usually preferable**:

```text id="nkg4cv"
O(n) time
O(1) auxiliary space
```

Recursive solution:

```text id="jv7z0c"
O(n) time
O(n) call stack
```

So don't automatically use recursion just because factorial has a mathematical recursive definition.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text id="5d0dr2"
n = 5
```

Calculate:

```text id="z3h1be"
5 × 4 × 3 × 2 × 1
```

Output:

```text id="9m7y4j"
120
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of factorial as repeated multiplication.

Start:

```text id="1e5pl0"
result = 1
```

Then:

```text id="d7f8pz"
result × 2
result × 3
result × 4
result × 5
```

For `5`:

```text id="1k8q7s"
1
↓ ×2
2
↓ ×3
6
↓ ×4
24
↓ ×5
120
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Read `n`.
2. If `n < 0`, factorial is not defined in this basic integer problem.
3. Initialize:

   ```text
   result = 1
   ```
4. Loop from `2` to `n`.
5. Multiply:

   ```text
   result *= i
   ```
6. Return `result`.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="v8p5s6"
def factorial(n):

    if n < 0:
        return None

    result = 1

    for i in range(2, n + 1):
        result *= i

    return result


n = int(input("Enter a number: "))

answer = factorial(n)

if answer is None:
    print("Factorial is not defined for negative numbers.")
else:
    print("Factorial =", answer)
```

### Example

```text id="0w0e1j"
Input:
5

Output:
Factorial = 120
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="1v5trm"
import java.util.Scanner;

public class Main {

    static long factorial(int n) {

        if (n < 0) {
            return -1;
        }

        long result = 1;

        for (int i = 2; i <= n; i++) {
            result *= i;
        }

        return result;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        long answer = factorial(n);

        if (answer == -1) {
            System.out.println("Factorial is not defined for negative numbers.");
        } else {
            System.out.println("Factorial = " + answer);
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="zq27is"
n = 5
```

Initial:

```text id="52h6an"
result = 1
```

### i = 2

```text id="1ecvvm"
result = 1 × 2
       = 2
```

### i = 3

```text id="kr1t3n"
result = 2 × 3
       = 6
```

### i = 4

```text id="0r2m1p"
result = 6 × 4
       = 24
```

### i = 5

```text id="g8cewk"
result = 24 × 5
       = 120
```

Final:

```text id="k25w4b"
5! = 120
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same state progression:

|     i | result |
| ----: | -----: |
| Start |      1 |
|     2 |      2 |
|     3 |      6 |
|     4 |     24 |
|     5 |    120 |

Final:

```text id="6vws0u"
120
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

The loop runs from `2` to `n`.

### Time

```text id="jysl5s"
O(n)
```

### Auxiliary Space

Only `result` and `i`:

```text id="e2p6nz"
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is `0!`?

```text id="vznv5j"
0! = 1
```

This is a mathematical definition and is important in combinations, permutations and probability.

---

### Q2. Why initialize result to `1`?

Because `1` is the multiplicative identity.

If we initialized:

```python id="e1qzv4"
result = 0
```

every multiplication would remain zero.

---

### Q3. Recursive or iterative?

For this basic problem:

```text id="q8f6wz"
Iterative:
O(n) time
O(1) space
```

Recursive:

```text id="y0kqjb"
O(n) time
O(n) call stack
```

---

### Q4. What happens for large `n`?

Factorials grow extremely quickly.

Fixed-width integer types eventually overflow.

Python's integers automatically expand, but the number itself becomes extremely large.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Factorial teaches:

```text id="4k0ck9"
Initialize accumulator
        ↓
Repeated multiplication
        ↓
Return accumulator
```

General template:

```python id="8r9q6m"
result = 1

for i in range(...):
    result *= i
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Starting with `result = 0`.

❌ Forgetting `0! = 1`.

❌ Using `range(1, n)` and accidentally excluding `n`.

❌ Treating negative factorial as an ordinary integer factorial.

❌ Ignoring integer overflow in Java/C++.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="0b7js6"
Factorial
   ↓
result = 1
   ↓
multiply 2...n
   ↓
return result
```

---

# 🔥 PROBLEM 18 — POWER OF A NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Problem

Calculate:

```text id="shk3e5"
x^n
```

Example:

```text id="s3c9w9"
2^5 = 32
```

### Exact LeetCode Match

🔥 **LC 50 — Pow(x, n)**

Difficulty: **Medium**

---

## 🚨 Senior Insight

The naive solution:

```python id="h3y3ts"
result = 1

for _ in range(n):
    result *= x
```

takes:

```text id="07at4n"
O(n)
```

For very large `n`, that's inefficient.

The important algorithm is:

# ⚡ Binary Exponentiation / Fast Power

Instead of multiplying `x` `n` times, repeatedly square the base.

Example:

```text id="i8x0d5"
2^10
```

We know:

```text id="j2r7fk"
2^10 = (2^5)^2
```

and:

```text id="p4gc73"
2^5 = 2 × 2^4
```

More generally:

### If exponent is even:

```text id="40p9bv"
x^n = (x^(n/2))²
```

### If exponent is odd:

```text id="u0b1cn"
x^n = x × x^(n-1)
```

This reduces the number of operations dramatically.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text id="s1k7nt"
x = 2
n = 10
```

Return:

```text id="s5ksb7"
1024
```

because:

```text id="byj2yo"
2^10 = 1024
```

We should also handle negative exponents:

```text id="k0jj5s"
2^-2 = 1/4
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Use:

```text id="6lyf9r"
result = 1
base = x
exponent = n
```

While exponent > 0:

### If exponent is odd

Multiply:

```text id="v88n9b"
result *= base
```

Then square:

```text id="8k4y14"
base *= base
```

Then halve exponent:

```text id="h70cl6"
exponent //= 2
```

### Example

```text id="2d2f9s"
2^10
```

Binary representation:

```text id="05gl2t"
10 = 1010₂
```

The algorithm uses that binary structure.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Read `x` and `n`.
2. If `n == 0`, return `1`.
3. If `n < 0`:

   * replace `x` with `1/x`
   * make `n` positive.
4. Set:

   ```text
   result = 1
   ```
5. While `n > 0`:

   * If `n` is odd:

     ```text
     result *= x
     ```
   * Square:

     ```text
     x *= x
     ```
   * Halve:

     ```text
     n //= 2
     ```
6. Return result.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="j0l8k4"
def power(x, n):

    if n == 0:
        return 1

    if n < 0:
        x = 1 / x
        n = -n

    result = 1

    while n > 0:

        if n % 2 == 1:
            result *= x

        x *= x

        n //= 2

    return result


x = float(input("Enter base: "))
n = int(input("Enter exponent: "))

print("Answer =", power(x, n))
```

### Example

```text id="k4s4q5"
Base:
2

Exponent:
10

Answer = 1024.0
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="9phuv7"
import java.util.Scanner;

public class Main {

    static double power(double x, long n) {

        if (n == 0) {
            return 1.0;
        }

        if (n < 0) {
            x = 1.0 / x;
            n = -n;
        }

        double result = 1.0;

        while (n > 0) {

            if (n % 2 == 1) {
                result *= x;
            }

            x *= x;

            n /= 2;
        }

        return result;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        double x = sc.nextDouble();
        long n = sc.nextLong();

        System.out.println("Answer = " + power(x, n));

        sc.close();
    }
}
```

### ⚠️ Production-level Java note

The `n = -n` operation can overflow for the smallest `long` value (`Long.MIN_VALUE`). For ordinary placement constraints this implementation is fine, but a fully defensive implementation needs special handling.

That is the kind of edge case a senior interviewer may ask about.

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="p9eqb9"
x = 2
n = 10
```

Initial:

```text id="3m1s76"
result = 1
base = 2
n = 10
```

---

### Iteration 1

`n` is even:

```text id="6pn9v8"
10 % 2 = 0
```

Don't multiply result.

Square base:

```text id="q0ypj6"
base = 2 × 2
     = 4
```

Half exponent:

```text id="m2x42m"
n = 10 // 2
  = 5
```

State:

```text id="9r4p91"
result = 1
base = 4
n = 5
```

---

### Iteration 2

`n` is odd:

```text id="ccr7ba"
5 % 2 = 1
```

Multiply:

```text id="j4pfko"
result = 1 × 4
       = 4
```

Square:

```text id="j92qqk"
base = 4 × 4
     = 16
```

Half:

```text id="p8glqz"
n = 5 // 2
  = 2
```

---

### Iteration 3

`n = 2` even.

No multiplication.

Square:

```text id="7ab7ny"
base = 16²
     = 256
```

Half:

```text id="l2o5y5"
n = 1
```

State:

```text id="9jv7cw"
result = 4
base = 256
n = 1
```

---

### Iteration 4

`n = 1` odd.

Multiply:

```text id="4d7tgs"
result = 4 × 256
       = 1024
```

Square base:

```text id="2j57ml"
base = 256²
```

Not important anymore.

Half:

```text id="ccqz1w"
n = 0
```

Stop.

Final:

```text id="u5n3z3"
1024
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same state transitions:

|  n | base | result | Action          |
| -: | ---: | -----: | --------------- |
| 10 |    2 |      1 | even            |
|  5 |    4 |      1 | multiply → 4    |
|  2 |   16 |      4 | even            |
|  1 |  256 |      4 | multiply → 1024 |
|  0 |    — |   1024 | stop            |

Final:

```text id="ebod4x"
2^10 = 1024
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Every iteration halves `n`.

Therefore:

```text id="p3t9bb"
n
n/2
n/4
n/8
...
1
```

Number of iterations:

```text id="x9gh2q"
O(log n)
```

### Time

```text id="4t7f9m"
O(log n)
```

### Space

```text id="l7o6dr"
O(1)
```

This is the major improvement over repeated multiplication:

```text
O(n) → O(log n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is fast exponentiation O(log n)?

Because the exponent is divided by 2 during every iteration.

```text id="zy0d8c"
n → n/2 → n/4 → n/8 → ...
```

---

### Q2. Why do we check whether `n` is odd?

Because an odd exponent contains one extra factor of the current base.

For example:

```text id="jbdz6y"
x^5 = x × x^4
```

So when `n` is odd:

```text id="0gkwj4"
result *= base
```

---

### Q3. Why square the base?

Because:

```text id="80d2jg"
x²
x⁴
x⁸
x¹⁶
...
```

Each squaring doubles the exponent represented by the base.

---

### Q4. What is the core pattern?

```text id="3hx2tj"
Exponentiation
      ↓
Binary representation
      ↓
Repeated squaring
      ↓
O(log n)
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

🔥 This is one of today's most important algorithms.

Whenever you see:

> "Calculate x raised to a large power efficiently"

think:

```text id="a4i3th"
Fast Power
Binary Exponentiation
Repeated Squaring
```

The template:

```python id="5t8s3j"
result = 1

while n > 0:

    if n % 2 == 1:
        result *= x

    x *= x
    n //= 2
```

Memorize the **idea**, not just the code.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Using a loop `n` times for huge exponent.

❌ Forgetting negative exponent handling.

❌ Forgetting `n == 0`.

❌ Squaring before handling an odd exponent.

❌ Confusing:

```text id="4o9zj3"
x = x * x
```

with:

```text id="a3x7ib"
result = result * result
```

The **base** is squared, not the result.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="t4k4vw"
result = 1

while n > 0:

    if n is odd:
        result *= base

    base *= base

    n //= 2
```

🔥

```text
O(n) repeated multiplication
        ↓
O(log n) fast exponentiation
```

---

# 🔥 PROBLEM 19 — DECIMAL TO BINARY

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we move into **number systems**.

Decimal uses base:

```text id="m1x3jw"
10
```

Binary uses base:

```text id="l9k5z8"
2
```

Every decimal integer can be represented using only:

```text id="6d6z0w"
0 and 1
```

Example:

```text id="psrjpk"
10 → 1010
```

because:

```text id="g0jym4"
1×2³ + 0×2² + 1×2¹ + 0×2⁰

= 8 + 0 + 2 + 0

= 10
```

There is no exact canonical LeetCode match for this standalone placement problem.

---

## 🚨 Senior Insight

The mathematical trick is:

### Repeated division by 2

For every division:

```text id="f34zjb"
remainder = n % 2
n = n // 2
```

The remainder is a binary digit.

Example:

```text id="vmbj8s"
10 % 2 = 0
10 // 2 = 5

5 % 2 = 1
5 // 2 = 2

2 % 2 = 0
2 // 2 = 1

1 % 2 = 1
1 // 2 = 0
```

Remainders:

```text id="8sbbz5"
0 1 0 1
```

But they are generated **right-to-left**.

So reverse them:

```text id="b7h6qh"
1010
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text id="w2gc01"
10
```

Output:

```text id="9c1yhi"
1010
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Binary conversion follows:

```text id="q3d1e5"
Repeated division by base
```

For decimal → binary:

```text id="4w6h3n"
base = 2
```

At each step:

```text id="whm5ad"
remainder = n % 2
```

Then:

```text id="2l6h9k"
n //= 2
```

The remainders are reversed.

### Important connection

This is another version of the digit-extraction idea:

```text id="2m1xqn"
% 10 → decimal digit
% 2  → binary digit
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. If `n == 0`, return `"0"`.
2. Create an empty result.
3. While `n > 0`:

   * `remainder = n % 2`
   * add remainder to result
   * `n //= 2`
4. Reverse the result.
5. Return it.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="8r4g4w"
def decimal_to_binary(n):

    if n == 0:
        return "0"

    result = []

    while n > 0:

        remainder = n % 2

        result.append(str(remainder))

        n //= 2

    result.reverse()

    return "".join(result)


n = int(input("Enter decimal number: "))

if n < 0:
    print("Enter a non-negative number.")
else:
    print("Binary =", decimal_to_binary(n))
```

### Example

```text id="eqk7q8"
Input:
10

Output:
Binary = 1010
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="sp6p5z"
import java.util.Scanner;

public class Main {

    static String decimalToBinary(int n) {

        if (n == 0) {
            return "0";
        }

        StringBuilder result = new StringBuilder();

        while (n > 0) {

            int remainder = n % 2;

            result.append(remainder);

            n /= 2;
        }

        return result.reverse().toString();
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (n < 0) {
            System.out.println("Enter a non-negative number.");
        } else {
            System.out.println("Binary = " + decimalToBinary(n));
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="zv0m7k"
n = 10
```

Initial:

```text id="l1g5oj"
result = []
```

### Iteration 1

```text id="vy8qjm"
10 % 2 = 0
```

Append:

```text id="5w3q7s"
result = ["0"]
```

Then:

```text id="g1g8y6"
10 // 2 = 5
```

---

### Iteration 2

```text id="0p8lqq"
5 % 2 = 1
```

```text id="j2m4f4"
result = ["0", "1"]
```

Then:

```text id="93t7pr"
5 // 2 = 2
```

---

### Iteration 3

```text id="5vrxkf"
2 % 2 = 0
```

```text id="ybxxkl"
result = ["0", "1", "0"]
```

Then:

```text id="j47g4f"
2 // 2 = 1
```

---

### Iteration 4

```text id="bqpgib"
1 % 2 = 1
```

```text id="z8z9hy"
result = ["0", "1", "0", "1"]
```

Then:

```text id="u1m7kq"
1 // 2 = 0
```

Stop.

Current order:

```text id="z9vdr8"
0101
```

Reverse:

```text id="4sqj4g"
1010
```

Final:

```text id="t9p1f4"
10 → 1010
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses `StringBuilder`.

Remainders are appended:

```text id="x3jj2m"
0
01
010
0101
```

Then:

```text id="k8avp6"
reverse()
```

gives:

```text id="iy3y5a"
1010
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Every division by 2 reduces the number roughly by half.

Number of iterations:

```text id="q5j6p9"
O(log₂ n)
```

### Time

```text id="q8g6d0"
O(log n)
```

### Space

We store the binary representation:

```text id="p5hy5v"
O(log n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we divide by 2?

Because binary is base 2.

For base `b`, repeated division by `b` gives the digits.

---

### Q2. Why reverse the remainders?

Because the first remainder represents the **least significant bit**.

For `10`:

```text id="12l4lj"
first remainder = 0
```

which becomes the rightmost bit.

---

### Q3. What is the binary representation of zero?

```text id="bqgl5a"
0
```

Special handling is needed because the `while n > 0` loop would otherwise produce an empty result.

---

### Q4. Is there a built-in Python solution?

Yes:

```python id="fghlve"
bin(n)
```

For example:

```python id="w15s3f"
bin(10)
```

returns:

```text id="0b1010"
```

But in a coding interview, implementing the conversion yourself demonstrates the underlying logic.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Base conversion pattern:

```text id="0y0a5m"
number
 ↓
remainder = number % base
 ↓
number //= base
 ↓
repeat
 ↓
reverse digits
```

For binary:

```text id="g6n6zv"
base = 2
```

For decimal:

```text id="2xj3ap"
base = 10
```

This is a general number-system concept.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Forgetting to reverse.

❌ Forgetting the zero case.

❌ Using `% 10` instead of `% 2`.

❌ Using normal division instead of integer division.

❌ Including `0b` when the question asks for only the binary digits.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="k8qjlf"
Decimal → Binary

n % 2
   ↓
remainder
   ↓
n //= 2
   ↓
repeat
   ↓
reverse
```

---

# 🔥 PROBLEM 20 — BINARY TO DECIMAL

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we reverse the previous process.

Given:

```text id="j8k5m1"
1010
```

we want:

```text id="0kjj4p"
10
```

Binary uses powers of 2:

```text id="7a7v5x"
1010

= 1×2³
+ 0×2²
+ 1×2¹
+ 0×2⁰

= 8 + 0 + 2 + 0

= 10
```

There is no exact canonical LeetCode match for this basic standalone conversion.

---

## 🚨 Senior Insight

There are two common ways to understand this.

### Method 1 — Powers

For each bit:

```text id="0x91ve"
decimal += bit × 2^position
```

### Method 2 — Horner-style accumulation

Start:

```text id="a2p3hr"
result = 0
```

For every binary digit:

```text id="j1fx0y"
result = result × 2 + bit
```

This second method is cleaner.

Example:

```text id="t8j1d8"
1010
```

Process `1`:

```text id="9j7j2x"
0 × 2 + 1 = 1
```

Process `0`:

```text id="6ghv4e"
1 × 2 + 0 = 2
```

Process `1`:

```text id="yq4qg8"
2 × 2 + 1 = 5
```

Process `0`:

```text id="h1z5ec"
5 × 2 + 0 = 10
```

Done.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text id="a7p8r1"
1010
```

Output:

```text id="w6x6fr"
10
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Every time we read a new binary digit, we shift the current number left by one binary position.

Multiplying by 2 does exactly that.

So:

```text id="4c0v8n"
result = result × 2 + current_bit
```

is the cleanest formula.

### Example

```text id="4a0r8k"
1011
```

Process:

```text
0 × 2 + 1 = 1
1 × 2 + 0 = 2
2 × 2 + 1 = 5
5 × 2 + 1 = 11
```

Therefore:

```text id="f5y3jh"
1011₂ = 11₁₀
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Read the binary string.
2. Set:

   ```text
   result = 0
   ```
3. For every character:

   * convert it to a digit
   * validate that it is `0` or `1`
   * update:

     ```text
     result = result * 2 + bit
     ```
4. Return result.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="p9v6v7"
def binary_to_decimal(binary):

    result = 0

    for char in binary:

        if char not in "01":
            return None

        bit = int(char)

        result = result * 2 + bit

    return result


binary = input("Enter binary number: ")

answer = binary_to_decimal(binary)

if answer is None:
    print("Invalid binary number.")
else:
    print("Decimal =", answer)
```

### Example

```text id="b5k8pl"
Input:
1010

Output:
Decimal = 10
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="5rj6dd"
import java.util.Scanner;

public class Main {

    static Long binaryToDecimal(String binary) {

        long result = 0;

        for (char ch : binary.toCharArray()) {

            if (ch != '0' && ch != '1') {
                return null;
            }

            int bit = ch - '0';

            result = result * 2 + bit;
        }

        return result;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String binary = sc.nextLine();

        Long answer = binaryToDecimal(binary);

        if (answer == null) {
            System.out.println("Invalid binary number.");
        } else {
            System.out.println("Decimal = " + answer);
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="0g4jvx"
1010
```

Initial:

```text id="2u1k0e"
result = 0
```

### Character 1

```text id="2y4gq4"
bit = 1
```

Update:

```text id="z7e4fa"
result = 0 × 2 + 1
       = 1
```

---

### Character 2

```text id="u1p1i0"
bit = 0
```

```text id="m0n1ah"
result = 1 × 2 + 0
       = 2
```

---

### Character 3

```text id="w7ym52"
bit = 1
```

```text id="5xgq8e"
result = 2 × 2 + 1
       = 5
```

---

### Character 4

```text id="0b9jzh"
bit = 0
```

```text id="9e0n3v"
result = 5 × 2 + 0
       = 10
```

Final:

```text id="w4s0lm"
1010 → 10
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

| Bit | Previous Result | New Result |
| --: | --------------: | ---------: |
|   1 |               0 |          1 |
|   0 |               1 |          2 |
|   1 |               2 |          5 |
|   0 |               5 |         10 |

Final:

```text id="e4e2dy"
10
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="8e4m1p"
d = number of binary digits
```

We process each digit once.

### Time

```text id="qv68i4"
O(d)
```

### Space

Only `result` and `bit`:

```text id="o9n2d4"
O(1)
```

excluding the input string itself.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why multiply the current result by 2?

Because binary is base 2.

Moving to the next binary position is equivalent to:

```text id="k7l9is"
result × 2
```

---

### Q2. Why add the current bit?

Because the current bit represents the new least-significant contribution:

```text id="t5j7r8"
result = result × 2 + bit
```

---

### Q3. How would this generalize to another base?

For base `b`:

```text id="z9g8oc"
result = result × b + digit
```

This is a general base-conversion technique.

---

### Q4. What happens if the input contains `2`?

It is invalid binary.

Binary can contain only:

```text id="yq39gu"
0
1
```

Our implementation explicitly validates this.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

The key formula is:

```text id="s5i6eq"
result = result * base + digit
```

For binary:

```text id="1zj2ra"
base = 2
```

So:

```text id="e8ty9u"
result = result * 2 + bit
```

This is essentially **Horner's method** for evaluating a number in a given base.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Treating the binary string as decimal:

```python id="u3gh7e"
int("1010")  # 1010, not 10
```

❌ Forgetting multiplication by 2.

❌ Accepting digits other than `0` and `1`.

❌ Confusing decimal digits with binary digits.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Memorize:

```text id="hj7f8p"
result = 0

for bit in binary:

    result = result * 2 + bit
```

🔥 General principle:

```text id="8j1h9f"
result = result * base + digit
```

---

# 🧠 DAY 2 — SESSION 3 MASTER PATTERN

These four problems are very important together.

## 17 — Factorial

```text id="z9v3k8"
Repeated multiplication
```

```text
result *= i
```

---

## 18 — Power

```text id="4x4tqj"
Repeated squaring
```

```text
result *= base
base *= base
exponent //= 2
```

🔥 Complexity:

```text
O(log n)
```

---

## 19 — Decimal → Binary

```text id="l7g6pq"
Repeated division by base
```

```text
remainder = n % 2
n //= 2
reverse
```

---

## 20 — Binary → Decimal

```text id="e0y3dy"
Repeated base accumulation
```

```text
result = result * 2 + bit
```

---

# 🔥 DAY 2 — SESSION 3 MEMORY CARD

```text id="3t5k6w"
╔══════════════════════════════════════════════╗
║ FACTORIAL                                    ║
║                                              ║
║ result = 1                                   ║
║ result *= i                                  ║
║ O(n)                                         ║
╠══════════════════════════════════════════════╣
║ POWER                                        ║
║                                              ║
║ if exponent odd → result *= base             ║
║ base *= base                                 ║
║ exponent //= 2                               ║
║ O(log n)                                     ║
╠══════════════════════════════════════════════╣
║ DECIMAL → BINARY                             ║
║                                              ║
║ remainder = n % 2                            ║
║ n //= 2                                      ║
║ reverse                                      ║
║ O(log n)                                     ║
╠══════════════════════════════════════════════╣
║ BINARY → DECIMAL                             ║
║                                              ║
║ result = result * 2 + bit                    ║
║ O(number of bits)                             ║
╚══════════════════════════════════════════════╝
```

---

# 🏆 DAY 2 — COMPLETE

You have now finished all 10 Day 2 problems.

| #  | Problem          | Status |
| -- | ---------------- | ------ |
| 11 | Happy Number     | ✅      |
| 12 | Strong Number    | ✅      |
| 13 | Fibonacci Series | ✅      |
| 14 | Nth Fibonacci    | ✅      |
| 15 | All Factors      | ✅      |
| 16 | Perfect Square   | ✅      |
| 17 | Factorial        | ✅      |
| 18 | Power of Number  | ✅      |
| 19 | Decimal → Binary | ✅      |
| 20 | Binary → Decimal | ✅      |

### CR2 Progress

```text
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅

TOTAL → 20/100
```

But again:

```text
20/100 completed
≠
20/100 mastered
```

Your actual progression:

```text
🟢 Understand
      ↓
🟡 Reproduce
      ↓
🟠 Independent
      ↓
🔴 Master
```

---

# 🧪 DAY 2 — FINAL NO-SOLUTION TEST

Do this **without looking back at today's solutions**.

### Q1 — Factorial

```text
7!
```

---

### Q2 — Power

Calculate:

```text
2^20
```

using **fast exponentiation**, not a loop running 20 times.

---

### Q3 — Decimal → Binary

Convert:

```text
25
```

Expected:

```text
11001
```

---

### Q4 — Binary → Decimal

Convert:

```text
11010
```

Expected:

```text
26
```

---

### Q5 — Fibonacci

Find:

```text
F(15)
```

---

### Q6 — Perfect Square

Determine whether:

```text
121
```

is a perfect square.

**Use binary search.**

---

### Q7 — Factor Recognition 🔥

For:

```text
n = 72
```

find all factors using the **√n divisor-pair method**.

---

### Q8 — Combined Number-System Challenge 🔥🔥

Write a program that:

```text
Decimal number
      ↓
Binary
      ↓
Convert that binary back
      ↓
Decimal
```

For:

```text
25
```

you should get:

```text
25
 ↓
11001
 ↓
25
```

If your final answer is not the original number, debug your conversion logic.

---

# 🚨 DAY 2 SENIOR TAKEAWAY

Don't memorize 20 separate programs.

You should now recognize these fundamental building blocks:

```text
NUMBER LOGIC
│
├── %10 / //10
│     └── digit processing
│
├── divisor pairs
│     └── O(√n)
│
├── two-state iteration
│     └── Fibonacci
│
├── cycle detection
│     └── Happy Number
│
├── repeated multiplication
│     └── Factorial
│
├── repeated squaring
│     └── Fast Power O(log n)
│
├── repeated division
│     └── Decimal → Binary
│
├── base accumulation
│     └── Binary → Decimal
│
└── binary search
      └── Perfect Square
```

🔥 **This is the real Day 2 achievement: 10 problems → multiple reusable patterns.**

**DAY 2 = 20/100 completed.**

Next in the locked syllabus:

# 🚀 DAY 3 — STRING FUNDAMENTALS

### Session 1 → Problems 21–23

1. Reverse a String
2. Check Palindrome String
3. Count Vowels and Consonants

Would you like to start Day 3 Session 1 with reversing a string, or do the Day 2 final no-solution test first?

