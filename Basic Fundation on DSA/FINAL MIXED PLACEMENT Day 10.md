# 🔥 DAY 10

## FINAL MIXED PLACEMENT CHALLENGE

### Problems 91–100

```text 
Date Validation
Roman Numeral
Simple Calculator
Best Time to Buy/Sell Stock
Longest Common Prefix
Product Except Self
Merge Intervals
Missing + Repeating
Spiral Matrix
Rotate Matrix
```

### 🎯 Skill

**Problem recognition without category hints**



# 🔥 CR2 — DAY 10 — SESSION 1

## Problems 91–94 | FINAL MIXED PLACEMENT CHALLENGE

**LOCKED EXECUTION PRESERVED.**
**No reduction. No syllabus changes. No mixing with the deeper DSA roadmap.**

Today is the **final 10-problem placement challenge**. These problems deliberately mix the patterns you've already learned.

---

# 📌 DAY 10 — SESSION 1 SCOPE

| #      | Problem                     | Exact LeetCode Match                                      | Difficulty |
| ------ | --------------------------- | --------------------------------------------------------- | ---------- |
| **91** | Validate Date + Leap Year   | No exact canonical LC match                               | Basic      |
| **92** | Roman Numeral to Integer    | **LC 13 — Roman to Integer**                              | Easy       |
| **93** | Simple Calculator           | No exact match; LC 224 is a much harder/different problem | Basic      |
| **94** | Best Time to Buy/Sell Stock | **LC 121 — Best Time to Buy and Sell Stock**              | Easy       |

---

# 🟦 PROBLEM 91 — VALIDATE DATE + LEAP YEAR

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a **validation + conditional logic** problem.

The important thing is not memorizing a huge formula.

Break the problem into two separate questions:

```text
1. Is the date structurally valid?
2. If February is involved, is this a leap year?
```

### Months and maximum days

```text
January   → 31
February  → 28 or 29
March     → 31
April     → 30
May       → 31
June      → 30
July      → 31
August    → 31
September → 30
October   → 31
November  → 30
December  → 31
```

### 🔥 Leap-year rule

A year is a leap year if:

```text
year divisible by 400
OR
year divisible by 4 AND NOT divisible by 100
```

Examples:

```text
2000 → leap year
1900 → NOT leap year
2024 → leap year
2023 → NOT leap year
```

### Senior mindset

Don't write:

```text
"if year % 4 == 0, leap year"
```

That fails for:

```text
1900
```

The century rule matters.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
day
month
year
```

determine whether the date is valid.

### Examples

```text
Input:
29 2 2024

Output:
True
```

Because 2024 is a leap year.

---

```text
Input:
29 2 2023

Output:
False
```

Because February 2023 has only 28 days.

---

```text
Input:
31 4 2025

Output:
False
```

April has only 30 days.

---

```text
Input:
31 12 2025

Output:
True
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We need three levels of validation.

### Level 1 — Basic ranges

```text
month must be 1–12
day must be >= 1
year must be valid positive year
```

### Level 2 — Determine maximum days

For:

```text
April
June
September
November
```

maximum:

```text
30
```

For:

```text
January
March
May
July
August
October
December
```

maximum:

```text
31
```

February:

```text
28 or 29
```

### Level 3 — Compare

```text
1 <= day <= days_in_month
```

That's the entire validation strategy.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Check that `month` is between `1` and `12`.
2. Check that `day >= 1`.
3. Determine whether `year` is a leap year.
4. Set February's maximum to:

   ```text
   29 if leap year else 28
   ```
5. Store maximum days for every month.
6. Get the maximum allowed day for the given month.
7. Check:

   ```text
   day <= max_days
   ```
8. Return `True` if valid; otherwise `False`.

### Pseudocode

```text
is_leap_year(year):

    if year % 400 == 0:
        return True

    if year % 100 == 0:
        return False

    return year % 4 == 0
```

Then:

```text
validate_date(day, month, year):

    if month < 1 or month > 12:
        return False

    if day < 1:
        return False

    determine maximum days

    return day <= maximum_days
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_leap_year(year):
    return year % 400 == 0 or (
        year % 4 == 0 and year % 100 != 0
    )


def is_valid_date(day, month, year):

    # Month must be between 1 and 12
    if month < 1 or month > 12:
        return False

    # Day must be positive
    if day < 1:
        return False

    # Days in each month
    days_in_month = [
        31,
        28,
        31,
        30,
        31,
        30,
        31,
        31,
        30,
        31,
        30,
        31
    ]

    # February has 29 days in a leap year
    if is_leap_year(year):
        days_in_month[1] = 29

    return day <= days_in_month[month - 1]


# Tests
print(is_valid_date(29, 2, 2024))
print(is_valid_date(29, 2, 2023))
print(is_valid_date(31, 4, 2025))
print(is_valid_date(31, 12, 2025))
print(is_valid_date(31, 13, 2025))
```

### Output

```text
True
False
False
True
False
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static boolean isLeapYear(int year) {

        return year % 400 == 0 ||
               (year % 4 == 0 && year % 100 != 0);
    }

    static boolean isValidDate(int day, int month, int year) {

        // Month validation
        if (month < 1 || month > 12) {
            return false;
        }

        // Day validation
        if (day < 1) {
            return false;
        }

        int[] daysInMonth = {
            31, 28, 31, 30,
            31, 30, 31, 31,
            30, 31, 30, 31
        };

        // February gets 29 days during leap year
        if (isLeapYear(year)) {
            daysInMonth[1] = 29;
        }

        return day <= daysInMonth[month - 1];
    }

    public static void main(String[] args) {

        System.out.println(isValidDate(29, 2, 2024));
        System.out.println(isValidDate(29, 2, 2023));
        System.out.println(isValidDate(31, 4, 2025));
        System.out.println(isValidDate(31, 12, 2025));
        System.out.println(isValidDate(31, 13, 2025));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
day = 29
month = 2
year = 2024
```

### Step 1

```text
month = 2
```

Valid because:

```text
1 <= 2 <= 12
```

---

### Step 2

```text
day = 29
```

Valid because:

```text
29 >= 1
```

---

### Step 3 — Leap year

```text
2024 % 400 != 0
2024 % 100 != 0
2024 % 4 == 0
```

Therefore:

```text
2024 → leap year
```

February:

```text
29 days
```

---

### Step 4

```text
day = 29
max_days = 29
```

Check:

```text
29 <= 29
```

Therefore:

```text
True
```

---

### Counterexample

```text
29 / 2 / 2023
```

2023 is not a leap year.

Maximum February days:

```text
28
```

Check:

```text
29 <= 28
```

False.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Take:

```text
31 / 4 / 2025
```

April:

```text
month = 4
```

Lookup:

```text
daysInMonth[3] = 30
```

Check:

```text
31 <= 30
```

False.

Therefore:

```text
Invalid date
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

The month list contains exactly 12 elements.

We perform a constant number of checks.

Therefore:

### Time

```text
O(1)
```

### Space

```text
O(1)
```

The array has fixed size 12.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Is every year divisible by 4 a leap year?

No.

Example:

```text
1900
```

is divisible by 4 but not a leap year because it is divisible by 100 and not 400.

---

### Q2. Why is 2000 a leap year?

```text
2000 % 400 == 0
```

Therefore it is a leap year.

---

### Q3. Why do we use `month - 1`?

Programming arrays are zero-indexed:

```text
January → index 0
February → index 1
...
December → index 11
```

---

### Q4. What pattern is this?

```text
Validation + conditional rules + lookup table
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

When a problem says:

> "Validate X according to several rules."

Think:

```text
1. Validate basic range
2. Identify special cases
3. Apply rule
4. Return boolean
```

For dates:

```text
month → lookup maximum days
February → leap-year exception
day → compare
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

```python
year % 4 == 0
```

alone.

Fails for century years.

### ❌ Mistake 2

Allowing:

```text
32 January
31 April
30 February
```

### ❌ Mistake 3

Using:

```python
days_in_month[month]
```

instead of:

```python
days_in_month[month - 1]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Leap-year formula

```python
year % 400 == 0 or (
    year % 4 == 0 and year % 100 != 0
)
```

### Date validation

```text
Valid month
+
Positive day
+
Day <= maximum days in month
```

### Complexity

```text
Time  → O(1)
Space → O(1)
```

### Exact LeetCode Match

**No exact canonical LeetCode match.**

---

# 🟦 PROBLEM 92 — ROMAN NUMERAL TO INTEGER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 13 — Roman to Integer — Easy** ✅

Roman symbols:

```text
I → 1
V → 5
X → 10
L → 50
C → 100
D → 500
M → 1000
```

Most Roman numerals work by addition:

```text
VIII = 5 + 1 + 1 + 1 = 8
```

But there are subtraction cases:

```text
IV = 4
IX = 9
XL = 40
XC = 90
CD = 400
CM = 900
```

### 🔥 Core pattern

Look at the current value and the **next value**.

If:

```text
current < next
```

then subtract current.

Otherwise:

```text
add current
```

This is a very important **look-ahead pattern**.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Convert a valid Roman numeral string into an integer.

Examples:

```text
III → 3
IV → 4
IX → 9
LVIII → 58
MCMXCIV → 1994
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Consider:

```text
MCM
```

Values:

```text
M = 1000
C = 100
M = 1000
```

At `M`:

```text
1000 > 100
```

Add:

```text
+1000
```

At `C`:

```text
100 < 1000
```

So subtract:

```text
-100
```

At final `M`:

```text
+1000
```

Total:

```text
1000 - 100 + 1000
= 1900
```

### 🔥 Recognition

Whenever:

> current value is smaller than next value

think:

```text
SUBTRACT
```

Otherwise:

```text
ADD
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Create a dictionary mapping Roman symbols to values.
2. Initialize `total = 0`.
3. Traverse the string.
4. For each character:

   * get current value.
   * if a next character exists and:

     ```text
     current < next
     ```

     subtract current.
   * otherwise add current.
5. Return total.

### Pseudocode

