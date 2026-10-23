
# 🟣 DAY 3

## STRING FUNDAMENTALS

### Problems 21–30

```text
Reverse String
Palindrome String
Vowels & Consonants
Character Types
Remove Spaces
Remove Duplicates
Character Frequency
Anagram
First Non-Repeating Character
Toggle Case
```

### 🎯 Skill

**Character manipulation + frequency**

---

# 🔥 DAY 3 — SESSION 1

## STRING FUNDAMENTALS — Problems 21–23

We continue with the **exact locked CR2 depth**.

No reduction in:

* Senior insights
* Problem understanding
* Logic/intuitions
* Algorithm step-by-step
* Python + Java
* Detailed dry run
* Complexity derivation
* Interview Q&A
* Pattern extraction
* Common mistakes
* Interview-ready summary

---

# 🎯 DAY 3 — SESSION 1

| #  | Problem                   | Core Pattern                     | LeetCode              |
| -- | ------------------------- | -------------------------------- | --------------------- |
| 21 | Reverse a String          | Two Pointers / In-place reversal | LC 344 — Easy         |
| 22 | Check Palindrome String   | Two Pointers                     | LC 125 — Easy         |
| 23 | Count Vowels & Consonants | Character Classification         | No exact canonical LC |

### 🧠 Today's progression

```text
Reverse String
      ↓
Two Pointers

Palindrome String
      ↓
Two Pointers + Comparison

Vowels / Consonants
      ↓
Character Classification
```

This is your first serious transition from **number logic → string logic**.

---

# 🔥 PROBLEM 21 — REVERSE A STRING

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

Given a string, reverse the order of its characters.

Example:

```text
Input:
hello

Output:
olleh
```

### LeetCode Match

🔥 **LC 344 — Reverse String**

Difficulty: **Easy**

---

## 🚨 Senior Insight

There are several ways to reverse a string in Python:

```python
s[::-1]
```

or:

```python
"".join(reversed(s))
```

Both are valid Python.

But if this is an interview problem, the deeper pattern being tested is often:

# 👉 Two Pointers

Use:

```text
left  → beginning
right → end
```

Swap:

```text
s[left] ↔ s[right]
```

Then:

```text
left += 1
right -= 1
```

until:

```text
left >= right
```

### Why learn this if Python has slicing?

Because **two pointers is a reusable DSA pattern**.

It appears in:

* Palindrome checking
* Array reversal
* Two Sum on sorted arrays
* Removing duplicates
* Partitioning
* String manipulation

So don't just memorize:

```python
s[::-1]
```

Understand the underlying algorithm.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
s = "hello"
```

Reverse it:

```text
hello
 ↓
olleh
```

Character positions:

```text
Index:
0 1 2 3 4

h e l l o
```

We swap:

```text
h ↔ o
e ↔ l
```

Middle `l` stays where it is.

Result:

```text
o l l e h
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine two people standing at opposite ends of a line:

```text
h e l l o
↑       ↑
L       R
```

Swap them:

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

Move again:

```text
o l l e h
    ↑
   L/R
```

They meet.

Stop.

### 🔥 The reusable idea

```text
left = 0
right = len(s) - 1

while left < right:
    swap
    left += 1
    right -= 1
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Convert the string into a mutable character list.
2. Set:

   ```text
   left = 0
   right = len(s) - 1
   ```
3. While:

   ```text
   left < right
   ```
4. Swap:

   ```text
   characters[left]
   characters[right]
   ```
5. Move both pointers inward.
6. Convert the character list back to a string.
7. Return it.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def reverse_string(s):

    chars = list(s)

    left = 0
    right = len(chars) - 1

    while left < right:

        chars[left], chars[right] = chars[right], chars[left]

        left += 1
        right -= 1

    return "".join(chars)


s = input("Enter a string: ")

print("Reversed string:", reverse_string(s))
```

### Example

```text
Input:
hello

Output:
Reversed string: olleh
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static String reverseString(String s) {

        char[] chars = s.toCharArray();

        int left = 0;
        int right = chars.length - 1;

        while (left < right) {

            char temp = chars[left];

            chars[left] = chars[right];

            chars[right] = temp;

            left++;
            right--;
        }

        return new String(chars);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String s = sc.nextLine();

        System.out.println("Reversed string: " + reverseString(s));

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
hello
```

Convert:

```text
chars = ['h', 'e', 'l', 'l', 'o']
```

Initial:

```text
left = 0
right = 4
```

Visual:

```text
h  e  l  l  o
↑           ↑
L           R
```

---

### Iteration 1

Swap:

```text
chars[0] ↔ chars[4]
```

So:

```text
h ↔ o
```

Array:

```text
o  e  l  l  h
```

Move:

```text
left = 1
right = 3
```

---

### Iteration 2

Visual:

```text
o  e  l  l  h
   ↑     ↑
   L     R
```

Swap:

```text
e ↔ l
```

Array:

```text
o  l  l  e  h
```

Move:

```text
left = 2
right = 2
```

---

### Stop

Condition:

```text
left < right
2 < 2
```

False.

Return:

```text
olleh
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses a character array:

```text
h e l l o
```

Swaps:

```text
h ↔ o

o e l l h
```

then:

```text
e ↔ l

o l l e h
```

Result:

```text
olleh
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We visit roughly half the characters for swapping.

But asymptotically:

### Time

```text
O(n)
```

### Auxiliary Space

The character array requires:

```text
O(n)
```

because Python strings are immutable and Java uses a mutable character array.

### Important distinction

The **two-pointer algorithm itself** uses:

```text
O(1)
```

extra pointer space.

But converting a string into a mutable array requires:

```text
O(n)
```

storage.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why can't we directly swap characters in a Python string?

Python strings are immutable.

You cannot do:

```python
s[0] = 'x'
```

So we convert it to a list.

---

### Q2. What is the two-pointer pattern?

Two indices start from opposite ends and move toward each other.

```text
left →

← right
```

---

### Q3. Can Python reverse the string in one line?

Yes:

```python
s[::-1]
```

But if asked to implement reversal manually, two pointers demonstrate the underlying algorithm.

---

### Q4. Can we reverse using extra space O(1)?

For a mutable character array, yes, the reversal operation itself is in-place and uses O(1) auxiliary space.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

🔥 **Two Pointers — Opposite Direction**

Recognition:

> "Process the beginning and end simultaneously."

Think:

```text
left = 0
right = n - 1
```

Then:

```text
while left < right:
    process/swap
    left += 1
    right -= 1
```

This pattern will immediately reappear in **Problem 22 — Palindrome String**.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Using `right = len(s)`.

Correct:

```python
right = len(s) - 1
```

❌ Using:

```python
while left <= right
```

It can work, but:

```python
while left < right
```

is cleaner for swapping.

❌ Forgetting to move both pointers.

❌ Trying to modify the Python string directly.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
String
  ↓
Convert to mutable array
  ↓
left = 0
right = n-1
  ↓
swap
  ↓
left++
right--
  ↓
repeat
```

🔥 **Pattern: Opposite-End Two Pointers**

---

# 🔥 PROBLEM 22 — CHECK PALINDROME STRING

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Definition

A string is a palindrome if it reads the same from left to right and right to left.

Examples:

```text
madam → Palindrome
racecar → Palindrome
level → Palindrome
```

Not:

```text
hello → Not Palindrome
```

### LeetCode Match

🔥 **LC 125 — Valid Palindrome**

Difficulty: **Easy**

---

## 🚨 Important LeetCode Difference

LC 125 ignores:

* non-alphanumeric characters
* case differences

For example:

```text
"A man, a plan, a canal: Panama"
```

is considered a palindrome.

But our basic CR2 problem is simply:

> Check whether a string is a palindrome.

We should not silently change the problem definition.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
madam
```

Compare:

```text
m ↔ m
a ↔ a
d ↔ d
```

Everything matches.

Therefore:

```text
Palindrome
```

For:

```text
hello
```

Compare:

```text
h ↔ o
```

Mismatch immediately.

Therefore:

```text
Not Palindrome
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

This is almost the same two-pointer structure as Problem 21.

Start:

```text
m a d a m
↑       ↑
L       R
```

Compare:

```text
s[L] == s[R]
```

If not equal:

```text
return False
```

If equal:

```text
L += 1
R -= 1
```

Continue.

### 🚨 Senior insight

You don't need to reverse the string.

You only need to compare corresponding characters.

That means we can solve the basic problem in:

```text
O(n) time
O(1) auxiliary space
```

without constructing a reversed string.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Set:

   ```text
   left = 0
   right = len(s) - 1
   ```
2. While:

   ```text
   left < right
   ```
3. Compare:

   ```text
   s[left] == s[right]
   ```
4. If different → return `False`.
5. Move:

   ```text
   left += 1
   right -= 1
   ```
6. If all pairs match → return `True`.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_palindrome(s):

    left = 0
    right = len(s) - 1

    while left < right:

        if s[left] != s[right]:
            return False

        left += 1
        right -= 1

    return True


s = input("Enter a string: ")

if is_palindrome(s):
    print("Palindrome")
else:
    print("Not a Palindrome")
```

