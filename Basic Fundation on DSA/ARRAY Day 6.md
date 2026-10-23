# 🔴 DAY 6

## ARRAY INTERVIEW BASICS

### Problems 51–60

```text
Merge Sorted Arrays
Array Intersection
Rotate by One
Rotate by K
Second Smallest
Maximum Subarray
Two Sum
Majority Element
Pivot Index
Sort 0/1/2
```

### 🎯 Skill

**High-value array patterns**

---


# 🔥 CR2 — DAY 6 — SESSION 1

# ARRAY INTERVIEW BASICS — PROBLEMS 51–53

Day 6 begins. We are now moving from **basic array fundamentals** into actual **placement/interview-style array manipulation**.

We keep the **locked CR2 execution depth** for every problem.

---

# 🎯 DAY 6 — SESSION 1

| #      | Problem                      | Exact LeetCode Match                                                                                          | Difficulty | Core Pattern |
| ------ | ---------------------------- | ------------------------------------------------------------------------------------------------------------- | ---------- | ------------ |
| **51** | Merge Two Sorted Arrays      | ⚠️ **LC 88 — Merge Sorted Array** is related/exact in core task, but LC88 uses the first array as destination | Easy       |              |
| **52** | Intersection of Two Arrays   | ✅ **LC 349 — Intersection of Two Arrays**                                                                     | Easy       |              |
| **53** | Rotate Array by One Position | ❌ No exact canonical LC match                                                                                 | Basic      |              |

### Today's progression

```text
51 → MERGE
52 → INTERSECTION
53 → ROTATION
```

The important goal is not just solving them.

You should learn to recognize:

```text
SORTED INPUT
      ↓
MERGING / TWO POINTERS

COMMON VALUES
      ↓
HASHING / MEMBERSHIP

ROTATE
      ↓
INDEX MAPPING / REVERSAL
```

---

# 🟢 PROBLEM 51 — MERGE TWO SORTED ARRAYS

## ⚠️ LEETCODE CONNECTION

**LC 88 — Merge Sorted Array — Easy**

LC 88 is closely aligned with this task, but the exact LC formulation gives the first array extra space and asks you to modify it in-place.

Our CR2 version is the general placement problem:

> Given two sorted arrays, create one sorted array containing all elements.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

## What is the real pattern?

Suppose:

```text id="l7x2jm"
A = [1, 4, 7]
B = [2, 3, 6]
```

Both arrays are already sorted.

We don't need to compare every element with every other element.

Instead, look only at the **smallest unprocessed element** from each array.

```text id="9m6jph"
A → 1
B → 2
```

Take `1`.

Then:

```text id="t0uv2n"
A → 4
B → 2
```

Take `2`.

Then:

```text id="0g1l9k"
A → 4
B → 3
```

Take `3`.

This is the classic:

# TWO POINTER MERGE

---

## The key insight

At any point:

```text
pointer A → smallest remaining element in A
pointer B → smallest remaining element in B
```

Therefore:

> The smaller of those two must be the next element in the final sorted array.

This is exactly the core idea behind merge sort.

---

## Why is this important?

This pattern appears in:

* merge sort
* merging sorted lists
* merging sorted streams
* interval processing
* external sorting
* database query processing

So although the problem is basic, the underlying idea is highly reusable.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two sorted arrays, merge them into one sorted array.

### Example

```text id="ex2q0c"
A = [1, 4, 7]
B = [2, 3, 6]
```

Output:

```text id="t8n0tg"
[1, 2, 3, 4, 6, 7]
```

---

## Why is the result sorted?

We repeatedly choose the smaller front element.

Initial:

```text id="8kqvpf"
A: [1, 4, 7]
     ↑

B: [2, 3, 6]
     ↑
```

`1 < 2`, so:

```text id="sn1zcy"
result = [1]
```

Then:

```text id="2aok4o"
A → 4
B → 2
```

Choose `2`.

And so on.

---

## Input assumptions

For the core problem:

```text id="f17mgs"
A is sorted
B is sorted
```

They may contain:

* duplicates
* negative numbers
* different lengths
* empty arrays

---

## Examples

```text id="j4x6p5"
A = [1, 3]
B = [2, 4]

→ [1, 2, 3, 4]
```

```text id="7w20g7"
A = []
B = [1, 2, 3]

→ [1, 2, 3]
```

```text id="9w3k7d"
A = [1, 1, 3]
B = [1, 2]

→ [1, 1, 1, 2, 3]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine two queues of people sorted by height.

Queue A:

```text id="h6v5y0"
1, 4, 7
```

Queue B:

```text id="0exx9d"
2, 3, 6
```

You always look at the person at the front of both queues.

```text id="8azbyr"
A front = 1
B front = 2
```

The shorter one goes first.

Take `1`.

Then:

```text id="f9k2hc"
A front = 4
B front = 2
```

Take `2`.

Then:

```text id="q40e0s"
A front = 4
B front = 3
```

Take `3`.

Continue.

---

## Visual

```text id="q0r5aj"
A: [1, 4, 7]
     ↑

B: [2, 3, 6]
     ↑

Compare 1 and 2
       ↓
      take 1
```

Then:

```text id="wqgtrf"
A: [1, 4, 7]
        ↑

B: [2, 3, 6]
     ↑

Compare 4 and 2
       ↓
      take 2
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

We need:

```text id="3vixh7"
i = pointer for A
j = pointer for B
```

### Step 1

Initialize:

```python id="v9s8da"
i = 0
j = 0
result = []
```

### Step 2

While both arrays still contain elements:

```python id="9u4z3j"
while i < len(a) and j < len(b):
```

### Step 3

Compare:

```python id="31z2f5"
a[i] <= b[j]
```

### Step 4

If `a[i]` is smaller:

```python id="ng7h3c"
result.append(a[i])
i += 1
```

Otherwise:

```python id="8yn5pr"
result.append(b[j])
j += 1
```

### Step 5

One array may finish first.

Append the remaining elements of the other array.

---

## Pseudocode

```text id="x5y1ei"
i = 0
j = 0

while i < len(A) AND j < len(B):

    if A[i] <= B[j]:
        add A[i]
        i++
    else:
        add B[j]
        j++

append remaining A
append remaining B
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="1tdgcm"
def merge_sorted_arrays(a, b):

    i = 0
    j = 0

    result = []

    # Compare elements while both arrays have elements
    while i < len(a) and j < len(b):

        if a[i] <= b[j]:
            result.append(a[i])
            i += 1

        else:
            result.append(b[j])
            j += 1

    # Add remaining elements from a
    while i < len(a):
        result.append(a[i])
        i += 1

    # Add remaining elements from b
    while j < len(b):
        result.append(b[j])
        j += 1

    return result


a = [1, 4, 7]
b = [2, 3, 6]

answer = merge_sorted_arrays(a, b)

print("Merged array:", answer)
```

### Output

```text id="ax5n1f"
Merged array: [1, 2, 3, 4, 6, 7]
```

---

## Why not concatenate and sort?

You could write:

```python id="k5q2fs"
sorted(a + b)
```

It works.

But it ignores the fact that:

```text id="f2u6v4"
A is already sorted
B is already sorted
```

The two-pointer merge uses that information.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="j13rcs"
import java.util.*;

public class Main {

    static int[] mergeSortedArrays(int[] a, int[] b) {

        int i = 0;
        int j = 0;
        int k = 0;

        int[] result = new int[a.length + b.length];

        // Compare elements while both arrays have elements
        while (i < a.length && j < b.length) {

            if (a[i] <= b[j]) {
                result[k] = a[i];
                i++;
            } else {
                result[k] = b[j];
                j++;
            }

            k++;
        }

        // Add remaining elements from a
        while (i < a.length) {
            result[k] = a[i];
            i++;
            k++;
        }

        // Add remaining elements from b
        while (j < b.length) {
            result[k] = b[j];
            j++;
            k++;
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 4, 7};
        int[] b = {2, 3, 6};

        int[] result = mergeSortedArrays(a, b);

        System.out.println(Arrays.toString(result));
    }
}
```

### Output

```text id="7jz9pm"
[1, 2, 3, 4, 6, 7]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="8p1l2n"
A = [1, 4, 7]
B = [2, 3, 6]
```

Initial:

```text id="6w7x0r"
i = 0
j = 0
result = []
```

---

### Step 1

Compare:

```text id="8qv2sy"
A[0] = 1
B[0] = 2
```

Since:

```text id="mbt6eq"
1 <= 2
```

take `1`.

```text id="9fy3hc"
result = [1]
i = 1
j = 0
```

---

### Step 2

Compare:

```text id="2wbrd9"
4 vs 2
```

Take `2`.

```text id="s1qk4g"
result = [1,2]
j = 1
```

---

### Step 3

Compare:

```text id="gksy0r"
4 vs 3
```

Take `3`.

```text id="wqjcb8"
result = [1,2,3]
j = 2
```

---

### Step 4

Compare:

```text id="g6ce01"
4 vs 6
```

Take `4`.

```text id="9ek1d0"
result = [1,2,3,4]
i = 2
```

---

### Step 5

Compare:

```text id="9gml70"
7 vs 6
```

Take `6`.

```text id="f1i7bq"
result = [1,2,3,4,6]
j = 3
```

B is finished.

Remaining A:

```text id="5ndt5n"
7
```

Append it.

Final:

```text id="h6z4z1"
[1,2,3,4,6,7]
```

---

## Complete trace

| Step | `A[i]` | `B[j]` |        Pick | Result          |
| ---: | -----: | -----: | ----------: | --------------- |
|    1 |      1 |      2 |           1 | `[1]`           |
|    2 |      4 |      2 |           2 | `[1,2]`         |
|    3 |      4 |      3 |           3 | `[1,2,3]`       |
|    4 |      4 |      6 |           4 | `[1,2,3,4]`     |
|    5 |      7 |      6 |           6 | `[1,2,3,4,6]`   |
|    6 |      — |      — | remaining 7 | `[1,2,3,4,6,7]` |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text id="xw9b2a"
i = 0
j = 0
k = 0
```

### Compare 1 and 2

Take `1`:

```text id="22m5o7"
result[0] = 1
i = 1
k = 1
```

### Compare 4 and 2

Take `2`:

```text id="5r4xzi"
result[1] = 2
j = 1
k = 2
```

### Compare 4 and 3

Take `3`.

### Compare 4 and 6

Take `4`.

