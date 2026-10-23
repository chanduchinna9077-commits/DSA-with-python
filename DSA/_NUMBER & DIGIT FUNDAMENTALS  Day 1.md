
# 🟢 DAY 1

## NUMBER & DIGIT FUNDAMENTALS

### Problems 1–10

```text
Reverse Number
Palindrome Number
Count Digits
Sum of Digits
Prime Number
GCD
LCM
Armstrong Number
Perfect Number
Harshad Number
```

### 🎯 Skill

**Digit manipulation + mathematical loops**

# 🔥 CR2 SPECIAL TRAINING — DAY 1

## 📕 SESSION 1 — PROBLEMS 1–3

### 🎯 DAY 1 THEME

**NUMBER & DIGIT FUNDAMENTALS**

Today's objective is to build the first major coding pattern:

```text
NUMBER
  ↓
EXTRACT DIGIT
  ↓
PROCESS DIGIT
  ↓
REMOVE DIGIT
  ↓
REPEAT
```

The three problems are deliberately connected:

```text
1️⃣ Reverse Number
       ↓
2️⃣ Palindrome Number
       ↓
3️⃣ Count Digits
```

If you understand Problem 1 properly, Problems 2 and 3 become much easier.

---

# 🟢 PROBLEM 1 — REVERSE A NUMBER

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Reverse a Number

**LeetCode:** ✅ Exact interview version exists

**LeetCode #7 — Reverse Integer**

**Difficulty:** 🟡 Medium on LeetCode. The basic placement version is easier than the full LeetCode version because LeetCode adds signed 32-bit overflow requirements. ([LeetCode][1])

### 🔥 What are we actually testing?

This looks extremely basic, but it teaches one of the most important number-manipulation patterns:

```text
% 10  → get last digit
// 10  → remove last digit
* 10   → shift digits left
```

This pattern will reappear in:

* Palindrome Number
* Armstrong Number
* Strong Number
* Sum of Digits
* Product of Digits
* Reverse-related problems
* Digit-frequency problems

### 🧠 Senior recognition

Whenever you see:

> "Process each digit of an integer"

your first thought should be:

```text
digit = n % 10
n = n // 10
```

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Problem

Given an integer `n`, reverse its digits.

### 📥 Input

```text
1234
```

### 📤 Output

```text
4321
```

### 🧪 Examples

```text
1234 → 4321
5678 → 8765
1200 → 21
7    → 7
```

For the basic placement version, we'll handle non-negative integers.

### ⚠️ Important LeetCode difference

LeetCode 7 also handles negative numbers and requires the result to remain within the signed 32-bit integer range. ([LeetCode][1])

---

# 💡 BLOCK 3 — LOGIC / INTUITION

Suppose:

```text
n = 1234
```

We want:

```text
4321
```

Take the last digit:

```text
1234 % 10 = 4
```

Now remove it:

```text
1234 // 10 = 123
```

Our answer currently becomes:

```text
4
```

Next:

```text
123 % 10 = 3
```

Append `3`:

```text
4 × 10 + 3 = 43
```

Continue:

```text
43
432
4321
```

### 🔥 Core formula

```text
digit = n % 10

reverse = reverse * 10 + digit

n = n // 10
```

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → Read n
STEP 2 → Create reverse = 0
STEP 3 → Extract last digit using n % 10
STEP 4 → Add digit to reverse
STEP 5 → Remove last digit using n // 10
STEP 6 → Repeat until n becomes 0
STEP 7 → Return reverse
```

### 🧠 Memorize this pattern

```text
EXTRACT → APPEND → REMOVE → REPEAT
```

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def reverse_number(n):
    reversed_num = 0

    while n > 0:
        digit = n % 10
        reversed_num = reversed_num * 10 + digit
        n = n // 10

    return reversed_num


# Main program
num = int(input("Enter a number: "))

result = reverse_number(num)

print("Reversed number:", result)
```

### 🚀 Why this solution?

We process every digit exactly once.

We don't need:

```python
str(n)[::-1]
```

because the purpose of this problem is to master **integer digit manipulation**.

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static int reverseNumber(int n) {
        int reversedNum = 0;

        while (n > 0) {
            int digit = n % 10;
            reversedNum = reversedNum * 10 + digit;
            n = n / 10;
        }

        return reversedNum;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

        int result = reverseNumber(num);

        System.out.println("Reversed number: " + result);

        scanner.close();
    }
}
```

### ☕ Java placement structure

Remember:

```text
import
   ↓
class Main
   ↓
method
   ↓
main()
   ↓
input
   ↓
call method
   ↓
output
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
1234
```

### Initial state

```text
n = 1234
reversed_num = 0
```

### 🔄 Iteration 1

```text
digit = 1234 % 10
      = 4
```

```text
reversed_num = 0 * 10 + 4
             = 4
```

```text
n = 1234 // 10
  = 123
```

State:

```text
n = 123
reversed_num = 4
```

---

### 🔄 Iteration 2

```text
digit = 123 % 10
      = 3
```

```text
reversed_num = 4 * 10 + 3
             = 43
```

```text
n = 123 // 10
  = 12
```

State:

```text
n = 12
reversed_num = 43
```

---

### 🔄 Iteration 3

```text
digit = 12 % 10
      = 2
```

```text
reversed_num = 43 * 10 + 2
             = 432
```

```text
n = 12 // 10
  = 1
```

---

### 🔄 Iteration 4

```text
digit = 1 % 10
      = 1
```

```text
reversed_num = 432 * 10 + 1
             = 4321
```

```text
n = 1 // 10
  = 0
```

Loop stops.

### 📊 Complete dry-run table

| Iteration |  `n` | `digit` | `reversed_num` |
| --------- | ---: | ------: | -------------: |
| Initial   | 1234 |       — |              0 |
| 1         | 1234 |       4 |              4 |
| 2         |  123 |       3 |             43 |
| 3         |   12 |       2 |            432 |
| 4         |    1 |       1 |           4321 |
| End       |    0 |       — |       **4321** |

### ✅ Final output

```text
Reversed number: 4321
```

---

# ☕ BLOCK 8 — JAVA DRY RUN

The mathematical execution is identical.

For:

```text
n = 1234
```

Java performs:

```text
1234 % 10 → 4
1234 / 10 → 123

123 % 10 → 3
123 / 10 → 12

12 % 10 → 2
12 / 10 → 1

1 % 10 → 1
1 / 10 → 0
```

Final:

```text
reversedNum = 4321
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

Let `d` = number of digits.

### ⏱️ Time

```text
O(d)
```

Why?

Every digit is processed exactly once.

For a number `n`, the number of digits is:

```text
O(log₁₀ n + 1)
```

So you can also describe the time as:

```text
O(log n)
```

### 💾 Auxiliary Space

```text
O(1)
```

Only a fixed number of variables are used.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. Why do we use `% 10`?

`% 10` gives the remainder after division by 10, which is exactly the last digit.

```text
1234 % 10 = 4
```

So:

> `% 10` → extract last digit.

---

### 🎤 Q2. Why do we use `// 10`?

Integer division by 10 removes the last digit.

```text
1234 // 10 = 123
```

So:

> `// 10` → remove last digit.

---

### 🎤 Q3. Why is `reverse * 10 + digit` used?

Suppose:

```text
reverse = 43
digit = 2
```

We need:

```text
432
```

Multiplying by 10 shifts `43`:

```text
43 × 10 = 430
```

Then:

```text
430 + 2 = 432
```

Therefore:

```text
reverse * 10 + digit
```

adds a new digit to the right side.

---

### 🎤 Q4. What is the LeetCode complication?

LeetCode 7 requires the reversed value to fit inside:

```text
[-2³¹, 2³¹ - 1]
```

If it overflows, return `0`. ([LeetCode][1])

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

# 🔥 DIGIT MANIPULATION MASTER PATTERN

```text
          NUMBER
             ↓
        n % 10
             ↓
       LAST DIGIT
             ↓
       PROCESS IT
             ↓
        n // 10
             ↓
      REMOVE DIGIT
             ↓
          REPEAT
```

### 🚨 Remember

```text
% 10  → GET
// 10  → REMOVE
* 10   → SHIFT
```

This is one of your first CR2 **must-remember templates**.

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Forgetting `reversed_num * 10`

❌ Writing:

```python
reversed_num = reversed_num + digit
```

instead of:

```python
reversed_num = reversed_num * 10 + digit
```

❌ Forgetting:

```python
n = n // 10
```

which causes an infinite loop.

❌ Ignoring negative numbers when the actual problem requires them.

❌ Ignoring overflow in Java/LeetCode 7.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** "I need to process digits of an integer."

> ⚙️ **Approach:** Extract last digit → append → remove last digit.

> 🐍 **Python:** `% 10`, `// 10`.

> ☕ **Java:** `% 10`, `/ 10`.

> ⏱️ **Complexity:** `O(d)` time.

> 💾 **Space:** `O(1)` auxiliary.

---

# 🟢 PROBLEM 2 — PALINDROME NUMBER

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Check Palindrome Number

**LeetCode:** ✅ Exact problem

**LeetCode #9 — Palindrome Number**

**Difficulty:** 🟢 Easy. LeetCode's problem is the direct match. ([LeetCode][2])

### 🔥 Core idea

A number is a palindrome if:

```text
ORIGINAL == REVERSED
```

Examples:

```text
121 → 121 → YES

123 → 321 → NO
```

This problem is intentionally placed immediately after Reverse Number.

