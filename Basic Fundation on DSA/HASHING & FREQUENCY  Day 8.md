
# 🟢 DAY 8

## HASHING & FREQUENCY

### Problems 71–80

```text
Frequency Map
First Repeating
First Non-Repeating
Array Equality
Union
Three-Way Common Elements
Group Anagrams
Longest Consecutive Sequence
Pair Difference
Intersection With Multiplicity
```

### 🎯 Skill

**HashMap + Set recognition**


# 🟣 CR2 — DAY 8: HASHING & FREQUENCY

## SESSION 1 — Problems 71–73

Today we start **Hashing & Frequency**, one of the most important placement patterns.

### 🎯 Today's Problems

| #  | Problem                     | Difficulty      | LeetCode                |
| -- | --------------------------- | --------------- | ----------------------- |
| 71 | Frequency Map of Array      | 🟢 Basic        | ❌ No exact canonical LC |
| 72 | First Repeating Element     | 🟢 Basic        | ❌ No exact canonical LC |
| 73 | First Non-Repeating Element | 🟢 Basic–Medium | 🔗 Related: LC 387      |

### 🧠 Today's Core Pattern

> **See repeated values / count occurrences / find unique values → THINK HASH MAP / DICTIONARY.**

---

# 🔥 PROBLEM 71 — FREQUENCY MAP OF ARRAY

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode problem.**

This is a foundational hashing problem that prepares you for many real interview problems.

The requirement is simple:

> Given an array, count how many times each element appears.

Example:

```text
Input:
[1, 2, 2, 3, 1, 2]

Output:
1 → 2
2 → 3
3 → 1
```

### Senior Recognition

Whenever you hear:

* "frequency"
* "count occurrences"
* "how many times"
* "duplicate count"
* "number of appearances"

immediately think:

```text
HashMap / Dictionary
```

Instead of repeatedly scanning the entire array.

### Why?

Without hashing:

```text
For every element:
    scan the whole array to count it
```

That can become:

```text
O(n²)
```

With a hash map:

```text
one pass → update count
```

Approximately:

```text
O(n)
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Problem

Given an integer array, print the frequency of every distinct element.

### Example

```text
Input:
[4, 2, 4, 1, 2, 4]

Output:
4 → 3
2 → 2
1 → 1
```

We don't care about the order unless the problem specifically asks for a particular order.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine you have boxes:

```text
Number → Count
```

Initially:

```text
{}
```

Read `4`:

```text
{4: 1}
```

Read `2`:

```text
{4: 1, 2: 1}
```

Read another `4`:

```text
{4: 2, 2: 1}
```

Read another `4`:

```text
{4: 3, 2: 1}
```

The dictionary remembers the previous count.

### The fundamental operation

```python
freq[x] = freq.get(x, 0) + 1
```

Meaning:

```text
If x exists:
    get its current count

If x doesn't exist:
    use 0

Then add 1
```

This single line is one of the most important Python hashing patterns.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Algorithm

1. Create an empty dictionary `freq`.
2. Traverse every element in the array.
3. For each element:

   * Get its current frequency.
   * Increase it by `1`.
4. After traversal, print the dictionary.

### Pseudocode

```text
create empty frequency map

for each number in array:
    if number exists:
        increase its count
    else:
        set count to 1

print frequency map
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def frequency_map(nums):
    freq = {}

    for num in nums:
        freq[num] = freq.get(num, 0) + 1

    return freq


# Example
nums = [4, 2, 4, 1, 2, 4]

result = frequency_map(nums)

print(result)
```

### Output

```text
{4: 3, 2: 2, 1: 1}
```

### Line-by-line

```python
freq = {}
```

Creates an empty dictionary.

---

```python
for num in nums:
```

Visit every array element.

---

```python
freq.get(num, 0)
```

Ask:

> "What is the current count of `num`?"

If it doesn't exist:

```text
0
```

---

```python
+ 1
```

Because we just found one more occurrence.

---

```python
freq[num] = ...
```

Store the updated frequency.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;

class Main {

    public static Map<Integer, Integer> frequencyMap(int[] nums) {

        Map<Integer, Integer> freq = new HashMap<>();

        for (int num : nums) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }

        return freq;
    }

    public static void main(String[] args) {

        int[] nums = {4, 2, 4, 1, 2, 4};

        Map<Integer, Integer> result = frequencyMap(nums);

        System.out.println(result);
    }
}
```

### Output

```text
{1=1, 2=2, 4=3}
```

Java equivalent:

```python
freq.get(num, 0)
```

is:

```java
freq.getOrDefault(num, 0)
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [4, 2, 4, 1, 2, 4]
```

Start:

```text
freq = {}
```

### Iteration 1

```text
num = 4
```

Current:

```text
freq.get(4, 0) = 0
```

Add 1:

```text
freq[4] = 1
```

Map:

```text
{4: 1}
```

### Iteration 2

```text
num = 2
```

```text
freq.get(2, 0) = 0
```

Map:

```text
{4: 1, 2: 1}
```

### Iteration 3

```text
num = 4
```

Existing count:

```text
freq.get(4, 0) = 1
```

Add 1:

```text
2
```

Map:

```text
{4: 2, 2: 1}
```

### Iteration 4

```text
num = 1
```

New value:

```text
0 + 1 = 1
```

Map:

```text
{4: 2, 2: 1, 1: 1}
```

### Iteration 5

```text
num = 2
```

Existing:

```text
1 + 1 = 2
```

Map:

```text
{4: 2, 2: 2, 1: 1}
```

### Iteration 6

```text
num = 4
```

Existing:

```text
2 + 1 = 3
```

Final:

```text
{4: 3, 2: 2, 1: 1}
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows exactly the same logical process:

```text
num = 4 → {4=1}

num = 2 → {4=1, 2=1}

num = 4 → {4=2, 2=1}

num = 1 → {4=2, 2=1, 1=1}

num = 2 → {4=2, 2=2, 1=1}

num = 4 → {4=3, 2=2, 1=1}
```

The language changes.

The **algorithm does not**.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of elements
```

We traverse the array once:

```text
n iterations
```

Each dictionary insertion/update is expected:

```text
O(1)
```

Therefore:

```text
Time = O(n)
```

The map can contain up to `n` distinct values:

```text
Space = O(n)
```

### Final

```text
Time:  O(n) expected
Space: O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a HashMap?

Because it allows expected O(1) lookup/update, avoiding repeated scans.

---

### Q2. What happens if every element is unique?

Example:

```text
[1, 2, 3, 4, 5]
```

The map becomes:

```text
{1:1, 2:1, 3:1, 4:1, 5:1}
```

Space becomes O(n).

---

### Q3. What if the array contains negative numbers?

No problem.

```text
[-2, 5, -2, 5, 5]
```

produces:

```text
{-2: 2, 5: 3}
```

---

### Q4. Can we solve this without extra space?

If the values are from a small known range, an array can sometimes be used as a frequency table.

Example:

```text
values = 0 to 100
```

But for arbitrary integers, a dictionary is more flexible.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Memorize:

```text
COUNT → HASH MAP
```

Template:

```python
freq = {}

for x in nums:
    freq[x] = freq.get(x, 0) + 1
```

This pattern appears everywhere.

### Recognition

```text
"frequency"
"count"
"occurrences"
"appears"
"how many times"
```

→ HashMap.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Writing:

```python
freq[num] += 1
```

immediately.

If `num` isn't present, you'll get:

```text
KeyError
```

Use:

```python
freq[num] = freq.get(num, 0) + 1
```

---

### ❌ Mistake 2

Using nested loops unnecessarily.

That often becomes:

```text
O(n²)
```

---

### ❌ Mistake 3

Confusing frequency with first occurrence.

Frequency asks:

```text
HOW MANY?
```

First repeating asks:

```text
WHICH ONE REPEATS FIRST?
```

Different problem.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Problem 71 — Frequency Map

```text
Input → Array
Output → value → frequency
Pattern → HashMap
Python → dict
Java → HashMap
Time → O(n) expected
Space → O(n)
```

### 🔥 Master Template

```python
freq = {}

for x in nums:
    freq[x] = freq.get(x, 0) + 1
```

**Mastery target:** You should be able to write this without looking.

---

# 🔥 PROBLEM 72 — FIRST REPEATING ELEMENT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode match** for this basic placement formulation.

Do not confuse it with:

* LC 217 — Contains Duplicate
* LC 219 — Contains Duplicate II

Those are related, but they ask different questions.

### Problem

Find the **first element that appears more than once while scanning from left to right**.

Example:

```text
[10, 5, 3, 4, 3, 5, 6]
```

Answer:

```text
3
```

Why?

Scanning:

```text
10 → first
5  → first
3  → first
4  → first
3  → already seen
```

So `3` is the first repeating element encountered.

### Senior Insight

The key phrase is:

> **first repeating**

This means **order matters**.

We need a `set` to remember what we've already seen.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, return the first element whose value has already appeared earlier.

Example:

```text
Input:
[7, 2, 5, 2, 9, 5]

Output:
2
```

Because:

```text
7 → unseen
2 → unseen
5 → unseen
2 → seen before → ANSWER
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a security checkpoint.

Every number enters.

We maintain:

```text
seen = {}
```

For each number:

### If not seen:

```text
put it into seen
```

### If already seen:

```text
this is the first repeating element
return it
```

Example:

```text
[4, 7, 2, 7, 2]
```

Process:

```text
4 → remember
7 → remember
2 → remember
7 → already remembered → STOP
```

Answer:

```text
7
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Create an empty set `seen`.
2. Traverse the array from left to right.
3. For every element:

   * If it exists in `seen`, return it.
   * Otherwise add it to `seen`.
4. If traversal finishes without finding a duplicate, return `-1`.

### Pseudocode

```text
seen = empty set

for x in array:

    if x is already in seen:
        return x

    add x to seen

return -1
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def first_repeating(nums):

    seen = set()

    for num in nums:

        if num in seen:
            return num

        seen.add(num)

    return -1


# Example
nums = [10, 5, 3, 4, 3, 5, 6]

result = first_repeating(nums)

print(result)
```

### Output

```text
3
```

### Why `set` instead of dictionary?

We only need to know:

```text
Have I seen this before?
```

We don't need:

```text
How many times did I see it?
```

Therefore:

```text
Set → membership
Dictionary → frequency/mapping
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Set;

