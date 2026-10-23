#  Next: CARD 3 — Problem Solving (Locked Order)

We'll solve the Hashing problem bank in this sequence:

### Foundation

1. LC 217 — Contains Duplicate *(HashSet)*
2. LC 1 — Two Sum *(HashMap)*

### Frequency

3. LC 242 — Valid Anagram
4. LC 387 — First Unique Character

### Grouping & Mapping

5. LC 49 — Group Anagrams
6. LC 205 — Isomorphic Strings

### Prefix + HashMap (Most Important)

7. ⭐ LC 560 — Subarray Sum Equals K

### Advanced

8. LC 128 — Longest Consecutive Sequence

This progression builds your HashMap/HashSet intuition from simple lookup to advanced interview patterns without skipping foundational ideas.



Excellent. This order is logical and progressively builds the concepts. The only adjustment I'd make is to move **LC 560** to the **Prefix Sum** module rather than treating it as a Hashing problem, because its primary pattern is Prefix Sum; the HashMap is a supporting data structure. Since you've already mastered LC 560 in the Prefix Sum section, we'll mark it as completed instead of repeating it.

# 🔒 HASHING MASTERY ROADMAP (ML/MLOps Track)

## What You'll Master

Hashing is about trading **extra memory for faster lookups**.

Core operations:

```text
Insert  → O(1)
Search  → O(1)
Delete  → O(1)
```

This makes HashMap and HashSet some of the most frequently tested interview tools.

---

# 📚 Pattern 1 — Foundation (HashSet & HashMap)

### Goal

Learn when to use a **HashSet** versus a **HashMap**.

### Problems

✅ **LC 217 — Contains Duplicate** *(HashSet)*

Skills:

* Fast duplicate detection
* Membership testing
* O(1) lookup

---

✅ **LC 1 — Two Sum** *(HashMap)*

Skills:

* Value → Index mapping
* Complement lookup
* One-pass HashMap

---

# 📚 Pattern 2 — Frequency Counting

### Goal

Count occurrences efficiently.

### Problems

✅ **LC 242 — Valid Anagram**

Skills:

* Character frequency counting
* Dictionary/Counter usage
* Comparing frequency maps

---

✅ **LC 387 — First Unique Character**

Skills:

* Frequency map
* Two-pass HashMap strategy

---

# 📚 Pattern 3 — Grouping & Mapping

### Goal

Group data by a computed key.

### Problems

✅ **LC 49 — Group Anagrams**

Skills:

* HashMap of lists
* Canonical key generation
* Grouping strings

---

✅ **LC 205 — Isomorphic Strings**

Skills:

* One-to-one mapping
* Bidirectional consistency
* Two HashMaps

---

# 📚 Pattern 4 — Prefix Sum + HashMap (Already Mastered)

### Problem

✅ **LC 560 — Subarray Sum Equals K**

Skills:

* Prefix Sum
* Running Sum
* Frequency HashMap
* O(n) subarray counting

**Status:** Already completed in the Prefix Sum module.

---

# 📚 Pattern 5 — Advanced Hashing

### Goal

Use hashing to eliminate sorting and repeated scanning.

### Problem

✅ **LC 128 — Longest Consecutive Sequence**

Skills:

* HashSet
* Sequence expansion
* O(n) optimization
* Boundary detection

---

# 🔥 Hashing Pattern Recognition

| Interview Signal        | Pattern              |
| ----------------------- | -------------------- |
| Duplicate detection     | HashSet              |
| Find complement         | HashMap              |
| Count occurrences       | Frequency HashMap    |
| Group similar objects   | HashMap of Lists     |
| Character mapping       | Two HashMaps         |
| Prefix relationships    | Prefix Sum + HashMap |
| Fast sequence detection | HashSet              |

---

# 🧠 Master Templates

## 1. HashSet

```python
seen = set()

for x in nums:
    if x in seen:
        return True
    seen.add(x)
```

---

## 2. HashMap Lookup

```python
mapping = {}

for i, value in enumerate(nums):

    target_value = target - value

    if target_value in mapping:
        return [mapping[target_value], i]

    mapping[value] = i
```

---

## 3. Frequency Counter

```python
freq = {}

for item in data:
    freq[item] = freq.get(item, 0) + 1
```

---

## 4. Grouping

```python
groups = {}

for item in data:

    key = compute_key(item)

    groups.setdefault(key, []).append(item)
```

---

# 📌 Locked Hashing Question Bank

| Level            | Problem                               | Pattern              | Status      |
| ---------------- | ------------------------------------- | -------------------- | ----------- |
| Foundation       | LC 217 — Contains Duplicate           | HashSet              | ⬜           |
| Foundation       | LC 1 — Two Sum                        | HashMap              | ⬜           |
| Frequency        | LC 242 — Valid Anagram                | Frequency Counter    | ⬜           |
| Frequency        | LC 387 — First Unique Character       | Frequency Counter    | ⬜           |
| Grouping         | LC 49 — Group Anagrams                | HashMap of Lists     | ⬜           |
| Grouping         | LC 205 — Isomorphic Strings           | Two HashMaps         | ⬜           |
| Prefix + HashMap | LC 560 — Subarray Sum Equals K        | Prefix Sum + HashMap | ✅ Completed |
| Advanced         | LC 128 — Longest Consecutive Sequence | HashSet              | ⬜           |

---

## 🎯 Learning Order (Locked)

We will follow this exact sequence:

1. **LC 217 — Contains Duplicate**
2. **LC 1 — Two Sum**
3. **LC 242 — Valid Anagram**
4. **LC 387 — First Unique Character**
5. **LC 49 — Group Anagrams**
6. **LC 205 — Isomorphic Strings**
7. **LC 128 — Longest Consecutive Sequence**

Since **LC 560** is already mastered in the Prefix Sum section, we'll skip it here and avoid unnecessary repetition.

**Next Problem:** **LC 217 — Contains Duplicate (HashSet Foundation)**. This is the simplest and most fundamental hashing interview problem, and it introduces the mindset of using a **HashSet for O(1) membership checks**.


# 📖 HOW WE WILL SOLVE EVERY PROBLEM

This is also locked.

Each problem will have the same professional structure.

---

## 🔹 Step 1 — Pattern Recognition

How do we know this is a Hashing problem?

Trigger words.

Why not:

* Two Pointers
* Sliding Window
* Binary Search

---

## 🔹 Step 2 — Brute Force

Not because we'll use it.

Because interviewers often ask:

> "Can you think of a straightforward solution first?"

We'll discuss:

* idea
* complexity
* limitation

---

## 🔹 Step 3 — Observation

The key insight.

The sentence that transforms

```
O(n²)
```

into

```
O(n)
```

---

## 🔹 Step 4 — Optimal Algorithm

We'll explain

WHY

before writing code.

---

## 🔹 Step 5 — Fully Commented Code

Every important line explained.

No magic.

---

## 🔹 Step 6 — Complete Dry Run

Every iteration.

Every variable.

Every HashMap update.

Every HashSet update.

---

## 🔹 Step 7 — Complexity Proof

Not

```
O(n)
```

Instead

WHY

is it O(n)?

---

## 🔹 Step 8 — Common Mistakes

Real interview mistakes.

---

## 🔹 Step 9 — Interview Explanation

Exactly what to tell the interviewer.

---

## 🔹 Step 10 — ML/MLOps Connection

Real industry usage.

---

# 🏆 MY ADDITION (One More Upgrade)

I want to add one section that I think will dramatically improve your interview skills.

## 🧩 Pattern Evolution

At the end of every problem we'll answer:

> **"If the interviewer changes one constraint, how does the solution change?"**

Example:

### LC 217 — Contains Duplicate

Original:

> Any duplicate?

↓

HashSet.

---

Interviewer changes:

> Duplicate within distance **k**?

↓

Sliding Window + HashSet.

---

Interviewer changes:

> Return duplicate frequency.

↓

HashMap.

---

Interviewer changes:

> Numbers arrive continuously from a stream.

↓

Streaming HashSet / HashMap.

---

This teaches you **how to adapt**, not just memorize.

That's exactly the kind of thinking expected in strong ML/MLOps coding interviews.

---

## ✅ Locked Order

We'll now start with:

**⭐ LC 217 — Contains Duplicate (HashSet Foundation)**

It looks like an easy problem, but it's where you build the HashSet intuition that later powers graph traversal, BFS/DFS, cycle detection, and many real-world deduplication tasks. Once that foundation is solid, we'll move to **LC 1 — Two Sum** and continue layer by layer.


# Foundation

1. LC 217 — Contains Duplicate *(HashSet)*
2. LC 1 — Two Sum *(HashMap)*

# 1. LC 217 — Contains Duplicate *(HashSet)*

# LC 217 — Contains Duplicate ⭐⭐⭐⭐

**Pattern:** HashSet (Membership Testing)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐ (Foundation of Hashing)

> **This is the "Hello World" of Hashing.**
>
> Almost every HashSet interview problem is based on one simple question:
>
> **"Have I seen this element before?"**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given an integer array:

```python
nums = [1,2,3,1]
```

Return

```python
True
```

because

```text
1 appears twice.
```

Another example

```python
nums = [1,2,3,4]
```

Return

```python
False
```

because every element is unique.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Contains Duplicate
```

A senior engineer immediately thinks

```text
Need fast membership checking

↓

HashSet
```

The entire problem is simply

> "While scanning the array, has this number appeared before?"

If yes

```text
Duplicate Found
```

Otherwise

```text
Store it
```

---

# 3. Brute Force Solution

Compare every pair.

```python
for i in range(len(nums)):
    for j in range(i + 1, len(nums)):
        if nums[i] == nums[j]:
            return True

return False
```

---

## Time Complexity

Outer loop

×

Inner loop

[
O(n^2)
]

Too slow for large arrays.

---

# 4. Better Observation

Suppose we have

```python
nums = [4,7,2,9]
```

While scanning

```text
Seen:

{}
```

Read

```text
4
```

Store

```text
{4}
```

Read

```text
7
```

Store

```text
{4,7}
```

Read

```text
2
```

Store

```text
{4,7,2}
```

Now read

```text
7
```

Question

```text
Is 7 already inside the set?
```

Answer

```text
Yes
```

Immediately return

```python
True
```

No need to continue scanning.

---

# 5. Why HashSet?

HashSet provides average:

| Operation | Complexity |
| --------- | ---------- |
| Insert    | O(1)       |
| Search    | O(1)       |
| Delete    | O(1)       |

Instead of searching the whole array every time

```text
O(n)
```

we search the HashSet

```text
O(1)
```

---

# 6. Why Not Use a List?

Suppose

```python
seen = []
```

Checking

```python
if x in seen
```

requires scanning the list.

Time

```text
O(n)
```

Doing this for every element

[
O(n^2)
]

Using a HashSet reduces membership testing to average O(1).

---

# 7. Alternative Solution

You may see

```python
return len(nums) != len(set(nums))
```

Example

```python
nums = [1,2,3,1]
```

Original length

```text
4
```

Set

```python
{1,2,3}
```

Length

```text
3
```

Lengths differ

Duplicate exists.

This is elegant but not ideal for interviews because:

* It scans the whole array.
* It cannot exit early.

Interviewers usually prefer the explicit HashSet approach.

---

# 8. Recognition Signals

Whenever you see

```text
Duplicate

Repeated

Already Seen

Unique

Distinct
```

Immediately think

```text
HashSet
```

---

# 9. Complexity

Each number

```text
Lookup

+

Insert
```

Average

```text
O(1)
```

Total

[
O(n)
]

Space

Worst case

Every element is unique

[
O(n)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def containsDuplicate(self, nums):

        seen = set()

        for num in nums:

            if num in seen:
                return True

            seen.add(num)

        return False
```

---

## Time Complexity

[
O(n)
]

Each element is checked and inserted at most once.

---

## Space Complexity

[
O(n)
]

In the worst case, all elements are unique and stored in the set.

---

## Interview Justification

> I maintain a HashSet containing all previously seen numbers. For each element, I first check whether it already exists in the set. If it does, I've found a duplicate and return immediately. Otherwise, I insert it into the set and continue. HashSet membership checks are O(1) on average, giving an overall O(n) solution.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def containsDuplicate(self, nums):

        seen = set()

        for num in nums:

            if num in seen:
                return True

            seen.add(num)

        return False


nums = [1,2,3,1]

obj = Solution()

print(obj.containsDuplicate(nums))
```

Output

```text
True
```

---

# Detailed Dry Run

Input

```python
nums = [1,2,3,1]
```

Initial

```text
seen = {}
```

---

### Step 1

Current

```text
1
```

Already seen?

```text
No
```

Store

```text
{1}
```

---

### Step 2

Current

```text
2
```

Already seen?

```text
No
```

Store

```text
{1,2}
```

---

### Step 3

Current

```text
3
```

Already seen?

```text
No
```

Store

```text
{1,2,3}
```

---

### Step 4

Current

```text
1
```

Already seen?

```text
Yes
```

Return

```text
True
```

---

# Dry Run Table

| Index | Current Number | Seen Before? | HashSet After Step |      Result     |
| ----: | -------------: | :----------: | -----------------: | :-------------: |
|     0 |              1 |       ❌      |                {1} |     Continue    |
|     1 |              2 |       ❌      |              {1,2} |     Continue    |
|     2 |              3 |       ❌      |            {1,2,3} |     Continue    |
|     3 |              1 |       ✅      |            {1,2,3} | Return **True** |

---

# Visual Understanding

```text
Array

1   2   3   1
            ↑
        Already in HashSet

HashSet Growth

{}

↓

{1}

↓

{1,2}

↓

{1,2,3}

↓

1 already exists

↓

Duplicate Found
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is a HashSet better than a list?

### Model Answer

> A list requires O(n) time for membership checks because it scans each element. A HashSet uses hashing, allowing average O(1) membership checks and reducing the overall complexity to O(n).

---

## Q2. Why do we check before adding?

### Model Answer

> If we add first, every element would always be found in the set afterward. Checking first lets us detect whether the element was already present before the current occurrence.

---

## Q3. Can this be solved by sorting?

### Model Answer

Yes.

```python
nums.sort()

for i in range(1, len(nums)):
    if nums[i] == nums[i - 1]:
        return True

return False
```

Time:

[
O(n \log n)
]

Space:

* Depends on the sorting algorithm.

The HashSet solution is faster on average.

---

## Q4. Why is the average lookup O(1)?

### Model Answer

> A HashSet stores elements using hash values. The hash determines where an element should be stored, allowing direct access instead of scanning sequentially. Although collisions can occur, modern hash tables keep the average lookup close to O(1).

---

## Q5. When would you prefer sorting over a HashSet?

### Model Answer

> If memory is very limited and modifying the input is allowed, sorting may be acceptable because it avoids storing every element in a separate hash table. However, it increases the time complexity to O(n log n).

---

## Q6. What broader interview pattern does LC 217 teach?

### Model Answer

> LC 217 introduces the "visited elements" pattern. Whenever a problem asks whether an element has been seen before, or whether values are unique, a HashSet is often the right choice.

---

# Pattern Extraction

For **LC 217**, memorize this decision flow:

```text
Read Current Element

↓

Already in HashSet?

↓

YES  → Duplicate Found

NO

↓

Insert into HashSet

↓

Continue
```

---

# Master Template

