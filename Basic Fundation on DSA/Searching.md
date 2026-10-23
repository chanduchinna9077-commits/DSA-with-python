# 🔴 4. SEARCHING — 10 Problems

### Patterns

```text
Linear Search
Binary Search
First occurrence
Last occurrence
Counting occurrences
Search in sorted array
Search position
Condition-based search
```

### Problems

1. Linear Search
2. Find First Occurrence
3. Find Last Occurrence
4. Count Occurrences
5. Binary Search
6. Search Insert Position
7. Find Minimum in Sorted Array
8. Find Maximum in Sorted Array
9. Square Root using Binary Search
10. Search in Rotated Sorted Array

For **Basic DSA**, #1–#6 are the priority.

---


# 🔵 SEARCHING — CONVERSATION 1

## Problems 1–4

We are starting **Searching** with the locked TopGun/basic-DSA execution format.

### 🎯 Session Mission

| Problem              | Pattern                           | Difficulty |
| -------------------- | --------------------------------- | ---------- |
| 1. Linear Search     | Linear Traversal                  | 🟢 Basic   |
| 2. First Occurrence  | Linear Search + Position Tracking | 🟢 Basic   |
| 3. Last Occurrence   | Linear Search + Position Tracking | 🟢 Basic   |
| 4. Count Occurrences | Linear Search + Counter           | 🟢 Basic   |

---

# 🔹 PROBLEM 1 — Linear Search

## 1. Problem Statement

Given an array and a target value, find whether the target exists in the array.

If found, return its **index**. Otherwise, return `-1`.

### Example

```text
Array = [10, 25, 30, 45, 50]
Target = 30

Output = 2
```

Because `30` is present at index `2`.

If:

```text
Target = 100
```

Output:

```text
-1
```

---

## 2. Problem Theory

**Linear Search** means checking elements **one by one from left to right** until:

1. We find the target, or
2. We reach the end.

It works on:

* Sorted arrays
* Unsorted arrays
* Arrays with duplicates

No sorting is required.

---

## 3. Pattern Being Tested

### 🔥 Pattern: Linear Traversal

```text
Start → Check → Move → Check → Move → ...
```

The core structure is:

```python
for each element:
    if element == target:
        return index
```

---

## 4. ELI10 Intuition

Imagine you are looking for your friend in a line of students.

You don't know where they are.

So you ask:

```text
Student 1 → Is your name Rahul? ❌
Student 2 → Is your name Rahul? ❌
Student 3 → Is your name Rahul? ✅
```

You stop immediately.

That's linear search.

---

# 5. Example

```text
arr = [8, 3, 15, 6, 20]
target = 6
```

Search:

```text
index 0 → 8 == 6 ❌
index 1 → 3 == 6 ❌
index 2 → 15 == 6 ❌
index 3 → 6 == 6 ✅
```

Answer:

```text
3
```

---

# 6. Algorithm — Step-by-Step

### Algorithm

1. Start from index `0`.
2. Look at the current element.
3. Compare it with the target.
4. If equal:

   * return the current index.
5. Otherwise move to the next index.
6. Continue until the array ends.
7. If target was never found, return `-1`.

### Pseudocode

```text
FOR i from 0 to n-1:
    IF arr[i] == target:
        RETURN i

RETURN -1
```

---

# 7. Python Solution — Using Built-in Method

Python provides `.index()`.

```python
arr = [8, 3, 15, 6, 20]
target = 6

if target in arr:
    index = arr.index(target)
else:
    index = -1

print(index)
```

### Output

```text
3
```

### Important

Do **not** blindly write:

```python
arr.index(target)
```

because if the target does not exist, Python raises:

```text
ValueError
```

---

# 8. Python Solution — Without Built-in Search Methods

```python
arr = [8, 3, 15, 6, 20]
target = 6

index = -1

for i in range(len(arr)):
    if arr[i] == target:
        index = i
        break

print(index)
```

### Output

```text
3
```

---

# 9. Line-by-Line Explanation

```python
index = -1
```

We initially assume the target does not exist.

---

```python
for i in range(len(arr)):
```

Visit every index.

For:

```python
arr = [8, 3, 15, 6, 20]
```

`i` becomes:

```text
0
1
2
3
4
```

---

```python
if arr[i] == target:
```

Check whether the current element equals the target.

---

```python
index = i
```

If found, store its index.

---

```python
break
```

Stop searching.

There is no reason to continue because we only need the **first occurrence**.

---

```python
print(index)
```

Print the answer.

---

# 10. Detailed Dry Run

```text
arr = [8, 3, 15, 6, 20]
target = 6
```

| Step | `i` | `arr[i]` | Target | Match? | Action             |
| ---: | --: | -------: | -----: | ------ | ------------------ |
|    1 |   0 |        8 |      6 | ❌      | Continue           |
|    2 |   1 |        3 |      6 | ❌      | Continue           |
|    3 |   2 |       15 |      6 | ❌      | Continue           |
|    4 |   3 |        6 |      6 | ✅      | `index = 3`, break |

### Final Answer

```text
3
```

---

# 11. Complexity

### Time

Worst case:

```text
O(n)
```

Because we may inspect every element.

Best case:

```text
O(1)
```

If target is at index `0`.

### Space

```text
O(1)
```

No additional data structure is required.

---

# 12. Edge Cases

### Empty array

```python
arr = []
target = 5
```

Answer:

```text
-1
```

### Target at first position

```text
[10, 20, 30]
target = 10
```

Answer:

```text
0
```

### Target at last position

```text
[10, 20, 30]
target = 30
```

Answer:

```text
2
```

### Target absent

```text
[10, 20, 30]
target = 50
```

Answer:

```text
-1
```

### Duplicate values

```text
[5, 2, 5, 8]
target = 5
```

Answer:

```text
0
```

Because we stop at the **first** occurrence.

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Returning the value instead of index

```python
return arr[i]
```

The question asks for the **index**.

Correct:

```python
return i
```

### ❌ Mistake 2 — Forgetting `-1`

If the target doesn't exist, we need a clear answer:

```python
-1
```

### ❌ Mistake 3 — Continuing after finding target

If we want the first occurrence:

```python
break
```

after finding it.

---

# 14. Pattern Recognition

> **When you see:**
> "Find whether an element exists" / "Find the index of target"
>
> **Think:**
> 🔥 **Linear Search**

If the array is **unsorted** and no special structure exists:

```text
→ Linear Search
```

---

# 🔵 PROBLEM 2 — First Occurrence

## 1. Problem Statement

Given an array and a target value, find the **first index** where the target occurs.

If it doesn't exist, return `-1`.

### Example

```text
Array = [4, 7, 2, 7, 9, 7]
Target = 7
```

Occurrences:

```text
index 1 → 7
index 3 → 7
index 5 → 7
```

Answer:

```text
1
```

---

# 2. Problem Theory

This is still **Linear Search**.

The only difference is that the array may contain duplicates.

We need the **first** occurrence.

Therefore:

```text
Search from LEFT → RIGHT
```

and stop at the first match.

---

# 3. Pattern Being Tested

### 🔥 Linear Search + Early Exit

```text
LEFT → RIGHT
   ↓
First match → STOP
```

---

# 4. ELI10 Intuition

Suppose you have:

```text
[Apple, Mango, Apple, Banana, Apple]
```

Someone asks:

> Where is the first Apple?

You start from the left:

```text
Apple ← Found!
```

You don't continue searching.

That's the entire idea.

---

# 5. Example

```text
arr = [5, 8, 3, 8, 10]
target = 8
```

```text
index 0 → 5 ❌
index 1 → 8 ✅
```

Answer:

```text
1
```

---

# 6. Algorithm — Step-by-Step

1. Start from index `0`.
2. Check the current element.
3. If it equals target:

   * return its index immediately.
4. Otherwise continue.
5. If the loop ends:

   * return `-1`.

---

# 7. Python — Using Built-in Method

```python
arr = [5, 8, 3, 8, 10]
target = 8

if target in arr:
    result = arr.index(target)
else:
    result = -1

print(result)
```

Output:

```text
1
```

---

# 8. Python — Without Built-in Method

```python
arr = [5, 8, 3, 8, 10]
target = 8

result = -1

for i in range(len(arr)):
    if arr[i] == target:
        result = i
        break

print(result)
```

---

# 9. Line-by-Line Explanation

```python
result = -1
```

Assume target doesn't exist.

```python
for i in range(len(arr)):
```

Visit every index from left to right.

```python
if arr[i] == target:
```

Check for a match.

```python
result = i
```

Save the first matching index.

```python
break
```

Stop immediately.