Why?

Because **Palindrome Number is basically Reverse Number + one comparison**.

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Problem

Given an integer `x`, determine whether it reads the same from left to right and right to left.

### Examples

```text
121   → True
1221  → True
123   → False
10    → False
0     → True
```

### ⚠️ Negative number

For the LeetCode problem:

```text
-121 → False
```

because the negative sign makes it non-palindromic.

---

# 💡 BLOCK 3 — LOGIC / INTUITION

Take:

```text
1221
```

Reverse it:

```text
1221
```

Compare:

```text
1221 == 1221
```

Therefore:

```text
True
```

Take:

```text
1234
```

Reverse:

```text
4321
```

Comparison:

```text
1234 != 4321
```

Therefore:

```text
False
```

### 🔥 Formula

```text
Palindrome
    =
Original Number == Reversed Number
```

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → Reject negative numbers
STEP 2 → Store original number
STEP 3 → Reverse the number
STEP 4 → Compare original and reversed
STEP 5 → If equal → True
STEP 6 → Otherwise → False
```

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def is_palindrome_number(n):
    if n < 0:
        return False

    original = n
    reversed_num = 0

    while n > 0:
        digit = n % 10
        reversed_num = reversed_num * 10 + digit
        n = n // 10

    return original == reversed_num


# Main program
num = int(input("Enter a number: "))

result = is_palindrome_number(num)

print("Is palindrome:", result)
```

### 🧠 Why save `original`?

Because the variable `n` is destroyed during:

```python
n = n // 10
```

So we need another variable for comparison.

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static boolean isPalindromeNumber(int n) {

        if (n < 0) {
            return false;
        }

        int original = n;
        int reversedNum = 0;

        while (n > 0) {
            int digit = n % 10;
            reversedNum = reversedNum * 10 + digit;
            n = n / 10;
        }

        return original == reversedNum;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

        boolean result = isPalindromeNumber(num);

        System.out.println("Is palindrome: " + result);

        scanner.close();
    }
}
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
1221
```

Initial:

```text
original = 1221
n = 1221
reversed_num = 0
```

### Iteration 1

```text
digit = 1221 % 10
      = 1

reversed_num = 0 * 10 + 1
             = 1

n = 1221 // 10
  = 122
```

### Iteration 2

```text
digit = 122 % 10
      = 2

reversed_num = 1 * 10 + 2
             = 12

n = 122 // 10
  = 12
```

### Iteration 3

```text
digit = 12 % 10
      = 2

reversed_num = 12 * 10 + 2
             = 122

n = 12 // 10
  = 1
```

### Iteration 4

```text
digit = 1 % 10
      = 1

reversed_num = 122 * 10 + 1
             = 1221

n = 1 // 10
  = 0
```

Loop ends.

Now:

```text
original = 1221
reversed = 1221
```

Therefore:

```text
1221 == 1221
```

### ✅ Answer

```text
True
```

### 📊 Complete table

| Step    |  `n` | Digit | Reverse |
| ------- | ---: | ----: | ------: |
| Initial | 1221 |     — |       0 |
| 1       | 1221 |     1 |       1 |
| 2       |  122 |     2 |      12 |
| 3       |   12 |     2 |     122 |
| 4       |    1 |     1 |    1221 |
| End     |    0 |     — |    1221 |

---

# ☕ BLOCK 8 — JAVA DRY RUN

For:

```text
1221
```

the Java variables evolve identically:

```text
original = 1221

n = 1221 → reverse = 1
n = 122  → reverse = 12
n = 12   → reverse = 122
n = 1    → reverse = 1221
n = 0
```

Then:

```java
return original == reversedNum;
```

becomes:

```text
1221 == 1221
```

Result:

```text
true
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

Let `d` be the number of digits.

### ⏱️ Time

```text
O(d)
```

Each digit is processed once.

### 💾 Auxiliary Space

```text
O(1)
```

Only a constant number of variables.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. Why can we use the Reverse Number algorithm here?

Because:

```text
Palindrome
=
Number equals its reverse
```

So we reuse the digit-reversal technique instead of inventing a new approach.

---

### 🎤 Q2. Can we solve it without reversing the entire number?

Yes.

For the LeetCode version, you can reverse only **half of the number** and compare the two halves.

That avoids constructing the entire reversed number.

Time remains:

```text
O(d)
```

and auxiliary space remains:

```text
O(1)
```

The number of processed digits is approximately half, but Big-O remains `O(d)`.

---

### 🎤 Q3. Why are negative numbers rejected?

Because the minus sign exists only on the left:

```text
-121
```

It does not form a symmetric representation.

LeetCode 9 explicitly treats negative integers as non-palindromes.

---

### 🎤 Q4. What happens with `10`?

```text
10 → reverse = 1
```

Therefore:

```text
10 != 1
```

So:

```text
False
```

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

This is the direct connection:

```text
PROBLEM 1
Reverse Number
      ↓
PROBLEM 2
Palindrome Number
      ↓
Original == Reverse
```

🔥 **Major CR2 pattern:**

> If a problem asks whether something reads the same backward, immediately consider reversal or two-pointer comparison.

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Forgetting to save the original number.

❌ Returning `True` after merely reversing.

❌ Forgetting negative numbers.

❌ Mishandling `0`.

❌ Writing the reverse formula incorrectly.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** Same forward and backward → palindrome.

> ⚙️ **Approach:** Reverse the number and compare.

> 🐍 **Python:** `% 10` + `// 10`.

> ☕ **Java:** `% 10` + `/ 10`.

> ⏱️ **Time:** `O(d)`.

> 💾 **Space:** `O(1)`.

---

# 🟢 PROBLEM 3 — COUNT DIGITS OF A NUMBER

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Count Digits of a Number

**LeetCode:** ❌ No exact standard LeetCode problem that simply asks "count the number of digits of an integer."

There are related digit-counting problems, such as **LC 2520 — Count the Digits That Divide a Number (Easy)**, but that asks a different question: how many digits of a number divide the number. ([LeetCode][3])

So we should **not falsely assign LC 2520 to this problem**.

### 🎯 Difficulty

🟢 **Easy**

### 🔥 Why is it in CR2?

Because it teaches one of the most fundamental number-processing patterns:

```text
n // 10
```

Every division removes one digit.

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Problem

Given an integer `n`, count how many digits it contains.

### Examples

```text
12345 → 5
987   → 3
7     → 1
1000  → 4
0     → 1
-456  → 3
```

The negative sign is **not a digit**.

---

# 💡 BLOCK 3 — LOGIC / INTUITION

Take:

```text
5832
```

Repeatedly divide by 10:

```text
5832 → 583
 583 → 58
  58 → 5
   5 → 0
```

How many times did we divide?

```text
4
```

Therefore:

```text
5832 has 4 digits
```

### Special case

What about:

```text
0
```

If we simply write:

```python
while n > 0:
```

the loop won't execute.

But:

```text
0
```

is still **one digit**.

So we handle it separately.

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → Take n
STEP 2 → Ignore negative sign using absolute value
STEP 3 → If n == 0, return 1
STEP 4 → Set count = 0
STEP 5 → Divide n by 10
STEP 6 → Increase count
STEP 7 → Repeat until n becomes 0
STEP 8 → Return count
```

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def count_digits(n):
    n = abs(n)

    if n == 0:
        return 1

    count = 0

    while n > 0:
        n = n // 10
        count += 1

    return count


# Main program
num = int(input("Enter a number: "))

result = count_digits(num)

print("Number of digits:", result)
```

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static int countDigits(int n) {

        n = Math.abs(n);

        if (n == 0) {
            return 1;
        }

        int count = 0;

        while (n > 0) {
            n = n / 10;
            count++;
        }

        return count;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

        int result = countDigits(num);

        System.out.println("Number of digits: " + result);

        scanner.close();
    }
}
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
5832
```

Initial:

```text
n = 5832
count = 0
```

### Iteration 1

```text
5832 // 10 = 583

count = 1
```

### Iteration 2

```text
583 // 10 = 58

count = 2
```

### Iteration 3

```text
58 // 10 = 5

count = 3
```

### Iteration 4

```text
5 // 10 = 0

count = 4
```

Loop stops.

### 📊 Complete dry run

| Step    | `n` Before | `n // 10` | `count` |
| ------- | ---------: | --------: | ------: |
| Initial |       5832 |         — |       0 |
| 1       |       5832 |       583 |       1 |
| 2       |        583 |        58 |       2 |
| 3       |         58 |         5 |       3 |
| 4       |          5 |         0 |       4 |

### ✅ Final answer

```text
4
```

---

# 🧪 EDGE CASE DRY RUN — ZERO

Input:

```text
0
```

First:

```python
n = abs(0)
```

Result:

```text
0
```

Then:

```python
if n == 0:
    return 1
```

Therefore:

```text
Answer = 1
```

Correct.

---

# ☕ BLOCK 8 — JAVA DRY RUN

For:

```text
5832
```

```text
n = 5832
count = 0

n = 583
count = 1

n = 58
count = 2

n = 5
count = 3

n = 0
count = 4
```

Return:

```text
4
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

Let `d` be the number of digits.

### ⏱️ Time

```text
O(d)
```

because each iteration removes exactly one digit.

Since:

```text
d ≈ log₁₀(n) + 1
```

we can also describe it as:

```text
O(log n)
```

### 💾 Auxiliary Space

```text
O(1)
```

Only:

```text
n
count
```

are required.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. Why does `n // 10` remove one digit?