class Main {

    public static int firstRepeating(int[] nums) {

        Set<Integer> seen = new HashSet<>();

        for (int num : nums) {

            if (seen.contains(num)) {
                return num;
            }

            seen.add(num);
        }

        return -1;
    }

    public static void main(String[] args) {

        int[] nums = {10, 5, 3, 4, 3, 5, 6};

        int result = firstRepeating(nums);

        System.out.println(result);
    }
}
```

Output:

```text
3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[10, 5, 3, 4, 3, 5, 6]
```

Start:

```text
seen = {}
```

| Step | num | Already seen? | Action | seen       |
| ---: | --: | ------------- | ------ | ---------- |
|    1 |  10 | No            | Add    | {10}       |
|    2 |   5 | No            | Add    | {10,5}     |
|    3 |   3 | No            | Add    | {10,5,3}   |
|    4 |   4 | No            | Add    | {10,5,3,4} |
|    5 |   3 | **Yes**       | Return | —          |

Answer:

```text
3
```

### Important

We stop immediately.

We do **not** continue looking for another duplicate.

That is what makes this:

> **First repeating element**

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text
seen = {}
```

```text
10 → not present → add
5  → not present → add
3  → not present → add
4  → not present → add
3  → present → return 3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of elements
```

Worst case:

```text
No duplicate exists.
```

We scan all `n` elements.

Each `set` lookup is expected:

```text
O(1)
```

Therefore:

```text
Time = O(n)
```

Set may store all `n` elements:

```text
Space = O(n)
```

### Final

```text
Time:  O(n) expected
Space: O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we stop at the first duplicate?

Because the problem asks for the first repeating element according to left-to-right traversal.

---

### Q2. Why use a set?

We only need membership information:

```text
seen or not seen
```

A set is exactly designed for this.

---

### Q3. What if there is no repeating element?

Return:

```text
-1
```

Example:

```text
[1, 2, 3, 4]
```

Output:

```text
-1
```

---

### Q4. What is the difference between this and "contains duplicate"?

`Contains Duplicate` asks:

```text
Does ANY duplicate exist?
```

This asks:

```text
Which duplicate is encountered FIRST?
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Pattern

```text
FIRST REPEATING
        ↓
SCAN LEFT → RIGHT
        ↓
SET
        ↓
IF ALREADY SEEN → RETURN
```

### Master template

```python
seen = set()

for x in nums:
    if x in seen:
        return x
    seen.add(x)

return -1
```

Memorize this.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using frequency unnecessarily

You could count everything first, but that's extra work.

For first repeating:

```text
Set is enough.
```

---

### ❌ Mistake 2 — Sorting first

Don't do:

```python
nums.sort()
```

Sorting destroys the original left-to-right order.

Example:

```text
[5, 2, 7, 2]
```

The first repeating element is:

```text
2
```

Order matters.

---

### ❌ Mistake 3 — Returning after seeing a value twice in a frequency map

You don't need the entire frequency table.

You only need:

```text
seen/not seen
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → First Repeating Element
Exact LC → No exact canonical match
Pattern → Hashing / Set
Direction → Left → Right
Python → set()
Java → HashSet
Time → O(n) expected
Space → O(n)
```

### 🔥 Master Template

```python
seen = set()

for x in nums:
    if x in seen:
        return x
    seen.add(x)

return -1
```

---

# 🔥 PROBLEM 73 — FIRST NON-REPEATING ELEMENT

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### LeetCode Match

🔗 **Related: LC 387 — First Unique Character in a String — Easy**

Important distinction:

The CR2 problem is the **general array version**:

```text
[4, 5, 1, 2, 1, 5, 4, 9]
```

LC 387 is specifically about a **string** and asks for the index of the first unique character.

So:

> **Related pattern, not exact statement match.**

---

## What are we looking for?

The **first element whose total frequency is exactly 1**.

Example:

```text
[4, 5, 1, 2, 1, 5, 4, 9]
```

Frequencies:

```text
4 → 2
5 → 2
1 → 2
2 → 1
9 → 1
```

Scanning from left:

```text
4 → repeated
5 → repeated
1 → repeated
2 → unique
```

Answer:

```text
2
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array, find the first element that occurs exactly once.

Example:

```text
Input:
[2, 3, 4, 2, 3, 5]

Output:
4
```

Frequency:

```text
2 → 2
3 → 2
4 → 1
5 → 1
```

First unique:

```text
4
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

This problem is slightly different from Problem 72.

### Problem 72

```text
FIRST REPEATING
```

We need:

```text
Have I seen this before?
```

A `set` is enough.

---

### Problem 73

```text
FIRST NON-REPEATING
```

We need:

```text
How many times does this occur in the ENTIRE array?
```

Therefore:

> We need a **frequency map first**.

Then we scan the array again.

### Two-pass pattern

```text
Pass 1 → Count frequencies
Pass 2 → Find first element with frequency == 1
```

This is extremely important.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Pass 1

Create:

```text
freq = {}
```

Count every element.

### Pass 2

Traverse the original array again.

For each element:

```text
if freq[element] == 1:
    return element
```

If none exists:

```text
return -1
```

### Pseudocode

```text
create frequency map

for every element:
    increase its frequency

for every element:
    if frequency == 1:
        return element

return -1
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def first_non_repeating(nums):

    freq = {}

    # Pass 1: Count frequencies
    for num in nums:
        freq[num] = freq.get(num, 0) + 1

    # Pass 2: Find first element with frequency 1
    for num in nums:
        if freq[num] == 1:
            return num

    return -1


# Example
nums = [2, 3, 4, 2, 3, 5]

result = first_non_repeating(nums)

print(result)
```

Output:

```text
4
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;

class Main {

    public static int firstNonRepeating(int[] nums) {

        Map<Integer, Integer> freq = new HashMap<>();

        // Pass 1: Count frequencies
        for (int num : nums) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }

        // Pass 2: Find first frequency-1 element
        for (int num : nums) {
            if (freq.get(num) == 1) {
                return num;
            }
        }

        return -1;
    }

    public static void main(String[] args) {

        int[] nums = {2, 3, 4, 2, 3, 5};

        int result = firstNonRepeating(nums);

        System.out.println(result);
    }
}
```

Output:

```text
4
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [2, 3, 4, 2, 3, 5]
```

## PASS 1 — Build frequency map

Start:

```text
{}
```

### `2`

```text
{2: 1}
```

### `3`

```text
{2: 1, 3: 1}
```

### `4`

```text
{2: 1, 3: 1, 4: 1}
```

### second `2`

```text
{2: 2, 3: 1, 4: 1}
```

### second `3`

```text
{2: 2, 3: 2, 4: 1}
```

### `5`

```text
{2: 2, 3: 2, 4: 1, 5: 1}
```

Final frequency map:

```text
2 → 2
3 → 2
4 → 1
5 → 1
```

---

## PASS 2 — Find first unique

Scan original array:

```text
2 → frequency 2 → skip
3 → frequency 2 → skip
4 → frequency 1 → RETURN
```

Answer:

```text
4
```

### Why not return `5`?

Because `4` appears **before** `5`.

The word **first** means original array order matters.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Frequency map:

```text
2 → 2
3 → 2
4 → 1
5 → 1
```

Second pass:

```text
2 → repeated
3 → repeated
4 → unique → return
```

Result:

```text
4
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = array length
```

### Pass 1

We inspect every element:

```text
O(n)
```

### Pass 2

Again, at worst we inspect every element:

```text
O(n)
```

Total:

```text
O(n) + O(n)
= O(2n)
= O(n)
```

The frequency map can store up to `n` distinct values:

```text
Space = O(n)
```

### Final

```text
Time:  O(n) expected
Space: O(n)
```

### Important interview point

Two passes do **not** mean O(n²).

They are sequential:

```text
O(n) + O(n)
= O(n)
```

Not:

```text
O(n × n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can't we use only a set?

Because a set only tells us:

```text
seen / not seen
```

We need:

```text
frequency == 1
```

Therefore we need a frequency map.

---

### Q2. Why do we need two passes?

The first pass determines the **total frequency**.

Only after knowing total frequencies can we determine whether an element is unique.

---

### Q3. Can we return the first element that has not appeared before?

No.

That would solve a different problem.

Example:

```text
[2, 3, 2]
```

When we first see `2`, it hasn't appeared before—but eventually it repeats.

For non-repeating, we need:

```text
total frequency == 1
```

---

### Q4. What happens if every element repeats?

Example:

```text
[1, 1, 2, 2, 3, 3]
```

No unique element exists.

Return:

```text
-1
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is one of the most important distinctions from today's session.

## 🟢 First Repeating

```text
Need:
Have I seen this before?

Tool:
SET
```

Template:

```python
seen = set()

for x in nums:
    if x in seen:
        return x
    seen.add(x)
```

---

## 🔵 First Non-Repeating

```text
Need:
How many times does this occur?

Tool:
HASH MAP
```

Template:

```python
freq = {}

for x in nums:
    freq[x] = freq.get(x, 0) + 1

for x in nums:
    if freq[x] == 1:
        return x

return -1
```

### 🔥 This distinction must be automatic.

| Requirement     | Tool                  |
| --------------- | --------------------- |
| Have I seen it? | `set`                 |
| How many times? | `dict`                |
| First repeated? | `set` + left-to-right |
| First unique?   | `dict` + 2 passes     |

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using a set for non-repeating

A set cannot tell:

```text
frequency = 1
```

It only knows whether something exists.

---

### ❌ Mistake 2 — Returning the first newly seen element

Wrong.

Example:

```text
[5, 5, 2]
```

`5` is initially new, but it is not unique.

Correct answer:

```text
2
```

---

### ❌ Mistake 3 — Sorting the array

Sorting changes the original order.

Example:

```text
[5, 2, 3, 5, 2]
```

Unique:

```text
3
```

You must preserve original order to determine the **first** unique element.

---

### ❌ Mistake 4 — Thinking two loops means O(n²)

This:

```python
for x in nums:
    ...

for x in nums:
    ...
```

is:

```text
O(n) + O(n)
= O(n)
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

### Problem 73

```text
Problem → First Non-Repeating Element
Exact LC → No exact array match
Related → LC 387 First Unique Character in a String
Pattern → Frequency HashMap
Approach → Two passes
Time → O(n) expected
Space → O(n)
```

### 🔥 Master Template

```python
freq = {}

