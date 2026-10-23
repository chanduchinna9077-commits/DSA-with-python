# 🟣 11. PATTERN PRINTING — 10 Problems

And **yes, this should be its own topic.**

Pattern printing isn't really a DSA data structure, but it's extremely useful for screening tests because it tests:

* nested loops
* row/column thinking
* conditions
* spaces
* pattern relationships
* mathematical indexing

## 🔥 Pattern Printing — 10 Problems

### 1. Right Triangle — Stars

```text
*
**
***
****
*****
```

**Pattern:** increasing columns.

---

### 2. Inverted Triangle

```text
*****
****
***
**
*
```

**Pattern:** decreasing columns.

---

### 3. Number Triangle

```text
1
12
123
1234
12345
```

**Pattern:** column goes from `1 → row`.

---

### 4. Repeated Number Triangle

```text
1
22
333
4444
55555
```

**Pattern:** print row number repeatedly.

---

### 5. Pyramid

```text
    *
   ***
  *****
 *******
*********
```

**Pattern:**

```text
spaces = n - row
stars  = 2 * row - 1
```

---

### 6. Inverted Pyramid

```text
*********
 *******
  *****
   ***
    *
```

Same concept but reversed.

---

### 7. Hollow Square

```text
*****
*   *
*   *
*   *
*****
```

**Pattern:** boundary condition.

This one is particularly useful because it teaches:

```python
if i == 0 or i == n-1 or j == 0 or j == n-1:
```

---

### 8. Floyd's Triangle

```text
1
2 3
4 5 6
7 8 9 10
```

**Pattern:** running counter.

---

### 9. 0–1 Triangle

```text
1
01
101
0101
10101
```

**Pattern:** `(row + column) % 2`.

---

### 10. Diamond Pattern

```text
    *
   ***
  *****
 *******
  *****
   ***
    *
```

This combines:

```text
Increasing pyramid
+
Decreasing pyramid
```




Absolutely. We’ll start **PATTERN PRINTING using the same locked TopGun execution version** — no reduction in depth.

# 🟦 PATTERN PRINTING — CONVERSATION 1

## Problems 1–4

### Locked Pattern Printing Roadmap

|  # | Problem                    | Core Pattern                |
| -: | -------------------------- | --------------------------- |
|  1 | Right-Angled Star Triangle | Nested loops                |
|  2 | Inverted Star Triangle     | Reverse row control         |
|  3 | Number Triangle            | Row-based number generation |
|  4 | Repeated Number Triangle   | Fixed value per row         |
|  5 | Inverted Number Triangle   | Reverse row control         |
|  6 | Pyramid                    | Spaces + stars              |
|  7 | Inverted Pyramid           | Spaces + decreasing stars   |
|  8 | Number Pyramid             | Spaces + numbers            |
|  9 | Floyd's Triangle           | Running number              |
| 10 | Hollow Square / Rectangle  | Boundary condition          |

### Execution structure for **every problem**

1. Problem statement
2. Problem theory
3. Pattern being tested
4. ELI10 intuition
5. Example
6. Algorithm — Step-by-step
7. Python using built-in methods
8. Python without built-in methods
9. Line-by-line explanation
10. Detailed dry run/table
11. Time complexity
12. Space complexity
13. Edge cases
14. Common mistakes/traps
15. Pattern recognition — **When you see X → think Y**

---

# 🔵 PROBLEM 1 — RIGHT-ANGLED STAR TRIANGLE

## 1. Problem Statement

Given `n`, print a right-angled triangle of stars.

For:

```text
n = 5
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

# 2. Problem Theory

Pattern printing is mainly about understanding:

> **Rows + Columns**

Every pattern can be converted into questions:

```text
How many rows?
How many things in each row?
What should each thing contain?
```

For this pattern:

```text
Row 1 → 1 star
Row 2 → 2 stars
Row 3 → 3 stars
Row 4 → 4 stars
Row 5 → 5 stars
```

Therefore:

```text
Row i → i stars
```

This is the fundamental pattern-printing relationship.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

```text
Outer loop → rows
Inner loop → columns/items
```

Specifically:

```text
for i in range(1, n + 1):
    print i stars
```

---

# 4. ELI10 Intuition

Imagine building stairs.

First row:

```text
*
```

Second row:

```text
**
```

Third row:

```text
***
```

Every time you go to a new row:

> Add one more star.

So:

```text
row number = number of stars
```

That's the entire idea.

---

# 5. Example

Input:

```text
n = 4
```

Output:

```text
*
**
***
****
```

Observe:

```text
Row 1 → 1
Row 2 → 2
Row 3 → 3
Row 4 → 4
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Take `n`.

### Step 2

Run an outer loop from `1` to `n`.

### Step 3

For each row `i`, print exactly `i` stars.

### Step 4

Move to the next line.

### Pseudocode

```text
for row = 1 to n:
    for column = 1 to row:
        print "*"
    move to next line
```

---

# 7. Python Solution — Using Built-in Methods

Python allows string multiplication:

```python id="4d1wz3"
def star_triangle(n):
    for i in range(1, n + 1):
        print("*" * i)


star_triangle(5)
```

Output:

```text id="w2okd6"
*
**
***
****
*****
```

### Why does this work?

```python id="3q5w42"
"*" * 3
```

produces:

```text id="z0w3fq"
***
```

So:

```python id="8v9c6v"
"*" * i
```

prints `i` stars.

---

# 8. Python Solution — Without Built-in Methods

Now we explicitly build every star.

```python id="mtj0je"
def star_triangle_manual(n):

    for i in range(1, n + 1):

        for j in range(1, i + 1):
            print("*", end="")

        print()


star_triangle_manual(5)
```

Output:

```text id="wm7e1p"
*
**
***
****
*****
```

This is the version you should understand deeply because it exposes the **nested-loop pattern**.

---

# 9. Line-by-Line Explanation

```python id="e6dx6c"
for i in range(1, n + 1):
```

Controls the rows.

If:

```text
n = 5
```

then:

```text
i = 1, 2, 3, 4, 5
```

---

```python id="2wsyj0"
for j in range(1, i + 1):
```

Controls how many stars appear in the current row.

If:

```text
i = 3
```

then:

```text
j = 1, 2, 3
```

So three stars are printed.

---

```python id="f6h21e"
print("*", end="")
```

Prints a star without moving to a new line.

---

```python id="n1d84m"
print()
```

After finishing one row, move to the next line.

---

# 10. Detailed Dry Run

For:

```text id="i9ij48"
n = 4
```

### Row 1

```text
i = 1
```

Inner loop:

```text
j = 1
```

Print:

```text
*
```

---

### Row 2

```text
i = 2
```

Inner loop:

```text
j = 1
j = 2
```

Print:

```text
**
```

---

### Row 3

```text
i = 3
```

Print:

```text
***
```

---

### Row 4

```text
i = 4
```

Print:

```text
****
```

### Dry Run Table

| Row `i` | Inner-loop values | Stars  |
| ------: | ----------------- | ------ |
|       1 | `1`               | `*`    |
|       2 | `1,2`             | `**`   |
|       3 | `1,2,3`           | `***`  |
|       4 | `1,2,3,4`         | `****` |

---

# 11. Time Complexity

Number of stars:

```text
1 + 2 + 3 + ... + n
```

This equals:

```text
n(n + 1) / 2
```

Therefore:

