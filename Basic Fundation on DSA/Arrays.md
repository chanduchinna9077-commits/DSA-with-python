
# 🧠 FINAL DSA TOPIC LIST

## 🔴 1. ARRAYS — 10 Problems

This is one of the most important topics.

### Patterns

1. Basic traversal
2. Min/Max
3. One-pass tracking
4. Frequency
5. Hashing
6. Two Pointers
7. Rearrangement
8. Searching
9. Prefix Sum
10. Subarray/Kadane

### 10 Problems

| #  | Problem              | Pattern      |
| -- | -------------------- | ------------ |
| 1  | Find Maximum Element | Traversal    |
| 2  | Find Minimum Element | Traversal    |
| 3  | Find Second Largest  | One-pass     |
| 4  | Count Frequency      | Counting     |
| 5  | Remove Duplicates    | Set          |
| 6  | Two Sum              | Hashing      |
| 7  | Reverse Array        | Two Pointers |
| 8  | Move Zeros to End    | Two Pointers |
| 9  | Missing Number       | Math/XOR     |
| 10 | Maximum Subarray Sum | Kadane       |

---

# 🔥 ARRAYS — CONVERSATION 1

## Problems 1–4 of our 10-problem Array Mastery Set

### Our 10-array roadmap

| #     | Problem                       | Core Pattern        |
| ----- | ----------------------------- | ------------------- |
| **1** | Find Maximum Element          | Linear Traversal    |
| **2** | Find Minimum Element          | Linear Traversal    |
| **3** | Find Second Largest           | One-Pass Tracking   |
| **4** | Count Frequency of an Element | Traversal + Counter |
| 5     | Remove Duplicates             | Set / Hashing       |
| 6     | Two Sum                       | Hashing             |
| 7     | Reverse Array                 | Two Pointers        |
| 8     | Move Zeros to End             | Rearrangement       |
| 9     | Missing Number                | Math / XOR          |
| 10    | Maximum Subarray Sum          | Kadane's Algorithm  |

Today: **1–4**.

---

# 🟦 PROBLEM 1 — FIND MAXIMUM ELEMENT

## 1. Problem

Given an array of integers, find the **largest element**.

### Example

```text
Input:
10 25 7 42 18

Output:
42
```

---

## 2. Problem Theory

This is the most basic **array traversal** pattern.

We need to inspect every element and keep track of the largest value found so far.

Think like this:

```text
Array:
10  25  7  42  18
↑
Start with 10 as maximum

25 > 10 → maximum = 25
7  > 25 → No
42 > 25 → maximum = 42
18 > 42 → No

Answer = 42
```

### Pattern

> **Find something extreme in an array → traverse the array while maintaining an answer variable.**

---

# 3. ELI10 Intuition

Imagine you are checking the heights of 5 people.

You initially say:

> "The first person is the tallest."

Then you check everyone else.

Whenever you find someone taller, you change your answer.

That's exactly what we're doing.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Read the array.
Step 2 → Assume the first element is the maximum.
Step 3 → Visit every element.
Step 4 → Compare current element with maximum.
Step 5 → If current > maximum, update maximum.
Step 6 → Print maximum.
```

---

# 5. Method 1 — Using Python Built-in Method

Python already provides `max()`.

```python
arr = list(map(int, input().split()))

maximum = max(arr)

print(maximum)
```

### Example

Input:

```text
10 25 7 42 18
```

`max(arr)` finds:

```text
42
```

Output:

```text
42
```

### Important

This is perfectly acceptable Python.

But if an interviewer asks:

> "Can you find the maximum without using built-in functions?"

You need the next solution.

---

# 6. Method 2 — WITHOUT Built-in `max()`

```python
arr = list(map(int, input().split()))

maximum = arr[0]

for x in arr:
    if x > maximum:
        maximum = x

print(maximum)
```

---

# 7. Code Explanation

```python
maximum = arr[0]
```

We assume the first element is the largest.

Then:

```python
for x in arr:
```

Visit every element.

Then:

```python
if x > maximum:
```

Ask:

> "Is the current element bigger?"

If yes:

```python
maximum = x
```

Update our answer.

---

# 8. Dry Run

Array:

```text
[10, 25, 7, 42, 18]
```

Initially:

```text
maximum = 10
```

| Step  | Current `x` | Maximum Before | Comparison | Maximum After |
| ----- | ----------: | -------------: | ---------- | ------------: |
| Start |           — |              — | —          |            10 |
| 1     |          10 |             10 | 10 > 10 ❌  |            10 |
| 2     |          25 |             10 | 25 > 10 ✅  |            25 |
| 3     |           7 |             25 | 7 > 25 ❌   |            25 |
| 4     |          42 |             25 | 42 > 25 ✅  |            42 |
| 5     |          18 |             42 | 18 > 42 ❌  |            42 |

Final:

```text
42
```

---

# 9. Complexity

### Built-in

Conceptually, finding the maximum requires looking through the elements:

```text
Time: O(n)
```

### Manual

```text
Time: O(n)
Space: O(1)
```

Why `O(n)`?

Because in the worst case we inspect all `n` elements.

---

# 10. Edge Cases

### One element

```text
[50]
```

Answer:

```text
50
```

### Negative numbers

```text
[-10, -5, -20, -2]
```

Answer:

```text
-2
```

### All equal

```text
[5, 5, 5, 5]
```

Answer:

```text
5
```

---

# 🧠 PATTERN RECOGNITION

When you see:

> "Find the largest/smallest/best/worst element."

Think:

```text
Array
 ↓
Traversal
 ↓
Maintain answer
 ↓
Update when better value appears
```

This is **Pattern #1: Linear Scan / Tracking**.

---

# 🟦 PROBLEM 2 — FIND MINIMUM ELEMENT

## 1. Problem

Find the smallest element in an array.

### Example

```text
Input:
10 25 7 42 18