```text
total = 0

for i from 0 to n-1:

    current = value(s[i])

    if i+1 exists AND current < value(s[i+1]):
        total -= current
    else:
        total += current

return total
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def roman_to_integer(s):

    values = {
        'I': 1,
        'V': 5,
        'X': 10,
        'L': 50,
        'C': 100,
        'D': 500,
        'M': 1000
    }

    total = 0

    for i in range(len(s)):

        current = values[s[i]]

        # If current is smaller than next,
        # subtract it.
        if i + 1 < len(s) and current < values[s[i + 1]]:
            total -= current
        else:
            total += current

    return total


# Tests
print(roman_to_integer("III"))
print(roman_to_integer("IV"))
print(roman_to_integer("LVIII"))
print(roman_to_integer("MCMXCIV"))
```

### Output

```text
3
4
58
1994
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;

public class Main {

    static int romanToInteger(String s) {

        Map<Character, Integer> values = new HashMap<>();

        values.put('I', 1);
        values.put('V', 5);
        values.put('X', 10);
        values.put('L', 50);
        values.put('C', 100);
        values.put('D', 500);
        values.put('M', 1000);

        int total = 0;

        for (int i = 0; i < s.length(); i++) {

            int current = values.get(s.charAt(i));

            if (i + 1 < s.length()
                    && current < values.get(s.charAt(i + 1))) {

                total -= current;

            } else {

                total += current;
            }
        }

        return total;
    }

    public static void main(String[] args) {

        System.out.println(romanToInteger("III"));
        System.out.println(romanToInteger("IV"));
        System.out.println(romanToInteger("LVIII"));
        System.out.println(romanToInteger("MCMXCIV"));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
MCMXCIV
```

Values:

```text
M = 1000
C = 100
M = 1000
X = 10
C = 100
I = 1
V = 5
```

| Current | Next | Comparison | Action |    Total |
| ------- | ---: | ---------- | ------ | -------: |
| M       |    C | 1000 > 100 | +1000  |     1000 |
| C       |    M | 100 < 1000 | -100   |      900 |
| M       |    X | 1000 > 10  | +1000  |     1900 |
| X       |    C | 10 < 100   | -10    |     1890 |
| C       |    I | 100 > 1    | +100   |     1990 |
| I       |    V | 1 < 5      | -1     |     1989 |
| V       |    — | last       | +5     | **1994** |

Final answer:

```text
1994
```

### 🔥 This table is the pattern.

You don't need separate special cases for:

```text
IV
IX
XL
XC
CD
CM
```

The comparison automatically handles them.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
IX
```

### `I`

```text
current = 1
next = 10
```

Since:

```text
1 < 10
```

subtract:

```text
total = -1
```

### `X`

Last element:

```text
total = -1 + 10
      = 9
```

Answer:

```text
9
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of Roman numeral
```

We visit every character once.

HashMap lookup is expected `O(1)`.

Therefore:

### Time

```text
O(n)
```

### Space

The Roman mapping has exactly 7 symbols:

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we subtract `I` in `IV`?

Because:

```text
I < V
```

So the current value is smaller than the next value.

---

### Q2. Why not hardcode `IV`, `IX`, etc.?

You can, but the comparison-based approach is cleaner and generalizes the subtraction rule.

---

### Q3. What is the core pattern?

```text
current < next → subtract
otherwise → add
```

---

### Q4. Complexity?

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Look-ahead pattern

```python
if current < next:
    subtract
else:
    add
```

This is a reusable technique:

```text
Current element's action
depends on next element
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Always adding values.

Fails:

```text
IV
IX
XL
...
```

### ❌ Mistake 2

Forgetting the final character.

### ❌ Mistake 3

Accessing:

```python
s[i + 1]
```

without checking whether `i` is the last index.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
current < next
     ↓
subtract

current >= next
     ↓
add
```

### Exact LeetCode

**LC 13 — Roman to Integer — Easy** ✅

### Complexity

```text
Time  → O(n)
Space → O(1)
```

---

# 🟦 PROBLEM 93 — SIMPLE CALCULATOR

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### ⚠️ Exact LeetCode distinction

This CR2 problem is a **basic placement calculator**.

It is **NOT** the same problem as:

**LC 224 — Basic Calculator — Hard**

LC 224 involves parentheses and significantly more parsing logic.

For CR2, we deliberately keep:

```text
number operator number
```

with basic operators.

Example:

```text
10 + 5
```

```text
20 - 7
```

```text
6 * 4
```

```text
20 / 5
```

### Senior mindset

The core skill here is:

```text
input
→ parse
→ identify operator
→ perform operation
→ return result
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two numbers and an operator:

```text
a
operator
b
```

perform:

```text
+
-
*
/
```

Example:

```text
10 + 5 → 15
10 - 5 → 5
10 * 5 → 50
10 / 5 → 2
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We have exactly four cases:

```text
operator == '+'
operator == '-'
operator == '*'
operator == '/'
```

So:

```text
if
elif
elif
elif
```

is completely appropriate for this beginner placement problem.

### Division by zero

Must be handled.

```text
10 / 0
```

is invalid.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Receive `a`, `b`, and `operator`.
2. Check the operator.
3. Perform corresponding operation.
4. For division, verify `b != 0`.
5. Return the result.
6. If operator is unsupported, report invalid operator.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def calculator(a, b, operator):

    if operator == '+':
        return a + b

    elif operator == '-':
        return a - b

    elif operator == '*':
        return a * b

    elif operator == '/':
        if b == 0:
            return "Error: Division by zero"
        return a / b

    else:
        return "Error: Invalid operator"


# Tests
print(calculator(10, 5, '+'))
print(calculator(10, 5, '-'))
print(calculator(10, 5, '*'))
print(calculator(10, 5, '/'))
print(calculator(10, 0, '/'))
```

### Output

```text
15
5
50
2.0
Error: Division by zero
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static double calculator(double a, double b, char operator) {

        switch (operator) {

            case '+':
                return a + b;

            case '-':
                return a - b;

            case '*':
                return a * b;

            case '/':
                if (b == 0) {
                    throw new ArithmeticException(
                        "Division by zero"
                    );
                }
                return a / b;

            default:
                throw new IllegalArgumentException(
                    "Invalid operator"
                );
        }
    }

    public static void main(String[] args) {

        System.out.println(calculator(10, 5, '+'));
        System.out.println(calculator(10, 5, '-'));
        System.out.println(calculator(10, 5, '*'));
        System.out.println(calculator(10, 5, '/'));
    }
}
```

### Output

```text
15.0
5.0
50.0
2.0
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Take:

```text
a = 20
b = 4
operator = "/"
```

### Step 1

Check:

```text
operator == '+'
```

False.

### Step 2

```text
operator == '-'
```

False.

### Step 3

```text
operator == '*'
```

False.

### Step 4

```text
operator == '/'
```

True.

Check:

```text
b == 0?
```

No.

Perform:

```text
20 / 4
```

Result:

```text
5.0
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
a = 7
b = 3
operator = '*'
```

`switch` finds:

```text
case '*'
```

Performs:

```text
7 * 3
```

Result:

```text
21
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

There are only a constant number of operator checks.

Therefore:

### Time

```text
O(1)
```

### Space

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why check division by zero?

Because division by zero is undefined.

---

### Q2. Is this LC 224?

No.

**LC 224 is a much harder calculator/parser problem involving parentheses.**

This CR2 problem is intentionally a basic placement calculator.

---

### Q3. Why use `switch` in Java?

The operation is determined by one fixed operator value, making `switch` natural.

---

### Q4. What pattern is this?

```text
Input classification
→ corresponding operation
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

When there are a small fixed number of choices:

```text
operator
status
menu choice
command
option
```

think:

```text
if/elif
```

or:

```text
switch
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Not handling division by zero.

### ❌ Mistake 2

Using `^` for exponentiation.

In Python:

```python
^
```

is XOR, **not power**.

### ❌ Mistake 3

Confusing:

```text
/
```

with integer division.

Python:

```python
10 / 4 = 2.5
```

If the placement question explicitly asks integer division, use:

```python
10 // 4 = 2
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
+ → addition
- → subtraction
* → multiplication
/ → division
```

Always handle:

```text
division by zero
invalid operator
```

### Exact LeetCode Match

**No exact match.**

**LC 224 — Basic Calculator is related but NOT an exact match and is Hard.**

### Complexity

```text
Time  → O(1)
Space → O(1)
```

---

# 🟦 PROBLEM 94 — BEST TIME TO BUY AND SELL STOCK

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 121 — Best Time to Buy and Sell Stock — Easy** ✅

This is one of the most important beginner greedy/one-pass problems.

The naive thinking is:

> "Try every buy day with every sell day."

That is:

```text
O(n²)
```

But we don't need to do that.

### 🔥 Core observation

As we scan from left to right:

```text
Current price
```

can be today's selling price.

To maximize profit, we need the **cheapest price seen before today**.

So maintain:

```text
minimum price so far
```

and:

```text
maximum profit so far
```

### Formula

```text
profit = current_price - minimum_price
```

Then update the maximum.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
prices[i]
```

where `prices[i]` is the stock price on day `i`.

You must:

```text
buy once
sell once
buy before selling
```

and maximize profit.

### Example

```text
[7, 1, 5, 3, 6, 4]
```

Best choice:

```text
Buy at 1
Sell at 6
```

Profit:

```text
6 - 1 = 5
```

Answer:

```text
5
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Scan the array.

```text
7
```

Minimum so far:

```text
7
```

Profit:

```text
0
```

Next:

```text
1
```

New minimum:

```text
1
```

Next:

```text
5
```

Potential profit:

```text
5 - 1 = 4
```

Next:

```text
3
```

Profit:

```text
3 - 1 = 2
```

Next:

```text
6
```

Profit:

```text
6 - 1 = 5
```

Best so far:

```text
5
```

Next:

```text
4
```

Profit:

```text
4 - 1 = 3
```

Final:

```text
5
```

### 🔥 Pattern

This is:

```text
minimum-so-far
+
best-answer-so-far
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Initialize:

   ```text
   min_price = infinity
   max_profit = 0
   ```
2. Scan every price.
3. Update the minimum price:

   ```text
   min_price = min(min_price, price)
   ```
4. Calculate today's possible profit:

   ```text
   profit = price - min_price
   ```
5. Update:

   ```text
   max_profit
   ```
6. Return `max_profit`.

### Pseudocode

```text
min_price = infinity
max_profit = 0

for price in prices:

    min_price = minimum(min_price, price)

    profit = price - min_price

    max_profit = maximum(max_profit, profit)