---

# 10. Detailed Dry Run

```text
arr = [5, 8, 3, 8, 10]
target = 8
```

| `i` | `arr[i]` | Match? | Action         |
| --: | -------: | ------ | -------------- |
|   0 |        5 | ❌      | Continue       |
|   1 |        8 | ✅      | Save `1`, stop |

Final:

```text
1
```

---

# 11. Complexity

Time:

```text
O(n)
```

Worst case.

Space:

```text
O(1)
```

---

# 12. Edge Cases

```text
[] → -1
[5] target=5 → 0
[5] target=10 → -1
[5,5,5] target=5 → 0
```

---

# 13. Common Mistakes / Traps

### ❌ Searching from right to left

That finds the **last** occurrence.

For first occurrence:

```text
LEFT → RIGHT
```

### ❌ Not using `break`

You may overwrite the first answer with a later occurrence.

---

# 14. Pattern Recognition

> **"First occurrence"**
>
> → Search **left to right**
>
> → Stop at first match.

---

# 🔵 PROBLEM 3 — Last Occurrence

## 1. Problem Statement

Given an array and target, find the **last index** where the target occurs.

Return `-1` if it doesn't exist.

### Example

```text
arr = [4, 7, 2, 7, 9, 7]
target = 7
```

Occurrences:

```text
1
3
5
```

Answer:

```text
5
```

---

# 2. Problem Theory

This is the opposite of first occurrence.

For the first occurrence:

```text
LEFT → RIGHT
STOP at first match
```

For the last occurrence, two approaches are possible.

### Approach A

Search left → right and keep updating the answer.

### Approach B

Search right → left and stop at the first match.

For beginners, both are important.

---

# 3. Pattern Being Tested

### 🔥 Linear Search + Position Tracking

```text
Every match → update answer
```

or:

```text
RIGHT → LEFT
First match → STOP
```

---

# 4. ELI10 Intuition

Imagine:

```text
A B C B D B
```

You want the **last B**.

Start from the right:

```text
B ← Found!
```

Done.

---

# 5. Example

```text
arr = [10, 5, 7, 5, 8, 5]
target = 5
```

From right:

```text
index 5 → 5 ✅
```

Answer:

```text
5
```

---

# 6. Algorithm — Step-by-Step

### Method used here: right-to-left

1. Start from the final index.
2. Check the current element.
3. If it equals target:

   * return index.
4. Otherwise move one position left.
5. If nothing matches, return `-1`.

---

# 7. Python — Using Built-in Method

Python's `list.index()` can find from a specified range, but for clarity we can use reversed enumeration.

```python
arr = [10, 5, 7, 5, 8, 5]
target = 5

result = -1

for i in range(len(arr) - 1, -1, -1):
    if arr[i] == target:
        result = i
        break

print(result)
```

Output:

```text
5
```

This is already the cleanest direct approach; there isn't a single basic list method equivalent to "last index" for arbitrary lists.

---

# 8. Python — Without Built-in Search Method

```python
arr = [10, 5, 7, 5, 8, 5]
target = 5

result = -1

i = len(arr) - 1

while i >= 0:
    if arr[i] == target:
        result = i
        break

    i -= 1

print(result)
```

---

# 9. Line-by-Line Explanation

```python
result = -1
```

Default answer if target doesn't exist.

---

```python
i = len(arr) - 1
```

Start at the final index.

For:

```text
[10, 5, 7, 5, 8, 5]
```

last index is:

```text
5
```

---

```python
while i >= 0:
```

Continue until we pass the beginning.

---

```python
if arr[i] == target:
```

Check current element.

---

```python
result = i
break
```

We found the last occurrence, so stop.

---

```python
i -= 1
```

Move one position to the left.

---

# 10. Detailed Dry Run

```text
arr = [10, 5, 7, 5, 8, 5]
target = 5
```

| Step | `i` | `arr[i]` | Match? | Action        |
| ---: | --: | -------: | ------ | ------------- |
|    1 |   5 |        5 | ✅      | Save 5 → Stop |

Answer:

```text
5
```

### Another example

```text
arr = [10, 5, 7, 5, 8, 6]
target = 5
```

| Step | `i` | Value | Match? |
| ---: | --: | ----: | ------ |
|    1 |   5 |     6 | ❌      |
|    2 |   4 |     8 | ❌      |
|    3 |   3 |     5 | ✅      |

Answer:

```text
3
```

---

# 11. Complexity

Time:

```text
O(n)
```

Worst case.

Space:

```text
O(1)
```

---

# 12. Edge Cases

### One element

```text
[5], target=5 → 0
```

### Target absent

```text
[1,2,3], target=5 → -1
```

### All elements same

```text
[7,7,7,7]
```

Last occurrence:

```text
3
```

### Target at final position

Immediately found:

```text
O(1)
```

---

# 13. Common Mistakes / Traps

### ❌ Starting from index 0 and immediately breaking

That gives the **first** occurrence.

### ❌ Forgetting to decrement

```python
i -= 1
```

Without it, the `while` loop never progresses.

### ❌ Using `len(arr)` as an index

Wrong:

```python
i = len(arr)
```

Correct:

```python
i = len(arr) - 1
```

Because indexes start from `0`.

---

# 14. Pattern Recognition

> **"Last occurrence"**
>
> Think:
>
> 🔥 **RIGHT → LEFT + STOP**

Alternative:

```text
LEFT → RIGHT
update answer every time
```

Both are valid.

---

# 🔵 PROBLEM 4 — Count Occurrences

## 1. Problem Statement

Given an array and a target, count how many times the target appears.

### Example

```text
arr = [2, 5, 2, 8, 2, 9]
target = 2
```

`2` occurs:

```text
3 times
```

Output:

```text
3
```

---

# 2. Problem Theory

This is another simple linear traversal.

But instead of stopping after finding the target, we maintain a **counter**.

Core idea:

```text
If match:
    count += 1
```

---

# 3. Pattern Being Tested

### 🔥 Linear Traversal + Counter

```text
Initialize count = 0

for every element:
    if target:
        count += 1
```

---

# 4. ELI10 Intuition

Imagine counting how many red balls are in a box.

You check each ball:

```text
Red → count = 1
Blue → nothing
Red → count = 2
Green → nothing
Red → count = 3
```

Final answer:

```text
3
```

---

# 5. Example

```text
arr = [4, 4, 2, 7, 4, 9]
target = 4
```

Matches:

```text
index 0 → 4
index 1 → 4
index 4 → 4
```

Answer:

```text
3
```

---

# 6. Algorithm — Step-by-Step

1. Create a variable `count = 0`.
2. Traverse every element.
3. Compare the current element with target.
4. If equal:

   * increment `count`.
5. Continue until the array ends.
6. Return `count`.

### Pseudocode

```text
count = 0

FOR each element:
    IF element == target:
        count = count + 1

RETURN count
```

---

# 7. Python — Using Built-in Method

Python provides:

```python
list.count()
```

```python
arr = [4, 4, 2, 7, 4, 9]
target = 4

count = arr.count(target)

print(count)
```

Output:

```text
3
```

---

# 8. Python — Without Built-in Method

```python
arr = [4, 4, 2, 7, 4, 9]
target = 4

count = 0

for i in range(len(arr)):
    if arr[i] == target:
        count += 1

print(count)
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

Initially we have found zero occurrences.

---

```python
for i in range(len(arr)):
```

Visit every index.

---

```python
if arr[i] == target:
```

Check whether current element is target.

---

```python
count += 1
```

If yes, increase the counter.

Equivalent to:

```python
count = count + 1
```

---

```python
print(count)
```

Display total occurrences.

---

# 10. Detailed Dry Run

```text
arr = [4, 4, 2, 7, 4, 9]
target = 4
```

| Step | Index | Value | Match? | Count |
| ---: | ----: | ----: | ------ | ----: |
|    1 |     0 |     4 | ✅      |     1 |
|    2 |     1 |     4 | ✅      |     2 |
|    3 |     2 |     2 | ❌      |     2 |
|    4 |     3 |     7 | ❌      |     2 |
|    5 |     4 |     4 | ✅      |     3 |
|    6 |     5 |     9 | ❌      |     3 |

Final:

```text
count = 3
```

---

# 11. Complexity

Time:

```text
O(n)
```

We must inspect every element.

Space:

```text
O(1)
```

Only one counter is used.

---

# 12. Edge Cases

### Empty array

```text
[] → 0
```

### Target doesn't exist

```text
[1,2,3], target=5 → 0
```

### Every element is target

```text
[5,5,5,5]
```

Answer:

```text
4
```

### Single element

```text
[5], target=5 → 1
```

```text
[5], target=10 → 0
```

---

# 13. Common Mistakes / Traps

### ❌ Using `break`

Don't do this:

```python
if arr[i] == target:
    count += 1
    break
