# 🟡 DAY 5

## ARRAY FUNDAMENTALS

### Problems 41–50

```text
Largest Element
Smallest Element
Second Largest
Reverse Array
Sum & Average
Even/Odd Count
Sorted Array
Missing Number
Duplicate Number
Move Zeroes
```

### 🎯 Skill

**Array traversal + manipulation**


❓ **You don't get that hint.**



# 🔥 CR2 — DAY 5 — SESSION 1

# ARRAY FUNDAMENTALS — PROBLEMS 41–43

We are rebuilding this session at the **locked execution depth**.

No shortcuts. No compressed explanations. Each problem follows the full CR2 structure:

1. 🔹 BLOCK 1 — Senior Insights
2. 🔹 BLOCK 2 — Problem Understanding
3. 🔹 BLOCK 3 — Logic / Intuition
4. 🔹 BLOCK 4 — Algorithm — Step by Step
5. 🔹 BLOCK 5 — Optimal Python Solution
6. 🔹 BLOCK 6 — Optimal Java Solution
7. 🔹 BLOCK 7 — Python Dry Run
8. 🔹 BLOCK 8 — Java Dry Run
9. 🔹 BLOCK 9 — Complexity Analysis
10. 🔹 BLOCK 10 — Interview Q&A
11. 🔹 BLOCK 11 — Pattern Extraction
12. 🔹 BLOCK 12 — Common Mistakes
13. 🔹 BLOCK 13 — Interview-Ready Summary

---

# 📘 DAY 5 — ARRAY FUNDAMENTALS

## 🎯 SESSION 1

| #      | Problem                         | Exact LeetCode Match       | Difficulty   |
| ------ | ------------------------------- | -------------------------- | ------------ |
| **41** | Largest Element in an Array     | ❌ No exact canonical match | Basic        |
| **42** | Smallest Element in an Array    | ❌ No exact canonical match | Basic        |
| **43** | Second Largest Distinct Element | ❌ No exact canonical match | Basic–Medium |

### 🎯 What this session actually teaches

These three problems are not about memorizing three programs.

They build one important placement skill:

```text
ARRAY
  ↓
SCAN
  ↓
MAINTAIN INFORMATION
  ↓
UPDATE ANSWER
```

We progress from:

```text
ONE VALUE
   ↓
largest

ONE VALUE
   ↓
smallest

TWO VALUES
   ↓
largest + second largest
```

---

# 🟢 PROBLEM 41 — LARGEST ELEMENT IN AN ARRAY

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

## 1. What is the real skill being tested?

At beginner level, the question is:

> "Can you find the biggest number?"

At interview level, the real question is:

> **Can you scan an array while continuously maintaining the best answer so far?**

This is the **running maximum pattern**.

---

## 2. First instinct you should develop

When you see:

* largest element
* maximum element
* highest value
* greatest number
* maximum score
* best value

your first thought should be:

```text
Can I maintain a running maximum?
```

Usually:

```python
largest = arr[0]

for x in arr[1:]:
    if x > largest:
        largest = x
```

---

## 3. Why don't we sort?

A beginner may write:

```python
arr.sort()
answer = arr[-1]
```

This works.

But it solves a much bigger problem than necessary.

We don't need:

```text
"Put every element in order."
```

We only need:

```text
"Tell me which element is biggest."
```

Therefore:

```text
Sorting → unnecessary
Scanning → sufficient
```

---

## 4. Senior observation

Suppose:

```text
[7, 12, 4, 19, 3]
```

After processing the first element:

```text
largest = 7
```

After processing first two:

```text
largest = 12
```

After processing first three:

```text
largest = 12
```

After processing first four:

```text
largest = 19
```

At every point:

> `largest` represents the largest element seen **so far**.

That phrase is extremely important.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

## Problem

Given an array of integers, find the largest element.

### Example

```text
Input:
[10, 5, 25, 8, 15]

Output:
25
```

Because:

```text
10
5
25 ← biggest
8
15
```

Therefore:

```text
Answer = 25
```

---

## Input structure

We have:

```text
arr = [10, 5, 25, 8, 15]
```

The array contains:

```text
n = 5
```

elements.

---

## Expected behavior

For:

```text
[4, 8, 2, 15]
```

return:

```text
15
```

For:

```text
[-10, -5, -20]
```

return:

```text
-5
```

For:

```text
[42]
```

return:

```text
42
```

---

## Important edge case

Do **not** assume that zero is the largest starting point.

This is wrong:

```python
largest = 0
```

because:

```text
[-10, -20, -5]
```

contains no zero.

Correct:

```python
largest = arr[0]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine you're watching a race.

Every participant comes one by one.

You maintain one variable:

```text
current_champion
```

First person:

```text
10
```

So:

```text
champion = 10
```

Next:

```text
5
```

Is 5 greater than 10?

```text
No.
```

Champion remains:

```text
10
```

Next:

```text
25
```

Is 25 greater than 10?

```text
Yes.
```

New champion:

```text
25
```

Next:

```text
8
```

8 cannot beat 25.

Next:

```text
15
```

15 cannot beat 25.

Final:

```text
champion = 25
```

The array problem is exactly the same.

---

## Mental model

```text
              ARRAY
                ↓
        inspect one element
                ↓
       compare with current best
          ↙             ↘
       bigger          not bigger
          ↓                ↓
       update            ignore
          ↓                ↓
             continue
                ↓
              answer
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Take the first element.

```python
largest = arr[0]
```

---

### Step 2

Start from the second element.

Why?

Because the first element is already our initial candidate.

```python
for num in arr[1:]:
```

---

### Step 3

Compare the current number with the largest seen so far.

```python
if num > largest:
```

---

### Step 4

If the current number is bigger, replace the answer.

```python
largest = num
```

---

### Step 5

Continue until the array ends.

---

### Step 6

Return `largest`.

---

## Pseudocode

```text
largest = first element

for every remaining element:
    if element > largest:
        largest = element

return largest
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def find_largest(arr):
    # Assume the first element is the largest initially
    largest = arr[0]

    # Check every remaining element
    for num in arr[1:]:

        # If current number is bigger,
        # update the largest value
        if num > largest:
            largest = num

    return largest


arr = [10, 5, 25, 8, 15]

answer = find_largest(arr)

print("Largest element:", answer)
```

### Output

```text
Largest element: 25
```

---

## Why `arr[1:]`?

Suppose:

```python
arr = [10, 5, 25, 8]
```

Then:

```python
arr[1:]
```

means:

```text
[5, 25, 8]
```

We already used:

```text
10
```

as the initial largest.

---

## Even more memory-efficient version

For strict interview optimization, avoid creating the slice `arr[1:]`:

```python
def find_largest(arr):
    largest = arr[0]

    for i in range(1, len(arr)):
        if arr[i] > largest:
            largest = arr[i]

    return largest
```

This is the version you should prefer when discussing auxiliary space precisely.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static int findLargest(int[] arr) {

        // Assume first element is largest
        int largest = arr[0];

        // Start from index 1
        for (int i = 1; i < arr.length; i++) {

            // If current element is larger,
            // update largest
            if (arr[i] > largest) {
                largest = arr[i];
            }
        }

        return largest;
    }

    public static void main(String[] args) {

        int[] arr = {10, 5, 25, 8, 15};

        int answer = findLargest(arr);

        System.out.println("Largest element: " + answer);
    }
}
```

### Output

```text
Largest element: 25
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
arr = [10, 5, 25, 8, 15]
```

### Initial state

```text
largest = arr[0]
largest = 10
```

Now process remaining elements.

| Step | Current `num` | `largest` Before | Comparison | Update? | `largest` After |
| ---: | ------------: | ---------------: | ---------- | ------- | --------------: |
|    1 |             5 |               10 | 5 > 10 ❌   | No      |              10 |
|    2 |            25 |               10 | 25 > 10 ✅  | Yes     |              25 |
|    3 |             8 |               25 | 8 > 25 ❌   | No      |              25 |
|    4 |            15 |               25 | 15 > 25 ❌  | No      |              25 |

Final:

```text
largest = 25
```

---

## Important invariant

After processing each element:

> `largest` contains the maximum value among all elements processed so far.

This is the deeper DSA concept behind the problem.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Array:

```text
{10, 5, 25, 8, 15}
```

Initial:

```text
largest = 10
```

### `i = 1`

```text
arr[1] = 5
```

Check:

```text
5 > 10 → false
```

So:

```text
largest = 10
```

---

### `i = 2`

```text
arr[2] = 25
```

Check:

```text
25 > 10 → true
```

Update:

```text
largest = 25
```

---

### `i = 3`

```text
arr[3] = 8
```

```text
8 > 25 → false
```

No update.

---

### `i = 4`

```text
arr[4] = 15
```

```text
15 > 25 → false
```

No update.

Final:

```text
largest = 25
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of elements
```

We inspect each element exactly once.

Therefore:

```text
Time = O(n)
```

### Why?

There are approximately:

```text
n - 1
```

comparisons.

Dropping constants:

```text
O(n - 1) = O(n)
```

---

## Space

We use only:

```text
largest
num
```

No additional data structure is required.

Therefore:

```text
Auxiliary Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

## Comparison with sorting

Sorting:

```text
O(n log n)
```

Scanning:

```text
O(n)
```

Therefore, scanning is asymptotically more efficient for finding only the maximum.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why not use `max(arr)`?

You can in production Python:

```python
max(arr)
```

But in an interview, the interviewer may be testing whether you understand how maximum finding works internally.

The underlying logic is:

```python
largest = arr[0]

for x in arr[1:]:
    if x > largest:
        largest = x
```

---

### Q2. What happens with all-negative values?

Example:

```text
[-20, -8, -15]
```

Start:

```text
largest = -20
```

Then:

```text
-8 > -20 → yes
```

So:

```text
largest = -8
```

Answer:

```text
-8
```

---

### Q3. What happens with duplicates?

```text
[5, 9, 9, 3]
```

The answer is:

```text
9
```

Duplicates do not affect finding the largest value.

---

### Q4. What if the array contains one element?

```text
[100]
```

Answer:

```text
100
```

No comparison is required.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# RUNNING MAXIMUM

Master template:

```python
best = arr[0]

for x in arr[1:]:
    if x > best:
        best = x
```

### Recognition triggers

If the question says:

```text
largest
maximum
highest
greatest
best
```

think:

```text
RUNNING MAXIMUM
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

```python
largest = 0
```

Fails for all-negative arrays.

---

### ❌ Mistake 2

Sorting unnecessarily:

```python
arr.sort()
answer = arr[-1]
```

Correct result, but unnecessary `O(n log n)` work.

---

### ❌ Mistake 3

Wrong comparison:

```python
if num < largest:
```

That searches for the minimum.

---

### ❌ Mistake 4

Starting from index `0` after already using `arr[0]`.

Not wrong if written carefully, but unnecessary.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Scan the array once while maintaining the largest value seen so far. Initialize the maximum with the first element so negative arrays are handled correctly.**

```text
Time  → O(n)
Space → O(1)
Pattern → Running Maximum
```

---

# 🟢 PROBLEM 42 — SMALLEST ELEMENT IN AN ARRAY

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Problem 42 is deliberately similar to Problem 41.

The purpose is to make you recognize the **same pattern under a different comparison**.

Problem 41:

```python
if x > largest:
```

Problem 42:

```python
if x < smallest:
```

Everything else is almost identical.

---

## Core lesson

Don't memorize:

```text
Largest code
Smallest code
```

Memorize:

```text
TRACK A BEST VALUE WHILE SCANNING
```

Then decide whether "best" means:

```text
maximum
```

or:

```text
minimum
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, find its smallest element.

Example:

```text
Input:
[10, 5, 25, 8, 15]

Output:
5
```

Because:

```text
5
```

is smaller than every other value.

---

## More examples

```text
[8, 3, 11, 2]
→ 2
```

```text
[-4, -10, -2]
→ -10
```

```text
[7]
→ 7
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine looking for the shortest person in a group.

First person:

```text
10
```

Current shortest:

```text
10
```

Next:

```text
5
```

5 is shorter.

Update:

```text
smallest = 5
```

Next:

```text
25
```

25 is not smaller.

Keep:

```text
smallest = 5
```

The algorithm continuously remembers:

> **the smallest value encountered so far.**

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Initialize:

```python
smallest = arr[0]
```

### Step 2

Scan the remaining elements.

### Step 3

For each number:

```python
if num < smallest:
```

### Step 4

If true:

```python
smallest = num
```

### Step 5

Continue until the end.

### Step 6

Return `smallest`.

---

## Pseudocode

```text
smallest = first element