Output:
7
```

---

# 2. Problem Theory

This is almost identical to maximum.

Instead of asking:

```text
Is current > minimum?
```

we ask:

```text
Is current < minimum?
```

This is important because you're learning a **general pattern**, not two unrelated programs.

---

# 3. ELI10

Imagine you have several boxes and want to find the box with the smallest weight.

Start by assuming the first box is the smallest.

Then compare every other box.

If you find something lighter, replace your answer.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Read the array.
Step 2 → Assume first element is minimum.
Step 3 → Traverse the array.
Step 4 → Compare current element with minimum.
Step 5 → If current < minimum, update minimum.
Step 6 → Print minimum.
```

---

# 5. Method 1 — Built-in

```python
arr = list(map(int, input().split()))

minimum = min(arr)

print(minimum)
```

---

# 6. Method 2 — Without Built-in `min()`

```python
arr = list(map(int, input().split()))

minimum = arr[0]

for x in arr:
    if x < minimum:
        minimum = x

print(minimum)
```

---

# 7. Dry Run

Array:

```text
[10, 25, 7, 42, 18]
```

Initial:

```text
minimum = 10
```

| Step  | Current | Minimum Before | Comparison | Minimum After |
| ----- | ------: | -------------: | ---------- | ------------: |
| Start |       — |              — | —          |            10 |
| 1     |      10 |             10 | 10 < 10 ❌  |            10 |
| 2     |      25 |             10 | 25 < 10 ❌  |            10 |
| 3     |       7 |             10 | 7 < 10 ✅   |             7 |
| 4     |      42 |              7 | 42 < 7 ❌   |             7 |
| 5     |      18 |              7 | 18 < 7 ❌   |             7 |

Answer:

```text
7
```

---

# 8. Complexity

```text
Time  → O(n)
Space → O(1)
```

---

# 9. Important Edge Case

Consider:

```text
[-10, -30, -5, -100]
```

The minimum is:

```text
-100
```

Don't make the mistake of thinking `-5` is smaller than `-100`.

On the number line:

```text
-100 < -30 < -10 < -5
```

---

# 🧠 PATTERN RECOGNITION

Maximum:

```python
if x > answer:
```

Minimum:

```python
if x < answer:
```

The **structure is identical**.

That's an important DSA lesson:

> Many problems are the same pattern with one condition changed.

---

# 🟦 PROBLEM 3 — FIND SECOND LARGEST ELEMENT

## ⭐ Important

This is more valuable than simple maximum/minimum because it teaches **multiple-variable tracking**.

---

# 1. Problem

Find the **second largest distinct element**.

### Example

```text
Input:
10 5 20 8 20 15

Output:
15
```

Why?

Distinct values:

```text
5, 8, 10, 15, 20
```

Largest:

```text
20
```

Second largest:

```text
15
```

---

# 2. Problem Theory

A beginner might do:

```python
arr.sort()
print(arr[-2])
```

That can work for some inputs, but there is a problem with duplicates.

Example:

```text
10 20 20 15
```

After sorting:

```text
10 15 20 20
```

`arr[-2]` gives:

```text
20
```

But we want the **second largest distinct value**:

```text
15
```

So we need to track:

```text
largest
second_largest
```

---

# 3. ELI10

Imagine a race.

You want to know:

```text
1st place
2nd place
```

When someone faster arrives:

```text
New person → 1st
Old 1st → 2nd
```

That's exactly the algorithm.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Initialize largest and second largest.
Step 2 → Traverse every element.
Step 3 → If current > largest:
            second = largest
            largest = current

Step 4 → Otherwise, if current is between largest and second:
            update second.

Step 5 → Print second largest.
```

---

# 5. Method 1 — Using Built-in Methods

The easiest Python approach:

```python
arr = list(map(int, input().split()))

unique = list(set(arr))

unique.sort()

print(unique[-2])
```

### What happens?

Input:

```text
10 5 20 8 20 15
```

`set()`:

```text
{5, 8, 10, 15, 20}
```

Sort:

```text
[5, 8, 10, 15, 20]
```

Second last:

```text
15
```

---

## ⚠️ Important

This assumes there are at least **two distinct elements**.

A robust version:

```python
arr = list(map(int, input().split()))

unique = list(set(arr))

if len(unique) < 2:
    print("No second largest")
else:
    unique.sort()
    print(unique[-2])
```

---

# 6. Method 2 — WITHOUT `set()` and `sort()`

This is the important DSA version.

```python
arr = list(map(int, input().split()))

largest = float('-inf')
second = float('-inf')

for x in arr:

    if x > largest:
        second = largest
        largest = x

    elif x > second and x != largest:
        second = x

if second == float('-inf'):
    print("No second largest")
else:
    print(second)
```

---

# 7. Understand the Core Logic

Suppose:

```text
arr = [10, 5, 20, 8, 15]
```

Start:

```text
largest = -∞
second = -∞
```

### `10`

```text
10 > largest
```

So:

```text
second = -∞
largest = 10
```

### `5`

```text
5 > largest? No
5 > second? Yes
```

So:

```text
second = 5
largest = 10
```

### `20`

```text
20 > 10
```

Therefore:

```text
second = 10
largest = 20
```

### `8`

```text
8 > 20? No
8 > 10? No
```

Nothing changes.

### `15`

```text
15 > 20? No
15 > 10? Yes
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

---

# 8. Detailed Dry Run

Input:

```text
[10, 5, 20, 8, 20, 15]
```

| Current | Largest Before | Second Before | Action                     | Largest After | Second After |
| ------: | -------------: | ------------: | -------------------------- | ------------: | -----------: |
|      10 |             -∞ |            -∞ | New largest                |            10 |           -∞ |
|       5 |             10 |            -∞ | New second                 |            10 |            5 |
|      20 |             10 |             5 | New largest                |            20 |           10 |
|       8 |             20 |            10 | Ignore                     |            20 |           10 |
|      20 |             20 |            10 | Duplicate largest → ignore |            20 |           10 |
|      15 |             20 |            10 | New second                 |            20 |           15 |

