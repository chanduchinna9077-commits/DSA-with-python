# 🔴 2. STRINGS — 10 Problems

### Patterns

1. Traversal
2. Character classification
3. Reverse
4. Palindrome
5. Frequency
6. Hashing
7. Duplicate detection
8. Anagram
9. Word manipulation
10. Sliding Window/basic substring

### 10 Problems

| #  | Problem                             | Pattern             |
| -- | ----------------------------------- | ------------------- |
| 1  | Count Vowels/Consonants             | Traversal           |
| 2  | Count Uppercase/Lowercase/Digits    | Classification      |
| 3  | Reverse String                      | Two Pointer         |
| 4  | Palindrome String                   | Two Pointer         |
| 5  | Character Frequency                 | Hashing             |
| 6  | First Repeating Character           | Set                 |
| 7  | First Non-Repeating Character       | HashMap             |
| 8  | Valid Anagram                       | Frequency           |
| 9  | Reverse Words                       | String manipulation |
| 10 | Longest Substring Without Repeating | Sliding Window      |

---




👍

# 🔵 STRINGS — CONVERSATION 1

## Problems 1–4 of 10

We are following the **locked TopGun execution format** without reducing the depth.

### String Problem Roadmap

| # | Problem                                                 | Main Pattern                         |
| - | ------------------------------------------------------- | ------------------------------------ |
| 1 | Count Vowels and Consonants                             | Traversal + Character Classification |
| 2 | Count Uppercase, Lowercase, Digits & Special Characters | Character Classification             |
| 3 | Reverse a String                                        | Two Pointers / String Traversal      |
| 4 | Check Palindrome                                        | Two Pointers                         |

---

# 🔹 PROBLEM 1 — Count Vowels and Consonants

## 1. Problem Statement

Given a string, count how many **vowels** and **consonants** it contains.

### Example

```text
Input:
"Hello World"

Output:
Vowels = 3
Consonants = 7
```

Vowels are:

```text
a, e, i, o, u
```

Both uppercase and lowercase should be considered.

---

# 2. Problem Theory

A string is a sequence of characters.

For every character, we need to determine:

```text
Is it a vowel?
        ↓
      Yes → vowel_count++

        No
        ↓
Is it an alphabet?
        ↓
      Yes → consonant_count++
```

### Important

Spaces, digits and special characters are **not consonants**.

For:

```text
"Hello123!"
```

We process:

```text
H → consonant
e → vowel
l → consonant
l → consonant
o → vowel
1 → ignore
2 → ignore
3 → ignore
! → ignore
```

Result:

```text
Vowels = 2
Consonants = 3
```

---

# 3. Pattern Being Tested

### Pattern: Linear Traversal + Classification

This is one of the most basic string patterns.

The general structure is:

```python
for character in string:
    classify(character)
    update_counter()
```

You will use this pattern for:

* counting vowels
* counting consonants
* counting digits
* counting uppercase letters
* counting lowercase letters
* counting special characters
* character frequency
* validating strings

---

# 4. ELI10 Intuition 🧒

Imagine your teacher gives you a box containing letters:

```text
H e l l o
```

You pick one character at a time.

Ask:

> "Are you a vowel?"

If yes:

```text
vowels += 1
```

Otherwise, if it is an alphabet:

```text
consonants += 1
```

Keep doing this until the string is finished.

---

# 5. Example

```text
Input:
"Hello"

H → consonant
e → vowel
l → consonant
l → consonant
o → vowel
```

Therefore:

```text
Vowels = 2
Consonants = 3
```

---

# 6. Algorithm — Step-by-Step

### Algorithm

1. Read the string.
2. Create `vowel_count = 0`.
3. Create `consonant_count = 0`.
4. Traverse every character.
5. Convert/check the character in lowercase.
6. If the character is one of `a, e, i, o, u`, increment vowel count.
7. Otherwise, if it is an alphabet, increment consonant count.
8. Ignore digits, spaces and special characters.
9. Print both counts.

---

# 7. Python Solution — Using Built-in Methods

```python
s = input("Enter a string: ")

vowels = "aeiou"
vowel_count = 0
consonant_count = 0

for ch in s.lower():
    if ch in vowels:
        vowel_count += 1
    elif ch.isalpha():
        consonant_count += 1

print("Vowels =", vowel_count)
print("Consonants =", consonant_count)
```

### Example

```text
Enter a string: Hello World

Vowels = 3
Consonants = 7
```

---

# 8. Python Solution — Without Built-in Character Methods

Now we expose the actual logic.

```python
s = input("Enter a string: ")

vowels = "aeiouAEIOU"

vowel_count = 0
consonant_count = 0

for ch in s:

    if ch in vowels:
        vowel_count += 1

    elif ('a' <= ch <= 'z') or ('A' <= ch <= 'Z'):
        consonant_count += 1

print("Vowels =", vowel_count)
print("Consonants =", consonant_count)
```

Here we don't use:

```python
.lower()
.isalpha()
```

We manually determine whether the character is an alphabet.

---

# 9. Line-by-Line Explanation

```python
s = input("Enter a string: ")
```

Reads the string.

---

```python
vowels = "aeiouAEIOU"
```

Stores all possible vowels.

---

```python
vowel_count = 0
consonant_count = 0
```

Initially there are no vowels or consonants.

---

```python
for ch in s:
```

Visits every character.

For:

```text
Hello
```

the loop sees:

```text
H
e
l
l
o
```

---

```python
if ch in vowels:
```

Checks whether the current character is a vowel.

---

```python
vowel_count += 1
```

If yes, increase the vowel count.

---

```python
elif ('a' <= ch <= 'z') or ('A' <= ch <= 'Z'):
```

Checks whether the character is an alphabet.

---

```python
consonant_count += 1
```

If it's an alphabet but wasn't a vowel, it is a consonant.

---

# 10. Detailed Dry Run

Input:

```text
"Hello123!"
```

| Step | Character | Vowel? | Alphabet? | Vowels | Consonants |
| ---: | --------- | ------ | --------- | -----: | ---------: |
|    1 | H         | No     | Yes       |      0 |          1 |
|    2 | e         | Yes    | Yes       |      1 |          1 |
|    3 | l         | No     | Yes       |      1 |          2 |
|    4 | l         | No     | Yes       |      1 |          3 |
|    5 | o         | Yes    | Yes       |      2 |          3 |
|    6 | 1         | No     | No        |      2 |          3 |
|    7 | 2         | No     | No        |      2 |          3 |
|    8 | 3         | No     | No        |      2 |          3 |
|    9 | !         | No     | No        |      2 |          3 |

Final:

```text
Vowels = 2
Consonants = 3
```

---

# 11. Time Complexity

There are `n` characters.

We inspect each character exactly once.

```text
Time = O(n)
```

### Space

Only two counters are used:

```text
vowel_count
consonant_count
```

Therefore:

```text
Space = O(1)
```

---

# 12. Edge Cases

### Empty string

```text
""
```

Output:

```text
Vowels = 0
Consonants = 0
```

### Only spaces

```text
"     "
```

```text
Vowels = 0
Consonants = 0
```

### Only digits

```text
"123456"
```

```text
Vowels = 0
Consonants = 0
```

### All vowels

```text
"AEIOU"
```

```text
Vowels = 5
Consonants = 0
```

### All consonants

```text
"bcdfg"
```

```text
Vowels = 0
Consonants = 5
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Counting every non-vowel as consonant

Wrong:

```python
else:
    consonant_count += 1
```

Why?

Because:

```text
1
@
space
#
```

are not consonants.

---

### ❌ Mistake 2 — Handling only lowercase vowels

Wrong:

```python
if ch in "aeiou":
```

without converting uppercase letters.

Then:

```text
A E I O U
```

would not be counted.

---

### ❌ Mistake 3 — Forgetting spaces

For:

```text
"Hello World"
```

the space must be ignored.

---

# 14. Pattern Recognition

### When you see:

> "Count how many characters satisfy condition X"

Think:

```text
Linear Traversal
        ↓
Check condition
        ↓
Update counter
```

### Master template

```python
count = 0

for ch in s:
    if condition(ch):
        count += 1