for x in nums:
    freq[x] = freq.get(x, 0) + 1

for x in nums:
    if freq[x] == 1:
        return x

return -1
```

---

# 🧠 DAY 8 — SESSION 1 MASTER COMPARISON

You have now learned **three closely related hashing patterns**:

```text
71 → COUNT
72 → FIRST REPEATING
73 → FIRST NON-REPEATING
```

## Pattern Map

```text
                 HASHING
                    │
        ┌───────────┴───────────┐
        │                       │
   FREQUENCY                 SET
        │                       │
   "HOW MANY?"           "SEEN BEFORE?"
        │                       │
        ▼                       ▼
      #71                    #72
 Frequency Map         First Repeating
        │
        ▼
      #73
 First Non-Repeating
```

---

# 🎯 SESSION 1 — FINAL MASTER TEST

**Do these WITHOUT looking at the solutions.**

### Problem 71

```text
nums = [5, 2, 5, 3, 2, 5, 4]
```

Expected frequency:

```text
5 → 3
2 → 2
3 → 1
4 → 1
```

---

### Problem 72

```text
nums = [8, 4, 6, 2, 4, 8]
```

Find the first repeating element.

---

### Problem 73

```text
nums = [7, 3, 5, 3, 7, 9, 5, 2]
```

Find the first non-repeating element.

---

## 🔥 TRICK TEST

Determine which data structure you should immediately think of:

```text
A. Count every number
B. Find first duplicate
C. Find first number appearing exactly once
D. Check whether a number has appeared before
E. Count character occurrences
```

Your mental answers should become:

```text
A → Dictionary
B → Set
C → Dictionary + 2 passes
D → Set
E → Dictionary
```

---

# 📈 CR2 PROGRESS

```text
DAY 1  ██████████ 10/10
DAY 2  ██████████ 20/20
DAY 3  ██████████ 30/30
DAY 4  ██████████ 40/40
DAY 5  ██████████ 50/50
DAY 6  ██████████ 60/60
DAY 7  ██████████ 70/70

DAY 8
Session 1 → 71–73 ✅
Session 2 → 74–76 ⏳
Session 3 → 77–80 ⏳

TOTAL → 73/100
```

### 🎯 Reproduction Drill

Before moving to Session 2, you should be able to write from memory:

```python
# Frequency
freq[x] = freq.get(x, 0) + 1

# First repeating
seen = set()
if x in seen:
    ...

# First non-repeating
# Pass 1 → frequency
# Pass 2 → frequency[x] == 1
```

**Do not memorize the three problems separately. Memorize the three patterns.**

Would you like to try the three master-test answers first, or move straight to Session 2?



# 🟣 CR2 — DAY 8: HASHING & FREQUENCY

# SESSION 2 — Problems 74–76

We continue from **73/100**.

Today:

| #  | Problem                                | Difficulty      | LeetCode                |
| -- | -------------------------------------- | --------------- | ----------------------- |
| 74 | Check Two Arrays Equal as Multisets    | 🟢 Basic        | ❌ No exact canonical LC |
| 75 | Union of Two Arrays                    | 🟢 Basic        | ❌ No exact canonical LC |
| 76 | Common Elements in Three Sorted Arrays | 🟢 Basic–Medium | ❌ No exact canonical LC |

## 🎯 Today's Core Skills

```text
74 → Frequency comparison
75 → Set / uniqueness
76 → Three-pointer intersection
```

The important progression is:

```text
Frequency Map
      ↓
Compare Frequencies
      ↓
Set Operations
      ↓
Multiple-Array Pointer Logic
```

---

# 🔥 PROBLEM 74 — CHECK TWO ARRAYS EQUAL AS MULTISETS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode match** for this basic formulation.

The important word is:

> **multiset**

A multiset cares about **how many times** each value occurs, but **does not care about order**.

Example:

```text
A = [1, 2, 2, 3]
B = [2, 3, 2, 1]
```

These are equal as multisets.

Why?

```text
1 → 1 time
2 → 2 times
3 → 1 time
```

Both have exactly the same frequency distribution.

But:

```text
A = [1, 2, 2]
B = [1, 2, 3]
```

are NOT equal.

### Senior Recognition

When you see:

> "Same elements with the same frequency, order doesn't matter"

think:

```text
HASH MAP → FREQUENCY COMPARISON
```

This is different from:

```text
Set comparison
```

because sets throw away duplicate counts.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two arrays, determine whether they contain exactly the same elements with exactly the same frequencies.

### Example 1

```text
A = [1, 2, 2, 3]
B = [3, 2, 1, 2]
```

Output:

```text
True
```

### Example 2

```text
A = [1, 2, 2, 3]
B = [1, 2, 3, 3]
```

Output:

```text
False
```

Because:

```text
A:
2 → 2 times

B:
2 → 1 time
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine two warehouses.

Warehouse A:

```text
1 → 1 box
2 → 2 boxes
3 → 1 box
```

Warehouse B:

```text
1 → 1 box
2 → 2 boxes
3 → 1 box
```

They contain the same inventory.

We don't care where the boxes are stored.

We only care about:

```text
ITEM → COUNT
```

Therefore:

### Step 1

Build frequency map of A.

### Step 2

Build frequency map of B.

### Step 3

Compare the two maps.

If identical:

```text
True
```

Otherwise:

```text
False
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Algorithm

1. Create `freq_a`.
2. Count every element in `A`.
3. Create `freq_b`.
4. Count every element in `B`.
5. Compare the dictionaries.
6. If equal → `True`.
7. Otherwise → `False`.

### Pseudocode

```text
freq_a = frequency map of A
freq_b = frequency map of B

if freq_a == freq_b:
    return True
else:
    return False
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def are_equal_multisets(a, b):

    if len(a) != len(b):
        return False

    freq_a = {}
    freq_b = {}

    # Count elements in first array
    for num in a:
        freq_a[num] = freq_a.get(num, 0) + 1

    # Count elements in second array
    for num in b:
        freq_b[num] = freq_b.get(num, 0) + 1

    return freq_a == freq_b


# Example
a = [1, 2, 2, 3]
b = [3, 2, 1, 2]

print(are_equal_multisets(a, b))
```

### Output

```text
True
```

### Important optimization

This:

```python
if len(a) != len(b):
    return False
```

is not strictly necessary if we compare complete frequency maps, but it is a useful early rejection.

If the lengths differ:

```text
They cannot possibly contain the same multiset.
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;

class Main {

    public static boolean areEqualMultisets(int[] a, int[] b) {

        if (a.length != b.length) {
            return false;
        }

        Map<Integer, Integer> freqA = new HashMap<>();
        Map<Integer, Integer> freqB = new HashMap<>();

        // Count first array
        for (int num : a) {
            freqA.put(num, freqA.getOrDefault(num, 0) + 1);
        }

        // Count second array
        for (int num : b) {
            freqB.put(num, freqB.getOrDefault(num, 0) + 1);
        }

        return freqA.equals(freqB);
    }

    public static void main(String[] args) {

        int[] a = {1, 2, 2, 3};
        int[] b = {3, 2, 1, 2};

        System.out.println(areEqualMultisets(a, b));
    }
}
```

Output:

```text
true
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
A = [1, 2, 2, 3]
B = [3, 2, 1, 2]
```

## Step 1 — Frequency of A

Start:

```text
{}
```

Read `1`:

```text
{1: 1}
```

Read `2`:

```text
{1: 1, 2: 1}
```

Read another `2`:

```text
{1: 1, 2: 2}
```

Read `3`:

```text
{1: 1, 2: 2, 3: 1}
```

---

## Step 2 — Frequency of B

Read `3`:

```text
{3: 1}
```

Read `2`:

```text
{3: 1, 2: 1}
```

Read `1`:

```text
{3: 1, 2: 1, 1: 1}
```

Read another `2`:

```text
{3: 1, 2: 2, 1: 1}
```

---

## Step 3 — Compare

```text
A frequency:
1 → 1
2 → 2
3 → 1

B frequency:
1 → 1
2 → 2
3 → 1
```

Equal:

```text
True
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text
freqA = {1=1, 2=2, 3=1}

freqB = {3=1, 2=2, 1=1}
```

Java `Map.equals()` compares mappings, not insertion order.

Therefore:

```text
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = len(A)
m = len(B)
```

Building the first frequency map:

```text
O(n)
```

Building the second:

```text
O(m)
```

Comparing maps is proportional to the number of distinct keys in the maps, at most:

```text
O(n + m)
```

Therefore:

```text
Time = O(n + m)
```

Space:

```text
O(n + m)
```

in the worst case when every element is distinct.

### Final

```text
Time:  O(n + m) expected
Space: O(n + m)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can't we simply compare the arrays?

Because order may differ.

```text
[1,2,2,3]
[3,2,1,2]
```

are equal as multisets.

---

### Q2. Why can't we use a set?

Because a set removes duplicate information.

For example:

```text
[1, 2, 2]
```

and

```text
[1, 2]
```

both become:

```text
{1, 2}
```

A set incorrectly says they contain the same elements.

---

### Q3. Could sorting solve this?

Yes.

You could sort both arrays and compare:

```text
sort(A)
sort(B)
```

But that gives approximately:

```text
O(n log n + m log m)
```

The frequency-map approach gives expected:

```text
O(n + m)
```

when hashing is appropriate.

---

### Q4. What is a multiset?

A collection where:

```text
order does not matter
frequency does matter
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recognition phrase

```text
Same elements
+
same frequency
+
order doesn't matter
```

↓

```text
FREQUENCY MAP
```

### Master template

```python
freq = {}

for x in arr:
    freq[x] = freq.get(x, 0) + 1
```

Then compare maps.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Comparing arrays directly

```python
[1, 2, 3] == [3, 2, 1]
```

returns:

```text
False
```

because list equality cares about order.

---

### ❌ Mistake 2 — Using sets

```python
set([1, 2, 2])
```

becomes:

```text
{1, 2}
```

Duplicate information disappears.

---

### ❌ Mistake 3 — Sorting unnecessarily

Sorting works, but hashing is the more direct pattern when values are hashable.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Equal as multisets
Exact LC → No exact canonical match
Key concept → Frequency equality
Tool → Dictionary / HashMap
Order → Doesn't matter
Duplicates → Matter
Time → O(n + m) expected
Space → O(n + m)
```