```text
Time = O(n²)
```

---

# 12. Space Complexity

Ignoring the output itself:

```text
Space = O(1)
```

We only use loop variables.

---

# 13. Edge Cases

### `n = 1`

```text
*
```

### `n = 0`

Nothing should be printed.

### Negative `n`

Usually treat as invalid input or print nothing.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```python
range(n)
```

without understanding that it gives:

```text
0 → n-1
```

For pattern printing, both styles can work, but the relationship becomes less intuitive.

---

### ❌ Mistake 2

Using:

```python
print("*")
```

inside the inner loop.

That produces:

```text
*
*
*
*
```

instead of:

```text
****
```

We need:

```python
print("*", end="")
```

---

### ❌ Mistake 3

Forgetting:

```python
print()
```

after each row.

Then everything appears on one line.

---

# 15. Pattern Recognition

## 🔥 When you see:

> Increasing number of stars per row

Think:

```text
Row i
↓
i stars
```

Template:

```python
for i in range(1, n + 1):
    for j in range(1, i + 1):
        print("*", end="")
    print()
```

### Master trigger

```text
1
12
123
1234
```

or

```text
*
**
***
****
```

→ **Inner loop depends on row number.**

---

# 🔵 PROBLEM 2 — INVERTED STAR TRIANGLE

## 1. Problem Statement

Print stars in decreasing order.

For:

```text
n = 5
```

Output:

```text
*****
****
***
**
*
```

---

# 2. Problem Theory

Compare Problem 1:

```text
1
2
3
4
5
```

Now we need:

```text
5
4
3
2
1
```

So the number of stars decreases by one every row.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

> **Reverse row control**

Instead of:

```text
1 → n
```

we need:

```text
n → 1
```

---

# 4. ELI10 Intuition

Imagine removing one block from a staircase every time.

Start:

```text
*****
```

Remove one:

```text
****
```

Remove one:

```text
***
```

And continue.

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
****
***
**
*
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Start with `n` stars.

### Step 2

Print them.

### Step 3

Decrease the number of stars by one.

### Step 4

Continue until one star remains.

Pseudocode:

```text
for row = n down to 1:
    print row stars
```

---

# 7. Python Solution — Using Built-in Methods

```python id="3zq4su"
def inverted_star_triangle(n):

    for i in range(n, 0, -1):
        print("*" * i)


inverted_star_triangle(5)
```

Output:

```text id="h0g1d7"
*****
****
***
**
*
```

---

# 8. Python Solution — Without Built-in Methods

```python id="c8yr29"
def inverted_star_triangle_manual(n):

    for i in range(n, 0, -1):

        for j in range(1, i + 1):
            print("*", end="")

        print()


inverted_star_triangle_manual(5)
```

---

# 9. Line-by-Line Explanation

```python id="o2q0sl"
for i in range(n, 0, -1):
```

Means:

```text
n, n-1, n-2, ..., 1
```

For `n = 5`:

```text
5 → 4 → 3 → 2 → 1
```

Then:

```python id="80os9g"
for j in range(1, i + 1):
```

prints `i` stars.

---

# 10. Detailed Dry Run

For `n = 5`:

| Row | `i` | Stars   |
| --: | --: | ------- |
|   1 |   5 | `*****` |
|   2 |   4 | `****`  |
|   3 |   3 | `***`   |
|   4 |   2 | `**`    |
|   5 |   1 | `*`     |

Final:

```text
*****
****
***
**
*
```

---

# 11. Time Complexity

Total stars:

```text
n + (n-1) + ... + 1
```

Therefore:

```text
O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

```text
n = 1
```

Output:

```text
*
```

```text
n = 0
```

Output:

```text
nothing
```

---

# 14. Common Mistakes / Traps

### ❌ Wrong direction

```python
range(1, n + 1)
```

produces increasing rows.

We need:

```python
range(n, 0, -1)
```

---

# 15. Pattern Recognition

```text
*****
****
***
**
*
```

Immediately think:

```text
Row size decreases
↓
n → 1
↓
reverse outer loop
```

---

# 🔵 PROBLEM 3 — NUMBER TRIANGLE

## 1. Problem Statement

Print:

```text
1
12
123
1234
12345
```

For `n = 5`.

---

# 2. Problem Theory

Now the shape is exactly like Problem 1.

The difference:

```text
Problem 1 → "*"
Problem 3 → numbers
```

For row `i`, print:

```text
1 2 3 ... i
```

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

```text
Outer loop
→ rows

Inner loop
→ values from 1 to row number
```

---

# 4. ELI10 Intuition

Imagine each row is counting from one.

Row 1:

```text
1
```

Row 2:

```text
1 2
```

Row 3:

```text
1 2 3
```

The row number tells us where counting stops.

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
1
12
123
1234
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Loop through rows:

```text
1 → n
```

### Step 2

For row `i`, loop:

```text
1 → i
```

### Step 3

Print each number.

### Step 4

Move to the next row.

---

# 7. Python Solution — Using Built-in Methods

A simple Python approach:

```python id="ytj3uf"
def number_triangle(n):

    for i in range(1, n + 1):
        print("".join(str(j) for j in range(1, i + 1)))


number_triangle(5)
```

Output:

```text
1
12
123
1234
12345
```

---

# 8. Python Solution — Without Built-in Methods

For fundamentals, use nested loops:

```python id="9p8qkt"
def number_triangle_manual(n):

    for i in range(1, n + 1):

        for j in range(1, i + 1):
            print(j, end="")

        print()


number_triangle_manual(5)
```

---

# 9. Line-by-Line Explanation

Outer loop:

```python id="d8m9ad"
for i in range(1, n + 1):
```

Controls the row.

Inner loop:

```python id="crj4mz"
for j in range(1, i + 1):
```

Controls the numbers printed in that row.

If:

```text
i = 4
```

then:

```text
j = 1, 2, 3, 4
```

So:

```text
1234
```

---

# 10. Detailed Dry Run

For `n = 4`:

| Row | `i` | `j` values | Output |
| --: | --: | ---------- | ------ |
|   1 |   1 | `1`        | `1`    |
|   2 |   2 | `1,2`      | `12`   |
|   3 |   3 | `1,2,3`    | `123`  |
|   4 |   4 | `1,2,3,4`  | `1234` |

---

# 11. Time Complexity

Number of printed values:

```text
1 + 2 + ... + n
```

Therefore:

```text
O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

`n = 1`:

```text
1
```

`n = 0`:

```text
nothing
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake

Printing `i` instead of `j`.

Wrong:

```python
print(i, end="")
```

That creates:

```text
1
22
333
4444
```

That's actually our **next pattern**.

For this problem we need:

```python
print(j, end="")
```

---

# 15. Pattern Recognition

When you see:

```text
1
12
123
1234
```

Think:

```text
Row i
↓
print j from 1 → i
```

---

# 🔵 PROBLEM 4 — REPEATED NUMBER TRIANGLE

## 1. Problem Statement

Print:

```text
1
22
333
4444
55555
```

For `n = 5`.

---

# 2. Problem Theory

This looks similar to Problem 3.

But there is one critical difference.

### Problem 3

```text
1
12
123
1234
```

The **column number changes**.

### Problem 4

```text
1
22
333
4444
```

The **row number stays fixed throughout that row**.

That distinction is extremely important.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

> **Same value repeated according to row number.**

For row `i`:

```text
print i exactly i times
```

---

# 4. ELI10 Intuition

Think of each row as having its own number.

Row 1 owns:

```text
1
```

Row 2 owns:

```text
22
```

Row 3 owns:

```text
333
```

Row 4 owns:

```text
4444
```

So:

```text
row number = printed value = repetition count
```

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
1
22
333
4444
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Loop from row `1` to `n`.

### Step 2

For each row `i`, run an inner loop `i` times.

### Step 3

Print `i`, not `j`.

### Step 4

Move to the next line.

Pseudocode:

```text
for i = 1 to n:
    for j = 1 to i:
        print i
    new line
