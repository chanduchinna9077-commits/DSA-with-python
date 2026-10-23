# 🟤 DAY 7

## SEARCH + SORT + GREEDY

### Problems 61–70

```text
Linear Search
Binary Search
Bubble Sort
Selection Sort
Insertion Sort
Merge Sorted Data
Kth Largest
Frequency Sorting
Assign Cookies
Canonical Coin Greedy
```

### 🎯 Skill

**Algorithm implementation + complexity**

---


# 🔥 CR2 — DAY 7 — SESSION 1

## Problems 61–63 | Search + Sorting Fundamentals

We are now entering **Day 7: Search + Sort + Greedy**.

| #  | Problem       | LeetCode                    | Difficulty | Core Pattern      |
| -- | ------------- | --------------------------- | ---------- | ----------------- |
| 61 | Linear Search | No exact canonical LC match | —          | Sequential Search |
| 62 | Binary Search | **LC 704 — Binary Search**  | Easy       | Divide & Conquer  |
| 63 | Bubble Sort   | No exact canonical LC match | —          | Adjacent Swapping |

### 🎯 Session Goal

By the end of this session, you should instantly recognize:

```text
Unsorted array + find value
        ↓
Linear Search

Sorted array + find value
        ↓
Binary Search

Repeated adjacent comparison/swapping
        ↓
Bubble Sort
```

---

# 🟦 PROBLEM 61 — LINEAR SEARCH

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Linear Search is the simplest searching algorithm.

It is not difficult, but **do not underestimate it**.

Why?

Because placement tests often test whether you can:

* correctly traverse an array
* handle indexes
* stop when found
* handle "not found"
* understand worst-case complexity

### Core idea

Check elements **one by one from left to right**.

Example:

```text
arr = [10, 25, 7, 40, 15]
target = 40
```

Search:

```text
10 ❌
25 ❌
7  ❌
40 ✅
```

Return:

```text
index = 3
```

---

## 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Definition

**Linear Search** checks every element sequentially until:

1. the target is found, or
2. the array ends.

### Example

```text
arr = [4, 9, 2, 7, 5]
target = 7
```

Indices:

```text
0 → 4
1 → 9
2 → 2
3 → 7
```

Answer:

```text
3
```

If target is absent:

```text
arr = [4,9,2,7,5]
target = 10
```

Answer:

```text
-1
```

### Exact LeetCode match

❌ **No exact canonical LeetCode problem specifically for the basic Linear Search task.**

There are many LeetCode problems that use linear scanning, but they are not the exact standalone problem.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine looking for a particular book on a shelf.

You don't know where it is.

You check:

```text
Book 1 → no
Book 2 → no
Book 3 → no
Book 4 → yes
```

That's Linear Search.

The computer does exactly the same thing:

```python
for i in range(len(arr)):
    if arr[i] == target:
        return i
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given:

```text
arr
target
```

### Step 1

Start from index `0`.

### Step 2

Compare:

```text
arr[i] == target
```

### Step 3

If equal:

```text
return i
```

### Step 4

Otherwise move to:

```text
i + 1
```

### Step 5

If the loop finishes:

```text
return -1
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def linear_search(arr, target):

    for i in range(len(arr)):

        # Check whether current element is target
        if arr[i] == target:
            return i

    # Target was not found
    return -1


arr = [10, 25, 7, 40, 15]
target = 40

answer = linear_search(arr, target)

print("Index:", answer)
```

### Output

```text
Index: 3
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int linearSearch(int[] arr, int target) {

        for (int i = 0; i < arr.length; i++) {

            // Check current element
            if (arr[i] == target) {
                return i;
            }
        }

        // Target not found
        return -1;
    }

    public static void main(String[] args) {

        int[] arr = {10, 25, 7, 40, 15};

        int target = 40;

        int answer = linearSearch(arr, target);

        System.out.println("Index: " + answer);
    }
}
```

### Output

```text
Index: 3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
arr = [10, 25, 7, 40, 15]
target = 40
```

|  i | arr[i] | Compare    | Result |
| -: | -----: | ---------- | ------ |
|  0 |     10 | `10 == 40` | ❌      |
|  1 |     25 | `25 == 40` | ❌      |
|  2 |      7 | `7 == 40`  | ❌      |
|  3 |     40 | `40 == 40` | ✅      |

Immediately return:

```text
3
```

Notice that `15` was never examined.

That is an important property of search algorithms:

> **If the target is found early, we stop early.**

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows the same process.

```text
i = 0 → 10 ≠ 40
i = 1 → 25 ≠ 40
i = 2 → 7 ≠ 40
i = 3 → 40 = 40
```

Return:

```text
3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Suppose there are `n` elements.

### Best case

Target is first:

```text
[50, ...]
 ↑
target
```

Only one comparison.

```text
O(1)
```

### Worst case

Target is last:

```text
[1,2,3,...,50]
             ↑
           target
```

We perform `n` comparisons.

```text
O(n)
```

### Average case

Approximately half the elements are examined:

```text
n/2
```

Ignoring constants:

```text
O(n)
```

### Space

Only the loop variable and a few variables are used:

```text
O(1)
```

### Final

```text
Best  → O(1)
Average → O(n)
Worst → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Can Linear Search work on an unsorted array?

✅ Yes.

That is one of its biggest advantages.

---

### Q2. Does Linear Search require sorted data?

❌ No.

---

### Q3. When would you stop early?

As soon as the target is found.

---

### Q4. What if the target appears multiple times?

The basic implementation returns the **first occurrence**.

Example:

```text
[5,2,5,7]
target = 5
```

Answer:

```text
0
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Whenever you see:

> Find whether a particular value exists in an arbitrary array.

Think:

```python
for x in arr:
    if x == target:
        ...
```

### Recognition rule

```text
No sorting guarantee
        +
Simple target lookup
        ↓
Linear Search
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Starting from index `1` instead of `0`.

### ❌ Mistake 2

Returning `0` when target isn't found.

Use:

```text
-1
```

when that is the specified convention.

### ❌ Mistake 3

Continuing the loop after finding the target when only the first occurrence is required.

### ❌ Mistake 4

Thinking Linear Search requires sorted data.

It doesn't.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Linear Search = Check one element at a time.**

```text
Best  → O(1)
Worst → O(n)
Space → O(1)
```

No sorting required.

---

# 🟦 PROBLEM 62 — BINARY SEARCH

# 🔥 IMPORTANT

This is one of the most important search algorithms in your CR2 training.

## Exact LeetCode:

🔥 **LC 704 — Binary Search — Easy**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

The biggest difference between Linear Search and Binary Search is:

```text
Linear Search
→ checks one-by-one

Binary Search
→ eliminates HALF the search space each step
```

But there is a critical requirement:

# ⚠️ THE ARRAY MUST BE SORTED

Example:

```text
nums = [1,3,5,7,9,11,13]
target = 9
```

Instead of checking:

```text
1
3
5
7
9
```

we inspect the middle.

Middle:

```text
7
```

Since:

```text
9 > 7
```

everything left of `7` can be discarded.

Remaining:

```text
[9,11,13]
```

Then continue.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Definition

**Binary Search** repeatedly divides a sorted search space into two halves.

Given:

```text
nums = [-1,0,3,5,9,12]
target = 9
```

Answer:

```text
4
```

because:

```text
nums[4] = 9
```

### Exact LeetCode

🔥 **LC 704 — Binary Search — Easy**

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine guessing a number between 1 and 100.

If someone tells you:

> Is it 50?

If answer is:

> Too low.

You immediately know:

```text
1–50 → discard
51–100 → continue
```

Then ask:

```text
75?
```

Again, half disappears.

That's Binary Search.

### Core invariant

At every step:

```text
target must be somewhere inside [left, right]
```

We keep shrinking this interval.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given sorted array:

```text
nums
```

Initialize:

```python
left = 0
right = len(nums) - 1
```

While:

```python
left <= right
```

### Step 1

Calculate middle:

```python
mid = left + (right - left) // 2
```

This is the standard safe formula.

### Step 2

If:

```python
nums[mid] == target
```

return `mid`.

### Step 3

If:

```python
nums[mid] < target
```

target must be on the right:

```python
left = mid + 1
```

### Step 4

Otherwise:

```python
right = mid - 1
```

### Step 5

If search ends:

```text
return -1
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def binary_search(nums, target):

    left = 0
    right = len(nums) - 1

    while left <= right:

        # Find middle index
        mid = left + (right - left) // 2

        # Target found
        if nums[mid] == target:
            return mid

        # Target is on the right
        elif nums[mid] < target:
            left = mid + 1

        # Target is on the left
        else:
            right = mid - 1

    # Target not found
    return -1


nums = [-1, 0, 3, 5, 9, 12]
target = 9

answer = binary_search(nums, target)

print("Index:", answer)
```

### Output

```text
Index: 4
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int binarySearch(int[] nums, int target) {

        int left = 0;
        int right = nums.length - 1;

        while (left <= right) {

            int mid = left + (right - left) / 2;

            // Target found
            if (nums[mid] == target) {
                return mid;
            }

            // Search right half
            else if (nums[mid] < target) {
                left = mid + 1;
            }

            // Search left half
            else {
                right = mid - 1;
            }
        }

        return -1;
    }

    public static void main(String[] args) {

        int[] nums = {-1, 0, 3, 5, 9, 12};

        int target = 9;

        int answer = binarySearch(nums, target);

        System.out.println("Index: " + answer);
    }
}
```

### Output

```text
Index: 4
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [-1,0,3,5,9,12]
target = 9
```

Indices:

```text
0  1  2  3  4   5
-1 0  3  5  9  12
```

---

### Iteration 1

```text
left = 0
right = 5
```

Calculate:

```text
mid = 0 + (5-0)//2
    = 2
```

Value:

```text
nums[2] = 3
```

Compare:

```text
3 < 9
```

Therefore:

```text
left = 3
```

Discard:

```text
[-1,0,3]
```

---

### Iteration 2

```text
left = 3
right = 5
```

```text
mid = 3 + (5-3)//2
    = 4