```

That counts only the first occurrence.

---

### ❌ Forgetting initialization

You need:

```python
count = 0
```

before traversal.

---

### ❌ Returning immediately

```python
if arr[i] == target:
    return 1
```

This answers "does it exist?" rather than "how many times?"

---

# 14. Pattern Recognition

> **"Count how many times X occurs"**
>
> Think:
>
> 🔥 **Traversal + Counter**

Template:

```python
count = 0

for element in arr:
    if element == target:
        count += 1
```

---

# 🧠 SEARCHING — CONVERSATION 1 PATTERN MAP

We have now covered the first four searching patterns.

| Problem              | Core Pattern           | Mental Trigger   |
| -------------------- | ---------------------- | ---------------- |
| 1. Linear Search     | Traversal              | "Find target"    |
| 2. First Occurrence  | Traversal + Early Exit | "First position" |
| 3. Last Occurrence   | Reverse Traversal      | "Last position"  |
| 4. Count Occurrences | Traversal + Counter    | "How many?"      |

---

# 🔥 THE MOST IMPORTANT CONNECTION

These four problems are **not four completely different algorithms**.

They are variations of the same fundamental pattern:

```text
TRAVERSE THE ARRAY
        ↓
      CHECK
        ↓
    TAKE ACTION
```

The **action** changes.

### 1️⃣ Find target

```python
if arr[i] == target:
    return i
```

### 2️⃣ First occurrence

```python
if arr[i] == target:
    return i
```

Same logic — left-to-right.

### 3️⃣ Last occurrence

```python
if arr[i] == target:
    return i
```

But traversal is:

```text
right → left
```

### 4️⃣ Count

```python
if arr[i] == target:
    count += 1
```

---

# 🎯 MASTER TEMPLATES

## Template 1 — Find First

```python
for i in range(len(arr)):
    if arr[i] == target:
        return i

return -1
```

---

## Template 2 — Find Last

```python
for i in range(len(arr) - 1, -1, -1):
    if arr[i] == target:
        return i

return -1
```

---

## Template 3 — Count

```python
count = 0

for i in range(len(arr)):
    if arr[i] == target:
        count += 1

return count
```

---

# 🧠 SENIOR PATTERN RECOGNITION

When the question says:

| Question wording         | Immediately think        |
| ------------------------ | ------------------------ |
| "Does X exist?"          | Linear Search            |
| "Find index of X"        | Linear Search            |
| "Find first X"           | Left → Right             |
| "Find last X"            | Right → Left             |
| "How many X?"            | Counter                  |
| "Return -1 if not found" | Sentinel value           |
| "Array is unsorted"      | Linear Search is natural |

### Core mental rule

```text
FIRST  → LEFT → RIGHT → STOP
LAST   → RIGHT → LEFT → STOP
COUNT  → LEFT → RIGHT → COUNT
```

---

# ⚠️ TOPGUN SCREENING TAKEAWAY

For basic-level coding, these four problems are designed to test whether you understand:

```text
for loop
↓
index
↓
comparison
↓
counter
↓
break
↓
return
```

If you cannot comfortably write these **without `max()`, `min()`, `.index()`, `.count()`, etc.**, your array traversal foundation is not yet strong enough.

### Your current DSA progress

```text
ARRAYS       10/10 ✅
STRINGS      10/10 ✅
HASHING      10/10 ✅
SEARCHING     4/10 🔵
```

**Next locked set:** Searching Conversation 2 → **Problems 5–8**

1. Binary Search
2. Search Insert Position
3. Find Minimum in Sorted Array
4. Find Maximum in Sorted Array

Would you like to continue with Searching — Conversation 2, or try a short mastery quiz on Problems 1–4 first?

# 🔵 SEARCHING — CONVERSATION 2

## Problems 5–8

We continue **exactly from the locked Searching roadmap**.

| # | Problem                      | Main Pattern                      | Level           |
| - | ---------------------------- | --------------------------------- | --------------- |
| 5 | Binary Search                | Divide & Conquer / Two Pointers   | 🟢 Basic–Medium |
| 6 | Search Insert Position       | Binary Search                     | 🟢 Basic–Medium |
| 7 | Find Minimum in Sorted Array | Binary Search / Boundary Thinking | 🟢 Basic–Medium |
| 8 | Find Maximum in Sorted Array | Binary Search / Boundary Thinking | 🟢 Basic–Medium |

> 🔥 **Important:** Problems 5–8 are where we transition from **linear search `O(n)`** to **binary search `O(log n)`**.

---

# 🔵 PROBLEM 5 — Binary Search

## 1. Problem Statement

Given a **sorted array** and a target value, find the index of the target.

If the target doesn't exist, return `-1`.

### Example

```text
arr = [2, 5, 8, 12, 16, 20, 25]
target = 16

Output = 4
```

---

# 2. Problem Theory

Binary Search works only when we have an important property:

> **The array is sorted.**

Instead of checking every element, we repeatedly eliminate **half of the remaining search space**.

Linear Search:

```text
Check 1
Check 2
Check 3
Check 4
...
```

Binary Search:

```text
Check middle
   ↓
Discard half
   ↓
Check middle
   ↓
Discard half
```

That's why binary search is much faster for large sorted arrays.

---

# 3. Pattern Being Tested

### 🔥 Pattern: Binary Search

Three variables:

```text
left
mid
right
```

Core formula:

```python
mid = (left + right) // 2
```

Then:

```text
arr[mid] == target → FOUND

arr[mid] < target → search RIGHT half

arr[mid] > target → search LEFT half
```

---

# 4. ELI10 Intuition

Imagine looking for a word in a dictionary.

You don't start at page 1.

You open somewhere in the middle.

Suppose you're looking for:

```text
"Mango"
```

You open the middle.

If the middle says:

```text
"Orange"
```

You know Mango must be **before Orange**.

So you throw away half the dictionary.

Then repeat.

That's binary search.

---

# 5. Example

```text
arr = [2, 5, 8, 12, 16, 20, 25]
target = 16
```

Indexes:

```text
 0   1   2   3   4   5   6
[2,  5,  8, 12, 16, 20, 25]
```

Initial:

```text
left = 0
right = 6
```

Middle:

```text
mid = (0 + 6) // 2
    = 3
```

```text
arr[3] = 12
```

Since:

```text
12 < 16
```

Target must be on the right.

So:

```text
left = 4
```

Now:

```text
left = 4
right = 6
mid = 5
```

```text
arr[5] = 20
```

Since:

```text
20 > 16
```

Search left:

```text
right = 4
```

Now:

```text
left = 4
right = 4
mid = 4
```

```text
arr[4] = 16
```

Found.

Answer:

```text
4
```

---

# 6. Algorithm — Step-by-Step

### Algorithm

1. Set `left = 0`.
2. Set `right = len(arr) - 1`.
3. While `left <= right`:

   * Calculate middle.
   * Compare `arr[mid]` with target.
4. If equal:

   * return `mid`.
5. If `arr[mid] < target`:

   * target is on the right.
   * move `left`.
6. If `arr[mid] > target`:

   * target is on the left.
   * move `right`.
7. If loop finishes:

   * target doesn't exist.
   * return `-1`.

### Pseudocode

```text
left = 0
right = n - 1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid

    if arr[mid] < target:
        left = mid + 1

    else:
        right = mid - 1

return -1
```

---

# 7. Python Solution — Using Built-in Method

Python does not have a simple built-in `binary_search()` for lists.

For a sorted list, the standard library provides `bisect`, which performs binary-search-based insertion-point operations.

For finding the exact target:

```python
import bisect

arr = [2, 5, 8, 12, 16, 20, 25]
target = 16

index = bisect.bisect_left(arr, target)

if index < len(arr) and arr[index] == target:
    print(index)
else:
    print(-1)
```

Output:

```text
4
```

### What does `bisect_left()` do?

It finds the position where `target` could be inserted while keeping the list sorted.

For:

```text
[2, 5, 8, 12, 16, 20, 25]
```

and:

```text
target = 16
```

it returns:

```text
4
```

---

# 8. Python Solution — Without Built-in Search Method

This is the version you **must master for screening tests**.

```python
arr = [2, 5, 8, 12, 16, 20, 25]
target = 16

left = 0
right = len(arr) - 1

result = -1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        result = mid
        break

    elif arr[mid] < target:
        left = mid + 1

    else:
        right = mid - 1