for every remaining element:
    if element < smallest:
        smallest = element

return smallest
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def find_smallest(arr):

    # Assume first element is smallest
    smallest = arr[0]

    # Scan remaining elements
    for num in arr[1:]:

        # If current number is smaller,
        # update smallest
        if num < smallest:
            smallest = num

    return smallest


arr = [10, 5, 25, 8, 15]

answer = find_smallest(arr)

print("Smallest element:", answer)
```

### Output

```text
Smallest element: 5
```

---

## Strict O(1)-auxiliary version

```python
def find_smallest(arr):
    smallest = arr[0]

    for i in range(1, len(arr)):
        if arr[i] < smallest:
            smallest = arr[i]

    return smallest
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static int findSmallest(int[] arr) {

        // Assume first element is smallest
        int smallest = arr[0];

        // Scan remaining elements
        for (int i = 1; i < arr.length; i++) {

            // Update if current element is smaller
            if (arr[i] < smallest) {
                smallest = arr[i];
            }
        }

        return smallest;
    }

    public static void main(String[] args) {

        int[] arr = {10, 5, 25, 8, 15};

        int answer = findSmallest(arr);

        System.out.println("Smallest element: " + answer);
    }
}
```

### Output

```text
Smallest element: 5
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[10, 5, 25, 8, 15]
```

Initial:

```text
smallest = 10
```

| Step | Current | Smallest Before | Comparison | Update? | Smallest After |
| ---: | ------: | --------------: | ---------- | ------- | -------------: |
|    1 |       5 |              10 | 5 < 10 ✅   | Yes     |              5 |
|    2 |      25 |               5 | 25 < 5 ❌   | No      |              5 |
|    3 |       8 |               5 | 8 < 5 ❌    | No      |              5 |
|    4 |      15 |               5 | 15 < 5 ❌   | No      |              5 |

Final:

```text
smallest = 5
```

---

## Negative-number dry run

Input:

```text
[-4, -10, -2, -20]
```

Start:

```text
smallest = -4
```

Then:

```text
-10 < -4 → yes → smallest = -10
-2 < -10 → no
-20 < -10 → yes → smallest = -20
```

Answer:

```text
-20
```

This is why initialization with the first element matters.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
{10, 5, 25, 8, 15}
```

Initial:

```text
smallest = 10
```

### Index 1

```text
5 < 10
```

Yes:

```text
smallest = 5
```

### Index 2

```text
25 < 5
```

No.

### Index 3

```text
8 < 5
```

No.

### Index 4

```text
15 < 5
```

No.

Final:

```text
smallest = 5
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For `n` elements:

We inspect:

```text
n - 1
```

remaining elements.

Therefore:

```text
Time = O(n)
```

Only one tracking variable is required:

```text
smallest
```

Therefore:

```text
Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the difference from finding the largest?

Only the comparison:

```python
# Largest
if x > largest:
```

versus:

```python
# Smallest
if x < smallest:
```

---

### Q2. Why can't you safely initialize `smallest = 0`?

Consider:

```text
[4, 8, 2]
```

The answer is `2`, but if your logic is based on finding values smaller than zero, you would never update.

The safe general solution is:

```python
smallest = arr[0]
```

---

### Q3. Can duplicates exist?

Yes.

```text
[4, 2, 2, 8]
```

Answer:

```text
2
```

No special handling is required.

---

### Q4. What is the fastest possible asymptotic time?

For an unsorted array, you must inspect every element to guarantee the minimum.

Therefore:

```text
Ω(n)
```

is the lower bound.

Our algorithm:

```text
O(n)
```

matches that lower bound.

So the algorithm is asymptotically optimal.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# RUNNING MINIMUM

Template:

```python
best = arr[0]

for x in arr[1:]:
    if x < best:
        best = x
```

Recognition:

```text
smallest
minimum
lowest
least
```

↓

```text
RUNNING MINIMUM
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

```python
smallest = 0
```

Unsafe.

---

### ❌ Mistake 2

Using:

```python
if num > smallest:
```

This moves toward the maximum, not minimum.

---

### ❌ Mistake 3

Sorting:

```python
sorted(arr)[0]
```

Works, but unnecessary.

---

### ❌ Mistake 4

Forgetting negative numbers.

Always test:

```text
[-10, -3, -20]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Initialize the minimum with the first element and scan the array once, replacing it whenever a smaller value is found.**

```text
Time  → O(n)
Space → O(1)
Pattern → Running Minimum
```

---

# 🟠 PROBLEM 43 — SECOND LARGEST DISTINCT ELEMENT

This is the **most important problem of today's session**.

Problem 41 taught:

```text
ONE BEST VALUE
```

Problem 43 teaches:

```text
TWO BEST VALUES
```

This is where array scanning becomes more interesting.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

## What is the actual pattern?

We need to maintain:

```text
largest
second_largest
```

while scanning once.

Instead of asking:

> "What is the largest number?"

we now ask:

> "What are the top two distinct numbers seen so far?"

---

## Why is "distinct" important?

Consider:

```text
[10, 20, 20, 5]
```

Largest:

```text
20
```

What is the second largest?

If duplicates are allowed:

```text
20
```

But the problem specifically says **distinct**.

Distinct values are:

```text
10, 20, 5
```

Therefore:

```text
second largest = 10
```

---

## Senior recognition

When a problem asks for:

```text
largest
second largest
top 2
two highest
two smallest
top K
```

you should immediately think:

```text
TRACK MULTIPLE BEST VALUES
```

For today's problem:

```text
largest
second_largest
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer array, find the **second largest distinct element**.

### Example 1

```text
Input:
[10, 5, 20, 8, 15]

Largest = 20
Second largest = 15
```

Answer:

```text
15
```

---

### Example 2

```text
Input:
[10, 20, 20, 5]
```

Distinct values:

```text
5, 10, 20
```

Therefore:

```text
Answer = 10
```

---

### Example 3

```text
[5, 5, 5]
```

There is only one distinct value.

Therefore:

```text
No second largest distinct value
```

Our implementation will return:

```text
None
```

The interviewer may specify another sentinel such as `-1`.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a leaderboard.

We maintain:

```text
🥇 First place
🥈 Second place
```

Suppose the scores arrive:

```text
10
5
20
8
15
```

---

## First score: 10

Nobody exists yet.

So:

```text
largest = 10
second = None
```

---

## Second score: 5

5 is less than 10.

Therefore:

```text
largest = 10
second = 5
```

---

## Third score: 20

20 beats the current champion.

The old champion becomes second:

```text
second = 10
largest = 20
```

This is the critical operation:

```python
second = largest
largest = num
```

---

## Fourth score: 8

8 does not beat 20.

Could it become second?

Current second is 10.

```text
8 > 10?
No.
```

Therefore:

```text
second = 10
```

---

## Fifth score: 15

15 doesn't beat 20.

But:

```text
15 > 10
```

So:

```text
second = 15
```

Final:

```text
largest = 20
second = 15
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

We maintain two variables:

```text
largest
second
```

---

## Step 1 — Initialize

Use:

```python
largest = None
second = None
```

Why not zero?

Because the array can contain negative values.

---

## Step 2 — Read each number

For every `num`:

```python
for num in arr:
```

---

## Step 3 — Is it a new largest?

Check:

```python
if largest is None or num > largest:
```

If yes:

```python
second = largest
largest = num
```

Why?

Because the old largest becomes the new second largest.

---

## Step 4 — Otherwise, could it become second largest?

We need:

```text
num < largest
```

because if:

```text
num == largest
```

it is a duplicate and therefore not distinct.

Then:

```text
num > second
```

means it beats the current second largest.

So:

```python
elif num != largest and (second is None or num > second):
```

update:

```python
second = num
```

---

## Step 5 — Ignore duplicates

Example:

```text
largest = 20
num = 20
```

Do nothing.

Why?

Because:

```text
20
```

is already represented as the largest distinct value.

---

## Step 6 — Return second

At the end:

```python
return second
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def second_largest(arr):

    # No largest value exists yet
    largest = None

    # No second-largest value exists yet
    second = None

    # Scan every element
    for num in arr:

        # Case 1:
        # Current number is larger than the current largest
        if largest is None or num > largest:

            # Old largest becomes second largest
            second = largest

            # Current number becomes new largest
            largest = num

        # Case 2:
        # Current number is distinct from largest
        # and can become second largest
        elif num != largest and (second is None or num > second):

            second = num

    return second


arr = [10, 5, 20, 8, 15]

answer = second_largest(arr)

print("Second largest distinct:", answer)
```

### Output

```text
Second largest distinct: 15
```

---

# 🔥 Why this solution is powerful

It does **not**:

```text
sort
```

It does **not**:

```text
create another array
```

It does **not**:

```text
create a set
```

It only tracks:

```text
largest
second
```

Therefore:

```text
One pass
O(1) auxiliary space
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static Integer secondLargest(int[] arr) {

        // No largest value initially
        Integer largest = null;

        // No second-largest value initially
        Integer second = null;

        // Scan every element
        for (int num : arr) {

            // Current number becomes the new largest
            if (largest == null || num > largest) {

                // Old largest becomes second largest
                second = largest;

                // Update largest
                largest = num;
            }

            // Current number is distinct
            // and can become second largest
            else if (num != largest &&
                     (second == null || num > second)) {

                second = num;
            }
        }

        return second;
    }

    public static void main(String[] args) {

        int[] arr = {10, 5, 20, 8, 15};

        Integer answer = secondLargest(arr);

        System.out.println("Second largest distinct: " + answer);
    }
}
```

### Output

```text
Second largest distinct: 15
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
arr = [10, 5, 20, 8, 15]
```

Initial:

```text
largest = None
second = None
```

---

## 🔵 Step 1 — `num = 10`

Check:

```text
largest is None
```

True.

Therefore:

```text
second = None
largest = 10
```

State:

```text
largest = 10
second  = None
```

---

## 🔵 Step 2 — `num = 5`

Check:

```text
5 > 10?
No.
```

Now:

```text
5 != 10
```

True.

Since `second` is currently `None`, 5 becomes second:

```text
largest = 10
second = 5
```

---

## 🔵 Step 3 — `num = 20`

Check:

```text
20 > 10?
Yes.
```

Therefore:

```text
second = largest
```

So:

```text
second = 10
```

Then:

```text
largest = 20
```

State:

```text
largest = 20
second = 10
```

---

## 🔵 Step 4 — `num = 8`

Check:

```text
8 > 20?
No.
```

Check:

```text
8 != 20?
Yes.
```

Check:

```text
8 > 10?
No.
```

No update.

State:

```text
largest = 20
second = 10
```

---

## 🔵 Step 5 — `num = 15`

Check:

```text
15 > 20?
No.
```

Check:

```text
15 != 20?
Yes.
```

Check:

```text
15 > 10?
Yes.
```

Therefore:

```text
second = 15
```

Final:

```text
largest = 20
second = 15
```

### Answer

```text
15
```

---

# 🔥 DUPLICATE DRY RUN

Input:

```text
[10, 20, 20, 5]
```

| Step | Current | Largest | Second | Action             |
| ---: | ------: | ------: | -----: | ------------------ |
|    1 |      10 |      10 |      — | First value        |
|    2 |      20 |      20 |     10 | New largest        |
|    3 |      20 |      20 |     10 | Duplicate → ignore |
|    4 |       5 |      20 |     10 | Too small          |

Final:

```text
largest = 20
second = 10
```

Answer:

```text
10
```

---

# 🔥 ALL-EQUAL DRY RUN

Input:

```text
[7, 7, 7]
```

### First 7

```text
largest = 7
second = None
```

### Second 7

```text
7 > 7 → No
7 != 7 → No
```

Ignore.

### Third 7

Same.

Final:

```text
largest = 7
second = None
```

Therefore:

```text
No second distinct element
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
int[] arr = {10, 20, 20, 5};
```

Initial:

```text
largest = null
second = null
```

---

### Iteration 1

```text
num = 10
```

New largest:

```text
largest = 10
second = null
```

---

### Iteration 2

```text
num = 20
```

Since:

```text
20 > 10
```

old largest becomes second:

```text
second = 10
largest = 20
```

---

### Iteration 3

```text
num = 20
```

Check:

```text
20 > 20 → false
20 != 20 → false
```

Ignore.

---

### Iteration 4

```text
num = 5
```

Check:

```text
5 > 20 → false
5 != 20 → true
5 > 10 → false
```

Ignore.

Final:

```text
largest = 20
second = 10
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of elements
```