```

---

# 7. Python Solution — Using Built-in Methods

```python id="7t6xg0"
def repeated_number_triangle(n):

    for i in range(1, n + 1):
        print(str(i) * i)


repeated_number_triangle(5)
```

Output:

```text
1
22
333
4444
55555
```

---

# 8. Python Solution — Without Built-in Methods

```python id="b6f9zq"
def repeated_number_triangle_manual(n):

    for i in range(1, n + 1):

        for j in range(1, i + 1):
            print(i, end="")

        print()


repeated_number_triangle_manual(5)
```

---

# 9. Line-by-Line Explanation

```python id="dshg0u"
for i in range(1, n + 1):
```

Controls the row.

For:

```text
n = 5
```

we get:

```text
1, 2, 3, 4, 5
```

Then:

```python id="8f8e88"
for j in range(1, i + 1):
```

controls how many times the number is printed.

But notice:

```python id="zk2mnj"
print(i, end="")
```

We print **`i`**.

Not `j`.

---

# 10. Detailed Dry Run

For `n = 4`:

### Row 1

```text
i = 1
j = 1
```

Output:

```text
1
```

### Row 2

```text
i = 2
j = 1,2
```

Output:

```text
22
```

### Row 3

```text
i = 3
j = 1,2,3
```

Output:

```text
333
```

### Row 4

```text
i = 4
j = 1,2,3,4
```

Output:

```text
4444
```

### Dry Run Table

| Row | `i` | Number printed | Repetitions | Output |
| --: | --: | -------------: | ----------: | ------ |
|   1 |   1 |              1 |           1 | `1`    |
|   2 |   2 |              2 |           2 | `22`   |
|   3 |   3 |              3 |           3 | `333`  |
|   4 |   4 |              4 |           4 | `4444` |

---

# 11. Time Complexity

Total printed numbers:

```text
1 + 2 + ... + n
```

Therefore:

```text
O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

### `n = 1`

```text
1
```

### `n = 0`

Nothing.

### Large `n`

The algorithm remains conceptually simple, but output itself becomes large.

---

# 14. Common Mistakes / Traps

## 🔴 Most important mistake

Confusing `i` and `j`.

### `j` changes inside the row:

```text
1,2,3,4...
```

### `i` stays fixed during the row:

```text
4,4,4,4
```

Therefore:

```text
1234 pattern
→ print j

4444 pattern
→ print i
```

---

# 15. Pattern Recognition

When you see:

```text
1
22
333
4444
55555
```

Think:

```text
Row i
↓
print i
↓
i times
```

---

# 🧠 CONVERSATION 1 — PATTERN PRINTING MASTER MAP

We have now established the four fundamental patterns:

### Pattern 1 — Increasing Stars

```text
*
**
***
****
```

```text
row i → i stars
```

---

### Pattern 2 — Decreasing Stars

```text
****
***
**
*
```

```text
row i → decreasing count
```

---

### Pattern 3 — Increasing Numbers

```text
1
12
123
1234
```

```text
row i → print j
```

---

### Pattern 4 — Repeated Row Number

```text
1
22
333
4444
```

```text
row i → print i
```

---

# 🔥 THE MOST IMPORTANT PATTERN-PRINTING RULE

Before writing code, **never immediately start coding**.

First make this table:

```text
Rows?
Columns?
What gets printed?
Does it increase/decrease?
Does value depend on row or column?
Are spaces involved?
```

For example:

```text
1
22
333
4444
```

becomes:

```text
Rows       → n
Columns    → i
Value      → i
Direction  → increasing
```

Then coding becomes almost mechanical.

---

# 🧠 PATTERN PRINTING MASTER FORMULA

Almost every basic pattern starts with:

```python
for i in range(...):          # ROWS

    for j in range(...):      # COLUMNS

        print(..., end="")

    print()
```

The **real problem** is not the nested loops.

The real problem is determining:

```text
1. Outer loop range
2. Inner loop range
3. What to print
```

That is the pattern-recognition skill TopGun is actually testing.

Would you like to continue with Problems 5–8 next, or try a short pattern-recognition quiz first?


# 🟦 PATTERN PRINTING — CONVERSATION 2

## Problems 5–8

### Continuing the locked TopGun execution version

We completed:

```text
PATTERN PRINTING
1. Right-Angled Star Triangle       ✅
2. Inverted Star Triangle           ✅
3. Number Triangle                  ✅
4. Repeated Number Triangle        ✅
```

Now:

```text
5. Inverted Number Triangle
6. Pyramid
7. Inverted Pyramid
8. Number Pyramid
```

---

# 🔵 PROBLEM 5 — INVERTED NUMBER TRIANGLE

## 1. Problem Statement

Given `n`, print numbers in decreasing row length.

For:

```text
n = 5
```

Output:

```text
12345
1234
123
12
1
```

---

# 2. Problem Theory

This combines two ideas we already learned:

### Problem 3

```text
1
12
123
1234
12345
```

The row length increases.

### Problem 5

```text
12345
1234
123
12
1
```

The row length decreases.

The **values themselves still start from 1**.

So for row `i`:

```text
print 1 → i
```

but `i` decreases from `n` to `1`.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

```text
Reverse outer-loop control
+
Increasing inner values
```

The outer loop:

```text
n → 1
```

The inner loop:

```text
1 → i
```

---

# 4. ELI10 Intuition

Imagine writing:

```text
12345
```

Then erase the last number:

```text
1234
```

Erase again:

```text
123
```

Then:

```text
12
```

Then:

```text
1
```

So every row loses one number.

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
1234
123
12
1
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Start from `n`.

### Step 2

For each row, print numbers from `1` to current row length.

### Step 3

Decrease the row length by `1`.

### Step 4

Continue until row length becomes `1`.

### Pseudocode

```text
for i = n down to 1:
    for j = 1 to i:
        print j
    new line
```

---

# 7. Python Solution — Using Built-in Methods

```python
def inverted_number_triangle(n):

    for i in range(n, 0, -1):
        print("".join(str(j) for j in range(1, i + 1)))


inverted_number_triangle(5)
```

Output:

```text
12345
1234
123
12
1
```

---

# 8. Python Solution — Without Built-in Methods

```python
def inverted_number_triangle_manual(n):

    for i in range(n, 0, -1):

        for j in range(1, i + 1):
            print(j, end="")

        print()


inverted_number_triangle_manual(5)
```

---

# 9. Line-by-Line Explanation

```python
for i in range(n, 0, -1):
```

For `n = 5`:

```text
5 → 4 → 3 → 2 → 1
```

Then:

```python
for j in range(1, i + 1):
```

If `i = 4`:

```text
j = 1,2,3,4
```

Therefore:

```text
1234
```

Notice the important distinction:

```text
i → controls HOW MANY numbers
j → controls WHICH number
```