```

Value:

```text
nums[4] = 9
```

Found.

Return:

```text
4
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Exactly the same:

```text
left = 0
right = 5
mid = 2
nums[2] = 3
```

Since:

```text
3 < 9
```

move:

```text
left = 3
```

Then:

```text
mid = 4
nums[4] = 9
```

Return:

```text
4
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

This is where Binary Search becomes powerful.

Suppose:

```text
n = 16
```

Each iteration approximately halves the search space:

```text
16
↓
8
↓
4
↓
2
↓
1
```

Number of divisions is approximately:

```text
log₂(n)
```

Therefore:

### Time

```text
O(log n)
```

### Space — iterative

```text
O(1)
```

This is dramatically better than:

```text
O(n)
```

for very large sorted arrays.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the most important requirement for Binary Search?

The search space must have an ordering property.

For basic LC704:

```text
array must be sorted
```

---

### Q2. Why do we use:

```python
mid = left + (right - left) // 2
```

instead of:

```python
mid = (left + right) // 2
```

In languages with fixed-size integers such as Java, `left + right` can theoretically overflow.

The safer standard form is:

```python
left + (right-left)//2
```

Python integers don't have Java-style fixed-width overflow here, but this form is excellent interview habit.

---

### Q3. Why is the condition:

```python
while left <= right
```

?

Because `left == right` means there is still one candidate element to inspect.

---

### Q4. What happens when target isn't present?

Eventually:

```text
left > right
```

The search space becomes empty.

Return:

```text
-1
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Your first Binary Search recognition rule:

> **Sorted search space + target lookup → think Binary Search.**

Master template:

```python
left = 0
right = n - 1

while left <= right:

    mid = left + (right - left) // 2

    if nums[mid] == target:
        return mid

    elif nums[mid] < target:
        left = mid + 1

    else:
        right = mid - 1

return -1
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using Binary Search on an unsorted array.

Example:

```text
[7,2,9,1,5]
```

Basic binary search does not work.

---

### ❌ Mistake 2

Writing:

```python
left = mid
```

instead of:

```python
left = mid + 1
```

This can cause an infinite loop.

---

### ❌ Mistake 3

Writing:

```python
right = mid
```

instead of:

```python
right = mid - 1
```

for this exact closed-interval implementation.

---

### ❌ Mistake 4

Using:

```python
while left < right
```

without adjusting the rest of the algorithm.

For our standard `[left, right]` inclusive implementation:

```python
while left <= right
```

is correct.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Binary Search = Sorted data + repeatedly eliminate half.**

```text
Time  → O(log n)
Space → O(1)
```

🔥 **LC 704 — Easy**

---

# 🟦 PROBLEM 63 — BUBBLE SORT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Bubble Sort is **not** a sorting algorithm you should choose for production code.

But it is useful for:

* understanding sorting fundamentals
* placement exams
* learning adjacent swaps
* understanding how sorting algorithms work internally

### Core idea

Compare adjacent elements:

```text
arr[i]
arr[i+1]
```

If they are in the wrong order:

```text
swap
```

The largest unsorted element gradually "bubbles" toward the end.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
[5,3,8,4,2]
```

Sort ascending.

Compare:

```text
5 and 3
```

Since:

```text
5 > 3
```

swap:

```text
[3,5,8,4,2]
```

Then:

```text
5 and 8
```

No swap.

Then:

```text
8 and 4
```

Swap:

```text
[3,5,4,8,2]
```

Continue.

### Exact LeetCode match

❌ **No exact canonical LeetCode standalone Bubble Sort problem.**

LeetCode contains many sorting problems, but this basic implementation is a fundamental algorithm exercise rather than a specific LC problem.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think about bubbles in water.

The larger element gradually moves toward the right.

Example:

```text
[5,3,8,4,2]
```

After one complete pass:

```text
[3,5,4,2,8]
```

Notice:

```text
8
```

has reached the end.

After another pass:

```text
[3,4,2,5,8]
```

Now:

```text
5
```

moves into its correct region.

Eventually:

```text
[2,3,4,5,8]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

For an array of `n` elements:

### Step 1

Run multiple passes.

```python
for i in range(n):
```

### Step 2

Compare adjacent elements.

```python
arr[j] > arr[j+1]
```

### Step 3

If they are out of order, swap.

### Step 4

After each pass, the largest remaining element reaches the end.

Therefore, we don't need to check the already sorted suffix.

Use:

```python
range(n - 1 - i)
```

### Step 5 — Optimization

Track whether a swap happened.

If no swap occurs during an entire pass:

```text
array is already sorted
```

Stop early.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def bubble_sort(arr):

    n = len(arr)

    for i in range(n):

        swapped = False

        # Last i elements are already sorted
        for j in range(n - 1 - i):

            # Swap if elements are in wrong order
            if arr[j] > arr[j + 1]:

                arr[j], arr[j + 1] = arr[j + 1], arr[j]

                swapped = True

        # If no swap happened, array is already sorted
        if not swapped:
            break

    return arr


arr = [5, 3, 8, 4, 2]

answer = bubble_sort(arr)

print(answer)
```

### Output

```text
[2, 3, 4, 5, 8]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static void bubbleSort(int[] arr) {

        int n = arr.length;

        for (int i = 0; i < n; i++) {

            boolean swapped = false;

            // Last i elements are already sorted
            for (int j = 0; j < n - 1 - i; j++) {

                if (arr[j] > arr[j + 1]) {

                    int temp = arr[j];
                    arr[j] = arr[j + 1];
                    arr[j + 1] = temp;

                    swapped = true;
                }
            }

            // Already sorted
            if (!swapped) {
                break;
            }
        }
    }

    public static void main(String[] args) {

        int[] arr = {5, 3, 8, 4, 2};

        bubbleSort(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text
[2, 3, 4, 5, 8]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[5,3,8,4,2]
```

## PASS 1

Compare `5` and `3`:

```text
[3,5,8,4,2]
```

Compare `5` and `8`:

```text
[3,5,8,4,2]
```

Compare `8` and `4`:

```text
[3,5,4,8,2]
```

Compare `8` and `2`:

```text
[3,5,4,2,8]
```

Largest element:

```text
8
```

is now fixed at the end.

---

## PASS 2

Only process:

```text
[3,5,4,2]
```

Compare:

```text
3,5 → no swap
5,4 → swap
```

Array:

```text
[3,4,5,2,8]
```

Then:

```text
5,2 → swap
```

Array:

```text
[3,4,2,5,8]
```

Now:

```text
5,8
```

doesn't need processing because `8` is already sorted.

---

## PASS 3

Process:

```text
[3,4,2]
```

```text
3,4 → no swap
4,2 → swap
```

Array:

```text
[3,2,4,5,8]
```

---

## PASS 4

Process:

```text
[3,2]
```

Swap:

```text
[2,3,4,5,8]
```

---

## PASS 5

No swaps.

Therefore:

```text
swapped = False
```

Stop.

Final:

```text
[2,3,4,5,8]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows the exact same adjacent-swap process.

Initial:

```text
[5,3,8,4,2]
```

After Pass 1:

```text
[3,5,4,2,8]
```

After Pass 2:

```text
[3,4,2,5,8]
```

After Pass 3:

```text
[3,2,4,5,8]
```

After Pass 4:

```text
[2,3,4,5,8]
```

No swap on the next pass → terminate.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

## Worst case

Consider reverse-sorted:

```text
[5,4,3,2,1]
```

We need many swaps.

Number of comparisons is approximately:

```text
(n-1) + (n-2) + ... + 1
```

This equals:

```text
n(n-1)/2
```

Therefore:

```text
O(n²)
```

### Best case with `swapped` optimization

Already sorted:

```text
[1,2,3,4,5]
```

First pass makes:

```text
0 swaps
```

We stop.

Therefore:

```text
O(n)
```

### Space

Only temporary swap storage is needed:

```text
O(1)
```

### Final

```text
Best  → O(n)    with optimization
Average → O(n²)
Worst → O(n²)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is it called Bubble Sort?

Because larger elements progressively "bubble" toward the end.

---

### Q2. Why does the inner loop shrink?

After each pass, one largest unsorted element reaches its final position.

So:

```python
range(n - 1 - i)
```

avoids comparing the sorted suffix.

---

### Q3. What does `swapped` do?

It detects whether the array became sorted before all possible passes were completed.

---

### Q4. Is Bubble Sort good for large production data?

Generally, no.

Its worst-case complexity is:

```text
O(n²)
```

More efficient sorting algorithms are normally used.

For this CR2 exercise, the goal is **algorithmic fundamentals and placement fluency**.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

The recognition pattern is:

```text
Adjacent elements
+
Compare
+
Swap if wrong order
```

Think:

# Bubble Sort

Mental template:

```python
for i in range(n):
    for j in range(n - 1 - i):
        if arr[j] > arr[j + 1]:
            swap
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
range(n)
```

for the inner loop every time.

The sorted suffix doesn't need to be checked.

---

### ❌ Mistake 2

Writing:

```python
if arr[j] < arr[j+1]:
```

when you want ascending order.

For ascending order, swap when:

```python
arr[j] > arr[j+1]
```

---

### ❌ Mistake 3

Forgetting the `swapped` optimization.

It isn't required for correctness, but it improves best-case behavior.

---

### ❌ Mistake 4

Thinking one pass completely sorts every array.

One pass guarantees only that the largest remaining element reaches the end.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Bubble Sort = Repeatedly compare adjacent elements and swap them if they are out of order.**

```text
Best     → O(n)
Average  → O(n²)
Worst    → O(n²)
Space    → O(1)
```

No exact standalone LeetCode match.

---

# 🏆 DAY 7 — SESSION 1 MASTER CONNECTION

You have now learned three search/sort fundamentals.

