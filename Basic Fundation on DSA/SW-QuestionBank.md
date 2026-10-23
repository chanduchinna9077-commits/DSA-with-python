#  SLIDING WINDOW QUESTION BANK (ML/MLOps TRACK)


# FINAL SYLLABUS

~~~

# 🥈 2. SLIDING WINDOW — MUST MASTER

This is one of the patterns I would **absolutely not skip** before your interview.

### 🔴 P0

- **LC 3 — Longest Substring Without Repeating Characters**
- **LC 209 — Minimum Size Subarray Sum**
- **LC 424 — Longest Repeating Character Replacement**
- **LC 1004 — Max Consecutive Ones III**

### 🟠 P1

- LC 438 — Find All Anagrams in a String
- LC 567 — Permutation in String
- LC 904 — Fruit Into Baskets

### 🟡 P2

- LC 76 — Minimum Window Substring

### Pattern

```text
Expand right
     ↓
Window becomes invalid?
     ↓
Move left
     ↓
Update answer
```

The key skill isn't memorizing a template.

It's answering:

> **What makes my window invalid?**

Examples:

```text
Duplicate character
Too many zeros
Character frequency mismatch
Sum >= target
Frequency constraint
```

---

~~~


# ⭐ Fixed Window

1. LC 643 — Maximum Average Subarray I
2. LC 1456 — Maximum Number of Vowels in Substring of Given Length
3. LC 2461 — Maximum Sum of Distinct Subarrays With Length K

---

# ⭐ Dynamic Window

4. LC 209 — Minimum Size Subarray Sum
5. LC 3 — Longest Substring Without Repeating Characters
6. LC 904 — Fruit Into Baskets
7. LC 1004 — Max Consecutive Ones III
8. LC 424 — Longest Repeating Character Replacement
9. LC 713 — Subarray Product Less Than K
10. LC 438 — Find All Anagrams in a String




# ===============================================================================
# ⭐ Fixed Window

1. LC 643 — Maximum Average Subarray I
2. LC 1456 — Maximum Number of Vowels in Substring of Given Length
3. LC 2461 — Maximum Sum of Distinct Subarrays With Length K

# ⚔ LC 643 — Maximum Average Subarray I

### Pattern: **Fixed Sliding Window**

Difficulty: Easy
Importance for ML/MLOps Interviews: 🔥🔥🔥🔥

---

# 🧠 1. Problem Statement

Given:

```python
nums = [1, 12, -5, -6, 50, 3]
k = 4
```

Find the **maximum average** of any contiguous subarray of size `k`.

---

## Example

Possible windows:

```python
[1, 12, -5, -6]
[12, -5, -6, 50]
[-5, -6, 50, 3]
```

Sums:

```python
2
51
42
```

Maximum sum:

```python
51
```

Maximum average:

```python
51 / 4 = 12.75
```

Answer:

```python
12.75
```

---

# 🧠 2. Why Brute Force is Bad

## Brute Force Thinking

For every starting index:

```python
calculate sum of next k elements
```

Code:

```python
for i in range(n - k + 1):
    total = 0

    for j in range(i, i + k):
        total += nums[j]
```

---

### Time Complexity

Outer loop:

```python
O(n)
```

Inner loop:

```python
O(k)
```

Total:

```text
O(n × k)
```

---

If:

```python
n = 100000
k = 50000
```

Impossible in interviews.

---

# 🧠 3. Observation (THIS IS THE KEY)

Window 1:

```python
[1,12,-5,-6]
sum = 2
```

Window 2:

```python
[12,-5,-6,50]
sum = 51
```

What changed?

Removed:

```python
1
```

Added:

```python
50
```

Everything else remained.

---

Instead of recalculating:

```python
12 + (-5) + (-6) + 50
```

We can do:

```python
new_sum = old_sum - removed + added
```

This is the entire Sliding Window idea.

---

# 🧠 4. Why This is Fixed Window

Because:

```python
k = 4
```

Never changes.

Window always has:

```python
exactly 4 elements
```

Whenever you see:

* size K
* length K
* exactly K

Immediately think:

# ✅ Fixed Sliding Window

---

# 🧠 5. Fixed Window Template

```python
window_sum = 0
left = 0

for right in range(len(arr)):

    # expand
    window_sum += arr[right]

    # remove extra element
    if right >= k:
        window_sum -= arr[left]
        left += 1

    # valid window formed
    if right >= k - 1:
        # process answer
```

---

# 🧠 ELI10 Intuition

Imagine:

You have a box that can hold exactly:

```python
k items
```

Whenever a new item enters:

One old item must leave.

The box size never changes.

---

# ⚔ Optimal Solution

```python
def findMaxAverage(nums, k):

    # current sum of our window
    window_sum = 0

    # maximum window sum found so far
    max_sum = float("-inf")

    # left boundary of window
    left = 0

    # right boundary expands
    for right in range(len(nums)):

        # include new element
        window_sum += nums[right]

        # if window becomes too large
        if right >= k:

            # remove oldest element
            window_sum -= nums[left]

            # move left boundary
            left += 1

        # first valid window formed
        if right >= k - 1:

            # update answer
            max_sum = max(max_sum,
                          window_sum)

    # convert sum into average
    return max_sum / k
```

---

# 🧪 DRY RUN (VERY IMPORTANT)

## Input

```python
nums = [1,12,-5,-6,50,3]
k = 4
```

---

## Initial

```python
window_sum = 0
max_sum = -inf
left = 0
```

---

## Iteration 1

```python
right = 0
```

Add:

```python
1
```

Window:

```python
[1]
```

Sum:

```python
1
```

Not size 4 yet.

---

## Iteration 2

```python
right = 1
```

Add:

```python
12
```

Window:

```python
[1,12]
```

Sum:

```python
13
```

Not size 4.

---

## Iteration 3

```python
right = 2
```

Add:

```python
-5
```

Window:

```python
[1,12,-5]
```

Sum:

```python
8
```

Not size 4.

---

## Iteration 4

```python
right = 3
```

Add:

```python
-6
```

Window:

```python
[1,12,-5,-6]
```

Sum:

```python
2
```

Window size = 4.

```python
max_sum = 2
```

---

## Iteration 5

```python
right = 4
```

Add:

```python
50
```

Sum:

```python
52
```

Window too large.

Remove:

```python
nums[left] = 1
```

New sum:

```python
51
```

Move:

```python
left = 1
```

Window:

```python
[12,-5,-6,50]
```

Update:

```python
max_sum = 51
```

---

## Iteration 6

```python
right = 5
```

Add:

```python
3
```

Sum:

```python
54
```

Remove:

```python
12
```

New sum:

```python
42
```

Window:

```python
[-5,-6,50,3]
```

Update:

```python
max_sum = 51
```

---

# Final Answer

```python
51 / 4
=
12.75
```

---

# 🧠 Why O(n)?

Because:

Every element:

### enters window once

```python
window_sum += nums[right]
```

and

### leaves window once

```python
window_sum -= nums[left]
```

No element is processed repeatedly.

Time:

```text
O(n)
```

Space:

```text
O(1)
```

---

# 🎯 Senior Interview Explanation

> Since the subarray size is fixed at k, I use a fixed sliding window. Instead of recalculating every window sum, I update the current window by removing the leftmost element and adding the new rightmost element. This reduces the complexity from O(n × k) to O(n).

---

# 🏭 Real ML/MLOps Analogy

Suppose:

```python
CPU usage every minute
```

```python
[45, 47, 50, 49, 60, 55]
```

Question:

> Highest average CPU usage in any 5-minute period?

Exactly this problem.

Other examples:

* rolling loss
* moving averages
* monitoring metrics
* anomaly detection
* streaming analytics

Fixed Sliding Window is used everywhere in production systems.

---

# 🔥 Mastery Checklist

You have mastered this pattern if you can answer:

1. Why is this Fixed Window and not Dynamic Window?
2. Why don't we recompute every sum?
3. Why does each element enter and leave only once?
4. Can you write the template from memory?
5. If I replace sum with count/max/frequency, does the template still work?

If yes → **Fixed Sliding Window is locked.**

---

## Next Fixed Window Problem (Recommended Order)

1. ✅ LC 643 — Maximum Average Subarray I
2. ➡️ LC 1456 — Maximum Number of Vowels in a Substring of Given Length K
3. ➡️ LC 2461 — Maximum Sum of Distinct Subarrays With Length K

These three are enough to completely understand **Fixed Sliding Window** for your ML/MLOps interviews.

# LC 1456 — Maximum Number of Vowels in a Substring of Given Length

**Pattern:** Fixed-Size Sliding Window

The problem asks for the maximum number of vowels in **any substring of exactly length `k`**, which maps directly to a **fixed-size sliding window** problem. The optimal approach is to maintain the vowel count while sliding a window of size `k` across the string instead of recounting every substring from scratch. ([LeetCode][1])

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

Input:

```python
s = "abciiidef"
k = 3
```

Possible windows:

```text
abc → 1 vowel
bci → 1 vowel
cii → 2 vowels
iii → 3 vowels
iid → 2 vowels
ide → 2 vowels
def → 1 vowel
```

Answer:

```python
3
```

---

# Brute Force Thinking

Generate every substring of size `k`:

```python
for i in range(n - k + 1):
    count vowels in s[i:i+k]
```

### Complexity

Windows:

[
n-k+1
]

Each window:

[
O(k)
]

Total:

[
O(nk)
]

Too expensive for large inputs. ([NeetCode][2])

---

# Senior Engineer Mindset

Notice:

```text
abc
 bci
  cii
   iii
```

Consecutive windows overlap heavily.

When moving:

```text
abc → bci
```

Only two characters matter:

* Remove:

```python
'a'
```

* Add:

```python
'i'
```

Everything else stays.

This is the defining characteristic of a Sliding Window problem.

---

# Core Insight

Maintain:

```python
current_vowels
```

When window moves:

```python
current_vowels += entering_char_is_vowel
current_vowels -= leaving_char_is_vowel
```

Update:

```python
answer = max(answer, current_vowels)
```

---

# Recognition Signals

Whenever you see:

### Signal 1

```text
Substring
```

### Signal 2

```text
Contiguous
```

### Signal 3

```text
Exactly length k
```

### Signal 4

```text
Maximum/Minimum over all windows
```

Think:

```text
Fixed-Size Sliding Window
```

immediately.

---

# Complexity Derivation

Each character:

* Enters window once
* Leaves window once

Total operations:

[
O(n)
]

Space:

Only counters and a vowel set.

[
O(1)
]

---

# Interview Trick

The theoretical maximum answer is:

```python
k
```

because a window of size `k` cannot contain more than `k` vowels.

So if:

```python
answer == k
```

we can return immediately.

This is a small optimization.

---