```python
seen = set()

for item in data:

    if item in seen:
        return True

    seen.add(item)

return False
```

---

# Hashing Mastery Progress (Locked)

| Problem    | Pattern          | Core Idea                    |    Status   |
| ---------- | ---------------- | ---------------------------- | :---------: |
| **LC 217** | HashSet          | Fast membership testing      |      ✅      |
| LC 1       | HashMap          | Value → Index mapping        |      ⬜      |
| LC 242     | Frequency Map    | Count occurrences            |      ⬜      |
| LC 387     | Frequency Map    | First unique element         |      ⬜      |
| LC 49      | HashMap of Lists | Group by key                 |      ⬜      |
| LC 205     | Two HashMaps     | One-to-one mapping           |      ⬜      |
| LC 560     | Prefix + HashMap | Count subarrays              | ✅ Completed |
| LC 128     | HashSet          | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...                              | Best Data Structure  | Why?                      |
| ---------------------------------------------- | -------------------- | ------------------------- |
| Duplicate detection                            | **HashSet**          | Fast membership testing   |
| Unique elements                                | **HashSet**          | Store seen values         |
| Need extra information (index, count, mapping) | **HashMap**          | Key → Value relationships |
| Frequency counting                             | **HashMap**          | Element → Count           |
| Group similar items                            | **HashMap of Lists** | One key, multiple values  |

## 💡 The One-Line Takeaway

> **If the interview question can be rephrased as *"Have I seen this value before?"*, your first instinct should be to reach for a `HashSet`.**




# LC 1 — Two Sum ⭐⭐⭐⭐⭐

**Pattern:** HashMap (Value → Index Mapping)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐⭐ (One of the Most Asked Interview Questions)

> **LC 1 is the foundation of HashMap problems.**
>
> It teaches one of the most important interview patterns:
>
> **Store information about previous elements so future elements can find them in O(1).**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given:

```python
nums = [2,7,11,15]

target = 9
```

Return:

```python
[0,1]
```

because

```text
nums[0] + nums[1]

=

2 + 7

=

9
```

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Find two numbers whose sum equals target.
```

A senior engineer immediately thinks:

```text
For every number

↓

Find its complement

↓

Have I already seen it?

↓

HashMap
```

The important observation is:

Instead of asking

> "Which two numbers add to 9?"

Ask

> "For the current number, what number do I still need?"

---

# 3. Brute Force Solution

Compare every pair.

```python
for i in range(len(nums)):

    for j in range(i+1, len(nums)):

        if nums[i] + nums[j] == target:
            return [i, j]
```

---

## Time Complexity

Outer Loop

×

Inner Loop

[
O(n^2)
]

Too slow.

---

# 4. The Key Insight — Complement

Suppose

```python
target = 9
```

Current number

```text
2
```

Needed value

```text
9 - 2 = 7
```

Question:

```text
Have I already seen 7?
```

If yes

Return both indices.

Otherwise

Store

```text
2
```

for future numbers.

---

Example:

```python
nums = [2,7,11,15]
```

Scan:

Read

```text
2
```

Need

```text
7
```

Not found.

Store

```text
{
2:0
}
```

---

Read

```text
7
```

Need

```text
2
```

Already exists!

Return

```python
[0,1]
```

---

# 5. Why Value → Index?

The problem asks for

```text
Indices
```

not values.

If we store only values

```python
{2,7}
```

we lose the index information.

Instead

```python
{
2:0,
7:1
}
```

Now we know exactly where each value appeared.

---

# 6. Why Check Before Storing?

Consider

```python
nums = [3,3]

target = 6
```

Correct answer

```python
[0,1]
```

Scan

Current

```text
3
```

Need

```text
3
```

If we store first

```python
{
3:0
}
```

and then immediately search,

we would incorrectly match the element with itself.

Correct order:

1. Check if complement exists.
2. Store current value.

This guarantees two different indices.

---

# 7. Recognition Signals

Whenever you see

```text
Two numbers

Target Sum

Pair Exists

Complement
```

Think

```text
HashMap

Value

↓

Index
```

---

# 8. Complexity

Each element

```text
Lookup

+

Insert
```

Average

[
O(1)
]

Overall

[
O(n)
]

Space

Worst case

Every value stored

[
O(n)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def twoSum(self, nums, target):

        value_to_index = {}

        for i, num in enumerate(nums):

            complement = target - num

            if complement in value_to_index:
                return [value_to_index[complement], i]

            value_to_index[num] = i
```

---

## Time Complexity

[
O(n)
]

Each element is processed exactly once.

---

## Space Complexity

[
O(n)
]

The HashMap may store every element.

---

## Interview Justification

> I scan the array once while maintaining a HashMap from value to index. For each number, I compute the complement needed to reach the target. If that complement has already been seen, I return its stored index together with the current index. Otherwise, I store the current value and its index for future lookups. This gives O(n) time with O(n) extra space.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def twoSum(self, nums, target):

        value_to_index = {}

        for i, num in enumerate(nums):

            complement = target - num

            if complement in value_to_index:

                return [value_to_index[complement], i]

            value_to_index[num] = i


nums = [2,7,11,15]
target = 9

obj = Solution()

print(obj.twoSum(nums, target))
```

Output

```text
[0, 1]
```

---

# Detailed Dry Run

Input

```python
nums = [2,7,11,15]

target = 9
```

Initial

```text
HashMap

{}
```

---

### Step 1

Current Index

```text
0
```

Current Value

```text
2
```

Complement

```text
9 - 2 = 7
```

Is

```text
7
```

inside HashMap?

```text
No
```

Store

```python
{
2:0
}
```

---

### Step 2

Current Index

```text
1
```

Current Value

```text
7
```

Complement

```text
9 - 7 = 2
```

Is

```text
2
```

inside HashMap?

```text
Yes
```

HashMap

```python
{
2:0
}
```

Return

```python
[0,1]
```

Done.

---

# Dry Run Table

| Index | Current Value | Complement | HashMap Before | Found? | Action         |
| ----: | ------------: | ---------: | -------------- | :----: | -------------- |
|     0 |             2 |          7 | `{}`           |    ❌   | Store `2 → 0`  |
|     1 |             7 |          2 | `{2:0}`        |    ✅   | Return `[0,1]` |

---

# Visual Understanding

```text
Target = 9

Array

2     7     11     15

↓

Read 2

Need 7

↓

HashMap

{2:0}

↓

Read 7

Need 2

↓

Found

↓

Answer

[0,1]
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why do we store **value → index** instead of **index → value**?

### Model Answer

> We search using the complement value. A HashMap lookup is based on keys, so storing `value → index` lets us check whether the complement exists in O(1) and immediately retrieve its index.

---

## Q2. Why check before inserting?

### Model Answer

> Checking first prevents using the same element twice. For example, with `nums = [3,3]` and `target = 6`, inserting before checking could incorrectly match the current element with itself.

---

## Q3. Can this be solved by sorting?

### Model Answer

Yes, using the Two Pointers technique after sorting.

Time:

[
O(n \log n)
]

However, sorting changes the element order, so additional work is needed to recover the original indices. The HashMap solution is simpler and runs in O(n).

---

## Q4. Why is HashMap lookup O(1)?

### Model Answer

> HashMaps compute a hash for each key and use it to locate the bucket directly. This provides average O(1) insertion and lookup, though worst-case performance can degrade if many keys collide.

---

## Q5. What if there are duplicate values?

### Model Answer

> The algorithm still works because it always searches for the complement before inserting the current value. This correctly handles cases like `[3,3]`.

---

## Q6. What broader interview pattern does LC 1 teach?

### Model Answer

> LC 1 teaches the **complement lookup** pattern: instead of searching for a pair directly, compute the value you need and use a HashMap to determine whether it has already been seen.