print(result)
```

Output:

```text
4
```

---

# 9. Line-by-Line Explanation

```python
left = 0
```

Start of search range.

---

```python
right = len(arr) - 1
```

End of search range.

---

```python
result = -1
```

Assume target isn't present.

---

```python
while left <= right:
```

Continue while there is still a valid search range.

This condition is extremely important.

---

```python
mid = (left + right) // 2
```

Find the middle index.

---

```python
if arr[mid] == target:
```

If middle element is target, we found it.

---

```python
result = mid
break
```

Store the answer and stop.

---

```python
elif arr[mid] < target:
```

Middle value is too small.

Because the array is sorted:

```text
everything LEFT of mid
is also smaller
```

So discard the left half.

---

```python
left = mid + 1
```

Search right half.

---

```python
else:
    right = mid - 1
```

Middle value is too large.

Search left half.

---

# 10. Detailed Dry Run

```text
arr = [2, 5, 8, 12, 16, 20, 25]
target = 16
```

| Step | Left | Right | Mid | `arr[mid]` | Decision        |
| ---: | ---: | ----: | --: | ---------: | --------------- |
|    1 |    0 |     6 |   3 |         12 | 12 < 16 → right |
|    2 |    4 |     6 |   5 |         20 | 20 > 16 → left  |
|    3 |    4 |     4 |   4 |         16 | Found           |

Answer:

```text
4
```

---

# 11. Complexity

### Time

```text
O(log n)
```

Why?

Every iteration removes approximately half of the remaining elements.

For example:

```text
1,000,000
→ 500,000
→ 250,000
→ 125,000
→ ...
```

Only around 20 checks are needed to reduce one million elements to one.

### Space

```text
O(1)
```

Iterative binary search uses only `left`, `right`, `mid`.

---

# 12. Edge Cases

### Empty array

```python
arr = []
```

Answer:

```text
-1
```

### One element

```text
[10], target = 10 → 0
```

### One element, target absent

```text
[10], target = 5 → -1
```

### Target at beginning

```text
[2,5,8,12]
target = 2
```

Answer:

```text
0
```

### Target at end

```text
[2,5,8,12]
target = 12
```

Answer:

```text
3
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Using binary search on an unsorted array

Wrong:

```text
[8, 2, 15, 4, 10]
```

Binary search relies on sorted order.

---

### ❌ Mistake 2 — Wrong loop condition

Usually:

```python
while left <= right:
```

for this closed-interval implementation.

---

### ❌ Mistake 3 — Forgetting `+1`

Wrong:

```python
left = mid
```

Correct:

```python
left = mid + 1
```

Otherwise you can get stuck.

---

### ❌ Mistake 4 — Forgetting `-1`

Wrong:

```python
right = mid
```

Correct:

```python
right = mid - 1
```

---

# 14. Pattern Recognition

> **When you see:**
> "sorted array + search for target"
>
> Think:
>
> 🔥 **Binary Search**

Mental rule:

```text
SORTED + SEARCH
      ↓
BINARY SEARCH
      ↓
O(log n)
```

---

# 🔵 PROBLEM 6 — Search Insert Position

## 1. Problem Statement

Given a sorted array and a target:

* If target exists → return its index.
* If target doesn't exist → return the position where it should be inserted to maintain sorted order.

### Example 1

```text
arr = [1, 3, 5, 6]
target = 5
```

Output:

```text
2
```

### Example 2

```text
arr = [1, 3, 5, 6]
target = 2
```

Output:

```text
1
```

Because:

```text
[1, 2, 3, 5, 6]
    ↑
  index 1
```

---

# 2. Problem Theory

This is a **binary-search boundary problem**.

We aren't only asking:

> "Does target exist?"

We're asking:

> "Where is the first position where target can be placed?"

This is one of the most important binary-search concepts.

---

# 3. Pattern Being Tested

### 🔥 Lower Bound / Insertion Position

We want:

```text
first index where arr[index] >= target
```

Example:

```text
arr = [1, 3, 5, 6]
target = 4
```

First value `>= 4` is:

```text
5
```

Index:

```text
2
```

Therefore answer = `2`.

---

# 4. ELI10 Intuition

Imagine students standing in height order:

```text
150 160 170 180
```

A new student is `165`.

Where should they stand?

```text
150 160 [165] 170 180
         ↑
       index 2
```

We need to find the first position where the target can fit.

---

# 5. Example

```text
arr = [1, 3, 5, 6]
target = 2
```

We want:

```text
[1, 2, 3, 5, 6]
```

So answer:

```text
1
```

---

# 6. Algorithm — Step-by-Step

Use two pointers:

```text
left = 0
right = n
```

Notice:

> `right = n`, not `n - 1`.

We search for a boundary.

While:

```text
left < right
```

1. Calculate `mid`.
2. If `arr[mid] < target`:

   * target must come after `mid`.
   * `left = mid + 1`
3. Otherwise:

   * `arr[mid] >= target`
   * `mid` could be the answer.
   * move `right = mid`
4. At the end:

   * `left` is the insertion position.

---

# 7. Python — Using Built-in Method

Python's `bisect_left()` directly implements this lower-bound operation.

```python
import bisect

arr = [1, 3, 5, 6]
target = 2

position = bisect.bisect_left(arr, target)

print(position)
```

Output:

```text
1
```

---

# 8. Python — Without Built-in Method

```python
arr = [1, 3, 5, 6]
target = 2

left = 0
right = len(arr)

while left < right:

    mid = (left + right) // 2

    if arr[mid] < target:
        left = mid + 1

    else:
        right = mid

print(left)
```

Output:

```text
1
```

---

# 9. Line-by-Line Explanation

```python
left = 0
```

Start of array.

---

```python
right = len(arr)
```

We use `n` because the answer can legally be at the position **after the final element**.

Example:

```text
[1, 2, 3]
target = 10
```

Answer:

```text
3
```

---

```python
while left < right:
```

We are searching for a boundary.

---

```python
mid = (left + right) // 2
```

Find middle.

---

```python
if arr[mid] < target:
```

Current value is too small.

So insertion position must be after `mid`.

```python
left = mid + 1
```

---

```python
else:
    right = mid
```

Current value is greater than or equal to target.

Therefore `mid` itself could be the answer.

We **do not discard `mid`**.

That's why:

```python
right = mid
```

not:

```python
right = mid - 1
```

---

# 10. Detailed Dry Run

```text
arr = [1, 3, 5, 6]
target = 2
```

Initial:

```text
left = 0
right = 4
```

| Step | Left | Right | Mid | `arr[mid]` | Decision          |
| ---: | ---: | ----: | --: | ---------: | ----------------- |
|    1 |    0 |     4 |   2 |          5 | 5 ≥ 2 → `right=2` |
|    2 |    0 |     2 |   1 |          3 | 3 ≥ 2 → `right=1` |
|    3 |    0 |     1 |   0 |          1 | 1 < 2 → `left=1`  |

Now:

```text
left = right = 1
```

Answer:

```text
1
```

---

# 11. Complexity

Time:

```text
O(log n)
```

Space:

```text
O(1)
```

---

# 12. Edge Cases

### Target smaller than everything

```text
[3,5,7]
target = 1
```

Answer:

```text
0
```

### Target larger than everything

```text
[3,5,7]
target = 10
```

Answer:

```text
3
```

### Target exactly exists

```text
[3,5,7]
target = 5
```

Answer:

```text
1
```

### Empty array

```text
[]
target = 5
```

Answer:

```text
0
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```python
right = len(arr) - 1
```

for this exact lower-bound implementation.

Use:

```python
right = len(arr)
```

---

### ❌ Mistake 2

Writing:

```python
right = mid - 1
```

when `arr[mid] >= target`.

That can skip the correct insertion position.

Correct:

```python
right = mid
```

---

### ❌ Mistake 3

Thinking the answer must be an existing index.

It doesn't.

For:

```text
[1,3,5]
target=4
```

answer is:

```text
2
```

---

# 14. Pattern Recognition

> **"Where should target be inserted?"**
>
> Think:
>
> 🔥 **Lower Bound**
>
> Find:
>
> ```text
> first index where arr[i] >= target
> ```

This pattern becomes extremely important in later binary-search problems.

---

# 🔵 PROBLEM 7 — Find Minimum in Sorted Array

## 1. Problem Statement

Given a sorted array, find the minimum element.

### Example

```text
arr = [2, 5, 8, 12, 20]
```

Output:

```text
2
```

---

# 2. Problem Theory

For a **normally ascending sorted array**, the minimum is simply the first element.

```text
[2, 5, 8, 12, 20]
 ↑