### Example

```text
Input:
madam

Output:
Palindrome
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static boolean isPalindrome(String s) {

        int left = 0;
        int right = s.length() - 1;

        while (left < right) {

            if (s.charAt(left) != s.charAt(right)) {
                return false;
            }

            left++;
            right--;
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String s = sc.nextLine();

        if (isPalindrome(s)) {
            System.out.println("Palindrome");
        } else {
            System.out.println("Not a Palindrome");
        }

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
madam
```

Characters:

```text
m a d a m
```

Initial:

```text
left = 0
right = 4
```

### Iteration 1

Compare:

```text
s[0] = m
s[4] = m
```

Equal.

Move:

```text
left = 1
right = 3
```

---

### Iteration 2

Compare:

```text
s[1] = a
s[3] = a
```

Equal.

Move:

```text
left = 2
right = 2
```

---

### Stop

```text
left < right
2 < 2
```

False.

All pairs matched.

Return:

```text
True
```

Output:

```text
Palindrome
```

---

# 🔬 NOT PALINDROME DRY RUN

Input:

```text
hello
```

Initial:

```text
left = 0
right = 4
```

Compare:

```text
h != o
```

Mismatch.

Immediately:

```text
return False
```

### 🔥 Senior optimization

We **stop immediately** when the first mismatch is found.

No reason to continue checking the rest.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
racecar
```

Pairs:

```text
r ↔ r
a ↔ a
c ↔ c
```

Pointers meet at the center.

Result:

```text
true
```

For:

```text
hello
```

First comparison:

```text
h != o
```

Return `false` immediately.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = string length
```

At most `n/2` comparisons.

Therefore:

### Time

```text
O(n)
```

### Space

Only two pointers:

```text
O(1)
```

🔥 This is better than:

```python
s == s[::-1]
```

from an algorithmic-space perspective because the slicing approach creates another string.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use two pointers instead of reversing?

We don't need to construct another string.

We compare symmetric characters directly.

---

### Q2. When can we stop?

Immediately when:

```text
s[left] != s[right]
```

because the string can no longer be a palindrome.

---

### Q3. What is the complexity?

```text
Time = O(n)
Space = O(1)
```

for the basic two-pointer implementation.

---

### Q4. How would LC 125 differ?

We would:

* ignore spaces/punctuation
* ignore case
* compare only alphanumeric characters

Example:

```text
"A man, a plan, a canal: Panama"
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is the same pattern as Problem 21:

```text
left = 0
right = n - 1

while left < right:
    compare/process
    left += 1
    right -= 1
```

### Difference:

Problem 21:

```text
swap
```

Problem 22:

```text
compare
```

🔥 **Same pattern, different operation.**

That is exactly how you should learn DSA.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Comparing only adjacent characters.

❌ Forgetting to move both pointers.

❌ Using `right = len(s)`.

❌ Reversing unnecessarily.

❌ Confusing palindrome with anagram.

Palindrome:

```text
same forward/backward
```

Anagram:

```text
same character frequencies
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Palindrome
     ↓
Two Pointers
     ↓
Compare left/right
     ↓
Mismatch → False
     ↓
Move inward
     ↓
All match → True
```

---

# 🔥 PROBLEM 23 — COUNT VOWELS AND CONSONANTS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we move from **two pointers** to **character classification**.

### Problem

Given a string, count:

```text
Vowels
Consonants
```

For the basic English alphabet:

### Vowels

```text
a e i o u
```

Both uppercase and lowercase should generally be handled.

Example:

```text
"Hello World"
```

Letters:

```text
H e l l o W o r l d
```

Vowels:

```text
e, o, o
```

Count:

```text
3
```

Consonants:

```text
H, l, l, W, r, l, d
```

Count:

```text
7
```

There is no exact canonical LeetCode problem for this standalone placement question.

---

## 🚨 Senior Insight

This is not a "string algorithm" problem in the DSA sense.

It's a:

# Character Classification Problem

For every character:

```text
Is it a letter?
      ↓
Is it a vowel?
      ↓
Otherwise → consonant
```

This distinction matters.

Spaces, digits, and punctuation should **not** be counted as consonants.

For example:

```text
"hello123!"
```

The `1`, `2`, `3`, `!` are neither vowels nor consonants.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
"Hello World!"
```

Process each character.

```text
H → consonant
e → vowel
l → consonant
l → consonant
o → vowel
space → ignore
W → consonant
o → vowel
r → consonant
l → consonant
d → consonant
! → ignore
```

Final:

```text
Vowels = 3
Consonants = 7
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

For each character:

### Step 1

Check whether it's a letter.

Python:

```python
char.isalpha()
```

### Step 2

Convert to lowercase:

```python
char.lower()
```

### Step 3

Check:

```python
char in "aeiou"
```

If yes:

```text
vowel++
```

Otherwise:

```text
consonant++
```

### Why check alphabet first?

Consider:

```text
"123!"
```

None of these are consonants.

If you only did:

```python
if char not in "aeiou":
    consonants += 1
```

you would incorrectly count digits and punctuation as consonants.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

1. Initialize:

   ```text
   vowels = 0
   consonants = 0
   ```
2. Traverse each character.
3. Check whether it is alphabetic.
4. If not alphabetic → ignore.
5. Convert to lowercase.
6. If it belongs to:

   ```text
   aeiou
   ```

   increment vowels.
7. Otherwise increment consonants.
8. Return both counts.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def count_vowels_consonants(s):

    vowels = 0
    consonants = 0

    for char in s:

        if char.isalpha():

            char = char.lower()

            if char in "aeiou":
                vowels += 1
            else:
                consonants += 1

    return vowels, consonants


s = input("Enter a string: ")

vowels, consonants = count_vowels_consonants(s)

print("Vowels =", vowels)
print("Consonants =", consonants)
```

### Example

```text
Input:
Hello World!

Output:
Vowels = 3
Consonants = 7
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    static void countVowelsConsonants(String s) {

        int vowels = 0;
        int consonants = 0;

        for (int i = 0; i < s.length(); i++) {

            char ch = Character.toLowerCase(s.charAt(i));

            if (ch >= 'a' && ch <= 'z') {

                if (ch == 'a' ||
                    ch == 'e' ||
                    ch == 'i' ||
                    ch == 'o' ||
                    ch == 'u') {

                    vowels++;
                } else {
                    consonants++;
                }
            }
        }

        System.out.println("Vowels = " + vowels);
        System.out.println("Consonants = " + consonants);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        String s = sc.nextLine();

        countVowelsConsonants(s);

        sc.close();
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"Hello World!"
```

Initial:

```text
vowels = 0
consonants = 0
```

### Character 1

```text
H
```

Alphabetic:

```text
Yes
```

Lowercase:

```text
h
```

Is `h` in `aeiou`?

```text
No
```

Therefore:

```text
consonants = 1
```

---

### Character 2

```text
e
```

Alphabetic:

```text
Yes
```

`e` is a vowel.

```text
vowels = 1
```

---

### Character 3

```text
l
```

Consonant:

```text
consonants = 2
```

---

### Character 4

```text
l
```

Consonant:

```text
consonants = 3
```

---

### Character 5

```text
o
```

Vowel:

```text
vowels = 2
```

---

### Character 6

```text
space
```

Not alphabetic.

Ignore.

---

### Character 7

```text
W
```

Lowercase:

```text
w
```

Consonant:

```text
consonants = 4
```

---

### Character 8

```text
o
```

Vowel:

```text
vowels = 3
```

---

### Character 9

```text
r
```

Consonant:

```text
consonants = 5
```

---

### Character 10

```text
l
```

Consonant:

```text
consonants = 6
```

---

### Character 11

```text
d
```

Consonant:

```text
consonants = 7
```

---

### Character 12

```text
!
```

Not alphabetic.

Ignore.

Final:

```text
Vowels = 3
Consonants = 7
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

For:

```text
Hello123!
```

Process:

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

Final:

```text
Vowels = 2
Consonants = 3
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We inspect every character once.

### Time

```text
O(n)
```

### Space

Only two counters:

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why should digits not be counted as consonants?

Because consonants are alphabetic characters that aren't vowels.

Digits and punctuation aren't letters.

---

### Q2. Why convert to lowercase?

It lets us check one vowel set:

```text
"aeiou"
```

instead of:

```text
"aeiouAEIOU"
```

---

### Q3. What is the complexity?

```text
Time = O(n)
Space = O(1)
```

---

### Q4. What if the string contains only digits?

Then:

```text
Vowels = 0
Consonants = 0
```

because there are no alphabetic characters.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is the fundamental pattern:

```text
for each character:
    classify(character)
    update counter
```

This generalizes to:

```text
count vowels
count consonants
count digits
count spaces
count uppercase
count lowercase
count special characters
frequency maps
```

You will use this heavily in Problems 24–30.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