| Problem              | Core Pattern        | Key Formula / Idea             |
| -------------------- | ------------------- | ------------------------------ |
| **61 Linear Search** | Sequential Scan     | Check every element            |
| **62 Binary Search** | Divide Search Space | `mid = left + (right-left)//2` |
| **63 Bubble Sort**   | Adjacent Swapping   | Swap if `arr[j] > arr[j+1]`    |

---

# 🧠 THE MOST IMPORTANT DIFFERENCE

## Linear Search

```text
Data does NOT need to be sorted.

Time:
O(n)
```

## Binary Search

```text
Data must have an appropriate sorted/order property.

Time:
O(log n)
```

## Bubble Sort

```text
Used to learn sorting fundamentals.

Time:
O(n²) worst case
```

---

# 🔥 SEARCH RECOGNITION RULE

When an interviewer gives you:

### Unsorted array

```text
"Find X"
```

Think:

```text
Linear Search
```

unless another structure/pattern gives a better solution.

### Sorted array

```text
"Find X"
```

Think:

```text
Binary Search
```

### Sorted array required from scratch

```text
"Sort using adjacent swaps"
```

Think:

```text
Bubble Sort
```

---

# 🧪 SESSION 1 — NO-SOLUTION MASTER TEST

Do these **without looking back at the code**.

## Test 1 — Linear Search

```text
arr = [14, 7, 23, 9, 31]
target = 23
```

Expected:

```text
2
```

---

## Test 2 — Binary Search

```text
nums = [2,5,8,12,16,23,38]
target = 16
```

Expected:

```text
4
```

---

## Test 3 — Binary Search — Not Found

```text
nums = [1,4,7,10,13,20]
target = 9
```

Expected:

```text
-1
```

---

## Test 4 — Bubble Sort

```text
arr = [9,4,7,2,8,1]
```

Expected:

```text
[1,2,4,7,8,9]
```

---

# 🎯 REPRODUCTION DRILL

You should now be able to write these three templates **from memory**:

### Linear Search

```python
for i in range(len(arr)):
    if arr[i] == target:
        return i
return -1
```

### Binary Search

```python
left = 0
right = len(nums) - 1

while left <= right:
    mid = left + (right - left) // 2

    if nums[mid] == target:
        return mid
    elif nums[mid] < target:
        left = mid + 1
    else:
        right = mid - 1

return -1
```

### Bubble Sort

```python
for i in range(n):
    swapped = False

    for j in range(n - 1 - i):
        if arr[j] > arr[j + 1]:
            arr[j], arr[j + 1] = arr[j + 1], arr[j]
            swapped = True

    if not swapped:
        break
```

---

# 📊 CR2 PROGRESS

```text
DAY 1  ██████████  10/10
DAY 2  ██████████  10/10
DAY 3  ██████████  10/10
DAY 4  ██████████  10/10
DAY 5  ██████████  10/10
DAY 6  ██████████  10/10
DAY 7  ███░░░░░░░  3/10
```

# 🟢 OVERALL: 63 / 100

**Day 7 Session 1 complete.**

### Next locked sequence — Day 7 Session 2

**64. Selection Sort**
**65. Insertion Sort**
**66. Merge Two Sorted Lists/Arrays — LC 88 related/core match**

These three will focus on **sorting fundamentals + merging**, with special attention to when each sorting approach is useful and what interviewers expect you to understand.

Would you like to continue with Day 7 — Session 2, or do the no-solution master test for Problems 61–63 first?


# 🔥 CR2 — DAY 7 — SESSION 2

## Problems 64–66 | Sorting Fundamentals + Merge

We continue exactly from **63/100**.

| #  | Problem                       | LeetCode                                            | Difficulty | Core Pattern        |
| -- | ----------------------------- | --------------------------------------------------- | ---------- | ------------------- |
| 64 | Selection Sort                | No exact canonical LC                               | —          | Select Minimum      |
| 65 | Insertion Sort                | No exact canonical LC                               | —          | Build Sorted Prefix |
| 66 | Merge Two Sorted Lists/Arrays | **LC 88 — Merge Sorted Array** (related/core match) | Easy       | Two Pointers        |

### 🎯 Session Goal

By the end of this session, you should recognize:

```text
Selection Sort
→ Find minimum → put it at correct position

Insertion Sort
→ Take current element → insert into sorted left side

Merge Sorted Arrays
→ Compare two pointers → take smaller
```

---

# 🟦 PROBLEM 64 — SELECTION SORT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Selection Sort is another fundamental sorting algorithm.

The central idea is extremely simple:

> **Find the smallest remaining element and place it at the front.**

Example:

```text
[64, 25, 12, 22, 11]
```

Find minimum:

```text
11
```

Put it at index `0`:

```text
[11, 25, 12, 22, 64]
```

Then repeat for the remaining portion.

### Important interview distinction

Selection Sort and Bubble Sort are both:

```text
O(n²)
```

in their typical/worst-case time complexity.

But their **behavior is different**.

Selection Sort performs relatively few swaps:

```text
at most O(n) swaps
```

while Bubble Sort can perform:

```text
O(n²) swaps
```

That distinction is worth knowing.

### Exact LeetCode match

❌ No exact canonical LeetCode problem for basic Selection Sort.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
arr = [64, 25, 12, 22, 11]
```

Sort in ascending order.

Selection Sort divides the array conceptually into:

```text
[sorted portion | unsorted portion]
```

Initially:

```text
[ | 64,25,12,22,11]
```

Find minimum of unsorted part:

```text
11
```

Swap with first element:

```text
[11 | 25,12,22,64]
```

Next minimum:

```text
12
```

```text
[11,12 | 25,22,64]
```

Continue until everything is sorted.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine arranging students by height.

You stand at position `0` and ask:

> Who is the shortest student among everyone remaining?

Bring that student to position `0`.

Then:

> Who is the shortest among the remaining students?

Bring them to position `1`.

Repeat.

That's Selection Sort.

### Key idea

At position `i`:

```text
Find minimum from i → n-1
```

Then:

```text
Swap minimum with arr[i]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

For an array of size `n`:

### Step 1

Start at:

```text
i = 0
```

### Step 2

Assume:

```python
min_index = i
```

### Step 3

Search the remaining unsorted portion:

```text
i+1 → n-1
```

### Step 4

Whenever a smaller element is found:

```python
min_index = j
```

### Step 5

After finding the minimum:

```python
swap(arr[i], arr[min_index])
```

### Step 6

Move to:

```text
i + 1
```

Repeat.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def selection_sort(arr):

    n = len(arr)

    for i in range(n - 1):

        # Assume current position contains minimum
        min_index = i

        # Find smaller element in remaining array
        for j in range(i + 1, n):

            if arr[j] < arr[min_index]:
                min_index = j

        # Put minimum at correct position
        arr[i], arr[min_index] = arr[min_index], arr[i]

    return arr


arr = [64, 25, 12, 22, 11]

answer = selection_sort(arr)