### Compare 7 and 6

Take `6`.

Then B finishes.

Copy remaining:

```text id="e4f0fw"
7
```

Final:

```text id="spm6b7"
[1,2,3,4,6,7]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="v5ed3g"
m = length of A
n = length of B
```

Every element from both arrays is processed exactly once.

Total elements:

```text id="u6l7yq"
m + n
```

Therefore:

```text id="3m6d5s"
Time = O(m + n)
```

The output itself contains:

```text id="1h2cy9"
m + n
```

elements.

So the result requires:

```text id="9e4vkw"
O(m + n)
```

space.

### Important distinction

The **algorithmic auxiliary space**, excluding the required output array, is:

```text id="f2y4je"
O(1)
```

But because we must return a merged array:

```text id="2r1p9y"
Output Space = O(m+n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is this better than sorting?

Because sorting the combined array would cost approximately:

```text id="z7x4p9"
O((m+n) log(m+n))
```

The merge takes:

```text id="a1n8cz"
O(m+n)
```

---

### Q2. What if one array becomes empty?

Append the remaining elements from the other array.

Example:

```text id="2pfm81"
A = [1,2,3]
B = []
```

Answer:

```text id="50p6pp"
[1,2,3]
```

---

### Q3. Why use `<=` instead of `<`?

Using:

```python id="x8spq2"
a[i] <= b[j]
```

means equal elements can be taken from `A` first.

Either choice still produces a sorted result; `<=` also gives a consistent tie preference.

---

### Q4. What famous algorithm uses this exact merge idea?

# Merge Sort.

The merge step of merge sort combines two sorted halves using essentially this same two-pointer process.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# TWO POINTERS — MERGING SORTED DATA

Template:

```python id="w20kq0"
i = 0
j = 0

while i < len(a) and j < len(b):

    if a[i] <= b[j]:
        use(a[i])
        i += 1
    else:
        use(b[j])
        j += 1
```

Recognition trigger:

```text id="x8h9b0"
TWO SORTED ARRAYS
        ↓
    TWO POINTERS
        ↓
       MERGE
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Sorting the combined array unnecessarily.

### ❌ Mistake 2

Forgetting remaining elements.

### ❌ Mistake 3

Moving the wrong pointer.

If you take:

```text id="b5l6k2"
A[i]
```

then:

```text id="h5j88h"
i += 1
```

If you take:

```text id="jdfc57"
B[j]
```

then:

```text id="4c5o2s"
j += 1
```

### ❌ Mistake 4

Using nested loops.

The entire merge can be done in one combined scan.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Because both input arrays are sorted, compare their current smallest unprocessed elements and repeatedly append the smaller one. When one array finishes, append the remainder of the other.**

```text id="l6i5t4"
LC 88 connection
Time   → O(m+n)
Output → O(m+n)
Pattern → Two-Pointer Merge
```

---

# 🟢 PROBLEM 52 — INTERSECTION OF TWO ARRAYS

## ✅ EXACT LEETCODE MATCH: LC 349 — INTERSECTION OF TWO ARRAYS

**Difficulty:** Easy

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The word **intersection** means:

> Values that appear in **both** arrays.

Example:

```text id="4nyk2g"
A = [1, 2, 2, 3]
B = [2, 2, 4]
```

Unique intersection:

```text id="7mndom"
[2]
```

Notice:

```text id="3f4k2e"
2
```

appears multiple times, but LC 349 returns each common value only once.

---

## Two main approaches

### Approach 1 — Set

Convert one array to a set and test membership.

Average:

```text id="9w20o8"
O(m+n)
```

space:

```text id="j8gubc"
O(m)
```

### Approach 2 — Sort + Two Pointers

If arrays are sorted, use two pointers.

But the LC 349 input is not guaranteed sorted.

For CR2 and LC 349, hashing is the cleanest approach.

---

## Senior trigger

When you see:

```text id="b6s1xj"
common elements
intersection
appears in both
shared values
```

think:

```text id="i3cq0d"
SET / HASHING
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two arrays, return the unique values present in both.

Example:

```text id="2iqg9s"
A = [1, 2, 2, 1]
B = [2, 2]
```

Output:

```text id="2o0x2w"
[2]
```

---

## Another example

```text id="g7f2qv"
A = [4, 9, 5]
B = [9, 4, 9, 8, 4]
```

Intersection:

```text id="q3xg1c"
[4,9]
```

Order is not required by LC 349.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine two guest lists.

List A:

```text id="v0x3ka"
Alice
Bob
Charlie
```

List B:

```text id="w3ocgu"
Bob
David
```

Who appears on both lists?

```text id="m8k4tb"
Bob
```

A set lets us ask very quickly:

```text id="2nd2v9"
"Is this person present in list A?"
```

---

## Example

```text id="msv7kl"
A = [1, 2, 3, 4]
```

Convert to:

```text id="b8o5m3"
{1,2,3,4}
```

Then inspect B:

```text id="kw05q7"
[3,5,2]
```

`3` exists → include.

`5` doesn't → ignore.

`2` exists → include.

Result:

```text id="v8e8h8"
[3,2]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create a set containing all elements of the first array.

```python id="zq6f5v"
set_a = set(a)
```

### Step 2

Create an empty result set.

```python id="b25y72"
result = set()
```

### Step 3

Scan the second array.

### Step 4

If the element exists in `set_a`:

```python id="4gjxpr"
if num in set_a:
```

add it to the result set.

### Step 5

Convert the result set to a list.

---

## Why does this automatically remove duplicates?

A set stores only unique values.

If:

```text id="6ppb1s"
2
```

is added five times, the set still contains only:

```text id="l8z3jh"
{2}
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="z1r7fa"
def intersection(a, b):

    # Store unique elements from the first array
    set_a = set(a)

    # Result must also contain unique values
    result = set()

    # Check every element in the second array
    for num in b:

        if num in set_a:
            result.add(num)

    return list(result)


a = [1, 2, 2, 1]
b = [2, 2]

answer = intersection(a, b)

print("Intersection:", answer)
```

### Output

```text id="zq9xjg"
Intersection: [2]
```

Order may vary because sets are unordered.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="gn4qf9"
import java.util.*;

public class Main {

    static int[] intersection(int[] a, int[] b) {

        HashSet<Integer> setA = new HashSet<>();
        HashSet<Integer> resultSet = new HashSet<>();

        // Add all elements of first array
        for (int num : a) {
            setA.add(num);
        }

        // Check second array
        for (int num : b) {

            if (setA.contains(num)) {
                resultSet.add(num);
            }
        }

        // Convert result set to array
        int[] result = new int[resultSet.size()];

        int index = 0;

        for (int num : resultSet) {
            result[index++] = num;
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 2, 2, 1};
        int[] b = {2, 2};

        int[] answer = intersection(a, b);

        System.out.println(Arrays.toString(answer));
    }
}
```

### Output

```text id="qud7as"
[2]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="k0wq67"
A = [1, 2, 2, 1]
B = [2, 2]
```

Create:

```text id="cb5j1m"
set_a = {1,2}
```

Result:

```text id="w4s9z2"
{}
```

---

### First `2`

```text id="5y4tko"
2 in {1,2}? Yes
```

Add:

```text id="w1p2xn"
{2}
```

---

### Second `2`

Again:

```text id="5u4nbs"
2 exists
```

Adding it again changes nothing.

Final:

```text id="k8v4gy"
{2}
```

Convert:

```text id="0xyk36"
[2]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text id="y35b1r"
setA = {}
resultSet = {}
```

Process A:

```text id="1u0i1x"
1 → {1}
2 → {1,2}
2 → unchanged
1 → unchanged
```

Now process B:

```text id="2 → exists → resultSet={2}
2 → exists → resultSet remains {2}
```

Final:

```text id="4htr02"
[2]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="07m6p4"
m = length of A
n = length of B
```

Creating the set:

```text id="d0b6f3"
O(m)
```

Scanning B:

```text id="qv8b0s"
O(n)
```

Total average:

```text id="7e5m08"
O(m+n)
```

Space:

```text id="2t8sqf"
O(m)
```

for the first set plus the result.

Overall:

```text id="65t9xn"
Time  → O(m+n) average
Space → O(m)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does the result contain no duplicates?

Because the result is a set.

---

### Q2. What is the difference between LC 349 and LC 350?

LC 349:

```text id="jbh4m1"
unique intersection
```

LC 350:

```text id="v0h9v8"
intersection with multiplicity
```

Example:

```text id="0cegqu"
A = [1,2,2]
B = [2,2,2]
```

LC 349:

```text id="o9qfif"
[2]
```

LC 350:

```text id="x4o6n4"
[2,2]
```

This distinction is important.

---

### Q3. Can this be solved with two pointers?

Yes, if both arrays are sorted first.

But sorting introduces:

```text id="q3ytjp"
O(m log m + n log n)
```

cost.

Hashing gives average:

```text id="d2v8k1"
O(m+n)
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# SET INTERSECTION

Recognition:

```text id="f5l7jd"
COMMON
BOTH
INTERSECTION
SHARED
```

Think:

```text id="p3f2ap"
SET
```

General idea:

```python id="t0m1g7"
set_a = set(a)

for x in b:
    if x in set_a:
        ...
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Returning every matching duplicate.

LC 349 requires unique values.

---

### ❌ Mistake 2

Using nested loops unnecessarily:

```text id="m0rjib"
O(m*n)
```

---

### ❌ Mistake 3

Confusing intersection with union.

Intersection:

```text id="x8qf3g"
COMMON
```

Union:

```text id="y4h8m3"
EVERY UNIQUE VALUE
```

---

### ❌ Mistake 4

Assuming output order matters.

LC 349 does not require a particular order.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Store the unique values of one array in a hash set, scan the second array, and add values that exist in the first set to a result set.**

```text id="8d3x9n"
LC 349
Time  → O(m+n) average
Space → O(m)
Pattern → Hash Set / Intersection
```

---

# 🟢 PROBLEM 53 — ROTATE ARRAY BY ONE POSITION

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem is simple but teaches **index movement**.

There are two possible interpretations:

### Right rotation by one

```text id="1tyxgr"
[1,2,3,4,5]
```

becomes:

```text id="j9ofq1"
[5,1,2,3,4]
```

### Left rotation by one

```text id="0x1zha"
[1,2,3,4,5]
```

becomes:

```text id="h0jq4r"
[2,3,4,5,1]
```

