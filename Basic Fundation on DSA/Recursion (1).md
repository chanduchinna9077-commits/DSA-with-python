# 🔴 9. RECURSION — 10 Problems

### Patterns

```text
Base case
Recursive case
Parameter reduction
Returning values
String recursion
Array recursion
```

### Problems

1. Print 1 to N
2. Print N to 1
3. Sum 1 to N
4. Factorial
5. Fibonacci
6. Sum of digits
7. Reverse string
8. Palindrome
9. Power
10. Recursive array maximum

---



# 🔵 RECURSION — CONVERSATION 1

## Problems 1–4

We are switching the topic order as you requested because **Recursion is currently a college-focused area**.

### 🎯 Session Mission

| # | Problem        | Main Pattern           | Level    |
| - | -------------- | ---------------------- | -------- |
| 1 | Print `1 → N`  | Basic Recursion        | 🟢 Basic |
| 2 | Print `N → 1`  | Recursive Backtracking | 🟢 Basic |
| 3 | Sum of `1 → N` | Return-Value Recursion | 🟢 Basic |
| 4 | Factorial      | Mathematical Recursion | 🟢 Basic |

---

# 🧠 BEFORE PROBLEM 1 — RECURSION FUNDAMENTALS

Before writing recursion code, understand these **3 things**.

## 1. What is Recursion?

**Recursion is when a function calls itself to solve a smaller version of the same problem.**

Example:

```python
def countdown(n):
    if n == 0:
        return

    print(n)
    countdown(n - 1)
```

The function:

```text
countdown(5)
```

calls:

```text
countdown(4)
    ↓
countdown(3)
    ↓
countdown(2)
    ↓
countdown(1)
    ↓
countdown(0)
```

---

## 2. Base Case

The **base case** tells recursion when to stop.

Example:

```python
if n == 0:
    return
```

Without a base case:

```text
function
 ↓
function
 ↓
function
 ↓
function
 ↓
...
```

Eventually Python raises:

```text
RecursionError
```

---

## 3. Recursive Case

The recursive case makes the problem **smaller**.

```python
countdown(n - 1)
```

The important rule is:

> Every recursive call must move toward the base case.

---

# 🔥 RECURSION MENTAL MODEL

Every recursion problem should make you ask:

```text
1. What is my BASE CASE?
          ↓
2. What is my SMALLER PROBLEM?
          ↓
3. How do I MOVE toward the base case?
          ↓
4. What happens while CALLING?
          ↓
5. What happens while RETURNING?
```

The last two are particularly important because recursion uses the **call stack**.

---

# 🔵 PROBLEM 1 — Print 1 → N

## 1. Problem Statement

Given an integer `N`, print all numbers from:

```text
1 → N
```

### Example

```text
N = 5
```

Output:

```text
1 2 3 4 5
```

---

# 2. Problem Theory

This is the simplest recursion pattern.

We need:

```text
1
2
3
4
5
```

A recursive function can solve this by first going down toward `1`, then printing while the recursion returns.

This teaches an extremely important concept:

> **Work done before the recursive call vs. work done after the recursive call.**

For `1 → N`, we'll use:

```python
print(...)
recursive_call(...)
```

or, even more importantly for understanding recursion order:

```python
recursive_call(...)
print(...)
```

Let's use the second form because it teaches the **return phase**.

---

# 3. Pattern Being Tested

### 🔥 Basic Recursion + Backtracking

Pattern:

```text
function(n)
    ↓
function(n-1)
    ↓
function(n-2)
    ↓
...
BASE CASE
    ↓
return
    ↓
print
```

---

# 4. ELI10 Intuition

Suppose I tell you:

> "Print numbers from 1 to 5."

You say:

> "I'll first ask someone else to print 1 to 4."

That person says:

> "I'll ask someone else to print 1 to 3."

And so on.

Eventually:

```text
print 1
```

Then everyone returns and prints their own number.

So:

```text
1
↓
2
↓
3
↓
4
↓
5
```

---

# 5. Example

```text
N = 5
```

Function calls:

```text
print_1_to_n(5)
    ↓
print_1_to_n(4)
    ↓
print_1_to_n(3)
    ↓
print_1_to_n(2)
    ↓
print_1_to_n(1)
```

At `1`:

```text
print(1)
```

Then return.

Then:

```text
print(2)
print(3)
print(4)
print(5)
```

Final:

```text
1 2 3 4 5
```

---

# 6. Algorithm — Step-by-Step

1. Create a function `print_1_to_n(n)`.
2. Base case:

   * If `n == 0`, stop.
3. Call the function for `n - 1`.
4. Print `n`.
5. Return.

### Pseudocode

```text
FUNCTION print_1_to_n(n):

    IF n == 0:
        RETURN

    print_1_to_n(n - 1)

    PRINT n
```

---

# 7. Python Solution — Using Built-in Methods

There isn't a meaningful built-in recursion method for this problem.

For comparison, the normal Python approach would be:

```python
n = 5

for i in range(1, n + 1):
    print(i, end=" ")
```

Output:

```text
1 2 3 4 5
```

But this is **iteration, not recursion**.

For the recursion question, you should implement it yourself.

---

# 8. Python Solution — Without Built-in Methods

```python
def print_1_to_n(n):

    # Base case
    if n == 0:
        return

    # Recursive call
    print_1_to_n(n - 1)

    # Print while returning
    print(n, end=" ")


n = 5

print_1_to_n(n)
```

Output:

```text
1 2 3 4 5
```

---

# 9. Line-by-Line Explanation

```python
def print_1_to_n(n):
```

Creates a recursive function.

---

```python
if n == 0:
    return
```

### Base case.

When `n` becomes `0`, stop calling the function.

---

```python
print_1_to_n(n - 1)
```

This is the recursive call.

For `5`:

```text
5 → 4 → 3 → 2 → 1 → 0
```

---

```python
print(n, end=" ")
```

Notice this comes **after** the recursive call.

That's the key.

The function first goes all the way down:

```text
5
4
3
2
1
0
```

Then while returning:

```text
1
2
3
4
5
```

---

# 10. Detailed Dry Run

Input:

```text
n = 5
```

### Call phase

```text
print_1_to_n(5)
        ↓
print_1_to_n(4)
        ↓
print_1_to_n(3)
        ↓
print_1_to_n(2)
        ↓
print_1_to_n(1)
        ↓
print_1_to_n(0)
```

At `0`:

```text
return
```

Now the functions start returning.

| Return From | What gets printed |
| ----------: | ----------------: |
|     `n = 1` |                 1 |
|     `n = 2` |                 2 |
|     `n = 3` |                 3 |
|     `n = 4` |                 4 |
|     `n = 5` |                 5 |

Final:

```text
1 2 3 4 5
```

---

# 11. Call Stack Visualization

This is **very important for recursion**.

While calling:

```text
┌─────────────────────┐
│ print_1_to_n(0)     │
├─────────────────────┤
│ print_1_to_n(1)     │
├─────────────────────┤
│ print_1_to_n(2)     │
├─────────────────────┤
│ print_1_to_n(3)     │
├─────────────────────┤
│ print_1_to_n(4)     │
├─────────────────────┤
│ print_1_to_n(5)     │
└─────────────────────┘
```

The `0` call reaches the base case.

Then the stack unwinds:

```text
0 → return
1 → print
2 → print
3 → print
4 → print
5 → print
```

This is why the output is:

```text
1 2 3 4 5
```

---

# 12. Complexity

There are `N` function calls.

### Time

```text
O(N)
```

### Space

Because recursion uses the call stack:

```text
O(N)
```

This is different from a normal iterative loop, which usually uses:

```text
O(1)
```

extra space.

---

# 13. Edge Cases

### `N = 0`

```text
Output: nothing
```

### `N = 1`

```text
Output: 1
```

### Negative `N`

For a basic problem, define the input as `N >= 0`.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — No base case

```python
def f(n):
    f(n - 1)
```

This never stops.

---

### ❌ Mistake 2 — Not reducing `n`

Wrong:

```python
f(n)
```

Correct:

```python
f(n - 1)
```

---

### ❌ Mistake 3 — Printing before recursive call

If you write:

```python
print(n)
print_1_to_n(n - 1)
```

you get:

```text
5 4 3 2 1
```

That's Problem 2.

---

# 15. Pattern Recognition

> **When you see:**
> "Print 1 to N using recursion"
>
> Think:
>
> 🔥 **Recursive call first → print during return**

```text
f(n)
 ↓
f(n-1)
 ↓
...
 ↓
BASE
 ↑
print
 ↑
print
 ↑
print
```

---

# 🔵 PROBLEM 2 — Print N → 1

## 1. Problem Statement

Given `N`, print:

```text
N → 1
```

### Example

```text
N = 5
```

Output:

```text
5 4 3 2 1
```

---

# 2. Problem Theory

This is almost the same recursion as Problem 1.

The **only major difference** is where we place the `print()`.

For:

```text
1 → N
```

we printed **after** recursion.

For:

```text
N → 1
```

we print **before** recursion.

---

# 3. Pattern Being Tested

### 🔥 Recursive Call Order

```text
print(n)
↓
recursive call
```

This produces descending output.

---

# 4. ELI10 Intuition