We inspect each element once.

Therefore:

```text
Time = O(n)
```

We maintain only:

```text
largest
second
num
```

These are constant-size variables.

Therefore:

```text
Auxiliary Space = O(1)
```

---

## Compare three approaches

### Approach 1 — Sort

```python
sorted(arr)
```

Time:

```text
O(n log n)
```

---

### Approach 2 — Set + Sort

```python
sorted(set(arr))
```

Time:

```text
O(n log n)
```

and additional space:

```text
O(n)
```

---

### Approach 3 — One-pass tracking

```text
largest
second
```

Time:

```text
O(n)
```

Space:

```text
O(1)
```

For this specific problem, the one-pass solution gives the optimal asymptotic complexity.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can't we simply use the second-last element after sorting?

You can if duplicates are handled correctly, but sorting is unnecessary.

The question only asks for two values.

We can maintain those values during one scan.

---

### Q2. Why can't we simply do this?

```python
largest = max(arr)
second = max(x for x in arr if x != largest)
```

It can work, but it requires multiple passes.

The one-pass solution is more efficient:

```text
O(n)
```

with constant auxiliary space.

---

### Q3. Why is `num != largest` necessary?

Consider:

```text
[10, 20, 20, 5]
```

After seeing the first `20`:

```text
largest = 20
second = 10
```

When the next `20` appears:

```text
num == largest
```

It is a duplicate.

If we allowed it to update `second`, we'd incorrectly get:

```text
second = 20
```

But the problem asks for a **distinct** second largest value.

---

### Q4. What if there are only two distinct values?

Example:

```text
[5, 5, 10, 10, 10]
```

Distinct values:

```text
5, 10
```

Answer:

```text
5
```

Our algorithm correctly produces:

```text
largest = 10
second = 5
```

---

### Q5. What if all values are negative?

Example:

```text
[-10, -5, -20, -8]
```

Largest:

```text
-5
```

Second largest:

```text
-8
```

The `None` initialization handles this correctly.

---

### Q6. What if the array is empty?

There is no largest or second-largest value.

The implementation assumes a valid input array.

In a real interview, clarify the expected behavior for empty input rather than inventing one.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🧠 PATTERN — TOP-2 TRACKING

This is the main pattern of Problem 43.

Instead of:

```text
track one answer
```

we track:

```text
rank 1 → largest
rank 2 → second
```

---

## Core state

```text
largest
second
```

---

## Core transitions

### New largest

```text
new > largest
```

Then:

```text
second = largest
largest = new
```

---

### New second

```text
new < largest
AND
new > second
AND
new != largest
```

Then:

```text
second = new
```

---

### Duplicate

```text
new == largest
```

Ignore.

---

## Recognition trigger

Whenever you see:

```text
second largest
second smallest
top two
two highest
two lowest
```

think:

```text
MULTI-VALUE TRACKING
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

## ❌ Mistake 1 — Initialize with zero

```python
largest = 0
second = 0
```

Fails for:

```text
[-10, -5, -20]
```

---

## ❌ Mistake 2 — Forget distinctness

For:

```text
[10, 20, 20, 5]
```

incorrect:

```text
20
```

correct:

```text
10
```

---

## ❌ Mistake 3 — Forget the old largest

Wrong:

```python
if num > largest:
    largest = num
```

You lose the old largest.

Correct:

```python
second = largest
largest = num
```

---

## ❌ Mistake 4 — Use sorting immediately

```python
sorted(set(arr))
```

Works but misses the intended one-pass pattern.

---

## ❌ Mistake 5 — Confuse second largest with second element

For:

```text
[100, 2, 50, 80]
```

The second element is:

```text
2
```

but the second largest is:

```text
80
```

Array position has nothing to do with ranking.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Maintain two variables—`largest` and `second`—while scanning the array once. When a new largest appears, move the old largest into second place. Ignore duplicate values so that the second value remains distinct.**

```text
Time  → O(n)
Space → O(1)
Pattern → Top-2 Tracking
```

---

# 🧠 DAY 5 SESSION 1 — DEEP PATTERN CONNECTION

These three problems should now look like **one family**, not three separate questions.

---

## LEVEL 1 — ONE MAXIMUM

```python
largest = arr[0]

for x in arr:
    if x > largest:
        largest = x
```

Pattern:

```text
RUNNING MAXIMUM
```

---

## LEVEL 2 — ONE MINIMUM

```python
smallest = arr[0]

for x in arr:
    if x < smallest:
        smallest = x
```

Pattern:

```text
RUNNING MINIMUM
```

---

## LEVEL 3 — TOP TWO

```python
largest = None
second = None
```

Then maintain both.

Pattern:

```text
TOP-2 TRACKING
```

---

# 🔥 THE REAL SKILL

You should mentally transform:

```text
Find largest
```

into:

```text
Maintain maximum while scanning.
```

Transform:

```text
Find smallest
```

into:

```text
Maintain minimum while scanning.
```

Transform:

```text
Find second largest
```

into:

```text
Maintain top two distinct values while scanning.
```

That is the actual placement skill.

---

# 🧪 SESSION 1 — GUIDED PRACTICE

## Problem A — Largest

```text
[4, 17, 2, 99, 31, 8]
```

Expected:

```text
99
```

Your state should evolve:

```text
4
↓
17
↓
17
↓
99
↓
99
↓
99
```

---

## Problem B — Smallest

```text
[12, -4, 7, -20, 3]
```

Expected:

```text
-20
```

---

## Problem C — Second Largest Distinct

```text
[7, 3, 9, 9, 5, 8]
```

Distinct values:

```text
3, 5, 7, 8, 9
```

Answer:

```text
8
```

---

## Problem D — Duplicate Stress Test

```text
[10, 10, 20, 20, 5, 20]
```

Distinct values:

```text
5, 10, 20
```

Answer:

```text
10
```

---

## Problem E — Negative Numbers

```text
[-10, -3, -25, -7, -3]
```

Largest:

```text
-3
```

Second largest distinct:

```text
-7
```

---

# 🔴 NO-SOLUTION MASTER TEST

Now close the solution.

Write all three functions completely from memory.

### TEST 1

```text
Find the largest element:

[23, 7, 91, 45, 12, 88]
```

Expected:

```text
91
```

---

### TEST 2

```text
Find the smallest element:

[-3, -17, 5, -9, 2]
```

Expected:

```text
-17
```

---

### TEST 3

```text
Find the second largest DISTINCT element:

[12, 45, 7, 45, 32, 18]
```

Expected:

```text
32
```

---

### TEST 4 — Edge Case

```text
[5, 5, 5]
```

What is the second largest **distinct** element?

Answer:

```text
None
```

unless the problem specifies another return value.

---

### TEST 5 — Negative Edge Case

```text
[-100, -50, -20, -50, -10]
```

Find:

```text
largest
second largest distinct
```

Expected:

```text
largest = -10
second = -20
```

---

# 🔥 VARIATION DRILL

Now change the problem yourself:

## Variation 1

Find the **second smallest distinct** element.

```text
[8, 3, 5, 3, 1, 8]
```

Answer:

```text
3
```

Your mental transformation:

```text
largest
   ↓
smallest

second largest
   ↓
second smallest
```

---

## Variation 2

Find the **largest and smallest simultaneously**.

```text
[7, -3, 20, 4, -10, 8]
```

Expected:

```text
largest = 20
smallest = -10
```

You can do both in **one pass**.

---

# 🧠 CR2 MASTERY CHECK

For Problems 41–43:

| Level              | Meaning                                                             |
| ------------------ | ------------------------------------------------------------------- |
| 🟢 **Understood**  | You understand the explanation                                      |
| 🟡 **Reproduced**  | You can rewrite the solution while looking at the pattern           |
| 🟠 **Independent** | You can solve unseen examples without help                          |
| 🔴 **Mastered**    | You can solve variations and explain complexity/interview reasoning |

### Do NOT mark these mastered just because you read this session.

The actual target is:

```text
Read
 ↓
Understand
 ↓
Close solution
 ↓
Code from memory
 ↓
Pass edge cases
 ↓
Solve variation
 ↓
Explain to interviewer
```

---

# 📊 DAY 5 PROGRESS

```text
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅
DAY 3 → 10/10 ✅
DAY 4 → 10/10 ✅

DAY 5
41 → Largest Element              🟡/🟠
42 → Smallest Element             🟡/🟠
43 → Second Largest Distinct      🟡/🟠

TOTAL → 43/100
```

# 🎯 SESSION 1 FINAL TAKEAWAY

```text
41. Largest
        ↓
Running Maximum
        ↓
One best value

42. Smallest
        ↓
Running Minimum
        ↓
One best value

43. Second Largest Distinct
        ↓
Top-2 Tracking
        ↓
Two best values
```

## 🔥 THE ONE SENTENCE TO REMEMBER

> **Don't think "How do I find the answer?" Think "What information must I maintain while scanning the array so the answer is always available?"**

That mindset is what turns these from **basic placement questions** into the foundation of real DSA pattern recognition.

**Next locked session:** **Day 5 Session 2 → 44. Reverse Array In-Place + 45. Sum & Average of Array + 46. Count Even & Odd Elements.**


# 🔥 CR2 — DAY 5 — SESSION 2

# ARRAY FUNDAMENTALS — PROBLEMS 44–46

We continue with the **locked CR2 execution depth**.

Today we move from simple **value tracking** to **array manipulation + aggregation + classification**.

---

## 🎯 SESSION 2

| #      | Problem                   | Exact LeetCode Match       | Difficulty | Core Pattern              |
| ------ | ------------------------- | -------------------------- | ---------- | ------------------------- |
| **44** | Reverse Array In-Place    | ❌ No exact canonical match | Basic      | Two Pointers              |
| **45** | Sum & Average of Array    | ❌ No exact canonical match | Basic      | Running Sum               |
| **46** | Count Even & Odd Elements | ❌ No exact canonical match | Basic      | Classification + Counting |

### Today's progression

```text
41 → Track ONE best value
42 → Track ONE best value
43 → Track TWO best values

44 → Rearrange elements
45 → Aggregate elements
46 → Classify + count elements
```

---

# 🟢 PROBLEM 44 — REVERSE ARRAY IN-PLACE

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

## 1. What is the actual skill?

The problem says:

> Reverse the array **in-place**.

The critical phrase is:

# `IN-PLACE`

That means:

> Modify the original array instead of creating another array containing the reversed result.

Example:

```text
Before:
[1, 2, 3, 4, 5]

After:
[5, 4, 3, 2, 1]
```

---

## 2. First instinct

A beginner may write:

```python
arr.reverse()
```

or:

```python
arr[::-1]
```

Those are useful Python operations, but they hide the actual algorithm.

For placement coding, you should understand the underlying pattern:

# TWO POINTERS

We place:

```text
left  → beginning
right → end
```

Then swap them.

---

## 3. Why two pointers?

Consider:

```text
[1, 2, 3, 4, 5]
 ↑           ↑
left        right
```

The first element belongs at the last position.

The last element belongs at the first position.

So:

```text
1 ↔ 5
```

Then:

```text
[5, 2, 3, 4, 1]
```

Move inward:

```text
   ↑       ↑
  left   right
```

Swap:

```text
2 ↔ 4
```

Result:

```text
[5, 4, 3, 2, 1]
```

The middle element does not need to move.

---

## 4. Senior pattern recognition

Whenever you see:

* reverse array
* reverse string
* swap from both ends
* palindrome
* compare beginning and ending
* process from both sides

think:

```text
TWO POINTERS
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, reverse it **without creating another array**.

### Example

Input:

```text
[10, 20, 30, 40, 50]
```

Output:

```text
[50, 40, 30, 20, 10]
```

---

## What does "in-place" mean?

We start with:

```text
arr = [10, 20, 30, 40, 50]
```

and modify that same array.

We don't create:

```text
reversed_arr = [50, 40, 30, 20, 10]
```

Instead:

```text
arr itself
```

becomes:

```text
[50, 40, 30, 20, 10]
```

---

## Important edge cases

### Empty array

```text
[]
```

remains:

```text
[]
```

### One element

```text
[7]
```

remains:

```text
[7]
```

### Two elements

```text
[1, 2]
```

becomes:

```text
[2, 1]
```

### Odd length

```text
[1, 2, 3, 4, 5]
```

The middle `3` stays where it is.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a row of people.

You want the person at the left to move to the right, and the person at the right to move to the left.

Start:

```text
[1, 2, 3, 4, 5]
 ↑           ↑
 L           R
```

Swap:

```text
[5, 2, 3, 4, 1]
```

Move pointers inward:

```text
[5, 2, 3, 4, 1]
    ↑       ↑
    L       R
```

Swap:

```text
[5, 4, 3, 2, 1]
```

Move again:

```text
[5, 4, 3, 2, 1]
       ↑
      L/R
```

They meet.

Stop.

---

## Why stop when `left >= right`?

Because once the pointers meet or cross, every required pair has already been swapped.

```text
left < right
```

means:

> There is still a pair to process.

```text
left >= right
```

means:

> We're done.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Set:

```python
left = 0
```

The first index.

### Step 2

Set:

```python
right = len(arr) - 1
```

The last index.

### Step 3

While:

```python
left < right
```

perform a swap.

### Step 4

Swap:

```python
arr[left], arr[right] = arr[right], arr[left]
```

### Step 5

Move inward:

```python
left += 1
right -= 1
```

### Step 6

Return the modified array.

---

## Pseudocode

```text
left = 0
right = n - 1

while left < right:

    swap arr[left] and arr[right]

    left++
    right--

return arr
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def reverse_array(arr):

    left = 0
    right = len(arr) - 1

    while left < right:

        # Swap the elements at both ends
        arr[left], arr[right] = arr[right], arr[left]

        # Move both pointers toward the center
        left += 1
        right -= 1

    return arr


arr = [10, 20, 30, 40, 50]

result = reverse_array(arr)

print("Reversed array:", result)
```

### Output

```text
Reversed array: [50, 40, 30, 20, 10]
```

---

## Why this is genuinely in-place

We don't create:

```text
new array
```

We directly modify:

```text
arr
```

using swaps.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static void reverseArray(int[] arr) {

        int left = 0;
        int right = arr.length - 1;

        while (left < right) {

            // Swap both ends
            int temp = arr[left];
            arr[left] = arr[right];
            arr[right] = temp;

            // Move toward the center
            left++;
            right--;
        }
    }

    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40, 50};

        reverseArray(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text
[50, 40, 30, 20, 10]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
arr = [10, 20, 30, 40, 50]
```

Initial:

```text
left = 0
right = 4
```

Visual:

```text
[10, 20, 30, 40, 50]
 ↑                 ↑
 L                 R
```

---

## Step 1

Swap:

```text
10 ↔ 50
```

Array:

```text
[50, 20, 30, 40, 10]
```

Move:

```text
left = 1
right = 3
```

---

## Step 2

```text
20 ↔ 40
```

Array:

```text
[50, 40, 30, 20, 10]
```

Move:

```text
left = 2
right = 2
```

---

## Step 3

Check:

```text
left < right
2 < 2
```

False.

Stop.

---

## Full trace

|    Step | Left | Right | Swap      | Array              |
| ------: | ---: | ----: | --------- | ------------------ |
| Initial |    0 |     4 | —         | `[10,20,30,40,50]` |
|       1 |    0 |     4 | `10 ↔ 50` | `[50,20,30,40,10]` |
|       2 |    1 |     3 | `20 ↔ 40` | `[50,40,30,20,10]` |
|    Stop |    2 |     2 | None      | `[50,40,30,20,10]` |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text
arr = {10,20,30,40,50}
left = 0
right = 4
```

### Iteration 1

```text
arr[0] = 10
arr[4] = 50
```

Swap:

```text
{50,20,30,40,10}
```

Then:

```text
left = 1
right = 3
```

### Iteration 2

Swap:

```text
arr[1] = 20
arr[3] = 40
```

Result:

```text
{50,40,30,20,10}
```

Then:

```text
left = 2
right = 2
```

Stop.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For `n` elements:

Approximately half the elements are swapped.

Number of swaps:

```text
n / 2
```

Therefore:

```text
Time = O(n)
```

Why not `O(n/2)`?

Big-O ignores constant factors:

```text
O(n/2) = O(n)
```

---

## Space

We use only:

```text
left
right
temporary swap storage
```

No new array.

Therefore:

```text
Auxiliary Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

This is optimal because every element must be moved at least once in the general case.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we use two pointers?

Because we need to exchange elements symmetrically from both ends.

```text
left → beginning
right → end
```

Then move inward.

---

### Q2. Why `left < right` instead of `left <= right`?

When:

```text
left == right
```

both pointers point to the same middle element.

Swapping an element with itself is unnecessary.

---

### Q3. Can we use slicing?

Yes:

```python
arr[:] = arr[::-1]
```

This reverses the original array in-place from the caller's perspective, but internally `arr[::-1]` creates a new list.

For understanding the **true constant-space two-pointer algorithm**, use explicit swaps.

---

### Q4. What pattern does this problem teach?

```text
Two Pointers
```

Specifically:

```text
Opposite-direction two pointers
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# TWO POINTERS — OPPOSITE ENDS

Master template:

```python
left = 0
right = len(arr) - 1

while left < right:

    # process/swap arr[left], arr[right]

    left += 1
    right -= 1
```

### Recognition triggers

```text
reverse
palindrome
compare ends
swap ends
process from both sides
```

Think:

```text
TWO POINTERS
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Only moving `left`:

```python
left += 1
```

You must also move:

```python
right -= 1
```

---

### ❌ Mistake 2

Using:

```python
while left <= right:
```

Not incorrect in every implementation, but unnecessary because the middle element doesn't need swapping.

---

### ❌ Mistake 3

Creating a second array when the question explicitly says **in-place**.

---

### ❌ Mistake 4

Incorrect swap order in Java.

Use a temporary variable:

```java
int temp = arr[left];
arr[left] = arr[right];
arr[right] = temp;
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Use two pointers starting at opposite ends of the array. Swap their elements and move both pointers toward the center until they meet. This reverses the array in O(n) time and O(1) auxiliary space.**

```text
Pattern → Two Pointers
Time    → O(n)
Space   → O(1)
```

---

# 🟢 PROBLEM 45 — SUM & AVERAGE OF AN ARRAY

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This looks extremely simple, but it introduces another fundamental array pattern:

# RUNNING SUM / ACCUMULATION

The idea is:

```text
sum = 0

for every number:
    sum += number
```

You're continuously accumulating information.

This same idea becomes important later for:

* prefix sums
* subarray problems
* averages
* cumulative statistics
* numerical ML preprocessing
* streaming data

---

## Important distinction

The sum requires:

```text
integer accumulation
```

The average requires:

```text
sum / number_of_elements
```

So don't repeatedly calculate the average during the loop unless necessary.

First calculate:

```text
sum
```

then:

```text
average
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array:

```text
[10, 20, 30, 40]
```

find:

```text
Sum = 100
Average = 25
```

Because:

```text
10 + 20 + 30 + 40 = 100
```

and:

```text
100 / 4 = 25
```

---

## Formula

### Sum

```text
sum = x₁ + x₂ + ... + xₙ
```

### Average

```text
average = sum / n
```

---

## Important edge case

For:

```text
[]
```

average is undefined because:

```text
0 elements
```

and division by zero is invalid.

In an interview, clarify expected behavior.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine collecting marks from students.

Scores:

```text
10
20
30
40
```

Start:

```text
sum = 0
```

Add 10:

```text
sum = 10
```

Add 20:

```text
sum = 30
```

Add 30:

```text
sum = 60
```

Add 40:

```text
sum = 100
```

Then:

```text
average = 100 / 4
        = 25
```

The variable `sum` represents:

> **the total of everything processed so far.**

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Initialize:

```python
total = 0
```

### Step 2

Scan every element.

### Step 3

Add each number:

```python
total += num
```

### Step 4

Count elements.

We already know:

```python
n = len(arr)
```

### Step 5

Calculate:

```python
average = total / n
```

### Step 6

Return both.

---

## Pseudocode

```text
total = 0

for every number:
    total += number

average = total / number_of_elements

return total, average
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def sum_and_average(arr):

    total = 0

    for num in arr:
        total += num

    if len(arr) == 0:
        return 0, None

    average = total / len(arr)

    return total, average


arr = [10, 20, 30, 40]

total, average = sum_and_average(arr)

print("Sum:", total)
print("Average:", average)
```

### Output

```text
Sum: 100
Average: 25.0
```

---

## Why `25.0`?

Python `/` performs floating-point division.

```python
100 / 4
```

produces:

```text
25.0
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static void sumAndAverage(int[] arr) {

        if (arr.length == 0) {
            System.out.println("Array is empty.");
            return;
        }

        long total = 0;

        for (int num : arr) {
            total += num;
        }

        double average = (double) total / arr.length;

        System.out.println("Sum: " + total);
        System.out.println("Average: " + average);
    }

    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40};

        sumAndAverage(arr);
    }
}
```

### Output

```text
Sum: 100
Average: 25.0
```

---

## Why `long total`?

For basic placement arrays, `int` may be enough.

But if the array contains many large integers, the sum can exceed the `int` range even when individual elements fit inside an `int`.

Using:

```java
long total
```

makes the accumulation safer.

This is a useful interview-level detail.

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[10, 20, 30, 40]
```

Initial:

```text
total = 0
```

| Step | Current | Total Before | Operation | Total After |
| ---: | ------: | -----------: | --------- | ----------: |
|    1 |      10 |            0 | `0 + 10`  |          10 |
|    2 |      20 |           10 | `10 + 20` |          30 |
|    3 |      30 |           30 | `30 + 30` |          60 |
|    4 |      40 |           60 | `60 + 40` |         100 |

Then:

```text
n = 4
```

Average:

```text
100 / 4 = 25
```

Final:

```text
sum = 100
average = 25.0
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text
total = 0
```

### `num = 10`

```text
total = 10
```

### `num = 20`

```text
total = 30
```

### `num = 30`

```text
total = 60
```

### `num = 40`

```text
total = 100
```

Then:

```text
average = (double)100 / 4
        = 25.0
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For `n` elements:

Every element is processed once.

Therefore:

```text
Time = O(n)
```

Only:

```text
total
```

and a few scalar variables are maintained.

Therefore:

```text
Auxiliary Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why calculate sum first?

Because:

```text
average = sum / count
```

The sum is the required intermediate result.

---

### Q2. What happens with an empty array?

Average is undefined because:

```text
count = 0
```

Therefore:

```text
sum = 0
average = undefined
```

Our Python solution returns:

```text
(0, None)
```

---

### Q3. Why does Java use `double` for average?

Because an average may contain a fractional value.

Example:

```text
[10, 20, 21]
```

Sum:

```text
51
```

Average:

```text
17.0
```

Another:

```text
[10, 20]
```

Average:

```text
15.0
```

And:

```text
[1, 2]
```

Average:

```text
1.5
```

Therefore floating-point representation is appropriate.

---

### Q4. Why use `long` for Java sum?

Because:

```text
sum of many int values
```

can overflow an `int`.

Using:

```java
long total
```

reduces that risk.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# RUNNING SUM / ACCUMULATION

Template:

```python
total = 0

for x in arr:
    total += x
```

Recognition triggers:

```text
sum
total
cumulative
aggregate
count
```

Think:

```text
ACCUMULATOR
```

This pattern later becomes:

```text
Prefix Sum
Running Total
Subarray Sum
Cumulative Statistics
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Starting with:

```python
total = 1
```

Sum accumulation should start at:

```python
total = 0
```

---

### ❌ Mistake 2

Dividing by zero for an empty array.

---

### ❌ Mistake 3

Integer division when a fractional average is required.

In Python:

```python
total // len(arr)
```

would discard the decimal part.

---

### ❌ Mistake 4

Using unnecessary sorting.

The array doesn't need to be sorted.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Scan the array once while accumulating the total, then divide the total by the number of elements to calculate the average.**

```text
Time  → O(n)
Space → O(1)
Pattern → Running Sum / Accumulation
```

---

# 🟢 PROBLEM 46 — COUNT EVEN & ODD ELEMENTS

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem introduces:

# CLASSIFICATION + COUNTING

Every number belongs to one of two categories:

```text
Even
Odd
```

We classify each number using:

```python
num % 2
```

If:

```text
num % 2 == 0
```

the number is even.

Otherwise:

```text
odd
```

Then maintain two counters:

```text
even_count
odd_count
```

---

## Why is this useful?

This pattern appears everywhere:

```text
positive vs negative
even vs odd
vowels vs consonants
valid vs invalid
zero vs non-zero
matching vs non-matching
```

The general pattern is:

```text
READ
 ↓
CLASSIFY
 ↓
COUNT
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, count how many elements are:

* even
* odd

Example:

```text
[1, 2, 3, 4, 6]
```

Even:

```text
2, 4, 6
```