---

# Pattern Extraction

For **LC 1**, memorize this decision flow:

```text
Current Number

↓

Complement = Target - Current

↓

Complement in HashMap?

↓

YES

↓

Return Previous Index + Current Index

↓

NO

↓

Store

Current Value → Current Index

↓

Continue
```

---

# Master Template

```python
mapping = {}

for i, value in enumerate(nums):

    needed = target - value

    if needed in mapping:
        return [mapping[needed], i]

    mapping[value] = i
```

---

# Hashing Mastery Progress (Locked)

| Problem  | Pattern          | Core Idea                    |    Status   |
| -------- | ---------------- | ---------------------------- | :---------: |
| LC 217   | HashSet          | Fast membership testing      |      ✅      |
| **LC 1** | HashMap          | Value → Index mapping        |      ✅      |
| LC 242   | Frequency Map    | Count occurrences            |      ⬜      |
| LC 387   | Frequency Map    | First unique element         |      ⬜      |
| LC 49    | HashMap of Lists | Group by key                 |      ⬜      |
| LC 205   | Two HashMaps     | One-to-one mapping           |      ⬜      |
| LC 560   | Prefix + HashMap | Count subarrays              | ✅ Completed |
| LC 128   | HashSet          | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...                      | Best Data Structure  | Why?                         |
| -------------------------------------- | -------------------- | ---------------------------- |
| Duplicate detection                    | **HashSet**          | Fast membership checking     |
| Need an element's partner (complement) | **HashMap**          | Value → Index lookup         |
| Count occurrences                      | **HashMap**          | Value → Frequency            |
| Group similar elements                 | **HashMap of Lists** | Key → Collection             |
| One-to-one mapping                     | **Two HashMaps**     | Maintain consistent mappings |

## 💡 The One-Line Takeaway

> **Whenever the problem can be rephrased as *"For this value, have I already seen the value I need?"*, think `HashMap` with a `value → index` mapping.**



# Frequency

## 3. LC 242 — Valid Anagram
## 4. LC 387 — First Unique Character


# LC 242 — Valid Anagram ⭐⭐⭐⭐

**Pattern:** Frequency HashMap (Character Counting)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐ (Foundation of Frequency Counting)

> **LC 242 is the "Hello World" of Frequency Maps.**
>
> It teaches one of the most important HashMap patterns:
>
> **Count occurrences instead of comparing positions.**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given two strings:

```python
s = "anagram"

t = "nagaram"
```

Return

```python
True
```

because both strings contain exactly the same letters with exactly the same frequencies.

Example:

```python
s = "rat"

t = "car"
```

Return

```python
False
```

because

```text
r,a,t

≠

c,a,r
```

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Are these two strings anagrams?
```

A senior engineer immediately translates it into

```text
Do both strings have identical character frequencies?
```

Not

```text
Same order ❌
```

Instead

```text
Same frequency ✅
```

---

# 3. Brute Force Solution

One possible approach:

Sort both strings.

```python
return sorted(s) == sorted(t)
```

Example

```python
anagram

↓

aaagmnr
```

```python
nagaram

↓

aaagmnr
```

Equal.

---

## Complexity

Sorting

[
O(n \log n)
]

Good.

But not optimal.

---

# 4. Better Observation

We don't actually care about order.

We only care about

```text
How many times each character appears.
```

Example

```python
s = "aabbc"
```

Frequency

```text
a → 2

b → 2

c → 1
```

Another string

```python
t = "abcab"
```

Frequency

```text
a → 2

b → 2

c → 1
```

Identical.

Therefore

```python
True
```

---

# 5. Why HashMap?

HashMap stores

```text
Character

↓

Frequency
```

Example

```python
{
'a':2,
'b':2,
'c':1
}
```

After counting both strings

Compare the two maps.

If identical

They're anagrams.

---

# 6. One-Pass Optimization

Instead of building two frequency maps

We can use only one.

Step 1

Count characters from

```python
s
```

```text
a → +1

n → +1

...
```

Step 2

Remove characters using

```python
t
```

```text
a → -1

n → -1

...
```

If every frequency becomes

```text
0
```

The strings are anagrams.

This is the interview-preferred solution.

---

# 7. Why Check Length First?

Suppose

```python
s = "abc"

t = "ab"
```

Different lengths.

Impossible to have equal frequencies.

Immediately return

```python
False
```

No need to build any HashMap.

---

# 8. Recognition Signals

Whenever you see

```text
Anagram

Frequency

Occurrences

Character Count

Permutation
```

Think

```text
Frequency HashMap
```

---

# 9. Complexity

Each character

Count once

Update once

Overall

[
O(n)
]

Space

At most

26 lowercase letters

or

all unique characters

[
O(k)
]

where

```text
k = unique characters
```

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def isAnagram(self, s, t):

        if len(s) != len(t):
            return False

        freq = {}

        for ch in s:
            freq[ch] = freq.get(ch, 0) + 1

        for ch in t:

            if ch not in freq:
                return False

            freq[ch] -= 1

            if freq[ch] < 0:
                return False

        return True
```

---

## Time Complexity

[
O(n)
]

Each string is scanned once.

---

## Space Complexity

[
O(k)
]

where

```text
k = number of distinct characters
```

---

## Interview Justification

> I first reject strings with different lengths because they cannot be anagrams. Then I count character frequencies from the first string using a HashMap. While scanning the second string, I decrement the counts. If any character is missing or its count becomes negative, the strings cannot be anagrams. If all counts balance, the strings are anagrams.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def isAnagram(self, s, t):

        if len(s) != len(t):
            return False

        freq = {}

        for ch in s:
            freq[ch] = freq.get(ch, 0) + 1

        for ch in t:

            if ch not in freq:
                return False

            freq[ch] -= 1

            if freq[ch] < 0:
                return False

        return True


s = "anagram"
t = "nagaram"

obj = Solution()

print(obj.isAnagram(s, t))
```

Output

```text
True
```

---

# Detailed Dry Run

Input

```python
s = "anagram"

t = "nagaram"
```

---

### Step 1 — Count Characters

After scanning

```python
s
```

HashMap

```text
{
a:3,
n:1,
g:1,
r:1,
m:1
}
```

---

### Step 2 — Remove Using Second String

Read

```text
n
```

Map

```text
n:1→0
```

---

Read

```text
a
```

```text
a:3→2
```

---

Read

```text
g
```

```text
g:1→0
```

---

Read

```text
a
```

```text
a:2→1
```

---

Read

```text
r
```

```text
r:1→0
```

---

Read

```text
a
```

```text
a:1→0
```

---

Read

```text
m
```

```text
m:1→0
```

Every frequency has been balanced.

Return

```python
True
```

---

# Dry Run Table

| Character | Count After First String | Count After Second String |
| --------- | -----------------------: | ------------------------: |
| a         |                        3 |                         0 |
| n         |                        1 |                         0 |
| g         |                        1 |                         0 |
| r         |                        1 |                         0 |
| m         |                        1 |                         0 |

All counts become **0** → Valid Anagram.

---

# Visual Understanding

```text
String 1

anagram

↓

Frequency Map

a → 3

n → 1

g → 1

r → 1

m → 1

↓

Process String 2

nagaram

↓

Subtract Frequencies

↓

All become 0

↓

Anagram
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why compare frequencies instead of sorting?

### Model Answer

> Sorting works but takes O(n log n). A frequency HashMap counts characters in O(n), making it more efficient for large inputs.

---

## Q2. Why check lengths first?

### Model Answer

> If the lengths differ, the strings cannot have identical character frequencies, so we can immediately return `False` without additional work.

---

## Q3. Why can we use one HashMap instead of two?

### Model Answer

> We increment counts while processing the first string and decrement them while processing the second. If the strings are anagrams, every count returns to zero.