---

# 10. Detailed Dry Run

For `n = 4`:

| Row | `i` | `j` values | Output |
| --: | --: | ---------- | ------ |
|   1 |   4 | `1,2,3,4`  | `1234` |
|   2 |   3 | `1,2,3`    | `123`  |
|   3 |   2 | `1,2`      | `12`   |
|   4 |   1 | `1`        | `1`    |

Final:

```text
1234
123
12
1
```

---

# 11. Time Complexity

Total numbers printed:

```text
n + (n-1) + ... + 1
```

Therefore:

```text
O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

### `n = 1`

```text
1
```

### `n = 0`

Nothing is printed.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```python
range(1, n + 1)
```

for the outer loop.

That creates an increasing pattern.

We need:

```python
range(n, 0, -1)
```

---

### ❌ Mistake 2

Printing `i` instead of `j`.

Wrong:

```text
4444
333
22
1
```

Correct:

```text
1234
123
12
1
```

---

# 15. Pattern Recognition

When you see:

```text
12345
1234
123
12
1
```

Think:

```text
Outer → n → 1
Inner → 1 → i
Print → j
```

---

# 🔵 PROBLEM 6 — PYRAMID

## 1. Problem Statement

Print a centered pyramid of stars.

For:

```text
n = 5
```

Output:

```text
    *
   ***
  *****
 *******
*********
```

---

# 2. Problem Theory

This is the first pattern where **spaces become important**.

A pyramid has two components:

```text
SPACES + STARS
```

For each row:

```text
Spaces decrease
Stars increase
```

Specifically:

```text
Row 1 → 4 spaces + 1 star
Row 2 → 3 spaces + 3 stars
Row 3 → 2 spaces + 5 stars
Row 4 → 1 space  + 7 stars
Row 5 → 0 spaces + 9 stars
```

The number of stars follows:

```text
2 × row - 1
```

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

> **Spaces + odd number of stars**

For row `i`:

```text
spaces = n - i
stars  = 2*i - 1
```

This formula is extremely important.

---

# 4. ELI10 Intuition

Imagine putting stars in the middle.

First row:

```text
    *
```

To keep the star centered, we need spaces before it.

Next row:

```text
   ***
```

We reduce one space and add two stars.

Next:

```text
  *****
```

Again:

```text
spaces ↓
stars  ↑
```

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
   *
  ***
 *****
*******
```

---

# 6. Algorithm — Step-by-Step

For each row `i` from `1` to `n`:

### Step 1

Calculate spaces:

```text
n - i
```

### Step 2

Calculate stars:

```text
2*i - 1
```

### Step 3

Print spaces.

### Step 4

Print stars.

### Step 5

Move to next row.

### Pseudocode

```text
for i = 1 to n:

    spaces = n - i
    stars = 2*i - 1

    print spaces
    print stars

    new line
```

---

# 7. Python Solution — Using Built-in Methods

```python
def pyramid(n):

    for i in range(1, n + 1):

        spaces = n - i
        stars = 2 * i - 1

        print(" " * spaces + "*" * stars)


pyramid(5)
```

Output:

```text
    *
   ***
  *****
 *******
*********
```

---

# 8. Python Solution — Without Built-in Methods

```python
def pyramid_manual(n):

    for i in range(1, n + 1):

        spaces = n - i
        stars = 2 * i - 1

        for j in range(spaces):
            print(" ", end="")

        for j in range(stars):
            print("*", end="")

        print()


pyramid_manual(5)
```

---

# 9. Line-by-Line Explanation

```python
for i in range(1, n + 1):
```

Controls rows.

---

```python
spaces = n - i
```

For `n = 5`:

```text
i = 1 → 4 spaces
i = 2 → 3 spaces
i = 3 → 2 spaces
i = 4 → 1 space
i = 5 → 0 spaces
```

So:

```text
spaces decrease by 1
```

---

```python
stars = 2 * i - 1
```

For each row:

```text
i = 1 → 1
i = 2 → 3
i = 3 → 5
i = 4 → 7
i = 5 → 9
```

These are consecutive odd numbers.

---

# 10. Detailed Dry Run

For `n = 5`:

| Row `i` | Spaces `n-i` | Stars `2i-1` | Output      |
| ------: | -----------: | -----------: | ----------- |
|       1 |            4 |            1 | `    *`     |
|       2 |            3 |            3 | `   ***`    |
|       3 |            2 |            5 | `  *****`   |
|       4 |            1 |            7 | ` *******`  |
|       5 |            0 |            9 | `*********` |

---

# 11. Time Complexity

There are approximately:

```text
O(n²)
```

characters printed overall.

Therefore:

```text
Time = O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

### `n = 1`

```text
*
```

### `n = 0`

Nothing.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Forgetting spaces

Without spaces:

```text
*
***
*****
*******
```

That's not a centered pyramid.

---

### ❌ Mistake 2 — Using `i` stars

If you use:

```text
stars = i
```

you get:

```text
    *
   **
  ***
 ****
```

That's a different pattern.

---

### ❌ Mistake 3 — Wrong star formula

Remember:

```text
1, 3, 5, 7, 9...
```

Therefore:

```text
2*i - 1
```

---

# 15. Pattern Recognition

When you see:

```text
    *
   ***
  *****
 *******
```

Immediately think:

```text
PYRAMID
↓
spaces = n - i
stars = 2*i - 1
```

### 🔥 Master trigger

```text
Centered
+
Stars grow by 2
+
Spaces shrink by 1
```

→ **Pyramid**

---

# 🔵 PROBLEM 7 — INVERTED PYRAMID

## 1. Problem Statement

Print a centered inverted pyramid.

For:

```text
n = 5
```

Output:

```text
*********
 *******
  *****
   ***
    *
```

---

# 2. Problem Theory

This is the reverse of Problem 6.

Normal pyramid:

```text
1 star
3 stars
5 stars
7 stars
9 stars
```

Inverted pyramid:

```text
9 stars
7 stars
5 stars
3 stars
1 star
```

Spaces do the opposite:

```text
0
1
2
3
4
```

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

```text
Stars decrease by 2
Spaces increase by 1
```

For row `i`:

```text
spaces = i - 1
stars = 2*n - 2*i + 1
```

Equivalent:

```text
stars = 2 * (n - i) + 1
```

---

# 4. ELI10 Intuition

Take the normal pyramid and turn it upside down.

Start wide:

```text
*********
```

Then shrink:

```text
*******
```

Then:

```text
*****
```

Eventually:

```text
*
```

At the same time, spaces move the stars toward the right.

---

# 5. Example

For `n = 4`:

```text
*******
 *****
  ***
   *
```

---

# 6. Algorithm — Step-by-Step

For each row `i` from `1` to `n`:

### Step 1

Calculate spaces:

```text
i - 1
```

### Step 2

Calculate stars:

```text
2*n - 2*i + 1
```

### Step 3

Print spaces.

### Step 4

Print stars.

### Step 5

Move to next row.

---

# 7. Python Solution — Using Built-in Methods

```python
def inverted_pyramid(n):

    for i in range(1, n + 1):

        spaces = i - 1
        stars = 2 * n - 2 * i + 1

        print(" " * spaces + "*" * stars)


inverted_pyramid(5)
```

Output:

```text
*********
 *******
  *****
   ***
    *
