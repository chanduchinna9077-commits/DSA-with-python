# 🔴 10. 2D ARRAYS / MATRIX — 10 Problems

**YES — we should absolutely add this.**

This is different from normal 1D arrays.

### Patterns

```text
Matrix traversal
Row traversal
Column traversal
Diagonal
Boundary
Transpose
Search
Rotation
2D accumulation
```

### 10 Problems

| #  | Problem                  | Pattern          |
| -- | ------------------------ | ---------------- |
| 1  | Print Matrix             | Traversal        |
| 2  | Matrix Sum               | Traversal        |
| 3  | Row Sum                  | Row traversal    |
| 4  | Column Sum               | Column traversal |
| 5  | Main Diagonal Sum        | Diagonal         |
| 6  | Secondary Diagonal Sum   | Diagonal         |
| 7  | Transpose Matrix         | Row ↔ Column     |
| 8  | Search Element in Matrix | Traversal        |
| 9  | Boundary Traversal       | Boundary         |
| 10 | Rotate Matrix 90°        | Transformation   |

For your assessment, **1–9** are much more important than complicated matrix algorithms.

---


👍

# 🔵 2D ARRAYS / MATRIX — CONVERSATION 1

## Problems 1–4

We’ll keep the **same locked TopGun flow**: each problem gets theory → pattern → ELI10 → example → algorithm → built-in + manual Python → line-by-line → dry run → complexity → edge cases → traps → pattern recognition.

### 🧭 2D ARRAY / MATRIX ROADMAP

|  # | Problem                | Main Pattern                    |
| -: | ---------------------- | ------------------------------- |
|  1 | Print Matrix           | Nested Traversal                |
|  2 | Matrix Sum             | Nested Traversal + Accumulation |
|  3 | Row Sum                | Row-wise Traversal              |
|  4 | Column Sum             | Column-wise Traversal           |
|  5 | Main Diagonal Sum      | `i == j`                        |
|  6 | Secondary Diagonal Sum | `i + j == n - 1`                |
|  7 | Transpose Matrix       | Row ↔ Column                    |
|  8 | Search Element         | Nested Traversal                |
|  9 | Boundary Traversal     | Boundary Pattern                |
| 10 | Rotate Matrix 90°      | Transpose + Reverse             |

---

# 🔹 PROBLEM 1 — PRINT A MATRIX

## 1. Problem Statement

Given a 2D matrix, print every element row by row.

### Example

```text
Input:
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Output:
1 2 3
4 5 6
7 8 9
```

---

# 2. Problem Theory

A **2D array** is an array containing multiple arrays.

Think of it as a table:

```text
       Column
       0  1  2
      ┌─────────
Row 0 │ 1  2  3
Row 1 │ 4  5  6
Row 2 │ 7  8  9
```

Each element is accessed using:

```python
matrix[row][column]
```

For example:

```python
matrix[1][2]
```

means:

```text
row = 1
column = 2
```

so the answer is:

```text
6
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Nested Loop / Matrix Traversal

Whenever you see:

> "Visit every element of a matrix"

think:

```text
for every row
    for every column
        process matrix[row][column]
```

Template:

```python
for i in range(rows):
    for j in range(cols):
        process(matrix[i][j])
```

This is the **most important basic matrix pattern**.

---

# 4. ELI10 Intuition 🧒

Imagine a classroom with students sitting in rows.

```text
👦 👧 👦
👧 👦 👧
👦 👧 👦
```

You need to talk to everyone.

You:

1. Finish row 1.
2. Move to row 2.
3. Finish row 2.
4. Move to row 3.
5. Finish row 3.

So:

```text
Row 0 → Column 0 → Column 1 → Column 2
Row 1 → Column 0 → Column 1 → Column 2
Row 2 → Column 0 → Column 1 → Column 2
```

That's exactly what nested loops do.

---

# 5. Example

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]
```

Traversal:

```text
1 → 2 → 3
4 → 5 → 6
7 → 8 → 9
```

---

# 6. Algorithm — Step-by-Step

1. Find the number of rows.
2. Loop through each row.
3. For each row, loop through every column.
4. Print the current element.
5. After finishing a row, move to the next line.

### Pseudocode

```text
for each row:
    for each column:
        print matrix[row][column]
```

---

# 7. Python Solution — Using Built-in Features

Python allows direct iteration over rows:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    print(*row)
```

Output:

```text
1 2 3
4 5 6
7 8 9
```

Here:

```python
print(*row)
```

unpacks the row.

For:

```python
row = [1, 2, 3]
```

it behaves approximately like:

```python
print(1, 2, 3)
```

---

# 8. Python Solution — Without Built-in Unpacking

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

rows = len(matrix)

for i in range(rows):

    columns = len(matrix[i])

    for j in range(columns):
        print(matrix[i][j], end=" ")

    print()
```

---

# 9. Line-by-Line Explanation

```python
rows = len(matrix)
```

Finds the number of rows.

For our matrix:

```text
3 rows
```

---

```python
for i in range(rows):
```

Moves through each row.

Values of `i`:

```text
0
1
2
```

---

```python
columns = len(matrix[i])
```

Finds the number of elements in the current row.

For example:

```text
matrix[0] = [1, 2, 3]
```

so:

```text
columns = 3
```

---

```python
for j in range(columns):
```

Moves through the columns.

```text
j = 0
j = 1
j = 2
```

---

```python
print(matrix[i][j], end=" ")
```

Accesses the current element.

Example:

```text
i = 1
j = 2
```

gives:

```python
matrix[1][2]
```

which is:

```text
6
```

---

```python
print()
```

Moves to the next line after completing a row.

---

# 10. Detailed Dry Run

Matrix:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

| `i` | `j` | `matrix[i][j]` | Output |
| --: | --: | -------------: | ------ |
|   0 |   0 |              1 | 1      |
|   0 |   1 |              2 | 2      |
|   0 |   2 |              3 | 3      |
|   1 |   0 |              4 | 4      |
|   1 |   1 |              5 | 5      |
|   1 |   2 |              6 | 6      |
|   2 |   0 |              7 | 7      |
|   2 |   1 |              8 | 8      |
|   2 |   2 |              9 | 9      |

Final:

```text
1 2 3
4 5 6
7 8 9
```

---

# 11. Time Complexity

Suppose the matrix has:

* `R` rows
* `C` columns

Every element is visited exactly once.

$$
\boxed{O(R \times C)}
$$

For an `N × N` matrix:

$$
\boxed{O(N^2)}
$$

---

# 12. Space Complexity

We don't create another matrix.

$$
\boxed{O(1)}
$$

excluding the input matrix itself.

---

# 13. Edge Cases

### Empty matrix

```python
[]
```

No elements to print.

### One row

```text
[1, 2, 3]
```

### One column

```text
[
 [1],
 [2],
 [3]
]
```

### Single element

```text
[[5]]
```

Output:

```text
5
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using rows for both loops

```python
for i in range(rows):
    for j in range(rows):
```

This only works for square matrices.

For a rectangular matrix:

```text
2 × 4
```

it fails.

Correct:

```python
for i in range(rows):
    for j in range(len(matrix[i])):
```

---

### ❌ Mistake 2 — Confusing row and column

Remember:

```python
matrix[i][j]
```

means:

```text
matrix[row][column]
```

---

# 15. Pattern Recognition

### When you see:

> Print / visit / process every matrix element

Immediately think:

```text
2D ARRAY
   ↓
Nested Loops
   ↓
row → column
   ↓
matrix[i][j]
```

---

# 🔹 PROBLEM 2 — MATRIX SUM

## 1. Problem Statement

Given a matrix, find the sum of all elements.

### Example

```text
Input:
[
 [1, 2, 3],
 [4, 5, 6]
]

Output:
21
```

Because:

$$
1+2+3+4+5+6=21
$$

---

# 2. Problem Theory

This is simply **matrix traversal + accumulation**.

We visit every element and keep a running sum.

```text
sum = 0

1 → sum = 1
2 → sum = 3
3 → sum = 6
4 → sum = 10
5 → sum = 15
6 → sum = 21
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Nested Traversal + Accumulator

General pattern:

```python
answer = initial_value

for row:
    for element:
        answer = answer + element
```

This pattern is extremely common.

It is the matrix version of:

```text
array → traversal → accumulation
```

---

# 4. ELI10 Intuition 🧒

Imagine collecting coins from every box.

```text
Box 1 → 1 coin
Box 2 → 2 coins
Box 3 → 3 coins
...
```

You keep one counter:

```text
total
```

Every time you find something:

```text
total = total + value
```

That's exactly what we're doing.

---

# 5. Example

```text
[
 [2, 4],
 [6, 8]
]
```

Calculation:

```text
2 + 4 + 6 + 8
= 20
```

---

# 6. Algorithm — Step-by-Step

1. Create `total = 0`.
2. Traverse every row.
3. Traverse every element in that row.
4. Add the element to `total`.
5. Return `total`.

---

# 7. Python Solution — Using Built-in Methods

Python provides `sum()`:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

total = sum(sum(row) for row in matrix)

print(total)
```

Output:

```text
21
```

---

# 8. Python Solution — Without Built-in `sum()`

```python
def matrix_sum(matrix):

    total = 0

    for i in range(len(matrix)):

        for j in range(len(matrix[i])):

            total = total + matrix[i][j]

    return total


matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

print(matrix_sum(matrix))
```

Output:

```text
21
```

---

# 9. Line-by-Line Explanation

```python
total = 0
```

Start with zero.

---

```python
for i in range(len(matrix)):
```

Visit each row.

---

```python
for j in range(len(matrix[i])):
```

Visit each element inside that row.

---

```python
total = total + matrix[i][j]
```

Add the current element.

Equivalent shorthand:

```python
total += matrix[i][j]
```

---

```python
return total
```

Return the final sum.

---

# 10. Detailed Dry Run

Input:

```text
[
 [1, 2, 3],
 [4, 5, 6]
]
```

| `i` | `j` | Value | `total` |
| --: | --: | ----: | ------: |
|   0 |   0 |     1 |       1 |
|   0 |   1 |     2 |       3 |
|   0 |   2 |     3 |       6 |
|   1 |   0 |     4 |      10 |
|   1 |   1 |     5 |      15 |
|   1 |   2 |     6 |      21 |

Final:

```text
21
```

---

# 11. Time Complexity

Every element is visited once:

$$
\boxed{O(R \times C)}
$$

---

# 12. Space Complexity

Only `total` and loop variables:

$$
\boxed{O(1)}
$$

---

# 13. Edge Cases

```text
[]
```

→ `0`

Single element:

```text
[[10]]
```

→ `10`

Negative values:

```text
[[-1, 2], [-3, 4]]
```

→ `2`

---

# 14. Common Mistakes

### ❌ Forgetting to initialize

```python
total += matrix[i][j]
```

before defining `total`.

Correct:

```python
total = 0
```

### ❌ Resetting total inside the loop

Wrong:

```python
for i in range(...):
    total = 0
```

That destroys previous results.

---

# 15. Pattern Recognition

### When you see:

> "Find total/sum of all matrix elements"

Think:

```text
Nested loops
     ↓
Accumulator
     ↓
total += matrix[i][j]
```

---

# 🔹 PROBLEM 3 — ROW SUM

## 1. Problem Statement

Given a matrix, calculate the sum of **each row**.

### Example

```text
Input:
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Output:
6
15
24
```

Because:

```text
Row 0 → 1 + 2 + 3 = 6
Row 1 → 4 + 5 + 6 = 15
Row 2 → 7 + 8 + 9 = 24
```

---

# 2. Problem Theory

This is different from total matrix sum.

We need a **separate sum for each row**.

The important idea:

```text
Start row
    ↓
sum = 0
    ↓
process all columns
    ↓
print row sum
    ↓
move to next row
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Row-Wise Traversal

Template:

```python
for i in range(rows):

    row_sum = 0

    for j in range(columns):
        row_sum += matrix[i][j]

    print(row_sum)
```

The key difference from Problem 2:

> **The accumulator resets for every row.**

---

# 4. ELI10 Intuition 🧒

Imagine three students each have several coins.

```text
Student 1: 1 2 3
Student 2: 4 5 6
Student 3: 7 8 9
```

You want to know how many coins **each student** has.

You count Student 1 completely:

```text
1 + 2 + 3 = 6
```

Then start a **new counter** for Student 2:

```text
4 + 5 + 6 = 15
```

That's why `row_sum` must reset.

---

# 5. Example

```text
[
 [5, 5],
 [10, 10],
 [2, 3]
]
```

Row sums:

```text
10
20
5
```

---

# 6. Algorithm — Step-by-Step

1. Traverse each row.
2. Create `row_sum = 0`.
3. Traverse every column in that row.
4. Add each element to `row_sum`.
5. Output the row sum.
6. Reset the sum for the next row.

---

# 7. Python Solution — Using Built-in `sum()`

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for row in matrix:
    print(sum(row))
```

Output:

```text
6
15
24
```

---

# 8. Python Solution — Without Built-in `sum()`

```python
def row_sums(matrix):

    for i in range(len(matrix)):

        row_sum = 0

        for j in range(len(matrix[i])):

            row_sum += matrix[i][j]

        print(row_sum)


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

row_sums(matrix)
```

Output:

```text
6
15
24
```

---

# 9. Line-by-Line Explanation

```python
for i in range(len(matrix)):
```

Move through each row.

---

```python
row_sum = 0
```

Create a fresh accumulator for this row.

This line is **inside** the outer loop.

---

```python
for j in range(len(matrix[i])):
```

Visit every element in the current row.

---

```python
row_sum += matrix[i][j]
```

Add the current element.

---

```python
print(row_sum)
```

After finishing the row, output its sum.

---

# 10. Detailed Dry Run

Matrix:

```text
[
 [1,2,3],
 [4,5,6],
 [7,8,9]
]
```

### Row 0

```text
row_sum = 0
```

| Element | `row_sum` |
| ------: | --------: |
|       1 |         1 |
|       2 |         3 |
|       3 |         6 |

Output:

```text
6
```

### Row 1

Reset:

```text
row_sum = 0
```

| Element | `row_sum` |
| ------: | --------: |
|       4 |         4 |
|       5 |         9 |
|       6 |        15 |

Output:

```text
15
```

### Row 2

Reset:

```text
row_sum = 0
```

| Element | `row_sum` |
| ------: | --------: |
|       7 |         7 |
|       8 |        15 |
|       9 |        24 |

Output:

```text
24
```

---

# 11. Time Complexity

Every matrix element is visited once:

$$
\boxed{O(R \times C)}
$$

---

# 12. Space Complexity

No additional matrix.

$$
\boxed{O(1)}
$$

---

# 13. Edge Cases

### One row

```text
[[1,2,3]]
```

Output:

```text
6
```

### One column

```text
[
 [1],
 [2],
 [3]
]
```

Output:

```text
1
2
3
```

### Empty matrix

No rows → no output.

---

# 14. Common Mistakes / Traps

### ❌ Mistake — Putting `row_sum = 0` outside the outer loop

Wrong:

```python
row_sum = 0

for i in range(rows):
    for j in range(columns):
        row_sum += matrix[i][j]
```

That calculates the **total matrix sum**, not individual row sums.

Correct:

```python
for i in range(rows):
    row_sum = 0
```

---

# 15. Pattern Recognition

### When you see:

> "Sum of each row"

Think:

```text
OUTER LOOP → rows
INNER LOOP → columns
ACCUMULATOR → reset for each row
```

---

# 🔹 PROBLEM 4 — COLUMN SUM

## 1. Problem Statement

Given a matrix, calculate the sum of **each column**.

### Example

```text
Input:
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Output:
12
15
18
```

Because:

```text
Column 0 → 1 + 4 + 7 = 12
Column 1 → 2 + 5 + 8 = 15
Column 2 → 3 + 6 + 9 = 18
```

---

# 2. Problem Theory

This is the opposite direction from row sum.

### Row sum:

```text
row fixed
column changes
```

### Column sum:

```text
column fixed
row changes
```

This distinction is **very important** for matrix questions.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Column-Wise Traversal

Template:

```python
for j in range(columns):

    column_sum = 0

    for i in range(rows):

        column_sum += matrix[i][j]

    print(column_sum)
```

Notice the order:

```text
j → outer loop
i → inner loop
```

---

# 4. ELI10 Intuition 🧒

Imagine a building:

```text
1  2  3
4  5  6
7  8  9
```

For row sum, you walk:

```text
→ → →
→ → →
→ → →
```

For column sum, you walk:

```text
↓ ↓ ↓
↓ ↓ ↓
↓ ↓ ↓
```

So:

```text
Column 0:
1
4
7
```

Then:

```text
Column 1:
2
5
8
```

Then:

```text
Column 2:
3
6
9
```

---

# 5. Example

```text
[
 [2, 4],
 [6, 8],
 [10, 12]
]
```

Column sums:

```text
Column 0:
2 + 6 + 10 = 18

