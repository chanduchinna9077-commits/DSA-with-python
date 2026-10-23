# 🔴 3. HASHING — 10 Problems

This deserves its **own topic**, even though hashing appears inside Arrays/Strings.

### Patterns

1. Frequency map
2. Set lookup
3. Duplicate detection
4. Complement lookup
5. First unique
6. Pair counting
7. Common elements
8. Difference
9. Grouping
10. Lookup optimization

### Problems

| #  | Problem                      |
| -- | ---------------------------- |
| 1  | Character Frequency          |
| 2  | Element Frequency            |
| 3  | Contains Duplicate           |
| 4  | First Repeating Element      |
| 5  | First Non-Repeating Element  |
| 6  | Two Sum                      |
| 7  | Count Pairs With Given Sum   |
| 8  | Common Elements              |
| 9  | Group Anagrams               |
| 10 | Longest Consecutive Sequence |

For your basic assessment, #1–#8 are the immediate priority.

---

# 🔵 HASHING — CONVERSATION 1

## Problems 1–4 of 10

We now start the **HASHING** topic.

The goal is not to memorize dictionary syntax. The goal is to understand **when hashing removes unnecessary repeated searching and turns many O(n²) solutions into O(n)**.

---

# 🧠 HASHING — 10-PROBLEM ROADMAP

|  # | Problem                      | Main Pattern           |
| -: | ---------------------------- | ---------------------- |
|  1 | Character Frequency          | HashMap / Frequency    |
|  2 | Element Frequency            | HashMap / Frequency    |
|  3 | Contains Duplicate           | HashSet                |
|  4 | First Repeating Element      | HashSet / Traversal    |
|  5 | First Non-Repeating Element  | Frequency + Traversal  |
|  6 | Two Sum                      | Complement Hashing     |
|  7 | Count Pairs With Target Sum  | Frequency + Complement |
|  8 | Common Elements              | HashSet Intersection   |
|  9 | Group Anagrams               | Frequency / Signature  |
| 10 | Longest Consecutive Sequence | HashSet                |

### Conversation structure

```text
Conversation 1 → Problems 1–4
Conversation 2 → Problems 5–8
Conversation 3 → Problems 9–10 + Mastery
```

---

# 🔥 HASHING — CORE IDEA BEFORE PROBLEMS

## What is Hashing?

Hashing is a technique that lets us store information so we can **find it quickly**.

For example:

```text
Array:
[10, 20, 30, 40]
```

If I ask:

> Have we already seen `30`?

With a normal list, you may search through elements.

With a hash set:

```python
seen = {10, 20, 30, 40}
```

we can usually check:

```python
30 in seen
```

in:

```text
Average O(1)
```

---

# 🧒 ELI10

Imagine 100 students enter a classroom.

Instead of asking:

> "Have I already seen Rahul?"

by checking every student's face one by one, you maintain a register:

```text
Rahul
Priya
John
...
```

You can quickly check whether a name exists.

That is the basic intuition behind hashing.

---

# 🔑 HASHING MASTER PATTERNS

We will repeatedly use:

### Pattern 1 — Frequency Map

```python
frequency = {}

for x in data:
    if x in frequency:
        frequency[x] += 1
    else:
        frequency[x] = 1
```

### Pattern 2 — Seen Set

```python
seen = set()

for x in data:
    if x in seen:
        # duplicate
    else:
        seen.add(x)
```

### Pattern 3 — Complement

```python
needed = target - x
```

Then:

```python
if needed in seen:
```

These three ideas solve a huge percentage of basic hashing questions.

---

# 🔹 PROBLEM 1 — Character Frequency

## 1. Problem Statement

Given a string, count the frequency of every character.

### Example

```text
Input:
"programming"

Output:
p → 1
r → 2
o → 1
g → 2
a → 1
m → 2
i → 1
n → 1
```

---

# 2. Problem Theory

We need to answer:

> How many times does each character occur?

We need a structure:

```text
character → count
```

A Python dictionary is perfect for this.

```python
frequency = {}
```

For:

```text
"banana"
```

we want:

```text
b → 1
a → 3
n → 2
```

---

# 3. Pattern Being Tested

## 🔥 Frequency Map

This is the most fundamental hashing pattern.

```text
Input
 ↓
Traverse
 ↓
Store count
 ↓
Dictionary
```

---

# 4. ELI10 Intuition 🧒

Imagine each character has its own counting box.

For:

```text
banana
```

You create:

```text
b box
a box
n box
```

Every time you see a character, put one more coin into its box.

At the end:

```text
b → 🪙
a → 🪙🪙🪙
n → 🪙🪙
```

---

# 5. Example

```text
Input:
"apple"
```

Process:

```text
a → 1
p → 1
p → 2
l → 1
e → 1
```

Final:

```text
a → 1
p → 2
l → 1
e → 1
```

---

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Create an empty dictionary.
3. Traverse every character.
4. Check whether the character already exists.
5. If it exists, increment its count.
6. Otherwise create it with count `1`.
7. Print the frequency map.

---

# 7. Python Solution — Using Built-in Method

Python has `Counter`.

```python
from collections import Counter

s = input("Enter a string: ")

frequency = Counter(s)

for ch, count in frequency.items():
    print(ch, "->", count)
```

### Example

```text
Enter a string: banana

b -> 1
a -> 3
n -> 2
```

---

# 8. Python Solution — Without Built-in Frequency Counter

This is the important DSA implementation.

```python
s = input("Enter a string: ")

frequency = {}

for ch in s:

    if ch in frequency:
        frequency[ch] += 1
    else:
        frequency[ch] = 1

for ch in frequency:
    print(ch, "->", frequency[ch])
```

---

# 9. Line-by-Line Explanation

```python
frequency = {}
```

Creates an empty dictionary.

Initially:

```text
{}
```

---

```python
for ch in s:
```

Visits every character.

---

```python
if ch in frequency:
```

Checks:

> Have I seen this character before?

---

```python
frequency[ch] += 1
```

If yes, increase its count.

---

```python
else:
    frequency[ch] = 1
```

If this is the first occurrence, initialize it.

---

# 10. Detailed Dry Run

Input:

```text
"banana"
```

| Step | Character | Frequency Map        |
| ---: | --------- | -------------------- |
|    1 | b         | `{b: 1}`             |
|    2 | a         | `{b: 1, a: 1}`       |
|    3 | n         | `{b: 1, a: 1, n: 1}` |
|    4 | a         | `{b: 1, a: 2, n: 1}` |
|    5 | n         | `{b: 1, a: 2, n: 2}` |
|    6 | a         | `{b: 1, a: 3, n: 2}` |

Final:

```text
b → 1
a → 3
n → 2
```

---

# 11. Time Complexity

There are `n` characters.

Each dictionary operation is **average O(1)**.

Therefore:

```text
Time = O(n)
```

### Space

In the worst case, every character is different:

```text
Space = O(n)
```

---

# 12. Edge Cases

### Empty string

```text
""
```

Result:

```text
{}
```

### One character

```text
"a"
```

Result:

```text
a → 1
```

### All same

```text
"aaaa"
```

Result:

```text
a → 4
```

### All different

```text
"abcd"
```

Result:

```text
a → 1
b → 1
c → 1
d → 1
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Forgetting initialization

This can fail:

```python
frequency[ch] += 1
```

if `ch` doesn't exist yet.

---

### ❌ Mistake 2 — Using repeated `.count()`

Example:

```python
for ch in s:
    print(ch, s.count(ch))
```

This repeatedly scans the string.

Potential complexity:

```text
O(n²)
```

Hashing gives us approximately:

```text
O(n)
```

---

# 14. Pattern Recognition

When you see:

> "Count how many times each element occurs"

Immediately think:

# FREQUENCY MAP

Master template:

```python
frequency = {}

for x in data:
    if x in frequency:
        frequency[x] += 1
    else:
        frequency[x] = 1
```

---

# 🔹 PROBLEM 2 — Element Frequency

## 1. Problem Statement

Given an integer array, count the frequency of every element.

### Example

```text
Input:
[1, 2, 2, 3, 1, 1]

Output:
1 → 3
2 → 2
3 → 1
```

---

# 2. Problem Theory

This is the **same hashing pattern as character frequency**, but now our keys are integers.

We need:

```text
number → frequency
```

For:

```text
[4, 5, 4, 6, 5, 4]
```

we build:

```text
4 → 3
5 → 2
6 → 1
```

### Important insight

Hashing is not only for strings.

It works for:

```text
characters
integers
strings
objects/keys
```

as long as they can be used as hashable keys.

---

# 3. Pattern Being Tested

## Frequency Map on Arrays

```text
Array
 ↓
Traverse
 ↓
Count each value
 ↓
Dictionary
```

This becomes the foundation for:

* duplicates
* most frequent element
* first repeating
* pair counting
* common elements

---

# 4. ELI10 Intuition 🧒

Suppose you have:

```text
[2, 5, 2, 3, 5, 2]
```

Create boxes:

```text
2 box
3 box
5 box
```

Every time a number appears, increase its box count.

Final:

```text
2 → 3
3 → 1
5 → 2
```

---

# 5. Example

Input:

```text
[10, 20, 10, 30, 20, 10]
```

Frequency:

```text
10 → 3
20 → 2
30 → 1
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty dictionary.
2. Traverse the array.
3. For every number:

   * if it exists, increment its count.
   * otherwise initialize it to `1`.
4. Print the frequency map.

---

# 7. Python Solution — Using Built-in Method