```

---

# 8. Python Solution — Without Built-in Methods

```python
def inverted_pyramid_manual(n):

    for i in range(1, n + 1):

        spaces = i - 1
        stars = 2 * n - 2 * i + 1

        for j in range(spaces):
            print(" ", end="")

        for j in range(stars):
            print("*", end="")

        print()


inverted_pyramid_manual(5)
```

---

# 9. Line-by-Line Explanation

```python
spaces = i - 1
```

For `n = 5`:

```text
0
1
2
3
4
```

Spaces increase.

---

```python
stars = 2 * n - 2 * i + 1
```

For `n = 5`:

```text
i = 1 → 9
i = 2 → 7
i = 3 → 5
i = 4 → 3
i = 5 → 1
```

Stars decrease by 2.

---

# 10. Detailed Dry Run

| Row | `i` | Spaces | Stars | Output      |
| --: | --: | -----: | ----: | ----------- |
|   1 |   1 |      0 |     9 | `*********` |
|   2 |   2 |      1 |     7 | ` *******`  |
|   3 |   3 |      2 |     5 | `  *****`   |
|   4 |   4 |      3 |     3 | `   ***`    |
|   5 |   5 |      4 |     1 | `    *`     |

---

# 11. Time Complexity

Total output is quadratic:

```text
O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

### `n = 1`

```text
*
```

### `n = 0`

Nothing.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```text
spaces = n - i
```

That's for the normal pyramid.

Here:

```text
spaces = i - 1
```

---

### ❌ Mistake 2

Using:

```text
stars = 2*i - 1
```

That increases stars.

For inverted pyramid we need:

```text
stars = 2*n - 2*i + 1
```

---

# 15. Pattern Recognition

When you see:

```text
*********
 *******
  *****
   ***
    *
```

Think:

```text
INVERTED PYRAMID

spaces ↑
stars  ↓ by 2
```

Template:

```text
spaces = i - 1
stars = 2*n - 2*i + 1
```

---

# 🔵 PROBLEM 8 — NUMBER PYRAMID

## 1. Problem Statement

Print a centered pyramid containing numbers.

For:

```text
n = 5
```

Output:

```text
    1
   123
  12345
 1234567
123456789
```

---

# 2. Problem Theory

This combines two previous patterns:

### From Problem 3

Increasing numbers:

```text
1
123
12345
```

### From Problem 6

Centered pyramid:

```text
    *
   ***
  *****
```

So now:

```text
spaces + increasing numbers
```

The number of values is:

```text
2*i - 1
```

and values are:

```text
1 → 2*i-1
```

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

```text
Centered pattern
+
Odd number of values
+
Sequential numbers
```

For row `i`:

```text
spaces = n - i
values = 2*i - 1
```

---

# 4. ELI10 Intuition

Think of a normal pyramid:

```text
    *
   ***
  *****
```

Now replace:

```text
*
```

with numbers:

```text
1
```

and:

```text
***
```

with:

```text
123
```

and:

```text
*****
```

with:

```text
12345
```

So:

```text
    1
   123
  12345
```

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
   1
  123
 12345
1234567
```

---

# 6. Algorithm — Step-by-Step

For every row `i`:

### Step 1

Calculate spaces:

```text
n - i
```

### Step 2

Calculate number of values:

```text
2*i - 1
```

### Step 3

Print the spaces.

### Step 4

Print numbers:

```text
1 → 2*i - 1
```

### Step 5

Move to next line.

---

# 7. Python Solution — Using Built-in Methods

```python
def number_pyramid(n):

    for i in range(1, n + 1):

        spaces = n - i
        count = 2 * i - 1

        numbers = ""

        for j in range(1, count + 1):
            numbers += str(j)

        print(" " * spaces + numbers)


number_pyramid(5)
```

Output:

```text
    1
   123
  12345
 1234567
123456789
```

---

# 8. Python Solution — Without Built-in Convenience

```python
def number_pyramid_manual(n):

    for i in range(1, n + 1):

        spaces = n - i
        count = 2 * i - 1

        for j in range(spaces):
            print(" ", end="")

        for j in range(1, count + 1):
            print(j, end="")

        print()


number_pyramid_manual(5)
```

---

# 9. Line-by-Line Explanation

```python
spaces = n - i
```

Centers the row.

For `n = 5`:

```text
4
3
2
1
0
```

---

```python
count = 2 * i - 1
```

Number of values:

```text
1
3
5
7
9
```

---

```python
for j in range(1, count + 1):
```

Print:

```text
1 → count
```

For row 3:

```text
count = 5
```

So:

```text
12345
```

---

# 10. Detailed Dry Run

For `n = 4`:

| Row | Spaces | Count | Numbers   | Output    |
| --: | -----: | ----: | --------- | --------- |
|   1 |      3 |     1 | `1`       | `   1`    |
|   2 |      2 |     3 | `123`     | `  123`   |
|   3 |      1 |     5 | `12345`   | ` 12345`  |
|   4 |      0 |     7 | `1234567` | `1234567` |

---

# 11. Time Complexity

The total number of printed characters is quadratic:

```text
O(n²)
```

---

# 12. Space Complexity

The manual printing version uses:

```text
O(1)
```

auxiliary space, ignoring output.

The first version temporarily constructs a row string, which can take `O(n)` space for that row.

For basic screening, remember:

```text
Time → O(n²)
Auxiliary space → O(1)
```

for the direct-print version.

---

# 13. Edge Cases

### `n = 1`

```text
1
```

### `n = 0`

Nothing.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Forgetting spaces

Then:

```text
1
123
12345
```

is not centered.

---

### ❌ Mistake 2 — Printing only `i` numbers

If you use:

```python
range(1, i + 1)
```

you get:

```text
   1
  12
 123
1234
```

That's not the required number pyramid.

We need:

```python
range(1, 2 * i)
```

---

### ❌ Mistake 3 — Confusing star pyramid with number pyramid

Star pyramid:

```text
    *
   ***
```

Number pyramid:

```text
    1
   123
```

The **shape formula is the same**:

```text
spaces = n - i
count = 2*i - 1
```

Only the printed content changes.

---

# 15. Pattern Recognition

When you see:

```text
    1
   123
  12345
 1234567
```

Think:

```text
NUMBER PYRAMID
↓
spaces = n - i
↓
odd count = 2*i - 1
↓
print 1 → count
```

---

# 🧠 CONVERSATION 2 — MASTER PATTERN MAP

We now have eight patterns.

|  # | Pattern                  | Key Formula / Rule            |
| -: | ------------------------ | ----------------------------- |
|  1 | Right Star Triangle      | `stars = i`                   |
|  2 | Inverted Star Triangle   | `stars = i`, `i ↓`            |
|  3 | Number Triangle          | `print j`, `j = 1 → i`        |
|  4 | Repeated Number Triangle | `print i`, `i times`          |
|  5 | Inverted Number Triangle | `i ↓`, print `j`              |
|  6 | Pyramid                  | `spaces=n-i`, `stars=2i-1`    |
|  7 | Inverted Pyramid         | `spaces=i-1`, `stars=2n-2i+1` |
|  8 | Number Pyramid           | `spaces=n-i`, `count=2i-1`    |

---

# 🔥 PATTERN PRINTING FORMULA SHEET

## Type 1 — Increasing Triangle

```text
*
**
***
****
```

Think:

```text
row i → i items
```

---

## Type 2 — Decreasing Triangle

```text
****
***
**
*
```

Think:

```text
row size → n → 1
```

---

## Type 3 — Row Number

```text
1
22
333
4444
```

Think:

```text
print i
repeat i times
```

---

## Type 4 — Column Number

```text
1
12
123
1234
```

Think:

```text
print j
j = 1 → i
```

---

## Type 5 — Pyramid

```text
    *
   ***
  *****
