Excellent progression. This roadmap covers almost every **string pattern** used in FAANG/MAANG interviews. Since your goal is **mastering patterns**, here's the recommended learning sequence with what each layer teaches and why it's important.

# FINAL SYLLABUS

~~~

# 5️⃣ STRINGS — HIGH PRIORITY

Strings should **not** be studied as an isolated giant topic.

Most interview String problems are actually:

```text
String
 +
HashMap
 +
Sliding Window
 +
Two Pointers
 +
Stack
```

### 🔴 P0

- **LC 125 — Valid Palindrome**
- **LC 242 — Valid Anagram**
- **LC 3 — Longest Substring Without Repeating Characters**
- **LC 49 — Group Anagrams**
- **LC 20 — Valid Parentheses**
- **LC 387 — First Unique Character in a String**

### 🟠 P1

- LC 438 — Find All Anagrams
- LC 567 — Permutation in String
- LC 424 — Longest Repeating Character Replacement
- LC 394 — Decode String

### 🟡 P2

- LC 5 — Longest Palindromic Substring
- LC 76 — Minimum Window Substring

For your target, don't spend huge amounts of time on advanced string algorithms such as:

❌ KMP  
❌ Rabin-Karp  
❌ Z-algorithm  
❌ suffix arrays  

Those violate our current ROI constraint.

---

~~~
---

# 📚 String Pattern Mastery Roadmap

| Layer | Pattern                  | Goal                                                     | Problems                       |
| ----: | ------------------------ | -------------------------------------------------------- | ------------------------------ |
|     1 | Traversal + Two Pointers | Learn how to scan and manipulate strings efficiently     | LC 58, LC 344, LC 125          |
|     2 | HashMap + Strings        | Count frequencies and build character mappings           | LC 242, LC 387, LC 205, LC 290 |
|     3 | Sliding Window           | Solve substring optimization problems                    | LC 3, LC 424, LC 438, LC 567   |
|     4 | Parsing + Stack          | Decode nested expressions and process structured strings | LC 151, LC 394, LC 71          |
|     5 | Advanced String Patterns | Learn grouping, matching, and compression                | LC 49, LC 14, LC 28, LC 443    |
|     6 | Interview Mastery        | Master the hardest interview string problems             | LC 76, LC 30, LC 68            |

---

# 🟢 Layer 1 — Traversal + Two Pointers

## Goal

Learn how to move through strings efficiently without extra memory.

### Skills

* Character-by-character traversal
* Left and right pointers
* Ignoring unwanted characters
* Reversing strings
* Comparing characters
* Building answers in-place

### Problems

### LC 58 — Length of Last Word

Pattern

```text
Simple Traversal
```

---

### LC 344 — Reverse String

Pattern

```text
Two Pointers
```

---

### LC 125 — Valid Palindrome

Pattern

```text
Two Pointers

+

Skip Invalid Characters
```

---

## Recognition Signals

Whenever you see

```text
Reverse

Palindrome

Compare

Ignore Spaces

Scan
```

Think

```text
Traversal

or

Two Pointers
```

---

# 🟡 Layer 2 — HashMap + Strings

## Goal

Master character frequencies and mappings.

### Skills

* Frequency counting
* Character mapping
* Pattern matching
* One-to-one mapping
* First occurrence
* Uniqueness

### Problems

### LC 242

Frequency Map

---

### LC 387

Frequency + Two Passes

---

### LC 205

Two HashMaps

---

### LC 290

Word Pattern

(Two HashMaps again)

---

## Recognition Signals

```text
Frequency

Count

Unique

Mapping

Pattern
```

↓

```text
HashMap
```

---

# 🟠 Layer 3 — Sliding Window

This is where interviews become more interesting.

## Goal

Maintain information about a **moving substring**.

Instead of checking every substring,

maintain

```text
Window

↓

Expand

↓

Shrink
```

### Skills

* Dynamic window
* Character frequencies
* Longest substring
* Shortest substring
* Fixed window
* Variable window

---

### LC 3

Longest Substring Without Repeating Characters

Pattern

```text
Sliding Window

+

HashSet
```

---

### LC 424

Longest Repeating Character Replacement

Pattern

```text
Sliding Window

+

Frequency
```

---

### LC 438

Find All Anagrams

Pattern

```text
Fixed Window

+

Frequency
```

---

### LC 567

Permutation in String

Pattern

```text
Fixed Window

+

Frequency Comparison
```

---

## Recognition Signals

Whenever you hear

```text
Substring

Longest

Shortest

Window

Continuous
```

↓

Think

```text
Sliding Window
```

---

# 🔵 Layer 4 — Parsing + Stack

Here we stop treating strings as plain characters.

Instead,

we interpret them.

---

### LC 151

Reverse Words

Pattern

```text
Parsing
```

---

### LC 394

Decode String

Pattern

```text
Stack
```

---

### LC 71

Simplify Path

Pattern

```text
Stack

+

Parsing
```

---

## Recognition Signals

```text
Nested

Parentheses

Decode

Directory

Expression
```

↓

```text
Stack
```

---

# 🟣 Layer 5 — Advanced String Patterns

These are combinations of multiple earlier patterns.

---

### LC 49

Canonical Key

(HashMap of Lists)

---

### LC 14

Longest Common Prefix

Pattern

```text
Vertical Scanning
```

---

### LC 28

Find First Occurrence

Pattern

```text
Substring Matching
```

(Interview note: Know the basic solution first, then learn KMP later.)

---

### LC 443

String Compression

Pattern

```text
Two Pointers

+

Run-Length Encoding
```

---

## Recognition Signals

```text
Group

Compress

Common Prefix

Find Pattern
```

↓

```text
Advanced String Algorithms
```

---

# 🔴 Layer 6 — Interview Mastery

These are the hardest and most frequently discussed string interview problems.

---

### LC 76

Minimum Window Substring

Pattern

```text
Variable Sliding Window

+

Frequency Map
```

Difficulty

⭐⭐⭐⭐⭐

---

### LC 30

Substring with Concatenation of All Words

Pattern

```text
Sliding Window

+

HashMap

+

Word Matching
```

Difficulty

⭐⭐⭐⭐⭐

---

### LC 68

Text Justification

Pattern

```text
Greedy

+

String Construction
```

Difficulty

⭐⭐⭐⭐⭐

---

# 🎯 Pattern Evolution

```text
Traversal
      │
      ▼
Two Pointers
      │
      ▼
HashMap
      │
      ▼
Sliding Window
      │
      ▼
Parsing + Stack
      │
      ▼
Advanced String Algorithms
      │
      ▼
Interview Mastery
```

---

# 🧠 Master Pattern Cheat Sheet

| Interview Signal           | Pattern                            |
| -------------------------- | ---------------------------------- |
| Reverse string             | Two Pointers                       |
| Palindrome                 | Two Pointers                       |
| Character frequency        | HashMap                            |
| Unique character           | Frequency Map                      |
| Character mapping          | Two HashMaps                       |
| Longest/Shortest substring | Sliding Window                     |
| Fixed-size substring       | Fixed Sliding Window               |
| Decode nested string       | Stack                              |
| File path simplification   | Stack                              |
| Group anagrams             | HashMap of Lists                   |
| Common prefix              | Vertical Scanning                  |
| String compression         | Two Pointers + Run-Length Encoding |
| Minimum window             | Variable Sliding Window            |
| Text formatting            | Greedy                             |

---

#  Recommended Learning Order

Since you've already completed the HashMap string problems (LC 242, LC 387, LC 205) and LC 49, the next logical sequence is:

1. **Layer 1:** LC 58 → LC 344 → LC 125
2. **Finish Layer 2:** LC 290
3. **Layer 3:** LC 3 → LC 424 → LC 438 → LC 567
4. **Layer 4:** LC 151 → LC 394 → LC 71
5. **Finish Layer 5:** LC 14 → LC 28 → LC 443
6. **Layer 6:** LC 76 → LC 30 → LC 68

This order builds each new pattern on top of the previous one, making the transition to advanced interview questions much smoother.

# LC 58 — Length of Last Word ⭐⭐⭐

**Pattern:** String Traversal (Reverse Scan)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐ (Foundation of String Traversal)

> **LC 58 is the "Hello World" of String Traversal.**
>
> It teaches one of the most important interview skills:
>
> **Scan from the direction that makes the problem easier.**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given a string

```python
s = "Hello World"
```

Return

```python
5
```

because

```text
Last Word = "World"

Length = 5
```

---

Example 2

```python
s = "   fly me   to   the moon  "
```

Return

```python
4
```

Last word

```text
moon
```

Length

```text
4
```

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Length of Last Word
```

A senior engineer immediately thinks

```text
Need only the LAST word

↓

Why scan from the beginning?

↓

Scan from the END.
```

This immediately removes unnecessary work.

---

# 3. Why Brute Force Isn't Ideal

One approach:

```python
words = s.split()

return len(words[-1])
```

Works.

But interviewers usually expect you to solve it **without creating another list**, because:

* `split()` creates extra memory.
* You're asked to demonstrate string traversal.

---

# 4. The Key Observation

Example

```python
s = "Hello World   "
```

Start from the end.

```text
Hello World___
            ↑
```

Skip spaces.

```text
Hello World
          ↑
```

Now count until the next space.

```text
d

↓

l

↓

r

↓

o

↓

W
```

Stop.

Answer

```text
5
```

---

# 5. Why Reverse Traversal?

Forward traversal:

```text
Hello World

Need entire string

↓

Need remember last word
```

Reverse traversal:

```text
Hello World

↓

Already at last word

↓

Much easier
```

---

# 6. Algorithm

Step 1

Skip trailing spaces.

```text
____

↓

Ignore
```

---

Step 2

Count letters.

```text
World

↓

5
```

---

Step 3

Stop when space appears.

Done.

---

# 7. Recognition Signals

Whenever you see

```text
Last

Trailing

End

Suffix

Right-most
```

Think

```text
Reverse Traversal
```

---

# 8. Complexity

Single scan.

Time

[
O(n)
]

Space

[
O(1)
]

No extra string or list.

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def lengthOfLastWord(self, s):

        i = len(s) - 1

        # Skip trailing spaces
        while i >= 0 and s[i] == ' ':
            i -= 1

        length = 0

        # Count characters
        while i >= 0 and s[i] != ' ':
            length += 1
            i -= 1

        return length
```

---

## Time Complexity

[
O(n)
]

Every character is visited at most once.

---

## Space Complexity

[
O(1)
]

---

## Interview Justification

> I traverse the string from right to left because only the last word matters. First, I skip trailing spaces. Then I count consecutive non-space characters until I reach another space or the beginning of the string. This avoids creating extra data structures and runs in O(n) time with O(1) space.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def lengthOfLastWord(self, s):

        i = len(s) - 1

        while i >= 0 and s[i] == ' ':
            i -= 1

        length = 0

        while i >= 0 and s[i] != ' ':
            length += 1
            i -= 1

        return length


s = "Hello World   "

obj = Solution()

print(obj.lengthOfLastWord(s))
```

Output

```text
5
```

---

# Detailed Dry Run

Input

```python
s = "Hello World   "
```

### Step 1

Start

```text
Hello World___
             ↑
```

Skip spaces.

Pointer moves left until

```text
Hello World
          ↑
```

---

### Step 2

Count characters.

| Character | Length |
| --------- | -----: |
| d         |      1 |
| l         |      2 |
| r         |      3 |
| o         |      4 |
| W         |      5 |

Next character

```text
(space)
```

Stop.

Return

```python
5
```

---

# Dry Run Table

| Pointer | Character | Action | Length |
| ------: | --------- | ------ | -----: |
|     End | Space     | Skip   |      0 |
|   End-1 | Space     | Skip   |      0 |
|   End-2 | Space     | Skip   |      0 |
|      10 | d         | Count  |      1 |
|       9 | l         | Count  |      2 |
|       8 | r         | Count  |      3 |
|       7 | o         | Count  |      4 |
|       6 | W         | Count  |      5 |
|       5 | Space     | Stop   |      5 |

---

# Visual Understanding

```text
Hello World___
             ↑

Skip Spaces

↓

Hello World
          ↑

Count Backwards

d

↓

l

↓

r

↓

o

↓

W

↓

Space

↓

Answer = 5
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why scan from the end?

### Model Answer

> The problem only asks about the last word. Starting from the end lets us ignore everything before it and avoid tracking previous words.

---

## Q2. Why not use `split()`?

### Model Answer

> `split()` is valid but creates an additional list of words, using O(n) extra space. The reverse traversal solution achieves O(1) extra space.

---

## Q3. Why skip trailing spaces first?

### Model Answer

> The input may end with spaces. If we begin counting immediately, we would incorrectly count zero characters. Skipping trailing spaces ensures we start at the last word.

---

## Q4. What if the string contains only one word?

### Model Answer

Example:

```python
s = "Python"
```

There are no spaces to skip. We simply count every character and return `6`.

---

## Q5. What if the string ends immediately after the last word?

### Model Answer

> The first loop does nothing because there are no trailing spaces. The second loop directly counts the characters of the last word.

---

## Q6. What broader interview pattern does LC 58 teach?

### Model Answer

> LC 58 teaches the **Reverse Traversal Pattern**: when the required information is near the end of a string or array, scanning backward often simplifies the solution and avoids unnecessary work.

---

# Pattern Extraction

For **LC 58**, memorize this flow:

```text
Start From End

↓

Skip Spaces

↓

Count Letters

↓

Encounter Space?

↓

Return Length
```

---

# Master Template

```python
i = len(s) - 1

while i >= 0 and s[i] == ' ':
    i -= 1

length = 0

while i >= 0 and s[i] != ' ':
    length += 1
    i -= 1

return length
```

---

# String Mastery Progress

| Layer | Pattern           | Problem   | Status |
| ----: | ----------------- | --------- | :----: |
|     1 | Traversal         | **LC 58** |    ✅   |
|     1 | Two Pointers      | LC 344    |    ⬜   |
|     1 | Two Pointers      | LC 125    |    ⬜   |
|     2 | HashMap + Strings | LC 242    |    ✅   |
|     2 | HashMap + Strings | LC 387    |    ✅   |
|     2 | HashMap + Strings | LC 205    |    ✅   |
|     2 | HashMap + Strings | LC 290    |    ⬜   |
|     3 | Sliding Window    | LC 3      |    ⬜   |
|     3 | Sliding Window    | LC 424    |    ⬜   |
|     3 | Sliding Window    | LC 438    |    ⬜   |
|     3 | Sliding Window    | LC 567    |    ⬜   |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...  | Pattern               | Why?                         |
| ------------------ | --------------------- | ---------------------------- |
| Last element/word  | **Reverse Traversal** | Start where the answer is    |
| Reverse a string   | Two Pointers          | Swap from both ends          |
| Palindrome check   | Two Pointers          | Compare symmetric characters |
| Character counting | HashMap               | Frequency lookup             |
| Longest substring  | Sliding Window        | Maintain a dynamic range     |

## 💡 The One-Line Takeaway

> **Whenever the answer is naturally located at the end of a string (such as the last word, trailing digits, or suffix), scan from right to left. Reverse traversal often produces the simplest O(n), O(1)-space solution.**



# LC 344 — Reverse String ⭐⭐⭐⭐

**Pattern:** Two Pointers (In-Place Swapping)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐⭐ (Foundation of Two Pointers)

> **LC 344 is the "Hello World" of the Two Pointers pattern.**
>
> It teaches the most important Two Pointer idea:
>
> **Process two ends of a sequence simultaneously until they meet.**

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given a character array

```python
s = ["h","e","l","l","o"]
```

Reverse it **in-place**.

Output

```python
["o","l","l","e","h"]
```

Notice:

* Don't create another array.
* Modify the original array.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Reverse String
```

A senior engineer immediately thinks

```text
Need both ends

↓

Left Pointer

+

Right Pointer

↓

Swap

↓

Move Towards Center
```

The keyword **"in-place"** is the biggest clue.

---

# 3. Why Brute Force Isn't Ideal

One solution:

```python
s.reverse()
```

or

```python
s[:] = s[::-1]
```

Although correct, these solutions **hide the algorithm**.

Interviewers ask this problem to test whether you know the **Two Pointers** technique, not Python shortcuts.

---

# 4. The Key Observation

Example

```python
s = ["h","e","l","l","o"]
```

Initially

```text
L                 R

h   e   l   l   o
```

Swap

```text
o   e   l   l   h
```

Move pointers

```text
    L       R

o   e   l   l   h
```

Swap

```text
o   l   l   e   h
```

Pointers meet.

Done.

---

# 5. Why Two Pointers?

To reverse an array:

First element ↔ Last element

Second ↔ Second Last

Third ↔ Third Last

...

This naturally leads to

```text
Left Pointer

+

Right Pointer
```

---

# 6. Pointer Movement

Start

```text
left = 0

right = n-1
```

After every swap

```python
left += 1

right -= 1
```

Stop when

```python
left >= right
```

---

# 7. Recognition Signals

Whenever you see

```text
Reverse

Palindrome

Mirror

Symmetric

Swap Ends
```

Think

```text
Two Pointers
```

---

# 8. Complexity

Each swap fixes two characters.

Total swaps

[
\frac{n}{2}
]

Time

[
O(n)
]

Space

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def reverseString(self, s):

        left = 0
        right = len(s) - 1

        while left < right:

            s[left], s[right] = s[right], s[left]

            left += 1
            right -= 1
```

---

## Time Complexity

[
O(n)
]

