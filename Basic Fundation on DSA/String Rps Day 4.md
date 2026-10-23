# 🟠 DAY 4

## STRING PROBLEM SOLVING

### Problems 31–40

```text
Reverse Words
Longest Word
Digits-only String
String → Integer
Most Frequent Character
String Rotation
Longest Common Prefix
Pangram
Run-Length Encoding
Balanced Brackets
```

### 🎯 Skill

**Practical string problem solving**

---


You must decide the technique yourself.


# 🔥 DAY 4 — SESSION 1

## STRING PROBLEM SOLVING — PROBLEMS 31–33

You have completed:

* ✅ Day 1 → 10/10
* ✅ Day 2 → 10/10
* ✅ Day 3 → 10/10
* 🎯 Total → **30/100**
* 🚀 Today → **Problems 31, 32, 33**

---

# 🧠 TODAY'S CORE THEME

Day 3 taught you:

```text
Character
   ↓
Classify / Count / Transform
```

Day 4 starts moving toward **actual string problem-solving**:

```text
31 → Reverse words
32 → Longest word
33 → Validate string contents
```

### Today's patterns

```text
31 → String parsing + reversal
32 → Linear scan + tracking maximum
33 → Character validation + early exit
```

The important mindset:

> Don't immediately search for a complicated algorithm.
> First identify what information you need to maintain while scanning the string.

---

# 🔴 PROBLEM 31 — REVERSE WORDS IN A SENTENCE

### Exact LeetCode Match

🔥 **LC 151 — Reverse Words in a String**

Difficulty: **Medium**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is an important string problem because it introduces **word-level processing** instead of character-level processing.

Example:

```text
"I love Python"
```

We want:

```text
"Python love I"
```

Notice:

```text
Character reversal:
"I love Python"
→
"nohtyP evol I"       ❌

Word reversal:
"I love Python"
→
"Python love I"       ✅
```

That's the first thing you must recognize.

### 🔥 Recognition rule

If the problem says:

> "Reverse the words"

do NOT reverse the characters.

Think:

```text
STRING
  ↓
WORDS
  ↓
REVERSE WORD ORDER
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a sentence, reverse the order of its words.

### Example 1

```text
Input:
"I love Python"

Output:
"Python love I"
```

### Example 2

```text
Input:
"Machine Learning Engineer"

Output:
"Engineer Learning Machine"
```

### Example 3 — Extra spaces

```text
Input:
"  hello   world  "
```

Expected:

```text
"world hello"
```

For our placement version:

* leading spaces should disappear
* trailing spaces should disappear
* multiple spaces between words should become a single space

This is essentially the same behavior as LC 151.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

The easiest way to understand this is:

### Step 1 — Extract words

```text
"I love Python"
```

becomes:

```text
["I", "love", "Python"]
```

### Step 2 — Reverse the word list

```text
["Python", "love", "I"]
```

### Step 3 — Join

```text
"Python love I"
```

So the algorithm is:

```text
String
  ↓
Split into words
  ↓
Reverse word order
  ↓
Join with one space
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read the entire sentence.

### Step 2

Remove unnecessary whitespace and split into words.

```python
words = s.split()
```

Important:

```python
split()
```

with no argument automatically handles multiple whitespace characters.

For:

```text
"  hello   world  "
```

we get:

```text
["hello", "world"]
```

### Step 3

Reverse the list.

### Step 4

Join the reversed words with a single space.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a sentence: ")

words = s.split()

words.reverse()

result = " ".join(words)

print(result)
```

### Cleaner version

```python
s = input()

result = " ".join(s.split()[::-1])

print(result)
```

### Placement recommendation

Understand the first version.

Don't memorize:

```python
[::-1]
```

without understanding what it does.

---

## 🔥 Why is this efficient?

Each character is processed a constant number of times:

```text
split → O(n)
reverse → O(w)
join → O(n)
```

where:

```text
n = number of characters
w = number of words
```

Therefore:

```text
O(n + w) = O(n)
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a sentence: ");
        String s = sc.nextLine();

        String[] words = s.trim().split("\\s+");

        StringBuilder result = new StringBuilder();

        for (int i = words.length - 1; i >= 0; i--) {

            result.append(words[i]);

            if (i != 0) {
                result.append(" ");
            }
        }

        System.out.println(result);
    }
}
```

### Why `\\s+`?

It means:

```text
\s → whitespace
+  → one or more
```

So:

```text
"hello   world"
```

is treated as:

```text
hello
world
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"  Machine   Learning   Engineer  "
```

### Step 1

```python
words = s.split()
```

Result:

```text
["Machine", "Learning", "Engineer"]
```

### Step 2

Reverse:

```text
["Engineer", "Learning", "Machine"]
```

### Step 3

Join:

```text
"Engineer Learning Machine"
```

Final:

```text
Engineer Learning Machine
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
"I love AI"
```

After splitting:

```text
["I", "love", "AI"]
```

Loop starts from the last index:

```text
AI
love
I
```

Result:

```text
"AI love I"
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = number of characters
w = number of words
```

Splitting:

```text
O(n)
```

Reversing:

```text
O(w)
```

Joining:

```text
O(n)
```

Total:

```text
O(n + w)
```

Since:

```text
w <= n
```

we simplify:

```text
Time = O(n)
```

### Space

We store the words:

```text
O(n)
```

So:

```text
Time  → O(n)
Space → O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. What is the difference between reversing a string and reversing words?

```text
String reversal:
"hello world"
→
"dlrow olleh"
```

Word reversal:

```text
"hello world"
→
"world hello"
```

---

### Q2. Why does `split()` without an argument help?

It handles arbitrary whitespace.

```text
"hello   world"
```

becomes:

```text
["hello", "world"]
```

---

### Q3. Can this be done in O(n)?

Yes.

Every character must be processed at least once, so O(n) is asymptotically optimal.

---

### Q4. What happens with an empty string?

```text
""
```

Then:

```python
s.split()
```

returns:

```python
[]
```

and:

```python
" ".join([])
```

returns:

```text
""
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 WORD-LEVEL STRING PATTERN

Whenever you see:

> Reverse words / process words / manipulate words

Think:

```text
String
 ↓
Split into words
 ↓
Process word list
 ↓
Join
```

Master template:

```python
words = s.split()

# process words

answer = " ".join(words)
```

This is a very useful placement template.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Doing:

```python
s[::-1]
```

That reverses characters, not words.

---

### ❌ Mistake 2

Not handling multiple spaces.

```text
"hello   world"
```

should not produce unwanted multiple spaces in the output.

---

### ❌ Mistake 3

Forgetting leading/trailing spaces.

---

### ❌ Mistake 4

Using `split(" ")` without understanding the difference.

For:

```text
"hello   world"
```

it can produce empty strings between consecutive spaces.

Prefer:

```python
s.split()
```

for whitespace-separated words.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you hear:

> "Reverse the words in a sentence."

Immediately think:

```text
Split
 ↓
Reverse word order
 ↓
Join
```

Complexity:

```text
O(n) time
O(n) space
```

---

# 🟢 PROBLEM 31 COMPLETE

---

# 🔴 PROBLEM 32 — FIND THE LONGEST WORD

### Exact LeetCode Match

❌ **No exact canonical LeetCode problem for this basic placement formulation.**

There are related word/string problems, but we will **not falsely label them as exact matches**.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a very common placement question.

The problem tests whether you can maintain a **running maximum**.

Example:

```text
"I am a Machine Learning Engineer"
```

Words:

```text
I
am
a
Machine
Learning
Engineer
```

Lengths:

```text
1
2
1
7
8
8
```

Longest word:

```text
Learning
```

If two words have the same maximum length, our basic version returns the **first** longest word.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a sentence, find the longest word.

Example:

```text
Input:
"I love programming"

Output:
programming
```

Because:

```text
I          → 1
love       → 4
programming → 11
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We don't need to sort the words.

Why?

Because sorting would be unnecessary work.

Instead:

```text
best = current longest word
```

For each word:

```text
if len(word) > len(best):
    best = word
```

This is the classic:

# 🔥 RUNNING MAXIMUM PATTERN

You will use the same logic for:

* largest number
* longest string
* maximum score
* maximum subarray value
* maximum frequency
* best candidate seen so far

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Split the sentence into words.

### Step 2

Set:

```python
longest = ""
```

### Step 3

Traverse each word.

### Step 4

Compare:

```python
if len(word) > len(longest):
```

### Step 5

Update:

```python
longest = word
```

### Step 6

Print `longest`.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a sentence: ")

words = s.split()

longest = ""

for word in words:

    if len(word) > len(longest):
        longest = word

print("Longest word:", longest)
```

### Why this is optimal

We examine every word exactly once.

No sorting.

No nested loops.

Therefore:

```text
O(n)
```

with respect to the total input size.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a sentence: ");
        String s = sc.nextLine();

        String[] words = s.trim().split("\\s+");

        String longest = "";

        for (String word : words) {

            if (word.length() > longest.length()) {
                longest = word;
            }
        }

        System.out.println("Longest word: " + longest);
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"I love Machine Learning"
```

Split:

```text
["I", "love", "Machine", "Learning"]
```

Initial:

```text
longest = ""
```

### Word 1

```text
I
length = 1
```

```text
1 > 0
```

Update:

```text
longest = "I"
```

### Word 2

```text
love
length = 4
```

```text
4 > 1
```

Update:

```text
longest = "love"
```

### Word 3

```text
Machine
length = 7
```

```text
7 > 4
```

Update:

```text
longest = "Machine"
```

### Word 4

```text
Learning
length = 8
```

```text
8 > 7
```

Update:

```text
longest = "Learning"
```

Final:

```text
Learning
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same algorithm:

```text
I        → longest = I
love     → longest = love
Machine  → longest = Machine
Learning → longest = Learning
```

Result:

```text
Learning
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = total number of characters
w = number of words
```

Splitting:

```text
O(n)
```

Scanning words:

```text
O(w)
```

Since:

```text
w <= n
```

total:

```text
O(n)
```

### Space

The word list requires:

```text
O(n)
```

Therefore:

```text
Time  → O(n)
Space → O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why not sort the words by length?

Sorting takes:

```text
O(w log w)
```

We only need the maximum.

A linear scan is enough:

```text
O(w)
```

---

### Q2. What if two words have the same maximum length?

Our condition is:

```python
len(word) > len(longest)
```

not:

```python
>=
```

Therefore the **first** longest word is retained.

Example:

```text
"Machine Learning"
```

Both have length 7 and 8 respectively, but if equal:

```text
"coding machine"
```

`coding` length 6, `machine` length 7.

For:

```text
"Python Coding"
```

both length 6, so:

```text
Python
```

is returned.

---

### Q3. Can we return the longest word without storing all words?

Yes.

A more memory-conscious implementation can scan the sentence and build words manually.

That can reduce auxiliary storage, but the standard `split()` solution is simpler and highly appropriate for basic placement rounds.

---

### Q4. What is the pattern here?

```text
Running maximum.
```

You maintain the best answer found so far.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 RUNNING MAXIMUM

Template:

```python
best = initial_value

for item in data:

    if item > best:
        best = item
```

For strings:

```python
if len(word) > len(longest):
    longest = word
```

This is one of the most important basic coding templates.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Sorting when unnecessary.

---

### ❌ Mistake 2

Comparing the words themselves:

```python
if word > longest:
```

That compares lexicographically, **not by length**.

You need:

```python
if len(word) > len(longest):
```

---

### ❌ Mistake 3

Using `>=` unintentionally.

That changes the tie-breaking behavior to the **last** longest word.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Question:

> Find the longest word.

Think:

```text
Split
 ↓
Running maximum
 ↓
Compare lengths
 ↓
Update best
```

Complexity:

```text
O(n) time
O(n) space
```

---

# 🟢 PROBLEM 32 COMPLETE

---

# 🔴 PROBLEM 33 — CHECK WHETHER STRING CONTAINS ONLY DIGITS

### Exact LeetCode Match

❌ **No exact basic LeetCode match.**

There is **LC 65 — Valid Number**, but that is a substantially broader and harder problem involving decimal numbers, signs, exponents, etc.

We are **not** calling LC 65 an exact match.

Our problem is simply:

> Does every character in the string represent a digit from `0` to `9`?

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a **validation problem**.

Examples:

```text
"12345"    → True
"987001"   → True
"123a45"   → False
"12.34"    → False
"123 45"   → False
```

The important optimization:

# 🔥 EARLY EXIT

The moment we find an invalid character:

```text
return False
```

There is no reason to inspect the rest.

Example:

```text
"123X456789"
```

Once we reach:

```text
X
```

the answer is already known.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, determine whether it contains only digits.

### Example

```text
Input:
"123456"

Output:
True
```

### Example

```text
Input:
"12345A"

Output:
False
```

### Example

```text
Input:
"123 456"

Output:
False
```

A space is not a digit.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

We need to validate every character.

For every character:

```text
Is it a digit?
```

If yes:

```text
continue
```

If no:

```text
return False
```

If we finish the entire string:

```text
return True
```

Think:

```text
VALIDATION PATTERN

for item:
    if invalid:
        return False

return True
```

🔥 This pattern is extremely important.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Read the string.

### Step 2

Traverse every character.

### Step 3

Check:

```python
if not ch.isdigit():
```

### Step 4

If invalid:

```python
return False
```

### Step 5

If loop finishes:

```python
return True
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def contains_only_digits(s):

    for ch in s:

        if not ch.isdigit():
            return False

    return True


s = input("Enter a string: ")

print(contains_only_digits(s))
```

### Important edge case

For an empty string:

```text
""
```

the loop runs zero times and returns:

```text
True
```

But many placement problems consider an empty string invalid.

If the problem says **at least one digit must exist**, use:

```python
def contains_only_digits(s):

    if not s:
        return False

    for ch in s:

        if not ch.isdigit():
            return False

    return True
```

For our placement version, we'll use the second interpretation:

> Empty string → False.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static boolean containsOnlyDigits(String s) {

        if (s.isEmpty()) {
            return false;
        }

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (!Character.isDigit(ch)) {
                return false;
            }
        }

        return true;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter a string: ");
        String s = sc.nextLine();

        System.out.println(containsOnlyDigits(s));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"12345"
```

### Character 1

```text
1 → digit
```

Continue.

### Character 2

```text
2 → digit
```

Continue.

### Character 3

```text
3 → digit
```

Continue.

### Character 4

```text
4 → digit
```

Continue.

### Character 5

```text
5 → digit
```

Loop completes.

Therefore:

```text
True
```

---

### Now:

```text
"123A45"
```

Trace:

```text
1 → valid
2 → valid
3 → valid
A → INVALID
```

Immediately:

```text
return False
```

We don't even inspect:

```text
45
```

🔥 That's early exit.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Input:

```text
"987X123"
```

```text
9 → valid
8 → valid
7 → valid
X → invalid
```

Immediately:

```text
false
```

No need to process `123`.

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Worst case:

Every character is a digit.

We inspect all `n` characters:

```text
Time = O(n)
```

Best case:

The first character is invalid.

```text
Time = O(1)
```

Therefore:

```text
Worst case → O(n)
Best case  → O(1)
```

Extra space:

```text
O(1)
```

Final:

```text
Time  → O(n) worst case
Space → O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use early exit?

Once an invalid character is found, the final answer cannot change.

Therefore continuing is wasted work.

---

### Q2. What's the best-case complexity?

If the first character is invalid:

```text
O(1)
```

---

### Q3. What's the worst-case complexity?

If all characters are valid:

```text
O(n)
```

---

### Q4. Is `"123.45"` valid?

No.

The `.` character is not a digit.

Our problem asks for:

```text
0–9 only
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 VALIDATION + EARLY EXIT

Memorize:

```python
for item in data:

    if invalid(item):
        return False

return True
```

This pattern appears in:

* validation
* checking sorted arrays
* checking parentheses
* checking passwords
* checking constraints
* checking whether all elements satisfy a condition

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Converting the whole string to an integer:

```python
int(s)
```

This is not the same as learning to validate each character.

Also, it introduces behavior you may not want for a coding problem.

---

### ❌ Mistake 2

Allowing decimal points accidentally.

```text
"12.5"
```

is not "only digits."

---

### ❌ Mistake 3

Allowing negative sign:

```text
"-123"
```

The `-` is not a digit.

Therefore:

```text
False
```

---

### ❌ Mistake 4

Continuing after an invalid character.

Use early exit.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you hear:

> "Check whether every character satisfies a condition."

Think:

```text
VALIDATION
   ↓
SCAN
   ↓
INVALID?
   ↓
YES → return False
   ↓
finish
   ↓
return True
```

Complexity:

```text
Worst → O(n)
Best  → O(1)
Space → O(1)
```

---

# 🟢 PROBLEM 33 COMPLETE

# 🏆 DAY 4 — SESSION 1 COMPLETE

You are now at:

```text
DAY 1 → 10/10 ✅
DAY 2 → 10/10 ✅
DAY 3 → 10/10 ✅
DAY 4 → 3/10 ✅
```

## 📊 TOTAL PROGRESS

```text
33 / 100
```

🔥 **33% of CR2 completed.**

---

# 🧠 TODAY'S 3 PATTERNS

You should now be able to recognize these instantly:

### 1️⃣ WORD PROCESSING

```text
sentence
   ↓
split
   ↓
words
   ↓
process
   ↓
join
```

### 2️⃣ RUNNING MAXIMUM

```text
best = initial

for item:
    if item is better:
        best = item
```

### 3️⃣ VALIDATION + EARLY EXIT

```text
for item:
    if invalid:
        return False

return True
```

---

# 🧪 SESSION 1 — INDEPENDENT PRACTICE

Do these **without looking at the solutions above**.

## 🟢 LEVEL 1 — REPRODUCTION

### Problem A

Input:

```text
"I am learning Python"
```

Output:

```text
"Python learning am I"
```

---

### Problem B

Input:

```text
"I love artificial intelligence"
```

Find the longest word.

Expected:

```text
artificial
```

---

### Problem C

Check:

```text
"123456789"
```

Expected:

```text
True
```

Then:

```text
"12345a678"
```

Expected:

```text
False
```

---

# 🟡 LEVEL 2 — VARIATIONS

### Variation 1

Reverse words while handling:

```text
"   Python     is    powerful   "
```

Expected:

```text
"powerful is Python"
```

---

### Variation 2

Find the longest word in:

```text
"Python Machine Learning Engineering"
```

If there is a tie, return the **first** longest word.

---

### Variation 3

Check whether these contain only digits:

```text
"000123"
"123.45"
"-123"
"123 456"
"987654"
```

Predict first, then code.

---

# 🟠 LEVEL 3 — COMBINED PROBLEM

Given:

```text
"Machine Learning 2026"
```

Write one program that:

1. Reverses the words.
2. Finds the longest word.
3. Checks whether the original string contains only digits.

Don't use three unrelated built-in shortcuts blindly. Implement the logic you've learned.

---

# 🔴 MASTER TEST — NO SOLUTION

Given:

```text
"  Python   Machine   Learning   Engineer  "
```

Your program must output:

```text
Reversed words:
Engineer Learning Machine Python