```python
from collections import Counter

arr = list(map(int, input("Enter elements: ").split()))

frequency = Counter(arr)

for num, count in frequency.items():
    print(num, "->", count)
```

### Input

```text
1 2 2 3 1 1
```

### Output

```text
1 -> 3
2 -> 2
3 -> 1
```

---

# 8. Python Solution — Without Built-in Counter

```python
arr = list(map(int, input("Enter elements: ").split()))

frequency = {}

for num in arr:

    if num in frequency:
        frequency[num] += 1
    else:
        frequency[num] = 1

for num in frequency:
    print(num, "->", frequency[num])
```

---

# 9. Line-by-Line Explanation

```python
arr = list(map(int, input().split()))
```

Suppose input is:

```text
1 2 2 3
```

It becomes:

```python
[1, 2, 2, 3]
```

---

```python
frequency = {}
```

Creates our hash map.

---

```python
for num in arr:
```

Process every number.

---

```python
if num in frequency:
```

Check whether we've already encountered the number.

---

```python
frequency[num] += 1
```

Increase its count.

---

```python
else:
    frequency[num] = 1
```

First occurrence.

---

# 10. Detailed Dry Run

Input:

```text
[5, 2, 5, 3, 2, 5]
```

| Step | Number | Frequency Map        |
| ---: | -----: | -------------------- |
|    1 |      5 | `{5: 1}`             |
|    2 |      2 | `{5: 1, 2: 1}`       |
|    3 |      5 | `{5: 2, 2: 1}`       |
|    4 |      3 | `{5: 2, 2: 1, 3: 1}` |
|    5 |      2 | `{5: 2, 2: 2, 3: 1}` |
|    6 |      5 | `{5: 3, 2: 2, 3: 1}` |

Final:

```text
5 → 3
2 → 2
3 → 1
```

---

# 11. Time Complexity

One traversal:

```text
O(n)
```

### Space

At most `n` different values:

```text
O(n)
```

---

# 12. Edge Cases

### Empty array

```text
[]
```

Frequency:

```text
{}
```

### All same

```text
[7, 7, 7, 7]
```

```text
7 → 4
```

### All unique

```text
[1, 2, 3, 4]
```

Each frequency is `1`.

### Negative numbers

```text
[-1, -2, -1, 3]
```

Works normally:

```text
-1 → 2
-2 → 1
3 → 1
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Confusing frequency with index

```text
number → frequency
```

not:

```text
number → position
```

---

### ❌ Mistake 2 — Assuming hashing only works with strings

It works with many hashable data types.

---

# 14. Pattern Recognition

When you see:

> "Frequency of every element in an array"

Think:

```text
ARRAY
 ↓
HASH MAP
 ↓
VALUE → COUNT
```

The exact same template from Problem 1 works.

---

# 🔹 PROBLEM 3 — Contains Duplicate

## 1. Problem Statement

Given an array, determine whether any value appears more than once.

### Example 1

```text
Input:
[1, 2, 3, 1]

Output:
True
```

Because `1` appears twice.

### Example 2

```text
Input:
[1, 2, 3, 4]

Output:
False
```

No duplicates.

---

# 2. Problem Theory

We don't actually need to know the exact frequency.

We only need to know:

> Have I seen this value before?

That means a **set** is ideal.

```python
seen = set()
```

A set stores unique values.

---

# 3. Pattern Being Tested

# 🔥 HashSet / Seen Pattern

Template:

```python
seen = set()

for x in data:

    if x in seen:
        # duplicate found

    seen.add(x)
```

This is one of the most important basic hashing templates.

---

# 4. ELI10 Intuition 🧒

Imagine students entering a room.

You maintain a guest list:

```text
Rahul
Priya
John
```

A new student arrives.

If the name is already on the list:

> Duplicate!

Otherwise add the student.

Same idea:

```text
number already seen?
    ↓
YES → duplicate
NO  → add it
```

---

# 5. Example

Input:

```text
[4, 2, 7, 2]
```

Process:

```text
4 → not seen → add
2 → not seen → add
7 → not seen → add
2 → already seen → DUPLICATE
```

Answer:

```text
True
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty set `seen`.
2. Traverse the array.
3. For each element:

   * check whether it is already in `seen`.
4. If yes:

   * return `True`.
5. Otherwise add it to `seen`.
6. If traversal finishes without finding a duplicate:

   * return `False`.

---

# 7. Python Solution — Using Built-in Method

The shortest Python approach:

```python
arr = list(map(int, input("Enter elements: ").split()))

if len(arr) != len(set(arr)):
    print("Contains Duplicate")
else:
    print("No Duplicate")
```

### Why does this work?

A set removes duplicates.

Example:

```text
arr:
[1, 2, 2, 3]

set(arr):
{1, 2, 3}
```

Lengths:

```text
4 != 3
```

Therefore a duplicate exists.

---

# 8. Python Solution — Without Built-in Duplicate Logic

```python
arr = list(map(int, input("Enter elements: ").split()))

seen = set()

has_duplicate = False

for num in arr:

    if num in seen:
        has_duplicate = True
        break

    seen.add(num)

if has_duplicate:
    print("Contains Duplicate")
else:
    print("No Duplicate")
```

This is the important DSA implementation.

---

# 9. Line-by-Line Explanation

```python
seen = set()
```

Creates an empty set.

---

```python
has_duplicate = False
```

Initially assume there is no duplicate.

---

```python
for num in arr:
```

Process elements one by one.

---

```python
if num in seen:
```

Ask:

> Have I already seen this number?

---

```python
has_duplicate = True
```

If yes, duplicate exists.

---

```python
break
```

We can stop immediately.

There is no need to process the remaining elements.

---

```python
seen.add(num)
```

If this is the first occurrence, remember it.

---

# 10. Detailed Dry Run

Input:

```text
[4, 7, 2, 9, 7]
```

| Step | Number | `seen` Before | Duplicate? | `seen` After |
| ---: | -----: | ------------- | ---------- | ------------ |
|    1 |      4 | `{}`          | No         | `{4}`        |
|    2 |      7 | `{4}`         | No         | `{4,7}`      |
|    3 |      2 | `{4,7}`       | No         | `{4,7,2}`    |
|    4 |      9 | `{4,7,2}`     | No         | `{4,7,2,9}`  |
|    5 |      7 | `{4,7,2,9}`   | **Yes**    | Stop         |

Final:

```text
Contains Duplicate
```

---

# 11. Why Hashing Is Better Than Nested Loops

A beginner solution could compare every pair:

```python
for i in range(n):
    for j in range(i + 1, n):
        if arr[i] == arr[j]:
            ...
```

Complexity:

```text
O(n²)
```

HashSet approach:

```text
O(n) average
```

We trade extra memory for speed.

This is one of the most important ideas behind hashing.

---

# 12. Time Complexity

For the set approach:

```text
Time = O(n) average
```

### Space

The set can contain up to `n` unique values:

```text
Space = O(n)
```

---

# 13. Edge Cases

### Empty array

```text
[]
```

No duplicate.

### One element

```text
[5]
```

No duplicate.

### All same

```text
[5, 5, 5]
```

Duplicate immediately at the second element.

### Negative values

```text
[-1, -2, -1]
```

Duplicate exists.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Adding before checking

Wrong:

```python
seen.add(num)

if num in seen:
    # duplicate
```

Every element would appear to be a duplicate because you just added it.

Correct order:

```python
if num in seen:
    # duplicate

seen.add(num)
```

---

### ❌ Mistake 2 — Continuing after finding duplicate

Once found:

```python
break
```

This is early termination.

---

# 15. Pattern Recognition

When the question asks:

> "Has this appeared before?"

Think:

# HASH SET

Template:

```python
seen = set()

for x in data:

    if x in seen:
        return True

    seen.add(x)

return False
```

---

# 🔹 PROBLEM 4 — First Repeating Element

## 1. Problem Statement

Given an array, find the **first element that repeats** while scanning from left to right.

### Example

```text
Input:
[10, 20, 30, 20, 40]

Output:
20
```

Why?

Scanning:

```text
10 → first time
20 → first time
30 → first time
20 → already seen
```

Therefore:

```text
20
```

---

# 2. Problem Theory

This is different from:

> Find the most frequent element.

We are asking:

> Which element is the first one that we encounter for the second time?

The moment we encounter an element already in `seen`, we have our answer.

This means we **do not need a frequency map**.

A set is enough.

---

# 3. Pattern Being Tested

## HashSet + Original Traversal

```text
Array
 ↓
Seen Set
 ↓
Already seen?
 ↓
YES → answer
```

This is an important distinction:

### Frequency problem

```text
Need exact count?
→ Dictionary
```

### Duplicate existence / first repeat

```text
Only need "seen before?"
→ Set
```

---

# 4. ELI10 Intuition 🧒

Imagine collecting unique stickers.

```text
A
B
C
B
```

You already have sticker `B`.

So when `B` appears again:

> That's the first repeated sticker!

Immediately stop.

---

# 5. Example

Input:

```text
[5, 3, 8, 2, 3, 5]
```

Scan:

```text
5 → new
3 → new
8 → new
2 → new
3 → repeated
```

Answer:

```text
3
```

Notice that `5` also repeats later, but `3` is encountered as a repeat first.

---

# 6. Algorithm — Step-by-Step

1. Create an empty set `seen`.
2. Traverse the array from left to right.
3. For every element:

   * if it already exists in `seen`, return it.
   * otherwise add it to `seen`.
4. If the loop finishes:

   * no repeating element exists.

---

# 7. Python Solution — Using Built-in Method

