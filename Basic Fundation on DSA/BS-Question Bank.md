#  LOCKED BINARY SEARCH QUESTION BANK (ML/MLOps TRACK)

This sequence is well-structured and covers the complete Binary Search progression from fundamentals to answer-space search.


# FINAL SYLLABUS

~~~

3. BINARY SEARCH — MUST MASTER

Binary Search deserves extremely high priority because interviewers can turn it into several different-looking problems.

### 🔴 P0

- **LC 704 — Binary Search**
- **LC 35 — Search Insert Position**
- **LC 34 — Find First and Last Position**
- **LC 153 — Find Minimum in Rotated Sorted Array**
- **LC 33 — Search in Rotated Sorted Array**

### 🟠 P1

- **LC 875 — Koko Eating Bananas**
- LC 74 — Search a 2D Matrix
- LC 69 — Sqrt(x)

### 🟡 P2

- LC 1011 — Capacity To Ship Packages Within D Days
- LC 410 — Split Array Largest Sum

The last two are excellent, but they are **Binary Search on Answer**, so don't touch them until ordinary Binary Search is automatic.

~~~

## Level 1 — Mandatory (Foundation)

1. LC 704 — Binary Search
2. LC 35 — Search Insert Position
3. LC 278 — First Bad Version
4. LC 69 — Sqrt(x)

### Skills Built

* Search space definition
* Mid calculation
* Boundary movement
* Search invariants
* Left/right pointer reasoning

---

## Level 2 — Must Know (Interview Core)

5. LC 34 — Find First and Last Position
6. LC 33 — Search in Rotated Sorted Array
7. LC 153 — Find Minimum in Rotated Sorted Array

### Skills Built

* Modified Binary Search
* Boundary Binary Search
* Rotated Array Logic
* Monotonic Region Detection

---

## Level 3 — Answer Space Search (Advanced)

8. LC 875 — Koko Eating Bananas
9. LC 1011 — Capacity To Ship Packages
10. LC 1283 — Smallest Divisor Given Threshold

### Skills Built

* Binary Search on Answer
* Monotonic Feasibility Functions
* Optimization Problems
* Interview Hard Pattern Recognition

---

# LC 704 — Binary Search

**Pattern:** Classic Binary Search

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Binary Search

The problem gives the most important Binary Search signal:

```text
Sorted Array
```

Input:

```python
nums = [-1,0,3,5,9,12]
target = 9
```

Goal:

```text
Find target index
```

This is the textbook Binary Search problem.

---

## Brute Force Thinking

Scan linearly:

```python
for i in range(len(nums)):
    if nums[i] == target:
        return i
```

### Complexity

[
O(n)
]

For:

```python
n = 1,000,000
```

Worst case:

```python
1,000,000 comparisons
```

---

# Senior Engineer Mindset

A senior engineer asks:

> "The array is sorted. Why inspect every element?"

Instead:

```text
Eliminate half the search space every step.
```

This is the entire idea behind Binary Search.

---

## The Core Observation

Suppose:

```python
nums = [1,3,5,7,9,11,13]
target = 9
```

Choose middle:

```python
mid = 3
nums[mid] = 7
```

Compare:

```python
7 < 9
```

Since the array is sorted:

```text
Everything left of 7 is useless.
```

Discard:

```python
[1,3,5,7]
```

Search only:

```python
[9,11,13]
```

Half the array disappears instantly.

---

## Recognition Signals

Whenever you see:

### Signal 1

```text
Sorted Array
```

### Signal 2

```text
Search Target
```

### Signal 3

```text
Need Better Than O(n)
```

Think:

```text
Binary Search
```

immediately.

---

## The Most Important Binary Search Invariant

At every iteration:

```text
If target exists,
it is inside [left, right]
```

Your entire implementation should preserve this invariant.

---

## Why Mid Is Calculated Like This

Instead of:

```python
mid = (left + right) // 2
```

Many engineers write:

```python
mid = left + (right - left) // 2
```

Reason:

Avoid integer overflow in languages like:

* Java
* C++
* C

Python doesn't overflow here, but interviewers like seeing the safer form.

---

## Complexity Derivation

Every iteration removes half.

Size progression:

[
n
]

[
n/2
]

[
n/4
]

[
n/8
]

...

After k iterations:

[
\frac{n}{2^k}=1
]

Solving:

[
k=\log_2 n
]

Therefore:

[
O(\log n)
]

---

## Interview Trick

If interviewer asks:

> "Why is Binary Search logarithmic?"

Don't say:

```text
Because it halves.
```

Say:

[
n \rightarrow n/2 \rightarrow n/4 \rightarrow ...
]

which gives:

[
O(\log n)
]

That's a stronger answer.

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def search(self, nums, target):
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

---

## Time Complexity

[
O(\log n)
]

Because half of the search space is eliminated every iteration.

---

## Space Complexity

[
O(1)
]

Only:

```python
left
right
mid
```

are used.

---

## Interview Justification

> Since the array is sorted, I compare the target with the middle element and eliminate half of the remaining search space each iteration. This yields O(log n) time and O(1) extra space.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:
    def search(self, nums, target):
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


nums = [-1,0,3,5,9,12]
target = 9

obj = Solution()

print(obj.search(nums, target))
```

---

## Output

```python
4
```

---

# Detailed Dry Run

## Input

```python
nums = [-1,0,3,5,9,12]
target = 9
```

---

### Iteration 1

```python
left = 0
right = 5
```

Mid:

```python
mid = 2
```

Value:

```python
nums[2] = 3
```

Compare:

```python
3 < 9
```

Discard left half.

Update:

```python
left = 3
```

---

### Iteration 2

```python
left = 3
right = 5
```

Mid:

```python
mid = 4
```

Value:

```python
nums[4] = 9
```

Match found.

Return:

```python
4
```

---

# Visual Walkthrough

```text
[-1,0,3,5,9,12]

 L     M     R

3 < 9

Discard Left Half


[-1,0,3,5,9,12]

       L M R