❌ Counting every non-vowel as a consonant.

Wrong:

```python
if char not in "aeiou":
    consonants += 1
```

because spaces/digits/punctuation get counted.

❌ Forgetting uppercase letters.

❌ Forgetting `y` is normally treated as a consonant in the basic English classification.

❌ Counting numbers as letters.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
For every character
       ↓
Is alphabetic?
       ↓
No → ignore
       ↓
Yes
       ↓
Lowercase
       ↓
aeiou?
 ↙       ↘
Yes      No
 ↓        ↓
Vowel   Consonant
```

🔥 **Pattern: Character Classification + Counting**

---

# 🧠 DAY 3 — SESSION 1 MASTER PATTERN

You have now learned three problems, but there are really **two major patterns**.

## 21 — Reverse String

```text
left →       ← right
      swap
```

### Pattern:

**Two Pointers — Opposite Direction**

---

## 22 — Palindrome

```text
left →       ← right
      compare
```

### Pattern:

**Two Pointers — Opposite Direction**

---

## 23 — Vowels & Consonants

```text
character
    ↓
classify
    ↓
counter
```

### Pattern:

**Character Classification**

---

# 🔥 THE BIG CONNECTION

Problems 21 and 22 are **not two completely different algorithms**.

They share:

```text
left = 0
right = len(s) - 1

while left < right:
```

Only the operation changes.

### Reverse:

```text
swap
```

### Palindrome:

```text
compare
```

This is how you should learn DSA:

> **Learn patterns, not isolated programs.**

---

# 📊 DAY 3 — SESSION 1 COMPLETION

| Problem                 | Status |
| ----------------------- | ------ |
| 21. Reverse a String    | ✅      |
| 22. Palindrome String   | ✅      |
| 23. Vowels & Consonants | ✅      |

### CR2 Progress

```text
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅
DAY 3 → 3/10 ✅

TOTAL → 23/100
```

Again:

```text
23 read
≠
23 mastered
```

---

# 🧪 SESSION 1 — INDEPENDENT PRACTICE

Do these **without looking at today's solutions**.

## 🟢 BASIC

### Q1 — Reverse

```text
Input:
Python
```

Expected:

```text
nohtyP
```

---

### Q2 — Palindrome

Check:

```text
racecar
```

Expected:

```text
Palindrome
```

---

### Q3 — Vowels/Consonants

For:

```text
"Python Programming"
```

find:

```text
Vowels = ?
Consonants = ?
```

---

# 🟡 REPRODUCTION DRILL

Write from memory:

```text
1. Reverse String using two pointers
2. Palindrome String using two pointers
3. Count vowels and consonants
```

Do **not** use:

```python
[::-1]
```

for the reverse exercise.

The point is to reproduce the algorithm.

---

# 🟠 SENIOR VARIATION DRILL

### Challenge 1

Reverse:

```text
"Machine Learning"
```

while preserving spaces exactly.

Expected concept:

```text
"gninraeL enihcaM"
```

---

### Challenge 2

Check:

```text
"level"
```

using two pointers.

Then check:

```text
"hello"
```

Your program should stop at the **first mismatch**.

---

### Challenge 3

For:

```text
"Hello123! World"
```

calculate:

```text
Vowels
Consonants
Digits
Special Characters
Spaces
```

🔥 This is preparing you directly for **Problem 24 — Count Uppercase, Lowercase, Digits & Special Characters**.

---

# 🔴 MASTER TEST — NO CATEGORY HINT

Given:

```text
"Madam123!"
```

Without being told which pattern to use, write a program that:

1. Reverses the string.
2. Checks whether it is a palindrome.
3. Counts vowels.
4. Counts consonants.
5. Counts digits.
6. Counts special characters.

### Expected conceptual result:

```text
Original:
Madam123!

Reverse:
!321madaM

Palindrome:
No

Vowels:
2

Consonants:
3

Digits:
3

Special Characters:
1
```

🚨 **Don't copy the expected result into your code. Calculate it.**

---

# 🚀 DAY 3 SESSION 1 — SENIOR TAKEAWAY

Today's real learning is:

```text
STRING FUNDAMENTALS
│
├── Two Pointers
│     │
│     ├── Reverse → swap
│     │
│     └── Palindrome → compare
│
└── Character Classification
      │
      ├── vowel
      ├── consonant
      ├── digit
      ├── uppercase
      └── special
```

### 🔥 The recognition rules you should now have:

```text
"Reverse from both ends"
        ↓
Two Pointers


"Same forward and backward?"
        ↓
Two Pointers + Compare


"Count/classify characters?"
        ↓
Character Traversal + Conditions
```

**DAY 3 SESSION 1 = 23/100 completed.**

Next locked problems:

### DAY 3 — SESSION 2

**24. Count Uppercase, Lowercase, Digits & Special Characters**
**25. Remove Spaces from String**
**26. Remove Duplicate Characters**

Would you like to try the three independent practice questions first, or move straight to Day 3 Session 2?


# 🔥 DAY 3 — SESSION 2

## STRING FUNDAMENTALS — PROBLEMS 24–26

You have already completed:

* ✅ Day 1 → 10/10
* ✅ Day 2 → 10/10
* ✅ Day 3 Session 1 → Problems 21–23
* 🎯 Current total → **23/100**
* 🚀 Today → **Problems 24, 25, 26**

### Today's 3 Problems

| #  | Problem                                                 | Main Skill                   | Exact LeetCode?            |
| -- | ------------------------------------------------------- | ---------------------------- | -------------------------- |
| 24 | Count Uppercase, Lowercase, Digits & Special Characters | Character Classification     | ❌ No exact                 |
| 25 | Remove Spaces from String                               | String Traversal / Filtering | ❌ No exact                 |
| 26 | Remove Duplicate Characters                             | Hashing / Set                | ❌ No exact canonical match |

### 🧠 Today's Core Patterns

```text
Character → classify → count
Character → condition → keep/remove
Character → seen before? → skip/keep
```

These are **very common placement-round fundamentals** because they test whether you can manipulate strings without depending on advanced libraries.

---

# 🔴 PROBLEM 24 — COUNT UPPERCASE, LOWERCASE, DIGITS & SPECIAL CHARACTERS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This looks extremely easy.

But this problem is important because it teaches a pattern you'll repeatedly use in:

* password validation
* input validation
* data cleaning
* log processing
* text preprocessing
* security checks
* placement coding tests

The key is:

> Don't think about the entire string at once.
> Process **one character at a time** and classify it.

For every character:

```text
Uppercase? → uppercase++
Lowercase? → lowercase++
Digit?     → digit++
Otherwise  → special++
```

### Senior recognition

Whenever you see:

> "Count different types of characters"

Immediately think:

```text
for ch in string:
    classify ch
    increment corresponding counter
```

No sorting.

No nested loop.

No dictionary required.

No regex required.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

### Problem

Given a string, count:

1. Uppercase letters
2. Lowercase letters
3. Digits
4. Special characters

### Example

```text
Input:
Hello123@World!
```

Characters:

```text
H → Uppercase
e → Lowercase
l → Lowercase
l → Lowercase
o → Lowercase
1 → Digit
2 → Digit
3 → Digit
@ → Special
W → Uppercase
o → Lowercase
r → Lowercase
l → Lowercase
d → Lowercase
! → Special
```

Result:

```text
Uppercase = 2
Lowercase = 8
Digits    = 3
Special   = 2
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Python gives us useful character classification functions:

```python
ch.isupper()
ch.islower()
ch.isdigit()
```

But understand the underlying logic.

A character belongs to exactly one of these categories:

```text
Alphabet
   │
   ├── Uppercase
   │
   └── Lowercase

Number
   │
   └── Digit

Everything else
   │
   └── Special
```

For example:

```text
'A' → uppercase
'b' → lowercase
'7' → digit
'@' → special
' ' → special
```

⚠️ Important:

Whether spaces should be counted as "special" depends on the problem statement.

For our CR2 version:

> Everything that isn't uppercase, lowercase, or digit is treated as special.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read the string.

### Step 2

Create four counters:

```python
uppercase = 0
lowercase = 0
digits = 0
special = 0
```

### Step 3

Traverse every character.

```python
for ch in s:
```

### Step 4

Check uppercase.

```python
if ch.isupper():
    uppercase += 1
```

### Step 5

Otherwise check lowercase.

```python
elif ch.islower():
    lowercase += 1
```

### Step 6

Otherwise check digit.

```python
elif ch.isdigit():
    digits += 1
```

### Step 7

Anything remaining is special.

```python
else:
    special += 1
```

### Step 8

Print the four counters.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

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