~~~
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowels = set("aeiou")  
        # ✅ Create a set of vowels for O(1) membership checks.

        count = 0  
        # ✅ Current count of vowels in the window.

        # Initialize the first window of size k
        for i in range(k):
            if s[i] in vowels:
                count += 1
        # ✅ Count vowels in the first k characters.

        answer = count  
        # ✅ Store the maximum vowels seen so far.

        # Slide the window from index k to end
        for right in range(k, len(s)):

            if s[right] in vowels:
                count += 1
            # ✅ Add the new character entering the window.

            if s[right - k] in vowels:
                count -= 1
            # ✅ Remove the character leaving the window.

            answer = max(answer, count)
            # ✅ Update maximum vowels seen in any window.

            if answer == k:
                return k
            # ✅ Early exit: if we ever hit k vowels, that’s the max possible.

        return answer
        # ✅ Return the best result after scanning all windows.

~~~
# 🔹 Block 2: Efficient Code

```python
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowels = set("aeiou")

        count = 0

        for i in range(k):
            if s[i] in vowels:
                count += 1

        answer = count

        for right in range(k, len(s)):

            if s[right] in vowels:
                count += 1

            if s[right - k] in vowels:
                count -= 1

            answer = max(answer, count)

            if answer == k:
                return k

        return answer
```

---

## Time Complexity

[
O(n)
]

Each character is processed at most twice.

---

## Space Complexity

[
O(1)
]

The vowel set size is fixed:

```python
{'a','e','i','o','u'}
```

---

## Interview Justification

> I maintain the number of vowels inside a fixed-size window of length `k`. When the window slides, I only update the count using the entering and leaving characters instead of recounting the entire window. This reduces the complexity from O(nk) to O(n).

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:
    def maxVowels(self, s: str, k: int) -> int:
        vowels = set("aeiou")

        count = 0

        for i in range(k):
            if s[i] in vowels:
                count += 1

        answer = count

        for right in range(k, len(s)):

            if s[right] in vowels:
                count += 1

            if s[right - k] in vowels:
                count -= 1

            answer = max(answer, count)

        return answer


s = "abciiidef"
k = 3

obj = Solution()

print(obj.maxVowels(s, k))
```

---

## Output

```python
3
```

---

# Detailed Dry Run

Input:

```python
s = "abciiidef"
k = 3
```

---

## Initial Window

```text
[a b c]
```

Vowels:

```python
a
```

Count:

```python
1
```

Answer:

```python
1
```

---

## Slide 1

Window:

```text
[b c i]
```

Leaving:

```python
a
```

Entering:

```python
i
```

Count:

```python
1 - 1 + 1 = 1
```

Answer:

```python
1
```

---

## Slide 2

Window:

```text
[c i i]
```

Leaving:

```python
b
```

Entering:

```python
i
```

Count:

```python
1 + 1 = 2
```

Answer:

```python
2
```

---

## Slide 3

Window:

```text
[i i i]
```

Leaving:

```python
c
```

Entering:

```python
i
```

Count:

```python
2 + 1 = 3
```

Answer:

```python
3
```

---

## Remaining Windows

```text
iid → 2
ide → 2
def → 1
```

Maximum:

```python
3
```

---

# Visual Understanding

```text
abc → 1
bci → 1
cii → 2
iii → 3   ← maximum
iid → 2
ide → 2
def → 1
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why use Sliding Window?

### Answer

Because every substring has the same size `k`, and consecutive windows overlap heavily. We only need to process one entering and one leaving character.

---

## Q2: Why is the solution O(n)?

### Answer

Each character enters and leaves the window at most once.

---

## Q3: Why not generate every substring?

### Answer

That approach takes:

[
O(nk)
]

because we repeatedly recount vowels.

---

## Q4: What makes this a Fixed-Size Sliding Window?

### Answer

The window length remains exactly:

```python
k
```

throughout the algorithm.

---

## Q5: Can we terminate early?

### Answer

Yes.

If:

```python
answer == k
```

we can immediately return because no window can contain more than `k` vowels.

---

## Q6: What Sliding Window variant is this?

### Answer

**Fixed-Size Sliding Window**

Same family as:

* LC 643 — Maximum Average Subarray I
* LC 1456 — Maximum Number of Vowels in a Substring of Given Length
* LC 1343 — Number of Subarrays of Size K and Average ≥ Threshold

---

# Pattern Extraction

For LC 1456, the reusable pattern is:

```text
Contiguous Substring
          +
Exactly Length k
          +
Maximum/Minimum Query
          =
Fixed-Size Sliding Window
```

### Master Template

```python
build first window

for right in range(k, n):

    remove left element
    add right element

    update answer
```

This template is one of the most frequently asked Sliding Window patterns because it teaches the fundamental idea of **incrementally maintaining information inside a fixed-size window instead of recomputing it from scratch**. ([AlgoMonster][3])

[1]: https://leetcode.com/problems/maximum-number-of-vowels-in-a-substring-of-given-length/?utm_source=chatgpt.com "Maximum Number of Vowels in a Substring of Given Length"
[2]: https://neetcode.io/solutions/maximum-number-of-vowels-in-a-substring-of-given-length?utm_source=chatgpt.com "1456. Maximum Number of Vowels in a Substring of Given ..."
[3]: https://algo.monster/liteproblems/1456?utm_source=chatgpt.com "1456. Maximum Number of Vowels in a Substring of Given ..."






# LC 2461 — Maximum Sum of Distinct Subarrays With Length K

**Pattern:** Fixed-Size Sliding Window + HashMap (Frequency Counter)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem asks:

> Find the maximum sum of a subarray of **exactly length `k`** such that **all elements are distinct**.

Example:

```python id="gs3a7s"
nums = [1,5,4,2,9,9,9]
k = 3
```

Possible windows:

```text id="0jlvsm"
[1,5,4] → distinct → sum = 10
[5,4,2] → distinct → sum = 11
[4,2,9] → distinct → sum = 15
[2,9,9] → duplicate
[9,9,9] → duplicate
```

Answer:

```python id="0x6mga"
15
```

---

# Why Brute Force Is Bad

Generate every window of size `k`.

For every window:

1. Compute sum
2. Check duplicates

```python id="r6zbke"
for each window:
    compute sum
    check uniqueness
```

---

## Complexity

Windows:

[
O(n)
]

Each window:

* Sum → O(k)
* Distinct check → O(k)

Total:

[
O(nk)
]

Too slow.

---

# Senior Engineer Mindset

Notice:

```text id="q7j31d"
[1,5,4]
 [5,4,2]
  [4,2,9]
```

Consecutive windows overlap heavily.

Only:

* One element leaves
* One element enters

This screams:

```text id="vb95od"
Fixed-Size Sliding Window
```

---

# But There Is One Extra Constraint

Unlike LC 1456:

```text id="u0z7ak"
Need maximum sum
```

AND

```text id="4vfiyr"
All elements must be distinct
```

Therefore we need:

### Window Sum

```python id="sok1hn"
window_sum
```

### Frequency Map

```python id="j39b97"
freq
```

to know whether duplicates exist.

---

# Core Insight

Maintain:

```python id="evx8ks"
window_sum
frequency dictionary
```

For every slide:

### Remove Left Element

```python id="wmft7z"
window_sum -= nums[left]
freq[nums[left]] -= 1
```

### Add Right Element

```python id="vfmslr"
window_sum += nums[right]
freq[nums[right]] += 1
```

---

# How to Check Distinctness

If:

```python id="fjg8nk"
len(freq) == k
```

then:

```text id="kpsjgj"
All elements are unique.
```

Why?

Because:

* Window size = k
* Number of distinct values = k

Therefore every element appears exactly once.

This is the key observation.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="ck0vyj"
Subarray
```

### Signal 2

```text id="lg6sfo"
Exactly length k
```

### Signal 3

```text id="e0al1d"
Maximum / Minimum
```

### Signal 4

```text id="h95x8f"
Distinct elements
```

Think:

```text id="fzwqrr"
Fixed Sliding Window
+
HashMap Frequency
```

---

# Complexity Derivation

Each element:

* Enters window once
* Leaves window once

HashMap operations:

[
O(1)
]

Total:

[
O(n)
]

Space:

Frequency dictionary can hold at most:

[
k
]

elements.

Therefore:

[
O(k)
]

---

# Interview Trick

Many candidates write:

```python id="c61mcf"
len(set(window))
```

inside the loop.

That becomes:

[
O(k)
]

per window.

The interviewer expects:

```text id="v8ssm0"
Incremental maintenance
```

using a frequency map.

---
~~~
from typing import List

class Solution:
    def maximumSubarraySum(self, nums: List[int], k: int) -> int:
        # Dictionary to store frequency of elements in the current window
        freq = {}
        
        # Running sum of the current window
        window_sum = 0
        
        # Variable to track the maximum sum of valid subarrays
        max_sum = 0
        
        # Left pointer for the sliding window
        left = 0

        # Iterate through the array with the right pointer
        for right in range(len(nums)):
            # Add the new element at 'right' into the window
            if nums[right] in freq:
                freq[nums[right]] += 1
            else:
                freq[nums[right]] = 1
            window_sum += nums[right]

            # If window size exceeds k, shrink from the left
            if right - left + 1 > k:
                # Decrease frequency of the element going out of the window
                freq[nums[left]] -= 1
                # If its frequency becomes 0, remove it from the dictionary
                if freq[nums[left]] == 0:
                    del freq[nums[left]]
                # Subtract its value from the running sum
                window_sum -= nums[left]
                # Move left pointer forward
                left += 1

            # If window size is exactly k and all elements are distinct
            if right - left + 1 == k and len(freq) == k:
                # Update maximum sum
                max_sum = max(max_sum, window_sum)

        # Return the maximum sum found, or 0 if no valid subarray exists
        return max_sum

~~~
# 🔹 Block 2: Efficient Code

```python id="3t8zsj"
from collections import defaultdict

class Solution:
    def maximumSubarraySum(self, nums, k):

        freq = defaultdict(int)

        window_sum = 0
        answer = 0
        left = 0

        for right in range(len(nums)):

            window_sum += nums[right]
            freq[nums[right]] += 1

            if right - left + 1 > k:

                outgoing = nums[left]

                window_sum -= outgoing
                freq[outgoing] -= 1

                if freq[outgoing] == 0:
                    del freq[outgoing]

                left += 1

            if right - left + 1 == k:

                if len(freq) == k:
                    answer = max(answer, window_sum)

        return answer