---

# 🔥 PROBLEM 75 — UNION OF TWO ARRAYS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode match** for this basic formulation.

### Problem

Given two arrays, return all **distinct** elements that appear in either array.

Example:

```text
A = [1, 2, 2, 3]
B = [3, 4, 4, 5]
```

Union:

```text
[1, 2, 3, 4, 5]
```

Duplicates are removed.

### Senior Recognition

The keyword is:

> **distinct elements from both arrays**

Think:

```text
SET
```

Because a set automatically stores unique values.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Union means:

```text
Everything present in A
+
Everything present in B
```

but each value appears only once.

Example:

```text
A = [1, 2, 3]
B = [3, 4, 5]
```

Result:

```text
[1, 2, 3, 4, 5]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine two classrooms.

Class A has:

```text
Alice
Bob
Charlie
```

Class B has:

```text
Charlie
David
Eve
```

If we want everyone across both classrooms:

```text
Alice
Bob
Charlie
David
Eve
```

Charlie appears in both but should be listed only once.

That's exactly what a set does.

```text
set(A) ∪ set(B)
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Approach 1 — Python set union

1. Convert first array into a set.
2. Convert second array into a set.
3. Take their union.
4. Convert to list if required.

### Pseudocode

```text
setA = set(A)
setB = set(B)

union = setA ∪ setB

return union
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def union_of_arrays(a, b):

    result = set(a)

    for num in b:
        result.add(num)

    return list(result)


# Example
a = [1, 2, 2, 3]
b = [3, 4, 4, 5]

print(union_of_arrays(a, b))
```

Possible output:

```text
[1, 2, 3, 4, 5]
```

The exact order of a set-based result is not guaranteed.

### If the problem requires sorted output:

```python
return sorted(set(a) | set(b))
```

But don't sort unless the problem asks for ordering.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Set;

class Main {

    public static Set<Integer> unionOfArrays(int[] a, int[] b) {

        Set<Integer> result = new HashSet<>();

        for (int num : a) {
            result.add(num);
        }

        for (int num : b) {
            result.add(num);
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 2, 2, 3};
        int[] b = {3, 4, 4, 5};

        Set<Integer> result = unionOfArrays(a, b);

        System.out.println(result);
    }
}
```

Possible output:

```text
[1, 2, 3, 4, 5]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
A = [1, 2, 2, 3]
B = [3, 4, 4, 5]
```

Start:

```text
result = {}
```

Process A:

```text
1 → {1}
2 → {1,2}
2 → {1,2}
3 → {1,2,3}
```

Process B:

```text
3 → {1,2,3}
4 → {1,2,3,4}
4 → {1,2,3,4}
5 → {1,2,3,4,5}
```

Final:

```text
{1,2,3,4,5}
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java `HashSet` performs the same uniqueness logic:

```text
1 → add
2 → add
2 → ignored
3 → add

3 → ignored
4 → add
4 → ignored
5 → add
```

Final set:

```text
{1,2,3,4,5}
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = len(A)
m = len(B)
```

We process every element once:

```text
n + m
```

Expected set insertion:

```text
O(1)
```

Therefore:

```text
Time = O(n + m)
```

The result can contain up to:

```text
n + m
```

distinct elements.

Therefore:

```text
Space = O(n + m)
```

### Final

```text
Time:  O(n + m) expected
Space: O(n + m)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a set?

Because the union requires **unique elements**.

---

### Q2. What happens to duplicates?

They are automatically ignored.

```text
[1, 1, 1]
```

becomes:

```text
{1}
```

---

### Q3. Is union the same as concatenation?

No.

Concatenation:

```text
[1,2] + [2,3]
= [1,2,2,3]
```

Union:

```text
{1,2,3}
```

---

### Q4. Does union preserve order?

A normal set does not guarantee the original order.

If order is required, the implementation must explicitly preserve it.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recognition

```text
UNIQUE ELEMENTS
FROM A + B
```

↓

```text
SET
```

Master idea:

```python
result = set(a)

for x in b:
    result.add(x)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using a list and checking every time

```python
if x not in result:
    result.append(x)
```

This can become O(n²) because list membership is O(n).

---

### ❌ Mistake 2 — Using a frequency map

You don't need counts.

The question only asks:

```text
Does the value exist?
```

Therefore:

```text
Set > Dictionary
```

---

### ❌ Mistake 3 — Assuming output order

Set order should not be treated as the required order unless the problem specifies it.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Union of Two Arrays
Exact LC → No exact canonical match
Need → Distinct values
Tool → Set
Duplicates → Removed
Time → O(n + m) expected
Space → O(n + m)
```

### 🔥 Master Template

```python
result = set(a)

for x in b:
    result.add(x)
```

---

# 🔥 PROBLEM 76 — COMMON ELEMENTS IN THREE SORTED ARRAYS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No exact canonical LeetCode match** for this specific three-sorted-array formulation.

This is an important **multi-pointer / intersection** pattern.

### Problem

Given **three sorted arrays**, find elements that appear in all three.

Example:

```text
A = [1, 5, 10, 20, 40, 80]
B = [6, 7, 20, 80, 100]
C = [3, 4, 15, 20, 30, 70, 80, 120]
```

Common elements:

```text
[20, 80]
```

### Senior Recognition

The critical clue is:

> **Three arrays are sorted.**

Don't immediately use nested loops.

Sorted order gives us pointer movement.

Think:

```text
THREE SORTED ARRAYS
        ↓
THREE POINTERS
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

We need values that exist in:

```text
A AND B AND C
```

Example:

```text
A = [1, 2, 3, 4]
B = [2, 3, 4, 5]
C = [3, 4, 5, 6]
```

Common:

```text
[3, 4]
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Suppose:

```text
A[i] = 2
B[j] = 5
C[k] = 7
```

Can `2` ever match `5` or `7` if we move the pointers in the wrong direction?

No.

Because arrays are sorted.

The smallest current value cannot possibly catch a larger value by moving backward.

### Key rule

At every step:

> **Advance the pointer pointing to the smallest current value.**

Why?

Suppose:

```text
A[i] = 2
B[j] = 5
C[k] = 7
```

`2` is too small.

Moving `B` or `C` would make them even larger.

The only useful move is:

```text
i += 1
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

Let:

```text
i = 0
j = 0
k = 0
```

While all three pointers are inside their arrays:

### Case 1 — All equal

```text
A[i] == B[j] == C[k]
```

We found a common element.

Add it.

Then move all three pointers.

---

### Case 2 — A is smallest

```text
A[i] < B[j]
```

Move `i`.

---

### Case 3 — B is smallest

```text
B[j] < C[k]
```

Move `j`.

---

### Otherwise

C is the smallest.

Move `k`.

### Pseudocode

```text
i = j = k = 0

while i < len(A) and j < len(B) and k < len(C):

    if A[i] == B[j] == C[k]:
        add A[i]
        i++
        j++
        k++

    else if A[i] < B[j]:
        i++

    else if B[j] < C[k]:
        j++

    else:
        k++
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def common_elements(a, b, c):

    i = 0
    j = 0
    k = 0

    result = []

    while i < len(a) and j < len(b) and k < len(c):

        if a[i] == b[j] == c[k]:
            result.append(a[i])

            i += 1
            j += 1
            k += 1

        elif a[i] < b[j]:
            i += 1

        elif b[j] < c[k]:
            j += 1

        else:
            k += 1

    return result


# Example
a = [1, 5, 10, 20, 40, 80]
b = [6, 7, 20, 80, 100]
c = [3, 4, 15, 20, 30, 70, 80, 120]

print(common_elements(a, b, c))
```

Output:

```text
[20, 80]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.ArrayList;
import java.util.List;

class Main {

    public static List<Integer> commonElements(
            int[] a,
            int[] b,
            int[] c) {

        int i = 0;
        int j = 0;
        int k = 0;

        List<Integer> result = new ArrayList<>();

        while (i < a.length &&
               j < b.length &&
               k < c.length) {

            if (a[i] == b[j] && b[j] == c[k]) {

                result.add(a[i]);

                i++;
                j++;
                k++;

            } else if (a[i] < b[j]) {

                i++;

            } else if (b[j] < c[k]) {

                j++;

            } else {

                k++;
            }
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 5, 10, 20, 40, 80};
        int[] b = {6, 7, 20, 80, 100};
        int[] c = {3, 4, 15, 20, 30, 70, 80, 120};

        List<Integer> result = commonElements(a, b, c);

        System.out.println(result);
    }
}
```

Output:

```text
[20, 80]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
A = [1, 5, 10, 20, 40, 80]
B = [6, 7, 20, 80, 100]
C = [3, 4, 15, 20, 30, 70, 80, 120]
```

Start:

```text
i = 0 → A[i] = 1
j = 0 → B[j] = 6
k = 0 → C[k] = 3
```

We have:

```text
1, 6, 3
```

Smallest:

```text
1
```

Move `i`.

---

### Step 2

```text
A[i] = 5
B[j] = 6
C[k] = 3
```

Smallest:

```text
3
```

Move `k`.

---

### Step 3

```text
5, 6, 4
```

Smallest:

```text
4
```

Move `k`.

---

### Step 4

```text
5, 6, 15
```

Smallest:

```text
5
```

Move `i`.

---

### Step 5

```text
10, 6, 15
```

Smallest:

```text
6
```

Move `j`.

---

### Step 6

```text
10, 7, 15
```

Smallest:

```text
7
```

Move `j`.

---

### Step 7

```text
10, 20, 15
```

Smallest:

```text
10
```

Move `i`.

---

### Step 8

```text
20, 20, 15
```

Smallest:

```text
15
```

Move `k`.

---

### Step 9

```text
20, 20, 20
```

🎯 All equal!

Add:

```text
20
```

Move all:

```text
i → 4
j → 3
k → 4
```

---

### Step 10

```text
A[i] = 40
B[j] = 80
C[k] = 30
```

Smallest:

```text
30
```

Move `k`.

---

### Step 11

```text
40, 80, 70
```

Smallest:

```text
40
```

Move `i`.

---

### Step 12

```text
80, 80, 70
```

Smallest:

```text
70
```