```

This is a **very important TopGun basic pattern**.

---

# 🔹 PROBLEM 2 — Count Uppercase, Lowercase, Digits & Special Characters

## 1. Problem Statement

Given a string, count:

* uppercase letters
* lowercase letters
* digits
* special characters

### Example

```text
Input:
"Hello123@"

Output:
Uppercase = 1
Lowercase = 4
Digits = 3
Special = 1
```

---

# 2. Problem Theory

Every character belongs to a category.

```text
Character
   |
   ├── Uppercase?
   |
   ├── Lowercase?
   |
   ├── Digit?
   |
   └── Special character
```

We simply classify every character.

---

# 3. Pattern Being Tested

### Pattern: Character Classification

This pattern is extremely common in basic coding assessments.

Typical questions:

```text
Count uppercase
Count lowercase
Count digits
Count special characters
Validate password
Check alphanumeric string
```

---

# 4. ELI10 Intuition 🧒

Imagine four boxes:

```text
┌────────────┐
│ UPPERCASE  │
├────────────┤
│ lowercase  │
├────────────┤
│ DIGITS     │
├────────────┤
│ SPECIAL    │
└────────────┘
```

Take every character and put it into exactly one box.

---

# 5. Example

```text
"Abc123@X"
```

Classification:

```text
A → uppercase
b → lowercase
c → lowercase
1 → digit
2 → digit
3 → digit
@ → special
X → uppercase
```

Result:

```text
Uppercase = 2
Lowercase = 2
Digits = 3
Special = 1
```

---

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Create four counters.
3. Traverse every character.
4. Check whether it is uppercase.
5. Otherwise check lowercase.
6. Otherwise check digit.
7. Otherwise classify it as special.
8. Print all counters.

---

# 7. Python Solution — Using Built-in Methods

```python
s = input("Enter a string: ")

uppercase = 0
lowercase = 0
digits = 0
special = 0

for ch in s:

    if ch.isupper():
        uppercase += 1

    elif ch.islower():
        lowercase += 1

    elif ch.isdigit():
        digits += 1

    else:
        special += 1

print("Uppercase =", uppercase)
print("Lowercase =", lowercase)
print("Digits =", digits)
print("Special =", special)
```

---

# 8. Python Solution — Without Built-in Methods

```python
s = input("Enter a string: ")

uppercase = 0
lowercase = 0
digits = 0
special = 0

for ch in s:

    if 'A' <= ch <= 'Z':
        uppercase += 1

    elif 'a' <= ch <= 'z':
        lowercase += 1

    elif '0' <= ch <= '9':
        digits += 1

    else:
        special += 1

print("Uppercase =", uppercase)
print("Lowercase =", lowercase)
print("Digits =", digits)
print("Special =", special)
```

This version teaches you the actual character-range logic.

---

# 9. Line-by-Line Explanation

```python
uppercase = 0
lowercase = 0
digits = 0
special = 0
```

Four separate counters.

---

```python
for ch in s:
```

Process one character at a time.

---

```python
if 'A' <= ch <= 'Z':
```

Checks uppercase ASCII alphabet range.

---

```python
elif 'a' <= ch <= 'z':
```

Checks lowercase alphabet range.

---

```python
elif '0' <= ch <= '9':
```

Checks digit range.

---

```python
else:
```

Anything else is classified as special.

For example:

```text
@
#
$
!
%
```

---

# 10. Detailed Dry Run

Input:

```text
"Ab12@C#"
```

| Step | Character | Category | Upper | Lower | Digit | Special |
| ---: | --------- | -------- | ----: | ----: | ----: | ------: |
|    1 | A         | Upper    |     1 |     0 |     0 |       0 |
|    2 | b         | Lower    |     1 |     1 |     0 |       0 |
|    3 | 1         | Digit    |     1 |     1 |     1 |       0 |
|    4 | 2         | Digit    |     1 |     1 |     2 |       0 |
|    5 | @         | Special  |     1 |     1 |     2 |       1 |
|    6 | C         | Upper    |     2 |     1 |     2 |       1 |
|    7 | #         | Special  |     2 |     1 |     2 |       2 |

Final:

```text
Uppercase = 2
Lowercase = 1
Digits = 2
Special = 2
```

---

# 11. Time Complexity

Every character is processed once.

```text
Time = O(n)
```

Space:

```text
O(1)
```

---

# 12. Edge Cases

```text
"ABC"
```

→ all uppercase.

```text
"abc"
```

→ all lowercase.

```text
"12345"
```

→ all digits.

```text
"@#$%"
```

→ all special.

```text
""
```

→ all counts are zero.

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1

Using:

```python
if ch.isalpha():
```

and assuming this tells uppercase/lowercase.

It only tells you whether it's alphabetic.

You still need:

```python
isupper()
isupper/lower classification
```

---

### ❌ Mistake 2

Counting spaces as special without understanding the problem.

Whether spaces count as special depends on the exact problem statement.

Always check the expected definition.

---

# 14. Pattern Recognition

### When you see:

> "Count different types of characters"

Think:

```text
Traversal
   ↓
if / elif / else
   ↓
multiple counters
```

### Master template

```python
for ch in s:

    if condition_1:
        count_1 += 1

    elif condition_2:
        count_2 += 1

    elif condition_3:
        count_3 += 1

    else:
        count_4 += 1
```

This template is **high-value for screening tests**.

---

# 🔹 PROBLEM 3 — Reverse a String

## 1. Problem Statement

Given a string, reverse it.

### Example

```text
Input:
"hello"

Output:
"olleh"
```

---

# 2. Problem Theory

Reversing means changing:

```text
Original:
h e l l o

Reversed:
o l l e h
```

There are two major ways to think about this:

### Approach 1

Use Python's built-in slicing:

```python
s[::-1]
```

### Approach 2

Use the **two-pointer pattern**.

Start:

```text
left → first character
right → last character
```

Swap them.

Then move inward.

---

# 3. Pattern Being Tested

### Pattern: Two Pointers

This is one of the most important patterns in basic DSA.

```text
left →             ← right
```

Move:

```text
left += 1
right -= 1
```

Common applications:

* reverse array
* reverse string
* palindrome
* pair problems
* sorted-array problems

---

# 4. ELI10 Intuition 🧒

Imagine two children standing at opposite ends of a line.

```text
H E L L O
↑       ↑
L       R
```

They swap their positions:

```text
O E L L H
```

Then they move toward each other.

```text
O E L L H
  ↑   ↑
  L   R
```

Continue until they meet.

---

# 5. Example

```text
"hello"
```

Initial:

```text
h e l l o
↑       ↑
L       R
```

Swap:

```text
o e l l h
```

Move inward:

```text
o e l l h
  ↑   ↑
  L   R
```

Swap:

```text
o l l e h
```

Done.

---

# 6. Algorithm — Step-by-Step

### Manual algorithm

1. Convert the string into a mutable list of characters.
2. Set `left = 0`.
3. Set `right = len(chars) - 1`.
4. While `left < right`:

   * swap the characters
   * increment `left`
   * decrement `right`
5. Join the characters.
6. Print the reversed string.

Why convert to a list?

Because Python strings are **immutable**.

We cannot directly do:

```python
s[0] = 'x'
```

---

# 7. Python Solution — Using Built-in Method

The simplest solution:

```python
s = input("Enter a string: ")

reversed_string = s[::-1]

print("Reversed string =", reversed_string)
```

Example:

```text
Enter a string: hello
Reversed string = olleh
```

---

# 8. Python Solution — Without Built-in Reverse

```python
s = input("Enter a string: ")

chars = list(s)

left = 0
right = len(chars) - 1

while left < right:

    temp = chars[left]
    chars[left] = chars[right]
    chars[right] = temp

    left += 1
    right -= 1

reversed_string = ""

for ch in chars:
    reversed_string += ch

print("Reversed string =", reversed_string)
```

This exposes the actual two-pointer algorithm.

---

# 9. Line-by-Line Explanation

```python
chars = list(s)
```

Convert:

```text
"hello"
```

into:

```python
['h', 'e', 'l', 'l', 'o']
```

---

```python
left = 0
```

Start from the first position.

---

```python
right = len(chars) - 1
```

Start from the final position.

For five characters:

```text
right = 4
```

---

```python
while left < right:
```

Continue until the two pointers cross.

---

```python
temp = chars[left]
```

Save the left character.

---

```python
chars[left] = chars[right]
```

Put the right character on the left.

---

```python
chars[right] = temp
```

Put the original left character on the right.

---

```python
left += 1
right -= 1
```

Move toward the center.

---

# 10. Detailed Dry Run

Input:

```text
"HELLO"
```

Initial:

```text
H E L L O
↑       ↑
0       4
```

### Iteration 1

Swap:

```text
O E L L H
```

Pointers:

```text
0 → 1
4 → 3
```

---

### Iteration 2

```text
O E L L H
  ↑   ↑
  1   3