Every character is swapped at most once.

---

## Space Complexity

[
O(1)
]

The reversal is performed in-place.

---

## Interview Justification

> I use two pointers, one starting at the beginning and the other at the end of the array. At each step, I swap the characters at these pointers and move them toward the center. Each character participates in at most one swap, giving O(n) time and O(1) extra space.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def reverseString(self, s):

        left = 0
        right = len(s) - 1

        while left < right:

            s[left], s[right] = s[right], s[left]

            left += 1
            right -= 1


s = ["h","e","l","l","o"]

obj = Solution()

obj.reverseString(s)

print(s)
```

Output

```text
['o', 'l', 'l', 'e', 'h']
```

---

# Detailed Dry Run

Input

```python
s = ["h","e","l","l","o"]
```

---

### Step 1

Pointers

```text
L                 R

h   e   l   l   o
```

Swap

```text
o   e   l   l   h
```

Move

```text
left = 1

right = 3
```

---

### Step 2

Pointers

```text
    L       R

o   e   l   l   h
```

Swap

```text
o   l   l   e   h
```

Move

```text
left = 2

right = 2
```

Pointers meet.

Stop.

---

# Dry Run Table

| Left | Right | Before Swap   | After Swap |
| ---: | ----: | ------------- | ---------- |
|    0 |     4 | `h ... o`     | `o ... h`  |
|    1 |     3 | `e ... l`     | `l ... e`  |
|    2 |     2 | Pointers Meet | Stop       |

---

# Visual Understanding

```text
Initial

L                 R

h   e   l   l   o

↓

Swap

o   e   l   l   h

↓

Move

    L       R

↓

Swap

o   l   l   e   h

↓

Pointers Meet

Done
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why use two pointers instead of another array?

### Model Answer

> The problem explicitly requires an in-place solution. Two pointers allow us to reverse the array without allocating additional memory, achieving O(1) extra space.

---

## Q2. Why stop when `left >= right`?

### Model Answer

> Once the pointers meet or cross, every required pair has already been swapped. Continuing beyond that point would either repeat work or undo previous swaps.

---

## Q3. How many swaps are performed?

### Model Answer

> Exactly `⌊n/2⌋` swaps, because each swap places two characters in their correct positions.

---

## Q4. What happens if the string length is odd?

### Model Answer

Example:

```python
["a","b","c","d","e"]
```

The middle character (`c`) remains unchanged because it is already in its correct position.

---

## Q5. Can this approach reverse arrays as well?

### Model Answer

> Yes. The Two Pointers pattern is independent of the data type. It works for arrays, lists, strings represented as character arrays, and many other sequential data structures.

---

## Q6. What broader interview pattern does LC 344 teach?

### Model Answer

> LC 344 teaches the **Opposite Direction Two Pointers Pattern**: start from both ends, process a pair of elements, then move inward. This pattern is fundamental for palindrome checking, array reversal, partitioning, and many string manipulation problems.

---

# Pattern Extraction

For **LC 344**, memorize this flow:

```text
Left Pointer

↓

Right Pointer

↓

Swap

↓

Move Inward

↓

Pointers Meet

↓

Done
```

---

# Master Template

```python
left = 0
right = len(data) - 1

while left < right:

    data[left], data[right] = data[right], data[left]

    left += 1
    right -= 1
```

---

# String Mastery Progress

| Layer | Pattern           | Problem    | Status |
| ----: | ----------------- | ---------- | :----: |
|     1 | Traversal         | LC 58      |    ✅   |
|     1 | **Two Pointers**  | **LC 344** |    ✅   |
|     1 | Two Pointers      | LC 125     |    ⬜   |
|     2 | HashMap + Strings | LC 242     |    ✅   |
|     2 | HashMap + Strings | LC 387     |    ✅   |
|     2 | HashMap + Strings | LC 205     |    ✅   |
|     2 | HashMap + Strings | LC 290     |    ⬜   |
|     3 | Sliding Window    | LC 3       |    ⬜   |
|     3 | Sliding Window    | LC 424     |    ⬜   |
|     3 | Sliding Window    | LC 438     |    ⬜   |
|     3 | Sliding Window    | LC 567     |    ⬜   |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...           | Pattern           | Why?                |
| --------------------------- | ----------------- | ------------------- |
| Reverse string/array        | **Two Pointers**  | Swap from both ends |
| Compare mirrored characters | **Two Pointers**  | Move inward         |
| Last element/word           | Reverse Traversal | Start from the end  |
| Character frequency         | HashMap           | Count occurrences   |
| Longest substring           | Sliding Window    | Dynamic window      |

## 💡 The One-Line Takeaway

> **Whenever a problem involves processing symmetric elements from both ends—such as reversing, palindrome checking, or mirrored comparisons—your first instinct should be the *Two Pointers* pattern.**

# LC 125 — Valid Palindrome ⭐⭐⭐⭐⭐

**Pattern:** Two Pointers + String Traversal (Skip Invalid Characters)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐⭐ (One of the Most Asked String Problems)

> **LC 125 is the first "real" Two Pointer interview problem.**
>
> Unlike LC 344, we don't simply swap characters.
>
> We must **ignore non-alphanumeric characters** and compare only meaningful characters.

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given

```python
s = "A man, a plan, a canal: Panama"
```

Return

```python
True
```

Because after removing punctuation and ignoring case:

```text
amanaplanacanalpanama
```

It reads the same forwards and backwards.

---

Example 2

```python
s = "race a car"
```

After cleaning:

```text
raceacar
```

Forward

```text
raceacar
```

Backward

```text
racaecar
```

Different.

Return

```python
False
```

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Valid Palindrome
```

A senior engineer immediately thinks

```text
Compare

First Character

↓

Last Character

↓

Move Towards Center

↓

Skip Invalid Characters
```

The important clue is

```text
Ignore punctuation

Ignore spaces

Ignore case
```

This tells us

```text
Two Pointers

+

Traversal
```

---

# 3. Why Brute Force Isn't Ideal

One approach

```python
clean = ""

for ch in s:
    if ch.isalnum():
        clean += ch.lower()

return clean == clean[::-1]
```

Works.

But

* Creates another string.
* Uses O(n) extra space.

Interviewers usually prefer

```text
In-place comparison

using

Two Pointers
```

---

# 4. The Key Observation

Input

```python
"A man, a plan, a canal: Panama"
```

Pointers

```text
L                                   R
A man, a plan, a canal: Panama
```

Compare

```text
A

↓

a
```

Equal after lowercase.

Move inward.

---

Next

```text
(space)
```

Skip.

---

Next

```text
m

↓

m
```

Equal.

Continue.

Eventually

Pointers meet.

Palindrome.

---

# 5. Skip Invalid Characters

Suppose

```python
s = "a,b"
```

Pointer

```text
a , b
  ↑
```

Comma

```text
Not alphanumeric
```

Ignore.

Move pointer.

This is the interview trick.

---

# 6. Why Lowercase?

Example

```python
"A"
```

and

```python
"a"
```

Should be considered equal.

Use

```python
lower()
```

before comparing.

---

# 7. Recognition Signals

Whenever you see

```text
Palindrome

Mirror

Symmetric

Ignore Spaces

Ignore Symbols
```

Think

```text
Two Pointers

+

Skip Characters
```

---

# 8. Complexity

Every character is visited at most once.

Time

[
O(n)
]

Space

[
O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def isPalindrome(self, s):

        left = 0
        right = len(s) - 1

        while left < right:

            while left < right and not s[left].isalnum():
                left += 1

            while left < right and not s[right].isalnum():
                right -= 1

            if s[left].lower() != s[right].lower():
                return False

            left += 1
            right -= 1

        return True
```

---

## Time Complexity

[
O(n)
]

Each pointer moves only forward or backward once.

---

## Space Complexity

[
O(1)
]

No extra string is created.

---

## Interview Justification

> I use two pointers starting from both ends of the string. Before comparing characters, I skip any non-alphanumeric characters and convert both characters to lowercase. If a mismatch is found, I immediately return `False`; otherwise, I continue until the pointers meet. This gives O(n) time and O(1) extra space.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def isPalindrome(self, s):

        left = 0
        right = len(s) - 1

        while left < right:

            while left < right and not s[left].isalnum():
                left += 1

            while left < right and not s[right].isalnum():
                right -= 1

            if s[left].lower() != s[right].lower():
                return False

            left += 1
            right -= 1

        return True


s = "A man, a plan, a canal: Panama"

obj = Solution()

print(obj.isPalindrome(s))
```

Output

```text
True
```

---

# Detailed Dry Run

Input

```python
"A man, a plan, a canal: Panama"
```

---

### Step 1

Pointers

```text
L                             R

A man, a plan, a canal: Panama
```

Compare

```text
A

↓

a
```

Lowercase

```text
a == a
```

Move inward.

---

### Step 2

Left

```text
(space)
```

Skip.

---

### Step 3

Compare

```text
m

↓

m
```

Equal.

Move.

---

### Step 4

Encounter

```text
,
```

Skip.

---

Continue until

```text
Left >= Right
```

Return

```python
True
```

---

# Dry Run Table

| Left Char     | Right Char | Action      |
| ------------- | ---------- | ----------- |
| A             | a          | Match       |
| Space         | —          | Skip        |
| m             | m          | Match       |
| Comma         | —          | Skip        |
| a             | a          | Match       |
| ...           | ...        | Continue    |
| Pointers Meet | —          | Return True |

---

# Visual Understanding

```text
A man, a plan, a canal: Panama

↓

Ignore

Spaces

Commas

Colon

↓

amanaplanacanalpanama

↓

L                 R

↓

Compare

↓

Move

↓

Pointers Meet

↓

Palindrome
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why use Two Pointers instead of creating a cleaned string?

### Model Answer

> Creating a cleaned string requires O(n) additional space. The Two Pointer approach performs comparisons directly on the original string while skipping invalid characters, reducing the extra space to O(1).

---

## Q2. Why do we skip non-alphanumeric characters?

### Model Answer

> The problem explicitly states that only letters and digits should be considered when checking whether the string is a palindrome. Spaces and punctuation should not affect the result.

---

## Q3. Why convert both characters to lowercase?

### Model Answer

> The comparison is case-insensitive. Converting both characters to lowercase ensures that `'A'` and `'a'` are treated as equal.

---

## Q4. What happens if the string contains only punctuation?

Example

```python
s = ".,,"
```

### Model Answer

> All characters are skipped, the pointers cross, and the algorithm returns `True`. An empty string after filtering is considered a valid palindrome.

---

## Q5. Why is the algorithm O(n)?

### Model Answer

> Although there are nested `while` loops, each pointer moves only in one direction and never revisits a character. Therefore, every character is processed at most once.

---

## Q6. What broader interview pattern does LC 125 teach?

### Model Answer

> LC 125 teaches the **Filtered Two Pointers Pattern**: maintain two pointers from opposite ends while skipping characters that do not satisfy a condition. This technique appears in many string-processing problems.

---

# Pattern Extraction

For **LC 125**, memorize this flow:

```text
Left Pointer

↓

Skip Invalid

↓

Right Pointer

↓

Skip Invalid

↓

Lowercase Compare

↓

Mismatch?

↓

False

↓

Move Inward

↓

Pointers Meet

↓

True
```

---

# Master Template

```python
left = 0
right = len(s) - 1

while left < right:

    while left < right and not valid(left):
        left += 1

    while left < right and not valid(right):
        right -= 1

    if process(s[left]) != process(s[right]):
        return False

    left += 1
    right -= 1

return True
```

---

# String Mastery Progress

| Layer | Pattern                      | Problem    | Status |
| ----: | ---------------------------- | ---------- | :----: |
|     1 | Traversal                    | LC 58      |    ✅   |
|     1 | Two Pointers                 | LC 344     |    ✅   |
|     1 | **Two Pointers + Filtering** | **LC 125** |    ✅   |
|     2 | HashMap + Strings            | LC 242     |    ✅   |
|     2 | HashMap + Strings            | LC 387     |    ✅   |
|     2 | HashMap + Strings            | LC 205     |    ✅   |
|     2 | HashMap + Strings            | LC 290     |    ⬜   |
|     3 | Sliding Window               | LC 3       |    ⬜   |
|     3 | Sliding Window               | LC 424     |    ⬜   |
|     3 | Sliding Window               | LC 438     |    ⬜   |
|     3 | Sliding Window               | LC 567     |    ⬜   |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...   | Pattern                   | Why?                                       |
| ------------------- | ------------------------- | ------------------------------------------ |
| Reverse string      | Two Pointers              | Swap from both ends                        |
| Palindrome          | **Filtered Two Pointers** | Compare while skipping unwanted characters |
| Last word           | Reverse Traversal         | Start from the end                         |
| Character frequency | HashMap                   | Count occurrences                          |
| Longest substring   | Sliding Window            | Dynamic window                             |

## 💡 The One-Line Takeaway

> **Whenever you need to compare characters from both ends while ignoring certain characters (spaces, punctuation, etc.), use the *Filtered Two Pointers* pattern: skip invalid characters, normalize the valid ones, then compare.**
# LC 290 — Word Pattern ⭐⭐⭐⭐⭐

**Pattern:** Two HashMaps (Bidirectional Mapping: Pattern → Word)
**Difficulty:** Easy
**Interview Importance:** ⭐⭐⭐⭐⭐ (Very Common HashMap Interview Pattern)

> **LC 290 is the word-level extension of LC 205 (Isomorphic Strings).**
>
> **LC 205:** Character ↔ Character Mapping
>
> **LC 290:** Pattern Character ↔ Word Mapping
>
> If you understand LC 205, LC 290 becomes almost identical.

---

# 🔹 Block 1: Senior Insights

# 1. Problem Statement Simplified

Given:

```python
pattern = "abba"

s = "dog cat cat dog"
```

Return

```python
True
```

Because the mapping is

```text
a → dog

b → cat
```

Every occurrence follows the same mapping.

---

Example 2

```python
pattern = "abba"

s = "dog cat cat fish"
```

Return

```python
False
```

Because

```text
a → dog

Last 'a'

↓

fish ❌
```

Mapping changes.

---

Example 3

```python
pattern = "abba"

s = "dog dog dog dog"
```

Return

```python
False
```

Because

```text
a → dog

b → dog ❌
```

Two pattern characters map to the same word.

---

# 2. Hidden Translation (Senior Engineer Thinking)

The interviewer says

```text
Word Pattern
```

A senior engineer immediately thinks

```text
One-to-One Mapping

Pattern Character

↓

Word

AND

Word

↓

Pattern Character
```

This is exactly

```text
LC 205

but

Characters

↓

Words
```

---

# 3. First Observation

The string

```python
"dog cat cat dog"
```

must first become

```python
["dog","cat","cat","dog"]
```

So the very first step is

```python
words = s.split()
```

Now the problem becomes

```text
Character

↓

Word
```

instead of

```text
Character

↓

Character
```

---

# 4. Why Check Length First?

Example

```python
pattern = "abba"
```

Length

```text
4
```

Words

```python
["dog","cat"]
```

Length

```text
2
```

Impossible.

Immediately

```python
False
```

---

# 5. Why Two HashMaps?

Forward Map

```text
Pattern

↓

Word
```

Example

```python
{
'a':"dog",

'b':"cat"
}
```

Reverse Map

```text
Word

↓

Pattern
```

Example

```python
{
"dog":'a',

"cat":'b'
}
```

Both maps must stay consistent.

---

# 6. Step-by-Step Example

Input

```python
pattern = "abba"

words = ["dog","cat","cat","dog"]
```

---

Read

```text
a

↓

dog
```

Store

```text
a → dog

dog → a
```

---

Read

```text
b

↓

cat
```

Store

```text
b → cat

cat → b
```

---

Read

```text
b

↓

cat
```

Already mapped correctly.

Continue.

---

Read

```text
a

↓

dog
```

Already mapped.

Return

```python
True
```

---

# 7. Recognition Signals

Whenever you see

```text
Pattern

Mapping

Replacement

Dictionary

One-to-One

Words
```

Think

```text
Two HashMaps
```

---

# 8. Complexity

Split

[
O(n)
]

Traversal

[
O(n)
]

Overall

[
O(n)
]

Space

Two HashMaps