Because integer division discards the remainder.

Example:

```text
5832 / 10 = 583.2
```

Integer division:

```text
5832 // 10 = 583
```

The last digit `2` disappears.

---

### 🎤 Q2. Can you solve this using a string?

Yes.

```python
len(str(abs(n)))
```

This is extremely simple.

But the arithmetic solution is valuable because it teaches the underlying digit-manipulation technique without converting the number into a string.

---

### 🎤 Q3. Can this be done in O(1)?

For ordinary fixed-width integers, a logarithmic formula or a finite number of comparisons can be treated as `O(1)`.

For example, mathematically:

```text
digits = floor(log10(n)) + 1
```

for positive `n`.

But there are special cases involving `0` and floating-point precision.

For CR2, the integer-division approach is the better learning template.

---

### 🎤 Q4. What is the difference between this and Sum of Digits?

Count Digits:

```text
5832
→ 4 digits
```

Sum Digits:

```text
5 + 8 + 3 + 2
= 18
```

The traversal pattern is the same.

Only the accumulation changes.

```text
COUNT:
count += 1

SUM:
sum += digit
```

🔥 This is an important pattern connection for **Problem 4**.

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

You now have another fundamental digit template:

```text
        NUMBER
           ↓
      n // 10
           ↓
     REMOVE DIGIT
           ↓
       COUNT++
           ↓
        REPEAT
```

Compare today's three problems:

```text
🔄 Reverse Number
    ↓
digit = n % 10
reverse = reverse * 10 + digit
n = n // 10
```

```text
🔁 Palindrome Number
    ↓
Reverse Number
    ↓
original == reverse
```

```text
🔢 Count Digits
    ↓
n = n // 10
count += 1
```

### 🔥 This is the foundation.

You should now start seeing digit problems as **variations of one underlying loop**, not as completely separate problems.

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Forgetting that `0` contains one digit.

❌ Counting the negative sign as a digit.

❌ Using:

```python
n = n / 10
```

instead of integer division.

❌ Forgetting to increment `count`.

❌ Using a loop that never changes `n`.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** "I need the number of digits."

> ⚙️ **Approach:** Repeatedly divide by 10.

> 🐍 **Python:** `n //= 10`

> ☕ **Java:** `n /= 10`

> ⏱️ **Time:** `O(d)` / `O(log n)`

> 💾 **Space:** `O(1)`

---

# 🏆 DAY 1 — SESSION 1 COMPLETE

## ✅ 3 / 10 PROBLEMS

### 1️⃣ Reverse a Number

```text
🔥 Core Pattern:
% 10 → extract
// 10 → remove
* 10 → shift
```

### 2️⃣ Palindrome Number

```text
🔥 Core Pattern:
Original == Reverse
```

### 3️⃣ Count Digits

```text
🔥 Core Pattern:
// 10 → remove digit
count++ → count digit
```

---

# 🧠 SESSION 1 MASTER CONNECTION

This is what I want you to retain—not three isolated programs:

```text
                 🔢 NUMBER
                    │
             ┌──────┴──────┐
             ↓             ↓
          % 10           // 10
             │             │
        Extract Digit   Remove Digit
             │             │
             └──────┬──────┘
                    ↓
             PROCESS DIGIT
                    │
          ┌─────────┼─────────┐
          ↓         ↓         ↓
       Reverse     Sum      Count
          │
          ↓
     Palindrome
```

# 🚨 YOUR PRACTICE TASK

Before moving to **Session 2**, do these three **without looking back at the code**:

```text
🔥 Q1 → Reverse 48391

🔥 Q2 → Check whether 12321 is a palindrome

🔥 Q3 → Count digits in 908765
```

Then write each program **from scratch in Python**.

After that, you can move to:

# 📗 DAY 1 — SESSION 2

## Problems 4–6

**4️⃣ Sum of Digits**
**5️⃣ Check Prime Number**
**6️⃣ Find GCD of Two Numbers**

These three will build directly on today's digit and mathematical patterns.

Would you like to continue with Day 1, Session 2, or do a quick no-solution check on these three problems first?

[1]: https://leetcode.com/discuss/post/2021593/7-reverse-integer/?utm_source=chatgpt.com "7. Reverse Integer - Discuss - LeetCode"
[2]: https://leetcode.com/discuss/post/2259436/palindromic-problems-list-with-hints/?utm_source=chatgpt.com "Palindromic Problems List with Hints - Discuss - LeetCode"
[3]: https://leetcode.com/problems/count-the-digits-that-divide-a-number/description/?envId=math&envType=problem-list-v2&utm_source=chatgpt.com "Count the Digits That Divide a Number - LeetCode"


# 🔥 CR2 SPECIAL TRAINING — DAY 1

## 📗 SESSION 2 — PROBLEMS 4–6

### 🎯 TODAY'S THEME

**NUMBER LOGIC → DIGIT PROCESSING → MATHEMATICAL ALGORITHMS**

Today we move from the digit-extraction foundation into three very important placement patterns:

```text
4️⃣ Sum of Digits
       ↓
5️⃣ Prime Number
       ↓
6️⃣ GCD
```

These three problems teach you three different ways of thinking:

```text
🔢 Digit traversal
🧮 Divisibility / factors
⚙️ Mathematical optimization
```

---

# 🟢 PROBLEM 4 — SUM OF DIGITS

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Sum of Digits of a Number

**LeetCode:** ❌ No exact standard LeetCode problem matching the basic placement statement.

There are related digit-sum problems on LeetCode, but we should not falsely assign one as an exact match.

**Difficulty:** 🟢 Easy

### 🔥 Why is this important?

This is a direct extension of **Problem 3 — Count Digits**.

Previously:

```text
n % 10 → extract digit
n // 10 → remove digit
count += 1
```

Now:

```text
n % 10 → extract digit
n // 10 → remove digit
sum += digit
```

🔥 The traversal is identical.

Only the **accumulation operation** changes.

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Problem

Given a positive integer `n`, calculate the sum of all its digits.

### 🧪 Examples

```text
1234 → 1 + 2 + 3 + 4 = 10

5832 → 5 + 8 + 3 + 2 = 18

900 → 9 + 0 + 0 = 9

7 → 7
```

### 📥 Input

```text
12345
```

### 📤 Output

```text
15
```

---

# 💡 BLOCK 3 — LOGIC / INTUITION

Take:

```text
n = 5832
```

Extract the last digit:

```text
5832 % 10 = 2
```

Add it:

```text
sum = 0 + 2 = 2
```

Remove the digit:

```text
5832 // 10 = 583
```

Again:

```text
583 % 10 = 3
sum = 2 + 3 = 5
```

Continue:

```text
8 → sum = 13
5 → sum = 18
```

Final:

```text
18
```

### 🔥 Core pattern

```text
EXTRACT → ADD → REMOVE → REPEAT
```

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → Read n
STEP 2 → Convert n to positive using abs()
STEP 3 → Initialize sum = 0
STEP 4 → Extract last digit using n % 10
STEP 5 → Add digit to sum
STEP 6 → Remove last digit using n // 10
STEP 7 → Repeat until n becomes 0
STEP 8 → Return sum
```

### 🧠 One-line algorithm

```text
sum += n % 10
n //= 10
```

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def sum_of_digits(n):
    n = abs(n)

    total = 0

    while n > 0:
        digit = n % 10
        total += digit
        n = n // 10

    return total


# Main program
num = int(input("Enter a number: "))

result = sum_of_digits(num)

print("Sum of digits:", result)
```

### ⚠️ Zero case

For:

```text
0
```

the loop does not execute, so `total` remains `0`.

That's correct:

```text
sum of digits of 0 = 0
```

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static int sumOfDigits(int n) {

        n = Math.abs(n);

        int total = 0;

        while (n > 0) {
            int digit = n % 10;
            total += digit;
            n = n / 10;
        }

        return total;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

        int result = sumOfDigits(num);

        System.out.println("Sum of digits: " + result);

        scanner.close();
    }
}
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
5832
```

Initial:

```text
n = 5832
total = 0
```

### 🔄 Iteration 1

```text
digit = 5832 % 10
      = 2

total = 0 + 2
      = 2

n = 5832 // 10
  = 583
```

### 🔄 Iteration 2

```text
digit = 583 % 10
      = 3

total = 2 + 3
      = 5

n = 583 // 10
  = 58
```

### 🔄 Iteration 3

```text
digit = 58 % 10
      = 8

total = 5 + 8
      = 13

n = 58 // 10
  = 5
```

### 🔄 Iteration 4

```text
digit = 5 % 10
      = 5

total = 13 + 5
      = 18

n = 5 // 10
  = 0
```

Loop ends.

### 📊 Complete table

| Step    |  `n` | Digit | `total` |
| ------- | ---: | ----: | ------: |
| Initial | 5832 |     — |       0 |
| 1       | 5832 |     2 |       2 |
| 2       |  583 |     3 |       5 |
| 3       |   58 |     8 |      13 |
| 4       |    5 |     5 |      18 |
| End     |    0 |     — |  **18** |

### ✅ Final output

```text
Sum of digits: 18
```

---

# ☕ BLOCK 8 — JAVA DRY RUN

For:

```text
5832
```

Java executes:

```text
5832 % 10 → 2
total = 2
5832 / 10 → 583

583 % 10 → 3
total = 5
583 / 10 → 58

58 % 10 → 8
total = 13
58 / 10 → 5