```

Swap:

```text
O L L E H
```

Pointers:

```text
left = 2
right = 2
```

Stop because:

```text
left < right
```

is false.

Final:

```text
OLLEH
```

---

# 11. Dry Run Table

|  Step | String    | Left | Right | Action     |
| ----: | --------- | ---: | ----: | ---------- |
| Start | H E L L O |    0 |     4 | —          |
|     1 | O E L L H |    1 |     3 | Swap H ↔ O |
|     2 | O L L E H |    2 |     2 | Swap E ↔ L |
|   End | O L L E H |    2 |     2 | Stop       |

---

# 12. Time Complexity

We process approximately half of the characters.

But asymptotically:

```text
Time = O(n)
```

The conversion to list and final construction also take O(n).

### Space

We create a list containing `n` characters:

```text
Space = O(n)
```

---

# 13. Edge Cases

### Empty string

```text
""
```

Output:

```text
""
```

### One character

```text
"a"
```

Output:

```text
"a"
```

### Two characters

```text
"ab"
```

Output:

```text
"ba"
```

### Spaces

```text
"hello world"
```

Reverse:

```text
"dlrow olleh"
```

The space remains a character.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Trying to modify a string directly

```python
s[0] = 'x'
```

Python doesn't allow this because strings are immutable.

---

### ❌ Mistake 2 — Wrong right pointer

Correct:

```python
right = len(chars) - 1
```

Not:

```python
right = len(chars)
```

---

### ❌ Mistake 3 — Using `<=` carelessly

Normally:

```python
while left < right:
```

is sufficient.

---

# 15. Pattern Recognition

### When you see:

> "Reverse something"

Immediately think:

```text
Two Pointers
```

Template:

```python
left = 0
right = len(arr) - 1

while left < right:
    swap(arr[left], arr[right])

    left += 1
    right -= 1
```

This exact thinking transfers directly to arrays.

---

# 🔹 PROBLEM 4 — Check Whether a String Is a Palindrome

## 1. Problem Statement

Given a string, determine whether it reads the same forward and backward.

### Examples

```text
"madam"
```

Forward:

```text
madam
```

Backward:

```text
madam
```

Therefore:

```text
Palindrome
```

Another:

```text
"hello"
```

Forward:

```text
hello
```

Backward:

```text
olleh
```

Therefore:

```text
Not Palindrome
```

---

# 2. Problem Theory

A palindrome has this property:

```text
s[i] == s[n - 1 - i]
```

We compare characters from both ends.

For:

```text
"madam"
```

```text
m a d a m
↑       ↑
```

Compare:

```text
m == m ✓
a == a ✓
d == d ✓
```

Everything matches.

Therefore it is a palindrome.

---

# 3. Pattern Being Tested

### Pattern: Two Pointers + Symmetry

This is an extremely important screening pattern.

It is essentially:

```text
Left side ↔ Right side
```

Applications:

* palindrome
* reverse string
* palindrome array
* valid palindrome
* comparing two ends

---

# 4. ELI10 Intuition 🧒

Imagine a word written on a piece of paper.

Two children stand at opposite ends.

```text
M A D A M
↑       ↑
```

They compare their letters.

If they are different:

```text
NOT palindrome
```

If they match:

```text
move inward
```

Continue until the middle.

---

# 5. Example

Input:

```text
"level"
```

Compare:

```text
l == l ✓
e == e ✓
v == v ✓
```

Therefore:

```text
Palindrome
```

---

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Set `left = 0`.
3. Set `right = len(s) - 1`.
4. While `left < right`:

   * compare `s[left]` and `s[right]`
5. If they are different:

   * immediately return/print `Not Palindrome`.
6. Otherwise move both pointers inward.
7. If all comparisons succeed:

   * print `Palindrome`.

---

# 7. Python Solution — Using Built-in Method

```python
s = input("Enter a string: ")

if s == s[::-1]:
    print("Palindrome")
else:
    print("Not Palindrome")
```

Example:

```text
Enter a string: madam
Palindrome
```

---

# 8. Python Solution — Without Built-in Reverse

```python
s = input("Enter a string: ")

left = 0
right = len(s) - 1

is_palindrome = True

while left < right:

    if s[left] != s[right]:
        is_palindrome = False
        break

    left += 1
    right -= 1

if is_palindrome:
    print("Palindrome")
else:
    print("Not Palindrome")
```

This is the important DSA version.

---

# 9. Line-by-Line Explanation

```python
left = 0
```

Start from the first character.

---

```python
right = len(s) - 1
```

Start from the final character.

---

```python
is_palindrome = True
```

Initially assume it is a palindrome.

We will change this if we find a mismatch.

---

```python
while left < right:
```

Compare characters until reaching the middle.

---

```python
if s[left] != s[right]:
```

If opposite characters don't match, it cannot be a palindrome.

---

```python
is_palindrome = False
```

Mark the answer as false.

---

```python
break
```

Stop immediately.

There is no reason to continue once a mismatch is found.

---

```python
left += 1
right -= 1
```

Move inward.

---

# 10. Detailed Dry Run

Input:

```text
"madam"
```

String positions:

```text
0 1 2 3 4
m a d a m
```

### Step 1

```text
left = 0
right = 4
```

Compare:

```text
s[0] = m
s[4] = m
```

Match ✓

Move:

```text
left = 1
right = 3
```

---

### Step 2

Compare:

```text
s[1] = a
s[3] = a
```

Match ✓

Move:

```text
left = 2
right = 2
```

Stop.

Therefore:

```text
Palindrome
```

---

# 11. Dry Run Table

| Step | Left | Right | Left Char | Right Char | Match? |
| ---: | ---: | ----: | --------- | ---------- | ------ |
|    1 |    0 |     4 | m         | m          | ✓      |
|    2 |    1 |     3 | a         | a          | ✓      |
|  End |    2 |     2 | —         | —          | Stop   |

---

# 12. Non-Palindrome Dry Run

Input:

```text
"hello"
```

| Step | Left | Right | Comparison |
| ---: | ---: | ----: | ---------- |
|    1 |    0 |     4 | h vs o ❌   |

Immediately:

```text
Not Palindrome
```

This is an important optimization:

> **Stop as soon as you find a mismatch.**

---

# 13. Time Complexity

Worst case:

```text
O(n)
```

We compare at most half the string, but:

```text
O(n/2) = O(n)
```

### Space

Only two pointers and one Boolean:

```text
O(1)
```

This is better than creating a reversed copy.

---

# 14. Edge Cases

### Empty string

```text
""
```

Generally considered a palindrome.

### One character

```text
"a"
```

Palindrome.

### Two equal characters

```text
"aa"
```

Palindrome.

### Two different characters

```text
"ab"
```

Not palindrome.

### Case sensitivity

```text
"Madam"
```

Depending on the problem, this may be considered **not** a palindrome because:

```text
M != m
```

If the problem says case-insensitive, normalize first.

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Comparing only adjacent characters

Wrong idea:

```text
m-a
a-d
d-a
a-m
```

Palindrome does **not** mean adjacent characters match.

We compare:

```text
first ↔ last
second ↔ second-last
```

---

### ❌ Mistake 2 — Forgetting `-1`

Correct:

```python
right = len(s) - 1
```

---

### ❌ Mistake 3 — Continuing after mismatch

Once:

```python
s[left] != s[right]
```

is found, the answer is already known.

Stop.

---

# 16. Pattern Recognition

### When you see:

> "Same from both ends"

Think:

# TWO POINTERS

Template:

```python
left = 0
right = len(s) - 1

while left < right:

    if s[left] != s[right]:
        # Not valid
        break

    left += 1
    right -= 1