A concise approach can use a set to identify duplicates, but we must preserve the original traversal order.

```python
arr = list(map(int, input("Enter elements: ").split()))

seen = set()
answer = None

for num in arr:

    if num in seen:
        answer = num
        break

    seen.add(num)

if answer is not None:
    print("First repeating element =", answer)
else:
    print("No repeating element")
```

This is already the cleanest screening solution.

---

# 8. Python Solution — Without High-Level Duplicate Logic

The DSA logic itself is:

```python
arr = list(map(int, input("Enter elements: ").split()))

seen = set()

answer = None

for i in range(len(arr)):

    num = arr[i]

    if num in seen:
        answer = num
        break

    seen.add(num)

if answer is not None:
    print("First repeating element =", answer)
else:
    print("No repeating element")
```

Here we deliberately use index-based traversal to expose the underlying process.

---

# 9. Line-by-Line Explanation

```python
seen = set()
```

Stores elements encountered so far.

---

```python
for i in range(len(arr)):
```

Moves through the array from left to right.

---

```python
num = arr[i]
```

Gets the current element.

---

```python
if num in seen:
```

Checks whether we have already encountered this number.

---

```python
answer = num
```

This is the first element we encounter for the second time.

---

```python
break
```

Stop immediately.

---

```python
seen.add(num)
```

If this is its first appearance, remember it.

---

# 10. Detailed Dry Run

Input:

```text
[10, 20, 30, 20, 40]
```

| Step | Element | `seen` Before | Already Seen? | Action      |
| ---: | ------: | ------------- | ------------- | ----------- |
|    1 |      10 | `{}`          | No            | Add 10      |
|    2 |      20 | `{10}`        | No            | Add 20      |
|    3 |      30 | `{10,20}`     | No            | Add 30      |
|    4 |      20 | `{10,20,30}`  | **Yes**       | Answer = 20 |

Stop.

Final:

```text
First repeating element = 20
```

---

# 11. Important Example — Why Order Matters

Consider:

```text
[5, 1, 2, 1, 5]
```

Frequencies:

```text
5 → 2
1 → 2
2 → 1
```

If someone simply says:

> `5` is repeated

that doesn't answer the actual question.

Scan the array:

```text
5 → first occurrence
1 → first occurrence
2 → first occurrence
1 → second occurrence ← FIRST REPEAT
```

Answer:

```text
1
```

So:

> **First repeating element depends on encounter order, not just frequency.**

---

# 12. Time Complexity

Each element is inserted into the set at most once.

Each membership check is average O(1).

Therefore:

```text
Time = O(n) average
```

### Space

The set can contain up to `n` elements:

```text
Space = O(n)
```

---

# 13. Edge Cases

### No repeating element

```text
[1, 2, 3, 4]
```

Output:

```text
No repeating element
```

### First two are same

```text
[5, 5, 8]
```

Answer immediately:

```text
5
```

### All same

```text
[7, 7, 7]
```

Answer:

```text
7
```

### Negative numbers

```text
[-1, -2, -3, -2]
```

Answer:

```text
-2
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Finding the most frequent element

Different problem.

For:

```text
[5, 1, 1, 5]
```

the first repeating element is:

```text
1
```

because:

```text
5 → first occurrence
1 → first occurrence
1 → repeat
```

---

### ❌ Mistake 2 — Using a frequency map unnecessarily

You can solve it with:

```python
seen = set()
```

because we only care:

```text
"Have I seen this before?"
```

---

### ❌ Mistake 3 — Checking all pairs

Nested loops work, but:

```text
O(n²)
```

HashSet gives:

```text
O(n) average
```

---

# 15. Pattern Recognition

When you see:

> "Find the first element that appears again"

Think:

```text
LEFT → RIGHT
     ↓
SEEN SET
     ↓
Already seen?
     ↓
YES → ANSWER
```

### Master template

```python
seen = set()

for x in data:

    if x in seen:
        return x

    seen.add(x)

return None
```

---

# 🧠 HASHING — CONVERSATION 1 MASTER SUMMARY

You have now completed:

```text
HASHING
████░░░░░░ 4 / 10
```

### The four problems are really teaching only **two major patterns**.

---

## 🔥 PATTERN 1 — FREQUENCY MAP

Used in:

### Problem 1

```text
Character Frequency
```

### Problem 2

```text
Element Frequency
```

Template:

```python
frequency = {}

for x in data:

    if x in frequency:
        frequency[x] += 1
    else:
        frequency[x] = 1
```

Think:

> **"How many times?" → Dictionary**

---

# 🔥 PATTERN 2 — SEEN SET

Used in:

### Problem 3

```text
Contains Duplicate
```

### Problem 4

```text
First Repeating Element
```

Template:

```python
seen = set()

for x in data:

    if x in seen:
        # repeated
        ...

    seen.add(x)
```

Think:

> **"Have I seen this before?" → Set**

---

# 🎯 CRITICAL DIFFERENCE

This is what I want you to permanently remember:

| Question                               | Data Structure         |
| -------------------------------------- | ---------------------- |
| How many times does it occur?          | `dict` / frequency map |
| Has it appeared before?                | `set`                  |
| Is there a duplicate?                  | `set`                  |
| What is the first repeated element?    | `set` + traversal      |
| What is the frequency of each element? | `dict`                 |

---

# 🧠 SENIOR PATTERN RECOGNITION

When reading a TopGun question, don't immediately write code.

First translate the wording:

```text
"frequency"
      ↓
HASH MAP


"duplicate"
      ↓
HASH SET


"already seen"
      ↓
HASH SET


"first repeating"
      ↓
HASH SET + LEFT→RIGHT


"most frequent"
      ↓
HASH MAP + MAX


"pair with target"
      ↓
COMPLEMENT HASHING
```

That translation step is the real DSA skill.

---

# 🏆 HASHING — PROBLEMS COMPLETED

```text
1. Character Frequency             ✅
2. Element Frequency               ✅
3. Contains Duplicate              ✅
4. First Repeating Element         ✅
```

### Next — HASHING CONVERSATION 2

```text
5. First Non-Repeating Element
6. Two Sum
7. Count Pairs With Target Sum
8. Common Elements
```

These four are particularly important because we move from basic hashing into **hashing + traversal + complement logic**, especially **Two Sum**, which is one of the most fundamental hashing interview patterns.

Would you like to continue with Hashing Conversation 2, or do a short mastery test on Problems 1–4 first?



# 🔵 HASHING — CONVERSATION 2

## Problems 5–8 of 10

We continue with the **locked version** without reducing the depth.

Today's progression moves from basic `set`/frequency logic into the most important hashing interview idea:

> **Use previously seen information to answer the current element quickly.**

### Roadmap

|  # | Problem                     | Main Pattern              |
| -: | --------------------------- | ------------------------- |
|  5 | First Non-Repeating Element | Frequency Map + Traversal |
|  6 | Two Sum                     | Complement Hashing        |
|  7 | Count Pairs With Target Sum | Frequency + Complement    |
|  8 | Common Elements             | HashSet / Intersection    |

---

# 🔹 PROBLEM 5 — First Non-Repeating Element

## 1. Problem Statement

Given an array, find the **first element that occurs exactly once**.

### Example

```text
Input:
[4, 5, 1, 2, 1, 4, 5]

Output:
2
```

Frequencies:

```text
4 → 2
5 → 2
1 → 2
2 → 1
```

Scanning from left to right:

```text
4 → repeated
5 → repeated
1 → repeated
2 → unique ✅
```

Therefore:

```text
First non-repeating element = 2
```

---

# 2. Problem Theory

This is the array version of the **first non-repeating character** problem.

The key idea is:

```text
First
+
Non-repeating
```

We need two pieces of information:

1. How many times does each element occur?
2. What is the original order?

Therefore:

```text
Phase 1 → Build frequency map
Phase 2 → Scan original array
```

---

# 3. Pattern Being Tested

## 🔥 Frequency Map + Original Traversal

This is a very important hashing pattern.

```text
Array
 ↓
Count frequencies
 ↓
Scan original order
 ↓
frequency == 1
 ↓
Answer
```

---

# 4. ELI10 Intuition 🧒

Imagine students standing in a line:

```text
4  5  1  2  1  4  5
```

First, make a register:

```text
4 → 2
5 → 2
1 → 2
2 → 1
```

Now walk through the original line again.

```text
4 → appears twice ❌
5 → appears twice ❌
1 → appears twice ❌
2 → appears once ✅
```

Stop.

---

# 5. Example

```text
Input:
[7, 3, 7, 8, 3, 9]
```

Frequency:

```text
7 → 2
3 → 2
8 → 1
9 → 1
```

Traversal:

```text
7 → repeated
3 → repeated
7 → repeated
8 → unique
```

Answer:

```text
8
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty frequency dictionary.
2. Traverse the array.
3. Count every element.
4. Traverse the array again from left to right.
5. Check `frequency[element] == 1`.
6. The first such element is the answer.
7. If no element has frequency `1`, report that none exists.

---

# 7. Python Solution — Using Built-in Method

```python
from collections import Counter

arr = list(map(int, input("Enter elements: ").split()))

frequency = Counter(arr)

answer = None

for num in arr:
    if frequency[num] == 1:
        answer = num
        break

if answer is not None:
    print("First non-repeating element =", answer)
else:
    print("No non-repeating element")
```

---

# 8. Python Solution — Without Built-in Counter