Answer:

```text
15
```

---

# 9. Complexity

### Built-in version

Sorting dominates:

```text
Time → O(n log n)
Space → O(n)
```

### Manual one-pass version

```text
Time → O(n)
Space → O(1)
```

This is the better algorithmic solution.

---

# 10. Edge Cases

### Duplicate largest

```text
[10, 20, 20, 5]
```

Answer:

```text
10
```

### All equal

```text
[5, 5, 5]
```

There is no second distinct largest.

### Only one distinct value

```text
[10, 10, 10]
```

No second largest.

---

# 🧠 PATTERN RECOGNITION

When you see:

> "Find largest AND second largest."

Think:

```text
One answer variable isn't enough.
             ↓
Track two values.
             ↓
largest + second
```

More generally:

> **Top K / second best / runner-up → maintain multiple candidates or use sorting/heap.**

For Basic DSA, the **two-variable tracking method** is extremely useful.

---

# 🟦 PROBLEM 4 — COUNT FREQUENCY OF AN ELEMENT

## ⭐ Important Hashing Introduction

---

# 1. Problem

Given an array and a target value, count how many times the target occurs.

### Example

```text
Array:
1 2 3 2 4 2 5

Target:
2

Output:
3
```

---

# 2. Problem Theory

We need to visit every element and count whenever:

```text
current == target
```

This is the simplest form of **frequency counting**.

Later, we'll generalize this into:

> "Count the frequency of every element."

That will introduce dictionaries/hashing.

---

# 3. ELI10

Imagine a teacher asks:

> "How many students are wearing blue?"

You look at each student.

Whenever you see blue:

```text
count = count + 1
```

Same idea.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Read the array.
Step 2 → Read the target.
Step 3 → Set count = 0.
Step 4 → Traverse the array.
Step 5 → If current == target:
            count += 1
Step 6 → Print count.
```

---

# 5. Method 1 — Built-in `count()`

Python provides:

```python
arr.count(target)
```

Complete solution:

```python
arr = list(map(int, input().split()))
target = int(input())

count = arr.count(target)

print(count)
```

Input:

```text
1 2 3 2 4 2 5
2
```

Output:

```text
3
```

---

# 6. Method 2 — WITHOUT `count()`

```python
arr = list(map(int, input().split()))
target = int(input())

count = 0

for x in arr:
    if x == target:
        count += 1

print(count)
```

This is the underlying logic.

---

# 7. Dry Run

Array:

```text
[1, 2, 3, 2, 4, 2, 5]
```

Target:

```text
2
```

Initial:

```text
count = 0
```

| Current | Is `current == 2`? | Count |
| ------: | ------------------ | ----: |
|       1 | ❌                  |     0 |
|       2 | ✅                  |     1 |
|       3 | ❌                  |     1 |
|       2 | ✅                  |     2 |
|       4 | ❌                  |     2 |
|       2 | ✅                  |     3 |
|       5 | ❌                  |     3 |

Final:

```text
3
```

---

# 8. Complexity

```text
Time → O(n)
Space → O(1)
```

Why?

We inspect every element exactly once.

---

# 9. Edge Cases

### Target doesn't exist

```text
Array:
1 3 5 7

Target:
2
```

Answer:

```text
0
```

### Target occurs once

```text
[5, 1, 2]
target = 5
```

Answer:

```text
1
```

### Target occurs everywhere

```text
[7, 7, 7, 7]
target = 7
```

Answer:

```text
4
```

---

# 🧠 PATTERN RECOGNITION

When the question says:

> "How many times does X appear?"

Think:

```text
Traversal
+
Counter
```

When it says:

> "How many times does EACH element appear?"

Think:

```text
Dictionary / HashMap
```

That's an important distinction.

---

# 🧠 ARRAY CONVERSATION 1 — PATTERN SUMMARY

You've now learned four different levels of array thinking:

```text
PROBLEM 1
Find Maximum
      ↓
Traversal + Tracking
```

```text
PROBLEM 2
Find Minimum
      ↓
Traversal + Tracking
```

```text
PROBLEM 3
Second Largest
      ↓
Multiple-variable Tracking
```

```text
PROBLEM 4
Count Frequency
      ↓
Traversal + Counter
```

## The progression is deliberate

```text
        ARRAY
          │
          ▼
     Basic Traversal
          │
      ┌───┴───┐
      ▼       ▼
    MAX      MIN
      │
      ▼
 Multiple Values
      │
      ▼
 Second Largest
      │
      ▼
 Counting
      │
      ▼
 Frequency / Hashing
```

---

# 🔥 YOUR FIRST ARRAY DRILL

Before moving to Problems **5–8**, you should be able to write these four **without looking back**:

### Q1

Find maximum without `max()`.

### Q2

Find minimum without `min()`.

### Q3

Find second largest **distinct** element without `set()` or `sort()`.

### Q4

Count target frequency without `.count()`.

If you can write all four from a blank editor, **Conversation 1 is actually learned**.

Next in the locked roadmap:

# **ARRAYS — CONVERSATION 2**

### Problems 5–8

**5. Remove Duplicates → Set/Hashing**
**6. Two Sum → Complement Hashing**
**7. Reverse Array → Two Pointers**
**8. Move Zeros → In-place Rearrangement**

Those four are a significant step up from today's basic traversal problems.

Would you like to try Q1–Q4 yourself first, or should we move straight to Problems 5–8?
# 🔥 ARRAYS — CONVERSATION 2

## Problems 5–8: Hashing + Two Pointers + Rearrangement

We now move from simple traversal into the **most useful basic array patterns**.

| #     | Problem           | Pattern                |
| ----- | ----------------- | ---------------------- |
| **5** | Remove Duplicates | Set / Hashing          |
| **6** | Two Sum           | Hashing / Complement   |
| **7** | Reverse Array     | Two Pointers           |
| **8** | Move Zeros to End | In-place Rearrangement |

---

# 🟦 PROBLEM 5 — REMOVE DUPLICATES FROM ARRAY

## 1. Problem

Given an array, remove duplicate elements while **preserving the original order**.

### Example

```text
Input:
4 2 4 3 2 1 3