return max_profit
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def max_profit(prices):

    min_price = float('inf')
    max_profit = 0

    for price in prices:

        # Cheapest price seen so far
        min_price = min(min_price, price)

        # Profit if we sell today
        profit = price - min_price

        # Best profit seen so far
        max_profit = max(max_profit, profit)

    return max_profit


# Test
prices = [7, 1, 5, 3, 6, 4]

print(max_profit(prices))
```

### Output

```text
5
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
public class Main {

    static int maxProfit(int[] prices) {

        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;

        for (int price : prices) {

            // Cheapest price seen so far
            minPrice = Math.min(minPrice, price);

            // Profit if selling today
            int profit = price - minPrice;

            // Best profit so far
            maxProfit = Math.max(maxProfit, profit);
        }

        return maxProfit;
    }

    public static void main(String[] args) {

        int[] prices = {7, 1, 5, 3, 6, 4};

        System.out.println(maxProfit(prices));
    }
}
```

### Output

```text
5
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[7, 1, 5, 3, 6, 4]
```

Initial:

```text
min_price = ∞
max_profit = 0
```

| Price | Min Price | Profit Today | Max Profit |
| ----: | --------: | -----------: | ---------: |
|     7 |         7 |            0 |          0 |
|     1 |         1 |            0 |          0 |
|     5 |         1 |            4 |          4 |
|     3 |         1 |            2 |          4 |
|     6 |         1 |            5 |          5 |
|     4 |         1 |            3 |          5 |

Final:

```text
max_profit = 5
```

### Why does this work?

When we reach price `6`, we already know:

```text
minimum previous price = 1
```

Therefore the best legal transaction ending today is:

```text
6 - 1 = 5
```

We never need to check every previous day individually.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
[7, 6, 4, 3, 1]
```

Track:

```text
7 → min = 7 → profit = 0
6 → min = 6 → profit = 0
4 → min = 4 → profit = 0
3 → min = 3 → profit = 0
1 → min = 1 → profit = 0
```

Final:

```text
0
```

### Why not negative?

The problem allows us to make **no transaction**, so maximum profit remains:

```text
0
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of prices
```

We scan the array once.

Therefore:

### Time

```text
O(n)
```

### Space

Only two variables:

```text
min_price
max_profit
```

Therefore:

```text
O(1)
```

### Why this beats brute force

Brute force:

```text
every buy day × every sell day
```

≈

```text
O(n²)
```

One-pass solution:

```text
O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we track minimum price?

Because for any selling day, the best possible buying price is the smallest price seen before that day.

---

### Q2. Why can't we simply calculate `max(prices) - min(prices)`?

Because the minimum may occur **after** the maximum.

Example:

```text
[7, 6, 4, 3, 1]
```

`max - min = 6`, but you cannot buy at `1` and sell at `7` because buying must happen first.

---

### Q3. What pattern is this?

```text
Minimum-so-far
+
best-answer-so-far
```

---

### Q4. Can we make multiple transactions?

Not in LC 121.

The problem allows:

```text
one buy
+
one sell
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Master pattern

Whenever you see:

> "Maximum difference where the smaller element must come before the larger element"

think:

```text
minimum so far
+
current value
+
best answer
```

Template:

```python
min_value = float('inf')
best = 0

for x in arr:

    min_value = min(min_value, x)

    candidate = x - min_value

    best = max(best, candidate)
```

This pattern is extremely important for placement coding.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
max(prices) - min(prices)
```

without considering order.

---

### ❌ Mistake 2

Brute force:

```python
for i in range(n):
    for j in range(i + 1, n):
```

Works, but is `O(n²)`.

---

### ❌ Mistake 3

Allowing the same day for buy and sell.

We conceptually need:

```text
buy before sell
```

---

### ❌ Mistake 4

Returning negative profit.

If prices continuously decrease:

```text
[7,6,5,4,3]
```

answer is:

```text
0
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Core idea

```text
minimum price so far
        +
current price
        ↓
potential profit
        ↓
maximum profit
```

### Formula

```python
profit = price - min_price
```

### Complexity

```text
Time  → O(n)
Space → O(1)
```

### Exact LeetCode

**LC 121 — Best Time to Buy and Sell Stock — Easy** ✅

---

# 🧠 DAY 10 — SESSION 1 MASTER PATTERN MAP

You just covered four different placement patterns:

```text
91 → DATE VALIDATION
     Range checks
     + lookup table
     + leap-year rule

92 → ROMAN TO INTEGER
     Current vs next
     ↓
     smaller → subtract
     otherwise → add

93 → SIMPLE CALCULATOR
     Fixed operation selection
     ↓
     if/elif or switch

94 → STOCK PROFIT
     Minimum-so-far
     +
     Best-answer-so-far
```

---

# 🔥 FOUR PATTERNS TO MEMORIZE

```text
DATE
→ validation + special case

ROMAN
→ current < next ? subtract : add

CALCULATOR
→ operator → operation

STOCK
→ min-so-far + best-so-far
```

---

# 🧪 DAY 10 — SESSION 1 NO-SOLUTION MASTER TEST

**Stop looking at the solutions above. Solve independently.**

## Test 91 — Date Validation

Write:

```python
is_valid_date(day, month, year)
```

Test:

```text
29 / 2 / 2024
29 / 2 / 2023
31 / 4 / 2025
31 / 12 / 2025
31 / 13 / 2025
```

Expected:

```text
True
False
False
True
False
```

### Extra interview test

Determine whether:

```text
1900
2000
2024
2025
```

are leap years.

Expected:

```text
1900 → False
2000 → True
2024 → True
2025 → False
```

---

# Test 92 — Roman Numeral

Write:

```python
roman_to_integer(s)
```

Test:

```text
III
IV
IX
LVIII
MCMXCIV
```

Expected:

```text
3
4
9
58
1994
```

### Recognition test

Without coding, determine:

```text
XIV
```

Answer:

```text
14
```

Reason:

```text
X = 10
I < V → -1 + 5
10 - 1 + 5 = 14
```

---

# Test 93 — Calculator

Write:

```python
calculator(a, b, operator)
```

Test:

```text
20 + 5
20 - 5
20 * 5
20 / 5
20 / 0
```

Expected:

```text
25
15
100
4
Error
```

---

# Test 94 — Stock

Given:

```text
prices = [7, 1, 5, 3, 6, 4]
```

Find maximum profit **without brute force**.

Expected:

```text
5
```

Then test:

```text
[7, 6, 4, 3, 1]
```

Expected:

```text
0
```

And:

```text
[2, 4, 1, 7]
```

Expected:

```text
6
```

because:

```text
buy = 1
sell = 7
profit = 6
```

---

# 🔴 SESSION 1 MASTERY CHECK

### 🟢 Understood

You can explain each solution.

### 🟡 Reproduced

You can rewrite the code after studying it.

### 🟠 Independent

You solve all four master tests without looking.

### 🔴 Mastered

You can see a new placement question and immediately recognize:

```text
validation?
look-ahead?
fixed choices?
minimum-so-far?
```

without blindly trying loops.

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
DAY 9  → 90/90 ✅

DAY 10
Session 1 → 91–94 ✅
Session 2 → 95–97 ⏳
Session 3 → 98–100 ⏳

━━━━━━━━━━━━━━━━━━━━━━
TOTAL → 94/100
REMAIN → 6
━━━━━━━━━━━━━━━━━━━━━━
```

## 🎯 NEXT LOCKED SET

**Day 10 — Session 2 → Problems 95–97**

```text
95. Longest Common Prefix
96. Product of Array Except Self
97. Merge Overlapping Intervals
```

These are the final **higher-value mixed placement problems** before Problems **98–100** close the entire CR2 100-problem program.

Would you like to solve the four Session 1 master tests independently before moving on to Problems 95–97?


# 🔥 CR2 — DAY 10 — SESSION 2

## Problems 95–97 | Final Mixed Placement Challenge

**LOCKED EXECUTION PRESERVED.**
No reduction. No syllabus changes. No mixing with the deeper DSA roadmap.

These are the **final 3 problems before the last Session 3 (98–100)**.

---

# 📌 SESSION 2 SCOPE

| #      | Problem                      | Exact LeetCode                            | Difficulty |
| ------ | ---------------------------- | ----------------------------------------- | ---------- |
| **95** | Longest Common Prefix        | **LC 14 — Longest Common Prefix**         | Easy       |
| **96** | Product of Array Except Self | **LC 238 — Product of Array Except Self** | Medium     |
| **97** | Merge Overlapping Intervals  | **LC 56 — Merge Intervals**               | Medium     |

---

# 🟦 PROBLEM 95 — LONGEST COMMON PREFIX

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 14 — Longest Common Prefix — Easy** ✅

The problem sounds complicated, but the core idea is extremely simple:

> Find the characters that are identical at the same position in **every string**.

Example:

```text id="p1y1i7"
["flower", "flow", "flight"]
```

Compare from the beginning:

```text id="7ml3u9"
f → same
l → same
o → same
w → not same
```

Therefore:

```text id="0v9y5h"
"fl"
```

### 🔥 Senior recognition

When you see:

> "common prefix"

think:

```text id="t3u9zw"
Compare characters column-by-column
```

### Important distinction

**Prefix** means:

```text id="l4pj0v"
starts from index 0
```

It does NOT mean common characters anywhere in the string.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array of strings, return their longest common starting substring.

### Example 1

```text id="d1f7b7"
["flower", "flow", "flight"]
```

Output:

```text id="j70v3j"
"fl"
```

### Example 2

```text id="1f2j2p"
["dog", "racecar", "car"]
```

Output:

```text id="d5c5x4"
""
```

There is no common prefix.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Take:

```text id="w1qv8g"
["flower", "flow", "flight"]
```

We can use the first string as our current prefix:

```text id="x7uh9u"
prefix = "flower"
```

Compare it with:

```text id="ehh4gf"
"flow"
```

Common prefix:

```text id="j0zj7r"
"flow"
```

Now:

```text id="g5odk8"
prefix = "flow"
```

Compare with:

```text id="t3jrr2"
"flight"
```

Character comparison:

```text
f = f
l = l
o != i
```

Therefore:

```text id="u8s2k2"
prefix = "fl"
```

Final answer:

```text id="4v3trn"
"fl"
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. If the string list is empty, return `""`.
2. Take the first string as the current prefix.
3. Compare it against every remaining string.
4. While:

   * prefix has characters,
   * current string has characters,
   * characters at the same position match,

   continue.