minimum
```

However, because this is our **binary-search section**, the important lesson is recognizing the boundary property.

For a normally sorted array:

```python
arr[0]
```

is enough.

But we can also use binary-search-style reasoning.

---

# 3. Pattern Being Tested

### 🔥 Sorted Array + Boundary Reasoning

For ascending order:

```text
minimum = leftmost element
```

This problem is intentionally basic.

It teaches an important interview habit:

> **Don't use binary search when the answer is already directly available.**

---

# 4. ELI10 Intuition

If books are arranged from shortest to tallest:

```text
shortest → tallest
```

the first book is automatically the shortest.

Same with a sorted ascending array.

---

# 5. Example

```text
arr = [3, 7, 10, 15, 20]
```

Minimum:

```text
3
```

---

# 6. Algorithm — Step-by-Step

### Direct sorted-array approach

1. Check whether the array is empty.
2. Since the array is ascending:

   * return the first element.

### Algorithm

```text
IF array is empty:
    no minimum

ELSE:
    minimum = arr[0]
```

---

# 7. Python — Using Built-in Method

```python
arr = [3, 7, 10, 15, 20]

if len(arr) > 0:
    minimum = min(arr)
    print(minimum)
else:
    print("Array is empty")
```

Output:

```text
3
```

---

# 8. Python — Without Built-in Method

```python
arr = [3, 7, 10, 15, 20]

if len(arr) == 0:
    print("Array is empty")
else:
    minimum = arr[0]

    for i in range(1, len(arr)):
        if arr[i] < minimum:
            minimum = arr[i]

    print(minimum)
```

Output:

```text
3
```

### Important

This manual traversal works even if the array is **not sorted**.

For a sorted array, however, we can exploit the ordering:

```python
minimum = arr[0]
```

in `O(1)` time.

---

# 9. Line-by-Line Explanation

```python
if len(arr) == 0:
```

Check whether array is empty.

---

```python
minimum = arr[0]
```

Initially assume the first element is minimum.

---

```python
for i in range(1, len(arr)):
```

Start checking from the second element.

---

```python
if arr[i] < minimum:
```

If current value is smaller, update.

---

```python
minimum = arr[i]
```

Store the new minimum.

---

# 10. Detailed Dry Run

```text
arr = [3, 7, 10, 15, 20]
```

Initial:

```text
minimum = 3
```

| Step | Index | Value | Current Minimum | Update? |
| ---: | ----: | ----: | --------------: | ------- |
|    1 |     1 |     7 |               3 | ❌       |
|    2 |     2 |    10 |               3 | ❌       |
|    3 |     3 |    15 |               3 | ❌       |
|    4 |     4 |    20 |               3 | ❌       |

Final:

```text
3
```

---

# 11. Complexity

### Using sorted property

```text
Time: O(1)
Space: O(1)
```

Because:

```python
arr[0]
```

directly gives the minimum.

### Manual generic traversal

```text
Time: O(n)
Space: O(1)
```

---

# 12. Edge Cases

### One element

```text
[7] → 7
```

### Empty

```text
[] → no minimum
```

### Negative values

```text
[-10, -5, 0, 3]
```

Minimum:

```text
-10
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Assuming `min()` is always the intended solution

In a coding interview, they may explicitly prohibit built-ins.

Know the manual logic.

### ❌ Mistake 2 — Confusing sorted direction

For ascending:

```text
[1, 3, 5, 7]
```

minimum = first.

For descending:

```text
[7, 5, 3, 1]
```

minimum = last.

### ❌ Mistake 3 — Overengineering

If the array is guaranteed sorted ascending:

```python
arr[0]
```

is better than writing a complicated algorithm.

---

# 14. Pattern Recognition

> **Sorted ascending array + minimum**
>
> Think:
>
> 🔥 **Leftmost element**

```text
[MIN → ... → MAX]
 ↑
answer
```

---

# 🔵 PROBLEM 8 — Find Maximum in Sorted Array

## 1. Problem Statement

Given a sorted array in ascending order, find the maximum element.

### Example

```text
arr = [2, 5, 8, 12, 20]
```

Output:

```text
20
```

---

# 2. Problem Theory

For an ascending sorted array:

```text
[2, 5, 8, 12, 20]
 ↑                 ↑
MIN               MAX
```

The maximum is the **rightmost element**.

Therefore:

```python
arr[-1]
```

is enough.

---

# 3. Pattern Being Tested

### 🔥 Sorted Array + Boundary Reasoning

Ascending array:

```text
minimum → left boundary
maximum → right boundary
```

---

# 4. ELI10 Intuition

Imagine children arranged from shortest to tallest:

```text
shortest → tallest
```

The tallest child is standing at the end.

Same idea.

---

# 5. Example

```text
arr = [4, 8, 12, 17, 25]
```

Maximum:

```text
25
```

---

# 6. Algorithm — Step-by-Step

1. Check if the array is empty.
2. Because it is sorted ascending:

   * the final element is the maximum.
3. Return `arr[-1]`.

---

# 7. Python — Using Built-in Method

```python
arr = [4, 8, 12, 17, 25]

if len(arr) > 0:
    maximum = max(arr)
    print(maximum)
else:
    print("Array is empty")
```

Output:

```text
25
```

---

# 8. Python — Without Built-in Method

Since the array is sorted:

```python
arr = [4, 8, 12, 17, 25]

if len(arr) == 0:
    print("Array is empty")
else:
    maximum = arr[-1]
    print(maximum)
```

Output:

```text
25
```

### Generic manual traversal

If the array were not guaranteed sorted:

```python
arr = [4, 8, 12, 17, 25]

maximum = arr[0]

for i in range(1, len(arr)):
    if arr[i] > maximum:
        maximum = arr[i]

print(maximum)
```

---

# 9. Line-by-Line Explanation

```python
if len(arr) == 0:
```

Check whether array has elements.

---

```python
maximum = arr[-1]
```

Because the array is ascending, the final element is largest.

Python:

```text
arr[-1]
```

means:

```text
last element
```

---

```python
print(maximum)
```

Display result.

---

# 10. Detailed Dry Run

```text
arr = [4, 8, 12, 17, 25]
```

Because the array is already sorted:

```text
4 < 8 < 12 < 17 < 25
```

Therefore:

```text
arr[-1] = 25
```

| Position |            Value |
| -------: | ---------------: |
|        0 |                4 |
|        1 |                8 |
|        2 |               12 |
|        3 |               17 |
|        4 | **25 ← maximum** |

Answer:

```text
25
```

---

# 11. Complexity

Using sorted property:

```text
Time: O(1)
Space: O(1)
```

Generic traversal:

```text
Time: O(n)
Space: O(1)
```

---

# 12. Edge Cases

### Single element

```text
[10] → 10
```

### Empty

```text
[] → no maximum
```

### Negative numbers

```text
[-20, -10, -5, -1]
```

Maximum:

```text
-1
```

### Duplicate maximum

```text
[2, 5, 5, 5]
```

Maximum:

```text
5
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```python
arr[len(arr)]
```

Wrong.

Last valid index is:

```python
len(arr) - 1
```

Or simply:

```python
arr[-1]
```

---

### ❌ Mistake 2

Confusing ascending and descending arrays.

Ascending:

```text
[1, 3, 5, 7]
             ↑ MAX
```

Descending:

```text
[7, 5, 3, 1]
 ↑ MAX
```

---

### ❌ Mistake 3

Using binary search unnecessarily.

If the array is already guaranteed sorted:

```python
arr[-1]
```

is `O(1)`.

---

# 14. Pattern Recognition

> **Sorted ascending array + maximum**
>
> Think:
>
> 🔥 **Rightmost element**

```text
[MIN → ... → MAX]
                 ↑
               answer
```

---

# 🧠 SEARCHING — CONVERSATION 2 MASTER PATTERN MAP

We have now added four important patterns.

| Problem | Pattern                | Key Idea       |
| ------- | ---------------------- | -------------- |
| 5       | Binary Search          | Eliminate half |
| 6       | Search Insert Position | Lower Bound    |
| 7       | Find Minimum           | Left boundary  |
| 8       | Find Maximum           | Right boundary |

---

# 🔥 BINARY SEARCH MASTER TEMPLATE

This is the template you should memorize for TopGun.

```python
left = 0
right = len(arr) - 1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid

    elif arr[mid] < target:
        left = mid + 1

    else:
        right = mid - 1

return -1
```

### Mental picture

```text
          SORTED ARRAY
               ↓
        ┌──────┴──────┐
      LEFT           RIGHT
        └──────┬──────┘
              MID
               ↓
       ┌───────┴────────┐
     smaller           larger
       ↓                  ↓
     RIGHT              LEFT