Move `k`.

---

### Step 13

```text
80, 80, 80
```

🎯 All equal!

Add:

```text
80
```

Move all pointers.

Now:

```text
i = 6
```

`A` is exhausted.

Stop.

Final:

```text
[20, 80]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs identical pointer movement:

```text
A=1 B=6 C=3 → move A
A=5 B=6 C=3 → move C
A=5 B=6 C=4 → move C
A=5 B=6 C=15 → move A
A=10 B=6 C=15 → move B
A=10 B=7 C=15 → move B
A=10 B=20 C=15 → move A
A=20 B=20 C=15 → move C
A=20 B=20 C=20 → FOUND 20
```

Then:

```text
A=40 B=80 C=30 → move C
A=40 B=80 C=70 → move A
A=80 B=80 C=70 → move C
A=80 B=80 C=80 → FOUND 80
```

Final:

```text
[20, 80]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = len(A)
m = len(B)
p = len(C)
```

Every pointer only moves **forward**.

Pointer `i` moves at most `n` times.

Pointer `j` moves at most `m` times.

Pointer `k` moves at most `p` times.

Therefore total pointer movements are bounded by:

```text
n + m + p
```

So:

```text
Time = O(n + m + p)
```

Output space:

```text
O(r)
```

where `r` is the number of common elements.

Auxiliary space excluding output:

```text
O(1)
```

### Final

```text
Time:  O(n + m + p)
Auxiliary Space: O(1)
Output Space: O(r)
```

### 🔥 Why this is better than nested loops

Naive approach:

```text
for every A element:
    search B
    search C
```

can approach:

```text
O(n × m × p)
```

The sorted property lets us reduce this to:

```text
O(n + m + p)
```

That's the interview-worthy insight.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can we move only the smallest pointer?

Because all arrays are sorted.

If:

```text
A[i] = 5
B[j] = 10
C[k] = 15
```

`5` cannot match either `10` or `15`.

Moving B or C would only increase their values.

So `A` must advance.

---

### Q2. Why do all three pointers move when values are equal?

Because we have already consumed that common value from all three arrays.

Moving only one pointer could cause unnecessary repeated comparison.

---

### Q3. What is the critical prerequisite?

The arrays must be sorted.

Without sorting, the pointer logic is invalid.

---

### Q4. Can we use sets?

Yes.

You could create sets and intersect them:

```python
set(a) & set(b) & set(c)
```

But the three-pointer solution specifically exploits the fact that the arrays are already sorted and uses O(1) auxiliary space.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 Three Sorted Arrays → Three Pointers

Memorize:

```text
Sorted arrays
      ↓
Multiple pointers
      ↓
Compare current values
      ↓
Move smallest
```

### Master template

```python
i = j = k = 0

while i < len(a) and j < len(b) and k < len(c):

    if a[i] == b[j] == c[k]:
        result.append(a[i])
        i += 1
        j += 1
        k += 1

    elif a[i] < b[j]:
        i += 1

    elif b[j] < c[k]:
        j += 1

    else:
        k += 1
```

### 🧠 Recognition trigger

> **"Several sorted arrays + common elements/intersection"**

→ Think **multi-pointer technique**.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using nested loops

This ignores the sorted property and can be much slower.

---

### ❌ Mistake 2 — Moving the largest pointer

Suppose:

```text
2, 5, 9
```

If you move `9`, you get an even larger value.

It won't help `2` catch up.

Move the **smallest**.

---

### ❌ Mistake 3 — Forgetting to move all pointers after a match

If:

```text
A[i] == B[j] == C[k]
```

we found the common value.

Advance all three.

---

### ❌ Mistake 4 — Applying this to unsorted arrays

The logic depends on sorted order.

For unsorted arrays, consider hashing instead.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Common Elements in Three Sorted Arrays
Exact LC → No exact canonical match
Pattern → Three pointers
Prerequisite → Arrays sorted
Rule → Move smallest current value
Time → O(n + m + p)
Auxiliary Space → O(1)
Output Space → O(r)
```

---

# 🧠 DAY 8 — SESSION 2 MASTER PATTERN MAP

You now have **six hashing/frequency fundamentals**:

```text
71 ─ Frequency Map
       ↓
       "HOW MANY?"

72 ─ First Repeating
       ↓
       "SEEN BEFORE?"
       ↓
       SET

73 ─ First Non-Repeating
       ↓
       "FREQUENCY == 1?"
       ↓
       HASH MAP + 2 PASSES

74 ─ Equal Multisets
       ↓
       "SAME FREQUENCIES?"
       ↓
       TWO HASH MAPS

75 ─ Union
       ↓
       "UNIQUE FROM A + B?"
       ↓
       SET

76 ─ Common in 3 Sorted Arrays
       ↓
       "COMMON + SORTED?"
       ↓
       THREE POINTERS
```

## 🔥 The Decision Tree

```text
What does the problem ask?
          │
          ├── Count occurrences?
          │       ↓
          │    DICTIONARY
          │
          ├── Have I seen it?
          │       ↓
          │      SET
          │
          ├── Same elements + same frequencies?
          │       ↓
          │    FREQUENCY MAP
          │
          ├── Unique elements only?
          │       ↓
          │      SET
          │
          └── Common elements in sorted arrays?
                  ↓
            MULTI-POINTER
```

---

# 🎯 SESSION 2 — FINAL MASTER TEST

Do these **without looking back at the solutions**.

### 74 — Multiset

```text
A = [4, 2, 2, 7, 4]
B = [2, 4, 7, 2, 4]
```

Should return:

```text
True
```

Now test:

```text
A = [4, 2, 2, 7, 4]
B = [2, 4, 7, 7, 4]
```

Should return:

```text
False
```

---

### 75 — Union

```text
A = [1, 2, 2, 4]
B = [2, 3, 4, 5]
```

Expected distinct values:

```text
{1, 2, 3, 4, 5}
```

---

### 76 — Three Sorted Arrays

```text
A = [1, 2, 3, 4, 5, 6]
B = [2, 3, 5, 7]
C = [1, 3, 5, 8]
```

Expected:

```text
[3, 5]
```

---

# 🧪 TRICK QUESTIONS

### Trick 1

```text
A = [1, 1, 2]
B = [1, 2]
```

Are they equal as **sets**?

```text
YES
```

Are they equal as **multisets**?

```text
NO
```

Why?

```text
Set → ignores frequency
Multiset → respects frequency
```

---

### Trick 2

You have:

```text
A = [2, 10]
B = [3, 10]
C = [5, 10]
```

Current values:

```text
2, 3, 5
```

Which pointer moves?

```text
A pointer
```

Because `2` is smallest.

---

### Trick 3

You have:

```text
A = [5, 10]
B = [5, 12]
C = [5, 20]
```

All current values are:

```text
5
```

What happens?

```text
5 is common
→ add 5
→ move all three pointers
```

---

# 📈 CR2 PROGRESS

```text
DAY 1  ██████████ 10/10
DAY 2  ██████████ 20/20
DAY 3  ██████████ 30/30
DAY 4  ██████████ 40/40
DAY 5  ██████████ 50/50
DAY 6  ██████████ 60/60
DAY 7  ██████████ 70/70

DAY 8
Session 1 → 71–73 ✅
Session 2 → 74–76 ✅
Session 3 → 77–80 ⏳

TOTAL → 76/100
```

## 🔥 Reproduction Drill

Before Session 3, you should be able to write these three patterns from memory:

### 74

```python
freq_a = {}
freq_b = {}
```

Count both and compare.

### 75

```python
result = set(a)

for x in b:
    result.add(x)
```

### 76

```python
i = j = k = 0

while ...:
    if all equal:
        ...
    elif a[i] < b[j]:
        i += 1
    elif b[j] < c[k]:
        j += 1
    else:
        k += 1
```

**The real mastery goal today is not remembering three programs. It is recognizing which tool the problem is asking for: `dict`, `set`, or multi-pointer.**

Would you like to solve the Session 2 master test on your own first, or should I give you the answers with brief explanations?



# 🟣 CR2 — DAY 8: HASHING & FREQUENCY

# SESSION 3 — Problems 77–80

You are now at:

```text
DAY 8 → 76/100 complete
```

This is the **final session of Day 8**.

Today we move from basic hashing into **real interview-level frequency patterns**:

| #  | Problem                              | Difficulty      | LeetCode                                         |
| -- | ------------------------------------ | --------------- | ------------------------------------------------ |
| 77 | Group Anagrams                       | 🟡 Medium       | LC 49                                            |
| 78 | Longest Consecutive Sequence         | 🟡 Medium       | LC 128                                           |
| 79 | Pairs With Given Difference          | 🟢 Basic–Medium | Related pattern; no single exact canonical match |
| 80 | Array Intersection With Multiplicity | 🟢 Easy         | LC 350                                           |

---

# 🔥 PROBLEM 77 — GROUP ANAGRAMS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

🔥 **LC 49 — Group Anagrams — Medium**

This is an actual interview problem.

The key concept is:

> **Different strings can have the same character frequency.**

Example:

```text
"eat"
"tea"
"ate"
```

All contain:

```text
a → 1
e → 1
t → 1
```

Therefore they belong to the same group.

Another group:

```text
"tan"
"nat"
```

Both contain:

```text
a → 1
n → 1
t → 1
```

---

## 🧠 Senior Pattern Recognition

Whenever you see:

```text
Anagrams
Group anagrams
Same characters
Rearrangements
```

Think:

```text
STRING
   ↓
CANONICAL REPRESENTATION
   ↓
HASH MAP
```

There are two major ways to create the canonical representation.

### Method 1 — Sorted string

```text
"eat" → "aet"
"tea" → "aet"
"ate" → "aet"
```

Same key → same group.

### Method 2 — Character frequency

```text
"aet" frequency
```

or:

```text
(1,0,0,1,...)
```

This can be more efficient when the alphabet is fixed.

For CR2, we will use the **easy-to-recognize sorted-key approach** first.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a list of strings, group strings that are anagrams of each other.

Example:

```text
Input:
["eat", "tea", "tan", "ate", "nat", "bat"]
```

Valid output:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

The order of groups does not matter.

The order inside a group also generally does not matter unless explicitly specified.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of every word needing an **ID card**.

For:

```text
eat
```

Sort its letters:

```text
eat
↓
aet
```