For this CR2 syllabus, **"Rotate Array by One Position" means right rotation by one position.**

---

## Core idea

The last element moves to the beginning.

Everything else shifts right by one.

```text id="t2of4u"
[1,2,3,4,5]

last = 5

5 moves to front
1 → right
2 → right
3 → right
4 → right

[5,1,2,3,4]
```

---

## Senior observation

A direct implementation can be:

```text id="rj5wpp"
save last
shift right
put last at index 0
```

This teaches:

# INDEX SHIFTING

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text id="x2j3ny"
[10,20,30,40,50]
```

perform a right rotation by one position.

Output:

```text id="9rj13r"
[50,10,20,30,40]
```

---

## What moves?

Only one element crosses the boundary:

```text id="u6qps1"
50 → index 0
```

Every other element moves one index right.

---

## Edge cases

### Empty

```text id="gh43o9"
[]
```

stays:

```text id="7e0v2y"
[]
```

### One element

```text id="f20n99"
[5]
```

stays:

```text id="tx6k6n"
[5]
```

### Two elements

```text id="y0y4n6"
[1,2]
```

becomes:

```text id="i8h8uc"
[2,1]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine books on a shelf:

```text id="qcb2xk"
[Book1, Book2, Book3, Book4]
```

Right rotation means:

```text id="lpx4o8"
Book4
```

moves to the front.

The others shift right:

```text id="9j3t5m"
[Book4, Book1, Book2, Book3]
```

The important thing:

> Save the last element before shifting because otherwise you can overwrite it.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

If array length is `0` or `1`, return.

### Step 2

Save last element:

```python id="ujh0pf"
last = arr[-1]
```

### Step 3

Start from the second-last position.

### Step 4

Shift each element one position right:

```python id="qvtxb3"
arr[i] = arr[i - 1]
```

### Step 5

Put the saved last element at index `0`.

```python id="6b8j8o"
arr[0] = last
```

---

## Pseudocode

```text id="2g4u5a"
if n <= 1:
    return

last = arr[n-1]

for i from n-1 down to 1:
    arr[i] = arr[i-1]

arr[0] = last
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="ufh2hy"
def rotate_right_by_one(arr):

    # Nothing to rotate
    if len(arr) <= 1:
        return arr

    # Save the last element
    last = arr[-1]

    # Shift all elements one position to the right
    for i in range(len(arr) - 1, 0, -1):
        arr[i] = arr[i - 1]

    # Put the old last element at the beginning
    arr[0] = last

    return arr


arr = [10, 20, 30, 40, 50]

rotate_right_by_one(arr)

print(arr)
```

### Output

```text id="0vr1lj"
[50, 10, 20, 30, 40]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="i3m2iw"
import java.util.*;

public class Main {

    static void rotateRightByOne(int[] arr) {

        if (arr.length <= 1) {
            return;
        }

        // Save the last element
        int last = arr[arr.length - 1];

        // Shift elements from right to left
        for (int i = arr.length - 1; i >= 1; i--) {
            arr[i] = arr[i - 1];
        }

        // Place old last element at index 0
        arr[0] = last;
    }

    public static void main(String[] args) {

        int[] arr = {10, 20, 30, 40, 50};

        rotateRightByOne(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text id="wl9a4k"
[50, 10, 20, 30, 40]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="i7d2am"
[10,20,30,40,50]
```

First:

```text id="c8jq4k"
last = 50
```

Array:

```text id="1q9o4j"
[10,20,30,40,50]
```

---

### `i = 4`

```text id="f0u9hj"
arr[4] = arr[3]
```

So:

```text id="a1p5z7"
[10,20,30,40,40]
```

---

### `i = 3`

```text id="4q11o9"
arr[3] = arr[2]
```

Now:

```text id="xw47j4"
[10,20,30,30,40]
```

---

### `i = 2`

```text id="j5g0lb"
arr[2] = arr[1]
```

Now:

```text id="t4zj7n"
[10,20,20,30,40]
```

---

### `i = 1`

```text id="gq0f3u"
arr[1] = arr[0]
```

Now:

```text id="9n5o3a"
[10,10,20,30,40]
```

Finally:

```text id="l0qg8r"
arr[0] = last
```

So:

```text id="u3m1u0"
[50,10,20,30,40]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Initial:

```text id="wqg6m1"
{10,20,30,40,50}
```

Save:

```text id="b4k6p3"
last = 50
```

Then shift from right to left:

```text id="4p3fcr"
index 4 ← index 3
{10,20,30,40,40}

index 3 ← index 2
{10,20,30,30,40}

index 2 ← index 1
{10,20,20,30,40}

index 1 ← index 0
{10,10,20,30,40}
```

Finally:

```text id="e4j1bx"
index 0 = 50
```

Final:

```text id="t3t9ne"
{50,10,20,30,40}
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For an array of `n` elements:

We shift approximately:

```text id="z1p3ul"
n - 1
```

elements.

Therefore:

```text id="8gkzcm"
Time = O(n)
```

Only one extra variable:

```text id="jts7x0"
last
```

is required.

Therefore:

```text id="c3efbq"
Space = O(1)
```

### Final

```text id="4z8jcd"
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we shift from right to left?

Because if we shifted from left to right, we'd overwrite values before using them.

Correct:

```text id="r1t8ij"
right → left
```

---

### Q2. Why save the last element first?

Because the first shift:

```python id="b27l2y"
arr[n-1] = arr[n-2]
```

would otherwise destroy the original last element.

So:

```python id="m72z9g"
last = arr[-1]
```

must happen first.

---

### Q3. What is the difference between left and right rotation?

Right:

```text id="y9u5kp"
[1,2,3,4]
→ [4,1,2,3]
```

Left:

```text id="n5d8bg"
[1,2,3,4]
→ [2,3,4,1]
```

---

### Q4. Can Python slicing solve it?

Yes:

```python id="h0x2jq"
arr[:] = [arr[-1]] + arr[:-1]
```

But this creates additional lists.

For learning the in-place algorithm:

```text id="3k7i4w"
save → shift → place
```

is the important pattern.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# INDEX SHIFTING

Recognition triggers:

```text id="q9kj47"
rotate
shift
move elements by one position
insert at beginning
remove from beginning
```

Think:

```text id="l2z5uo"
SAVE IMPORTANT VALUE
        ↓
SHIFT CAREFULLY
        ↓
RESTORE SAVED VALUE
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Shift left-to-right:

```python id="o7j2b8"
for i in range(1, len(arr)):
    arr[i] = arr[i - 1]
```

This destroys values.

---

### ❌ Mistake 2

Not saving the last element.

---

### ❌ Mistake 3

Confusing left rotation with right rotation.

---

### ❌ Mistake 4

Forgetting empty/single-element arrays.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **For a right rotation by one, save the last element, shift every other element one position to the right starting from the end, then place the saved value at index zero.**

```text id="q9d2k6"
Time  → O(n)
Space → O(1)
Pattern → Index Shifting
```

---

# 🔥 DAY 6 — SESSION 1 — PATTERN CONNECTION

You have now learned three different array operations.

---

## 51 — MERGE

```text id="rj8xq5"
Two sorted arrays
       ↓
Two pointers
       ↓
Choose smaller
       ↓
Sorted result
```

Pattern:

# TWO-POINTER MERGE

---

## 52 — INTERSECTION

```text id="gq6d6w"
Two arrays
     ↓
What is common?
     ↓
Hash Set
     ↓
Unique intersection
```

Pattern:

# HASHING / SET

---

## 53 — ROTATE

```text id="l7gk0j"
Array
 ↓
Save boundary element
 ↓
Shift
 ↓
Restore
```

Pattern:

# INDEX SHIFTING

---

# 🧠 SESSION 1 PATTERN CHEAT SHEET

| Problem wording         | Immediate thought       |
| ----------------------- | ----------------------- |
| Merge two sorted arrays | Two-pointer merge       |
| Common elements         | Hash Set                |
| Intersection            | Set                     |
| Rotate right            | Save last + shift right |
| Rotate left             | Save first + shift left |

---

# 🧪 SESSION 1 — GUIDED PRACTICE

## Q1 — Merge

```text id="f8p7f4"
A = [1, 3, 5]
B = [2, 4, 6]
```

Expected:

```text id="2t6y83"
[1,2,3,4,5,6]
```

---

## Q2 — Merge With Duplicates

```text id="t6p9r1"
A = [1, 2, 2, 5]
B = [2, 3, 5]
```

Expected:

```text id="x8p2ya"
[1,2,2,2,3,5,5]
```

---

## Q3 — Intersection

```text id="2f6b3e"
A = [1,2,2,3,4]
B = [2,2,4,5]
```

Expected unique intersection:

```text id="g4q7x0"
[2,4]
```

---

## Q4 — Rotation

```text id="0h2a3r"
[1,2,3,4,5]
```

Right rotate once:

```text id="7x8g1b"
[5,1,2,3,4]
```

---

## Q5 — Edge Case

Merge:

```text id="8m2zqv"
A = []
B = [2,4,6]
```

Expected:

```text id="4qj2k5"
[2,4,6]
```

---

# 🔴 NO-SOLUTION MASTER TEST

Close the solution.

Code all three from scratch.

---

## TEST 1 — MERGE

```text id="0x2h1c"
A = [-5, 0, 3, 10]
B = [-4, 1, 2, 8, 12]
```

Expected:

```text id="h6j3ob"
[-5,-4,0,1,2,3,8,10,12]
```

---

## TEST 2 — INTERSECTION

```text id="k1t8sl"
A = [4, 9, 5, 9, 4]
B = [9, 4, 9, 8, 4]
```

Expected unique values:

```text id="6u6d1f"
[4,9]
```

Order does not matter.

---

## TEST 3 — ROTATE RIGHT

```text id="z6g1t4"
[10,20,30,40,50,60]
```

Expected:

```text id="x4p1g5"
[60,10,20,30,40,50]
```

---

# 🔥 VARIATION DRILL

## Variation 1 — Left Rotation

Take:

```text id="q7x7hz"
[1,2,3,4,5]
```

and perform one **left rotation**.

Expected:

```text id="n6j9yq"
[2,3,4,5,1]
```

Think:

```text id="g7p8yq"
save first
shift left
put first at end
```

---

## Variation 2 — Merge Without Extra Result?

Ask yourself:

> Can two sorted arrays be merged in-place?

Yes, depending on the memory layout and problem constraints.