[
O(k)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def wordPattern(self, pattern, s):

        words = s.split()

        if len(pattern) != len(words):
            return False

        char_to_word = {}
        word_to_char = {}

        for ch, word in zip(pattern, words):

            if ch in char_to_word:

                if char_to_word[ch] != word:
                    return False

            else:
                char_to_word[ch] = word

            if word in word_to_char:

                if word_to_char[word] != ch:
                    return False

            else:
                word_to_char[word] = ch

        return True
```

---

## Time Complexity

[
O(n)
]

Each pattern character and word pair is processed once.

---

## Space Complexity

[
O(k)
]

where `k` is the number of unique pattern characters and words.

---

## Interview Justification

> I first split the input string into words and verify that the number of words matches the pattern length. Then I maintain two HashMaps: one mapping pattern characters to words and another mapping words back to pattern characters. This bidirectional mapping guarantees a one-to-one correspondence and detects any conflict immediately.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def wordPattern(self, pattern, s):

        words = s.split()

        if len(pattern) != len(words):
            return False

        char_to_word = {}
        word_to_char = {}

        for ch, word in zip(pattern, words):

            if ch in char_to_word:

                if char_to_word[ch] != word:
                    return False

            else:
                char_to_word[ch] = word

            if word in word_to_char:

                if word_to_char[word] != ch:
                    return False

            else:
                word_to_char[word] = ch

        return True


pattern = "abba"

s = "dog cat cat dog"

obj = Solution()

print(obj.wordPattern(pattern, s))
```

Output

```text
True
```

---

# Detailed Dry Run

Input

```python
pattern = "abba"

words = ["dog","cat","cat","dog"]
```

Initial

```text
char_to_word = {}

word_to_char = {}
```

---

### Step 1

Pattern

```text
a
```

Word

```text
dog
```

Store

```text
a → dog

dog → a
```

---

### Step 2

Pattern

```text
b
```

Word

```text
cat
```

Store

```text
b → cat

cat → b
```

---

### Step 3

Pattern

```text
b
```

Word

```text
cat
```

Already mapped.

Continue.

---

### Step 4

Pattern

```text
a
```

Word

```text
dog
```

Already mapped.

Return

```python
True
```

---

# Dry Run Table

| Pattern | Word | Forward Map    | Reverse Map    | Valid? |
| ------- | ---- | -------------- | -------------- | :----: |
| a       | dog  | a→dog          | dog→a          |    ✅   |
| b       | cat  | b→cat          | cat→b          |    ✅   |
| b       | cat  | Already Exists | Already Exists |    ✅   |
| a       | dog  | Already Exists | Already Exists |    ✅   |

---

# Visual Understanding

```text
Pattern

a   b   b   a

↓

Words

dog cat cat dog

↓

Forward Map

a → dog

b → cat

↓

Reverse Map

dog → a

cat → b

↓

No Conflicts

↓

True
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why do we need two HashMaps?

### Model Answer

> One HashMap only ensures that each pattern character maps consistently to a word. It does not prevent two different pattern characters from mapping to the same word. The second HashMap enforces the reverse mapping, guaranteeing a true one-to-one relationship.

---

## Q2. Why split the string first?

### Model Answer

> The input string contains words separated by spaces. Splitting converts it into a list of words so that each pattern character can be matched with one corresponding word.

---

## Q3. Why compare the lengths before processing?

### Model Answer

> Each pattern character must correspond to exactly one word. If the counts differ, a valid mapping is impossible.

---

## Q4. How is LC 290 different from LC 205?

### Model Answer

> The underlying algorithm is identical. LC 205 maps **character → character**, whereas LC 290 maps **character → word**. Both require bidirectional HashMaps to enforce one-to-one mappings.

---

## Q5. Can we solve this using one HashMap?

### Model Answer

> No. A single forward map cannot detect when two different pattern characters map to the same word. The reverse map is required to detect that conflict.

---

## Q6. What broader interview pattern does LC 290 teach?

### Model Answer

> LC 290 reinforces the **Bidirectional Mapping Pattern**. Whenever two sets of objects must correspond uniquely—characters to words, IDs to names, or symbols to values—two HashMaps are the safest and cleanest solution.

---

# Pattern Extraction

For **LC 290**, memorize:

```text
Split String

↓

Length Match?

↓

NO

↓

False

↓

YES

↓

Pattern Character

↓

Word

↓

Forward Mapping Valid?

↓

Reverse Mapping Valid?

↓

Store Both

↓

Continue

↓

True
```

---

# Master Template

```python
items = s.split()

if len(pattern) != len(items):
    return False

forward = {}
reverse = {}

for a, b in zip(pattern, items):

    if a in forward and forward[a] != b:
        return False

    if b in reverse and reverse[b] != a:
        return False

    forward[a] = b
    reverse[b] = a

return True
```

---

# String Mastery Progress

| Layer | Pattern                             | Problem    | Status |
| ----: | ----------------------------------- | ---------- | :----: |
|     1 | Traversal                           | LC 58      |    ✅   |
|     1 | Two Pointers                        | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering            | LC 125     |    ✅   |
|     2 | HashMap + Strings                   | LC 242     |    ✅   |
|     2 | HashMap + Strings                   | LC 387     |    ✅   |
|     2 | HashMap + Strings                   | LC 205     |    ✅   |
|     2 | **Two HashMaps (Character → Word)** | **LC 290** |    ✅   |
|     3 | Sliding Window                      | LC 3       |    ⬜   |
|     3 | Sliding Window                      | LC 424     |    ⬜   |
|     3 | Sliding Window                      | LC 438     |    ⬜   |
|     3 | Sliding Window                      | LC 567     |    ⬜   |

---

# 🎯 Senior Pattern Recognition Summary

| Interview asks...             | Pattern          | Why?                      |
| ----------------------------- | ---------------- | ------------------------- |
| Character ↔ Character mapping | Two HashMaps     | Bidirectional consistency |
| Character ↔ Word mapping      | **Two HashMaps** | One-to-one relationship   |
| Frequency counting            | HashMap          | Count occurrences         |
| Duplicate detection           | HashSet          | Fast membership lookup    |
| Group equivalent strings      | HashMap of Lists | Canonical key grouping    |

## 💡 The One-Line Takeaway

> **Whenever a problem requires a unique relationship between two different domains (such as characters ↔ words), use *two HashMaps* to enforce a true one-to-one mapping in both directions.**


# Layer 3 Sliding Window

# LC 3 — Longest Substring Without Repeating Characters ⭐⭐⭐⭐⭐

**Pattern:** Variable Sliding Window + HashSet
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐ — one of the most important Sliding Window problems.

> **LC 3 is the fundamental problem for learning variable-size Sliding Window.**
>
> The core idea is:
>
> **Expand the window while it is valid. When it becomes invalid, shrink it until it becomes valid again.**

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement

Given a string `s`, find the length of the **longest substring without repeating characters**.

Example:

```python
s = "abcabcbb"
```

Longest valid substrings include:

```text
"abc"
```

Length:

```text
3
```

So:

```text
Answer = 3
```

Another example:

```python
s = "bbbbb"
```

Longest substring:

```text
"b"
```

Answer:

```text
1
```

---

# 2. First Important Distinction: Substring ≠ Subsequence

This matters in interviews.

### Substring

Characters must be **contiguous**.

```text
abc
```

is a substring of:

```text
zabcxy
```

### Subsequence

Characters don't need to be adjacent.

For:

```text
abcde
```

`ace` is a subsequence, but not a substring.

LC 3 specifically asks for a **substring**.

---

# 3. Hidden Translation

The interviewer says:

> Find the longest substring without repeating characters.

Senior translation:

```text
Need a contiguous range

↓

Need longest valid range

↓

Maintain a window

↓

Window must contain unique characters

↓

Sliding Window
```

The key question becomes:

> **How do I maintain a window that never contains duplicates?**

Use a HashSet.

---

# 4. Why Brute Force Is Bad

A brute-force approach generates every possible substring.

For example:

```text
a
ab
abc
abca
...

b
bc
bca
...
```

There are approximately:

[
O(n^2)
]

substrings.

Checking each substring for duplicates can make the solution:

[
O(n^2)
]

or worse depending on implementation.

We can do better.

---

# 5. The Sliding Window

For:

```python
s = "abcabcbb"
```

Start:

```text
L
↓
a b c a b c b b
```

Window:

```text
"a"
```

Valid.

Expand:

```text
a b
```

Valid.

Expand:

```text
a b c
```

Valid.

Now next character:

```text
a
```

would create:

```text
a b c a
```

Invalid because `a` already exists.

So we shrink from the left.

---

# 6. The Most Important Sliding Window Rule

There are always two operations:

### Expand

Move `right`.

```text
right += 1
```

### Shrink

Move `left`.

```text
left += 1
```

The invariant is:

```text
Window always contains unique characters.
```

---

# 7. The Senior Engineer Mindset

Don't think:

> "How do I find the longest substring?"

Think:

> **"What condition makes my current window invalid?"**

Here:

```text
Invalid condition:

duplicate character exists
```

Therefore:

```text
while duplicate:
    shrink window
```

Then:

```text
update maximum
```

That's the reusable Sliding Window framework.

---

# 8. Why HashSet?

We need to quickly answer:

> "Is this character already inside the current window?"

HashSet gives average:

[
O(1)
]

membership testing.

So:

```python
if s[right] in window:
```

is efficient.

---

# 9. Recognition Signals

When you see:

```text
Longest substring
Longest contiguous sequence
No duplicates
At most K
At least K
Distinct characters
```

Think:

```text
Sliding Window
```

Then identify the window state:

```text
Need uniqueness?

↓

HashSet
```

---

# 10. Complexity

Both pointers only move forward.

`right` moves at most `n` times.

`left` also moves at most `n` times.

Therefore:

[
O(n+n)=O(n)
]

Space:

The HashSet contains characters inside the current window.

[
O(k)
]

where `k` is the number of distinct characters.

For a fixed ASCII character set, this can be considered `O(1)`, but the safer interview answer is **O(min(n, character-set-size))**.

---

# 🔹 Block 2: Efficient Code

## Best Clean Python Solution

```python
class Solution:
    def lengthOfLongestSubstring(self, s):

        window = set()

        left = 0
        longest = 0

        for right in range(len(s)):

            while s[right] in window:
                window.remove(s[left])
                left += 1

            window.add(s[right])

            longest = max(longest, right - left + 1)

        return longest
```

---

## Complexity

### Time

[
O(n)
]

Why?

Each character is:

* added to the set at most once
* removed from the set at most once

So the total number of operations is linear.

### Space

[
O(k)
]

where `k` is the number of distinct characters in the current window.

---

## Interview Complexity Explanation

Say this:

> "The right pointer visits each character once, and although the left pointer moves inside the while loop, each character can be removed only once. Therefore, both pointers together perform O(n) work. The HashSet stores the characters currently inside the window, requiring O(k) space."

That's a much better explanation than simply saying "there are two loops, so O(n²)." The nested loop does **not** automatically make an algorithm quadratic.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def lengthOfLongestSubstring(self, s):

        window = set()

        left = 0
        longest = 0

        for right in range(len(s)):

            while s[right] in window:
                window.remove(s[left])
                left += 1

            window.add(s[right])

            longest = max(longest, right - left + 1)

        return longest


# Example
s = "abcabcbb"

obj = Solution()

answer = obj.lengthOfLongestSubstring(s)

print("Input :", s)
print("Output:", answer)
```

Output:

```text
Input : abcabcbb
Output: 3
```

---

# Detailed Dry Run

Input:

```text
abcabcbb
```

Initial:

```text
left = 0
longest = 0
window = {}
```

---

## Step 1 — `right = 0`

Character:

```text
a
```

Not in window.

Add:

```text
{a}
```

Window:

```text
[a]
```

Length:

```text
1
```

Longest:

```text
1
```

---

## Step 2 — `right = 1`

Character:

```text
b
```

Not in window.

Add:

```text
{a,b}
```

Window:

```text
[a b]
```

Length:

```text
2
```

Longest:

```text
2
```

---

## Step 3 — `right = 2`

Character:

```text
c
```

Not in window.

Add:

```text
{a,b,c}
```

Window:

```text
[a b c]
```

Length:

```text
3
```

Longest:

```text
3
```

---

## Step 4 — `right = 3`

Character:

```text
a
```

But:

```text
a ∈ window
```

Duplicate!

Current window:

```text
[a b c]
```

We must shrink.

Remove:

```text
a
```

Move:

```text
left = 1
```

Window:

```text
[b c]
```

Now `a` is no longer present.

Add `a`:

```text
[b c a]
```

Current length:

```text
3
```

Longest remains:

```text
3
```

---

## Step 5 — `right = 4`

Character:

```text
b
```

Duplicate.

Current:

```text
[b c a]
```

Remove from left:

```text
b
```

Move:

```text
left = 2
```

Window:

```text
[c a]
```

Add `b`:

```text
[c a b]
```

Length:

```text
3
```

---

## Step 6 — `right = 5`

Character:

```text
c
```

Duplicate.

Remove:

```text
c
```

Move:

```text
left = 3
```

Window:

```text
[a b]
```

Add:

```text
c
```

Window:

```text
[a b c]
```

Length:

```text
3
```

---

## Step 7 — `right = 6`

Character:

```text
b
```

Duplicate.

Current:

```text
[a b c]
```

Remove:

```text
a
```

```text
left = 4
```

Window:

```text
[b c]
```

Still contains `b`.

Remove:

```text
b
```

```text
left = 5
```

Window:

```text
[c]
```

Now add `b`:

```text
[c b]
```

Length:

```text
2
```

Longest remains:

```text
3
```

---

## Step 8 — `right = 7`

Character:

```text
b
```

Duplicate.

Remove:

```text
c
```

```text
left = 6
```

Window:

```text
[b]
```

Still duplicate `b`.

Remove:

```text
b
```

```text
left = 7
```

Window:

```text
{}
```

Add new `b`:

```text
{b}
```

Length:

```text
1
```

Final answer:

```text
3
```

---

# Dry Run Table

| Right | Char | Action                | Window        | Length | Best |
| ----: | ---- | --------------------- | ------------- | -----: | ---: |
|     0 | a    | Add                   | `abc` → `[a]` |      1 |    1 |
|     1 | b    | Add                   | `[ab]`        |      2 |    2 |
|     2 | c    | Add                   | `[abc]`       |      3 |    3 |
|     3 | a    | Remove `a`, add `a`   | `[bca]`       |      3 |    3 |
|     4 | b    | Remove `b`, add `b`   | `[cab]`       |      3 |    3 |
|     5 | c    | Remove `c`, add `c`   | `[abc]`       |      3 |    3 |
|     6 | b    | Shrink twice, add `b` | `[cb]`        |      2 |    3 |
|     7 | b    | Shrink twice, add `b` | `[b]`         |      1 |    3 |

Answer:

```text
3
```

---

# The Critical Invariant

This is what you should remember for interviews:

```text
┌───────────────────────────────┐
│ Current window has NO duplicate │
└───────────────────────────────┘
```

Whenever adding `s[right]` violates that rule:

```text
while duplicate:
    remove from left
```

Once valid again:

```text
update answer
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is this Sliding Window?

### Model Answer

> We maintain a contiguous range `[left, right]` representing the current substring. The right pointer expands the window, while the left pointer contracts it whenever the uniqueness constraint is violated. This is the variable-size Sliding Window pattern.

---

## Q2. Why do we use a `while` loop instead of an `if`?

### Model Answer

> A single removal may not be enough to eliminate the duplicate. We need to keep shrinking from the left until the incoming character no longer exists in the window. Therefore, `while` is required.

Example:

```text
window = "abc"
incoming = "b"
```

We may need to remove:

```text
a
b
```

before `b` becomes available again.

---

## Q3. Why is the solution O(n) despite the nested `while` loop?

### Model Answer

> The right pointer moves from left to right once, and the left pointer also moves from left to right at most once across the entire algorithm. Each character is inserted and removed at most once, so the total work is O(n), not O(n²).

---

## Q4. Why can't we use a normal array instead of a HashSet?

### Model Answer

> We could use an array when the character set is known and bounded, such as ASCII. But a HashSet provides direct membership checking without relying on a fixed character range and keeps the implementation general.

---

## Q5. Can this problem be solved using a HashMap instead?

### Model Answer

> Yes, and there is an even more optimized variant. Instead of storing only whether a character exists, we store its latest index. Then when a duplicate appears, we can jump `left` directly instead of removing characters one by one.

For example:

```python
last_seen = {}

left = 0
answer = 0

for right, ch in enumerate(s):

    if ch in last_seen:
        left = max(left, last_seen[ch] + 1)

    last_seen[ch] = right

    answer = max(answer, right - left + 1)
```

This is also:

```text
Time:  O(n)
Space: O(k)
```

---

## Q6. Which implementation would you choose in an interview?

### Model Answer

> For teaching and pattern clarity, I would start with the HashSet window because the expand/shrink invariant is very explicit. If the interviewer asks for optimization, I would switch to the HashMap latest-index approach, which jumps the left pointer directly to the correct position.

---

# ⚡ Two Valid Solutions — Know Both

## Version 1 — HashSet

```text
Duplicate?

↓

Remove from left

↓

Until valid
```

Best for:

**Learning Sliding Window.**

---

## Version 2 — HashMap

```text
Duplicate?

↓

Jump left directly

↓

last_seen[ch] + 1
```

Best for:

**Interview optimization.**

---

# HashMap Version — Interview Master Solution

```python
class Solution:
    def lengthOfLongestSubstring(self, s):

        last_seen = {}

        left = 0
        longest = 0

        for right, ch in enumerate(s):

            if ch in last_seen:
                left = max(left, last_seen[ch] + 1)

            last_seen[ch] = right

            longest = max(longest, right - left + 1)

        return longest
```

### Complexity

```text
Time  → O(n)
Space → O(k)
```

### Why `max()` is critical

Consider:

```text
s = "abba"
```

When processing the final `a`, its previous occurrence is before the current window's left boundary.

You **must not move `left` backwards**.

Therefore:

```python
left = max(left, last_seen[ch] + 1)
```

not simply:

```python
left = last_seen[ch] + 1
```

That detail is a common interview trap.

---

# Pattern Extraction

For **LC 3**, memorize:

```text
Longest Valid Substring
        ↓
Sliding Window
        ↓
Maintain Window State
        ↓
Duplicate?
   ↙           ↘
 YES           NO
  ↓             ↓
Shrink       Expand
  ↓             ↓
Until valid
        ↓
Update maximum
```

---

# Master Template — Variable Sliding Window

```python
left = 0
state = ...
answer = 0

for right in range(len(s)):

    add(s[right])

    while window_is_invalid():

        remove(s[left])
        left += 1

    answer = max(answer, right - left + 1)

return answer
```

This template is far more important than memorizing LC 3 itself.

---

# String Mastery Progress

| Layer | Pattern                               | Problem  | Status |
| ----: | ------------------------------------- | -------- | :----: |
|     1 | Traversal                             | LC 58    |    ✅   |
|     1 | Two Pointers                          | LC 344   |    ✅   |
|     1 | Two Pointers + Filtering              | LC 125   |    ✅   |
|     2 | Frequency HashMap                     | LC 242   |    ✅   |
|     2 | Two-Pass Frequency                    | LC 387   |    ✅   |
|     2 | Bidirectional Mapping                 | LC 205   |    ✅   |
|     2 | Bidirectional Mapping                 | LC 290   |    ✅   |
|     3 | **Variable Sliding Window + HashSet** | **LC 3** |    ✅   |
|     3 | Sliding Window + Frequency            | LC 424   |    ⬜   |
|     3 | Fixed Sliding Window                  | LC 438   |    ⬜   |
|     3 | Fixed Sliding Window                  | LC 567   |    ⬜   |

---

# 🎯 Senior Pattern Recognition

| Signal                                   | Pattern                                       |
| ---------------------------------------- | --------------------------------------------- |
| Reverse                                  | Two Pointers                                  |
| Palindrome                               | Two Pointers + Filtering                      |
| Character frequency                      | HashMap                                       |
| Character mapping                        | Two HashMaps                                  |
| **Longest substring without duplicates** | **Variable Sliding Window + HashSet/HashMap** |
| Longest substring with ≤ K distinct      | Sliding Window + Frequency Map                |
| Minimum valid substring                  | Variable Sliding Window                       |
| Fixed-length substring                   | Fixed Sliding Window                          |

## 💡 One-Line Takeaway

> **LC 3 teaches the fundamental Sliding Window invariant: expand the right side, and whenever the window becomes invalid, shrink from the left until it becomes valid again.**

# LC 424 — Longest Repeating Character Replacement ⭐⭐⭐⭐⭐

**Pattern:** Sliding Window + Frequency Map
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐

> This is the **next logical step after LC 3**.
>
> LC 3 asks:
> **"Can I keep this window completely unique?"**
>
> LC 424 asks:
> **"Can I make this entire window the same character using at most `k` replacements?"**

The key upgrade is learning how to define a **window validity condition using frequency**.

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement

Given:

```python
s = "AABABBA"
k = 1
```

You can replace at most **1 character**.

The goal is to find the longest substring that can be converted into the same character.

Consider:

```text
A A B A B B A
```

Take:

```text
A A B A
```

There are:

```text
A → 3
B → 1
```

If we replace `B` with `A`:

```text
A A A A
```

Only **1 replacement**.

Therefore:

```text
Answer = 4
```

---

# 2. Hidden Translation

Don't think:

> "Which character should I replace?"

That's the wrong direction.

Think:

> **"For my current window, how many characters would I need to replace to make everything equal?"**

Suppose the window has:

```text
A → 3
B → 1
C → 1
```

Window size:

```text
5
```

Most frequent character:

```text
A = 3
```

Keep those 3.

Everything else must be replaced:

```text
5 - 3 = 2
```

Therefore:

[
\text{replacements needed}
==========================

## \text{window length}

\text{maximum frequency}
]

This is the **entire problem**.

---

# 3. Senior Pattern Recognition

The interviewer says:

> Longest substring where you can replace at most `k` characters.

Immediately translate:

```text
Longest
    ↓
Sliding Window

Substring
    ↓
Contiguous Window

Replacement allowed
    ↓
Frequency Map

At most k changes
    ↓
Window validity condition
```

Therefore:

```text
Sliding Window + Frequency Map
```

---

# 4. Window Validity Condition

For every window:

```text
window_length - max_frequency <= k
```

If:

```text
window_length - max_frequency <= k
```

the window is valid.

If:

```text
window_length - max_frequency > k
```

the window is invalid.

Then shrink from the left.

---

# 5. Example

```python
s = "AABABBA"
k = 1
```

Window:

```text
A A B A
```

Frequency:

```text
A → 3
B → 1
```

Length:

```text
4
```

Maximum frequency:

```text
3
```

Required replacements:

```text
4 - 3 = 1
```

Since:

```text
1 <= k
```

valid.

---

Now expand:

```text
A A B A B
```

Frequency:

```text
A → 3
B → 2
```

Length:

```text
5
```

Required replacements:

```text
5 - 3 = 2
```

But:

```text
2 > 1
```

Invalid.

So shrink.

---

# 6. The Critical Insight

You **do not need to decide which character to replace**.

You only need:

```text
maximum frequency
```

Why?

Because keeping the most frequent character minimizes replacements.

Example:

```text
A A A B C
```

Counts:

```text
A = 3
B = 1
C = 1
```

Keep `A`.

Replace:

```text
B → A
C → A
```

2 replacements.

Any other choice would require more.

---

# 7. Why Frequency Map?

We need to know:

```text
How many times does each character appear inside the window?
```

So maintain:

```python
freq = {}
```

Example:

```text
A → 3
B → 2
```

Then calculate:

```python
window_length - max_frequency
```

---

# 8. Recognition Signals

When you see:

```text
Longest substring
At most K replacements
At most K changes
Can replace
Can modify
Make all characters equal
```

Think:

```text
Sliding Window
+
Frequency Map
```

Then ask:

> **What makes my window invalid?**

For LC 424:

```text
window_size - max_frequency > k
```

---

# 9. Complexity

We scan the string once.

The left and right pointers each move forward at most `n` times.

Therefore:

[
O(n)
]

Space:

At most the number of distinct characters:

[
O(k)
]

For uppercase English letters, this is effectively:

[
O(26)=O(1)
]

---

# 🔹 Block 2: Efficient Code

```python
class Solution:
    def characterReplacement(self, s, k):

        freq = {}

        left = 0
        max_freq = 0
        longest = 0

        for right in range(len(s)):

            ch = s[right]
            freq[ch] = freq.get(ch, 0) + 1

            max_freq = max(max_freq, freq[ch])

            window_length = right - left + 1

            replacements = window_length - max_freq

            if replacements > k:
                freq[s[left]] -= 1
                left += 1

            longest = max(longest, right - left + 1)

        return longest
```

---

## Time Complexity

[
O(n)
]

Each character enters the window once and leaves at most once.

---

## Space Complexity

[
O(k)
]

For uppercase English letters:

[
O(26)=O(1)
]

---

## Interview Justification

> I maintain a sliding window and a frequency map. `max_freq` stores the highest character frequency seen in the current or previously processed windows. The number of replacements required is the window size minus `max_freq`. If that exceeds `k`, I shrink the window from the left. The largest valid window gives the answer.

---

# ⚠️ Important Interview Detail: `max_freq` Doesn't Decrease

You may notice something strange:

When we remove a character from the left, we don't decrease `max_freq`.

That is intentional.

For example:

```python
max_freq = max(max_freq, freq[ch])
```

only increases.

Why is this safe?

Because we're interested in finding the **maximum possible valid window length**. Keeping a historical upper bound for `max_freq` may temporarily make a window appear valid, but it cannot cause us to return an incorrect maximum.

This is a subtle but important optimization.

If the interviewer asks:

> "Why don't you recompute max frequency after shrinking?"

Answer:

> Recomputing it is unnecessary. A non-decreasing upper bound for the maximum frequency is sufficient for determining the maximum window length, and it keeps the algorithm linear.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def characterReplacement(self, s, k):

        freq = {}

        left = 0
        max_freq = 0
        longest = 0

        for right in range(len(s)):

            ch = s[right]

            # Add current character
            freq[ch] = freq.get(ch, 0) + 1

            # Track highest frequency
            max_freq = max(max_freq, freq[ch])

            # Current window size
            window_length = right - left + 1

            # Characters that must be replaced
            replacements = window_length - max_freq

            # Shrink if invalid
            if replacements > k:

                freq[s[left]] -= 1
                left += 1

            # Update answer
            longest = max(longest, right - left + 1)

        return longest


s = "AABABBA"
k = 1

obj = Solution()

print(obj.characterReplacement(s, k))
```

Output:

```text
4
```

---

# Detailed Dry Run

Input:

```text
s = "AABABBA"
k = 1
```

---

## Step 1

Character:

```text
A
```

Frequency:

```text
A → 1
```

Window:

```text
A
```

Size:

```text
1
```

Max frequency:

```text
1
```

Replacements:

```text
1 - 1 = 0
```

Valid.

Best:

```text
1
```

---

## Step 2

Character:

```text
A
```

Frequency:

```text
A → 2
```

Window:

```text
AA
```

Size:

```text
2
```

Max frequency:

```text
2
```

Replacements:

```text
2 - 2 = 0
```

Valid.

Best:

```text
2
```

---

## Step 3

Character:

```text
B
```

Frequency:

```text
A → 2
B → 1
```

Window:

```text
AAB
```

Size:

```text
3
```

Max frequency:

```text
2
```

Replacements:

```text
3 - 2 = 1
```

Since:

```text
1 <= k
```

valid.

Best:

```text
3
```

---

## Step 4

Character:

```text
A
```

Frequency:

```text
A → 3
B → 1
```

Window:

```text
AABA
```

Size:

```text
4
```

Max frequency:

```text
3
```

Replacements:

```text
4 - 3 = 1
```

Valid.

Best:

```text
4
```

---

## Step 5

Character:

```text
B
```

Frequency:

```text
A → 3
B → 2
```

Window:

```text
AABAB
```

Size:

```text
5
```

Max frequency:

```text
3
```

Replacements:

```text
5 - 3 = 2
```

But:

```text
2 > 1
```

Invalid.

Shrink from left.

Remove:

```text
A
```

New frequency:

```text
A → 2
B → 2
```

Move:

```text
left = 1
```

Window becomes:

```text
ABAB
```

Length:

```text
4
```

Best remains:

```text
4
```

---

## Step 6

Character:

```text
B
```

Frequency:

```text
A → 2
B → 3
```

Window:

```text
ABABB
```

Size:

```text
5
```

Historical `max_freq`:

```text
3
```

Required replacements:

```text
5 - 3 = 2
```

Invalid.

Shrink:

```text
A
```

Window:

```text
BABB
```

Length:

```text
4
```

Best:

```text
4
```

---

## Step 7

Character:

```text
A
```

Window:

```text
BABBA
```

Again:

```text
window size = 5
max_freq = 3
```

Required:

```text
5 - 3 = 2
```

Invalid.

Shrink:

```text
B
```

Window:

```text
ABBA
```

Length:

```text
4
```

Final:

```text
4
```

---

# Dry Run Table

| Right | Char | Window Conceptually | Max Freq | Window Size | Replacements | Action |  Best |
| ----: | ---- | ------------------- | -------: | ----------: | -----------: | ------ | ----: |
|     0 | A    | `A`                 |        1 |           1 |            0 | Keep   |     1 |
|     1 | A    | `AA`                |        2 |           2 |            0 | Keep   |     2 |
|     2 | B    | `AAB`               |        2 |           3 |            1 | Keep   |     3 |
|     3 | A    | `AABA`              |        3 |           4 |            1 | Keep   | **4** |
|     4 | B    | `AABAB`             |        3 |           5 |            2 | Shrink |     4 |
|     5 | B    | `ABABB`             |        3 |           5 |            2 | Shrink |     4 |
|     6 | A    | `BABBA`             |        3 |           5 |            2 | Shrink | **4** |

Answer:

```text
4
```

---

# Visual Understanding

```text
s = A A B A B B A
    ↑       ↑
   left    right
```

At:

```text
A A B A
```

we have:

```text
A → 3
B → 1
```

So:

```text
4 characters
-
3 already matching
=
1 replacement
```

Valid.

But:

```text
A A B A B
```

requires:

```text
5 - 3 = 2 replacements
```

and:

```text
k = 1
```

Therefore:

```text
INVALID
```

Shrink.

---

# 🔹 Block 4: Interview Q&A

## Q1. What is the key formula in LC 424?

### Model Answer

> The number of replacements required to make the current window contain one repeated character is the window length minus the frequency of the most common character in that window.

---

## Q2. Why do we subtract the maximum frequency?

### Model Answer

> We keep all occurrences of the most frequent character and replace every other character with it. Choosing the most frequent character minimizes the number of replacements.

---

## Q3. What makes the sliding window invalid?

### Model Answer

> The window is invalid when the number of required replacements exceeds `k`:
>
> `window_length - max_frequency > k`.

---

## Q4. Why do we use a frequency map instead of a HashSet?

### Model Answer

> LC 3 only needed to know whether a character existed, so a HashSet was sufficient. LC 424 needs to know how many times each character occurs because the maximum frequency determines how many replacements are required. Therefore, we need a frequency map.

---

## Q5. Why is this O(n) despite the shrinking step?

### Model Answer

> Both pointers only move forward. Every character enters the window once and leaves it at most once, so the total number of pointer movements is linear.

---

## Q6. Why don't we decrease `max_freq` when shrinking?

### Model Answer

> `max_freq` is maintained as a historical upper bound. Recomputing it after every shrink would add unnecessary work. Using the non-decreasing value still gives the correct maximum window length while preserving O(n) time.

---

# 🔥 LC 3 vs LC 424

This comparison is **extremely important** for interviews.

|                   | LC 3                                 | LC 424                                     |
| ----------------- | ------------------------------------ | ------------------------------------------ |
| Goal              | Longest substring without duplicates | Longest substring after ≤ `k` replacements |
| Window State      | Set                                  | Frequency Map                              |
| Invalid Condition | Duplicate exists                     | `window_size - max_freq > k`               |
| Shrink            | Remove until duplicate gone          | Shrink until replacements ≤ k              |
| Pattern           | Sliding Window                       | Sliding Window                             |
| Complexity        | O(n)                                 | O(n)                                       |

### The evolution:

```text
LC 3

Sliding Window
+
HashSet
+
"No duplicates"
        ↓
        ↓
LC 424
        ↓
Sliding Window
+
Frequency Map
+
"At most K replacements"
```

That's exactly why **LC 424 comes after LC 3** in your roadmap.

---

# 🧠 Master Sliding Window Template

```python
left = 0
answer = 0
state = {}

for right in range(len(s)):

    # Expand
    update_state(s[right])

    # Restore validity
    while window_is_invalid():

        remove_from_state(s[left])
        left += 1

    # Record best valid window
    answer = max(answer, right - left + 1)

return answer
```

For LC 424:

```python
window_is_invalid()
```

means:

```text
window_length - max_frequency > k
```

---

# String Mastery Progress

| Layer | Pattern                           | Problem    | Status |
| ----: | --------------------------------- | ---------- | :----: |
|     1 | Traversal                         | LC 58      |    ✅   |
|     1 | Two Pointers                      | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering          | LC 125     |    ✅   |
|     2 | Frequency HashMap                 | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                | LC 387     |    ✅   |
|     2 | Bidirectional Mapping             | LC 205     |    ✅   |
|     2 | Bidirectional Mapping             | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet | LC 3       |    ✅   |
|     3 | **Sliding Window + Frequency**    | **LC 424** |    ✅   |
|     3 | Fixed Sliding Window              | LC 438     |    ⬜   |
|     3 | Fixed Sliding Window              | LC 567     |    ⬜   |

---

# 🎯 Senior Pattern Recognition

| Problem Signal                              | Pattern                            |
| ------------------------------------------- | ---------------------------------- |
| Longest substring without duplicates        | Sliding Window + HashSet           |
| **Longest substring with ≤ K replacements** | **Sliding Window + Frequency Map** |
| Fixed-length substring                      | Fixed Sliding Window               |
| Find all anagrams                           | Fixed Window + Frequency           |
| Permutation inside string                   | Fixed Window + Frequency           |
| Minimum valid substring                     | Variable Sliding Window            |

## 💡 One-Line Takeaway

> **LC 424 teaches the real power of Sliding Window: don't ask which character to change—track the window's frequency distribution and use `window_size - max_frequency <= k` as your validity condition.**


# LC 438 — Find All Anagrams in a String ⭐⭐⭐⭐⭐

**Pattern:** Fixed Sliding Window + Frequency Map
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐

> **LC 438 is the problem that teaches you how to combine Sliding Window + Frequency Counting correctly.**
>
> You already learned:
>
> * **LC 3:** variable window + HashSet
> * **LC 424:** variable window + frequency map
>
> Now:
>
> **LC 438 = fixed-size window + frequency comparison.**
>
> The official problem asks for all starting indices where an anagram of `p` occurs in `s`. ([LeetCode][1])

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement Simplified

Given:

```python
s = "cbaebabacd"
p = "abc"
```

Find every substring of `s` that is an anagram of `p`.

Output:

```python
[0, 6]
```

Because:

```text
index 0 → "cba"
index 6 → "bac"
```

Both contain:

```text
a → 1
b → 1
c → 1
```

So both are anagrams of `"abc"`. ([LeetCode Wiki][2])

---

# 2. Senior Translation

Don't think:

> "Generate all anagrams of `p`."

That's a trap.

For:

```text
abc
```

there are:

```text
abc
acb
bac
bca
cab
cba
```

Generating permutations is completely unnecessary.

Instead ask:

> **What makes two strings anagrams?**

Answer:

```text
Same characters
+
Same frequencies
```

Therefore:

```text
Pattern p
   ↓
Frequency Map

Every window of size len(p)
   ↓
Frequency Map

Compare
   ↓
Equal?
   ↓
Anagram
```

---

# 3. Why Fixed Sliding Window?

This is the crucial difference from LC 3 and LC 424.

If:

```python
p = "abc"
```

then every anagram must contain exactly:

```text
3 characters
```

Therefore, we only need windows of size:

```text
len(p)
```

For:

```python
s = "cbaebabacd"
p = "abc"
```

we inspect:

```text
cba
bae
aeb
eba
bab
aba
bac
acd
```

Every window has exactly 3 characters.

That is a **Fixed Sliding Window**. ([NeetCode][3])

---

# 4. Why Not Sort Every Window?

You could do:

```python
sorted(window) == sorted(p)
```

For every window.

But if:

```text
n = len(s)
m = len(p)
```

you sort roughly `n` windows, each costing:

[
O(m\log m)
]

So:

[
O(nm\log m)
]

That's unnecessarily expensive.

---

# 5. Frequency Map Is the Real Solution

For:

```python
p = "abc"
```

we build:

```text
a → 1
b → 1
c → 1
```

Now inspect:

```text
cba
```

Its frequency is:

```text
c → 1
b → 1
a → 1
```

Same frequencies.

Therefore:

```text
Anagram ✓
```

---

# 6. The Fixed Window Movement

Suppose:

```text
s = "cbaebabacd"
p = "abc"
```

Initial window:

```text
c b a
↑   ↑
L   R
```

Frequency:

```text
a:1
b:1
c:1
```

Match → answer `0`.

Now slide one position:

```text
c b a e
  ↑   ↑
  L   R
```

Remove:

```text
c
```

Add:

```text
e
```

New window:

```text
b a e
```

No need to rebuild the frequency map.

Just:

```text
remove outgoing character
+
add incoming character
```

That's the essence of Sliding Window.

---

# 7. Recognition Signals

When the interviewer says:

```text
Find all anagrams

Find all permutations

Substring has same character counts

Fixed-length pattern

All starting indices
```

Think:

```text
Fixed Sliding Window
+
Frequency Map
```

---

# 8. Complexity

Let:

```text
n = len(s)
m = len(p)
```

We build the pattern frequency in:

[
O(m)
]

Then slide across `s`:

[
O(n)
]

Because each character enters and leaves the window at most once.

Therefore:

[
O(n+m)
]

Since `m <= n` in the useful case, this is commonly stated as:

[
O(n)
]

Space:

[
O(k)
]

where `k` is the number of distinct characters.

Because the problem guarantees lowercase English letters, a fixed array of size 26 gives:

[
O(1)
]

extra space. ([LeetCode Wiki][2])

---

# 🔹 Block 2: Efficient Code

Because LC 438 guarantees lowercase English letters, the **best interview implementation** is a 26-element frequency array.

```python
class Solution:
    def findAnagrams(self, s, p):

        if len(p) > len(s):
            return []

        result = []

        pattern_count = [0] * 26
        window_count = [0] * 26

        # Frequency of p
        for ch in p:
            pattern_count[ord(ch) - ord('a')] += 1

        window_size = len(p)

        # Build first window
        for i in range(window_size):
            index = ord(s[i]) - ord('a')
            window_count[index] += 1

        # Check first window
        if window_count == pattern_count:
            result.append(0)

        # Slide the window
        for right in range(window_size, len(s)):

            # Add incoming character
            index = ord(s[right]) - ord('a')
            window_count[index] += 1

            # Remove outgoing character
            left = right - window_size
            index = ord(s[left]) - ord('a')
            window_count[index] -= 1

            # Check current window
            if window_count == pattern_count:
                result.append(left + 1)

        return result
```

### Complexity

```text
Time  → O(n)
Space → O(1)
```

The arrays always contain exactly 26 positions.

### Interview Justification

> I create a frequency array for the pattern and maintain another frequency array for a fixed-size window in `s`. When the window moves, I add the incoming character and remove the outgoing character instead of recomputing frequencies. Whenever both frequency arrays match, the current window is an anagram of `p`.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def findAnagrams(self, s, p):

        if len(p) > len(s):
            return []

        result = []

        pattern_count = [0] * 26
        window_count = [0] * 26

        # Count characters in p
        for ch in p:
            pattern_count[ord(ch) - ord('a')] += 1

        window_size = len(p)

        # First window
        for i in range(window_size):
            index = ord(s[i]) - ord('a')
            window_count[index] += 1

        # Check first window
        if window_count == pattern_count:
            result.append(0)

        # Slide window
        for right in range(window_size, len(s)):

            # Add new character
            index = ord(s[right]) - ord('a')
            window_count[index] += 1

            # Remove old character
            left = right - window_size
            index = ord(s[left]) - ord('a')
            window_count[index] -= 1

            # Check anagram
            if window_count == pattern_count:
                result.append(left + 1)

        return result


s = "cbaebabacd"
p = "abc"

obj = Solution()

print(obj.findAnagrams(s, p))
```

Output:

```text
[0, 6]
```

---

# Detailed Dry Run

Input:

```text
s = "cbaebabacd"
p = "abc"
```

Pattern frequency:

```text
a → 1
b → 1
c → 1
```

---

## Window 1

```text
c b a
```

Frequency:

```text
a → 1
b → 1
c → 1
```

Matches `p`.

Therefore:

```text
result = [0]
```

---

## Slide 1

Remove:

```text
c
```

Add:

```text
e
```

Window:

```text
b a e
```

Frequency:

```text
a → 1
b → 1
e → 1
```

Not equal.

---

## Slide 2

Remove:

```text
b
```

Add:

```text
b
```

Window:

```text
a e b
```

Frequency:

```text
a → 1
b → 1
e → 1
```

Not equal.

---

## Slide 3

Remove:

```text
a
```

Add:

```text
a
```

Window:

```text
e b a
```

Still:

```text
a → 1
b → 1
e → 1
```

Not equal.

---

## Slide 4

Remove:

```text
e
```

Add:

```text
b
```

Window:

```text
b a b
```

Frequency:

```text
a → 1
b → 2
```

Not equal.

---

## Continue...

Eventually:

```text
b a c
```

appears at index `6`.

Frequency:

```text
a → 1
b → 1
c → 1
```

Matches.

Therefore:

```text
result = [0, 6]
```

---

# Dry Run Table

| Window Start | Window | Frequency       | Anagram? |
| -----------: | ------ | --------------- | :------: |
|            0 | `cba`  | `{a:1,b:1,c:1}` |     ✅    |
|            1 | `bae`  | `{a:1,b:1,e:1}` |     ❌    |
|            2 | `aeb`  | `{a:1,b:1,e:1}` |     ❌    |
|            3 | `eba`  | `{a:1,b:1,e:1}` |     ❌    |
|            4 | `bab`  | `{a:1,b:2}`     |     ❌    |
|            5 | `aba`  | `{a:2,b:1}`     |     ❌    |
|            6 | `bac`  | `{a:1,b:1,c:1}` |     ✅    |
|            7 | `acd`  | `{a:1,c:1,d:1}` |     ❌    |

Answer:

```text
[0, 6]
```

---

# Visual Understanding

```text
p = "abc"

Frequency:

a → 1
b → 1
c → 1
```

Now slide over `s`:

```text
[c b a] e b a b a c d
   ✓
   index 0


c [b a e] b a b a c d
     ✗


c b a e [b a c] d
         ✓
         index 6
```

The window always has exactly:

```text
len(p) = 3
```

characters.

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is LC 438 a fixed-size Sliding Window?

### Model Answer

> Every anagram of `p` must contain exactly the same number of characters as `p`. Therefore, every candidate substring must have length `len(p)`, so the window size remains fixed.

---

## Q2. Why do we compare frequencies instead of sorting?

### Model Answer

> Anagrams are defined by identical character frequencies, not character order. Maintaining frequencies lets us update the window incrementally instead of sorting every substring.

---

## Q3. Why remove one character and add one character when sliding?

### Model Answer

> When the window moves one position to the right, exactly one character leaves the window and exactly one new character enters. Updating those two frequencies is enough; rebuilding the entire frequency map would waste work.

---

## Q4. Why can we use an array of size 26?

### Model Answer

> The problem guarantees that `s` and `p` contain only lowercase English letters. Therefore, every character maps directly to one of 26 positions, giving constant auxiliary space.

---

## Q5. What is the difference between LC 438 and LC 424?

### Model Answer

> LC 424 uses a **variable-size window** and asks for the longest valid window. LC 438 uses a **fixed-size window** because every candidate anagram must have exactly the same length as `p`.

---

## Q6. What is the difference between LC 438 and LC 567?

### Model Answer

> Both use the same core fixed-window frequency technique. LC 567 asks whether at least one permutation exists, so it can return a boolean. LC 438 asks for **all starting positions**, so we continue sliding and collect every matching index.

---

# 🔥 LC 3 → LC 424 → LC 438

This progression is important for your pattern mastery.

| Problem    | Window    | State             | Validity                      |
| ---------- | --------- | ----------------- | ----------------------------- |
| **LC 3**   | Variable  | HashSet           | No duplicates                 |
| **LC 424** | Variable  | Frequency Map     | Replacements ≤ `k`            |
| **LC 438** | **Fixed** | **Frequency Map** | Frequencies exactly match `p` |
| LC 567     | Fixed     | Frequency Map     | Frequencies exactly match `p` |

So don't memorize LC 438 as an isolated problem.

Understand the progression:

```text
LC 3
│
├── Variable Window
├── HashSet
└── Remove until unique
       ↓
LC 424
│
├── Variable Window
├── Frequency Map
└── Shrink when replacements > k
       ↓
LC 438
│
├── Fixed Window
├── Frequency Map
└── Record every exact frequency match
```

---

# ⚡ Master Fixed Sliding Window Template

This is what you should actually memorize:

```python
window_size = len(pattern)

# Build target frequency
target = ...

# Build first window
window = ...

# Check first window

for right in range(window_size, len(s)):

    # Add incoming
    add(s[right])

    # Remove outgoing
    left = right - window_size
    remove(s[left])

    # Check current window
```

The template appears repeatedly in:

* **LC 438 — Find All Anagrams**
* **LC 567 — Permutation in String**
* LC 1456 — Maximum Number of Vowels
* Other fixed-length substring problems

---

# String Mastery Progress

| Layer | Pattern                              | Problem    | Status |
| ----: | ------------------------------------ | ---------- | :----: |
|     1 | Traversal                            | LC 58      |    ✅   |
|     1 | Two Pointers                         | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering             | LC 125     |    ✅   |
|     2 | Frequency HashMap                    | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                   | LC 387     |    ✅   |
|     2 | Bidirectional Mapping                | LC 205     |    ✅   |
|     2 | Bidirectional Mapping                | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet    | LC 3       |    ✅   |
|     3 | Sliding Window + Frequency           | LC 424     |    ✅   |
|     3 | **Fixed Sliding Window + Frequency** | **LC 438** |    ✅   |
|     3 | Fixed Sliding Window                 | LC 567     |    ⬜   |

---

# 🎯 Senior Pattern Recognition

| Signal                                    | Pattern                      |
| ----------------------------------------- | ---------------------------- |
| Longest substring without duplicates      | Variable Window + HashSet    |
| Longest substring with ≤ K replacements   | Variable Window + Frequency  |
| **Find all anagrams**                     | **Fixed Window + Frequency** |
| Find permutation of pattern               | Fixed Window + Frequency     |
| Maximum property in every length-K window | Fixed Window                 |
| Minimum/maximum valid substring           | Variable Window              |

## 💡 One-Line Takeaway

> **When every valid substring must have exactly the same length as a pattern and contain the same character frequencies, use a *Fixed Sliding Window + Frequency Map*: add one character, remove one character, compare frequencies, and record the window's start index.** ([NeetCode][3])

[1]: https://leetcode.com/problems/find-all-anagrams-in-a-string/?envId=apple&envType=company&favoriteSlug=apple-a&utm_source=chatgpt.com "Find All Anagrams in a String - LeetCode"
[2]: https://leetcode.doocs.org/en/lc/438/?utm_source=chatgpt.com "438. Find All Anagrams in a String - LeetCode Wiki"
[3]: https://neetcode.io/solutions/find-all-anagrams-in-a-string?utm_source=chatgpt.com "LeetCode 438 Find All Anagrams in a String Solution & Explanation | NeetCode"


# LC 567 — Permutation in String ⭐⭐⭐⭐⭐

**Pattern:** Fixed Sliding Window + Frequency Map
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐

> **LC 567 is basically the boolean version of LC 438.**
>
> **LC 438:** Find **all** anagram starting indices.
> **LC 567:** Determine whether **at least one** anagram exists.
>
> If you truly understand LC 438, LC 567 should feel familiar—not like a new algorithm.

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement

Given two strings:

```python
s1 = "ab"
s2 = "eidbaooo"
```

Return:

```text
True
```

because `s2` contains:

```text
"ba"
```

and `"ba"` is a permutation of `"ab"`.

---

Another example:

```python
s1 = "ab"
s2 = "eidboaoo"
```

There is no substring containing exactly:

```text
a → 1
b → 1
```

So:

```text
False
```

---

# 2. Senior Translation

Don't generate permutations.

For:

```text
ab
```

the permutations are:

```text
ab
ba
```

But generating them is unnecessary.

Instead ask:

> **Does `s2` contain any substring whose character frequencies exactly match `s1`?**

That translates directly to:

```text
s1
 ↓
Frequency Map

s2
 ↓
Fixed-size windows
 ↓
Frequency comparison
```

Therefore:

```text
Fixed Sliding Window
+
Frequency Map
```

---

# 3. Why Is the Window Fixed?

Suppose:

```python
s1 = "ab"
```

Then every permutation must contain exactly:

```text
2 characters
```

So in:

```python
s2 = "eidbaooo"
```

we inspect only windows of size `2`:

```text
ei
id
db
ba   ← match
ao
oo
```

We never need:

```text
e
eid
eidb
```

because their lengths cannot possibly equal `len(s1)`.

That's the key fixed-window insight.

---

# 4. What Makes a Window Valid?

For:

```python
s1 = "ab"
```

frequency:

```text
a → 1
b → 1
```

A window is valid only when its frequencies are exactly the same.

For example:

```text
"ba"
```

has:

```text
b → 1
a → 1
```

Valid.

But:

```text
"aa"
```

has:

```text
a → 2
b → 0
```

Invalid.

Therefore:

```text
Window frequency == Pattern frequency
```

means:

```text
Permutation exists
```

---

# 5. Why This Is the Same Pattern as LC 438

Compare them:

|                    | LC 438                   | LC 567                   |
| ------------------ | ------------------------ | ------------------------ |
| Pattern            | Fixed Window + Frequency | Fixed Window + Frequency |
| Window size        | `len(p)`                 | `len(s1)`                |
| Frequency matching | Exact                    | Exact                    |
| Match behavior     | Collect index            | Return `True`            |
| No match           | Continue                 | Eventually `False`       |

So the actual algorithm is nearly identical.

---

# 6. Example

```python
s1 = "ab"
s2 = "eidbaooo"
```

Target:

```text
a → 1
b → 1
```

Now scan:

```text
ei
```

Frequency:

```text
e → 1
i → 1
```

❌

Next:

```text
id
```

❌

Next:

```text
db
```

❌

Next:

```text
ba
```

Frequency:

```text
b → 1
a → 1
```

✅

Immediately return:

```text
True
```

No need to inspect the rest of the string.

---

# 7. Recognition Signals

When you see:

```text
Permutation

Anagram

Rearrangement

Contains permutation

Contains anagram

Same character frequencies
```

Think:

```text
Fixed Sliding Window
+
Frequency Map
```

---

# 8. Complexity

Let:

```text
n = len(s2)
m = len(s1)
```

Build the frequency array:

[
O(m)
]

Scan `s2`:

[
O(n)
]

Total:

[
O(n+m)
]

With lowercase English letters, frequency arrays contain only 26 entries, so comparison is constant-sized.

Space:

[
O(1)
]

because we use two arrays of size 26.

---

# 🔹 Block 2: Efficient Code

## Best Python Solution

Because the problem uses lowercase English letters, use fixed arrays.

```python
class Solution:
    def checkInclusion(self, s1, s2):

        if len(s1) > len(s2):
            return False

        need = [0] * 26
        window = [0] * 26

        # Frequency of s1
        for ch in s1:
            need[ord(ch) - ord('a')] += 1

        window_size = len(s1)

        # First window
        for i in range(window_size):
            window[ord(s2[i]) - ord('a')] += 1

        if window == need:
            return True

        # Slide the window
        for right in range(window_size, len(s2)):

            # Add incoming character
            window[ord(s2[right]) - ord('a')] += 1

            # Remove outgoing character
            left = right - window_size
            window[ord(s2[left]) - ord('a')] -= 1

            if window == need:
                return True

        return False
```

---

## Complexity

```text
Time  → O(n + m)
Space → O(1)
```

Because:

```text
need   = 26 elements
window = 26 elements
```

---

## Interview Justification

> I create a frequency array for `s1` and maintain a fixed-size window of the same length in `s2`. When the window slides, I add the incoming character and remove the outgoing character. If the two frequency arrays become equal, the current window is a permutation of `s1`, so I immediately return `True`. If no window matches, I return `False`.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def checkInclusion(self, s1, s2):

        if len(s1) > len(s2):
            return False

        need = [0] * 26
        window = [0] * 26

        # Count characters in s1
        for ch in s1:
            need[ord(ch) - ord('a')] += 1

        window_size = len(s1)

        # Build first window
        for i in range(window_size):
            window[ord(s2[i]) - ord('a')] += 1

        # Check first window
        if window == need:
            return True

        # Slide window
        for right in range(window_size, len(s2)):

            # Add incoming character
            window[ord(s2[right]) - ord('a')] += 1

            # Remove outgoing character
            left = right - window_size
            window[ord(s2[left]) - ord('a')] -= 1

            # Check current window
            if window == need:
                return True

        return False


s1 = "ab"
s2 = "eidbaooo"

obj = Solution()

print(obj.checkInclusion(s1, s2))
```

Output:

```text
True
```

---

# Detailed Dry Run

Input:

```text
s1 = "ab"
s2 = "eidbaooo"
```

## Step 1 — Build Target Frequency

For:

```text
ab
```

we get:

```text
a → 1
b → 1
```

Everything else:

```text
0
```

---

## Step 2 — First Window

Window size:

```text
len(s1) = 2
```

First window:

```text
ei
```

Frequency:

```text
e → 1
i → 1
```

Compare:

```text
ei ≠ ab
```

❌ Continue.

---

## Step 3 — Slide

Current:

```text
e i d
```

Remove outgoing:

```text
e
```

Add incoming:

```text
d
```

New window:

```text
id
```

Frequency:

```text
i → 1
d → 1
```

Not equal.

❌

---

## Step 4 — Slide Again

Current:

```text
i d b
```

Remove:

```text
i
```

Add:

```text
b
```

Window:

```text
db
```

Frequency:

```text
d → 1
b → 1
```

Not equal.

❌

---

## Step 5 — Slide Again

Current:

```text
d b a
```

Remove:

```text
d
```

Add:

```text
a
```

Window:

```text
ba
```

Frequency:

```text
b → 1
a → 1
```

Compare with:

```text
ab
```

Same frequencies.

Therefore:

```text
Permutation Found
```

Return:

```text
True
```

Immediately.

---

# Dry Run Table

| Window Start | Window | Frequency | Match? |
| -----------: | ------ | --------- | :----: |
|            0 | `ei`   | `e:1,i:1` |    ❌   |
|            1 | `id`   | `i:1,d:1` |    ❌   |
|            2 | `db`   | `d:1,b:1` |    ❌   |
|            3 | `ba`   | `b:1,a:1` |    ✅   |

Answer:

```text
True
```

---

# Visual Understanding

```text
s1 = "ab"

Target:

a → 1
b → 1
```

Scan `s2`:

```text
[e i] d b a o o o
  ❌

e [i d] b a o o o
    ❌

e i [d b] a o o o
      ❌

e i d [b a] o o o
        ✅
```

`"ba"` is a permutation of `"ab"`.

Therefore:

```text
True
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is this a fixed-size Sliding Window?

### Model Answer

> Every permutation of `s1` must have exactly `len(s1)` characters. Therefore, we only need to examine windows of that fixed size while sliding across `s2`.

---

## Q2. Why is frequency comparison enough to identify a permutation?

### Model Answer

> A permutation changes the order of characters but not their frequencies. Therefore, two strings of the same length are permutations of each other exactly when their character-frequency distributions are identical.

---

## Q3. Why don't we generate all permutations of `s1`?

### Model Answer

> Generating permutations can require factorial time, which is completely unnecessary. We only need to compare character frequencies, which gives us a linear-time sliding-window solution.

---

## Q4. Why can we return immediately when a match is found?

### Model Answer

> The problem asks whether at least one permutation of `s1` exists in `s2`. Once one matching window is found, the answer is definitively `True`, so processing the remaining characters is unnecessary.

---

## Q5. What is the difference between LC 567 and LC 438?

### Model Answer

> They use essentially the same algorithm. LC 567 returns a boolean once it finds the first matching window, while LC 438 continues scanning and records every matching starting index.

---

## Q6. What would change if the input contained arbitrary Unicode characters?

### Model Answer

> I would use a dictionary or Counter instead of a fixed 26-element array because the character set would no longer be bounded to lowercase English letters. The sliding-window logic would remain the same.

---

# 🔥 LC 438 vs LC 567 — Must Know

This is exactly the kind of comparison an interviewer may ask.

| Feature      | LC 438                       | LC 567                       |
| ------------ | ---------------------------- | ---------------------------- |
| Problem      | Find all anagrams            | Check if permutation exists  |
| Window       | Fixed                        | Fixed                        |
| Window size  | `len(p)`                     | `len(s1)`                    |
| State        | Frequency                    | Frequency                    |
| Match        | `result.append(index)`       | `return True`                |
| No match     | Continue                     | Return `False`               |
| Core pattern | **Fixed Window + Frequency** | **Fixed Window + Frequency** |

The algorithmic difference is tiny.

---

# 🧠 The Pattern Evolution

You have now completed the core progression:

```text
LC 3
│
├── Variable Window
├── HashSet
└── No duplicates
        ↓
LC 424
│
├── Variable Window
├── Frequency Map
└── At most K replacements
        ↓
LC 438
│
├── Fixed Window
├── Frequency Map
└── Find ALL matching windows
        ↓
LC 567
│
├── Fixed Window
├── Frequency Map
└── Find ANY matching window
```

This is the important part—not the individual LeetCode IDs.

---

# ⚡ Master Fixed-Window Template

```python
window_size = len(pattern)

target = ...
window = ...

# First window
for i in range(window_size):
    add(s[i])

# Check first window

for right in range(window_size, len(s)):

    # Add incoming
    add(s[right])

    # Remove outgoing
    left = right - window_size
    remove(s[left])

    # Check window
```

### LC 438

```python
if window == target:
    result.append(left + 1)
```

### LC 567

```python
if window == target:
    return True
```

That's the difference.

---

# String Mastery Progress

| Layer | Pattern                              | Problem    | Status |
| ----: | ------------------------------------ | ---------- | :----: |
|     1 | Traversal                            | LC 58      |    ✅   |
|     1 | Two Pointers                         | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering             | LC 125     |    ✅   |
|     2 | Frequency HashMap                    | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                   | LC 387     |    ✅   |
|     2 | Bidirectional Mapping                | LC 205     |    ✅   |
|     2 | Bidirectional Mapping                | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet    | LC 3       |    ✅   |
|     3 | Sliding Window + Frequency           | LC 424     |    ✅   |
|     3 | Fixed Sliding Window + Frequency     | LC 438     |    ✅   |
|     3 | **Fixed Sliding Window + Frequency** | **LC 567** |    ✅   |

---

# 🎯 Senior Pattern Recognition

| Interview Signal                        | Pattern                      |
| --------------------------------------- | ---------------------------- |
| Longest substring without duplicates    | Variable Window + HashSet    |
| Longest substring with ≤ K replacements | Variable Window + Frequency  |
| Find all anagrams                       | Fixed Window + Frequency     |
| **Check whether a permutation exists**  | **Fixed Window + Frequency** |
| Maximum value in every K-sized window   | Fixed Window + Deque         |
| Minimum valid substring                 | Variable Window              |

## 💡 One-Line Takeaway

> **If the question asks whether a permutation/anagram of one string exists inside another, don't generate permutations—use a fixed-size sliding window and compare character frequencies.**


# 🔵 Layer 4 — Parsing + Stack

You are now moving from **Sliding Window** into a different string pattern family:

> **Parsing + Stack = process a string according to structure, especially when information is nested or must be handled in reverse order.**

Your three problems are:

| Problem                                | Core Pattern    | What You Learn                       |
| -------------------------------------- | --------------- | ------------------------------------ |
| **LC 151 — Reverse Words in a String** | Parsing         | Tokenization + cleanup               |
| **LC 394 — Decode String**             | Stack           | Nested structure + state restoration |
| **LC 71 — Simplify Path**              | Parsing + Stack | Directory hierarchy + LIFO           |

### Recommended order

```text
LC 151
   ↓
LC 394
   ↓
LC 71
```

This order matters.

**LC 151** teaches you to parse a messy string into meaningful tokens.

**LC 394** adds nested structure and requires a stack.

**LC 71** combines parsing + stack to process hierarchical data.

---

# 🧠 Layer 4 Pattern Recognition

Before solving these individually, lock in these signals.

### If the problem says:

```text
Words separated by spaces
Extra spaces
Reverse words
Tokens
```

Think:

```text
PARSING
```

---

### If the problem says:

```text
Nested
Encoded
Decode
Repeat
Inside brackets
Parentheses
Nested expressions
```

Think:

```text
STACK
```

---

### If the problem says:

```text
/
../
./
Directory
Path
Parent
Child
```

Think:

```text
PARSING + STACK
```

---

# 🔹 1. LC 151 — Reverse Words in a String

## Core Pattern

**Parsing**

Example:

```text
"the sky is blue"
```

Output:

```text
"blue is sky the"
```

The important issue isn't actually reversing characters.

It's:

```text
String
   ↓
Extract words
   ↓
Ignore extra spaces
   ↓
Reverse word order
   ↓
Build result
```

### Senior Insight

Don't confuse:

```text
Reverse characters
```

with:

```text
Reverse words
```

For:

```text
"hello world"
```

Character reversal:

```text
"dlrow olleh"
```

Word reversal:

```text
"world hello"
```

That's a completely different operation.

### Main skill

```text
Parsing → Tokens → Reordering
```

---

# 🔹 2. LC 394 — Decode String

## Core Pattern

**Stack + Parsing**

Example:

```text
s = "3[a2[c]]"
```

Output:

```text
"accaccacc"
```

Break it down:

```text
3[
    a
    2[
        c
    ]
]
```

The structure is nested.

You cannot simply process characters independently.

You need to remember previous states.

That's exactly what a stack does.

---

## Senior Translation

When you encounter:

```text
3[
```

you don't yet know the complete string that belongs to `3`.

So save the current state.

```text
Stack
```

Then process the inner expression.

When you reach:

```text
]
```

restore the previous state.

Conceptually:

```text
Current state
      ↓
    PUSH
      ↓
Process nested expression
      ↓
      ]
      ↓
    POP
      ↓