5 % 10 → 5
total = 18
5 / 10 → 0
```

Final:

```text
18
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

Let `d` = number of digits.

### ⏱️ Time Complexity

```text
O(d)
```

Each digit is processed exactly once.

Equivalent in terms of numeric magnitude:

```text
O(log n)
```

### 💾 Space Complexity

```text
O(1)
```

Only a fixed number of variables are used.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. How would you find the digital root instead of the digit sum?

You repeatedly sum the digits until only one digit remains.

For example:

```text
9875
↓
9 + 8 + 7 + 5 = 29
↓
2 + 9 = 11
↓
1 + 1 = 2
```

Answer:

```text
2
```

There is also a mathematical digital-root formula involving modulo 9, but the iterative approach is easier to understand and code in a basic placement round.

---

### 🎤 Q2. Can you solve digit sum using a string?

Yes:

```python
sum(int(ch) for ch in str(abs(n)))
```

That's concise, but the arithmetic approach is more useful for mastering digit manipulation.

---

### 🎤 Q3. What changes if the number is negative?

Use:

```python
n = abs(n)
```

For example:

```text
-5832 → 5832 → 18
```

The minus sign isn't considered a digit.

---

### 🎤 Q4. How is this related to Count Digits?

The traversal is identical:

```text
n % 10
n // 10
```

Only the accumulator changes:

```text
Count Digits:
count += 1

Sum Digits:
total += digit
```

🔥 This is exactly the kind of pattern recognition you want to develop.

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

You now have:

```text
COUNT DIGITS
    ↓
count += 1
```

and:

```text
SUM DIGITS
    ↓
sum += digit
```

Both use:

```text
digit = n % 10
n = n // 10
```

### 🔥 MASTER DIGIT TEMPLATE

```text
while n > 0:

    digit = n % 10

    PROCESS digit

    n = n // 10
```

This is one of the most important templates in Day 1.

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Writing:

```python
total += n
```

instead of:

```python
total += digit
```

❌ Forgetting:

```python
n //= 10
```

❌ Using `/` instead of `//` in Python.

❌ Forgetting negative numbers if they are allowed.

❌ Overcomplicating a problem that requires only one loop.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** Process every digit.

> ⚙️ **Approach:** Extract → Add → Remove → Repeat.

> 🐍 **Python:** `% 10`, `// 10`.

> ☕ **Java:** `% 10`, `/ 10`.

> ⏱️ **Time:** `O(d)`.

> 💾 **Space:** `O(1)`.

---

# 🔵 PROBLEM 5 — CHECK PRIME NUMBER

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Check Whether a Number Is Prime

**LeetCode:** ❌ No exact LeetCode problem that simply asks "is this number prime?"

Related LeetCode problems use prime-number logic, but assigning one as an exact match would be misleading.

**Difficulty:** 🟢 Easy

### 🔥 Why is this important?

Prime checking is a classic placement problem because it tests:

* Loops
* Conditions
* Divisibility
* Mathematical reasoning
* Complexity optimization

The beginner solution checks every number from `2` to `n - 1`.

That's correct.

But it is **not the solution I want you to use in an interview**.

We can optimize it to:

```text
2 → √n
```

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Definition

A prime number is a positive integer greater than 1 that has exactly two factors:

```text
1 and itself
```

Examples:

```text
2  → Prime
3  → Prime
5  → Prime
7  → Prime
11 → Prime
```

Non-prime:

```text
1  → Not prime
4  → Not prime
6  → Not prime
9  → Not prime
15 → Not prime
```

### 📥 Example

```text
Input: 29
Output: Prime
```

---

# 💡 BLOCK 3 — LOGIC / INTUITION

Suppose:

```text
n = 36
```

We need to know whether some number other than `1` and `36` divides it.

Try:

```text
2 → divides 36
```

Therefore:

```text
36 is NOT prime
```

Now:

```text
n = 29
```

Check:

```text
2 → no
3 → no
4 → no
5 → no
```

We don't need to check beyond `√29`.

Why?

Because if:

```text
n = a × b
```

then at least one of `a` or `b` must be less than or equal to `√n`.

### 🔥 Example

For `36`:

```text
36 = 6 × 6
```

and:

```text
√36 = 6
```

For `35`:

```text
35 = 5 × 7
```

One factor is `5`, which is less than `√35`.

So if no divisor exists up to `√n`, no larger paired divisor can suddenly make the number composite.

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → If n <= 1, return False
STEP 2 → If n == 2, return True
STEP 3 → Check divisors from 2 through √n
STEP 4 → If n % i == 0, return False
STEP 5 → If no divisor is found, return True
```

### 🔥 Practical optimization

We can also handle even numbers early:

```text
if n % 2 == 0:
    return n == 2
```

Then check only odd divisors.

This reduces unnecessary checks.

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def is_prime(n):
    if n <= 1:
        return False

    if n == 2:
        return True

    if n % 2 == 0:
        return False

    divisor = 3

    while divisor * divisor <= n:
        if n % divisor == 0:
            return False

        divisor += 2

    return True


# Main program
num = int(input("Enter a number: "))

if is_prime(num):
    print("Prime")
else:
    print("Not Prime")
```

### 🔥 Why `divisor * divisor <= n`?

We avoid calling `sqrt()` and floating-point calculations.

Instead of:

```python
while divisor <= sqrt(n):
```

we use:

```python
while divisor * divisor <= n:
```

This is exact integer arithmetic.

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static boolean isPrime(int n) {

        if (n <= 1) {
            return false;
        }

        if (n == 2) {
            return true;
        }

        if (n % 2 == 0) {
            return false;
        }

        int divisor = 3;

        while (divisor * divisor <= n) {

            if (n % divisor == 0) {
                return false;
            }

            divisor += 2;
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter a number: ");
        int num = scanner.nextInt();

        if (isPrime(num)) {
            System.out.println("Prime");
        } else {
            System.out.println("Not Prime");
        }

        scanner.close();
    }
}
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
29
```

Initial:

```text
n = 29
```

Check:

```text
29 <= 1 → False
29 == 2 → False
29 % 2 → 1
```

So:

```text
divisor = 3
```

### Iteration 1

Check:

```text
3 × 3 <= 29
9 <= 29 → True
```

Then:

```text
29 % 3 = 2
```

Not divisible.

Increment:

```text
divisor = 5
```

### Iteration 2

```text
5 × 5 <= 29
25 <= 29 → True
```

Check:

```text
29 % 5 = 4
```

Not divisible.

Increment:

```text
divisor = 7
```

### Iteration 3

```text
7 × 7 <= 29
49 <= 29 → False
```

Loop stops.

No divisor found.

Therefore:

```text
29 → Prime
```

---

### 📊 Complete dry-run table

| Step | Divisor | `divisor²` | `29 % divisor` | Result   |
| ---- | ------: | ---------: | -------------: | -------- |
| 1    |       3 |          9 |              2 | Continue |
| 2    |       5 |         25 |              4 | Continue |
| 3    |       7 |         49 |              — | Stop     |

### ✅ Output

```text
Prime
```

---

# 🔬 NEGATIVE EXAMPLE — `91`

```text
91 % 2 → 1
91 % 3 → 1
91 % 5 → 1
91 % 7 → 0
```

Therefore:

```text
91 = 7 × 13
```

So:

```text
91 → Not Prime
```

And we stop **immediately** when the divisor is found.

🔥 That's an important optimization.

---

# ☕ BLOCK 8 — JAVA DRY RUN

For:

```text
29
```

Java performs the same mathematical operations:

```text
29 % 2 = 1

3 × 3 <= 29 → true
29 % 3 = 2

5 × 5 <= 29 → true
29 % 5 = 4

7 × 7 <= 29 → false
```

Return:

```text
true
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

### ⏱️ Time Complexity

```text
O(√n)
```

More precisely, because we skip even divisors:

```text
O(√n)
```

Big-O remains the same.

### 💾 Auxiliary Space

```text
O(1)
```

Only a few integer variables are used.

---

# 🧠 Why is this better than `O(n)`?

Naive approach:

```text
2 → 3 → 4 → ... → n-1
```

Complexity:

```text
O(n)
```

Optimized:

```text
2 → √n
```

Complexity:

```text
O(√n)
```

For a large number, that's a major reduction.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. Why do we only check up to √n?

Suppose:

```text
n = a × b
```

If both `a` and `b` were greater than `√n`, then:

```text
a × b > n
```

which is impossible.

Therefore, every composite number must have at least one factor `<= √n`.

🔥 This is the key mathematical justification.

---

### 🎤 Q2. Why do we skip even numbers?

After checking `2`, every other even number is automatically composite.

So instead of:

```text
2, 3, 4, 5, 6, 7...
```

we check:

```text
3, 5, 7, 9, 11...
```

This reduces the number of iterations approximately by half.

---

### 🎤 Q3. Why is 1 not prime?

A prime number must have exactly **two distinct positive divisors**:

```text
1 and itself
```

Number `1` has only:

```text
1
```

So:

```text
1 → Not Prime
```

---

### 🎤 Q4. What is the complexity of checking all numbers up to `n - 1`?

```text
O(n)
```

The optimized approach:

```text
O(√n)
```

Therefore, the square-root approach is the practical choice.

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

### 🔥 PRIME RECOGNITION

When you see:

> "Check whether a number has any divisor"

think:

```text
n <= 1 → false
      ↓
check 2
      ↓
check divisors ≤ √n
      ↓
divisible?
   ↙       ↘
 YES       NO
  ↓         ↓
false      prime
```