This leads directly into:

```text id="0x6z9m"
LC 88 — Merge Sorted Array
```

where the destination array already contains enough extra space.

---

## Variation 3 — Intersection With Duplicates

If the question changes from:

> “unique intersection”

to:

> “intersection including duplicates”

you should immediately think:

```text id="f6m8c4"
LC 350
```

For example:

```text id="5m4d4s"
A = [1,2,2,3]
B = [2,2,4]
```

Unique intersection:

```text id="h8q7b9"
[2]
```

Intersection with multiplicity:

```text id="f9n6c3"
[2,2]
```

---

# 🧠 DAY 6 — SESSION 1 SENIOR RECOGNITION

Before coding, force yourself to say the pattern.

### “Two sorted arrays need to become one sorted array.”

```text id="e7m9x3"
→ TWO-POINTER MERGE
```

### “Find values present in both arrays.”

```text id="x6w2d1"
→ HASH SET / INTERSECTION
```

### “Move the last element to the beginning.”

```text id="p4k8y6"
→ SAVE + SHIFT
```

That **pattern-first thinking** is more valuable than memorizing code.

---

# 📊 DAY 6 PROGRESS

```text id="0v8g2q"
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅
DAY 3 → 10/10 ✅
DAY 4 → 10/10 ✅
DAY 5 → 10/10 ✅

DAY 6 — SESSION 1

51 → Merge Two Sorted Arrays       🟡
52 → Intersection of Two Arrays    🟡
53 → Rotate Array by One Position  🟡

TOTAL COVERED → 53 / 100
```

# 🎯 SESSION 1 MASTERY TARGET

Do not mark these 🔴 just because you understand the code.

You should be able to independently:

```text id="k4u1r9"
51 → merge without sorting
52 → find unique common values
53 → rotate without losing elements
```

and explain:

```text id="s9m4v7"
why the pattern works
why the complexity is optimal
what happens on edge cases
```

---

# 🔥 FINAL MEMORY CARD

```text id="f7s1x0"
51 — MERGE
Sorted + Sorted
      ↓
Two Pointers
      ↓
O(m+n)

52 — INTERSECTION
Common Values
      ↓
Hash Set
      ↓
O(m+n) average

53 — ROTATE RIGHT
Last → Front
Others → Shift Right
      ↓
Index Manipulation
      ↓
O(n)
```

## 🏆 DAY 6 SESSION 1 COMPLETE

**Next:** **Day 6 Session 2 → Problem 54: Rotate Array by K Positions + 55: Second Smallest Distinct Element + 56: Maximum Subarray Sum.**

Would you like to continue with Day 6 Session 2, or try the three master-test problems first?

# 🔥 CR2 — DAY 6 — SESSION 2

## Problems 54–56 | Array Interview Basics

**Session Goal:** Master three important array patterns:

| #  | Problem                          | LeetCode                     | Difficulty | Core Pattern       |
| -- | -------------------------------- | ---------------------------- | ---------- | ------------------ |
| 54 | Rotate Array by K Positions      | **LC 189 — Rotate Array**    | Medium     | Array Rotation     |
| 55 | Second Smallest Distinct Element | No exact canonical LC        | —          | Top-2 Tracking     |
| 56 | Maximum Subarray Sum             | **LC 53 — Maximum Subarray** | Medium     | Kadane's Algorithm |

**Current CR2 progress:** **56 / 100**
**Day 6 progress:** **6 / 10**

---

# 🟦 PROBLEM 54 — ROTATE ARRAY BY K POSITIONS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a very important placement/interview problem because it tests whether you understand **index movement** rather than simply knowing syntax.

### What are we doing?

Given:

```text
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3
```

Rotate the array **to the right** by 3 positions.

Result:

```text
[5, 6, 7, 1, 2, 3, 4]
```

### Senior observation #1

If:

```text
n = 7
k = 3
```

you don't actually need to perform 3 individual rotations.

There is a much cleaner **O(n)** solution.

### Senior observation #2

Always reduce:

```python
k = k % n
```

Why?

Suppose:

```text
n = 7
k = 10
```

Rotating 10 times is equivalent to rotating:

```text
10 % 7 = 3
```

times.

---

## 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Definition

**Right rotation by K positions** means the last `k` elements move to the front, while the remaining elements move to the right.

Example:

```text
Original:

[1, 2, 3, 4, 5, 6, 7]

k = 3

Last 3 elements:
[5, 6, 7]

Remaining:
[1, 2, 3, 4]

Result:

[5, 6, 7, 1, 2, 3, 4]
```

### Exact LeetCode match

✅ **LeetCode 189 — Rotate Array — Medium**

The original LeetCode problem asks for an **in-place** rotation.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

The best way to understand the optimal solution is with **three reversals**.

For:

```text
[1, 2, 3, 4, 5, 6, 7]
k = 3
```

### Step 1 — Reverse entire array

```text
[7, 6, 5, 4, 3, 2, 1]
```

### Step 2 — Reverse first k elements

First 3:

```text
[7, 6, 5]
```

Reverse them:

```text
[5, 6, 7]
```

Array becomes:

```text
[5, 6, 7, 4, 3, 2, 1]
```

### Step 3 — Reverse remaining elements

Remaining:

```text
[4, 3, 2, 1]
```

Reverse:

```text
[1, 2, 3, 4]
```

Final:

```text
[5, 6, 7, 1, 2, 3, 4]
```

🎯 Done.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given:

```text
nums
k
```

### Step 1

Find array length:

```python
n = len(nums)
```

### Step 2

Handle empty array:

```python
if n == 0:
    return
```

### Step 3

Reduce unnecessary rotations:

```python
k = k % n
```

### Step 4

Reverse the entire array.

### Step 5

Reverse indices:

```text
0 → k-1
```

### Step 6

Reverse indices:

```text
k → n-1
```

### Final result

The last `k` elements appear at the beginning.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def rotate(nums, k):
    n = len(nums)

    if n == 0:
        return

    k = k % n

    def reverse(left, right):
        while left < right:
            nums[left], nums[right] = nums[right], nums[left]
            left += 1
            right -= 1

    # Step 1: Reverse entire array
    reverse(0, n - 1)

    # Step 2: Reverse first k elements
    reverse(0, k - 1)

    # Step 3: Reverse remaining elements
    reverse(k, n - 1)


# Example
nums = [1, 2, 3, 4, 5, 6, 7]
k = 3

rotate(nums, k)

print(nums)
```

### Output

```text
[5, 6, 7, 1, 2, 3, 4]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static void rotate(int[] nums, int k) {

        int n = nums.length;

        if (n == 0) {
            return;
        }

        k = k % n;

        // Step 1: Reverse entire array
        reverse(nums, 0, n - 1);

        // Step 2: Reverse first k elements
        reverse(nums, 0, k - 1);

        // Step 3: Reverse remaining elements
        reverse(nums, k, n - 1);
    }

    public static void reverse(int[] nums, int left, int right) {

        while (left < right) {

            int temp = nums[left];
            nums[left] = nums[right];
            nums[right] = temp;

            left++;
            right--;
        }
    }

    public static void main(String[] args) {

        int[] nums = {1, 2, 3, 4, 5, 6, 7};

        int k = 3;

        rotate(nums, k);

        System.out.println(Arrays.toString(nums));
    }
}
```

### Output

```text
[5, 6, 7, 1, 2, 3, 4]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [1,2,3,4,5,6,7]
k = 3
```

## Phase 1

```text
Reverse entire array
```

Before:

```text
[1,2,3,4,5,6,7]
```

After:

```text
[7,6,5,4,3,2,1]
```

---

## Phase 2

Reverse first `k = 3`:

```text
[7,6,5]
```

After reversal:

```text
[5,6,7]
```

Array:

```text
[5,6,7,4,3,2,1]
```

---

## Phase 3

Reverse:

```text
[4,3,2,1]
```

After:

```text
[1,2,3,4]
```

Final:

```text
[5,6,7,1,2,3,4]
```

### Why does it work?

Because the first reversal puts the elements in reverse order.

Then the two smaller reversals restore the internal order of the two groups.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

The Java algorithm is identical.

For:

```text
[1,2,3,4,5,6,7]
```

### Reverse whole array

```text
[7,6,5,4,3,2,1]
```

### Reverse `[0...2]`

```text
[5,6,7,4,3,2,1]
```

### Reverse `[3...6]`

```text
[5,6,7,1,2,3,4]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We perform three reversals.

For an array of size `n`:

### First reversal

Approximately:

```text
n/2
```

swaps.

### Second reversal

Approximately:

```text
k/2
```

swaps.

### Third reversal

Approximately:

```text
(n-k)/2
```

swaps.

Total:

```text
n/2 + k/2 + (n-k)/2
```

Simplifies to:

```text
n
```

Therefore:

### Time

```text
O(n)
```

### Auxiliary Space

```text
O(1)
```

because we only use a few variables.

🔥 This is the important part of LC189.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we use `k % n`?

Because rotating an array `n` times returns it to the original arrangement.

```text
k = 10
n = 7

10 % 7 = 3
```

So 10 rotations = 3 effective rotations.

---

### Q2. Why use three reversals?

Three reversals allow us to rearrange the array **in-place** without creating another array.

---

### Q3. What happens when `k > n`?

Use:

```python
k %= n
```

---

### Q4. What is the space complexity?

```text
O(1)
```

auxiliary space.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Pattern:

## 🔥 ARRAY ROTATION

Whenever you see:

> Rotate array by K

Immediately think:

```text
k = k % n

Reverse whole array
Reverse first k
Reverse remaining
```

### Master template

```python
k %= n

reverse(0, n-1)
reverse(0, k-1)
reverse(k, n-1)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Forgetting:

```python
k %= n
```

### ❌ Mistake 2

Doing:

```python
for _ in range(k):
    # shift entire array
```

This can become:

```text
O(nk)
```

which is unnecessary.

### ❌ Mistake 3

Confusing left rotation and right rotation.

For:

```text
[1,2,3,4,5]
```

right rotation by 2:

```text
[4,5,1,2,3]
```

left rotation by 2:

```text
[3,4,5,1,2]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember:

> **Right rotate by K → reduce K → reverse all → reverse first K → reverse rest.**

```text
LC 189
Medium
O(n) time
O(1) extra space
```

---

# 🟦 PROBLEM 55 — SECOND SMALLEST DISTINCT ELEMENT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This looks extremely easy.