```

---

## Time Complexity

[
O(n)
]

Each element is added and removed once.

---

## Space Complexity

[
O(k)
]

Frequency dictionary stores at most `k` values.

---

## Interview Justification

> I maintain a fixed-size sliding window and keep track of both the window sum and element frequencies. Since frequencies are updated incrementally, each element is processed only once, giving O(n) time complexity.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="3b2ch0"
from collections import defaultdict


class Solution:
    def maximumSubarraySum(self, nums, k):

        freq = defaultdict(int)

        window_sum = 0
        answer = 0
        left = 0

        for right in range(len(nums)):

            window_sum += nums[right]
            freq[nums[right]] += 1

            if right - left + 1 > k:

                outgoing = nums[left]

                window_sum -= outgoing
                freq[outgoing] -= 1

                if freq[outgoing] == 0:
                    del freq[outgoing]

                left += 1

            if right - left + 1 == k:

                if len(freq) == k:
                    answer = max(answer, window_sum)

        return answer


nums = [1,5,4,2,9,9,9]
k = 3

obj = Solution()

print(obj.maximumSubarraySum(nums, k))
```

---

## Output

```python id="zj4qks"
15
```

---

# Detailed Dry Run

Input:

```python id="e7s2yu"
nums = [1,5,4,2,9,9,9]
k = 3
```

---

## Window 1

```text id="uwjlwm"
[1,5,4]
```

Sum:

```python id="fkhm5u"
10
```

Frequency:

```python id="ey9d93"
{1:1,5:1,4:1}
```

Distinct:

```python id="vqvnhf"
len(freq) = 3
```

Answer:

```python id="q0kksx"
10
```

---

## Window 2

Slide:

```text id="ukjrfy"
[5,4,2]
```

Remove:

```python id="y9k2wx"
1
```

Add:

```python id="w27vcd"
2
```

Sum:

```python id="jlwm8n"
11
```

Distinct:

```python id="4xykna"
True
```

Answer:

```python id="ytjcdm"
11
```

---

## Window 3

Slide:

```text id="lkvnlw"
[4,2,9]
```

Remove:

```python id="ub6sgs"
5
```

Add:

```python id="ys2v34"
9
```

Sum:

```python id="yhq82q"
15
```

Distinct:

```python id="djlwm7"
True
```

Answer:

```python id="ft8z0w"
15
```

---

## Window 4

```text id="xhkycf"
[2,9,9]
```

Frequency:

```python id="bwm0s4"
{2:1,9:2}
```

Distinct count:

```python id="nvay0l"
2
```

Not valid.

Ignore.

---

## Window 5

```text id="6mybup"
[9,9,9]
```

Frequency:

```python id="3glx9l"
{9:3}
```

Not distinct.

Ignore.

---

Final Answer:

```python id="p1dzyj"
15
```

---

# Visual Understanding

```text id="sl6u1a"
[1,5,4] → sum=10 ✅
[5,4,2] → sum=11 ✅
[4,2,9] → sum=15 ✅
[2,9,9] → duplicate ❌
[9,9,9] → duplicate ❌
```

Maximum:

```python id="07mqww"
15
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why use Sliding Window?

### Answer

Because the window size remains exactly `k`, and consecutive windows overlap heavily.

---

## Q2: Why use a HashMap?

### Answer

To maintain frequencies incrementally and determine whether the current window contains duplicates.

---

## Q3: Why does `len(freq) == k` imply all elements are distinct?

### Answer

The window size is exactly `k`.

If there are also `k` distinct values, every element must occur exactly once.

---

## Q4: Why not use `set(window)` every iteration?

### Answer

Constructing a set costs:

[
O(k)
]

per window, resulting in:

[
O(nk)
]

instead of:

[
O(n)
]

---

## Q5: What is the hardest part of this problem?

### Answer

Maintaining both:

```python id="0zow7k"
window_sum
frequency map
```

incrementally.

---

## Q6: What Sliding Window category is this?

### Answer

**Fixed-Size Sliding Window + Frequency Map**

Same family as:

* LC 1456 — Maximum Number of Vowels
* LC 2461 — Maximum Sum of Distinct Subarrays With Length K
* LC 1343 — Number of Subarrays of Size K and Average ≥ Threshold

---

# Pattern Extraction

For LC 2461, the reusable pattern is:

```text id="kr4v8l"
Subarray
        +
Exactly Length k
        +
Distinct Constraint
        +
Maximum/Minimum Query
        =
Fixed Sliding Window
        +
HashMap Frequency
```

---

# Master Template

```python id="n0tqzi"
add incoming element
update frequency
update window information

if window too large:
    remove outgoing element
    update frequency

if window size == k:
    if condition satisfied:
        update answer
```

This is one of the most important interview templates because it teaches how to combine:

```text id="rt9iyv"
Sliding Window
+
Running Sum
+
HashMap Frequencies
```

which reappears in many medium and hard string/array interview problems.




# ===================================================================================================================================================================================
# ⭐ Dynamic Window

4. LC 209 — Minimum Size Subarray Sum
5. LC 3 — Longest Substring Without Repeating Characters
6. LC 904 — Fruit Into Baskets
7. LC 1004 — Max Consecutive Ones III
8. LC 424 — Longest Repeating Character Replacement
9. LC 713 — Subarray Product Less Than K
10. LC 438 — Find All Anagrams in a String


# LC 209 — Minimum Size Subarray Sum

**Pattern:** Variable-Size Sliding Window (Expand → Satisfy → Shrink)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem asks:

> Find the minimum length of a contiguous subarray whose sum is greater than or equal to `target`.

Example:

```python id="crdtrv"
target = 7
nums = [2,3,1,2,4,3]
```

Answer:

```python id="2ukw90"
2
```

because:

```python id="12ldiv"
[4,3]
```

has:

```python id="m9b4x1"
sum = 7
length = 2
```

---

# Why This Is NOT a Fixed Window Problem

In LC 1456:

```text id="ixg7j7"
Window size = exactly k
```

In LC 2461:

```text id="4t2vxw"
Window size = exactly k
```

Here:

```text id="6r98cu"
Window size changes dynamically.
```

We don't know the answer length beforehand.

Therefore:

```text id="uk2by5"
Variable-Size Sliding Window
```

---

# Brute Force Thinking

Generate every subarray.

```python id="3vb36g"
for i in range(n):
    total = 0

    for j in range(i, n):
        total += nums[j]

        if total >= target:
            update answer
```

---

## Complexity

Outer loop:

[
O(n)
]

Inner loop:

[
O(n)
]

Total:

[
O(n^2)
]

Too slow.

---

# Senior Engineer Mindset

The numbers are:

```text id="7gyqag"
All positive.
```

This is the most important observation.

Because all numbers are positive:

### Expanding Window

```text id="09y7ck"
Sum increases.
```

### Shrinking Window

```text id="lyrly4"
Sum decreases.
```

This monotonic behavior makes Sliding Window possible.

---

# The Core Idea

Maintain:

```python id="r2x0nd"
window_sum
left
right
```

---

## Step 1 — Expand

Keep adding numbers:

```python id="8v0h4d"
window_sum += nums[right]
```

until:

```python id="q6shry"
window_sum >= target
```

---

## Step 2 — Shrink

Once condition is satisfied:

```text id="zv27t6"
Try making the window smaller.
```

Because:

```text id="q8rq4s"
We want minimum length.
```

So:

```python id="6q8tkk"
answer = min(answer, window_length)

window_sum -= nums[left]
left += 1
```

Continue shrinking while:

```python id="lglqav"
window_sum >= target
```

---

# This Is The Entire Pattern

```text id="ub90gl"
Expand
Expand
Expand
Condition Satisfied
Shrink
Shrink
Break
Expand Again
```

This exact flow appears repeatedly in interview questions.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="syc4q6"
Subarray
```

### Signal 2

```text id="w2o4r8"
Contiguous
```

### Signal 3

```text id="r4t77q"
Positive numbers
```

### Signal 4

```text id="lpkxpj"
Minimum or Maximum window
```

Think:

```text id="hm5m2o"
Variable Sliding Window
```

---

# Why Positive Numbers Matter

Suppose negatives existed:

```python id="pdq7q5"
[2,-5,10]
```

Removing:

```python id="2n7bs8"
-5
```

actually:

```text id="jlwmgw"
increases the sum
```

The monotonic property breaks.

Sliding Window would fail.

This is why the constraint:

```text id="f9lm6o"
Positive integers only
```

is critical.

---

# Complexity Derivation

Each element:

* Enters window once
* Leaves window once

Therefore:

[
O(n)
]

Space:

Only variables:

[
O(1)
]

---

# Interview Trick

If asked:

> Why is it O(n) and not O(n²)?

Answer:

> Although there are nested loops, both pointers move only forward. Each index is visited at most twice—once by the right pointer and once by the left pointer.

This is the standard Sliding Window proof.

---

# 🔹 Block 2: Efficient Code

```python id="ntfwf6"
class Solution:
    def minSubArrayLen(self, target, nums):

        left = 0
        window_sum = 0
        answer = float("inf")

        for right in range(len(nums)):

            window_sum += nums[right]

            while window_sum >= target:

                length = right - left + 1
                answer = min(answer, length)

                window_sum -= nums[left]
                left += 1

        return 0 if answer == float("inf") else answer
```

---

## Time Complexity

[
O(n)
]

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> Since all numbers are positive, expanding the window always increases the sum and shrinking always decreases it. Therefore I can maintain a variable-size window and greedily shrink whenever the target condition is satisfied.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="fjlwm4"
class Solution:
    def minSubArrayLen(self, target, nums):

        left = 0
        window_sum = 0
        answer = float("inf")

        for right in range(len(nums)):

            window_sum += nums[right]

            while window_sum >= target:

                answer = min(answer, right - left + 1)

                window_sum -= nums[left]
                left += 1

        return 0 if answer == float("inf") else answer


target = 7
nums = [2,3,1,2,4,3]

obj = Solution()