```python
arr = list(map(int, input("Enter elements: ").split()))

frequency = {}

for num in arr:

    if num in frequency:
        frequency[num] += 1
    else:
        frequency[num] = 1

answer = None

for num in arr:

    if frequency[num] == 1:
        answer = num
        break

if answer is not None:
    print("First non-repeating element =", answer)
else:
    print("No non-repeating element")
```

---

# 9. Line-by-Line Explanation

```python
frequency = {}
```

Stores:

```text
element → number of occurrences
```

---

```python
for num in arr:
```

First traversal.

---

```python
if num in frequency:
    frequency[num] += 1
```

Already seen → increase frequency.

---

```python
else:
    frequency[num] = 1
```

First occurrence.

---

Then:

```python
for num in arr:
```

Second traversal preserves the original order.

---

```python
if frequency[num] == 1:
```

We found an element occurring exactly once.

---

```python
break
```

Stop immediately because we want the **first** one.

---

# 10. Detailed Dry Run

Input:

```text
[4, 5, 1, 2, 1, 4, 5]
```

### Phase 1

| Element | Frequency |
| ------: | --------: |
|       4 |         2 |
|       5 |         2 |
|       1 |         2 |
|       2 |         1 |

### Phase 2

| Position | Element | Frequency | Decision |
| -------: | ------: | --------: | -------- |
|        0 |       4 |         2 | ❌        |
|        1 |       5 |         2 | ❌        |
|        2 |       1 |         2 | ❌        |
|        3 |       2 |         1 | ✅        |

Answer:

```text
2
```

---

# 11. Time Complexity

First traversal:

```text
O(n)
```

Second traversal:

```text
O(n)
```

Overall:

```text
O(n)
```

Space:

```text
O(n)
```

---

# 12. Edge Cases

### All elements unique

```text
[1, 2, 3]
```

Answer:

```text
1
```

### All elements repeated

```text
[1, 2, 1, 2]
```

No non-repeating element.

### One element

```text
[10]
```

Answer:

```text
10
```

### Negative numbers

```text
[-2, -1, -2, 5]
```

Answer:

```text
-1
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Returning the last unique element

We need the **first** unique element.

Always scan from left to right.

### ❌ Mistake 2 — Using a set alone

A set tells us whether something exists.

It does **not** tell us frequency.

Here we need:

```text
frequency == 1
```

So use a dictionary.

---

# 14. Pattern Recognition

When you see:

> "First element that occurs only once"

Think:

```text
FREQUENCY MAP
      ↓
ORIGINAL ARRAY
      ↓
frequency == 1
```

---

# 🔹 PROBLEM 6 — Two Sum

## 1. Problem Statement

Given an array and a target value, find two elements whose sum equals the target.

### Example

```text
Input:
arr = [2, 7, 11, 15]
target = 9

Output:
[2, 7]
```

Because:

```text
2 + 7 = 9
```

---

# 2. Problem Theory

The brute-force idea is:

```text
Try every pair.
```

That gives:

```text
O(n²)
```

Hashing lets us improve this.

For every number:

```text
x
```

we ask:

> What number do I need?

Answer:

```text
target - x
```

This is called the **complement**.

---

# 3. Pattern Being Tested

# 🔥 COMPLEMENT HASHING

This is one of the most important hashing patterns.

```text
current number = x

needed = target - x

Have I already seen needed?
        ↓
       YES → answer
       NO  → store x
```

---

# 4. ELI10 Intuition 🧒

Suppose target is:

```text
10
```

You see:

```text
6
```

You immediately ask:

> "What number do I need to make 10?"

```text
10 - 6 = 4
```

So you look in your notebook:

```text
Have I seen 4?
```

If yes:

```text
4 + 6 = 10
```

Done.

---

# 5. Example

```text
arr = [3, 8, 4, 7]
target = 11
```

Process:

```text
3 → need 8 → not seen → store 3

8 → need 3 → found!
```

Answer:

```text
[3, 8]
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty set or dictionary of seen values.
2. Traverse the array.
3. For each value `x`:

   * calculate `needed = target - x`.
4. Check whether `needed` has already been seen.
5. If yes, return the pair.
6. Otherwise store `x`.
7. If the loop ends, no valid pair exists.

---

# 7. Python Solution — Using Built-in Method

A simple Python approach using combinations:

```python
from itertools import combinations

arr = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

answer = None

for a, b in combinations(arr, 2):

    if a + b == target:
        answer = [a, b]
        break

if answer:
    print("Pair =", answer)
else:
    print("No pair found")
```

This is easy to understand, but:

```text
Time = O(n²)
```

It is **not** the optimal DSA solution.

---

# 8. Python Solution — Without High-Level Pair Generation

```python
arr = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

seen = set()

answer = None

for num in arr:

    needed = target - num

    if needed in seen:
        answer = [needed, num]
        break

    seen.add(num)

if answer:
    print("Pair =", answer)
else:
    print("No pair found")
```

This is the important hashing solution.

---

# 9. Line-by-Line Explanation

```python
seen = set()
```

Stores numbers encountered so far.

---

```python
for num in arr:
```

Process each number.

---

```python
needed = target - num
```

Calculate its complement.

Example:

```text
target = 9
num = 7

needed = 9 - 7
       = 2
```

---

```python
if needed in seen:
```

Ask:

> Did I already encounter the number that completes the target?

---

```python
answer = [needed, num]
```

We found the pair.

---

```python
seen.add(num)
```

If no pair is found yet, remember the current number.

---

# 10. Detailed Dry Run

Input:

```text
arr = [2, 7, 11, 15]
target = 9
```

| Step | `num` | Needed | `seen` Before | Found?  | Action         |
| ---: | ----: | -----: | ------------- | ------- | -------------- |
|    1 |     2 |      7 | `{}`          | No      | Add 2          |
|    2 |     7 |      2 | `{2}`         | **Yes** | Answer `[2,7]` |

Final:

```text
[2, 7]
```

---

# 11. Why Do We Check Before Adding?

This is extremely important.

For:

```text
arr = [3]
target = 6
```

When processing `3`:

```text
needed = 6 - 3
       = 3
```

If we add `3` first and then check:

```text
seen = {3}

3 in seen → True
```

we might incorrectly use the same element twice.

Correct order:

```text
1. Calculate complement
2. Check seen
3. Add current number
```

This ensures we use **two different positions**.

---

# 12. Duplicate Example

```text
arr = [3, 3]
target = 6
```

First `3`:

```text
needed = 3
seen = {}
```

Not found.

Add:

```text
seen = {3}
```

Second `3`:

```text
needed = 3
```

Found.

Therefore:

```text
3 + 3 = 6
```

Correct.

---

# 13. Time Complexity

Each number is processed once.

Hash set lookup is average O(1).

Therefore:

```text
Time = O(n)
```

Space:

```text
Space = O(n)
```

---

# 14. Edge Cases

### No pair

```text
[1, 2, 3]
target = 10
```

No pair.

### Negative numbers

```text
[-3, 4, 7]
target = 1
```

Pair:

```text
-3 + 4 = 1
```

### Duplicate values

```text
[3, 3]
target = 6
```

Valid.

### Zero

```text
[0, 4, 5]
target = 4
```

Pair:

```text
0 + 4
```

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Using nested loops unnecessarily

That gives:

```text
O(n²)
```

Hashing gives:

```text
O(n)
```

---

### ❌ Mistake 2 — Forgetting the complement

Don't ask:

> "What is the current number?"

Ask:

> **"What number do I need?"**

```text
needed = target - current
```

---

### ❌ Mistake 3 — Checking after inserting

As discussed, that can accidentally use the same element twice.

---

# 16. Pattern Recognition

When you see:

> "Find two numbers whose sum is target"

Immediately think:

# COMPLEMENT HASHING

Template:

```python
seen = set()

for x in arr:

    needed = target - x

    if needed in seen:
        return [needed, x]

    seen.add(x)
```

Memorize this pattern.

---

# 🔹 PROBLEM 7 — Count Pairs With Target Sum

## 1. Problem Statement

Given an array and a target, count how many **pairs of elements** have a sum equal to the target.

### Example

```text
Input:
arr = [1, 5, 7, -1, 5]
target = 6
```

Valid pairs by index:

```text
1 + 5 = 6
1 + 5 = 6
7 + (-1) = 6
```

Therefore:

```text
Output = 3
```

---

# 2. Problem Theory

This looks similar to Two Sum, but there is a major difference.

### Two Sum

Usually asks:

> Find one pair.

### Count Pairs

Asks:

> How many valid pairs exist?

Therefore we cannot stop at the first match.

We need to keep counting.

---

# 3. Pattern Being Tested

# 🔥 FREQUENCY + COMPLEMENT

For each current number:

```text
needed = target - current
```

Then:

> How many times have I already seen `needed`?

Instead of a set, we use a **frequency dictionary**.

---

# 4. ELI10 Intuition 🧒

Target:

```text
6
```

You see:

```text
1
```

You need:

```text
5
```

Suppose you've already seen `5` twice.

Then the current `1` creates:

```text
1 + 5
1 + 5
```

That's **two pairs**.

So instead of asking:

```text
Have I seen 5?
```

we ask:

```text
How many 5s have I seen?
```

---

# 5. Example

```text
arr = [1, 5, 5]
target = 6
```

Process:

```text
1 → need 5 → seen 5 = 0 → add 1

5 → need 1 → seen 1 = 1
     pairs += 1

5 → need 1 → seen 1 = 1
     pairs += 1
```

Answer:

```text
2
```

The two pairs are:

```text
(1, first 5)
(1, second 5)
```

---

# 6. Algorithm — Step-by-Step