Longest word:
Learning

Only digits:
False
```

Then test:

```text
"123456789"
```

for the digit-validation part.

---

# 🎯 MASTERY CHECK

Before moving to Session 2, you should be able to write from memory:

```python
# Word processing
words = s.split()

# Running maximum
if len(word) > len(longest):
    longest = word

# Validation
if invalid:
    return False
```

If these three patterns become automatic, you're progressing exactly as intended.

---

## 🔜 NEXT: DAY 4 — SESSION 2

Problems **34–36**:

1. 🔥 **String to Integer — LC 8 (`atoi`)**
2. **Most Frequent Character**
3. **Check String Rotation — LC 796**

This is where string parsing becomes more interview-oriented.

Would you like to try the Day 4 master test first, or move on to Session 2?

# 🔥 DAY 4 — SESSION 2

## STRING PROBLEM SOLVING — PROBLEMS 34–36

You have completed:

* ✅ Day 1 → 10/10
* ✅ Day 2 → 10/10
* ✅ Day 3 → 10/10
* ✅ Day 4 Session 1 → 31–33
* 🎯 Current progress → **33/100**
* 🚀 Today's session → **34, 35, 36**

---

# 🧠 TODAY'S CORE THEME

Today's problems move from basic string traversal into **real interview-style string reasoning**.

```text
34 → String Parsing
35 → Frequency + Maximum
36 → String Rotation
```

### Core patterns

```text
34 → State-based parsing
35 → Frequency Map + Running Maximum
36 → Rotation Property / Concatenation
```

The biggest jump today is **Problem 34**.

LC 8 is not just:

```python
int(s)
```

You need to understand how a parser processes characters and handles:

* leading spaces
* optional sign
* digits
* invalid characters
* overflow

---

# 🔴 PROBLEM 34 — STRING TO INTEGER

## Exact LeetCode Match

🔥 **LC 8 — String to Integer (atoi)**

Difficulty: **Medium**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a classic interview problem.

The trap is thinking:

```python
int(s)
```

That's not the algorithm they're testing.

The interviewer wants to know whether you can build a **small parser**.

For example:

```text
"   -42abc"
```

The parser should understand:

```text
spaces
   ↓
sign
   ↓
digits
   ↓
stop at invalid character
```

So the mental model is:

```text
READ → PARSE → VALIDATE → BUILD NUMBER
```

### 🔥 Senior recognition

Whenever you see:

> Convert a string representation into a number under specific rules.

Think:

```text
STATE MACHINE / PARSER
```

You maintain:

```text
result
sign
index
```

and process characters one by one.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

For the CR2 version, we follow the important LC 8 rules.

Given a string:

1. Ignore leading spaces.
2. Check optional `+` or `-`.
3. Read consecutive digits.
4. Stop when a non-digit appears.
5. If no digit exists, return `0`.
6. Clamp the result to 32-bit signed integer range.

Range:

```text
-2³¹ to 2³¹ - 1
```

Therefore:

```text
INT_MIN = -2147483648
INT_MAX = 2147483647
```

### Examples

```text
"42"          → 42
"   -42"      → -42
"+42"         → 42
"4193 with"   → 4193
"words 987"   → 0
"-912abc"     → -912
"912xyz"      → 912
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Let's understand:

```text
"   -42abc"
```

### Step 1 — Skip spaces

```text
"   -42abc"
   ↑
```

Move until:

```text
'-'
```

### Step 2 — Read sign

```text
sign = -1
```

### Step 3 — Read digits

```text
4
2
```

How do we build the number?

Start:

```text
result = 0
```

Read `4`:

```text
result = 0 * 10 + 4
       = 4
```

Read `2`:

```text
result = 4 * 10 + 2
       = 42
```

Apply sign:

```text
42 * -1
= -42
```

Then:

```text
a
```

is not a digit.

Stop.

---

# 🔥 The mathematical trick

For every digit:

```text
new_result = old_result × 10 + digit
```

Example:

```text
123
```

Build:

```text
0
→ 1
→ 12
→ 123
```

This is one of the most important number-building patterns in coding.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Set:

```python
i = 0
result = 0
sign = 1
```

### Step 2

Skip leading spaces.

```python
while s[i] == ' ':
    i += 1
```

### Step 3

Check sign.

```text
+ → sign = +1
- → sign = -1
```

Move index forward.

### Step 4

Process digits.

For each digit:

```python
digit = ord(s[i]) - ord('0')
result = result * 10 + digit
```

### Step 5

Check overflow.

If result becomes too large, return the appropriate boundary.

### Step 6

Return:

```python
sign * result
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def my_atoi(s):

    INT_MAX = 2**31 - 1
    INT_MIN = -2**31

    i = 0
    n = len(s)

    # Step 1: Skip leading spaces
    while i < n and s[i] == ' ':
        i += 1

    # Step 2: Check sign
    sign = 1

    if i < n and (s[i] == '+' or s[i] == '-'):
        if s[i] == '-':
            sign = -1
        i += 1

    # Step 3: Build number
    result = 0

    while i < n and s[i].isdigit():

        digit = ord(s[i]) - ord('0')

        # Step 4: Overflow check
        if result > (INT_MAX - digit) // 10:

            if sign == 1:
                return INT_MAX
            else:
                return INT_MIN

        result = result * 10 + digit

        i += 1

    return sign * result


s = input("Enter string: ")

print(my_atoi(s))
```

---

# 🧠 Understanding the overflow formula

This line looks scary:

```python
if result > (INT_MAX - digit) // 10:
```

Why?

We want:

```text
new_result = result * 10 + digit
```

to remain:

```text
<= INT_MAX
```

Therefore:

```text
result * 10 + digit <= INT_MAX
```

Rearrange:

```text
result * 10 <= INT_MAX - digit
```

Therefore:

```text
result <= (INT_MAX - digit) / 10
```

Integer division gives:

```python
(result <= (INT_MAX - digit) // 10)
```

So before multiplying, we check whether doing so would overflow.