Output:
4 2 3 1
```

The first occurrence of each value is kept.

---

## 2. Problem Theory

Suppose:

```text
[4, 2, 4, 3, 2, 1]
```

We encounter:

```text
4 → first time → keep
2 → first time → keep
4 → already seen → skip
3 → first time → keep
2 → already seen → skip
1 → first time → keep
```

So:

```text
[4, 2, 3, 1]
```

This introduces the **Set pattern**.

A set is useful when we need to answer:

> "Have I seen this value before?"

---

# 3. ELI10

Imagine you're collecting stickers.

You don't want two copies of the same sticker.

You keep a notebook called:

```text
seen
```

Whenever you get a sticker:

* If it's already in `seen` → throw it away.
* Otherwise → keep it and record it.

That's exactly what the algorithm does.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Read the array.
Step 2 → Create an empty set called seen.
Step 3 → Create an empty result list.
Step 4 → Traverse every element.
Step 5 → If element is not in seen:
            Add it to result.
            Add it to seen.
Step 6 → Print result.
```

---

# 5. Method 1 — Using Built-in Methods

The simplest Python approach:

```python
arr = list(map(int, input().split()))

result = list(dict.fromkeys(arr))

print(*result)
```

### Why `dict.fromkeys()`?

A dictionary keeps keys unique while preserving insertion order.

Example:

```python
arr = [4, 2, 4, 3, 2, 1]

dict.fromkeys(arr)
```

Conceptually gives:

```text
4 → 2 → 3 → 1
```

Then:

```python
list(...)
```

converts it back into a list.

### Easier built-in approach

For beginner understanding, you can also use:

```python
arr = list(map(int, input().split()))

result = []

for x in arr:
    if x not in result:
        result.append(x)

print(*result)
```

This is easier to understand, but less efficient for large arrays.

---

# 6. Method 2 — WITHOUT Built-in Duplicate Removal

Use a `set` explicitly:

```python
arr = list(map(int, input().split()))

seen = set()
result = []

for x in arr:

    if x not in seen:
        result.append(x)
        seen.add(x)

print(*result)
```

This is the version I want you to understand.

---

# 7. Dry Run

Input:

```text
[4, 2, 4, 3, 2, 1]
```

Initially:

```text
seen = {}
result = []
```

| Current | Already Seen? | Action | `seen`      | `result`    |
| ------: | ------------- | ------ | ----------- | ----------- |
|       4 | No            | Keep   | `{4}`       | `[4]`       |
|       2 | No            | Keep   | `{4,2}`     | `[4,2]`     |
|       4 | Yes           | Skip   | `{4,2}`     | `[4,2]`     |
|       3 | No            | Keep   | `{4,2,3}`   | `[4,2,3]`   |
|       2 | Yes           | Skip   | `{4,2,3}`   | `[4,2,3]`   |
|       1 | No            | Keep   | `{4,2,3,1}` | `[4,2,3,1]` |

Final:

```text
4 2 3 1
```

---

# 8. Complexity

Using a set:

```text
Time  → O(n) average
Space → O(n)
```

Why space `O(n)`?

Because in the worst case every element is unique, so `seen` stores all of them.

---

# 9. Edge Cases

### All elements unique

```text
1 2 3 4
```

Output:

```text
1 2 3 4
```

### Everything duplicated

```text
5 5 5 5
```

Output:

```text
5
```

### Negative values

```text
-1 -2 -1 -3
```

Output:

```text
-1 -2 -3
```

---

# 🧠 Pattern Recognition

When you see:

> "Remove duplicates."

Think:

```text
Duplicates
    ↓
Have I seen this before?
    ↓
SET
```

When you see:

> "Preserve original order."

Think:

```text
Traverse from left → right
+
Keep first occurrence
```

---

# 🟦 PROBLEM 6 — TWO SUM

## ⭐⭐⭐⭐⭐ VERY IMPORTANT

This is one of the most important basic array/hash problems.

---

# 1. Problem

Given an array and a target, find two numbers whose sum equals the target.

### Example

```text
Array:
2 7 11 15

Target:
9
```

Output:

```text
2 7
```

Because:

```text
2 + 7 = 9
```

---

# 2. Problem Theory

The brute-force approach is:

```text
Take every pair.
Check their sum.
```

For:

```text
[2, 7, 11, 15]
```

You check:

```text
2 + 7
2 + 11
2 + 15
7 + 11
7 + 15
11 + 15
```

That can become **O(n²)**.

Instead, use this mathematical relationship:

```text
a + b = target
```

Therefore:

```text
b = target - a
```

So for every number, we ask:

> "Have I already seen the number I need?"

That is **hashing**.

---

# 3. ELI10

Suppose your target is ₹100.

You have ₹40.

You immediately know:

> "I need someone with ₹60."

So you check whether ₹60 has already appeared.

That's:

```text
target - current
```

---

# 4. Algorithm — Step by Step

```text
Step 1 → Read array and target.
Step 2 → Create an empty set called seen.
Step 3 → Traverse the array.
Step 4 → Calculate:
            complement = target - current
Step 5 → Check whether complement exists in seen.
Step 6 → If yes, we found the pair.
Step 7 → Otherwise add current to seen.
```

---

# 5. Method 1 — Built-in / Simple Python

A straightforward Python approach uses combinations:

```python
from itertools import combinations

arr = list(map(int, input().split()))
target = int(input())

for a, b in combinations(arr, 2):
    if a + b == target:
        print(a, b)
        break
```

This is easy to read, but internally it checks many pairs.

### Complexity

```text
Time → O(n²)
Space → O(n)
```

---

# 6. Method 2 — Hashing WITHOUT Pair Generation