---

## Q4. What happens if a frequency becomes negative?

### Model Answer

> A negative frequency means the second string contains a character more times than the first string, so they cannot be anagrams.

---

## Q5. When can we use an array instead of a HashMap?

### Model Answer

> If the input is guaranteed to contain only lowercase English letters, we can use an array of size 26 instead of a HashMap. This reduces overhead while keeping O(n) time.

Example:

```python
count = [0] * 26
```

---

## Q6. What broader interview pattern does LC 242 teach?

### Model Answer

> LC 242 introduces the **frequency counting pattern**. Whenever a problem asks how many times each element or character appears, a HashMap (or fixed-size array for small alphabets) is usually the right solution.

---

# Pattern Extraction

For **LC 242**, memorize this flow:

```text
First String

↓

Increase Frequency

↓

Second String

↓

Decrease Frequency

↓

Any Missing Character?

↓

False

↓

Any Negative Count?

↓

False

↓

All Counts Balanced

↓

True
```

---

# Master Template

```python
freq = {}

for item in first:
    freq[item] = freq.get(item, 0) + 1

for item in second:

    if item not in freq:
        return False

    freq[item] -= 1

    if freq[item] < 0:
        return False

return True
```

---

# Hashing Mastery Progress (Locked)

| Problem    | Pattern           | Core Idea                    |    Status   |
| ---------- | ----------------- | ---------------------------- | :---------: |
| LC 217     | HashSet           | Fast membership testing      |      ✅      |
| LC 1       | HashMap           | Value → Index mapping        |      ✅      |
| **LC 242** | Frequency HashMap | Character counting           |      ✅      |
| LC 387     | Frequency HashMap | First unique character       |      ⬜      |
| LC 49      | HashMap of Lists  | Group by canonical key       |      ⬜      |
| LC 205     | Two HashMaps      | One-to-one mapping           |      ⬜      |
| LC 560     | Prefix + HashMap  | Count subarrays              | ✅ Completed |
| LC 128     | HashSet           | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...            | Best Data Structure   | Why?                      |
| ---------------------------- | --------------------- | ------------------------- |
| Duplicate detection          | **HashSet**           | Fast membership checks    |
| Find complement              | **HashMap**           | Value → Index lookup      |
| Count frequencies            | **HashMap / Array**   | Element → Count           |
| Compare multisets (anagrams) | **Frequency HashMap** | Compare occurrence counts |
| Group similar items          | **HashMap of Lists**  | Key → Group               |
| Maintain mappings            | **Two HashMaps**      | One-to-one relationships  |

## 💡 The One-Line Takeaway

> **Whenever the problem asks whether two collections contain the same elements with the same counts (regardless of order), think *Frequency HashMap*.**


# LC 387 — First Unique Character in a String ⭐⭐⭐⭐

**Pattern:** Frequency HashMap (Two-Pass Strategy)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐ (Classic Frequency Counting Problem)

> **LC 387 teaches the next evolution of frequency maps.**
>
> In **LC 242**, we counted frequencies.
>
> In **LC 387**, we **count first**, then **use those counts to make a decision**.
>
> This is known as the **Two-Pass Frequency Pattern**.

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given:

```python
s = "leetcode"
```

Return:

```python
0
```

because

```text
l
```

appears only once, and it is the first such character.

Another example:

```python
s = "loveleetcode"
```

Return:

```python
2
```

because

```text
v
```

is the first character whose frequency is exactly `1`.

Example:

```python
s = "aabb"
```

Return:

```python
-1
```

because no character is unique.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says:

```text
First Unique Character
```

A senior engineer immediately translates it into:

```text
Step 1:
Know the frequency of every character.

↓

Step 2:
Find the first character whose frequency is 1.
```

Notice something important:

We **cannot** decide whether the first character is unique while reading it.

Example:

```python
s = "abca"
```

When reading the first `'a'`, we don't yet know another `'a'` appears later.

Therefore, we need **two passes**.

---

# 3. Why Brute Force Fails

For every character:

Scan the whole string again.

```python
for i in range(len(s)):

    count = 0

    for j in range(len(s)):

        if s[i] == s[j]:
            count += 1

    if count == 1:
        return i
```

---

## Time Complexity

Outer Loop

×

Inner Loop

[
O(n^2)
]

Too slow.

---

# 4. Better Observation

Instead of recounting every character repeatedly,

Count once.

Example:

```python
s = "loveleetcode"
```

Frequency Map:

```text
l → 2

o → 2

v → 1

e → 4

t → 1

c → 1

d → 1
```

Now simply scan the string again.

The first character with frequency

```text
1
```

is

```text
v
```

Index:

```python
2
```

Done.

---

# 5. Why Two Passes?

Many beginners ask:

> Why not solve it in one pass?

Because uniqueness depends on the **entire string**.

Example:

```python
s = "abcda"
```

When reading

```text
a
```

at index `0`, you don't know another `a` appears at index `4`.

Only after scanning the whole string do you know the final frequencies.

Hence:

```text
Pass 1 → Count

Pass 2 → Find
```

---

# 6. Why HashMap?

HashMap stores:

```text
Character

↓

Frequency
```

Example:

```python
{
'a':2,
'b':1,
'c':3
}
```

Lookup:

```python
freq[ch]
```

Average:

[
O(1)
]

---

# 7. Recognition Signals

Whenever you see:

```text
Unique

First Unique

Frequency

Occurrences

Exactly Once
```

Think:

```text
Frequency HashMap

+

Two Passes
```

---

# 8. Complexity

First Pass:

Count frequencies.

Second Pass:

Find first unique.

Overall:

[
O(n)
]

Space:

[
O(k)
]

where

```text
k = number of distinct characters
```

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def firstUniqChar(self, s):

        freq = {}

        # Pass 1: Count frequencies
        for ch in s:
            freq[ch] = freq.get(ch, 0) + 1

        # Pass 2: Find first unique
        for i, ch in enumerate(s):

            if freq[ch] == 1:
                return i

        return -1
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
O(k)
]

where `k` is the number of distinct characters.

---

## Interview Justification

> I first count the frequency of every character using a HashMap. Then I scan the string again and return the index of the first character whose frequency equals one. This avoids repeatedly counting characters and achieves O(n) time.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def firstUniqChar(self, s):

        freq = {}

        # First Pass
        for ch in s:
            freq[ch] = freq.get(ch, 0) + 1

        # Second Pass
        for i, ch in enumerate(s):

            if freq[ch] == 1:
                return i

        return -1


s = "loveleetcode"

obj = Solution()

print(obj.firstUniqChar(s))
```

Output:

```text
2
```

---

# Detailed Dry Run

Input:

```python
s = "loveleetcode"
```

---

## Pass 1 — Build Frequency Map

After counting:

| Character | Frequency |
| --------- | --------: |
| l         |         2 |
| o         |         2 |
| v         |         1 |
| e         |         4 |
| t         |         1 |
| c         |         1 |
| d         |         1 |

---

## Pass 2 — Find First Unique

### Index 0

Character:

```text
l
```

Frequency:

```text
2
```

Not unique.

---

### Index 1

Character:

```text
o
```

Frequency:

```text
2
```

Not unique.

---

### Index 2

Character:

```text
v
```

Frequency:

```text
1
```

Return:

```python
2
```

Done.

---

# Dry Run Table

| Index | Character | Frequency | Unique? | Action     |
| ----: | --------- | --------: | :-----: | ---------- |
|     0 | l         |         2 |    ❌    | Continue   |
|     1 | o         |         2 |    ❌    | Continue   |
|     2 | v         |         1 |    ✅    | Return `2` |

---

# Visual Understanding

```text
String

l  o  v  e  l  e  e  t  c  o  d  e

↓

Frequency Map