Found 9
```

---

# Example 2 (Target Missing)

Input:

```python
nums = [-1,0,3,5,9,12]
target = 2
```

Process:

```text
mid = 3
target < 3

search left

mid = 0
target > 0

search right

No elements left
```

Return:

```python
-1
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What condition is required for Binary Search?

### Answer

The search space must be sorted or exhibit a monotonic property.

---

## Q2: Why use `left <= right` instead of `<`?

### Answer

Because when:

```python
left == right
```

there is still one candidate element remaining that must be checked.

---

## Q3: Why do we use `mid + 1` and `mid - 1`?

### Answer

Because `mid` has already been evaluated and can no longer contain the target.

---

## Q4: Why is complexity O(log n)?

### Answer

Each iteration cuts the search space approximately in half.

---

## Q5: When would Binary Search fail?

### Answer

If the data is unsorted and lacks any monotonic structure.

Example:

```python
[5,2,9,1,7]
```

---

## Q6: What pattern category is this?

### Answer

**Classic Binary Search**

This is the parent pattern for:

* LC 35 — Search Insert Position
* LC 278 — First Bad Version
* LC 69 — Sqrt(x)
* LC 34 — First and Last Position
* LC 33 — Rotated Sorted Array
* Answer Space Search problems

---

# Pattern Extraction

For LC 704, the reusable pattern is:

```text
Sorted Search Space
        +
Target Lookup
        +
Half Elimination
        =
Binary Search
```

### Master Template

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
```

This template is the foundation of the entire Binary Search family. Master it completely before moving to **LC 35 — Search Insert Position**, where the focus shifts from finding an exact target to finding the correct insertion boundary.


# LC 35 — Search Insert Position

**Pattern:** Binary Search (Lower Bound)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Different From LC 704

LC 704 asks:

```text
Find target
```

LC 35 asks:

```text
Find target OR where it should be inserted
```

This is the first boundary-search problem.

---

## Senior Engineer Mindset

Instead of thinking:

```text
Find exact target
```

Think:

```text
Find first position >= target
```

This is called:

```text
Lower Bound
```

---

## Example

```python
nums = [1,3,5,6]
target = 2
```

Answer:

```python
1
```

Because:

```python
nums[1] = 3
```

is the first value:

[
\ge 2
]

---

## Recognition Signals

Whenever you see:

* Insert position
* First valid index
* Boundary
* Lower bound

Think:

```text
Binary Search on Boundary
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def searchInsert(self, nums, target):
        left = 0
        right = len(nums) - 1

        while left <= right:

            mid = left + (right - left) // 2

            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1

        return left
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

## Interview Justification

> I search for the first index whose value is greater than or equal to the target. When the loop ends, `left` naturally points to the insertion position.

---

# 🔹 Block 3: Full Code + Dry Run

```python
class Solution:
    def searchInsert(self, nums, target):
        left = 0
        right = len(nums) - 1

        while left <= right:

            mid = left + (right - left) // 2

            if nums[mid] < target:
                left = mid + 1
            else:
                right = mid - 1

        return left


nums = [1,3,5,6]
target = 2

obj = Solution()
print(obj.searchInsert(nums, target))
```

Output:

```python
1
```

---

## Dry Run

Input:

```python
nums = [1,3,5,6]
target = 2
```

### Iteration 1

```python
mid = 1
nums[mid] = 3
```

Since:

```python
3 >= 2
```

Move left boundary search:

```python
right = 0
```

---

### Iteration 2

```python
mid = 0
nums[mid] = 1
```

Since:

```python
1 < 2
```

Move:

```python
left = 1
```

Loop ends.

Return:

```python
1
```

---

# 🔹 Block 4: Interview Q&A

### Q1: What is the actual goal?

**Answer:**

Find the first index where:

[
nums[i] \ge target
]

---

### Q2: Why return `left`?

**Answer:**

At loop termination, `left` points to the insertion location.

---

### Q3: What Binary Search variant is this?

**Answer:**

Lower Bound Search.

---

### Q4: If target is larger than all elements?

**Answer:**

Return:

```python
len(nums)
```

---

### Q5: Complexity?

**Answer:**

[
O(\log n)
]

---

---

# LC 278 — First Bad Version

**Pattern:** Binary Search on Monotonic Predicate

---

# 🔹 Block 1: Senior Insights

## Key Observation

Suppose versions:

```text
Good Good Good Bad Bad Bad Bad
```

Once bad appears:

```text
Everything after it is also bad
```

This creates:

```text
False False False True True True
```

A monotonic pattern.

---

## Senior Engineer Mindset

Don't search:

```text
Bad version
```

Search:

```text
First True
```

This is one of the most important Binary Search concepts.

---

## Recognition Signals

Whenever you see:

* First valid
* First bad
* First true
* Earliest failure

Think:

```text
Binary Search on Predicate
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def firstBadVersion(self, n):

        left = 1
        right = n

        while left < right:

            mid = left + (right - left) // 2

            if isBadVersion(mid):
                right = mid
            else:
                left = mid + 1

        return left
```

---

## Interview Justification

> I search for the first version where the predicate becomes true. If mid is bad, the answer could still be mid, so I keep it in the search space.

---

# 🔹 Block 3: Full Code + Dry Run

Assume:

```python
bad = 4
```

Versions:

```text
1 2 3 4 5 6 7
F F F T T T T
```

---

### Iteration 1

```python
mid = 4
```

Bad.

```python
right = 4
```

---

### Iteration 2

```python
mid = 2
```

Good.

```python
left = 3
```

---

### Iteration 3

```python
mid = 3
```

Good.

```python
left = 4
```

Done.

Answer:

```python
4
```

---

# 🔹 Block 4: Interview Q&A

### Q1: Why use `right = mid`?

**Answer:**

Because mid itself could be the first bad version.

---

### Q2: Why not `mid - 1`?

**Answer:**

We would risk skipping the answer.

---

### Q3: What pattern is this?

**Answer:**

First True Binary Search.

---

### Q4: What is the monotonic property?

**Answer:**

Once a version becomes bad, all later versions are bad.

---

### Q5: Complexity?