```

---

# 🔥 LOWER-BOUND TEMPLATE

For:

> "Where should target be inserted?"

```python
left = 0
right = len(arr)

while left < right:

    mid = (left + right) // 2

    if arr[mid] < target:
        left = mid + 1
    else:
        right = mid

return left
```

### Critical difference

Normal binary search:

```text
left <= right
right = mid - 1
```

Lower bound:

```text
left < right
right = mid
```

This distinction is **very important**.

---

# 🧠 SEARCHING — CONVERSATION 1 → 2 CONNECTION

You should now see the progression:

```text
PROBLEM 1
Linear Search
O(n)
   ↓
PROBLEM 2
First Occurrence
O(n)
   ↓
PROBLEM 3
Last Occurrence
O(n)
   ↓
PROBLEM 4
Count Occurrences
O(n)
   ↓
PROBLEM 5
Binary Search
O(log n)
   ↓
PROBLEM 6
Lower Bound
O(log n)
```

Then:

```text
Sorted Array
     ↓
Know the boundaries
     ↓
Minimum → LEFT
Maximum → RIGHT
```

---

# 🎯 SENIOR PATTERN RECOGNITION

When you see:

### `"Search in an unsorted array"`

```text
→ Linear Search
→ O(n)
```

### `"Search in a sorted array"`

```text
→ Think Binary Search
→ O(log n)
```

### `"Find insertion position"`

```text
→ Lower Bound
→ first index where arr[i] >= target
```

### `"Minimum in ascending sorted array"`

```text
→ arr[0]
```

### `"Maximum in ascending sorted array"`

```text
→ arr[-1]
```

---

# 🧪 TOPGUN SCREENING CHECKPOINT

Before moving to Searching Conversation 3, you should be able to write these **without looking**:

### Linear Search

```python
for i in range(len(arr)):
    if arr[i] == target:
        return i
return -1
```

### Reverse Search

```python
for i in range(len(arr) - 1, -1, -1):
    if arr[i] == target:
        return i
return -1
```

### Count

```python
count = 0

for x in arr:
    if x == target:
        count += 1
```

### Binary Search

```python
left = 0
right = len(arr) - 1

while left <= right:
    mid = (left + right) // 2

    if arr[mid] == target:
        return mid
    elif arr[mid] < target:
        left = mid + 1
    else:
        right = mid - 1

return -1
```

### Lower Bound

```python
left = 0
right = len(arr)

while left < right:
    mid = (left + right) // 2

    if arr[mid] < target:
        left = mid + 1
    else:
        right = mid

return left
```

---

# 📊 SEARCHING PROGRESS

```text
SEARCHING

1. Linear Search                    ✅
2. First Occurrence                 ✅
3. Last Occurrence                  ✅
4. Count Occurrences                ✅
5. Binary Search                    ✅
6. Search Insert Position           ✅
7. Find Minimum in Sorted Array     ✅
8. Find Maximum in Sorted Array     ✅
9. Square Root using Binary Search ⏳
10. Search in Rotated Sorted Array ⏳
```

### Overall TopGun DSA Progress

```text
ARRAYS       10/10 ✅
STRINGS      10/10 ✅
HASHING      10/10 ✅
SEARCHING     8/10 🔵

TOTAL         38/40 problems ✅
```

**Next locked set:** 🔵 **Searching — Conversation 3 → Problems 9–10 + Searching Mastery + Pattern Recognition + Mini Test.**

Would you like to continue with Searching Conversation 3, or do a quick mini-test on Problems 5–8 first?

# 🔵 SEARCHING — CONVERSATION 3

## Problems 9–10

We are completing the **Searching 10/10 locked roadmap**.

| #  | Problem                         | Main Pattern            | Level           |
| -- | ------------------------------- | ----------------------- | --------------- |
| 9  | Square Root using Binary Search | Binary Search on Answer | 🟢 Basic–Medium |
| 10 | Search in Rotated Sorted Array  | Modified Binary Search  | 🟢 Medium       |

---

# 🔵 PROBLEM 9 — Square Root Using Binary Search

## 1. Problem Statement

Given a non-negative integer `x`, find its **integer square root**.

Return the largest integer `n` such that:

```text
n × n <= x
```

Do **not** use a built-in square-root function.

### Examples

```text
x = 16
Output = 4
```

Because:

```text
4 × 4 = 16
```

---

```text
x = 20
Output = 4
```

Because:

```text
4 × 4 = 16 <= 20

5 × 5 = 25 > 20
```

Therefore:

```text
sqrt(20) = 4
```

for integer square root.

---

# 2. Problem Theory

This problem teaches an extremely important variation of binary search:

> **Binary Search on the Answer**

We aren't searching for a value directly inside an array.

Instead, we are searching for the largest number whose square is less than or equal to `x`.

For:

```text
x = 20
```

possible answers are:

```text
0 1 2 3 4 5 6 ...
```

We need to find the boundary:

```text
4² <= 20 ✅
5² > 20 ❌
```

So:

```text
4 | 5
  ↑
answer boundary
```

---

# 3. Pattern Being Tested

### 🔥 Binary Search on Answer

The key condition is:

```python
mid * mid <= x
```

If true:

```text
mid could be the answer
```

So we try larger values.

If false:

```text
mid is too large
```

So we move left.

---

# 4. ELI10 Intuition

Imagine you're guessing a number whose square should not exceed `20`.

Try:

```text
3 × 3 = 9     ✅
```

Maybe bigger.

```text
5 × 5 = 25    ❌
```

Too big.

So the answer must be somewhere between:

```text
3 and 5
```

Try:

```text
4 × 4 = 16    ✅
```

So answer = `4`.

Binary search lets us find that boundary quickly.

---

# 5. Example

```text
x = 20
```

We can search:

```text
0 → 20
```

But we know the square root cannot be greater than `20`.

A tighter range is:

```text
0 → 10
```

because:

```text
10 × 10 = 100
```

is already greater than `20`.

---

# 6. Algorithm — Step-by-Step

1. If `x < 2`, return `x`.
2. Set:

   ```text
   left = 1
   right = x // 2
   ```
3. While `left <= right`:

   * Calculate `mid`.
   * Calculate `mid * mid`.
4. If:

   ```text
   mid * mid == x
   ```

   return `mid`.
5. If:

   ```text
   mid * mid < x
   ```

   `mid` is valid, but a larger answer may exist.

   * Save `mid`.
   * Move right.
6. Otherwise:

   * `mid` is too large.
   * Move left.
7. Return the largest valid answer.

---

# 7. Python Solution — Using Built-in Method

For comparison, Python can calculate square roots using `math.sqrt()`.

```python
import math

x = 20

answer = int(math.sqrt(x))

print(answer)
```

Output:

```text
4
```

### Important

For the actual screening question:

> **If they ask you to implement square root using binary search, don't use `math.sqrt()`.**

You need to understand the manual solution.

---

# 8. Python Solution — Without Built-in Square Root

```python
x = 20

if x < 2:
    print(x)
else:
    left = 1
    right = x // 2

    answer = 1

    while left <= right:

        mid = (left + right) // 2

        if mid * mid == x:
            answer = mid
            break

        elif mid * mid < x:
            answer = mid
            left = mid + 1

        else:
            right = mid - 1

    print(answer)
```

Output:

```text
4
```

---

# 9. Line-by-Line Explanation

```python
if x < 2:
    print(x)
```

For:

```text
0 → 0
1 → 1
```

we already know the answer.

---

```python
left = 1
```

Smallest positive possible answer.

---

```python
right = x // 2
```

For `x >= 2`, the square root cannot be greater than `x // 2`.

For example:

```text
x = 20
right = 10
```

---

```python
answer = 1
```

Stores the largest valid answer found so far.

---

```python
mid = (left + right) // 2
```

Choose the middle candidate.

---

```python
if mid * mid == x:
```

Perfect square.

Example:

```text
4 × 4 = 16
```

Return `4`.

---

```python
elif mid * mid < x:
```

The candidate is valid.

Example:

```text
4 × 4 = 16 < 20
```

But perhaps `5` also works.

So:

```python
answer = mid
left = mid + 1
```

Search for something larger.

---

```python
else:
    right = mid - 1
```

Candidate is too large.

Search smaller values.

---

# 10. Detailed Dry Run

### Input

```text
x = 20
```

Initial:

```text
left = 1
right = 10
answer = 1
```

### Step 1

```text
mid = (1 + 10) // 2
    = 5
```

Check:

```text
5 × 5 = 25
```

```text
25 > 20
```

Too large.

Therefore:

```text
right = 4
```

---

### Step 2

```text
left = 1
right = 4

mid = (1 + 4) // 2
    = 2
```

Check:

```text
2 × 2 = 4
```

```text
4 < 20
```

Valid.

```text
answer = 2
left = 3
```

---

### Step 3

```text
left = 3
right = 4

mid = (3 + 4) // 2
    = 3
```

Check:

```text
3 × 3 = 9
```

Valid.

```text
answer = 3
left = 4
```

---

### Step 4

```text
left = 4
right = 4

mid = 4
```

Check:

```text
4 × 4 = 16
```

Valid.

```text
answer = 4
left = 5
```

---

Now:

```text
left = 5
right = 4
```

Condition:

```python
left <= right
```

is false.

Stop.

Final:

```text
answer = 4
```

---

# 11. Dry Run Table

| Step | Left | Right | Mid | `mid²` | Decision      | Answer |
| ---: | ---: | ----: | --: | -----: | ------------- | -----: |
|    1 |    1 |    10 |   5 |     25 | Too large     |      1 |
|    2 |    1 |     4 |   2 |      4 | Valid → right |      2 |
|    3 |    3 |     4 |   3 |      9 | Valid → right |      3 |
|    4 |    4 |     4 |   4 |     16 | Valid → right |      4 |

Final:

```text
4
```

---

# 12. Complexity

### Time

```text
O(log x)
```

Because each step cuts the search range approximately in half.

### Space

```text
O(1)
```

Only a few variables are used.

---

# 13. Edge Cases

### `x = 0`

```text
0
```

### `x = 1`

```text
1
```

### Perfect square

```text
x = 25
```

Answer:

```text
5
```

### Non-perfect square

```text
x = 26
```

Because:

```text
5² = 25 <= 26
6² = 36 > 26
```

Answer:

```text
5
```

### Large number

The same binary-search logic works without traversing every possible number.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Returning `mid` whenever `mid² < x`

Example:

```text
x = 20
mid = 2
```

`2² < 20`, but `2` isn't the final answer.

You must continue searching right.

---

### ❌ Mistake 2 — Using floating-point square root

The question may explicitly require binary search.

```python
math.sqrt(x)
```

doesn't demonstrate the required algorithm.

---

### ❌ Mistake 3 — Forgetting non-perfect squares

The answer is:

```text
floor(sqrt(x))
```

not the nearest integer.

For:

```text
x = 20
```

answer is:

```text
4
```

not `5`.

---

# 15. Pattern Recognition

> **When you see:**
> "Find the maximum/minimum value satisfying a mathematical condition"
>
> Think:
>
> 🔥 **Binary Search on Answer**

Here:

```text
candidate² <= x
```

is the condition.

---

# 🔵 PROBLEM 10 — Search in Rotated Sorted Array

## 1. Problem Statement

You are given a sorted array that has been rotated.

Find the target's index.

If target doesn't exist, return `-1`.

Assume all values are **distinct**.

### Example

Original sorted array:

```text
[0, 1, 2, 4, 5, 6, 7]
```

After rotation:

```text
[4, 5, 6, 7, 0, 1, 2]
```

Target:

```text
0
```

Output:

```text
4
```

---

# 2. Problem Theory

This is a **modified binary search** problem.

The array is not completely sorted:

```text
[4, 5, 6, 7 | 0, 1, 2]
```

But here's the key:

> **At least one half of the array is always sorted.**

That's the trick.

At every iteration:

```text
left ---- mid ---- right
```

Either:

```text
left → mid
```

is sorted,

or:

```text
mid → right
```

is sorted.

We identify the sorted half and determine whether the target lies inside it.

---

# 3. Pattern Being Tested

### 🔥 Modified Binary Search

Core reasoning:

```text
Find MID
   ↓
Which half is sorted?
   ↓
Is target inside sorted half?
   ↓
YES → search there
NO  → search other half
```

---

# 4. ELI10 Intuition

Imagine numbers were originally arranged:

```text
1 2 3 4 5 6 7
```

Someone cuts the line and moves the first part to the end:

```text
4 5 6 7 | 1 2 3
```

The whole line isn't sorted anymore.

But:

```text
4 5 6 7
```

is sorted.

And:

```text
1 2 3
```

is also sorted.

So we can still use binary-search reasoning by figuring out which side is ordered.

---

# 5. Example

```text
arr = [4, 5, 6, 7, 0, 1, 2]
target = 0
```

Initial:

```text
left = 0
right = 6
mid = 3
```

```text
arr[mid] = 7
```

Left half:

```text
[4, 5, 6, 7]
```

is sorted because:

```text
arr[left] <= arr[mid]
```

Now ask:

> Is `0` between `4` and `7`?

No.

Therefore target must be on the other side.

Move:

```text
left = mid + 1
```

Now search:

```text
[0, 1, 2]
```

and find `0`.

---

# 6. Algorithm — Step-by-Step

1. Set:

   ```text
   left = 0
   right = n - 1
   ```
2. While `left <= right`:

   * Calculate `mid`.
3. If `arr[mid] == target`:

   * return `mid`.
4. Determine which half is sorted.
5. If left half is sorted:

   ```text
   arr[left] <= arr[mid]
   ```
6. Check whether target lies inside that sorted range:

   ```text
   arr[left] <= target < arr[mid]
   ```
7. If yes:

   * search left.
8. Otherwise:

   * search right.
9. If right half is sorted:

   * perform the equivalent check.
10. If target isn't found:

* return `-1`.

---

# 7. Python Solution — Using Built-in Methods

There is no standard Python list method that directly solves rotated-array search.

We can use a simple built-in membership check to locate the target, but that is **not binary search**:

```python
arr = [4, 5, 6, 7, 0, 1, 2]
target = 0

if target in arr:
    print(arr.index(target))
else:
    print(-1)
```

Output:

```text
4
```

### Important

This is:

```text
O(n)
```

not:

```text
O(log n)
```

So it is **not the interview solution**.

The purpose here is only to show the built-in equivalent.

---

# 8. Python Solution — Without Built-in Search

This is the solution you should master.

```python
arr = [4, 5, 6, 7, 0, 1, 2]
target = 0

left = 0
right = len(arr) - 1

result = -1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        result = mid
        break

    # Check if the LEFT half is sorted
    if arr[left] <= arr[mid]:

        # Check whether target lies in the sorted left half
        if arr[left] <= target < arr[mid]:
            right = mid - 1
        else:
            left = mid + 1

    # Otherwise, the RIGHT half is sorted
    else:

        # Check whether target lies in the sorted right half
        if arr[mid] < target <= arr[right]:
            left = mid + 1
        else:
            right = mid - 1

print(result)
```

Output:

```text
4
```

---

# 9. Line-by-Line Explanation

```python
left = 0
right = len(arr) - 1
```

Create the search range.

---

```python
while left <= right:
```

Continue while the search range exists.

---

```python
mid = (left + right) // 2
```

Find middle.

---

```python
if arr[mid] == target:
```

If we found target, we're done.

---

## The Most Important Part

```python
if arr[left] <= arr[mid]:
```

This tells us:

```text
LEFT → MID
```

is sorted.

Example:

```text
[4, 5, 6, 7, 0, 1, 2]
 ↑        ↑
left     mid
```

Here:

```text
4 <= 7
```

Therefore left half is sorted.

---

### Is target inside this sorted half?

```python
if arr[left] <= target < arr[mid]:
```

Suppose:

```text
left value = 4
mid value = 7
target = 6
```

Then:

```text
4 <= 6 < 7
```

Yes.

So search left:

```python
right = mid - 1
```

---

### Otherwise

Target isn't in sorted left half.

Therefore:

```python
left = mid + 1
```

Search right.

---

## Right Half

If:

```python
arr[left] > arr[mid]
```

then the left half isn't sorted, so the right half must be sorted.

We check:

```python
if arr[mid] < target <= arr[right]:
```

If target belongs there:

```python
left = mid + 1
```

Otherwise:

```python
right = mid - 1
```

---

# 10. Detailed Dry Run

### Input

```text
arr = [4, 5, 6, 7, 0, 1, 2]
target = 0
```

---

### Step 1

```text
left = 0
right = 6
mid = 3
```

Values:

```text
arr[left] = 4
arr[mid] = 7
arr[right] = 2
```

Target:

```text
0
```

Target not equal to `7`.

Check:

```text
4 <= 7
```

Therefore left half is sorted:

```text
[4, 5, 6, 7]
```

Is target between `4` and `7`?