print(answer)
```

### Output

```text
[11, 12, 22, 25, 64]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static void selectionSort(int[] arr) {

        int n = arr.length;

        for (int i = 0; i < n - 1; i++) {

            // Assume current position has minimum
            int minIndex = i;

            // Search remaining unsorted portion
            for (int j = i + 1; j < n; j++) {

                if (arr[j] < arr[minIndex]) {
                    minIndex = j;
                }
            }

            // Put minimum at correct position
            int temp = arr[i];
            arr[i] = arr[minIndex];
            arr[minIndex] = temp;
        }
    }

    public static void main(String[] args) {

        int[] arr = {64, 25, 12, 22, 11};

        selectionSort(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text
[11, 12, 22, 25, 64]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[64,25,12,22,11]
```

## Pass 1 — `i = 0`

Unsorted:

```text
[64,25,12,22,11]
```

Find minimum:

```text
11
```

`min_index = 4`

Swap:

```text
[11,25,12,22,64]
```

Now:

```text
11
```

is permanently sorted.

---

## Pass 2 — `i = 1`

Unsorted:

```text
[25,12,22,64]
```

Minimum:

```text
12
```

Swap:

```text
[11,12,25,22,64]
```

---

## Pass 3 — `i = 2`

Unsorted:

```text
[25,22,64]
```

Minimum:

```text
22
```

Swap:

```text
[11,12,22,25,64]
```

---

## Pass 4 — `i = 3`

Unsorted:

```text
[25,64]
```

Minimum:

```text
25
```

No meaningful change.

Final:

```text
[11,12,22,25,64]
```

### Full trace

| Pass | Minimum | Array              |
| ---- | ------: | ------------------ |
| 1    |      11 | `[11,25,12,22,64]` |
| 2    |      12 | `[11,12,25,22,64]` |
| 3    |      22 | `[11,12,22,25,64]` |
| 4    |      25 | `[11,12,22,25,64]` |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows the same process.

Initial:

```text
[64,25,12,22,11]
```

### `i = 0`

Minimum = `11`

```text
[11,25,12,22,64]
```

### `i = 1`

Minimum = `12`

```text
[11,12,25,22,64]
```

### `i = 2`

Minimum = `22`

```text
[11,12,22,25,64]
```

### `i = 3`

Minimum = `25`

Final:

```text
[11,12,22,25,64]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

For each position we search the remaining elements.

Number of comparisons:

```text
(n-1) + (n-2) + ... + 1
```

This equals:

```text
n(n-1)/2
```

Therefore:

```text
O(n²)
```

### Best case

Even if already sorted:

```text
[1,2,3,4,5]
```

Selection Sort still searches for the minimum in every remaining section.

So:

```text
Best = O(n²)
```

### Average

```text
O(n²)
```

### Worst

```text
O(n²)
```

### Space

Only a few variables:

```text
O(1)
```

### Important characteristic

Selection Sort performs at most approximately:

```text
n - 1
```

swaps.

That's much fewer swaps than naive Bubble Sort.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is Selection Sort called Selection Sort?

Because every pass **selects** the minimum remaining element.

---

### Q2. Does an already sorted array make Selection Sort O(n)?

❌ No.

It still performs the comparisons.

Therefore:

```text
O(n²)
```

even in the best case.

---

### Q3. What is the advantage over Bubble Sort?

Selection Sort performs relatively few swaps:

```text
O(n)
```

maximum swaps.

---

### Q4. Is Selection Sort used for large production datasets?

Generally no.

Its:

```text
O(n²)
```

time complexity makes it unsuitable for large inputs.

Its value here is understanding fundamental sorting mechanics.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Recognition:

> Sort by repeatedly finding the minimum remaining element.

Think:

```text
Selection Sort
```

Master template:

```python
for i in range(n - 1):

    min_index = i

    for j in range(i + 1, n):

        if arr[j] < arr[min_index]:
            min_index = j

    swap(i, min_index)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Updating the array immediately whenever you find a smaller value.

Selection Sort should first find the **minimum index**, then swap.

### ❌ Mistake 2

Searching from index `0` every time.

After position `i`, everything before `i` is sorted.

### ❌ Mistake 3

Confusing:

```python
min_index
```

with:

```python
arr[min_index]
```

One is an index, the other is the value.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Selection Sort = Find minimum → swap into current position.**

```text
Best     O(n²)
Average  O(n²)
Worst    O(n²)
Space    O(1)
```

No exact standalone LC match.

---

# 🟦 PROBLEM 65 — INSERTION SORT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Insertion Sort is much more interesting than Selection Sort.

Its mental model is:

> **Build a sorted section one element at a time.**

Think about sorting playing cards in your hand.

You have:

```text
[2,5,8]
```

Then receive:

```text
4
```

You don't completely reorder everything.

You insert `4` into the correct location:

```text
[2,4,5,8]
```

That's exactly what Insertion Sort does.

### Exact LeetCode match

❌ No exact canonical standalone LeetCode problem for basic Insertion Sort.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
[5,3,4,1,2]
```

Initially:

```text
[5] | [3,4,1,2]
```

`5` is considered sorted.

Take `3`.

Insert it before `5`:

```text
[3,5] | [4,1,2]
```

Take `4`.

Insert into sorted section:

```text
[3,4,5] | [1,2]
```

Continue.

Final:

```text
[1,2,3,4,5]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

At each position:

```text
key = current element
```

Move larger elements one position to the right until the correct position for `key` is found.

Example:

```text
[2,5,8,10,4]
             ↑
            key
```

Compare `4` with `10`.

`10 > 4`, shift:

```text
[2,5,8,10,10]
```

Compare `4` with `8`.

Shift:

```text
[2,5,8,8,10]
```

Compare `4` with `5`.

Shift:

```text
[2,5,5,8,10]
```

Compare `4` with `2`.

Stop.

Insert:

```text
[2,4,5,8,10]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Start from index `1`.

Why?

The first element is trivially sorted.

### Step 2

Store:

```python
key = arr[i]
```

### Step 3

Set:

```python
j = i - 1
```

### Step 4

While:

```python
j >= 0
```

and:

```python
arr[j] > key
```

shift:

```python
arr[j + 1] = arr[j]
```

### Step 5

Move:

```python
j -= 1
```

### Step 6

Insert:

```python
arr[j + 1] = key
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def insertion_sort(arr):

    n = len(arr)

    # Start from second element
    for i in range(1, n):

        key = arr[i]

        # Previous element
        j = i - 1

        # Shift larger elements to the right
        while j >= 0 and arr[j] > key:

            arr[j + 1] = arr[j]

            j -= 1

        # Insert key at correct position
        arr[j + 1] = key

    return arr


arr = [5, 3, 4, 1, 2]

answer = insertion_sort(arr)

print(answer)
```

### Output

```text
[1, 2, 3, 4, 5]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static void insertionSort(int[] arr) {

        int n = arr.length;

        for (int i = 1; i < n; i++) {

            int key = arr[i];

            int j = i - 1;

            // Shift larger elements right
            while (j >= 0 && arr[j] > key) {

                arr[j + 1] = arr[j];

                j--;
            }

            // Insert key
            arr[j + 1] = key;
        }
    }

    public static void main(String[] args) {

        int[] arr = {5, 3, 4, 1, 2};

        insertionSort(arr);

        System.out.println(Arrays.toString(arr));
    }
}
```

### Output

```text
[1, 2, 3, 4, 5]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[5,3,4,1,2]
```

---

## Pass 1

```text
i = 1
key = 3
```

Sorted portion:

```text
[5]
```

Since:

```text
5 > 3
```

shift:

```text
[5,5,4,1,2]
```

Insert `3`:

```text
[3,5,4,1,2]
```

---

## Pass 2

```text
key = 4
```

Sorted portion:

```text
[3,5]
```

`5 > 4`

Shift:

```text
[3,5,5,1,2]
```

Insert:

```text
[3,4,5,1,2]
```

---

## Pass 3

```text
key = 1
```

Sorted portion:

```text
[3,4,5]
```

Shift `5`:

```text
[3,4,5,5,2]
```

Shift `4`:

```text
[3,4,4,5,2]
```

Shift `3`:

```text
[3,3,4,5,2]
```

Insert `1`:

```text
[1,3,4,5,2]
```

---

## Pass 4

```text
key = 2
```

Sorted portion:

```text
[1,3,4,5]
```

Shift `5`:

```text
[1,3,4,5,5]
```

Shift `4`:

```text
[1,3,4,4,5]
```

Shift `3`:

```text
[1,3,3,4,5]
```

Insert `2`:

```text
[1,2,3,4,5]
```

---

# 🔥 DRY-RUN TABLE

|  i | key | Sorted prefix after insertion |
| -: | --: | ----------------------------- |
|  1 |   3 | `[3,5]`                       |
|  2 |   4 | `[3,4,5]`                     |
|  3 |   1 | `[1,3,4,5]`                   |
|  4 |   2 | `[1,2,3,4,5]`                 |

The important concept is:

> **The left side is always sorted.**

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs the same shifting process.

Initial:

```text
[5,3,4,1,2]
```

After inserting `3`:

```text
[3,5,4,1,2]
```

After inserting `4`:

```text
[3,4,5,1,2]
```

After inserting `1`:

```text
[1,3,4,5,2]
```

After inserting `2`:

```text
[1,2,3,4,5]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

## Best case

Already sorted:

```text
[1,2,3,4,5]
```

Each element requires only one comparison.

Total:

```text
O(n)
```

### Average case

Elements need some shifting:

```text
O(n²)
```

### Worst case

Reverse sorted:

```text
[5,4,3,2,1]
```

Every new element must move across almost the entire sorted prefix.

Number of shifts is approximately:

```text
1 + 2 + 3 + ... + (n-1)
```

which is:

```text
n(n-1)/2
```

Therefore:

```text
O(n²)
```

### Space

Only `key`, `i`, `j`:

```text
O(1)
```

### Final

```text
Best     O(n)
Average  O(n²)
Worst    O(n²)
Space    O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is Insertion Sort good for nearly sorted arrays?

Because if elements are already close to their correct positions, very few shifts are required.

It can approach:

```text
O(n)
```

in the best/already-sorted case.

---

### Q2. What is the main difference between Selection and Insertion Sort?

Selection:

```text
Find minimum → swap
```

Insertion:

```text
Take current element → shift larger elements → insert
```

---

### Q3. Is Insertion Sort stable?

✅ Yes, when implemented with:

```python
arr[j] > key
```

rather than moving equal elements unnecessarily.

---

### Q4. Is Insertion Sort useful in production?

It can be useful for **small or nearly sorted collections**, but it is not the general choice for large unsorted datasets.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Recognition:

> Maintain a sorted prefix and insert each new element into it.

Think:

# INSERTION SORT

Mental template:

```python
for i in range(1, n):

    key = arr[i]
    j = i - 1

    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
        j -= 1

    arr[j + 1] = key
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Overwriting `key`.

You must save:

```python
key = arr[i]
```

before shifting.

### ❌ Mistake 2

Forgetting:

```python
j -= 1
```

This causes an infinite loop.

### ❌ Mistake 3

Inserting at:

```python
arr[j]
```

instead of:

```python
arr[j + 1]
```

After the loop, `j` has moved one position too far left.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Insertion Sort = Build a sorted prefix by inserting each new element.**

```text
Best     O(n)
Average  O(n²)
Worst    O(n²)
Space    O(1)
```

No exact standalone LC match.

---

# 🟦 PROBLEM 66 — MERGE TWO SORTED ARRAYS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem connects directly to a major DSA pattern:

# 🔥 TWO-POINTER MERGE

You already encountered this pattern in **Problem 51**.

Now we're deliberately repeating it because this pattern is extremely important.

### Example

```text
A = [1,3,5,7]
B = [2,4,6,8]
```

Both arrays are already sorted.

We don't need to sort the combined array.

Instead:

```text
1 vs 2 → take 1
3 vs 2 → take 2
3 vs 4 → take 3
5 vs 4 → take 4
...
```

Result:

```text
[1,2,3,4,5,6,7,8]
```

### LeetCode mapping

🔥 **LC 88 — Merge Sorted Array — Easy**

However, our CR2 problem is the **general "merge two sorted arrays" version**.

So:

> **Related/core LeetCode match, but not an exact statement match.**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two sorted arrays:

```text
A = [1,4,7]
B = [2,3,6,8]
```

Merge them into:

```text
[1,2,3,4,6,7,8]
```

### Important property

Both inputs are already sorted.

That is what makes the two-pointer solution possible.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Use:

```text
i → A
j → B
```

Initially:

```text
i = 0
j = 0
```

Compare:

```text
A[i]
B[j]
```

Take the smaller value.

### Example

```text
A = [1,4,7]
B = [2,3,6,8]
```

Compare:

```text
1 vs 2
```

Take:

```text
1
```

Move `i`.

Now:

```text
4 vs 2
```

Take:

```text
2
```

Move `j`.

Continue.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create result:

```python
result = []
```

### Step 2

Initialize:

```python
i = 0
j = 0
```

### Step 3

While both arrays still have elements:

```python
while i < len(A) and j < len(B):
```

### Step 4

Compare:

```python
A[i] <= B[j]
```

If true:

```python
result.append(A[i])
i += 1
```

Otherwise:

```python
result.append(B[j])
j += 1
```

### Step 5

One array may have remaining elements.

Append them.

```python
result.extend(A[i:])
result.extend(B[j:])
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def merge_sorted_arrays(a, b):

    result = []

    i = 0
    j = 0

    # Compare elements while both arrays have values
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
b = [2, 3, 6, 8]

answer = merge_sorted_arrays(a, b)

print(answer)
```

### Output

```text
[1, 2, 3, 4, 6, 7, 8]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int[] mergeSortedArrays(int[] a, int[] b) {

        int[] result = new int[a.length + b.length];

        int i = 0;
        int j = 0;
        int k = 0;

        // Compare while both arrays have elements
        while (i < a.length && j < b.length) {

            if (a[i] <= b[j]) {

                result[k] = a[i];

                i++;
                k++;

            } else {

                result[k] = b[j];

                j++;
                k++;
            }
        }

        // Remaining elements from a
        while (i < a.length) {

            result[k] = a[i];

            i++;
            k++;
        }

        // Remaining elements from b
        while (j < b.length) {

            result[k] = b[j];

            j++;
            k++;
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 4, 7};
        int[] b = {2, 3, 6, 8};

        int[] answer = mergeSortedArrays(a, b);

        System.out.println(Arrays.toString(answer));
    }
}
```

### Output

```text
[1, 2, 3, 4, 6, 7, 8]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
A = [1,4,7]
B = [2,3,6,8]
```

Start:

```text
i = 0
j = 0
result = []
```

### Step 1

Compare:

```text
1 vs 2
```

Take `1`.

```text
result = [1]
i = 1
```

---

### Step 2

Compare:

```text
4 vs 2
```

Take `2`.

```text
result = [1,2]
j = 1
```

---

### Step 3

Compare:

```text
4 vs 3
```

Take `3`.

```text
result = [1,2,3]
j = 2
```

---

### Step 4

Compare:

```text
4 vs 6
```

Take `4`.

```text
result = [1,2,3,4]
i = 2
```

---

### Step 5

Compare:

```text
7 vs 6
```

Take `6`.

```text
result = [1,2,3,4,6]
j = 3
```

---

### Step 6

Compare:

```text
7 vs 8
```

Take `7`.

```text
result = [1,2,3,4,6,7]
i = 3
```

Array `A` is finished.

Remaining `B`:

```text
[8]
```

Append:

```text
[1,2,3,4,6,7,8]
```

---

# 🔥 FULL TRACE TABLE

| Step | `A[i]` | `B[j]` | Take | Result            |
| ---: | -----: | -----: | ---: | ----------------- |
|    1 |      1 |      2 |    1 | `[1]`             |
|    2 |      4 |      2 |    2 | `[1,2]`           |
|    3 |      4 |      3 |    3 | `[1,2,3]`         |
|    4 |      4 |      6 |    4 | `[1,2,3,4]`       |
|    5 |      7 |      6 |    6 | `[1,2,3,4,6]`     |
|    6 |      7 |      8 |    7 | `[1,2,3,4,6,7]`   |
|    7 |      — |      8 |    8 | `[1,2,3,4,6,7,8]` |

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

The Java pointers behave identically:

```text
i → A
j → B
k → result
```

Example:

```text
A = [1,4,7]
B = [2,3,6,8]
```

Pointer progression:

```text
1 vs 2 → A
4 vs 2 → B
4 vs 3 → B
4 vs 6 → A
7 vs 6 → B
7 vs 8 → A
remaining 8 → B
```

Final:

```text
[1,2,3,4,6,7,8]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
m = length of A
n = length of B
```

Every element is processed exactly once.

Therefore:

```text
m + n
```

operations approximately.

### Time

```text
O(m + n)
```

### Output Space

The merged array contains:

```text
m + n
```

elements.

Therefore:

```text
O(m + n)
```

space is required for the returned result.

### Important distinction

The **auxiliary working space excluding the output** is:

```text
O(1)
```

But because we must return/store the merged array:

```text
Output space = O(m+n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why don't we concatenate and sort?

You could:

```python
sorted(a + b)
```

but that costs:

```text
O((m+n) log(m+n))
```

The arrays are already sorted, so throwing away that information is wasteful.

Two-pointer merge gives:

```text
O(m+n)
```

---

### Q2. Why does the two-pointer method work?

Because both arrays are sorted.

The smallest unprocessed element must be either:

```text
A[i]
```

or:

```text
B[j]
```

So comparing those two is sufficient.

---

### Q3. What happens when one array finishes first?

Append the remaining elements from the other array.

---

### Q4. What if both arrays contain duplicates?

No problem.

Example:

```text
A = [1,2,2]
B = [2,2,3]
```

Result:

```text
[1,2,2,2,2,3]
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 TWO-POINTER MERGE

Recognition trigger:

> **Two sorted sequences need to be combined.**

Think:

```text
i → first array
j → second array

compare
take smaller
advance that pointer
```

This pattern is foundational for:

* Merge Sort
* LC88
* merging intervals/data streams
* comparing sorted datasets
* external data processing

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Sorting the combined array.

Works functionally, but misses the intended `O(m+n)` solution.

### ❌ Mistake 2

Forgetting leftover elements.

One array will usually finish before the other.

### ❌ Mistake 3

Incrementing both pointers after every comparison.

Only advance the pointer whose element was selected.

### ❌ Mistake 4

Confusing this with LC88's exact implementation.

LC88 specifically provides a first array with extra space at the end and asks you to modify it in-place.

Our CR2 version is the general merge-two-sorted-arrays problem.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Two sorted arrays → compare their current elements → take smaller → move that pointer.**

```text
Time  → O(m+n)
Output Space → O(m+n)
Auxiliary Space → O(1)
```

🔥 **LC 88 — Merge Sorted Array — Easy** is the closest/core LeetCode match, but this CR2 formulation is not exactly the same statement.

---

# 🏆 DAY 7 — SESSION 2 MASTER CONNECTION

You now have three sorting/merge patterns:

| Problem                    | Pattern        | Mental Trigger           |
| -------------------------- | -------------- | ------------------------ |
| **64 Selection Sort**      | Select Minimum | `find min → swap`        |
| **65 Insertion Sort**      | Sorted Prefix  | `shift → insert`         |
| **66 Merge Sorted Arrays** | Two Pointers   | `compare → take smaller` |

---

# 🧠 SORTING PATTERN CHEAT SHEET

## 64 — Selection Sort

```text
[sorted | unsorted]

Find minimum in unsorted
↓
Swap into sorted position
```

```text
O(n²) time
O(1) space
```

---

## 65 — Insertion Sort

```text
[sorted | current | unsorted]

Save current
↓
Shift larger values right
↓
Insert current
```

```text
Best: O(n)
Worst: O(n²)
Space: O(1)
```

---

## 66 — Merge

```text
A → i
B → j

Compare A[i] and B[j]
↓
Take smaller
↓
Advance one pointer
```

```text
O(m+n)
```

---

# 🔥 THE THREE SORTING ALGORITHMS YOU NOW KNOW

### Bubble Sort

```text
Adjacent comparison
→ swap
→ largest bubbles right
```

### Selection Sort

```text
Find minimum
→ swap into position
```

### Insertion Sort

```text
Take current
→ shift larger elements
→ insert
```

### Merge

```text
Two sorted arrays
→ compare front elements
→ merge
```

---

# 🧪 SESSION 2 — NO-SOLUTION MASTER TEST

Don't look back at the code.

## Test 1 — Selection Sort

```text
arr = [29, 10, 14, 37, 13]
```

Expected:

```text
[10,13,14,29,37]
```

---

## Test 2 — Insertion Sort

```text
arr = [8,5,2,9,1]
```

Expected:

```text
[1,2,5,8,9]
```

---

## Test 3 — Merge

```text
A = [1,5,9]
B = [2,3,7,10]
```

Expected:

```text
[1,2,3,5,7,9,10]
```

---

# 🎯 REPRODUCTION DRILL

Write these from memory.

### Selection Sort

```python
for i in range(n - 1):
    min_index = i

    for j in range(i + 1, n):
        if arr[j] < arr[min_index]:
            min_index = j

    arr[i], arr[min_index] = arr[min_index], arr[i]
```

### Insertion Sort

```python
for i in range(1, n):
    key = arr[i]
    j = i - 1

    while j >= 0 and arr[j] > key:
        arr[j + 1] = arr[j]
        j -= 1

    arr[j + 1] = key
```

### Merge

```python
while i < len(a) and j < len(b):

    if a[i] <= b[j]:
        result.append(a[i])
        i += 1
    else:
        result.append(b[j])
        j += 1
```

---

# 📊 CR2 PROGRESS

```text
DAY 1  ██████████  10/10
DAY 2  ██████████  10/10
DAY 3  ██████████  10/10
DAY 4  ██████████  10/10
DAY 5  ██████████  10/10
DAY 6  ██████████  10/10
DAY 7  ██████░░░░  6/10
```

# 🟢 OVERALL: 66 / 100

### Day 7 completed so far

```text
61 ✅ Linear Search
62 ✅ Binary Search — LC704
63 ✅ Bubble Sort
64 ✅ Selection Sort
65 ✅ Insertion Sort
66 ✅ Merge Two Sorted Arrays — LC88 related
```

### Next locked sequence

# 🔥 DAY 7 — SESSION 3

## Problems 67–70

**67. Kth Largest Element Using Sorting — LC 215 — Medium**
**68. Sort Characters by Frequency — LC 451 — Medium**
**69. Assign Cookies — LC 455 — Easy**
**70. Minimum Coins — Greedy — No exact canonical LC**

That session will close **Day 7** and introduce the transition from basic sorting into **greedy problem recognition**.

Would you like to try the three no-solution master tests first, or move straight to Day 7 — Session 3?

# 🔥 CR2 — DAY 7 — SESSION 3

## Problems 67–70 | Sorting + Frequency + Greedy

This is the **final session of Day 7**.

| #      | Problem                      | LeetCode                                                 | Difficulty | Core Pattern          |
| ------ | ---------------------------- | -------------------------------------------------------- | ---------- | --------------------- |
| **67** | Kth Largest Using Sorting    | **LC 215 — Kth Largest Element in an Array**             | Medium     | Sorting / Selection   |
| **68** | Sort Characters by Frequency | **LC 451 — Sort Characters By Frequency**                | Medium     | HashMap + Sorting     |
| **69** | Assign Cookies               | **LC 455 — Assign Cookies**                              | Easy       | Greedy + Two Pointers |
| **70** | Minimum Coins                | No exact canonical LC match for the basic greedy version | —          | Greedy                |

# 🎯 Session Goal

By the end of this session, recognize:

```text
Kth largest
    ↓
Sort / selection

Frequency + ordering by frequency
    ↓
HashMap + sorting

Maximize satisfied assignments
    ↓
Greedy + two pointers

Use largest useful denomination first
    ↓
Greedy
```

---

# 🟦 PROBLEM 67 — KTH LARGEST ELEMENT USING SORTING

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem teaches an important distinction:

> **Kth largest is not necessarily the same as finding the maximum repeatedly.**

Example:

```text
nums = [3,2,1,5,6,4]
k = 2
```

Sorted descending:

```text
[6,5,4,3,2,1]
```

The 2nd largest is:

```text
5
```

### Exact LeetCode

🔥 **LC 215 — Kth Largest Element in an Array — Medium**

The CR2 problem specifically says **using sorting**, so we will intentionally use sorting.

### Senior note

LC215 also has more advanced solutions using:

* Quickselect
* Heap

But for this CR2 problem, don't overcomplicate it.

The goal is:

> **Understand the problem and solve it cleanly with sorting.**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
nums = [3,2,1,5,6,4]
k = 2
```

Find the element that would appear at position `k` if the array were sorted from largest to smallest.

Descending:

```text
6 → 1st largest
5 → 2nd largest
4 → 3rd largest
3 → 4th largest
2 → 5th largest
1 → 6th largest
```

Answer:

```text
5
```

### Important

This problem does **not** ask for the index.

It asks for the **value**.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

The easiest approach:

### Step 1

Sort the array.

Ascending:

```text
[1,2,3,4,5,6]
```

### Step 2

The kth largest is located at:

```text
n - k
```

Why?

For:

```text
n = 6
k = 2
```

Index:

```text
6 - 2 = 4
```

And:

```text
nums[4] = 5
```

So:

```python
answer = nums[n-k]
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Given:

```text
nums
k
```

### Step 1

Find:

```text
n = len(nums)
```

### Step 2

Sort ascending.

### Step 3

Calculate:

```text
index = n - k
```

### Step 4

Return:

```text
nums[index]
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def kth_largest(nums, k):

    # Sort in ascending order
    nums.sort()

    n = len(nums)

    # kth largest is at index n - k
    return nums[n - k]


nums = [3, 2, 1, 5, 6, 4]
k = 2

answer = kth_largest(nums, k)

print("Kth largest:", answer)
```

### Output

```text
Kth largest: 5
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int kthLargest(int[] nums, int k) {

        Arrays.sort(nums);

        int n = nums.length;

        return nums[n - k];
    }

    public static void main(String[] args) {

        int[] nums = {3, 2, 1, 5, 6, 4};

        int k = 2;

        int answer = kthLargest(nums, k);

        System.out.println("Kth largest: " + answer);
    }
}
```

### Output

```text
Kth largest: 5
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [3,2,1,5,6,4]
k = 2
```

### Step 1 — Sort

Before:

```text
[3,2,1,5,6,4]
```

After:

```text
[1,2,3,4,5,6]
```

### Step 2 — Find index

```text
n = 6
k = 2

index = n - k
      = 6 - 2
      = 4
```

### Step 3

```text
nums[4] = 5
```

Answer:

```text
5
```

### Visual

```text
Index:   0  1  2  3  4  5
         ↓  ↓  ↓  ↓  ↓  ↓
Array:  [1, 2, 3, 4, 5, 6]
                    ↑
                 2nd largest
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java:

```text
nums = [3,2,1,5,6,4]
```

After:

```text
Arrays.sort(nums)
```

we have:

```text
[1,2,3,4,5,6]
```

Then:

```text
n = 6
k = 2

n-k = 4
```

Therefore:

```text
nums[4] = 5
```

Return `5`.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Sorting takes:

```text
O(n log n)
```

Then accessing:

```text
nums[n-k]
```

takes:

```text
O(1)
```

Total:

```text
O(n log n) + O(1)
= O(n log n)
```

### Space

This depends on the language/library's sorting implementation.

For CR2 algorithm analysis, the important comparison is:

```text
Time → O(n log n)
```

The array is sorted in place in Python's `list.sort()` and Java's primitive `Arrays.sort(int[])`, though implementation-level auxiliary memory details differ.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is the index `n-k`?

Because ascending order places the largest element at:

```text
n-1
```

So:

```text
1st largest → n-1
2nd largest → n-2
3rd largest → n-3
```

Therefore:

```text
kth largest → n-k
```

---

### Q2. What if `k = 1`?

```text
n - 1
```

which is the last element.

That's the maximum.

---

### Q3. What if `k = n`?

```text
n - n = 0
```

which is the minimum.

---

### Q4. Is sorting the fastest possible approach?

Not necessarily.

LC215 can be solved using Quickselect in average:

```text
O(n)
```

But that is beyond this CR2 problem's requested sorting approach.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Recognition:

> Find kth largest/smallest and sorting is allowed.

Think:

```text
sort
↓
convert rank to index
```

For ascending:

```text
kth largest → n-k
```

For 1-indexed kth smallest:

```text
kth smallest → k-1
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
nums[k]
```

for kth largest.

Wrong.

### ❌ Mistake 2

Forgetting zero-based indexing.

### ❌ Mistake 3

Confusing kth largest with kth distinct largest.

LC215 allows duplicates.

Example:

```text
[3,3,2]
```

The 2nd largest is:

```text
3
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Kth largest + sorting → sort ascending → return `nums[n-k]`.**

```text
Time → O(n log n)
```

🔥 **LC 215 — Medium**

---

# 🟦 PROBLEM 68 — SORT CHARACTERS BY FREQUENCY

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we're combining two patterns you've already learned:

```text
HashMap / Dictionary
        +
Sorting
```

Given:

```text
s = "tree"
```

Frequencies:

```text
t → 1
r → 1
e → 2
```

Sort characters by frequency:

```text
"eert"
```

or:

```text
"eetr"
```

Both satisfy the frequency requirement.

### Exact LeetCode

🔥 **LC 451 — Sort Characters By Frequency — Medium**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, rearrange its characters so that characters with higher frequency appear first.

Example:

```text
s = "cccaaa"
```

Frequency:

```text
c → 3
a → 3
```

Possible answer:

```text
"cccaaa"
```

or:

```text
"aaaccc"
```

Both have frequency groups correctly arranged.

### Another example

```text
s = "Aabb"
```

Frequencies:

```text
A → 1
a → 1
b → 2
```

Possible result:

```text
"bbAa"
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Break the problem into two stages.

## Stage 1 — Count

Use a dictionary:

```python
frequency = {}
```

For:

```text
"tree"
```

we get:

```text
{
    't': 1,
    'r': 1,
    'e': 2
}
```

## Stage 2 — Sort

Sort the characters according to their frequency in descending order.

```text
e → 2
t → 1
r → 1
```

Then repeat each character its frequency number of times:

```text
e × 2 → "ee"
t × 1 → "t"
r × 1 → "r"
```

Result:

```text
"eetr"
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create frequency map.

### Step 2

Count every character.

### Step 3

Sort the `(character, frequency)` pairs by frequency descending.

### Step 4

For each pair:

```python
character * frequency
```

### Step 5

Join everything.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def frequency_sort(s):

    frequency = {}

    # Count frequency of every character
    for ch in s:
        frequency[ch] = frequency.get(ch, 0) + 1

    # Sort by frequency in descending order
    sorted_chars = sorted(
        frequency.items(),
        key=lambda item: item[1],
        reverse=True
    )

    result = []

    # Repeat each character according to its frequency
    for ch, count in sorted_chars:
        result.append(ch * count)

    return ''.join(result)


s = "tree"

answer = frequency_sort(s)

print(answer)
```

### Output

One valid output:

```text
eert
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static String frequencySort(String s) {

        HashMap<Character, Integer> frequency = new HashMap<>();

        // Count characters
        for (char ch : s.toCharArray()) {
            frequency.put(ch, frequency.getOrDefault(ch, 0) + 1);
        }

        // Convert map entries to list
        List<Map.Entry<Character, Integer>> entries =
                new ArrayList<>(frequency.entrySet());

        // Sort by frequency descending
        entries.sort((a, b) ->
                Integer.compare(b.getValue(), a.getValue())
        );

        StringBuilder result = new StringBuilder();

        // Build result
        for (Map.Entry<Character, Integer> entry : entries) {

            char ch = entry.getKey();
            int count = entry.getValue();

            for (int i = 0; i < count; i++) {
                result.append(ch);
            }
        }

        return result.toString();
    }

    public static void main(String[] args) {

        String s = "tree";

        String answer = frequencySort(s);

        System.out.println(answer);
    }
}
```

### Output

```text
eert
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
s = "tree"
```

### Frequency counting

Start:

```text
{}
```

Read `t`:

```text
{'t': 1}
```

Read `r`:

```text
{'t': 1, 'r': 1}
```

Read `e`:

```text
{'t': 1, 'r': 1, 'e': 1}
```

Read `e` again:

```text
{'t': 1, 'r': 1, 'e': 2}
```

### Sort by frequency

Before:

```text
t → 1
r → 1
e → 2
```

After descending frequency:

```text
e → 2
t → 1
r → 1
```

### Build

```text
e × 2 → "ee"
t × 1 → "t"
r × 1 → "r"
```

Final:

```text
"eetr"
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java builds:

```text
frequency:
e → 2
t → 1
r → 1
```

Sort entries:

```text
e(2)
t(1)
r(1)
```

Build:

```text
ee
eet
eetr
```

Final:

```text
eetr
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
k = number of distinct characters
```

### Frequency counting

Every character is visited once:

```text
O(n)
```

### Sorting distinct characters

There are `k` distinct characters:

```text
O(k log k)
```

### Building result

Every character is output exactly once:

```text
O(n)
```

Total:

```text
O(n + k log k)
```

Since:

```text
k <= n
```

worst case:

```text
O(n log n)
```

### Space

Frequency map:

```text
O(k)
```

Output:

```text
O(n)
```

Therefore total including output:

```text
O(n + k)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a HashMap?

We need to know how many times each character appears.

---

### Q2. Why sort the map entries?

Because we need characters ordered by frequency.

---

### Q3. Can two characters have the same frequency?

Yes.

Their relative order can generally be arbitrary unless the problem specifies a tie-breaker.

---

### Q4. What is the difference between this and normal character sorting?

Normal sorting orders by character value.

Here we order by:

```text
frequency
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is a very important compound pattern:

```text
COUNT
↓
STORE FREQUENCY
↓
SORT BY FREQUENCY
↓
BUILD RESULT
```

Recognition:

> "Most frequent", "sort by frequency", "top frequent"

Think:

```text
HashMap / Counter
+
Ordering
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Sorting characters alphabetically instead of by frequency.

### ❌ Mistake 2

Counting incorrectly.

### ❌ Mistake 3

Appending the character only once.

If:

```text
e → 3
```

you need:

```text
eee
```

### ❌ Mistake 4

Assuming one unique output when multiple tie-valid outputs exist.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Frequency Sort = Count → Sort by frequency → Rebuild.**

```text
Time → O(n + k log k)
Space → O(n + k) including output
```

🔥 **LC 451 — Medium**

---

# 🟦 PROBLEM 69 — ASSIGN COOKIES

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we enter the **Greedy** section.

This is one of the most important greedy ideas:

> **Use the smallest resource that can satisfy the smallest requirement.**

We have:

* children with greed factors
* cookies with sizes

A child is satisfied if:

```text
cookie_size >= greed_factor
```

### Exact LeetCode

🔥 **LC 455 — Assign Cookies — Easy**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Suppose:

```text
children = [1,2,3]
cookies = [1,1]
```

Child requirements:

```text
1
2
3
```

Cookie sizes:

```text
1
1
```

Only one child can be satisfied.

Answer:

```text
1
```

---

### Another example

```text
g = [1,2]
s = [1,2,3]
```

We can satisfy:

```text
child 1 ← cookie 1
child 2 ← cookie 2
```

Answer:

```text
2
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Sort both arrays.

Example:

```text
g = [1,2,3]
s = [1,1]
```

Already sorted.

Start with smallest child:

```text
child = 1
```

Smallest cookie:

```text
cookie = 1
```

Can cookie satisfy child?

```text
1 >= 1
```

Yes.

Assign it.

Now:

```text
child pointer → next child
cookie pointer → next cookie
```

Next:

```text
child = 2
cookie = 1
```

Not enough.

So use a larger cookie.

But there isn't one.

Stop.

Answer:

```text
1
```

### Why is this greedy strategy safe?

If the smallest cookie can satisfy the least-demanding child, using it there doesn't waste a larger cookie that might be needed for a more demanding child.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Sort greed factors:

```python
g.sort()
```

### Step 2

Sort cookie sizes:

```python
s.sort()
```

### Step 3

Use:

```text
i → children
j → cookies
```

### Step 4

If:

```text
cookie >= child's greed
```

assign:

```text
count += 1
i += 1
j += 1
```

### Step 5

Otherwise cookie is too small:

```text
j += 1
```

Try a larger cookie.

### Step 6

Stop when either:

```text
all children satisfied
```

or:

```text
no cookies remain
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def assign_cookies(g, s):

    # Sort children by greed
    g.sort()

    # Sort cookies by size
    s.sort()

    child = 0
    cookie = 0

    while child < len(g) and cookie < len(s):

        # Current cookie can satisfy current child
        if s[cookie] >= g[child]:

            child += 1
            cookie += 1

        # Cookie is too small
        else:

            cookie += 1

    return child


g = [1, 2, 3]
s = [1, 1]

answer = assign_cookies(g, s)

print("Satisfied children:", answer)
```

### Output

```text
Satisfied children: 1
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int assignCookies(int[] g, int[] s) {

        Arrays.sort(g);
        Arrays.sort(s);

        int child = 0;
        int cookie = 0;

        while (child < g.length && cookie < s.length) {

            // Cookie can satisfy child
            if (s[cookie] >= g[child]) {

                child++;
                cookie++;

            } else {

                // Cookie is too small
                cookie++;
            }
        }

        return child;
    }

    public static void main(String[] args) {

        int[] g = {1, 2, 3};
        int[] s = {1, 1};

        int answer = assignCookies(g, s);

        System.out.println("Satisfied children: " + answer);
    }
}
```

### Output

```text
Satisfied children: 1
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
g = [1,2,3]
s = [1,1]
```

Sorted:

```text
g = [1,2,3]
s = [1,1]
```

Initial:

```text
child = 0
cookie = 0
```

### Step 1

Child requirement:

```text
1
```

Cookie:

```text
1
```

Check:

```text
1 >= 1
```

Yes.

Satisfied:

```text
count = 1
```

Move both:

```text
child = 1
cookie = 1
```

---

### Step 2

Child:

```text
2
```

Cookie:

```text
1
```

Check:

```text
1 >= 2
```

False.

Cookie is useless for this child.

Move cookie:

```text
cookie = 2
```

No cookies remain.

Return:

```text
1
```

---

# 🔥 SECOND EXAMPLE

```text
g = [1,2]
s = [1,2,3]
```

### Step 1

```text
1 >= 1
```

Satisfied.

### Step 2

```text
2 >= 2
```

Satisfied.

Answer:

```text
2
```

The third cookie isn't needed.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses the same two-pointer logic.

For:

```text
g = [1,2,3]
s = [1,1]
```

Pointer movement:

```text
1 >= 1 → assign
1 < 2  → discard cookie
```

Result:

```text
1
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
m = number of children
n = number of cookies
```

Sorting children:

```text
O(m log m)
```

Sorting cookies:

```text
O(n log n)
```

Two-pointer traversal:

```text
O(m+n)
```

Total:

```text
O(m log m + n log n)
```

The sorting terms dominate.

### Space

Ignoring the sorting implementation's internal memory:

```text
O(1)
```

extra algorithmic pointer space.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why assign the smallest suitable cookie?

Because a larger cookie may be useful for a more demanding child.

---

### Q2. Why sort both arrays?

Sorting allows us to make the greedy decision from smallest requirements/resources upward.

---

### Q3. Why skip a cookie when it is too small?

Because if it cannot satisfy the current smallest remaining child, it cannot satisfy any larger-demand child either.

So it can safely be discarded.

---

### Q4. What is the greedy principle?

> Make the locally safest choice that preserves resources for future choices.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Recognition trigger:

> Maximize the number of successful assignments/matches.

Think:

```text
Sort both
↓
Two pointers
↓
Use smallest sufficient resource
```

This is a classic greedy pattern.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Giving the largest cookie to the smallest child immediately.

It may waste a resource needed later.

### ❌ Mistake 2

Not sorting.

### ❌ Mistake 3

When cookie is too small, moving to the next child.

Wrong.

The child still needs a cookie.

You should move to a **larger cookie**.

### ❌ Mistake 4

Counting cookies rather than successfully satisfied children.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Assign Cookies = Sort requirements + sort resources + smallest sufficient resource.**

```text
Time → O(m log m + n log n)
Space → O(1) auxiliary
```

🔥 **LC 455 — Easy**

---

# 🟦 PROBLEM 70 — MINIMUM COINS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is our introduction to a very common greedy pattern:

# 🔥 TAKE THE LARGEST USEFUL DENOMINATION

Example:

```text
coins = [25,10,5,1]
amount = 63
```

Greedy:

```text
25 → remaining 38
25 → remaining 13
10 → remaining 3
1  → remaining 2
1  → remaining 1
1  → remaining 0
```

Coins:

```text
25 + 25 + 10 + 1 + 1 + 1
```

Number of coins:

```text
6
```

---

# ⚠️ VERY IMPORTANT

The greedy solution is **not universally optimal for arbitrary coin systems**.

For example:

```text
coins = [1,3,4]
amount = 6
```

Greedy:

```text
4 + 1 + 1
```

uses:

```text
3 coins
```

But optimal is:

```text
3 + 3
```

using:

```text
2 coins
```

Therefore:

> **Greedy works for some denomination systems, but not all.**

This is an extremely important interview concept.

### Exact LeetCode match

❌ No exact canonical LeetCode match for the basic **greedy minimum-coins** formulation.

⚠️ **LC 322 — Coin Change** is related, but it is a **Dynamic Programming** problem and should NOT be falsely labeled as an exact match for this greedy problem.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given denominations:

```text
coins = [25,10,5,1]
```

and:

```text
amount = 63
```

Find the minimum number of coins using the standard currency-style denominations.

We choose the largest denomination that does not exceed the remaining amount.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine you need to pay:

```text
₹63
```

and have:

```text
₹25, ₹10, ₹5, ₹1
```

If you use ₹1 repeatedly:

```text
63 × ₹1
```

you need:

```text
63 coins
```

Clearly inefficient.

Take the largest useful coin:

```text
₹25
```

Remaining:

```text
63 - 25 = 38
```

Again:

```text
38 - 25 = 13
```

Then:

```text
13 - 10 = 3
```

Then:

```text
3 × ₹1
```

So:

```text
25 + 25 + 10 + 1 + 1 + 1
```

uses:

```text
6 coins
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Assume denominations are suitable for greedy selection.