You are at `5`.

Say:

```text
5
```

Then ask:

> "Now handle 4."

Then:

```text
4
```

Then:

```text
3
```

and so on.

No waiting for the return phase.

---

# 5. Example

```text
n = 5
```

Execution:

```text
print 5
 ↓
call 4
 ↓
print 4
 ↓
call 3
 ↓
print 3
 ↓
call 2
 ↓
print 2
 ↓
call 1
 ↓
print 1
 ↓
call 0
 ↓
return
```

Output:

```text
5 4 3 2 1
```

---

# 6. Algorithm — Step-by-Step

1. Create function `print_n_to_1(n)`.
2. If `n == 0`, stop.
3. Print `n`.
4. Call function with `n - 1`.

### Pseudocode

```text
FUNCTION print_n_to_1(n):

    IF n == 0:
        RETURN

    PRINT n

    print_n_to_1(n - 1)
```

---

# 7. Python Solution — Using Built-in / Iterative Equivalent

```python
n = 5

for i in range(n, 0, -1):
    print(i, end=" ")
```

Output:

```text
5 4 3 2 1
```

Again, this is **iteration**, not recursion.

---

# 8. Python Solution — Without Built-in Recursion

```python
def print_n_to_1(n):

    # Base case
    if n == 0:
        return

    # Print before recursive call
    print(n, end=" ")

    # Recursive call
    print_n_to_1(n - 1)


n = 5

print_n_to_1(n)
```

Output:

```text
5 4 3 2 1
```

---

# 9. Line-by-Line Explanation

```python
if n == 0:
    return
```

Stop condition.

---

```python
print(n, end=" ")
```

Print current value **before** going deeper.

---

```python
print_n_to_1(n - 1)
```

Move toward `1`.

---

# 10. Detailed Dry Run

Input:

```text
n = 5
```

| Call   | Action  | Output      |
| ------ | ------- | ----------- |
| `f(5)` | print 5 | `5`         |
| `f(4)` | print 4 | `5 4`       |
| `f(3)` | print 3 | `5 4 3`     |
| `f(2)` | print 2 | `5 4 3 2`   |
| `f(1)` | print 1 | `5 4 3 2 1` |
| `f(0)` | return  | Done        |

---

# 11. Call Stack

The calls build:

```text
f(5)
 ↓
f(4)
 ↓
f(3)
 ↓
f(2)
 ↓
f(1)
 ↓
f(0)
```

But unlike Problem 1, the printing already happened while going **down**.

---

# 12. Complexity

Time:

```text
O(N)
```

Space:

```text
O(N)
```

because of the recursive call stack.

---

# 13. Edge Cases

```text
N = 0 → nothing
N = 1 → 1
N = 5 → 5 4 3 2 1
```

---

# 14. Common Mistakes / Traps

### ❌ Putting print after recursion

That changes the output to:

```text
1 2 3 4 5
```

### ❌ Forgetting `n - 1`

Again, recursion must move toward the base case.

---

# 15. Pattern Recognition

> **"Print N to 1"**
>
> Think:
>
> 🔥 **Print first → Recursive call**

```text
PRINT
 ↓
RECURSE
```

---

# 🔵 PROBLEM 3 — Sum of 1 → N

## 1. Problem Statement

Given `N`, calculate:

```text
1 + 2 + 3 + ... + N
```

### Example

```text
N = 5
```

Output:

```text
15
```

Because:

```text
1 + 2 + 3 + 4 + 5 = 15
```

---

# 2. Problem Theory

This introduces an important new recursion concept:

> **A recursive function can return a value.**

Instead of just printing, our function calculates something.

The key relationship is:

```text
sum(n) = n + sum(n - 1)
```

For example:

```text
sum(5)
= 5 + sum(4)
= 5 + 4 + sum(3)
= 5 + 4 + 3 + sum(2)
= 5 + 4 + 3 + 2 + sum(1)
```

Base case:

```text
sum(1) = 1
```

---

# 3. Pattern Being Tested

### 🔥 Return-Value Recursion

Pattern:

```text
answer(n)
    =
current value
    +
answer(smaller problem)
```

This is one of the most important recursion patterns.

---

# 4. ELI10 Intuition

Suppose I ask:

> "What is the sum from 1 to 5?"

You can say:

> "Give me the sum from 1 to 4, then I'll add 5."

So:

```text
sum(5)
=
sum(4) + 5
```

Then:

```text
sum(4)
=
sum(3) + 4
```

Eventually:

```text
sum(1) = 1
```

Then the answers return upward.

---

# 5. Example

```text
sum(5)
```

becomes:

```text
5 + sum(4)
```

then:

```text
5 + 4 + sum(3)
```

then:

```text
5 + 4 + 3 + sum(2)
```

then:

```text
5 + 4 + 3 + 2 + sum(1)
```

Base:

```text
sum(1) = 1
```

Returning:

```text
1
↓
1 + 2 = 3
↓
3 + 3 = 6
↓
6 + 4 = 10
↓
10 + 5 = 15
```

---

# 6. Algorithm — Step-by-Step

1. Create `sum_n(n)`.
2. Base case:

   * if `n == 0`, return `0`.
3. Otherwise:

   * return `n + sum_n(n - 1)`.
4. The recursive calls eventually reach `0`.
5. Values are added while the calls return.

### Pseudocode

```text
FUNCTION sum_n(n):

    IF n == 0:
        RETURN 0

    RETURN n + sum_n(n - 1)
```

---

# 7. Python Solution — Using Built-in / Formula

A direct mathematical solution is:

```python
n = 5

total = n * (n + 1) // 2

print(total)
```

Output:

```text
15
```

This is:

```text
O(1)
```

but it is **not recursion**.

For learning recursion, implement the recursive version.

---

# 8. Python Solution — Without Built-in Methods

```python
def sum_n(n):

    # Base case
    if n == 0:
        return 0

    # Recursive case
    return n + sum_n(n - 1)


n = 5

result = sum_n(n)

print(result)
```

Output:

```text
15
```

---

# 9. Line-by-Line Explanation

```python
if n == 0:
    return 0
```

When there are no numbers left to add, the sum is `0`.

This is the base case.

---

```python
return n + sum_n(n - 1)
```

This means:

> "My answer is my current number + the answer to the smaller problem."

For `n = 5`:

```text
5 + sum_n(4)
```

---

# 10. Detailed Dry Run

Input:

```text
n = 5
```

### Call phase

```text
sum_n(5)
↓
5 + sum_n(4)
↓
5 + 4 + sum_n(3)
↓
5 + 4 + 3 + sum_n(2)
↓
5 + 4 + 3 + 2 + sum_n(1)
↓
5 + 4 + 3 + 2 + 1 + sum_n(0)
```

Base:

```text
sum_n(0) = 0
```

### Return phase

| Function   | Calculation | Returns |
| ---------- | ----------- | ------: |
| `sum_n(0)` | `0`         |       0 |
| `sum_n(1)` | `1 + 0`     |       1 |
| `sum_n(2)` | `2 + 1`     |       3 |
| `sum_n(3)` | `3 + 3`     |       6 |
| `sum_n(4)` | `4 + 6`     |      10 |
| `sum_n(5)` | `5 + 10`    |  **15** |

---

# 11. Call Stack Visualization

During calls:

```text
sum_n(5)
   |
sum_n(4)
   |
sum_n(3)
   |
sum_n(2)
   |
sum_n(1)
   |
sum_n(0)
```

At `sum_n(0)`:

```text
return 0
```

Then:

```text
sum_n(1) → 1
sum_n(2) → 3
sum_n(3) → 6
sum_n(4) → 10
sum_n(5) → 15
```

---

# 12. Complexity

### Time

```text
O(N)
```

We make `N` recursive calls.

### Space

```text
O(N)
```

because of the call stack.

---

# 13. Edge Cases

### `N = 0`

```text
sum = 0
```

### `N = 1`

```text
sum = 1
```

### `N = 5`

```text
sum = 15
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

```python
return n + sum_n(n)
```

This never decreases `n`.

---

### ❌ Mistake 2

Wrong base case:

```python
if n == 1:
    return 0
```

That would lose the value `1`.

Correct:

```python
if n == 0:
    return 0
```

---

### ❌ Mistake 3 — Forgetting `return`

Wrong:

```python
sum_n(n - 1)
```

Correct:

```python
return n + sum_n(n - 1)
```

The recursive result must come back to the caller.

---

# 15. Pattern Recognition

> **When you see:**
> "Calculate something for `1 → N`"
>
> Think:
>
> 🔥 **Current value + answer of smaller problem**

Template:

```python
def solve(n):

    if base_case:
        return base_value

    return current_value + solve(n - 1)
```

---

# 🔵 PROBLEM 4 — Factorial

## 1. Problem Statement

Given a non-negative integer `N`, calculate:

```text
N!
```

Factorial means:

```text
N! = N × (N-1) × (N-2) × ... × 1
```

### Example

```text
5!
```

means:

```text
5 × 4 × 3 × 2 × 1
```

Therefore:

```text
120
```

---

# 2. Problem Theory

Factorial has a perfect recursive definition:

```text
n! = n × (n - 1)!
```

The most important base case is:

```text
0! = 1
```

This is mathematically important.

Therefore:

```text
factorial(0) = 1
```

---

# 3. Pattern Being Tested

### 🔥 Mathematical Recursion

Pattern:

```text
factorial(n)
    =