Count:

```text
3
```

Odd:

```text
1, 3
```

Count:

```text
2
```

Output:

```text
Even = 3
Odd = 2
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine putting numbers into two boxes:

```text
┌─────────────┐
│ EVEN BOX    │
└─────────────┘

┌─────────────┐
│ ODD BOX     │
└─────────────┘
```

Take:

```text
7
```

Check:

```text
7 % 2 = 1
```

So it goes into:

```text
ODD
```

Take:

```text
12
```

Check:

```text
12 % 2 = 0
```

So it goes into:

```text
EVEN
```

We don't actually need to create boxes or arrays.

We only need counters:

```text
even_count
odd_count
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Initialize:

```python
even_count = 0
odd_count = 0
```

### Step 2

Scan each number.

### Step 3

Check:

```python
if num % 2 == 0:
```

### Step 4

If even:

```python
even_count += 1
```

### Step 5

Otherwise:

```python
odd_count += 1
```

### Step 6

Return both counts.

---

## Pseudocode

```text
even = 0
odd = 0

for each number:

    if number % 2 == 0:
        even++
    else:
        odd++

return even, odd
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def count_even_odd(arr):

    even_count = 0
    odd_count = 0

    for num in arr:

        # Even numbers have remainder 0
        # when divided by 2
        if num % 2 == 0:
            even_count += 1

        # Everything else is odd
        else:
            odd_count += 1

    return even_count, odd_count


arr = [1, 2, 3, 4, 6]

even, odd = count_even_odd(arr)

print("Even:", even)
print("Odd:", odd)
```

### Output

```text
Even: 3
Odd: 2
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static void countEvenOdd(int[] arr) {

        int evenCount = 0;
        int oddCount = 0;

        for (int num : arr) {

            // Even if remainder is 0
            if (num % 2 == 0) {
                evenCount++;
            }

            // Otherwise odd
            else {
                oddCount++;
            }
        }

        System.out.println("Even: " + evenCount);
        System.out.println("Odd: " + oddCount);
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 3, 4, 6};

        countEvenOdd(arr);
    }
}
```

### Output

```text
Even: 3
Odd: 2
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[1, 2, 3, 4, 6]
```

Initial:

```text
even_count = 0
odd_count = 0
```

| Step | Number | `num % 2` | Classification | Even | Odd |
| ---: | -----: | --------: | -------------- | ---: | --: |
|    1 |      1 |         1 | Odd            |    0 |   1 |
|    2 |      2 |         0 | Even           |    1 |   1 |
|    3 |      3 |         1 | Odd            |    1 |   2 |
|    4 |      4 |         0 | Even           |    2 |   2 |
|    5 |      6 |         0 | Even           |    3 |   2 |

Final:

```text
Even = 3
Odd = 2
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text
evenCount = 0
oddCount = 0
```

### `num = 1`

```text
1 % 2 = 1
```

Odd:

```text
oddCount = 1
```

### `num = 2`

```text
2 % 2 = 0
```

Even:

```text
evenCount = 1
```

### `num = 3`

Odd:

```text
oddCount = 2
```

### `num = 4`

Even:

```text
evenCount = 2
```

### `num = 6`

Even:

```text
evenCount = 3
```

Final:

```text
Even = 3
Odd = 2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For `n` elements:

Every number must be inspected.

Therefore:

```text
Time = O(n)
```

Only two counters are maintained:

```text
even_count
odd_count
```

Therefore:

```text
Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. How do you determine if a number is even?

Use:

```python
num % 2 == 0
```

The remainder is zero.

---

### Q2. What about negative numbers?

The same rule works.

```text
-4 % 2 = 0
```

So `-4` is even.

```text
-5 % 2 != 0
```

So `-5` is odd.

---

### Q3. What about zero?

Zero is even.

```text
0 % 2 = 0
```

Therefore it increments:

```text
even_count
```

---

### Q4. Can we count only even numbers?

Yes:

```python
count = 0

for num in arr:
    if num % 2 == 0:
        count += 1
```

But this problem specifically asks for both counts, so maintain both counters.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# CLASSIFY + COUNT

General template:

```python
count_a = 0
count_b = 0

for x in arr:

    if condition(x):
        count_a += 1
    else:
        count_b += 1
```

Examples:

```text
Even / Odd
Positive / Negative
Vowel / Consonant
Valid / Invalid
Zero / Non-zero
```

Recognition trigger:

```text
"How many elements satisfy condition X?"
```

Think:

```text
SCAN + CONDITION + COUNTER
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
num / 2 == 0
```

Wrong.

Division is not the test.

Use:

```python
num % 2 == 0
```

---

### ❌ Mistake 2

Forgetting zero.

Zero is even.

---

### ❌ Mistake 3

Creating separate arrays unnecessarily:

```python
even_numbers = []
odd_numbers = []
```

The question asks for counts, so storing all values is unnecessary.

---

### ❌ Mistake 4

Using bitwise operations before understanding modulo.

You can test evenness using:

```python
num & 1
```

but `% 2` is clearer for this beginner placement problem.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Scan each array element, classify it using `num % 2`, and increment either the even or odd counter. This requires one pass and constant auxiliary space.**

```text
Time  → O(n)
Space → O(1)
Pattern → Classification + Counting
```

---

# 🔥 DAY 5 — SESSION 2 — MASTER PATTERN CONNECTION

Today's three problems are actually three different ways of processing an array.

---

## 44 — TRANSFORMATION

```text
Input
 ↓
Modify positions
 ↓
Output
```

Pattern:

```text
TWO POINTERS
```

---

## 45 — AGGREGATION

```text
Input
 ↓
Accumulate values
 ↓
Sum
 ↓
Average
```

Pattern:

```text
RUNNING SUM
```

---

## 46 — CLASSIFICATION

```text
Input
 ↓
Check condition
 ↓
Classify
 ↓
Count
```

Pattern:

```text
CONDITION + COUNTER
```

---

# 🧠 THE THREE PATTERNS YOU SHOULD REMEMBER

```text
44. Reverse Array
        ↓
   TWO POINTERS
        ↓
   modify in-place


45. Sum & Average
        ↓
   ACCUMULATOR
        ↓
   total information


46. Even & Odd
        ↓
CLASSIFY + COUNT
        ↓
   frequency/count
```

---

# 🧪 SESSION 2 — GUIDED PRACTICE

## Q1 — Reverse

```text
[1, 2, 3, 4, 5, 6]
```

Expected:

```text
[6, 5, 4, 3, 2, 1]
```

---

## Q2 — Reverse With Negatives

```text
[-10, 5, 0, 20, -3]
```

Expected:

```text
[-3, 20, 0, 5, -10]
```

---

## Q3 — Sum & Average

```text
[10, 20, 30, 40, 50]
```

Expected:

```text
Sum = 150
Average = 30
```

---

## Q4 — Sum With Negative Values

```text
[-10, 20, -5, 15]
```

Expected:

```text
Sum = 20
Average = 5
```

---

## Q5 — Even/Odd

```text
[1, 2, 3, 4, 5, 6, 7, 8]
```

Expected:

```text
Even = 4
Odd = 4
```

---

## Q6 — Edge Case

```text
[0, -2, -3, 7, 10]
```

Expected:

```text
Even = 3
Odd = 2
```

Remember:

```text
0 → EVEN
```

---

# 🔴 NO-SOLUTION MASTER TEST

Close the solution and code these from scratch.

## TEST 1 — Reverse In-Place

```text
Input:
[11, 22, 33, 44, 55, 66]

Expected:
[66, 55, 44, 33, 22, 11]
```

Requirements:

```text
No second array.
Use two pointers.
```

---

## TEST 2 — Sum + Average

```text
Input:
[5, 10, 15, 20, 25]

Expected:
Sum = 75
Average = 15.0
```

---

## TEST 3 — Even/Odd

```text
Input:
[12, 7, 8, 3, 10, 15, 0]

Expected:
Even = 4
Odd = 3
```

---

## TEST 4 — Combined Challenge

Given:

```text
[8, -3, 10, 7, 0, -2, 15]
```

Find:

```text
1. Reverse the array in-place
2. Sum
3. Average
4. Even count
5. Odd count
```

Expected:

```text
Reversed:
[15, -2, 0, 7, 10, -3, 8]

Sum:
35

Average:
5.0

Even:
4

Odd:
3
```

---

# 🔥 VARIATION DRILL

## Variation 1 — Reverse String

The same two-pointer pattern can reverse:

```text
"HELLO"
```

into:

```text
"OLLEH"
```

Mental transfer:

```text
Array reversal
     ↓
String reversal
     ↓
Same two-pointer idea
```

---

## Variation 2 — Count Positive/Negative

Given:

```text
[-4, 7, -2, 10, 0, -8]
```

Classify into:

```text
positive
negative
zero
```

This is the same:

```text
CLASSIFY + COUNT
```

pattern.

---

## Variation 3 — Running Sum

Given:

```text
[2, 4, 6, 8]
```

Track:

```text
2
6
12
20
```

This is the beginning of:

# PREFIX SUM

You will use this concept later in deeper DSA.

---

# 📊 DAY 5 PROGRESS

```text
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅
DAY 3 → 10/10 ✅
DAY 4 → 10/10 ✅

DAY 5 SESSION 1
41 → Largest Element
42 → Smallest Element
43 → Second Largest Distinct

DAY 5 SESSION 2
44 → Reverse Array In-Place       🟡
45 → Sum & Average                🟡
46 → Count Even & Odd             🟡

TOTAL COVERED → 46/100
```

## 🎯 Mastery requirement

Do not mark 44–46 as 🔴 merely because you understood the explanation.

You should be able to:

```text
Understand
    ↓
Reproduce
    ↓
Code without looking
    ↓
Handle edge cases
    ↓
Solve variation
    ↓
Explain to interviewer
```

### 🔥 Session 2 core memory

```text
44 → TWO POINTERS
45 → ACCUMULATOR
46 → CLASSIFY + COUNT
```

**Next: Day 5 Session 3 → Problems 47–50: Check Whether Array Is Sorted, Missing Number, Find Duplicate Element, Move Zeroes to End.**

Would you like to try the no-solution master test for Problems 44–46 before moving on to Session 3?

# 🔥 CR2 — DAY 5 — SESSION 3

# ARRAY FUNDAMENTALS → PROBLEMS 47–50

We now finish **Day 5**.

This is the most important session of Day 5 because we move from basic array scanning into four patterns that appear repeatedly in placement coding and later DSA:

```text
47 → Ordered-property checking
48 → Missing-value reasoning
49 → Duplicate-value reasoning
50 → In-place stable rearrangement
```

---

# 🎯 SESSION 3 MAP

| #      | Problem                       | Exact LeetCode Match                 | Difficulty | Core Pattern                 |
| ------ | ----------------------------- | ------------------------------------ | ---------- | ---------------------------- |
| **47** | Check Whether Array Is Sorted | ⚠️ Related: LC 1752                  | Basic      | Adjacent Comparison          |
| **48** | Missing Number                | ✅ LC 268 — Missing Number            | Easy       |                              |
| **49** | Find Duplicate Element        | ✅ LC 287 — Find the Duplicate Number | Medium     |                              |
| **50** | Move Zeroes to End            | ✅ LC 283 — Move Zeroes               | Easy       | Two Pointers / Write Pointer |

> **Important exact-match rule:** Problem 47 is the simple placement version: “Is this array non-decreasing?” LC 1752 asks a related but different question involving a sorted-and-rotated array, so it is **not an exact match**.

---

# 🟢 PROBLEM 47 — CHECK WHETHER ARRAY IS SORTED

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

## What is really being tested?

The question looks like:

> “Is the array sorted?”

But the actual skill is:

# **CHECK A LOCAL PROPERTY**

For a non-decreasing array:

```text
arr[i] <= arr[i + 1]
```

must be true for **every adjacent pair**.

That gives us a powerful idea:

```text
Don't compare everything with everything.
Compare neighboring elements.
```

---

## Example

```text
[2, 4, 4, 7, 10]
```

Check:

```text
2 <= 4 ✅
4 <= 4 ✅
4 <= 7 ✅
7 <= 10 ✅
```

Therefore:

```text
Sorted → True
```

Now:

```text
[2, 4, 3, 7]
```

Check:

```text
2 <= 4 ✅
4 <= 3 ❌
```

We immediately know:

```text
Not sorted
```

We don't need to inspect the remaining elements.

---

## 🚨 Senior optimization

The moment you find a violation:

```text
arr[i] > arr[i+1]
```

you can return:

```text
False
```

This is called:

# **Early Exit**

---

## Important distinction

Usually, “sorted” in placement problems means:

```text
Non-decreasing
```

meaning:

```text
a <= b
```

Duplicates are allowed.

Example:

```text
[1, 2, 2, 3]
```

is sorted.

If the problem says **strictly increasing**, then the condition changes to:

```text
a < b
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, determine whether it is sorted in **non-decreasing order**.

### Example 1

```text
[1, 2, 3, 4, 5]
```

Output:

```text
True
```

---

### Example 2

```text
[1, 2, 2, 4]
```

Output:

```text
True
```

Duplicates are allowed.

---

### Example 3

```text
[1, 3, 2, 4]
```

Output:

```text
False
```

because:

```text
3 > 2
```

---

### Example 4

```text
[5, 4, 3, 2]
```

Output:

```text
False
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine walking up stairs.

A sorted array means:

```text
Every next step is the same height or higher.
```

For:

```text
[2, 4, 4, 8]
```

we have:

```text
2 → 4  ↑
4 → 4  →
4 → 8  ↑
```

Never goes down.

Therefore sorted.

But:

```text
[2, 6, 4, 9]
```

has:

```text
2 → 6 ↑
6 → 4 ↓  ❌
```

The moment we go downward:

```text
NOT SORTED
```

---

## Mental model

```text
arr[i]       arr[i+1]
   ↓             ↓
  current      next
       \       /
        compare
           ↓
      current > next?
        /       \
      YES        NO
       ↓          ↓
     False      continue
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Start from index `0`.

### Step 2

Compare:

```python
arr[i]
```

with:

```python
arr[i + 1]
```

### Step 3

If:

```python
arr[i] > arr[i + 1]
```

the array is not sorted.

Return:

```python
False
```

### Step 4

Otherwise continue.

### Step 5

If the entire array passes:

```python
return True
```

---

## Pseudocode

```text
for i from 0 to n-2:

    if arr[i] > arr[i+1]:
        return False

return True
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_sorted(arr):

    # Compare every element with the next element
    for i in range(len(arr) - 1):

        # A larger element followed by a smaller one
        # means the array is not sorted
        if arr[i] > arr[i + 1]:
            return False

    # No violation was found
    return True


arr = [1, 2, 2, 4, 7]