```

This is one of the most important templates to memorize for TopGun.

---

# 🧠 STRINGS — CONVERSATION 1 PATTERN SUMMARY

We have now covered the first **4/10 string problems**.

| Problem                 | Core Pattern               | Key Idea               |
| ----------------------- | -------------------------- | ---------------------- |
| 1. Vowels & Consonants  | Traversal + Classification | Inspect each character |
| 2. Character Categories | Multiple Counters          | `if / elif / else`     |
| 3. Reverse String       | Two Pointers               | Swap from both ends    |
| 4. Palindrome           | Two Pointers               | Compare both ends      |

---

# 🔥 WHAT YOU SHOULD REMEMBER FOR THE SCREENING

There are **4 templates** from today's session.

### Template 1 — Count

```python
count = 0

for ch in s:
    if condition:
        count += 1
```

### Template 2 — Multiple Classification

```python
for ch in s:

    if condition_1:
        count1 += 1

    elif condition_2:
        count2 += 1

    else:
        count3 += 1
```

### Template 3 — Reverse

```python
left = 0
right = len(arr) - 1

while left < right:
    swap(arr[left], arr[right])

    left += 1
    right -= 1
```

### Template 4 — Compare From Both Ends

```python
left = 0
right = len(s) - 1

while left < right:

    if s[left] != s[right]:
        return False

    left += 1
    right -= 1

return True
```

---

# 🎯 TOPGUN PATTERN RECOGNITION

| If the question says...        | Immediately think...                   |
| ------------------------------ | -------------------------------------- |
| "Count characters..."          | **Traversal + Counter**                |
| "Count different types..."     | **Classification + Multiple Counters** |
| "Reverse..."                   | **Two Pointers**                       |
| "Same forward and backward..." | **Two Pointers + Comparison**          |
| "Ignore digits/symbols..."     | **Character classification**           |
| "Stop when mismatch..."        | **Early termination**                  |

### Current progress

```text
STRINGS
████░░░░░░  4 / 10
```

**Next in Strings — Conversation 2: Problems 5–8**

5. Character Frequency
6. First Repeating Character
7. First Non-Repeating Character
8. Valid Anagram

Would you like to continue with Strings — Conversation 2, Problems 5–8, or try a short unseen-string test first?


# 🔵 STRINGS — CONVERSATION 2

## Problems 5–8 of 10

We continue with the **locked TopGun execution format**. These four problems move from basic traversal into **hashing/frequency patterns**, which are extremely important for screening questions.

### Today's Roadmap

| # | Problem                       | Main Pattern                 |
| - | ----------------------------- | ---------------------------- |
| 5 | Character Frequency           | HashMap / Dictionary         |
| 6 | First Repeating Character     | Frequency + Traversal        |
| 7 | First Non-Repeating Character | Frequency + Second Traversal |
| 8 | Valid Anagram                 | Frequency Matching / Hashing |

---

# 🔹 PROBLEM 5 — Character Frequency

## 1. Problem Statement

Given a string, count how many times each character appears.

### Example

```text
Input:
"hello"

Output:
h → 1
e → 1
l → 2
o → 1
```

---

# 2. Problem Theory

This is a classic **frequency counting** problem.

We need a data structure that remembers:

```text
character → number of occurrences
```

For:

```text
"banana"
```

we build:

```text
b → 1
a → 3
n → 2
```

The ideal data structure is a **dictionary/hash map**.

In Python:

```python
frequency = {}
```

---

# 3. Pattern Being Tested

## Hashing / Frequency Map

The general pattern is:

```python
frequency = {}

for item in data:
    if item in frequency:
        frequency[item] += 1
    else:
        frequency[item] = 1
```

This pattern appears everywhere:

* character frequency
* element frequency
* duplicate detection
* anagrams
* first repeating character
* first non-repeating character
* counting pairs

---

# 4. ELI10 Intuition 🧒

Imagine you have boxes labeled with letters.

For:

```text
banana
```

You see `b`:

```text
b → 1
```

You see `a`:

```text
a → 1
```

Another `n`:

```text
n → 1
```

Another `a`:

```text
a → 2
```

Eventually:

```text
b → 1
a → 3
n → 2
```

The dictionary is basically your collection of counting boxes.

---

# 5. Example

```text
Input:
"programming"
```

Frequency:

```text
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

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Create an empty dictionary.
3. Traverse every character.
4. If the character already exists:

   * increase its count.
5. Otherwise:

   * create it with count `1`.
6. Print the dictionary.

---

# 7. Python Solution — Using Built-in Methods

Python provides `Counter` for frequency counting.

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

Process every character.

---

```python
if ch in frequency:
```

Ask:

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

If this is the first occurrence, create the entry.

---

# 10. Detailed Dry Run

Input:

```text
"banana"
```

### Step-by-step

| Step | Character | Dictionary           |
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

We traverse the string once.

Average dictionary lookup:

```text
O(1)
```

Therefore:

```text
Time = O(n)
```

### Space

In the worst case every character is different.

```text
Space = O(n)
```

---

# 12. Edge Cases

### Empty string

```text
""
```

Frequency:

```text
{}
```

### One character

```text
"a"
```

```text
a → 1
```

### All same

```text
"aaaa"
```

```text
a → 4
```

### All different

```text
"abcd"
```

```text
a → 1
b → 1
c → 1
d → 1
```

---

# 13. Common Mistakes / Traps

### ❌ Mistake 1 — Using a list and repeatedly counting

For every character:

```python
s.count(ch)
```

can lead to approximately:

```text
O(n²)
```

The dictionary gives us average:

```text
O(n)
```

---

### ❌ Mistake 2 — Forgetting to initialize

This would fail:

```python
frequency[ch] += 1
```

if `ch` isn't already present.

You need:

```python
if ch in frequency:
```

---

# 14. Pattern Recognition

When you see:

> "How many times does each X appear?"

Immediately think:

# HASH MAP / FREQUENCY DICTIONARY

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

# 🔹 PROBLEM 6 — First Repeating Character

## 1. Problem Statement

Given a string, find the **first character that appears more than once**.

### Example

```text
Input:
"abca"

Output:
a
```

Why?

```text
a → appears twice
b → once
c → once
```

The first repeating character when scanning from left to right is `a`.

---

# 2. Problem Theory

There is an important distinction:

### First repeating

Find the first character whose total frequency is greater than `1`.

Example:

```text
"abcbad"
```

Frequencies:

```text
a → 2
b → 2
c → 1
d → 1
```

Scanning from left:

```text
a → repeating
```

Answer:

```text
a
```

---

# 3. Pattern Being Tested

## Frequency Map + Traversal

This problem teaches an important two-phase pattern:

```text
Phase 1 → Count
Phase 2 → Find according to original order
```

This is different from simply finding the most frequent character.

---

# 4. ELI10 Intuition 🧒

First, make a notebook:

```text
a → 2
b → 2
c → 1
d → 1
```

Then walk through the original string:

```text
a b c b a d
↑
```

Ask:

> Does this character have frequency greater than 1?

`a` does.

So answer:

```text
a
```

---

# 5. Example

```text
"swiss"
```

Frequency:

```text
s → 3
w → 1
i → 1
```

Scan:

```text
s → frequency = 3
```

Answer:

```text
s
```

---

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Create a frequency dictionary.
3. Traverse the string and count every character.
4. Traverse the string again from left to right.
5. For each character:

   * if its frequency is greater than `1`, return it.
6. If none exists, print `"No repeating character"`.

---

# 7. Python Solution — Using Built-in Methods

```python
from collections import Counter

s = input("Enter a string: ")

frequency = Counter(s)

answer = None

for ch in s:
    if frequency[ch] > 1:
        answer = ch
        break

if answer is not None:
    print("First repeating character =", answer)
else:
    print("No repeating character")
```

---

# 8. Python Solution — Without Built-in Counter

```python
s = input("Enter a string: ")

frequency = {}

for ch in s:
    if ch in frequency:
        frequency[ch] += 1
    else:
        frequency[ch] = 1

answer = None

for ch in s:
    if frequency[ch] > 1:
        answer = ch
        break

if answer is not None:
    print("First repeating character =", answer)
else:
    print("No repeating character")
```

---

# 9. Line-by-Line Explanation

First phase:

```python
frequency = {}
```

Create the frequency map.

---

```python
for ch in s:
```

Count all characters.