5. Shorten the prefix to the matching portion.
6. If prefix becomes empty, return `""`.
7. Return the final prefix.

### Pseudocode

```text id="ym9gch"
prefix = first string

for every other string:

    compare characters from index 0

    keep only matching prefix

    if prefix becomes empty:
        return ""

return prefix
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="fr1bkk"
def longest_common_prefix(strs):

    if not strs:
        return ""

    prefix = strs[0]

    for current in strs[1:]:

        i = 0

        # Compare characters while they match
        while (
            i < len(prefix)
            and i < len(current)
            and prefix[i] == current[i]
        ):
            i += 1

        # Keep only the common part
        prefix = prefix[:i]

        # No common prefix
        if prefix == "":
            return ""

    return prefix


# Tests
print(longest_common_prefix(
    ["flower", "flow", "flight"]
))

print(longest_common_prefix(
    ["dog", "racecar", "car"]
))

print(longest_common_prefix(
    ["interview", "internet", "internal"]
))
```

### Output

```text id="0ah6yy"
fl

inter
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="i7c7hy"
public class Main {

    static String longestCommonPrefix(String[] strs) {

        if (strs.length == 0) {
            return "";
        }

        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++) {

            String current = strs[i];

            int j = 0;

            while (
                j < prefix.length()
                && j < current.length()
                && prefix.charAt(j) == current.charAt(j)
            ) {
                j++;
            }

            prefix = prefix.substring(0, j);

            if (prefix.isEmpty()) {
                return "";
            }
        }

        return prefix;
    }

    public static void main(String[] args) {

        String[] strs = {
            "flower",
            "flow",
            "flight"
        };

        System.out.println(
            longestCommonPrefix(strs)
        );
    }
}
```

### Output

```text id="y3p9dh"
fl
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="r7h3ny"
["flower", "flow", "flight"]
```

Initial:

```text id="j4l55w"
prefix = "flower"
```

### Compare with `"flow"`

| Index | Prefix | Current | Match? |
| ----: | ------ | ------- | ------ |
|     0 | f      | f       | ✅      |
|     1 | l      | l       | ✅      |
|     2 | o      | o       | ✅      |
|     3 | w      | w       | ✅      |
|     4 | e      | —       | ❌      |

Therefore:

```text id="2v9l8s"
prefix = "flow"
```

---

### Compare `"flow"` with `"flight"`

| Index | Prefix | Current | Match? |
| ----: | ------ | ------- | ------ |
|     0 | f      | f       | ✅      |
|     1 | l      | l       | ✅      |
|     2 | o      | i       | ❌      |

Therefore:

```text id="0m8r0v"
prefix = "fl"
```

Final:

```text id="l5uh9h"
"fl"
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text id="n1r2ch"
["car", "card", "care"]
```

Initial:

```text id="c1qj8h"
prefix = "car"
```

Compare `"card"`:

```text id="26qg4e"
c = c
a = a
r = r
```

Prefix remains:

```text id="8b6t5z"
"car"
```

Compare `"care"`:

```text id="m2y3yk"
c = c
a = a
r = r
```

Final:

```text id="h8i0k4"
"car"
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="n1pmu0"
N = number of strings
M = length of the shortest relevant prefix/string
```

In the worst case, we compare up to `M` characters across `N` strings.

Therefore:

```text id="k2j6dv"
Time = O(N × M)
```

Space:

```text id="xjgb6v"
O(M)
```

for the maintained prefix in this implementation.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use the first string as the prefix?

Because the common prefix can never be longer than any individual string.

The first string gives us an initial candidate.

---

### Q2. Why does the prefix only become shorter?

Every additional string can only:

```text id="1czm09"
maintain
or
reduce
```

the common prefix.

It can never make it longer.

---

### Q3. What happens with one string?

```text id="3n5v4j"
["hello"]
```

Answer:

```text id="r1t4ma"
"hello"
```

---

### Q4. What happens with an empty list?

Return:

```text id="5oh5h8"
""
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Common-prefix pattern

```text id="1xaqay"
candidate answer
      ↓
compare with next item
      ↓
shrink candidate
      ↓
repeat
```

### Recognition trigger

> "Longest common prefix"

→ compare from index `0`.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Checking common characters instead of common **prefix**.

Example:

```text id="z0d3c0"
["abc", "xbc"]
```

Both contain `b` and `c`, but common prefix is:

```text id="exkq3p"
""
```

---

### ❌ Mistake 2

Forgetting the shortest string.

```text id="d5lvxk"
["hello", "he"]
```

Answer:

```text id="2xyq0m"
"he"
```

---

### ❌ Mistake 3

Accessing characters beyond string length.

Always ensure:

```python id="v29jyn"
i < len(current)
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="6r72z1"
Start with first string
        ↓
Compare with next string
        ↓
Shrink prefix
        ↓
Repeat
```

### Exact LeetCode

**LC 14 — Longest Common Prefix — Easy** ✅

### Complexity

```text id="4h5taz"
Time  → O(N × M)
Space → O(M)
```

---

# 🟦 PROBLEM 96 — PRODUCT OF ARRAY EXCEPT SELF

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 238 — Product of Array Except Self — Medium** ✅

This is an extremely important placement/interview problem.

Given:

```text id="ykwtgy"
[1, 2, 3, 4]
```

we need:

```text id="i4rcg7"
[24, 12, 8, 6]
```

Because:

```text
index 0 → 2×3×4 = 24
index 1 → 1×3×4 = 12
index 2 → 1×2×4 = 8
index 3 → 1×2×3 = 6
```

### ❌ Naive approach

For every index, multiply all other elements.

That becomes:

```text id="fj6i6t"
O(n²)
```

### 🔥 Senior insight

Split the product into:

```text id="6q7c1e"
LEFT PRODUCT
+
RIGHT PRODUCT
```

For every position:

```text id="w5d6ay"
answer[i]
=
product of everything left
×
product of everything right
```

This is the key.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer array, return an array where:

```text id="a1q2h7"
answer[i]
=
product of all elements except nums[i]
```

### Example

```text id="v2z3or"
nums = [1,2,3,4]
```

Output:

```text id="xjcvh8"
[24,12,8,6]
```

### Important constraint

The standard LC 238 solution should be done **without division**.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Consider:

```text id="u4j22s"
[1, 2, 3, 4]
```

For index 2:

```text id="f2q86n"
[1, 2] × [4]
```

So:

```text id="xzx99s"
answer[2] = 1 × 2 × 4
          = 8
```

We can calculate all left products in one pass.

### Pass 1 — Prefix products

For:

```text id="ycc1c9"
[1,2,3,4]
```

we store:

```text id="p9my2a"
[1,1,2,6]
```

Meaning:

```text id="i4z3au"
index 0 → product before index 0 = 1
index 1 → product before index 1 = 1
index 2 → product before index 2 = 1×2 = 2
index 3 → product before index 3 = 1×2×3 = 6
```

Then scan from right.

Maintain:

```text id="9e5bif"
right_product
```

Multiply each answer by it.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Create result array of size `n`.
2. Set:

   ```text
   prefix = 1
   ```
3. Traverse left → right.
4. Store current prefix in `result[i]`.
5. Update:

   ```text
   prefix *= nums[i]
   ```
6. Set:

   ```text
   suffix = 1
   ```
7. Traverse right → left.
8. Multiply:

   ```text
   result[i] *= suffix
   ```
9. Update:

   ```text
   suffix *= nums[i]
   ```
10. Return result.

### Pseudocode

```text id="j0glf8"
result = [1] * n

prefix = 1

for i from left to right:
    result[i] = prefix
    prefix *= nums[i]

suffix = 1

for i from right to left:
    result[i] *= suffix
    suffix *= nums[i]

return result
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="sk7g5g"
def product_except_self(nums):

    n = len(nums)

    result = [1] * n

    # Pass 1: prefix products
    prefix = 1

    for i in range(n):

        result[i] = prefix

        prefix *= nums[i]

    # Pass 2: suffix products
    suffix = 1

    for i in range(n - 1, -1, -1):

        result[i] *= suffix

        suffix *= nums[i]

    return result


# Test
nums = [1, 2, 3, 4]

print(product_except_self(nums))
```

### Output

```text id="o6w9ca"
[24, 12, 8, 6]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="w5g3gu"
import java.util.Arrays;

public class Main {

    static int[] productExceptSelf(int[] nums) {

        int n = nums.length;

        int[] result = new int[n];

        // Pass 1: prefix products
        int prefix = 1;

        for (int i = 0; i < n; i++) {

            result[i] = prefix;

            prefix *= nums[i];
        }

        // Pass 2: suffix products
        int suffix = 1;

        for (int i = n - 1; i >= 0; i--) {

            result[i] *= suffix;

            suffix *= nums[i];
        }

        return result;
    }

    public static void main(String[] args) {

        int[] nums = {1, 2, 3, 4};

        System.out.println(
            Arrays.toString(productExceptSelf(nums))
        );
    }
}
```

### Output

```text id="z3f9kl"
[24, 12, 8, 6]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="7f5qkq"
[1,2,3,4]
```

## Pass 1 — Prefix

Start:

```text id="o1z2r6"
prefix = 1
result = [1,1,1,1]
```

### i = 0

```text id="axq1rf"
result[0] = 1
prefix = 1 × 1 = 1
```

Result:

```text id="xg2o9g"
[1,1,1,1]
```

### i = 1

```text id="0rqm1n"
result[1] = 1
prefix = 1 × 2 = 2
```

### i = 2

```text id="n9m4sl"
result[2] = 2
prefix = 2 × 3 = 6
```

### i = 3

```text id="f75zkg"
result[3] = 6
prefix = 6 × 4 = 24
```

After first pass:

```text id="6xkwl9"
[1,1,2,6]
```

---

## Pass 2 — Suffix

Start:

```text id="jv6d9a"
suffix = 1
```

### i = 3

```text id="3x5znp"
result[3] = 6 × 1 = 6
suffix = 1 × 4 = 4
```

### i = 2

```text id="g3b1yw"
result[2] = 2 × 4 = 8
suffix = 4 × 3 = 12
```

### i = 1

```text id="7r9s9p"
result[1] = 1 × 12 = 12
suffix = 12 × 2 = 24
```

### i = 0

```text id="f3yqne"
result[0] = 1 × 24 = 24
```

Final:

```text id="3m4z5f"
[24,12,8,6]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text id="tr9r1j"
[2,3,4,5]
```

Prefix pass:

```text id="vknk13"
[1,2,6,24]
```

Suffix pass:

```text id="g7f9u0"
index 3 → 24
index 2 → 2×3×5 = 30
index 1 → 2×4×5 = 40
index 0 → 3×4×5 = 60
```

Final:

```text id="lxy1pn"
[60,40,30,24]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