1. Create a frequency dictionary for previously seen elements.
2. Set `pair_count = 0`.
3. Traverse the array.
4. For each number:

   * calculate `needed = target - num`.
5. Add `frequency[needed]` to `pair_count`.
6. Increase the frequency of the current number.
7. Continue until the array ends.
8. Return the total pair count.

---

# 7. Python Solution — Using Built-in / Brute Force

For learning, the straightforward approach is:

```python
arr = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

count = 0

for i in range(len(arr)):

    for j in range(i + 1, len(arr)):

        if arr[i] + arr[j] == target:
            count += 1

print("Number of pairs =", count)
```

This is easy to understand.

But:

```text
Time = O(n²)
```

---

# 8. Python Solution — Without Brute Force / Optimal Hashing

```python
arr = list(map(int, input("Enter elements: ").split()))
target = int(input("Enter target: "))

frequency = {}

pair_count = 0

for num in arr:

    needed = target - num

    if needed in frequency:
        pair_count += frequency[needed]

    if num in frequency:
        frequency[num] += 1
    else:
        frequency[num] = 1

print("Number of pairs =", pair_count)
```

This is the important pattern.

---

# 9. Line-by-Line Explanation

```python
frequency = {}
```

Stores how many times each previously seen number occurred.

---

```python
pair_count = 0
```

Stores total valid pairs.

---

```python
needed = target - num
```

Find the complement.

---

```python
if needed in frequency:
```

Check whether the complement has appeared before.

---

```python
pair_count += frequency[needed]
```

This is the key line.

If:

```text
needed = 5
frequency[5] = 3
```

then the current number forms **3 pairs**.

---

```python
frequency[num] += 1
```

Only after counting pairs do we add the current number.

This prevents pairing the current element with itself.

---

# 10. Detailed Dry Run

Input:

```text
arr = [1, 5, 7, -1, 5]
target = 6
```

Start:

```text
frequency = {}
pair_count = 0
```

### Step 1

Current:

```text
num = 1
needed = 5
```

Frequency of `5`:

```text
0
```

No pair.

Add `1`:

```text
frequency = {1: 1}
```

---

### Step 2

Current:

```text
num = 5
needed = 1
```

Frequency:

```text
1 → 1
```

Therefore:

```text
pair_count = 1
```

Add 5:

```text
frequency = {1: 1, 5: 1}
```

---

### Step 3

Current:

```text
num = 7
needed = -1
```

No `-1`.

Add 7.

---

### Step 4

Current:

```text
num = -1
needed = 7
```

Frequency of `7` is `1`.

Therefore:

```text
pair_count = 2
```

Add `-1`.

---

### Step 5

Current:

```text
num = 5
needed = 1
```

Frequency of `1` is still `1`.

Therefore:

```text
pair_count = 3
```

Final answer:

```text
3
```

---

# 11. Dry Run Table

| Step | `num` | Needed | Previous Frequency | Pairs Added | Total |
| ---: | ----: | -----: | -----------------: | ----------: | ----: |
|    1 |     1 |      5 |                  0 |           0 |     0 |
|    2 |     5 |      1 |                  1 |           1 |     1 |
|    3 |     7 |     -1 |                  0 |           0 |     1 |
|    4 |    -1 |      7 |                  1 |           1 |     2 |
|    5 |     5 |      1 |                  1 |           1 |     3 |

Final:

```text
Number of pairs = 3
```

---

# 12. Why Does `pair_count += frequency[needed]` Work?

Suppose:

```text
target = 10
```

and we currently process:

```text
x = 6
```

We need:

```text
4
```

If we've already seen:

```text
4, 4, 4
```

then current `6` can pair with each one:

```text
4₁ + 6
4₂ + 6
4₃ + 6
```

So:

```text
frequency[4] = 3
```

means:

```text
3 new pairs
```

That's the key insight.

---

# 13. Time Complexity

Each element is processed once:

```text
Time = O(n)
```

Space:

```text
Space = O(n)
```

Compared with brute force:

```text
Brute Force → O(n²)
Hashing     → O(n)
```

---

# 14. Edge Cases

### No pairs

```text
[1, 2, 3]
target = 20
```

Answer:

```text
0
```

### Duplicate pairs

```text
[1, 1, 1, 5]
target = 6
```

The three `1`s can pair with the `5`:

```text
3 pairs
```

### Negative numbers

```text
[-2, 2, 0, 4]
target = 0
```

Pairs:

```text
(-2, 2)
```

Answer:

```text
1
```

### Target zero

Works normally.

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Using a set

A set only tells you:

```text
exists / doesn't exist
```

But here we need:

```text
HOW MANY?
```

Therefore:

```text
Set → Two Sum
Dictionary → Count Pairs
```

---

### ❌ Mistake 2 — Adding current number before counting

Wrong order can cause an element to pair with itself.

Correct:

```text
1. Find complement
2. Count previous complement
3. Add current number
```

---

# 16. Pattern Recognition

When you see:

> "Count how many pairs have sum K"

Think:

```text
COMPLEMENT
+
FREQUENCY MAP
```

Template:

```python
frequency = {}
count = 0

for x in arr:

    needed = target - x

    if needed in frequency:
        count += frequency[needed]

    frequency[x] = frequency.get(x, 0) + 1
```

This is a **high-value TopGun pattern**.

---

# 🔹 PROBLEM 8 — Common Elements in Two Arrays

## 1. Problem Statement

Given two arrays, find the elements that occur in both arrays.

### Example

```text
Array 1:
[1, 2, 3, 4]

Array 2:
[3, 4, 5, 6]

Output:
[3, 4]
```

---

# 2. Problem Theory

We need to determine:

> Does this element from array 2 exist in array 1?

A set makes this very easy.

Convert one array into:

```text
set1
```

Then check each element of the second array.

---

# 3. Pattern Being Tested

# 🔥 HASH SET INTERSECTION

Basic idea:

```text
Array 1
 ↓
Set

Array 2
 ↓
Check membership
 ↓
Found?
 ↓
Common element
```

---

# 4. ELI10 Intuition 🧒

Imagine two classrooms.

Class A:

```text
1 2 3 4
```

Class B:

```text
3 4 5 6
```

Ask each student in Class B:

> "Are you also in Class A?"

```text
3 → Yes
4 → Yes
5 → No
6 → No
```

Common students:

```text
3, 4
```

---

# 5. Example

```text
arr1 = [10, 20, 30, 40]
arr2 = [30, 40, 50]
```

Create:

```text
set1 = {10, 20, 30, 40}
```

Check:

```text
30 → found
40 → found
50 → not found
```

Answer:

```text
[30, 40]
```

---

# 6. Algorithm — Step-by-Step

1. Create a set containing the elements of the first array.
2. Create an empty result list.
3. Traverse the second array.
4. If the current element exists in the first set:

   * add it to the result.
5. Avoid adding the same common value multiple times if unique common elements are required.
6. Print the result.

---

# 7. Python Solution — Using Built-in Set Intersection

```python
arr1 = list(map(int, input("Enter first array: ").split()))
arr2 = list(map(int, input("Enter second array: ").split()))

common = list(set(arr1) & set(arr2))

print("Common elements =", common)
```

Example:

```text
First array:
1 2 3 4

Second array:
3 4 5 6

Common elements = [3, 4]
```

---

# 8. Python Solution — Without Built-in Set Intersection

```python
arr1 = list(map(int, input("Enter first array: ").split()))
arr2 = list(map(int, input("Enter second array: ").split()))

seen = set()

for num in arr1:
    seen.add(num)

result = []
already_added = set()

for num in arr2:

    if num in seen and num not in already_added:
        result.append(num)
        already_added.add(num)

print("Common elements =", result)
```

This explicitly exposes the hashing logic.

---

# 9. Line-by-Line Explanation

```python
seen = set()
```

This will represent all unique elements from the first array.

---

```python
for num in arr1:
    seen.add(num)
```

Build the set.

For:

```text
[1, 2, 2, 3]
```

we get:

```text
{1, 2, 3}
```

---

```python
result = []
```

Stores common elements.

---

```python
already_added = set()
```

Prevents duplicate output.

For example:

```text
arr2 = [3, 3, 3]
```

we generally want:

```text
[3]
```

if the question asks for unique common elements.

---

```python
if num in seen and num not in already_added:
```

Two conditions:

1. Is it present in array 1?
2. Have we already added it?

---

```python
result.append(num)
```

Add common element.

---

```python
already_added.add(num)
```

Remember that we've already included it.

---

# 10. Detailed Dry Run

Input:

```text
arr1 = [1, 2, 3, 4]
arr2 = [3, 4, 4, 5]
```

### Build first set

```text
seen = {1, 2, 3, 4}
```

Now scan `arr2`.

| Step | Number | In `seen`? | Already added? | Result  |
| ---: | -----: | ---------- | -------------- | ------- |
|    1 |      3 | Yes        | No             | `[3]`   |
|    2 |      4 | Yes        | No             | `[3,4]` |
|    3 |      4 | Yes        | Yes            | `[3,4]` |
|    4 |      5 | No         | —              | `[3,4]` |

Final:

```text
[3, 4]
```

---

# 11. Time Complexity

Build first set:

```text
O(n)
```

Scan second array:

```text
O(m)
```

Therefore:

```text
Time = O(n + m)
```

where:

```text
n = length of arr1
m = length of arr2
```

### Space

Set + result:

```text
O(n + m)
```

in the worst case.

---

# 12. Edge Cases

### No common elements

```text
[1, 2]
[3, 4]
```

Result:

```text
[]
```

### Same arrays