**Answer:**

[
O(\log n)
]

---

---

# LC 69 — Sqrt(x)

**Pattern:** Binary Search on Value Space

---

# 🔹 Block 1: Senior Insights

## Problem

Find:

[
\lfloor \sqrt{x} \rfloor
]

without using:

```python
sqrt()
```

---

## Brute Force

Try:

```python
1²
2²
3²
...
```

Until exceeding x.

Complexity:

[
O(\sqrt{x})
]

---

## Senior Engineer Mindset

The answer lies between:

[
1
]

and

[
x
]

Search the answer itself.

This introduces:

```text
Binary Search on Values
```

---

## Key Observation

If:

[
mid^2 < x
]

then answer must be:

```text
Right side
```

If:

[
mid^2 > x
]

then answer must be:

```text
Left side
```

Monotonic property exists.

---

## Complexity

Time:

[
O(\log x)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def mySqrt(self, x):

        if x < 2:
            return x

        left = 1
        right = x

        answer = 0

        while left <= right:

            mid = left + (right - left) // 2

            square = mid * mid

            if square == x:
                return mid

            elif square < x:
                answer = mid
                left = mid + 1

            else:
                right = mid - 1

        return answer
```

---

## Interview Justification

> I binary search the answer space. Whenever mid² is less than x, mid becomes a candidate answer and I search larger values. Otherwise I search smaller values.

---

# 🔹 Block 3: Full Code + Dry Run

```python
x = 8
```

---

### Iteration 1

```python
mid = 4
```

[
4^2 = 16
]

Too large.

Move left.

---

### Iteration 2

```python
mid = 2
```

[
2^2 = 4
]

Valid.

Store:

```python
answer = 2
```

Search right.

---

### Iteration 3

```python
mid = 3
```

[
3^2 = 9
]

Too large.

Move left.

---

Done.

Return:

```python
2
```

because:

[
\lfloor \sqrt{8} \rfloor = 2
]

---

# 🔹 Block 4: Interview Q&A

### Q1: Why Binary Search works?

**Answer:**

Because squared values form a monotonic sequence.

---

### Q2: What are we searching?

**Answer:**

The answer itself, not an array.

---

### Q3: Why store `answer`?

**Answer:**

To remember the largest valid value whose square is ≤ x.

---

### Q4: Complexity?

**Answer:**

[
O(\log x)
]

---

### Q5: What pattern category is this?

**Answer:**

Binary Search on Answer/Value Space.

---

# Binary Search Progression So Far

| Problem | Core Concept     |
| ------- | ---------------- |
| LC 704  | Exact Search     |
| LC 35   | Lower Bound      |
| LC 278  | First True       |
| LC 69   | Search on Values |

These four problems form the foundation for all advanced Binary Search interview questions. The next step is Level 2, where the search space becomes modified or rotated rather than perfectly sorted.





# Level 2 — Must Know (Interview Core)

5. LC 34 — Find First and Last Position
6. LC 33 — Search in Rotated Sorted Array
7. LC 153 — Find Minimum in Rotated Sorted Array

### Skills Built

* Modified Binary Search
* Boundary Binary Search
* Rotated Array Logic
* Monotonic Region Detection

Excellent progression.

These three problems are where Binary Search becomes an actual interview skill instead of just a coding exercise.

# 🔒 Level 2 — Must Know (Interview Core)

## 5. LC 34 — Find First and Last Position

**Pattern:** Boundary Binary Search

## 6. LC 33 — Search in Rotated Sorted Array

**Pattern:** Modified Binary Search

## 7. LC 153 — Find Minimum in Rotated Sorted Array

**Pattern:** Binary Search on Rotated Structure

---

# LC 34 — Find First and Last Position of Element in Sorted Array

**Pattern:** Boundary Binary Search (Lower Bound + Upper Bound)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Important

Many candidates think:

```text
Find target
```

But the real problem is:

```text
Find left boundary
Find right boundary
```

This is your first true **boundary search** problem.

---

## Example

```python
nums = [5,7,7,8,8,10]
target = 8
```

Answer:

```python
[3,4]
```

---

## Why Normal Binary Search Fails

Normal Binary Search:

```python
if nums[mid] == target:
    return mid
```

might return:

```python
3
```

or

```python
4
```

Randomly.

But we need:

```text
First occurrence
Last occurrence
```

---

## Senior Engineer Mindset

Think:

```text
Find First 8
Find Last 8
```

These are two different Binary Searches.

---

## Core Idea

### First Position

Search:

```text
First index where nums[i] >= target
```

### Last Position

Search:

```text
Last index where nums[i] <= target
```

---

## Complexity

Two Binary Searches:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def searchRange(self, nums, target):

        def findFirst():
            left = 0
            right = len(nums) - 1
            ans = -1

            while left <= right:
                mid = (left + right) // 2

                if nums[mid] >= target:
                    right = mid - 1
                else:
                    left = mid + 1

                if nums[mid] == target:
                    ans = mid

            return ans

        def findLast():
            left = 0
            right = len(nums) - 1
            ans = -1

            while left <= right:
                mid = (left + right) // 2

                if nums[mid] <= target:
                    left = mid + 1
                else:
                    right = mid - 1

                if nums[mid] == target:
                    ans = mid

            return ans

        return [findFirst(), findLast()]
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 3: Full Code + Dry Run

Input:

```python
nums = [5,7,7,8,8,10]
target = 8
```

---

### First Search

Find First 8

```text
5 7 7 8 8 10
      M
```

Move right.

Eventually:

```text
First 8 → index 3
```

---

### Second Search

Find Last 8

```text
5 7 7 8 8 10
        M
```

Move left.

Eventually:

```text
Last 8 → index 4
```

Answer:

```python
[3,4]
```

---

# 🔹 Block 4: Interview Q&A

### Q1: Why not stop when target is found?

**Answer:**

Because we need boundaries, not just existence.

---

### Q2: How many Binary Searches are used?

**Answer:**

Two.

One for first occurrence and one for last occurrence.

---

### Q3: Complexity?

**Answer:**

[
O(\log n)
]

---

### Q4: Pattern?

**Answer:**

Boundary Binary Search.

---

### Q5: Similar problems?

**Answer:**

LC 35, LC 278, LC 540.

---

---

# LC 33 — Search in Rotated Sorted Array

**Pattern:** Modified Binary Search

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Harder

Normal sorted array:

```python
[1,2,3,4,5,6,7]
```

Rotated:

```python
[4,5,6,7,0,1,2]
```

Sorting property appears broken.

But it isn't.

---

## Key Observation

At least one half is always sorted.

Example:

```python
[4,5,6,7,0,1,2]
```

Mid:

```python
7
```

Left half:

```python
[4,5,6,7]
```

sorted.

Right half:

```python
[0,1,2]
```

rotated.

---

## Senior Engineer Mindset

Don't ask:

```text
Which side has target?
```

Ask:

```text
Which side is sorted?
```

Then determine whether target lies there.

---

## Recognition Signals

Whenever you see:

* Rotated sorted array
* Search target
* O(log n)

Think:

```text
Modified Binary Search
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def search(self, nums, target):

        left = 0
        right = len(nums) - 1

        while left <= right:

            mid = (left + right) // 2

            if nums[mid] == target:
                return mid

            if nums[left] <= nums[mid]:

                if nums[left] <= target < nums[mid]:
                    right = mid - 1
                else:
                    left = mid + 1

            else:

                if nums[mid] < target <= nums[right]:
                    left = mid + 1
                else:
                    right = mid - 1

        return -1
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 3: Full Code + Dry Run

Input:

```python
nums = [4,5,6,7,0,1,2]
target = 0
```

---

### Iteration 1

```python
mid = 3
value = 7
```

Left side sorted.

Target:

```python
0
```

not inside:

```python
[4,5,6,7]
```

Search right.

---

### Iteration 2

Search:

```python
[0,1,2]
```

Mid:

```python
1
```

Target found at index:

```python
4
```

---

# 🔹 Block 4: Interview Q&A

### Q1: Why does Binary Search still work?

**Answer:**

Because at least one half remains sorted.

---

### Q2: Key observation?

**Answer:**

One side is always sorted.

---

### Q3: How decide which half to search?

**Answer:**

Check whether target belongs to the sorted half.

---

### Q4: Complexity?

**Answer:**

[
O(\log n)
]

---

### Q5: Pattern?

**Answer:**

Modified Binary Search.

---

---

# LC 153 — Find Minimum in Rotated Sorted Array

**Pattern:** Binary Search on Rotated Structure

---

# 🔹 Block 1: Senior Insights

## Problem

Input:

```python
[4,5,6,7,0,1,2]
```

Output:

```python
0
```

---

## Brute Force

Scan:

```python
min(nums)
```

Complexity:

[
O(n)
]

---

## Senior Engineer Mindset

The minimum is exactly where rotation happened.

Example:

```text
4 5 6 7 | 0 1 2
         ^
      minimum
```

Find the pivot.

---

## Key Observation

Compare:

```python
nums[mid]
```

with

```python
nums[right]
```

---

### Case 1

```python
nums[mid] > nums[right]
```

Minimum must be:

```text
Right side
```

---

### Case 2

```python
nums[mid] <= nums[right]
```

Minimum may be:

```text
Mid or Left side
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def findMin(self, nums):

        left = 0
        right = len(nums) - 1

        while left < right:

            mid = (left + right) // 2

            if nums[mid] > nums[right]:
                left = mid + 1
            else:
                right = mid

        return nums[left]
```

---

## Complexity

Time:

[
O(\log n)
]

Space:

[
O(1)
]

---

# 🔹 Block 3: Full Code + Dry Run

Input:

```python
nums = [4,5,6,7,0,1,2]
```

---

### Iteration 1

```python
mid = 3
value = 7
```

Compare:

```python
7 > 2
```

Minimum must be right.

Move:

```python
left = 4
```

---

### Iteration 2

Search:

```python
[0,1,2]
```

Mid:

```python
1
```

Compare:

```python
1 <= 2
```

Minimum may be left.

Move:

```python
right = mid
```

Continue.

Eventually:

```python
left = right = 4
```

Answer:

```python
0
```

---

# 🔹 Block 4: Interview Q&A

### Q1: Why compare with `nums[right]`?

**Answer:**

It tells us which side contains the rotation point.

---

### Q2: Why use `right = mid` instead of `mid - 1`?

**Answer:**

Because `mid` itself could be the minimum.

---

### Q3: Complexity?

**Answer:**

[
O(\log n)
]

---

### Q4: Pattern?

**Answer:**

Binary Search on Rotated Structure.

---

### Q5: Key insight?

**Answer:**

The minimum lies at the rotation pivot.

---

# Level 2 Pattern Summary

| Problem | Main Concept            |
| ------- | ----------------------- |
| LC 34   | Boundary Search         |
| LC 33   | Search in Rotated Array |
| LC 153  | Find Rotation Pivot     |

These three problems teach the core interview skill:

```text
Binary Search is NOT about finding values.
Binary Search is about exploiting monotonic structure.
```

That mindset is essential before moving to **Level 3 — Answer Space Search**:

* LC 875 — Koko Eating Bananas
* LC 1011 — Capacity To Ship Packages
* LC 1283 — Smallest Divisor Given Threshold.





## Level 3 — Answer Space Search (Advanced)

8. LC 875 — Koko Eating Bananas
9. LC 1011 — Capacity To Ship Packages
10. LC 1283 — Smallest Divisor Given Threshold

### Skills Built

* Binary Search on Answer
* Monotonic Feasibility Functions
* Optimization Problems
* Interview Hard Pattern Recognition

# LC 875 — Koko Eating Bananas

**Pattern:** Binary Search on Answer Space (First Valid Answer)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Important

This is the problem where Binary Search changes from:

```text id="v5j8r1"
Searching an array
```

to

```text id="m2x9p4"
Searching the answer
```

Most candidates know LC 704.

Strong candidates know LC 875.

---

## Problem Statement Simplified

Koko has banana piles:

```python
piles = [3,6,7,11]
h = 8
```

She can eat:

```python
k bananas/hour
```

Find:

```text
Minimum eating speed k
```

so she finishes within:

```python
h hours
```

---

# Brute Force Thinking

Try every speed:

```python
k = 1
k = 2
k = 3
...
```

For each speed:

Calculate total hours.

---

## Complexity

Worst case:

[
O(max(piles) \times n)
]

Too expensive.

---

# Senior Engineer Mindset

The interviewer asks:

> Find the minimum valid speed.

Immediately think:

```text
Binary Search on Answer
```

---

# Key Observation

Suppose:

```python
speed = 1
```

Hours needed:

```python
27
```

Too slow.

---

Suppose:

```python
speed = 4
```

Hours needed:

```python
8
```

Valid.

---

Suppose:

```python
speed = 5
```

Hours needed:

```python
7
```

Valid.

---

Notice:

```text
1 → Invalid
2 → Invalid
3 → Invalid
4 → Valid
5 → Valid
6 → Valid
...
```

Pattern:

```text
F F F T T T T T
```

This is a monotonic sequence.

Binary Search loves monotonic sequences.

---

# The Feasibility Function

Core question:

```python
Can Koko finish at speed = k ?
```

Return:

```python
True
```

or

```python
False
```

This is called a:

```text
Feasibility Function
```

---

# Search Space

Minimum possible speed:

```python
1
```

Maximum possible speed:

```python
max(piles)
```

Why?

Because eating faster than the largest pile provides no benefit.

---

# Computing Hours

For pile:

```python
pile = 11
speed = 4
```

Hours:

[
\lceil 11/4 \rceil
]

[
= 3
]

---

## Python Trick

Instead of:

```python
math.ceil(pile / speed)
```

Use:

```python
(pile + speed - 1) // speed
```

Interviewers love this.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text
Minimum speed
```

### Signal 2

```text
Minimum capacity
```

### Signal 3

```text
Smallest divisor
```

### Signal 4

```text
Can we do it?
```

Think:

```text
Binary Search on Answer
```

---

# Complexity Derivation

Binary Search Range:

[
1 \to max(piles)
]

Iterations:

[
O(\log(max(piles)))
]

Each iteration:

Scan all piles.

[
O(n)
]

Total:

[
O(n \log(max(piles)))
]

---

# Interview Trick

If interviewer asks:

> Why Binary Search works?

Answer:

> Because the feasibility function is monotonic. If Koko can finish at speed k, she can also finish at every speed greater than k.

That's the entire proof.

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def minEatingSpeed(self, piles, h):

        left = 1
        right = max(piles)

        answer = right

        while left <= right:

            speed = left + (right - left) // 2

            hours = 0

            for pile in piles:
                hours += (pile + speed - 1) // speed

            if hours <= h:

                answer = speed
                right = speed - 1

            else:

                left = speed + 1

        return answer
```

---

## Time Complexity

[
O(n \log(max(piles)))
]

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I binary search the eating speed. For each candidate speed, I calculate the number of hours required. If Koko can finish within h hours, the speed is feasible and I search for a smaller valid speed. Otherwise I increase the speed.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:
    def minEatingSpeed(self, piles, h):

        left = 1
        right = max(piles)

        answer = right

        while left <= right:

            speed = left + (right - left) // 2

            hours = 0

            for pile in piles:
                hours += (pile + speed - 1) // speed

            if hours <= h:

                answer = speed
                right = speed - 1

            else:

                left = speed + 1

        return answer


piles = [3, 6, 7, 11]
h = 8

obj = Solution()

print(obj.minEatingSpeed(piles, h))
```

---

## Output

```python
4
```

---

# Detailed Dry Run

## Input

```python
piles = [3,6,7,11]
h = 8
```

---

### Initial Search Space

```python
left = 1
right = 11
```

---

## Iteration 1

```python
speed = 6
```

Hours:

```python
3 -> 1
6 -> 1
7 -> 2
11 -> 2
```

Total:

```python
6
```

Since:

```python
6 <= 8
```

Valid.

Store:

```python
answer = 6
```

Try smaller speed:

```python
right = 5
```

---

## Iteration 2

```python
speed = 3
```

Hours:

```python
3 -> 1
6 -> 2
7 -> 3
11 -> 4
```

Total:

```python
10
```

Too many.

Invalid.

Move right:

```python
left = 4
```

---

## Iteration 3

```python
speed = 4
```

Hours:

```python
3 -> 1
6 -> 2
7 -> 2
11 -> 3
```

Total:

```python
8
```

Valid.

Store:

```python
answer = 4
```

Search smaller:

```python
right = 3
```

Loop ends.

Return:

```python
4
```

---

# Visual Understanding

```text
Speed

1  -> False
2  -> False
3  -> False
4  -> True
5  -> True
6  -> True
7  -> True
8  -> True
...
```

Binary Search finds:

```text
First True
```

which is:

```python
4
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What are we Binary Searching?

### Answer

The eating speed.

Not the piles.

---

## Q2: What is the search space?

### Answer

[
[1, max(piles)]
]

---

## Q3: Why is the feasibility function monotonic?

### Answer

If Koko can finish at speed k, she can finish at every speed greater than k.

---

## Q4: Why use ceiling division?

### Answer

A partial hour still counts as a full hour.

Example:

[
11/4 = 2.75
]

requires:

[
3
]

hours.

---

## Q5: Why store `answer`?

### Answer

We want the minimum valid speed, so every feasible speed becomes a candidate answer.

---

## Q6: What pattern category is this?

### Answer

**Binary Search on Answer Space**

Also known as:

```text
First Valid Answer Search
```

---

# Pattern Extraction

For LC 875, the reusable pattern is:

```text
Optimization Problem
          +
Can We Do It?
          +
Monotonic Feasibility
          +
Minimum Valid Answer
          =
Binary Search on Answer
```

### Universal Template

```python
while left <= right:

    mid = (left + right) // 2

    if feasible(mid):

        answer = mid
        right = mid - 1

    else:

        left = mid + 1
```

This exact pattern reappears in:

* LC 1011 — Capacity To Ship Packages Within D Days
* LC 1283 — Smallest Divisor Given Threshold
* LC 1482 — Minimum Days to Make Bouquets
* LC 1552 — Magnetic Force Between Two Balls
* Many FAANG optimization problems

Master LC 875 thoroughly. It is the foundation of the entire **Answer Space Search** category.

# LC 1011 — Capacity To Ship Packages Within D Days

**Pattern:** Binary Search on Answer Space (Minimum Valid Capacity)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Important

This is essentially:

```text id="y6n2gx"
LC 875 (Koko)
        ↓
Different Story
```

Koko:

```text id="e1azs8"
Minimum Eating Speed
```

LC 1011:

```text id="m8wxtl"
Minimum Ship Capacity
```

The underlying pattern is identical:

```text id="4zsv3h"
Optimization Problem
        +
Can We Do It?
        +
Monotonic Answer
        =
Binary Search on Answer
```

---

# Problem Statement Simplified

Given:

```python id="7vjlwm"
weights = [1,2,3,4,5,6,7,8,9,10]
days = 5
```

Find the minimum ship capacity needed to ship all packages within:

```python id="n8pb5m"
5 days
```

---

# Brute Force Thinking

Try:

```python id="v6thj0"
capacity = 1
capacity = 2
capacity = 3
...
```

For each capacity:

Simulate shipping.

---

## Complexity

Potentially:

[
O(sum(weights)\times n)
]

Too expensive.

---

# Senior Engineer Mindset

The interviewer asks:

> Find the minimum capacity.

Immediately think:

```text id="jpt1sm"
Binary Search on Answer
```

---

# The Feasibility Function

Question:

```python id="0y71s3"
Can we ship everything
with capacity = C
within D days?
```

Return:

```python id="ht6g9j"
True
```

or

```python id="5b8dbu"
False
```

This is our feasibility function.

---

# Search Space

## Minimum Capacity

Must be:

```python id="yhv6wi"
max(weights)
```

Why?

Suppose:

```python id="vlyw7s"
weights = [1,2,10]
```

Capacity:

```python id="g9byms"
8
```

Impossible.

Package:

```python id="0v9llj"
10
```

cannot even fit.

Therefore:

[
left=max(weights)
]

---

## Maximum Capacity

Ship everything in one day:

```python id="4o8eql"
sum(weights)
```

Therefore:

[
right=sum(weights)
]

---

# The Monotonic Property

Example:

```python id="8ef7b4"
capacity = 10
```

Needs:

```python id="bj5ahw"
7 days
```

Invalid.

---

```python id="e5y82m"
capacity = 15
```

Needs:

```python id="rydbz6"
5 days
```

Valid.

---

```python id="ll4rr1"
capacity = 20
```

Needs:

```python id="vxho69"
4 days
```

Valid.

Pattern:

```text id="mkg58c"
F F F T T T T
```

Monotonic.

Binary Search works.

---

# The Simulation Function

Suppose:

```python id="0jmgzj"
capacity = 15
```

Packages:

```python id="4k0aeh"
1,2,3,4,5,6,7,8,9,10
```

Day 1:

```python id="ewtw0s"
1+2+3+4+5 = 15
```

Day 2:

```python id="1f95jk"
6+7 = 13
```

Day 3:

```python id="0f8dhl"
8
```

Day 4:

```python id="v7h2wg"
9
```

Day 5:

```python id="n73yvj"
10
```

Exactly:

```python id="m6g2nd"
5 days
```

Valid.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="1zc5uo"
Minimum Capacity
```

### Signal 2

```text id="f6ajzr"
Minimum Speed
```

### Signal 3

```text id="izj9dr"
Minimum Days
```

### Signal 4

```text id="b9u8a4"
Can we finish?
```

Think:

```text id="w4hkh6"
Binary Search on Answer
```

---

# Complexity Derivation

Binary Search range:

[
max(weights)
\rightarrow
sum(weights)
]

Iterations:

[
O(\log(sum(weights)))
]

Each iteration:

Scan entire array:

[
O(n)
]

Total:

[
O(n\log(sum(weights)))
]

---

# Interview Trick

If asked:

> Why does Binary Search work?

Answer:

> If a capacity C works, then every capacity greater than C also works. This creates a monotonic feasibility function.

---

# 🔹 Block 2: Efficient Code

```python id="5pv8m1"
class Solution:
    def shipWithinDays(self, weights, days):

        left = max(weights)
        right = sum(weights)

        answer = right

        while left <= right:

            capacity = left + (right - left) // 2

            needed_days = 1
            current_load = 0

            for weight in weights:

                if current_load + weight > capacity:
                    needed_days += 1
                    current_load = 0

                current_load += weight

            if needed_days <= days:

                answer = capacity
                right = capacity - 1

            else:

                left = capacity + 1

        return answer
```

---

## Time Complexity

[
O(n\log(sum(weights)))
]

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I binary search the ship capacity. For each candidate capacity, I simulate loading packages in order and count the required days. If the packages can be shipped within the given days, the capacity is feasible and I try to find a smaller valid capacity.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="6lztzv"
class Solution:
    def shipWithinDays(self, weights, days):

        left = max(weights)
        right = sum(weights)

        answer = right

        while left <= right:

            capacity = left + (right - left) // 2

            needed_days = 1
            current_load = 0

            for weight in weights:

                if current_load + weight > capacity:
                    needed_days += 1
                    current_load = 0

                current_load += weight

            if needed_days <= days:
                answer = capacity
                right = capacity - 1
            else:
                left = capacity + 1

        return answer


weights = [1,2,3,4,5,6,7,8,9,10]
days = 5

obj = Solution()

print(obj.shipWithinDays(weights, days))
```

---

## Output

```python id="jlwm6j"
15
```

---

# Detailed Dry Run

Input:

```python id="tr5zow"
weights = [1,2,3,4,5,6,7,8,9,10]
days = 5
```

---

## Initial Search Space

```python id="kwfb89"
left = 10
right = 55
```

---

## Iteration 1

```python id="3ty7dv"
capacity = 32
```

Simulation:

Day 1:

```python id="l44a3n"
1+2+3+4+5+6+7 = 28
```

Day 2:

```python id="q4v68q"
8+9+10 = 27
```

Days:

```python id="5w1dgh"
2
```

Valid.

Try smaller capacity.

---

## Iteration 2

```python id="mdx0ck"
capacity = 20
```

Days:

```python id="6fs95z"
4
```

Valid.

Try smaller.

---

## Iteration 3

```python id="0h87mx"
capacity = 14
```

Days:

```python id="t9i2vc"
6
```

Too many.

Invalid.

Need larger capacity.

---

Eventually:

```python id="mff4mj"
capacity = 15
```

Days:

```python id="n3v7zu"
5
```

Valid.

Return:

```python id="zlk5ov"
15
```

---

# Visual Understanding

```text id="fcd2gm"
Capacity

10 -> False
11 -> False
12 -> False
13 -> False
14 -> False
15 -> True
16 -> True
17 -> True
...
```

Binary Search finds:

```text id="cn2n4k"
First True
```

which is:

```python id="mrmr0n"
15
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What are we Binary Searching?

### Answer

The ship capacity.

Not the weights array.

---

## Q2: Why does the minimum capacity start at `max(weights)`?

### Answer

Because every package must fit individually.

Any smaller capacity is impossible.

---

## Q3: Why does the maximum capacity equal `sum(weights)`?

### Answer

Because that allows shipping all packages in one day.

---

## Q4: Why is the feasibility function monotonic?

### Answer

If capacity C works, then every capacity greater than C also works.

---

## Q5: Why do we simulate shipping?

### Answer

Because we need to determine whether a candidate capacity can finish within the required number of days.

---

## Q6: What pattern category is this?

### Answer

**Binary Search on Answer Space**

More specifically:

```text id="xydncm"
Minimum Valid Capacity Search
```

---

# Pattern Extraction

For LC 1011, the reusable pattern is:

```text id="srh0n8"
Optimization Problem
          +
Can We Finish?
          +
Monotonic Feasibility
          +
Minimum Valid Answer
          =
Binary Search on Answer
```

---

# Universal Template

```python id="h7y5e1"
left = minimum_possible_answer
right = maximum_possible_answer

while left <= right:

    mid = (left + right) // 2

    if feasible(mid):
        answer = mid
        right = mid - 1
    else:
        left = mid + 1
```

This exact pattern reappears in:

* LC 875 — Koko Eating Bananas
* LC 1283 — Smallest Divisor Given Threshold
* LC 1482 — Minimum Days to Make Bouquets
* LC 410 — Split Array Largest Sum
* Many scheduling and capacity optimization problems in interviews and distributed systems.



# LC 1283 — Smallest Divisor Given Threshold

**Pattern:** Binary Search on Answer Space (Minimum Valid Divisor)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Is Important

This is the third canonical **Answer Space Search** problem.

The story changes again:

* LC 875 → Minimum Eating Speed
* LC 1011 → Minimum Ship Capacity
* LC 1283 → Minimum Divisor

But the underlying pattern remains identical:

```text id="uazsdr"
Optimization Problem
        +
Can We Do It?
        +
Monotonic Feasibility
        =
Binary Search on Answer
```

---

## Problem Statement Simplified

Given:

```python id="zcg1qe"
nums = [1,2,5,9]
threshold = 6
```

Choose a divisor:

```python id="j4c3hy"
d
```

Compute:

[
\lceil 1/d \rceil
+
\lceil 2/d \rceil
+
\lceil 5/d \rceil
+
\lceil 9/d \rceil
]

Find the **smallest divisor** such that:

[
sum \le threshold
]

---

# Brute Force Thinking

Try:

```python id="rkjl9e"
d = 1
d = 2
d = 3
...
```

For each divisor:

Compute the entire sum.

---

## Complexity

Potentially:

[
O(max(nums)\times n)
]

Too slow.

---

# Senior Engineer Mindset

The interviewer asks:

> Find the smallest divisor.

Immediately think:

```text id="mxv6mz"
Binary Search on Answer
```

---

# The Feasibility Function

Question:

```python id="qz7o90"
Can divisor = d
produce a sum <= threshold ?
```

Return:

```python id="o7g0up"
True
```

or

```python id="f38u8k"
False
```

---

# Search Space

## Minimum Divisor

Smallest possible:

```python id="8knj4t"
1
```

---

## Maximum Divisor

Largest useful divisor:

```python id="p4bcdv"
max(nums)
```

Why?

Because:

```python id="4qq9ps"
ceil(num / max(nums))
```

is always:

```python id="z0h7rb"
1
```

or

```python id="b3n0q6"
0
```

for every element.

A larger divisor gives the same result and is unnecessary.

Therefore:

```python id="kg4zdx"
left = 1
right = max(nums)
```

---

# The Monotonic Property

Example:

```python id="gsy0zg"
nums = [1,2,5,9]
threshold = 6
```

---

### Divisor = 1

Sum:

[
1+2+5+9=17
]

Invalid.

---

### Divisor = 3

Sum:

[
1+1+2+3=7
]

Invalid.

---

### Divisor = 5

Sum:

[
1+1+1+2=5
]

Valid.

---

### Divisor = 6

Sum:

[
1+1+1+2=5
]

Valid.

Pattern:

```text id="aqg2k9"
F F F F T T T T
```

Monotonic.

Binary Search works.

---

# The Most Important Formula

For:

```python id="35j9g7"
num = 9
divisor = 4
```

Need:

[
\lceil 9/4 \rceil
]

which equals:

[
3
]

---

## Python Trick

Avoid:

```python id="xg0k4u"
math.ceil(num / divisor)
```

Use integer arithmetic:

```python id="sgwd0w"
(num + divisor - 1) // divisor
```

Example:

```python id="92okzk"
(9 + 4 - 1) // 4
= 12 // 4
= 3
```

Interviewers love this optimization.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="3j5p2q"
Smallest divisor
```

### Signal 2

```text id="vml2k7"
Minimum speed
```

### Signal 3

```text id="v1w0n8"
Minimum capacity
```

### Signal 4

```text id="fquybo"
Can we do it?
```

Think:

```text id="0y3k7u"
Binary Search on Answer
```

---

# Complexity Derivation

Binary Search range:

[
1
\rightarrow
max(nums)
]

Iterations:

[
O(\log(max(nums)))
]

Each iteration:

Scan all numbers:

[
O(n)
]

Total:

[
O(n\log(max(nums)))
]

---

# Interview Trick

If asked:

> Why does Binary Search work?

Answer:

> Increasing the divisor can only decrease or keep the same value of every ceiling term. Therefore the total sum is monotonically non-increasing.

This is the proof.

---

# 🔹 Block 2: Efficient Code

```python id="5mq3go"
class Solution:
    def smallestDivisor(self, nums, threshold):

        left = 1
        right = max(nums)

        answer = right

        while left <= right:

            divisor = left + (right - left) // 2

            total = 0

            for num in nums:
                total += (num + divisor - 1) // divisor

            if total <= threshold:

                answer = divisor
                right = divisor - 1

            else:

                left = divisor + 1

        return answer
```

---

## Time Complexity

[
O(n\log(max(nums)))
]

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I binary search the divisor. For each candidate divisor, I compute the ceiling division sum. If the sum is within the threshold, the divisor is feasible and I try to find a smaller valid divisor.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="j3ol2q"
class Solution:
    def smallestDivisor(self, nums, threshold):

        left = 1
        right = max(nums)

        answer = right

        while left <= right:

            divisor = left + (right - left) // 2

            total = 0

            for num in nums:
                total += (num + divisor - 1) // divisor

            if total <= threshold:
                answer = divisor
                right = divisor - 1
            else:
                left = divisor + 1

        return answer


nums = [1,2,5,9]
threshold = 6

obj = Solution()

print(obj.smallestDivisor(nums, threshold))
```

---

## Output

```python id="tf3f1q"
5
```

---

# Detailed Dry Run

## Input

```python id="vgmn4v"
nums = [1,2,5,9]
threshold = 6
```

---

## Initial Search Space

```python id="7fwwx8"
left = 1
right = 9
```

---

## Iteration 1

```python id="3ftqvl"
divisor = 5
```

Compute:

```python id="29jphn"
ceil(1/5) = 1
ceil(2/5) = 1
ceil(5/5) = 1
ceil(9/5) = 2
```

Total:

```python id="z9x0w7"
5
```

Since:

```python id="vjlwm5"
5 <= 6
```

Valid.

Store:

```python id="m9hy8g"
answer = 5
```

Try smaller divisor:

```python id="7duotj"
right = 4
```

---

## Iteration 2

```python id="5ntx0o"
divisor = 2
```

Compute:

```python id="l0s2pc"
1 + 1 + 3 + 5 = 10
```

Invalid.

Need larger divisor.

```python id="70rnhf"
left = 3
```

---

## Iteration 3

```python id="r87z4h"
divisor = 3
```

Compute:

```python id="8pgp8h"
1 + 1 + 2 + 3 = 7
```

Invalid.

Need larger divisor.

```python id="twy2th"
left = 4
```

---

## Iteration 4

```python id="1tkk6l"
divisor = 4
```

Compute:

```python id="qzzw6z"
1 + 1 + 2 + 3 = 7
```

Still invalid.

```python id="t8ow0e"
left = 5
```

Loop ends.

Return:

```python id="g2q0jz"
5
```

---

# Visual Understanding

```text id="myylwk"
Divisor

1 -> False
2 -> False
3 -> False
4 -> False
5 -> True
6 -> True
7 -> True
8 -> True
9 -> True
```

Binary Search finds:

```text id="lcp8kn"
First True
```

which is:

```python id="xt6dq3"
5
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What are we Binary Searching?

### Answer

The divisor.

Not the array.

---

## Q2: Why does the feasibility function become monotonic?

### Answer

As the divisor increases, every ceiling division result either decreases or remains unchanged.

Therefore the total sum is monotonically non-increasing.

---

## Q3: Why is the maximum divisor `max(nums)`?

### Answer

Any divisor larger than `max(nums)` produces the same ceiling values and provides no additional benefit.

---

## Q4: Why use ceiling division?

### Answer

The problem explicitly requires:

[
\lceil num/divisor \rceil
]

Using:

```python id="yj0p04"
(num + divisor - 1) // divisor
```

avoids floating-point operations.

---

## Q5: Why store `answer`?

### Answer

Because we want the smallest valid divisor. Every feasible divisor becomes a candidate answer.

---

## Q6: What pattern category is this?

### Answer

**Binary Search on Answer Space**

More specifically:

```text id="hld5jy"
Minimum Valid Divisor Search
```

---

# Pattern Extraction

For LC 1283, the reusable pattern is:

```text id="tydtp0"
Optimization Problem
          +
Can We Do It?
          +
Monotonic Feasibility
          +
Minimum Valid Answer
          =
Binary Search on Answer
```

---

# Universal Template

```python id="2j4g3k"
left = minimum_possible_answer
right = maximum_possible_answer

while left <= right:

    mid = (left + right) // 2

    if feasible(mid):
        answer = mid
        right = mid - 1
    else:
        left = mid + 1
```

---

# Binary Search Level 3 Summary

| Problem | Search Space  | Feasibility Question               |
| ------- | ------------- | ---------------------------------- |
| LC 875  | Eating Speed  | Can Koko finish in h hours?        |
| LC 1011 | Ship Capacity | Can packages be shipped in D days? |
| LC 1283 | Divisor       | Is the ceiling sum ≤ threshold?    |

## Master Formula

```text id="8fhtza"
Minimum X
      +
Can X work?
      +
F F F T T T
      =
Binary Search on Answer
```

These three problems form the foundation of almost every advanced Binary Search optimization problem asked in FAANG-level interviews.