First pass:

```text id="2s8o7f"
O(n)
```

Second pass:

```text id="2iw2df"
O(n)
```

Total:

```text id="4h2qkv"
O(n) + O(n)
= O(n)
```

Result array:

```text id="b4j6z7"
O(n)
```

Additional variables:

```text id="0o6fjh"
O(1)
```

### Standard LC 238 complexity

```text id="r6zh5m"
Time  → O(n)
Space → O(n) output
Extra auxiliary space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why not use division?

Because LC 238 specifically expects a solution that handles zeroes correctly and avoids division.

---

### Q2. Why two passes?

One pass builds:

```text id="o0j3py"
left product
```

The other builds:

```text id="a9yp4c"
right product
```

---

### Q3. What does `result[i]` contain after the first pass?

The product of all elements **before** `i`.

---

### Q4. What does the second pass do?

It multiplies each position by the product of all elements **after** it.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Prefix + suffix pattern

Whenever a problem asks for:

> Everything before me + everything after me

think:

```text id="a6o0k0"
prefix pass
+
suffix pass
```

For this problem:

```text id="9f48am"
answer[i]
=
left_product[i]
×
right_product[i]
```

This pattern is much more important than memorizing the exact code.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python id="5u0e9q"
total_product / nums[i]
```

This fails with zero and violates the intended approach.

### ❌ Mistake 2

Forgetting:

```text id="7x40kv"
prefix = 1
suffix = 1
```

### ❌ Mistake 3

Wrong reverse range:

```python id="y1jczr"
range(n - 1, -1, -1)
```

is correct.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="f48x9f"
LEFT PRODUCT
     ↓
result[i]

RIGHT PRODUCT
     ↓
multiply result[i]
```

### Exact LeetCode

**LC 238 — Product of Array Except Self — Medium** ✅

### Complexity

```text id="yvhx1h"
Time → O(n)
Output → O(n)
Auxiliary → O(1)
```

---

# 🟦 PROBLEM 97 — MERGE OVERLAPPING INTERVALS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 56 — Merge Intervals — Medium** ✅

This is a classic **sort + scan** problem.

Example:

```text id="k14o8n"
[1,3]
[2,6]
[8,10]
[15,18]
```

The first two overlap:

```text id="w3t4am"
1---3
  2------6
```

So merge:

```text id="i4p4ml"
[1,6]
```

Final:

```text id="l4v0nq"
[[1,6],[8,10],[15,18]]
```

### 🔥 Senior insight

The key is:

> **Sort intervals by start time first.**

Then we only need to compare the current interval with the last merged interval.

Without sorting, overlapping relationships can appear in arbitrary order.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given intervals:

```text id="8idn7r"
[start, end]
```

merge all overlapping intervals.

Example:

```text id="2i7y95"
[[1,3],[2,6],[8,10],[15,18]]
```

Output:

```text id="p2h9gu"
[[1,6],[8,10],[15,18]]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

First sort:

```text id="6n8gti"
[[1,3],[2,6],[8,10],[15,18]]
```

Already sorted.

Start:

```text id="o2v5ls"
merged = [[1,3]]
```

Now inspect:

```text id="kwm5w4"
[2,6]
```

Compare:

```text id="9ow7ae"
2 <= 3
```

They overlap.

Merge:

```text id="8f5l4k"
[1, max(3,6)]
=
[1,6]
```

Next:

```text id="6ky0p9"
[8,10]
```

Check:

```text id="qcfh7v"
8 > 6
```

No overlap.

Add it.

Next:

```text id="7c73ql"
[15,18]
```

```text id="9j7p6c"
15 > 10
```

No overlap.

Add it.

Final:

```text id="04ayzo"
[[1,6],[8,10],[15,18]]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Sort intervals by their starting point.
2. Create an empty `merged` list.
3. Add the first interval.
4. For every remaining interval:

   * Compare its start with the last merged interval's end.
5. If:

   ```text
   current_start <= last_end
   ```

   they overlap.
6. Extend the last merged interval:

   ```text
   last_end = max(last_end, current_end)
   ```
7. Otherwise, append the current interval.
8. Return merged intervals.

### Pseudocode

```text id="o7m1o8"
sort intervals by start

merged = []

for current interval:

    if merged is empty:
        add current

    else if current.start <= last.end:
        last.end = max(last.end, current.end)

    else:
        add current

return merged
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="n4h7ic"
def merge_intervals(intervals):

    if not intervals:
        return []

    # Sort by starting point
    intervals.sort(key=lambda interval: interval[0])

    merged = [intervals[0]]

    for current in intervals[1:]:

        last = merged[-1]

        # Overlap exists
        if current[0] <= last[1]:

            last[1] = max(last[1], current[1])

        else:

            # No overlap
            merged.append(current)

    return merged


# Test
intervals = [
    [1, 3],
    [2, 6],
    [8, 10],
    [15, 18]
]

print(merge_intervals(intervals))
```

### Output

```text id="a1a0pt"
[[1, 6], [8, 10], [15, 18]]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="w2gg4u"
import java.util.*;

public class Main {

    static int[][] mergeIntervals(int[][] intervals) {

        if (intervals.length == 0) {
            return new int[0][0];
        }

        // Sort by starting point
        Arrays.sort(
            intervals,
            Comparator.comparingInt(a -> a[0])
        );

        List<int[]> merged = new ArrayList<>();

        merged.add(intervals[0]);

        for (int i = 1; i < intervals.length; i++) {

            int[] current = intervals[i];
            int[] last = merged.get(merged.size() - 1);

            // Overlap
            if (current[0] <= last[1]) {

                last[1] = Math.max(last[1], current[1]);

            } else {

                merged.add(current);
            }
        }

        return merged.toArray(new int[merged.size()][]);
    }

    static void printIntervals(int[][] intervals) {

        for (int[] interval : intervals) {

            System.out.println(
                "[" + interval[0] +
                ", " + interval[1] + "]"
            );
        }
    }

    public static void main(String[] args) {

        int[][] intervals = {
            {1, 3},
            {2, 6},
            {8, 10},
            {15, 18}
        };

        int[][] result = mergeIntervals(intervals);

        printIntervals(result);
    }
}
```

### Output

```text id="x7qu22"
[1, 6]
[8, 10]
[15, 18]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="t5y2hp"
[[1,3],[2,6],[8,10],[15,18]]
```

### Step 1 — Sort

Already sorted:

```text id="7f5xzw"
[[1,3],[2,6],[8,10],[15,18]]
```

### Step 2

Start:

```text id="y53z6w"
merged = [[1,3]]
```

---

### Current = `[2,6]`

Last merged:

```text id="4v2d0m"
[1,3]
```

Check:

```text id="s6qjpo"
2 <= 3
```

Overlap.

Update:

```text id="m9u8ls"
end = max(3,6)
    = 6
```

Now:

```text id="0wdr7k"
[[1,6]]
```

---

### Current = `[8,10]`

Check:

```text id="6ph4ur"
8 <= 6?
```

False.

Append:

```text id="y8x5eo"
[[1,6],[8,10]]
```

---

### Current = `[15,18]`

Check:

```text id="cnr5q4"
15 <= 10?
```

False.

Append:

```text id="k3z7t5"
[[1,6],[8,10],[15,18]]
```

Final answer:

```text id="s88v9b"
[[1,6],[8,10],[15,18]]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Consider:

```text id="fgr3cn"
[[1,4],[4,5]]
```

Sorted order unchanged.

Start:

```text id="7bsmfl"
merged = [[1,4]]
```

Current:

```text id="j6hjfr"
[4,5]
```

Check:

```text id="89j5eq"
4 <= 4
```

True.

Therefore they overlap/touch and are merged:

```text id="w42lqq"
[1,5]
```

Final:

```text id="pss7bb"
[[1,5]]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="p5k49d"
n = number of intervals
```

### Sorting

Sorting costs:

```text id="rj2q1t"
O(n log n)
```

### Scan

We visit each interval once:

```text id="q5h6cm"
O(n)
```

Total:

```text id="0w3o6a"
O(n log n) + O(n)
= O(n log n)
```

### Space

The merged result may contain `n` intervals:

```text id="wsp6tj"
O(n)
```

depending on whether output storage is counted.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why sort first?

Sorting guarantees intervals are processed from left to right by their start point.

Then only the last merged interval needs to be checked.

---

### Q2. What is the overlap condition?

```text id="m5b7g6"
current_start <= last_end
```

---

### Q3. Why use `max()` for the end?

Consider:

```text id="yubc5t"
[1,10]
[2,5]
```

The merged interval must remain:

```text id="x9agmc"
[1,10]
```

not `[1,5]`.

Therefore:

```python id="b3z1p4"
last[1] = max(last[1], current[1])
```

---

### Q4. What is the main pattern?

```text id="b2r6mw"
SORT
+
SCAN
+
MERGE
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Interval pattern

Whenever you see:

> "Merge overlapping intervals"

immediately think:

```text id="5zyz6k"
1. Sort by start
2. Compare with last merged
3. Overlap → extend
4. No overlap → append
```

### Master condition

```text id="b4p7jx"
current_start <= last_end
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Trying to merge before sorting.

### ❌ Mistake 2

Using:

```python id="0w2v6x"
current[1]
```

instead of:

```python id="4o8h19"
max(last[1], current[1])
```

### ❌ Mistake 3

Using:

```text id="7a6u3s"
current_start < last_end
```

when touching intervals should also merge.

For:

```text id="q7ufxj"
[1,4]
[4,5]
```