Combine
```

---

# 🔹 3. LC 71 — Simplify Path

## Core Pattern

**Parsing + Stack**

Example:

```text
"/home/user/../docs/./file"
```

You interpret path components.

Rules:

```text
"."   → current directory → ignore

".."  → parent directory → remove previous directory

"name" → enter directory → push
```

So:

```text
/home/user/../docs/./file
```

becomes conceptually:

```text
home
user
..
docs
.
file
```

Process:

```text
home   → push
user   → push
..     → pop user
docs   → push
.      → ignore
file   → push
```

Result:

```text
/home/docs/file
```

---

# 🔥 Why Does a Stack Work?

Because directory navigation has a **last-in, first-out** relationship.

Suppose:

```text
/home/user/projects
```

Then:

```text
..
```

means:

```text
go back to /home/user
```

The most recently added directory must be removed first.

That's exactly:

```text
LIFO

Last In
First Out
```

which is a stack.

---

# 🧠 The Three Problems Are Building One Skill

Don't memorize three unrelated solutions.

Understand the progression:

```text
                STRING
                   │
                   ▼
              PARSING
                   │
          ┌────────┴────────┐
          ▼                 ▼
       Tokens            Structure
          │                 │
       LC 151            LC 394
                            │
                         Nested
                            │
                          Stack
                            │
                            ▼
                         LC 71