### 🧠 Interview trigger

```text
"Prime?"
     ↓
"Divisor?"
     ↓
"Only need √n"
```

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Treating `1` as prime.

❌ Checking all the way to `n`.

❌ Forgetting `2`.

❌ Writing:

```python
while divisor < n:
```

instead of checking only up to the square root.

❌ Continuing after finding a divisor.

Once:

```python
n % divisor == 0
```

is true:

> 🚨 You already know the answer.

Return immediately.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** Need to determine whether a number has a divisor.

> ⚙️ **Approach:** Check divisors only up to √n.

> 🐍 **Python:** `divisor * divisor <= n`.

> ☕ **Java:** Same integer arithmetic.

> ⏱️ **Time:** `O(√n)`.

> 💾 **Space:** `O(1)`.

---

# 🔴 PROBLEM 6 — GCD OF TWO NUMBERS

## 🧠 BLOCK 1 — SENIOR INSIGHTS

### 🎯 Problem Identification

**Problem:** Find GCD of Two Numbers

**LeetCode:** ❌ No exact standalone canonical LeetCode problem matching the basic placement statement.

LeetCode contains several problems involving greatest common divisors, but the fundamental standalone problem is better treated as a mathematical algorithm.

**Difficulty:** 🟢 Easy

### 🔥 Senior choice

There are two obvious approaches.

### Approach 1 — Brute force

Check every number from:

```text
1 → min(a, b)
```

and keep the largest common divisor.

Complexity:

```text
O(min(a, b))
```

### Approach 2 — Euclidean Algorithm ⭐

Use:

```text
GCD(a, b) = GCD(b, a % b)
```

until:

```text
b = 0
```

Then:

```text
GCD = a
```

Complexity:

```text
O(log(min(a, b)))
```

🔥 **This is the solution you should know for interviews.**

---

# 📖 BLOCK 2 — PROBLEM UNDERSTANDING

### 📌 Definition

The **Greatest Common Divisor (GCD)** of two numbers is the largest positive integer that divides both numbers without leaving a remainder.

Example:

```text
12 → factors: 1, 2, 3, 4, 6, 12
18 → factors: 1, 2, 3, 6, 9, 18
```

Common factors:

```text
1, 2, 3, 6
```

Largest:

```text
6
```

Therefore:

```text
GCD(12, 18) = 6
```

---

# 💡 BLOCK 3 — LOGIC / INTUITION

This is where we use the **Euclidean Algorithm**.

Suppose:

```text
a = 48
b = 18
```

Calculate:

```text
48 % 18 = 12
```

Therefore:

```text
GCD(48,18)
=
GCD(18,12)
```

Again:

```text
18 % 12 = 6
```

Therefore:

```text
GCD(18,12)
=
GCD(12,6)
```

Again:

```text
12 % 6 = 0
```

Therefore:

```text
GCD(12,6)
=
6
```

Final answer:

```text
GCD(48,18) = 6
```

---

# 🔥 THE KEY FORMULA

```text
GCD(a, b) = GCD(b, a % b)
```

Keep applying it until:

```text
b == 0
```

Then:

```text
a = GCD
```

---

# ⚙️ BLOCK 4 — ALGORITHM — STEP BY STEP

```text
STEP 1 → Take a and b
STEP 2 → Make them positive if required
STEP 3 → While b != 0
STEP 4 → Calculate remainder = a % b
STEP 5 → Move b into a
STEP 6 → Move remainder into b
STEP 7 → When b becomes 0, a is the GCD
STEP 8 → Return a
```

### 🔥 Compact form

```python
while b != 0:
    a, b = b, a % b
```

This one line contains the entire Euclidean Algorithm.

---

# 🐍 BLOCK 5 — OPTIMAL PYTHON SOLUTION

```python
def gcd(a, b):
    a = abs(a)
    b = abs(b)

    while b != 0:
        a, b = b, a % b

    return a


# Main program
num1 = int(input("Enter first number: "))
num2 = int(input("Enter second number: "))

result = gcd(num1, num2)

print("GCD:", result)
```

### 🔥 Why this is optimal

We don't search through all possible divisors.

Instead, every iteration reduces the problem dramatically.

That is why Euclid's algorithm runs in logarithmic time.

---

# ☕ BLOCK 6 — OPTIMAL JAVA SOLUTION

```java
import java.util.Scanner;

public class Main {

    public static int gcd(int a, int b) {

        a = Math.abs(a);
        b = Math.abs(b);

        while (b != 0) {

            int remainder = a % b;

            a = b;
            b = remainder;
        }

        return a;
    }

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter first number: ");
        int num1 = scanner.nextInt();

        System.out.print("Enter second number: ");
        int num2 = scanner.nextInt();

        int result = gcd(num1, num2);

        System.out.println("GCD: " + result);

        scanner.close();
    }
}
```

---

# 🔬 BLOCK 7 — PYTHON DRY RUN

### Input

```text
a = 48
b = 18
```

Initial:

```text
a = 48
b = 18
```

---

### 🔄 Iteration 1

Calculate:

```text
48 % 18 = 12
```

Then:

```text
a = 18
b = 12
```

State:

```text
a = 18
b = 12
```

---

### 🔄 Iteration 2

```text
18 % 12 = 6
```

Then:

```text
a = 12
b = 6
```

---

### 🔄 Iteration 3

```text
12 % 6 = 0
```

Then:

```text
a = 6
b = 0
```

Loop ends because:

```text
b == 0
```

Return:

```text
6
```

### 📊 Complete dry-run table

| Iteration | `a` | `b` | `a % b` | New `a` | New `b` |
| --------- | --: | --: | ------: | ------: | ------: |
| Initial   |  48 |  18 |       — |       — |       — |
| 1         |  48 |  18 |      12 |      18 |      12 |
| 2         |  18 |  12 |       6 |      12 |       6 |
| 3         |  12 |   6 |       0 |       6 |       0 |

### ✅ Final answer

```text
GCD = 6
```

---

# ☕ BLOCK 8 — JAVA DRY RUN

Java performs:

```text
a = 48
b = 18

remainder = 48 % 18 = 12
a = 18
b = 12

remainder = 18 % 12 = 6
a = 12
b = 6

remainder = 12 % 6 = 0
a = 6
b = 0
```

Loop terminates.

Return:

```text
6
```

---

# 📊 BLOCK 9 — COMPLEXITY ANALYSIS

Let:

```text
n = min(a, b)
```

### ⏱️ Time Complexity

```text
O(log n)
```

More precisely:

```text
O(log(min(a,b)))
```

This is the major advantage over brute force.

### 💾 Auxiliary Space

For the iterative implementation:

```text
O(1)
```

No recursion stack.

---

# 🎤 BLOCK 10 — INTERVIEW Q&A

### 🎤 Q1. Why does the Euclidean Algorithm work?

Suppose:

```text
a = bq + r
```

Any common divisor of `a` and `b` also divides `r`.

Therefore:

```text
GCD(a,b) = GCD(b,r)
```

Since:

```text
r = a % b
```

we get:

```text
GCD(a,b) = GCD(b,a%b)
```

That's the mathematical foundation.

---

### 🎤 Q2. Why is Euclidean Algorithm better than checking every number?

Brute force:

```text
O(min(a,b))
```

Euclidean Algorithm:

```text
O(log(min(a,b)))
```

The Euclidean Algorithm dramatically reduces the size of the problem after every iteration.

---

### 🎤 Q3. What happens when one number is zero?

For:

```text
GCD(12, 0)
```

the answer is:

```text
12
```

because every number divides zero, and the greatest common divisor is the non-zero number.

Our loop naturally handles this:

```text
b = 0
```

so it immediately returns `a`.

---

### 🎤 Q4. Can GCD be implemented recursively?

Yes:

```python
def gcd(a, b):
    if b == 0:
        return abs(a)

    return gcd(b, a % b)
```

Time:

```text
O(log(min(a,b)))
```

Auxiliary stack space:

```text
O(log(min(a,b)))
```

The iterative version is therefore preferable when we specifically want constant auxiliary space.

---

# 🧩 BLOCK 11 — PATTERN EXTRACTION

### 🔥 EUCLIDEAN ALGORITHM

Whenever you see:

> "Find GCD"

immediately think:

```text
GCD(a,b)
   ↓
GCD(b,a%b)
   ↓
repeat
   ↓
b == 0
   ↓
a = answer
```

### 🧠 Interview trigger

```text
GCD?
 ↓
Euclidean Algorithm
 ↓
Modulo
 ↓
O(log min(a,b))
```

---

# ⚠️ BLOCK 12 — COMMON MISTAKES

❌ Checking all numbers up to `a`.

❌ Forgetting the `b == 0` stopping condition.

❌ Reversing the assignment incorrectly.

Correct:

```python
a, b = b, a % b
```

❌ Using floating-point division.

❌ Forgetting negative inputs if the problem allows them.

---

# 🚀 BLOCK 13 — INTERVIEW-READY SUMMARY

> 🧠 **Recognition:** "I need the greatest common divisor."

> ⚙️ **Approach:** Euclidean Algorithm.

> 🐍 **Python:** `a, b = b, a % b`.

> ☕ **Java:** remainder + variable update.

> ⏱️ **Time:** `O(log(min(a,b)))`.

> 💾 **Space:** `O(1)` iterative.

---

# 🏆 DAY 1 — SESSION 2 COMPLETE