print(is_sorted(arr))
```

### Output

```text
True
```

---

## Why `len(arr) - 1`?

Suppose:

```text
arr = [10, 20, 30, 40]
```

Valid indices:

```text
0  1  2  3
```

We compare:

```text
0 with 1
1 with 2
2 with 3
```

So the last comparison starts at:

```text
index = 2
```

Therefore:

```python
range(len(arr) - 1)
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static boolean isSorted(int[] arr) {

        // Compare every element with the next element
        for (int i = 0; i < arr.length - 1; i++) {

            // Violation of non-decreasing order
            if (arr[i] > arr[i + 1]) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {

        int[] arr = {1, 2, 2, 4, 7};

        System.out.println(isSorted(arr));
    }
}
```

### Output

```text
true
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[1, 2, 2, 4, 7]
```

### Initial

```text
i = 0
```

Compare:

```text
1 > 2?
No
```

Continue.

---

### `i = 1`

```text
2 > 2?
No
```

Equal values are allowed.

Continue.

---

### `i = 2`

```text
2 > 4?
No
```

Continue.

---

### `i = 3`

```text
4 > 7?
No
```

Reached the end.

Return:

```text
True
```

---

## Unsorted example

```text
[1, 5, 3, 8]
```

### `i = 0`

```text
1 > 5? No
```

### `i = 1`

```text
5 > 3? YES
```

Immediately:

```text
return False
```

We never need to inspect `8`.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
{1, 5, 3, 8}
```

Initial:

```text
i = 0
```

Check:

```text
arr[0] > arr[1]
1 > 5 → false
```

Next:

```text
i = 1
```

Check:

```text
5 > 3 → true
```

Therefore:

```text
return false
```

Output:

```text
false
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Worst case:

```text
[1,2,3,4,5,...]
```

We inspect every adjacent pair.

There are:

```text
n - 1
```

comparisons.

Therefore:

```text
Time = O(n)
```

We use only:

```text
i
```

and no extra data structure.

Therefore:

```text
Space = O(1)
```

### Early-exit best case

For:

```text
[5, 2, 3, 4, 5]
```

we fail immediately.

Best-case time:

```text
O(1)
```

Worst-case:

```text
O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Are duplicates allowed?

Yes, because we are checking **non-decreasing** order.

```text
[1, 2, 2, 3]
```

is sorted.

---

### Q2. What if the array is empty?

There are no adjacent pairs that violate the property.

Usually:

```text
True
```

is returned.

---

### Q3. What if the array has one element?

It is sorted.

```text
[10] → True
```

---

### Q4. What is the difference between increasing and non-decreasing?

Strictly increasing:

```text
1 < 2 < 3 < 4
```

Non-decreasing:

```text
1 <= 2 <= 2 <= 4
```

Our problem uses non-decreasing.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# ADJACENT COMPARISON

Template:

```python
for i in range(len(arr) - 1):

    if condition(arr[i], arr[i + 1]):
        return False

return True
```

Recognition triggers:

```text
sorted?
valid order?
neighbor relationship?
consecutive elements?
```

Think:

```text
ADJACENT ELEMENT CHECK
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
arr[i] < arr[i + 1]
```

This incorrectly rejects equal values.

---

### ❌ Mistake 2

Checking every pair:

```text
O(n²)
```

is unnecessary.

Only adjacent elements matter.

---

### ❌ Mistake 3

Forgetting early exit.

Once:

```text
arr[i] > arr[i+1]
```

is found, the answer is already known.

---

### ❌ Mistake 4

Confusing sorted ascending with sorted descending.

Our problem specifically checks:

```text
non-decreasing
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **An array is non-decreasing if every element is less than or equal to the element immediately after it. Scan adjacent pairs and return false at the first violation.**

```text
Time  → O(n)
Space → O(1)
Pattern → Adjacent Comparison
```

---

# 🟢 PROBLEM 48 — MISSING NUMBER

## ✅ EXACT LEETCODE MATCH: LC 268 — MISSING NUMBER

**Difficulty:** Easy

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is the first problem in today's session where there is a **direct canonical LeetCode match**.

The problem:

> Given `n` distinct numbers taken from `0` through `n`, find the one missing number.

Example:

```text
[3, 0, 1]
```

The complete range should be:

```text
0, 1, 2, 3
```

Missing:

```text
2
```

---

## The key observation

The array has:

```text
n elements
```

but the complete range:

```text
0 through n
```

contains:

```text
n + 1 numbers
```

Exactly one number is missing.

---

## Three possible approaches

### Approach 1 — Sorting

Sort and search.

```text
O(n log n)
```

Not optimal.

---

### Approach 2 — Set

Put all values into a set and search.

```text
O(n) time
O(n) space
```

Works, but uses extra memory.

---

### Approach 3 — Mathematical sum

Expected sum:

```text
n(n+1)/2
```

Then:

```text
missing = expected_sum - actual_sum
```

This gives:

```text
O(n)
```

time and:

```text
O(1)
```

extra space.

---

## But there is an important issue

In fixed-width languages like Java, the mathematical sum can overflow `int` for large `n`.

We can use:

```java
long
```

or use the XOR approach.

For this CR2 problem, we'll learn the **mathematical approach first** because the logic is easiest to understand.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array containing `n` distinct numbers from the range:

```text
0 to n
```

find the missing number.

### Example

```text
Input:
[3, 0, 1]
```

Here:

```text
n = 3
```

Expected numbers:

```text
0, 1, 2, 3
```

Actual:

```text
0, 1, 3
```

Missing:

```text
2
```

---

## Example 2

```text
[0, 1]
```

Here:

```text
n = 2
```

Expected:

```text
0, 1, 2
```

Missing:

```text
2
```

---

## Example 3

```text
[1]
```

Here:

```text
n = 1
```

Expected:

```text
0, 1
```

Missing:

```text
0
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of a classroom with numbered seats.

If there are:

```text
0, 1, 2, 3, 4
```

there should be five seats.

But you only find:

```text
0, 1, 3, 4
```

Which seat is empty?

```text
2
```

Instead of checking every number manually, calculate:

### What should the total be?

For:

```text
0 + 1 + 2 + 3 + 4
```

we get:

```text
10
```

Actual values:

```text
0 + 1 + 3 + 4 = 8
```

Difference:

```text
10 - 8 = 2
```

Therefore:

```text
missing = 2
```

---

## Formula

Sum of numbers from `0` to `n`:

```text
n(n + 1) / 2
```

Example:

```text
n = 4
```

Expected:

```text
4 × 5 / 2
= 10
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Let:

```text
n = len(nums)
```

### Step 2

Calculate expected sum:

```text
expected = n * (n + 1) // 2
```

### Step 3

Calculate actual sum:

```text
actual = sum(nums)
```

### Step 4

Subtract:

```text
missing = expected - actual
```

### Step 5

Return missing.

---

## Pseudocode

```text
n = length of array

expected = n * (n + 1) / 2

actual = sum of array

return expected - actual
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def missing_number(nums):

    n = len(nums)

    # Sum of numbers from 0 to n
    expected_sum = n * (n + 1) // 2

    # Sum of numbers actually present
    actual_sum = 0

    for num in nums:
        actual_sum += num

    # Difference is the missing number
    return expected_sum - actual_sum


nums = [3, 0, 1]

answer = missing_number(nums)

print("Missing number:", answer)
```

### Output

```text
Missing number: 2
```

---

## Python shortcut

Python can also do:

```python
return n * (n + 1) // 2 - sum(nums)
```

But for learning and interviews, understand the explicit accumulation first.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static int missingNumber(int[] nums) {

        int n = nums.length;

        // Use long to avoid integer overflow
        long expectedSum = (long) n * (n + 1) / 2;

        long actualSum = 0;

        for (int num : nums) {
            actualSum += num;
        }

        return (int) (expectedSum - actualSum);
    }

    public static void main(String[] args) {

        int[] nums = {3, 0, 1};

        int answer = missingNumber(nums);

        System.out.println("Missing number: " + answer);
    }
}
```

### Output

```text
Missing number: 2
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[3, 0, 1]
```

### Step 1

```text
n = 3
```

Expected numbers:

```text
0, 1, 2, 3
```

Expected sum:

```text
3 × 4 / 2
= 6
```

---

### Step 2 — Actual sum

Start:

```text
actual = 0
```

Read `3`:

```text
actual = 3
```

Read `0`:

```text
actual = 3
```

Read `1`:

```text
actual = 4
```

---

### Step 3

Difference:

```text
6 - 4 = 2
```

Answer:

```text
2
```

---

## Trace table

|    Step | Number | Actual Sum |
| ------: | -----: | ---------: |
| Initial |      — |          0 |
|       1 |      3 |          3 |
|       2 |      0 |          3 |
|       3 |      1 |          4 |

Expected:

```text
6
```

Actual:

```text
4
```

Missing:

```text
2
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
{3, 0, 1}
```

```text
n = 3
```

Expected:

```text
3 × 4 / 2 = 6
```

Actual:

```text
0
→ 3
→ 3
→ 4
```

Therefore:

```text
6 - 4 = 2
```

Return:

```text
2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We calculate the actual sum by scanning all `n` elements.

Therefore:

```text
Time = O(n)
```

We use only:

```text
expected_sum
actual_sum
n
```

Therefore:

```text
Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does the formula work?

Because the array contains every number from `0` to `n` except exactly one.

Therefore:

```text
expected sum - actual sum
```

leaves exactly the missing number.

---

### Q2. Why does the formula use `n`, not `n-1`?

If the array contains `n` elements, the complete range is:

```text
0 through n
```

which contains `n+1` values.

Example:

```text
n = 3
```

Range:

```text
0,1,2,3
```

---

### Q3. What if zero is missing?

Example:

```text
[1, 2, 3]
```

Here:

```text
n = 3
```

Expected:

```text
0+1+2+3 = 6
```

Actual:

```text
1+2+3 = 6
```

Difference:

```text
0
```

Correct.

---

### Q4. What if `n` itself is missing?

Example:

```text
[0,1,2,3]
```

Here:

```text
n = 4
```

Expected:

```text
10
```

Actual:

```text
6
```

Difference:

```text
4
```

Correct.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# EXPECTED TOTAL − ACTUAL TOTAL

This is a very useful mathematical pattern.

Whenever you have:

```text
complete known collection
-
actual collection
```

you may be able to identify what is missing.

Here:

```text
Expected
   -
Actual
   =
Missing
```

This exact idea appears in many basic coding problems.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```text
n(n-1)/2
```

Wrong.

Correct:

```text
n(n+1)/2
```

---

### ❌ Mistake 2

Forgetting that zero is part of the range.

---

### ❌ Mistake 3

Using `int` carelessly in Java.

For large `n`:

```java
n * (n + 1)
```

can overflow `int`.

Use:

```java
(long) n * (n + 1)
```

---

### ❌ Mistake 4

Using sorting unnecessarily.

The problem can be solved in:

```text
O(n)
```

time and:

```text
O(1)
```

space.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **The complete range is `0..n`. Calculate its expected sum using `n(n+1)/2`, subtract the actual array sum, and the difference is the missing number.**

```text
LC 268
Time  → O(n)
Space → O(1)
Pattern → Expected Total − Actual Total
```

---

# 🟠 PROBLEM 49 — FIND DUPLICATE ELEMENT

## ✅ EXACT LEETCODE MATCH: LC 287 — FIND THE DUPLICATE NUMBER

**Difficulty:** Medium

This problem is slightly more advanced than the previous three.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The basic placement problem is:

> Given an array containing numbers where one number appears more than once, find the duplicate.

But LC 287 has important constraints:

* array length is `n + 1`
* values are in `[1, n]`
* exactly one value is duplicated
* the duplicate may appear more than twice

Example:

```text
[1, 3, 4, 2, 2]
```

Answer:

```text
2
```

---

## ⚠️ Important

There are several ways to solve duplicate detection.

### Hash Set

```text
O(n) time
O(n) space
```

Easy to understand.

### Sorting

```text
O(n log n)
```

### Floyd's Cycle Detection

```text
O(n) time
O(1) space
```

LC 287 is famous because the optimal solution uses:

# **Floyd's Tortoise and Hare**

However, this is more advanced than the normal CR2 placement version.

We will first understand the **hashing solution**, then understand why the official optimal constraint-based solution is different.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Example:

```text
[1, 3, 4, 2, 2]
```

Numbers:

```text
1
3
4
2
2 ← duplicate
```

Answer:

```text
2
```

---

## Basic idea

Maintain a set:

```text
seen = {}
```

For every number:

1. If it is already in `seen`, we found the duplicate.
2. Otherwise add it to `seen`.

---

## Example

```text
[1, 3, 4, 2, 2]
```

Process:

```text
1 → not seen → add
3 → not seen → add
4 → not seen → add
2 → not seen → add
2 → already seen → DUPLICATE
```

Answer:

```text
2
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a security guard checking ID numbers.

First:

```text
ID 101 → new
ID 105 → new
ID 109 → new
ID 102 → new
ID 102 → already checked
```

The second appearance tells us:

```text
DUPLICATE
```

A set is perfect because membership checking is approximately:

```text
O(1)
```

on average.

---

## Why not compare every pair?

You could do:

```text
for i:
    for j:
```

But that requires:

```text
O(n²)
```

comparisons.

A set gives:

```text
O(n)
```

average time.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create:

```python
seen = set()
```

### Step 2

Scan every number.

### Step 3

Check:

```python
if num in seen:
```

### Step 4

If yes:

```python
return num
```

### Step 5

Otherwise:

```python
seen.add(num)
```

### Step 6

Continue.

---

## Pseudocode

```text
seen = empty set

for number:

    if number already in seen:
        return number

    add number to seen
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

For the **basic placement version**, this is the cleanest practical solution:

```python
def find_duplicate(arr):

    seen = set()

    for num in arr:

        # If already seen, this is the duplicate
        if num in seen:
            return num

        # Otherwise remember it
        seen.add(num)

    return None


arr = [1, 3, 4, 2, 2]

answer = find_duplicate(arr)

print("Duplicate:", answer)
```

### Output

```text
Duplicate: 2
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static Integer findDuplicate(int[] arr) {

        HashSet<Integer> seen = new HashSet<>();

        for (int num : arr) {

            // Already present means duplicate
            if (seen.contains(num)) {
                return num;
            }

            // Remember this number
            seen.add(num);
        }

        return null;
    }

    public static void main(String[] args) {

        int[] arr = {1, 3, 4, 2, 2};

        Integer answer = findDuplicate(arr);

        System.out.println("Duplicate: " + answer);
    }
}
```

### Output

```text
Duplicate: 2
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[1, 3, 4, 2, 2]
```

Initial:

```text
seen = {}
```

### Step 1

`num = 1`

```text
1 in seen?
No
```

Add:

```text
{1}
```

---

### Step 2

`num = 3`

```text
3 in seen?
No
```

Set:

```text
{1,3}
```

---

### Step 3

`num = 4`

Set:

```text
{1,3,4}
```

---

### Step 4

`num = 2`

Set:

```text
{1,3,4,2}
```

---

### Step 5

`num = 2`

Check:

```text
2 in seen?
Yes
```

Therefore:

```text
return 2
```

---

## Trace table

| Step | Number | Already Seen? | Set After Step | Result        |
| ---: | -----: | ------------- | -------------- | ------------- |
|    1 |      1 | No            | `{1}`          | Continue      |
|    2 |      3 | No            | `{1,3}`        | Continue      |
|    3 |      4 | No            | `{1,3,4}`      | Continue      |
|    4 |      2 | No            | `{1,3,4,2}`    | Continue      |
|    5 |      2 | Yes           | —              | Duplicate = 2 |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text
seen = {}
```

### `1`

Not found:

```text
seen = {1}
```

### `3`

```text
seen = {1,3}
```

### `4`

```text
seen = {1,3,4}
```

### `2`

```text
seen = {1,3,4,2}
```

### `2`

Already exists:

```text
return 2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We inspect each element once.

Average set lookup:

```text
O(1)
```

Therefore:

```text
Time = O(n)
```

But the set can contain up to `n` elements.

Therefore:

```text
Space = O(n)
```

### Final for hashing approach

```text
Time  → O(n) average
Space → O(n)
```

---

## But LC 287 has a stronger solution

Under the exact LC 287 constraints, we can solve it with:

```text
Time  → O(n)
Space → O(1)
```

using Floyd's cycle detection.

That solution is more advanced and is worth learning for the **deeper DSA track**.

For CR2, the important placement pattern is:

```text
DUPLICATE
   ↓
SEEN SET
   ↓
O(n) average
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a set?

Because we need to know:

> “Have I seen this number before?”

A set is designed for fast membership testing.

---

### Q2. What is the average lookup complexity of a Python set?

Approximately:

```text
O(1)
```

average.

Worst-case behavior can degrade, but interview complexity for hash-table lookup is normally described as average `O(1)`.

---

### Q3. Can we solve it without extra space?

For the **general duplicate problem**, not necessarily.

But for **LC 287's special constraints**, yes.

The famous solution is:

```text
Floyd's Cycle Detection
```

with:

```text
O(n) time
O(1) space
```

---

### Q4. Why is sorting not optimal?

Sorting takes:

```text
O(n log n)
```

while hashing gives:

```text
O(n)
```

average time.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# SEEN SET / DUPLICATE DETECTION

Template:

```python
seen = set()

for x in arr:

    if x in seen:
        return x

    seen.add(x)
```

Recognition triggers:

```text
duplicate
repeated
already seen
first repeating
unique
```

Think:

```text
HASH SET
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using nested loops immediately:

```text
O(n²)
```

---

### ❌ Mistake 2

Checking the set after inserting:

```python
seen.add(num)

if num in seen:
```

This will always find the current number.

Correct order:

```python
if num in seen:
    return num

seen.add(num)
```

---

### ❌ Mistake 3

Confusing duplicate with frequency.

The set only answers:

```text
Have I seen it?
```

If you need counts, use a dictionary/HashMap.

---

### ❌ Mistake 4

Claiming the hash-set solution is `O(1)` space.

It is:

```text
O(n)
```

space in the worst case.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Maintain a set of previously seen elements. If the current value is already in the set, it is the duplicate; otherwise add it. This gives O(n) average time and O(n) auxiliary space.**

```text
LC 287
Basic practical pattern → Hash Set
Time → O(n) average
Space → O(n)
```

---

# 🟢 PROBLEM 50 — MOVE ZEROES TO END

## ✅ EXACT LEETCODE MATCH: LC 283 — MOVE ZEROES

**Difficulty:** Easy

This is the final problem of Day 5 and an important one.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The problem:

> Move all zeroes to the end while keeping the relative order of non-zero elements.

Example:

```text
[0, 1, 0, 3, 12]
```

becomes:

```text
[1, 3, 12, 0, 0]
```

---

## Three requirements

We must:

### 1. Move all zeroes to the end

```text
0 0
```

must appear at the end.

### 2. Preserve non-zero order

Original:

```text
1, 3, 12
```

Final:

```text
1, 3, 12
```

Same order.

### 3. Do it in-place

No second array.

---

# 🔥 The key pattern

Use a:

# WRITE POINTER

Think:

```text
write = next position where a non-zero value should go
```

Scan using another pointer:

```text
read
```

So we have:

```text
read
write
```

This is a form of:

# TWO POINTERS

---

## Example

```text
[0, 1, 0, 3, 12]
 ↑
write
```

Read `0`:

```text
ignore
```

Read `1`:

```text
write it at position 0
```

Array becomes conceptually:

```text
[1, ?, ?, ?, ?]
 ↑
write
```

Read `0`:

```text
ignore
```

Read `3`:

```text
write at next position
```

Then `12`.

Finally fill remaining positions with zeroes.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text
[0, 1, 0, 3, 12]
```

Output:

```text
[1, 3, 12, 0, 0]
```

---

## Relative order

Input non-zero values:

```text
1 → 3 → 12
```

Output:

```text
1 → 3 → 12
```

So the algorithm must be **stable** for non-zero elements.

---

## Edge cases

### No zeroes

```text
[1, 2, 3]
```

remains:

```text
[1, 2, 3]
```

### All zeroes

```text
[0, 0, 0]
```

remains unchanged.

### Zero at beginning

```text
[0, 1, 2]
```

becomes:

```text
[1, 2, 0]
```

### Zero at end

```text
[1, 2, 0]
```

already satisfies the requirement.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a row of boxes.

You want:

```text
non-zero values → front
zeroes → back
```

But you must preserve the order of the useful values.

Use:

```text
read
```

to inspect every element.

Use:

```text
write
```

to remember where the next non-zero value belongs.

---

## Example

```text
[0, 1, 0, 3, 12]
```

Start:

```text
write = 0
```

### Read `0`

It's zero.

Don't write it.

```text
write = 0
```

### Read `1`

It's non-zero.

Put it at:

```text
arr[write]
```

which is:

```text
arr[0] = 1
```

Then:

```text
write = 1
```

### Read `0`

Ignore.

### Read `3`

Write:

```text
arr[1] = 3
```

Then:

```text
write = 2
```

### Read `12`

Write:

```text
arr[2] = 12
```

Then:

```text
write = 3
```

Now:

```text
[1, 3, 12, ?, ?]
```

All remaining positions from `write` onward become zero:

```text
[1, 3, 12, 0, 0]
```

Done.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

We'll use two phases.

## Phase 1 — Move non-zero values forward

Initialize:

```python
write = 0
```

Scan every element.

If:

```python
arr[read] != 0
```

place it at:

```python
arr[write] = arr[read]
```

Then:

```python
write += 1
```

---

## Phase 2 — Fill remaining positions with zero

After all non-zero elements are placed:

```text
write
```

points to the first position that should contain zero.

So:

```python
while write < len(arr):
    arr[write] = 0
    write += 1
```

---

## Pseudocode

```text
write = 0

for each element:

    if element != 0:
        arr[write] = element
        write++

while write < n:
    arr[write] = 0
    write++
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def move_zeroes(arr):

    # Position where the next non-zero
    # element should be placed
    write = 0

    # First pass:
    # move all non-zero elements forward
    for read in range(len(arr)):

        if arr[read] != 0:

            arr[write] = arr[read]

            write += 1

    # Second pass:
    # fill the remaining positions with zero
    while write < len(arr):

        arr[write] = 0

        write += 1

    return arr


arr = [0, 1, 0, 3, 12]

move_zeroes(arr)

print(arr)
```

### Output

```text
[1, 3, 12, 0, 0]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    static void moveZeroes(int[] arr) {

        // Position where the next non-zero
        // element should be written
        int write = 0;

        // First pass:
        // move non-zero elements forward
        for (int read = 0; read < arr.length; read++) {

            if (arr[read] != 0) {

                arr[write] = arr[read];

                write++;
            }
        }

        // Second pass:
        // fill remaining positions with zero
        while (write < arr.length) {

            arr[write] = 0;

            write++;
        }
    }

    public static void main(String[] args) {

        int[] arr = {0, 1, 0, 3, 12};

        moveZeroes(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text
[1, 3, 12, 0, 0]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[0, 1, 0, 3, 12]
```

Initial:

```text
write = 0
```

---

### Read index 0

```text
arr[0] = 0
```

Zero.

Ignore.

```text
write = 0
```

---

### Read index 1

```text
arr[1] = 1
```

Non-zero.

Write:

```text
arr[0] = 1
```

Now:

```text
[1, 1, 0, 3, 12]
```

Then:

```text
write = 1
```

The temporary duplicate `1` is harmless because we will overwrite the remaining positions.

---

### Read index 2

```text
arr[2] = 0
```

Ignore.

```text
write = 1
```

---

### Read index 3

```text
arr[3] = 3
```

Write:

```text
arr[1] = 3
```

Array:

```text
[1, 3, 0, 3, 12]
```

Then:

```text
write = 2
```

---

### Read index 4

```text
arr[4] = 12
```

Write:

```text
arr[2] = 12
```

Array:

```text
[1, 3, 12, 3, 12]
```

Then:

```text
write = 3
```

---

## Phase 2

Now:

```text
write = 3
```

Fill:

```text
arr[3] = 0
arr[4] = 0
```

Final:

```text
[1, 3, 12, 0, 0]
```

---

## Complete trace

| Read | Value | Write Before | Action      | Write After |
| ---: | ----: | -----------: | ----------- | ----------: |
|    0 |     0 |            0 | Ignore      |           0 |
|    1 |     1 |            0 | `arr[0]=1`  |           1 |
|    2 |     0 |            1 | Ignore      |           1 |
|    3 |     3 |            1 | `arr[1]=3`  |           2 |
|    4 |    12 |            2 | `arr[2]=12` |           3 |

Then fill positions:

```text
3 → 0
4 → 0
```

Final:

```text
[1, 3, 12, 0, 0]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
{0, 1, 0, 3, 12}
```

Initial:

```text
write = 0
```

### `read = 0`

```text
arr[0] = 0
```

Ignore.

---

### `read = 1`

```text
arr[1] = 1
```

Write:

```text
arr[0] = 1
write = 1
```

---

### `read = 2`

```text
arr[2] = 0
```

Ignore.

---

### `read = 3`

```text
arr[3] = 3
```

Write:

```text
arr[1] = 3
write = 2
```

---

### `read = 4`

```text
arr[4] = 12
```

Write:

```text
arr[2] = 12
write = 3
```

Now:

```text
[1,3,12,?,?]
```

Fill:

```text
arr[3] = 0
arr[4] = 0
```

Final:

```text
[1,3,12,0,0]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

### First pass

We inspect all `n` elements:

```text
O(n)
```

### Second pass

We fill remaining positions.

At most `n` positions:

```text
O(n)
```

Total:

```text
O(n) + O(n)
```

Dropping the constant:

```text
O(n)
```

---

## Space

We don't create another array.

We only use:

```text
write
read
```

Therefore:

```text
O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

This matches the optimal complexity for LC 283.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can't we simply sort the array?

Because sorting destroys the relative order of non-zero elements.

The problem requires:

```text
[1, 3, 12]
```

to remain:

```text
1 → 3 → 12
```

---

### Q2. Why is `write` needed?

`read` answers:

> What element am I currently looking at?

`write` answers:

> Where should the next useful element go?

That distinction is the heart of the algorithm.

---

### Q3. What does `write` represent?

At every moment:

> `write` is the next position where a non-zero element should be placed.

That is the invariant.

---

### Q4. Can we use another array?

Yes:

```python
result = [x for x in arr if x != 0]
```

then append zeros.

But that uses:

```text
O(n)
```

additional space.

The optimal LC 283 solution is:

```text
O(n) time
O(1) space
```

---

### Q5. Is the order of non-zero elements preserved?

Yes.

We process them from left to right and write them sequentially.

Therefore:

```text
stable
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# WRITE POINTER / COMPACTION

This is a major pattern.

Template:

```python
write = 0

for read in range(len(arr)):

    if condition(arr[read]):

        arr[write] = arr[read]
        write += 1
```

Then handle the remaining positions.

---

## Recognition triggers

Think **write pointer** when the problem says:

```text
remove elements
move elements
compact array
move zeroes
keep valid elements
filter in-place
preserve order
```

The mental model:

```text
READ
 ↓
Does this element belong?
 ↓
YES → WRITE
NO  → SKIP
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Sorting

```python
arr.sort()
```

Wrong approach for this problem.

---

### ❌ Mistake 2 — Creating another array

It works, but violates the intended `O(1)` auxiliary-space solution.

---

### ❌ Mistake 3 — Losing order

A careless swapping solution can move non-zero elements out of their original relative order.

---

### ❌ Mistake 4 — Forgetting the second phase

After moving non-zero values forward:

```text
[1, 3, 12, ?, ?]
```

the remaining positions must become zero.

---

### ❌ Mistake 5 — Confusing `read` and `write`

Remember:

```text
read
→ scans original/current data

write
→ marks next destination
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Use a write pointer to compact all non-zero elements toward the front while preserving their order, then fill the remaining positions with zeroes.**

```text
LC 283
Pattern → Write Pointer / Two Pointers
Time    → O(n)
Space   → O(1)
```

---

# 🔥 DAY 5 — SESSION 3 — PATTERN CONNECTION

We just covered four very different array patterns.

---

## 47 — ADJACENT COMPARISON

```text
current ↔ next
```

Used for:

```text
sorted?
valid order?
```

---

## 48 — EXPECTED VS ACTUAL

```text
expected total
       -
actual total
       =
missing
```

Used for:

```text
LC 268
```

---

## 49 — SEEN SET

```text
Have I seen this before?
```

Used for:

```text
duplicate detection
```

---

## 50 — WRITE POINTER

```text
read → inspect
write → place
```

Used for:

```text
move zeroes
remove elements
in-place filtering
compaction
```

---

# 🧠 DAY 5 — COMPLETE PATTERN MAP

You have now seen:

```text
41 → Running Maximum
42 → Running Minimum
43 → Top-2 Tracking
44 → Two Pointers
45 → Running Sum
46 → Classification + Counting
47 → Adjacent Comparison
48 → Expected Total − Actual Total
49 → Hash Set
50 → Write Pointer
```

These are **10 foundational array patterns**.

Do not memorize 10 separate programs.

Memorize the **trigger** for each pattern.

---

# 🧩 PATTERN RECOGNITION CHEAT SHEET

| If the question says...             | Think...                 |
| ----------------------------------- | ------------------------ |
| Largest / maximum                   | Running Maximum          |
| Smallest / minimum                  | Running Minimum          |
| Second largest                      | Top-2 Tracking           |
| Reverse in-place                    | Two Pointers             |
| Sum / total                         | Accumulator              |
| Count categories                    | Classification + Counter |
| Is sorted?                          | Adjacent Comparison      |
| One number missing from known range | Expected − Actual        |
| Duplicate / repeated                | Hash Set                 |
| Move / remove / compact in-place    | Write Pointer            |

---

# 🧪 DAY 5 — FINAL MASTER TEST

You have now completed all 10 Day 5 problems.

Do **not** immediately look back at the solutions.

Solve these independently.

---

## 🔴 MASTER TEST 1 — Sorted Array

Determine whether:

```text
[2, 4, 4, 8, 10, 15]
```

is sorted.

Expected:

```text
True
```

---

## 🔴 MASTER TEST 2 — Unsorted Array

```text
[2, 7, 5, 10]
```

Expected:

```text
False
```

---

## 🔴 MASTER TEST 3 — Missing Number

```text
[9, 6, 4, 2, 3, 5, 7, 0, 1]
```

Expected:

```text
8
```

---

## 🔴 MASTER TEST 4 — Duplicate

```text
[1, 4, 3, 2, 2]
```

Expected:

```text
2
```

---

## 🔴 MASTER TEST 5 — Move Zeroes

```text
[0, 1, 0, 3, 12]
```

Expected:

```text
[1, 3, 12, 0, 0]
```

---

# 🔥 COMBINED DAY 5 CHALLENGE

Given:

```text
arr = [0, 7, 3, 0, 5, 7, 2, 0]
```

Perform the following:

### 1. Is the original array sorted?

Expected:

```text
False
```

### 2. Find the largest.

Expected:

```text
7
```

### 3. Find the smallest.

Expected:

```text
0
```

### 4. Find the second largest distinct.

Distinct values:

```text
0, 2, 3, 5, 7
```

Expected:

```text
5
```

### 5. Find the sum.

```text
0 + 7 + 3 + 0 + 5 + 7 + 2 + 0
= 24
```

Expected:

```text
24
```

### 6. Find average.

There are 8 elements:

```text
24 / 8 = 3
```

Expected:

```text
3.0
```

### 7. Count even and odd.

Even:

```text
0, 0, 2, 0
```

Count:

```text
4
```

Odd:

```text
7, 3, 5, 7
```

Count:

```text
4
```

### 8. Find duplicate.

Expected:

```text
7
```

### 9. Move zeroes to end.

Expected:

```text
[7, 3, 5, 7, 2, 0, 0, 0]
```

---

# 🧠 DAY 5 — SENIOR RECOGNITION DRILL

Don't solve based on memorized code.

Instead, look at the question and say the pattern **before coding**.

### Question:

> Find the largest number.

Your brain:

```text
RUNNING MAXIMUM
```

---

### Question:

> Find the second largest distinct number.

Your brain:

```text
TOP-2 TRACKING
```

---

### Question:

> Reverse the array without using another array.

Your brain:

```text
TWO POINTERS
```

---

### Question:

> Find the total of all elements.

Your brain:

```text
ACCUMULATOR
```

---

### Question:

> Count how many elements are even.

Your brain:

```text
CLASSIFY + COUNT
```

---

### Question:

> Check if array is sorted.

Your brain:

```text
ADJACENT COMPARISON
```

---

### Question:

> One number from 0 to n is missing.

Your brain:

```text
EXPECTED − ACTUAL
```

---

### Question:

> Find repeated element.

Your brain:

```text
HASH SET
```

---

### Question:

> Move zeroes to the end without changing non-zero order.

Your brain:

```text
WRITE POINTER
```

---

# 🏆 DAY 5 COMPLETE

```text
DAY 5 — ARRAY FUNDAMENTALS

41 → Largest Element                  ✅
42 → Smallest Element                 ✅
43 → Second Largest Distinct          ✅
44 → Reverse Array In-Place           ✅
45 → Sum & Average                    ✅
46 → Count Even & Odd                 ✅
47 → Check Sorted                     ✅
48 → Missing Number — LC 268          ✅
49 → Duplicate Element — LC 287      ✅
50 → Move Zeroes — LC 283             ✅
```

# 📊 CR2 OVERALL PROGRESS

```text
Day 1 → 10/10
Day 2 → 10/10
Day 3 → 10/10
Day 4 → 10/10
Day 5 → 10/10

TOTAL = 50 / 100
```

# 🔥 50% COMPLETE

But **50/100 covered does NOT automatically mean 50/100 mastered**.

The actual target is:

```text
🟢 Understand
      ↓
🟡 Reproduce
      ↓
🟠 Independent
      ↓
🔴 Mastered
```

---

# 🧠 DAY 5 — FINAL MASTER PATTERN MAP

```text
                ARRAYS
                   │
       ┌───────────┼───────────┐
       │           │           │
    TRACK        SCAN       MODIFY
       │           │           │
       │           │           ├── Two Pointers
       ├── Max     ├── Sorted │
       ├── Min     ├── Sum    └── Write Pointer
       └── Top-2   ├── Count
                   ├── Missing
                   └── Duplicate
```

## 🚀 What you should now be able to recognize

```text
MAXIMUM             → Running Max
MINIMUM             → Running Min
SECOND MAX          → Top-2
REVERSE             → Two Pointers
SUM                 → Accumulator
COUNT               → Condition + Counter
SORTED?             → Adjacent Comparison
MISSING             → Expected − Actual
DUPLICATE           → Hash Set
MOVE/REMOVE         → Write Pointer
```

**Day 5 is complete: 50/100.**

**Next: Day 6 — Array Interview Basics, Problems 51–60.**