```

---

# 🎯 Pattern Recognition Cheat Sheet

| Signal in Problem                 | Think           |
| --------------------------------- | --------------- |
| Reverse words                     | Parsing         |
| Extra spaces                      | Parsing         |
| Split into tokens                 | Parsing         |
| Nested brackets                   | Stack           |
| Decode nested expressions         | Stack           |
| Repeat inner expression           | Stack           |
| Parent directory `..`             | Stack           |
| Last item must be processed first | Stack           |
| Hierarchical path                 | Parsing + Stack |

---

# ⚠️ Common Beginner Mistakes

### Mistake 1 — Using `split()` for everything

`split()` is sometimes perfectly valid.

But don't blindly use it.

You need to understand **why** the tokens matter and what structure you're processing.

---

### Mistake 2 — Treating LC 394 like normal string manipulation

This fails because:

```text
3[a2[c]]
```

contains nested state.

You need to remember:

```text
repeat count
previous decoded string
```

for each nesting level.

---

### Mistake 3 — Not understanding LIFO

For:

```text
a → b → c
```

then undoing the most recent operation means:

```text
c
```

must be removed first.

That's why:

```text
Stack
```

is the natural data structure.

---

# 📚 Your Layer 4 Sequence

We'll solve them **exactly in this order**:

### 1️⃣ LC 151 — Reverse Words in a String

Learn:

```text
Parsing
Tokenization
Whitespace handling
String construction
```

↓

### 2️⃣ LC 394 — Decode String

Learn:

```text
Parsing
Nested structures
Stack
State restoration
```

↓

### 3️⃣ LC 71 — Simplify Path

Learn:

```text
Parsing
Stack
LIFO
Hierarchical processing
```

---

# String Mastery Progress

| Layer | Pattern                           | Problem    | Status |
| ----: | --------------------------------- | ---------- | :----: |
|     1 | Traversal                         | LC 58      |    ✅   |
|     1 | Two Pointers                      | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering          | LC 125     |    ✅   |
|     2 | Frequency HashMap                 | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                | LC 387     |    ✅   |
|     2 | Bidirectional Mapping             | LC 205     |    ✅   |
|     2 | Bidirectional Mapping             | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet | LC 3       |    ✅   |
|     3 | Sliding Window + Frequency        | LC 424     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 438     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 567     |    ✅   |
|     4 | **Parsing**                       | **LC 151** |    ⬜   |
|     4 | **Parsing + Stack**               | **LC 394** |    ⬜   |
|     4 | **Parsing + Stack**               | **LC 71**  |    ⬜   |

# LC 151 — Reverse Words in a String ⭐⭐⭐⭐

**Pattern:** Parsing + String Traversal
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐

> **Core lesson:** Don't reverse characters. **Parse the string into words, ignore unnecessary whitespace, then reverse the order of the words.**
>
> This is your first problem in **Layer 4 — Parsing + Stack**. It intentionally does **not** require a stack; it builds the parsing foundation needed for LC 394 and LC 71.

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement

Given a string containing words separated by spaces, return the words in reverse order.

Example:

```python
s = "the sky is blue"
```

Output:

```text
"blue is sky the"
```

But the real interview difficulty comes from spaces.

Example:

```python
s = "  hello   world  "
```

Output:

```text
"world hello"
```

You must:

* Ignore leading spaces.
* Ignore trailing spaces.
* Treat multiple spaces as one separator.
* Reverse **word order**, not characters.

---

# 2. Senior Translation

When you hear:

```text
Reverse Words
```

don't immediately think:

```text
Two Pointers
```

Instead ask:

> **What exactly is being reversed?**

For:

```text
"hello world"
```

Character reversal:

```text
"dlrow olleh"
```

Word reversal:

```text
"world hello"
```

The second one is required.

So translate the problem:

```text
Raw String
    ↓