the standard LC 56 solution merges them.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Core pattern

```text id="y5p25f"
SORT BY START
      ↓
SCAN
      ↓
OVERLAP?
      ↓
EXTEND
```

### Formula

```python id="1x2txf"
if current[0] <= last[1]:
    last[1] = max(last[1], current[1])
```

### Exact LeetCode

**LC 56 — Merge Intervals — Medium** ✅

### Complexity

```text id="h6zqvf"
Time  → O(n log n)
Space → O(n) output/result
```

---

# 🧠 DAY 10 — SESSION 2 MASTER PATTERN MAP

You have now covered:

```text id="c3dq9m"
95 → LONGEST COMMON PREFIX
     Compare same-position characters
     Shrink candidate prefix

96 → PRODUCT EXCEPT SELF
     Prefix products
     +
     Suffix products

97 → MERGE INTERVALS
     Sort by start
     +
     Scan
     +
     Merge overlap
```

---

# 🔥 THREE HIGH-VALUE PATTERNS TO MEMORIZE

```text id="xaxl3c"
COMMON PREFIX
     ↓
candidate answer shrinks


PRODUCT EXCEPT SELF
     ↓
left product × right product


MERGE INTERVALS
     ↓
sort + scan + merge
```

---

# 🧪 SESSION 2 — NO-SOLUTION MASTER TEST

**Do not look at the solutions while solving.**

## 🧪 TEST 95 — LONGEST COMMON PREFIX

Input:

```text id="blq0v8"
["interview", "internet", "internal"]
```

Expected:

```text id="qww1hf"
"inter"
```

Then:

```text id="w5r8a0"
["apple", "application", "apply"]
```

Find the answer.

---

## 🧪 TEST 96 — PRODUCT EXCEPT SELF

Input:

```text id="2c8z9q"
[2, 3, 4, 5]
```

Expected:

```text id="3xjp8h"
[60, 40, 30, 24]
```

### Zero test

Solve:

```text id="j3e0e5"
[1, 2, 0, 4]
```

Expected:

```text id="e4o0kq"
[0, 0, 8, 0]
```

This is one reason the division approach is problematic.

---

## 🧪 TEST 97 — MERGE INTERVALS

Input:

```text id="prjv7d"
[[1,4],[2,5],[7,9],[8,10]]
```

Expected:

```text id="9f6t6w"
[[1,5],[7,10]]
```

### Tricky test

```text id="jydj6b"
[[1,10],[2,3],[4,8]]
```

Expected:

```text id="0k1a4d"
[[1,10]]
```

The later intervals are completely contained inside the first one.

---

# 🔴 SESSION 2 MASTERY CHECK

### 🟢 Understood

You can explain:

```text
prefix
prefix/suffix
interval merging
```

### 🟡 Reproduced

You can rewrite all three solutions after reviewing them.

### 🟠 Independent

You solve Tests 95–97 without looking.

### 🔴 Mastered

Given a completely new placement problem, you can recognize:

```text
"common beginning"
      ↓
Common Prefix

"everything except current"
      ↓
Prefix + Suffix

"overlapping ranges"
      ↓
Sort + Merge
```

---

# 📊 CR2 PROGRESS

```text id="4q3cql"
DAY 1  → 10/10 ✅
DAY 2  → 20/20 ✅
DAY 3  → 30/30 ✅
DAY 4  → 40/40 ✅
DAY 5  → 50/50 ✅
DAY 6  → 60/60 ✅
DAY 7  → 70/70 ✅
DAY 8  → 80/80 ✅
DAY 9  → 90/90 ✅

DAY 10
Session 1 → 91–94 ✅
Session 2 → 95–97 ✅
Session 3 → 98–100 ⏳

━━━━━━━━━━━━━━━━━━━━━━
TOTAL   → 97/100
REMAIN  → 3
━━━━━━━━━━━━━━━━━━━━━━
```

# 🎯 NEXT LOCKED SET

## DAY 10 — SESSION 3

```text
98. Missing + Repeating Number
99. Spiral Matrix
100. Rotate Matrix 90°
```

These **final 3 problems complete the locked CR2 100-problem placement program.**

Would you like to continue with Day 10 — Session 3 and finish Problems 98–100?


# 🔥 CR2 — DAY 10 — SESSION 3

# 🏁 FINAL SESSION — PROBLEMS 98–100

**LOCKED EXECUTION PRESERVED.**
**No reduction. No syllabus changes. No mixing with the deeper DSA roadmap.**

This is the **final 3-problem session of CR2**.

After this:

```text
100 / 100
```

will be completed.

---

# 📌 SESSION 3 SCOPE

| #       | Problem                    | Exact LeetCode Match               | Difficulty       |
| ------- | -------------------------- | ---------------------------------- | ---------------- |
| **98**  | Missing + Repeating Number | No exact single canonical LC match | Medium placement |
| **99**  | Spiral Matrix              | **LC 54 — Spiral Matrix**          | Medium           |
| **100** | Rotate Matrix 90°          | **LC 48 — Rotate Image**           | Medium           |

---

# 🟦 PROBLEM 98 — MISSING + REPEATING NUMBER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a classic placement problem.

Suppose:

```text
[1, 2, 2, 4, 5]
```

The numbers should be:

```text
1, 2, 3, 4, 5
```

But:

```text
3 → missing
2 → repeated
```

Answer:

```text
Missing = 3
Repeating = 2
```

### 🔥 Senior observation

There are two different abnormalities:

```text
one number appears twice
one number does not appear
```

The easiest placement-friendly approach is:

```text
Frequency counting
```

Create a frequency map and inspect numbers from `1` to `n`.

### Why not jump immediately to XOR?

There are XOR-based solutions, but for CR2 the priority is:

```text
correct logic
easy recognition
easy implementation
easy debugging
```

Frequency counting is extremely clear.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array containing `n` numbers from:

```text
1 to n
```

exactly one number appears twice and exactly one number is missing.

Find both.

### Example

```text
Input:
[1, 2, 2, 4, 5]

Output:
Repeating = 2
Missing = 3
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Create:

```text
frequency = {}
```

For:

```text
[1,2,2,4,5]
```

we get:

```text
1 → 1
2 → 2
3 → 0
4 → 1
5 → 1
```

Therefore:

```text
frequency == 2
→ repeating

frequency == 0
→ missing
```

### 🔥 Pattern

Whenever the question says:

> "Find duplicate/missing/frequency"

think:

```text
HashMap / Dictionary
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Let `n = len(nums)`.
2. Create an empty frequency dictionary.
3. Count every number.
4. Loop from `1` through `n`.
5. If frequency is `2`:

   ```text
   repeating = number
   ```
6. If frequency is `0`:

   ```text
   missing = number
   ```
7. Return both.

### Pseudocode

```text
n = length(nums)

frequency = empty map

for x in nums:
    frequency[x] += 1

for number from 1 to n:

    if frequency[number] == 2:
        repeating = number

    if frequency[number] == 0:
        missing = number

return repeating, missing
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="b0s5t2"
def find_missing_and_repeating(nums):

    n = len(nums)

    frequency = {}

    # Count occurrences
    for num in nums:
        frequency[num] = frequency.get(num, 0) + 1

    missing = -1
    repeating = -1

    # Check numbers from 1 to n
    for num in range(1, n + 1):

        if frequency.get(num, 0) == 0:
            missing = num

        elif frequency.get(num, 0) == 2:
            repeating = num

    return repeating, missing


# Test
nums = [1, 2, 2, 4, 5]

print(find_missing_and_repeating(nums))
```

### Output

```text id="f5y3qn"
(2, 3)
```

Meaning:

```text
Repeating = 2
Missing = 3
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="q2t1d7"
import java.util.HashMap;
import java.util.Map;

public class Main {

    static int[] findMissingAndRepeating(int[] nums) {

        int n = nums.length;

        Map<Integer, Integer> frequency = new HashMap<>();

        // Count occurrences
        for (int num : nums) {

            frequency.put(
                num,
                frequency.getOrDefault(num, 0) + 1
            );
        }

        int missing = -1;
        int repeating = -1;

        // Check numbers from 1 to n
        for (int num = 1; num <= n; num++) {

            int count = frequency.getOrDefault(num, 0);

            if (count == 0) {

                missing = num;

            } else if (count == 2) {

                repeating = num;
            }
        }

        return new int[]{repeating, missing};
    }

    public static void main(String[] args) {

        int[] nums = {1, 2, 2, 4, 5};

        int[] result = findMissingAndRepeating(nums);

        System.out.println(
            "Repeating = " + result[0]
        );

        System.out.println(
            "Missing = " + result[1]
        );
    }
}
```

### Output

```text id="n7l7v4"
Repeating = 2
Missing = 3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="0v4m9p"
[1,2,2,4,5]
```

### Frequency construction

| Number | Frequency |
| -----: | --------: |
|      1 |         1 |
|      2 |         2 |
|      4 |         1 |
|      5 |         1 |

Notice:

```text
3
```

doesn't appear.

Therefore:

```text
freq[3] = 0
```

### Second scan

| Number | Frequency | Action        |
| -----: | --------: | ------------- |
|      1 |         1 | nothing       |
|      2 |         2 | repeating = 2 |
|      3 |         0 | missing = 3   |
|      4 |         1 | nothing       |
|      5 |         1 | nothing       |

Final:

```text
Repeating = 2
Missing = 3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text id="3n5n5n"
[3,1,3,4,5]
```

Expected range:

```text
1 2 3 4 5
```

Frequency:

```text
1 → 1
2 → 0
3 → 2
4 → 1
5 → 1
```

Therefore:

```text
2 → missing
3 → repeating
```

Output:

```text
Repeating = 3
Missing = 2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of elements
```

First pass:

```text
O(n)
```

Second pass:

```text
O(n)
```

Total:

```text
O(n)
```

Frequency map can contain up to `n` entries.

Therefore:

```text
Time  → O(n)
Space → O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we check numbers from `1` to `n`?

Because the problem guarantees the expected range is:

```text
1 ... n
```

---

### Q2. How do we identify the repeating number?

Its frequency is:

```text
2
```

---

### Q3. How do we identify the missing number?

Its frequency is:

```text
0
```

---

### Q4. Is there an O(1)-extra-space solution?

Yes.

There are mathematical/XOR approaches, but the CR2 version intentionally prioritizes the simple frequency-map solution.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recognition trigger

```text
missing
duplicate
frequency
repeating
occurrences
```

Think:

```text
HashMap / Dictionary
```

### Master idea

```text
frequency == 0 → missing
frequency == 2 → repeating
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Only finding the duplicate.