This is the important DSA solution:

```python
arr = list(map(int, input().split()))
target = int(input())

seen = set()

for x in arr:

    complement = target - x

    if complement in seen:
        print(complement, x)
        break

    seen.add(x)
```

---

# 7. Dry Run

Input:

```text
arr = [2, 7, 11, 15]
target = 9
```

Initially:

```text
seen = {}
```

### Current = 2

```text
complement = 9 - 2
            = 7
```

Is `7` in `seen`?

```text
No
```

Add `2`.

```text
seen = {2}
```

### Current = 7

```text
complement = 9 - 7
            = 2
```

Is `2` in `seen`?

```text
YES
```

Therefore:

```text
2 + 7 = 9
```

Answer:

```text
2 7
```

---

# 8. Complexity

Hashing solution:

```text
Time  → O(n) average
Space → O(n)
```

This is substantially better than checking every pair.

---

# 9. Important Edge Case

Input:

```text
3 3
```

Target:

```text
6
```

At second `3`:

```text
complement = 6 - 3 = 3
```

The first `3` is already in `seen`.

So:

```text
3 + 3 = 6
```

Correct.

---

# 🧠 Pattern Recognition

When you see:

> "Find two numbers that satisfy some target relationship."

Immediately consider:

```text
Pair
+
Target
     ↓
Complement
     ↓
Hashing
```

This pattern appears repeatedly in interviews.

---

# 🟦 PROBLEM 7 — REVERSE AN ARRAY

## ⭐⭐⭐⭐ TWO POINTERS

---

# 1. Problem

Reverse an array **in-place**.

### Input

```text
1 2 3 4 5
```

### Output

```text
5 4 3 2 1
```

---

# 2. Problem Theory

"In-place" means:

> Modify the existing array instead of creating another array.

We can use two pointers:

```text
left →             ← right

1  2  3  4  5
```

Swap:

```text
5  2  3  4  1
```

Move pointers:

```text
   left →     ← right

5  2  3  4  1
```

Swap again:

```text
5  4  3  2  1
```

Done.

---

# 3. ELI10

Imagine two people standing at opposite ends of a line.

They swap places.

Then both move toward the center.

They continue until they meet.

That's **Two Pointers**.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Set left = 0.
Step 2 → Set right = n - 1.
Step 3 → While left < right:
            Swap arr[left] and arr[right].
Step 4 → Move left forward.
Step 5 → Move right backward.
Step 6 → Stop when they meet/cross.
```

---

# 5. Method 1 — Built-in

The easiest Python method:

```python
arr = list(map(int, input().split()))

arr.reverse()

print(*arr)
```

Another common method:

```python
arr = list(map(int, input().split()))

arr = arr[::-1]

print(*arr)
```

But `[::-1]` creates a new list.

---

# 6. Method 2 — WITHOUT Built-in Reverse

```python
arr = list(map(int, input().split()))

left = 0
right = len(arr) - 1

while left < right:

    arr[left], arr[right] = arr[right], arr[left]

    left += 1
    right -= 1

print(*arr)
```

---

# 7. Dry Run

Input:

```text
[1, 2, 3, 4, 5]
```

Initial:

```text
left = 0
right = 4
```

### Step 1

Swap:

```text
1 ↔ 5
```

Array:

```text
[5, 2, 3, 4, 1]
```

Move:

```text
left = 1
right = 3
```

### Step 2

Swap:

```text
2 ↔ 4
```

Array:

```text
[5, 4, 3, 2, 1]
```

Move:

```text
left = 2
right = 2
```

Condition:

```text
left < right
2 < 2 → False
```

Stop.

---

# 8. Complexity

```text
Time  → O(n)
Space → O(1)
```

This is excellent because we don't need another array.

---

# 🧠 Pattern Recognition

When you see:

> Reverse / compare from both ends / rearrange from both sides.

Think:

```text
LEFT ---------------- RIGHT
  ↓                      ↓
Two Pointers
```

---

# 🟦 PROBLEM 8 — MOVE ZEROS TO END

## ⭐⭐⭐⭐⭐ VERY IMPORTANT

---

# 1. Problem

Move all zeroes to the end while maintaining the relative order of non-zero elements.

### Input

```text
0 1 0 3 12
```

### Output

```text
1 3 12 0 0
```

Notice:

```text
1 → 3 → 12
```

still maintain their original order.

---

# 2. Problem Theory

We want to separate:

```text
NON-ZERO elements
+
ZERO elements
```

We can use an index called `position`.

It tells us:

> "Where should the next non-zero element go?"

---

# 3. ELI10

Imagine a row of boxes.

You want all the useful objects at the front and empty boxes at the end.

You scan from left to right.

Whenever you find a non-zero number, put it into the next available front position.

Then fill the remaining positions with zero.

---

# 4. Algorithm — Step by Step

```text
Step 1 → Set position = 0.
Step 2 → Traverse the array.
Step 3 → If current element is NOT zero:
            Put it at arr[position].
            Increase position.
Step 4 → After processing all elements,
         fill the remaining positions with zero.
Step 5 → Print array.
```

---

# 5. Method 1 — Built-in / Simple Python

An easy Python approach:

```python
arr = list(map(int, input().split()))

non_zero = [x for x in arr if x != 0]
zeros = [0] * (len(arr) - len(non_zero))

result = non_zero + zeros

print(*result)
```

Example:

```text
arr = [0, 1, 0, 3, 12]
```

Non-zero:

```text
[1, 3, 12]
```

Zeros:

```text
[0, 0]
```

Final:

```text
[1, 3, 12, 0, 0]
```

---

# 6. Method 2 — WITHOUT Creating Another Array

This is the DSA version.

```python
arr = list(map(int, input().split()))

position = 0

for i in range(len(arr)):

    if arr[i] != 0:
        arr[position] = arr[i]
        position += 1

while position < len(arr):
    arr[position] = 0
    position += 1