🔥 This is the kind of detail interviewers may ask.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static int myAtoi(String s) {

        int INT_MAX = Integer.MAX_VALUE;
        int INT_MIN = Integer.MIN_VALUE;

        int i = 0;
        int n = s.length();

        // Step 1: Skip leading spaces
        while (i < n && s.charAt(i) == ' ') {
            i++;
        }

        // Step 2: Check sign
        int sign = 1;

        if (i < n &&
            (s.charAt(i) == '+' || s.charAt(i) == '-')) {

            if (s.charAt(i) == '-') {
                sign = -1;
            }

            i++;
        }

        // Step 3: Build number
        int result = 0;

        while (i < n &&
               Character.isDigit(s.charAt(i))) {

            int digit = s.charAt(i) - '0';

            // Step 4: Overflow check
            if (result > (INT_MAX - digit) / 10) {

                if (sign == 1) {
                    return INT_MAX;
                } else {
                    return INT_MIN;
                }
            }

            result = result * 10 + digit;

            i++;
        }

        return result * sign;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter string: ");

        String s = sc.nextLine();

        System.out.println(myAtoi(s));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"   -42abc"
```

Initial:

```text
i = 0
sign = 1
result = 0
```

### Step 1 — Spaces

```text
s[0] = ' '
```

Skip.

```text
i = 1
```

Again:

```text
s[1] = ' '
```

Skip.

```text
i = 2
```

Again:

```text
s[2] = ' '
```

Skip.

```text
i = 3
```

Now:

```text
s[3] = '-'
```

---

### Step 2 — Sign

```text
sign = -1
```

Move:

```text
i = 4
```

---

### Step 3 — Digit `4`

```text
digit = 4
```

```text
result = 0 * 10 + 4
       = 4
```

---

### Step 4 — Digit `2`

```text
digit = 2
```

```text
result = 4 * 10 + 2
       = 42
```

---

### Step 5 — Character `a`

```text
'a'.isdigit()
```

False.

Stop.

Return:

```text
42 * -1
```

Final:

```text
-42
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same input:

```text
"   -42abc"
```

State:

```text
spaces → skip
-      → sign = -1
4      → result = 4
2      → result = 42
a      → stop
```

Final:

```text
-42
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text
n = length of string
```

Worst case, we scan the entire string:

```text
Time = O(n)
```

We maintain only:

```text
i
sign
result
digit
```

Therefore:

```text
Space = O(1)
```

### Final

```text
Time  → O(n)
Space → O(1)
```

This is asymptotically optimal because we may need to inspect every character.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why don't we simply use `int(s)`?

Because the problem defines custom parsing rules.

For example:

```text
"4193 with words"
```

should produce:

```text
4193
```

A general integer conversion function isn't implementing the requested algorithm.

---

### Q2. Why do we stop at the first non-digit?

Because LC 8 defines the number as the consecutive digit sequence after optional whitespace/sign.

Example:

```text
"123abc456"
```

→

```text
123
```

The `456` is ignored.

---

### Q3. Why is the complexity O(n)?

In the worst case, every character may need to be inspected.

Therefore:

```text
O(n)
```

is required.

---

### Q4. What is the hardest part of LC 8?

Not reading digits.

The tricky parts are:

```text
leading spaces
sign
invalid characters
overflow
```

That's why it is Medium difficulty.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 STRING PARSER PATTERN

Whenever you see:

> Convert string according to custom rules

think:

```text
INDEX
  ↓
SKIP
  ↓
CHECK SIGN / PREFIX
  ↓
READ VALID CHARACTERS
  ↓
BUILD RESULT
  ↓
STOP ON INVALID
```

And remember:

```text
result = result * 10 + digit
```

This formula is extremely important.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Forgetting leading spaces.

---

### ❌ Mistake 2

Allowing multiple signs:

```text
"--42"
```

Invalid.

---

### ❌ Mistake 3

Continuing after a non-digit.

```text
"123abc456"
```

must stop at `a`.

---

### ❌ Mistake 4

Ignoring integer overflow.

For a true LC 8 solution, overflow handling is required.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you see:

> String → Integer with rules

think:

```text
PARSER
 ↓
skip spaces
 ↓
read sign
 ↓
read digits
 ↓
result = result * 10 + digit
 ↓
stop invalid
 ↓
handle overflow
```

🔥 **LC 8 is a parser problem, not a simple conversion problem.**

---

# 🟢 PROBLEM 34 COMPLETE

---

# 🔴 PROBLEM 35 — MOST FREQUENT CHARACTER

### Exact LeetCode Match

❌ **No exact canonical LeetCode problem for this basic formulation.**

There are related frequency problems such as LC 451, but LC 451 asks you to **sort characters by frequency**, which is a different task.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This problem combines two patterns you already learned:

```text
Frequency Map
       +
Running Maximum
```

Example:

```text
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

Maximum frequency = 2.

There is a tie:

```text
r
g
m
```

For our version:

> Return the **first character** that reaches the maximum frequency in original order.

So the result is:

```text
r
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, find the character occurring the most times.

Example:

```text
Input:
banana
```

Frequency:

```text
b → 1
a → 3
n → 2
```

Output:

```text
a
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

This problem naturally breaks into two phases.

### Phase 1

Count:

```text
character → frequency
```

### Phase 2

Find the maximum frequency.

```text
best_count = 0
best_char = ''
```

For each character:

```text
if frequency[ch] > best_count:
    update
```

This is:

```text
FREQUENCY
   ↓
RUNNING MAX
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Build frequency map.

### Step 2

Set:

```python
best_char = ''
best_count = 0
```

### Step 3

Traverse the original string.

### Step 4

If:

```python
frequency[ch] > best_count
```

update both.

### Step 5

Return `best_char`.

Using `>` rather than `>=` ensures the first maximum is retained.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
s = input("Enter a string: ")

frequency = {}

# Step 1: Count frequency
for ch in s:
    frequency[ch] = frequency.get(ch, 0) + 1

# Step 2: Find maximum
best_char = ''
best_count = 0

for ch in s:

    if frequency[ch] > best_count:
        best_count = frequency[ch]
        best_char = ch

print("Most frequent character:", best_char)
print("Frequency:", best_count)
```

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

        // Step 1: Count frequency
        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            frequency.put(
                ch,
                frequency.getOrDefault(ch, 0) + 1
            );
        }

        // Step 2: Find maximum
        char bestChar = '\0';
        int bestCount = 0;

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            if (frequency.get(ch) > bestCount) {

                bestCount = frequency.get(ch);
                bestChar = ch;
            }
        }

        System.out.println(
            "Most frequent character: " + bestChar
        );

        System.out.println(
            "Frequency: " + bestCount
        );
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
"banana"
```

### Frequency phase

```text
b → 1
a → 3
n → 2
```

Now:

```text
best_char = ''
best_count = 0
```

### Scan original string

`b`:

```text
frequency[b] = 1

1 > 0
```

Update:

```text
best_char = b
best_count = 1
```

`a`:

```text
frequency[a] = 3

3 > 1
```

Update:

```text
best_char = a
best_count = 3
```

`n`:

```text
2 > 3
```

False.

`a`:

```text
3 > 3
```

False.

Continue.

Final:

```text
a → 3
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same:

```text
banana

frequency:
b → 1
a → 3
n → 2

best:
b → 1
a → 3
n → no update
```

Answer:

```text
a
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Frequency construction:

```text
O(n)
```

Finding maximum:

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

where `k` = distinct characters.

Therefore:

```text
Time  → O(n)
Space → O(k)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why don't we sort characters by frequency?

Sorting is unnecessary if we only need the maximum.

Frequency + linear scan gives:

```text
O(n)
```

---

### Q2. What happens if multiple characters have the same maximum frequency?

Our code uses:

```python
>
```

not:

```python
>=
```

Therefore the first maximum in the original string is retained.

---

### Q3. Could we combine frequency counting and maximum tracking into one pass?

Yes, you can update the maximum whenever a frequency is incremented.

For example:

```python
frequency[ch] += 1

if frequency[ch] > best_count:
    best_count = frequency[ch]
    best_char = ch
```

That can be implemented in one traversal.

However, the two-phase version is often easier for beginners to reason about.

---

### Q4. What's the core pattern?

```text
Frequency Map + Running Maximum
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

🔥 Important combination:

```text
COUNT
  ↓
COMPARE
  ↓
MAXIMUM
```

Template:

```python
freq = {}

for x in data:
    freq[x] = freq.get(x, 0) + 1

best = None
best_count = 0

for x in data:
    if freq[x] > best_count:
        best = x
        best_count = freq[x]
```

This pattern will appear again in more advanced problems.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using:

```python
max(frequency)
```

That finds the largest **key**, not the most frequent character.

---

### ❌ Mistake 2

Using `>=` when the problem requires the first maximum.

That would select the last tied maximum.

---

### ❌ Mistake 3

Sorting unnecessarily.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Question:

> Find most frequent character.

Brain:

```text
Frequency Map
      ↓
Running Maximum
      ↓
O(n)
```

---

# 🟢 PROBLEM 35 COMPLETE

---

# 🔴 PROBLEM 36 — CHECK STRING ROTATION

### Exact LeetCode Match

🔥 **LC 796 — Rotate String**

Difficulty: **Easy**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is a beautiful string property problem.

Suppose:

```text
s = "abcde"
```

Rotations include:

```text
abcde
bcdea
cdeab
deabc
eabcd
```

Now imagine:

```text
s + s
```

```text
abcdeabcde
```

Every possible rotation of `s` appears as a substring inside `s + s`.

Therefore:

# 🔥 ROTATION PROPERTY

```text
goal:
Is goal a rotation of s?

check:
goal in (s + s)
```

But we must also check equal length.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given two strings:

```text
s = "abcde"
goal = "cdeab"
```

Is `goal` a rotation of `s`?

Yes.

Because:

```text
abcde
   ↓ rotate
cdeab
```

Another:

```text
s = "abcde"
goal = "abced"
```

Not a rotation.

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Take:

```text
s = "abcde"
```

Duplicate it:

```text
s + s
```

gives:

```text
abcdeabcde
```

Now look for:

```text
cdeab
```

It exists:

```text
abcdeabcde
  ↑↑↑↑↑
 cdeab
```

Therefore it's a valid rotation.

### Why does this work?

Imagine cutting the circular string at a different point.

Every rotation is simply a different starting point on the same circle.

Duplicating the string gives us all possible starting positions linearly.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Check lengths.

```text
if len(s) != len(goal):
    return False
```

### Step 2

Create:

```text
s + s
```

### Step 3

Check whether `goal` occurs inside it.

```python
goal in (s + s)
```

### Step 4

Return the result.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python
def is_rotation(s, goal):

    if len(s) != len(goal):
        return False

    return goal in (s + s)


s = input("Enter first string: ")
goal = input("Enter second string: ")

print(is_rotation(s, goal))
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java
import java.util.Scanner;

public class Main {

    public static boolean isRotation(String s, String goal) {

        if (s.length() != goal.length()) {
            return false;
        }

        return (s + s).contains(goal);
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter first string: ");
        String s = sc.nextLine();

        System.out.print("Enter second string: ");
        String goal = sc.nextLine();

        System.out.println(isRotation(s, goal));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text
s = "abcde"
goal = "cdeab"
```

### Length check

```text
5 == 5
```

Pass.

### Duplicate

```text
s + s
```

becomes:

```text
abcdeabcde
```

Check:

```text
"cdeab" in "abcdeabcde"
```

Yes.

Therefore:

```text
True
```

---

### Non-rotation example

```text
s = "abcde"
goal = "abced"
```

Lengths equal.

```text
abcdeabcde
```

Does it contain:

```text
abced
```

No.

Therefore:

```text
False
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

```text
s = abcde
goal = cdeab
```

Create:

```text
abcdeabcde
```

`contains("cdeab")`:

```text
true
```

Return:

```text
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Creating:

```text
s + s
```

takes:

```text
O(n)
```

Substring search using the language's built-in implementation is generally efficient, but the exact worst-case complexity depends on the underlying implementation.

For placement-level analysis, the standard expected discussion is:

```text
Time ≈ O(n)
Space = O(n)
```

because the doubled string requires O(n) additional storage.

### Important interview nuance

Don't blindly claim every substring search implementation is mathematically O(n).

If the interviewer asks for strict worst-case substring matching, you can mention algorithms such as:

```text
KMP
```

But for the basic LC 796 problem, the concatenation property is the key insight.

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we check equal lengths first?

A rotation does not change the number of characters.

Therefore:

```text
different lengths → impossible
```

---

### Q2. Why does `s + s` contain every rotation?

Because every rotation corresponds to choosing a different starting point in the circular representation of `s`.

The duplicated string exposes those circular continuations linearly.

---

### Q3. Can we solve it without `s + s`?

Yes.

You could manually try each possible rotation.

But that is more complicated and can lead to:

```text
O(n²)
```

The concatenation property gives a much cleaner solution.

---

### Q4. Is `"abc"` a rotation of `"abcabc"`?

No.

Lengths differ:

```text
3 != 6
```

so immediately:

```text
False
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 ROTATION = CONCATENATION PROPERTY

Memorize:

```text
Same length
     +
goal in s+s
     ↓
Rotation
```

Template:

```python
if len(s) != goal.length:
    return False

return goal in s + s
```

This is a classic **mathematical/string property shortcut**.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Checking:

```python
s in goal
```

That's not rotation logic.

---

### ❌ Mistake 2

Forgetting equal length.

---

### ❌ Mistake 3

Actually generating every rotation.

Unnecessary for this problem.

---

### ❌ Mistake 4

Confusing rotation with anagram.

These are very different.

```text
Anagram:
same characters + same frequencies

Rotation:
same order preserved cyclically
```

Example:

```text
abc
bca
```

Both anagrams **and** rotations.

But:

```text
abc
acb
```

are anagrams but **not rotations**.

🔥 Excellent interview distinction.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

Question:

> Is one string a rotation of another?

Think immediately:

```text
Same length?
     ↓
s + s
     ↓
goal inside?
     ↓
YES → rotation
```

---

# 🟢 PROBLEM 36 COMPLETE

# 🏆 DAY 4 — SESSION 2 COMPLETE

Current progress:

```text
DAY 1 → ██████████ 10/10
DAY 2 → ██████████ 10/10
DAY 3 → ██████████ 10/10
DAY 4 → ██████░░░░ 6/10
```

# 📊 TOTAL = 36 / 100

🔥 **36% completed.**

---

# 🧠 TODAY'S 3 MAJOR PATTERNS

## 1️⃣ PARSER

```text
String
 ↓
Skip
 ↓
Sign
 ↓
Read valid characters
 ↓
Build result
 ↓
Stop
```

LC 8.

---

## 2️⃣ FREQUENCY + MAXIMUM

```text
String
 ↓
Frequency Map
 ↓
Running Maximum
```

---

## 3️⃣ ROTATION PROPERTY

```text
Same length
 +
goal ∈ s+s
 =
rotation
```

---

# 🧪 SESSION 2 — INDEPENDENT PRACTICE

## 🟢 LEVEL 1 — REPRODUCTION

### Problem A — LC 8

Predict:

```text
"42"
"   -42"
"4193 with words"
"words and 987"
"+123"
"-912abc"
```

Then implement.

---

### Problem B — Most Frequent

```text
"banana"
```

Expected:

```text
a → 3
```

---

### Problem C — Rotation

```text
s = "waterbottle"
goal = "erbottlewat"
```

Determine whether it is a rotation.

---

# 🟡 LEVEL 2 — VARIATIONS

### Variation 1 — Atoi

Test:

```text
"   +00123abc"
"00042"
"-00056xyz"
"91283472332"
"-91283472332"
```

---

### Variation 2 — Most Frequent Character

Input:

```text
"mississippi"
```

Find the most frequent character.

If multiple characters tie, return the **first** one in the original string.

---

### Variation 3 — Rotation

Test:

```text
"abcde", "cdeab"
"abcde", "abced"
"aa", "aa"
"abc", "abc"
"abc", "abcd"
```

Predict the answers before running code.

---

# 🟠 LEVEL 3 — COMBINED PROBLEM

Given two strings:

```text
s1 = "programming"
s2 = "grammingpro"
```

Your program must:

1. Check whether `s2` is a rotation of `s1`.
2. If yes, find the most frequent character in `s1`.
3. Print its frequency.

This combines:

```text
Rotation + Frequency Map + Maximum
```

---

# 🔴 MASTER TEST — NO SOLUTION

Don't look back.

### Test 1

Implement your own `atoi` for:

```text
"   -2048abc"
```

Expected:

```text
-2048
```

### Test 2

Find the most frequent character:

```text
"engineering"
```

### Test 3

Check:

```text
s = "machinelearning"
goal = "learningmachine"
```

Is it a rotation?

### Test 4

Explain **in one sentence** why:

```text
goal in s + s
```

works for rotation detection.

---

# 🎯 MASTERY CHECK

Before Session 3, you should be able to write these from memory:

### Parser

```python
result = result * 10 + digit
```

### Frequency + maximum

```python
freq[ch] = freq.get(ch, 0) + 1
```

followed by a running maximum.

### Rotation

```python
len(s) == len(goal) and goal in s + s
```

If these three patterns are automatic, **Session 2 is genuinely learned**.

---

# 🔜 NEXT — DAY 4 SESSION 3

Problems **37–40**:

1. 🔥 **Longest Common Prefix — LC 14**
2. **Check Pangram — LC 1832**
3. **Run-Length Encoding**
4. 🔥 **Balanced Brackets — LC 20**

The final problem introduces the **Stack pattern**, which will become important later in your DSA roadmap.

Would you like to start with the Day 4 Session 2 master test, or review any one of the three patterns first?


# 🔥 DAY 4 — SESSION 3

## STRING PROBLEM SOLVING — PROBLEMS 37–40

You have completed:

* ✅ Day 1 → 10/10
* ✅ Day 2 → 10/10
* ✅ Day 3 → 10/10
* ✅ Day 4 Session 1 → 31–33
* ✅ Day 4 Session 2 → 34–36
* 🎯 Current progress → **36/100**
* 🚀 Today's final session → **37–40**

---

# 🧠 TODAY'S CORE THEME

Today's session finishes the **String Problem-Solving** day.

The four problems introduce four highly reusable patterns:

```text
37 → Prefix Comparison
38 → Set / Coverage
39 → Compression / Counting Consecutive Characters
40 → Stack / Matching
```

The most important transition is:

```text
String
  ↓
Pattern Recognition
  ↓
Choose the right data structure
```

Especially **Problem 40 — Balanced Brackets**.

When you see:

> matching brackets / nested brackets / opening-closing pairs

your brain should immediately think:

# 🔥 STACK

---

# 🔴 PROBLEM 37 — LONGEST COMMON PREFIX

## Exact LeetCode Match

🔥 **LC 14 — Longest Common Prefix**

Difficulty: **Easy**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Suppose:

```text id="e3k5gu"
["flower", "flow", "flight"]
```

The longest prefix common to all three is:

```text id="74h1mt"
"fl"
```

The important word is:

# PREFIX

A prefix starts from the **beginning**.

For:

```text id="5v3x3f"
"flower"
```

prefixes include:

```text id="3pjjrx"
f
fl
flo
flow
flowe
flower
```

But:

```text id="r6v4gh"
"lower"
```

is not a prefix of `"flower"`.

---

# 🔥 Senior recognition

Whenever you see:

> common beginning / common prefix

think:

```text id="u4cz9y"
Compare characters at the same index.
```

You do **not** need:

* HashMap
* Sorting
* Stack
* Binary search

The simplest optimal idea is vertical comparison.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given an array of strings, find their longest common prefix.

### Example

```text id="8o3pvr"
["flower", "flow", "flight"]
```

Compare:

```text id="w7ijx8"
index 0 → f f f
index 1 → l l l
index 2 → o o i  ❌
```

Stop.

Answer:

```text id="q6d1av"
"fl"
```

---

### Example 2

```text id="ys4b6t"
["dog", "racecar", "car"]
```

At index 0:

```text id="xj7j2g"
d != r
```

Therefore:

```text id="y31p9f"
""
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Take the first string as the reference:

```text id="7trj9h"
flower
```

Compare it against every other string.

Start with:

```text id="z4oq0k"
prefix = "flower"
```

Compare with `"flow"`.

Common part:

```text id="1z2l8n"
"flow"
```

Now:

```text id="r8b1op"
prefix = "flow"
```

Compare `"flow"` with `"flight"`.

Common part:

```text id="9g1z6f"
"fl"
```

Final:

```text id="0o1uk6"
"fl"
```

### ELI10 analogy

Imagine several words standing in a line.

You ask:

> "How many letters do all of you agree on from the beginning?"

The moment one person gives a different letter:

```text
STOP.
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

If there are no strings:

```text id="l1t3s4"
return ""
```

### Step 2

Take the first string as the current prefix.

### Step 3

Compare the prefix with each remaining string.

### Step 4

While characters match, continue.

### Step 5

Stop at:

* mismatch
* end of either string

### Step 6

Update prefix.

### Step 7

If prefix becomes empty, return immediately.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="z0j4m9"
def longest_common_prefix(strs):

    if not strs:
        return ""

    prefix = strs[0]

    for i in range(1, len(strs)):

        word = strs[i]

        j = 0

        while j < len(prefix) and j < len(word):
            if prefix[j] != word[j]:
                break

            j += 1

        prefix = prefix[:j]

        if prefix == "":
            return ""

    return prefix


n = int(input("Enter number of strings: "))

strs = []

for _ in range(n):
    strs.append(input())

print("Longest Common Prefix:", longest_common_prefix(strs))
```

### Short Python version

A common alternative:

```python id="y1r0j6"
def longest_common_prefix(strs):

    if not strs:
        return ""

    prefix = strs[0]

    for word in strs[1:]:

        while not word.startswith(prefix):
            prefix = prefix[:-1]

            if not prefix:
                return ""

    return prefix
```

The first version makes the character comparison logic clearer.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="f0r8wk"
import java.util.Scanner;

public class Main {

    public static String longestCommonPrefix(String[] strs) {

        if (strs.length == 0) {
            return "";
        }

        String prefix = strs[0];

        for (int i = 1; i < strs.length; i++) {

            String word = strs[i];

            int j = 0;

            while (j < prefix.length()
                    && j < word.length()
                    && prefix.charAt(j) == word.charAt(j)) {

                j++;
            }

            prefix = prefix.substring(0, j);

            if (prefix.isEmpty()) {
                return "";
            }
        }

        return prefix;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of strings: ");

        int n = sc.nextInt();
        sc.nextLine();

        String[] strs = new String[n];

        for (int i = 0; i < n; i++) {
            strs[i] = sc.nextLine();
        }

        System.out.println(
            "Longest Common Prefix: "
            + longestCommonPrefix(strs)
        );
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="n4v50h"
["flower", "flow", "flight"]
```

Initial:

```text id="a8kknb"
prefix = "flower"
```

### Compare with `"flow"`

```text id="c6r8nz"
f == f → yes
l == l → yes
o == o → yes
w == w → yes
```

`"flow"` ends.

Therefore:

```text id="i5ompc"
prefix = "flow"
```

---

### Compare `"flow"` with `"flight"`

```text id="2a9fif"
f == f → yes
l == l → yes
o != i → STOP
```

Therefore:

```text id="5xg0p6"
prefix = "fl"
```

Final:

```text id="z8qj9f"
"fl"
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same comparison:

```text id="c9d2qn"
flower
  ↓
flow
  ↓
fl
```

Final:

```text id="gn7i2c"
fl
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="4j3e4h"
N = number of strings
M = length of shortest string
```

In the worst case, we compare roughly:

```text id="c7p8vq"
N × M
```

characters.

Therefore:

```text id="3v0t40"
Time = O(N × M)
```

Space depends on the implementation.

Ignoring the output and input storage:

```text id="k4d6lw"
Auxiliary Space = O(1)
```

The prefix itself can contain up to `M` characters, so if counting output storage:

```text id="g6n31p"
O(M)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why compare only up to the shortest string?

A common prefix cannot be longer than the shortest string.

---

### Q2. Why can we stop immediately after a mismatch?

Once two strings differ at position `j`, no later characters can make that prefix common again.

---

### Q3. Can sorting solve this?

Yes.

If sorted, the common prefix only needs to be compared between the first and last strings.

But sorting adds:

```text id="f1s7q0"
O(N log N)
```

and is unnecessary.

---

### Q4. What is the main pattern?

```text id="2vq5oh"
Position-by-position comparison.
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 PREFIX COMPARISON

Think:

```text id="4q5n8m"
Same starting characters?
       ↓
Compare same index
       ↓
Stop at mismatch
```

Master idea:

> A prefix problem is usually about comparing from index `0` forward.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Confusing prefix with substring.

---

### ❌ Mistake 2

Comparing characters at different indexes.

---

### ❌ Mistake 3

Continuing after mismatch.

---

### ❌ Mistake 4

Forgetting the shortest string boundary.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="l0du9s"
Longest Common Prefix
        ↓
Start at index 0
        ↓
Compare characters
        ↓
Stop at mismatch
        ↓
Return common part
```

---

# 🟢 PROBLEM 37 COMPLETE

---

# 🔴 PROBLEM 38 — CHECK PANGRAM

## Exact LeetCode Match

🔥 **LC 1832 — Check if the Sentence Is Pangram**

Difficulty: **Easy**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

A pangram is a sentence containing **every letter of the English alphabet at least once**.

There are:

```text id="v2bdxk"
26
```

English lowercase letters.

Example:

```text id="xxjzse"
"The quick brown fox jumps over the lazy dog"
```

is a pangram.

The important pattern:

# 🔥 COVERAGE / SET

We don't care how many times a letter appears.

We only care:

> Have we seen this letter?

Therefore:

```text id="t2v7kr"
seen = set()
```

Add every alphabetic character.

At the end:

```text id="9ukfca"
len(seen) == 26
```

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Input:

```text id="xyu6dg"
"thequickbrownfoxjumpsoverthelazydog"
```

Every letter `a` through `z` appears.

Therefore:

```text id="v7v1sf"
True
```

Input:

```text id="s4p4w8"
"hello world"
```

Many letters are missing.

Therefore:

```text id="yx7d8r"
False
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Think of a checklist:

```text id="e3x7q0"
a ✓
b ✓
c ✓
d ✓
...
z ✓
```

Every time you see a letter:

```text id="snn3jv"
seen.add(letter)
```

At the end:

```text id="p2d1i1"
26 different letters?
```

If yes:

```text id="h9n1pq"
Pangram
```

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Create empty set.

### Step 2

Traverse sentence.

### Step 3

Convert character to lowercase.

### Step 4

If it is a letter:

```text id="l7u7j7"
add to set
```

### Step 5

If set size reaches 26:

```text id="4q6j8y"
return True
```

This is an excellent **early-exit optimization**.

### Step 6

If traversal ends and fewer than 26 letters exist:

```text id="7d1k8m"
return False
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="e5w6pt"
def is_pangram(sentence):

    seen = set()

    for ch in sentence.lower():

        if 'a' <= ch <= 'z':
            seen.add(ch)

            if len(seen) == 26:
                return True

    return False


s = input("Enter a sentence: ")

print(is_pangram(s))
```

### Why this is efficient

We stop as soon as all 26 letters have been found.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="5ftq6q"
import java.util.HashSet;
import java.util.Scanner;
import java.util.Set;

public class Main {

    public static boolean isPangram(String sentence) {

        Set<Character> seen = new HashSet<>();

        sentence = sentence.toLowerCase();

        for (int i = 0; i < sentence.length(); i++) {

            char ch = sentence.charAt(i);

            if (ch >= 'a' && ch <= 'z') {

                seen.add(ch);

                if (seen.size() == 26) {
                    return true;
                }
            }
        }

        return false;
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter sentence: ");

        String s = sc.nextLine();

        System.out.println(isPangram(s));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="5f8t9h"
"The quick brown fox jumps over the lazy dog"
```

We scan letters.

Eventually:

```text id="6y75zz"
a
b
c
d
...
z
```

are all present.

At the moment:

```text id="9c4r40"
len(seen) == 26
```

we immediately return:

```text id="s1d5fl"
True
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text id="1z6vsi"
character
    ↓
is a-z?
    ↓
add to HashSet
    ↓
size == 26?
    ↓
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="i47c3d"
n = sentence length
```

We scan at most `n` characters:

```text id="9v0at1"
Time = O(n)
```

The set can contain at most 26 letters:

```text id="f0k91n"
Space = O(26)
```

Since 26 is constant:

```text id="iy5h2h"
Space = O(1)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why use a set instead of a list?

We only care whether a letter exists.

A set naturally represents uniqueness.

---

### Q2. Why is space O(1)?

There are only 26 lowercase English letters.

The set cannot grow beyond 26 elements.

---

### Q3. Why convert to lowercase?

Because:

```text id="5r4y5j"
'A'
'a'
```

should represent the same alphabet letter if the problem is case-insensitive.

---

### Q4. Can we use a Boolean array?

Yes.

```python id="m7xj7u"
seen = [False] * 26
```

That is another excellent O(n) / O(1) solution.

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 COVERAGE PATTERN

Question:

> Have we seen every required item?

Think:

```text id="j3b6p0"
seen = set()
```

Examples:

* Pangram
* Unique elements
* Required characters
* Visited nodes
* Distinct values

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Counting frequency when frequency doesn't matter.

---

### ❌ Mistake 2

Forgetting case normalization.

---

### ❌ Mistake 3

Counting spaces/punctuation as alphabet letters.

---

### ❌ Mistake 4

Not using early exit when all 26 letters are already found.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="7z9i5x"
Pangram
 ↓
Need all 26 letters
 ↓
Set
 ↓
len(set) == 26
```

---

# 🟢 PROBLEM 38 COMPLETE

---

# 🔴 PROBLEM 39 — RUN-LENGTH ENCODING

### Exact LeetCode Match

❌ **No exact canonical LeetCode problem for this basic formulation.**

There are related compression problems, but we will treat this as the standard placement-level **Run-Length Encoding (RLE)** problem.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

Run-Length Encoding compresses **consecutive repeated characters**.

Example:

```text id="f7f5up"
aaabbcccc
```

becomes:

```text id="10b0yv"
a3b2c4
```

Important:

```text id="72j2v4"
aaabbcccc
```

means:

```text id="i1glk5"
aaa → a3
bb  → b2
cccc → c4
```

But:

```text id="54sqj4"
abab
```

does NOT become:

```text id="w0m57p"
a2b2
```

because the `a`s are not consecutive.

It remains:

```text id="l29tqu"
a1b1a1b1
```

🔥 This distinction is extremely important.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string, encode consecutive groups as:

```text id="c0tqkl"
character + count
```

Examples:

```text id="t4w2fy"
aaabbc → a3b2c1
```

```text id="zv3w6j"
wwwwaaadex → w4a3d1e1x1
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Use two pointers conceptually:

```text id="3l0u2f"
start
  ↓
current run
  ↓
count consecutive equal characters
```

For:

```text id="g8ppr4"
aaabbc
```

Start at first `a`.

Count:

```text id="o0t1u6"
a a a
```

count = 3.

Then move to `b`.

Count:

```text id="h1z8n3"
b b
```

count = 2.

Then `c`.

count = 1.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

### Step 1

Start at index `i = 0`.

### Step 2

Store current character.

```python id="7z9d6n"
ch = s[i]
```

### Step 3

Set:

```python id="j4j9b5"
count = 0
```

### Step 4

Move forward while characters are equal.

### Step 5

Append:

```text id="f5e9r0"
character + count
```

### Step 6

Move to the next run.

### Step 7

Continue until the string ends.

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="s4qv1f"
def run_length_encode(s):

    if not s:
        return ""

    result = []

    i = 0

    while i < len(s):

        ch = s[i]
        count = 0

        while i < len(s) and s[i] == ch:

            count += 1
            i += 1

        result.append(ch + str(count))

    return ''.join(result)


s = input("Enter string: ")

print("Encoded:", run_length_encode(s))
```

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="8d2r8v"
import java.util.Scanner;

public class Main {

    public static String runLengthEncode(String s) {

        if (s.isEmpty()) {
            return "";
        }

        StringBuilder result = new StringBuilder();

        int i = 0;

        while (i < s.length()) {

            char ch = s.charAt(i);

            int count = 0;

            while (i < s.length()
                    && s.charAt(i) == ch) {

                count++;
                i++;
            }

            result.append(ch);
            result.append(count);
        }

        return result.toString();
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter string: ");

        String s = sc.nextLine();

        System.out.println(
            "Encoded: " + runLengthEncode(s)
        );
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="8g1q8j"
aaabbc
```

Initial:

```text id="9p0plk"
i = 0
```

### Run 1

```text id="crw5ju"
ch = a
```

Process:

```text id="x4w2c7"
a → count 1
a → count 2
a → count 3
```

Now next character:

```text id="9y7n8v"
b
```

Append:

```text id="j8t4m4"
a3
```

---

### Run 2

```text id="wdm9bm"
b
```

Process:

```text id="e7k2yp"
b → 1
b → 2
```

Append:

```text id="t0h8df"
b2
```

---

### Run 3

```text id="0t9r0u"
c
```

Count:

```text id="1m9wjd"
1
```

Append:

```text id="zv6c6a"
c1
```

Final:

```text id="twq3ka"
a3b2c1
```

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text id="00p2et"
aaabbc

aaa → a3
bb  → b2
c   → c1
```

Result:

```text id="5n3f0g"
a3b2c1
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

This looks like nested loops:

```python id="r5sq4y"
while outer:
    while inner:
```

But don't automatically conclude O(n²).

Why?

Because the inner loop advances `i`.

Each character is processed exactly once.

Therefore:

```text id="rvj9z7"
Time = O(n)
```

Output storage:

```text id="n5by87"
O(n)
```

So:

```text id="g8h4g8"
Time  → O(n)
Space → O(n)
```

🔥 This is a classic interview question:

> Nested loops do not automatically mean O(n²).

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why isn't this O(n²)?

Because `i` never moves backward.

Across all inner loops, every character is processed once.

Therefore total work is:

```text id="v7p4r6"
O(n)
```

---

### Q2. What does run-length encoding count?

**Consecutive** repeated characters.

Not total frequency.

Example:

```text id="g1r8i6"
aabaa
```

RLE:

```text id="8d2x5n"
a2b1a2
```

Frequency would be:

```text id="w8j1ip"
a → 4
b → 1
```

Completely different.

---

### Q3. Can this be done in-place?

Yes, if working with a mutable character array and following a specific compression-output constraint.

But for our basic placement version, constructing a result is clearer.

---

### Q4. What happens for an empty string?

Return:

```text id="2h7zv8"
""
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 CONSECUTIVE GROUPING PATTERN

Think:

```text id="wzj0ag"
Current item
    ↓
Count consecutive equal items
    ↓
Write group
    ↓
Move to next group
```

This pattern is useful for:

* Run-Length Encoding
* compressing repeated values
* grouping consecutive elements
* basic string compression
* sequence processing

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using a frequency map.

That counts total occurrences, not consecutive occurrences.

---

### ❌ Mistake 2

Forgetting the final group.

---

### ❌ Mistake 3

Thinking nested loops automatically mean O(n²).

Here the pointer moves forward globally.

---

### ❌ Mistake 4

Not handling empty strings.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

```text id="20d44g"
RLE
 ↓
Take current character
 ↓
Count consecutive copies
 ↓
Append character + count
 ↓
Move to next group
```

Complexity:

```text id="h1n9zv"
O(n) time
O(n) output space
```

---

# 🟢 PROBLEM 39 COMPLETE

---

# 🔴 PROBLEM 40 — BALANCED BRACKETS

## Exact LeetCode Match

🔥 **LC 20 — Valid Parentheses**

Difficulty: **Easy**

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS 🧠

This is the most important problem of today's session.

Why?

Because it introduces a fundamental data structure:

# 🔥 STACK

Given:

```text id="y9s0ak"
"()[]{}"
```

Valid.

But:

```text id="z3n0q2"
"([)]"
```

Invalid.

Why?

Because brackets must close in **reverse order of opening**.

Example:

```text id="7yn2or"
([{}])
```

Opening sequence:

```text id="s1t2v4"
(
[
{
```

Closing sequence must be:

```text id="o5j5jm"
}
]
)
```

That's:

```text id="d8d7xx"
Last opened
    ↓
First closed
```

That is exactly:

# LIFO — Last In, First Out

And that's what a stack provides.

---

# 🔹 BLOCK 2 — PROBLEM UNDERSTANDING 📖

Given a string containing:

```text id="s3x1pf"
()
{}
[]
```

determine whether brackets are correctly matched.

### Valid

```text id="9emz8v"
()
[] 
{}
({[]})
```

### Invalid

```text id="vl5qka"
(]
([)]
(((
```

---

# 🔹 BLOCK 3 — LOGIC / INTUITION 💡

Imagine stacking plates.

```text id="plj5w8"
Plate A
Plate B
Plate C
```

Which plate do you remove first?

```text id="q1h9yz"
C
```

because C was placed last.

Same with brackets.

For:

```text id="8x7w90"
{ [ ( ) ] }
```

When we see:

```text id="0axq0a"
{
```

push it.

Then:

```text id="h9j6as"
[
```

push it.

Then:

```text id="5os2ak"
(
```

push it.

When `)` arrives:

```text id="yby2k8"
top must be (
```

Correct → pop.

Then `]`:

```text id="z9q5jw"
top must be [
```

Correct → pop.

Then `}`:

```text id="i3v4ft"
top must be {
```

Correct → pop.

At the end:

```text id="c7zv6q"
stack empty
```

Therefore valid.

---

# 🔹 BLOCK 4 — ALGORITHM — STEP BY STEP ⚙️

We'll use:

```python id="w0k7c4"
stack = []
```

and a mapping:

```python id="v0fmb9"
')' → '('
']' → '['
'}' → '{'
```

### Step 1

Traverse each character.

### Step 2

If opening bracket:

```text id="zv3k54"
push
```

### Step 3

If closing bracket:

Check:

```text id="u6c1v0"
Is stack empty?
```

If yes:

```text id="1ff3tb"
False
```

Otherwise check:

```text id="z1x1w6"
stack[-1] == matching opening bracket
```

If not:

```text id="mx7pxb"
False
```

### Step 4

If correct:

```python id="6h5h2j"
stack.pop()
```

### Step 5

At the end:

```python id="e0e4jr"
return len(stack) == 0
```

---

# 🔹 BLOCK 5 — OPTIMAL PYTHON SOLUTION 🐍

```python id="0i5d4u"
def is_valid(s):

    stack = []

    matching = {
        ')': '(',
        ']': '[',
        '}': '{'
    }

    for ch in s:

        # Opening bracket
        if ch in '([{':
            stack.append(ch)

        # Closing bracket
        else:

            if not stack:
                return False

            if stack[-1] != matching[ch]:
                return False

            stack.pop()

    return len(stack) == 0


s = input("Enter brackets: ")

print(is_valid(s))
```

### 🔥 Critical assumption

This implementation assumes the input contains only:

```text id="z7rv11"
()[]{}
```

which matches LC 20.

If arbitrary characters are allowed, the algorithm should explicitly decide how those characters should be handled.

---

# 🔹 BLOCK 6 — OPTIMAL JAVA SOLUTION ☕

```java id="n3sqy1"
import java.util.HashMap;
import java.util.Map;
import java.util.Scanner;
import java.util.Stack;

public class Main {

    public static boolean isValid(String s) {

        Stack<Character> stack = new Stack<>();

        Map<Character, Character> matching = new HashMap<>();

        matching.put(')', '(');
        matching.put(']', '[');
        matching.put('}', '{');

        for (int i = 0; i < s.length(); i++) {

            char ch = s.charAt(i);

            // Opening bracket
            if (ch == '(' || ch == '[' || ch == '{') {

                stack.push(ch);
            }

            // Closing bracket
            else {

                if (stack.isEmpty()) {
                    return false;
                }

                if (stack.peek() != matching.get(ch)) {
                    return false;
                }

                stack.pop();
            }
        }

        return stack.isEmpty();
    }

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        System.out.print("Enter brackets: ");

        String s = sc.nextLine();

        System.out.println(isValid(s));
    }
}
```

---

# 🔹 BLOCK 7 — PYTHON DRY RUN 🔬

Input:

```text id="7k9q8m"
"({[]})"
```

Initial:

```text id="3ox2b8"
stack = []
```

### `(`

Opening:

```text id="5v48ju"
push '('
```

Stack:

```text id="o8lq3v"
['(']
```

### `{`

```text id="rx8prj"
push '{'
```

Stack:

```text id="7z10g1"
['(', '{']
```

### `[`

```text id="8k4xdu"
push '['
```

Stack:

```text id="k7f10y"
['(', '{', '[']
```

### `]`

Expected:

```text id="x0m9o7"
[
```

Top:

```text id="7f8ksr"
[
```

Match.

Pop:

```text id="yn02ez"
['(', '{']
```

### `}`

Expected:

```text id="qpxq4a"
{
```

Top:

```text id="5v6hkj"
{
```

Match.

Pop:

```text id="xq8r2p"
['(']
```

### `)`

Expected:

```text id="u3m6yn"
(
```

Top:

```text id="2k9w4f"
(
```

Match.

Pop:

```text id="0g6fvh"
[]
```

End:

```text id="sm8j4p"
stack empty
```

Therefore:

```text id="9f7h2x"
True
```

---

# 🔥 Invalid Example

Input:

```text id="8g7b7d"
"([)]"
```

### `(`

```text id="quh01e"
['(']
```

### `[`

```text id="m9k7l1"
['(', '[']
```

### `)`

Expected:

```text id="v2g1x9"
(
```

But stack top:

```text id="7p8d4q"
[
```

Mismatch.

Immediately:

```text id="c4f1v6"
False
```

🔥 This is why the stack is necessary.

---

# 🔹 BLOCK 8 — JAVA DRY RUN ☕

Same logic:

```text id="x2i5j1"
([{}])

( → push
[ → push
{ → push
} → match + pop
] → match + pop
) → match + pop
```

Stack ends empty.

Result:

```text id="c9x9x4"
true
```

---

# 🔹 BLOCK 9 — COMPLEXITY ANALYSIS 📊

Let:

```text id="8q1vda"
n = length of string
```

Each bracket is:

* pushed once, or
* popped once.

Therefore:

```text id="e5x5zt"
Time = O(n)
```

Worst-case stack size:

```text id="7p0kzq"
O(n)
```

For:

```text id="a7a3i0"
(((((((((
```

every bracket remains in the stack.

Therefore:

```text id="j3j3k6"
Space = O(n)
```

Final:

```text id="m1i2xy"
Time  → O(n)
Space → O(n)
```

---

# 🔹 BLOCK 10 — INTERVIEW Q&A 🎤

### Q1. Why do we need a stack?

Because brackets follow:

```text id="yq7t9d"
LIFO
```

The most recently opened bracket must be closed first.

---

### Q2. Why can't we simply count brackets?

Because counts don't capture order.

For example:

```text id="j3z6wa"
([)]
```

has:

```text id="9fpg0r"
( count = 1
) count = 1
[ count = 1
] count = 1
```

Counts match.

But ordering is invalid.

The stack detects the ordering problem.

---

### Q3. What is the key recognition signal for Stack?

Nested matching relationships:

```text id="f7u6w5"
opening → closing
last opened → first closed
```

Think Stack.

---

### Q4. What if the stack is not empty at the end?

Example:

```text id="u9j5g6"
"((("
```

There are unmatched opening brackets.

Therefore:

```text id="k4a9hp"
False
```

---

# 🔹 BLOCK 11 — PATTERN EXTRACTION 🧩

# 🔥 STACK — MATCHING BRACKETS

Master template:

```python id="7zcl9c"
stack = []

for ch in s:

    if opening(ch):
        stack.append(ch)

    else:

        if not stack:
            return False

        if stack[-1] != matching[ch]:
            return False

        stack.pop()

return not stack
```

Whenever you see:

```text id="6opqvn"
nested
matching
last opened / first closed
```

think:

# STACK.

---

# 🔹 BLOCK 12 — COMMON MISTAKES ⚠️

### ❌ Mistake 1

Using counts only.

Order matters.

---

### ❌ Mistake 2

Using:

```python id="7k2h1q"
stack.pop()
```

without checking whether the stack is empty.

That can cause an error.

---

### ❌ Mistake 3

Checking only whether the bracket type exists.

You must compare against the **top**.

---

### ❌ Mistake 4

Forgetting final stack validation.

```text id="lq1q8m"
"((("
```

has no mismatch while scanning, but it's still invalid.

---

# 🔹 BLOCK 13 — INTERVIEW-READY SUMMARY 🚀

When you hear:

> "Validate brackets."

Immediately think:

```text id="a1m4kr"
STACK
 ↓
Opening → PUSH
 ↓
Closing → compare TOP
 ↓
Match → POP
 ↓
Mismatch → FALSE
 ↓
End → stack empty?
```

🔥 This is one of the most important beginner interview patterns.

---

# 🟢 PROBLEM 40 COMPLETE

# 🏆 DAY 4 COMPLETE — 10/10

You have now completed the entire **String Problem Solving** day.

```text id="x3j5by"
31. Reverse Words                 ✅
32. Longest Word                  ✅
33. Only Digits                   ✅
34. String to Integer             ✅
35. Most Frequent Character       ✅
36. String Rotation               ✅
37. Longest Common Prefix         ✅
38. Pangram                       ✅
39. Run-Length Encoding           ✅
40. Balanced Brackets             ✅
```

---

# 📊 CR2 OVERALL PROGRESS

```text id="m8jv6y"
DAY 1   ██████████ 10/10
DAY 2   ██████████ 10/10
DAY 3   ██████████ 10/10
DAY 4   ██████████ 10/10

TOTAL
████████████████████████████████████████ 40/100
```

# 🔥 40 / 100 COMPLETE

**40% of the entire CR2 bootcamp is done.**

But again:

> 40 solutions read ≠ 40 problems mastered.

---

# 🧠 DAY 4 — PATTERN MAP

You should now recognize these without hesitation:

```text
31 → SPLIT + REVERSE WORDS
32 → RUNNING MAXIMUM
33 → VALIDATION + EARLY EXIT
34 → STRING PARSER
35 → FREQUENCY + RUNNING MAXIMUM
36 → ROTATION PROPERTY
37 → PREFIX COMPARISON
38 → SET / COVERAGE
39 → CONSECUTIVE GROUPING
40 → STACK / LIFO
```

---

# 🔥 THE MOST IMPORTANT TAKEAWAYS

## Pattern 1 — Running Maximum

```python id="n9oh9p"
best = initial

for item in data:
    if better(item, best):
        best = item
```

Used in:

```text id="z8nh5j"
32
35
```

---

## Pattern 2 — Validation

```python id="z3j0f8"
for item in data:
    if invalid(item):
        return False

return True
```

Used in:

```text id="x3r6c7"
33
```

---

## Pattern 3 — Frequency Map

```python id="z8y1au"
freq[item] = freq.get(item, 0) + 1
```

Used in:

```text id="c2v8lo"
35
```

and heavily in:

```text id="g2n1x4"
Day 3
```

---

## Pattern 4 — String Property

```python id="f5r3nw"
len(s) == len(goal) and goal in s + s
```

Used in:

```text id="9v4k3p"
36
```

---

## Pattern 5 — Stack

```python id="m6n5jg"
opening → push
closing → compare top → pop
```

Used in:

```text id="r8x7pt"
40
```

This pattern will become **very important** in your later DSA training.

---

# 🧪 DAY 4 — FINAL MASTER TEST

Do this **without looking at today's solutions**.

## Question 1 — LC 151

Input:

```text id="b9b4z8"
"  I   love   machine   learning  "
```

Expected:

```text id="0d6z6h"
"learning machine love I"
```

---

## Question 2

Find the longest word:

```text id="3fj6gy"
"Python Machine Learning Engineering"
```

---

## Question 3

Check:

```text id="e1s8mx"
"123456789"
"12345A789"
```

---

## Question 4 — LC 8

Convert:

```text id="k5y2y4"
"   -4193 with words"
```

Expected:

```text id="h1d4vi"
-4193
```

---

## Question 5

Find the most frequent character:

```text id="w0p5s6"
"mississippi"
```

---

## Question 6 — LC 796

Check:

```text id="2b6d0o"
"abcde"
"cdeab"
```

---

## Question 7 — LC 14

Find:

```text id="u5q9a0"
["flower", "flow", "flight"]
```

Expected:

```text id="f8m1j7"
"fl"
```

---

## Question 8 — LC 1832

Check:

```text id="4m2v3h"
"The quick brown fox jumps over the lazy dog"
```

Expected:

```text id="7b8n2c"
True
```

---

## Question 9

Run-length encode:

```text id="6k3t1p"
"aaabbcccc"
```

Expected:

```text id="2p4v8r"
"a3b2c4"
```

---

## Question 10 — LC 20

Validate:

```text id="6x9j4q"
"({[]})"
"([)]"
"{[]}"
```

Expected:

```text id="r5x8y2"
True
False
True
```

---

# 🔴 DAY 4 MASTER CHALLENGE

Write **one Python program** that processes:

```text id="3p4w8q"
"  Machine   Learning   Engineer 123  "
```

and performs:

1. Reverse words
2. Find longest word
3. Check whether original string contains only digits
4. Find most frequent character
5. Toggle case
6. Run-length encode the cleaned string

Then separately test your bracket validator on:

```text id="v5n7c2"
"{[()]}"
"([)]"
```

No solution lookup.

---

# 🎯 DAY 4 MASTERY STANDARD

You should be able to reproduce these from memory:

```text
🟢 Split → process → join
🟢 Running maximum
🟢 Validation + early exit
🟢 Parser
🟢 Frequency map
🟢 Rotation via s + s
🟢 Prefix comparison
🟢 Set coverage
🟢 Consecutive grouping
🔴 Stack matching
```

The **Stack pattern from Problem 40** is the one I especially want you to retain.

---

# 🔜 NEXT — DAY 5

## ARRAY FUNDAMENTALS — PROBLEMS 41–50

```text
41. Largest Element
42. Smallest Element
43. Second Largest Distinct Element
44. Reverse Array In-Place
45. Sum & Average of Array
46. Count Even & Odd Elements
47. Check Whether Array Is Sorted
48. Missing Number — LC 268
49. Find Duplicate Element — LC 287
50. Move Zeroes — LC 283
```

Day 5 is where we transition from **String Fundamentals → Array Fundamentals**, and the patterns will start connecting directly to your main DSA preparation.