n × factorial(n-1)
```

This is another **return-value recursion** problem.

---

# 4. ELI10 Intuition

Suppose someone asks:

> What is `5!`?

You can say:

> "Give me `4!`, and I'll multiply it by 5."

```text
5! = 5 × 4!
```

Then:

```text
4! = 4 × 3!
```

Eventually:

```text
0! = 1
```

Then everything comes back.

---

# 5. Example

```text
5!
```

Expansion:

```text
5 × 4!
```

```text
5 × 4 × 3!
```

```text
5 × 4 × 3 × 2!
```

```text
5 × 4 × 3 × 2 × 1!
```

```text
5 × 4 × 3 × 2 × 1 × 0!
```

Since:

```text
0! = 1
```

we get:

```text
5 × 4 × 3 × 2 × 1
= 120
```

---

# 6. Algorithm — Step-by-Step

1. Create `factorial(n)`.
2. If `n == 0`:

   * return `1`.
3. Otherwise:

   * calculate `n * factorial(n - 1)`.
4. Return the result.

### Pseudocode

```text
FUNCTION factorial(n):

    IF n == 0:
        RETURN 1

    RETURN n × factorial(n - 1)
```

---

# 7. Python Solution — Using Built-in Method

Python provides `math.factorial()`:

```python
import math

n = 5

result = math.factorial(n)

print(result)
```

Output:

```text
120
```

Again, this is useful for comparison, but it doesn't demonstrate the recursive logic.

---

# 8. Python Solution — Without Built-in Method

```python
def factorial(n):

    # Base case
    if n == 0:
        return 1

    # Recursive case
    return n * factorial(n - 1)


n = 5

result = factorial(n)

print(result)
```

Output:

```text
120
```

---

# 9. Line-by-Line Explanation

```python
if n == 0:
    return 1
```

This is the base case.

Remember:

```text
0! = 1
```

---

```python
return n * factorial(n - 1)
```

Current number is multiplied by the factorial of the smaller number.

For `5`:

```text
5 × factorial(4)
```

---

# 10. Detailed Dry Run

Input:

```text
n = 5
```

### Call phase

```text
factorial(5)
↓
5 × factorial(4)
↓
5 × 4 × factorial(3)
↓
5 × 4 × 3 × factorial(2)
↓
5 × 4 × 3 × 2 × factorial(1)
↓
5 × 4 × 3 × 2 × 1 × factorial(0)
```

Base:

```text
factorial(0) = 1
```

### Return phase

| Function       | Calculation | Returns |
| -------------- | ----------- | ------: |
| `factorial(0)` | `1`         |       1 |
| `factorial(1)` | `1 × 1`     |       1 |
| `factorial(2)` | `2 × 1`     |       2 |
| `factorial(3)` | `3 × 2`     |       6 |
| `factorial(4)` | `4 × 6`     |      24 |
| `factorial(5)` | `5 × 24`    | **120** |

---

# 11. Call Stack Visualization

```text
factorial(5)
     ↓
factorial(4)
     ↓
factorial(3)
     ↓
factorial(2)
     ↓
factorial(1)
     ↓
factorial(0)
```

Then:

```text
factorial(0) → 1
       ↑
factorial(1) → 1
       ↑
factorial(2) → 2
       ↑
factorial(3) → 6
       ↑
factorial(4) → 24
       ↑
factorial(5) → 120
```

---

# 12. Complexity

### Time

```text
O(N)
```

There are approximately `N + 1` calls.

### Space

```text
O(N)
```

because the recursive calls remain on the call stack until the base case is reached.

---

# 13. Edge Cases

### `0`

```text
0! = 1
```

### `1`

```text
1! = 1
```

### `5`

```text
5! = 120
```

### Negative numbers

Factorial is normally defined for non-negative integers in this basic programming context.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Base case returns 0

Wrong:

```python
if n == 0:
    return 0
```

That would make every factorial become `0`.

Correct:

```python
if n == 0:
    return 1
```

---

### ❌ Mistake 2 — Adding instead of multiplying

Wrong:

```python
return n + factorial(n - 1)
```

That's closer to the **sum 1 → N** problem.

Correct:

```python
return n * factorial(n - 1)
```

---

### ❌ Mistake 3 — Not decreasing `n`

Wrong:

```python
return n * factorial(n)
```

This never reaches `0`.

---

# 15. Pattern Recognition

> **When you see:**
> `n!`, product from `1 → n`, or a mathematical recurrence
>
> Think:
>
> 🔥 **Current value × smaller problem**

Template:

```python
def solve(n):

    if n == 0:
        return 1

    return n * solve(n - 1)
```

---

# 🧠 RECURSION — CONVERSATION 1 MASTER PATTERN MAP

We completed the first four patterns.

| # | Problem       | Core Pattern               |
| - | ------------- | -------------------------- |
| 1 | Print `1 → N` | Recursive call → work      |
| 2 | Print `N → 1` | Work → recursive call      |
| 3 | Sum `1 → N`   | Current + recursive result |
| 4 | Factorial     | Current × recursive result |

---

# 🔥 THE MOST IMPORTANT LESSON OF THESE 4

The biggest thing you should learn is **not the individual problems**.

It is the position of the work relative to the recursive call.

## Pattern A — Work AFTER recursion

```python
solve(n - 1)
print(n)
```

Produces:

```text
1 → N
```

---

## Pattern B — Work BEFORE recursion

```python
print(n)
solve(n - 1)
```

Produces:

```text
N → 1
```

---

## Pattern C — Return a calculated value

```python
return n + solve(n - 1)
```

Produces:

```text
1 + 2 + ... + N
```

---

## Pattern D — Return a product

```python
return n * solve(n - 1)
```

Produces:

```text
N!
```

---

# 🧠 RECURSION DECISION PATTERN

When you see a recursion question, ask:

```text
                 RECURSION
                     |
          ┌──────────┴──────────┐
          |                     |
       Printing              Calculation
          |                     |
    ┌─────┴─────┐         ┌─────┴─────┐
    |           |         |           |
  Before      After      Sum        Product
  call        call
    |           |          |           |
   N→1         1→N      n + f(n-1)  n × f(n-1)
```

---

# 🏆 FOUR MASTER TEMPLATES

### 1. Print `N → 1`

```python
def solve(n):

    if n == 0:
        return

    print(n)
    solve(n - 1)
```

### 2. Print `1 → N`

```python
def solve(n):

    if n == 0:
        return

    solve(n - 1)
    print(n)
```

### 3. Sum `1 → N`

```python
def solve(n):

    if n == 0:
        return 0

    return n + solve(n - 1)
```

### 4. Factorial

```python
def solve(n):

    if n == 0:
        return 1

    return n * solve(n - 1)
```

---

# ⚠️ TOPGUN / COLLEGE SCREENING CHECKPOINT

Before moving to Problems 5–8, you should be able to answer these instantly:

### Q1. What stops recursion?

```text
→ Base Case
```

### Q2. What makes recursion progress?

```text
→ The input/problem becomes smaller.
```

### Q3. Why does `1 → N` print after the recursive call?

```text
→ Because printing happens during stack unwinding.
```

### Q4. Why does `N → 1` print before the recursive call?

```text
→ Because printing happens during the downward call phase.
```

### Q5. What is the base case of factorial?

```text
→ 0! = 1
```

### Q6. What is the complexity of these simple recursive functions?

```text
Time  → O(N)
Space → O(N) because of call stack
```

---

# 📊 CURRENT TOPGUN DSA PROGRESS

```text
ARRAYS       10/10 ✅
STRINGS      10/10 ✅
HASHING      10/10 ✅
SEARCHING    10/10 ✅
RECURSION     4/10 🔵
```

### Total

```text
44 / 50 problems completed
```

**Next locked set:** 🔵 **Recursion — Conversation 2 → Problems 5–8**

1. Fibonacci
2. Sum of Digits
3. Reverse a String
4. Palindrome Check

Would you like to continue with Recursion Problems 5–8, starting with Fibonacci?

# 🔵 RECURSION — CONVERSATION 2

## Problems 5–8

We continue with the **same locked flow and depth**. No reduction.

### 🎯 Session Mission

| # | Problem          | Main Pattern                          | Level           |
| - | ---------------- | ------------------------------------- | --------------- |
| 5 | Fibonacci Number | Recurrence / Multiple Recursive Calls | 🟢 Basic–Medium |
| 6 | Sum of Digits    | Recursive Digit Decomposition         | 🟢 Basic        |
| 7 | Reverse a String | Recursive Two-Pointer Thinking        | 🟢 Basic        |
| 8 | Palindrome Check | Recursive Two-Pointer                 | 🟢 Basic–Medium |

---

# 🔵 PROBLEM 5 — Fibonacci Number

## 1. Problem Statement

Given an integer `n`, return the `n`th Fibonacci number.

The Fibonacci sequence is:

```text
0, 1, 1, 2, 3, 5, 8, 13, 21, ...
```

Definition:

```text
F(0) = 0
F(1) = 1
F(n) = F(n-1) + F(n-2)
```

### Example

```text
n = 6
```

Output:

```text
8
```

Because:

```text
F(6) = F(5) + F(4)
     = 5 + 3
     = 8