l → 2

o → 2

v → 1

e → 4

t → 1

c → 1

d → 1

↓

Scan Again

l ❌

o ❌

v ✅

↓

Answer = 2
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why do we need two passes?

### Model Answer

> During the first pass, we don't know whether a character will appear again later. The first pass determines final frequencies, and the second pass finds the first character whose frequency is exactly one.

---

## Q2. Can this be solved in one pass?

### Model Answer

> Not with only a simple frequency map. A character's uniqueness depends on future characters, so we must know the complete frequency distribution before identifying the first unique one.

---

## Q3. Why use a HashMap?

### Model Answer

> A HashMap stores each character's frequency and provides O(1) average lookup. This allows counting in one pass and checking frequencies efficiently in the second pass.

---

## Q4. Can we use an array instead of a HashMap?

### Model Answer

Yes, if the input contains only lowercase English letters.

```python
count = [0] * 26
```

This reduces constant overhead while maintaining O(n) time.

---

## Q5. How is LC 387 different from LC 242?

### Model Answer

> LC 242 compares the frequency maps of two strings. LC 387 builds one frequency map and then uses it to locate the first character that appears exactly once.

---

## Q6. What broader interview pattern does LC 387 teach?

### Model Answer

> LC 387 teaches the **Two-Pass Frequency Pattern**: first gather statistics (frequencies), then make decisions using those statistics. This pattern appears in many string and array interview problems.

---

# Pattern Extraction

For **LC 387**, memorize this flow:

```text
First Pass

↓

Count Frequencies

↓

Second Pass

↓

Frequency == 1 ?

↓

YES

↓

Return Index

↓

NO

↓

Continue

↓

No Unique Character

↓

Return -1
```

---

# Master Template

```python
freq = {}

# Pass 1
for item in data:
    freq[item] = freq.get(item, 0) + 1

# Pass 2
for index, item in enumerate(data):

    if freq[item] == 1:
        return index

return -1
```

---

# Hashing Mastery Progress (Locked)

| Problem    | Pattern           | Core Idea                    |    Status   |
| ---------- | ----------------- | ---------------------------- | :---------: |
| LC 217     | HashSet           | Fast membership testing      |      ✅      |
| LC 1       | HashMap           | Value → Index mapping        |      ✅      |
| LC 242     | Frequency HashMap | Character counting           |      ✅      |
| **LC 387** | Frequency HashMap | Two-pass frequency lookup    |      ✅      |
| LC 49      | HashMap of Lists  | Group by canonical key       |      ⬜      |
| LC 205     | Two HashMaps      | One-to-one mapping           |      ⬜      |
| LC 560     | Prefix + HashMap  | Count subarrays              | ✅ Completed |
| LC 128     | HashSet           | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...                                | Best Data Structure                | Why?                      |
| ------------------------------------------------ | ---------------------------------- | ------------------------- |
| Duplicate detection                              | **HashSet**                        | Fast membership checks    |
| Find a complement                                | **HashMap**                        | Value → Index lookup      |
| Count occurrences                                | **Frequency HashMap**              | Element → Count           |
| First element with a property based on frequency | **Frequency HashMap + Two Passes** | Count first, then decide  |
| Group similar items                              | **HashMap of Lists**               | Key → Group               |
| Maintain one-to-one mappings                     | **Two HashMaps**                   | Bidirectional consistency |

## 💡 The One-Line Takeaway

> **Whenever the decision depends on the final frequency of every element (such as "first unique"), use the *Two-Pass Frequency Pattern*: first count, then scan.**


# Grouping & Mapping
### LC 49 — Group Anagrams
### LC 205 — Isomorphic Strings

# LC 49 — Group Anagrams ⭐⭐⭐⭐⭐

**Pattern:** HashMap of Lists (Grouping by Canonical Key)
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐ (Very Frequently Asked)

> **LC 49 introduces one of the most powerful HashMap patterns:**
>
> **Convert each object into a canonical (standard) representation and use it as the HashMap key.**
>
> This pattern appears in many real interview problems.

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given:

```python id="8y3kd7"
strs = ["eat", "tea", "tan", "ate", "nat", "bat"]
```

Return:

```python id="g6v1h9"
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

The order of groups doesn't matter.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says:

```text id="5vq9ld"
Group Anagrams
```

A senior engineer immediately translates it into:

```text id="qhgk5w"
Find a common identity
(shared key)
for every anagram.
```

The problem is **not** about comparing every pair of strings.

The real question is:

> **"How can all anagrams produce exactly the same key?"**

---

# 3. Brute Force Solution

Compare every string with every other string.

```text id="7h7s2x"
Compare

eat

with

tea

↓

Compare

eat

with

tan

↓

Compare

eat

with

ate

...
```

Each comparison requires checking character counts or sorting.

Overall complexity:

[
O(n^2 \cdot k)
]

where

* `n` = number of strings
* `k` = average string length

Too slow.

---

# 4. The Key Insight — Canonical Representation

Consider

```python id="6qkm5v"
"eat"

"tea"

"ate"
```

If we sort them:

```text id="2rlvbo"
eat

↓

aet
```

```text id="3zwbn8"
tea

↓

aet
```

```text id="1p4x3s"
ate

↓

aet
```

All become

```text id="5g1z4g"
"aet"
```

Now we have a **common identity**.

This sorted string becomes the **HashMap key**.

---

# 5. HashMap of Lists

Instead of storing

```text id="lvn4fr"
key → value
```

we store

```text id="gtlnlq"
key → list of words
```

Example:

```python id="5vmlwb"
{
"aet": ["eat", "tea", "ate"],

"ant": ["tan", "nat"],

"abt": ["bat"]
}
```

Finally:

Return all values.

---

# 6. Why Sorting Works

Anagrams contain

```text id="sop7f7"
Same letters

Same frequencies
```

Sorting puts identical letters into the same order.

Example

```python id="w0z1h7"
listen

silent
```

Both become

```text id="3ph4tb"
eilnst
```

Therefore

```text id="9s67mv"
Sorted String

↓

Unique Signature
```

---

# 7. Alternative Key (Frequency Tuple)

Instead of sorting:

Count characters.

Example:

```text id="tv7jlwm"
a → 2

b → 1

c → 0
...
```

Store as

```python id="lj3gwz"
(2,1,0,0,...)
```

Two anagrams have identical frequency tuples.

This achieves

[
O(k)
]

key construction instead of

[
O(k\log k)
]

Sorting, however, is simpler and is the most common interview solution.

---

# 8. Recognition Signals

Whenever you see

```text id="f0ktwu"
Group

Cluster

Categorize

Same Characters

Anagram
```

Think

```text id="2fwopn"
Canonical Key

↓

HashMap of Lists
```

---

# 9. Complexity

Suppose

* `n` strings
* average length `k`

Sorting one string:

[
O(k\log k)
]

Total:

[
O(n \cdot k\log k)
]

Space:

HashMap stores every string.

[
O(nk)
]

---

# 🔹 Block 2: Efficient Code

```python id="ed3qwn"
from collections import defaultdict

class Solution:
    def groupAnagrams(self, strs):

        groups = defaultdict(list)

        for word in strs:

            key = "".join(sorted(word))

            groups[key].append(word)

        return list(groups.values())
```

---

## Time Complexity

[
O(n \cdot k\log k)
]

Sorting each string dominates the runtime.

---

## Space Complexity

[
O(nk)
]

All strings are stored in the grouped lists.

---

## Interview Justification

> I transform each word into its canonical representation by sorting its characters. All anagrams produce the same sorted string, so I use that sorted string as the HashMap key. Each key maps to a list of words sharing that signature. Finally, I return all grouped lists.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python id="g57mxg"
from collections import defaultdict

class Solution:

    def groupAnagrams(self, strs):

        groups = defaultdict(list)

        for word in strs:

            key = "".join(sorted(word))

            groups[key].append(word)

        return list(groups.values())


strs = ["eat", "tea", "tan", "ate", "nat", "bat"]

obj = Solution()

print(obj.groupAnagrams(strs))
```