```text
[1, 2, 3]
[1, 2, 3]
```

Result:

```text
[1, 2, 3]
```

### Duplicates

```text
[1, 2, 2, 3]
[2, 2, 2]
```

Unique common result:

```text
[2]
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Nested loops

You could do:

```python
for x in arr1:
    for y in arr2:
        ...
```

but that gives:

```text
O(n × m)
```

Hashing gives:

```text
O(n + m)
```

on average.

---

### ❌ Mistake 2 — Forgetting duplicate output requirements

If the question asks for **unique common elements**, use a set to prevent duplicates.

---

# 14. Pattern Recognition

When you see:

> "Find elements present in both arrays"

Think:

```text
ARRAY 1
 ↓
HASH SET

ARRAY 2
 ↓
MEMBERSHIP CHECK
```

Template:

```python
seen = set(arr1)

for x in arr2:
    if x in seen:
        # common
```

---

# 🧠 HASHING — CONVERSATION 2 COMPLETE

You have now completed:

```text
HASHING
████████░░ 8 / 10
```

### Problems covered

|  # | Problem                     | Core Pattern           |
| -: | --------------------------- | ---------------------- |
|  5 | First Non-Repeating Element | Frequency + Traversal  |
|  6 | Two Sum                     | Complement Hashing     |
|  7 | Count Pairs Target Sum      | Frequency + Complement |
|  8 | Common Elements             | HashSet Intersection   |

---

# 🔥 THE MOST IMPORTANT HASHING PROGRESSION

Notice how the data structure changes based on the question.

```text
                 HASHING
                    │
       ┌────────────┴────────────┐
       ↓                         ↓
   Need COUNT?              Need EXISTENCE?
       ↓                         ↓
   Dictionary                   Set
       │                         │
       ├── Frequency             ├── Duplicate
       ├── First unique          ├── First repeat
       └── Pair counting         └── Common elements
```

Then comes the most important extension:

```text
                 TARGET
                   ↓
          target - current
                   ↓
              COMPLEMENT
                   ↓
            Hash Set / Map
```

That's the heart of **Two Sum**.

---

# 🎯 TOPGUN PATTERN RECOGNITION

| Question wording                  | Think immediately          |
| --------------------------------- | -------------------------- |
| "Frequency of each"               | **Dictionary**             |
| "First non-repeating"             | **Frequency + traversal**  |
| "Contains duplicate"              | **Set**                    |
| "First repeating"                 | **Set + traversal**        |
| "Two numbers sum to K"            | **Complement hashing**     |
| "Count pairs sum to K"            | **Frequency + complement** |
| "Present in both arrays"          | **Set intersection**       |
| "Have I seen this before?"        | **Set**                    |
| "How many previous values match?" | **Frequency map**          |

---

# 🧠 MASTER TEMPLATES FROM CONVERSATION 2

## Template 1 — First Unique

```python
frequency = {}

for x in data:
    frequency[x] = frequency.get(x, 0) + 1

for x in data:
    if frequency[x] == 1:
        return x
```

---

## Template 2 — Two Sum

```python
seen = set()

for x in arr:

    needed = target - x

    if needed in seen:
        return [needed, x]

    seen.add(x)
```

---

## Template 3 — Count Target Pairs

```python
frequency = {}
count = 0

for x in arr:

    needed = target - x

    if needed in frequency:
        count += frequency[needed]

    frequency[x] = frequency.get(x, 0) + 1
```

---

## Template 4 — Common Elements

```python
seen = set(arr1)

result = []

for x in arr2:
    if x in seen:
        result.append(x)
```

---

# 📈 CURRENT DSA PROGRESS

```text
ARRAYS
██████████ 10/10 ✅

STRINGS
██████████ 10/10 ✅

HASHING
████████░░ 8/10 🔥
```

### Next: HASHING — CONVERSATION 3

**Problem 9 — Group Anagrams**
→ Hashing + frequency/signature

**Problem 10 — Longest Consecutive Sequence**
→ HashSet + sequence detection

Then:

### 🏆 HASHING MASTERY

* All 10 problems connected into patterns
* Pattern recognition
* Master templates
* Common traps
* Unseen TopGun-style problems
* Mini test without giving the pattern beforehand.

Would you like to continue with Hashing Conversation 3, or take a short mastery test on Problems 5–8 first?

# 🔵 HASHING — CONVERSATION 3

## Problems 9–10 + Hashing Mastery

We preserve the **locked version** completely.

Today's final two problems move into more interview-oriented hashing patterns:

|  # | Problem                      | Main Pattern                  |
| -: | ---------------------------- | ----------------------------- |
|  9 | Group Anagrams               | Hashing + Frequency Signature |
| 10 | Longest Consecutive Sequence | HashSet + Sequence Detection  |

After Problem 10, we will connect all **10 hashing problems into a small number of reusable patterns**, then finish with a mastery framework and unseen-question recognition.

---

# 🔹 PROBLEM 9 — Group Anagrams

## 1. Problem Statement

Given a list of strings, group strings that are anagrams of each other.

### Example

```text
Input:
["eat", "tea", "tan", "ate", "nat", "bat"]
```

Output can be:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

The exact group order is not important unless the question specifies it.

---

# 2. Problem Theory

We already learned:

> Two strings are anagrams if they contain the same characters with the same frequencies.

For example:

```text
"eat"
"tea"
"ate"
```

All have:

```text
a → 1
e → 1
t → 1
```

Therefore they belong to the same group.

The challenge is:

> How do we quickly identify that two strings have the same character composition?

We create a **signature/key** for every word.

For example, one simple signature is the sorted characters:

```text
eat → aet
tea → aet
ate → aet
```

Same key → same group.

---

# 3. Pattern Being Tested

# 🔥 HASHING + SIGNATURE

The general pattern is:

```text
Item
 ↓
Convert into a unique signature
 ↓
Use signature as dictionary key
 ↓
Group matching items
```

This is a very important extension of basic hashing.

---

# 4. ELI10 Intuition 🧒

Imagine every word needs an identity card.

For:

```text
eat
tea
ate
```

we rearrange their letters alphabetically:

```text
eat → aet
tea → aet
ate → aet
```

They all have the same identity card:

```text
"aet"
```

So put them into the same box.

For:

```text
bat → abt
```

it gets a different box.

---

# 5. Example

Input:

```text
["cat", "dog", "tac", "god"]
```

Signatures:

```text
cat → act
dog → dgo
tac → act
god → dgo
```

Therefore:

```text
[
    ["cat", "tac"],
    ["dog", "god"]
]
```

---

# 6. Algorithm — Step-by-Step

### Sorting-signature approach

1. Create an empty dictionary.
2. Traverse every word.
3. Sort the characters in the word.
4. Convert the sorted characters into a string.
5. Use that string as the dictionary key.
6. Add the original word to that key's group.
7. After processing all words, return the dictionary values.

---

# 7. Python Solution — Using Built-in Methods

```python
from collections import defaultdict

words = input("Enter words separated by space: ").split()

groups = defaultdict(list)

for word in words:

    key = "".join(sorted(word))

    groups[key].append(word)

result = list(groups.values())

print("Grouped anagrams =", result)
```

### Example

Input:

```text
eat tea tan ate nat bat
```

Possible output:

```text
[['eat', 'tea', 'ate'], ['tan', 'nat'], ['bat']]
```

---

# 8. Python Solution — Without `sorted()`

Now we expose the underlying **frequency-signature** idea.

For lowercase English letters, there are 26 possible characters.

We can create a 26-element frequency signature.

```python
words = input("Enter words separated by space: ").split()

groups = {}

for word in words:

    frequency = [0] * 26

    for ch in word:
        index = ord(ch) - ord('a')
        frequency[index] += 1

    key = tuple(frequency)

    if key not in groups:
        groups[key] = []

    groups[key].append(word)

result = list(groups.values())

print("Grouped anagrams =", result)
```

This is a much more important DSA implementation because it teaches you that an anagram can be represented by its **frequency signature**.

---

# 9. Line-by-Line Explanation

### Create groups

```python
groups = {}
```

This dictionary stores:

```text
signature → list of words
```

---

### Create frequency array

```python
frequency = [0] * 26
```

Initially:

```text
[0, 0, 0, ..., 0]
```

Each position represents one letter.

```text
a → index 0
b → index 1
c → index 2
...
z → index 25
```

---

### Convert character into index

```python
index = ord(ch) - ord('a')
```

For:

```text
'a'
```

we get:

```text
ord('a') - ord('a') = 0
```

For:

```text
'c'
```

we get:

```text
ord('c') - ord('a') = 2
```

---

### Increase frequency

```python
frequency[index] += 1
```

This records how many times that letter occurs.

---

### Convert list into tuple

```python
key = tuple(frequency)
```

Why?

Because lists are mutable and cannot be dictionary keys.

Tuples are immutable and hashable.

---

### Add word to its group

```python
if key not in groups:
    groups[key] = []