```

---

# 2. Problem Theory

Fibonacci is one of the most important recursion examples because, unlike our previous problems, **one function call creates two recursive calls**.

Previous:

```python
solve(n - 1)
```

Fibonacci:

```python
fib(n - 1)
fib(n - 2)
```

The mathematical recurrence is:

```text
F(n) = F(n-1) + F(n-2)
```

This creates a **recursion tree**.

---

# 3. Pattern Being Tested

### 🔥 Multiple Recursive Calls

```text
             fib(5)
            /      \
       fib(4)      fib(3)
       /   \        /   \
   fib(3) fib(2) fib(2) fib(1)
```

This is the first major difference from the previous four problems.

---

# 4. ELI10 Intuition

Imagine you're trying to find the answer for `5`.

You say:

> "I need the answer for 4 and the answer for 3."

So:

```text
fib(5)
   ↓
fib(4) + fib(3)
```

But `fib(4)` also needs:

```text
fib(3) + fib(2)
```

And the tree keeps growing.

---

# 5. Example

For:

```text
n = 4
```

We have:

```text
fib(4)
= fib(3) + fib(2)

fib(3)
= fib(2) + fib(1)

fib(2)
= fib(1) + fib(0)
```

Base cases:

```text
fib(0) = 0
fib(1) = 1
```

Therefore:

```text
fib(2) = 1 + 0 = 1
fib(3) = 1 + 1 = 2
fib(4) = 2 + 1 = 3
```

---

# 6. Algorithm — Step-by-Step

1. Create `fib(n)`.
2. If `n == 0`, return `0`.
3. If `n == 1`, return `1`.
4. Otherwise:

   ```text
   return fib(n-1) + fib(n-2)
   ```
5. The recursive calls continue until reaching the base cases.
6. Add the returned values.

### Pseudocode

```text
FUNCTION fib(n):

    IF n == 0:
        RETURN 0

    IF n == 1:
        RETURN 1

    RETURN fib(n-1) + fib(n-2)
```

---

# 7. Python Solution — Using Built-in / Library Approach

Python doesn't have a direct standard `fibonacci()` built-in.

A library-free iterative version is more efficient, but it doesn't demonstrate recursion:

```python
n = 6

a = 0
b = 1

for i in range(n):
    a, b = b, a + b

print(a)
```

Output:

```text
8
```

For recursion practice, we need the recursive version.

---

# 8. Python Solution — Without Built-in Methods

```python
def fibonacci(n):

    # Base case 1
    if n == 0:
        return 0

    # Base case 2
    if n == 1:
        return 1

    # Two recursive calls
    return fibonacci(n - 1) + fibonacci(n - 2)


n = 6

result = fibonacci(n)

print(result)
```

Output:

```text
8
```

---

# 9. Line-by-Line Explanation

```python
if n == 0:
    return 0
```

First base case.

---

```python
if n == 1:
    return 1
```

Second base case.

We need two base cases because Fibonacci starts with:

```text
F(0) = 0
F(1) = 1
```

---

```python
return fibonacci(n - 1) + fibonacci(n - 2)
```

This is the heart of the problem.

We calculate **two smaller Fibonacci problems**.

Example:

```text
fib(5)
```

becomes:

```text
fib(4) + fib(3)
```

---

# 10. Detailed Dry Run

Let's use:

```text
n = 5
```

We start:

```text
fib(5)
```

which becomes:

```text
fib(4) + fib(3)
```

Then:

```text
fib(4)
= fib(3) + fib(2)
```

and:

```text
fib(3)
= fib(2) + fib(1)
```

The recursion tree:

```text
                 fib(5)
                /      \
           fib(4)      fib(3)
           /   \        /   \
      fib(3)  fib(2) fib(2) fib(1)
      /   \    / \    / \
 fib(2) fib(1) 1  0  1  0
 /   \
1     0
```

Base values:

```text
fib(0) = 0
fib(1) = 1
```

Then:

```text
fib(2) = 1
fib(3) = 2
fib(4) = 3
fib(5) = 5
```

---

# 11. Dry Run Table

| Function | Calculation | Result |
| -------- | ----------- | -----: |
| `fib(0)` | Base case   |      0 |
| `fib(1)` | Base case   |      1 |
| `fib(2)` | `1 + 0`     |      1 |
| `fib(3)` | `1 + 1`     |      2 |
| `fib(4)` | `2 + 1`     |      3 |
| `fib(5)` | `3 + 2`     |  **5** |
| `fib(6)` | `5 + 3`     |  **8** |

---

# 12. Complexity

This is extremely important.

### Time

Naive recursive Fibonacci:

```text
O(2^n)
```

More precisely, it grows exponentially.

Why?

Because every non-base call creates **two more calls**.

---

### Space

```text
O(n)
```

because the deepest recursion path contains approximately `n` calls.

---

# 13. Edge Cases

### `n = 0`

```text
0
```

### `n = 1`

```text
1
```

### `n = 2`

```text
1
```

### `n = 6`

```text
8
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Only one base case

Wrong:

```python
if n == 0:
    return 0
```

You also need:

```python
if n == 1:
    return 1
```

---

### ❌ Mistake 2 — Wrong recurrence

Wrong:

```python
return fibonacci(n - 1)
```

That doesn't calculate Fibonacci.

Correct:

```python
return fibonacci(n - 1) + fibonacci(n - 2)
```

---

### ❌ Mistake 3 — Thinking this is efficient

The basic recursive version is excellent for **learning recursion**, but inefficient for large `n`.

A memoized/dynamic-programming version reduces the time dramatically.

For your current **basic recursion track**, however, the important goal is understanding the recursion tree.

---

# 15. Pattern Recognition

> **When you see a recurrence depending on multiple smaller values:**
>
> Think:
>
> 🔥 **Multiple Recursive Calls**

Template:

```python
def solve(n):

    if base_case:
        return base_value

    return solve(n - 1) + solve(n - 2)
```

---

# 🔵 PROBLEM 6 — Sum of Digits

## 1. Problem Statement

Given a positive integer `N`, find the sum of all its digits.

### Example

```text
N = 12345
```

Output:

```text
15
```

Because:

```text
1 + 2 + 3 + 4 + 5 = 15
```

---

# 2. Problem Theory

We can separate the last digit using:

```python
n % 10
```

Example:

```text
12345 % 10 = 5
```

Then remove the last digit using:

```python
n // 10
```

Example:

```text
12345 // 10 = 1234
```

Therefore:

```text
sum_digits(n)
=
last digit
+
sum_digits(remaining digits)
```

Mathematically:

```text
sumDigits(n) = n % 10 + sumDigits(n // 10)
```

---

# 3. Pattern Being Tested

### 🔥 Recursive Digit Decomposition

```text
12345
 ↓
5 + sum(1234)
 ↓
5 + 4 + sum(123)
 ↓
5 + 4 + 3 + sum(12)
 ↓
5 + 4 + 3 + 2 + sum(1)
```

---

# 4. ELI10 Intuition

Imagine a number written on paper:

```text
12345
```

Take the last digit:

```text
5
```

Now erase it:

```text
1234
```

Take:

```text
4
```

Erase it:

```text
123
```

Keep doing this until nothing remains.

---

# 5. Example

```text
N = 1234
```

First:

```text
1234 % 10 = 4
1234 // 10 = 123
```

Then:

```text
123 % 10 = 3
123 // 10 = 12
```

Then:

```text
12 % 10 = 2
12 // 10 = 1
```

Then:

```text
1 % 10 = 1
1 // 10 = 0
```

Total:

```text
4 + 3 + 2 + 1 = 10
```

---

# 6. Algorithm — Step-by-Step

1. Create `sum_digits(n)`.
2. Base case:

   * if `n == 0`, return `0`.
3. Get last digit:

   ```text
   n % 10
   ```
4. Remove last digit:

   ```text
   n // 10
   ```
5. Recursively process the remaining number.
6. Add the last digit to the recursive result.

### Pseudocode

```text
FUNCTION sum_digits(n):

    IF n == 0:
        RETURN 0

    last_digit = n % 10

    remaining = n // 10

    RETURN last_digit + sum_digits(remaining)
```

---

# 7. Python Solution — Using Built-in Methods

A simple built-in/string approach is:

```python
n = 12345

total = sum(int(digit) for digit in str(n))

print(total)
```

Output:

```text
15
```

But this does not demonstrate recursive digit decomposition.

---

# 8. Python Solution — Without Built-in Methods

```python
def sum_digits(n):

    # Base case
    if n == 0:
        return 0

    # Get the last digit
    last_digit = n % 10

    # Remove the last digit
    remaining = n // 10

    # Recursive case
    return last_digit + sum_digits(remaining)


n = 12345

result = sum_digits(n)

print(result)
```

Output:

```text
15
```

---

# 9. Line-by-Line Explanation

```python
if n == 0:
    return 0
```

When there are no digits left, stop.

---

```python
last_digit = n % 10
```

Gets the final digit.

For:

```text
12345
```

we get:

```text
5
```

---

```python
remaining = n // 10
```

Removes the last digit.

```text
12345 → 1234
```

---

```python
return last_digit + sum_digits(remaining)
```

Add the current digit to the answer for the remaining digits.

---

# 10. Detailed Dry Run

Input:

```text
12345
```

### Call phase

```text
sum_digits(12345)
```

becomes:

```text
5 + sum_digits(1234)
```

then:

```text
5 + 4 + sum_digits(123)
```

then:

```text
5 + 4 + 3 + sum_digits(12)
```

then:

```text
5 + 4 + 3 + 2 + sum_digits(1)
```

then:

```text
5 + 4 + 3 + 2 + 1 + sum_digits(0)
```

Base:

```text
sum_digits(0) = 0
```

---

### Return phase

| Function            | Last Digit | Recursive Result |  Total |
| ------------------- | ---------: | ---------------: | -----: |
| `sum_digits(0)`     |          — |                0 |      0 |
| `sum_digits(1)`     |          1 |                0 |      1 |
| `sum_digits(12)`    |          2 |                1 |      3 |
| `sum_digits(123)`   |          3 |                3 |      6 |
| `sum_digits(1234)`  |          4 |                6 |     10 |
| `sum_digits(12345)` |          5 |               10 | **15** |

---

# 11. Complexity

If the number has `d` digits:

### Time

```text
O(d)
```

Since we process one digit per call.

For an integer `N`, this can also be expressed as:

```text
O(log N)
```

because the number of digits is proportional to `log₁₀(N)`.

### Space

```text
O(d)
```

because of the recursive call stack.

---

# 12. Edge Cases

### `N = 0`

```text
0
```

### Single digit

```text
7 → 7
```

### Multiple digits

```text
123 → 6
```

### Number containing zero

```text
10203
```

Sum:

```text
1 + 0 + 2 + 0 + 3 = 6
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Using `% 10` as the remaining number

Wrong:

```python
remaining = n % 10
```

That gives the last digit.

Correct:

```python
remaining = n // 10
```

---

### ❌ Mistake 2 — Forgetting `% 10`

Then you don't extract the digit.

---

### ❌ Mistake 3 — No base case

Eventually:

```text
123 → 12 → 1 → 0
```

You need to stop at `0`.

---

# 14. Pattern Recognition

> **When you see:**
> "Process each digit recursively"
>
> Think:
>
> 🔥 `% 10` → extract digit
> 🔥 `// 10` → remove digit

Master pattern:

```python
digit = n % 10
remaining = n // 10
```

---

# 🔵 PROBLEM 7 — Reverse a String

## 1. Problem Statement

Given a string, reverse it using recursion.

### Example

```text
Input:
"hello"

Output:
"olleh"
```

---

# 2. Problem Theory

We can reverse a string recursively by:

1. Taking the first character.
2. Reversing the remaining string.
3. Putting the first character at the end.

Mathematically:

```text
reverse("hello")
=
reverse("ello") + "h"
```

Then:

```text
reverse("ello")
=
reverse("llo") + "e"
```

Eventually:

```text
reverse("o") = "o"
```

---

# 3. Pattern Being Tested

### 🔥 Recursive String Decomposition

```text
"hello"
 ↓
"h" + "ello"
 ↓
"e" + "llo"
 ↓
"l" + "lo"
 ↓
...
```

Then rebuild in reverse order.

---

# 4. ELI10 Intuition

Imagine a line of children:

```text
A B C D
```

Ask the first child:

> "Go to the back."

Then:

```text
B C D A
```

Do the same recursively.

Eventually:

```text
D C B A
```

---

# 5. Example

```text
"cat"
```

We want:

```text
"tac"
```

Break it:

```text
reverse("cat")
=
reverse("at") + "c"
```

Then:

```text
reverse("at")
=
reverse("t") + "a"
```

Base:

```text
reverse("t") = "t"
```

Return:

```text
"t" + "a" + "c"
```

Result:

```text
"tac"
```

---

# 6. Algorithm — Step-by-Step

1. Create `reverse_string(s)`.
2. Base case:

   * if length is `0` or `1`, return the string.
3. Take the first character.
4. Recursively reverse everything after the first character.
5. Put the first character at the end.
6. Return the result.

### Pseudocode

```text
FUNCTION reverse_string(s):

    IF length(s) <= 1:
        RETURN s

    RETURN reverse_string(s[1:]) + s[0]
```

---

# 7. Python Solution — Using Built-in Methods

Python can reverse a string using slicing:

```python
text = "hello"

result = text[::-1]

print(result)
```

Output:

```text
olleh
```

But again, this doesn't demonstrate recursion.

---

# 8. Python Solution — Without Built-in Reverse

```python
def reverse_string(s):

    # Base case
    if len(s) <= 1:
        return s

    # Reverse everything except first character,
    # then place first character at the end
    return reverse_string(s[1:]) + s[0]


text = "hello"

result = reverse_string(text)

print(result)
```

Output:

```text
olleh
```

---

# 9. Line-by-Line Explanation

```python
if len(s) <= 1:
    return s
```

A string with zero or one character is already reversed.

Examples:

```text
"" → ""
"a" → "a"
```

---

```python
s[1:]
```

Gets everything except the first character.

For:

```text
"hello"
```

we get:

```text
"ello"
```

---

```python
s[0]
```

Gets the first character:

```text
"h"
```

---

```python
return reverse_string(s[1:]) + s[0]
```

Reverse the remaining string first, then append the original first character.

---

# 10. Detailed Dry Run

Input:

```text
"hello"
```

### Call phase

```text
reverse("hello")
↓
reverse("ello") + "h"
↓
reverse("llo") + "e" + "h"
↓
reverse("lo") + "l" + "e" + "h"
↓
reverse("o") + "l" + "l" + "e" + "h"
```

Base:

```text
reverse("o") = "o"
```

Return:

```text
"o"
↓
"ol"
↓
"oll"
↓
"olle"
↓
"olleh"
```

---

# 11. Dry Run Table

| Call               | Remaining String | First Character |
| ------------------ | ---------------- | --------------- |
| `reverse("hello")` | `"ello"`         | `h`             |
| `reverse("ello")`  | `"llo"`          | `e`             |
| `reverse("llo")`   | `"lo"`           | `l`             |
| `reverse("lo")`    | `"o"`            | `l`             |
| `reverse("o")`     | —                | `o`             |

Return phase:

```text
o
ol
oll
olle
olleh
```

---

# 12. Complexity

Let `n` be string length.

### Time

With Python slicing:

```text
O(n²)
```

because each recursive call creates a sliced string.

For basic recursion understanding, this is acceptable.

A more optimized index-based implementation can achieve:

```text
O(n)
```

time.

### Space

The recursion stack is:

```text
O(n)
```

and the slicing also creates additional strings.

---

# 13. Edge Cases

```text
"" → ""
"a" → "a"
"ab" → "ba"
"hello" → "olleh"
```

Spaces are treated as normal characters unless the problem says otherwise.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Returning `s[1:]`

That doesn't reverse anything.

### ❌ Mistake 2 — Adding the first character before recursion

```python
return s[0] + reverse_string(s[1:])
```

That reconstructs the original order.

Correct:

```python
return reverse_string(s[1:]) + s[0]
```

---

### ❌ Mistake 3 — No base case

Eventually the string becomes empty and recursion must stop.

---

# 15. Pattern Recognition

> **When you see:**
> "Reverse a string recursively"
>
> Think:
>
> 🔥 **Solve the smaller string → place current character afterward**

Template:

```python
return solve(s[1:]) + s[0]
```

---

# 🔵 PROBLEM 8 — Palindrome Check

## 1. Problem Statement

Given a string, determine whether it reads the same forward and backward.

### Example

```text
"madam"
```

Output:

```text
True
```

Because:

```text
madam
madam
```

---

Another example:

```text
"hello"
```

Output:

```text
False
```

---

# 2. Problem Theory

A palindrome has matching characters from both ends.

For:

```text
"madam"
```

compare:

```text
m ↔ m
a ↔ a
d
```

Everything matches.

Therefore it is a palindrome.

The recursive approach compares:

```text
left character
```

with:

```text
right character
```

and then moves inward.

---

# 3. Pattern Being Tested

### 🔥 Recursive Two-Pointer

```text
LEFT →           ← RIGHT
  ↓                 ↓
compare characters
       ↓
move inward
       ↓
left + 1
right - 1
```

This is a very important pattern.

---

# 4. ELI10 Intuition

Imagine two people standing at opposite ends of a word.

For:

```text
MADAM
```

Person 1 checks:

```text
M
```

Person 2 checks:

```text
M
```

Match.

Move inward:

```text
 A   A
```

Match.

Move inward:

```text
 D
```

Done.

Therefore palindrome.

---

# 5. Example

```text
"racecar"
```

Compare:

```text
r == r ✅
a == a ✅
c == c ✅
```

Middle reached.

Therefore:

```text
True
```

---

# 6. Algorithm — Step-by-Step

Use two indexes:

```text
left = 0
right = len(s) - 1
```

1. If `left >= right`, return `True`.
2. Compare `s[left]` and `s[right]`.
3. If they are different:

   * return `False`.