The question asks for **both**.

### ❌ Mistake 2

Checking only the input array.

The missing number is precisely the number that **never appears**.

### ❌ Mistake 3

Forgetting the expected range:

```text
1 to n
```

### ❌ Mistake 4

Returning:

```text
missing, repeating
```

when the required order is:

```text
repeating, missing
```

Always read the requested output format carefully.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Count frequencies
      ↓
0 occurrences → Missing
2 occurrences → Repeating
```

### Exact LeetCode Match

**No exact single canonical LeetCode match for this exact two-output placement formulation.**

### Complexity

```text
Time  → O(n)
Space → O(n)
```

---

# 🟦 PROBLEM 99 — SPIRAL MATRIX

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 54 — Spiral Matrix — Medium** ✅

This is a classic matrix-boundary problem.

Example:

```text
1  2  3
4  5  6
7  8  9
```

Spiral order:

```text
1 → 2 → 3 → 6 → 9 → 8 → 7 → 4 → 5
```

Output:

```text
[1,2,3,6,9,8,7,4,5]
```

### 🔥 Senior insight

Do NOT think:

> "How do I turn?"

Think:

> **Which boundary am I processing?**

Maintain four boundaries:

```text
top
bottom
left
right
```

Then repeatedly process:

```text
→ top row
↓ right column
← bottom row
↑ left column
```

and shrink the boundaries.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a matrix, return all elements in spiral order.

Example:

```text
Input:

1 2 3
4 5 6
7 8 9
```

Output:

```text
[1,2,3,6,9,8,7,4,5]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Start with:

```text
top = 0
bottom = rows - 1
left = 0
right = cols - 1
```

For:

```text
1 2 3
4 5 6
7 8 9
```

Initial boundaries:

```text
top = 0
bottom = 2
left = 0
right = 2
```

### Step 1 → Top row

```text
1 2 3
```

Then:

```text
top += 1
```

---

### Step 2 → Right column

```text
6
9
```

Then:

```text
right -= 1
```

---

### Step 3 → Bottom row

Right → left:

```text
8 7
```

Then:

```text
bottom -= 1
```

---

### Step 4 → Left column

Bottom → top:

```text
4
```

Then:

```text
left += 1
```

Remaining:

```text
5
```

Add it.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Initialize:

   ```text
   top = 0
   bottom = rows - 1
   left = 0
   right = cols - 1
   ```
2. While:

   ```text
   top <= bottom AND left <= right
   ```
3. Traverse the top row from left → right.
4. Increment `top`.
5. Traverse the right column from top → bottom.
6. Decrement `right`.
7. If `top <= bottom`, traverse bottom row right → left.
8. Decrement `bottom`.
9. If `left <= right`, traverse left column bottom → top.
10. Increment `left`.
11. Continue until boundaries cross.

### ⚠️ Why are the extra conditions important?

For a rectangular/single-row/single-column matrix, you can accidentally visit elements twice.

So after changing boundaries, verify the remaining region still exists.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="9qjpjm"
def spiral_order(matrix):

    if not matrix:
        return []

    result = []

    top = 0
    bottom = len(matrix) - 1
    left = 0
    right = len(matrix[0]) - 1

    while top <= bottom and left <= right:

        # 1. Left → Right across top row
        for col in range(left, right + 1):
            result.append(matrix[top][col])

        top += 1

        # 2. Top → Bottom down right column
        for row in range(top, bottom + 1):
            result.append(matrix[row][right])

        right -= 1

        # 3. Right → Left across bottom row
        if top <= bottom:

            for col in range(right, left - 1, -1):
                result.append(matrix[bottom][col])

            bottom -= 1

        # 4. Bottom → Top up left column
        if left <= right:

            for row in range(bottom, top - 1, -1):
                result.append(matrix[row][left])

            left += 1

    return result


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(spiral_order(matrix))
```

### Output

```text
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="n9qf6v"
import java.util.*;

public class Main {

    static List<Integer> spiralOrder(int[][] matrix) {

        List<Integer> result = new ArrayList<>();

        if (matrix.length == 0) {
            return result;
        }

        int top = 0;
        int bottom = matrix.length - 1;
        int left = 0;
        int right = matrix[0].length - 1;

        while (top <= bottom && left <= right) {

            // 1. Left → Right
            for (int col = left; col <= right; col++) {
                result.add(matrix[top][col]);
            }

            top++;

            // 2. Top → Bottom
            for (int row = top; row <= bottom; row++) {
                result.add(matrix[row][right]);
            }

            right--;

            // 3. Right → Left
            if (top <= bottom) {

                for (int col = right; col >= left; col--) {
                    result.add(matrix[bottom][col]);
                }

                bottom--;
            }

            // 4. Bottom → Top
            if (left <= right) {

                for (int row = bottom; row >= top; row--) {
                    result.add(matrix[row][left]);
                }

                left++;
            }
        }

        return result;
    }

    public static void main(String[] args) {

        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        System.out.println(spiralOrder(matrix));
    }
}
```

### Output

```text
[1, 2, 3, 6, 9, 8, 7, 4, 5]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
1 2 3
4 5 6
7 8 9
```

Initial:

```text
top = 0
bottom = 2
left = 0
right = 2
```

### Round 1 — Top

```text
1 2 3
```

Result:

```text
[1,2,3]
```

Update:

```text
top = 1
```

---

### Right column

```text
6
9
```

Result:

```text
[1,2,3,6,9]
```

Update:

```text
right = 1
```

---

### Bottom row

Right → left:

```text
8 7
```

Result:

```text
[1,2,3,6,9,8,7]
```

Update:

```text
bottom = 1
```

---

### Left column

Bottom → top:

```text
4
```

Result:

```text
[1,2,3,6,9,8,7,4]
```

Update:

```text
left = 1
```

---

### Final remaining cell

```text
5
```

Result:

```text
[1,2,3,6,9,8,7,4,5]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Consider:

```text
1 2 3 4
5 6 7 8
9 10 11 12
```

Spiral:

```text
1
2
3
4
8
12
11
10
9
5
6
7
```

Final:

```text
[1,2,3,4,8,12,11,10,9,5,6,7]
```

The boundaries shrink after every side.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For an `m × n` matrix:

Every element is visited exactly once.

Therefore:

```text
Time = O(m × n)
```

Output contains all elements:

```text
Space = O(m × n)
```

for the returned result.

Auxiliary variables:

```text
O(1)
```

excluding the output.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What are the four boundaries?

```text
top
bottom
left
right
```

---

### Q2. What are the four traversal directions?

```text
left → right
top → bottom
right → left
bottom → top
```

---

### Q3. Why do we need boundary checks?

To avoid processing the same row or column twice when the remaining matrix collapses to one row or one column.

---

### Q4. Complexity?

```text
Time → O(mn)
Space → O(mn) output
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Matrix boundary pattern

```text
TOP ROW
   ↓
RIGHT COLUMN
   ↓
BOTTOM ROW
   ↓
LEFT COLUMN
   ↓
SHRINK BOUNDARIES
   ↓
REPEAT
```

### Recognition trigger

> "Traverse matrix clockwise / spiral"

Immediately think:

```text
top
bottom
left
right
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Forgetting:

```text
top += 1
right -= 1
bottom -= 1
left += 1
```

### ❌ Mistake 2

Always traversing bottom/left without checking whether the boundaries still exist.

### ❌ Mistake 3

Wrong direction on bottom row.

Correct:

```text
right → left
```

### ❌ Mistake 4

Wrong direction on left column.

Correct:

```text
bottom → top
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Master template

```text
top, bottom, left, right

→ top row
↓ right column
← bottom row
↑ left column

shrink boundaries
repeat
```

### Exact LeetCode

**LC 54 — Spiral Matrix — Medium** ✅

### Complexity

```text
Time  → O(mn)
Space → O(mn) output
```

---

# 🟦 PROBLEM 100 — ROTATE MATRIX 90° CLOCKWISE

# 🏆 FINAL CR2 PROBLEM

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Exact LeetCode:** **LC 48 — Rotate Image — Medium** ✅

Given a square matrix:

```text
1 2 3
4 5 6
7 8 9
```

rotate it **90° clockwise**:

```text
7 4 1
8 5 2
9 6 3
```

### 🔥 The key insight

90° clockwise rotation can be broken into:

```text
STEP 1
Transpose matrix

STEP 2
Reverse every row
```

That's the cleanest interview pattern.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an `n × n` matrix, rotate it 90 degrees clockwise **in-place**.

Example:

```text
Input:

1 2 3
4 5 6
7 8 9
```

Output:

```text
7 4 1
8 5 2
9 6 3
```

### Important

The standard LC 48 version requires:

```text
in-place
```

So we should not create another matrix.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Start:

```text
1 2 3
4 5 6
7 8 9
```

## Step 1 — Transpose

Swap:

```text
matrix[i][j]
```

with:

```text
matrix[j][i]
```

Result:

```text
1 4 7
2 5 8
3 6 9
```

## Step 2 — Reverse every row

```text
1 4 7 → 7 4 1
2 5 8 → 8 5 2
3 6 9 → 9 6 3
```

Final:

```text
7 4 1
8 5 2
9 6 3
```

### 🔥 This is the pattern you must remember.

```text
90° clockwise
=
Transpose
+
Reverse every row
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1 — Transpose

For:

```text
i = 0 to n-1
j = i+1 to n-1
```

swap:

```text
matrix[i][j]
matrix[j][i]
```

### Why start `j` at `i+1`?

Because we only need to swap one side of the diagonal.

If we swap everything, we undo our previous swaps.

---

### Step 2 — Reverse every row

For each row:

```text
left = 0
right = n-1
```

swap until:

```text
left >= right
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="jj7qv9"
def rotate_matrix(matrix):

    n = len(matrix)

    # Step 1: Transpose the matrix
    for i in range(n):

        for j in range(i + 1, n):

            matrix[i][j], matrix[j][i] = (
                matrix[j][i],
                matrix[i][j]
            )

    # Step 2: Reverse every row
    for row in matrix:

        left = 0
        right = n - 1

        while left < right:

            row[left], row[right] = (
                row[right],
                row[left]
            )

            left += 1
            right -= 1


# Test
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

rotate_matrix(matrix)

print(matrix)
```

### Output

```text
[[7, 4, 1],
 [8, 5, 2],
 [9, 6, 3]]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="l3x9sm"
import java.util.Arrays;

public class Main {

    static void rotateMatrix(int[][] matrix) {

        int n = matrix.length;

        // Step 1: Transpose
        for (int i = 0; i < n; i++) {

            for (int j = i + 1; j < n; j++) {

                int temp = matrix[i][j];

                matrix[i][j] = matrix[j][i];

                matrix[j][i] = temp;
            }
        }

        // Step 2: Reverse every row
        for (int[] row : matrix) {

            int left = 0;
            int right = n - 1;

            while (left < right) {

                int temp = row[left];

                row[left] = row[right];

                row[right] = temp;

                left++;
                right--;
            }
        }
    }

    public static void main(String[] args) {

        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        rotateMatrix(matrix);

        for (int[] row : matrix) {
            System.out.println(Arrays.toString(row));
        }
    }
}
```

### Output

```text
[7, 4, 1]
[8, 5, 2]
[9, 6, 3]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Initial:

```text
1 2 3
4 5 6
7 8 9
```

## STEP 1 — Transpose

Swap:

```text
matrix[0][1] ↔ matrix[1][0]
```

So:

```text
2 ↔ 4
```

Matrix:

```text
1 4 3
2 5 6
7 8 9
```

Next:

```text
matrix[0][2] ↔ matrix[2][0]
```

```text
3 ↔ 7
```

Matrix:

```text
1 4 7
2 5 6
3 8 9
```

Next:

```text
matrix[1][2] ↔ matrix[2][1]
```

```text
6 ↔ 8
```

Final transpose:

```text
1 4 7
2 5 8
3 6 9
```

---

## STEP 2 — Reverse each row

Row 1:

```text
1 4 7
```

becomes:

```text
7 4 1
```

Row 2:

```text
2 5 8
```

becomes:

```text
8 5 2
```

Row 3:

```text
3 6 9
```

becomes:

```text
9 6 3
```

Final:

```text
7 4 1
8 5 2
9 6 3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
1 2
3 4
```

### Transpose

Swap:

```text
2 ↔ 3
```

Result:

```text
1 3
2 4
```

### Reverse rows

```text
1 3 → 3 1
2 4 → 4 2
```

Final:

```text
3 1
4 2
```

That is a 90° clockwise rotation.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

### Transpose

There are approximately:

```text
n² / 2
```

swaps.

Therefore:

```text
O(n²)
```

### Reverse rows

There are `n` rows and each takes approximately `n/2` swaps:

```text
O(n²)
```

Total:

```text
O(n²)
```

### Space

No additional matrix is created.

Only temporary variables are used.

Therefore:

```text
O(1)
```

auxiliary space.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the easiest way to rotate 90° clockwise?

```text
Transpose
+
Reverse every row
```

---

### Q2. Why do we transpose only one side of the diagonal?

Because swapping both:

```text
[i][j]
```

and:

```text
[j][i]
```

twice would undo the transpose.

---

### Q3. Is this in-place?

Yes.

No second matrix is created.

---

### Q4. What is the complexity?

```text
Time  → O(n²)
Space → O(1) auxiliary
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 MATRIX ROTATION MASTER PATTERN

### 90° clockwise

```text
Transpose
+
Reverse every row
```

### 90° counterclockwise

```text
Transpose
+
Reverse every column
```

For CR2, **memorize clockwise first**.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Creating another matrix.

That works, but violates the standard in-place LC 48 requirement.

### ❌ Mistake 2

Reversing before transposing.

Order matters.

Correct:

```text
Transpose
→ Reverse rows
```

### ❌ Mistake 3

Transposing using:

```python
for i in range(n):
    for j in range(n):
```

and swapping everything.

That causes double swaps.

Correct:

```python
for i in range(n):
    for j in range(i + 1, n):
```

### ❌ Mistake 4

Confusing clockwise with counterclockwise.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### One sentence:

> **90° clockwise rotation = transpose + reverse every row.**

### Exact LeetCode

**LC 48 — Rotate Image — Medium** ✅

### Complexity

```text
Time  → O(n²)
Space → O(1)
```

---

# 🏆 CR2 — FINAL 3-PROBLEM PATTERN MAP

```text
98 → MISSING + REPEATING
     Frequency Map
     0 → Missing
     2 → Repeating

99 → SPIRAL MATRIX
     Four boundaries
     → ↓ ← ↑
     Shrink boundaries

100 → ROTATE MATRIX 90°
      Transpose
      +
      Reverse every row
```

---

# 🔥 FINAL CR2 PATTERN CHEAT SHEET

You have now covered the full **100-problem foundation**.

## NUMBER / MATH

```text
Reverse number
Palindrome
Digits
Sum digits
Prime
GCD
LCM
Armstrong
Perfect number
Harshad
Happy
Strong
Fibonacci
Factors
Perfect square
Factorial
Power
Decimal/Binary
```

## STRINGS

```text
Reverse
Palindrome
Character counting
Frequency
Duplicates
Anagram
First unique
Toggle case
Reverse words
Longest word
String → integer
Rotation
Common prefix
Pangram
Run-length encoding
Balanced brackets
```

## ARRAYS

```text
Min / Max
Second largest/smallest
Reverse
Sum
Average
Even / Odd
Sorted check
Missing number
Duplicate
Move zeroes
Merge arrays
Intersection
Rotation
Maximum subarray
Two Sum
Majority
Pivot index
Sort 0/1/2
```

## SEARCH / SORT / GREEDY

```text
Linear Search
Binary Search

Bubble Sort
Selection Sort
Insertion Sort

Kth Largest
Frequency Sort
Assign Cookies
Minimum Coins
```

## HASHING

```text
Frequency Map
First Repeating
First Non-Repeating
Equal Multisets
Union
3-array intersection
Group Anagrams
Longest Consecutive
Pair Difference
Intersection with multiplicity
```

## BITWISE

```text
n & 1
n & (n-1)
XOR
Power of Two

SET:
n | (1 << k)

CLEAR:
n & ~(1 << k)

TOGGLE:
n ^ (1 << k)
```

## RECURSION

```text
Factorial
Reverse String
```

## MATRIX

```text
Transpose
Main Diagonal
Spiral Traversal
90° Rotation
```

## MIXED INTERVIEW PATTERNS

```text
Date Validation
Roman → Integer
Calculator
Stock Profit
Longest Common Prefix
Product Except Self
Merge Intervals
Missing + Repeating
```

---

# 🧠 THE 100-PROBLEM CR2 MASTER PATTERN LIBRARY

The most important thing is **not memorizing 100 programs individually**.

You should now compress them into reusable patterns:

```text
1. Linear Scan
2. Two Pointers
3. Sliding Window basics
4. Binary Search
5. HashMap / Frequency
6. HashSet
7. Sorting
8. Greedy
9. Stack
10. Queue
11. Bitwise
12. XOR
13. Recursion
14. Nested Loops
15. Prefix/Suffix
16. Matrix Coordinates
17. Matrix Boundaries
18. Interval Merge
19. Validation
20. Look-Ahead
```

---

# 🧪 FINAL CR2 MASTER TEST — 100-PROBLEM GRADUATION TEST

## 🚨 RULE

No notes.

No solutions.

No ChatGPT help.

Use only your compiler.

Solve these **20 representative problems** to verify whether the 100 problems became actual skill rather than passive reading.

### Round 1 — Fundamentals

**1.** Reverse a number
**2.** Check palindrome number
**3.** Find GCD
**4.** Check prime
**5.** Armstrong number

### Round 2 — Strings

**6.** Reverse string
**7.** Check anagram
**8.** First non-repeating character
**9.** Balanced brackets
**10.** Longest common prefix

### Round 3 — Arrays

**11.** Missing number
**12.** Move zeroes
**13.** Two Sum
**14.** Maximum subarray
**15.** Majority element

### Round 4 — Core Patterns

**16.** Binary Search
**17.** Group Anagrams
**18.** Longest Consecutive Sequence

### Round 5 — Final Matrix/Interview

**19.** Spiral Matrix
**20.** Rotate Matrix 90°

---

# 🔴 CR2 MASTERY STANDARD

You are **not** finished merely because you have seen all 100 solutions.

Your real target is:

```text
🟢 UNDERSTOOD
     ↓
🟡 REPRODUCED
     ↓
🟠 INDEPENDENT
     ↓
🔴 MASTERED
```

For a placement-ready candidate, the critical ability is:

```text
Question
   ↓
Identify pattern
   ↓
Choose data structure
   ↓
Write algorithm
   ↓
Code without copying
   ↓
Dry run
   ↓
Explain complexity
```

---

# 🏆 CR2 — OFFICIAL COMPLETION

```text
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
        CR2 BOOTCAMP
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

DAY 1   → 10/10  ✅
DAY 2   → 20/20  ✅
DAY 3   → 30/30  ✅
DAY 4   → 40/40  ✅
DAY 5   → 50/50  ✅
DAY 6   → 60/60  ✅
DAY 7   → 70/70  ✅
DAY 8   → 80/80  ✅
DAY 9   → 90/90  ✅
DAY 10  → 100/100 ✅

━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
       🎯 100 / 100
       CR2 COMPLETE
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

# 🏁 FINAL VERDICT ON THE TRAINING

**CR2 has achieved its intended purpose:** building **basic coding fluency, placement logic, syntax confidence, pattern recognition, and independent implementation** across Python + Java.

But this is **not the end of your DSA preparation**.

The correct next step is to take these patterns into your **separate deeper DSA/LeetCode track**, where the goal changes from:

```text
"Can I code this?"
```

to:

```text
"Can I recognize the optimal pattern
under interview pressure,
prove why it works,
handle variations,
and solve MAANG-level problems?"
```

**CR2 = Foundation completed.
Deep DSA = Mastery phase.**

Would you like to start with the 20-problem graduation test, or review any of the final three patterns first?