---

Second phase:

```python
for ch in s:
```

Important:

We traverse the **original string**, not the dictionary.

Why?

Because we need to preserve the original order.

---

```python
if frequency[ch] > 1:
```

Check whether this character occurs more than once.

---

```python
break
```

Once we find the first repeating character, stop.

---

# 10. Detailed Dry Run

Input:

```text
"abcbad"
```

### Phase 1 — Frequency

| Character | Frequency |
| --------- | --------: |
| a         |         2 |
| b         |         2 |
| c         |         1 |
| d         |         1 |

### Phase 2 — Original order

| Position | Character | Frequency | Repeating? |
| -------: | --------- | --------: | ---------- |
|        0 | a         |         2 | ✅          |

Immediately stop.

Answer:

```text
a
```

---

# 11. Important Trap

Consider:

```text
"abcb"
```

Frequencies:

```text
a → 1
b → 2
c → 1
```

Answer:

```text
b
```

Now consider:

```text
"abcdaab"
```

Frequencies:

```text
a → 2
b → 2
c → 1
d → 1
```

Answer is:

```text
a
```

because `a` appears first in the original string among repeating characters.

---

# 12. Time Complexity

First traversal:

```text
O(n)
```

Second traversal:

```text
O(n)
```

Together:

```text
O(n + n) = O(n)
```

Space:

```text
O(n)
```

---

# 13. Edge Cases

### No repeating character

```text
"abcd"
```

Output:

```text
No repeating character
```

### All same

```text
"aaaa"
```

Answer:

```text
a
```

### Empty

```text
""
```

No repeating character.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Returning the most frequent character

These are different questions.

**First repeating:**

> Which repeating character appears earliest?

**Most frequent:**

> Which character has the largest count?

Do not confuse them.

---

### ❌ Mistake 2 — Iterating through the dictionary

The safest screening approach is:

```python
for ch in s:
```

because the original string establishes the required order.

---

# 15. Pattern Recognition

When you see:

> "First X according to original order, but X depends on frequency"

Think:

```text
COUNT FIRST
     ↓
SCAN ORIGINAL STRING
     ↓
CHECK FREQUENCY
```

This is a **very important pattern**.

---

# 🔹 PROBLEM 7 — First Non-Repeating Character

## 1. Problem Statement

Given a string, find the first character that appears **exactly once**.

### Example

```text
Input:
"swiss"

Output:
w
```

Frequencies:

```text
s → 3
w → 1
i → 1
```

Scanning from left:

```text
s → repeating
w → appears once
```

Therefore:

```text
w
```

---

# 2. Problem Theory

This is almost the reverse of Problem 6.

### First repeating:

```text
frequency[ch] > 1
```

### First non-repeating:

```text
frequency[ch] == 1
```

The important pattern remains:

```text
Frequency Map
       ↓
Original-order traversal
```

---

# 3. Pattern Being Tested

## Hashing + Two-Pass Traversal

This is a very common interview/screening pattern.

---

# 4. ELI10 Intuition 🧒

First count everything.

For:

```text
"swiss"
```

you get:

```text
s → 3
w → 1
i → 1
```

Now walk through the word:

```text
s → appears 3 times ❌
w → appears 1 time ✅
```

Stop.

Answer:

```text
w
```

---

# 5. Example

Input:

```text
"loveleetcode"
```

The first character whose frequency is `1` is:

```text
v
```

---

# 6. Algorithm — Step-by-Step

1. Read the string.
2. Create a frequency dictionary.
3. Count every character.
4. Traverse the original string again.
5. Check whether `frequency[ch] == 1`.
6. If yes, return that character.
7. If no character satisfies the condition, report that none exists.

---

# 7. Python Solution — Using Built-in Methods

```python
from collections import Counter

s = input("Enter a string: ")

frequency = Counter(s)

answer = None

for ch in s:
    if frequency[ch] == 1:
        answer = ch
        break

if answer is not None:
    print("First non-repeating character =", answer)
else:
    print("No non-repeating character")
```

---

# 8. Python Solution — Without Built-in Counter

```python
s = input("Enter a string: ")

frequency = {}

for ch in s:

    if ch in frequency:
        frequency[ch] += 1
    else:
        frequency[ch] = 1

answer = None

for ch in s:

    if frequency[ch] == 1:
        answer = ch
        break

if answer is not None:
    print("First non-repeating character =", answer)
else:
    print("No non-repeating character")
```

---

# 9. Line-by-Line Explanation

### Phase 1

```python
frequency = {}
```

Create the map.

---

```python
for ch in s:
```

Visit every character.

---

```python
if ch in frequency:
    frequency[ch] += 1
else:
    frequency[ch] = 1
```

Build frequencies.

---

### Phase 2

```python
for ch in s:
```

Again scan the original string.

---

```python
if frequency[ch] == 1:
```

We only want characters appearing exactly once.

---

```python
break
```

The first one is our answer.

---

# 10. Detailed Dry Run

Input:

```text
"swiss"
```

### Phase 1

| Character | Frequency |
| --------- | --------: |
| s         |         3 |
| w         |         1 |
| i         |         1 |

### Phase 2

| Position | Character | Frequency | Decision |
| -------: | --------- | --------: | -------- |
|        0 | s         |         3 | ❌        |
|        1 | w         |         1 | ✅        |

Answer:

```text
w
```

---

# 11. Another Example

Input:

```text
"aabbcdd"
```

Frequency:

```text
a → 2
b → 2
c → 1
d → 2
```

Traversal:

```text
a → 2 ❌
a → 2 ❌
b → 2 ❌
b → 2 ❌
c → 1 ✅
```

Answer:

```text
c
```

---

# 12. Time Complexity

Two traversals:

```text
O(n) + O(n)
```

Therefore:

```text
Time = O(n)
```

Space:

```text
O(n)
```

---

# 13. Edge Cases

### All repeating

```text
"abab"
```

No non-repeating character.

### One character

```text
"a"
```

Answer:

```text
a
```

### Empty string

No answer.

### Every character unique

```text
"abcd"
```

Answer:

```text
a
```

because the first character already appears once.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1

Stopping when you see the first character for the first time.

Wrong.

You must know its **total frequency** first.

---

### ❌ Mistake 2

Using:

```python
frequency[ch] > 1
```

That finds repeating characters.

For this problem we need:

```python
frequency[ch] == 1
```

---

# 15. Pattern Recognition

When you see:

> "First unique / first non-repeating"

Think:

```text
FREQUENCY MAP
      ↓
SCAN ORIGINAL ORDER
      ↓
frequency == 1
```

### Master template

```python
frequency = {}

for x in data:
    frequency[x] = frequency.get(x, 0) + 1

for x in data:
    if frequency[x] == 1:
        return x
```

This template is worth memorizing.

---

# 🔹 PROBLEM 8 — Valid Anagram

## 1. Problem Statement

Given two strings, determine whether they are **anagrams**.

Two strings are anagrams if they contain the **same characters with the same frequencies**, regardless of order.

### Example

```text
"listen"
"silent"
```

Both contain:

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

Therefore:

```text
Valid Anagram
```

---

# 2. Problem Theory

Anagram means:

```text
Same characters
+
Same frequency
+
Different order is allowed
```

Example:

```text
"race"
"care"
```

Both contain:

```text
r → 1
a → 1
c → 1
e → 1
```

So they are anagrams.

But:

```text
"rat"
"car"
```

are not.

Because:

```text
rat:
r → 1
a → 1
t → 1

car:
c → 1
a → 1
r → 1
```

Different characters.

---

# 3. Pattern Being Tested

## Frequency Map Comparison

This is one of the most important hashing patterns.

Think:

```text
String 1
   ↓
Frequency Map 1

String 2
   ↓
Frequency Map 2

Compare
   ↓
Same?
```

---

# 4. ELI10 Intuition 🧒

Imagine two bags.

Bag A:

```text
A A B C
```

Bag B:

```text
C A B A
```

The order inside the bags doesn't matter.

Both contain:

```text
A → 2
B → 1
C → 1
```

Therefore they match.

---

# 5. Example

```text
s1 = "anagram"
s2 = "nagaram"
```

Frequency:

```text
a → 3
n → 1
g → 1
r → 1
m → 1
```

Both are identical.

Therefore:

```text
Valid Anagram
```

---

# 6. Algorithm — Step-by-Step

### Hashing approach

1. Read two strings.
2. If their lengths are different:

   * immediately return false.
3. Create a frequency dictionary for the first string.
4. Traverse the second string.
5. For each character:

   * if it does not exist in the frequency map, return false.
   * decrease its frequency.
6. If all frequencies become zero, the strings are anagrams.
7. Otherwise they are not.

---

# 7. Python Solution — Using Built-in Methods

The simplest built-in approach is sorting.

```python
s1 = input("Enter first string: ")
s2 = input("Enter second string: ")

if sorted(s1) == sorted(s2):
    print("Valid Anagram")
else:
    print("Not Anagram")
```

Example:

```text
Enter first string: listen
Enter second string: silent

Valid Anagram
```

### Complexity

Sorting:

```text
O(n log n)
```

---

# 8. Python Solution — Without Built-in Sorting

Now use the actual hashing pattern.

```python
s1 = input("Enter first string: ")
s2 = input("Enter second string: ")

if len(s1) != len(s2):
    print("Not Anagram")

else:

    frequency = {}

    for ch in s1:

        if ch in frequency:
            frequency[ch] += 1
        else:
            frequency[ch] = 1

    is_anagram = True

    for ch in s2:

        if ch not in frequency:
            is_anagram = False
            break

        frequency[ch] -= 1

        if frequency[ch] < 0:
            is_anagram = False
            break

    if is_anagram:
        print("Valid Anagram")
    else:
        print("Not Anagram")
```

---

# 9. Line-by-Line Explanation

### Step 1 — Length check

```python
if len(s1) != len(s2):
```

If lengths differ, they cannot contain exactly the same characters.

Example:

```text
"abc" → 3
"abcd" → 4
```

Immediately:

```text
Not Anagram
```

This is an optimization.

---

### Step 2 — Build frequency

```python
frequency = {}
```

Then count characters from the first string.

For:

```text
"listen"
```

we get:

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

---

### Step 3 — Consume using second string

For every character in `s2`:

```python
frequency[ch] -= 1
```

If the strings are anagrams, every count should eventually become zero.

---

# 10. Detailed Dry Run

Input:

```text
s1 = "listen"
s2 = "silent"
```

### Build frequency from `s1`

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

Now process `s2`.

| Step | Character | Frequency after processing |
| ---: | --------- | -------------------------- |
|    1 | s         | s → 0                      |
|    2 | i         | i → 0                      |
|    3 | l         | l → 0                      |
|    4 | e         | e → 0                      |
|    5 | n         | n → 0                      |
|    6 | t         | t → 0                      |

All characters successfully consumed.

Therefore:

```text
Valid Anagram
```

---

# 11. Important Counterexample

Consider:

```text
s1 = "aab"
s2 = "abb"
```

Both have length `3`.

Frequency of `s1`:

```text
a → 2
b → 1
```

Process `s2`:

```text
a → 1
b → 0
b → -1
```

We now have too many `b`s.

Therefore:

```text
Not Anagram
```

This is why the negative-frequency check is useful.

---

# 12. Time Complexity

### Built-in sorting approach

```text
sorted(s1)
sorted(s2)
```

Each takes:

```text
O(n log n)
```

Therefore:

```text
Time = O(n log n)
```

---

### Hashing approach

Build frequency:

```text
O(n)
```

Process second string:

```text
O(n)
```

Total:

```text
O(n)
```

### Space

Frequency dictionary:

```text
O(n)
```

Therefore the optimal general hashing solution is:

```text
Time  = O(n)
Space = O(n)
```

---

# 13. Edge Cases

### Different lengths

```text
"abc"
"abcd"
```

Not anagram.

---

### Empty strings

```text
""
""
```

Mathematically they contain the same multiset of characters, so this is generally considered a valid anagram.

---

### Same characters, different order

```text
"abc"
"bca"
```

Valid.

---

### Different frequency

```text
"aabb"
"abbb"
```

Not valid.

---

### Case sensitivity

```text
"Listen"
"silent"
```

Depending on the problem, uppercase/lowercase may be treated differently.

Always check whether the problem requires case-insensitive comparison.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Checking only whether characters exist

This is insufficient.

For:

```text
"aab"
"abb"
```

all characters `a` and `b` exist in both.

But frequencies differ.

Anagrams require:

```text
same characters
+
same frequencies
```

---

### ❌ Mistake 2 — Forgetting length check

Different lengths automatically mean:

```text
Not Anagram
```

---

### ❌ Mistake 3 — Thinking order matters

These are anagrams:

```text
"abc"
"cba"
```

Order doesn't matter.

Frequency does.

---

# 15. Pattern Recognition

When you see:

> "Are these two strings made from the same characters?"

Immediately think:

# FREQUENCY MAP

Template:

```python
frequency = {}

for ch in s1:
    frequency[ch] = frequency.get(ch, 0) + 1

for ch in s2:
    if ch not in frequency:
        return False

    frequency[ch] -= 1

return True
```

---

# 🧠 STRINGS — CONVERSATION 2 SUMMARY

You have now completed **8/10 string problems**.

| # | Problem             | Core Pattern         | Key Skill         |
| - | ------------------- | -------------------- | ----------------- |
| 5 | Character Frequency | Hashing              | Count occurrences |
| 6 | First Repeating     | Hashing + Traversal  | `frequency > 1`   |
| 7 | First Non-Repeating | Hashing + Traversal  | `frequency == 1`  |
| 8 | Valid Anagram       | Frequency Comparison | Same counts       |

---

# 🔥 THE MOST IMPORTANT PATTERN FROM TODAY

Problems **5, 6, 7 and 8** are not four completely separate ideas.

They are mostly one master pattern:

```text
                 STRING
                    ↓
             BUILD FREQUENCY
                    ↓
          ┌─────────┴─────────┐
          ↓                   ↓
   Need frequency?      Need original order?
          ↓                   ↓
    Frequency Map       Scan original string
          ↓                   ↓
       Answer              Answer
```

### Memorize these four conditions:

```python
frequency[ch] += 1
```

→ Count character

```python
frequency[ch] > 1
```

→ Repeating character

```python
frequency[ch] == 1
```

→ Non-repeating character

```python
frequency1 == frequency2
```

→ Anagram

---

# 🎯 TOPGUN SCREENING RECOGNITION

| Question wording                     | Pattern                        |
| ------------------------------------ | ------------------------------ |
| "Count occurrences"                  | HashMap                        |
| "Frequency of each character"        | HashMap                        |
| "First repeating"                    | Frequency + original traversal |
| "First unique/non-repeating"         | Frequency + original traversal |
| "Same characters in different order" | Anagram + frequency            |
| "Duplicate characters"               | Hashing                        |
| "Most/least frequent"                | Frequency map                  |

---

## 📈 STRING PROGRESS

```text
Problems completed: 8 / 10

████████░░ 80%
```

### Remaining — Conversation 3

**9. Reverse Words in a String**
→ String splitting/traversal

**10. Longest Substring Without Repeating Characters**
→ Basic Sliding Window + Hashing

After Problem 10, the String topic will get a **mastery revision + pattern recognition + mini TopGun test**, so the 10 problems become usable patterns rather than just solved questions.

Would you like to continue with Problems 9–10, or try a short unseen-string test first?

# 🔵 STRINGS — CONVERSATION 3

## Problems 9–10 + Topic Mastery

We continue with the **locked version**: full theory → pattern → ELI10 → algorithm → built-in solution → no-built-in solution → line-by-line explanation → detailed dry run → complexity → edge cases → traps → pattern recognition.

---

# 🔹 PROBLEM 9 — Reverse Words in a String

## 1. Problem Statement

Given a sentence, reverse the **order of the words**.

### Example

```text
Input:
"hello world python"

Output:
"python world hello"
```

⚠️ Important:

We are **not reversing the characters inside each word**.

Wrong:

```text
olleh dlrow nohtyp
```

Correct:

```text
python world hello
```

---

# 2. Problem Theory

There are two different operations:

### Reverse characters

```text
hello → olleh
```

### Reverse word order

```text
hello world → world hello
```

This problem asks for **word-order reversal**.

The main idea:

```text
Sentence
   ↓
Separate words
   ↓
Reverse word order
   ↓
Join words
```

---

# 3. Pattern Being Tested

## String Traversal + Word Processing

This teaches an important screening pattern:

```text
String
  ↓
Words
  ↓
Process words
  ↓
Construct result
```

This appears in:

* reverse words
* count words
* longest word
* shortest word
* word frequency
* remove extra spaces
* sentence processing

---

# 4. ELI10 Intuition 🧒

Imagine:

```text
"I love coding"
```

There are three cards:

```text
[I] [love] [coding]
```

Turn the cards around:

```text
[coding] [love] [I]
```

So the answer is:

```text
coding love I
```

We don't turn the letters inside each card.

---

# 5. Example

Input:

```text
"I love Python"
```

Words:

```text
I
love
Python
```

Reverse the order:

```text
Python
love
I
```

Final:

```text
"Python love I"
```

---

# 6. Algorithm — Step-by-Step

### Approach

1. Read the sentence.
2. Separate it into words.
3. Start from the last word.
4. Add each word to the result.
5. Continue until the first word.
6. Join the words with spaces.
7. Print the result.

---

# 7. Python Solution — Using Built-in Methods

```python
s = input("Enter a sentence: ")

words = s.split()

words.reverse()

result = " ".join(words)

print("Reversed words =", result)
```

### Example

```text
Enter a sentence: I love Python

Reversed words = Python love I
```

---

# 8. Python Solution — Without Built-in Reverse

We can still use `split()` because the main DSA challenge here is reversing the **word order**, not implementing Python's parser.

```python
s = input("Enter a sentence: ")

words = s.split()

result = []

i = len(words) - 1

while i >= 0:
    result.append(words[i])
    i -= 1

answer = ""

for i in range(len(result)):
    
    answer += result[i]

    if i != len(result) - 1:
        answer += " "

print("Reversed words =", answer)
```

This version exposes the actual traversal.

---

# 9. Line-by-Line Explanation

```python
words = s.split()
```

Converts:

```text
"I love Python"
```

into:

```python
["I", "love", "Python"]
```

---

```python
i = len(words) - 1
```

Start at the last word.

For three words:

```text
i = 2
```

---

```python
while i >= 0:
```

Move backwards through the word list.

---

```python
result.append(words[i])
```

Add the current word.

---

```python
i -= 1
```

Move toward the first word.

---

```python
answer += result[i]
```

Build the final sentence.

---

# 10. Detailed Dry Run

Input:

```text
"I love Python"
```

Initial:

```text
words = ["I", "love", "Python"]
```

### Iteration 1

```text
i = 2
words[2] = "Python"
```

Result:

```text
["Python"]
```

### Iteration 2

```text
i = 1
words[1] = "love"
```

Result:

```text
["Python", "love"]
```

### Iteration 3

```text
i = 0
words[0] = "I"
```

Result:

```text
["Python", "love", "I"]
```

Final:

```text
"Python love I"
```

---

# 11. Dry Run Table

| Step | `i` | Selected word | Result        |
| ---: | --: | ------------- | ------------- |
|    1 |   2 | Python        | Python        |
|    2 |   1 | love          | Python love   |
|    3 |   0 | I             | Python love I |

---

# 12. Time Complexity

Let `n` be the number of characters.

Splitting:

```text
O(n)
```

Traversing words:

```text
O(n)
```

Building result:

```text
O(n)
```

Overall:

```text
Time = O(n)
```

### Space

The words and result require additional memory:

```text
Space = O(n)
```

---

# 13. Edge Cases

### Single word

```text
"Python"
```

Output:

```text
"Python"
```

### Empty string

```text
""
```

Output:

```text
""
```

### Multiple spaces

```text
"I   love   Python"
```

Using `split()` normalizes the spaces:

```text
"Python love I"
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Reversing characters instead of words

```text
"I love Python"
```

Do not produce:

```text
"nohtyP evol I"
```

---

### ❌ Mistake 2 — Forgetting word order

The answer must start with the **last word**.

---

### ❌ Mistake 3 — Extra spaces

Avoid producing:

```text
"Python  love  I"
```

unless the problem specifically asks to preserve spaces.

---

# 15. Pattern Recognition

When you see:

> "Reverse the order of words"

Think:

```text
STRING
  ↓
WORDS
  ↓
TRAVERSE FROM RIGHT → LEFT
  ↓
BUILD RESULT
```

### Master template

```python
words = s.split()

i = len(words) - 1

while i >= 0:
    process(words[i])
    i -= 1
```

---

# 🔹 PROBLEM 10 — Longest Substring Without Repeating Characters

## 1. Problem Statement

Given a string, find the length of the **longest substring containing no repeated characters**.

### Example

```text
Input:
"abcabcbb"

Output:
3
```

The longest substring is:

```text
"abc"
```

Length:

```text
3
```

---

# 2. Problem Theory

This introduces one of the most important DSA patterns:

# SLIDING WINDOW

A **substring** means characters must be continuous.

For:

```text
"abcabcbb"
```

Possible substrings:

```text
abc
bca
cab
```

But:

```text
ac
```

is not a substring because characters were skipped.

---

# 3. Pattern Being Tested

## Sliding Window + HashSet

The window represents:

```text
[left ........ right]
```

We maintain a window where:

> **Every character is unique.**

When we encounter a duplicate, we move `left` forward until the duplicate disappears.

---

# 4. ELI10 Intuition 🧒

Imagine a window moving across the string.

```text
a b c a b c b b
↑     ↑
L     R
```

Initially:

```text
abc
```

Everything is unique.

Then we encounter another:

```text
a
```

But `a` is already inside the window.

So we shrink the window from the left.

Eventually:

```text
b c a
```

Again, all characters are unique.

We keep doing this and remember the largest window.

---

# 5. Example

Input:

```text
"abcabcbb"
```

Start:

```text
a
```

Length = 1

Then:

```text
ab
```

Length = 2

Then:

```text
abc
```

Length = 3

Next character:

```text
a
```

Duplicate.

Shrink from left until `a` can be added again.

Continue.

Maximum length remains:

```text
3
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty set called `seen`.
2. Set `left = 0`.
3. Set `maximum = 0`.
4. Move `right` through the string.
5. If `s[right]` is already in `seen`:

   * remove `s[left]`
   * move `left` forward.
6. Continue until the current character is no longer duplicated.
7. Add the current character to `seen`.
8. Calculate current window length:

   ```text
   right - left + 1
   ```
9. Update maximum.
10. Continue until the string ends.

---

# 7. Python Solution — Using Built-in Methods

A simple screening-friendly version:

```python
s = input("Enter a string: ")

maximum = 0

for i in range(len(s)):
    current = ""

    for j in range(i, len(s)):

        if s[j] in current:
            break

        current += s[j]

        maximum = max(maximum, len(current))

print("Longest length =", maximum)
```

This is easy to understand, but it is **O(n²)**.

---

# 8. Python Solution — Without Built-in High-Level Logic

Now the important optimized DSA solution.

```python
s = input("Enter a string: ")

seen = set()

left = 0
maximum = 0

for right in range(len(s)):

    while s[right] in seen:
        seen.remove(s[left])
        left += 1

    seen.add(s[right])

    current_length = right - left + 1

    if current_length > maximum:
        maximum = current_length

print("Longest length =", maximum)
```

This is the version you should understand for DSA.

---

# 9. Line-by-Line Explanation

### Create the set

```python
seen = set()
```

This stores characters currently inside our window.

---

```python
left = 0
```

Left boundary of the window.

---

```python
maximum = 0
```

Stores the largest valid window found so far.

---

```python
for right in range(len(s)):
```

Move the right boundary one character at a time.

---

```python
while s[right] in seen:
```

If the new character already exists inside the window, we have a duplicate.

---

```python
seen.remove(s[left])
```

Remove the leftmost character.

---

```python
left += 1
```

Shrink the window.

---

```python
seen.add(s[right])
```

Once the window is valid, add the new character.

---

```python
current_length = right - left + 1
```

Calculate window size.

Example:

```text
left = 2
right = 5
```

Then:

```text
5 - 2 + 1 = 4
```

---

```python
if current_length > maximum:
    maximum = current_length
```

Keep the largest window.

---

# 10. Detailed Dry Run

Input:

```text
"abcabcbb"
```

We'll track:

```text
left
right
character
seen
window
maximum
```

| Right | Char | Action             | Window | Length | Max |
| ----: | ---- | ------------------ | ------ | -----: | --: |
|     0 | a    | Add                | `a`    |      1 |   1 |
|     1 | b    | Add                | `ab`   |      2 |   2 |
|     2 | c    | Add                | `abc`  |      3 |   3 |
|     3 | a    | Remove old a       | `bca`  |      3 |   3 |
|     4 | b    | Remove old b       | `cab`  |      3 |   3 |
|     5 | c    | Remove old c       | `abc`  |      3 |   3 |
|     6 | b    | Remove until valid | `cb`   |      2 |   3 |
|     7 | b    | Remove old b       | `b`    |      1 |   3 |

Final:

```text
Longest length = 3
```

---

# 11. Let's Understand the Duplicate Step Carefully

At:

```text
abcab
```

Suppose:

```text
seen = {a, b, c}
```

and current character is:

```text
b
```

`b` already exists.

So:

```text
while b in seen:
```

Remove:

```text
a
```

Window becomes conceptually:

```text
bc
```

But `b` is still present.

Remove:

```text
b
```

Now:

```text
c
```

Add new `b`:

```text
cb
```

Now every character is unique again.

This is the heart of the sliding-window pattern.

---

# 12. Complexity

## Simple solution

The nested loops can revisit characters.

```text
Time = O(n²)
Space = O(n)
```

---

## Optimized sliding window

Although there is a `while` loop inside the `for` loop, each character enters and leaves the set at most once.

Therefore:

```text
Time = O(n)
```

Space:

```text
O(n)
```

---

# 13. Why Isn't It O(n²)?

This is a common interview question.

We have:

```python
for right in range(n):
```

and:

```python
while s[right] in seen:
```

It looks like nested loops.

But `left` only moves **forward**.

Across the entire algorithm:

```text
left: 0 → 1 → 2 → ... → n
```

It cannot move backward.

Therefore each character is removed at most once.

So total work is:

```text
right movements = O(n)
left movements  = O(n)
```

Therefore:

```text
O(n + n) = O(n)
```

---

# 14. Edge Cases

### Empty string

```text
""
```

Answer:

```text
0
```

### One character

```text
"a"
```

Answer:

```text
1
```

### All unique

```text
"abcdef"
```

Answer:

```text
6
```

### All same

```text
"aaaa"
```

Answer:

```text
1
```

### Example

```text
"pwwkew"
```

Longest valid substring:

```text
"wke"
```

Length:

```text
3
```

---

# 15. Common Mistakes / Traps

### ❌ Mistake 1 — Confusing substring with subsequence

Substring:

```text
continuous
```

Subsequence:

```text
can skip characters
```

This problem asks for a substring.

---

### ❌ Mistake 2 — Resetting the entire window

When a duplicate occurs, don't reset everything.

Only shrink enough to remove the duplicate.

---

### ❌ Mistake 3 — Forgetting `+1`

Window length is:

```python
right - left + 1
```

Not:

```python
right - left
```

---

### ❌ Mistake 4 — Using a list for membership

This:

```python
if s[right] in seen_list:
```

can take O(n).

A set provides average:

```text
O(1)
```

membership checking.

---

# 16. Pattern Recognition

When you see:

> "Longest/shortest contiguous substring satisfying a condition"

Think:

# SLIDING WINDOW

Typical clues:

```text
Longest substring
Shortest substring
At most K
At least K
No duplicates
Maximum/minimum window
Continuous segment
```

Basic template:

```python
left = 0

for right in range(len(data)):

    while window_is_invalid:
        remove(data[left])
        left += 1

    add(data[right])

    update_answer()
```

This template is **extremely important**.

---

# 🧠 STRINGS — ALL 10 PROBLEMS COMPLETE

|  # | Problem                   | Main Pattern               |
| -: | ------------------------- | -------------------------- |
|  1 | Count Vowels & Consonants | Traversal + Classification |
|  2 | Count Character Types     | Multiple Counters          |
|  3 | Reverse String            | Two Pointers               |
|  4 | Palindrome                | Two Pointers               |
|  5 | Character Frequency       | Hashing                    |
|  6 | First Repeating           | Frequency + Traversal      |
|  7 | First Non-Repeating       | Frequency + Traversal      |
|  8 | Valid Anagram             | Frequency Comparison       |
|  9 | Reverse Words             | Word Traversal             |
| 10 | Longest Unique Substring  | Sliding Window + Hashing   |

---

# 🔥 STRING MASTER PATTERN MAP

Don't memorize 10 independent solutions.

Compress them into **5 patterns**.

```text
STRINGS
│
├── 1. LINEAR TRAVERSAL
│      ├── Vowels
│      └── Character classification
│
├── 2. TWO POINTERS
│      ├── Reverse string
│      └── Palindrome
│
├── 3. FREQUENCY HASHING
│      ├── Character frequency
│      ├── First repeating
│      ├── First non-repeating
│      └── Anagram
│
├── 4. WORD PROCESSING
│      └── Reverse words
│
└── 5. SLIDING WINDOW
       └── Longest unique substring
```

---

# 🧠 STRING MASTER TEMPLATES

## Template 1 — Character Traversal

```python
for ch in s:
    # process character
```

---

## Template 2 — Frequency Map

```python
frequency = {}

for ch in s:
    if ch in frequency:
        frequency[ch] += 1
    else:
        frequency[ch] = 1
```

---

## Template 3 — Two Pointers

```python
left = 0
right = len(s) - 1

while left < right:

    # compare / swap

    left += 1
    right -= 1
```

---

## Template 4 — Frequency + Original Order

```python
frequency = {}

for ch in s:
    frequency[ch] = frequency.get(ch, 0) + 1

for ch in s:
    if frequency[ch] == 1:
        # answer
        break
```

---

## Template 5 — Sliding Window

```python
seen = set()
left = 0

for right in range(len(s)):

    while condition_is_invalid:
        seen.remove(s[left])
        left += 1

    seen.add(s[right])

    # update answer
```

---

# 🎯 SENIOR PATTERN RECOGNITION

For the TopGun screening, train yourself to translate the **question wording** into the algorithm.

| Question clue                 | Think                                    |
| ----------------------------- | ---------------------------------------- |
| Count each character          | **Frequency Map**                        |
| Duplicate characters          | **Hashing**                              |
| First repeating               | **Frequency + original traversal**       |
| First unique                  | **Frequency + original traversal**       |
| Same letters, different order | **Anagram / Frequency Map**              |
| Reverse                       | **Two Pointers**                         |
| Same from both ends           | **Palindrome / Two Pointers**            |
| Reverse word order            | **Split + reverse traversal**            |
| Longest substring             | **Sliding Window**                       |
| No repeated characters        | **Sliding Window + Set**                 |
| Continuous characters         | **Substring / Sliding Window candidate** |

---

# 🏆 STRINGS — MASTERY CHECK

Before moving to Hashing, you should be able to identify the pattern **without looking at the solution**.

### Question 1

> Find the number of vowels in a string.

Think:

```text
Traversal + Counter
```

### Question 2

> Reverse a string without using `[::-1]`.

Think:

```text
Two Pointers
```

### Question 3

> Determine whether `"race"` and `"care"` are anagrams.

Think:

```text
Frequency Map
```

### Question 4

> Find the first character appearing only once.

Think:

```text
Frequency Map + Original Traversal
```

### Question 5

> Find the longest continuous part of a string with no repeated characters.

Think:

```text
Sliding Window + Hashing
```

---

# 📊 TOPGUN DSA PROGRESS

```text
ARRAYS
██████████ 10/10 ✅

STRINGS
██████████ 10/10 ✅
```

### Strings are now **covered at the basic screening level**.

But one important distinction:

> **10 problems = pattern foundation, not automatic mastery.**

For actual mastery, you should be able to solve variations without remembering the exact code.

The next topic in our locked 12-topic sequence is:

# 🔵 HASHING — CONVERSATION 1

## Problems 1–4

1. Character Frequency
2. Element Frequency
3. Contains Duplicate
4. First Repeating Element

Would you like to start Hashing with Problems 1–4 now, or do a short strings mastery test first?