Parse words
    ↓
Ignore whitespace
    ↓
Reverse word order
    ↓
Build result
```

---

# 3. Why Parsing Is the Main Pattern

The string isn't necessarily clean:

```text
"  the   sky is   blue  "
```

If we blindly process every character, we have to deal with:

```text
leading spaces
multiple spaces
trailing spaces
```

The meaningful data is actually:

```text
["the", "sky", "is", "blue"]
```

Once you've extracted the words, the problem becomes trivial:

```text
["blue", "is", "sky", "the"]
```

Therefore the real challenge is **parsing**.

---

# 4. Approach 1 — Pythonic Solution

Python provides:

```python
s.split()
```

which automatically handles arbitrary whitespace.

Example:

```python
s = "  the   sky is   blue  "

s.split()
```

gives:

```python
["the", "sky", "is", "blue"]
```

Then:

```python
words[::-1]
```

gives:

```python
["blue", "is", "sky", "the"]
```

Finally:

```python
" ".join(...)
```

produces:

```text
"blue is sky the"
```

This is absolutely valid Python and is often the cleanest production solution.

---

# 5. But What Does a Senior Interviewer Want?

If the interviewer asks:

> "Can you solve it without using `split()`?"

You should be able to.

Why?

Because the point of this problem is understanding parsing—not memorizing:

```python
" ".join(s.split()[::-1])
```

So know **both**:

### Pythonic

```text
split → reverse → join
```

### Manual

```text
scan → extract words → reverse/build
```

---

# 6. Recognition Signals

Whenever you see:

```text
Reverse words
Normalize spaces
Ignore extra spaces
Extract tokens
Parse input
Words separated by delimiters
```

Think:

```text
PARSING
```

---

# 7. Complexity

Let:

```text
n = len(s)
```

We must inspect the input:

[
O(n)
]

We also construct the result:

[
O(n)
]

Overall:

[
O(n)
]

Space:

The list of words requires:

[
O(n)
]

and the output itself also requires:

[
O(n)
]

So auxiliary space is:

[
O(n)
]

---

# 🔹 Block 2: Efficient Code

## Best Pythonic LeetCode Solution

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        words = s.split()
        words.reverse()
        return " ".join(words)
```