```

Think:

```text
spaces = n-i
items = 2i-1
```

---

## Type 6 — Inverted Pyramid

```text
*******
 *****
  ***
   *
```

Think:

```text
spaces = i-1
items = 2n-2i+1
```

---

# 🧠 THE GOLDEN PATTERN-PRINTING QUESTIONS

Before solving **any** pattern, ask these five questions:

### 1. How many rows?

Usually:

```python
for i in range(1, n + 1):
```

---

### 2. How many things in each row?

Look for:

```text
i
n-i
2i-1
2n-2i+1
```

---

### 3. What is printed?

Is it:

```text
*
i
j
spaces
number sequence
```

---

### 4. Does the row grow or shrink?

```text
Grow → i
Shrink → n-i / reverse loop
```

---

### 5. Are spaces required?

If the pattern is centered:

```text
spaces are probably required
```

---

# 🚨 TOPGUN SCREENING TRAPS

These are the mistakes most likely to cost easy pattern-printing questions.

### Trap 1

Confusing:

```text
i = row
j = column
```

Remember:

```text
i → WHERE AM I? → row
j → WHAT POSITION? → column
```

---

### Trap 2

Confusing `i` and `j`.

```text
1234
```

usually means:

```python
print(j)
```

while:

```text
4444
```

means:

```python
print(i)
```

---

### Trap 3

Forgetting `end=""`

```python
print("*")
```

moves to the next line.

```python
print("*", end="")
```

stays on the same row.

---

### Trap 4

Forgetting the final:

```python
print()
```

after completing a row.

---

### Trap 5

Not calculating the formula first.

For pyramids, don't guess.

Memorize:

```text
Normal Pyramid:
spaces = n-i
stars  = 2i-1

Inverted Pyramid:
spaces = i-1
stars  = 2n-2i+1
```

---

# 🟢 CURRENT PATTERN PRINTING PROGRESS

```text
PATTERN PRINTING

Problem 1  Right Star Triangle       ✅
Problem 2  Inverted Star Triangle   ✅
Problem 3  Number Triangle          ✅
Problem 4  Repeated Number Triangle ✅

Problem 5  Inverted Number Triangle ✅
Problem 6  Pyramid                  ✅
Problem 7  Inverted Pyramid         ✅
Problem 8  Number Pyramid           ✅

Progress: 8/10
```

Next locked sequence:

```text
Conversation 3
├── Problem 9 — Floyd's Triangle
├── Problem 10 — Hollow Square / Rectangle
├── Pattern Printing Mastery
├── Complete Pattern Recognition Map
├── Master Templates
├── TopGun Traps
└── Mini Test
```

After that, **Pattern Printing becomes 10/10 complete**, and your overall locked basic-DSA problem count moves from **70/70 to 80/80**.

Would you like to continue with Problems 9–10 and finish the pattern-printing section?
# 🟦 PATTERN PRINTING — CONVERSATION 3

## Problems 9–10 + Complete Pattern Printing Mastery

We continue exactly from **8/10**.

```text
1. Right-Angled Star Triangle       ✅
2. Inverted Star Triangle           ✅
3. Number Triangle                  ✅
4. Repeated Number Triangle         ✅
5. Inverted Number Triangle         ✅
6. Pyramid                          ✅
7. Inverted Pyramid                 ✅
8. Number Pyramid                   ✅
9. Floyd's Triangle                 🔵
10. Hollow Square / Rectangle       🔵
```

---

# 🔵 PROBLEM 9 — FLOYD'S TRIANGLE

## 1. Problem Statement

Print **Floyd's Triangle**.

For `n = 5`:

```text
1
23
456
78910
1112131415
```

The numbers are **continuous** across rows.

---

# 2. Problem Theory

This problem looks similar to the number triangle:

```text
1
12
123
1234
```

But there is one major difference.

### Number Triangle

Every row starts again from `1`:

```text
1
12
123
1234
```

### Floyd's Triangle

The number **continues from where the previous row stopped**:

```text
1
23
456
789
101112131415
```

Therefore, we need an additional variable:

```text
number
```

that keeps increasing.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

> **Nested loops + running counter**

The key idea:

```text
number = 1

print number
number += 1
```

The number does **not reset** after each row.

---

# 4. ELI10 Intuition

Imagine counting normally:

```text
1 2 3 4 5 6 7 8 9 10 11 12...
```

But instead of writing them in one line, we put them into rows.

First row gets:

```text
1 number
```

Second row gets:

```text
2 numbers
```

Third row gets:

```text
3 numbers
```

Fourth row gets:

```text
4 numbers
```

So:

```text
Row 1 → 1
Row 2 → 2,3
Row 3 → 4,5,6
Row 4 → 7,8,9,10
```

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
1
23
456
78910
```

Notice:

```text
1
↓
2 3
↓
4 5 6
↓
7 8 9 10
```

The counter never resets.

---

# 6. Algorithm — Step-by-Step

### Step 1

Create:

```python
number = 1
```

### Step 2

Loop through rows:

```text
1 → n
```

### Step 3

For row `i`, print exactly `i` numbers.

### Step 4

Print the current `number`.

### Step 5

Increase `number`:

```python
number += 1
```

### Step 6

Move to the next row.

### Pseudocode

```text
number = 1

for i = 1 to n:

    for j = 1 to i:

        print number

        number = number + 1

    new line
```

---

# 7. Python Solution — Using Built-in Methods

```python
def floyd_triangle(n):

    number = 1

    for i in range(1, n + 1):

        row = []

        for j in range(1, i + 1):
            row.append(str(number))
            number += 1

        print("".join(row))


floyd_triangle(5)
```

Output:

```text
1
23
456
78910
1112131415
```

---

# 8. Python Solution — Without Built-in Methods

For understanding the actual pattern, directly print each number:

```python
def floyd_triangle_manual(n):

    number = 1

    for i in range(1, n + 1):

        for j in range(1, i + 1):

            print(number, end="")

            number += 1

        print()


floyd_triangle_manual(5)
```

Output:

```text
1
23
456
78910
1112131415
```

This is the **core screening version**.

---

# 9. Line-by-Line Explanation

```python
number = 1
```

This is our global running counter.

It starts at `1`.

---

```python
for i in range(1, n + 1):
```

Controls rows.

For `n = 5`:

```text
i = 1,2,3,4,5
```

---

```python
for j in range(1, i + 1):
```

Controls how many numbers appear in the current row.

If:

```text
i = 3
```

then:

```text
j = 1,2,3
```

So row 3 gets three numbers.

---

```python
print(number, end="")
```

Print the current running number.

---

```python
number += 1
```

Move to the next number.

This line is the **heart of Floyd's Triangle**.

---

```python
print()
```

Move to the next row.

---

# 10. Detailed Dry Run

For:

```text
n = 4
```

Initial:

```text
number = 1
```

### Row 1

```text
i = 1
```

One iteration:

```text
print 1
number = 2
```

Output:

```text
1
```

---

### Row 2