For:

```text
tea
```

Sort:

```text
tea
↓
aet
```

For:

```text
ate
↓
aet
```

Therefore:

```text
aet → ["eat", "tea", "ate"]
```

For:

```text
bat
↓
abt
```

That's a different key.

So:

```text
abt → ["bat"]
```

### The master idea

```text
Different input
       ↓
same canonical key
       ↓
same group
```

This is a huge general interview pattern.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Create an empty dictionary called `groups`.
2. Traverse every string.
3. Sort its characters.
4. Convert the sorted characters into a string key.
5. If the key doesn't exist, create an empty group.
6. Add the original string to that key's group.
7. Return all dictionary values.

### Pseudocode

```text
groups = {}

for word in words:

    key = sorted version of word

    if key not in groups:
        create empty list

    add word to groups[key]

return all groups
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def group_anagrams(words):

    groups = {}

    for word in words:

        # Create canonical key
        key = ''.join(sorted(word))

        # Create group if key doesn't exist
        if key not in groups:
            groups[key] = []

        # Add original word
        groups[key].append(word)

    return list(groups.values())


# Example
words = ["eat", "tea", "tan", "ate", "nat", "bat"]

result = group_anagrams(words)

print(result)
```

Possible output:

```text
[['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]
```

### 🔥 Important

We store:

```python
groups[key].append(word)
```

not:

```python
groups[key].append(key)
```

Because we want the **original strings** in the result.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.*;

class Main {

    public static List<List<String>> groupAnagrams(String[] words) {

        Map<String, List<String>> groups = new HashMap<>();

        for (String word : words) {

            char[] chars = word.toCharArray();

            Arrays.sort(chars);

            String key = new String(chars);

            if (!groups.containsKey(key)) {
                groups.put(key, new ArrayList<>());
            }

            groups.get(key).add(word);
        }

        return new ArrayList<>(groups.values());
    }

    public static void main(String[] args) {

        String[] words = {
            "eat",
            "tea",
            "tan",
            "ate",
            "nat",
            "bat"
        };

        List<List<String>> result = groupAnagrams(words);

        System.out.println(result);
    }
}
```

Possible output:

```text
[[eat, tea, ate], [bat], [tan, nat]]
```

The group ordering may differ because `HashMap` does not guarantee ordering.

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
["eat", "tea", "tan", "ate", "nat", "bat"]
```

Start:

```text
groups = {}
```

### Step 1

```text
word = "eat"
```

Sorted:

```text
"aet"
```

Create:

```text
"aet" → ["eat"]
```

---

### Step 2

```text
word = "tea"
```

Sorted:

```text
"aet"
```

Existing group:

```text
"aet" → ["eat", "tea"]
```

---

### Step 3

```text
word = "tan"
```

Sorted:

```text
"ant"
```

Create:

```text
"ant" → ["tan"]
```

---

### Step 4

```text
word = "ate"
```

Sorted:

```text
"aet"
```

Add:

```text
"aet" → ["eat", "tea", "ate"]
```

---

### Step 5

```text
word = "nat"
```

Sorted:

```text
"ant"
```

Add:

```text
"ant" → ["tan", "nat"]
```

---

### Step 6

```text
word = "bat"
```

Sorted:

```text
"abt"
```

Create:

```text
"abt" → ["bat"]
```

### Final dictionary

```text
{
    "aet": ["eat", "tea", "ate"],
    "ant": ["tan", "nat"],
    "abt": ["bat"]
}
```

Return values:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java performs the same transformation:

```text
eat → aet → group aet
tea → aet → same group
tan → ant → group ant
ate → aet → same group
nat → ant → same group
bat → abt → group abt
```

The important part is:

```text
Original word → canonical key → HashMap bucket
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of strings
k = average string length
```

For each string, we sort its characters.

Sorting one string costs approximately:

```text
O(k log k)
```

For `n` strings:

```text
O(n × k log k)
```

Hash-map insertion is expected O(1) after generating the key.

Therefore:

```text
Time = O(n × k log k)
```

Space:

The stored groups contain all input strings:

```text
O(nk)
```

The keys also require storage.

So overall:

```text
Space = O(nk)
```

### Final

```text
Time:  O(n × k log k)
Space: O(nk)
```

### Senior optimization

If the alphabet is fixed, e.g. lowercase English letters, you can use a **26-character frequency signature** instead of sorting.

That can reduce the per-string key generation to:

```text
O(k)
```

giving approximately:

```text
O(nk)
```

But for CR2, **sorted-key hashing is the easiest version to master first.**

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why does sorting work?

Because anagrams contain exactly the same characters.

Therefore their sorted representations are identical.

```text
eat → aet
tea → aet
ate → aet
```

---

### Q2. Why use a HashMap?

Because we need:

```text
canonical key → group of original strings
```

---

### Q3. Can we use character frequencies instead of sorting?

Yes.

For lowercase English letters:

```text
a → count
b → count
...
z → count
```

Two strings with the same frequency vector are anagrams.

---

### Q4. What is the key idea to remember?

> **Convert equivalent objects into the same canonical representation, then hash by that representation.**

This pattern appears far beyond anagrams.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

## 🔥 Canonical Key Pattern

```text
Different objects
      ↓
Same property
      ↓
Same canonical key
      ↓
HashMap
      ↓
Group
```

For anagrams:

```text
word
 ↓
sort characters
 ↓
key
 ↓
HashMap[key]
```

### Master Template

```python
groups = {}

for word in words:

    key = ''.join(sorted(word))

    if key not in groups:
        groups[key] = []

    groups[key].append(word)
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Comparing words directly

```text
eat != tea
```

But they are anagrams.

---

### ❌ Mistake 2 — Sorting the original words

Don't mutate the original word unnecessarily.

We need:

```text
original → result
key → grouping
```

---

### ❌ Mistake 3 — Forgetting to convert sorted characters back to a string

Python:

```python
sorted("eat")
```

returns:

```text
['a', 'e', 't']
```

Therefore use:

```python
''.join(sorted(word))
```

---

### ❌ Mistake 4 — Assuming output ordering

LeetCode generally accepts any valid grouping order.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Group Anagrams
LeetCode → LC 49
Difficulty → Medium
Pattern → Canonical Key + HashMap
Key → Sorted characters
Time → O(n × k log k)
Space → O(nk)
```

### 🔥 One-line recognition

> **"Group things that are equivalent under rearrangement" → canonical representation + HashMap.**

---

# 🔥 PROBLEM 78 — LONGEST CONSECUTIVE SEQUENCE

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

🔥 **LC 128 — Longest Consecutive Sequence — Medium**

This is a major interview problem.

Example:

```text
[100, 4, 200, 1, 3, 2]
```

The longest consecutive sequence is:

```text
1, 2, 3, 4
```

Length:

```text
4
```

### Critical Insight

The array is **not sorted**.

Don't sort immediately.

The optimal solution uses a:

```text
SET
```

and achieves expected:

```text
O(n)
```

This is a classic example of:

> **Using hashing to remove ordering requirements.**

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an unsorted array, find the length of the longest sequence of consecutive integers.

Example:

```text
Input:
[100, 4, 200, 1, 3, 2]

Output:
4
```

Because:

```text
1 → 2 → 3 → 4
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Put everything into a set:

```text
{100, 4, 200, 1, 3, 2}
```

Now suppose we look at:

```text
1
```

Ask:

```text
Does 0 exist?
```

No.

Therefore `1` is the **start** of a sequence.

Now check:

```text
2 → yes
3 → yes
4 → yes
5 → no
```

Sequence length:

```text
4
```

### Why don't we start from `2`?

Because:

```text
1 exists
```

So `2` is not the beginning.

This is the critical optimization.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Convert the array to a set.
2. Set `longest = 0`.
3. For each number:

   * Check whether `num - 1` exists.
4. If it exists:

   * `num` is not the start → skip.
5. If it does not exist:

   * `num` is a sequence start.
   * Check `num + 1`, `num + 2`, etc.
   * Count the sequence.
6. Update `longest`.
7. Return `longest`.

### Pseudocode

```text
numbers = set(nums)
longest = 0

for num in numbers:

    if num - 1 is not in numbers:

        current = num
        length = 1

        while current + 1 exists:
            current += 1
            length += 1

        longest = max(longest, length)

return longest
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def longest_consecutive(nums):

    numbers = set(nums)

    longest = 0

    for num in numbers:

        # Only start from the beginning
        # of a consecutive sequence.
        if num - 1 not in numbers:

            current = num
            length = 1

            # Build the sequence forward
            while current + 1 in numbers:
                current += 1
                length += 1

            longest = max(longest, length)

    return longest


# Example
nums = [100, 4, 200, 1, 3, 2]

print(longest_consecutive(nums))
```

Output:

```text
4
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Set;

class Main {

    public static int longestConsecutive(int[] nums) {

        Set<Integer> numbers = new HashSet<>();

        for (int num : nums) {
            numbers.add(num);
        }

        int longest = 0;

        for (int num : numbers) {

            // Start only if num is the beginning
            // of a consecutive sequence.
            if (!numbers.contains(num - 1)) {

                int current = num;
                int length = 1;

                while (numbers.contains(current + 1)) {
                    current++;
                    length++;
                }

                longest = Math.max(longest, length);
            }
        }

        return longest;
    }

    public static void main(String[] args) {

        int[] nums = {100, 4, 200, 1, 3, 2};

        System.out.println(longestConsecutive(nums));
    }
}
```

Output:

```text
4
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
[100, 4, 200, 1, 3, 2]
```

Set:

```text
{100, 4, 200, 1, 3, 2}
```

### `100`

Check:

```text
99 exists?
```

No.

So `100` starts a sequence.

```text
100 → 101?
```

No.

Length:

```text
1
```

---

### `4`

Check:

```text
3 exists?
```

Yes.

Therefore `4` is **not** a sequence start.

Skip.

---

### `200`

Check:

```text
199 exists?
```

No.

Start sequence:

```text
200 → 201?
```

No.

Length:

```text
1
```

---

### `1`

Check:

```text
0 exists?
```

No.

So `1` starts a sequence.

Check:

```text
2 → yes
3 → yes
4 → yes
5 → no
```

Therefore:

```text
length = 4
```

Update:

```text
longest = 4
```

---

### `3`

Check:

```text
2 exists?
```

Yes.

Skip.

---

### `2`

Check:

```text
1 exists?
```

Yes.

Skip.

Final:

```text
longest = 4
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text
100 → no 99 → start → length 1
4   → 3 exists → skip
200 → no 199 → start → length 1
1   → no 0 → start
      2 exists
      3 exists
      4 exists
      5 absent
      length 4