### Even shorter

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        return " ".join(s.split()[::-1])
```

For an interview, I prefer the **first version** because it makes each operation explicit.

---

## Complexity

### Time

[
O(n)
]

We process the input and construct the output.

### Space

[
O(n)
]

The words and resulting string require linear memory.

---

## Interview Explanation

Say:

> "I first parse the string into words using `split()`, which automatically removes leading, trailing, and repeated whitespace. Then I reverse the word list and join the words with a single space. The overall complexity is O(n) time and O(n) auxiliary space."

That's enough.

Don't over-explain a simple problem.

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def reverseWords(self, s: str) -> str:

        # Parse the string into words.
        # split() automatically handles extra spaces.
        words = s.split()

        # Reverse the order of words.
        words.reverse()

        # Join them using exactly one space.
        return " ".join(words)


# Example
s = "  the   sky is   blue  "

obj = Solution()

result = obj.reverseWords(s)

print("Input :", repr(s))
print("Output:", result)
```

Output:

```text
Input : '  the   sky is   blue  '
Output: blue is sky the
```

---

# Detailed Dry Run

Input:

```text
"  the   sky is   blue  "
```

### Step 1 — Parse

```python
words = s.split()
```

Result:

```text
["the", "sky", "is", "blue"]
```

All unnecessary spaces are gone.

---

### Step 2 — Reverse

```python
words.reverse()
```

Result:

```text
["blue", "is", "sky", "the"]
```

---

### Step 3 — Join

```python
" ".join(words)
```

Result:

```text
"blue is sky the"
```

---

# Dry Run Table

| Step    | Data                           |
| ------- | ------------------------------ |
| Input   | `"  the   sky is   blue  "`    |
| Parse   | `["the", "sky", "is", "blue"]` |
| Reverse | `["blue", "is", "sky", "the"]` |
| Join    | `"blue is sky the"`            |

---

# Manual Parsing — Interview Follow-Up

If the interviewer says:

> **"Don't use `split()`."**

Then use a right-to-left scan.

Why right-to-left?

Because the desired output is already in reverse word order.

Example:

```text
the sky is blue
            ↑
```

Start from the end.

Find:

```text
blue
```

then:

```text
is
```

then:

```text
sky
```

then:

```text
the
```

---

## Manual Version

```python
class Solution:
    def reverseWords(self, s: str) -> str:

        result = []
        i = len(s) - 1

        while i >= 0:

            # Skip spaces
            while i >= 0 and s[i] == ' ':
                i -= 1

            if i < 0:
                break

            # Find the end of the word
            end = i

            # Move to the beginning of the word
            while i >= 0 and s[i] != ' ':
                i -= 1

            # Extract the word
            result.append(s[i + 1:end + 1])

        return " ".join(result)
```

### Complexity

```text
Time  → O(n)
Space → O(n)
```

The result itself requires O(n) space.

---

# Manual Dry Run

Input:

```text
"the sky is blue"
```

Start:

```text
                i
                ↓
the sky is blue
```

Find:

```text
blue
```

Store:

```text
["blue"]
```

Continue backward.

Find:

```text
is
```

Store:

```text
["blue", "is"]
```

Then:

```text
sky
```

Then:

```text
the
```

Final:

```text
["blue", "is", "sky", "the"]
```

Join:

```text
"blue is sky the"
```

---

# 🔹 Block 4: Interview Q&A

## Q1. Why does `split()` solve the whitespace problem?

### Model Answer

> `split()` without an argument treats consecutive whitespace as a separator and removes leading and trailing whitespace. Therefore, it gives us exactly the meaningful words without having to manually handle repeated spaces.

---

## Q2. Why isn't `s[::-1]` correct?

### Model Answer

> `s[::-1]` reverses characters, not words. The problem requires preserving the characters inside each word while reversing the order of the words.

Example:

```text
"hello world"
```

Character reversal:

```text
"dlrow olleh"
```

Required:

```text
"world hello"
```

---

## Q3. What is the time complexity?

### Model Answer

> O(n), where n is the length of the input string. We parse the input, reverse the word order, and construct the output, all requiring linear work.

---

## Q4. What is the space complexity?

### Model Answer

> O(n), because we store the parsed words and construct the output string.

---

## Q5. How would you solve it without `split()`?

### Model Answer

> I would scan from right to left, skip spaces, identify each word's boundaries, append the word to a result list, and finally join the words with a single space. This maintains O(n) time.

---

## Q6. Why is this problem classified as Parsing rather than Two Pointers?

### Model Answer

> Although a pointer can be used to scan the string, the primary challenge is interpreting the raw string into meaningful tokens while handling whitespace. The dominant technique is therefore parsing rather than the classic two-pointer comparison pattern.

---

# ⚠️ Common Interview Traps

### Trap 1 — Reversing characters

```python
s[::-1]
```

❌ Wrong problem.

---

### Trap 2 — Using `split(" ")`

This is subtly different from:

```python
s.split()
```

For:

```text
"  hello   world  "
```

`split(" ")` can produce empty strings.

Use:

```python
s.split()
```

when you want whitespace-aware tokenization.

---

### Trap 3 — Forgetting the output spacing

The result must contain:

```text
exactly one space
```

between words.

Therefore:

```python
" ".join(words)
```

is cleaner than manually adding spaces.

---

# 🧠 Pattern Extraction

LC 151 gives you this template:

```text
Raw String
    ↓
Parse
    ↓
Extract meaningful tokens
    ↓
Process tokens
    ↓
Reconstruct output
```

For this problem:

```text
String
  ↓
Words
  ↓
Reverse order
  ↓
Join
```

---

# 🔥 Why LC 151 Comes Before LC 394

This is deliberate.

### LC 151

You learn:

```text
String
 ↓
Tokens
 ↓
Process tokens
```

### LC 394

You will learn:

```text
String
 ↓
Tokens + Numbers + Brackets
 ↓
Nested state
 ↓
Stack
 ↓
Decode
```

So:

```text
LC 151
Parsing
   ↓
LC 394
Parsing + Nested State + Stack
```

That's the progression you want to master—not just memorize individual LeetCode solutions.

---

# String Mastery Progress

| Layer | Pattern                           | Problem    | Status |
| ----: | --------------------------------- | ---------- | :----: |
|     1 | Traversal                         | LC 58      |    ✅   |
|     1 | Two Pointers                      | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering          | LC 125     |    ✅   |
|     2 | Frequency HashMap                 | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                | LC 387     |    ✅   |
|     2 | Bidirectional Mapping             | LC 205     |    ✅   |
|     2 | Bidirectional Mapping             | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet | LC 3       |    ✅   |
|     3 | Sliding Window + Frequency        | LC 424     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 438     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 567     |    ✅   |
|     4 | **Parsing**                       | **LC 151** |    ✅   |
|     4 | Parsing + Stack                   | LC 394     |    ⬜   |
|     4 | Parsing + Stack                   | LC 71      |    ⬜   |

---

# 🎯 Senior Pattern Recognition

| Signal                             | Pattern                  |
| ---------------------------------- | ------------------------ |
| Reverse characters                 | Two Pointers             |
| Palindrome                         | Two Pointers + Filtering |
| Character frequency                | HashMap                  |
| Longest substring                  | Sliding Window           |
| Find anagrams                      | Fixed Window + Frequency |
| **Reverse words / tokenize input** | **Parsing**              |
| Nested expressions                 | Parsing + Stack          |
| Directory navigation               | Parsing + Stack          |

## 💡 One-Line Takeaway

> **LC 151 teaches you to separate the raw string from its meaningful tokens: parse first, then operate on the words. That parsing mindset is the foundation for the harder stack-based string problems coming next.**


# LC 394 — Decode String ⭐⭐⭐⭐⭐

**Pattern:** Parsing + Stack
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐

> **Core lesson:** When a string contains **nested structures**, and you need to remember the state before entering each nested level, think **Stack**.

Example:

```text
3[a2[c]]
```

means:

```text
3 × (a + 2 × c)
```

so the result is:

```text
accaccacc
```

This problem is one of the best ways to learn **nested parsing + LIFO state management**.

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement

The encoding follows:

```text
k[encoded_string]
```

where `encoded_string` is repeated `k` times.

Examples:

```text
3[a]
```

becomes:

```text
aaa
```

---

```text
3[a2[c]]
```

First:

```text
2[c] → cc
```

Then:

```text
a + cc → acc
```

Finally:

```text
3 × acc → accaccacc
```

---

## 2. The Senior Translation

Don't look at:

```text
3[a2[c]]
```

as a normal string.

Look at it as a **nested expression**:

```text
3[
    a
    2[
        c
    ]
]
```

That immediately suggests:

```text
Nested structure
       ↓
Need previous state
       ↓
Stack
```

---

# 3. What State Do We Need to Remember?

Suppose we encounter:

```text
3[
```

At this point we need to remember:

```text
repeat count = 3
string before '['
```

Why?

Because after decoding the inside, we need to return to that previous context.

So before entering `[...]`, push:

```text
(current_string, repeat_count)
```

Then process the nested content.

When we encounter:

```text
]
```

we pop the previous state.

This is exactly what a stack is designed for.

---

# 4. The Core Mental Model

Think of every `[` as:

```text
ENTER NESTED LEVEL
```

and every `]` as:

```text
EXIT NESTED LEVEL
```

Therefore:

```text
[
 ↓
PUSH STATE

process inside

]
 ↓
POP STATE
```

This is **LIFO**:

```text
Last In
   ↓
First Out
```

---

# 5. Example: `3[a]`

Start:

```text
current = ""
number = 0
stack = []
```

Read:

```text
3
```

So:

```text
number = 3
```

Read:

```text
[
```

Push:

```text
("", 3)
```

Reset:

```text
current = ""
number = 0
```

Read:

```text
a
```

Now:

```text
current = "a"
```

Read:

```text
]
```

Pop:

```text
previous = ""
repeat = 3
```

Combine:

```text
"" + "a" * 3
```

Result:

```text
"aaa"
```

---

# 6. Nested Example: `3[a2[c]]`

This is where the stack becomes necessary.

Start:

```text
3
```

```text
number = 3
```

Then:

```text
[
```

Push:

```text
("", 3)
```

---

Read:

```text
a
```

Now:

```text
current = "a"
```

Then:

```text
2
```

```text
number = 2
```

Then:

```text
[
```

Push:

```text
("a", 2)
```

Now process:

```text
c
```

```text
current = "c"
```

Then:

```text
]
```

Pop:

```text
previous = "a"
repeat = 2
```

Combine:

```text
"a" + "c" * 2
```

Result:

```text
"acc"
```

Then outer:

```text
]
```

Pop:

```text
previous = ""
repeat = 3
```

Combine:

```text
"" + "acc" * 3
```

Final:

```text
"accaccacc"
```

---

# 7. Why a Simple Variable Isn't Enough

Consider:

```text
3[a2[c]]
```

You have:

```text
3
```

then enter another level:

```text
2
```

Now you must remember that the outer level was:

```text
3
```

After finishing `2[c]`, you need to return to the outer context.

A single variable cannot conveniently remember arbitrary nesting.

A stack can:

```text
Outer state
    ↓
Push

Inner state
    ↓
Push

Finish inner
    ↓
Pop

Finish outer
    ↓
Pop
```

That's the fundamental reason for the data structure.

---

# 8. Parsing Rules

We process four kinds of characters.

### Digit

Build the repeat number.

```python
number = number * 10 + int(ch)
```

This handles:

```text
3
12
100
```

not just single-digit counts.

For:

```text
"12[a]"
```

we process:

```text
1
↓
number = 1

2
↓
number = 12
```

---

### `[`

Save the current state:

```text
(current_string, number)
```

Then reset:

```text
current = ""
number = 0
```

---

### `]`

Restore the previous state:

```text
previous_string + current * repeat
```

---

### Letter

Append it:

```python
current += ch
```

---

# 9. Recognition Signals

When you see:

```text
Nested brackets
Nested parentheses
Encoded strings
Repeat expressions
Decode expressions
Nested expressions
```

Think:

```text
PARSING + STACK
```

More specifically:

```text
Opening delimiter
        ↓
Save state
        ↓
Process nested content
        ↓
Closing delimiter
        ↓
Restore state
```

---

# 10. Complexity

Let `n` be the size of the input and `N` be the size of the decoded output.

The parser itself processes the encoded input:

[
O(n)
]

But producing the final decoded string necessarily takes time proportional to its output size:

[
O(N)
]

Therefore the practical complexity is:

[
O(n + N)
]

Space:

```text
Stack → O(n) worst case
Output → O(N)
```

So auxiliary stack space is:

[
O(n)
]

---

# 🔹 Block 2: Efficient Code

## Best Clean Python Solution

```python
class Solution:
    def decodeString(self, s: str) -> str:

        stack = []

        current = ""
        number = 0

        for ch in s:

            if ch.isdigit():
                number = number * 10 + int(ch)

            elif ch == '[':
                stack.append((current, number))

                current = ""
                number = 0

            elif ch == ']':
                previous, repeat = stack.pop()

                current = previous + current * repeat

            else:
                current += ch

        return current
```

---

## Complexity

Let:

```text
n = encoded input size
N = decoded output size
```

### Time

[
O(n + N)
]

### Space

[
O(n + N)
]

if counting the output.

The **auxiliary stack** itself requires:

[
O(n)
]

in the worst case.

---

## Interview Justification

Say:

> "I scan the encoded string once and use a stack to save the current string and repeat count whenever I enter a nested bracket. When I encounter the closing bracket, I pop the previous state and combine it with the decoded inner string repeated the required number of times. The parsing work is linear in the input, while constructing the decoded result costs proportional to its output size."

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def decodeString(self, s: str) -> str:

        stack = []

        current = ""
        number = 0

        for ch in s:

            # Build the repeat number
            if ch.isdigit():
                number = number * 10 + int(ch)

            # Enter a nested expression
            elif ch == '[':
                stack.append((current, number))

                current = ""
                number = 0

            # Exit a nested expression
            elif ch == ']':
                previous, repeat = stack.pop()

                current = previous + current * repeat

            # Normal character
            else:
                current += ch

        return current


# Example
s = "3[a2[c]]"

obj = Solution()

result = obj.decodeString(s)