### Step 1

Sort coins descending.

```text
[25,10,5,1]
```

### Step 2

For each coin:

Determine how many times it can be used:

```python
count = amount // coin
```

### Step 3

Add that number to answer:

```python
coins_used += count
```

### Step 4

Reduce amount:

```python
amount %= coin
```

### Step 5

Continue with the next smaller denomination.

### Step 6

If amount becomes `0`, we're done.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def minimum_coins(coins, amount):

    # Largest denomination first
    coins.sort(reverse=True)

    count = 0

    for coin in coins:

        if coin <= amount:

            # Number of this coin we can use
            use = amount // coin

            count += use

            # Remaining amount
            amount %= coin

        # Stop once amount is zero
        if amount == 0:
            break

    # If amount is still non-zero, no solution exists
    if amount != 0:
        return -1

    return count


coins = [25, 10, 5, 1]
amount = 63

answer = minimum_coins(coins, amount)

print("Minimum coins:", answer)
```

### Output

```text
Minimum coins: 6
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

public class Main {

    public static int minimumCoins(int[] coins, int amount) {

        // Sort ascending first
        Arrays.sort(coins);

        int count = 0;

        // Traverse from largest to smallest
        for (int i = coins.length - 1; i >= 0; i--) {

            int coin = coins[i];

            if (coin <= amount) {

                int use = amount / coin;

                count += use;

                amount %= coin;
            }

            if (amount == 0) {
                break;
            }
        }

        // No exact solution
        if (amount != 0) {
            return -1;
        }

        return count;
    }