3   → 2 exists → skip
2   → 1 exists → skip
```

Answer:

```text
4
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

At first glance, the nested `while` may look like:

```text
O(n²)
```

But it isn't.

### Why?

We only start a sequence when:

```text
num - 1
```

does not exist.

Every number belongs to a consecutive chain that is expanded from its beginning.

Across all chains, each element is processed a bounded number of times.

Therefore expected total:

```text
O(n)
```

Building the set:

```text
O(n)
```

Scanning:

```text
O(n)
```

Sequence expansion overall:

```text
O(n)
```

Therefore:

```text
Time = O(n) expected
```

Set storage:

```text
Space = O(n)
```

### Final

```text
Time:  O(n) expected
Space: O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why not sort?

Sorting gives:

```text
O(n log n)
```

The HashSet solution achieves expected:

```text
O(n)
```

---

### Q2. Why check `num - 1`?

To identify the **start** of a sequence.

If:

```text
num - 1 exists
```

then `num` is inside an existing sequence.

---

### Q3. Why does the nested while not make it O(n²)?

Because sequence expansion is performed only from sequence starts, and across the input the consecutive elements are not repeatedly expanded from every position.

---

### Q4. What happens with duplicates?

The set automatically removes them.

Example:

```text
[1,2,2,3]
```

becomes:

```text
{1,2,3}
```

and the sequence length remains:

```text
3
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Recognition

```text
Unsorted numbers
+
Longest consecutive run
+
O(n) expected desired
```

↓

```text
SET
```

### Master trick

```text
num - 1 does NOT exist
        ↓
num is a sequence START
```

Then:

```text
num + 1
num + 2
num + 3
...
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Sorting automatically

Sorting works, but misses the optimal O(n) hashing solution.

---

### ❌ Mistake 2 — Expanding from every number

Wrong:

```text
for every num:
    search num+1
```

You must first check:

```text
num - 1 not in set
```

---

### ❌ Mistake 3 — Forgetting duplicates

Set handles duplicates automatically.

---

### ❌ Mistake 4 — Thinking nested loop always means O(n²)

This is a classic interview trap.

You need to analyze **total work**, not just count loops.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Longest Consecutive Sequence
LeetCode → LC 128
Difficulty → Medium
Pattern → HashSet
Key trick → Find sequence starts
Time → O(n) expected
Space → O(n)
```

### 🔥 One-line recognition

> **Unsorted integers + longest consecutive run → HashSet + sequence-start detection.**

---

# 🔥 PROBLEM 79 — PAIRS WITH GIVEN DIFFERENCE

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

❌ **No single exact canonical LeetCode match** for this basic formulation.

There are related problems involving pair differences, but this CR2 problem is the fundamental placement pattern.

### Problem

Given an array and a target difference `k`, count/find pairs satisfying:

```text
|a - b| = k
```

For example:

```text
nums = [1, 5, 3, 4, 2]
k = 2
```

Valid value pairs:

```text
(1,3)
(3,5)
(2,4)
```

So there are:

```text
3
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

We need pairs whose absolute difference equals `k`.

Example:

```text
[1, 5, 3, 4, 2]
k = 2
```

Check:

```text
1 ↔ 3 → difference 2
3 ↔ 5 → difference 2
2 ↔ 4 → difference 2
```

Answer:

```text
3
```

### Important assumption for CR2

We count **distinct value pairs**, not every possible duplicate-index pair.

So:

```text
[1, 1, 3]
k = 2
```

contains the distinct value pair:

```text
(1,3)
```

once.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Put all values into a set.

For each number `x`, ask:

```text
Does x + k exist?
```

If yes:

```text
(x, x+k)
```

is a valid pair.

### Why only `x + k`?

If we checked both:

```text
x + k
x - k
```

we could count the same pair twice.

Example:

```text
1, 3
k = 2
```

Checking:

```text
1 → 3
3 → 1
```

would count the pair twice.

So for `k > 0`, check only:

```text
x + k
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Put all numbers into a set.
2. Set `count = 0`.
3. For every unique number `x`:

   * Check whether `x + k` exists.
4. If yes, increment `count`.
5. Return `count`.

### Pseudocode

```text
numbers = set(nums)
count = 0

for x in numbers:
    if x + k exists:
        count += 1

return count
```

### Special case

If:

```text
k = 0
```

then:

```text
|a-b| = 0
```

means:

```text
a = b
```

The interpretation becomes different because we're counting repeated values rather than distinct unequal-value pairs.

For CR2, we will handle the standard **k > 0** version.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def count_pairs_with_difference(nums, k):

    if k <= 0:
        return 0

    numbers = set(nums)

    count = 0

    for num in numbers:

        if num + k in numbers:
            count += 1

    return count


# Example
nums = [1, 5, 3, 4, 2]
k = 2

print(count_pairs_with_difference(nums, k))
```

Output:

```text
3
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Set;

class Main {

    public static int countPairsWithDifference(int[] nums, int k) {

        if (k <= 0) {
            return 0;
        }

        Set<Integer> numbers = new HashSet<>();

        for (int num : nums) {
            numbers.add(num);
        }

        int count = 0;

        for (int num : numbers) {

            if (numbers.contains(num + k)) {
                count++;
            }
        }

        return count;
    }

    public static void main(String[] args) {

        int[] nums = {1, 5, 3, 4, 2};
        int k = 2;

        System.out.println(
            countPairsWithDifference(nums, k)
        );
    }
}
```

Output:

```text
3
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
nums = [1, 5, 3, 4, 2]
k = 2
```

Set:

```text
{1, 2, 3, 4, 5}
```

Start:

```text
count = 0
```

### `1`

Check:

```text
1 + 2 = 3
```

`3` exists.

```text
count = 1
```

Pair:

```text
(1,3)
```

---

### `2`

Check:

```text
2 + 2 = 4
```

Exists.

```text
count = 2
```

Pair:

```text
(2,4)
```

---

### `3`

Check:

```text
3 + 2 = 5
```

Exists.

```text
count = 3
```

Pair:

```text
(3,5)
```

---

### `4`

Check:

```text
4 + 2 = 6
```

Doesn't exist.

---

### `5`

Check:

```text
5 + 2 = 7
```

Doesn't exist.

Final:

```text
count = 3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same set logic:

```text
1 → 3 exists → count 1
2 → 4 exists → count 2
3 → 5 exists → count 3
4 → 6 absent
5 → 7 absent
```

Answer:

```text
3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Building the set:

```text
O(n)
```

Iterating through unique values:

```text
O(n)
```

Each membership lookup:

```text
O(1) expected
```

Therefore:

```text
Time = O(n)
```

Set space:

```text
O(n)
```

### Final

```text
Time:  O(n) expected
Space: O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a set?

Because we only need fast existence checks.

---

### Q2. Why check `x + k` instead of both directions?

To avoid counting the same unordered pair twice.

---

### Q3. What if `x + k` doesn't exist?

Then `x` cannot form a valid pair with a larger value.

---

### Q4. What if duplicates exist?

Because we're counting distinct value pairs in this CR2 formulation, the set removes duplicate values.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### Recognition

```text
Pair
+
Target difference
+
Fast existence lookup
```

↓

```text
SET
```

Master template:

```python
numbers = set(nums)

for x in numbers:
    if x + k in numbers:
        ...
```

This is the same general philosophy as Two Sum:

```text
Need partner
      ↓
Calculate partner
      ↓
Check HashSet
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Nested loops

```python
for i in range(n):
    for j in range(i + 1, n):
```

This gives:

```text
O(n²)
```

when hashing can give expected O(n).

---

### ❌ Mistake 2 — Checking both `x+k` and `x-k`

Can double-count pairs.

---

### ❌ Mistake 3 — Forgetting what "pair" means

Always inspect the problem statement:

```text
distinct value pairs?
index pairs?
duplicate occurrences?
```

Those are different problems.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Pairs With Given Difference
Exact LC → No exact canonical match
Pattern → HashSet lookup
Key idea → x + k
Time → O(n) expected
Space → O(n)
```

---

# 🔥 PROBLEM 80 — ARRAY INTERSECTION WITH MULTIPLICITY

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

🔥 **LC 350 — Intersection of Two Arrays II — Easy**

This is the exact core problem.

The important word is:

> **multiplicity**

That means duplicates matter.

Example:

```text
A = [1, 2, 2, 3]
B = [2, 2, 4]
```

Intersection:

```text
[2, 2]
```

Why two `2`s?

Because:

```text
A has 2 → 2 times
B has 2 → 2 times
```

So common count:

```text
min(2,2) = 2
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Return the intersection of two arrays, including duplicates.

Example:

```text
A = [4, 9, 5]
B = [9, 4, 9, 8, 4]
```

Output can be:

```text
[4, 9]
```

because:

```text
4 → min(1,2) = 1
9 → min(1,2) = 1
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Use a frequency map for the first array.

Example:

```text
A = [2, 2, 3, 4]
```

Frequency:

```text
2 → 2
3 → 1
4 → 1
```

Now scan B.

If B contains `2`:

```text
freq[2] > 0
```

then:

```text
add 2
freq[2] -= 1
```

Why decrease?

Because one copy has now been consumed.

Example:

```text
freq[2] = 2

B gives 2
→ output 2
→ freq[2] = 1

B gives another 2
→ output 2
→ freq[2] = 0

B gives another 2
→ no copies left
```

This is the heart of multiplicity.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Build frequency map from array A.
2. Create empty result.
3. Traverse B.
4. For each value:

   * If its frequency is greater than zero:

     * Add it to result.
     * Decrease frequency.
5. Return result.

### Pseudocode

```text
frequency = count(A)
result = []

for x in B:

    if frequency[x] > 0:

        add x to result
        frequency[x] -= 1

return result
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def intersection_with_multiplicity(a, b):

    freq = {}

    # Count elements in first array
    for num in a:
        freq[num] = freq.get(num, 0) + 1

    result = []

    # Consume frequencies using second array
    for num in b:

        if freq.get(num, 0) > 0:

            result.append(num)

            freq[num] -= 1

    return result


# Example
a = [1, 2, 2, 3]
b = [2, 2, 4]

print(intersection_with_multiplicity(a, b))
```