```text
i = 2
```

Two iterations:

```text
print 2
number = 3

print 3
number = 4
```

Output:

```text
23
```

---

### Row 3

```text
i = 3
```

Three iterations:

```text
4
5
6
```

Output:

```text
456
```

---

### Row 4

```text
i = 4
```

Four iterations:

```text
7
8
9
10
```

Output:

```text
78910
```

### Dry Run Table

| Row | `i` | Numbers Printed | Next `number` |
| --: | --: | --------------- | ------------: |
|   1 |   1 | `1`             |             2 |
|   2 |   2 | `2,3`           |             4 |
|   3 |   3 | `4,5,6`         |             7 |
|   4 |   4 | `7,8,9,10`      |            11 |

Final:

```text
1
23
456
78910
```

---

# 11. Time Complexity

Total numbers printed:

```text
1 + 2 + 3 + ... + n
```

Therefore:

```text
Time = O(n²)
```

---

# 12. Space Complexity

The direct-print version uses only:

```text
number
i
j
```

Therefore:

```text
Auxiliary Space = O(1)
```

---

# 13. Edge Cases

### `n = 1`

```text
1
```

### `n = 2`

```text
1
23
```

### `n = 0`

Nothing.

---

# 14. Common Mistakes / Traps

## ❌ Mistake 1 — Resetting the counter

Wrong:

```python
for i in range(1, n + 1):
    number = 1
```

This produces:

```text
1
12
123
1234
```

That's not Floyd's Triangle.

The counter must be initialized **before** the outer loop:

```python
number = 1

for i in range(...):
```

---

## ❌ Mistake 2 — Forgetting increment

If you don't do:

```python
number += 1
```

you get:

```text
1
11
111
1111
```

---

## ❌ Mistake 3 — Using `i` as the number

```python
print(i)
```

produces:

```text
1
22
333
4444
```

That's the repeated-number triangle.

---

# 15. Pattern Recognition

When you see:

```text
1
23
456
78910
```

Immediately think:

```text
FLOYD'S TRIANGLE
↓
nested loops
+
running counter
```

### Master trigger

```text
Numbers continue across rows
↓
Create counter OUTSIDE outer loop
↓
Increment after every print
```

---

# 🔵 PROBLEM 10 — HOLLOW SQUARE / RECTANGLE

## 1. Problem Statement

Print a hollow square.

For:

```text
n = 5
```

Output:

```text
*****
*   *
*   *
*   *
*****
```

Only the **boundary** contains stars.

The inside is empty.

---

# 2. Problem Theory

This is a different pattern from the previous triangles.

Instead of asking:

> How many stars should I print?

we ask:

> **Is this position on the boundary?**

For a square of size `n`:

```text
Top row       → all stars
Bottom row    → all stars
Left column   → stars
Right column  → stars
Inside        → spaces
```

This is a **boundary-condition pattern**.

---

# 3. Pattern Being Tested

### 🔥 Core Pattern

> **Boundary detection using row and column indices**

For position `(i, j)`:

Print `*` if:

```text
i == 0
OR
i == n-1
OR
j == 0
OR
j == n-1
```

Otherwise:

```text
print space
```

---

# 4. ELI10 Intuition

Imagine a square room.

You want to draw only its walls:

```text
*****
*   *
*   *
*   *
*****
```

The walls are:

```text
top
bottom
left
right
```

Everything inside stays empty.

---

# 5. Example

For:

```text
n = 4
```

Output:

```text
****
*  *
*  *
****
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Loop through every row:

```text
0 → n-1
```

### Step 2

Loop through every column:

```text
0 → n-1
```

### Step 3

Check whether the current position is on the boundary.

Boundary condition:

```text
i == 0
OR
i == n-1
OR
j == 0
OR
j == n-1
```

### Step 4

If boundary:

```text
print "*"
```

Otherwise:

```text
print " "
```

### Step 5

After each row:

```text
new line
```

---

# 7. Python Solution — Using Built-in Methods

```python
def hollow_square(n):

    for i in range(n):

        if i == 0 or i == n - 1:
            print("*" * n)

        else:
            print("*" + " " * (n - 2) + "*")


hollow_square(5)
```

Output:

```text
*****
*   *
*   *
*   *
*****
```

---

# 8. Python Solution — Without Built-in Methods

This version is much more important for understanding the pattern.

```python
def hollow_square_manual(n):

    for i in range(n):

        for j in range(n):

            if i == 0 or i == n - 1 or j == 0 or j == n - 1:
                print("*", end="")
            else:
                print(" ", end="")

        print()


hollow_square_manual(5)
```

Output:

```text
*****
*   *
*   *
*   *
*****
```

---

# 9. Line-by-Line Explanation

```python
for i in range(n):
```

Controls rows.

For `n = 5`:

```text
0,1,2,3,4
```

---

```python
for j in range(n):
```

Controls columns.

Each row has:

```text
5 columns
```

---

Now the key:

```python
if i == 0
```

This means:

> We are on the first/top row.

So print `*`.

---

```python
or i == n - 1
```

This means:

> We are on the last/bottom row.

Print `*`.

---

```python
or j == 0
```

This means:

> We are on the first/left column.

Print `*`.

---

```python
or j == n - 1
```

This means:

> We are on the last/right column.

Print `*`.

---

Otherwise:

```python
print(" ", end="")
```

We are inside the square.

Therefore print a space.

---

# 10. Detailed Dry Run

For:

```text
n = 5
```

Coordinates:

```text
       columns
       0 1 2 3 4