    public static void main(String[] args) {

        int[] coins = {25, 10, 5, 1};

        int amount = 63;

        int answer = minimumCoins(coins, amount);

        System.out.println("Minimum coins: " + answer);
    }
}
```

### Output

```text
Minimum coins: 6
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
coins = [25,10,5,1]
amount = 63
```

Already descending.

### Coin = 25

```text
63 // 25 = 2
```

Use:

```text
2 × 25 = 50
```

Remaining:

```text
63 % 25 = 13
```

Coins used:

```text
2
```

---

### Coin = 10

```text
13 // 10 = 1
```

Use:

```text
1 × 10
```

Remaining:

```text
3
```

Coins:

```text
3
```

---

### Coin = 5

```text
3 // 5 = 0
```

Use none.

Remaining:

```text
3
```

---

### Coin = 1

```text
3 // 1 = 3
```

Use:

```text
3 × 1
```

Remaining:

```text
0
```

Total:

```text
2 + 1 + 3 = 6
```

Final answer:

```text
6
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows the same process.

```text
amount = 63
```

### 25

```text
63 / 25 = 2
63 % 25 = 13
```

### 10

```text
13 / 10 = 1
13 % 10 = 3
```

### 5

```text
3 / 5 = 0
```

### 1

```text
3 / 1 = 3
3 % 1 = 0
```