4. Otherwise:

   * move `left + 1`.
   * move `right - 1`.
5. Recursively check the smaller section.

### Pseudocode

```text
FUNCTION palindrome(s, left, right):

    IF left >= right:
        RETURN True

    IF s[left] != s[right]:
        RETURN False

    RETURN palindrome(s, left + 1, right - 1)
```

---

# 7. Python Solution — Using Built-in Methods

A simple Python approach:

```python
text = "madam"

result = text == text[::-1]

print(result)
```

Output:

```text
True
```

But this uses slicing rather than recursion.

---

# 8. Python Solution — Without Built-in Reverse

```python
def is_palindrome(s, left, right):

    # Base case
    if left >= right:
        return True

    # Characters don't match
    if s[left] != s[right]:
        return False

    # Move toward the center
    return is_palindrome(s, left + 1, right - 1)


text = "madam"

result = is_palindrome(text, 0, len(text) - 1)

print(result)
```

Output:

```text
True
```

---

# 9. Line-by-Line Explanation

```python
if left >= right:
    return True
```

We've reached the middle.

Everything checked so far matched.

Therefore the string is a palindrome.

---

```python
if s[left] != s[right]:
    return False
```

If the outer characters differ, there is no way the string can be a palindrome.

We immediately stop.

---

```python
return is_palindrome(s, left + 1, right - 1)
```

Move both pointers toward the center.

Example:

```text
left:  0 → 1 → 2
right: 6 → 5 → 4
```

---

# 10. Detailed Dry Run

Input:

```text
"madam"
```

Indexes:

```text
0 1 2 3 4
m a d a m
```

Initial:

```text
left = 0
right = 4
```

### Step 1

```text
s[0] = m
s[4] = m
```

Match.

Move:

```text
left = 1
right = 3
```

---

### Step 2

```text
s[1] = a
s[3] = a
```

Match.

Move:

```text
left = 2
right = 2
```

---

### Step 3

```text
left >= right
```

Base case.

Return:

```text
True
```

---

# 11. Dry Run Table

| Step | Left | Right | Left Char | Right Char | Result    |
| ---: | ---: | ----: | --------- | ---------- | --------- |
|    1 |    0 |     4 | `m`       | `m`        | Match     |
|    2 |    1 |     3 | `a`       | `a`        | Match     |
|    3 |    2 |     2 | —         | —          | Base case |

Final:

```text
True
```

---

# 12. Non-Palindrome Dry Run

Input:

```text
"hello"
```

Indexes:

```text
0 1 2 3 4
h e l l o
```

First comparison:

```text
h != o
```

Immediately:

```text
False
```

We don't need to inspect the rest.

---

# 13. Complexity

Let `n` be string length.

### Time

```text
O(n)
```

At most `n/2` comparisons.

### Space

```text
O(n)
```

because of recursive call stack.

---

# 14. Edge Cases

### Empty string

```text
"" → True
```

There are no conflicting characters.

### One character

```text
"a" → True
```

### Two equal characters

```text
"aa" → True
```

### Two different characters

```text
"ab" → False
```

### Odd length

```text
"madam" → True
```

### Even length

```text
"abba" → True
```

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Moving only one pointer

Wrong:

```python
left += 1
```

You need:

```python
left += 1
right -= 1
```

---

### ❌ Mistake 2 — Forgetting the mismatch condition

You must immediately return `False` when:

```python
s[left] != s[right]
```

---

### ❌ Mistake 3 — Incorrect base case

Use:

```python
if left >= right:
```

not only:

```python
if left == right:
```

because even-length strings cross over:

```text
abba

left = 2
right = 1
```

---

# 16. Pattern Recognition

> **When you see:**
> "Check whether a string is a palindrome recursively"
>
> Think:
>
> 🔥 **Two pointers + recursion**

Template:

```python
def check(s, left, right):

    if left >= right:
        return True

    if s[left] != s[right]:
        return False

    return check(s, left + 1, right - 1)
```

---

# 🧠 RECURSION — CONVERSATION 2 MASTER PATTERN MAP

We have now added four important recursion patterns.

| # | Problem        | Pattern                  |
| - | -------------- | ------------------------ |
| 5 | Fibonacci      | Multiple Recursive Calls |
| 6 | Sum of Digits  | `% 10` + `// 10`         |
| 7 | Reverse String | Recursive Decomposition  |
| 8 | Palindrome     | Recursive Two Pointers   |

---

# 🔥 THE BIG CONNECTION

These four problems teach **four different recursion structures**.

### 1️⃣ Fibonacci

```text
             f(n)
            /    \
        f(n-1)  f(n-2)
```

**Multiple recursive calls**

---

### 2️⃣ Sum of Digits

```text
12345
 ↓
1234
 ↓
123
 ↓
12
 ↓
1
 ↓
0
```

**Shrink the number**

```python
n // 10
```

---

### 3️⃣ Reverse String

```text
"hello"
   ↓
"ello"
   ↓
"llo"
   ↓
"lo"
   ↓
"o"
```

**Shrink the string**

---

### 4️⃣ Palindrome

```text
LEFT →       ← RIGHT
       ↓
compare
       ↓
move inward
```

**Shrink from both sides**

---

# 🧠 RECURSION DECISION TREE

When you get a recursion question:

```text
                  RECURSION
                     |
       ┌─────────────┼─────────────┐
       |             |             |
    One call      Two calls     Two pointers
       |             |             |
   n → n-1       n-1 + n-2     left/right
       |             |             |
   Sum/Facts      Fibonacci     Palindrome
```

For digit problems:

```text
Number
  ↓
% 10 → extract
  ↓
/ 10 → shrink
```

For strings:

```text
String
  ↓
s[1:] → shrink
```

---

# 🏆 MASTER TEMPLATES

## Fibonacci

```python
def fibonacci(n):

    if n == 0:
        return 0

    if n == 1:
        return 1

    return fibonacci(n - 1) + fibonacci(n - 2)
```

---

## Sum of Digits

```python
def sum_digits(n):

    if n == 0:
        return 0

    return (n % 10) + sum_digits(n // 10)
```

---

## Reverse String

```python
def reverse_string(s):

    if len(s) <= 1:
        return s

    return reverse_string(s[1:]) + s[0]
```

---

## Palindrome

```python
def is_palindrome(s, left, right):

    if left >= right:
        return True

    if s[left] != s[right]:
        return False

    return is_palindrome(s, left + 1, right - 1)
```

---

# 🎯 COLLEGE / TOPGUN CHECKPOINT

You should now be able to explain these without code:

### Fibonacci

```text
F(n) = F(n-1) + F(n-2)
```

### Digit extraction

```text
Last digit  → n % 10
Remove digit → n // 10
```

### Reverse

```text
reverse(rest) + first_character
```

### Palindrome

```text
compare left/right
→ move inward
→ repeat
```

---

# ⚠️ IMPORTANT RECURSION INSIGHT

Do **not** judge recursion only by:

> "Does the function call itself?"

A stronger way to recognize recursion is:

> **Can I express the current problem as a smaller version of the same problem?**

Examples:

```text
sum(n)
    = n + sum(n-1)

factorial(n)
    = n × factorial(n-1)

fib(n)
    = fib(n-1) + fib(n-2)

sumDigits(n)
    = last_digit + sumDigits(remaining)

reverse(s)
    = reverse(smaller_string) + first_character

palindrome(s)
    = compare outer chars + solve inner string
```

That is the real recursion mindset.

---

# 📊 CURRENT TOPGUN DSA PROGRESS

```text
ARRAYS       10/10 ✅
STRINGS      10/10 ✅
HASHING      10/10 ✅
SEARCHING    10/10 ✅
RECURSION     8/10 🔵
```

### Total

```text
48 / 50 problems completed
```

### Remaining Recursion

**Conversation 3 → Problems 9–10**

1. **Power `xⁿ`** — Recursive Exponentiation
2. **Maximum Element in Array** — Recursive Traversal

Then:

```text
RECURSION → 10/10 ✅
```

and we will do the **complete Recursion Mastery + Pattern Recognition + Mini Test** before moving to your next college-priority topic.

Would you like to continue with Recursion Problems 9–10 in the same detailed flow, starting with Power xⁿ?



# 🔵 RECURSION — CONVERSATION 3

## Problems 9–10 → Final 2 Problems + Recursion Mastery

We are continuing the **locked TopGun execution flow** without reducing depth.

---

# 🔹 PROBLEM 9 — POWER `xⁿ`

## 1. Problem Statement

Given two integers `x` and `n`, calculate:

$$
x^n
$$

using **recursion**.

### Example

```text
Input:
x = 2
n = 5

Output:
32
```

Because:

$$
2^5 = 2 \times 2 \times 2 \times 2 \times 2 = 32
$$

---

# 2. Problem Theory

The mathematical definition of power is:

$$
x^n = x \times x^{n-1}
$$

So:

```text
2^5
= 2 × 2^4
= 2 × 2 × 2^3
= 2 × 2 × 2 × 2^2
= 2 × 2 × 2 × 2 × 2^1
= 32
```

The recursion naturally follows this definition.

### Base Case

$$
x^0 = 1
$$

Therefore:

```python
if n == 0:
    return 1
```