print("Uppercase:", uppercase)
print("Lowercase:", lowercase)
print("Digits:", digits)
print("Special Characters:", special)
```

### Why this is optimal

We inspect every character exactly once.

There is no reason to inspect a character twice.

Therefore:

```text
Minimum work = O(n)
Our solution = O(n)
```

So this is asymptotically optimal.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        int uppercase = 0;
        int lowercase = 0;
        int digits = 0;
        int special = 0;

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (Character.isUpperCase(ch)) {
                uppercase++;
            }
            else if (Character.isLowerCase(ch)) {
                lowercase++;
            }
            else if (Character.isDigit(ch)) {
                digits++;
            }
            else {
                special++;
            }
        }

        System.out.println("Uppercase: " + uppercase);
        System.out.println("Lowercase: " + lowercase);
        System.out.println("Digits: " + digits);
        System.out.println("Special Characters: " + special);
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
Hello123@World!
```

Initial:

```text
uppercase = 0
lowercase = 0
digits = 0
special = 0
```

### Character-by-character

| Character | Classification |  U |  L |  D |  S |
| --------- | -------------- | -: | -: | -: | -: |
| H         | Uppercase      |  1 |  0 |  0 |  0 |
| e         | Lowercase      |  1 |  1 |  0 |  0 |
| l         | Lowercase      |  1 |  2 |  0 |  0 |
| l         | Lowercase      |  1 |  3 |  0 |  0 |
| o         | Lowercase      |  1 |  4 |  0 |  0 |
| 1         | Digit          |  1 |  4 |  1 |  0 |
| 2         | Digit          |  1 |  4 |  2 |  0 |
| 3         | Digit          |  1 |  4 |  3 |  0 |
| @         | Special        |  1 |  4 |  3 |  1 |
| W         | Uppercase      |  2 |  4 |  3 |  1 |
| o         | Lowercase      |  2 |  5 |  3 |  1 |
| r         | Lowercase      |  2 |  6 |  3 |  1 |
| l         | Lowercase      |  2 |  7 |  3 |  1 |
| d         | Lowercase      |  2 |  8 |  3 |  1 |
| !         | Special        |  2 |  8 |  3 |  2 |

Final:

```text
Uppercase = 2
Lowercase = 8
Digits = 3
Special = 2
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java follows exactly the same logical flow:

```text
char ch
   ↓
Character.isUpperCase()
   ↓
Character.isLowerCase()
   ↓
Character.isDigit()
   ↓
special
```

The language syntax changes.

The algorithm does **not**.

This is important for your placement preparation:

> Learn the algorithm once. Learn how to express it in Python and Java.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We inspect every character once.

Therefore:

```text
Time = O(n)
```

### Space

Only four counters are maintained:

```text
uppercase
lowercase
digits
special
```

Constant extra space:

```text
Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why is the time complexity O(n)?

Because every character must be examined at least once to determine its category.

Therefore:

```text
n characters → O(n)
```

---

### Q2. Can this be done in O(1) time?

No.

You cannot know the number of uppercase/lowercase/digit characters without examining the input.

Therefore the lower bound is:

```text
Ω(n)
```

Our solution achieves:

```text
O(n)
```

So it is asymptotically optimal.

---

### Q3. Do we need a HashMap?

No.

We only have four fixed categories.

Four integer counters are enough.

Using a dictionary would add unnecessary complexity.

---

### Q4. What if spaces should not be considered special?

Change:

```python
else:
    special += 1
```

to:

```python
elif ch != ' ':
    special += 1
```

This is an example of adapting the classification rules to the exact problem statement.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

Memorize this:

```text
COUNT CHARACTER TYPES
        ↓
TRAVERSE STRING
        ↓
CLASSIFY CHARACTER
        ↓
INCREMENT COUNTER
```

### Master template

```python
for ch in s:

    if CONDITION_1:
        count1 += 1

    elif CONDITION_2:
        count2 += 1

    elif CONDITION_3:
        count3 += 1

    else:
        count4 += 1
```

This template is extremely useful for placement coding.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### Mistake 1 — Using multiple independent `if`s incorrectly

You usually want:

```python
if ...
elif ...
elif ...
else ...
```

because each character belongs to one classification.

---

### Mistake 2 — Forgetting spaces

If spaces are part of the input, decide explicitly whether they count as special.

---

### Mistake 3 — Using `isdigit()` before checking letters

Not technically wrong if the branches are mutually exclusive, but classification should follow a clear order.

---

### Mistake 4 — Using regex unnecessarily

For a basic placement problem:

```python
re.findall(...)
```

is overkill.

Simple character classification is clearer and easier to debug.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

If interviewer says:

> "Count uppercase, lowercase, digits and special characters."

Your brain should immediately produce:

```text
One pass
↓
Classify each character
↓
Four counters
↓
O(n) time
↓
O(1) space
```

### 🔥 Recognition sentence

> "This is a single-pass character classification problem."

---

# 🟢 PROBLEM 24 COMPLETE

---

# 🔴 PROBLEM 25 — REMOVE SPACES FROM A STRING

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem teaches a fundamental **filtering pattern**.

You have:

```text
Input:
"Machine Learning Is Fun"
```

You want:

```text
"MachineLearningIsFun"
```

The key question is:

> Which characters should survive?

Answer:

```text
if character != ' ':
    keep it
```

This same pattern appears everywhere in programming:

```text
Remove spaces
Remove zeros
Remove unwanted characters
Keep only digits
Keep only letters
Filter invalid input
```

The general mental model is:

```text
READ → CHECK → KEEP / DISCARD
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, remove all spaces.

### Example

```text
Input:
"Hello World Python"

Output:
"HelloWorldPython"
```

Another:

```text
Input:
"Machine Learning Engineer"

Output:
"MachineLearningEngineer"
```

All spaces are removed.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a conveyor belt:

```text
H e l l o _ W o r l d
```

For every character:

```text
H → keep
e → keep
l → keep
l → keep
o → keep
space → discard
W → keep
...
```

So we construct a new result.

### Core pattern

```python
result = ""

for ch in s:
    if ch != ' ':
        result += ch
```

For beginner understanding, this is excellent.

However, there is an important Python optimization issue.

Repeated string concatenation can create many temporary strings.

A better practical Python solution is:

```python
result = []

for ch in s:
    if ch != ' ':
        result.append(ch)

return ''.join(result)
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read string.

### Step 2

Create empty character collection.

### Step 3

Traverse every character.

### Step 4

Check:

```python
if ch != ' ':
```

### Step 5

Keep only non-space characters.

### Step 6

Join them into the final string.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a string: ")

result = []

for ch in s:

    if ch != ' ':
        result.append(ch)

result = ''.join(result)

print("String without spaces:", result)
```

### Short Python version

Once you understand the algorithm:

```python
s = input()
result = ''.join(ch for ch in s if ch != ' ')
print(result)
```

For placement coding, I recommend knowing **both**, but understand the loop version first.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        StringBuilder result = new StringBuilder();

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (ch != ' ') {
                result.append(ch);
            }
        }

        System.out.println("String without spaces: " + result);
    }
}
```

### Why `StringBuilder`?

Java `String` objects are immutable.

Repeated:

```java
result += ch;
```

can create many temporary objects.

`StringBuilder` is designed for repeated string construction.

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"AI ML Engineer"
```

Start:

```text
result = []
```

### Trace

| Character | Action  | Result          |
| --------- | ------- | --------------- |
| A         | Keep    | `[A]`           |
| I         | Keep    | `[A,I]`         |
| space     | Discard | `[A,I]`         |
| M         | Keep    | `[A,I,M]`       |
| L         | Keep    | `[A,I,M,L]`     |
| space     | Discard | `[A,I,M,L]`     |
| E         | Keep    | `[A,I,M,L,E]`   |
| n         | Keep    | `[A,I,M,L,E,n]` |
| g         | Keep    | ...             |
| i         | Keep    | ...             |
| n         | Keep    | ...             |
| e         | Keep    | ...             |
| e         | Keep    | ...             |
| r         | Keep    | ...             |

Final:

```text
AI MLEngine
```

Actually, let's carefully preserve the original characters:

```text
"AI ML Engineer"
```

becomes:

```text
"AIMLEngineer"
```

This is why dry-running carefully matters.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same algorithm:

```text
char
 ↓
Is it space?
 ↓
YES → discard
NO  → append
```

`StringBuilder` stores the characters that survive.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We inspect each character exactly once.

Therefore:

```text
Time = O(n)
```

The output itself can contain up to `n` characters.

Therefore:

```text
Auxiliary space = O(n)
```

and output space is also:

```text
O(n)
```

### Important distinction

If an interviewer asks:

> "Space complexity?"

Say:

```text
O(n) because we construct the output string.
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Can this be done in O(n) time?

Yes.

Every character needs to be inspected once.

```text
O(n)
```

is optimal.

---

### Q2. Can we do it in O(1) extra space?

For an immutable input string, constructing a separate output generally requires storage.

If given a mutable character array, we could modify it in place using a write pointer.

Then auxiliary space can be:

```text
O(1)
```

---

### Q3. Why use `join()` instead of repeated `+=`?

Because repeated string concatenation can create many intermediate strings.

Using:

```python
list + ''.join()
```

is the safer efficient construction pattern.

---

### Q4. What if we want to remove all whitespace, not just `' '`?

That's a different requirement.