Possible Output

```text id="jgkndh"
[
['eat','tea','ate'],
['tan','nat'],
['bat']
]
```

(The order of groups or words within groups may vary.)

---

# Detailed Dry Run

Input

```python id="mzw4i5"
["eat","tea","tan","ate","nat","bat"]
```

Initial

```text id="4jqbns"
groups = {}
```

---

### Word

```text id="8hhfbo"
eat
```

Sorted key

```text id="sx9y5g"
aet
```

Map

```python id="x9mjlwm"
{
"aet":["eat"]
}
```

---

### Word

```text id="v9hycs"
tea
```

Sorted key

```text id="jbhx0k"
aet
```

Append

```python id="aqcwfu"
{
"aet":["eat","tea"]
}
```

---

### Word

```text id="0d2ujm"
tan
```

Key

```text id="pc0m42"
ant
```

Map

```python id="5s5gdx"
{
"aet":["eat","tea"],
"ant":["tan"]
}
```

---

### Word

```text id="9v51y7"
ate
```

Key

```text id="mms0wo"
aet
```

Append

```python id="nvg71r"
{
"aet":["eat","tea","ate"],
"ant":["tan"]
}
```

---

### Word

```text id="w4t77j"
nat
```

Key

```text id="m9k3zx"
ant
```

Append

```python id="jaj0zr"
{
"aet":["eat","tea","ate"],
"ant":["tan","nat"]
}
```

---

### Word

```text id="vfdgrt"
bat
```

Key

```text id="zt2rkq"
abt
```

Final Map

```python id="e4hfe5"
{
"aet":["eat","tea","ate"],
"ant":["tan","nat"],
"abt":["bat"]
}
```

Return

```python id="ehl81t"
list(groups.values())
```

---

# Dry Run Table

| Word | Sorted Key | HashMap After Processing       |
| ---- | ---------- | ------------------------------ |
| eat  | aet        | `{"aet":["eat"]}`              |
| tea  | aet        | `{"aet":["eat","tea"]}`        |
| tan  | ant        | `{"aet":[...], "ant":["tan"]}` |
| ate  | aet        | `{"aet":["eat","tea","ate"]}`  |
| nat  | ant        | `{"ant":["tan","nat"]}`        |
| bat  | abt        | `{"abt":["bat"]}`              |

---

# Visual Understanding

```text id="k6z3vh"
eat

↓

Sort

↓

aet

↓

HashMap

aet

↓

["eat"]


tea

↓

Sort

↓

aet

↓

HashMap

aet

↓

["eat","tea"]


ate

↓

Sort

↓

aet

↓

HashMap

aet

↓

["eat","tea","ate"]
```

All words with the same key belong to the same group.

---

# 🔹 Block 4: Interview Q&A

## Q1. Why does sorting work?

### Model Answer

> Sorting places the characters of every anagram into the same order. Since anagrams contain the same characters with the same frequencies, they produce identical sorted strings, which serve as a canonical key.

---

## Q2. Why use a HashMap of lists?

### Model Answer

> Multiple words can share the same canonical key, so each key must map to a collection of words rather than a single value.

---

## Q3. Can we avoid sorting?

### Model Answer

> Yes. We can build a frequency tuple (for example, counts of the 26 lowercase letters) and use that tuple as the HashMap key. This reduces key construction from O(k log k) to O(k), although the implementation is a bit longer.

Example:

```python id="qzjlwm"
count = [0] * 26
```

Convert the list to a tuple before using it as a dictionary key.

---

## Q4. Why can't we use a list as a dictionary key?

### Model Answer

> Lists are mutable and therefore unhashable. Dictionary keys must be immutable and hashable, so we use strings (sorted words) or tuples (frequency counts).

---

## Q5. What if the words are very long?

### Model Answer

> For very long strings, repeatedly sorting becomes expensive. Using a fixed-size frequency tuple creates keys in O(k) time and is usually the better choice.

---

## Q6. What broader interview pattern does LC 49 teach?

### Model Answer

> LC 49 teaches the **Canonical Key Pattern**: transform objects into a standard representation so that equivalent objects map to the same HashMap key. This idea appears in many grouping and classification problems.

---

# Pattern Extraction

For **LC 49**, memorize this flow:

```text id="wlkv1y"
Word

↓

Build Canonical Key

↓

HashMap

↓

Append Word

↓

Next Word

↓

Return All Groups
```

---

# Master Template

```python id="vxncyu"
groups = {}

for item in items:

    key = build_key(item)

    groups.setdefault(key, []).append(item)

return list(groups.values())
```

---

# Hashing Mastery Progress (Locked)

| Problem   | Pattern           | Core Idea                    |    Status   |
| --------- | ----------------- | ---------------------------- | :---------: |
| LC 217    | HashSet           | Fast membership testing      |      ✅      |
| LC 1      | HashMap           | Value → Index mapping        |      ✅      |
| LC 242    | Frequency HashMap | Character counting           |      ✅      |
| LC 387    | Frequency HashMap | Two-pass frequency lookup    |      ✅      |
| **LC 49** | HashMap of Lists  | Group by canonical key       |      ✅      |
| LC 205    | Two HashMaps      | One-to-one mapping           |      ⬜      |
| LC 560    | Prefix + HashMap  | Count subarrays              | ✅ Completed |
| LC 128    | HashSet           | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...            | Best Pattern                         | Why?                      |
| ---------------------------- | ------------------------------------ | ------------------------- |
| Duplicate detection          | HashSet                              | Fast membership           |
| Complement lookup            | HashMap                              | Value → Index             |
| Frequency counting           | Frequency HashMap                    | Element → Count           |
| First unique element         | Two-Pass Frequency                   | Count, then decide        |
| **Group equivalent objects** | **Canonical Key + HashMap of Lists** | Same key → Same group     |
| One-to-one mapping           | Two HashMaps                         | Bidirectional consistency |

## 💡 The One-Line Takeaway

> **Whenever the problem asks you to group equivalent items, first find a *canonical representation* (key). Then use a `HashMap<key, list>` to collect all items that share that key.**

# LC 205 — Isomorphic Strings ⭐⭐⭐⭐⭐

**Pattern:** Two HashMaps (Bidirectional Mapping)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐⭐ (Classic Mapping Interview Problem)

> **LC 205 introduces the "One-to-One Mapping" pattern.**
>
> Unlike previous HashMap problems that stored **counts** or **indices**, this problem stores **relationships**.
>
> The key idea is:
>
> **Every character in one string must map to exactly one character in the other, and vice versa.**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given:

```python
s = "egg"

t = "add"
```

Return

```python
True
```

because

```text
e → a

g → d
```

Every mapping is consistent.

---

Another example

```python
s = "foo"

t = "bar"
```

Return

```python
False
```

because

```text
f → b ✓

o → a

o → r ❌
```

The same character (`o`) cannot map to two different characters.

---

Another example

```python
s = "ab"

t = "aa"
```

Return

```python
False
```

because

```text
a → a

b → a ❌
```

Two different characters cannot map to the same character.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says:

```text
Isomorphic Strings
```

A senior engineer immediately translates it into:

```text
Need a one-to-one relationship.

Every source character

↓

Exactly one destination character

AND

Every destination character

↓

Exactly one source character
```

This is called a **bijection**.

---

# 3. Why One HashMap Is Not Enough

Many beginners write:

```python
{
'a':'x',
'b':'y'
}
```

Looks correct.

But consider

```python
s = "ab"

t = "cc"
```