Column 1:
4 + 8 + 12 = 24
```

Output:

```text
18
24
```

---

# 6. Algorithm — Step-by-Step

1. Find the number of rows.
2. Find the number of columns.
3. Loop through each column.
4. Create `column_sum = 0`.
5. Loop through every row.
6. Add `matrix[i][j]`.
7. Print the column sum.
8. Repeat for the next column.

---

# 7. Python Solution — Using Built-in Features

Python doesn't have a simple built-in `column_sum()` for normal lists, but we can use `zip()`:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

for column in zip(*matrix):
    print(sum(column))
```

Output:

```text
12
15
18
```

---

# 8. Python Solution — Without Built-in Methods

```python
def column_sums(matrix):

    rows = len(matrix)
    columns = len(matrix[0])

    for j in range(columns):

        column_sum = 0

        for i in range(rows):

            column_sum += matrix[i][j]

        print(column_sum)


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

column_sums(matrix)
```

Output:

```text
12
15
18
```

---

# 9. Line-by-Line Explanation

```python
rows = len(matrix)
```

Number of rows.

Here:

```text
3
```

---

```python
columns = len(matrix[0])
```

Number of columns.

Here:

```text
3
```

---

```python
for j in range(columns):
```

Fix one column.

For example:

```text
j = 0
```

means:

```text
Column 0
```

---

```python
column_sum = 0
```

Start a fresh sum for this column.

---

```python
for i in range(rows):
```

Move vertically through the rows.

---

```python
column_sum += matrix[i][j]
```

Access:

```text
row i
column j
```

For column `0`:

```text
matrix[0][0] → 1
matrix[1][0] → 4
matrix[2][0] → 7
```

---

# 10. Detailed Dry Run

Matrix:

```text
[
 [1,2,3],
 [4,5,6],
 [7,8,9]
]
```

### Column 0

```text
j = 0
```

| `i` | Value | `column_sum` |
| --: | ----: | -----------: |
|   0 |     1 |            1 |
|   1 |     4 |            5 |
|   2 |     7 |           12 |

Output:

```text
12
```

---

### Column 1

```text
j = 1
```

| `i` | Value | `column_sum` |
| --: | ----: | -----------: |
|   0 |     2 |            2 |
|   1 |     5 |            7 |
|   2 |     8 |           15 |

Output:

```text
15
```

---

### Column 2

```text
j = 2
```

| `i` | Value | `column_sum` |
| --: | ----: | -----------: |
|   0 |     3 |            3 |
|   1 |     6 |            9 |
|   2 |     9 |           18 |

Output:

```text
18
```

---

# 11. Time Complexity

Every element is visited once:

$$
\boxed{O(R \times C)}
$$

---

# 12. Space Complexity

Ignoring the `zip()` built-in version's temporary iteration structure, the manual solution uses:

$$
\boxed{O(1)}
$$

extra space.

---

# 13. Edge Cases

### One column

```text
[
 [1],
 [2],
 [3]
]
```

Output:

```text
6
```

### One row

```text
[[1,2,3]]
```

Output:

```text
1
2
3
```

### Single element

```text
[[10]]
```

Output:

```text
10
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using `matrix[j][i]`

The correct access is:

```python
matrix[i][j]
```

because:

```text
i = row
j = column
```

---

### ❌ Mistake 2 — Reversing the loops

For column sums:

```python
for j in range(columns):
    for i in range(rows):
```

For row sums:

```python
for i in range(rows):
    for j in range(columns):
```

This distinction is important.

---

# 15. Pattern Recognition

### When you see:

> "Sum each column"

Think:

```text
COLUMN FIXED
     ↓
j stays same
     ↓
i changes
     ↓
matrix[i][j]
```

---

# 🧠 2D ARRAY FOUNDATION — PATTERN MAP

After these first four problems, you should recognize:

```text
┌───────────────────────────────┐
│       MATRIX TRAVERSAL        │
└───────────────────────────────┘

Print matrix
      ↓
Nested loops

Matrix total
      ↓
Nested loops + one accumulator

Row sums
      ↓
Rows outer
Columns inner
Accumulator resets per row

Column sums
      ↓
Columns outer
Rows inner
Accumulator resets per column
```

## 🔥 The critical distinction

### Row-wise

```python
for i in range(rows):
    for j in range(columns):
        matrix[i][j]
```

Think:

```text
→ → →
→ → →
→ → →
```

### Column-wise

```python
for j in range(columns):
    for i in range(rows):
        matrix[i][j]
```

Think:

```text
↓ ↓ ↓
↓ ↓ ↓
↓ ↓ ↓
```

---

# 📌 TOPGUN QUICK RECALL

If the question says:

```text
"Visit every element"
```

→ **Nested traversal**

```text
"Sum all elements"
```

→ **Nested traversal + accumulator**

```text
"Sum each row"
```

→ **Row outer loop + column inner loop**

```text
"Sum each column"
```

→ **Column outer loop + row inner loop**

---

## 🔵 2D ARRAYS / MATRIX PROGRESS

```text
Problems 1–4 / 10 ✅

1. Print Matrix       ✅
2. Matrix Sum         ✅
3. Row Sum            ✅
4. Column Sum         ✅
5. Main Diagonal      🔜
6. Secondary Diagonal
7. Transpose
8. Search Element
9. Boundary Traversal
10. Rotate 90°
```

**Next locked batch: Conversation 2 → Problems 5–8.**

Would you like to continue with Problems 5–8, starting with the main diagonal sum?


# 🔵 2D ARRAYS / MATRIX — CONVERSATION 2

## Problems 5–8 — LOCKED VERSION

We continue exactly from the locked roadmap.

|  # | Problem                | Main Pattern     |
| -: | ---------------------- | ---------------- |
|  5 | Main Diagonal Sum      | `i == j`         |
|  6 | Secondary Diagonal Sum | `i + j == n - 1` |
|  7 | Transpose Matrix       | Row ↔ Column     |
|  8 | Search Element         | Nested Traversal |

The important progression here is:

```text
Basic Traversal
      ↓
Diagonal Patterns
      ↓
Coordinate Transformation
      ↓
Matrix Searching
```

---

# 🔹 PROBLEM 5 — MAIN DIAGONAL SUM

## 1. Problem Statement

Given a square matrix, find the sum of the elements on the **main diagonal**.

### Example

```text
Input:

[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Output:

15
```

Because the main diagonal is:

```text
1
   5
      9
```

Therefore:

$$
1 + 5 + 9 = 15
$$

---

# 2. Problem Theory

The **main diagonal** goes from:

```text
Top-left → Bottom-right
```

For:

```text
1  2  3
4  5  6
7  8  9
```

the coordinates are:

```text
(0,0) → (1,1) → (2,2)
```

Notice something extremely important:

```text
row == column
```

Therefore:

$$
\boxed{i=j}
$$

This is the key pattern.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Main Diagonal Coordinate Pattern

Whenever you see:

> Main diagonal

Immediately think:

```text
matrix[i][i]
```

or:

```text
i == j
```

### Example

```text
matrix[0][0]
matrix[1][1]
matrix[2][2]
matrix[3][3]
```

---

# 4. ELI10 Intuition 🧒

Imagine a square classroom.

You start at the **top-left seat**.

Then move:

```text
↘
```

one row down and one column right every time.

```text
X  .  .
.  X  .
.  .  X
```

So both coordinates increase together:

```text
row = column
```

That's why:

```python
matrix[i][i]
```

finds every main-diagonal element.

---

# 5. Example

```text
[
 [5, 2, 1],
 [7, 8, 3],
 [4, 6, 9]
]
```

Main diagonal:

```text
5
   8
      9
```

Sum:

$$
5+8+9=22
$$

---

# 6. Algorithm — Step-by-Step

1. Create `diagonal_sum = 0`.
2. Traverse `i` from `0` to `n-1`.
3. Access:

   ```text
   matrix[i][i]
   ```
4. Add it to the sum.
5. Return the final sum.

### Pseudocode

```text
diagonal_sum = 0

for i = 0 to n-1:
    diagonal_sum += matrix[i][i]

return diagonal_sum
```

---

# 7. Python Solution — Using Built-in Methods

We can use `sum()` with a generator:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

diagonal_sum = sum(matrix[i][i] for i in range(len(matrix)))

print(diagonal_sum)
```

Output:

```text
15
```

---

# 8. Python Solution — Without Built-in `sum()`

```python
def main_diagonal_sum(matrix):

    diagonal_sum = 0

    for i in range(len(matrix)):
        diagonal_sum += matrix[i][i]

    return diagonal_sum


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(main_diagonal_sum(matrix))
```

Output:

```text
15
```

---

# 9. Line-by-Line Explanation

```python
def main_diagonal_sum(matrix):
```

Defines the function.

---

```python
diagonal_sum = 0
```

Creates the accumulator.

---

```python
for i in range(len(matrix)):
```

Moves through the diagonal index.

For a `3 × 3` matrix:

```text
i = 0
i = 1
i = 2
```

---

```python
diagonal_sum += matrix[i][i]
```

This is the key line.

When `i = 0`:

```python
matrix[0][0]
```

When `i = 1`:

```python
matrix[1][1]
```

When `i = 2`:

```python
matrix[2][2]
```

---

# 10. Detailed Dry Run

Input:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

| `i` | `matrix[i][i]` | Value | Sum |
| --: | -------------- | ----: | --: |
|   0 | `matrix[0][0]` |     1 |   1 |
|   1 | `matrix[1][1]` |     5 |   6 |
|   2 | `matrix[2][2]` |     9 |  15 |

Final:

```text
15
```

---

# 11. Time Complexity

We visit exactly `n` diagonal elements.

$$
\boxed{O(n)}
$$

This is better than scanning the entire matrix.

---

# 12. Space Complexity

Only one accumulator:

$$
\boxed{O(1)}
$$

---

# 13. Edge Cases

### `1 × 1`

```text
[[10]]
```

Answer:

```text
10
```

### Negative values

```text
[
 [-1, 2],
 [3, -4]
]
```

Main diagonal:

```text
-1 + -4 = -5
```

### Identity matrix

```text
[
 [1,0,0],
 [0,1,0],
 [0,0,1]
]
```

Answer:

```text
3
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using two independent indices

Wrong:

```python
for i in range(n):
    for j in range(n):
        diagonal_sum += matrix[i][j]
```

That sums the **entire matrix**.

For main diagonal:

```python
matrix[i][i]
```

is enough.

---

### ❌ Mistake 2 — Using `matrix[i][n-i-1]`

That is the **secondary diagonal**, not the main diagonal.

---

# 15. Pattern Recognition

### When you see:

> Main diagonal

Immediately think:

```text
i == j
↓
matrix[i][i]
```

### Visual:

```text
X  .  .
.  X  .
.  .  X
```

---

# 🔹 PROBLEM 6 — SECONDARY DIAGONAL SUM

## 1. Problem Statement

Given a square matrix, find the sum of elements on the **secondary diagonal**.

### Example

```text
Input:

[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Output:

15
```

Secondary diagonal:

```text
      3
   5
7
```

Therefore:

$$
3+5+7=15
$$

---

# 2. Problem Theory

The secondary diagonal goes:

```text
Top-right → Bottom-left
```

Coordinates:

```text
(0,2)
(1,1)
(2,0)
```

Notice:

```text
row + column = n - 1
```

For `n = 3`:

```text
0 + 2 = 2
1 + 1 = 2
2 + 0 = 2
```

Since:

```text
n - 1 = 2
```

Therefore:

$$
\boxed{i+j=n-1}
$$

And the element can be accessed using:

```python
matrix[i][n - 1 - i]
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Reverse Diagonal Coordinate

Main diagonal:

```text
matrix[i][i]
```

Secondary diagonal:

```text
matrix[i][n - 1 - i]
```

This distinction is **very important for screening tests**.

---

# 4. ELI10 Intuition 🧒

Imagine walking diagonally from the **top-right corner**.

```text
.  .  X
.  X  .
X  .  .
```

Every time you move down one row:

```text
row + 1
```

you move left one column:

```text
column - 1
```

Therefore:

```text
column = n - 1 - row
```

---

# 5. Example

```text
[
 [10, 20, 30],
 [40, 50, 60],
 [70, 80, 90]
]
```

Secondary diagonal:

```text
30
   50
70
```

Sum:

$$
30+50+70=150
$$

---

# 6. Algorithm — Step-by-Step

1. Set `diagonal_sum = 0`.
2. Loop through every row index `i`.
3. Calculate:

   ```text
   j = n - 1 - i
   ```
4. Add:

   ```text
   matrix[i][j]
   ```
5. Return the answer.

### Pseudocode

```text
sum = 0

for i = 0 to n-1:
    j = n - 1 - i
    sum += matrix[i][j]

return sum
```

---

# 7. Python Solution — Using Built-in `sum()`

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

n = len(matrix)

diagonal_sum = sum(matrix[i][n - 1 - i] for i in range(n))

print(diagonal_sum)
```

Output:

```text
15
```

---

# 8. Python Solution — Without Built-in `sum()`

```python
def secondary_diagonal_sum(matrix):

    n = len(matrix)

    diagonal_sum = 0

    for i in range(n):

        j = n - 1 - i

        diagonal_sum += matrix[i][j]

    return diagonal_sum


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

print(secondary_diagonal_sum(matrix))
```

Output:

```text
15
```

---

# 9. Line-by-Line Explanation

```python
n = len(matrix)
```

Gets the matrix size.

For a `3 × 3` matrix:

```text
n = 3
```

---

```python
for i in range(n):
```

Visit each row.

---

```python
j = n - 1 - i
```

Calculates the corresponding column.

For `n = 3`:

```text
i = 0 → j = 2
i = 1 → j = 1
i = 2 → j = 0
```

---

```python
diagonal_sum += matrix[i][j]
```

Adds the secondary diagonal element.

---

# 10. Detailed Dry Run

Matrix:

```text
[
 [1,2,3],
 [4,5,6],
 [7,8,9]
]
```

| `i` | `j = n-1-i` | Element | Sum |
| --: | ----------: | ------: | --: |
|   0 |           2 |       3 |   3 |
|   1 |           1 |       5 |   8 |
|   2 |           0 |       7 |  15 |

Final:

```text
15
```

---

# 11. Time Complexity

Exactly `n` elements are visited.

$$
\boxed{O(n)}
$$

---

# 12. Space Complexity

Only constant extra variables:

$$
\boxed{O(1)}
$$

---

# 13. Edge Cases

### `1 × 1`

```text
[[5]]
```

Secondary diagonal:

```text
5
```

### `2 × 2`

```text
[
 [1,2],
 [3,4]
]
```

Secondary diagonal:

```text
2 + 3 = 5
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using `matrix[i][i]`

That gives the main diagonal.

---

### ❌ Mistake 2 — Forgetting `-1`

Wrong:

```python
matrix[i][n - i]
```

Correct:

```python
matrix[i][n - 1 - i]
```

Why?

Because indexing starts from `0`.

---

# 15. Pattern Recognition

### Main diagonal

```text
matrix[i][i]
```

Visual:

```text
X . .
. X .
. . X
```

### Secondary diagonal

```text
matrix[i][n-1-i]
```

Visual:

```text
. . X
. X .
X . .
```

🔥 **Memorize this pair.**

---

# 🔹 PROBLEM 7 — TRANSPOSE MATRIX

## 1. Problem Statement

Given a matrix, find its **transpose**.

### Example

Input:

```text
[
 [1, 2, 3],
 [4, 5, 6]
]
```

Transpose:

```text
[
 [1, 4],
 [2, 5],
 [3, 6]
]
```

---

# 2. Problem Theory

Transpose means:

> Convert rows into columns and columns into rows.

Mathematically:

$$
A[i][j] \rightarrow A^T[j][i]
$$

Original:

```text
1  2  3
4  5  6
```

Rows:

```text
1 2 3
4 5 6
```

become columns:

```text
1 4
2 5
3 6
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Row ↔ Column Transformation

The key relationship:

```text
original[i][j]
        ↓
transpose[j][i]
```

This is one of the most important matrix transformations.

---

# 4. ELI10 Intuition 🧒

Imagine a table:

```text
Name  Age
A     20
B     21
```

Transpose swaps the direction:

```text
Name  A  B
Age   20 21
```

Rows become columns.

---

# 5. Example

Original:

```text
[
 [1, 2],
 [3, 4],
 [5, 6]
]
```

Transpose:

```text
[
 [1, 3, 5],
 [2, 4, 6]
]
```

Notice:

```text
3 rows × 2 columns
```

becomes:

```text
2 rows × 3 columns
```

---

# 6. Algorithm — Step-by-Step

For an `R × C` matrix:

1. Create a new matrix of size `C × R`.
2. Traverse every original element.
3. Place:

   ```text
   matrix[i][j]
   ```

   into:

   ```text
   transpose[j][i]
   ```
4. Return the new matrix.

### Pseudocode

```text
for i in rows:
    for j in columns:
        transpose[j][i] = matrix[i][j]
```

---

# 7. Python Solution — Using Built-in Method

Python's `zip()` provides a convenient approach:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

transpose = [list(row) for row in zip(*matrix)]

print(transpose)
```

Output:

```text
[[1, 4], [2, 5], [3, 6]]
```

---

# 8. Python Solution — Without Built-in Transpose

```python
def transpose_matrix(matrix):

    rows = len(matrix)
    columns = len(matrix[0])

    transpose = []

    for j in range(columns):

        new_row = []

        for i in range(rows):

            new_row.append(matrix[i][j])

        transpose.append(new_row)

    return transpose


matrix = [
    [1, 2, 3],
    [4, 5, 6]
]

result = transpose_matrix(matrix)

for row in result:
    print(row)
```

Output:

```text
[1, 4]
[2, 5]
[3, 6]
```

---

# 9. Line-by-Line Explanation

```python
rows = len(matrix)
```

Number of original rows.

```text
2
```

---

```python
columns = len(matrix[0])
```

Number of original columns.

```text
3
```

---

```python
transpose = []
```

Creates an empty result matrix.

---

```python
for j in range(columns):
```

Each original column becomes a new row.

For our matrix:

```text
j = 0
j = 1
j = 2
```

---

```python
new_row = []
```

Creates the new row.

---

```python
for i in range(rows):
```

Move down the original rows.

---

```python
new_row.append(matrix[i][j])
```

Take one column from the original matrix.

---

```python
transpose.append(new_row)
```

Add the completed new row.

---

# 10. Detailed Dry Run

Original:

```text
1 2 3
4 5 6
```

### `j = 0`

Take column 0:

```text
1
4
```

New row:

```text
[1,4]
```

---

### `j = 1`

Take column 1:

```text
2
5
```

New row:

```text
[2,5]
```

---

### `j = 2`

Take column 2:

```text
3
6
```

New row:

```text
[3,6]
```

Final:

```text
[
 [1,4],
 [2,5],
 [3,6]
]
```

---

# 11. Time Complexity

Every element is visited once.

$$
\boxed{O(R \times C)}
$$

---

# 12. Space Complexity

We create a new matrix containing all elements.

$$
\boxed{O(R \times C)}
$$

---

# 13. Edge Cases

### `1 × 1`

```text
[[5]]
```

Transpose:

```text
[[5]]
```

### One row

```text
[[1,2,3]]
```

Transpose:

```text
[
 [1],
 [2],
 [3]
]
```

### One column

```text
[
 [1],
 [2],
 [3]
]
```

Transpose:

```text
[[1,2,3]]
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Forgetting dimensions change

If original is:

```text
R × C
```

transpose is:

```text
C × R
```

---

### ❌ Mistake 2 — Using `matrix[j][i]`

The transformation is:

```text
original[i][j]
       ↓
transpose[j][i]
```

---

# 15. Pattern Recognition

### When you see:

> Transpose / swap rows and columns

Think:

```text
[i][j] → [j][i]
```

### Core formula:

$$
\boxed{A^T[j][i]=A[i][j]}
$$

---

# 🔹 PROBLEM 8 — SEARCH AN ELEMENT IN MATRIX

## 1. Problem Statement

Given a matrix and a target value, determine whether the target exists in the matrix.

### Example

```text
Matrix:

[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

Target = 6
```

Output:

```text
Found
```

---

# 2. Problem Theory

If the matrix is **not sorted in a special way**, the safest basic approach is:

> Visit every element until the target is found.

This is simply **linear search extended to two dimensions**.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Nested Linear Search

Array:

```text
for element:
    check target
```

Matrix:

```text
for row:
    for element:
        check target
```

The pattern is:

```text
2D traversal
      +
condition check
```

---

# 4. ELI10 Intuition 🧒

Imagine looking for a particular book in a library.

You check:

```text
Shelf 1 → every book
Shelf 2 → every book
Shelf 3 → every book
```

As soon as you find it:

```text
STOP
```

Same idea.

---

# 5. Example

```text
[
 [10, 20, 30],
 [40, 50, 60],
 [70, 80, 90]
]

target = 50
```

Traversal:

```text
10 → no
20 → no
30 → no
40 → no
50 → YES
```

Return immediately.

---

# 6. Algorithm — Step-by-Step

1. Traverse every row.
2. Traverse every column.
3. Compare the current element with `target`.
4. If equal:

   * return `True`.
5. If traversal finishes:

   * return `False`.

### Pseudocode

```text
for each row:
    for each column:
        if matrix[row][column] == target:
            return True

return False
```

---

# 7. Python Solution — Using Built-in Features

For a normal Python nested list:

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

target = 6

found = any(target in row for row in matrix)

print(found)
```

Output:

```text
True
```

---

# 8. Python Solution — Without Built-in Search

```python
def search_matrix(matrix, target):

    for i in range(len(matrix)):

        for j in range(len(matrix[i])):

            if matrix[i][j] == target:
                return True

    return False


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

target = 6

print(search_matrix(matrix, target))
```

Output:

```text
True
```

---

# 9. Line-by-Line Explanation

```python
for i in range(len(matrix)):
```

Visit every row.

---

```python
for j in range(len(matrix[i])):
```

Visit every element inside the current row.

---

```python
if matrix[i][j] == target:
```

Check whether current element equals target.

---

```python
return True
```

Immediately stop if found.

This is important.

There is no reason to keep searching after finding the target.

---

```python
return False
```

If both loops finish without finding it, target doesn't exist.

---

# 10. Detailed Dry Run

Input:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]

target = 6
```

| `i` | `j` | Value | Compare with 6 |
| --: | --: | ----: | -------------- |
|   0 |   0 |     1 | No             |
|   0 |   1 |     2 | No             |
|   0 |   2 |     3 | No             |
|   1 |   0 |     4 | No             |
|   1 |   1 |     5 | No             |
|   1 |   2 |     6 | **YES**        |

Function immediately returns:

```text
True
```

The remaining elements are never checked.

---

# 11. Target Not Found

Suppose:

```text
target = 100
```

Every element is checked:

```text
1
2
3
4
5
6
7
8
9
```

Nothing matches.

Therefore:

```text
False
```

---

# 12. Time Complexity

Worst case: target is at the end or doesn't exist.

Every element is visited.

$$
\boxed{O(R \times C)}
$$

Best case:

Target is the first element.

$$
O(1)
$$

---

# 13. Space Complexity

No additional matrix.

$$
\boxed{O(1)}
$$

---

# 14. Edge Cases

### Target at first position

```text
target = matrix[0][0]
```

→ `O(1)` best case.

### Target at last position

Entire matrix may be searched.

### Target doesn't exist

Entire matrix searched.

### Empty matrix

Return `False`.

A robust implementation:

```python
def search_matrix(matrix, target):

    for i in range(len(matrix)):
        for j in range(len(matrix[i])):
            if matrix[i][j] == target:
                return True

    return False
```

Naturally handles an empty matrix.

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Forgetting early return

Instead of:

```python
if matrix[i][j] == target:
    return True
```

some beginners continue unnecessarily.

---

### ❌ Mistake 2 — Assuming binary search

A normal matrix does **not** automatically allow binary search.

Unless the problem gives a specific sorted-matrix property, use nested traversal.

---

# 16. Pattern Recognition

### When you see:

> Search an element in a normal matrix

Think:

```text
2D Linear Search
      ↓
Nested loops
      ↓
if matrix[i][j] == target
      ↓
return True
```

---

# 🧠 CONVERSATION 2 — MASTER PATTERN MAP

You have now added four important matrix patterns.

## 1️⃣ Main Diagonal

```python
matrix[i][i]
```

Recognition:

```text
i == j
```

Visual:

```text
X . .
. X .
. . X
```

---

## 2️⃣ Secondary Diagonal

```python
matrix[i][n - 1 - i]
```

Recognition:

```text
i + j = n - 1
```

Visual:

```text
. . X
. X .
X . .
```

---

## 3️⃣ Transpose

```text
[i][j] → [j][i]
```

Recognition:

```text
Rows ↔ Columns
```

---

## 4️⃣ Matrix Search

```python
for i:
    for j:
        if matrix[i][j] == target:
```

Recognition:

```text
Normal matrix
+
Search target
=
Nested linear search
```

---

# 🔥 THE MATRIX PATTERN CHEAT SHEET

| Question wording    | Immediately think          |
| ------------------- | -------------------------- |
| Visit every element | Nested loops               |
| Sum all elements    | Nested loops + accumulator |
| Sum each row        | Row outer + column inner   |
| Sum each column     | Column outer + row inner   |
| Main diagonal       | `matrix[i][i]`             |
| Secondary diagonal  | `matrix[i][n-1-i]`         |
| Transpose           | `[i][j] → [j][i]`          |
| Search target       | Nested linear search       |

---

# 📊 CURRENT 2D ARRAY PROGRESS

```text
2D ARRAYS / MATRIX

1. Print Matrix          ✅
2. Matrix Sum            ✅
3. Row Sum               ✅
4. Column Sum            ✅
5. Main Diagonal         ✅
6. Secondary Diagonal    ✅
7. Transpose             ✅
8. Search Element        ✅
9. Boundary Traversal    🔜
10. Rotate Matrix 90°    🔜

STATUS: 8/10 🔵
```

### Overall TopGun DSA Progress

```text
ARRAYS          10/10 ✅
STRINGS         10/10 ✅
HASHING         10/10 ✅
SEARCHING       10/10 ✅
RECURSION       10/10 ✅
2D MATRIX        8/10 🔵
─────────────────────────
TOTAL           58/60
```

**Next locked batch → Conversation 3: Problems 9–10 + complete 2D Matrix Mastery, Pattern Recognition, Master Templates, and Mini Test.**

Would you like to continue with Problems 9–10, starting with boundary traversal?

# 🔵 2D ARRAYS / MATRIX — CONVERSATION 3

## Problems 9–10 + COMPLETE MATRIX MASTERY

### 🔒 Locked TopGun Version

We are finishing the topic without reducing the locked execution depth.

### Remaining problems

|  # | Problem            | Main Pattern            |
| -: | ------------------ | ----------------------- |
|  9 | Boundary Traversal | Four-boundary traversal |
| 10 | Rotate Matrix 90°  | Transpose + Reverse     |

Then:

* 🔥 Complete Matrix Pattern Recognition
* 🧠 Master Templates
* ⚠️ Common Screening Traps
* 🎯 Mini Test
* 📊 Final Progress Update

---

# 🔹 PROBLEM 9 — BOUNDARY TRAVERSAL

## 1. Problem Statement

Given a matrix, print all elements that lie on its **boundary**.

### Example

```text
Input:

1 2 3 4
5 6 7 8
9 10 11 12
13 14 15 16
```

Boundary elements are:

```text
1  2  3  4
5        8
9       12
13 14 15 16
```

Output:

```text
1 2 3 4 8 12 16 15 14 13 9 5
```

---

# 2. Problem Theory

The boundary consists of four sides:

```text
1 → 2 → 3 → 4
            ↓
5           8
↓           ↓
9          12
↓           ↓
13 → 14 → 15 → 16
```

We process:

### Top row

```text
matrix[0][0]
matrix[0][1]
...
matrix[0][C-1]
```

### Right column

```text
matrix[1][C-1]
matrix[2][C-1]
...
matrix[R-1][C-1]
```

### Bottom row — reverse

```text
matrix[R-1][C-2]
...
matrix[R-1][0]
```

### Left column — reverse

```text
matrix[R-2][0]
...
matrix[1][0]
```

The important part:

> **Don't print the four corners twice.**

---

# 3. Pattern Being Tested

## 🔥 Pattern: Four-Side Boundary Traversal

Think:

```text
TOP
 ↓
RIGHT
 ↓
BOTTOM REVERSE
 ↓
LEFT REVERSE
```

This is a very common matrix traversal pattern.

---

# 4. ELI10 Intuition 🧒

Imagine walking around the outside wall of a rectangular building.

You start at:

```text
TOP-LEFT
```

Walk:

```text
→ → →
```

Then:

```text
↓
```

Then:

```text
← ← ←
```

Then:

```text
↑
```

You are walking around the **border**, not through the middle.

---

# 5. Example

Matrix:

```text
1 2 3
4 5 6
7 8 9
```

Boundary:

```text
1 2 3
4   6
7 8 9
```

Traversal:

```text
1 → 2 → 3 → 6 → 9 → 8 → 7 → 4
```

Notice:

```text
5
```

is not part of the boundary.

---

# 6. Algorithm — Step-by-Step

For an `R × C` matrix:

### Step 1 — Top

Traverse:

```text
j = 0 → C-1
```

### Step 2 — Right

Traverse:

```text
i = 1 → R-1
```

### Step 3 — Bottom

Traverse backwards:

```text
j = C-2 → 0
```

### Step 4 — Left

Traverse backwards:

```text
i = R-2 → 1
```

The restricted ranges prevent corner duplication.

---

# 7. Python Solution — Using Built-in Features

A concise Python approach can build the boundary from slices.

```python
matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
    [13, 14, 15, 16]
]

rows = len(matrix)
cols = len(matrix[0])

boundary = []

# Top
boundary.extend(matrix[0])

# Right
for i in range(1, rows):
    boundary.append(matrix[i][cols - 1])

# Bottom
boundary.extend(matrix[rows - 1][cols - 2::-1])

# Left
for i in range(rows - 2, 0, -1):
    boundary.append(matrix[i][0])

print(*boundary)
```

Output:

```text
1 2 3 4 8 12 16 15 14 13 9 5
```

---

# 8. Python Solution — Without Built-in Convenience Methods

For screening practice, understand the loops directly:

```python
def boundary_traversal(matrix):

    rows = len(matrix)

    if rows == 0:
        return

    cols = len(matrix[0])

    # Top row
    for j in range(cols):
        print(matrix[0][j], end=" ")

    # Right column
    for i in range(1, rows):
        print(matrix[i][cols - 1], end=" ")

    # Bottom row
    for j in range(cols - 2, -1, -1):
        print(matrix[rows - 1][j], end=" ")

    # Left column
    for i in range(rows - 2, 0, -1):
        print(matrix[i][0], end=" ")


matrix = [
    [1, 2, 3, 4],
    [5, 6, 7, 8],
    [9, 10, 11, 12],
    [13, 14, 15, 16]
]

boundary_traversal(matrix)
```

Output:

```text
1 2 3 4 8 12 16 15 14 13 9 5
```

---

# 9. Line-by-Line Explanation

### Top row

```python
for j in range(cols):
    print(matrix[0][j], end=" ")
```

Row is fixed:

```text
0
```

Column changes:

```text
0 → 1 → 2 → 3
```

So:

```text
1 2 3 4
```

---

### Right column

```python
for i in range(1, rows):
    print(matrix[i][cols - 1], end=" ")
```

Column is fixed:

```text
cols - 1
```

For four columns:

```text
3
```

Rows move:

```text
1 → 2 → 3
```

So:

```text
8 12 16
```

We start at `1`, not `0`, because `matrix[0][3]` was already printed as part of the top row.

---

### Bottom row

```python
for j in range(cols - 2, -1, -1):
```

We start at:

```text
cols - 2
```

because the bottom-right corner was already printed.

For four columns:

```text
j = 2 → 1 → 0
```

Therefore:

```text
15 14 13
```

---

### Left column

```python
for i in range(rows - 2, 0, -1):
```

Start above the bottom-left corner.

For four rows:

```text
i = 2 → 1
```

Therefore:

```text
9 5
```

The top-left and bottom-left corners are avoided because they were already printed.

---

# 10. Detailed Dry Run

Matrix:

```text
1  2  3  4
5  6  7  8
9 10 11 12
13 14 15 16
```

### Step 1 — Top

```text
1 2 3 4
```

### Step 2 — Right

```text
8 12 16
```

### Step 3 — Bottom reverse

```text
15 14 13
```

### Step 4 — Left reverse

```text
9 5
```

Final:

```text
1 2 3 4 8 12 16 15 14 13 9 5
```

---

# 11. Complexity

For an `R × C` matrix, we visit only the boundary.

Boundary contains approximately:

$$
2R + 2C - 4
$$

elements.

Therefore:

$$
\boxed{O(R+C)}
$$

Space:

$$
\boxed{O(1)}
$$

if we directly print.

---

# 12. Edge Cases

## `1 × 1`

```text
[5]
```

Expected:

```text
5
```

---

## One row

```text
1 2 3 4
```

Boundary should be:

```text
1 2 3 4
```

not:

```text
1 2 3 4 3 2 1
```

---

## One column

```text
1
2
3
4
```

Boundary:

```text
1 2 3 4
```

Again, don't duplicate elements.

---

# 13. Common Mistakes / Traps

### ❌ Trap 1 — Printing corners twice

Very common.

For example:

```text
top-right
```

gets printed during the top traversal.

Don't print it again during the right traversal.

---

### ❌ Trap 2 — Incorrect bottom range

Wrong:

```python
range(cols - 1, -1, -1)
```

This repeats the bottom-right corner.

Correct:

```python
range(cols - 2, -1, -1)
```

---

### ❌ Trap 3 — Incorrect left range

Wrong:

```python
range(rows - 1, -1, -1)
```

This repeats bottom-left and top-left.

Correct:

```python
range(rows - 2, 0, -1)
```

---

# 14. Pattern Recognition

### When you see:

> Boundary / perimeter / outer elements

Think:

```text
TOP
RIGHT
BOTTOM ←
LEFT ↑
```

And immediately check:

```text
Are corners being duplicated?
```

---

# 🔹 PROBLEM 10 — ROTATE MATRIX 90° CLOCKWISE

## 1. Problem Statement

Given a square matrix, rotate it **90 degrees clockwise**.

### Example

Input:

```text
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

---

# 2. Problem Theory

A 90° clockwise rotation means:

```text
Top-left     → Top-right
Top-right    → Bottom-right
Bottom-right → Bottom-left
Bottom-left  → Top-left
```

The most important interview pattern is:

```text
ROTATE 90° CLOCKWISE
        ↓
TRANSPOSE
        ↓
REVERSE EACH ROW
```

This is the pattern you should memorize.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Transpose + Reverse

Two operations:

### Step 1

Transpose:

```text
1 2 3
4 5 6
7 8 9
```

becomes:

```text
1 4 7
2 5 8
3 6 9
```

### Step 2

Reverse every row:

```text
7 4 1
8 5 2
9 6 3
```

Done.

---

# 4. ELI10 Intuition 🧒

Imagine a piece of paper with:

```text
1 2 3
4 5 6
7 8 9
```

First flip the rows/columns:

```text
1 4 7
2 5 8
3 6 9
```

Then reverse each row:

```text
7 4 1
8 5 2
9 6 3
```

That gives a 90° clockwise rotation.

---

# 5. Example

Input:

```text
1 2
3 4
```

Transpose:

```text
1 3
2 4
```

Reverse each row:

```text
3 1
4 2
```

Final:

```text
3 1
4 2
```

---

# 6. Algorithm — Step-by-Step

For a square matrix:

### Step 1 — Transpose

Swap:

```text
matrix[i][j]
```

with:

```text
matrix[j][i]
```

Only process one side of the diagonal to avoid swapping twice.

### Step 2 — Reverse every row

For each row:

```text
left ↔ right
```

until the row is reversed.

---

# 7. Python Solution — Using Built-in Features

```python
matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

matrix = [list(row) for row in zip(*matrix)]

for row in matrix:
    row.reverse()

for row in matrix:
    print(row)
```

Output:

```text
[7, 4, 1]
[8, 5, 2]
[9, 6, 3]
```

---

# 8. Python Solution — Without Built-in Convenience Methods

For interview/screening mastery, understand the actual algorithm.

```python
def rotate_90_clockwise(matrix):

    n = len(matrix)

    # Step 1: Transpose
    for i in range(n):
        for j in range(i + 1, n):

            matrix[i][j], matrix[j][i] = \
                matrix[j][i], matrix[i][j]

    # Step 2: Reverse each row
    for i in range(n):

        left = 0
        right = n - 1

        while left < right:

            matrix[i][left], matrix[i][right] = \
                matrix[i][right], matrix[i][left]

            left += 1
            right -= 1


matrix = [
    [1, 2, 3],
    [4, 5, 6],
    [7, 8, 9]
]

rotate_90_clockwise(matrix)

for row in matrix:
    print(row)
```

Output:

```text
[7, 4, 1]
[8, 5, 2]
[9, 6, 3]
```

---

# 9. Line-by-Line Explanation

## Step 1 — Matrix size

```python
n = len(matrix)
```

For:

```text
3 × 3
```

we get:

```text
n = 3
```

---

## Step 2 — Transpose

```python
for i in range(n):
```

Select each row.

---

```python
for j in range(i + 1, n):
```

Start `j` one position after `i`.

Why?

Because we only need to swap one side of the diagonal.

For example:

```text
1 2 3
4 5 6
7 8 9
```

We need:

```text
2 ↔ 4
3 ↔ 7
6 ↔ 8
```

We don't need to swap:

```text
4 ↔ 2
7 ↔ 3
8 ↔ 6
```

again.

---

```python
matrix[i][j], matrix[j][i] = \
    matrix[j][i], matrix[i][j]
```

Swap symmetric elements.

Example:

```text
matrix[0][1] = 2
matrix[1][0] = 4
```

becomes:

```text
matrix[0][1] = 4
matrix[1][0] = 2
```

---

# Step 2 — Reverse Each Row

```python
for i in range(n):
```

Process every row.

---

```python
left = 0
right = n - 1
```

Set two pointers.

---

```python
while left < right:
```

Continue until the pointers meet.

---

```python
matrix[i][left], matrix[i][right] = \
    matrix[i][right], matrix[i][left]
```

Swap the left and right elements.

---

```python
left += 1
right -= 1
```

Move inward.

This is the same **two-pointer reversal pattern** you've already learned in arrays.

---

# 10. Detailed Dry Run

Original:

```text
1 2 3
4 5 6
7 8 9
```

## Phase 1 — Transpose

Swap:

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
6 ↔ 8
```

Matrix:

```text
1 4 7
2 5 8
3 6 9
```

Transpose complete.

---

## Phase 2 — Reverse each row

Row 0:

```text
1 4 7
```

Reverse:

```text
7 4 1
```

Row 1:

```text
2 5 8
```

Reverse:

```text
8 5 2
```

Row 2:

```text
3 6 9
```

Reverse:

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

# 11. Time Complexity

Transpose:

$$
O(n^2)
$$

Reverse rows:

$$
O(n^2)
$$

Overall:

$$
\boxed{O(n^2)}
$$

---

# 12. Space Complexity

We modify the matrix **in-place**.

No second matrix is required.

$$
\boxed{O(1)}
$$

This is an important interview advantage.

---

# 13. Edge Cases

### `1 × 1`

```text
[5]
```

Rotation:

```text
[5]
```

---

### `2 × 2`

```text
1 2
3 4
```

becomes:

```text
3 1
4 2
```

---

### Already symmetric matrix

```text
1 2
2 3
```

The algorithm still works correctly.

---

# 14. Common Mistakes / Traps

### ❌ Trap 1 — Reversing columns instead of rows

For clockwise rotation:

```text
Transpose + Reverse EACH ROW
```

---

### ❌ Trap 2 — Transposing with all `i, j`

Wrong:

```python
for i in range(n):
    for j in range(n):
        swap(...)
```

This swaps elements twice and restores the original matrix.

Correct:

```python
for i in range(n):
    for j in range(i + 1, n):
```

---

### ❌ Trap 3 — Confusing clockwise and anticlockwise

### Clockwise:

```text
Transpose
+
Reverse each row
```

### Anti-clockwise:

```text
Transpose
+
Reverse the order of rows
```

For this problem, memorize **clockwise = transpose + row reverse**.

---

# 15. Pattern Recognition

### When you see:

> Rotate matrix 90° clockwise

Immediately think:

```text
TRANSPOSE
    ↓
REVERSE EACH ROW
```

### Master formula:

$$
\boxed{\text{90° Clockwise} = \text{Transpose} + \text{Reverse Rows}}
$$

---

# 🧠 COMPLETE 2D ARRAY / MATRIX MASTERY

You have now completed all **10/10**.

---

# 🔥 MASTER PATTERN 1 — FULL MATRIX TRAVERSAL

Question:

> Visit/process every element.

Think:

```python
for i in range(rows):
    for j in range(columns):
        matrix[i][j]
```

Complexity:

$$
O(RC)
$$

---

# 🔥 MASTER PATTERN 2 — ROW-WISE PROCESSING

Question:

> Sum/process each row.

Think:

```python
for i in range(rows):
    answer = 0

    for j in range(columns):
        answer += matrix[i][j]
```

Key:

```text
i fixed
j changes
```

---

# 🔥 MASTER PATTERN 3 — COLUMN-WISE PROCESSING

Question:

> Sum/process each column.

Think:

```python
for j in range(columns):
    answer = 0

    for i in range(rows):
        answer += matrix[i][j]
```

Key:

```text
j fixed
i changes
```

---

# 🔥 MASTER PATTERN 4 — MAIN DIAGONAL

Question:

> Main diagonal.

Think:

```python
matrix[i][i]
```

Condition:

$$
\boxed{i=j}
$$

Visual:

```text
X . .
. X .
. . X
```

---

# 🔥 MASTER PATTERN 5 — SECONDARY DIAGONAL

Question:

> Secondary / anti-diagonal.

Think:

```python
matrix[i][n - 1 - i]
```

Condition:

$$
\boxed{i+j=n-1}
$$

Visual:

```text
. . X
. X .
X . .
```

---

# 🔥 MASTER PATTERN 6 — TRANSPOSE

Question:

> Convert rows into columns.

Think:

```text
[i][j] → [j][i]
```

Formula:

$$
\boxed{A^T[j][i]=A[i][j]}
$$

---

# 🔥 MASTER PATTERN 7 — MATRIX SEARCH

Question:

> Find whether target exists.

For an ordinary matrix:

```python
for i in range(rows):
    for j in range(columns):
        if matrix[i][j] == target:
            return True
```

Pattern:

```text
2D Linear Search
```

---

# 🔥 MASTER PATTERN 8 — BOUNDARY TRAVERSAL

Question:

> Print perimeter / boundary.

Think:

```text
TOP
 ↓
RIGHT
 ↓
BOTTOM ←
 ↓
LEFT ↑
```

Critical:

```text
Avoid duplicate corners.
```

---

# 🔥 MASTER PATTERN 9 — ROTATE 90° CLOCKWISE

Question:

> Rotate matrix 90° clockwise.

Think:

```text
TRANSPOSE
     ↓
REVERSE EACH ROW
```

This is one of the most valuable matrix patterns to memorize.

---

# 🧠 2D MATRIX MASTER TEMPLATE

## Template 1 — Standard Traversal

```python
for i in range(rows):
    for j in range(columns):
        # process matrix[i][j]
```

---

## Template 2 — Row Processing

```python
for i in range(rows):

    result = 0

    for j in range(columns):
        result += matrix[i][j]

    # use result
```

---

## Template 3 — Column Processing

```python
for j in range(columns):

    result = 0

    for i in range(rows):
        result += matrix[i][j]

    # use result
```

---

## Template 4 — Main Diagonal

```python
for i in range(n):
    result += matrix[i][i]
```

---

## Template 5 — Secondary Diagonal

```python
for i in range(n):
    result += matrix[i][n - 1 - i]
```

---

## Template 6 — Transpose

```python
for i in range(n):
    for j in range(i + 1, n):
        matrix[i][j], matrix[j][i] = \
            matrix[j][i], matrix[i][j]
```

---

## Template 7 — Search

```python
for i in range(rows):
    for j in range(columns):

        if matrix[i][j] == target:
            return True

return False
```

---

## Template 8 — Boundary

```python
# Top
for j in range(cols):
    process(matrix[0][j])

# Right
for i in range(1, rows):
    process(matrix[i][cols - 1])

# Bottom
for j in range(cols - 2, -1, -1):
    process(matrix[rows - 1][j])

# Left
for i in range(rows - 2, 0, -1):
    process(matrix[i][0])
```

---

## Template 9 — Rotate Clockwise

```python
# Transpose
for i in range(n):
    for j in range(i + 1, n):
        matrix[i][j], matrix[j][i] = \
            matrix[j][i], matrix[i][j]

# Reverse every row
for i in range(n):

    left = 0
    right = n - 1

    while left < right:

        matrix[i][left], matrix[i][right] = \
            matrix[i][right], matrix[i][left]

        left += 1
        right -= 1
```

---

# ⚠️ TOPGUN MATRIX TRAPS

These are the mistakes most likely to cost easy marks.

### Trap 1 — Mixing up `i` and `j`

Always remember:

```text
i = row
j = column
```

Therefore:

```text
matrix[i][j]
```

---

### Trap 2 — Row vs column traversal

```text
Row:
i fixed → j changes

Column:
j fixed → i changes
```

---

### Trap 3 — Main vs secondary diagonal

```text
Main:
matrix[i][i]

Secondary:
matrix[i][n-1-i]
```

Memorize this pair.

---

### Trap 4 — Assuming every matrix is square

This is wrong:

```python
for i in range(n):
    for j in range(n):
```

for a general matrix.

Use:

```python
rows = len(matrix)
cols = len(matrix[0])
```

when dimensions may differ.

---

### Trap 5 — Boundary corner duplication

Always inspect the four corners.

---

### Trap 6 — Rotate 90° clockwise incorrectly

Don't randomly swap rows and columns.

Use:

```text
Transpose
+
Reverse each row
```

---

# 🎯 TOPGUN "WHEN YOU SEE X → THINK Y"

| If question says...  | Think immediately          |
| -------------------- | -------------------------- |
| Print matrix         | Nested loops               |
| Visit all elements   | Nested loops               |
| Sum all elements     | Nested loops + accumulator |
| Sum each row         | Row-wise traversal         |
| Sum each column      | Column-wise traversal      |
| Main diagonal        | `i == j`                   |
| Secondary diagonal   | `i + j == n-1`             |
| Transpose            | `[i][j] → [j][i]`          |
| Search target        | 2D linear search           |
| Boundary/perimeter   | Four sides                 |
| Rotate 90° clockwise | Transpose + reverse rows   |

---

# 🧪 2D MATRIX MINI TEST

Now the important part: **don't look at the solutions immediately.**

Try these yourself.

---

## 🟢 Question 1 — Basic

Given:

```text
[
 [2, 4],
 [6, 8]
]
```

Find the total matrix sum.

---

## 🟢 Question 2 — Row Pattern

Given:

```text
[
 [1, 2, 3],
 [4, 5, 6]
]
```

What are the row sums?

---

## 🟢 Question 3 — Column Pattern

Given:

```text
[
 [1, 2, 3],
 [4, 5, 6]
]
```

What are the column sums?

---

## 🟡 Question 4 — Main Diagonal

Given:

```text
[
 [5, 2, 7],
 [1, 8, 3],
 [4, 6, 9]
]
```

Find the main diagonal sum.

---

## 🟡 Question 5 — Secondary Diagonal

Same matrix:

```text
[
 [5, 2, 7],
 [1, 8, 3],
 [4, 6, 9]
]
```

Find the secondary diagonal sum.

---

## 🟡 Question 6 — Search

Given:

```text
[
 [10, 20, 30],
 [40, 50, 60],
 [70, 80, 90]
]
```

Target:

```text
80
```

What should the search function return?

---

## 🟠 Question 7 — Transpose

Transpose:

```text
[
 [1, 2, 3],
 [4, 5, 6]
]
```

---

## 🟠 Question 8 — Boundary

Print the boundary clockwise:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

---

## 🔴 Question 9 — Rotation

Rotate 90° clockwise:

```text
[
 [1, 2, 3],
 [4, 5, 6],
 [7, 8, 9]
]
```

---

## 🔴 Question 10 — Pattern Recognition

Without writing code, identify the pattern:

> "Given an `N × N` matrix, calculate the sum of elements where row index equals column index."

Your answer should be:

```text
Pattern:
Formula:
Code access:
```

---

# ✅ MINI TEST ANSWERS

Don't memorize the answers. Understand the pattern.

### Q1

$$
2+4+6+8=\boxed{20}
$$

---

### Q2

```text
Row 0:
1 + 2 + 3 = 6

Row 1:
4 + 5 + 6 = 15
```

Answer:

```text
6, 15
```

---

### Q3

```text
Column 0:
1 + 4 = 5

Column 1:
2 + 5 = 7

Column 2:
3 + 6 = 9
```

Answer:

```text
5, 7, 9
```

---

### Q4

Main diagonal:

```text
5
  8
    9
```

$$
5+8+9=\boxed{22}
$$

---

### Q5

Secondary diagonal:

```text
    7
   8
  4
```

$$
7+8+4=\boxed{19}
$$

---

### Q6

Target `80` exists.

```text
True
```

---

### Q7

```text
[
 [1, 4],
 [2, 5],
 [3, 6]
]
```

---

### Q8

```text
1 2 3 6 9 8 7 4
```

---

### Q9

```text
[
 [7, 4, 1],
 [8, 5, 2],
 [9, 6, 3]
]
```

---

### Q10

```text
Pattern:
Main Diagonal

Formula:
i == j

Code:
matrix[i][i]
```

---

# 🏆 FINAL 2D ARRAY / MATRIX MASTERY CHECK

Before considering this topic mastered, you should be able to answer these instantly:

```text
Q: Every element?
A: Nested loops

Q: Every row's sum?
A: i outer, j inner

Q: Every column's sum?
A: j outer, i inner

Q: Main diagonal?
A: matrix[i][i]

Q: Secondary diagonal?
A: matrix[i][n-1-i]

Q: Transpose?
A: [i][j] → [j][i]

Q: Search normal matrix?
A: Nested linear search

Q: Boundary?
A: Top → Right → Bottom → Left

Q: 90° clockwise?
A: Transpose → Reverse each row
```

---

# 📊 TOPGUN DSA PROGRESS

```text
ARRAYS             10/10 ✅
STRINGS            10/10 ✅
HASHING            10/10 ✅
SEARCHING          10/10 ✅
RECURSION          10/10 ✅
2D ARRAYS/MATRIX   10/10 ✅
─────────────────────────────
TOTAL              60/60 🔥
```

## 🔵 6 TOPICS COMPLETED

You have now completed **60 high-value problems** across the first six topics of the TopGun basic DSA track.

The remaining locked topics are:

```text
7.  Stack
8.  Queue / Deque
9.  Linked List
10. Pattern Printing
11. Basic Bit Manipulation
```

**2D Arrays / Matrix is now fully complete: 10/10.**

Would you like to continue with Stack next, or take the mini test first?