---

# 3. Pattern Being Tested

### 🔥 Pattern: Mathematical Recursion

The pattern is:

```text
Current problem
      ↓
Smaller problem
      ↓
Return and combine
```

General form:

```python
def solve(n):
    if base_case:
        return base_value

    return current_work + solve(smaller_problem)
```

For power:

```python
return x * power(x, n - 1)
```

---

# 4. ELI10 Intuition 🧒

Imagine you have a multiplication machine.

You ask:

> "Give me 2⁵."

The machine says:

> "I don't know 2⁵ directly, but I know that 2⁵ = 2 × 2⁴."

Then:

```text
2⁵
 ↓
2 × 2⁴
       ↓
     2 × 2³
           ↓
         2 × 2²
               ↓
             2 × 2¹
                   ↓
                 2 × 2⁰
                       ↓
                       1
```

Then the answers come back upward:

```text
2⁰ = 1

2¹ = 2 × 1 = 2

2² = 2 × 2 = 4

2³ = 2 × 4 = 8

2⁴ = 2 × 8 = 16

2⁵ = 2 × 16 = 32
```

This is **recursion + return/unwinding**.

---

# 5. Example

```text
x = 3
n = 4
```

We want:

```text
3⁴ = 81
```

Recursive breakdown:

```text
power(3, 4)
    ↓
3 × power(3, 3)
          ↓
        3 × power(3, 2)
                  ↓
                3 × power(3, 1)
                          ↓
                        3 × power(3, 0)
                                  ↓
                                  1
```

Return:

```text
power(3, 0) = 1
power(3, 1) = 3 × 1 = 3
power(3, 2) = 3 × 3 = 9
power(3, 3) = 3 × 9 = 27
power(3, 4) = 3 × 27 = 81
```

---

# 6. Algorithm — Step-by-Step

### Algorithm

1. Define a function `power(x, n)`.
2. Check whether `n == 0`.
3. If yes, return `1`.
4. Otherwise calculate the smaller problem:

   ```text
   power(x, n - 1)
   ```
5. Multiply the result by `x`.
6. Return the result.

### Pseudocode

```text
power(x, n):

    if n == 0:
        return 1

    return x × power(x, n - 1)
```

---

# 7. Python Solution — Using Built-in Method

For comparison, Python already provides exponentiation.

```python
x = 2
n = 5

answer = pow(x, n)

print(answer)
```

Output:

```text
32
```

### Important

For the **recursion question**, don't use `pow()` as your actual algorithm.

The purpose is to demonstrate recursion.

---

# 8. Python Solution — Without Built-in Power

```python
def power(x, n):
    # Base case
    if n == 0:
        return 1

    # Recursive case
    return x * power(x, n - 1)


x = 2
n = 5

answer = power(x, n)

print(answer)
```

Output:

```text
32
```

---

# 9. Line-by-Line Explanation

```python
def power(x, n):
```

Creates a recursive function.

`x` = base.

`n` = exponent.

---

```python
if n == 0:
```

Checks the base case.

We know:

$$
x^0 = 1
$$

---

```python
return 1
```

Stops recursion.

Without this, recursion would never stop.

---

```python
return x * power(x, n - 1)
```

This is the heart of the algorithm.

We convert:

$$
x^n
$$

into:

$$
x \times x^{n-1}
$$

For example:

```text
2⁵
=
2 × 2⁴
```

So:

```python
power(2, 5)
```

becomes:

```python
2 * power(2, 4)
```

---

# 10. Detailed Dry Run

Input:

```text
x = 2
n = 5
```

### Calling phase

| Call         | What happens     |
| ------------ | ---------------- |
| `power(2,5)` | `2 × power(2,4)` |
| `power(2,4)` | `2 × power(2,3)` |
| `power(2,3)` | `2 × power(2,2)` |
| `power(2,2)` | `2 × power(2,1)` |
| `power(2,1)` | `2 × power(2,0)` |
| `power(2,0)` | returns `1`      |

Now recursion starts returning.

### Returning phase

| Function     | Calculation | Result |
| ------------ | ----------: | -----: |
| `power(2,0)` |         `1` |    `1` |
| `power(2,1)` |     `2 × 1` |    `2` |
| `power(2,2)` |     `2 × 2` |    `4` |
| `power(2,3)` |     `2 × 4` |    `8` |
| `power(2,4)` |     `2 × 8` |   `16` |
| `power(2,5)` |    `2 × 16` |   `32` |

Final:

```text
32
```

---

# 11. Time Complexity

There are `n` recursive calls.

```text
power(x,n)
power(x,n-1)
power(x,n-2)
...
power(x,0)
```

Therefore:

$$
\boxed{O(n)}
$$

### Space Complexity

There are `n` active recursive calls on the call stack.

$$
\boxed{O(n)}
$$

---

# 12. Edge Cases

### Case 1 — Exponent is zero

```text
power(5,0)
```

Output:

```text
1
```

---

### Case 2 — Base is zero

```text
power(0,5)
```

Output:

```text
0
```

---

### Case 3 — Base is one

```text
power(1,100)
```

Output:

```text
1
```

---

### Case 4 — Exponent is one

```text
power(7,1)
```

Output:

```text
7
```

---

### Case 5 — Negative exponent

Basic screening versions usually restrict `n >= 0`.

If negative powers are allowed:

$$
x^{-n} = \frac{1}{x^n}
$$

That requires additional handling.

For this **basic TopGun recursion problem**, focus on:

```text
n >= 0
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — No base case

```python
def power(x, n):
    return x * power(x, n - 1)
```

Eventually:

```text
n = -1
n = -2
n = -3
...
```

Infinite recursion.

---

### ❌ Mistake 2 — Wrong base case

```python
if n == 0:
    return 0
```

Wrong.

Because:

$$
x^0 = 1
$$

Correct:

```python
if n == 0:
    return 1
```

---

### ❌ Mistake 3 — Not reducing the problem

```python
return x * power(x, n)
```

`n` never decreases.

Therefore recursion never reaches the base case.

---

# 14. Pattern Recognition

### When you see:

> "Calculate x raised to n using recursion."

Think:

```text
POWER
 ↓
xⁿ = x × xⁿ⁻¹
 ↓
Base case: n = 0
 ↓
Return 1
```

### Mental template

```python
def power(x, n):

    if n == 0:
        return 1

    return x * power(x, n - 1)
```

🔥 **Remember:**

> Mathematical formula → often directly becomes the recursive relation.

---

# 🔹 PROBLEM 10 — MAXIMUM ELEMENT IN ARRAY

## 1. Problem Statement

Given an array, find the **maximum element using recursion**.

### Example

```text
Input:
[4, 7, 2, 9, 1]

Output:
9
```

---

# 2. Problem Theory

Normally, we would scan:

```text
4 → 7 → 2 → 9 → 1
```

and maintain:

```text
maximum
```

With recursion, we divide the problem conceptually:

```text
Maximum of [4,7,2,9,1]

= max(
    4,
    maximum of [7,2,9,1]
  )
```

Then:

```text
maximum [7,2,9,1]

= max(
    7,
    maximum [2,9,1]
  )
```

Eventually we reach one element.

---

# 3. Pattern Being Tested

### 🔥 Pattern: Recursive Traversal

General idea:

```text
Current element
      +
Smaller remaining array
```

This is an important recursion pattern because many recursive array problems follow:

```text
process current element
↓
move to next index
↓
recursive call
```

---

# 4. ELI10 Intuition 🧒

Imagine five students are standing in a line:

```text
4  7  2  9  1
```

You ask the first student:

> "Who is taller: you or everyone after you?"

The first student asks the next student.

Eventually the last student says:

> "I am the maximum because nobody is after me."

Then the answer travels backward.

```text
1
↓
max(9,1) = 9
↓
max(2,9) = 9
↓
max(7,9) = 9
↓
max(4,9) = 9
```

That's recursive traversal.

---

# 5. Example

Input:

```text
arr = [4, 7, 2, 9, 1]
```

Start:

```text
max(0)
```

Compare:

```text
arr[0] = 4
```

with maximum of the remaining array.

So:

```text
max(4, maximum from index 1)
```

Then:

```text
max(7, maximum from index 2)
```

Then:

```text
max(2, maximum from index 3)
```

Then:

```text
max(9, maximum from index 4)
```

Finally:

```text
1
```

Return upward.

---

# 6. Algorithm — Step-by-Step

We use an index.

### Algorithm

1. Start at index `0`.
2. If the index reaches the last element:

   * return that element.
3. Recursively find the maximum from the remaining array.
4. Compare the current element with that recursive maximum.
5. Return the larger value.
6. Continue until the first call receives the final answer.

### Pseudocode

```text
max_element(arr, index):

    if index == last index:
        return arr[index]

    remaining_max = max_element(arr, index + 1)

    return max(arr[index], remaining_max)
```

---

# 7. Python Solution — Using Built-in Method

Python provides:

```python
max()
```

So the normal built-in solution is:

```python
arr = [4, 7, 2, 9, 1]

answer = max(arr)