But there is an important word:

# **DISTINCT**

Example:

```text
[5, 2, 8, 2, 1]
```

Sorted:

```text
[1,2,2,5,8]
```

The second smallest **distinct** element is:

```text
2
```

Not another copy of `1`.

---

## 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer array, find the **second smallest distinct element**.

Example:

```text
[7, 3, 9, 1, 5]
```

Smallest:

```text
1
```

Second smallest:

```text
3
```

### Another example

```text
[4, 1, 1, 2, 3]
```

Distinct values:

```text
1,2,3,4
```

Answer:

```text
2
```

### Exact LeetCode match

❌ **No exact canonical LeetCode problem matching this exact basic task.**

It is a standard placement/interview array problem.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We don't need to sort.

Maintain two variables:

```text
smallest
second_smallest
```

Suppose:

```text
[8, 3, 5, 1, 6]
```

Start:

```text
smallest = infinity
second = infinity
```

Process `8`:

```text
smallest = 8
```

Process `3`:

```text
second = 8
smallest = 3
```

Process `5`:

```text
smallest = 3
second = 5
```

Process `1`:

```text
second = 3
smallest = 1
```

Process `6`:

No change.

Answer:

```text
3
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

For every number:

### Case 1

If:

```text
number < smallest
```

then:

```text
second = smallest
smallest = number
```

### Case 2

Otherwise, if:

```text
smallest < number < second
```

then:

```text
second = number
```

### Case 3

If:

```text
number == smallest
```

ignore it.

This is what guarantees **distinctness**.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def second_smallest(arr):

    smallest = float('inf')
    second = float('inf')

    for num in arr:

        # Found a new smallest
        if num < smallest:
            second = smallest
            smallest = num

        # Found a new second smallest
        elif smallest < num < second:
            second = num

    # No second distinct element exists
    if second == float('inf'):
        return None

    return second


arr = [7, 3, 9, 1, 5]

answer = second_smallest(arr)

print("Second smallest:", answer)
```

### Output

```text
Second smallest: 3
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static Integer secondSmallest(int[] arr) {

        int smallest = Integer.MAX_VALUE;
        int second = Integer.MAX_VALUE;

        for (int num : arr) {

            // Found a new smallest
            if (num < smallest) {

                second = smallest;
                smallest = num;
            }

            // Found a new second smallest
            else if (num > smallest && num < second) {

                second = num;
            }
        }

        // No second distinct element
        if (second == Integer.MAX_VALUE) {
            return null;
        }

        return second;
    }

    public static void main(String[] args) {

        int[] arr = {7, 3, 9, 1, 5};

        Integer answer = secondSmallest(arr);

        System.out.println("Second smallest: " + answer);
    }
}
```

### Output

```text
Second smallest: 3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
arr = [7,3,9,1,5]
```

Initial:

```text
smallest = ∞
second = ∞
```

| num | smallest | second |
| --: | -------: | -----: |
|   7 |        7 |      ∞ |
|   3 |        3 |      7 |
|   9 |        3 |      7 |
|   1 |        1 |      3 |
|   5 |        1 |      3 |

Final:

```text
smallest = 1
second = 3
```

Answer:

```text
3
```

---

## Duplicate test

Input:

```text
[4,1,1,2,3]
```

Processing:

```text
4 → smallest=4
1 → smallest=1, second=4
1 → ignored
2 → second=2
3 → ignored
```

Answer:

```text
2
```

🎯 This is why the condition:

```python
smallest < num
```

matters.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
[4,1,1,2,3]
```

### Start

```text
smallest = MAX_VALUE
second = MAX_VALUE
```

### 4

```text
smallest = 4
```

### 1

```text
second = 4
smallest = 1
```

### 1

Duplicate of smallest.

Ignore.

### 2

```text
second = 2
```

### 3

No improvement.

Final:

```text
1, 2
```

Answer:

```text
2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We scan the array exactly once.

For `n` elements:

```text
n comparisons
```

approximately.

Therefore:

### Time

```text
O(n)
```

### Space

Only:

```text
smallest
second
```

are stored.

Therefore:

```text
O(1)
```

### Why not sorting?

Sorting costs:

```text
O(n log n)
```

Our one-pass solution is:

```text
O(n)
```

So sorting is unnecessary.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why not sort the array?

Because sorting is unnecessary.

We can find the answer in one pass:

```text
O(n)
```

instead of:

```text
O(n log n)
```

---

### Q2. What does distinct mean?

Duplicates don't count as separate values.

```text
[1,1,2]
```

Second smallest distinct:

```text
2
```

---

### Q3. What if all values are identical?

Example:

```text
[5,5,5]
```

There is no second distinct value.

Return:

```text
None
```

or handle according to the problem's required output.

---

### Q4. Can the array contain negative numbers?

Yes.

Example:

```text
[-5,-10,-2,-10]
```

Distinct sorted values:

```text
[-10,-5,-2]
```

Answer:

```text
-5
```

Our algorithm handles this correctly.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This belongs to:

# 🔥 TOP-2 TRACKING

You can use the same idea for:

```text
Largest
Second Largest
Smallest
Second Smallest
```

### Mental template

```text
best
second_best
```

Scan once.

Whenever a new best appears:

```text
second_best = best
best = current
```

This pattern is extremely useful in placement coding.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Doing:

```python
sorted(arr)[1]
```

This fails for duplicates.

```text
[1,1,2]
```

would give:

```text
1
```

instead of:

```text
2
```

---

### ❌ Mistake 2

Not handling:

```text
[5,5,5]
```

---

### ❌ Mistake 3

Using:

```python
num < second
```

without checking:

```python
num > smallest
```

This can incorrectly treat the smallest value as the second smallest.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember:

> **Second smallest distinct → maintain smallest + second smallest in one scan.**

```text
Time  = O(n)
Space = O(1)
```

No sorting required.

---

# 🟦 PROBLEM 56 — MAXIMUM SUBARRAY SUM

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is one of the **most important problems in the entire CR2 syllabus.**

It is:

✅ **LeetCode 53 — Maximum Subarray**
✅ **Medium**

And it introduces one of the most famous algorithms:

# 🔥 KADANE'S ALGORITHM

You should absolutely know this pattern.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an integer array, find the **contiguous subarray** with the largest sum.

Example:

```text
nums = [-2,1,-3,4,-1,2,1,-5,4]
```

The best subarray is:

```text
[4,-1,2,1]
```

Sum:

```text
4 + (-1) + 2 + 1 = 6
```

Answer:

```text
6
```

### Important word

# CONTIGUOUS

The selected elements must be next to each other.

You cannot do:

```text
[4,2,1]
```

if they are separated.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

The key question at every element is:

> Should I continue my current subarray, or start a new subarray here?

Suppose:

```text
[-2,1,-3,4,-1,2,1,-5,4]
```

At every position, calculate:

```text
current_sum
```

We use:

```text
current_sum = max(num, current_sum + num)
```

Meaning:

### Option A

Start fresh:

```text
num
```

### Option B

Continue previous subarray:

```text
current_sum + num
```

Take whichever is larger.

---

# 🔥 THE KADANE IDEA

If your previous running sum is hurting the current number, **throw it away**.

Example:

```text
current_sum = -5
num = 4
```

Compare:

```text
4
```

versus:

```text
-5 + 4 = -1
```

Clearly:

```text
4 > -1
```

So start a new subarray.

This is the core intuition.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given:

```text
nums
```

### Step 1

Initialize:

```python
current_sum = nums[0]
max_sum = nums[0]
```

### Step 2

Start from index 1.

### Step 3

For each number:

```python
current_sum = max(num, current_sum + num)
```

### Step 4

Update global maximum:

```python
max_sum = max(max_sum, current_sum)
```

### Step 5

Return:

```python
max_sum
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def max_subarray_sum(nums):

    current_sum = nums[0]
    max_sum = nums[0]

    for i in range(1, len(nums)):

        # Decide:
        # Start a new subarray OR extend previous subarray
        current_sum = max(nums[i], current_sum + nums[i])

        # Update the best answer seen so far
        max_sum = max(max_sum, current_sum)

    return max_sum


nums = [-2, 1, -3, 4, -1, 2, 1, -5, 4]

answer = max_subarray_sum(nums)

print("Maximum subarray sum:", answer)
```

### Output

```text
Maximum subarray sum: 6
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int maxSubarraySum(int[] nums) {

        int currentSum = nums[0];
        int maxSum = nums[0];

        for (int i = 1; i < nums.length; i++) {

            // Start new OR extend previous
            currentSum = Math.max(
                nums[i],
                currentSum + nums[i]
            );

            // Update global maximum
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {

        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};

        int answer = maxSubarraySum(nums);

        System.out.println("Maximum subarray sum: " + answer);
    }
}
```

### Output

```text
Maximum subarray sum: 6
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[-2,1,-3,4,-1,2,1,-5,4]
```

Initial:

```text
current = -2
maximum = -2
```

Now process each element.

| num | current calculation | current | maximum |
| --: | ------------------- | ------: | ------: |
|  -2 | initial             |      -2 |      -2 |
|   1 | max(1, -2+1)        |       1 |       1 |
|  -3 | max(-3, 1-3)        |      -2 |       1 |
|   4 | max(4, -2+4)        |       4 |       4 |
|  -1 | max(-1, 4-1)        |       3 |       4 |
|   2 | max(2, 3+2)         |       5 |       5 |
|   1 | max(1, 5+1)         |       6 |       6 |
|  -5 | max(-5, 6-5)        |       1 |       6 |
|   4 | max(4, 1+4)         |       5 |       6 |

Final:

```text
maximum = 6
```

---

## 🔥 See the important section

At:

```text
4
```

we had:

```text
current = -2
```

Instead of:

```text
-2 + 4 = 2
```

we choose:

```text
4
```

because:

```text
4 > 2
```

We throw away the negative prefix.

Then:

```text
4
4 + (-1) = 3
3 + 2 = 5
5 + 1 = 6
```

So:

```text
[4,-1,2,1]
```

produces:

```text
6
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

The Java execution follows exactly the same recurrence.

For the important portion:

```text
4 → current = 4
-1 → current = 3
2 → current = 5
1 → current = 6
```

Global maximum becomes:

```text
6
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We visit every element exactly once.

For `n` elements:

```text
n - 1
```

iterations.

Each iteration performs constant work:

```text
max()
addition
comparison
assignment
```