groups[key].append(word)
```

All words with the same frequency signature enter the same list.

---

# 10. Detailed Dry Run

Input:

```text
["eat", "tea", "tan", "ate", "nat", "bat"]
```

Let's examine the first three.

### Word 1

```text
eat
```

Frequency:

```text
a → 1
e → 1
t → 1
```

Signature conceptually:

```text
[a:1, e:1, t:1]
```

Create:

```text
groups[signature] = ["eat"]
```

---

### Word 2

```text
tea
```

Frequency:

```text
a → 1
e → 1
t → 1
```

Same signature.

Therefore:

```text
groups[signature] = ["eat", "tea"]
```

---

### Word 3

```text
tan
```

Frequency:

```text
a → 1
n → 1
t → 1
```

Different signature.

New group:

```text
["tan"]
```

---

### Word 4

```text
ate
```

Frequency:

```text
a → 1
e → 1
t → 1
```

Matches the first signature.

```text
["eat", "tea", "ate"]
```

---

# 11. Dry Run Table

| Word  | Signature | Group             |
| ----- | --------- | ----------------- |
| `eat` | a1-e1-t1  | `[eat]`           |
| `tea` | a1-e1-t1  | `[eat, tea]`      |
| `tan` | a1-n1-t1  | `[tan]`           |
| `ate` | a1-e1-t1  | `[eat, tea, ate]` |
| `nat` | a1-n1-t1  | `[tan, nat]`      |
| `bat` | a1-b1-t1  | `[bat]`           |

Final:

```text
[
    ["eat", "tea", "ate"],
    ["tan", "nat"],
    ["bat"]
]
```

---

# 12. Time Complexity

### Sorting-signature solution

Suppose there are:

* `k` words
* each word has approximately `m` characters

Sorting each word costs:

```text
O(m log m)
```

For `k` words:

```text
O(k × m log m)
```

---

### Frequency-signature solution

Each word is traversed once:

```text
O(m)
```

Therefore:

```text
O(k × m)
```

assuming a fixed 26-letter alphabet.

### Space

Groups and signatures require:

```text
O(k × m)
```

overall for storing the words/results.

---

# 13. Edge Cases

### Empty input

```text
[]
```

Result:

```text
[]
```

### One word

```text
["hello"]
```

One group.

### All anagrams

```text
["eat", "tea", "ate"]
```

One group.

### No anagrams

```text
["cat", "dog", "fish"]
```

Three groups.

### Repeated words

```text
["cat", "cat"]
```

Both belong to the same group.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using the original word as the key

```python
groups[word]
```

would treat:

```text
eat
tea
ate
```

as different.

We need a common signature.

---

### ❌ Mistake 2 — Comparing only length

These have equal length:

```text
cat
dog
```

but aren't anagrams.

We need character composition.

---

### ❌ Mistake 3 — Forgetting frequency

These:

```text
aab
abb
```

have the same characters but different frequencies.

Therefore they are not anagrams.

---

# 15. Pattern Recognition

When you see:

> "Group items that have the same internal structure/property"

Think:

```text
ITEM
 ↓
CREATE SIGNATURE
 ↓
HASH MAP
 ↓
GROUP BY SIGNATURE
```

For anagrams:

```text
word
 ↓
character frequency
 ↓
signature
 ↓
dictionary key
```

This pattern is much more powerful than simply memorizing "Group Anagrams."

---

# 🔹 PROBLEM 10 — Longest Consecutive Sequence

## 1. Problem Statement

Given an unsorted array of integers, find the length of the longest sequence of consecutive numbers.

### Example

```text
Input:
[100, 4, 200, 1, 3, 2]

Output:
4
```

Because:

```text
1, 2, 3, 4
```

is a consecutive sequence of length `4`.

---

# 2. Problem Theory

The array is **not sorted**.

```text
[100, 4, 200, 1, 3, 2]
```

We need to discover:

```text
1 → 2 → 3 → 4
```

A brute-force approach could repeatedly search for the next number.

Sorting is another approach.

But hashing gives an O(n)-average solution.

---

# 3. Pattern Being Tested

# 🔥 HASHSET + SEQUENCE DETECTION

The key insight:

> Only start counting when the current number is the **beginning** of a sequence.

How do we know?

For number `x`, check:

```text
x - 1
```

If `x - 1` does not exist, then `x` is a sequence start.

Example:

```text
1
```

`0` doesn't exist.

So:

```text
1 → 2 → 3 → 4
```

Start counting.

But for:

```text
3
```

`2` exists.

Therefore `3` is not a sequence start.

---

# 4. ELI10 Intuition 🧒

Imagine numbers are houses:

```text
1   2   3   4       7       100
```

You want the longest row of houses with no gaps.

Start at `1` because there is no `0`.

Then check:

```text
2? Yes
3? Yes
4? Yes
5? No
```

Length:

```text
4
```

Don't start again from `2`, because you already know it belongs to the sequence beginning at `1`.

---

# 5. Example

```text
[9, 1, 4, 7, 3, 2, 6]
```

Set:

```text
{1, 2, 3, 4, 6, 7, 9}
```

Sequence:

```text
1 → 2 → 3 → 4
```

Length:

```text
4
```

Another sequence:

```text
6 → 7
```

Length:

```text
2
```

Answer:

```text
4
```

---

# 6. Algorithm — Step-by-Step

1. Put all numbers into a set.
2. Initialize `longest = 0`.
3. Traverse every number.
4. For each number `x`, check whether `x - 1` exists.
5. If `x - 1` exists:

   * `x` is not a sequence start.
   * skip it.
6. If `x - 1` does not exist:

   * `x` is the beginning of a sequence.
7. Start checking:

   ```text
   x + 1
   x + 2
   x + 3
   ...
   ```
8. Count the sequence length.
9. Update `longest`.
10. Return `longest`.

---

# 7. Python Solution — Using Built-in Sorting

The easier approach is to sort first.

```python
arr = list(map(int, input("Enter elements: ").split()))

if not arr:
    print("Longest consecutive length = 0")

else:
    arr.sort()

    longest = 1
    current = 1

    for i in range(1, len(arr)):

        if arr[i] == arr[i - 1] + 1:
            current += 1

        elif arr[i] != arr[i - 1]:
            current = 1

        if current > longest:
            longest = current

    print("Longest consecutive length =", longest)
```

### Complexity

Sorting makes this:

```text
O(n log n)
```

---

# 8. Python Solution — HashSet / Optimal Pattern

```python
arr = list(map(int, input("Enter elements: ").split()))

numbers = set(arr)

longest = 0

for num in numbers:

    if num - 1 not in numbers:

        current = num
        length = 1

        while current + 1 in numbers:
            current += 1
            length += 1

        if length > longest:
            longest = length

print("Longest consecutive length =", longest)
```

This is the important DSA solution.

---

# 9. Line-by-Line Explanation

```python
numbers = set(arr)
```

Creates a hash set.

For:

```text
[100, 4, 200, 1, 3, 2]
```

we get:

```text
{1, 2, 3, 4, 100, 200}
```

---

```python
longest = 0
```

Stores the largest sequence found.

---

```python
for num in numbers:
```

Process each unique number.

---

```python
if num - 1 not in numbers:
```

This is the **most important line**.

It asks:

> Is there a previous number?

If yes, this isn't the beginning.

If no, this is a sequence start.

---

```python
current = num
length = 1
```

Start a new sequence.

---

```python
while current + 1 in numbers:
```

Keep extending the sequence.

---

```python
current += 1
length += 1
```

Move to the next consecutive number.

---

```python
if length > longest:
    longest = length
```

Keep the maximum.

---

# 10. Detailed Dry Run

Input:

```text
[100, 4, 200, 1, 3, 2]
```

Set:

```text
{1, 2, 3, 4, 100, 200}
```

### Number = 1

Check:

```text
1 - 1 = 0
```

Is `0` in set?

```text
No
```

Therefore `1` starts a sequence.

Now:

```text
1 → 2 → 3 → 4
```

Check:

```text
2 exists ✓
3 exists ✓
4 exists ✓
5 doesn't exist ✗
```

Length:

```text
4
```

Update:

```text
longest = 4
```

---

### Number = 2

Check:

```text
1 exists
```

Therefore:

```text
2 is not a sequence start
```

Skip.

---

### Number = 3

Check:

```text
2 exists
```

Skip.

---

### Number = 4

Check:

```text
3 exists
```

Skip.

---

### Number = 100

Check:

```text
99 doesn't exist
```

Start sequence:

```text
100
```

Length:

```text
1
```

`longest` remains `4`.

---

### Number = 200

Check:

```text
199 doesn't exist
```

Sequence length:

```text
1
```

Final:

```text
4
```

---

# 11. Dry Run Table

| Number | `num-1` exists? | Sequence Start? | Sequence | Length |
| -----: | --------------- | --------------- | -------- | -----: |
|      1 | No              | ✅               | 1-2-3-4  |      4 |
|      2 | Yes             | ❌               | —        |      — |
|      3 | Yes             | ❌               | —        |      — |
|      4 | Yes             | ❌               | —        |      — |
|    100 | No              | ✅               | 100      |      1 |
|    200 | No              | ✅               | 200      |      1 |

Final:

```text
Longest consecutive length = 4
```

---

# 12. Why Don't We Start From Every Number?

Suppose:

```text
1, 2, 3, 4
```

If we start from every number:

```text
1 → 2 → 3 → 4
2 → 3 → 4
3 → 4
4
```

we repeat work.

Instead:

```text
1
```

is the only sequence start because:

```text
0 does not exist
```

Then:

```text
2
```

is skipped because `1` exists.

This is the key optimization.

---

# 13. Time Complexity

### Sorting approach

```text
O(n log n)
```

### HashSet approach

Creating set:

```text
O(n)
```

Sequence detection is O(n) overall because each sequence element is effectively processed as part of a sequence beginning only once.

Therefore average:

```text
Time = O(n)
```

### Space

Set:

```text
O(n)
```

Therefore:

```text
Space = O(n)
```

---

# 14. Edge Cases

### Empty array

```text
[]
```

Answer:

```text
0
```

### One element

```text
[10]
```

Answer:

```text
1
```

### Already consecutive

```text
[1, 2, 3, 4, 5]
```

Answer:

```text
5
```

### Completely scattered

```text
[10, 50, 100]
```

Answer:

```text
1
```

### Negative values

```text
[-3, -2, -1, 0, 1]
```

Answer:

```text
5
```

### Duplicate values

```text
[1, 2, 2, 3]
```

Set becomes:

```text
{1, 2, 3}
```

Longest consecutive length:

```text
3
```

Duplicates don't extend the sequence.

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Starting a sequence from every number

You must check:

```python
if num - 1 not in numbers:
```

---

### ❌ Mistake 2 — Assuming the array is sorted

The problem specifically tests an **unsorted** array.

---

### ❌ Mistake 3 — Counting duplicates as consecutive

```text
1, 2, 2, 3
```

The consecutive sequence is:

```text
1, 2, 3
```

Length `3`, not `4`.

---

# 16. Pattern Recognition

When you see:

> "Longest consecutive sequence in an unsorted array"

Think:

# HASH SET + SEQUENCE START

Immediately ask:

```text
Does x - 1 exist?
```

If:

```text
NO
```

then:

```text
x is a sequence start
```

Then expand:

```text
x + 1
x + 2
x + 3
...
```

---

# 🏆 HASHING — ALL 10 PROBLEMS COMPLETE

```text
HASHING
██████████ 10/10 ✅
```

Now the important part is **not memorizing 10 solutions**.

We compress all 10 into reusable patterns.

---

# 🧠 HASHING MASTER PATTERN MAP

## PATTERN 1 — FREQUENCY MAP

Problems:

```text
1. Character Frequency
2. Element Frequency
5. First Non-Repeating
7. Count Target Pairs
```

Core structure:

```python
frequency = {}