print(answer)
```

Output:

```text
9
```

Again, this is useful for comparison, but the actual recursion solution should implement the logic ourselves.

---

# 8. Python Solution — Without Built-in `max()`

```python
def recursive_max(arr, index):
    # Base case
    if index == len(arr) - 1:
        return arr[index]

    # Find maximum of remaining elements
    remaining_max = recursive_max(arr, index + 1)

    # Compare current element with remaining maximum
    if arr[index] > remaining_max:
        return arr[index]
    else:
        return remaining_max


arr = [4, 7, 2, 9, 1]

answer = recursive_max(arr, 0)

print(answer)
```

Output:

```text
9
```

---

# 9. Line-by-Line Explanation

```python
def recursive_max(arr, index):
```

Creates a recursive function.

`arr` = input array.

`index` = current position.

---

```python
if index == len(arr) - 1:
```

Checks whether we reached the final element.

For:

```text
[4, 7, 2, 9, 1]
```

last index is:

```text
4
```

---

```python
return arr[index]
```

If only one element remains, that element is automatically the maximum.

For example:

```text
[1]
```

maximum is obviously:

```text
1
```

This is the base case.

---

```python
remaining_max = recursive_max(arr, index + 1)
```

Move to the next element.

This is the recursive step.

For example:

```text
index = 0
```

becomes:

```text
index = 1
```

Then:

```text
1 → 2 → 3 → 4
```

---

```python
if arr[index] > remaining_max:
```

Compare the current element with the maximum found in the remaining array.

---

```python
return arr[index]
```

If the current element is larger, return it.

---

```python
else:
    return remaining_max
```

Otherwise return the maximum from the remaining portion.

---

# 10. Detailed Dry Run

Input:

```text
arr = [4, 7, 2, 9, 1]
```

Call:

```python
recursive_max(arr, 0)
```

### Calling phase

| Index | Current Element | Recursive Call         |
| ----: | --------------: | ---------------------- |
|     0 |               4 | `recursive_max(arr,1)` |
|     1 |               7 | `recursive_max(arr,2)` |
|     2 |               2 | `recursive_max(arr,3)` |
|     3 |               9 | `recursive_max(arr,4)` |
|     4 |               1 | Base case → return `1` |

Now the stack unwinds.

### Returning phase

#### Index 3

```text
current = 9
remaining_max = 1
```

Compare:

```text
9 > 1
```

Return:

```text
9
```

---

#### Index 2

```text
current = 2
remaining_max = 9
```

Compare:

```text
2 > 9 → False
```

Return:

```text
9
```

---

#### Index 1

```text
current = 7
remaining_max = 9
```

Compare:

```text
7 > 9 → False
```

Return:

```text
9
```

---

#### Index 0

```text
current = 4
remaining_max = 9
```

Compare:

```text
4 > 9 → False
```

Return:

```text
9
```

### Final answer

```text
9
```

---

# 11. Recursion Stack Visualization

```text
recursive_max(0)
      ↓
recursive_max(1)
      ↓
recursive_max(2)
      ↓
recursive_max(3)
      ↓
recursive_max(4)
      ↓
      1
      ↑
      9
      ↑
      9
      ↑
      9
      ↑
      9
```

The important idea:

> **Go forward recursively → get the answer → compare while returning.**

---

# 12. Time Complexity

Every element is visited once.

```text
n elements
↓
n recursive calls
```

Therefore:

$$
\boxed{O(n)}
$$

---

# 13. Space Complexity

There are `n` recursive calls on the call stack.

$$
\boxed{O(n)}
$$

Important:

The array itself isn't being copied because we're using an index.

---

# 14. Edge Cases

### Empty array

```text
[]
```

There is no maximum.

For a basic screening problem, either:

* assume array is non-empty, or
* explicitly handle it.

Example:

```python
if len(arr) == 0:
    return None
```

---

### One element

```text
[8]
```

Output:

```text
8
```

Base case handles this.

---

### Negative numbers

```text
[-5, -2, -9]
```

Output:

```text
-2
```

The algorithm works normally.

---

### Duplicate maximum

```text
[5, 9, 3, 9]
```

Output:

```text
9
```

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — No index progression

Wrong:

```python
recursive_max(arr, index)
```

Correct:

```python
recursive_max(arr, index + 1)
```

---

### ❌ Mistake 2 — Wrong base case

You need to stop when you reach the final element.

```python
if index == len(arr) - 1:
```

---

### ❌ Mistake 3 — Comparing before obtaining the recursive answer

The important pattern is:

```python
remaining_max = recursive_max(arr, index + 1)
```

Then:

```python
compare current vs remaining_max
```

---

# 16. Pattern Recognition

### When you see:

> "Find maximum/minimum of an array using recursion."

Think:

```text
Recursive Array Traversal
        ↓
Current element
        +
Remaining elements
        ↓
Base case = last element
```

Template:

```python
def recursive_max(arr, index):

    if index == len(arr) - 1:
        return arr[index]

    remaining_max = recursive_max(arr, index + 1)

    if arr[index] > remaining_max:
        return arr[index]

    return remaining_max
```

---

# 🧠 RECURSION — FINAL 10/10 MASTER MAP

You have now completed all **10 recursion problems**.

|  # | Problem         | Pattern                   |
| -: | --------------- | ------------------------- |
|  1 | Print `1 → N`   | Recursive call → work     |
|  2 | Print `N → 1`   | Work → recursive call     |
|  3 | Sum `1 → N`     | Current + smaller problem |
|  4 | Factorial       | Current × smaller problem |
|  5 | Fibonacci       | Multiple recursive calls  |
|  6 | Sum of digits   | `% 10` + `// 10`          |
|  7 | Reverse string  | Recursive decomposition   |
|  8 | Palindrome      | Recursive two pointers    |
|  9 | Power `xⁿ`      | Mathematical recursion    |
| 10 | Maximum element | Recursive array traversal |

---

# 🔥 RECURSION PATTERN RECOGNITION

This is the part you **must remember for the TopGun screening**.

## Pattern 1 — Simple Linear Recursion

```text
f(n)
 ↓
f(n-1)
```

Examples:

```text
Print 1→N
Sum 1→N
Factorial
Power
```

---

## Pattern 2 — Work Before Recursive Call

```python
work()
recursive_call()
```

Example:

```text
N → 1
```

---

## Pattern 3 — Work After Recursive Call

```python
recursive_call()
work()
```

Example:

```text
1 → N
```

---

## Pattern 4 — Return-Based Recursion

```python
return current + recursive_call()
```

or

```python
return current * recursive_call()
```

Examples:

```text
Sum
Factorial
Power
```

---

## Pattern 5 — Multiple Recursive Calls

```python
f(n - 1) + f(n - 2)
```

Example:

```text
Fibonacci
```

This creates a **recursion tree**.

---

## Pattern 6 — Digit Recursion

When you see:

```text
digits
```

think:

```text
n % 10
```

to extract the last digit.

And:

```text
n // 10
```

to remove it.

Example:

```text
Sum of digits
```

---

## Pattern 7 — Recursive Two Pointers

When you see:

```text
compare beginning and ending
```

think:

```text
left + 1
right - 1
```

Example:

```text
Palindrome
```

---

## Pattern 8 — Recursive Array Traversal

When you see:

```text
find max
find min
process every array element
```

think:

```text
index + 1
```

Example:

```text
Maximum element
```

---

# 🧠 THE 5 QUESTIONS YOU SHOULD ASK IN EVERY RECURSION PROBLEM

Before writing code, ask:

### 1. What is the base case?

```text
When should recursion stop?
```

### 2. What is the smaller problem?

```text
n - 1?
index + 1?
left + 1 / right - 1?
n // 10?
```

### 3. What happens before the recursive call?

```text
work first?
```

### 4. What happens after the recursive call?

```text
combine result?
```

### 5. Does every call move toward the base case?

This is critical.

If the answer is **NO**, your recursion is probably broken.

---

# 🏆 RECURSION MASTER TEMPLATE

```python
def solve(problem):

    # 1. Base case
    if base_condition:
        return base_answer

    # 2. Solve smaller problem
    smaller_answer = solve(smaller_problem)

    # 3. Combine current work + smaller answer
    return combine(smaller_answer)
```

For simple recursion:

```text
BASE CASE
    ↓
SMALLER PROBLEM
    ↓
RECURSIVE CALL
    ↓
RETURN / UNWIND
    ↓
FINAL ANSWER
```

---

# 🎯 TOPGUN RECURSION CHECKLIST

You should now be able to recognize:

```text
1 → N                  → recursive call before print
N → 1                  → print before recursive call
Sum                    → current + recursive result
Factorial              → current × recursive result
Fibonacci              → two recursive calls
Sum digits             → %10 and //10
Reverse string         → recursive decomposition
Palindrome             → two pointers
Power                  → mathematical recurrence
Maximum array element  → recursive traversal
```

## 🔵 RECURSION STATUS

```text
RECURSION       10/10 ✅
```

### Overall TopGun DSA progress

```text
ARRAYS          10/10 ✅
STRINGS         10/10 ✅
HASHING         10/10 ✅
SEARCHING       10/10 ✅
RECURSION       10/10 ✅
──────────────────────
TOTAL           50/50 🔥
```

**Recursion is now complete.**

Would you like to do the recursion mini test next, or move on to the next college-priority topic?