Total:

```text
6
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
k = number of denominations
```

Sorting costs:

```text
O(k log k)
```

Then we scan the denominations:

```text
O(k)
```

Total:

```text
O(k log k)
```

If denominations are already provided in descending order, the greedy scan itself is:

```text
O(k)
```

### Space

Only a few variables:

```text
O(1)
```

excluding the sorting implementation's internal memory.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Does greedy always produce the minimum number of coins?

❌ No.

This is extremely important.

Counterexample:

```text
coins = [1,3,4]
amount = 6
```

Greedy:

```text
4 + 1 + 1 = 3 coins
```

Optimal:

```text
3 + 3 = 2 coins
```

Therefore arbitrary coin systems require a different strategy, such as DP.

---

### Q2. When can greedy work?

It works for certain denomination systems, including common canonical currency systems such as:

```text
1,5,10,25
```

under the usual assumptions.

---

### Q3. What is the greedy decision?

At each step:

> Take the largest denomination that does not exceed the remaining amount.

---

### Q4. What happens if there is no `1` coin?

Example:

```text
coins = [5,10]
amount = 3
```

No exact solution exists.

Return:

```text
-1
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is your first basic greedy template:

```text
Sort descending
↓
Take largest useful choice
↓
Reduce remaining problem
↓
Repeat
```

### Recognition trigger

When a problem says:

> Minimize number of items while each larger item can safely replace multiple smaller items

consider greedy.

But **always verify that the greedy choice is actually valid for the given problem.**

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Assuming:

> Largest coin first always works.

False.

```text
[1,3,4], amount=6
```

proves it.

---

### ❌ Mistake 2

Calling LC322 an exact greedy match.

It isn't.

**LC322 Coin Change** is a different problem-solving approach involving DP.

---

### ❌ Mistake 3

Forgetting to reduce:

```python
amount %= coin
```

---

### ❌ Mistake 4

Using a coin larger than the remaining amount.

Only use:

```text
coin <= amount
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