Therefore:

### Time

```text
O(n)
```

### Space

Only:

```text
current_sum
max_sum
```

are stored.

Therefore:

```text
O(1)
```

---

# 🔥 WHY NOT BRUTE FORCE?

A brute-force solution can examine every possible subarray.

There are:

```text
n(n+1)/2
```

possible contiguous subarrays.

That is:

```text
O(n²)
```

candidate ranges.

If you calculate their sums independently, it can become:

```text
O(n³)
```

With prefix sums, brute-force range checking can be improved to:

```text
O(n²)
```

But Kadane gives:

```text
O(n)
```

with:

```text
O(1)
```

space.

That's why Kadane is the interview solution.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is Kadane's Algorithm?

Kadane's algorithm finds the maximum sum of a contiguous subarray in:

```text
O(n)
```

time and:

```text
O(1)
```

space.

---

### Q2. Why do we use:

```python
max(num, current_sum + num)
```

Because we have exactly two choices:

```text
1. Start a new subarray at num
2. Extend the existing subarray
```

---

### Q3. What if every number is negative?

Example:

```text
[-8,-3,-5,-2]
```

Correct answer:

```text
-2
```

Our initialization:

```python
current_sum = nums[0]
max_sum = nums[0]
```

handles this correctly.

⚠️ Don't initialize `max_sum = 0`.

Otherwise, an all-negative array incorrectly returns `0`.

---

### Q4. Does this work for a single element?

Yes.

```text
[7]
```

Answer:

```text
7
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is the pattern:

# 🔥 KADANE'S ALGORITHM

Whenever you see:

> Maximum sum contiguous subarray

Immediately think:

```python
current = max(num, current + num)
best = max(best, current)
```

### Mental question

At every element:

> **Should I extend or restart?**

That one question is Kadane's Algorithm.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — confusing subsequence with subarray

Subarray must be contiguous.

```text
[4,-1,2,1]
```

is valid.

Choosing:

```text
[4,2,1]
```

is not valid if the `-1` is skipped.

---

### ❌ Mistake 2

Initializing:

```python
max_sum = 0
```

Wrong for:

```text
[-5,-2,-8]
```

Correct answer:

```text
-2
```

---

### ❌ Mistake 3

Only calculating:

```python
current_sum += num
```

You must decide whether to restart.

---

### ❌ Mistake 4

Using nested loops immediately.

Kadane should be your first thought when the problem is the standard maximum contiguous subarray sum.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember this forever:

> **Kadane = Extend or Restart.**

```python
current = max(num, current + num)
best = max(best, current)
```

### Complexity

```text
Time  → O(n)
Space → O(1)
```

### Exact LeetCode

🔥 **LC 53 — Maximum Subarray — Medium**

---

# 🏆 DAY 6 — SESSION 2 MASTER CONNECTION

You just learned **three completely different array patterns**:

| Problem                    | Pattern        | Core Thought                |
| -------------------------- | -------------- | --------------------------- |
| **54 — Rotate Array by K** | Array Reversal | Reverse → Reverse → Reverse |
| **55 — Second Smallest**   | Top-2 Tracking | Maintain smallest + second  |
| **56 — Maximum Subarray**  | Kadane         | Extend or Restart           |

## 🧠 Three patterns to memorize

### 1️⃣ Rotation

```text
k %= n
reverse all
reverse first k
reverse rest
```

### 2️⃣ Second Smallest

```text
smallest
second_smallest
```

One scan.

### 3️⃣ Maximum Subarray

```text
current = max(num, current + num)
best = max(best, current)
```

---

# 🔥 SESSION 2 PRACTICE DRILL

Before moving to Session 3, reproduce these **without looking at the solutions**:

### Problem 54

```text
nums = [1,2,3,4,5]
k = 2

Expected:
[4,5,1,2,3]
```

### Problem 55

```text
nums = [8,3,3,5,1,1,9]

Expected:
3
```

### Problem 56

```text
nums = [-3,4,-1,2,-6,5,2]

Expected:
5
```

---

# 🧪 NO-SOLUTION MASTER TEST

Write all three from memory:

### Test 1

```text
Rotate [10,20,30,40,50,60] right by 4
```

### Test 2

```text
Find second smallest distinct:

[12, 5, 7, 5, 3, 9, 3, 8]
```

### Test 3

```text
Maximum subarray sum:

[-5, -2, -8, -1]
```

### Expected answers

```text
Test 1 → [30,40,50,60,10,20]

Test 2 → 5

Test 3 → -1
```

---

# 📊 CR2 PROGRESS

```text
DAY 1  ██████████  10/10
DAY 2  ██████████  10/10
DAY 3  ██████████  10/10
DAY 4  ██████████  10/10
DAY 5  ██████████  10/10
DAY 6  ██████░░░░  6/10
```

## Overall

# 🟢 56 / 100 COMPLETED

**Next locked sequence:**
**Day 6 — Session 3 → Problems 57, 58, 59, 60**

* Two Sum
* Majority Element
* Equilibrium / Pivot Index
* Sort 0s, 1s & 2s


# 🔥 CR2 — DAY 6 — SESSION 3

## Problems 57–60 | Array Interview Basics

This is the **final session of Day 6**.

| #  | Problem                   | LeetCode                      | Difficulty | Core Pattern        |
| -- | ------------------------- | ----------------------------- | ---------- | ------------------- |
| 57 | Two Sum                   | **LC 1 — Two Sum**            | Easy       | Hash Map            |
| 58 | Majority Element          | **LC 169 — Majority Element** | Easy       | Boyer-Moore Voting  |
| 59 | Equilibrium / Pivot Index | **LC 724 — Find Pivot Index** | Easy       | Prefix Sum          |
| 60 | Sort 0s, 1s & 2s          | **LC 75 — Sort Colors**       | Medium     | Dutch National Flag |

🎯 **After this session: 60/100 CR2 problems complete.**

---

# 🟦 PROBLEM 57 — TWO SUM

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

**Two Sum is one of the most important beginner interview problems.**

It teaches a pattern that appears everywhere:

> **Have I already seen the value I need?**

Given:

```text
nums = [2, 7, 11, 15]
target = 9
```

We need two different elements whose sum is `9`.

```text
2 + 7 = 9
```

Answer:

```text
[0, 1]
```

### Exact LeetCode

✅ **LC 1 — Two Sum — Easy**

---

## 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

We are given:

```text
nums
target
```

Find indices:

```text
i, j
```

such that:

```text
nums[i] + nums[j] = target
```

### Example

```text
nums = [3, 2, 4]
target = 6
```

Answer:

```text
[1, 2]
```

because:

```text
nums[1] + nums[2]
= 2 + 4
= 6
```

### Important

We return **indices**, not the values.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Suppose:

```text
nums = [2,7,11,15]
target = 9
```

At `2`:

```text
needed = 9 - 2
       = 7
```

Question:

> Have I already seen `7`?

No.

Store:

```text
2 → index 0
```

Next number:

```text
7
```

Needed:

```text
9 - 7 = 2
```

Have we seen `2`?

✅ Yes.

It was at index `0`.

Therefore:

```text
[0,1]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Create a dictionary:

```python
seen = {}
```

For every index `i`:

### Step 1

Get current number:

```python
num = nums[i]
```

### Step 2

Calculate required number:

```python
needed = target - num
```

### Step 3

Check whether `needed` exists in `seen`.

If yes:

```python
return [seen[needed], i]
```

### Step 4

Otherwise store current number:

```python
seen[num] = i
```

Continue.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def two_sum(nums, target):

    seen = {}

    for i in range(len(nums)):

        num = nums[i]

        # Number required to reach target
        needed = target - num

        # If we have already seen it
        if needed in seen:
            return [seen[needed], i]

        # Store current number and its index
        seen[num] = i

    return []


nums = [2, 7, 11, 15]
target = 9

answer = two_sum(nums, target)

print(answer)
```

### Output

```text
[0, 1]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int[] twoSum(int[] nums, int target) {

        HashMap<Integer, Integer> seen = new HashMap<>();

        for (int i = 0; i < nums.length; i++) {

            int num = nums[i];

            int needed = target - num;

            if (seen.containsKey(needed)) {

                return new int[] {
                    seen.get(needed),
                    i
                };
            }

            seen.put(num, i);
        }

        return new int[0];
    }

    public static void main(String[] args) {

        int[] nums = {2, 7, 11, 15};
        int target = 9;

        int[] answer = twoSum(nums, target);

        System.out.println(Arrays.toString(answer));
    }
}
```

### Output

```text
[0, 1]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [2, 7, 11, 15]
target = 9
```

Initially:

```text
seen = {}
```

### i = 0

```text
num = 2
needed = 9 - 2 = 7
```

Is `7` in `seen`?

```text
No
```

Store:

```text
seen = {
    2: 0
}
```

---

### i = 1

```text
num = 7
needed = 9 - 7 = 2
```

Is `2` in `seen`?

```text
YES
```

We know:

```text
2 → index 0
```

Current:

```text
7 → index 1
```

Return:

```text
[0,1]
```

### Complete trace

|  i | num | needed | seen before | Action          |
| -: | --: | -----: | ----------- | --------------- |
|  0 |   2 |      7 | `{}`        | store 2→0       |
|  1 |   7 |      2 | `{2:0}`     | found → `[0,1]` |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses the same algorithm.

```text
i = 0
num = 2
needed = 7
```

Store:

```text
2 → 0
```

Next:

```text
i = 1
num = 7
needed = 2
```

HashMap contains `2`.

Therefore:

```text
[0,1]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We scan the array once.

For every element, HashMap lookup is **O(1) average**.

Therefore:

### Time

```text
O(n)
```

### Space

In the worst case, we store `n` elements:

```text
O(n)
```

### Compare with brute force

Brute force:

```text
for i:
    for j:
```

Time:

```text
O(n²)
```

Hash map:

```text
O(n)
```

🔥 This is the interview upgrade.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a HashMap?

Because it gives average **O(1)** lookup for the required complement.

---

### Q2. Why calculate:

```python
needed = target - num
```

Because if:

```text
num + needed = target
```

then:

```text
needed = target - num
```

---

### Q3. What about duplicate numbers?

Example:

```text
[3,3]
target = 6
```

At the second `3`, we find the first `3`.

Answer:

```text
[0,1]
```

---

### Q4. Can we solve Two Sum after sorting?