row 0  * * * * *
row 1  *       *
row 2  *       *
row 3  *       *
row 4  * * * * *
```

### Row 0

`i = 0`

Since:

```text
i == 0
```

every position is a boundary.

Output:

```text
*****
```

---

### Row 1

`i = 1`

Columns:

```text
j = 0 → boundary → *
j = 1 → inside → space
j = 2 → inside → space
j = 3 → inside → space
j = 4 → boundary → *
```

Output:

```text
*   *
```

---

### Row 2

Same:

```text
*   *
```

---

### Row 3

Same:

```text
*   *
```

---

### Row 4

```text
i == n-1
```

Therefore:

```text
*****
```

### Dry Run Table

| Row `i` | Boundary positions | Output  |
| ------: | ------------------ | ------- |
|       0 | Entire row         | `*****` |
|       1 | `j=0,4`            | `*   *` |
|       2 | `j=0,4`            | `*   *` |
|       3 | `j=0,4`            | `*   *` |
|       4 | Entire row         | `*****` |

---

# 11. Time Complexity

We visit every cell:

```text
n × n
```

Therefore:

```text
Time = O(n²)
```

---

# 12. Space Complexity

Ignoring output:

```text
O(1)
```

---

# 13. Edge Cases

### `n = 1`

There is only one cell.

Output:

```text
*
```

### `n = 2`

Every position is a boundary:

```text
**
**
```

### `n = 0`

Nothing.

---

# 14. Common Mistakes / Traps

## ❌ Mistake 1 — Printing stars everywhere

That creates a solid square:

```text
*****
*****
*****
*****
*****
```

But we need a hollow square.

---

## ❌ Mistake 2 — Forgetting the bottom row

If you only check:

```python
i == 0
```

the bottom border disappears.

Remember all four sides.

---

## ❌ Mistake 3 — Forgetting the right column

You need:

```python
j == n - 1
```

not only:

```python
j == 0
```

---

## ❌ Mistake 4 — Wrong index

For `n = 5`, last index is:

```text
4
```

Therefore:

```python
n - 1
```

not:

```python
n
```

---

# 15. Pattern Recognition

When you see:

```text
*****
*   *
*   *
*   *
*****
```

Immediately think:

```text
HOLLOW / BOUNDARY PATTERN
↓
nested loops
↓
boundary condition
```

Master condition:

```python
if (
    i == 0
    or i == n - 1
    or j == 0
    or j == n - 1
):
```

→ print `*`

Otherwise:

→ print space.

---

# 🟣 PATTERN PRINTING — 10/10 COMPLETE

We have now completed the entire locked pattern-printing problem bank.

```text
1. Right-Angled Star Triangle       ✅
2. Inverted Star Triangle           ✅
3. Number Triangle                  ✅
4. Repeated Number Triangle         ✅
5. Inverted Number Triangle         ✅
6. Pyramid                          ✅
7. Inverted Pyramid                 ✅
8. Number Pyramid                   ✅
9. Floyd's Triangle                 ✅
10. Hollow Square / Rectangle       ✅
```

# 🧠 COMPLETE PATTERN RECOGNITION MAP

## PATTERN 1 — Increasing Star Triangle

```text
*
**
***
****
```

Think:

```text
row i → i stars
```

---

## PATTERN 2 — Inverted Star Triangle

```text
****
***
**
*
```

Think:

```text
row size → n → 1
```

---

## PATTERN 3 — Number Triangle

```text
1
12
123
1234
```

Think:

```text
print j
j = 1 → i
```

---

## PATTERN 4 — Repeated Number Triangle

```text
1
22
333
4444
```

Think:

```text
print i
repeat i times
```

---

## PATTERN 5 — Inverted Number Triangle

```text
1234
123
12
1
```

Think:

```text
i → n → 1
j → 1 → i
```

---

## PATTERN 6 — Pyramid

```text
   *
  ***
 *****
*******
```

Think:

```text
spaces = n-i
stars  = 2i-1
```

---

## PATTERN 7 — Inverted Pyramid

```text
*******
 *****
  ***
   *
```

Think:

```text
spaces = i-1
stars  = 2n-2i+1
```

---

## PATTERN 8 — Number Pyramid

```text
   1
  123
 12345
1234567
```

Think:

```text
spaces = n-i
count  = 2i-1
print  = 1 → count
```

---

## PATTERN 9 — Floyd's Triangle

```text
1
23
456
78910
```

Think:

```text
running counter
+
nested loops
```

Critical:

```python
number = 1

for i in ...:
    for j in ...:
        print(number)
        number += 1
```

---

## PATTERN 10 — Hollow Square

```text
*****
*   *
*   *
*   *
*****
```

Think:

```text
boundary condition
```

```python
if i == 0 or i == n-1 or j == 0 or j == n-1:
```

---

# 🔥 MASTER PATTERN PRINTING TEMPLATE

Almost every basic pattern can be reduced to:

```python
for i in range(...):          # ROW

    for j in range(...):      # COLUMN

        if CONDITION:
            print(VALUE, end="")
        else:
            print(OTHER_VALUE, end="")

    print()
```

Your job is to determine only:

```text
① Outer-loop range
② Inner-loop range
③ Condition
④ What to print
```

---

# 🧠 FIVE QUESTIONS BEFORE CODING

Whenever TopGun gives you an unknown pattern:

### Q1 — How many rows?

```text
n?
```

### Q2 — How many columns/items per row?

```text
i?
n-i?
2i-1?
```

### Q3 — What is printed?

```text
*
i
j
running number
space
```

### Q4 — Does it increase or decrease?

```text
↑ → i
↓ → n-i / reverse loop
```

### Q5 — Is it centered or hollow?

```text
Centered → SPACES
Hollow   → BOUNDARY CONDITION
```

---

# 🚨 TOPGUN PATTERN PRINTING TRAPS

## Trap 1 — `i` vs `j`

Remember:

```text
i = row
j = column
```

---

## Trap 2 — `print()` vs `end=""`

Same row:

```python
print("*", end="")
```

New row:

```python
print()
```

---

## Trap 3 — Pyramid formula

Normal:

```text
spaces = n-i
stars = 2i-1
```

Inverted:

```text
spaces = i-1
stars = 2n-2i+1
```

---

## Trap 4 — Floyd's Triangle

The counter must be **outside** the outer loop:

```python
number = 1
for i in ...:
```

not:

```python
for i in ...:
    number = 1
```

---

## Trap 5 — Hollow patterns

Don't count stars manually.

Think:

```text
Is this position on the boundary?
```

---

# 🏆 PATTERN PRINTING MASTER CHEAT SHEET

```text
Increasing triangle
→ count = i

Decreasing triangle
→ count = n-i+1

Repeated row number
→ print i

Sequential row numbers
→ print j

Pyramid
→ spaces = n-i
→ items = 2i-1

Inverted pyramid
→ spaces = i-1
→ items = 2n-2i+1

Floyd
→ running counter

Hollow
→ boundary condition
```

---

# 🧪 PATTERN PRINTING MINI TEST

Do these **without looking at the solutions**.

### Q1

What pattern is:

```text
*
**
***
****
```

### Q2

What pattern is:

```text
1234
123
12
1
```

### Q3

For a pyramid, what is the number of stars in row `i`?

### Q4

For a normal pyramid, what is the number of spaces in row `i`?

### Q5

What is the difference between:

```text
1
12
123
```

and:

```text
1
22
333
```

### Q6

What pattern does this represent?

```text
1
23
456
78910
```

### Q7

What is the key variable in Floyd's Triangle?

### Q8

What condition identifies a boundary cell in a hollow square?

### Q9

What is the time complexity of a typical `n × n` pattern?

### Q10

Complete this:

```python
for i in range(1, n + 1):
    for j in range(1, ______):
        print(j, end="")
```

to produce:

```text
1
12
123
1234
```

---

# ✅ ANSWER KEY

### Q1

Increasing Star Triangle.

```text
row i → i stars
```

### Q2

Inverted Number Triangle.

```text
i → n → 1
j → 1 → i
```

### Q3

```text
2*i - 1
```

### Q4

```text
n - i
```

### Q5

First:

```text
print(j)
```

Second:

```text
print(i)
```

### Q6

Floyd's Triangle.

### Q7

A running counter:

```python
number
```

### Q8

```python
i == 0 or i == n-1 or j == 0 or j == n-1
```

### Q9

Usually:

```text
O(n²)
```

### Q10

```python
i + 1
```

Complete:

```python
for i in range(1, n + 1):
    for j in range(1, i + 1):
        print(j, end="")
    print()
```

---

# 🟢 FINAL PROGRESS UPDATE

Your current locked **basic DSA pattern bank** is now:

```text
ARRAYS             10/10 ✅
STRINGS            10/10 ✅
HASHING            10/10 ✅
SEARCHING          10/10 ✅
RECURSION          10/10 ✅
2D ARRAYS/MATRIX   10/10 ✅
STACK              10/10 ✅
PATTERN PRINTING   10/10 ✅
--------------------------------
TOTAL              80/80 ✅
```

### Pattern Printing is officially **10/10 complete**.

The next topic can be **Queue / Deque**, with the same locked execution format.

Would you like to continue with Queue and Deque next?