For example:

```text
space
tab
newline
```

are all whitespace.

Python provides:

```python
ch.isspace()
```

So the condition could become:

```python
if not ch.isspace():
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is the:

# FILTER PATTERN

Memorize:

```text
for item:
    if item satisfies condition:
        keep item
```

Examples:

```python
# Keep non-space characters
if ch != ' ':
    keep
```

```python
# Keep digits
if ch.isdigit():
    keep
```

```python
# Keep letters
if ch.isalpha():
    keep
```

This is a foundational pattern.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
s.replace(" ", "")
```

There is nothing wrong with this in normal Python programming.

But for **placement training**, you should know how to implement the logic manually.

---

### ❌ Mistake 2

Using:

```python
split()
```

and then incorrectly joining without understanding what happens to whitespace.

Know the underlying character filtering approach.

---

### ❌ Mistake 3

Removing only the first space.

You need to process the entire string.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you hear:

> "Remove all spaces."

Think:

```text
FILTER
↓
Traverse
↓
If not space → keep
↓
Join
```

Complexity:

```text
Time  → O(n)
Space → O(n)
```

---

# 🟢 PROBLEM 25 COMPLETE

---

# 🔴 PROBLEM 26 — REMOVE DUPLICATE CHARACTERS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Now we move to a much more important placement pattern:

# HASHING / SET

Example:

```text
Input:
programming
```

We want to remove repeated characters while preserving the **first occurrence**:

```text
progamin
```

Let's verify:

```text
p → keep
r → keep
o → keep
g → keep
r → duplicate
a → keep
m → keep
m → duplicate
i → keep
n → keep
g → duplicate
```

Result:

```text
progamin
```

The key question is:

> "Have I seen this character before?"

That's exactly what a `set` answers efficiently.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, remove duplicate characters.

### Requirement

Preserve the original order of first appearances.

Example:

```text
Input:
banana
```

Process:

```text
b → keep
a → keep
n → keep
a → duplicate
n → duplicate
a → duplicate
```

Output:

```text
ban
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine a security guard maintaining a guest list.

```text
seen = {}
```

When someone arrives:

```text
Have I seen them before?
```

### No

Allow them in:

```text
result.append(character)
seen.add(character)
```

### Yes

Reject duplicate:

```text
skip
```

Therefore:

```text
Character
    ↓
Is it in seen?
   / \
 YES  NO
  ↓    ↓
skip  keep
       ↓
    add to seen
```

This is one of the most important beginner hashing patterns.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read the string.

### Step 2

Create an empty set:

```python
seen = set()
```

### Step 3

Create result:

```python
result = []
```

### Step 4

Traverse every character.

### Step 5

Check:

```python
if ch not in seen:
```

### Step 6

If new:

```python
result.append(ch)
seen.add(ch)
```

### Step 7

If already present:

```text
skip
```

### Step 8

Join the result.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a string: ")

seen = set()
result = []

for ch in s:

    if ch not in seen:
        result.append(ch)
        seen.add(ch)

result = ''.join(result)

print("After removing duplicates:", result)
```

### Why this is optimal

A set provides average:

```text
O(1)
```

membership checking.

Therefore:

```text
n characters × O(1)
```

gives:

```text
O(n)
```

Average-case time.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        Set<Character> seen = new HashSet<>();
        StringBuilder result = new StringBuilder();

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (!seen.contains(ch)) {

                result.append(ch);
                seen.add(ch);
            }
        }

        System.out.println("After removing duplicates: " + result);
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
banana
```

Initial:

```text
seen = {}
result = []
```

### Character 1

```text
b
```

Is `b` in seen?

```text
NO
```

Keep:

```text
seen = {b}
result = [b]
```

---

### Character 2

```text
a
```

Not seen.

```text
seen = {b, a}
result = [b, a]
```

---

### Character 3

```text
n
```

Not seen.

```text
seen = {b, a, n}
result = [b, a, n]
```

---

### Character 4

```text
a
```

Already seen.

Skip.

```text
result = [b, a, n]
```

---

### Character 5

```text
n
```

Already seen.

Skip.

---

### Character 6

```text
a
```

Already seen.

Skip.

---

### Final

```text
result = [b, a, n]
```

Join:

```text
"ban"
```

Output:

```text
ban
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text
banana
```

```text
b → HashSet doesn't contain → append
a → doesn't contain → append
n → doesn't contain → append
a → contains → skip
n → contains → skip
a → contains → skip
```

Final:

```text
ban
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We process every character once.

Set lookup:

```text
Average O(1)
```

Set insertion:

```text
Average O(1)
```

Therefore:

```text
Time = O(n)
```

The set can contain at most the number of distinct characters.

For a general character set:

```text
Space = O(n)
```

For ASCII-only input, the number of possible distinct characters is bounded, so the practical auxiliary space can be viewed as:

```text
O(1)
```

But the safest general interview answer is:

```text
O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a set?

Because we need fast membership testing:

```python
ch in seen
```

Average:

```text
O(1)
```

---

### Q2. Why can't we simply use a nested loop?

We could.

For every character, search whether it appeared previously.

That can lead to:

```text
O(n²)
```

The set improves this to:

```text
O(n)
```

average case.

---

### Q3. Does `set(s)` solve the problem?

It removes duplicates, but there is an important issue to understand.

A plain set is primarily about uniqueness, while the problem requires preserving the first-occurrence order.

The explicit:

```python
seen
result
```

solution makes the intended behavior clear and is the safest placement implementation.

---

### Q4. What happens if the input is `"aaaaaa"`?

```text
a → keep
a → skip
a → skip
a → skip
a → skip
a → skip
```

Output:

```text
a
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is a major pattern.

# 🔥 SEEN SET PATTERN

Whenever you see:

> "Have we seen this before?"

Think:

```python
seen = set()

for item in data:

    if item not in seen:
        # first occurrence
        seen.add(item)
```

This pattern appears in:

* duplicate detection
* first repeating element
* unique elements
* visited nodes
* duplicate removal
* array intersection
* longest consecutive sequence
* graph traversal

You will use this repeatedly in your DSA roadmap too.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1 — Forgetting to add to `seen`

Wrong:

```python
if ch not in seen:
    result.append(ch)
```

If you don't execute:

```python
seen.add(ch)
```

every character will look new.

---

### ❌ Mistake 2 — Sorting the string

Sorting destroys the original order.

Input:

```text
banana
```

We want:

```text
ban
```

not an alphabetically sorted result.

---

### ❌ Mistake 3 — Using nested loops unnecessarily

You can solve this in average O(n) with a set.

---

### ❌ Mistake 4 — Confusing duplicate removal with frequency counting

These are different tasks.

```text
Remove duplicates:
banana → ban
```

Frequency:

```text
banana → b:1, a:3, n:2
```

Different requirements → different patterns.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When interviewer says:

> "Remove duplicate characters while preserving order."

Your brain:

```text
Need to know if seen before
        ↓
Use SET
        ↓
Traverse once
        ↓
If not seen → keep + add
        ↓
O(n) average
```

### Master template

```python
seen = set()
result = []

for item in data:

    if item not in seen:
        result.append(item)
        seen.add(item)

answer = ''.join(result)
```

🔥 **Memorize this pattern.**

It will return many times in your DSA preparation.

---

# 🟢 PROBLEM 26 COMPLETE

# 🏁 DAY 3 — SESSION 2 COMPLETE

## 📊 CURRENT PROGRESS

```text
DAY 1
██████████ 10/10

DAY 2
██████████ 10/10

DAY 3 — SESSION 1
███░░░░░░░ 3/10

DAY 3 — SESSION 2
███░░░░░░░ 3/10
```

### Overall

```text
23 → 26 / 100
```

🔥 **26% of CR2 completed.**

But remember:

> Reading 26 solutions ≠ mastering 26 problems.

Your real objective is independent reproduction.

---

# 🧪 SESSION 2 — INDEPENDENT PRACTICE

## 🟢 LEVEL 1 — REPRODUCTION

Without looking back, code these:

### Problem A

Input:

```text
Hello123! World
```

Output:

```text
Uppercase: 2
Lowercase: 8
Digits: 3
Special: 2
```

---

### Problem B

Input:

```text
Machine Learning
```

Output:

```text
MachineLearning
```

---

### Problem C

Input:

```text
programming
```

Output:

```text
progamin
```

---

# 🟡 LEVEL 2 — VARIATION DRILL

### Variation 1

Count:

```text
uppercase
lowercase
digits
special
spaces
```

separately.

---

### Variation 2

Remove **all whitespace**, including:

```text
space
tab
newline
```

---

### Variation 3

Remove duplicates from:

```text
mississippi
```

Do it manually first.

Expected:

```text
misp
```

---

# 🟠 LEVEL 3 — COMBINED PROBLEM

Given:

```text
"Hello123! Hello"
```

Write one program that:

1. Counts uppercase
2. Counts lowercase
3. Counts digits
4. Counts special characters
5. Removes spaces
6. Removes duplicate characters