Yes, using two pointers, but there is an important issue:

> Sorting destroys the original indices unless you preserve them.

For the standard LC1 problem, HashMap is the cleanest direct approach.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 COMPLEMENT + HASH MAP

Whenever you see:

> Find two values whose sum equals target

Immediately think:

```python
needed = target - current
```

Then:

```python
if needed in seen:
```

This pattern extends to many problems involving:

* target sums
* complements
* frequency lookup
* previously seen values

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Returning values:

```text
[2,7]
```

instead of indices:

```text
[0,1]
```

### ❌ Mistake 2

Using nested loops immediately.

That gives:

```text
O(n²)
```

### ❌ Mistake 3

Checking after inserting the current value without thinking about the "different elements" requirement.

The standard order is:

```text
check complement
then store current
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember:

> **Two Sum = Find the complement in previously seen elements.**

```python
needed = target - num

if needed in seen:
    return [seen[needed], i]

seen[num] = i
```

### Complexity

```text
Time  → O(n) average
Space → O(n)
```

🔥 **LC 1 — Easy**

---

# 🟦 PROBLEM 58 — MAJORITY ELEMENT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem introduces an extremely important algorithm:

# 🔥 BOYER-MOORE VOTING ALGORITHM

Given an array, find the element appearing **more than `n/2` times**.

Example:

```text
[2,2,1,1,1,2,2]
```

Array length:

```text
n = 7
```

Majority threshold:

```text
7/2 = 3.5
```

`2` occurs 4 times.

Therefore:

```text
2
```

### Exact LeetCode

✅ **LC 169 — Majority Element — Easy**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

A majority element appears:

```text
> n / 2
```

times.

Example:

```text
[3,3,4,2,3,3,3]
```

`3` appears 5 times.

Length:

```text
7
```

Need:

```text
> 3.5
```

So `3` is majority.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine every number is a voter.

The majority element has more than half the votes.

We can let different values **cancel each other**.

Example:

```text
[2,2,1,1,1,2,2]
```

Think:

```text
2 vs 1 → cancel
2 vs 1 → cancel
```

The majority value has votes left.

This is the central idea of Boyer-Moore.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Maintain:

```text
candidate
count
```

Initially:

```python
candidate = None
count = 0
```

For each number:

### Step 1

If:

```text
count == 0
```

choose current number as candidate.

### Step 2

If current number equals candidate:

```text
count += 1
```

Otherwise:

```text
count -= 1
```

Because one vote for candidate is cancelled by one vote for another value.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def majority_element(nums):

    candidate = None
    count = 0

    for num in nums:

        # If no active candidate, choose current number
        if count == 0:
            candidate = num

        # Same value supports candidate
        if num == candidate:
            count += 1

        # Different value cancels one candidate vote
        else:
            count -= 1

    return candidate


nums = [2, 2, 1, 1, 1, 2, 2]

answer = majority_element(nums)

print("Majority element:", answer)
```

### Output

```text
Majority element: 2
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int majorityElement(int[] nums) {

        int candidate = 0;
        int count = 0;

        for (int num : nums) {

            if (count == 0) {
                candidate = num;
            }

            if (num == candidate) {
                count++;
            } else {
                count--;
            }
        }

        return candidate;
    }

    public static void main(String[] args) {

        int[] nums = {2, 2, 1, 1, 1, 2, 2};

        int answer = majorityElement(nums);

        System.out.println("Majority element: " + answer);
    }
}
```

### Output

```text
Majority element: 2
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[2,2,1,1,1,2,2]
```

| num | candidate | count | Action        |
| --: | --------: | ----: | ------------- |
|   2 |         2 |     1 | choose 2      |
|   2 |         2 |     2 | same          |
|   1 |         2 |     1 | cancel        |
|   1 |         2 |     0 | cancel        |
|   1 |         1 |     1 | new candidate |
|   2 |         1 |     0 | cancel        |
|   2 |         2 |     1 | new candidate |

Final candidate:

```text
2
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same state transitions:

```text
candidate = 2
count = 1

2 → count 2

1 → count 1

1 → count 0

1 → candidate becomes 1

2 → count 0

2 → candidate becomes 2
```

Result:

```text
2
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

We scan the array once:

```text
n elements
```

Each operation is constant time.

Therefore:

### Time

```text
O(n)
```

### Space

Only:

```text
candidate
count
```

are maintained.

Therefore:

```text
O(1)
```

🔥 This is significantly better than a frequency dictionary if the problem guarantees a majority element.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does Boyer-Moore work?

Because the majority element appears more than all other elements combined.

Therefore, even if every non-majority occurrence cancels one majority occurrence, majority occurrences remain.

---

### Q2. What if the problem does NOT guarantee a majority element?

Then the candidate alone is not enough.

You should perform a second pass to verify:

```text
count(candidate) > n/2
```

---

### Q3. Why is the space O(1)?

We don't maintain a frequency map.

Only:

```text
candidate
count
```

are stored.

---

### Q4. What pattern should I recognize?

If you see:

> Element appears more than half the array

think:

# Boyer-Moore Voting

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Mental template:

```python
candidate = None
count = 0

for num in nums:

    if count == 0:
        candidate = num

    if num == candidate:
        count += 1
    else:
        count -= 1
```

### Recognition trigger

```text
> n/2 occurrences
```

→ **Boyer-Moore**

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Thinking:

```text
count == 0
```

means there is no majority.

No.

It only means the current candidate has been cancelled by competing values.

---

### ❌ Mistake 2

Using sorting unnecessarily.

Sorting gives:

```text
O(n log n)
```

Boyer-Moore:

```text
O(n)
```

---

### ❌ Mistake 3

Confusing majority with most frequent.

Majority means:

```text
> n/2
```

Most frequent could be much less than `n/2`.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Majority > n/2 → Boyer-Moore Voting.**

```text
Time  → O(n)
Space → O(1)
```

🔥 **LC 169 — Easy**

---

# 🟦 PROBLEM 59 — EQUILIBRIUM / PIVOT INDEX

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem teaches the **prefix-sum mindset**.

Given:

```text
[1,7,3,6,5,6]
```

The pivot index is:

```text
3
```

Why?

Left side:

```text
1 + 7 + 3 = 11
```

Right side:

```text
5 + 6 = 11
```

Therefore index `3` is the pivot.

### Exact LeetCode

✅ **LC 724 — Find Pivot Index — Easy**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

For an index `i`:

```text
sum(left side) == sum(right side)
```

The pivot element itself is excluded from both sides.

Example:

```text
[1,7,3,6,5,6]
       ↑
       3
```

Left:

```text
1 + 7 + 3 = 11
```

Right:

```text
5 + 6 = 11
```

Answer:

```text
3
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

First calculate:

```text
total_sum
```

At each index, maintain:

```text
left_sum
```

Then:

```text
right_sum = total_sum - left_sum - nums[i]
```

We check:

```text
left_sum == right_sum
```

### Example

```text
total = 28
```

At index 3:

```text
left = 11
nums[3] = 6
```

Therefore:

```text
right = 28 - 11 - 6
      = 11
```

Equal.

Pivot found.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Calculate:

```python
total = sum(nums)
```

### Step 2

Initialize:

```python
left_sum = 0
```

### Step 3

For every index:

```python
right_sum = total - left_sum - nums[i]
```

### Step 4

Check:

```python
if left_sum == right_sum:
```

Return `i`.

### Step 5

If not:

```python
left_sum += nums[i]
```

### Step 6

If no pivot exists:

```text
-1
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def pivot_index(nums):

    total = sum(nums)

    left_sum = 0

    for i in range(len(nums)):

        right_sum = total - left_sum - nums[i]

        if left_sum == right_sum:
            return i

        left_sum += nums[i]

    return -1


nums = [1, 7, 3, 6, 5, 6]

answer = pivot_index(nums)

print("Pivot index:", answer)
```

### Output

```text
Pivot index: 3
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int pivotIndex(int[] nums) {

        int total = 0;

        for (int num : nums) {
            total += num;
        }

        int leftSum = 0;

        for (int i = 0; i < nums.length; i++) {

            int rightSum = total - leftSum - nums[i];

            if (leftSum == rightSum) {
                return i;
            }

            leftSum += nums[i];
        }

        return -1;
    }

    public static void main(String[] args) {

        int[] nums = {1, 7, 3, 6, 5, 6};

        int answer = pivotIndex(nums);

        System.out.println("Pivot index: " + answer);
    }
}
```

### Output

```text
Pivot index: 3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[1,7,3,6,5,6]
```

Total:

```text
28
```

Start:

```text
left_sum = 0
```

|  i | nums[i] | left | right | Equal? |
| -: | ------: | ---: | ----: | ------ |
|  0 |       1 |    0 |    27 | ❌      |
|  1 |       7 |    1 |    20 | ❌      |
|  2 |       3 |    8 |    17 | ❌      |
|  3 |       6 |   11 |    11 | ✅      |

Return:

```text
3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows the same formula:

```text
rightSum = total - leftSum - nums[i]
```

At index `3`:

```text
total = 28
leftSum = 11
nums[3] = 6
```

Therefore:

```text
rightSum = 28 - 11 - 6
         = 11
```

So:

```text
leftSum == rightSum
```

Return:

```text
3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

### First pass

Calculate total:

```text
O(n)
```

### Second pass

Find pivot:

```text
O(n)
```

Total:

```text
O(n) + O(n)
= O(n)
```

### Space

Only:

```text
total
left_sum
right_sum
```

Therefore:

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why subtract the current element?

Because pivot itself belongs to neither side.

Therefore:

```python
right = total - left - nums[i]
```

---

### Q2. Can the pivot be index 0?

Yes.

Example:

```text
[2,1,-1]
```

At index `0`:

```text
left = 0
right = 1 + (-1) = 0
```

Answer:

```text
0
```

---

### Q3. Can the pivot be the last index?

Yes.

Example:

```text
[-1,1,2]
```

At index `2`:

```text
left = 0
right = 0
```

---

### Q4. Why is this called a prefix-sum pattern?

Because `left_sum` represents the cumulative sum of all elements before the current index.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Whenever you see:

> Compare the sum on the left and right of every index

Think:

```text
total_sum
left_sum
right = total - left - current
```

This avoids repeatedly calculating left and right sums.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Including the pivot element in the right sum.

Wrong:

```python
right = total - left_sum
```

Correct:

```python
right = total - left_sum - nums[i]
```

---

### ❌ Mistake 2

Recalculating:

```python
sum(nums[:i])
sum(nums[i+1:])
```

for every index.

That can become:

```text
O(n²)
```

---

### ❌ Mistake 3

Returning the value instead of the index.

The answer is:

```text
index
```

not:

```text
nums[index]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Pivot Index = Left Sum == Total − Left Sum − Current Element**