## ✅ 6 / 10 PROBLEMS COMPLETED

### 1️⃣ Reverse Number

🔥 Extract → Append → Remove

### 2️⃣ Palindrome Number

🔥 Original == Reverse

### 3️⃣ Count Digits

🔥 Repeated `// 10`

### 4️⃣ Sum of Digits

🔥 Extract → Add → Remove

### 5️⃣ Prime Number

🔥 Check divisors only up to `√n`

### 6️⃣ GCD

🔥 Euclidean Algorithm

---

# 🧠 DAY 1 — CURRENT MASTER MAP

```text
             🔥 DAY 1
                 │
       NUMBER & DIGIT LOGIC
                 │
       ┌─────────┴─────────┐
       ↓                   ↓
   DIGIT LOGIC         MATH LOGIC
       │                   │
   Reverse              Prime
       │                   │
   Palindrome             GCD
       │
   Count Digits
       │
   Sum Digits
```

---

# 🚨 INDEPENDENT PRACTICE BEFORE SESSION 3

Do these **without looking at the solutions**:

### 🔥 Challenge 1

Find the sum of digits:

```text
98765
```

### 🔥 Challenge 2

Determine whether:

```text
97
```

is prime.

### 🔥 Challenge 3

Find:

```text
GCD(84, 126)
```

### 🔥 Challenge 4 — Combined

Write a program that:

```text
1. Takes a number
2. Counts its digits
3. Calculates its digit sum
4. Prints both results
```

### 🔥 Challenge 5 — Recognition

Without coding, answer:

> **What pattern would you immediately use if an interviewer asks you to process every individual digit of an integer?**

Expected mental trigger:

```text
% 10 → extract
// 10 → remove
```

---

# 📘 NEXT

## DAY 1 — SESSION 3

### Problems 7–10

**7️⃣ LCM of Two Numbers**
**8️⃣ Armstrong Number**
**9️⃣ Perfect Number**
**🔟 Harshad Number**

This will complete **Day 1's number-property foundation**.

Would you like to continue with Day 1, Session 3, or review the solutions to the Session 2 practice challenges first?
# 🔥 DAY 1 — SESSION 3

## Problems 7–10: LCM → Armstrong → Perfect Number → Harshad Number

We are continuing with the **exact locked depth**. No reduction.

### 🎯 Session 3 Objective

By the end of this session, you must be able to recognize and independently code:

| #  | Problem                 | Core Pattern             | LC                    |
| -- | ----------------------- | ------------------------ | --------------------- |
| 7  | Find LCM of Two Numbers | GCD → LCM                | No exact canonical LC |
| 8  | Armstrong Number        | Digit extraction + power | No exact LC           |
| 9  | Perfect Number          | Proper divisors + sum    | LC 507                |
| 10 | Harshad Number          | Digit sum + divisibility | No exact LC           |

### 🧠 DAY 1 COMPLETE AFTER THIS

You will have covered:

**Number → Digits → Divisibility → GCD/LCM → Special Numbers**

These are not "advanced DSA" problems. They are **coding-round fluency problems**. The objective is to make the underlying operations automatic.

---

# 🔹 PROBLEM 7 — FIND LCM OF TWO NUMBERS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### What is LCM?

**LCM = Least Common Multiple**

The LCM of two numbers is the **smallest positive number that is divisible by both numbers**.

Example:

```text
12 → 12, 24, 36, 48, 60...
18 → 18, 36, 54, 72...

First common multiple = 36

LCM(12,18) = 36
```

### 🚨 Senior insight

A beginner may do:

```text
i = max(a,b)

while True:
    if i % a == 0 and i % b == 0:
        return i
    i += 1
```

It works.

But it is **not the best general solution**.

The industry-standard mathematical relationship is:

```text
LCM(a,b) = |a × b| / GCD(a,b)
```

So if we know GCD, LCM becomes extremely easy.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Input

Two integers:

```text
a = 12
b = 18
```

### Output

```text
36
```

Because:

```text
36 % 12 = 0
36 % 18 = 0
```

and no smaller positive number satisfies both.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Suppose:

```text
a = 12
b = 18
```

Their GCD is:

```text
GCD(12,18) = 6
```

The relationship is:

```text
a × b = GCD × LCM
```

Therefore:

```text
LCM = (a × b) / GCD
```

So:

```text
LCM = (12 × 18) / 6
     = 216 / 6
     = 36
```

### 🧠 Memory trick

Whenever you see:

> "Find LCM of two numbers"

Immediately think:

```text
LCM → GCD
```

Then:

```text
LCM = abs(a*b) // gcd
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Algorithm

1. Read `a` and `b`.
2. Find their GCD using Euclidean Algorithm.
3. Multiply `a × b`.
4. Divide by GCD.
5. Return the result.

### Example

```text
a = 48
b = 18
```

Find GCD:

```text
48 % 18 = 12
18 % 12 = 6
12 % 6 = 0

GCD = 6
```

Now:

```text
LCM = (48 × 18) / 6
    = 864 / 6
    = 144
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def gcd(a, b):
    while b != 0:
        a, b = b, a % b

    return a


def lcm(a, b):
    if a == 0 or b == 0:
        return 0

    return abs(a * b) // gcd(abs(a), abs(b))


a = int(input("Enter first number: "))
b = int(input("Enter second number: "))

print("LCM =", lcm(a, b))
```

### Example

```text
Enter first number: 12
Enter second number: 18