print(obj.minSubArrayLen(target, nums))
```

---

## Output

```python id="m7w9ha"
2
```

---

# Detailed Dry Run

Input:

```python id="ikd0p4"
target = 7
nums = [2,3,1,2,4,3]
```

---

## right = 0

Window:

```text id="tyg85x"
[2]
```

Sum:

```python id="7ed4kh"
2
```

Less than 7.

Expand.

---

## right = 1

Window:

```text id="mpv85q"
[2,3]
```

Sum:

```python id="qfghj4"
5
```

Expand.

---

## right = 2

Window:

```text id="uw4t4q"
[2,3,1]
```

Sum:

```python id="hsjlwm"
6
```

Expand.

---

## right = 3

Window:

```text id="g2cy3o"
[2,3,1,2]
```

Sum:

```python id="77jtzl"
8
```

Condition satisfied.

Length:

```python id="5a67nl"
4
```

Answer:

```python id="r1bpb1"
4
```

Shrink.

Remove:

```python id="03h0yu"
2
```

New sum:

```python id="tql8mt"
6
```

Stop shrinking.

---

## right = 4

Add:

```python id="jlwm4q"
4
```

Window:

```text id="jlwm0w"
[3,1,2,4]
```

Sum:

```python id="jlwmfj"
10
```

Length:

```python id="jlwm93"
4
```

Shrink.

Remove:

```python id="jlwmcs"
3
```

Sum:

```python id="jlwmgi"
7
```

Still valid.

Length:

```python id="jlwm6b"
3
```

Answer:

```python id="jlwmga"
3
```

Shrink again.

Remove:

```python id="jljwma"
1
```

Sum:

```python id="jlwmu0"
6
```

Stop.

---

## right = 5

Add:

```python id="jlwm7p"
3
```

Window:

```text id="jlwmzl"
[2,4,3]
```

Sum:

```python id="jlwm8n"
9
```

Length:

```python id="jlwmc2"
3
```

Shrink.

Remove:

```python id="jlwmnt"
2
```

Window:

```text id="jlwm91"
[4,3]
```

Sum:

```python id="jlwmvl"
7
```

Length:

```python id="jlwmjt"
2
```

Answer:

```python id="jlwmhk"
2
```

Shrink again.

Remove:

```python id="jlwm9m"
4
```

Sum:

```python id="jlwmjq"
3
```

Stop.

---

Final Answer:

```python id="jlwmj0"
2
```

---

# Visual Understanding

```text id="7jlwmu"
[2]           sum=2
[2,3]         sum=5
[2,3,1]       sum=6
[2,3,1,2]     sum=8  ✅

Shrink

[3,1,2,4]     sum=10 ✅
[1,2,4]       sum=7  ✅

Shrink

[2,4,3]       sum=9  ✅
[4,3]         sum=7  ✅ ← minimum length
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why does Sliding Window work?

### Answer

Because all numbers are positive, making the window sum monotonic during expansion and contraction.

---

## Q2: Why do we shrink immediately after reaching the target?

### Answer

Because we are looking for the minimum valid window.

---

## Q3: Why is the complexity O(n)?

### Answer

Each pointer moves only forward, and every element enters and leaves the window at most once.

---

## Q4: Would this work with negative numbers?

### Answer

No.

Negative numbers break the monotonic behavior of the sum.

---

## Q5: What Sliding Window variant is this?

### Answer

**Variable-Size Sliding Window**

---

## Q6: What is the hardest insight?

### Answer

Recognizing that:

```text id="jlwmm0"
Positive numbers
+
Minimum/Maximum window
=
Variable Sliding Window
```

---

# Pattern Extraction

For LC 209, the reusable pattern is:

```text id="jlwm44"
Contiguous Subarray
        +
Positive Numbers
        +
Minimum/Maximum Window
        =
Variable Sliding Window
```

---

# Master Template

```python id="jlwm5s"
left = 0
window_info = 0

for right in range(n):

    add nums[right]

    while condition_satisfied:

        update_answer()

        remove nums[left]
        left += 1
```

This template reappears in:

* LC 209 — Minimum Size Subarray Sum
* LC 904 — Fruit Into Baskets
* LC 1004 — Max Consecutive Ones III
* LC 424 — Longest Repeating Character Replacement
* LC 76 — Minimum Window Substring

and is one of the most important **Variable Sliding Window** patterns in interviews.

# LC 3 — Longest Substring Without Repeating Characters

**Pattern:** Variable-Size Sliding Window + HashSet (Uniqueness Constraint)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem asks:

> Find the length of the longest substring without repeating characters.

Example:

```python id="l9a2ks"
s = "abcabcbb"
```

Possible valid substrings:

```text id="zgqv3d"
"a"       → 1
"ab"      → 2
"abc"     → 3
"abca"    → duplicate
```

Answer:

```python id="pcv6u7"
3
```

because:

```python id="wgnr85"
"abc"
```

has length:

```python id="6rbyui"
3
```

---

# Why This Is NOT a Fixed Window Problem

In LC 1456:

```text id="zdf4fz"
Window size = exactly k
```

In LC 2461:

```text id="y75o80"
Window size = exactly k
```

Here:

```text id="ftjlwm"
Window size changes continuously.
```

We want:

```text id="dkvlrt"
Longest valid window.
```

This is a:

```text id="z7tjqy"
Variable-Size Sliding Window
```

problem.

---

# Brute Force Thinking

Generate every substring.

For every substring:

Check whether characters repeat.

```python id="mjlwm4"
for i in range(n):
    for j in range(i, n):
        check duplicates
```

---

## Complexity

Substrings:

[
O(n^2)
]

Duplicate checking:

[
O(n)
]

Total:

[
O(n^3)
]

Even with optimization:

[
O(n^2)
]

Too slow.

---

# Senior Engineer Mindset

The question is really asking:

```text id="hjlwmn"
Maintain a window
where all characters are unique.
```

As long as:

```text id="yjlwm8"
No duplicates
```

we can expand.

The moment:

```text id="jlwmz4"
Duplicate appears
```

we must shrink.

---

# Core Insight

Maintain:

```python id="jlwmce"
left
right
seen_characters
```

---

## Expand

Keep adding:

```python id="jlwmo8"
s[right]
```

into the window.

---

## Duplicate Appears

Suppose:

```python id="jlwmh3"
s = "abca"
```

Window:

```text id="jlwmfk"
[a b c a]
```

Duplicate:

```python id="jlwms7"
a
```

appears.

We must shrink:

```text id="jlwm90"
Remove characters
from the left
until duplicate disappears.
```

---

# This Is The Entire Pattern

```text id="jlwmx1"
Expand
Expand
Expand
Duplicate Found
Shrink
Duplicate Removed
Expand Again
```

This exact flow appears repeatedly in medium and hard interview questions.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="jlwm42"
Substring
```

### Signal 2

```text id="jlwmds"
Contiguous
```

### Signal 3

```text id="jlwm8c"
Longest
```

### Signal 4

```text id="jlwm1k"
Distinct / Unique / No Repeating
```

Think:

```text id="jlwmb5"
Variable Sliding Window
+
HashSet
```

immediately.

---

# Why HashSet?

We need:

```text id="jlwm5v"
O(1)
```

operations:

* Add character
* Remove character
* Check duplicate

A set provides all three.

---

# Complexity Derivation

Every character:

* Enters window once
* Leaves window once

Therefore:

[
O(n)
]

Space:

At most all unique characters:

[
O(min(n,charset))
]

For English letters:

[
O(1)
]

Generally:

[
O(n)
]

---

# Interview Trick

If interviewer asks:

> Why is it O(n) and not O(n²)?

Answer:

> Although there is a nested while loop, the left pointer never moves backward. Each character is inserted and removed from the set at most once.

This is the standard Sliding Window proof.

---

# 🔹 Block 2: Efficient Code

```python id="jlwmoq"
class Solution:
    def lengthOfLongestSubstring(self, s):

        seen = set()

        left = 0
        answer = 0

        for right in range(len(s)):

            while s[right] in seen:
                seen.remove(s[left])
                left += 1

            seen.add(s[right])

            answer = max(
                answer,
                right - left + 1
            )

        return answer
```

---

## Time Complexity

[
O(n)
]

---

## Space Complexity

[
O(min(n,charset))
]

---

## Interview Justification

> I maintain a variable-size window containing only unique characters. Whenever a duplicate enters the window, I shrink from the left until the duplicate is removed. Since each character enters and leaves the set at most once, the solution runs in O(n).

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="jlwmym"
class Solution:
    def lengthOfLongestSubstring(self, s):

        seen = set()

        left = 0
        answer = 0

        for right in range(len(s)):

            while s[right] in seen:
                seen.remove(s[left])
                left += 1

            seen.add(s[right])

            answer = max(
                answer,
                right - left + 1
            )

        return answer


s = "abcabcbb"

obj = Solution()

print(obj.lengthOfLongestSubstring(s))
```

---

## Output

```python id="jlwm4v"
3
```

---

# Detailed Dry Run

Input:

```python id="jlwmyn"
s = "abcabcbb"
```

---

## right = 0

Window:

```text id="jlwmlt"
[a]
```

Set:

```python id="jlwmu8"
{'a'}
```

Length:

```python id="jlwm1n"
1
```

Answer:

```python id="jlwmy5"
1
```

---

## right = 1

Window:

```text id="jlwmdx"
[a b]
```

Length:

```python id="jlwmsh"
2
```

Answer:

```python id="jlwmo0"
2
```

---

## right = 2

Window:

```text id="jlwm3v"
[a b c]
```

Length:

```python id="jlwm9w"
3
```

Answer:

```python id="jlwmuw"
3
```

---

## right = 3

Character:

```python id="jlwmd0"
a
```

Duplicate.

Window:

```text id="jlwm9a"
[a b c a]
```

Shrink:

Remove:

```python id="jlwm7v"
a
```

Window:

```text id="jlwmsk"
[b c]
```

Add:

```python id="jlwmzf"
a
```

Window:

```text id="jlwmg9"
[b c a]
```

Length:

```python id="jlwm76"
3
```

Answer:

```python id="jlwmo1"
3
```

---

Continue.

Longest valid windows:

```python id="jlwmbf"
"abc"
"bca"
"cab"
```

Length:

```python id="jlwmdj"
3
```

---

Final Answer:

```python id="jlwmdo"
3
```

---

# Visual Understanding

```text id="jlwmbv"
a        → 1
ab       → 2
abc      → 3 ✅
abca     → duplicate
bca      → 3
bcab     → duplicate
cab      → 3
```

Maximum:

```python id="jlwm14"
3
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why use Sliding Window?

### Answer

Because we need the longest contiguous substring satisfying a dynamic uniqueness constraint.

---

## Q2: Why use a HashSet?

### Answer

It provides:

```text id="jlwmk5"
Insert  → O(1)
Delete  → O(1)
Lookup  → O(1)
```

which is ideal for detecting duplicates.

---

## Q3: Why shrink when a duplicate appears?

### Answer

Because the current window becomes invalid and cannot contribute to the answer until uniqueness is restored.

---

## Q4: Why is the complexity O(n)?

### Answer

Each character enters and leaves the window at most once.

---

## Q5: Could we solve it using nested loops?

### Answer

Yes.

But that would require:

[
O(n^2)
]

or worse.

---

## Q6: What Sliding Window category is this?

### Answer

**Variable-Size Sliding Window + HashSet**

---

# Pattern Extraction

For LC 3, the reusable pattern is:

```text id="jlwm3n"
Substring
        +
Longest Window
        +
Distinct Constraint
        =
Variable Sliding Window
        +
HashSet
```

---

# Master Template

```python id="jlwm2v"
left = 0
window = set()

for right in range(n):

    while violation_exists:
        remove_from_window()
        left += 1

    add_to_window()

    update_answer()