Single map becomes

```python
{
'a':'c',
'b':'c'
}
```

Nothing seems wrong.

But

```text
a

↓

c

b

↓

c
```

Two characters map to one character.

Not allowed.

---

Therefore we must also check

```text
c

↓

?
```

Hence

**Second HashMap.**

---

# 4. Why Two HashMaps?

We maintain

## Forward Map

```text
Character in s

↓

Character in t
```

Example

```python
{
'e':'a',
'g':'d'
}
```

---

## Reverse Map

```text
Character in t

↓

Character in s
```

Example

```python
{
'a':'e',
'd':'g'
}
```

Both maps must always agree.

---

# 5. Step-by-Step Example

Input

```python
s = "paper"

t = "title"
```

---

Read

```text
p
```

and

```text
t
```

Store

```text
p → t

t → p
```

---

Read

```text
a
```

and

```text
i
```

Store

```text
a → i

i → a
```

---

Read

```text
p
```

and

```text
t
```

Already mapped correctly.

Continue.

---

Read

```text
e
```

and

```text
l
```

Store.

---

Read

```text
r
```

and

```text
e
```

Store.

Everything consistent.

Return

```python
True
```

---

# 6. Recognition Signals

Whenever you see

```text
One-to-One

Mapping

Replacement

Character Mapping

Substitution

Isomorphic
```

Think

```text
Two HashMaps
```

---

# 7. Complexity

Each character processed once.

Time

[
O(n)
]

Space

At most

```text
Unique Characters
```

[
O(k)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def isIsomorphic(self, s, t):

        if len(s) != len(t):
            return False

        s_to_t = {}
        t_to_s = {}

        for c1, c2 in zip(s, t):

            if c1 in s_to_t:

                if s_to_t[c1] != c2:
                    return False

            else:
                s_to_t[c1] = c2

            if c2 in t_to_s:

                if t_to_s[c2] != c1:
                    return False

            else:
                t_to_s[c2] = c1

        return True
```

---

## Time Complexity

[
O(n)
]

Each character pair is processed exactly once.

---

## Space Complexity

[
O(k)
]

where

```text
k = distinct characters
```

---

## Interview Justification

> I maintain two HashMaps. The first maps characters from the first string to the second, and the second maps characters from the second string back to the first. For each character pair, I verify both mappings remain consistent. If either mapping conflicts, the strings are not isomorphic.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def isIsomorphic(self, s, t):

        if len(s) != len(t):
            return False

        s_to_t = {}
        t_to_s = {}

        for c1, c2 in zip(s, t):

            if c1 in s_to_t:

                if s_to_t[c1] != c2:
                    return False

            else:
                s_to_t[c1] = c2

            if c2 in t_to_s:

                if t_to_s[c2] != c1:
                    return False

            else:
                t_to_s[c2] = c1

        return True


s = "paper"
t = "title"

obj = Solution()

print(obj.isIsomorphic(s, t))
```

Output

```text
True
```

---

# Detailed Dry Run

Input

```python
s = "paper"

t = "title"
```

Initial

```text
s_to_t = {}

t_to_s = {}
```

---

### Step 1

```text
p

↓

t
```

Maps become

```text
s_to_t

p → t
```

```text
t_to_s

t → p
```

---

### Step 2

```text
a

↓

i
```

Maps

```text
p → t

a → i
```

---

### Step 3

```text
p

↓

t
```

Already mapped correctly.

Continue.

---

### Step 4

```text
e

↓

l
```

Store

---

### Step 5

```text
r

↓

e
```

Store

Return

```python
True
```

---

# Dry Run Table

| Step | s Character | t Character | Forward Map    | Reverse Map    | Valid? |
| ---: | ----------- | ----------- | -------------- | -------------- | :----: |
|    1 | p           | t           | p→t            | t→p            |    ✅   |
|    2 | a           | i           | a→i            | i→a            |    ✅   |
|    3 | p           | t           | already exists | already exists |    ✅   |
|    4 | e           | l           | e→l            | l→e            |    ✅   |
|    5 | r           | e           | r→e            | e→r            |    ✅   |

---

# Visual Understanding

```text
paper

↓

title

Forward Map

p → t

a → i

e → l

r → e

Reverse Map

t → p

i → a

l → e

e → r

↓

No conflicts

↓

True
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why do we need two HashMaps?

### Model Answer

> One HashMap only guarantees that each character in the first string maps consistently to the second. It does not prevent two different source characters from mapping to the same destination character. The second HashMap enforces the reverse direction, ensuring a one-to-one mapping.

---

## Q2. What happens if we use only one HashMap?

### Model Answer

Example:

```python
s = "ab"

t = "cc"
```

A single forward map allows:

```text
a → c

b → c
```

This is invalid because two different characters map to the same character. The reverse map detects this conflict.

---

## Q3. Why check the string lengths first?

### Model Answer

> Strings of different lengths cannot have a valid one-to-one correspondence, so we can immediately return `False`.

---

## Q4. What does "isomorphic" really mean?

### Model Answer

> Two strings are isomorphic if there exists a one-to-one mapping between their characters while preserving the order of appearance.

---

## Q5. Can this pattern be used elsewhere?

### Model Answer

> Yes. Any problem requiring consistent one-to-one relationships—such as pattern matching, encoding/decoding, symbol substitution, or schema mapping—can use this bidirectional HashMap technique.

---

## Q6. What broader interview pattern does LC 205 teach?

### Model Answer

> LC 205 teaches the **Bidirectional Mapping Pattern**. Whenever two entities must correspond uniquely to each other, maintain mappings in both directions to detect conflicts immediately.

---

# Pattern Extraction

For **LC 205**, memorize this flow:

```text
Current Pair

↓

Forward Mapping Exists?

↓

Conflict?

↓

False

↓

Reverse Mapping Exists?

↓

Conflict?

↓

False

↓

Store Both Directions

↓

Continue

↓

Finished

↓

True
```

---

# Master Template

```python
forward = {}
reverse = {}

for a, b in zip(first, second):

    if a in forward and forward[a] != b:
        return False

    if b in reverse and reverse[b] != a:
        return False

    forward[a] = b
    reverse[b] = a

return True
```

---

# Hashing Mastery Progress (Locked)

| Problem    | Pattern           | Core Idea                    |    Status   |
| ---------- | ----------------- | ---------------------------- | :---------: |
| LC 217     | HashSet           | Fast membership testing      |      ✅      |
| LC 1       | HashMap           | Value → Index mapping        |      ✅      |
| LC 242     | Frequency HashMap | Character counting           |      ✅      |
| LC 387     | Frequency HashMap | Two-pass frequency lookup    |      ✅      |
| LC 49      | HashMap of Lists  | Group by canonical key       |      ✅      |
| **LC 205** | Two HashMaps      | One-to-one mapping           |      ✅      |
| LC 560     | Prefix + HashMap  | Count subarrays              | ✅ Completed |
| LC 128     | HashSet           | Longest consecutive sequence |      ⬜      |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...             | Best Pattern                     | Why?                              |
| ----------------------------- | -------------------------------- | --------------------------------- |
| Duplicate detection           | HashSet                          | Fast membership                   |
| Complement lookup             | HashMap                          | Value → Index                     |
| Frequency counting            | Frequency HashMap                | Element → Count                   |
| Group equivalent items        | Canonical Key + HashMap of Lists | Same key → Same group             |
| **One-to-one correspondence** | **Two HashMaps**                 | Enforce bidirectional consistency |
| Prefix relationships          | Prefix Sum + HashMap             | Running state lookup              |

## 💡 The One-Line Takeaway

> **Whenever two sets of objects must map uniquely to each other, use *two HashMaps*—one for each direction—to guarantee a true one-to-one (bijective) mapping.**