for x in data:
    frequency[x] = frequency.get(x, 0) + 1
```

### Think:

> **"How many?" → Dictionary**

---

# PATTERN 2 — SEEN SET

Problems:

```text
3. Contains Duplicate
4. First Repeating
8. Common Elements
```

Core structure:

```python
seen = set()

for x in data:
    if x in seen:
        ...
    seen.add(x)
```

### Think:

> **"Have I seen this?" → Set**

---

# PATTERN 3 — COMPLEMENT HASHING

Problems:

```text
6. Two Sum
7. Count Pairs With Target Sum
```

Core idea:

```text
current
   ↓
target - current
   ↓
needed / complement
   ↓
look it up
```

### Two Sum:

```python
seen = set()

for x in arr:
    needed = target - x

    if needed in seen:
        return [needed, x]

    seen.add(x)
```

### Count pairs:

```python
frequency = {}
count = 0

for x in arr:
    needed = target - x

    if needed in frequency:
        count += frequency[needed]

    frequency[x] = frequency.get(x, 0) + 1
```

### Critical distinction:

```text
Need ONE matching value?
→ Set

Need HOW MANY matching values?
→ Frequency Map
```

---

# PATTERN 4 — HASHING + SIGNATURE

Problem:

```text
9. Group Anagrams
```

Core idea:

```text
item
 ↓
signature
 ↓
dictionary key
 ↓
group
```

For anagrams:

```text
eat → aet
tea → aet
ate → aet
```

Same signature → same group.

---

# PATTERN 5 — HASH SET + SEQUENCE DETECTION

Problem:

```text
10. Longest Consecutive Sequence
```

Core idea:

```python
if x - 1 not in numbers:
```

means:

> `x` is the beginning of a sequence.

Then:

```text
x → x+1 → x+2 → x+3...
```

---

# 🔥 HASHING DECISION TREE

When you see a new problem, use this:

```text
                    HASHING QUESTION
                           │
             ┌─────────────┴─────────────┐
             │                           │
       Need frequency?              Need existence?
             │                           │
          DICT                         SET
             │                           │
      ┌──────┴──────┐             ┌──────┴──────┐
      │             │             │             │
   Count        First unique   Duplicate    Common
      │
   Pair count
      │
  Complement
```

Then:

```text
"Two values make target?"
        ↓
Complement

"Group same structure?"
        ↓
Signature

"Longest consecutive?"
        ↓
Sequence start
```

---

# 🎯 SENIOR PATTERN RECOGNITION

| Question wording       | Immediately think                        |
| ---------------------- | ---------------------------------------- |
| "Frequency of each..." | **Dictionary**                           |
| "How many times..."    | **Frequency Map**                        |
| "First unique..."      | **Frequency + original traversal**       |
| "Duplicate?"           | **Set**                                  |
| "First repeating..."   | **Set + traversal**                      |
| "Two numbers sum to K" | **Complement Hashing**                   |
| "Count pairs sum to K" | **Frequency + Complement**               |
| "Common elements"      | **Set membership/intersection**          |
| "Group anagrams"       | **Frequency/Sorted Signature + HashMap** |
| "Longest consecutive"  | **Set + sequence-start detection**       |

---

# 🧠 HASHING MASTER TEMPLATES

## 1️⃣ Frequency Map

```python
frequency = {}

for x in data:

    if x in frequency:
        frequency[x] += 1
    else:
        frequency[x] = 1
```

Or:

```python
frequency[x] = frequency.get(x, 0) + 1
```

---

## 2️⃣ Seen Set

```python
seen = set()

for x in data:

    if x in seen:
        # already seen

    seen.add(x)
```

---

## 3️⃣ First Unique

```python
frequency = {}

for x in data:
    frequency[x] = frequency.get(x, 0) + 1

for x in data:
    if frequency[x] == 1:
        return x
```

---

## 4️⃣ Two Sum

```python
seen = set()

for x in arr:

    needed = target - x

    if needed in seen:
        return [needed, x]

    seen.add(x)
```

---

## 5️⃣ Count Pairs

```python
frequency = {}
count = 0

for x in arr:

    needed = target - x

    if needed in frequency:
        count += frequency[needed]

    frequency[x] = frequency.get(x, 0) + 1
```

---

## 6️⃣ Group By Signature

```python
groups = {}

for item in data:

    key = create_signature(item)

    if key not in groups:
        groups[key] = []

    groups[key].append(item)
```

---

## 7️⃣ Longest Consecutive

```python
numbers = set(arr)

longest = 0

for x in numbers:

    if x - 1 not in numbers:

        current = x
        length = 1

        while current + 1 in numbers:
            current += 1
            length += 1

        longest = max(longest, length)
```

---

# 🏆 HASHING — 10-PROBLEM COMPLETE CHECKLIST

|  # | Problem                     | Pattern                | Status |
| -: | --------------------------- | ---------------------- | ------ |
|  1 | Character Frequency         | Frequency Map          | ✅      |
|  2 | Element Frequency           | Frequency Map          | ✅      |
|  3 | Contains Duplicate          | HashSet                | ✅      |
|  4 | First Repeating Element     | HashSet + Traversal    | ✅      |
|  5 | First Non-Repeating Element | Frequency + Traversal  | ✅      |
|  6 | Two Sum                     | Complement Hashing     | ✅      |
|  7 | Count Target Pairs          | Frequency + Complement | ✅      |
|  8 | Common Elements             | HashSet                | ✅      |
|  9 | Group Anagrams              | Signature + HashMap    | ✅      |
| 10 | Longest Consecutive         | HashSet + Sequence     | ✅      |

---

# 🔥 THE 5 THINGS YOU MUST MASTER

If TopGun gives you a new hashing problem, your first thought should be one of these:

```text
1. "How many?"
       ↓
   FREQUENCY MAP


2. "Have I seen it?"
       ↓
   HASH SET


3. "What completes the target?"
       ↓
   COMPLEMENT


4. "Which items have the same structure?"
       ↓
   SIGNATURE


5. "Where does the sequence begin?"
       ↓
   x - 1 CHECK
```

If you can identify these five patterns quickly, you have the **basic hashing foundation** this 10-problem set is designed to build.

---

# 🧪 HASHING MASTERY TEST — NO PATTERN GIVEN

Do **not** immediately code. First identify the pattern.

### Q1

```text
arr = [4, 7, 4, 2, 7, 7]
```

Find the frequency of every element.

**Expected thinking:** `?`

---

### Q2

```text
arr = [5, 2, 8, 5, 9]
```

Determine whether the array contains a duplicate.

**Expected thinking:** `?`

---

### Q3

```text
arr = [3, 8, 2, 7]
target = 10
```

Find two numbers whose sum is `10`.

**Expected thinking:** `?`

---

### Q4

```text
arr = [1, 5, 3, 5, 2, 1]
```

Find the first element that appears for the second time.

**Expected thinking:** `?`

---

### Q5

```text
arr = [100, 4, 200, 1, 3, 2]
```

Find the length of the longest consecutive sequence.

**Expected thinking:** `?`

---

### Q6

```text
words = ["eat", "tea", "tan", "ate", "nat", "bat"]
```

Group the anagrams.

**Expected thinking:** `?`

---

# 📈 TOPGUN DSA PROGRESS

```text
ARRAYS
██████████ 10/10 ✅

STRINGS
██████████ 10/10 ✅

HASHING
██████████ 10/10 ✅
```

### Current coverage

**3 / 12 topics complete**

```text
██████████████████░░░░░░░░░░░░ 3 / 12
```

The next locked topic is:

# 🔵 SEARCHING — CONVERSATION 1

### Problems 1–4

1. Linear Search
2. First Occurrence
3. Last Occurrence
4. Count Occurrences

Would you like to answer the six hashing mastery questions first, or move on to Searching — Conversation 1?