```

---

# Sliding Window Evolution So Far

| Problem | Pattern                   |
| ------- | ------------------------- |
| LC 1456 | Fixed Window              |
| LC 2461 | Fixed Window + HashMap    |
| LC 209  | Variable Window           |
| LC 3    | Variable Window + HashSet |

This progression teaches one of the most important interview realizations:

```text id="jlwmrk"
Fixed Size Constraint
        →
Fixed Sliding Window

Dynamic Constraint
        →
Variable Sliding Window

Distinct Constraint
        →
Sliding Window + HashSet/HashMap
```

LC 3 is one of the highest-frequency Sliding Window questions and serves as the foundation for harder problems like:

* LC 424 — Longest Repeating Character Replacement
* LC 76 — Minimum Window Substring
* LC 159 — Longest Substring with At Most Two Distinct Characters
* LC 340 — Longest Substring with At Most K Distinct Characters

# 904
# LC 904 — Fruit Into Baskets

**Pattern:** Variable-Size Sliding Window + HashMap (At Most K Distinct)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem says:

> You have two baskets.
>
> Each basket can hold only one fruit type.
>
> Pick fruits from a contiguous subarray.

This translates to:

```text id="ly4gx3"
Find the longest subarray
containing at most 2 distinct numbers.
```

Example:

```python id="v6eh8z"
fruits = [1,2,1]
```

Answer:

```python id="0b5nlz"
3
```

because:

```python id="3f6e7s"
[1,2,1]
```

contains:

```text id="7vv1pm"
Fruit types = {1,2}
```

Exactly two types.

---

# The Hidden Translation

Interviewers intentionally disguise the problem.

They say:

```text id="r73f8m"
Basket
Fruit
Picking
```

But a senior engineer immediately translates:

```text id="c8mqk4"
Longest Subarray
At Most 2 Distinct Values
```

This translation skill is extremely important.

---

# Why This Is Variable Sliding Window

We don't know:

```text id="1jlulz"
window length
```

beforehand.

The answer could be:

```python id="79jlwm"
1
3
10
100
```

depending on the input.

Therefore:

```text id="wzg52o"
Variable-Size Sliding Window
```

---

# Brute Force Thinking

Generate every subarray.

For each subarray:

Count distinct fruit types.

```python id="c9shut"
for i:
    for j:
        count distinct fruits
```

---

## Complexity

Subarrays:

[
O(n^2)
]

Distinct counting:

up to

[
O(n)
]

Total:

[
O(n^3)
]

Even optimized:

[
O(n^2)
]

Too slow.

---

# Senior Engineer Mindset

Maintain:

```text id="cjlwm1"
A window that is always valid.
```

Valid means:

```python id="jlwmk9"
distinct_fruits <= 2
```

---

# Core Idea

Expand:

```python id="jlwm4p"
right
```

Add fruits.

If:

```python id="jlwm4m"
distinct_fruits > 2
```

window becomes invalid.

Shrink:

```python id="jlwm9k"
left
```

until:

```python id="jlwm0z"
distinct_fruits <= 2
```

again.

Update answer continuously.

---

# Why HashMap?

We need to know:

1. How many fruit types exist.
2. When a fruit completely disappears.

HashMap:

```python id="jlwmf7"
fruit -> frequency
```

solves both.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="jlwmj2"
Subarray
```

### Signal 2

```text id="jlwm71"
Longest
```

### Signal 3

```text id="jlwm1x"
At most K distinct
```

Think:

```text id="jlwmrh"
Variable Sliding Window
+
HashMap Frequency
```

immediately.

---

# The Most Important Pattern

This problem introduces one of the most reusable interview templates:

```text id="jlwmnb"
Longest Subarray
with At Most K Distinct Elements
```

This pattern appears everywhere.

---

# Complexity Derivation

Each fruit:

* Enters window once
* Leaves window once

HashMap operations:

[
O(1)
]

Total:

[
O(n)
]

Space:

At most:

```python id="jlwm3a"
3
```

keys exist temporarily.

Generally:

[
O(K)
]

For this problem:

[
O(1)
]

---

# Interview Trick

Many candidates think:

```text id="jlwmhj"
Exactly 2 fruit types
```

Wrong.

The condition is:

```text id="jlwmy7"
At most 2 fruit types.
```

Example:

```python id="jlwmr2"
[1,1,1]
```

Answer:

```python id="jlwmim"
3
```

Only one fruit type.

Still valid.

---

# 🔹 Block 2: Efficient Code
~~~
from typing import List

class Solution:
    def totalFruit(self, fruits: List[int]) -> int:
        left = 0                 # ✅ Left pointer of sliding window
        count = {}               # ✅ Dictionary to track fruit frequencies
        max_len = 0              # ✅ Stores the maximum length of valid window

        # Edge case: if input is empty, return 0
        if not fruits:
            return 0 

        # Expand window with right pointer
        for right in range(len(fruits)):
            # ✅ Add current fruit to frequency map
            count[fruits[right]] = count.get(fruits[right], 0) + 1

            # ✅ Shrink window if more than 2 fruit types
            while len(count) > 2:
                count[fruits[left]] -= 1   # remove outgoing fruit
                if count[fruits[left]] == 0:
                    del count[fruits[left]]  # delete fruit type completely
                left += 1                   # move left pointer forward

            # ✅ Update maximum window size
            max_len = max(max_len, right - left + 1)

        return max_len   # ✅ Return the longest valid subarray length

~~~
```python id="jlwm4u"
from collections import defaultdict

class Solution:
    def totalFruit(self, fruits):

        freq = defaultdict(int)

        left = 0
        answer = 0

        for right in range(len(fruits)):

            freq[fruits[right]] += 1

            while len(freq) > 2:

                outgoing = fruits[left]

                freq[outgoing] -= 1

                if freq[outgoing] == 0:
                    del freq[outgoing]

                left += 1

            answer = max(
                answer,
                right - left + 1
            )

        return answer
```

---

## Time Complexity

[
O(n)
]

---

## Space Complexity

[
O(K)
]

For this problem:

[
O(1)
]

because:

```python id="jlwm89"
K = 2
```

---

## Interview Justification

> I maintain a variable-size window containing at most two fruit types. Whenever the window becomes invalid, I shrink it until it again contains at most two distinct fruits. Since each element enters and leaves the window at most once, the solution runs in O(n).

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="jlwm0y"
from collections import defaultdict


class Solution:
    def totalFruit(self, fruits):

        freq = defaultdict(int)

        left = 0
        answer = 0

        for right in range(len(fruits)):

            freq[fruits[right]] += 1

            while len(freq) > 2:

                outgoing = fruits[left]

                freq[outgoing] -= 1

                if freq[outgoing] == 0:
                    del freq[outgoing]

                left += 1

            answer = max(
                answer,
                right - left + 1
            )

        return answer


fruits = [1,2,3,2,2]

obj = Solution()

print(obj.totalFruit(fruits))
```

---

## Output

```python id="jlwm6s"
4
```

---

# Detailed Dry Run

Input:

```python id="jlwm55"
fruits = [1,2,3,2,2]
```

---

## right = 0

Window:

```text id="jlwmke"
[1]
```

Map:

```python id="jlwm7q"
{1:1}
```

Answer:

```python id="jlwmt5"
1
```

---

## right = 1

Window:

```text id="jlwmr0"
[1,2]
```

Map:

```python id="jlwma0"
{1:1,2:1}
```

Answer:

```python id="jlwmyw"
2
```

---

## right = 2

Window:

```text id="jlwmiz"
[1,2,3]
```

Map:

```python id="jlwmbo"
{1:1,2:1,3:1}
```

Invalid.

Distinct fruits:

```python id="jlwm6q"
3
```

Shrink.

Remove:

```python id="jlwmd4"
1
```

Map:

```python id="jlwm4s"
{2:1,3:1}
```

Window:

```text id="jlwm4t"
[2,3]
```

---

## right = 3

Window:

```text id="jlwmvo"
[2,3,2]
```

Map:

```python id="jlwmq7"
{2:2,3:1}
```

Answer:

```python id="jlwmo4"
3
```

---

## right = 4

Window:

```text id="jlwmlm"
[2,3,2,2]
```

Map:

```python id="jlwm1s"
{2:3,3:1}
```

Answer:

```python id="jlwmsl"
4
```

---

Final Answer:

```python id="jlwmr9"
4
```

---

# Visual Understanding

```text id="jlwm2v"
[1]           ✅
[1,2]         ✅
[1,2,3]       ❌

Shrink

[2,3]         ✅
[2,3,2]       ✅
[2,3,2,2]     ✅
```

Maximum:

```python id="jlwmqq"
4
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What is the hidden translation of this problem?

### Answer

```text id="jlwm8r"
Longest subarray
with at most two distinct numbers.
```

---

## Q2: Why use Sliding Window?

### Answer

Because we need the longest contiguous subarray satisfying a dynamic constraint.

---

## Q3: Why use a HashMap?

### Answer

We need frequencies to know when a fruit type completely leaves the window.

---

## Q4: Why shrink when `len(freq) > 2`?

### Answer

Because the window becomes invalid and cannot contribute to the answer.

---

## Q5: Why is the complexity O(n)?

### Answer

Each fruit enters and leaves the window at most once.

---

## Q6: What Sliding Window category is this?

### Answer

**Variable-Size Sliding Window + HashMap (At Most K Distinct)**

---

# Pattern Extraction

For LC 904, the reusable pattern is:

```text id="jlwmbc"
Longest Subarray
        +
At Most K Distinct Elements
        =
Variable Sliding Window
        +
HashMap Frequency
```

---

# Master Template

```python id="jlwmnh"
left = 0
freq = {}

for right in range(n):

    add(nums[right])

    while window_invalid:
        remove(nums[left])
        left += 1

    update_answer()
```

---

# Sliding Window Progression So Far

| Problem | Pattern                                        |
| ------- | ---------------------------------------------- |
| LC 1456 | Fixed Window                                   |
| LC 2461 | Fixed Window + HashMap                         |
| LC 209  | Variable Window                                |
| LC 3    | Variable Window + HashSet                      |
| LC 904  | Variable Window + HashMap (At Most K Distinct) |

This pattern directly leads to:

* LC 159 — Longest Substring with At Most Two Distinct Characters
* LC 340 — Longest Substring with At Most K Distinct Characters
* LC 424 — Longest Repeating Character Replacement
* LC 76 — Minimum Window Substring

LC 904 is one of the most important **At Most K Distinct** templates in interview preparation.


# 1004
# LC 1004 — Max Consecutive Ones III

**Pattern:** Variable-Size Sliding Window (At Most K Violations)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem says:

> You can flip at most `k` zeros into ones.

Find:

> The maximum number of consecutive ones.

Example:

```python
nums = [1,1,1,0,0,0,1,1,1,1,0]
k = 2
```

Answer:

```python
6
```

because we can flip:

```text
[1,1,1,0,0,0,1,1,1,1,0]
          ↑     ↑
```