> **Minimum Coins — basic greedy version = largest useful denomination first.**

But memorize the warning:

```text
Greedy ≠ universally optimal.
```

```text
Time → O(k log k) if sorting is required
Space → O(1) auxiliary
```

No exact canonical LeetCode match for this **greedy formulation**.

---

# 🏆 DAY 7 — SESSION 3 MASTER CONNECTION

You have now completed four different patterns:

| #      | Problem        | Pattern               | Recognition Trigger          |
| ------ | -------------- | --------------------- | ---------------------------- |
| **67** | Kth Largest    | Sorting + Rank        | `n-k`                        |
| **68** | Frequency Sort | HashMap + Sorting     | Count → Order                |
| **69** | Assign Cookies | Greedy + Two Pointers | Smallest sufficient resource |
| **70** | Minimum Coins  | Greedy                | Largest useful choice        |

---

# 🧠 DAY 7 — COMPLETE PATTERN CHEAT SHEET

## 🔵 SEARCH

### Linear Search

```text
Unsorted data
↓
Check sequentially
```

```text
O(n)
```

### Binary Search

```text
Sorted/orderable search space
↓
Discard half
```

```text
O(log n)
```

---

# 🟢 SORTING

### Bubble

```text
Adjacent comparison
↓
Swap
```

```text
O(n²)
```

### Selection

```text
Find minimum
↓
Swap
```

```text
O(n²)
```

### Insertion

```text
Sorted prefix
↓
Shift
↓
Insert
```

```text
Best O(n)
Worst O(n²)
```

### Merge

```text
Two sorted sequences
↓
Compare pointers
↓
Take smaller
```

```text
O(m+n)
```

---

# 🟡 HASHING + SORTING

### Frequency Sort

```text
Count
↓
Sort by frequency
↓
Build
```

---

# 🔴 GREEDY

### Assign Cookies

```text
Smallest requirement
+
Smallest sufficient resource
```

### Minimum Coins

```text
Largest useful denomination
```

⚠️ But always verify greedy correctness.

---

# 🔥 DAY 7 — FINAL NO-SOLUTION MASTER TEST

Do these without looking at the solutions.

## Test 67 — Kth Largest

```text
nums = [7,4,9,2,10,6]
k = 3
```

Expected:

```text
7
```

---

## Test 68 — Frequency Sort

```text
s = "abbccc"
```

Expected:

```text
"cccbb a"
```

Ignoring the displayed spacing:

```text
"cccbba"
```

---

## Test 69 — Assign Cookies

```text
g = [1,2,3]
s = [1,2]
```

Expected:

```text
2
```

---

## Test 70 — Minimum Coins

```text
coins = [25,10,5,1]
amount = 87
```

Expected:

```text
25 + 25 + 25 + 10 + 1 + 1
```

So:

```text
6 coins
```

---

# 🧪 CRITICAL GREEDY TRICK QUESTION

Before claiming that a greedy coin solution is optimal, test:

```text
coins = [1,3,4]
amount = 6
```

Greedy:

```text
4 + 1 + 1
```

→ `3 coins`

But:

```text
3 + 3
```

→ `2 coins`

Therefore:

# ❗ GREEDY FAILS HERE

This distinction is **interview-important**.

---

# 📊 CR2 PROGRESS — DAY 7 COMPLETE

```text
DAY 1  ██████████  10/10
DAY 2  ██████████  10/10
DAY 3  ██████████  10/10
DAY 4  ██████████  10/10
DAY 5  ██████████  10/10
DAY 6  ██████████  10/10
DAY 7  ██████████  10/10
```

# 🟢 OVERALL: 70 / 100

## 🎯 70% CR2 COMPLETE

### Day 7 completed:

```text
61 ✅ Linear Search
62 ✅ Binary Search — LC 704
63 ✅ Bubble Sort
64 ✅ Selection Sort
65 ✅ Insertion Sort
66 ✅ Merge Two Sorted Arrays — LC 88 related
67 ✅ Kth Largest — LC 215
68 ✅ Frequency Sort — LC 451
69 ✅ Assign Cookies — LC 455
70 ✅ Minimum Coins — Greedy
```

# 🔥 DAY 7 CORE TAKEAWAY

You should now recognize these patterns without hesitation:

```text
Find target in unsorted array
→ Linear Search

Find target in sorted array
→ Binary Search

Adjacent swap
→ Bubble Sort

Repeatedly select minimum
→ Selection Sort

Maintain sorted prefix
→ Insertion Sort

Two sorted arrays
→ Two-Pointer Merge

Kth largest + sorting
→ n-k

Frequency ordering
→ HashMap + Sort

Maximum assignments
→ Greedy + Two Pointers

Largest useful denomination
→ Greedy
```

**Next locked block: Day 8 — Session 1 → Problems 71–73: Frequency Map of Array, First Repeating Element, First Non-Repeating Element.**

Would you like to start Day 8 — Session 1 with Problem 71, or do the four Day 7 master tests first?