print("Input :", s)
print("Output:", result)
```

Output:

```text
Input : 3[a2[c]]
Output: accaccacc
```

---

# Detailed Dry Run

Input:

```text
3[a2[c]]
```

We'll track:

```text
current
number
stack
```

---

## Step 1 — Read `3`

Digit:

```text
number = 3
```

State:

```text
current = ""
number = 3
stack = []
```

---

## Step 2 — Read `[`

Push:

```text
("", 3)
```

Stack:

```text
[("", 3)]
```

Reset:

```text
current = ""
number = 0
```

---

## Step 3 — Read `a`

Letter:

```text
current = "a"
```

---

## Step 4 — Read `2`

Digit:

```text
number = 2
```

State:

```text
current = "a"
number = 2
```

---

## Step 5 — Read `[`

Push:

```text
("a", 2)
```

Stack becomes:

```text
[
    ("", 3),
    ("a", 2)
]
```

Reset:

```text
current = ""
number = 0
```

---

## Step 6 — Read `c`

Letter:

```text
current = "c"
```

---

## Step 7 — Read `]`

Pop:

```text
previous = "a"
repeat = 2
```

Current:

```text
"c"
```

Decode:

```text
"a" + "c" * 2
```

Therefore:

```text
current = "acc"
```

Stack:

```text
[
    ("", 3)
]
```

---

## Step 8 — Read Final `]`

Pop:

```text
previous = ""
repeat = 3
```

Current:

```text
"acc"
```

Decode:

```text
"" + "acc" * 3
```

Therefore:

```text
current = "accaccacc"
```

---

## Final Answer

```text
accaccacc
```

---

# Dry Run Table

| Character | Action        | `current`     | `number` | Stack              |
| --------- | ------------- | ------------- | -------: | ------------------ |
| `3`       | Build number  | `""`          |        3 | `[]`               |
| `[`       | Push state    | `""`          |        0 | `[("",3)]`         |
| `a`       | Add character | `"a"`         |        0 | `[("",3)]`         |
| `2`       | Build number  | `"a"`         |        2 | `[("",3)]`         |
| `[`       | Push state    | `""`          |        0 | `[("",3),("a",2)]` |
| `c`       | Add character | `"c"`         |        0 | `[("",3),("a",2)]` |
| `]`       | Pop + decode  | `"acc"`       |        0 | `[("",3)]`         |
| `]`       | Pop + decode  | `"accaccacc"` |        0 | `[]`               |

---

# 🔥 Another Example

Consider:

```text
2[abc]3[cd]ef
```

Process:

```text
2[abc]
```

becomes:

```text
abcabc
```

Then:

```text
3[cd]
```

becomes:

```text
cdcdcd
```

Then append:

```text
ef
```

Final:

```text
abcabccdcdcdef
```

The important point is that the stack doesn't care whether the nested content contains one character or many characters.

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is a stack the correct data structure?

### Model Answer

> The expression can contain arbitrarily nested brackets. When entering a nested level, I need to save the current string and repeat count. When the closing bracket appears, I need to restore the most recently saved state. That's a LIFO operation, which naturally maps to a stack.

---

## Q2. What should be stored in the stack?

### Model Answer

> For each opening bracket, I store the string accumulated before that bracket and the repeat count associated with it. So each stack entry is `(previous_string, repeat_count)`.

---

## Q3. How do you handle multi-digit numbers such as `12[a]`?

### Model Answer

> I accumulate digits using `number = number * 10 + int(ch)`. For `12`, the first digit produces `1`, and the second produces `1 * 10 + 2 = 12`.

---

## Q4. Why do we reset `number` after `[`?

### Model Answer

> The repeat count belongs only to the current nested expression. Once that state is pushed onto the stack, the number for the next nested level should start from zero.

---

## Q5. Why can't we simply use recursion?

### Model Answer

> Recursion can also represent nested expressions because each recursive call naturally stores its previous state. However, an explicit stack gives direct control over the parsing process and avoids relying on the call stack. For an interview, both approaches are valid if implemented correctly.

---

## Q6. What is the biggest complexity trap in this problem?

### Model Answer

> Saying the solution is simply O(n) can be misleading because the decoded output can be much larger than the encoded input. If the output contains `N` characters, constructing it requires at least O(N) work. So a more accurate complexity is O(n + N).

---

# 🧠 The Most Important Pattern

Memorize this:

```text
             CHARACTER
                 │
       ┌─────────┼─────────┐
       ↓         ↓         ↓
     DIGIT       [         ]
       │         │         │
       ↓         ↓         ↓
    Build      PUSH       POP
    number     state      state
                 │         │
                 ↓         ↓
             Reset      Combine
```

The core state is:

```text
(current_string, repeat_count)
```

---

# ⚡ Master Template — Nested Parsing

```python
stack = []

current = ""
number = 0

for ch in s:

    if ch.isdigit():
        number = number * 10 + int(ch)

    elif ch == '[':
        stack.append((current, number))
        current = ""
        number = 0

    elif ch == ']':
        previous, repeat = stack.pop()
        current = previous + current * repeat

    else:
        current += ch

return current
```

Don't blindly memorize this code.

Understand the three operations:

```text
[  → SAVE STATE

inside → BUILD CURRENT STATE

]  → RESTORE + COMBINE
```

That's the transferable skill.

---

# LC 151 → LC 394 Progression

You just moved from:

```text
LC 151
Parsing
│
├── Extract tokens
├── Ignore whitespace
└── Reorder tokens
```

to:

```text
LC 394
Parsing + Stack
│
├── Read tokens
├── Detect nesting
├── Save state
├── Process inner expression
└── Restore state
```

The next problem, **LC 71 — Simplify Path**, will use the same fundamental idea of:

```text
parse → push → pop → reconstruct
```

but with filesystem hierarchy instead of encoded strings.

---

# String Mastery Progress

| Layer | Pattern                           | Problem    | Status |
| ----: | --------------------------------- | ---------- | :----: |
|     1 | Traversal                         | LC 58      |    ✅   |
|     1 | Two Pointers                      | LC 344     |    ✅   |
|     1 | Two Pointers + Filtering          | LC 125     |    ✅   |
|     2 | Frequency HashMap                 | LC 242     |    ✅   |
|     2 | Two-Pass Frequency                | LC 387     |    ✅   |
|     2 | Bidirectional Mapping             | LC 205     |    ✅   |
|     2 | Bidirectional Mapping             | LC 290     |    ✅   |
|     3 | Variable Sliding Window + HashSet | LC 3       |    ✅   |
|     3 | Sliding Window + Frequency        | LC 424     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 438     |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 567     |    ✅   |
|     4 | Parsing                           | LC 151     |    ✅   |
|     4 | **Parsing + Stack**               | **LC 394** |    ✅   |
|     4 | Parsing + Stack                   | LC 71      |    ⬜   |

---

# 🎯 Senior Pattern Recognition

| Problem Signal                            | Pattern             |
| ----------------------------------------- | ------------------- |
| Reverse words                             | Parsing             |
| Normalize whitespace                      | Parsing             |
| **Nested brackets / encoded expressions** | **Parsing + Stack** |
| Repeat nested content                     | Stack               |
| Parent directory `..`                     | Parsing + Stack     |
| Last operation must be undone first       | Stack               |

## 💡 One-Line Takeaway

> **When a string contains nested expressions, every `[` means "save the current state" and every `]` means "restore the most recent state"—that is the Stack pattern.**
# LC 71 — Simplify Path ⭐⭐⭐⭐⭐

**Pattern:** Parsing + Stack
**Difficulty:** Medium
**Interview Importance:** ⭐⭐⭐⭐⭐
**Core Skill:** Tokenization + LIFO + State Simplification

> **LC 71 teaches a highly reusable idea: parse a structured string into tokens, then use a stack to process operations that can undo previous state.**
>
> The critical relationship is:
>
> **normal directory → PUSH**
> **`..` → POP**
> **`.` → IGNORE**

---

# 🔹 Block 1: Senior Insights

## 1. Problem Statement Simplified

You're given an absolute Unix-style path.

Example:

```python
path = "/home/user/Documents/../Pictures"
```

Return the simplified canonical path:

```text
/home/user/Pictures
```

Why?

Because:

```text
/home/user/Documents
                  ↑
                 ..
```

means:

```text
Go back one directory
```

So `Documents` disappears.

---

## 2. Unix Path Rules You Must Know

There are four important cases.

### Case 1 — Normal directory

```text
home
user
documents
```

These should be kept.

```text
→ PUSH onto stack
```

---

### Case 2 — Single dot `.`

```text
.
```

means:

> Current directory.

So:

```text
/home/./user
```

is simply:

```text
/home/user
```

Action:

```text
IGNORE
```

---

### Case 3 — Double dot `..`

```text
..
```

means:

> Parent directory.

Example:

```text
/home/user/..
```

becomes:

```text
/home
```

Action:

```text
POP
```

---

### Case 4 — Multiple `/`

```text
/home//user///docs
```

Multiple slashes behave like one separator.

Result:

```text
/home/user/docs
```

---

# 3. Senior Translation

When you see:

```text
/home/user/../docs
```

don't process it character-by-character unless the interviewer specifically asks you to.

First **tokenize** it:

```python
path.split("/")
```

produces conceptually:

```text
["", "home", "user", "..", "docs"]
```

Now the problem becomes much easier:

```text
""      → ignore
home    → push
user    → push
..      → pop
docs    → push
```

Final stack:

```text
["home", "docs"]
```

Reconstruct:

```text
/home/docs
```

So the real algorithm is:

```text
PARSE
  ↓
CLASSIFY TOKEN
  ↓
PUSH / POP / IGNORE
  ↓
RECONSTRUCT
```

---

# 4. Why Stack?

Suppose we're currently at:

```text
/home/user/projects/python
```

Conceptually:

```text
home
 ↓
user
 ↓
projects
 ↓
python
```

Stack:

```python
["home", "user", "projects", "python"]
```

Now we encounter:

```text
..
```

Which directory should disappear?

The **most recently entered** directory:

```text
python
```

So:

```python
stack.pop()
```

Result:

```python
["home", "user", "projects"]
```

That's exactly:

```text
LIFO

Last In
First Out
```

Therefore Stack is the natural data structure.

---

# 5. Core Decision Table

This is the part you should memorize.

| Token         | Meaning              | Action          |
| ------------- | -------------------- | --------------- |
| `""`          | Empty because of `/` | Ignore          |
| `"."`         | Current directory    | Ignore          |
| `".."`        | Parent directory     | Pop if possible |
| Anything else | Directory name       | Push            |

That's basically the whole problem.

---

# 6. Important Edge Case — Already at Root

Consider:

```text
/../../home
```

Start:

```python
stack = []
```

First:

```text
..
```

Can we pop?

No.

We're already at:

```text
/
```

Going above root does nothing.

So:

```python
if stack:
    stack.pop()
```

is necessary.

Then eventually:

```text
home
```

gets pushed.

Answer:

```text
/home
```

---

# 7. Important Trap — `...` Is NOT `..`

This matters.

```text
.
```

has special meaning.

```text
..
```

has special meaning.

But:

```text
...
```

is just a normal directory name.

Therefore:

```python
elif token == "..":
```

must be an **exact comparison**.

Don't write logic that treats anything containing dots as a parent operation.

---

# 8. Another Trap — Directory Names Can Contain Dots

Example:

```text
/home/.../test
```

Here:

```text
...
```

is a valid directory.

Stack:

```python
["home", "...", "test"]
```

Result:

```text
/home/.../test
```

---

# 9. Recognition Signals

When you see:

```text
Canonical path
Simplify path
Directory traversal
Parent directory
Undo previous component
../
./
```

think:

```text
Parsing
   +
Stack
```

More generally:

> If the current token can **undo/remove the most recently accepted token**, Stack should immediately enter your mind.

---

# 10. Complexity

Let:

```text
n = len(path)
```

Splitting the path processes the input:

[
O(n)
]

Each token is processed once.

Push/pop are amortized:

[
O(1)
]

Reconstructing the result also takes up to:

[
O(n)
]

Therefore:

**Time: O(n)**

The token list and stack can contain up to O(n) total characters.

**Space: O(n)**

---

# 🔹 Block 2: Efficient Code

## Clean LeetCode Solution

```python
class Solution:
    def simplifyPath(self, path: str) -> str:

        stack = []

        for token in path.split("/"):

            if token == "" or token == ".":
                continue

            elif token == "..":
                if stack:
                    stack.pop()

            else:
                stack.append(token)

        return "/" + "/".join(stack)
```

This is the solution I'd use in a Python interview unless the interviewer explicitly bans `split()`.

---

## Time Complexity

[
O(n)
]

where `n` is the length of `path`.

We:

1. Parse the path.
2. Process every component once.
3. Reconstruct the final path.

---

## Space Complexity

[
O(n)
]

The stack may contain all directory components.

---

## Interview Complexity Justification

> "I split the path into directory components and process each component exactly once. Normal directory names are pushed onto the stack, `..` pops the most recent directory when possible, and empty components or `.` are ignored. Finally, I join the remaining stack components. This gives O(n) time and O(n) space."

---

# 🔹 Block 3: Full Code + Dry Run

## Full Runnable Code

```python
class Solution:

    def simplifyPath(self, path: str) -> str:

        stack = []

        # Break the path into components
        components = path.split("/")

        for token in components:

            # Ignore empty components and current directory
            if token == "" or token == ".":
                continue

            # Move to parent directory
            elif token == "..":

                if stack:
                    stack.pop()

            # Normal directory
            else:
                stack.append(token)

        # Reconstruct canonical path
        return "/" + "/".join(stack)


# Example
path = "/home/user/Documents/../Pictures"

obj = Solution()

result = obj.simplifyPath(path)

print("Input :", path)
print("Output:", result)
```

Output:

```text
Input : /home/user/Documents/../Pictures
Output: /home/user/Pictures
```

---

# Detailed Dry Run

Input:

```text
/home/user/Documents/../Pictures
```

## Step 1 — Parse

```python
components = path.split("/")
```

We get:

```text
[
    "",
    "home",
    "user",
    "Documents",
    "..",
    "Pictures"
]
```

Initial:

```python
stack = []
```

---

## Step 2 — `""`

Empty token.

Action:

```text
IGNORE
```

Stack:

```text
[]
```

---

## Step 3 — `"home"`

Normal directory.

Action:

```text
PUSH
```

Stack:

```python
["home"]
```

Current canonical state:

```text
/home
```

---

## Step 4 — `"user"`

Normal directory.

Push:

```python
["home", "user"]
```

Current state:

```text
/home/user
```

---

## Step 5 — `"Documents"`

Normal directory.

Push:

```python
["home", "user", "Documents"]
```

Current state:

```text
/home/user/Documents
```

---

## Step 6 — `".."`

Parent directory.

Therefore:

```python
stack.pop()
```

Remove:

```text
Documents
```

Stack becomes:

```python
["home", "user"]
```

Current state:

```text
/home/user
```

---

## Step 7 — `"Pictures"`

Normal directory.

Push:

```python
["home", "user", "Pictures"]
```

---

## Final Reconstruction

Stack:

```python
["home", "user", "Pictures"]
```

Join:

```python
"/".join(stack)
```

produces:

```text
home/user/Pictures
```

Add root slash:

```python
"/" + "/".join(stack)
```

Final:

```text
/home/user/Pictures
```

---

# Dry Run Table

| Token       | Meaning   | Action | Stack                   |
| ----------- | --------- | ------ | ----------------------- |
| `""`        | Empty     | Ignore | `[]`                    |
| `home`      | Directory | Push   | `[home]`                |
| `user`      | Directory | Push   | `[home,user]`           |
| `Documents` | Directory | Push   | `[home,user,Documents]` |
| `..`        | Parent    | Pop    | `[home,user]`           |
| `Pictures`  | Directory | Push   | `[home,user,Pictures]`  |

Final:

```text
/home/user/Pictures
```

---

# 🔥 Harder Dry Run

Consider:

```text
/a/./b/../../c/
```

Parse:

```text
["", "a", ".", "b", "..", "..", "c", ""]
```

Process:

```text
a
↓
push
[a]

.
↓
ignore
[a]

b
↓
push
[a, b]

..
↓
pop b
[a]

..
↓
pop a
[]

c
↓
push
[c]
```

Result:

```text
/c
```

This example tests whether you truly understand the stack instead of merely memorizing the code.

---

# 🔹 Block 4: Interview Q&A

## Q1. Why is Stack appropriate for LC 71?

### Model Answer

> A normal directory component moves us deeper into the path, while `..` removes the most recently entered directory. Since the most recently added component must be removed first, the behavior is naturally LIFO, making a stack appropriate.

---

## Q2. What should happen when `..` occurs at the root?

### Model Answer

> Nothing should happen because an absolute Unix path cannot move above the root directory. Therefore, I only pop when the stack is non-empty.

That's why:

```python
if stack:
    stack.pop()
```

matters.

---

## Q3. Why do we ignore `.`?

### Model Answer

> A single dot represents the current directory, so it doesn't change the canonical path and can simply be ignored.

---

## Q4. What happens with multiple consecutive slashes?

Example:

```text
/home///user
```

### Model Answer

> Splitting produces empty components between consecutive slashes. I ignore those empty components, which effectively treats multiple slashes as a single separator.

---

## Q5. Is `"..."` treated like `".."`?

### Model Answer

> No. Only the exact components `"."` and `".."` have special meanings. A component such as `"..."` is treated as a normal directory name and pushed onto the stack.

This is a good interview edge case.

---

## Q6. Could you solve this without an explicit stack?

### Model Answer

> Yes, another list could be used to store the valid path components, but operationally that list is still functioning as a stack because we append normal directories and pop when processing `..`. The important idea is the LIFO behavior, not the container's name.

---

# 🧠 LC 71 Pattern Template

Memorize the decisions, not the exact code:

```text
          TOKEN
            │
     ┌──────┼──────────┐
     ↓      ↓          ↓
   "" / "." ".."    directory
     │      │          │
     ↓      ↓          ↓
  IGNORE   POP        PUSH
            │
            ↓
      only if stack
       isn't empty
```

Then:

```text
Stack
 ↓
Join with "/"
 ↓
Add leading "/"
 ↓
Canonical Path
```

---

# ⚡ Master Parsing + Stack Template

```python
stack = []

for token in tokens:

    if token_should_be_ignored:
        continue

    elif token_means_undo:
        if stack:
            stack.pop()

    else:
        stack.append(token)

return reconstruct(stack)
```

This pattern is much broader than filesystem paths.

It applies whenever the input contains:

```text
normal operation
      ↓
save

undo operation
      ↓
remove latest
```

---

# 🔥 LC 394 vs LC 71

You should understand why **both use stacks but for different reasons**.

|              | LC 394                         | LC 71                    |
| ------------ | ------------------------------ | ------------------------ |
| Problem      | Decode nested string           | Simplify filesystem path |
| Parsing      | Character-level                | Token-level              |
| Push when    | `[` encountered                | Directory encountered    |
| Pop when     | `]` encountered                | `..` encountered         |
| Stack stores | Previous string + repeat count | Directory names          |
| Why stack?   | Restore nested state           | Undo latest directory    |
| Core concept | Nested state                   | LIFO navigation          |

### LC 394

```text
[
↓
SAVE previous state

]
↓
RESTORE previous state
```

### LC 71

```text
directory
↓
PUSH

..
↓
POP
```

Same data structure.

Different reason for using it.

That distinction matters.

---

# 🏆 Layer 4 — Parsing + Stack COMPLETE

| Layer | Pattern                           | Problem   | Status |
| ----: | --------------------------------- | --------- | :----: |
|     1 | Traversal                         | LC 58     |    ✅   |
|     1 | Two Pointers                      | LC 344    |    ✅   |
|     1 | Two Pointers + Filtering          | LC 125    |    ✅   |
|     2 | Frequency HashMap                 | LC 242    |    ✅   |
|     2 | Two-Pass Frequency                | LC 387    |    ✅   |
|     2 | Bidirectional Mapping             | LC 205    |    ✅   |
|     2 | Bidirectional Mapping             | LC 290    |    ✅   |
|     3 | Variable Sliding Window + HashSet | LC 3      |    ✅   |
|     3 | Sliding Window + Frequency        | LC 424    |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 438    |    ✅   |
|     3 | Fixed Sliding Window + Frequency  | LC 567    |    ✅   |
|     4 | Parsing                           | LC 151    |    ✅   |
|     4 | Parsing + Nested Stack            | LC 394    |    ✅   |
|     4 | **Parsing + LIFO Stack**          | **LC 71** |    ✅   |

## 🎯 One-Line Takeaway

> **LC 71 teaches the "parse → classify → push/pop → reconstruct" pattern: normal directories are pushed, `..` undoes the latest directory, `.` and empty tokens are ignored, and the remaining stack is the canonical path.**


# Note: yet to complete the L5 & L6