print(*arr)
```

---

# 7. Detailed Dry Run

Input:

```text
[0, 1, 0, 3, 12]
```

Initially:

```text
position = 0
```

### `i = 0`

Current:

```text
0
```

Zero → skip.

```text
position = 0
```

### `i = 1`

Current:

```text
1
```

Non-zero.

Put it at:

```text
arr[position]
arr[0] = 1
```

Array conceptually becomes:

```text
[1, 1, 0, 3, 12]
```

Then:

```text
position = 1
```

### `i = 2`

Current:

```text
0
```

Skip.

### `i = 3`

Current:

```text
3
```

Put:

```text
arr[1] = 3
```

Now:

```text
[1, 3, 0, 3, 12]
```

```text
position = 2
```

### `i = 4`

Current:

```text
12
```

Put:

```text
arr[2] = 12
```

Now:

```text
[1, 3, 12, 3, 12]
```

```text
position = 3
```

Now all non-zero elements are correctly placed in the front three positions.

Remaining positions:

```text
3 and 4
```

Fill them with zero:

```text
[1, 3, 12, 0, 0]
```

---

# 8. Complexity

```text
Time  → O(n)
Space → O(1)
```

That's the advantage of the in-place approach.

---

# 9. Edge Cases

### No zeros

```text
1 2 3 4
```

Output:

```text
1 2 3 4
```

### All zeros

```text
0 0 0 0
```

Output:

```text
0 0 0 0
```

### Zeros at beginning

```text
0 0 1 2 3
```

Output:

```text
1 2 3 0 0
```

### Zeros at end already

```text
1 2 3 0 0
```

No change.

---

# 🧠 Pattern Recognition

When you see:

> Move all X to one side while preserving the order of the other elements.

Think:

```text
Filtering / Rearrangement
        ↓
Position pointer
        ↓
In-place compaction
```

This same idea appears in many array problems.

---

# 🧠 ARRAY CONVERSATION 2 — WHAT YOU JUST LEARNED

You now have four major patterns:

```text
5. REMOVE DUPLICATES
        ↓
      SET
```

```text
6. TWO SUM
        ↓
Complement + Hashing
```

```text
7. REVERSE ARRAY
        ↓
    TWO POINTERS
```

```text
8. MOVE ZEROS
        ↓
In-place Rearrangement
```

The progression is important:

```text
Basic Array
    ↓
Hashing
    ↓
Complement Lookup
    ↓
Two Pointers
    ↓
In-place Manipulation
```

---

# 🔥 CURRENT ARRAY PROGRESS

| Problem              | Pattern           | Status |
| -------------------- | ----------------- | ------ |
| 1. Maximum           | Traversal         | ✅      |
| 2. Minimum           | Traversal         | ✅      |
| 3. Second Largest    | One-pass tracking | ✅      |
| 4. Frequency         | Counter           | ✅      |
| 5. Remove Duplicates | Set               | ✅      |
| 6. Two Sum           | Hashing           | ✅      |
| 7. Reverse Array     | Two Pointers      | ✅      |
| 8. Move Zeros        | Rearrangement     | ✅      |
| 9. Missing Number    | Math/XOR          | ⏳      |
| 10. Maximum Subarray | Kadane            | ⏳      |

## Next: **ARRAYS — CONVERSATION 3**

### Problem 9 — Missing Number

**Pattern:** Mathematical reasoning + XOR

### Problem 10 — Maximum Subarray Sum

**Pattern:** Kadane's Algorithm

Then we'll do the **Array Mastery section**:

* all 10 patterns
* when to recognize each pattern
* built-in vs manual templates
* complexity table
* common mistakes
* edge cases
* 10-question pattern-recognition drill
* assessment-style mixed questions.

Would you like to continue with Problem 9, Missing Number, or jump straight to Problem 10, Maximum Subarray Sum?
Absolutely. I’ll keep the **locked version unchanged**: 10 pattern-based problems per topic, 3-conversation structure, and every problem gets theory → pattern → ELI10 → step-by-step algorithm → built-in solution → no-built-in solution → line-by-line explanation → detailed dry run → complexity → edge cases → mistakes → pattern recognition.

# 🔥 ARRAYS — CONVERSATION 3

## Problems 9–10 + ARRAY MASTERY

We are finishing the first topic: **Arrays**.

| #  | Problem              | Core Pattern      |
| -- | -------------------- | ----------------- |
| 9  | Find Missing Number  | Math / XOR        |
| 10 | Maximum Subarray Sum | Kadane / Subarray |

---

# 🟦 PROBLEM 9 — FIND THE MISSING NUMBER

## 1. Problem Statement

You are given an array containing **n distinct numbers from `1` to `n+1`**, with exactly one number missing.

Find the missing number.

### Example

```text
Input:
1 2 3 5 6

Output:
4
```

The complete sequence should be:

```text
1 2 3 4 5 6
```

Therefore:

```text
Missing = 4
```

---

# 2. Problem Theory

This problem teaches an important idea:

> Sometimes we can calculate what **should exist** and compare it with what **actually exists**.

For numbers from `1` to `n`, the sum is:

```text
n × (n + 1)
─────────────
      2
```

For:

```text
1 2 3 4 5 6
```

Expected:

```text
6 × 7
───── = 21
  2
```

Actual:

```text
1 + 2 + 3 + 5 + 6 = 17
```

Therefore:

```text
21 - 17 = 4
```

---

# 3. ELI10

Imagine you have six numbered cards:

```text
1 2 3 4 5 6
```

But someone gives you:

```text
1 2 3 5 6
```

You know what the total value **should** be.

So:

```text
Expected total - Actual total
```

tells you which card is missing.

---

# 4. Algorithm — Method 1: Sum

### Step-by-step

```text
Step 1 → Read the array.
Step 2 → Find n.
Step 3 → Calculate expected sum from 1 to n.
Step 4 → Calculate actual sum of array.
Step 5 → Missing = expected - actual.
Step 6 → Print missing.
```

---

# 5. Method 1 — Using Built-in `sum()`

```python
arr = list(map(int, input().split()))