Do **not** use separate library shortcuts for the entire task.

This tests whether you can combine today's three patterns.

---

# 🔴 MASTER TEST — NO SOLUTION

Don't look at the previous solutions.

### Input

```text
"PyThOn 123 @ PyThOn!"
```

Write a program that outputs:

```text
Uppercase = ?
Lowercase = ?
Digits = ?
Special = ?
Without spaces = ?
Without duplicates = ?
```

You should be able to produce the solution from memory.

---

# 🎯 YOUR MASTERY CHECK

Before moving to Session 3, you should be able to write these three templates from memory:

### 1️⃣ Character classification

```python
for ch in s:
    if ...:
        ...
    elif ...:
        ...
```

### 2️⃣ Filtering

```python
result = []

for ch in s:
    if condition:
        result.append(ch)
```

### 3️⃣ Seen-set

```python
seen = set()
result = []

for ch in s:
    if ch not in seen:
        result.append(ch)
        seen.add(ch)
```

If you can reproduce these without copying, **Session 2 is genuinely learned**.

---

## 🔜 NEXT

**DAY 3 — SESSION 3 → Problems 27–30**

1. 🔥 **Character Frequency**
2. **Check Anagram — LC 242**
3. **First Non-Repeating Character — LC 387**
4. **Toggle Case of Characters**

That session introduces the very important **frequency-map pattern**, which connects directly to your upcoming hashing problems.


# 🔥 DAY 3 — SESSION 3

## STRING FUNDAMENTALS — PROBLEMS 27–30

You have completed:

* ✅ Day 1 → 10/10
* ✅ Day 2 → 10/10
* ✅ Day 3 Session 1 → 21–23
* ✅ Day 3 Session 2 → 24–26
* 🎯 Current progress → **26/100**
* 🚀 Today's final session → **27–30**

---

# 🧠 TODAY'S CORE THEME

Today is important because we move from basic string manipulation into **frequency + hashing patterns**.

```text
Problem 27 → Frequency Map
Problem 28 → Frequency Map → Anagram
Problem 29 → Frequency Map → First Unique
Problem 30 → Character Transformation
```

The most important pattern today:

# 🔥 "COUNT / CHECK FREQUENCY"

Whenever a problem says:

* How many times does each character appear?
* Are two strings anagrams?
* Find the first character appearing once.
* Find the most frequent character.

Your brain should immediately think:

```text
Dictionary / HashMap
```

---

# 🔴 PROBLEM 27 — CHARACTER FREQUENCY

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is one of the most important beginner hashing problems.

Given:

```text
"banana"
```

we need:

```text
b → 1
a → 3
n → 2
```

The naive approach would be:

```text
For every character:
    scan the entire string
    count it
```

That can become:

```text
O(n²)
```

Instead, maintain a frequency map.

```text
character → number of occurrences
```

Example:

```text
seen = {}

b → 1
a → 1
n → 1
a → 2
n → 2
a → 3
```

This gives average:

```text
O(n)
```

🔥 This exact concept becomes the foundation for:

* Anagrams
* First unique character
* Most frequent element
* Duplicate detection
* Top K frequency problems
* Group Anagrams
* HashMap DSA problems

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, count the frequency of every character.

### Example

```text
Input:
programming
```

Output:

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

We should preserve the order in which characters are first encountered.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of a dictionary:

```text
frequency = {}
```

For each character:

### If character does not exist

```python
frequency[ch] = 1
```

### Otherwise

```python
frequency[ch] += 1
```

So:

```text
banana
```

becomes:

```text
b → 1
a → 3
n → 2
```

### ELI10 analogy

Imagine a classroom.

Every time a student enters:

```text
Alice → +1
Bob   → +1
Alice → +1
```

At the end:

```text
Alice → 2
Bob   → 1
```

That's exactly a frequency map.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read the string.

### Step 2

Create an empty dictionary.

```python
frequency = {}
```

### Step 3

Visit every character.

### Step 4

If character exists:

```python
frequency[ch] += 1
```

Otherwise:

```python
frequency[ch] = 1
```

### Step 5

Print the dictionary.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a string: ")

frequency = {}

for ch in s:

    if ch in frequency:
        frequency[ch] += 1
    else:
        frequency[ch] = 1

for ch, count in frequency.items():
    print(ch, "->", count)
```

### Cleaner Python version

Once the logic is mastered:

```python
s = input()

frequency = {}

for ch in s:
    frequency[ch] = frequency.get(ch, 0) + 1

for ch, count in frequency.items():
    print(ch, "->", count)
```

### Placement recommendation

Learn the first version first.

The second version is a compact Python idiom.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        Map<Character, Integer> frequency = new HashMap<>();

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (frequency.containsKey(ch)) {
                frequency.put(ch, frequency.get(ch) + 1);
            } else {
                frequency.put(ch, 1);
            }
        }

        for (Map.Entry<Character, Integer> entry : frequency.entrySet()) {
            System.out.println(
                entry.getKey() + " -> " + entry.getValue()
            );
        }
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
banana
```

Initial:

```text
frequency = {}
```

### Character 1

```text
b
```

Not present.

```text
frequency = {b: 1}
```

### Character 2

```text
a
```

```text
frequency = {b: 1, a: 1}
```

### Character 3

```text
n
```

```text
frequency = {b: 1, a: 1, n: 1}
```

### Character 4

```text
a
```

Already present:

```text
a: 1 → 2
```

Now:

```text
{b: 1, a: 2, n: 1}
```

### Character 5

```text
n
```

```text
n: 1 → 2
```

### Character 6

```text
a
```

```text
a: 2 → 3
```

Final:

```text
b → 1
a → 3
n → 2
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Java uses the same algorithm:

```text
HashMap
    ↓
character → frequency
```

For:

```text
banana
```

Final map contains:

```text
b → 1
a → 3
n → 2
```

The syntax differs from Python, but the algorithm is identical.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

We process every character once.

HashMap/Dictionary lookup is average:

```text
O(1)
```

Therefore:

```text
Time = O(n)
```

If there are `k` distinct characters:

```text
Space = O(k)
```

For a fixed character alphabet, this can effectively be considered:

```text
O(1)
```

But general interview answer:

```text
Time  → O(n)
Space → O(k)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a HashMap?

Because we need:

```text
character → count
```

and HashMap provides average O(1) lookup/update.

---

### Q2. Can we solve this with nested loops?

Yes.

But it can take:

```text
O(n²)
```

The frequency map gives:

```text
O(n)
```

average time.

---

### Q3. Why is space O(k), not necessarily O(n)?

Because the map stores only **distinct characters**.

If:

```text
aaaaaaaaaa
```

has length 10, the map contains only:

```text
a → 10
```

So:

```text
k = 1
```

---

### Q4. What if the string contains uppercase and lowercase letters?

They are different characters:

```text
'A' != 'a'
```

unless the problem explicitly asks for case-insensitive counting.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 FREQUENCY MAP TEMPLATE

Memorize:

```python
frequency = {}

for item in data:
    frequency[item] = frequency.get(item, 0) + 1
```

Whenever you see:

```text
COUNT OCCURRENCES
```

think:

```text
HASHMAP / DICTIONARY
```

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Resetting the count:

```python
frequency[ch] = 1
```

every time.

That destroys previous counts.

---

### ❌ Mistake 2

Forgetting the first occurrence.

You need:

```python
frequency.get(ch, 0)
```

or an explicit existence check.

---

### ❌ Mistake 3

Using sorting unnecessarily.

Sorting introduces:

```text
O(n log n)
```

while hashing can solve frequency counting in:

```text
O(n)
```

average.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Question:

> "Count how many times each character appears."

Instant recognition:

```text
Frequency problem
        ↓
Dictionary / HashMap
        ↓
One pass
        ↓
O(n) average
```

Master template:

```python
freq = {}

for ch in s:
    freq[ch] = freq.get(ch, 0) + 1
```

🔥 **This template must become automatic.**

---

# 🟢 PROBLEM 27 COMPLETE

---

# 🔴 PROBLEM 28 — CHECK ANAGRAM

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

🔥 **LC 242 — Valid Anagram**

Difficulty:

**Easy**

---

An anagram means:

> Two strings contain the same characters with the same frequencies, but possibly in a different order.

Example:

```text
listen
silent
```

Frequency:

```text
listen:
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1

silent:
s → 1
i → 1
l → 1
e → 1
n → 1
t → 1
```

Same frequency → anagram.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two strings:

```text
s = "listen"
t = "silent"
```

return:

```text
True
```

But:

```text
s = "hello"
t = "world"
```

returns:

```text
False
```

### Critical observation

Order does NOT matter.

Frequency DOES matter.

```text
"abb"
"bab"
```

→ Anagrams.

But:

```text
"abb"
"abc"
```

→ Not anagrams.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

There are two major approaches.

### Approach 1 — Sorting

```text
listen → eilnst
silent → eilnst
```

Same → anagram.

Complexity:

```text
O(n log n)
```