to get:

```text
1 1 1 1 1 0 1 1 1 1 0
```

Longest consecutive ones:

```text
1 1 1 1 1 1
```

Length:

```python
6
```

---

# Hidden Translation

Interviewers say:

```text
Flip zeros
Consecutive ones
```

A senior engineer immediately translates:

```text
Longest subarray
containing at most k zeros
```

This translation is the entire problem.

---

# Why This Is Variable Sliding Window

We don't know the answer length beforehand.

The valid window could be:

```python
2
5
100
1000
```

depending on the input.

Therefore:

```text
Variable-Size Sliding Window
```

---

# Brute Force Thinking

Generate every subarray.

For every subarray:

Count zeros.

```python
for i:
    for j:
        count_zeros()
```

---

## Complexity

Subarrays:

[
O(n^2)
]

Counting zeros:

up to

[
O(n)
]

Total:

[
O(n^3)
]

Even optimized:

[
O(n^2)
]

Too slow.

---

# Senior Engineer Mindset

Maintain:

```text
A window that is always valid.
```

Valid means:

```python
zeros_in_window <= k
```

---

# Core Idea

Expand:

```python
right
```

Add numbers.

If:

```python
zeros > k
```

window becomes invalid.

Shrink:

```python
left
```

until:

```python
zeros <= k
```

again.

Keep updating the maximum length.

---

# Why We Only Count Zeros

Many beginners track:

```python
ones
zeros
window_length
```

Unnecessary.

Only:

```python
zero_count
```

matters.

Because:

```text
At most k zeros
```

is the only constraint.

Everything else can remain implicit.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text
Subarray
```

### Signal 2

```text
Longest
```

### Signal 3

```text
At most k changes
```

### Signal 4

```text
At most k violations
```

Think:

```text
Variable Sliding Window
+
Violation Counter
```

immediately.

---

# The Most Important Insight

This problem teaches one of the highest-frequency interview templates:

```text
Longest Window
with At Most K Bad Elements
```

The "bad element" here is:

```python
0
```

---

# Complexity Derivation

Each element:

* Enters window once
* Leaves window once

Total:

[
O(n)
]

Space:

Only:

```python
left
right
zero_count
answer
```

Therefore:

[
O(1)
]

---

# Interview Trick

If interviewer asks:

> Why don't you actually flip the zeros?

Answer:

> Flipping isn't necessary. We only need the window length. Tracking the number of zeros tells us whether the window is valid.

That answer sounds senior-level.

---

# 🔹 Block 2: Efficient Code


~~~
class Solution:
    def longestOnes(self, nums: List[int], k: int) -> int:
        left = 0              # ✅ Left pointer of sliding window
        zero_count = 0        # ✅ Tracks how many zeros are in the window
        answer = 0            # ✅ Stores the maximum length found

        # Expand window with right pointer
        for right in range(len(nums)):

            # ✅ If current element is zero, increment zero_count
            if nums[right] == 0:
                zero_count += 1

            # ✅ Shrink window until zero_count <= k
            while zero_count > k:
                if nums[left] == 0:
                    zero_count -= 1
                left += 1

            # ✅ Update maximum window length
            answer = max(answer, right - left + 1)

        return answer   # ✅ Return the longest valid subarray length

~~~
```python
class Solution:
    def longestOnes(self, nums, k):

        left = 0
        zero_count = 0
        answer = 0

        for right in range(len(nums)):

            if nums[right] == 0:
                zero_count += 1

            while zero_count > k:

                if nums[left] == 0:
                    zero_count -= 1

                left += 1

            answer = max(
                answer,
                right - left + 1
            )

        return answer
```

---

## Time Complexity

[
O(n)
]

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I maintain a variable-size window containing at most `k` zeros. Whenever the number of zeros exceeds `k`, I shrink the window until it becomes valid again. Since both pointers move only forward, the solution runs in O(n).

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:
    def longestOnes(self, nums, k):

        left = 0
        zero_count = 0
        answer = 0

        for right in range(len(nums)):

            if nums[right] == 0:
                zero_count += 1

            while zero_count > k:

                if nums[left] == 0:
                    zero_count -= 1

                left += 1

            answer = max(
                answer,
                right - left + 1
            )

        return answer


nums = [1,1,1,0,0,0,1,1,1,1,0]
k = 2

obj = Solution()

print(obj.longestOnes(nums, k))
```

---

## Output

```python
6
```

---

# Detailed Dry Run

Input:

```python
nums = [1,1,1,0,0,0,1,1,1,1,0]
k = 2
```

---

## right = 0

Window:

```text
[1]
```

Zeros:

```python
0
```

Answer:

```python
1
```

---

## right = 1

Window:

```text
[1,1]
```

Zeros:

```python
0
```

Answer:

```python
2
```

---

## right = 2

Window:

```text
[1,1,1]
```

Zeros:

```python
0
```

Answer:

```python
3
```

---

## right = 3

Window:

```text
[1,1,1,0]
```

Zeros:

```python
1
```

Answer:

```python
4
```

---

## right = 4

Window:

```text
[1,1,1,0,0]
```

Zeros:

```python
2
```

Answer:

```python
5
```

---

## right = 5

Window:

```text
[1,1,1,0,0,0]
```

Zeros:

```python
3
```

Invalid.

Shrink:

Remove:

```python
1
1
1
0
```

Window becomes:

```text
[0,0]
```

Zeros:

```python
2
```

Valid again.

---

Continue expanding.

Eventually:

Window:

```text
[0,1,1,1,1,0]
```

Zeros:

```python
2
```

Length:

```python
6
```

Answer:

```python
6
```

---

# Visual Understanding

```text
[1]                     ✅
[1,1]                   ✅
[1,1,1]                 ✅
[1,1,1,0]               ✅
[1,1,1,0,0]             ✅
[1,1,1,0,0,0]           ❌

Shrink

[0,0]                   ✅
[0,0,1]                 ✅
[0,0,1,1]               ✅
[0,0,1,1,1]             ✅
[0,0,1,1,1,1]           ✅ ← answer
```

Maximum:

```python
6
```

---

# 🔹 Block 4: Interview Q&A

## Q1: What is the hidden translation of this problem?

### Answer

```text
Longest subarray
containing at most k zeros.
```

---

## Q2: Why use Sliding Window?

### Answer

Because we need the longest contiguous subarray satisfying a dynamic constraint.

---

## Q3: Why track only zeros?

### Answer

Because zeros are the only elements affecting validity. Ones never violate the constraint.

---

## Q4: Why shrink when `zero_count > k`?

### Answer

Because the window becomes invalid and cannot contribute to the answer.

---

## Q5: Why is the complexity O(n)?

### Answer

Each element enters and leaves the window at most once, so both pointers move at most `n` times.

---

## Q6: What Sliding Window category is this?

### Answer

**Variable-Size Sliding Window + At Most K Violations**

---

# Pattern Extraction

For LC 1004, the reusable pattern is:

```text
Longest Subarray
        +
At Most K Bad Elements
        =
Variable Sliding Window
        +
Violation Counter
```

---

# Master Template

```python
left = 0
violations = 0

for right in range(n):

    add(nums[right])

    while violations > k:
        remove(nums[left])
        left += 1

    answer = max(answer, right - left + 1)
```

---

# Sliding Window Progression So Far

| Problem | Pattern                             |
| ------- | ----------------------------------- |
| LC 1456 | Fixed Window                        |
| LC 2461 | Fixed Window + HashMap              |
| LC 209  | Variable Window                     |
| LC 3    | Variable Window + HashSet           |
| LC 904  | Variable Window + HashMap           |
| LC 1004 | Variable Window + Violation Counter |

This problem introduces one of the most reusable interview templates:

```text
Longest Window
with At Most K Violations
```

This exact pattern reappears in:

* LC 1004 — Max Consecutive Ones III
* LC 424 — Longest Repeating Character Replacement
* LC 2024 — Maximize the Confusion of an Exam
* LC 1493 — Longest Subarray of 1's After Deleting One Element

Master LC 1004 thoroughly—it is one of the core Variable Sliding Window templates asked in interviews.

Excellent choice.

This is **one of the most important Sliding Window problems** in interviews because it teaches the concept of **maintaining a valid window using frequency counts**.

If you master **LC 424**, you'll also understand:

* LC 1004 — Max Consecutive Ones III
* LC 904 — Fruit Into Baskets
* LC 3 — Longest Substring Without Repeating Characters
* Many "Longest/At Most K" interview problems

---

# ⚔ LC 424 — Longest Repeating Character Replacement

**Difficulty:** Medium

**Pattern:** Dynamic Sliding Window + HashMap (Frequency)

**Importance:**
⭐⭐⭐⭐⭐ (Top-tier interview problem)

---

# 🧠 1. Problem Statement

Given a string:

```python
s = "AABABBA"
```

and

```python
k = 1
```

You may replace **at most k characters**.

Return the **length of the longest substring that can become all the same character.**

---

## Example

```
AABABBA
```

Replace one:

```
AAAA
```

Length:

```
4
```

Answer:

```
4
```

---

# 🧠 2. What Is the Question REALLY Asking?

Most beginners think:

> Which character should I replace?

Wrong.

The real question is:

> **How large can my window become while needing at most `k` replacements?**

This change in thinking is everything.

---

# 🧠 3. ELI10 Intuition

Imagine a classroom.

```
A A B A B B A
```

You want everyone in one classroom section to wear the **same uniform**.

You have:

```
k = 1
```

Only **one student** can change uniforms.

Question:

How large can that classroom section be?

---

# 🧠 4. Observation

Suppose current window is:

```
A A B A
```

Frequency:

```
A → 3
B → 1
```

To make all letters equal:

Replace:

```
B
```

Need:

```
1 replacement
```

Valid.

---

Now window becomes

```
A A B A B
```

Frequency:

```
A → 3
B → 2
```

Need:

```
2 replacements
```

Not valid if

```
k = 1
```

Window must shrink.

---

# 🧠 5. The Secret Formula (MOST IMPORTANT)

Suppose

Window size =

```
7
```

Most frequent letter appears

```
5
```

times.

Then

Need replacements:

```
window_size - max_frequency
```

Why?

Because:

Everything except the majority letter must change.

---

### Formula

```
Replacements Needed

=

Window Size

-

Most Frequent Character Count
```

This is the entire problem.

Memorize it.

---

# 🧠 6. Window Invariant (Senior Thinking)

Our window is **valid** only if:

```
window_size - max_frequency <= k
```

If this becomes false:

Shrink window.

This invariant is what senior engineers focus on—not the code.

---

# 🧠 7. Algorithm

1. Expand right pointer.
2. Update character frequency.
3. Track the highest frequency seen.
4. Check if the window violates the rule.
5. If yes, shrink from the left.
6. Keep the maximum valid window size.