n = len(arr) + 1

expected = n * (n + 1) // 2

actual = sum(arr)

missing = expected - actual

print(missing)
```

### Example

Input:

```text
1 2 3 5 6
```

There are 5 elements.

Therefore:

```text
n = 5 + 1
n = 6
```

Expected:

```text
6 × 7 / 2 = 21
```

Actual:

```text
17
```

Missing:

```text
21 - 17 = 4
```

---

# 6. Method 2 — WITHOUT `sum()`

```python
arr = list(map(int, input().split()))

n = len(arr) + 1

expected = n * (n + 1) // 2

actual = 0

for x in arr:
    actual += x

missing = expected - actual

print(missing)
```

Here we manually calculate the array sum.

---

# 7. Detailed Dry Run

Input:

```text
[1, 2, 3, 5, 6]
```

### Step 1

```text
n = len(arr) + 1
  = 5 + 1
  = 6
```

### Step 2 — Expected Sum

```text
6 × 7 / 2 = 21
```

### Step 3 — Actual Sum

| Current | Running Sum |
| ------: | ----------: |
|       1 |           1 |
|       2 |           3 |
|       3 |           6 |
|       5 |          11 |
|       6 |          17 |

### Step 4

```text
Expected = 21
Actual   = 17

Missing = 21 - 17
        = 4
```

### Final

```text
4
```

---

# 8. Complexity

```text
Time  → O(n)
Space → O(1)
```

We traverse the array once.

---

# 9. Edge Cases

### Missing first number

```text
Input:
2 3 4 5
```

Answer:

```text
1
```

### Missing last number

```text
Input:
1 2 3 4
```

Answer:

```text
5
```

### Only one number

```text
Input:
1
```

Depending on the problem's stated range, the missing value would be `2`.

---

# 10. Alternative — XOR Pattern

There is another important solution.

XOR has a useful property:

```text
x ^ x = 0
```

and:

```text
x ^ 0 = x
```

So if we XOR all expected numbers with all actual numbers, everything appearing twice cancels.

```python
arr = list(map(int, input().split()))

n = len(arr) + 1

result = 0

for i in range(1, n + 1):
    result ^= i

for x in arr:
    result ^= x

print(result)
```

For basic assessment preparation, **understand the sum method first**. Learn XOR as the second pattern.

---

# 🧠 Pattern Recognition

When you see:

> Numbers from a known continuous range, exactly one missing.

Think:

```text
Missing Number
      ↓
Expected - Actual
      OR
     XOR