```text
4 <= 0 < 7
```

False.

Therefore:

```text
left = mid + 1
     = 4
```

---

### Step 2

```text
left = 4
right = 6
mid = 5
```

Array section:

```text
[0, 1, 2]
```

```text
arr[mid] = 1
```

Target = `0`.

Not equal.

Check:

```text
arr[left] <= arr[mid]
0 <= 1
```

Left half is sorted:

```text
[0, 1]
```

Is target inside?

```text
0 <= 0 < 1
```

Yes.

Therefore:

```text
right = mid - 1
     = 4
```

---

### Step 3

```text
left = 4
right = 4
mid = 4
```

```text
arr[4] = 0
```

Target found.

Answer:

```text
4
```

---

# 11. Dry Run Table

| Step | Left | Right | Mid | `arr[mid]` | Sorted Half | Decision                |
| ---: | ---: | ----: | --: | ---------: | ----------- | ----------------------- |
|    1 |    0 |     6 |   3 |          7 | Left        | Target not left → right |
|    2 |    4 |     6 |   5 |          1 | Left        | Target in left → left   |
|    3 |    4 |     4 |   4 |          0 | —           | Found                   |

Final:

```text
4
```

---

# 12. Another Example

```text
arr = [6, 7, 8, 1, 2, 3, 4, 5]
target = 3
```

Initial:

```text
left = 0
right = 7
mid = 3
```

```text
arr[mid] = 1
```

Left side:

```text
[6,7,8,1]
```

is not sorted.

Therefore right side:

```text
[1,2,3,4,5]
```

is sorted.

Check:

```text
1 < 3 <= 5
```

True.

So:

```text
left = mid + 1
```

Continue searching right.

This is the exact reasoning pattern you need to recognize.

---

# 13. Complexity

### Time

```text
O(log n)
```

for distinct values.

Each iteration discards approximately half of the search space.

### Space

```text
O(1)
```

Only pointer variables are used.

---

# 14. Edge Cases

### Array not rotated

```text
[1, 2, 3, 4, 5]
```

The algorithm still works.

### Rotation by one position

```text
[5, 1, 2, 3, 4]
```

Still works.

### Target at first position

```text
[4, 5, 6, 7, 0, 1, 2]
target = 4
```

Answer:

```text
0
```

### Target at last position

```text
target = 2
```

Answer:

```text
6
```

### Target absent

```text
target = 10
```

Answer:

```text
-1
```

### Single element

```text
[5]
target = 5
```

Answer:

```text
0
```

---

# 15. Common Mistakes / Traps

## ❌ Mistake 1 — Treating the whole array as sorted

This is wrong:

```python
if arr[mid] < target:
    left = mid + 1
```

You cannot make this decision directly because the entire array isn't sorted.

First determine **which half is sorted**.

---

## ❌ Mistake 2 — Forgetting the sorted-half check

This is the heart of the problem:

```python
if arr[left] <= arr[mid]:
```

---

## ❌ Mistake 3 — Using incorrect boundaries

For left sorted half:

```text
arr[left] <= target < arr[mid]
```

For right sorted half:

```text
arr[mid] < target <= arr[right]
```

The inequalities matter.

---

## ❌ Mistake 4 — Thinking rotation destroys all order

It doesn't.

A rotated sorted array still has strong local order.

At least one half around `mid` is sorted when values are distinct.

---

# 16. Pattern Recognition

> **When you see:**
>
> "Sorted array was rotated"
>
> Think:
>
> 🔥 **Modified Binary Search**

Immediately ask:

```text
1. What is mid?
2. Which half is sorted?
3. Is target inside the sorted half?
4. If yes → search there.
5. If no → search other half.
```

---

# 🧠 SEARCHING — COMPLETE 10-PROBLEM PATTERN MAP

You have now completed all 10.

| #  | Problem                | Pattern                   |
| -- | ---------------------- | ------------------------- |
| 1  | Linear Search          | Linear Traversal          |
| 2  | First Occurrence       | Left → Right + Early Exit |
| 3  | Last Occurrence        | Right → Left              |
| 4  | Count Occurrences      | Traversal + Counter       |
| 5  | Binary Search          | Divide Search Space       |
| 6  | Search Insert Position | Lower Bound               |
| 7  | Find Minimum           | Left Boundary             |
| 8  | Find Maximum           | Right Boundary            |
| 9  | Square Root            | Binary Search on Answer   |
| 10 | Rotated Sorted Array   | Modified Binary Search    |

---

# 🔥 SEARCHING — MASTER PATTERN RECOGNITION

## Pattern 1 — Unsorted Search

```text
"Find target"
      ↓
Linear Search
      ↓
O(n)
```

---

## Pattern 2 — First Position

```text
"First occurrence"
      ↓
LEFT → RIGHT
      ↓
STOP at first match
```

---

## Pattern 3 — Last Position

```text
"Last occurrence"
      ↓
RIGHT → LEFT
      ↓
STOP at first match
```

---

## Pattern 4 — Count

```text
"How many?"
      ↓
Counter
      ↓
count += 1
```

---

## Pattern 5 — Sorted + Search

```text
Sorted array
     +
Search
     ↓
Binary Search
     ↓
O(log n)
```

---

## Pattern 6 — Insert Position

```text
"Where should target go?"
          ↓
Lower Bound
          ↓
first arr[i] >= target
```

---

## Pattern 7 — Search for Answer

```text
"Find largest/smallest value satisfying condition"
                ↓
Binary Search on Answer
```

Example:

```text
sqrt(x)
```

---

## Pattern 8 — Rotated Sorted Array

```text
Rotated sorted array
        ↓
Find sorted half
        ↓
Check target range
        ↓
Modified Binary Search
```

---

# 🧠 THE SEARCHING DECISION TREE

Memorize this:

```text
                    SEARCH PROBLEM
                          |
             ┌────────────┴────────────┐
             |                         |
         Unsorted                    Sorted
             |                         |
       Linear Search          ┌────────┴─────────┐
                              |                  |
                           Normal            Rotated
                              |                  |
                       Binary Search       Modified BS
                              |
                    ┌─────────┴─────────┐
                    |                   |
                Exact target       Position/boundary
                    |                   |
                 O(log n)          Lower Bound
```

And:

```text
Mathematical condition
        ↓
Binary Search on Answer
```

---

# 🏆 SEARCHING MASTER TEMPLATES

### 1. Linear Search

```python
for i in range(len(arr)):
    if arr[i] == target:
        return i

return -1
```

### 2. Last Occurrence

```python
for i in range(len(arr) - 1, -1, -1):
    if arr[i] == target:
        return i

return -1
```

### 3. Binary Search

```python
left = 0
right = len(arr) - 1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid

    elif arr[mid] < target:
        left = mid + 1

    else:
        right = mid - 1

return -1
```

### 4. Lower Bound

```python
left = 0
right = len(arr)

while left < right:

    mid = (left + right) // 2

    if arr[mid] < target:
        left = mid + 1
    else:
        right = mid

return left
```

### 5. Binary Search on Answer

```python
left = minimum_possible
right = maximum_possible
answer = initial_answer

while left <= right:

    mid = (left + right) // 2

    if condition(mid):
        answer = mid
        left = mid + 1
    else:
        right = mid - 1

return answer
```

### 6. Rotated Sorted Array

```python
left = 0
right = len(arr) - 1

while left <= right:

    mid = (left + right) // 2

    if arr[mid] == target:
        return mid

    if arr[left] <= arr[mid]:

        if arr[left] <= target < arr[mid]:
            right = mid - 1
        else:
            left = mid + 1

    else:

        if arr[mid] < target <= arr[right]:
            left = mid + 1
        else:
            right = mid - 1

return -1
```

---

# 🎯 SEARCHING — 10/10 COMPLETE

```text
ARRAYS       10/10 ✅
STRINGS      10/10 ✅
HASHING      10/10 ✅
SEARCHING    10/10 ✅
```

### Overall

```text
4 Topics
40 Problems
40/40 completed
```

The **Searching topic is now complete**. The critical transition you should retain for TopGun is:

```text
Unsorted → Linear Search → O(n)

Sorted → Binary Search → O(log n)

Sorted + insertion position → Lower Bound

Mathematical search space → Binary Search on Answer

Rotated Sorted → Modified Binary Search
```

**Next locked topic:** 🔵 **SORTING — Conversation 1 → Problems 1–4**

1. Bubble Sort
2. Selection Sort
3. Insertion Sort
4. Built-in Sort

Would you like to continue with Sorting — Conversation 1, or do a quick mini-test on Searching Problems 9–10 first?