---

# ⚔ Optimal Solution (Fully Commented)

```python
def characterReplacement(s, k):

    # Frequency map for characters inside the current window
    freq = {}

    # Left boundary of the sliding window
    left = 0

    # Highest frequency of any character inside the window
    max_freq = 0

    # Best (maximum) valid window length found so far
    answer = 0

    # Expand the window by moving the right pointer
    for right in range(len(s)):

        # Add the current character to the frequency map
        freq[s[right]] = freq.get(s[right], 0) + 1

        # Update the highest frequency seen in this window
        max_freq = max(max_freq, freq[s[right]])

        # Current window size
        window_size = right - left + 1

        # If more than k replacements are needed,
        # shrink the window from the left
        if window_size - max_freq > k:

            # Remove the leftmost character
            freq[s[left]] -= 1

            # Move left boundary forward
            left += 1

        # Update the maximum valid window length
        answer = max(answer, right - left + 1)

    return answer
```

---

# 🧪 Complete Dry Run

Input

```
s = "AABABBA"
k = 1
```

---

### Step 1

Window

```
A
```

Frequency

```
A:1
```

Window Size

```
1
```

Max Frequency

```
1
```

Need

```
1-1 = 0
```

Valid.

Answer

```
1
```

---

### Step 2

Window

```
AA
```

Frequency

```
A:2
```

Need

```
2-2=0
```

Valid.

Answer

```
2
```

---

### Step 3

Window

```
AAB
```

Frequency

```
A:2
B:1
```

Need

```
3-2=1
```

Valid.

Answer

```
3
```

---

### Step 4

Window

```
AABA
```

Frequency

```
A:3
B:1
```

Need

```
4-3=1
```

Still valid.

Answer

```
4
```

---

### Step 5

Window

```
AABAB
```

Frequency

```
A:3
B:2
```

Need

```
5-3=2
```

Too many replacements.

Shrink.

Remove first

```
A
```

Window becomes

```
ABAB
```

Now continue.

Maximum answer remains

```
4
```

---

# 🧠 Why We Don't Recalculate `max_freq`

A common interview question is:

> "Why don't we decrease `max_freq` when the window shrinks?"

Because we don't need to.

`max_freq` is allowed to be slightly stale. It may temporarily overestimate the true maximum frequency, but that only delays shrinking—not correctness. The algorithm still finds the correct maximum window in **O(n)**.

If you recompute the maximum frequency every time the window shrinks:

```
O(26)
```

for uppercase letters (still constant), but for a larger alphabet it becomes more expensive. The standard solution avoids that recomputation.

---

# 📊 Complexity

### Time

```
O(n)
```

Each character:

* enters once
* leaves once

---

### Space

```
O(1)
```

Uppercase English letters → at most 26 entries in the frequency map.

(If the alphabet were unrestricted, we'd describe it as **O(min(n, Σ))**, where Σ is the alphabet size.)

---

# 🎯 Interview Explanation (30 Seconds)

> "I use a dynamic sliding window with a frequency map. The key observation is that the minimum replacements needed equals the window size minus the count of the most frequent character. As long as that value is at most `k`, the window is valid. Otherwise, I shrink the window from the left. This gives an O(n) solution."

---

# 🏭 Real ML/MLOps Analogy

Imagine you're monitoring predictions from a model over time:

```
Dog Dog Cat Dog Dog Dog Cat
```

You allow **one noisy prediction** (`k = 1`) and want the longest continuous period where the model is essentially predicting the same class.

This is exactly the same sliding-window-with-frequency logic used in:

* streaming analytics
* anomaly tolerance
* sensor smoothing
* log analysis
* online quality monitoring

---

# 🔥 Mastery Checklist

You have mastered LC 424 if you can answer:

1. **Why is this a Dynamic Sliding Window problem instead of Fixed Window?**
2. **Why is the formula `window_size - max_freq` correct?**
3. **What invariant must always remain true?**
4. **Why is a frequency map necessary?**
5. **Why don't we decrease `max_freq` when shrinking the window?**

If you can explain all five without looking at notes, you've understood the pattern—not just memorized the solution.


# LC 713 — Subarray Product Less Than K

**Pattern:** Variable-Size Sliding Window (Multiplicative Window)

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem asks:

> Count the number of **contiguous subarrays** whose **product is less than `k`**.

Example:

```python
nums = [10,5,2,6]
k = 100
```

Valid subarrays:

```text
[10]
[5]
[2]
[6]
[10,5]
[5,2]
[2,6]
[5,2,6]
```

Answer:

```python
8
```

---

# Hidden Translation

Interviewers say:

```text
Product
Subarray
Less than K
```

A senior engineer immediately translates:

```text
Maintain the longest window
whose product is < k.
```

---

# Why This Is Variable Sliding Window

Unlike LC 1456:

```text
Window size = fixed
```

Here:

```text
Window size changes dynamically.
```

We expand while:

```python
product < k
```

Shrink whenever:

```python
product >= k
```

Exactly the same philosophy as:

* LC 209
* LC 904
* LC 1004

---

# Brute Force Thinking

Generate every subarray.

For every subarray:

Compute product.

```python
for i:
    product = 1
    for j:
        product *= nums[j]
```

---

## Complexity

Nested loops:

[
O(n^2)
]

Too slow.

---

# Senior Engineer Mindset

The key observation:

All numbers are **positive**.

Therefore:

### Expand

Product:

```text
increases
```

### Shrink

Product:

```text
decreases
```

This monotonic behavior makes Sliding Window possible.

---

# The Most Important Insight

Unlike LC 209, we are **not** asked to find one longest or shortest window.

We are asked to:

```text
Count all valid subarrays.
```

This changes everything.

---

# Counting Trick (Interview Favorite)

Suppose current window is:

```text
left           right
 ↓               ↓
[10, 5, 2, 6]
```

After shrinking, assume the valid window is:

```text
[5,2,6]
```

Ending at index:

```python
right
```

How many valid subarrays end here?

```text
[6]
[2,6]
[5,2,6]
```

Exactly:

```text
Window Length
```

Formula:

```python
count += right - left + 1
```

This single line is the heart of the problem.

---

# Recognition Signals

Whenever you see:

### Signal 1

```text
Contiguous Subarray
```

### Signal 2

```text
Positive Numbers
```

### Signal 3

```text
Product / Sum Constraint
```

### Signal 4

```text
Count Subarrays
```

Think:

```text
Variable Sliding Window
+
Count Windows
```

---

# Edge Case

If:

```python
k <= 1
```

No positive product can be:

```text
< 1
```

Answer:

```python
0
```

Always handle this first.

---

# Complexity Derivation

Each element:

* Enters window once
* Leaves window once

Total:

[
O(n)
]

Space:

[
O(1)
]

---

# Interview Trick

If asked:

> Why do we add `right - left + 1`?

Answer:

> Once the current window is valid, every suffix ending at `right` is also valid because removing elements from the left only decreases the product.

This is the key proof.

---

# 🔹 Block 2: Efficient Code

~~~
class Solution:
    def numSubarrayProductLessThanK(self, nums: List[int], k: int) -> int:
        # ✅ Edge case: if k <= 1, no product can be < k
        if k <= 1:
            return 0

        left = 0          # left pointer of sliding window
        product = 1       # running product of current window
        count = 0         # number of valid subarrays

        # Expand window with right pointer
        for right in range(len(nums)):
            product *= nums[right]   # include nums[right] in product

            # ✅ Shrink window until product < k
            while product >= k:
                product //= nums[left]
                left += 1

            # ✅ Every subarray ending at right and starting from [left..right] is valid
            count += right - left + 1

        return count


~~~

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums, k):

        if k <= 1:
            return 0

        left = 0
        product = 1
        count = 0

        for right in range(len(nums)):

            product *= nums[right]

            while product >= k:
                product //= nums[left]
                left += 1

            count += right - left + 1

        return count
```

---

## Time Complexity

[
O(n)
]

Each element is multiplied once and divided once.

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I maintain a variable-size window whose product is always less than `k`. After restoring validity, every suffix of the current window ending at `right` is also valid, so I add the current window length to the answer. Each element enters and leaves the window at most once, giving O(n) time.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:
    def numSubarrayProductLessThanK(self, nums, k):

        if k <= 1:
            return 0

        left = 0
        product = 1
        count = 0

        for right in range(len(nums)):

            product *= nums[right]

            while product >= k:
                product //= nums[left]
                left += 1

            count += right - left + 1

        return count


nums = [10,5,2,6]
k = 100

obj = Solution()

print(obj.numSubarrayProductLessThanK(nums, k))
```

---

## Output

```python
8
```

---

# Detailed Dry Run

Input:

```python
nums = [10,5,2,6]
k = 100
```

---

## right = 0

Window:

```text
[10]
```

Product:

```python
10
```

Valid.

Window length:

```python
1
```

Count:

```python
1
```

---

## right = 1

Window:

```text
[10,5]
```

Product:

```python
50
```

Valid.

Window length:

```python
2
```

New subarrays:

```text
[5]
[10,5]
```

Count:

```python
3
```

---

## right = 2

Window:

```text
[10,5,2]
```

Product:

```python
100
```

Invalid.

Shrink:

Remove:

```python
10
```

Window:

```text
[5,2]
```

Product:

```python
10
```

Valid.

Window length:

```python
2
```

New subarrays:

```text
[2]
[5,2]
```

Count:

```python
5
```

---

## right = 3

Window:

```text
[5,2,6]
```

Product:

```python
60
```

Valid.

Window length:

```python
3
```

New subarrays:

```text
[6]
[2,6]
[5,2,6]
```

Count:

```python
8
```

---

Final Answer:

```python
8
```

---

# Visual Understanding

```text
[10]          ✅
[10,5]        ✅
[10,5,2]      ❌

Shrink

[5,2]         ✅
[5,2,6]       ✅
```

Counting at each step:

```text
right = 0 → +1
right = 1 → +2
right = 2 → +2
right = 3 → +3
```

Total:

```text
1 + 2 + 2 + 3 = 8
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why does Sliding Window work?

### Answer

Because all numbers are positive. Expanding the window increases the product, and shrinking decreases it, giving a monotonic property.

---

## Q2: Why do we add `right - left + 1`?

### Answer

Because every suffix of the valid window ending at `right` also has a product less than `k`.

---

## Q3: Why doesn't this work with negative numbers?

### Answer

Negative numbers break the monotonic behavior of the product, so expanding or shrinking the window no longer has predictable effects.

---

## Q4: Why handle `k <= 1` separately?

### Answer

Since all numbers are positive integers, every subarray product is at least 1. Therefore, no valid subarray exists when `k <= 1`.

---

## Q5: Why is the complexity O(n)?

### Answer

Each element enters and leaves the window at most once, so both pointers move only forward.

---

## Q6: What Sliding Window category is this?

### Answer

**Variable-Size Sliding Window + Counting Valid Windows**

---

# Pattern Extraction

For LC 713, the reusable pattern is:

```text
Contiguous Subarray
        +