LCM = 36
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static int gcd(int a, int b) {
        while (b != 0) {
            int temp = a % b;
            a = b;
            b = temp;
        }

        return a;
    }

    static int lcm(int a, int b) {

        if (a == 0 || b == 0) {
            return 0;
        }

        return Math.abs(a * b) / gcd(Math.abs(a), Math.abs(b));
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int a = sc.nextInt();
        int b = sc.nextInt();

        System.out.println("LCM = " + lcm(a, b));

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
a = 12
b = 18
```

### Step 1 — GCD

Initial:

```text
a = 12
b = 18
```

Execute:

```python
a, b = b, a % b
```

Calculate:

```text
12 % 18 = 12
```

Therefore:

```text
a = 18
b = 12
```

Again:

```text
18 % 12 = 6
```

Now:

```text
a = 12
b = 6
```

Again:

```text
12 % 6 = 0
```

Now:

```text
a = 6
b = 0
```

Loop ends.

```text
GCD = 6
```

### Step 2 — LCM

```text
LCM = (12 × 18) // 6
```

```text
LCM = 216 // 6
```

```text
LCM = 36
```

### Final

```text
36
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows exactly the same mathematical process:

```text
12,18
 ↓
18,12
 ↓
12,6
 ↓
6,0
```

Therefore:

```text
GCD = 6
```

Then:

```text
LCM = 12 × 18 / 6
    = 36
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Euclidean GCD takes:

```text
O(log(min(a,b)))
```

LCM calculation after GCD:

```text
O(1)
```

Therefore:

### Time

```text
O(log(min(a,b)))
```

### Space

```text
O(1)
```

because the algorithm uses only a few variables.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is LCM?

LCM is the smallest positive integer divisible by both given numbers.

---

### Q2. What is the relationship between GCD and LCM?

For non-zero integers:

```text
GCD(a,b) × LCM(a,b) = |a × b|
```

Therefore:

```text
LCM = |a × b| / GCD
```

---

### Q3. Why use GCD instead of checking every multiple?

Checking multiples can require many iterations.

Euclidean GCD is logarithmic:

```text
O(log(min(a,b)))
```

so it is substantially more efficient.

---

### Q4. What happens if either number is zero?

For the usual programming definition:

```text
LCM(0,b) = 0
```

So we explicitly handle zero.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

```text
LCM problem
     ↓
Think GCD
     ↓
Euclidean Algorithm
     ↓
LCM = abs(a*b) // GCD
```

### 🔥 Recognition rule

**GCD + LCM almost always belong together.**

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Forgetting zero.

❌ Using floating-point `/` in Python.

Use:

```python
//
```

because LCM is an integer.

❌ Forgetting absolute values for negative inputs.

❌ Recalculating GCD inefficiently.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

If interviewer says:

> "Find LCM of two numbers."

Your mental response should be:

```text
LCM → GCD → Euclidean Algorithm

LCM = abs(a*b) // gcd(a,b)
```

That's the answer pattern you should memorize.

---

# 🔥 PROBLEM 8 — ARMSTRONG NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A number is called an **Armstrong number** if the sum of each digit raised to the power of the number of digits equals the original number.

For example:

```text
153
```

There are 3 digits.

Therefore:

```text
1³ + 5³ + 3³
```

```text
1 + 125 + 27
= 153
```

Therefore:

```text
153 is an Armstrong number.
```

---

## 🚨 Important distinction

For a 3-digit Armstrong number:

```text
digit³
```

But for a general Armstrong number:

```text
digit^number_of_digits
```

For example:

```text
9474
```

There are 4 digits:

```text
9⁴ + 4⁴ + 7⁴ + 4⁴
= 9474
```

So do NOT hard-code:

```python
digit ** 3
```

for a general solution.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
153
```

Determine whether:

```text
sum of digit^number_of_digits == original number
```

Output:

```text
Armstrong Number
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We need three things:

### 1️⃣ Preserve original number

Because repeatedly dividing the number destroys it.

```python
original = n
```

### 2️⃣ Count digits

```text
153 → 3 digits
```

### 3️⃣ Extract each digit

Using:

```python
digit = n % 10
```

Then remove it:

```python
n //= 10
```

For:

```text
153
```

we get:

```text
3
5
1
```

Then:

```text
3³ + 5³ + 1³
```

Finally compare with original.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Store the original number.
2. Count the number of digits.
3. Set `sum = 0`.
4. Extract the last digit using `% 10`.
5. Raise the digit to the power of digit count.
6. Add it to sum.
7. Remove the last digit using `// 10`.
8. Repeat until the number becomes zero.
9. Compare sum with original.
10. If equal → Armstrong.
11. Otherwise → not Armstrong.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_armstrong(n):
    if n < 0:
        return False

    original = n
    digits = len(str(n))
    total = 0

    while n > 0:
        digit = n % 10
        total += digit ** digits
        n //= 10

    return total == original


n = int(input("Enter a number: "))

if is_armstrong(n):
    print("Armstrong Number")
else:
    print("Not an Armstrong Number")
```

### Example

```text
Enter a number: 153
Armstrong Number
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static boolean isArmstrong(int n) {

        if (n < 0) {
            return false;
        }

        int original = n;

        int digits = String.valueOf(n).length();

        int total = 0;

        while (n > 0) {

            int digit = n % 10;

            total += (int) Math.pow(digit, digits);

            n /= 10;
        }

        return total == original;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (isArmstrong(n)) {
            System.out.println("Armstrong Number");
        } else {
            System.out.println("Not an Armstrong Number");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
153
```

Initial:

```text
original = 153
digits = 3
total = 0
n = 153
```

### Iteration 1

```python
digit = 153 % 10
```

```text
digit = 3
```

Then:

```text
total = 0 + 3³
      = 27
```

Remove digit:

```text
153 // 10 = 15
```

Now:

```text
n = 15
total = 27
```

---

### Iteration 2

```text
15 % 10 = 5
```

Therefore:

```text
total = 27 + 5³
      = 27 + 125
      = 152
```

Remove digit:

```text
15 // 10 = 1
```

---

### Iteration 3

```text
1 % 10 = 1
```

Therefore:

```text
total = 152 + 1³
      = 153
```

Remove:

```text
1 // 10 = 0
```

Loop ends.

Compare:

```text
total == original
153 == 153
```

Therefore:

```text
True
```

Output:

```text
Armstrong Number
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java does the same operations:

```text
n = 153

153 % 10 → 3
15 % 10  → 5
1 % 10   → 1
```

Calculation:

```text
3³ + 5³ + 1³
= 27 + 125 + 1
= 153
```

Comparison:

```text
153 == 153
```

Therefore Armstrong.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
d = number of digits
```

We inspect every digit once.

### Time

```text
O(d)
```

Power calculation is performed for each digit.

### Space

```text
O(1)
```

excluding the small representation used to count digits.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why store the original number?

Because:

```python
n //= 10
```

destroys the original value.

We need the original for final comparison.

---

### Q2. Why use `% 10`?

It extracts the last digit.

```text
153 % 10 = 3
```

---

### Q3. Why use `// 10`?

It removes the last digit.

```text
153 // 10 = 15
```

---

### Q4. Can you check Armstrong without converting to string?

Yes.

You can count digits mathematically:

```python
count = 0
temp = n

while temp > 0:
    count += 1
    temp //= 10
```

This avoids string conversion completely.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This problem reinforces the most important number pattern:

```text
% 10 → extract digit
// 10 → remove digit
```

Combined with:

```text
number of digits
+
power
+
accumulation
```

### Recognition

Whenever you see:

> "Perform something on every digit"

immediately think:

```text
while n > 0
    digit = n % 10
    n //= 10
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Hard-coding cube:

```python
digit ** 3
```

for all inputs.

❌ Forgetting the original number.

❌ Using `/ 10` instead of `// 10`.

❌ Forgetting to update `n`.

❌ Confusing Armstrong with palindrome.

Palindrome asks:

```text
original == reverse
```

Armstrong asks:

```text
original == sum(digit^number_of_digits)
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Memorize:

```text
Armstrong
    ↓
Count digits
    ↓
Extract digit using %10
    ↓
digit ^ number_of_digits
    ↓
Add
    ↓
Remove digit using //10
    ↓
Compare with original
```

---

# 🔥 PROBLEM 9 — PERFECT NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A **Perfect Number** is a positive integer equal to the sum of its **proper positive divisors**, excluding itself.

Example:

```text
6
```

Proper divisors:

```text
1, 2, 3
```

Sum:

```text
1 + 2 + 3 = 6
```

Therefore:

```text
6 is a Perfect Number.
```

### Exact LeetCode Match

🔥 **LeetCode 507 — Perfect Number**

Difficulty:

**Easy**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
n = 28
```

Find all proper divisors:

```text
1, 2, 4, 7, 14
```

Sum:

```text
1 + 2 + 4 + 7 + 14
= 28
```

Therefore:

```text
28 → Perfect Number
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

A naive approach checks:

```text
1, 2, 3, ..., n-1
```

That requires:

```text
O(n)
```

iterations.

But we can do much better.

### Divisor-pair insight

If:

```text
i divides n
```

then:

```text
n / i
```

is also a divisor.

Example:

```text
28
```

When:

```text
i = 2
```

we get:

```text
28 / 2 = 14
```

So we get the pair:

```text
2, 14
```

When:

```text
i = 4
```

we get:

```text
4, 7
```

Therefore we only need to search up to:

```text
sqrt(n)
```

This reduces complexity from:

```text
O(n)
```

to:

```text
O(sqrt(n))
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. If `n <= 1`, return false.
2. Start divisor sum with `1`.
3. Loop from `2` to `sqrt(n)`.
4. If `n % i == 0`:

   * add `i`
   * calculate paired divisor `n // i`
   * add the paired divisor if it is different from `i`.
5. Compare divisor sum with `n`.
6. Equal → Perfect Number.
7. Otherwise → Not Perfect.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_perfect(n):

    if n <= 1:
        return False

    divisor_sum = 1

    i = 2

    while i * i <= n:

        if n % i == 0:

            divisor_sum += i

            paired_divisor = n // i

            if paired_divisor != i:
                divisor_sum += paired_divisor

        i += 1

    return divisor_sum == n


n = int(input("Enter a number: "))

if is_perfect(n):
    print("Perfect Number")
else:
    print("Not a Perfect Number")
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static boolean isPerfect(int n) {

        if (n <= 1) {
            return false;
        }

        int divisorSum = 1;

        for (int i = 2; i * i <= n; i++) {

            if (n % i == 0) {

                divisorSum += i;

                int pairedDivisor = n / i;

                if (pairedDivisor != i) {
                    divisorSum += pairedDivisor;
                }
            }
        }

        return divisorSum == n;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (isPerfect(n)) {
            System.out.println("Perfect Number");
        } else {
            System.out.println("Not a Perfect Number");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
n = 28
```

Initial:

```text
divisor_sum = 1
i = 2
```

### Iteration 1

```text
2 × 2 <= 28
```

True.

Check:

```text
28 % 2 == 0
```

True.

Add:

```text
2
```

Paired divisor:

```text
28 // 2 = 14
```

Add:

```text
14
```

Now:

```text
divisor_sum = 1 + 2 + 14
            = 17
```

---

### Iteration 2

```text
i = 3
```

Check:

```text
28 % 3
```

Not zero.

Nothing added.

---

### Iteration 3

```text
i = 4
```

Check:

```text
28 % 4 == 0
```

True.

Paired divisor:

```text
28 // 4 = 7
```

Add:

```text
4 + 7
```

Now:

```text
divisor_sum = 17 + 4 + 7
            = 28
```

---

### Iteration 4

```text
i = 5
```

Check:

```text
5 × 5 <= 28
```

True.

But:

```text
28 % 5 != 0
```

Nothing added.

---

### Iteration 5

```text
i = 6
```

Now:

```text
6 × 6 <= 28
```

False.

Stop.

Final:

```text
divisor_sum = 28
n = 28
```

Therefore:

```text
28 == 28
```

Output:

```text
Perfect Number
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
28
```

the divisor pairs discovered are:

```text
2 → 14
4 → 7
```

Plus initial divisor:

```text
1
```

Therefore:

```text
1 + 2 + 14 + 4 + 7
= 28
```

Perfect.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We only check divisors until:

```text
sqrt(n)
```

Therefore:

### Time

```text
O(sqrt(n))
```

### Space

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why don't we loop until `n - 1`?

Because divisors occur in pairs.

If:

```text
i divides n
```

then:

```text
n/i
```

is another divisor.

Therefore checking beyond `sqrt(n)` is unnecessary.

---

### Q2. Why start divisor sum with 1?

For every perfect-number candidate greater than 1:

```text
1
```

is always a proper divisor.

So:

```python
divisor_sum = 1
```

saves an unnecessary iteration.

---

### Q3. Why check `paired_divisor != i`?

For perfect squares, the pair can be identical.

Example:

```text
36
```

At:

```text
i = 6
```

we get:

```text
36 // 6 = 6
```

We must not add `6` twice.

---

### Q4. What are examples of perfect numbers?

Common examples:

```text
6
28
496
8128
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This teaches an important optimization:

```text
Divisor problem
       ↓
Divisor pairs
       ↓
Check only up to sqrt(n)
```

### 🔥 Recognition rule

Whenever the problem asks:

> "Find/check divisors"

think:

```text
i * i <= n
```

rather than blindly:

```text
i <= n
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Including `n` itself in the proper-divisor sum.

For:

```text
6
```

do NOT include:

```text
6
```

❌ Double-counting square-root divisors.

❌ Treating `1` as a perfect number.

❌ Checking all numbers up to `n`.

❌ Forgetting that negative numbers aren't valid perfect-number candidates in this definition.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember:

```text
Perfect Number
      ↓
Proper divisors
      ↓
Divisor pairs
      ↓
Check i * i <= n
      ↓
Add i + n/i
      ↓
Compare sum with n
```

---

# 🔥 PROBLEM 10 — HARSHAD NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A **Harshad Number** is a positive integer that is divisible by the sum of its digits.

It is also commonly called a **Niven Number**.

Example:

```text
18
```

Digit sum:

```text
1 + 8 = 9
```

Check:

```text
18 % 9 = 0
```

Therefore:

```text
18 is a Harshad Number.
```

---

## 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
n = 21
```

Digit sum:

```text
2 + 1 = 3
```

Check:

```text
21 % 3 = 0
```

Therefore:

```text
21 → Harshad Number
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

This problem combines two things we already learned:

### From Problem 4:

```text
Sum of digits
```

using:

```python
digit = n % 10
n //= 10
```

### Then:

```text
original % digit_sum
```

If:

```text
remainder == 0
```

then Harshad.

### 🚨 Senior recognition

This is a **combination problem**.

You should immediately recognize:

```text
Harshad
    ↓
Digit Sum
    ↓
Divisibility
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Store the original number.
2. Calculate the digit sum.
3. Extract digits using `% 10`.
4. Remove digits using `// 10`.
5. After calculating digit sum, check:

```text
original % digit_sum == 0
```

6. If true → Harshad.
7. Otherwise → Not Harshad.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_harshad(n):

    if n <= 0:
        return False

    original = n
    digit_sum = 0

    while n > 0:

        digit = n % 10

        digit_sum += digit

        n //= 10

    return original % digit_sum == 0


n = int(input("Enter a number: "))

if is_harshad(n):
    print("Harshad Number")
else:
    print("Not a Harshad Number")
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static boolean isHarshad(int n) {

        if (n <= 0) {
            return false;
        }

        int original = n;
        int digitSum = 0;

        while (n > 0) {

            int digit = n % 10;

            digitSum += digit;

            n /= 10;
        }

        return original % digitSum == 0;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        int n = sc.nextInt();

        if (isHarshad(n)) {
            System.out.println("Harshad Number");
        } else {
            System.out.println("Not a Harshad Number");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
n = 18
```

Store:

```text
original = 18
digit_sum = 0
```

### Iteration 1

```text
18 % 10 = 8
```

Therefore:

```text
digit_sum = 0 + 8
          = 8
```

Remove digit:

```text
18 // 10 = 1
```

---

### Iteration 2

```text
1 % 10 = 1
```

Therefore:

```text
digit_sum = 8 + 1
          = 9
```

Remove:

```text
1 // 10 = 0
```

Loop ends.

Now:

```text
original = 18
digit_sum = 9
```

Check:

```text
18 % 9 == 0
```

Yes.

Therefore:

```text
Harshad Number
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same process:

```text
18
 ↓
digit = 8
sum = 8
 ↓
digit = 1
sum = 9
 ↓
18 % 9 = 0
```

Therefore:

```text
Harshad Number
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
d = number of digits
```

We process every digit once.

### Time

```text
O(d)
```

### Space

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is a Harshad Number?

A positive integer divisible by the sum of its digits.

Example:

```text
18 → digit sum 9 → 18 % 9 = 0
```

---

### Q2. Why preserve the original number?

Because we modify `n` while extracting digits.

At the end, we need:

```text
original % digit_sum
```

---

### Q3. What happens if digit sum is zero?

For positive integers, the digit sum is greater than zero.

For:

```text
0
```

the usual Harshad definition used in these coding problems excludes it, so we return false for `n <= 0`.

---

### Q4. What important pattern does this problem test?

It tests the combination:

```text
digit extraction
+
accumulation
+
divisibility
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is a direct combination of previously learned skills:

```text
Harshad
   ↓
Preserve original
   ↓
Extract digits
   ↓
Calculate digit sum
   ↓
original % digit_sum
```

### 🔥 Important

You have now seen the same digit-extraction skeleton multiple times:

```python
while n > 0:
    digit = n % 10
    # process digit
    n //= 10
```

This should become **automatic muscle memory**.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Checking:

```python
n % digit == 0
```

instead of:

```python
n % digit_sum == 0
```

❌ Losing the original number.

❌ Forgetting:

```python
n //= 10
```

❌ Using the modified `n` for the final divisibility check.

❌ Confusing Harshad with Armstrong.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Memorize:

```text
Harshad
   ↓
Digit Sum
   ↓
Original % Digit Sum
   ↓
0 → Harshad
non-zero → Not Harshad
```

---

# 🧠 DAY 1 — SESSION 3 MASTER PATTERN

Now look at Problems 7–10 together.

## Problem 7 — LCM

```text
LCM
 ↓
GCD
 ↓
LCM = |a*b| / GCD
```

## Problem 8 — Armstrong

```text
Number
 ↓
Count digits
 ↓
Extract each digit
 ↓
digit^count
 ↓
Sum
 ↓
Compare original
```

## Problem 9 — Perfect Number

```text
Number
 ↓
Find divisors
 ↓
Use divisor pairs
 ↓
sqrt(n)
 ↓
Sum proper divisors
 ↓
Compare original
```

## Problem 10 — Harshad

```text
Number
 ↓
Extract digits
 ↓
Digit sum
 ↓
original % digit_sum
```

---

# 🔥 THE MOST IMPORTANT NUMBER-CODING TEMPLATE

You have now solved enough problems to make this skeleton permanent:

```python
original = n

while n > 0:

    digit = n % 10

    # process digit here

    n //= 10
```

Different problems simply change:

```text
# process digit here
```

### Sum of digits

```python
total += digit
```

### Armstrong

```python
total += digit ** digits
```

### Count digits

```python
count += 1
```

### Harshad

```python
digit_sum += digit
```

### Reverse

```python
reverse = reverse * 10 + digit
```

🚨 **This is exactly the kind of pattern recognition you need for placement coding.**

---

# 📊 DAY 1 — SESSION 3 COMPLETION

| Problem            | Status      |
| ------------------ | ----------- |
| 7. LCM             | ✅ Completed |
| 8. Armstrong       | ✅ Completed |
| 9. Perfect Number  | ✅ Completed |
| 10. Harshad Number | ✅ Completed |

## 🏆 DAY 1 STATUS

```text
Session 1 → 3/3 ✅
Session 2 → 3/3 ✅
Session 3 → 4/4 ✅

TOTAL = 10/10
```

But remember:

**Reading ≠ mastery.**

Your actual goal is:

```text
🟢 Understood
      ↓
🟡 Reproduced
      ↓
🟠 Independent
      ↓
🔴 Mastered
```

---

# 🧪 SESSION 3 — INDEPENDENT PRACTICE

Do these **WITHOUT looking at the solutions above**.

### 🟢 Basic

**Q1.** Find LCM:

```text
a = 15
b = 20
```

Expected:

```text
60
```

---

**Q2.** Check:

```text
153
```

Is it Armstrong?

---

**Q3.** Check:

```text
28
```

Is it Perfect?

---

**Q4.** Check:

```text
24
```

Is it Harshad?

---

# 🟡 Reproduction Drill

Write all four programs from memory:

```text
1. LCM
2. Armstrong
3. Perfect Number
4. Harshad Number
```

No copy-paste.

---

# 🟠 Independent Challenge

### Challenge 1

Write one program that takes:

```text
n
```

and prints:

```text
Digit Count
Digit Sum
Reverse
Palindrome
Armstrong
Harshad
```

Example:

```text
Input:
153
```

Expected conceptually:

```text
Digits: 3
Sum: 9
Reverse: 351
Palindrome: No
Armstrong: Yes
Harshad: Yes
```

This is an important integration exercise because you must reuse the same digit-processing logic for multiple requirements.

---

# 🔴 MASTER TEST — NO SOLUTION

Tomorrow/after your practice, try these **without looking back**:

### 1.

```text
LCM(84, 126)
```

### 2.

Check whether:

```text
9474
```

is an Armstrong number.

### 3.

Check whether:

```text
496
```

is a Perfect Number.

### 4.

Check whether:

```text
1729
```

is a Harshad Number.

### 5. 🔥 Combined recognition test

Without being told the pattern, write a program that counts the digits of a number and determines whether the number is:

```text
Palindrome
Armstrong
Harshad
```

---

# 🚨 DAY 1 — FINAL SENIOR TAKEAWAY

Do **not** memorize 10 separate programs.

Memorize the **small number of primitives** behind them:

```text
% 10
↓
extract last digit

// 10
↓
remove last digit
```

Then:

```text
reverse      → reverse * 10 + digit
sum          → sum + digit
count        → count + 1
Armstrong    → sum + digit^digits
Harshad      → original % digit_sum
GCD          → a, b = b, a % b
LCM          → a*b / GCD
divisors     → i*i <= n
```

🔥 **That is the actual Day 1 skill.**

Not "I completed 10 questions."

It is:

> **"When I see a number problem, I can immediately identify which primitive operation and pattern it requires."**

**DAY 1 = 10/10 completed.**

Would you like to start with the Session 3 practice answers, or move straight to Day 2?