```

This is a classic assessment/interview pattern.

---

# 🟦 PROBLEM 10 — MAXIMUM SUBARRAY SUM

## ⭐⭐⭐⭐⭐ VERY IMPORTANT

This is the most advanced problem in our first 10-array set.

---

# 1. Problem Statement

Given an integer array, find the **maximum sum of a contiguous subarray**.

### Example

```text
Input:
-2 1 -3 4 -1 2 1 -5 4
```

The best subarray is:

```text
4 -1 2 1
```

Its sum:

```text
4 + (-1) + 2 + 1 = 6
```

Therefore:

```text
Output:
6
```

---

# 2. Problem Theory

The important word is:

> **CONTIGUOUS**

That means the elements must be next to each other.

You cannot choose:

```text
4, 2, 4
```

if those elements are separated.

For:

```text
[-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

we want to find the continuous section with the largest sum.

This is the famous:

# **Kadane's Algorithm**

---

# 3. ELI10

Imagine you're walking through a road.

You have a running score:

```text
current_sum
```

Every new number changes your score.

But sometimes your current score becomes so bad that carrying it forward is worse than simply **starting fresh from the current number**.

So at every number we ask:

> Should I continue the previous subarray, or start a new one here?

That gives us:

```text
current_sum = max(current_number,
                  current_sum + current_number)
```

---

# 4. The Core Decision

Suppose:

```text
current_sum = -5
current number = 4
```

Options:

```text
Continue:
-5 + 4 = -1

Start fresh:
4
```

Obviously:

```text
4 > -1
```

So start a new subarray.

That's the heart of Kadane's algorithm.

---

# 5. Algorithm — Step by Step

```text
Step 1 → Set current_sum = first element.
Step 2 → Set maximum_sum = first element.
Step 3 → Traverse from the second element.
Step 4 → Decide:
            continue previous subarray
            OR
            start new subarray.
Step 5 → Update current_sum.
Step 6 → Update maximum_sum.
Step 7 → Print maximum_sum.
```

Mathematically:

```text
current_sum = max(x, current_sum + x)
```

Then:

```text
maximum_sum = max(maximum_sum, current_sum)
```

---

# 6. Method 1 — Python Built-in / Simple Approach

For a simple Python solution, you could generate every possible subarray:

```python
arr = list(map(int, input().split()))

maximum = arr[0]

for i in range(len(arr)):
    current = 0

    for j in range(i, len(arr)):
        current += arr[j]

        maximum = max(maximum, current)

print(maximum)
```

This uses Python's built-in `max()` but manually explores subarrays.

### Complexity

```text
Time → O(n²)
Space → O(1)
```

It is understandable, but **not the optimal algorithm**.

---

# 7. Method 2 — WITHOUT Built-in `max()`

## ⭐ Kadane's Algorithm

```python
arr = list(map(int, input().split()))

current_sum = arr[0]
maximum_sum = arr[0]

for i in range(1, len(arr)):

    if current_sum + arr[i] > arr[i]:
        current_sum = current_sum + arr[i]
    else:
        current_sum = arr[i]

    if current_sum > maximum_sum:
        maximum_sum = current_sum

print(maximum_sum)
```

This is the version you should understand for DSA.

---

# 8. Easier Version to Remember

You can write the same logic more compactly:

```python
arr = list(map(int, input().split()))

current_sum = arr[0]
maximum_sum = arr[0]

for i in range(1, len(arr)):

    current_sum = max(arr[i], current_sum + arr[i])

    maximum_sum = max(maximum_sum, current_sum)

print(maximum_sum)
```

For your learning:

### First understand this:

```python
if current_sum + arr[i] > arr[i]:
```

Then learn:

```python
max(arr[i], current_sum + arr[i])
```

Don't memorize the one-liner without understanding the decision.

---

# 9. Detailed Dry Run

Input:

```text
[-2, 1, -3, 4, -1, 2, 1, -5, 4]
```

Initial:

```text
current_sum = -2
maximum_sum = -2
```

Now process each element.

| Current | `current_sum` calculation | Current Sum | Maximum |
| ------: | ------------------------- | ----------: | ------: |
|      -2 | Start                     |          -2 |      -2 |
|       1 | max(1, -2+1)              |           1 |       1 |
|      -3 | max(-3, 1-3)              |          -2 |       1 |
|       4 | max(4, -2+4)              |           4 |       4 |
|      -1 | max(-1, 4-1)              |           3 |       4 |
|       2 | max(2, 3+2)               |           5 |       5 |
|       1 | max(1, 5+1)               |           6 |       6 |
|      -5 | max(-5, 6-5)              |           1 |       6 |
|       4 | max(4, 1+4)               |           5 |       6 |

Final:

```text
maximum_sum = 6
```

The corresponding subarray is:

```text
[4, -1, 2, 1]
```

---

# 10. Why Kadane Works

At every position we only need two pieces of information:

```text
1. Best sum ending HERE
2. Best sum seen ANYWHERE
```

That's why we don't need to store every subarray.

We throw away useless history.

If the previous sum hurts us more than helping us:

```text
Start fresh.
```

Otherwise:

```text
Continue.
```

---

# 11. Complexity

### Brute-force/simple version

```text
Time  → O(n²)
Space → O(1)
```

### Kadane

```text
Time  → O(n)
Space → O(1)
```

This is the important optimization.

---

# 12. Edge Case — All Negative Numbers

This is a common mistake.

Consider:

```text
[-5, -2, -8, -1]
```

The answer is:

```text
-1
```

NOT:

```text
0
```

That's why we initialize:

```python
current_sum = arr[0]
maximum_sum = arr[0]
```

rather than:

```python
current_sum = 0
maximum_sum = 0
```

---

# 🧠 Pattern Recognition

When you see:

> **Maximum sum + contiguous subarray**

Immediately think:

```text
Contiguous Subarray
        ↓
Maximum Sum
        ↓
Kadane's Algorithm
```

The critical decision is:

```text
Continue previous subarray?
        OR
Start new subarray?
```

---

# 🏆 ARRAYS — ALL 10 COMPLETED

Now your complete foundation is:

| #  | Problem           | Pattern                |
| -- | ----------------- | ---------------------- |
| 1  | Maximum Element   | Linear Traversal       |
| 2  | Minimum Element   | Linear Traversal       |
| 3  | Second Largest    | One-Pass Tracking      |
| 4  | Frequency         | Counter                |
| 5  | Remove Duplicates | Set / Hashing          |
| 6  | Two Sum           | Complement Hashing     |
| 7  | Reverse Array     | Two Pointers           |
| 8  | Move Zeros        | In-place Rearrangement |
| 9  | Missing Number    | Math / XOR             |
| 10 | Maximum Subarray  | Kadane                 |

---

# 🧠 ARRAY PATTERN MAP

This is what you should remember—not 10 pieces of code.

```text
                    ARRAYS
                       │
       ┌───────────────┼────────────────┐
       ↓               ↓                ↓
   TRAVERSAL        HASHING          POINTERS
       │               │                │
   ┌───┴───┐       ┌───┴────┐      ┌───┴─────┐
   ↓       ↓       ↓        ↓      ↓         ↓
 Maximum Minimum  Duplicate Two    Reverse   Move
                    │       Sum              Zeros
                    ↓
                  Missing
```

And:

```text
Contiguous + Maximum Sum
          ↓
       Kadane
```

---

# 🔥 ARRAY MASTERY — WHAT YOU SHOULD NOW BE ABLE TO RECOGNIZE

| If question says...    | Think...               |
| ---------------------- | ---------------------- |
| Largest element        | Linear traversal       |
| Smallest element       | Linear traversal       |
| Second largest         | Two-variable tracking  |
| Count occurrence       | Counter                |
| Remove duplicates      | Set                    |
| Pair + target          | Hashing / complement   |
| Reverse in-place       | Two pointers           |
| Move zeros             | In-place rearrangement |
| One number missing     | Sum / XOR              |
| Maximum contiguous sum | Kadane                 |

---

# ⚠️ BUT DON'T CALL ARRAYS "MASTERED" YET

You've **completed the learning set**, but there is one more stage.

You need to prove you can solve **unseen variations**.

### Your Array Mastery Test should contain:

**5 questions — no pattern labels**

For example:

```text
Q1 → Find the element occurring most frequently.
Q2 → Rearrange an array so negative values come first.
Q3 → Find a pair whose difference is K.
Q4 → Find the maximum sum of a contiguous portion.
Q5 → Find the first element that appears only once.
```

You must identify the pattern yourself.

That's the difference between:

> **"I studied arrays."**

and

> **"I can solve basic array problems."**

---

## 🔒 ARRAY TOPIC STATUS

**Learning Set:** ✅ 10/10
**Pattern Coverage:** ✅
**Built-in + Manual Solutions:** ✅
**Dry Runs:** ✅
**Complexity:** ✅
**Edge Cases:** ✅
**Pattern Recognition:** ✅
**Unseen Problem Test:** ⏳

**Next topic in our locked roadmap: STRINGS — Conversation 1, Problems 1–4.**

Would you like to start Strings with Problem 1, or take the unseen Array mastery test first?