Positive Numbers
        +
Product/Sum Constraint
        +
Count Valid Subarrays
        =
Variable Sliding Window
        +
Window Counting
```

---

# Master Template

```python
left = 0
window_state = initial
answer = 0

for right in range(n):

    expand_window()

    while window_invalid:
        shrink_window()

    answer += right - left + 1
```

---

# Sliding Window Progression (Locked)

| Problem    | Pattern                                        |
| ---------- | ---------------------------------------------- |
| LC 1456    | Fixed Window                                   |
| LC 2461    | Fixed Window + HashMap                         |
| LC 209     | Variable Window (Minimum Window)               |
| LC 3       | Variable Window + HashSet                      |
| LC 904     | Variable Window + HashMap (At Most K Distinct) |
| LC 1004    | Variable Window + At Most K Violations         |
| **LC 713** | **Variable Window + Count Valid Subarrays**    |

**Key takeaway:** LC 713 introduces a new interview pattern: instead of finding the best window, you **count all valid windows** using the formula:

```python
answer += right - left + 1
```

This counting technique is reused in many advanced Sliding Window problems.



# LC 438 — Find All Anagrams in a String

**Pattern:** Fixed-Size Sliding Window + Frequency Counter

---

# 🔹 Block 1: Senior Insights

## Why This Problem Fits Sliding Window

The problem asks:

> Find all starting indices of substrings in `s` that are anagrams of `p`.

Example:

```python id="r7g5mw"
s = "cbaebabacd"
p = "abc"
```

Output:

```python id="c9h3tz"
[0, 6]
```

Because:

```text id="9x5kva"
Index 0 → "cba" → anagram of "abc"
Index 6 → "bac" → anagram of "abc"
```

---

# Hidden Translation

Interviewers say:

```text id="c8bw2j"
Find all anagrams
```

A senior engineer immediately translates:

```text id="q3j1lp"
Find every window
of size len(p)
whose character frequencies
match p.
```

---

# Why This Is a Fixed-Size Sliding Window

Window size is always:

```python id="j5u4xw"
len(p)
```

It never changes.

We simply slide one character at a time.

---

# Brute Force Thinking

Generate every substring of length:

```python id="g2q0ru"
len(p)
```

Sort both strings.

```python id="v8n2fh"
sorted(window) == sorted(p)
```

---

## Complexity

Windows:

[
O(n)
]

Sorting each window:

[
O(k\log k)
]

Total:

[
O(n \cdot k\log k)
]

Too slow.

---

# Senior Engineer Mindset

An anagram does **not** require the same order.

It only requires:

```text id="n9b6es"
Same character frequencies.
```

Instead of sorting every window, maintain:

```python id="f3c1au"
window_frequency
```

and compare it with:

```python id="n6v2pk"
pattern_frequency
```

---

# Core Idea

Build frequency for:

```python id="a8r4jt"
p
```

Slide a fixed window over:

```python id="k0m8cy"
s
```

For every window:

* Add incoming character
* Remove outgoing character
* Compare frequencies

If equal:

Store:

```python id="y9x7qw"
left_index
```

---

# Recognition Signals

Whenever you see:

### Signal 1

```text id="m7a5rd"
Substring
```

### Signal 2

```text id="g2n9vz"
Exactly length k
```

### Signal 3

```text id="r8y6bc"
Permutation / Anagram
```

### Signal 4

```text id="d1k4po"
Character frequency
```

Think:

```text id="t6j2fs"
Fixed Sliding Window
+
Frequency Counter
```

---

# Why Frequency Instead of Sorting?

Sorting:

```python id="s4e9mk"
"cba" -> "abc"
```

takes:

[
O(k\log k)
]

Frequency comparison:

```python id="b2q8hn"
{'a':1,'b':1,'c':1}
```

is much cheaper.

Since lowercase English letters are limited to **26**, comparing two frequency arrays is effectively constant time.

---

# Complexity Derivation

Each character:

* Enters the window once
* Leaves the window once

Frequency comparison:

26 elements.

Therefore:

Time:

[
O(n)
]

Space:

26 counts.

[
O(1)
]

---

# Interview Trick

Instead of dictionaries, use arrays of size:

```python id="p8u3zs"
26
```

for lowercase letters.

Reasons:

* Faster
* Less memory
* Cleaner comparisons

Interviewers generally prefer this optimization.

---

# 🔹 Block 2: Efficient Code


```
from typing import List

class Solution:
    def findAnagrams(self, s: str, p: str) -> List[int]:
        # ✅ Edge case: if p is longer than s, no anagrams possible
        if len(p) > len(s):
            return []

        result = []                 # ✅ Stores starting indices of anagrams
        p_count = [0] * 26          # ✅ Frequency of characters in p
        window = [0] * 26           # ✅ Frequency of current window in s

        # ✅ Build frequency count for p
        for ch in p:
            p_count[ord(ch) - ord('a')] += 1

        k = len(p)  # window size

        # ✅ Initialize first window of size k
        for i in range(k):
            window[ord(s[i]) - ord('a')] += 1

        # ✅ Check first window
        if window == p_count:
            result.append(0)

        # ✅ Slide window across s
        for right in range(k, len(s)):
            # Add new character
            window[ord(s[right]) - ord('a')] += 1

            # Remove outgoing character
            left = right - k
            window[ord(s[left]) - ord('a')] -= 1

            # Compare window with p_count
            if window == p_count:
                result.append(left + 1)

        return result


```
```python id="t9x4kl"
class Solution:
    def findAnagrams(self, s: str, p: str):

        if len(p) > len(s):
            return []

        result = []

        p_count = [0] * 26
        window = [0] * 26

        for ch in p:
            p_count[ord(ch) - ord('a')] += 1

        k = len(p)

        for i in range(k):
            window[ord(s[i]) - ord('a')] += 1

        if window == p_count:
            result.append(0)

        for right in range(k, len(s)):

            window[ord(s[right]) - ord('a')] += 1

            left = right - k

            window[ord(s[left]) - ord('a')] -= 1

            if window == p_count:
                result.append(left + 1)

        return result
```

---

## Time Complexity

[
O(n)
]

---

## Space Complexity

[
O(1)
]

(26-character frequency arrays)

---

## Interview Justification

> I maintain a fixed-size sliding window equal to the length of `p`. Instead of sorting every window, I compare character frequency arrays. Since the alphabet size is fixed at 26, each comparison is constant time, resulting in an overall O(n) solution.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="u5z8jd"
class Solution:
    def findAnagrams(self, s: str, p: str):

        if len(p) > len(s):
            return []

        result = []

        p_count = [0] * 26
        window = [0] * 26

        for ch in p:
            p_count[ord(ch) - ord('a')] += 1

        k = len(p)

        for i in range(k):
            window[ord(s[i]) - ord('a')] += 1

        if window == p_count:
            result.append(0)

        for right in range(k, len(s)):

            window[ord(s[right]) - ord('a')] += 1

            left = right - k

            window[ord(s[left]) - ord('a')] -= 1

            if window == p_count:
                result.append(left + 1)

        return result


s = "cbaebabacd"
p = "abc"

obj = Solution()

print(obj.findAnagrams(s, p))
```

---

## Output

```python id="m2q7vn"
[0, 6]
```

---

# Detailed Dry Run

Input:

```python id="e7v4tf"
s = "cbaebabacd"
p = "abc"
```

Window size:

```python id="k6n9rp"
3
```

---

## Window 1

```text id="b1r5qx"
cba
```

Frequency:

```text id="t9m4lz"
a=1
b=1
c=1
```

Matches pattern.

Answer:

```python id="v3j8wk"
[0]
```

---

## Window 2

```text id="y5f7hn"
bae
```

Frequency changes.

Not equal.

---

## Window 3

```text id="w2d8mq"
aeb
```

Not equal.

---

## Window 4

```text id="j7q1kt"
eba
```

Not equal.

---

## Window 5

```text id="h4m9zc"
bab
```

Not equal.

---

## Window 6

```text id="x8r3gv"
aba
```

Not equal.

---

## Window 7

```text id="p6k2yf"
bac
```

Frequency:

```text id="f9w4ds"
a=1
b=1
c=1
```

Matches.

Answer:

```python id="q1z6nj"
[0,6]
```

---

# Visual Understanding

```text id="s7v3xm"
cba ✅
bae ❌
aeb ❌
eba ❌
bab ❌
aba ❌
bac ✅
acd ❌
```

Final:

```python id="l4x9pt"
[0,6]
```

---

# 🔹 Block 4: Interview Q&A

## Q1: Why use Sliding Window?

### Answer

Because every candidate substring has the same fixed length as `p`.

---

## Q2: Why compare frequencies instead of sorting?

### Answer

Sorting every window costs O(k log k), while frequency comparison is O(1) for a fixed alphabet.

---

## Q3: Why use arrays instead of dictionaries?

### Answer

The input consists of lowercase English letters, so an array of size 26 is faster and more memory-efficient.

---

## Q4: Why is the complexity O(n)?

### Answer

Each character enters and leaves the window exactly once, and comparing two frequency arrays of length 26 is constant time.

---

## Q5: What if `len(p) > len(s)`?

### Answer

Return an empty list immediately because no valid window can exist.

---

## Q6: What Sliding Window category is this?

### Answer

**Fixed-Size Sliding Window + Frequency Counter**

---

# Pattern Extraction

For LC 438, the reusable pattern is:

```text id="w8n5jr"
Substring
        +
Fixed Window Size
        +
Character Frequency Match
        =
Fixed Sliding Window
        +
Frequency Counter
```

---

# Master Template

```python id="d2m7kf"
build pattern frequency

build first window frequency

if frequencies match:
    record answer

for each new window:

    add incoming character

    remove outgoing character

    if frequencies match:
        record answer
```

---

# Sliding Window Progression (Locked)

| Problem    | Pattern                                                 |
| ---------- | ------------------------------------------------------- |
| LC 1456    | Fixed Window                                            |
| LC 2461    | Fixed Window + HashMap                                  |
| LC 209     | Variable Window (Minimum Window)                        |
| LC 3       | Variable Window + HashSet                               |
| LC 904     | Variable Window + HashMap (At Most K Distinct)          |
| LC 1004    | Variable Window + At Most K Violations                  |
| LC 713     | Variable Window + Count Valid Windows                   |
| **LC 438** | **Fixed Window + Frequency Counter (Anagram Matching)** |

LC 438 is the canonical interview problem for recognizing that **anagrams are a frequency-matching problem, not a sorting problem**, and it forms the basis for many advanced string sliding-window questions.