Output:

```text
[2, 2]
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

class Main {

    public static List<Integer> intersectionWithMultiplicity(
            int[] a,
            int[] b) {

        Map<Integer, Integer> freq = new HashMap<>();

        // Count first array
        for (int num : a) {
            freq.put(num, freq.getOrDefault(num, 0) + 1);
        }

        List<Integer> result = new ArrayList<>();

        // Consume frequencies
        for (int num : b) {

            if (freq.getOrDefault(num, 0) > 0) {

                result.add(num);

                freq.put(num, freq.get(num) - 1);
            }
        }

        return result;
    }

    public static void main(String[] args) {

        int[] a = {1, 2, 2, 3};
        int[] b = {2, 2, 4};

        List<Integer> result =
            intersectionWithMultiplicity(a, b);

        System.out.println(result);
    }
}
```

Output:

```text
[2, 2]
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
A = [1, 2, 2, 3]
B = [2, 2, 4]
```

## PASS 1 — Frequency of A

```text
1 → 1
2 → 2
3 → 1
```

So:

```text
freq = {
    1: 1,
    2: 2,
    3: 1
}
```

Result:

```text
[]
```

---

## PASS 2 — Scan B

### First `2`

```text
freq[2] = 2
```

Greater than zero.

Add:

```text
result = [2]
```

Decrease:

```text
freq[2] = 1
```

---

### Second `2`

```text
freq[2] = 1
```

Add:

```text
result = [2,2]
```

Decrease:

```text
freq[2] = 0
```

---

### `4`

Check:

```text
freq[4] = 0
```

Don't add.

Final:

```text
[2,2]
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Frequency:

```text
{1=1, 2=2, 3=1}
```

Process:

```text
2 → output → frequency 2 becomes 1
2 → output → frequency 2 becomes 0
4 → frequency absent → skip
```

Final:

```text
[2,2]
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = len(A)
m = len(B)
```

Build frequency map:

```text
O(n)
```

Scan B:

```text
O(m)
```

Hash operations expected O(1).

Therefore:

```text
Time = O(n + m)
```

Frequency map:

```text
O(n)
```

Result:

```text
O(min(n,m))
```

So auxiliary + output considerations:

```text
Space = O(n + min(n,m))
```

Common interview convention often reports:

```text
O(n)
```

auxiliary space, excluding the returned result.

### Final

```text
Time:  O(n + m) expected
Auxiliary Space: O(n)
Output Space: O(min(n,m))
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why decrease the frequency after using an element?

Because each occurrence can only be matched once.

---

### Q2. Why can't we use a set?

A set loses duplicate information.

Example:

```text
A = [2,2]
B = [2,2]
```

Set intersection gives:

```text
{2}
```

But the correct multiset intersection is:

```text
[2,2]
```

---

### Q3. Why is this different from Problem 75?

Problem 75:

```text
UNION
```

asks for unique values.

Problem 80:

```text
INTERSECTION WITH MULTIPLICITY
```

asks for common values while preserving duplicate counts.

---

### Q4. What determines the number of copies in the answer?

For each value:

```text
min(
    frequency in A,
    frequency in B
)
```

Example:

```text
A has 2 → 5 times
B has 2 → 3 times

Answer contains 2 → 3 times
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

### 🔥 Multiplicity Pattern

```text
Intersection
+
duplicates matter
```

↓

```text
FREQUENCY MAP
```

Then:

```text
USE → DECREMENT
```

### Master Template

```python
freq = {}

for x in a:
    freq[x] = freq.get(x, 0) + 1

result = []

for x in b:
    if freq.get(x, 0) > 0:
        result.append(x)
        freq[x] -= 1
```

This is one of the most reusable HashMap patterns in placement interviews.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Using a set

That removes duplicates.

---

### ❌ Mistake 2 — Not decrementing frequency

If you don't decrement:

```text
A = [2]
B = [2,2,2]
```

you could incorrectly output:

```text
[2,2,2]
```

Correct:

```text
[2]
```

---

### ❌ Mistake 3 — Confusing union and intersection

```text
UNION
→ values in A OR B

INTERSECTION
→ values in A AND B
```

---

### ❌ Mistake 4 — Forgetting multiplicity

For:

```text
A = [1,2,2]
B = [2,2,2]
```

answer:

```text
[2,2]
```

not:

```text
[2,2,2]
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Problem → Intersection With Multiplicity
LeetCode → LC 350
Difficulty → Easy
Pattern → Frequency Map
Key trick → Decrement after matching
Time → O(n + m) expected
Auxiliary Space → O(n)
```

---

# 🧠 DAY 8 — SESSION 3 MASTER PATTERN MAP

You have now completed the entire **Hashing & Frequency day**.

```text
71 → Frequency Map
     ↓
     COUNT

72 → First Repeating
     ↓
     SET
     ↓
     SEEN BEFORE?

73 → First Non-Repeating
     ↓
     HASH MAP
     ↓
     FREQUENCY == 1

74 → Equal Multisets
     ↓
     TWO FREQUENCY MAPS

75 → Union
     ↓
     SET
     ↓
     UNIQUE VALUES

76 → Common in 3 Sorted Arrays
     ↓
     THREE POINTERS

77 → Group Anagrams
     ↓
     CANONICAL KEY + HASH MAP

78 → Longest Consecutive
     ↓
     HASH SET
     ↓
     SEQUENCE START

79 → Pair Difference
     ↓
     HASH SET
     ↓
     x + k

80 → Intersection II
     ↓
     FREQUENCY MAP
     ↓
     CONSUME + DECREMENT
```

---

# 🔥 THE BIG HASHING DECISION TREE

This is what I want you to recognize in an interview:

```text
                 HASHING
                    │
       ┌────────────┼─────────────┐
       │            │             │
     COUNT         SEEN?        GROUP?
       │            │             │
    DICT           SET       CANONICAL KEY
       │            │             │
       ▼            ▼             ▼
 Frequency      Duplicate      Anagrams
    Map          Detection
       │
       ├───────────────┐
       │               │
   Frequency=1     Consume count
       │               │
       ▼               ▼
 First Unique     Intersection II
```

And separately:

```text
UNSORTED + CONSECUTIVE
        ↓
      SET
        ↓
  sequence starts
        ↓
     O(n)
```

And:

```text
SORTED ARRAYS
      +
COMMON ELEMENTS
      ↓
MULTI-POINTER
```

---

# 🎯 DAY 8 — FINAL MASTER TEST

## Problem 77 — Group Anagrams

Without looking at the solution:

```text
words = ["cat", "dog", "tac", "god", "act"]
```

Expected groups:

```text
["cat", "tac", "act"]
["dog", "god"]
```

Your key recognition:

```text
cat → act
tac → act
act → act

dog → dgo
god → dgo
```

---

## Problem 78 — Longest Consecutive

```text
nums = [9, 1, 4, 7, 3, 2, 6, 5]
```

Find the longest consecutive sequence.

Answer:

```text
1, 2, 3, 4, 5, 6, 7
```

Length:

```text
7
```

---

## Problem 79 — Given Difference

```text
nums = [1, 5, 3, 4, 2]
k = 2
```

Valid distinct value pairs:

```text
(1,3)
(2,4)
(3,5)
```

Answer:

```text
3
```

---

## Problem 80 — Intersection II

```text
A = [4, 9, 5, 4]
B = [9, 4, 9, 8, 4]
```

Frequency:

```text
A:
4 → 2
9 → 1
5 → 1

B:
4 → 2
9 → 2
8 → 1
```

Therefore:

```text
4 → min(2,2) = 2
9 → min(1,2) = 1
```

Answer:

```text
[4, 4, 9]
```

Any ordering is valid unless specified.

---

# 🧪 🔥 SENIOR TRICK TEST — IDENTIFY THE PATTERN

Do **not** code these first. Just identify the correct technique.

### 1.

> Count how many times each number appears.

```text
?
```

### 2.

> Determine whether two arrays contain the same values with the same duplicate counts, regardless of order.

```text
?
```

### 3.

> Return every distinct value appearing in either array.

```text
?
```

### 4.

> Find the longest run of consecutive integers in an unsorted array in O(n) expected time.

```text
?
```

### 5.

> Group `"eat"`, `"tea"`, and `"ate"` together.

```text
?
```

### 6.

> Find common elements of three already-sorted arrays.

```text
?
```

### 7.

> Find pairs whose difference equals `k`.

```text
?
```

### 8.

> Find the intersection of two arrays where duplicates must be preserved.

```text
?
```

### Expected recognition

```text
1 → Dictionary / Frequency Map
2 → Frequency Map
3 → Set
4 → HashSet + Sequence Start
5 → Canonical Key + HashMap
6 → Three Pointers
7 → HashSet
8 → Frequency Map + Decrement
```

---

# 📈 CR2 PROGRESS — DAY 8 COMPLETE

```text
DAY 1  ██████████ 10/10
DAY 2  ██████████ 20/20
DAY 3  ██████████ 30/30
DAY 4  ██████████ 40/40
DAY 5  ██████████ 50/50
DAY 6  ██████████ 60/60
DAY 7  ██████████ 70/70
DAY 8  ██████████ 80/80

TOTAL → 80/100
```

## 🏆 DAY 8 STATUS

```text
🟢 Understood       → HashMap / HashSet fundamentals
🟡 Reproduced       → Core templates
🟠 Independent      → Target after master test
🔴 Mastered         → Only after solving without reference
```

### 🔥 Day 8's most important templates

```python
# Frequency
freq[x] = freq.get(x, 0) + 1
```

```python
# Seen before
seen = set()

if x in seen:
    ...
```

```python
# First unique
# frequency pass
# original-order pass
```

```python
# Group equivalent items
key = canonical_form(x)
groups[key].append(x)
```

```python
# Longest consecutive
if x - 1 not in nums:
    # x is a sequence start
```

```python
# Multiplicity
if freq.get(x, 0) > 0:
    result.append(x)
    freq[x] -= 1
```

**Day 8 is now complete: 10/10 problems for the day, 80/100 overall.**