```text
Time  → O(n)
Space → O(1)
```

🔥 **LC 724 — Easy**

---

# 🟦 PROBLEM 60 — SORT 0s, 1s & 2s

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is the final problem of Day 6.

And it is a very important **Medium** array problem.

### Exact LeetCode

🔥 **LC 75 — Sort Colors — Medium**

The array contains only:

```text
0
1
2
```

Example:

```text
[2,0,2,1,1,0]
```

Expected:

```text
[0,0,1,1,2,2]
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

We need to sort the array containing only three possible values:

```text
0, 1, 2
```

### Important restriction

The classic LC75 solution should be:

```text
O(n) time
O(1) extra space
```

So don't simply call:

```python
nums.sort()
```

The purpose is to demonstrate the **Dutch National Flag algorithm**.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Use three pointers:

```text
low
mid
high
```

They represent three regions.

```text
0 ... low-1       → 0s
low ... mid-1     → 1s
mid ... high      → unknown
high+1 ... n-1    → 2s
```

Initially:

```text
low = 0
mid = 0
high = n - 1
```

### If `nums[mid] == 0`

Move it to the beginning.

```text
swap(low, mid)
low += 1
mid += 1
```

### If `nums[mid] == 1`

It's already in the middle.

```text
mid += 1
```

### If `nums[mid] == 2`

Move it to the end.

```text
swap(mid, high)
high -= 1
```

⚠️ **Do not increment `mid` here.**

Why?

Because the element swapped from `high` into `mid` has not been examined yet.

This is a very important interview detail.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given:

```text
nums
```

Initialize:

```python
low = 0
mid = 0
high = len(nums) - 1
```

While:

```python
mid <= high
```

### Case 1 — `0`

```python
swap(nums[low], nums[mid])

low += 1
mid += 1
```

### Case 2 — `1`

```python
mid += 1
```

### Case 3 — `2`

```python
swap(nums[mid], nums[high])

high -= 1
```

No `mid += 1`.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def sort_colors(nums):

    low = 0
    mid = 0
    high = len(nums) - 1

    while mid <= high:

        # Current element is 0
        if nums[mid] == 0:

            nums[low], nums[mid] = nums[mid], nums[low]

            low += 1
            mid += 1

        # Current element is 1
        elif nums[mid] == 1:

            mid += 1

        # Current element is 2
        else:

            nums[mid], nums[high] = nums[high], nums[mid]

            high -= 1


nums = [2, 0, 2, 1, 1, 0]

sort_colors(nums)

print(nums)
```

### Output

```text
[0, 0, 1, 1, 2, 2]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static void sortColors(int[] nums) {

        int low = 0;
        int mid = 0;
        int high = nums.length - 1;

        while (mid <= high) {

            // Current element is 0
            if (nums[mid] == 0) {

                int temp = nums[low];
                nums[low] = nums[mid];
                nums[mid] = temp;

                low++;
                mid++;
            }

            // Current element is 1
            else if (nums[mid] == 1) {

                mid++;
            }

            // Current element is 2
            else {

                int temp = nums[mid];
                nums[mid] = nums[high];
                nums[high] = temp;

                high--;
            }
        }
    }

    public static void main(String[] args) {

        int[] nums = {2, 0, 2, 1, 1, 0};

        sortColors(nums);

        System.out.println(Arrays.toString(nums));
    }
}
```

### Output

```text
[0, 0, 1, 1, 2, 2]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[2,0,2,1,1,0]
```

Initial:

```text
low = 0
mid = 0
high = 5
```

---

### Step 1

`nums[mid] = 2`

Swap index `0` and `5`.

```text
[0,0,2,1,1,2]
```

Now:

```text
high = 4
```

⚠️ `mid` stays `0`.

---

### Step 2

`nums[mid] = 0`

Swap:

```text
index 0 with index 0
```

Array:

```text
[0,0,2,1,1,2]
```

Now:

```text
low = 1
mid = 1
```

---

### Step 3

`nums[mid] = 0`

Array remains:

```text
[0,0,2,1,1,2]
```

Now:

```text
low = 2
mid = 2
```

---

### Step 4

`nums[mid] = 2`

Swap index `2` and `4`:

```text
[0,0,1,1,2,2]
```

Now:

```text
high = 3
```

`mid` remains `2`.

---

### Step 5

`nums[mid] = 1`

Move:

```text
mid = 3
```

---

### Step 6

`nums[mid] = 1`

Move:

```text
mid = 4
```

Now:

```text
mid > high
```

Stop.

Final:

```text
[0,0,1,1,2,2]
```

---

# 🔥 THE MOST IMPORTANT DETAIL

Suppose:

```text
nums[mid] == 2
```

We do:

```python
swap(nums[mid], nums[high])
high -= 1
```

But **do not**:

```python
mid += 1
```

Why?

Example:

```text
mid contains 2
high contains 0
```

After swap:

```text
mid contains 0
```

We haven't processed that `0`.

If we increment `mid`, we skip it.

🔥 This is a classic interview trap.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs exactly the same pointer movement.

For:

```text
[2,0,2,1,1,0]
```

The important pointer progression is:

```text
2 → move to right
0 → move to left
0 → move to left
2 → move to right
1 → middle
1 → middle
```

Final:

```text
[0,0,1,1,2,2]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Every element is processed a constant number of times.

The `mid` pointer moves across the array, while `low` and `high` partition the array.

Therefore:

### Time

```text
O(n)
```

### Space

Only:

```text
low
mid
high
temp
```

are used.

Therefore:

```text
O(1)
```

🔥 This satisfies the classic LC75 requirement.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why three pointers?

Because we need to maintain three regions:

```text
0s | 1s | unknown | 2s
```

---

### Q2. Why don't we increment `mid` after swapping a 2?

Because the element coming from the right side is still unprocessed.

---

### Q3. What algorithm is this?

# Dutch National Flag Algorithm

Developed by Edsger Dijkstra.

---

### Q4. Could we count the number of 0s, 1s and 2s?

Yes.

That would also achieve:

```text
O(n)
```

time and:

```text
O(1)
```

space.

But the classic LC75 interview solution demonstrates the three-pointer partitioning technique.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This pattern is:

# 🔥 THREE-WAY PARTITIONING

Mental picture:

```text
[ 0s ][ 1s ][ unknown ][ 2s ]
       ↑       ↑        ↑
      low     mid      high
```

### Recognition trigger

When you see:

> Sort an array containing only three categories/values in one pass

think:

```text
low / mid / high
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
nums.sort()
```

This solves the practical task but misses the intended algorithmic requirement.

---

### ❌ Mistake 2

After swapping a `2`:

```python
mid += 1
```

❌ Wrong.

---

### ❌ Mistake 3

Using only two pointers without understanding the unknown region.

---

### ❌ Mistake 4

Forgetting:

```python
while mid <= high:
```

The unknown region exists while:

```text
mid <= high
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Remember:

> **0 → send left. 1 → leave it. 2 → send right.**

```text
0 → swap(low, mid), low++, mid++
1 → mid++
2 → swap(mid, high), high--
```

### Complexity

```text
Time  → O(n)
Space → O(1)
```

🔥 **LC 75 — Medium**

---

# 🏆 DAY 6 — SESSION 3 MASTER CONNECTION

You just completed four major interview patterns.

| Problem                 | Pattern         | Mental Trigger               |
| ----------------------- | --------------- | ---------------------------- |
| **57 Two Sum**          | Hash Map        | `target - current`           |
| **58 Majority Element** | Boyer-Moore     | `> n/2`                      |
| **59 Pivot Index**      | Prefix Sum      | `left == total-left-current` |
| **60 Sort 0/1/2**       | 3-Way Partition | `low / mid / high`           |

---

# 🧠 DAY 6 — PATTERN RECOGNITION CHEAT SHEET

## 57️⃣ Two Sum

Question says:

> Two numbers add to target?

Think:

```python
needed = target - num
```

HashMap.

---

## 58️⃣ Majority Element

Question says:

> Appears more than n/2?

Think:

```text
Boyer-Moore
```

---

## 59️⃣ Pivot Index

Question says:

> Left sum equals right sum?

Think:

```python
right = total - left - current
```

---

## 60️⃣ Sort 0,1,2

Question says:

> Three categories + O(n) + O(1)?

Think:

```text
Dutch National Flag
```

---

# 🧪 DAY 6 — FINAL MASTER TEST

Do **not** look at the solutions above.

## Test 57

```text
nums = [3, 8, 4, 7]
target = 11
```

Expected indices:

```text
[0, 1]
```

---

## Test 58

```text
nums = [3,3,4,2,3,3,3]
```

Expected:

```text
3
```

---

## Test 59

```text
nums = [2,1,-1]
```

Expected pivot index:

```text
0
```

---

## Test 60

```text
nums = [2,0,1,2,1,0,0]
```

Expected:

```text
[0,0,0,1,1,2,2]
```

---

# 🔥 DAY 6 — COMPLETE

```text
DAY 6

51 ✅ Merge Two Sorted Arrays
52 ✅ Intersection of Two Arrays
53 ✅ Rotate Array by One Position
54 ✅ Rotate Array by K Positions
55 ✅ Second Smallest Distinct Element
56 ✅ Maximum Subarray Sum
57 ✅ Two Sum
58 ✅ Majority Element
59 ✅ Pivot Index
60 ✅ Sort 0s, 1s & 2s
```

# 🟢 CR2 OVERALL: 60 / 100

```text
████████████████████░░░░░░░░░░ 60%
```

## 🔥 Day 6 patterns mastered

```text
Two-Pointer Merge
Hash Set
Index Shifting
Array Reversal
Top-2 Tracking
Kadane
Hash Map Complement
Boyer-Moore
Prefix Sum
Dutch National Flag
```

**Day 6 is now complete: 10/10.**

The next locked block is **Day 7 — Session 1: Problems 61–63**:
**Linear Search → Binary Search → Bubble Sort.**

Would you like to continue with Day 7 — Session 1, or do a quick no-solution review of Problems 57–60 first?