### Approach 2 — Frequency Map

```text
listen → frequency
silent → frequency
```

Complexity:

```text
O(n)
```

For our training, the **frequency-map solution is the key hashing pattern**.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

If lengths differ:

```python
return False
```

Because anagrams must contain the same number of characters.

### Step 2

Create frequency map for first string.

### Step 3

Create frequency map for second string.

### Step 4

Compare the two maps.

If equal:

```text
True
```

Otherwise:

```text
False
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_anagram(s, t):

    if len(s) != len(t):
        return False

    frequency_s = {}
    frequency_t = {}

    for ch in s:
        frequency_s[ch] = frequency_s.get(ch, 0) + 1

    for ch in t:
        frequency_t[ch] = frequency_t.get(ch, 0) + 1

    return frequency_s == frequency_t


s = input("Enter first string: ")
t = input("Enter second string: ")

print(is_anagram(s, t))
```

### More optimized version

We don't actually need two maps.

```python
def is_anagram(s, t):

    if len(s) != len(t):
        return False

    frequency = {}

    for ch in s:
        frequency[ch] = frequency.get(ch, 0) + 1

    for ch in t:

        if ch not in frequency:
            return False

        frequency[ch] -= 1

        if frequency[ch] < 0:
            return False

    return True
```

🔥 This is the version I want you to understand for interview mastery.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {

    public static boolean isAnagram(String s, String t) {

        if (s.length() != t.length()) {
            return false;
        }

        Map<Character, Integer> frequency = new HashMap<>();

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            frequency.put(
                ch,
                frequency.getOrDefault(ch, 0) + 1
            );
        }

        for (int i = 0; i < t.length(); i++) {

            char ch = t.charAt(i);

            if (!frequency.containsKey(ch)) {
                return false;
            }

            frequency.put(ch, frequency.get(ch) - 1);

            if (frequency.get(ch) < 0) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first string: ");
        String s = sc.nextLine();

        System.out.print("Enter second string: ");
        String t = sc.nextLine();

        System.out.println(isAnagram(s, t));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
s = "listen"
t = "silent"
```

### Build frequency from `listen`

```text
l → 1
i → 1
s → 1
t → 1
e → 1
n → 1
```

Now process `"silent"`.

### s

```text
s: 1 → 0
```

### i

```text
i: 1 → 0
```

### l

```text
l: 1 → 0
```

### e

```text
e: 1 → 0
```

### n

```text
n: 1 → 0
```

### t

```text
t: 1 → 0
```

Everything reaches zero.

Therefore:

```text
True
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Exactly the same:

```text
listen
 ↓
frequency map
 ↓
process silent
 ↓
decrement counts
 ↓
all counts balanced
 ↓
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of strings
```

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

Space:

```text
O(k)
```

where `k` is number of distinct characters.

For a fixed alphabet, effectively:

```text
O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why check lengths first?

Anagrams must contain exactly the same number of characters.

Therefore different lengths immediately imply:

```text
False
```

---

### Q2. Why is sorting not the optimal approach?

Sorting takes:

```text
O(n log n)
```

Frequency counting takes:

```text
O(n)
```

average.

---

### Q3. Can we solve it with one array instead of HashMap?

Yes, if the character set is fixed.

For lowercase English letters:

```python
count = [0] * 26
```

Then use character positions.

That gives:

```text
Time  → O(n)
Space → O(1)
```

---

### Q4. What if uppercase/lowercase should be ignored?

Normalize first:

```python
s = s.lower()
t = t.lower()
```

But only do this if the problem explicitly says case-insensitive.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

The key recognition:

```text
ANAGRAM
   ↓
Same characters?
   ↓
Same frequencies?
   ↓
HASHMAP
```

🔥 Memorize:

> **Anagram = Frequency Equality**

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Comparing only sets.

```text
"abb"
"ab"
```

Both sets:

```text
{a,b}
```

But they are not anagrams.

Frequency matters.

---

### ❌ Mistake 2

Ignoring length.

Length mismatch means immediate failure.

---

### ❌ Mistake 3

Sorting automatically without understanding the frequency approach.

Sorting is valid, but hashing is the more important pattern for your roadmap.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
Anagram
   ↓
Length check
   ↓
Frequency map
   ↓
Increment first string
   ↓
Decrement second string
   ↓
All balanced?
   ↓
YES → True
NO  → False
```

🔥 Pattern:

```text
Frequency comparison
```

---

# 🟢 PROBLEM 28 COMPLETE

---

# 🔴 PROBLEM 29 — FIRST NON-REPEATING CHARACTER

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

### Exact LeetCode Match

🔥 **LC 387 — First Unique Character in a String**

Difficulty:

**Easy**

This problem is extremely important because it combines **two passes**:

```text
Pass 1 → count frequency
Pass 2 → find first character with frequency 1
```

The critical insight:

> Don't try to determine whether a character is unique while seeing it for the first time.

You don't yet know whether it will appear again later.

Example:

```text
leetcode
```

When you first see:

```text
l
```

you don't know whether another `l` appears later.

So:

```text
Pass 1 → gather information
Pass 2 → make decision
```

This is a very important interview pattern.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given:

```text
"leetcode"
```

Find the first character that appears exactly once.

Frequencies:

```text
l → 1
e → 3
t → 1
c → 1
o → 1
d → 1
```

Scan original order:

```text
l → frequency 1
```

Therefore answer:

```text
l
```

Another example:

```text
aabbcdd
```

Frequencies:

```text
a → 2
b → 2
c → 1
d → 2
```

Answer:

```text
c
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We need two things:

### Information

How many times does each character occur?

Use:

```text
frequency map
```

### Order

Which unique character occurs first?

Use:

```text
original string
```

Therefore:

```text
Pass 1:
frequency

Pass 2:
original string
```

This is the key.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create frequency map.

### Step 2

Traverse the string and count every character.

### Step 3

Traverse the string again.

### Step 4

Check:

```python
if frequency[ch] == 1:
```

### Step 5

Return the first such character.

### Step 6

If none exists:

```text
No non-repeating character
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def first_non_repeating(s):

    frequency = {}

    # First pass: count frequencies
    for ch in s:
        frequency[ch] = frequency.get(ch, 0) + 1

    # Second pass: find first unique character
    for ch in s:
        if frequency[ch] == 1:
            return ch

    return None


s = input("Enter a string: ")

answer = first_non_repeating(s)

if answer is None:
    print("No non-repeating character")
else:
    print("First non-repeating character:", answer)
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;

public class Main {

    public static Character firstNonRepeating(String s) {

        Map<Character, Integer> frequency = new HashMap<>();

        // First pass
        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            frequency.put(
                ch,
                frequency.getOrDefault(ch, 0) + 1
            );
        }

        // Second pass
        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (frequency.get(ch) == 1) {
                return ch;
            }
        }

        return null;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        Character answer = firstNonRepeating(s);

        if (answer == null) {
            System.out.println("No non-repeating character");
        } else {
            System.out.println(
                "First non-repeating character: " + answer
            );
        }
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
swiss
```

### First pass

```text
s → 1
w → 1
i → 1
s → 2
s → 3
```

Final:

```text
s → 3
w → 1
i → 1
```

### Second pass

First character:

```text
s
```

Frequency:

```text
3
```

Skip.

Next:

```text
w
```

Frequency:

```text
1
```

Therefore:

```text
w
```

is the answer.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same:

```text
swiss

Frequency:
s → 3
w → 1
i → 1

Second pass:
s → skip
w → answer
```

Result:

```text
w
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

First pass:

```text
O(n)
```

Second pass:

```text
O(n)
```

Therefore:

```text
O(n) + O(n)
= O(2n)
= O(n)
```

Space:

```text
O(k)
```

where `k` is number of distinct characters.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we need two passes?

Because during the first pass we don't know whether a character will appear again later.

First pass gathers complete frequency information.

Second pass preserves original order and finds the first frequency-1 character.

---

### Q2. Can this be done in O(n)?

Yes.

Two linear passes still give:

```text
O(n)
```

---

### Q3. Why not use a nested loop?

You could compare every character with every other character, but that can become:

```text
O(n²)
```

The frequency map gives:

```text
O(n)
```

---

### Q4. What if there is no unique character?

Example:

```text
aabbcc
```

No character has frequency 1.

Return:

```text
None
```

or whatever output the problem specifies.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 TWO-PASS HASHING PATTERN

Whenever you need:

> "Find something based on information about the entire input, but preserve original order."

Think:

```text
PASS 1 → BUILD INFORMATION
PASS 2 → USE INFORMATION
```

Examples:

```text
Frequency
    ↓
First unique
```

This pattern is extremely important.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Trying to return immediately during the first pass.

You haven't seen the entire string yet.

---

### ❌ Mistake 2

Finding *any* unique character rather than the **first** unique character.

Order matters.

---

### ❌ Mistake 3

Sorting the string.

Sorting destroys the original order.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text
First Non-Repeating Character
            ↓
       Frequency Map
            ↓
       First Pass
            ↓
      Scan Original
            ↓
      frequency == 1
            ↓
          return
```

🔥 Master phrase:

> **Count first, decide second.**

---

# 🟢 PROBLEM 29 COMPLETE

---

# 🔴 PROBLEM 30 — TOGGLE CASE OF CHARACTERS

## 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is the final problem of Day 3.

The task:

```text
uppercase → lowercase
lowercase → uppercase
```

Example:

```text
Hello World
```

becomes:

```text
hELLO wORLD
```

The key is **character transformation**.

Unlike Problem 24, where we classified characters, here we modify them.

Mental model:

```text
Character
   ↓
Is uppercase?
   ↓
YES → lowercase
NO
   ↓
Is lowercase?
   ↓
YES → uppercase
NO
   ↓
Keep unchanged
```

Digits, spaces, punctuation should remain unchanged.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text
Hello123 World!
```

Output:

```text
hELLO123 wORLD!
```

Observe:

```text
H → h
e → E
l → L
l → L
o → O

1 → unchanged
2 → unchanged
3 → unchanged

space → unchanged

W → w
o → O
r → R
l → L
d → D

! → unchanged
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Python provides:

```python
ch.isupper()
ch.islower()
ch.lower()
ch.upper()
```

So:

```python
if ch.isupper():
    result.append(ch.lower())

elif ch.islower():
    result.append(ch.upper())

else:
    result.append(ch)
```

This is a simple **map/transform** pattern:

```text
INPUT CHARACTER
      ↓
TRANSFORM
      ↓
OUTPUT CHARACTER
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read string.

### Step 2

Create result.

### Step 3

Traverse every character.

### Step 4

If uppercase:

```text
convert to lowercase
```

### Step 5

If lowercase:

```text
convert to uppercase
```

### Step 6

Otherwise:

```text
keep unchanged
```

### Step 7

Join result.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a string: ")

result = []

for ch in s:

    if ch.isupper():
        result.append(ch.lower())

    elif ch.islower():
        result.append(ch.upper())

    else:
        result.append(ch)

result = ''.join(result)

print("Toggled string:", result)
```

### Short Python version

Python also provides:

```python
s.swapcase()
```

But for placement training, you should know the manual implementation first.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        StringBuilder result = new StringBuilder();

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (Character.isUpperCase(ch)) {
                result.append(Character.toLowerCase(ch));
            }
            else if (Character.isLowerCase(ch)) {
                result.append(Character.toUpperCase(ch));
            }
            else {
                result.append(ch);
            }
        }

        System.out.println("Toggled string: " + result);
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
AbC123!
```

Initial:

```text
result = []
```

### A

Uppercase:

```text
A → a
```

Result:

```text
a
```

### b

Lowercase:

```text
b → B
```

Result:

```text
aB
```

### C

```text
C → c
```

Result:

```text
aBc
```

### 1

Not alphabetic.

```text
1 → 1
```

### 2

```text
2 → 2
```

### 3

```text
3 → 3
```

### !

```text
! → !
```

Final:

```text
aBc123!
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same transformation:

```text
A → a
b → B
C → c
1 → 1
2 → 2
3 → 3
! → !
```

Output:

```text
aBc123!
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Every character is processed once.

Therefore:

```text
Time = O(n)
```

We construct an output string:

```text
Space = O(n)
```

So:

```text
Time  → O(n)
Space → O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What happens to digits?

They remain unchanged.

Example:

```text
A1b2 → a1B2
```

---

### Q2. What happens to special characters?

They remain unchanged.

```text
@#$
```

stay:

```text
@#$
```

---

### Q3. Can this be done without creating another string?

If using a mutable character array, yes.

You can modify the array in place.

Then auxiliary space can be:

```text
O(1)
```

depending on the language/input representation.

---

### Q4. Is `swapcase()` acceptable in Python?

Yes in normal programming:

```python
s.swapcase()
```

But in a coding assessment, you should understand the underlying logic rather than relying only on the built-in.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

This is the:

# 🔥 CHARACTER TRANSFORMATION PATTERN

Template:

```python
result = []

for ch in s:

    if condition_1:
        result.append(transformation_1)

    elif condition_2:
        result.append(transformation_2)

    else:
        result.append(ch)
```

This pattern is useful for:

* toggle case
* character replacement
* filtering
* normalization
* encoding
* text preprocessing

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Converting the entire string to lowercase.

That fails because we need to **toggle** each character.

---

### ❌ Mistake 2

Changing digits.

Digits should remain unchanged.

---

### ❌ Mistake 3

Changing punctuation.

Special characters should remain unchanged.

---

### ❌ Mistake 4

Forgetting to append unchanged characters.

You need:

```python
else:
    result.append(ch)
```

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you hear:

> "Toggle case."

Think:

```text
uppercase → lowercase
lowercase → uppercase
other → unchanged
```

One pass:

```text
O(n)
```

Output storage:

```text
O(n)
```

---

# 🟢 PROBLEM 30 COMPLETE

# 🏆 DAY 3 COMPLETE — 10/10

You have now finished the entire **String Fundamentals** day.

```text
DAY 3

21. Reverse String                    ✅
22. Palindrome String                 ✅
23. Count Vowels & Consonants         ✅
24. Count Character Types             ✅
25. Remove Spaces                     ✅
26. Remove Duplicate Characters       ✅
27. Character Frequency               ✅
28. Check Anagram                     ✅
29. First Non-Repeating Character     ✅
30. Toggle Case                       ✅
```

## 📊 OVERALL CR2 PROGRESS

```text
Day 1   ██████████ 10/10
Day 2   ██████████ 10/10
Day 3   ██████████ 10/10

TOTAL
██████████████████████████████ 30/100
```

# 🔥 THE 6 STRING PATTERNS YOU SHOULD NOW RECOGNIZE

```text
21 → TWO POINTERS
22 → TWO POINTERS
23 → CHARACTER CLASSIFICATION
24 → CHARACTER CLASSIFICATION
25 → FILTERING
26 → SEEN SET
27 → FREQUENCY MAP
28 → FREQUENCY COMPARISON
29 → TWO-PASS FREQUENCY
30 → CHARACTER TRANSFORMATION
```

The most important progression is:

```text
BASIC STRING
     ↓
CLASSIFICATION
     ↓
FILTERING
     ↓
SET
     ↓
HASHMAP
     ↓
FREQUENCY
     ↓
TWO-PASS HASHING
```

That progression is exactly what you want for placement fundamentals.

---

# 🧪 DAY 3 — FINAL NO-SOLUTION TEST

Do this **without looking at today's solutions**.

## Question 1

Input:

```text
"Programming123!"
```

Find:

```text
uppercase
lowercase
digits
special
```

---

## Question 2

Remove all spaces:

```text
"Machine Learning Engineer"
```

Expected:

```text
"MachineLearningEngineer"
```

---

## Question 3

Remove duplicates while preserving first occurrence:

```text
"mississippi"
```

Expected:

```text
"misp"
```

---

## Question 4

Find character frequencies:

```text
"engineering"
```

---

## Question 5

Check whether:

```text
"listen"
"silent"
```

are anagrams.

---

## Question 6

Find first non-repeating character:

```text
"swiss"
```

Expected:

```text
w
```

---

## Question 7

Toggle:

```text
"PyThOn123!"
```

Expected:

```text
"pYtHoN123!"
```

---

# 🔥 DAY 3 MASTER CHALLENGE

Write **one Python program** that receives:

```text
"PyThOn 123! PyThOn"
```

and produces:

```text
1. Uppercase count
2. Lowercase count
3. Digit count
4. Special-character count
5. String without spaces
6. String without duplicate characters
7. Character frequency
8. First non-repeating character
9. Toggled-case string
```

**No solution lookup.**

This is your actual Day 3 mastery test.

---

# 🎯 DAY 3 MASTERY STANDARD

Don't mark Day 3 as mastered merely because you understood the explanations.

You need:

```text
🟢 Understood
      ↓
🟡 Reproduced from memory
      ↓
🟠 Solved independently
      ↓
🔴 Mastered
```

For Day 3, your minimum target is:

```text
30/30 understood
30/30 reproduced
At least 8/10 final test independently
```

If you can write the **frequency-map**, **seen-set**, and **two-pass** templates from memory, you've built the exact foundation needed for the upcoming hashing problems.

# 🔜 NEXT

**DAY 4 — STRING PROBLEM SOLVING**

31. Reverse Words in a Sentence — LC 151
32. Find Longest Word
33. Check Whether String Contains Only Digits
34. String to Integer — LC 8
35. Most Frequent Character
36. Check String Rotation — LC 796
37. Longest Common Prefix — LC 14
38. Check Pangram — LC 1832
39. Run-Length Encoding
40. Balanced Brackets — LC 20

Day 4 will shift from **character-level fundamentals → actual string problem-solving patterns**.

Would you like to start with Problem 31, Reverse Words in a Sentence, or do the Day 3 master challenge first?
