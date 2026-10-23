# ⚔️ STACK — CARD 3

# 📚 Pattern-Wise LeetCode Problem Bank

~~~

# 🥇 1. STACK — MUST MASTER

Stack has excellent ROI because it produces several recognizable interview patterns.

### 🔴 P0

- **LC 20 — Valid Parentheses**
- **LC 155 — Min Stack**
- **LC 739 — Daily Temperatures**
- **LC 496 — Next Greater Element I**
- **LC 150 — Evaluate Reverse Polish Notation**

### 🟠 P1

- LC 503 — Next Greater Element II
- LC 853 — Car Fleet
- LC 394 — Decode String
- LC 71 — Simplify Path

### 🟡 P2

- LC 84 — Largest Rectangle in Histogram

**Why important?**

```text
Stack
 ↓
Monotonic Stack
 ↓
Next Greater / Smaller
 ↓
Temperature / Stock / Histogram patterns
```

For your 30-day sprint:

> **20 → 155 → 739 → 496 → 150 → 853**

is the core sequence.

~~~

> **Goal:** This is the **locked Stack practice bank for your ML/MLOps/AI Engineer interview preparation**.
>
> I am deliberately **not** giving you 40–50 random Stack problems. That's inefficient. We want the smallest set that gives you strong coverage of the patterns companies actually use.

We will solve these **one problem at a time in separate conversations**, using the deep solving format.

---

# 🟢 PATTERN 1 — Basic Stack / Matching

### Foundation — MUST MASTER

| # | LeetCode    | Problem                                  | Pattern                           | Priority |
| - | ----------- | ---------------------------------------- | --------------------------------- | -------- |
| 1 | **LC 20**   | Valid Parentheses                        | Matching Stack                    | 🔥🔥🔥   |
| 2 | **LC 1047** | Remove All Adjacent Duplicates In String | Cancellation Stack                | 🔥🔥     |
| 3 | **LC 1544** | Make The String Great                    | Cancellation + Character Matching | 🔥🔥     |

### What this layer teaches

* Push / pop
* Peek
* Empty-stack handling
* Matching
* Cancellation
* Stack invariants

### Mastery requirement

You should be able to look at a problem and immediately recognize:

```text
"most recent unresolved element"
            ↓
          STACK
```

---

# 🟡 PATTERN 2 — Parsing / Nested Structures

These are important because Stack becomes more than just brackets.

| # | LeetCode   | Problem                          | Pattern                | Priority |
| - | ---------- | -------------------------------- | ---------------------- | -------- |
| 4 | **LC 71**  | Simplify Path                    | Stack + Parsing        | 🔥🔥🔥   |
| 5 | **LC 394** | Decode String                    | Nested Parsing + Stack | 🔥🔥🔥   |
| 6 | **LC 150** | Evaluate Reverse Polish Notation | Expression Stack       | 🔥🔥     |
| 7 | **LC 224** | Basic Calculator                 | Expression + Stack     | 🔥🔥     |

### What this layer teaches

```text
Input
 ↓
Parse
 ↓
Store unresolved context
 ↓
Restore context
```

You should understand **why** the stack stores state rather than simply memorizing code.

---

# 🟠 PATTERN 3 — Monotonic Stack: Next Greater / Smaller

# ⭐ MOST IMPORTANT STACK PATTERN

This is where Stack becomes a serious interview algorithm.

| #  | LeetCode    | Problem                              | Pattern                        | Priority |
| -- | ----------- | ------------------------------------ | ------------------------------ | -------- |
| 8  | **LC 496**  | Next Greater Element I               | Next Greater                   | 🔥🔥🔥   |
| 9  | **LC 739**  | Daily Temperatures                   | Next Greater + Index Distance  | 🔥🔥🔥   |
| 10 | **LC 503**  | Next Greater Element II              | Circular Next Greater          | 🔥🔥     |
| 11 | **LC 1475** | Final Prices With a Special Discount | Next Smaller / Monotonic Stack | 🔥🔥     |

---

# 🧠 Why These Four Matter

They teach the progression:

```text
Next Greater
     ↓
Next Greater + indices
     ↓
Circular array
     ↓
Real-world pricing-style variation
```

The most important template:

```python
stack = []

for i in range(n):

    while stack and nums[i] > nums[stack[-1]]:
        j = stack.pop()
        answer[j] = nums[i]

    stack.append(i)
```

You should eventually be able to derive this instead of memorizing it.

---

# 🔵 PATTERN 4 — Previous Greater / Previous Smaller

| #  | Problem                         | Main Pattern                              | Priority |
| -- | ------------------------------- | ----------------------------------------- | -------- |
| 12 | **LC 901 — Online Stock Span**  | Previous Greater                          | 🔥🔥🔥   |
| 13 | **LC 739 — Daily Temperatures** | Closely related nearest-element reasoning | 🔥🔥     |

### Important note

There isn't a need to force four separate LeetCode questions just to mechanically cover:

* Previous Greater
* Previous Smaller
* Next Greater
* Next Smaller

Once you understand the monotonic-stack template, you should be able to **derive the variants**.

That's better interview preparation than solving four nearly identical questions.

---

# 🔴 PATTERN 5 — Advanced Monotonic Stack

These are the problems that prove whether you've actually mastered the pattern.

| #  | LeetCode  | Problem                        | Pattern               | Priority |
| -- | --------- | ------------------------------ | --------------------- | -------- |
| 14 | **LC 84** | Largest Rectangle in Histogram | Previous/Next Smaller | 🔥🔥🔥   |
| 15 | **LC 85** | Maximal Rectangle              | Histogram + Stack     | 🔥🔥     |
| 16 | **LC 42** | Trapping Rain Water            | Monotonic Stack       | 🔥🔥     |

---

# ⚠️ Priority Difference

Don't treat these equally.

### LC 84

**Must know.**

It teaches:

```text
Nearest Smaller Left
+
Nearest Smaller Right
+
Width
+
Area
```

This is one of the best tests of genuine monotonic-stack understanding.

---

### LC 85

Advanced extension of LC 84.

You don't need to spend huge amounts of time on it for an ML/MLOps interview.

Understand the relationship.

---

### LC 42

Excellent pattern exposure, but don't spend excessive time memorizing multiple solutions.

Understand the stack approach and recognize the pattern.

---

# 🟣 PATTERN 6 — Stack + Simulation

| #  | LeetCode   | Problem                  | Pattern                      | Priority |
| -- | ---------- | ------------------------ | ---------------------------- | -------- |
| 17 | **LC 735** | Asteroid Collision       | Stack + Collision Simulation | 🔥🔥🔥   |
| 18 | **LC 946** | Validate Stack Sequences | Stack Simulation             | 🔥🔥     |

These teach a different skill:

> **Simulate a process while maintaining unresolved state.**

---

# 🟤 PATTERN 7 — Stack + Greedy / Removal

| #  | LeetCode   | Problem                  | Pattern                  | Priority |
| -- | ---------- | ------------------------ | ------------------------ | -------- |
| 19 | **LC 402** | Remove K Digits          | Monotonic Stack + Greedy | 🔥🔥🔥   |
| 20 | **LC 316** | Remove Duplicate Letters | Monotonic Stack + Greedy | 🔥🔥     |

These are **advanced**.

Don't start here.

They combine:

```text
Stack
+
Greedy
+
Ordering
+
Frequency
```

They are useful once your basic monotonic stack is solid.

---

# 🧩 PATTERN 8 — Stack in Graph Traversal

This isn't a dedicated Stack problem, but it is important for your broader DSA syllabus.

### **LC 133 — Clone Graph**

Relevant concept:

```text
DFS
+
Explicit Stack
+
HashMap
```

And later:

### Trees / Graphs

You should understand:

```python
stack = [start]

while stack:
    node = stack.pop()
```

This connects Stack to your:

* Trees
* Graphs
* DFS

modules.

---

# 🎯 FINAL LOCKED STACK BANK

If I were training you specifically for **ML/MLOps/AI engineering interviews**, this is the set I'd actually make you finish:

## 🥇 Tier 1 — Non-Negotiable

```text
LC 20    Valid Parentheses
LC 1047  Remove All Adjacent Duplicates
LC 71    Simplify Path
LC 394   Decode String
LC 150   Evaluate Reverse Polish Notation
```

**5 problems**

---

## 🥈 Tier 2 — Monotonic Stack Core

```text
LC 496   Next Greater Element I
LC 739   Daily Temperatures
LC 503   Next Greater Element II
LC 901   Online Stock Span
LC 1475  Final Prices With a Special Discount
```

**5 problems**

---

## 🥉 Tier 3 — Advanced Stack

```text
LC 84    Largest Rectangle in Histogram
LC 42    Trapping Rain Water
LC 735   Asteroid Collision
LC 946   Validate Stack Sequences
```

**4 problems**

---

## 🔥 Tier 4 — Advanced Greedy + Stack

```text
LC 402   Remove K Digits
LC 316   Remove Duplicate Letters
LC 224   Basic Calculator
```

**3 problems**

---

# 🏆 TOTAL: 17 CORE PROBLEMS

That's the **actual bank I'd want you to master**, not blindly solve dozens.

---

# 📊 Pattern Coverage

| Pattern               | Problems |
| --------------------- | -------: |
| Basic Stack           |        3 |
| Matching              |        1 |
| Cancellation          |        2 |
| Parsing               |        2 |
| Expression            |        2 |
| Next Greater          |        3 |
| Previous Greater      |        1 |
| Next/Previous Smaller |        2 |
| Histogram             |        2 |
| Simulation            |        2 |
| Greedy + Stack        |        2 |
| DFS connection        |        1 |
| **Core unique bank**  |   **17** |

Some problems intentionally overlap patterns. **That's a feature, not a problem.** A strong interview question often combines two patterns.

---

# 🧠 YOUR STACK PROGRESSION

Don't solve randomly.

Follow:

```text
LC 20
 ↓
LC 1047
 ↓
LC 1544
 ↓
LC 71
 ↓
LC 394
 ↓
LC 150
 ↓
LC 496
 ↓
LC 739
 ↓
LC 503
 ↓
LC 901
 ↓
LC 1475
 ↓
LC 84
 ↓
LC 42
 ↓
LC 735
 ↓
LC 946
 ↓
LC 402
 ↓
LC 316
 ↓
LC 224
```

The progression is deliberate:

```text
Basic Stack
     ↓
Matching
     ↓
Cancellation
     ↓
Parsing
     ↓
Expression
     ↓
Monotonic Stack
     ↓
Nearest Greater/Smaller
     ↓
Advanced Monotonic Stack
     ↓
Greedy + Stack
```

---

# 🔥 THE 8 PROBLEMS I CARE ABOUT MOST FOR YOU

If time becomes limited, **do not try to finish everything equally**.

Master these:

1. **LC 20 — Valid Parentheses**
2. **LC 71 — Simplify Path**
3. **LC 394 — Decode String**
4. **LC 150 — Evaluate Reverse Polish Notation**
5. **LC 496 — Next Greater Element I**
6. **LC 739 — Daily Temperatures**
7. **LC 901 — Online Stock Span**
8. **LC 84 — Largest Rectangle in Histogram**

If you genuinely understand those eight, the majority of the Stack patterns relevant to your target interviews become much easier to recognize.

---

# 💎 SENIOR ENGINEER RULE FOR THIS BANK

**Don't measure Stack mastery by the number of problems solved.**

Measure it by whether you can see a new problem and answer:

```text
1. What does my stack represent?
2. What is the invariant?
3. When do I push?
4. When do I pop?
5. What does the top mean?
6. Why is the algorithm O(n)?
```

If you can answer those six questions **before writing code**, you've actually mastered Stack.

### Next in our structure → **CARD 4: Stack Mastery Pack**

That will be the final revision card covering the **interview decision tree, pattern cheat sheet, complexity traps, edge cases, senior-level explanations, ML/MLOps relevance, and a 5-minute revision sheet**.





# Layer 1

# LC 20 — Valid Parentheses

**Pattern:** Matching Stack
**Difficulty:** Easy
**Interview Importance:** 🔥🔥🔥 Very High

---

# 🔹 Block 1 — Senior Insights

## 1. Problem Simplification

You are given a string containing only:

```text
( ) { } [ ]
```

You must determine whether the brackets are **validly matched and properly nested**.

A string is valid when:

1. Every opening bracket has a corresponding closing bracket.
2. The closing bracket matches the correct opening bracket.
3. Brackets close in the correct order.

Examples:

```text
"()"       → True
"()[]{}"   → True
"([{}])"   → True
```

Invalid:

```text
"(]"        → False
"([)]"      → False
"((("       → False
"]"         → False
```

The important part is **order**.

For:

```text
"([{}])"
```

`{` must close before `[`, and `[` must close before `(`.

That means we need the **most recently opened but not yet closed bracket**.

That is exactly what a Stack is designed for.

---

## 2. Pattern Identification

### Pattern → Matching Stack

The recognition clue is:

> **"Match the current closing bracket with the most recent unresolved opening bracket."**

Translate it:

```text
Need the most recent unresolved opening bracket
                ↓
              STACK
```

This is the foundation rule from our locked Stack bank. 

### Senior engineer notices immediately

When you see nested structures such as:

```text
([{}])
```

think:

```text
Opening bracket
      ↓
remember it
      ↓
STACK
      ↓
closing bracket arrives
      ↓
compare with stack top
```

You do **not** need to search backward through the string.

The Stack already gives you the exact bracket you need.

---

## 3. Senior Engineer Mindset

Mental translation:

```text
Problem wording
      ↓
Brackets must match in reverse opening order
      ↓
Need most recent unresolved opening bracket
      ↓
Stack
      ↓
Push opening brackets
      ↓
For closing bracket → compare with stack top
      ↓
Match → pop
Mismatch → False
```

Think of opening brackets as **unfinished tasks**.

Example:

```text
"(["
```

Current unresolved work:

```text
[
(
```

`[` must be completed first.

Therefore the Stack gives:

```text
stack[-1] = '['
```

---

## 4. Brute Force / Naive Approach

A poor approach would repeatedly search backward through the string to find which opening bracket belongs to the current closing bracket.

That becomes complicated and can lead to unnecessary repeated work.

The Stack directly stores exactly what we need.

So instead of:

```text
"Where is the matching opening bracket?"
```

we maintain:

```text
"The matching candidate is already at stack[-1]."
```

---

## 5. Key Insight

The single most important observation:

> **Every closing bracket must match the most recently opened bracket that has not already been matched.**

Example:

```text
([{}])
```

Process:

```text
(     → push
[     → push
{     → push
}     → matches {
]     → matches [
)     → matches (
```

The Stack automatically enforces nesting order.

---

## 6. Algorithm

We process the string from left to right.

### Step 1 — Opening bracket

If we see:

```text
(   {   [
```

push it:

```python
stack.append(ch)
```

### Step 2 — Closing bracket

If we see:

```text
)   }   ]
```

first check whether the Stack is empty.

If it is empty:

```text
No opening bracket exists
        ↓
False
```

Otherwise inspect:

```python
stack[-1]
```

### Step 3 — Match

If the top matches the closing bracket:

```python
stack.pop()
```

Otherwise:

```text
False
```

### Step 4 — End

After processing the entire string:

```python
return not stack
```

Why?

Because any remaining opening brackets were never closed.

---

## 7. Invariant

### Core invariant:

> **The Stack contains exactly the opening brackets that have been seen but not yet matched.**

And:

> **The top of the Stack is always the most recent unresolved opening bracket.**

Example:

```text
Input processed: "(["
```

Then:

```text
stack = ['(', '[']
```

Therefore:

```text
stack[-1] = '['
```

If the next character is:

```text
']'
```

we compare it with `[`, pop it, and continue.

---

## 8. Complexity

Let:

```text
n = length of the string
```

We process every character exactly once.

For each character, we perform constant-time work:

* checking its type
* looking at `stack[-1]`
* pushing
* popping

Therefore:

```text
Time = O(n)
```

The Stack can contain at most every character if the input consists entirely of opening brackets.

Therefore:

```text
Space = O(n)
```

The important point:

> There is no nested traversal. Every character enters the Stack at most once and leaves it at most once.

---

## 9. Interview Tips / Traps

### Trap 1 — Empty Stack

This is dangerous:

```python
stack[-1]
```

when:

```python
stack = []
```

Always handle the empty case first.

---

### Trap 2 — Correct bracket but wrong order

```text
"([)]"
```

After:

```text
([
```

Stack:

```text
['(', '[']
```

Next:

```text
')'
```

But the top is:

```text
'['
```

`')'` cannot match `[`

Therefore:

```text
False
```

This is why a simple "count opening and closing brackets" solution is insufficient.

---

### Trap 3 — Same counts don't guarantee validity

Consider:

```text
"([)]"
```

Counts:

```text
( → 1
) → 1
[ → 1
] → 1
```

Everything has a matching count.

Yet the string is invalid.

**Order matters.**

---

### Trap 4 — Leftover opening brackets

```text
"((("
```

At the end:

```text
stack = ['(', '(', '(']
```

Therefore:

```text
not stack
```

is `False`.

---

### Trap 5 — Closing bracket first

```text
"]"
```

Stack is empty.

There is nothing that `]` can match.

Immediately:

```text
False
```

---

# 🔹 Block 2 — Efficient Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []

        pairs = {
            ')': '(',
            ']': '[',
            '}': '{'
        }

        for ch in s:
            if ch in pairs:
                if not stack or stack[-1] != pairs[ch]:
                    return False

                stack.pop()
            else:
                stack.append(ch)

        return not stack
```

### Time Complexity

```text
O(n)
```

We scan the string once. Every bracket is pushed at most once and popped at most once.

The dictionary lookups are average `O(1)`.

### Space Complexity

```text
O(n)
```

In the worst case, the input could contain only opening brackets, so the Stack could hold `n` elements.

### Interview Complexity Explanation

> "I process each bracket once. Opening brackets are pushed onto the stack, and every closing bracket checks the top and pops its matching opening bracket. Since each character is pushed and popped at most once, the total time is O(n). The stack can contain up to n characters, so the auxiliary space is O(n)."

---

# 🔹 Block 3 — Full Code + Dry Run

## Fully Runnable Python Program

```python
class Solution:
    def isValid(self, s: str) -> bool:
        stack = []

        pairs = {
            ')': '(',
            ']': '[',
            '}': '{'
        }

        for ch in s:
            if ch in pairs:
                if not stack or stack[-1] != pairs[ch]:
                    return False

                stack.pop()
            else:
                stack.append(ch)

        return not stack


# Example input
s = "([{}])"

# Create Solution object
solution = Solution()

# Call the function
result = solution.isValid(s)

# Print output
print("Input:", s)
print("Valid:", result)
```

### Output

```text
Input: ([{}])
Valid: True
```

---

# Step-by-Step Dry Run

Input:

```text
([{}])
```

Initial:

```text
stack = []
```

| Step | Character | Action            | Stack               | Result   |
| ---: | :-------: | ----------------- | ------------------- | -------- |
|    1 |    `(`    | Push              | `[`(`]`             | Continue |
|    2 |    `[`    | Push              | `[`(`, `[`]`        | Continue |
|    3 |    `{`    | Push              | `[`(`, `[`, `{` `]` | Continue |
|    4 |    `}`    | Matches `{` → Pop | `[`(`, `[`]`        | Continue |
|    5 |    `]`    | Matches `[` → Pop | `[`(`]`             | Continue |
|    6 |    `)`    | Matches `(` → Pop | `[]`                | Continue |

End:

```text
stack = []
```

Therefore:

```python
return not stack
```

becomes:

```python
return True
```

---

## Important Invalid Example

Input:

```text
([)]
```

Initial:

```text
stack = []
```

### Step 1

```text
(
```

Push:

```text
stack = ['(']
```

### Step 2

```text
[
```

Push:

```text
stack = ['(', '[']
```

### Step 3

```text
)
```

Expected matching opening bracket:

```text
(
```

But Stack top is:

```text
[
```

Therefore:

```text
[ ≠ (
```

Immediately:

```text
False
```

This demonstrates the most important property of the algorithm:

> **The current closing bracket must match the top, not just any opening bracket somewhere in the Stack.**

---

# 🔹 Block 4 — Interview Q&A

### Q1. Why is a Stack the correct data structure?

**Model Answer:**

> "Because brackets must close in reverse order of how they were opened. The most recently opened unmatched bracket must be checked first, which is exactly LIFO behavior."

---

### Q2. Why isn't counting brackets enough?

**Model Answer:**

> "Counting only verifies that the numbers of opening and closing brackets match. It doesn't verify ordering. For example, `([)]` has balanced counts but invalid nesting. The Stack preserves the required order."

---

### Q3. What does the Stack represent?

**Model Answer:**

> "The Stack contains all opening brackets that have been encountered but haven't been matched yet. Its top is always the most recent unresolved opening bracket."

---

### Q4. Why do we return `not stack` at the end?

**Model Answer:**

> "If the Stack isn't empty, there are opening brackets that never received matching closing brackets. Therefore the string is invalid. An empty Stack means every opening bracket was successfully matched."

---

### Q5. Can the algorithm terminate early?

**Model Answer:**

> "Yes. If a closing bracket appears when the Stack is empty, or if it doesn't match the Stack top, we can immediately return False because no later character can repair that invalid ordering."

---

### Q6. Why is the complexity O(n) despite using a loop and Stack operations?

**Model Answer:**

> "Each character is processed once. An opening bracket is pushed at most once, and a bracket can be popped at most once. Stack operations are constant time, so the total work is linear, O(n), rather than O(n²)."

---

# 🧠 Pattern Extraction

```text
Problem Clue
"Brackets must match in nested order"
        ↓
Pattern
Matching Stack
        ↓
Data Structure
Stack
        ↓
Invariant
Stack contains unmatched opening brackets
        ↓
Core Operation
Push opening
Match + pop closing
```

### Recognition trigger

```text
Most recent unresolved element
            ↓
          STACK
```

This is the foundational Stack recognition rule from the locked roadmap. 

---

# 🔥 Master Template

```python
stack = []

pairs = {
    ')': '(',
    ']': '[',
    '}': '{'
}

for ch in s:

    if ch in pairs:
        # Closing bracket
        if not stack or stack[-1] != pairs[ch]:
            return False

        stack.pop()

    else:
        # Opening bracket
        stack.append(ch)

return not stack
```

### The five questions you should be able to answer from memory

```text
1. What does the stack represent?
   → Unmatched opening brackets.

2. What does stack[-1] represent?
   → Most recent unresolved opening bracket.

3. When do I push?
   → When I see an opening bracket.

4. When do I pop?
   → When a closing bracket correctly matches the top.

5. When do I reject?
   → Empty stack or mismatched top.
```

---

# 📈 Progress Update

### Pattern 1 — Basic Stack / Matching

| Problem                                  | Status                     |
| ---------------------------------------- | -------------------------- |
| **LC 20 — Valid Parentheses**            | ✅ **MASTERED / COMPLETED** |
| LC 1047 — Remove All Adjacent Duplicates | ⏭️ Next                    |
| LC 1544 — Make The String Great          | 🔒                         |

The locked bank defines these three as the foundation layer and specifically identifies push/pop, peek, empty-stack handling, matching, cancellation, and stack invariants as the skills this layer must teach. 

---

# 🧠 Senior Pattern Recognition

When you encounter:

```text
nested structure
+
matching
+
most recent unresolved item
```

your brain should immediately go:

```text
             STACK
               ↓
       "What is unresolved?"
               ↓
      Push when it appears
               ↓
      Match against top
               ↓
        Match → pop
      Mismatch → reject
```

Don't memorize **LC 20 = parentheses**.

Memorize the reasoning:

> **Nested matching requires LIFO → Stack.**

---

# ⚡ One-Line Takeaway

> **When something must be matched with the most recently unresolved element, Stack is the natural data structure.**



# LC 1047 — Remove All Adjacent Duplicates In String

**Pattern:** Cancellation Stack
**Difficulty:** Easy
**Interview Importance:** 🔥🔥 High

---

# 🔹 Block 1 — Senior Insights

## 1. Problem Simplification

You are given a string.

Whenever **two identical characters become adjacent**, remove both.

Keep doing this until no adjacent duplicate pair remains.

Example:

```text
"abbaca"
```

Process:

```text
abbaca
 ↓
aaca        remove "bb"
 ↓
ca          remove "aa"
```

Answer:

```text
"ca"
```

The important word is **"become"**.

After removing one pair, two characters that were previously separated can become adjacent.

That's exactly why we need a Stack.

---

## 2. Pattern Identification

### Pattern → Cancellation Stack

This is the second problem in our Basic Stack foundation and is explicitly classified as **Cancellation Stack** in the locked bank. 

The recognition clue is:

> **"Does the current element cancel with the most recent unresolved element?"**

Translate:

```text
Current character
      ↓
Compare with most recent unresolved character
      ↓
      STACK
```

For:

```text
abbaca
```

we don't repeatedly scan the string looking for `"aa"` or `"bb"`.

Instead, the Stack represents the string **after all cancellations that have happened so far**.

---

## 3. Senior Engineer Mindset

Mental translation:

```text
Problem wording
      ↓
Adjacent equal elements must disappear
      ↓
Removal can create new adjacency
      ↓
Need to remember the most recent surviving element
      ↓
Stack
      ↓
Current == stack top?
      ↓
Yes → cancel / pop
No  → push
```

This is the deeper pattern.

You're not really solving a "string deletion" problem.

You're maintaining a **dynamic unresolved sequence**.

---

## 4. Brute Force / Naive Approach

A naive approach could repeatedly search for adjacent duplicates:

```text
abbaca
→ aaca
→ ca
```

But every deletion changes the string, potentially requiring repeated scanning and deletion.

That creates unnecessary work and complicates the implementation.

The Stack avoids physically deleting from the middle of a string.

Instead:

```text
push → character survives
pop  → character gets cancelled
```

---

## 5. Key Insight

The single most important observation:

> **The only character that can cancel the current character is the most recently surviving character.**

Example:

```text
abccba
```

Process:

```text
a → [a]
b → [a,b]
c → [a,b,c]
c → [a,b]       ← cancel c
b → [a]         ← cancel b
a → []          ← cancel a
```

Final result:

```text
""
```

The Stack naturally handles the chain reaction.

---

## 6. Algorithm

For every character `ch`:

### Case 1 — Stack is empty

Push it.

```python
stack.append(ch)
```

### Case 2 — Top equals current character

They form an adjacent duplicate in the **current surviving sequence**.

Cancel both:

```python
stack.pop()
```

We do **not** push `ch`, because both characters disappear.

### Case 3 — Top differs

The current character survives for now.

```python
stack.append(ch)
```

At the end:

```python
''.join(stack)
```

is the final string.

---

## 7. Invariant

This is the most important part.

> **After processing each character, the Stack contains exactly the remaining string after repeatedly cancelling all adjacent duplicate pairs within the processed prefix.**

In simpler words:

```text
Stack = current surviving string
```

Example after processing:

```text
"abb"
```

The Stack is:

```text
['a']
```

because:

```text
abb
 ↓
a
```

So when the next character arrives, comparing against `stack[-1]` is equivalent to checking the character immediately to its left in the **current reduced string**.

That's the key reason the algorithm works.

---

## 8. Complexity

Let:

```text
n = length of s
```

We process each character once.

Each character can:

* be pushed onto the Stack once
* be popped at most once

Therefore the total number of Stack operations is at most proportional to `2n`.

So:

```text
Time = O(n)
```

The Stack can contain up to `n` characters in the worst case, for example:

```text
"abcdef"
```

Therefore:

```text
Space = O(n)
```

---

## 9. Interview Tips / Traps

### Trap 1 — Don't compare only original neighbors

Consider:

```text
"abbaca"
```

After removing `bb`:

```text
"aaca"
```

Now `aa` becomes adjacent.

A solution that only checks the original neighboring characters will miss this.

The Stack automatically handles it.

---

### Trap 2 — Don't push after cancellation

Wrong:

```python
if stack[-1] == ch:
    stack.pop()
    stack.append(ch)  # WRONG
```

If they cancel, **both disappear**.

Correct:

```python
if stack and stack[-1] == ch:
    stack.pop()
else:
    stack.append(ch)
```

---

### Trap 3 — Empty Stack

This is unsafe:

```python
if stack[-1] == ch:
```

because the Stack may be empty.

Use:

```python
if stack and stack[-1] == ch:
```

---

### Trap 4 — Understand "adjacent"

The characters don't need to have been adjacent in the **original** string.

They need to become adjacent after previous cancellations.

That distinction is the entire reason this Stack solution works.

---

# 🔹 Block 2 — Efficient Code

```python
class Solution:
    def removeDuplicates(self, s: str) -> str:
        stack = []

        for ch in s:
            if stack and stack[-1] == ch:
                stack.pop()
            else:
                stack.append(ch)

        return ''.join(stack)
```

### Time Complexity

```text
O(n)
```

Every character is pushed at most once and popped at most once.

So even though there is a `pop()` inside the loop, the total number of operations remains linear.

### Space Complexity

```text
O(n)
```

In the worst case, no characters cancel and the Stack stores all `n` characters.

### Interview Complexity Explanation

> "I process the string once and maintain a stack representing the current reduced string. Each character is pushed at most once and popped at most once, so the total time is O(n). In the worst case no characters cancel, so the stack uses O(n) space."

---

# 🔹 Block 3 — Full Code + Dry Run

## Fully Runnable Python Program

```python
class Solution:
    def removeDuplicates(self, s: str) -> str:
        stack = []

        for ch in s:
            if stack and stack[-1] == ch:
                stack.pop()
            else:
                stack.append(ch)

        return ''.join(stack)


# Example input
s = "abbaca"

# Create Solution object
solution = Solution()

# Call the method
result = solution.removeDuplicates(s)

# Print output
print("Input:", s)
print("Output:", result)
```

### Output

```text
Input: abbaca
Output: ca
```

---

# Step-by-Step Dry Run

Input:

```text
abbaca
```

Initially:

```text
stack = []
```

### Step 1 — `a`

Stack is empty.

Push:

```text
[a]
```

---

### Step 2 — `b`

Top:

```text
a
```

Current:

```text
b
```

They are different.

Push:

```text
[a, b]
```

---

### Step 3 — `b`

Top:

```text
b
```

Current:

```text
b
```

They are equal.

Cancel them:

```text
[a, b]
     ↑
    pop
```

Stack becomes:

```text
[a]
```

The two `b`s disappear.

---

### Step 4 — `a`

Top:

```text
a
```

Current:

```text
a
```

They are equal.

Cancel:

```text
[a]
 ↑
pop
```

Stack becomes:

```text
[]
```

This is the important chain reaction.

The two `a`s weren't adjacent in the **original** string:

```text
a b b a
```

But after removing `bb`:

```text
a a
```

they became adjacent.

---

### Step 5 — `c`

Stack is empty.

Push:

```text
[c]
```

---

### Step 6 — `a`

Top:

```text
c
```

Current:

```text
a
```

Different.

Push:

```text
[c, a]
```

---

### Final

```text
stack = ['c', 'a']
```

Join:

```python
''.join(stack)
```

Result:

```text
"ca"
```

---

## Dry-Run Table

| Step | Current | Stack Before | Action         | Stack After |
| ---: | :-----: | ------------ | -------------- | ----------- |
|    1 |   `a`   | `[]`         | Push           | `[a]`       |
|    2 |   `b`   | `[a]`        | Push           | `[a,b]`     |
|    3 |   `b`   | `[a,b]`      | `b == b` → Pop | `[a]`       |
|    4 |   `a`   | `[a]`        | `a == a` → Pop | `[]`        |
|    5 |   `c`   | `[]`         | Push           | `[c]`       |
|    6 |   `a`   | `[c]`        | Push           | `[c,a]`     |

Final:

```text
[c, a]
 ↓
"ca"
```

---

## Chain-Reaction Example

This one is worth remembering:

```text
"azxxzy"
```

Process:

```text
a
az
azx
az
a
ay
```

Final:

```text
"ay"
```

The Stack handles all cancellations automatically.

---

# 🔹 Block 4 — Interview Q&A

### Q1. Why is a Stack appropriate for this problem?

**Model Answer:**

> "After removing a duplicate pair, the only character that can become adjacent to the current character is the most recently surviving character. A Stack gives direct access to that character through its top, so it naturally models the cancellation process."

---

### Q2. What does the Stack represent?

**Model Answer:**

> "At every point, the Stack represents the reduced version of the portion of the string processed so far. No adjacent duplicate pairs remain inside the Stack."

---

### Q3. Why is the solution O(n) even though we repeatedly pop?

**Model Answer:**

> "Each character can be pushed onto the stack at most once and popped at most once. Therefore the total number of stack operations is linear in the input size, giving O(n) time."

This is an important complexity trap.

A `while` loop or repeated `pop()` does **not automatically mean O(n²)**. The operation must be analyzed across the entire execution.

---

### Q4. Why can't we simply remove `s[i]` and `s[i+1]` whenever they match?

**Model Answer:**

> "Removing characters from the middle of a Python string is expensive and can require repeated reconstruction or shifting. More importantly, deletions can create new adjacent duplicates. The Stack handles both the dynamic adjacency and the removal efficiently."

---

### Q5. What happens if the Stack is empty when processing a character?

**Model Answer:**

> "There is no previous surviving character to cancel with, so the current character must be pushed onto the Stack."

---

### Q6. What is the deeper pattern behind LC 1047?

**Model Answer:**

> "The deeper pattern is cancellation using the most recent unresolved element. If the current element conflicts or cancels with the Stack top, I remove the top; otherwise I preserve the current element by pushing it. This generalizes to several Stack-based elimination problems."

---

# 🧠 Pattern Extraction

```text
Problem Clue
"Adjacent duplicates should disappear"
        ↓
Removal can create new adjacency
        ↓
Need the most recent surviving element
        ↓
Pattern
Cancellation Stack
        ↓
Data Structure
Stack
        ↓
Invariant
Stack = current reduced sequence
        ↓
Core Operation
Same as top → pop
Different → push
```

The locked bank explicitly identifies LC 1047 as **Cancellation Stack** and places it in the Basic Stack / Matching foundation layer. 

---

# 🔥 Master Template

```python
stack = []

for ch in s:
    if stack and stack[-1] == ch:
        stack.pop()
    else:
        stack.append(ch)

return ''.join(stack)
```

### Mental template

```text
Current element
      ↓
Is Stack empty?
      ↓
    YES → PUSH
      ↓
    NO
      ↓
Does current == stack top?
      ↓
   YES       NO
    ↓         ↓
  POP       PUSH
```

The critical thing to remember:

> **The Stack is not merely storing characters. It is storing the current surviving state of the string.**

---

# 📈 Progress Update

## Pattern 1 — Basic Stack / Matching

| Problem                                      | Status          |
| -------------------------------------------- | --------------- |
| **LC 20 — Valid Parentheses**                | ✅ Completed     |
| **LC 1047 — Remove All Adjacent Duplicates** | ✅ **Completed** |
| LC 1544 — Make The String Great              | ⏭️ **Next**     |

The locked bank defines these three as the foundation problems for Stack mastery. 

---

# 🧠 Senior Pattern Recognition

For a new problem, don't ask:

> "Have I seen this exact problem before?"

Ask:

```text
Does the current element interact with
the most recent unresolved/surviving element?
                    ↓
                   YES
                    ↓
                  STACK
```

For LC 1047:

```text
Adjacent cancellation
        ↓
Dynamic adjacency after deletion
        ↓
Most recent survivor matters
        ↓
Stack
        ↓
Equal → cancel
Different → preserve
```

---

# ⚡ One-Line Takeaway

> **When removing the current element depends on the most recent surviving element, use a Stack to make cancellation O(1) per character.**


# LC 1544 — Make The String Great

**Pattern:** Cancellation + Character Matching
**Difficulty:** Easy
**Interview Importance:** 🔥🔥 High

---

# 🔹 Block 1 — Senior Insights

## 1. Problem Simplification

You are given a string containing English letters.

The string is considered **good** when there are no two adjacent characters where:

* one is lowercase
* the other is the uppercase version of the same letter.

Examples of bad adjacent pairs:

```text
"aA"
"Aa"
"bB"
"Bb"
```

Whenever such a pair appears, remove both characters.

Continue doing this until no such pair remains.

### Example

```text
"leEeetcode"
```

Look at:

```text
"eE"
```

They cancel:

```text
"leetcode"
```

Now there are no more bad adjacent pairs.

Answer:

```text
"leetcode"
```

This problem is explicitly classified in our locked Stack bank as:

> **Cancellation + Character Matching**. 

---

## 2. Pattern Identification

### Pattern → Cancellation Stack

This is essentially **LC 1047 with a smarter cancellation condition**.

LC 1047:

```text
same character
    ↓
cancel
```

LC 1544:

```text
same letter
+
opposite case
    ↓
cancel
```

The underlying Stack pattern hasn't changed.

The key clue is:

> **The current character needs to interact with the most recently surviving character.**

Therefore:

```text
Current character
      ↓
Compare with stack[-1]
      ↓
Do they cancel?
   ↙        ↘
 YES        NO
  ↓          ↓
 POP        PUSH
```

---

## 3. Senior Engineer Mindset

Mental translation:

```text
Problem wording
      ↓
Adjacent opposite-case versions cancel
      ↓
Cancellation can create new adjacency
      ↓
Need the most recent surviving character
      ↓
STACK
      ↓
Compare current character with stack top
      ↓
Cancel → pop
Keep   → push
```

The important upgrade from LC 1047 is the **cancellation predicate**.

Instead of:

```python
stack[-1] == ch
```

we need:

```text
same letter?
+
different case?
```

---

## 4. Brute Force / Naive Approach

A naive solution could repeatedly scan the string for bad adjacent pairs:

```text
leEeetcode
  ↑↑
 eE → remove
```

Then restart scanning because the deletion might create another bad pair.

This is unnecessarily complicated.

The Stack gives us the current reduced string automatically.

Instead of physically deleting from the middle:

```text
push → character survives
pop  → character gets cancelled
```

---

## 5. Key Insight

The key observation is:

> **Two characters cancel exactly when they represent the same letter but have opposite cases.**

In Python, a clean way to test this is:

```python
ch.lower() == top.lower()
```

and:

```python
ch != top
```

Together:

```python
ch.lower() == top.lower() and ch != top
```

Example:

```text
'a' and 'A'
```

```text
'a'.lower() == 'A'.lower()
True
```

but:

```text
'a' != 'A'
True
```

Therefore they cancel.

But:

```text
'a' and 'a'
```

have the same letter **and** same case:

```text
'a' != 'a'
False
```

so they don't cancel.

---

## 6. Algorithm

For every character `ch`:

### Step 1

If the Stack is empty:

```python
stack.append(ch)
```

### Step 2

Otherwise inspect:

```python
top = stack[-1]
```

### Step 3

Check whether `top` and `ch` are opposite-case versions of the same letter.

If yes:

```python
stack.pop()
```

Do **not** push `ch`.

Both characters disappear.

### Step 4

Otherwise:

```python
stack.append(ch)
```

### Step 5

At the end:

```python
''.join(stack)
```

is the final good string.

---

## 7. Invariant

This is the critical invariant:

> **After processing every character, the Stack contains the fully reduced version of the processed prefix, with no cancellable adjacent pair remaining.**

In simpler terms:

```text
Stack = current surviving string
```

Example:

```text
processed: "leEe"
```

Process:

```text
l → [l]
e → [l,e]
E → [l]       ← e/E cancel
e → [l,e]
```

So the Stack always represents the current state after all possible cancellations in the processed portion.

---

## 8. Complexity

Let:

```text
n = length of s
```

We process every character once.

Each character can:

* be pushed at most once
* be popped at most once

Therefore:

```text
Time = O(n)
```

The Stack can contain all `n` characters in the worst case:

```text
"abcdef..."
```

So:

```text
Space = O(n)
```

The `.lower()` operations involve a single character, so they are constant time with respect to `n`.

---

## 9. Interview Tips / Traps

### Trap 1 — Don't use only `lower()`

This is wrong:

```python
if stack[-1].lower() == ch.lower():
```

because:

```text
"a" and "a"
```

would also be considered a match.

They should **not** cancel.

You need opposite cases too.

---

### Trap 2 — Same case does not cancel

```text
"aa"
```

remains:

```text
"aa"
```

Similarly:

```text
"AA"
```

remains:

```text
"AA"
```

Only:

```text
"aA"
"Aa"
```

cancel.

---

### Trap 3 — Cancellation can cascade

Consider:

```text
"abBAc"
```

Process:

```text
a
ab
a       ← bB cancel
aA      ← A arrives
""      ← aA cancel
c
```

Final:

```text
"c"
```

A local cancellation can expose another cancellable pair.

That's exactly why Stack is useful.

---

### Trap 4 — Don't confuse this with LC 1047

The Stack structure is identical, but the cancellation rule differs:

```text
LC 1047
top == current

LC 1544
same letter + opposite case
```

Recognizing that distinction is part of pattern mastery.

---

# 🔹 Block 2 — Efficient Code

```python
class Solution:
    def makeGood(self, s: str) -> str:
        stack = []

        for ch in s:
            if stack:
                top = stack[-1]

                if top.lower() == ch.lower() and top != ch:
                    stack.pop()
                    continue

            stack.append(ch)

        return ''.join(stack)
```

### Time Complexity

```text
O(n)
```

Each character is processed once, and each character can be pushed and popped at most once.

### Space Complexity

```text
O(n)
```

The Stack may contain all characters if no cancellations occur.

### Interview Complexity Explanation

> "I scan the string once and maintain a stack containing the current reduced string. For each character I compare it with the most recent surviving character. Each character is pushed at most once and popped at most once, so the total time is O(n), with O(n) worst-case auxiliary space."

---

# 🔹 Block 3 — Full Code + Dry Run

## Fully Runnable Python Program

```python
class Solution:
    def makeGood(self, s: str) -> str:
        stack = []

        for ch in s:
            if stack:
                top = stack[-1]

                # Same letter but opposite case
                if top.lower() == ch.lower() and top != ch:
                    stack.pop()
                    continue

            stack.append(ch)

        return ''.join(stack)


# Example input
s = "leEeetcode"

# Create Solution object
solution = Solution()

# Call the method
result = solution.makeGood(s)

# Print output
print("Input:", s)
print("Output:", result)
```

### Output

```text
Input: leEeetcode
Output: leetcode
```

---

# Step-by-Step Dry Run

Input:

```text
"leEeetcode"
```

Initial:

```text
stack = []
```

### Step 1 — `l`

Stack empty.

Push:

```text
[l]
```

---

### Step 2 — `e`

Compare:

```text
top = l
current = e
```

Different letters.

Push:

```text
[l, e]
```

---

### Step 3 — `E`

Compare:

```text
top = e
current = E
```

Check:

```text
'e'.lower() == 'E'.lower()
True
```

and:

```text
'e' != 'E'
True
```

Therefore they cancel.

Pop:

```text
[l]
```

Do not push `E`.

---

### Step 4 — `e`

Stack:

```text
[l]
```

Top:

```text
l
```

Current:

```text
e
```

Different letters.

Push:

```text
[l, e]
```

---

### Step 5 — `e`

Top:

```text
e
```

Current:

```text
e
```

Same letter, but:

```text
e == e
```

So they are **not opposite cases**.

Push:

```text
[l, e, e]
```

---

### Remaining characters

The remaining characters don't create cancellable pairs.

Final:

```text
[l, e, e, t, c, o, d, e]
```

Therefore:

```text
"leetcode"
```

---

## More Important Dry Run — Cascading Cancellation

Input:

```text
"abBAc"
```

| Step | Current | Stack Before | Decision                | Stack After |
| ---: | :-----: | ------------ | ----------------------- | ----------- |
|    1 |   `a`   | `[]`         | Push                    | `[a]`       |
|    2 |   `b`   | `[a]`        | Different letter → Push | `[a,b]`     |
|    3 |   `B`   | `[a,b]`      | `b/B` cancel            | `[a]`       |
|    4 |   `A`   | `[a]`        | `a/A` cancel            | `[]`        |
|    5 |   `c`   | `[]`         | Push                    | `[c]`       |

Final:

```text
"c"
```

Notice what happened:

```text
abBAc
  ↓
aAc
 ↓
c
```

The first cancellation exposed another cancellation.

This is the exact behavior the Stack handles naturally.

---

# 🔹 Block 4 — Interview Q&A

### Q1. How is LC 1544 different from LC 1047?

**Model Answer:**

> "Both use the same cancellation-stack structure, but the cancellation condition differs. LC 1047 removes identical adjacent characters, while LC 1544 removes adjacent characters representing the same letter in opposite cases."

---

### Q2. Why can't we simply compare `lower()` values?

**Model Answer:**

> "Because two characters with the same case would also have equal lowercase values. For example, `a` and `a` must not cancel. So I need both the same letter condition and the opposite-case condition."

---

### Q3. What does the Stack represent?

**Model Answer:**

> "It represents the reduced version of the processed prefix. After each iteration, no cancellable adjacent pair remains in the Stack."

---

### Q4. Why is the algorithm O(n)?

**Model Answer:**

> "Each input character is pushed at most once and popped at most once. Although a character can trigger a cancellation, the total number of push and pop operations is bounded by a constant multiple of n, so the overall complexity is O(n)."

---

### Q5. Can a cancellation trigger another cancellation?

**Model Answer:**

> "Yes. Removing a pair can make the character before that pair adjacent to the character after it. The Stack handles this automatically because after a pop, the new stack top becomes the next surviving character."

---

### Q6. What is the reusable pattern here?

**Model Answer:**

> "The reusable pattern is cancellation based on the most recent surviving element. I maintain that state in a Stack. If the current element cancels with the top, I pop; otherwise I push. The specific cancellation predicate can change between problems."

---

# 🧠 Pattern Extraction

```text
Problem Clue
Adjacent characters can cancel
        ↓
Cancellation may create new adjacency
        ↓
Need most recent surviving character
        ↓
Pattern
Cancellation Stack
        ↓
Data Structure
Stack
        ↓
Invariant
Stack = current reduced string
        ↓
Core Operation
Cancel → pop
Survive → push
```

### Compare the three foundation problems

```text
LC 20
Matching
    ↓
Closing bracket matches stack top
    ↓
MATCH → POP


LC 1047
Cancellation
    ↓
Current == stack top
    ↓
EQUAL → POP


LC 1544
Cancellation + Matching
    ↓
Same letter + opposite case
    ↓
CANCEL → POP
```

This is the progression deliberately built into our locked Stack bank. 

---

# 🔥 Master Template

```python
stack = []

for ch in s:

    if stack and should_cancel(stack[-1], ch):
        stack.pop()
    else:
        stack.append(ch)

return ''.join(stack)
```

For LC 1544:

```python
def should_cancel(top, ch):
    return top.lower() == ch.lower() and top != ch
```

The important thing is that **the Stack template stays the same**.

Only this changes:

```text
should_cancel(...)
```

That is exactly how you should think about reusable DSA patterns.

---

# 📈 Progress Update

## Pattern 1 — Basic Stack / Matching

| Problem                                      | Status          |
| -------------------------------------------- | --------------- |
| **LC 20 — Valid Parentheses**                | ✅ Completed     |
| **LC 1047 — Remove All Adjacent Duplicates** | ✅ Completed     |
| **LC 1544 — Make The String Great**          | ✅ **Completed** |

### Pattern 1 is now complete. 🔒

You have covered:

```text
Matching
   ↓
Cancellation
   ↓
Cancellation + Character Matching
```

The locked bank defines these three as the **Foundation — MUST MASTER** layer. 

---

# 🧠 Senior Pattern Recognition

You should now be able to see:

```text
"Most recent unresolved/surviving element"
                  ↓
                STACK
```

Then determine what causes the Stack top to disappear:

```text
LC 20
top matches closing bracket
        ↓
      POP


LC 1047
top == current
        ↓
      POP


LC 1544
same letter + opposite case
        ↓
      POP
```

**The algorithmic structure didn't change.
Only the cancellation/matching rule changed.**

That's the actual mastery point of Pattern 1.

---

# ⚡ One-Line Takeaway

> **Master the Stack template, not the problem: preserve with `push`, cancel with `pop`, and let the problem define what “cancel” means.**



# Pattern 2

LC 71 — Simplify Path

Pattern: Stack + Parsing
Difficulty: Medium
Interview Importance: 🔥🔥🔥 Very High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given an absolute Unix-style file path.

You need to convert it into its canonical simplified path.

There are three important tokens:

"."   → current directory → ignore it

".."  → parent directory → go back one directory

"name" → enter that directory → keep it

Multiple / characters are treated as one separator.

Example

"/home//foo/"

becomes:

"/home/foo"

Another:

"/a/./b/../../c/"

Process:

/a
/a/b
/a/./b       "." ignored
/a/b/..
/a
/a/../..     go up, but root cannot go above /
/c

Final:

"/c"


---

2. Pattern Identification

Why is this a Stack problem?

The key operation is:

".." = go back to the most recently entered directory

That means:

Most recent directory
        ↓
      STACK
        ↓
".." → POP

Recognition clue:

> A token can undo the most recent previous valid token.



That's classic Stack behavior.


---

What a senior engineer notices

Don't think:

> "I need to manipulate a complicated string."



Think:

Path
 ↓
Tokens separated by "/"
 ↓
Parse tokens
 ↓
Normal directory → PUSH
"." → IGNORE
".." → POP
 ↓
Join remaining directories

This is parsing + state management, not merely string manipulation.


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
Unix path normalization
      ↓
"." means nothing
".." means undo previous directory
      ↓
Need most recent directory
      ↓
STACK
      ↓
directory → push
"."       → ignore
".."      → pop

This is the important upgrade from our previous Stack problems.

In LC 20:

Stack → matching

In LC 1047 / 1544:

Stack → cancellation

Here:

Stack → previous-state management


---

4. Brute Force / Naive Approach

A naive approach could repeatedly modify the path string whenever .. appears.

For example:

/a/b/c/../..

You would need to repeatedly locate the previous directory and remove it.

That's unnecessary.

Instead, parse the path once and maintain the valid directories in a Stack.


---

5. Key Insight

The entire problem reduces to this:

Normal directory
      ↓
    PUSH

"."
      ↓
   IGNORE

".."
      ↓
If stack isn't empty → POP
Otherwise → stay at root

That's it.

The Stack represents:

> The current canonical path.




---

6. Algorithm

Step 1 — Split the path

parts = path.split("/")

For:

"/a/./b/../../c/"

we get roughly:

["", "a", ".", "b", "..", "..", "c", ""]

Empty strings come from repeated/leading/trailing /.

We don't need them.


---

Step 2 — Process each token

Normal directory

"a"
"home"
"projects"

Push:

stack.append(part)

"."

Ignore:

continue

".."

If Stack isn't empty:

stack.pop()

If Stack is empty:

Already at /
Cannot go above root

So do nothing.


---

Step 3 — Reconstruct the path

If:

stack = ["home", "foo"]

we need:

/home/foo

Therefore:

return "/" + "/".join(stack)


---

7. Invariant

Critical invariant:

> After processing each path component, the Stack contains exactly the directories in the canonical path represented by the processed prefix.



Example:

Input:
"/a/b/../c"

After a:

stack = ["a"]

After b:

stack = ["a", "b"]

After ..:

stack = ["a"]

After c:

stack = ["a", "c"]

So:

stack = current canonical path

This invariant makes the entire solution easy to reason about.


---

8. Complexity

Let:

n = length of the path

Time: O(n)

split("/") scans the path once.

Then we process every resulting token once.

Each directory is:

pushed at most once

popped at most once


Therefore the total processing remains linear.

Time = O(n)

Space: O(n)

In the worst case:

/a/b/c/d/e/f/...

none of the directories are removed.

The Stack can therefore contain O(n) characters/tokens.

Space = O(n)


---

9. Interview Tips / Traps

Trap 1 — "." does NOT mean push

Wrong:

stack.append(".")

"." simply means:

> Stay where you are.



So ignore it.


---

Trap 2 — ".." at root does nothing

Example:

"/../../.."

You cannot move above /.

Therefore:

"/"

not an error.


---

Trap 3 — Multiple slashes

"/home//foo///bar/"

must become:

"/home/foo/bar"

Empty tokens should be ignored.


---

Trap 4 — "..." is NOT ".."

This is a normal directory name:

"/.../"

Therefore:

"/..."

Only the exact token:

".."

means parent directory.


---

Trap 5 — Don't confuse "." with ".."

"."   → current directory → ignore
".."  → parent directory → pop

This distinction is fundamental.


---

🔹 Block 2 — Efficient Code

class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []

        for part in path.split("/"):
            if part == "" or part == ".":
                continue

            if part == "..":
                if stack:
                    stack.pop()
            else:
                stack.append(part)

        return "/" + "/".join(stack)

Time Complexity

O(n)

The path is split and then its components are processed once. Each directory is pushed and popped at most once.

Space Complexity

O(n)

The Stack may store all directory components in the worst case.

Interview Complexity Explanation

> "I parse the path into components once and use a stack to maintain the canonical directory state. Normal directories are pushed, . is ignored, and .. pops the most recent directory when possible. Since every component is processed once and each directory is pushed and popped at most once, the time complexity is O(n), with O(n) auxiliary space."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def simplifyPath(self, path: str) -> str:
        stack = []

        for part in path.split("/"):
            if part == "" or part == ".":
                continue

            if part == "..":
                if stack:
                    stack.pop()
            else:
                stack.append(part)

        return "/" + "/".join(stack)


# Example input
path = "/a/./b/../../c/"

# Create Solution object
solution = Solution()

# Call the method
result = solution.simplifyPath(path)

# Print output
print("Input:", path)
print("Output:", result)

Output

Input: /a/./b/../../c/
Output: /c


---

Step-by-Step Dry Run

Input:

/a/./b/../../c/

After splitting:

[
    "",
    "a",
    ".",
    "b",
    "..",
    "..",
    "c",
    ""
]

Initial:

stack = []

Step 1 — ""

Empty component.

Ignore:

stack = []


---

Step 2 — "a"

Normal directory.

Push:

stack = ["a"]

Current path:

/a


---

Step 3 — "."

Current directory.

Ignore:

stack = ["a"]

Current path remains:

/a


---

Step 4 — "b"

Normal directory.

Push:

stack = ["a", "b"]

Current path:

/a/b


---

Step 5 — ".."

Go to parent directory.

Pop:

stack = ["a"]

Current path:

/a


---

Step 6 — ".."

Again go to parent.

Pop:

stack = []

Current path:

/


---

Step 7 — "c"

Normal directory.

Push:

stack = ["c"]

Current path:

/c


---

Step 8 — ""

Trailing slash.

Ignore.

Final:

stack = ["c"]

Reconstruct:

"/" + "/".join(["c"])

Result:

"/c"


---

Dry-Run Table

Step	Token	Action	Stack After

1	""	Ignore	[]
2	a	Push	[a]
3	.	Ignore	[a]
4	b	Push	[a,b]
5	..	Pop b	[a]
6	..	Pop a	[]
7	c	Push	[c]
8	""	Ignore	[c]


Final:

["c"]
   ↓
"/c"


---

Important Edge Cases

Case 1

path = "/"

Tokens:

["", ""]

Nothing gets pushed.

Result:

"/"


---

Case 2

path = "/../"

.. appears while Stack is empty.

Nothing happens.

Result:

"/"


---

Case 3

path = "/home//foo/"

Result:

"/home/foo"


---

Case 4

path = "/a/../../b"

Process:

/a
/a/..
/
.. → still /
b → /b

Result:

"/b"


---

🔹 Block 4 — Interview Q&A

Q1. Why is a Stack appropriate for path simplification?

Model Answer:

> "A .. component means going back to the most recently entered directory. That's LIFO behavior, so a stack naturally represents the current directory hierarchy."




---

Q2. What does the Stack represent?

Model Answer:

> "The Stack represents the directories in the canonical path after processing the components seen so far."




---

Q3. What do "." and ".." mean?

Model Answer:

> ". represents the current directory, so I ignore it. .. represents the parent directory, so I pop the most recent directory if one exists."




---

Q4. What happens when ".." appears at the root?

Model Answer:

> "Nothing. The path is absolute, so we cannot move above /. If the stack is empty, I simply ignore the ..."




---

Q5. Why doesn't "...“ behave like ".."?

Model Answer:

> "Only the exact token .. has parent-directory semantics. ... is just a normal directory name and should be pushed onto the stack."




---

Q6. Could this be solved without a Stack?

Model Answer:

> "Conceptually, yes, because Python's list provides the stack behavior. But we still need LIFO state management. A list used with append and pop is the natural implementation."




---

🧠 Pattern Extraction

Problem Clue
".." means undo the most recent directory
        ↓
Pattern
Stack + Parsing
        ↓
Data Structure
Stack
        ↓
Invariant
Stack = current canonical directory path
        ↓
Core Operations
directory → PUSH
"."       → IGNORE
".."      → POP


---

🔥 Master Template

This is the reusable parsing-stack template:

stack = []

for token in tokens:

    if token_means_nothing:
        continue

    elif token_means_undo:
        if stack:
            stack.pop()

    else:
        stack.append(token)

For path parsing:

normal token → PUSH
"."          → IGNORE
".."         → POP

The deeper pattern

Current state
     ↓
New token changes state
     ↓
Some token means "go back"
     ↓
Need previous state
     ↓
STACK

That is more important than memorizing LC 71.


---

📈 Progress Update

Pattern 2 — Parsing / Nested Structures

Problem	Status

LC 71 — Simplify Path	✅ Completed
LC 394 — Decode String	✅ Previously completed
LC 150 — Evaluate Reverse Polish Notation	⏭️ Next
LC 224 — Basic Calculator	🔒


Current Stack progression

Pattern 1 — Matching / Cancellation
        ↓
LC 20     → Matching Stack          ✅
LC 1047   → Cancellation Stack      ✅
LC 1544   → Character Cancellation  ✅

Pattern 2 — Parsing / Nested Structures
        ↓
LC 71     → Path Parsing            ✅
LC 394    → Nested Parsing          ✅
LC 150    → Expression Stack        ⏭️
LC 224    → Expression + Stack      🔒


---

🧠 Senior Pattern Recognition

Don't memorize:

> LC 71 = Unix path problem.



Recognize:

Input contains structured tokens
        ↓
Some tokens create state
        ↓
Some tokens undo previous state
        ↓
Need most recent valid state
        ↓
STACK

The Stack has now evolved:

LC 20
Stack = unmatched brackets

LC 1047
Stack = surviving characters

LC 1544
Stack = surviving characters

LC 71
Stack = current canonical path

Same data structure. Different state interpretation.


---

⚡ One-Line Takeaway

> When parsing contains an operation that means "undo the most recent valid state," think Stack + Parsing.

LC 394 — Decode String

Pattern: Nested Parsing + Stack
Difficulty: Medium
Interview Importance: 🔥🔥🔥 Very High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given an encoded string using this format:

k[encoded_string]

Meaning:

> Repeat encoded_string exactly k times.



Examples:

3[a]       → aaa
3[a2[c]]   → accaccacc
2[abc]3[cd]ef → abcabccdcdcdef

The difficult part is nesting.

For:

3[a2[c]]

you cannot decode the outer 3[...] until you understand the inner:

2[c]

So we have nested states.

That is the exact reason a Stack is appropriate.


---

2. Pattern Identification

Pattern → Nested Parsing + Stack

The recognition clue is:

> When entering a nested structure, save the current state; when leaving it, restore that state and combine the result.



For:

3[a2[c]]

we have:

outer state
    ↓
3[
    ↓
save previous state
    ↓
inner state
    ↓
2[
    ↓
save previous state
    ↓
decode c
    ↓
restore inner state
    ↓
restore outer state

So:

Nested structure
       ↓
Need previous state
       ↓
STACK


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
k[...]
      ↓
Nested structure
      ↓
Need to remember state before "["
      ↓
Stack
      ↓
"[" → save state
"]" → restore state

There are two pieces of state we must save:

1. Previous decoded string
2. Repeat count

Therefore the Stack stores something like:

(previous_string, repeat_count)

This is the major conceptual difference from LC 71.

LC 71

".." → undo previous directory

LC 394

"[" → save previous decoding context
"]" → restore previous decoding context

Same Stack principle:

> Preserve previous state until the nested operation finishes.




---

4. Brute Force / Naive Approach

A naive approach would repeatedly find the innermost:

number[...]

decode it, replace it, then search again.

For:

3[a2[c]]

you might do:

3[a2[c]]
     ↓
3[acc]
     ↓
accaccacc

This can become awkward with multiple nested levels and repeated string manipulation.

A Stack lets us parse the entire input in one pass.


---

5. Key Insight

The most important observation:

> When we encounter [, the current string and repeat count belong to the outer level, so we save them before starting the new inner level.



When we encounter ]:

inner result
      ↓
repeat it
      ↓
attach it to previous string

For example:

3[a2[c]]

At the inner level:

current = "c"
number = 2

After ]:

"c" * 2
→ "cc"

Then restore the outer "a":

"a" + "cc"
→ "acc"

Finally:

"acc" * 3
→ "accaccacc"


---

6. Algorithm

Maintain:

num = 0
current = ""
stack = []

Case 1 — Digit

If we see a digit:

3
12
25

build the complete number.

num = num * 10 + int(ch)

This is important because numbers can have multiple digits.

For:

"123"

we calculate:

0
 ↓
1
 ↓
12
 ↓
123


---

Case 2 — "["

We are entering a nested expression.

Save:

current string
repeat count

onto the Stack.

Conceptually:

stack.append((current, num))

Then reset:

current = ""
num = 0

Now we can independently decode the inner section.


---

Case 3 — Normal character

Append it to the current decoded string:

current += ch


---

Case 4 — "]"

We have finished the current nested section.

Retrieve:

previous_string, repeat_count = stack.pop()

Then:

current = previous_string + current * repeat_count

This restores the previous context.


---

Final

Return:

current


---

7. Invariant

Critical invariant:

> current represents the decoded string at the current nesting level, while the Stack contains the saved states of all outer nesting levels.



For:

3[a2[c]]

while processing 2[c], conceptually:

current = "a"
stack = [
    ("", 3)
]

After entering 2[:

current = ""
stack = [
    ("", 3),
    ("a", 2)
]

The Stack is literally storing the unfinished outer contexts.


---

8. Complexity

Let:

n = length of the encoded input

The parsing itself scans the input once.

However, there is an important interview nuance:

The decoded output can be much larger than the input.

For example:

100[a]

has a tiny input but produces 100 characters.

Therefore, the realistic complexity is:

Time = O(n + D)
Space = O(n + D)

where D is the size of the decoded output.

If the interviewer asks for complexity relative to the input alone, be careful: the output itself may be exponentially larger under deep nesting/repetition.

A more precise statement is:

> The algorithm is linear in the amount of input plus the amount of decoded output it must construct.




---

9. Interview Tips / Traps

Trap 1 — Multi-digit numbers

Don't assume:

3[a]

is the only form.

You can have:

12[a]

So:

num = int(ch)

for every digit independently is wrong.

You need:

num = num * 10 + int(ch)


---

Trap 2 — Don't forget to reset num

After:

3[

we start a new nesting level.

So:

num = 0

must happen after saving the state.


---

Trap 3 — "[" does not mean just push the number

You must preserve both:

previous string
+
repeat count

Because after ], you need both.


---

Trap 4 — "]" means restore state

Don't simply multiply the current string.

You need:

previous_string + current * repeat_count

because the inner result belongs after whatever was already decoded outside.


---

Trap 5 — Nested expressions

For:

3[a2[c]]

the Stack must handle:

outer context
    ↓
inner context
    ↓
deeper context

This is why a simple variable isn't enough.


---

🔹 Block 2 — Efficient Code

class Solution:
    def decodeString(self, s: str) -> str:
        stack = []
        current = ""
        num = 0

        for ch in s:
            if ch.isdigit():
                num = num * 10 + int(ch)

            elif ch == "[":
                stack.append((current, num))
                current = ""
                num = 0

            elif ch == "]":
                previous_string, repeat_count = stack.pop()
                current = previous_string + current * repeat_count

            else:
                current += ch

        return current

Time Complexity

O(n + D)

n is the encoded input size and D is the size of the decoded output.

The parser processes every input character once, while constructing the final answer necessarily costs time proportional to the output produced.

Space Complexity

O(n + D)

The Stack stores nested contexts, and the decoded strings being constructed can require space proportional to the output.

Interview Complexity Explanation

> "The input is parsed once, but the decoded result can be much larger than the input because of repetition. Therefore the precise complexity is O(n + D), where D is the decoded output size. The stack depth is proportional to the nesting depth, and the constructed result also requires output space."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def decodeString(self, s: str) -> str:
        stack = []
        current = ""
        num = 0

        for ch in s:
            if ch.isdigit():
                num = num * 10 + int(ch)

            elif ch == "[":
                stack.append((current, num))
                current = ""
                num = 0

            elif ch == "]":
                previous_string, repeat_count = stack.pop()
                current = previous_string + current * repeat_count

            else:
                current += ch

        return current


# Example input
s = "3[a2[c]]"

# Create Solution object
solution = Solution()

# Call the method
result = solution.decodeString(s)

# Print output
print("Input:", s)
print("Output:", result)

Output

Input: 3[a2[c]]
Output: accaccacc


---

Step-by-Step Dry Run

Input:

3[a2[c]]

Initial state:

stack = []
current = ""
num = 0


---

Step 1 — 3

Digit.

num = 0 * 10 + 3
    = 3

State:

stack = []
current = ""
num = 3


---

Step 2 — [

We are entering:

3[ ... ]

Save:

("", 3)

Stack:

stack = [
    ("", 3)
]

Reset:

current = ""
num = 0


---

Step 3 — a

Normal character.

current = "a"


---

Step 4 — 2

Digit:

num = 2

State:

current = "a"
num = 2
stack = [
    ("", 3)
]


---

Step 5 — [

Save the current outer context:

("a", 2)

Stack becomes:

stack = [
    ("", 3),
    ("a", 2)
]

Reset:

current = ""
num = 0


---

Step 6 — c

Normal character:

current = "c"


---

Step 7 — ]

We finished:

2[c]

Pop:

previous_string = "a"
repeat_count = 2

Current inner result:

"c" * 2
= "cc"

Restore outer context:

current = "a" + "cc"
        = "acc"

Stack:

[
    ("", 3)
]


---

Step 8 — ]

Now we finished:

3[acc]

Pop:

previous_string = ""
repeat_count = 3

Repeat:

"acc" * 3

Result:

"accaccacc"

Stack:

[]


---

Final Answer

accaccacc


---

Dry-Run Table

Step	Character	num	current	Stack	Action

1	3	3	""	[]	Build number
2	[	0	""	[("",3)]	Save context
3	a	0	"a"	[("",3)]	Add character
4	2	2	"a"	[("",3)]	Build number
5	[	0	""	[("",3),("a",2)]	Save context
6	c	0	"c"	[("",3),("a",2)]	Add character
7	]	0	"acc"	[("",3)]	Restore + repeat
8	]	0	"accaccacc"	[]	Restore + repeat



---

Another Important Example

2[abc]3[cd]ef

Process:

2[abc]
   ↓
abcabc

3[cd]
   ↓
cdcdcd

then ef

Final:

abcabccdcdcdef

Notice that separate nested groups don't need to be nested inside each other. The same Stack mechanism handles them sequentially.


---

🔹 Block 4 — Interview Q&A

Q1. Why do we need a Stack for LC 394?

Model Answer:

> "Because the encoding is nested. When I encounter [, I need to save the current string and repeat count. When I encounter ], I restore that previous context and combine it with the decoded inner string. The Stack naturally handles multiple nesting levels using LIFO order."




---

Q2. What exactly does one Stack entry contain?

Model Answer:

> "Each entry contains the string that existed before entering the current bracket and the repeat count associated with that bracket. So conceptually each entry is (previous_string, repeat_count)."




---

Q3. Why do we reset current and num after [?

Model Answer:

> "Because we're entering a new nested context. The characters inside the brackets must be decoded independently, while the previous string and repeat count have already been saved on the Stack."




---

Q4. How do you handle a number like 123[a]?

Model Answer:

> "I accumulate digits using num = num * 10 + int(ch). That converts a sequence of digits into the complete repeat count rather than treating each digit independently."




---

Q5. What is the key invariant?

Model Answer:

> "The current string represents the decoded content at the current nesting level, while the Stack contains the unfinished contexts of all outer nesting levels."




---

Q6. What is the biggest complexity trap in this problem?

Model Answer:

> "The decoded output can be much larger than the encoded input. So saying simply O(n) can be misleading. The precise complexity is O(n + D), where D is the size of the decoded output."




---

🧠 Pattern Extraction

Problem Clue
Nested k[...]
        ↓
Need to preserve outer state
        ↓
Pattern
Nested Parsing + Stack
        ↓
Data Structure
Stack of (previous_string, repeat_count)
        ↓
Invariant
current = decoded string at current level
stack = unfinished outer contexts
        ↓
Core Operations

digit → build repeat count

[ → save state + enter new level

] → restore state + combine

letter → append


---

🔥 Master Template

This is the reusable nested-parsing template:

stack = []
current = ""
num = 0

for ch in s:

    if ch.isdigit():
        num = num * 10 + int(ch)

    elif ch == "[":
        stack.append((current, num))
        current = ""
        num = 0

    elif ch == "]":
        previous, repeat = stack.pop()
        current = previous + current * repeat

    else:
        current += ch

return current

Mental model

ENTER NESTED LEVEL
                  ↓
          Save previous state
                  ↓
              [ inner ]
                  ↓
          Finish inner state
                  ↓
          Restore previous state
                  ↓
              Combine

This is the real mastery point.

LC 394 isn't fundamentally about strings.

It's about:

> Saving state when entering a nested context and restoring that state when leaving it.




---

📈 Progress Update

Pattern 2 — Parsing / Nested Structures

Problem	Status

LC 71 — Simplify Path	✅ Completed
LC 394 — Decode String	✅ Completed
LC 150 — Evaluate Reverse Polish Notation	⏭️ Next
LC 224 — Basic Calculator	🔒


Your Stack progression is now:

Pattern 1
Matching
  ↓
Cancellation
  ↓
Character Cancellation
        ✅ COMPLETE

Pattern 2
Path Parsing
  ↓
Nested Parsing
  ↓
Expression Stack
  ↓
Expression + Stack


---

🧠 Senior Pattern Recognition

When you see:

Nested
+
Need to remember what was happening before entering the nested section
+
Need to restore it afterward

your first thought should be:

STACK
          ↓
Save previous state
          ↓
Process nested state
          ↓
Pop previous state
          ↓
Combine

Compare the two problems you've now covered:

LC 71
".." 
 ↓
Undo previous directory
 ↓
STACK


LC 394
"["
 ↓
Save previous decoding context
 ↓
STACK

Different problem.

Same fundamental Stack idea: state management.


---

⚡ One-Line Takeaway

> Nested structure + "remember what was happening before" = Stack; push the old state when entering, pop and restore it when leaving.


LC 150 — Evaluate Reverse Polish Notation

Pattern: Expression Stack
Difficulty: Medium
Interview Importance: 🔥🔥 High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given a mathematical expression written in Reverse Polish Notation (RPN).

Unlike normal math:

2 + 3

RPN puts the operator after its operands:

2 3 +

Meaning:

2 + 3 = 5

Another example:

["2", "1", "+", "3", "*"]

means:

(2 + 1) * 3
= 9

The key is that when an operator appears, it operates on the two most recent numbers.

That is exactly what a Stack provides.


---

2. Pattern Identification

Pattern → Expression Stack

Recognition clues:

Tokens are processed left-to-right.

Numbers need to be remembered.

An operator consumes the most recent operands.

The result becomes an operand for later operations.


Therefore:

Expression
    ↓
Operands arrive
    ↓
Need most recent operands
    ↓
STACK
    ↓
Operator → POP operands
    ↓
Calculate
    ↓
PUSH result

What a senior engineer notices immediately

The expression has no parentheses and no operator precedence to manage.

That's the major advantage of RPN.

For:

["4", "13", "5", "/", "+"]

you simply process tokens sequentially.

No need to ask:

> "Does multiplication happen before addition?"



The notation already encodes the evaluation order.


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
Postfix / Reverse Polish expression
      ↓
Operator uses previous two operands
      ↓
Need LIFO access
      ↓
STACK
      ↓
Number → PUSH
Operator → POP, calculate, PUSH

The core Stack operation is:

operand → push

operator
   ↓
pop right operand
pop left operand
   ↓
calculate
   ↓
push result

Important: the order of the two pops matters for - and /.


---

4. Brute Force / Naive Approach

You could repeatedly search for a pattern like:

number number operator

then replace it with the result.

For example:

2 1 + 3 *

becomes:

3 3 *

then:

9

But repeatedly modifying/searching the expression is unnecessary.

The Stack evaluates it naturally in one pass.


---

5. Key Insight

When you encounter an operator:

a b operator

the Stack contains:

... a, b

So:

right = stack.pop()
left = stack.pop()

Then:

result = left operator right

Finally:

stack.append(result)

Critical detail

For:

["4", "2", "/"]

you must calculate:

4 / 2

not:

2 / 4

Because:

right = 2
left = 4

Therefore:

left / right


---

6. Algorithm

Initialize:

stack = []

Process every token.

If token is a number

Convert it to an integer and push:

stack.append(int(token))

If token is an operator

Pop the operands:

right = stack.pop()
left = stack.pop()

Perform the operation:

+ → left + right
- → left - right
* → left * right
/ → left / right

Then push the result:

stack.append(result)

At the end:

return stack[-1]

There will be exactly one result.


---

7. Invariant

Critical invariant

> After processing any prefix of the RPN expression, the Stack contains the results of all completed subexpressions that have not yet been consumed by a later operator.



Example:

2 1 + 3 *

After:

2 1 +

the completed subexpression:

2 + 1 = 3

is represented by:

stack = [3]

Then 3 arrives:

stack = [3, 3]

Then * consumes both:

3 * 3 = 9

Stack:

[9]


---

8. Complexity

Let:

n = number of tokens

Time: O(n)

We inspect each token exactly once.

For every token:

number → one push

operator → two pops + one calculation + one push


All are O(1).

Therefore:

O(n)

Space: O(n)

In the worst case, many operands can appear before an operator.

Example:

1 2 3 4 5 ...

The Stack can temporarily contain O(n) values.

Therefore:

O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Operand order

This is the biggest trap.

Correct:

right = stack.pop()
left = stack.pop()

Then:

left - right
left / right

Wrong:

a = stack.pop()
b = stack.pop()

a - b

That reverses subtraction/division.


---

🚨 Trap 2 — Division truncation

The problem specifies integer division that truncates toward zero.

For example:

-7 / 3 → -2

Python's // would produce:

-7 // 3 = -3

That's wrong for this problem.

Use:

int(left / right)

This truncates the mathematical result toward zero.


---

🚨 Trap 3 — Don't use eval()

You might be tempted to convert the expression into a normal Python expression and call eval().

Don't.

It defeats the purpose of the problem and is poor interview practice.

The interviewer wants to see that you understand the Stack evaluation pattern.


---

🚨 Trap 4 — Negative numbers

Tokens can already be negative:

"-11"

So checking whether something is a digit using:

token.isdigit()

is insufficient.

A clean approach is to recognize operators explicitly and treat everything else as an integer.


---

🔹 Block 2 — Efficient Code

class Solution:
    def evalRPN(self, tokens: list[str]) -> int:
        stack = []

        for token in tokens:
            if token in {"+", "-", "*", "/"}:
                right = stack.pop()
                left = stack.pop()

                if token == "+":
                    result = left + right
                elif token == "-":
                    result = left - right
                elif token == "*":
                    result = left * right
                else:
                    result = int(left / right)

                stack.append(result)

            else:
                stack.append(int(token))

        return stack[-1]

Time Complexity

O(n)

Every token is processed once, and each Stack operation is O(1).

Space Complexity

O(n)

The Stack can contain up to O(n) operands in the worst case.

Interview Complexity Explanation

> "I process each RPN token exactly once. Operands are pushed onto the Stack, and each operator pops its two operands, computes the result, and pushes that result back. Since each token causes only constant-time Stack operations, the total time is O(n), with O(n) auxiliary space in the worst case."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def evalRPN(self, tokens: list[str]) -> int:
        stack = []

        for token in tokens:
            if token in {"+", "-", "*", "/"}:
                right = stack.pop()
                left = stack.pop()

                if token == "+":
                    result = left + right
                elif token == "-":
                    result = left - right
                elif token == "*":
                    result = left * right
                else:
                    result = int(left / right)

                stack.append(result)

            else:
                stack.append(int(token))

        return stack[-1]


# Example input
tokens = ["2", "1", "+", "3", "*"]

# Create Solution object
solution = Solution()

# Call the method
result = solution.evalRPN(tokens)

# Print output
print("Input:", tokens)
print("Output:", result)

Output

Input: ['2', '1', '+', '3', '*']
Output: 9


---

Step-by-Step Dry Run

Input:

["2", "1", "+", "3", "*"]

Initial:

stack = []

Step 1 — "2"

Number.

Push:

stack = [2]


---

Step 2 — "1"

Number.

Push:

stack = [2, 1]


---

Step 3 — "+"

Operator.

Pop right:

right = 1
stack = [2]

Pop left:

left = 2
stack = []

Calculate:

2 + 1 = 3

Push result:

stack = [3]


---

Step 4 — "3"

Number.

Push:

stack = [3, 3]


---

Step 5 — "*"

Operator.

Pop right:

right = 3
stack = [3]

Pop left:

left = 3
stack = []

Calculate:

3 * 3 = 9

Push:

stack = [9]

Final:

9


---

Dry-Run Table

Step	Token	Action	Stack

1	2	Push 2	[2]
2	1	Push 1	[2, 1]
3	+	2 + 1 = 3	[3]
4	3	Push 3	[3, 3]
5	*	3 * 3 = 9	[9]


Final answer:

9


---

More Important Dry Run — Subtraction

Consider:

["4", "13", "5", "/", "+"]

Process:

4
→ stack = [4]

13
→ stack = [4, 13]

5
→ stack = [4, 13, 5]

/
→ right = 5
→ left = 13
→ 13 / 5 = 2
→ stack = [4, 2]

+
→ right = 2
→ left = 4
→ 4 + 2 = 6
→ stack = [6]

Answer:

6

Notice:

left = 13
right = 5

not the other way around.


---

🔹 Block 4 — Interview Q&A

Q1. Why is a Stack the natural data structure for RPN?

Model Answer:

> "In RPN, an operator always applies to the two most recently available operands. A Stack gives us exactly that LIFO access, so operands can be pushed as they arrive and popped when an operator is encountered."




---

Q2. Why do you pop right before left?

Model Answer:

> "Because the right operand appears later in the RPN expression and is therefore on top of the Stack. I pop it first, then pop the left operand. This preserves the correct order for non-commutative operations such as subtraction and division."




---

Q3. Why can't you use // for division in Python?

Model Answer:

> "The problem requires truncation toward zero. Python's floor division rounds toward negative infinity, so -7 // 3 gives -3, whereas the required result is -2. I therefore use division followed by integer conversion to truncate toward zero."




---

Q4. What does the Stack represent during execution?

Model Answer:

> "It contains the results of completed subexpressions that haven't yet been consumed by another operator. Each operator replaces its two operands with their computed result."




---

Q5. What is the time complexity?

Model Answer:

> "O(n), where n is the number of tokens, because every token is processed exactly once and each token requires only constant-time Stack operations."




---

Q6. Why is this easier than evaluating a normal infix expression?

Model Answer:

> "RPN explicitly encodes the evaluation order, so there are no parentheses or operator-precedence rules to manage. I simply process tokens from left to right and let the Stack handle the operands."




---

🧠 Pattern Extraction

Problem Clue
Postfix expression
+
Operator consumes previous operands
        ↓
Pattern
Expression Stack
        ↓
Data Structure
Stack
        ↓
Invariant
Stack contains completed subexpression results
        ↓
Core Operation

number
   ↓
PUSH

operator
   ↓
POP right
POP left
   ↓
calculate
   ↓
PUSH result


---

🔥 Master Template

Memorize the pattern, not LC 150:

stack = []

for token in tokens:

    if token_is_operand:
        stack.append(value)

    else:
        right = stack.pop()
        left = stack.pop()

        result = operate(left, right)

        stack.append(result)

answer = stack[-1]

Universal mental model

Operand
  ↓
SAVE

Operator
  ↓
TAKE TWO
  ↓
COMPUTE
  ↓
SAVE RESULT

This same idea appears in:

Postfix expression evaluation

Calculator implementations

Expression trees

Compiler/interpreter evaluation

Stack-machine architectures



---

📈 Progress Update

Pattern 2 — Parsing / Nested Structures

Problem	Status

LC 71 — Simplify Path	✅
LC 394 — Decode String	✅
LC 150 — Evaluate Reverse Polish Notation	✅ Completed
LC 224 — Basic Calculator	⏭️ Next


Your Stack progression:

PATTERN 1 — Matching / Cancellation
        ↓
LC 20
LC 1047
LC 1544
        ↓
PATTERN 2 — Parsing / Nested Structures
        ↓
LC 71  → Path state
LC 394 → Nested state
LC 150 → Expression state
LC 224 → Expression + state

The important evolution is:

LC 71
Stack = previous directory state

LC 394
Stack = previous nesting state

LC 150
Stack = previous operand/subexpression state

Same Stack. Different meaning of "state."


---

🧠 Senior Pattern Recognition

When you see:

Operator consumes the most recent operands

immediately translate:

Most recent operands
        ↓
LIFO
        ↓
STACK

Then ask:

What does one Stack element represent?

For LC 150:

One Stack element
        ↓
A completed subexpression result

That question is more valuable than memorizing the code.


---

⚡ One-Line Takeaway

> In Reverse Polish Notation, push operands; when an operator appears, pop right then left, compute, and push the result back.



LC 224 — Basic Calculator

Pattern: Expression + Stack
Difficulty: Hard
Interview Importance: 🔥🔥🔥 Very High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given a normal mathematical expression containing:

digits

+

-

(

)

spaces


You need to evaluate it.

Examples:

"1 + 1"       → 2

"2-1 + 2"     → 3

"(1+(4+5+2)-3)+(6+8)" → 23

The problem becomes difficult because of parentheses.

For example:

1 - (2 - 3)

The expression inside the parentheses has its own calculation context.

The Stack is used to remember the state of the expression before entering the parentheses.


---

2. Pattern Identification

Pattern → Expression + Stack

The critical clue is:

> Parentheses create a nested expression context.



When we encounter:

(

we need to save the current calculation state.

When we encounter:

)

we need to restore that previous state.

That is exactly the same fundamental idea we saw in LC 394.

Nested expression
       ↓
Save outer state
       ↓
Process inner expression
       ↓
Restore outer state
       ↓
Combine

Therefore:

Parentheses
    ↓
Nested state
    ↓
Stack


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
Expression with parentheses
      ↓
Parentheses create nested contexts
      ↓
Need to preserve previous result/sign
      ↓
STACK
      ↓
"(" → save state
")" → restore state

There are two important pieces of state:

result
sign

Before entering parentheses, save:

previous_result
previous_sign

Conceptually:

stack.append(result)
stack.append(sign)

Then start calculating the inner expression.

When ) arrives:

sign = stack.pop()
previous_result = stack.pop()

and combine the inner result with the outer context.


---

4. Brute Force / Naive Approach

A naive approach would repeatedly find the innermost parentheses:

1 + (2 - (3 + 4))

Evaluate:

(3 + 4)

then:

(2 - 7)

then:

1 + (-5)

This requires repeatedly locating and replacing parenthesized expressions.

That's unnecessary.

A Stack lets us evaluate the expression left-to-right in one pass.


---

5. Key Insight

The most important insight is:

> Because the expression contains only + and -, we don't need a general operator-precedence engine. We only need to track the current result and sign, while the Stack stores the outer context created by parentheses.



For example:

1 - (2 + 3)

Outside:

result = 1
sign = +

When ( begins:

save:
    result = 1
    sign = -

Then calculate:

2 + 3 = 5

When ) arrives:

1 + (-1 × 5)
= -4

The outer - effectively applies to the entire parenthesized expression.


---

6. Algorithm

Maintain:

result = 0
number = 0
sign = 1
stack = []

Case 1 — Digit

Build the complete number:

number = number * 10 + int(ch)

This handles:

123

as one number.


---

Case 2 — +

The previous number is finished.

Apply the current sign:

result += sign * number

Then:

number = 0
sign = 1


---

Case 3 — -

Same idea:

result += sign * number

Then set:

sign = -1
number = 0


---

Case 4 — (

Save the outer context.

First store the current partial result:

stack.append(result)

Then store the sign that applies to the new parenthesized expression:

stack.append(sign)

Reset:

result = 0
sign = 1

Now we evaluate the expression inside the parentheses independently.


---

Case 5 — )

First finish the number currently being built:

result += sign * number
number = 0

Then restore:

previous_sign = stack.pop()
previous_result = stack.pop()

Combine:

result = previous_result + previous_sign * result

This is the key operation.


---

Case 6 — Space

Ignore it.


---

Final

There may be a number still waiting to be processed.

So:

result += sign * number

Return result.


---

7. Invariant

Critical invariant

> result represents the evaluated value of the expression processed so far within the current parenthesis level, while the Stack contains the unfinished outer contexts.



At any point:

current result
+
current sign
+
unfinished outer contexts

completely describes the calculation state.

For:

1-(2+3)

when entering (:

stack = [1, -1]

Meaning:

outer result = 1
outer sign   = -1

Then the inner expression can be evaluated independently.


---

8. Complexity

Let:

n = length of the expression

Time: O(n)

Every character is processed once.

For each character we perform only constant-time operations:

digit accumulation

addition

subtraction

Stack push

Stack pop


Therefore:

Time = O(n)

Space: O(n)

In the worst case, the expression can contain deeply nested parentheses:

((((((((1))))))))

The Stack must store the state of every nesting level.

Therefore:

Space = O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Forgetting the number before )

For:

(12+3)

when ) arrives, 12 or 3 may still be sitting in number.

You must first do:

result += sign * number

before restoring the outer context.


---

🚨 Trap 2 — Stack order

If you do:

stack.append(result)
stack.append(sign)

then you must pop:

previous_sign = stack.pop()
previous_result = stack.pop()

because Stack is LIFO.


---

🚨 Trap 3 — Parentheses change context, not arithmetic rules

Don't treat ( as an arithmetic operator.

Its purpose is:

SAVE STATE
RESET STATE

And ) means:

FINISH INNER STATE
RESTORE OUTER STATE
COMBINE


---

🚨 Trap 4 — Multi-digit numbers

You must support:

123
456
1000

So:

number = number * 10 + int(ch)

is required.


---

🚨 Trap 5 — Unary minus

Expressions can contain cases such as:

-2+1

or:

1-(-2)

A robust implementation needs the sign state to handle these correctly.


---

🔹 Block 2 — Efficient Code

class Solution:
    def calculate(self, s: str) -> int:
        stack = []

        result = 0
        number = 0
        sign = 1

        for ch in s:
            if ch.isdigit():
                number = number * 10 + int(ch)

            elif ch == "+":
                result += sign * number
                number = 0
                sign = 1

            elif ch == "-":
                result += sign * number
                number = 0
                sign = -1

            elif ch == "(":
                stack.append(result)
                stack.append(sign)

                result = 0
                sign = 1

            elif ch == ")":
                result += sign * number
                number = 0

                previous_sign = stack.pop()
                previous_result = stack.pop()

                result = previous_result + previous_sign * result

        result += sign * number

        return result

Time Complexity

O(n)

Each character is processed once, with only constant-time arithmetic or Stack operations.

Space Complexity

O(n)

The Stack stores one result/sign pair for each active parenthesis level.

Interview Complexity Explanation

> "I scan the expression once. The Stack only stores the result and sign of each outer parenthesis context, so every character and every Stack operation is constant time. Therefore the time complexity is O(n), and the auxiliary space is O(n) in the worst case due to nested parentheses."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def calculate(self, s: str) -> int:
        stack = []

        result = 0
        number = 0
        sign = 1

        for ch in s:
            if ch.isdigit():
                number = number * 10 + int(ch)

            elif ch == "+":
                result += sign * number
                number = 0
                sign = 1

            elif ch == "-":
                result += sign * number
                number = 0
                sign = -1

            elif ch == "(":
                stack.append(result)
                stack.append(sign)

                result = 0
                sign = 1

            elif ch == ")":
                result += sign * number
                number = 0

                previous_sign = stack.pop()
                previous_result = stack.pop()

                result = previous_result + previous_sign * result

        result += sign * number

        return result


# Example input
expression = "(1+(4+5+2)-3)+(6+8)"

# Create Solution object
solution = Solution()

# Call the method
result = solution.calculate(expression)

# Print output
print("Input:", expression)
print("Output:", result)

Output

Input: (1+(4+5+2)-3)+(6+8)
Output: 23


---

Step-by-Step Dry Run

Expression:

(1+(4+5+2)-3)+(6+8)

We will track:

result
number
sign
stack

Initial:

result = 0
number = 0
sign = 1
stack = []


---

Step 1 — (

Save outer context:

stack = [0, 1]

Reset:

result = 0
sign = 1
number = 0


---

Step 2 — 1

Build number:

number = 1


---

Step 3 — +

Apply:

result += 1 * 1
result = 1

Reset:

number = 0
sign = 1

State:

result = 1
stack = [0, 1]


---

Step 4 — (

Save current context:

stack = [0, 1, 1, 1]

Interpretation:

outer result = 1
outer sign   = +

Reset:

result = 0
sign = 1


---

Step 5 — 4

number = 4


---

Step 6 — +

Apply:

result = 4
number = 0
sign = 1


---

Step 7 — 5

number = 5


---

Step 8 — +

Apply:

result = 4 + 5
       = 9


---

Step 9 — 2

number = 2


---

Step 10 — )

First finish 2:

result = 9 + 2
       = 11

Now restore outer state:

previous_sign = 1
previous_result = 1

Combine:

result = 1 + 1 * 11
       = 12

Stack:

[0, 1]

So:

(1+(4+5+2))

has become:

12


---

Step 11 — -

Set:

sign = -1
number = 0


---

Step 12 — 3

number = 3


---

Step 13 — )

Finish 3:

result = 12 + (-1 * 3)
       = 9

Restore:

previous_sign = 1
previous_result = 0

Combine:

result = 0 + 1 * 9
       = 9

Stack:

[]

So:

(1+(4+5+2)-3)

evaluates to:

9


---

Step 14 — +

sign = 1
number = 0


---

Step 15 — (

Save:

stack = [9, 1]

Reset:

result = 0
sign = 1


---

Step 16 — 6

number = 6


---

Step 17 — +

result = 6
number = 0
sign = 1


---

Step 18 — 8

number = 8


---

Step 19 — )

Finish:

result = 6 + 8
       = 14

Restore:

previous_sign = 1
previous_result = 9

Combine:

result = 9 + 1 * 14
       = 23

Final:

23


---

Dry-Run Table

Token	Action	Result	Number	Sign	Stack

(	Save context	0	0	+	[0,+]
1	Build number	0	1	+	[0,+]
+	Apply number	1	0	+	[0,+]
(	Save context	1	0	+	[0,+,1,+]
4	Build	1	4	+	[0,+,1,+]
+	Apply	5	0	+	[0,+,1,+]
5	Build	5	5	+	[0,+,1,+]
+	Apply	10	0	+	[0,+,1,+]
2	Build	10	2	+	[0,+,1,+]
)	Restore	12	0	+	[0,+]
-	Change sign	12	0	−	[0,+]
3	Build	12	3	−	[0,+]
)	Restore	9	0	+	[]
+	Change sign	9	0	+	[]
(	Save context	9	0	+	[9,+]
6	Build	9	6	+	[9,+]
+	Apply	15	0	+	[9,+]
8	Build	15	8	+	[9,+]
)	Restore	23	0	+	[]



---

Important Mini Dry Run — Why the Saved Sign Matters

Consider:

1-(2+3)

When we reach (:

result = 1
sign = -1

Save:

stack = [1, -1]

Then calculate inside:

2 + 3 = 5

At ):

previous_result = 1
previous_sign = -1
current result = 5

Combine:

1 + (-1 * 5)
= -4

Without saving the sign, you would incorrectly get:

1 + 5 = 6

That's the central reason the Stack stores both result and sign.


---

🔹 Block 4 — Interview Q&A

Q1. Why is a Stack needed in Basic Calculator?

Model Answer:

> "Parentheses create nested expression contexts. When I enter a parenthesis, I need to preserve the result and sign from the outer context. When I leave it, I restore those values and combine the inner result with the outer expression. A Stack naturally handles those nested contexts."




---

Q2. What does one Stack frame contain?

Model Answer:

> "Each frame contains the result accumulated before entering the parenthesis and the sign that applies to the entire parenthesized expression."



Conceptually:

(previous_result, previous_sign)


---

Q3. Why don't we need operator precedence here?

Model Answer:

> "LC 224 only contains addition and subtraction, which have the same precedence and are evaluated left-to-right. Parentheses are handled explicitly using the Stack, so we don't need a general precedence mechanism."




---

Q4. What happens when you encounter )?

Model Answer:

> "First I finalize the number currently being built. Then I pop the previous sign and previous result from the Stack. The inner result is multiplied by the saved sign and added to the previous result."



result = previous_result + previous_sign * inner_result


---

Q5. Why is the time complexity O(n)?

Model Answer:

> "Every character is processed exactly once. Number construction, arithmetic, and Stack push/pop operations are all constant-time, so the total work is linear in the expression length."




---

Q6. How would you recognize this pattern in an unseen problem?

Model Answer:

> "If I see nested expressions where entering a nested section requires preserving the current computation and leaving it requires restoring that computation, I immediately consider a Stack. The Stack represents the unfinished outer contexts."




---

🧠 Pattern Extraction

Problem Clue
Expression + nested parentheses
        ↓
Parentheses create nested state
        ↓
Pattern
Expression + Stack
        ↓
Data Structure
Stack of (previous_result, previous_sign)
        ↓
Invariant
Current result = value of current nesting level
        ↓
Core Operations

digit
  ↓
build number

+
  ↓
apply current number
  ↓
sign = +

-
  ↓
apply current number
  ↓
sign = -

(
  ↓
save outer state
  ↓
reset inner state

)
  ↓
finish inner result
  ↓
restore outer state
  ↓
combine


---

🔥 Master Template

The reusable parentheses + expression Stack template:

stack = []

result = 0
number = 0
sign = 1

for ch in s:

    if ch.isdigit():
        number = number * 10 + int(ch)

    elif ch == "+":
        result += sign * number
        number = 0
        sign = 1

    elif ch == "-":
        result += sign * number
        number = 0
        sign = -1

    elif ch == "(":
        stack.append(result)
        stack.append(sign)

        result = 0
        sign = 1

    elif ch == ")":
        result += sign * number
        number = 0

        previous_sign = stack.pop()
        previous_result = stack.pop()

        result = previous_result + previous_sign * result

result += sign * number

Deeper pattern

Nested expression
       ↓
Save outer computation
       ↓
Evaluate inner computation
       ↓
Restore outer computation
       ↓
Combine

That is the actual pattern you should carry into other problems.


---

📈 Progress Update

Pattern 2 — Parsing / Nested Structures

Problem	Status

LC 71 — Simplify Path	✅
LC 394 — Decode String	✅
LC 150 — Evaluate Reverse Polish Notation	✅
LC 224 — Basic Calculator	✅ Completed


Pattern 2 is now COMPLETE.

PATTERN 2 — Parsing / Nested Structures
                ↓
LC 71
Stack = path state
                ↓
LC 394
Stack = nested decoding state
                ↓
LC 150
Stack = expression/subexpression state
                ↓
LC 224
Stack = nested expression state
                ↓
        ✅ MASTERED


---

🧠 Senior Pattern Recognition

You've now seen four different interpretations of the same Stack:

LC 71
".." 
 ↓
Undo previous directory
 ↓
Stack = path state


LC 394
"["
 ↓
Save previous decoding context
 ↓
Stack = nested state


LC 150
Operator
 ↓
Consume latest operands
 ↓
Stack = completed subexpressions


LC 224
"("
 ↓
Save previous calculation context
 ↓
Stack = unfinished expression contexts

The senior-level abstraction is:

> Stack is not "the bracket data structure." Stack is a mechanism for managing LIFO state.



When the problem says, implicitly:

"I need to remember what was happening before
until this current context finishes."

you should consider a Stack.


---

⚡ One-Line Takeaway

> Parentheses create nested calculation contexts: push the outer result/sign when entering, evaluate the inner expression, then pop and combine when leaving.




# Pattern 3

LC 496 — Next Greater Element I

Pattern: Monotonic Stack — Next Greater Element
Difficulty: Easy
Interview Importance: 🔥🔥🔥 Foundation for Monotonic Stack


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given two arrays:

nums1
nums2

Every element in nums1 appears in nums2.

For every element in nums1, find the first greater element to its right in nums2.

If no greater element exists, return:

-1

Example

nums1 = [4, 1, 2]
nums2 = [1, 3, 4, 2]

For 4:

4 → nothing greater on its right
→ -1

For 1:

1 → 3

For 2:

2 → nothing
→ -1

Answer:

[-1, 3, -1]


---

2. Pattern Identification

The key phrase is:

> Next greater element



That should immediately trigger:

Next Greater
     ↓
Monotonic Stack

Why?

A brute-force solution would take every element and scan everything to its right:

For each x:
    search right
    find first value > x

That can become:

O(n²)

But notice something more powerful:

Suppose we process:

[1, 3, 4, 2]

When we reach 3, we know:

3 > 1

Therefore 3 has just answered the unresolved question for 1.

When we reach 4:

4 > 3
4 > 1

Again, it resolves previous elements.

This gives us:

Current element
      ↓
Can it answer previous elements?
      ↓
YES
      ↓
POP unresolved smaller elements
      ↓
Record current as their answer

That's the Monotonic Stack pattern.


---

3. Senior Engineer Mindset

Translate the problem like this:

Problem wording
      ↓
"Next greater element"
      ↓
Need first greater value to the right
      ↓
Previous elements are waiting for answers
      ↓
Maintain unresolved elements
      ↓
Monotonic Stack
      ↓
Current value resolves smaller elements

The senior-level question

Don't ask:

> "How do I find the next greater element for this number?"



Ask:

> "Can I process the array once and let each new number resolve the elements waiting for a greater value?"



That change in viewpoint is the entire trick.


---

4. Brute Force / Naive Approach

For each element in nums2, scan to the right.

Example:

[1, 3, 4, 2]

For 1:

3 > 1
→ answer = 3

For 3:

4 > 3
→ answer = 4

For 4:

2 is not greater
→ nothing
→ -1

For every element, potentially scanning many elements gives:

Time: O(n²)

This works for small input but wastes repeated work.


---

5. Key Insight

🔥 The Stack stores unresolved elements.

Suppose we process:

[1, 3, 4, 2]

Start:

stack = []

Read 1:

stack = [1]

1 hasn't found a greater element yet.

Read 3:

3 > 1

So:

1 → 3

Pop 1.

Then push 3:

stack = [3]

Read 4:

4 > 3

Therefore:

3 → 4

Pop 3.

Push 4:

stack = [4]

Read 2:

2 < 4

So 2 cannot resolve 4.

Push:

stack = [4, 2]

At the end:

4 → -1
2 → -1

The Stack is therefore:

> A collection of elements that have not yet found their next greater element.



That's the reusable concept.


---

6. Algorithm

We need to answer only elements in nums1, but the relationships are found by processing nums2.

Use a HashMap:

next_greater = {}

Process nums2 using a Stack.

Step 1 — Read current value

for x in nums2:

Step 2 — Resolve smaller elements

While:

stack and x > stack[-1]

the current x is the next greater element for the Stack's top.

Therefore:

value = stack.pop()
next_greater[value] = x

Step 3 — Push current value

After resolving everything that x can resolve:

stack.append(x)

Step 4 — Remaining elements

Anything left in the Stack never found a greater element.

So:

answer = -1

We can either initialize missing values to -1 or use:

next_greater.get(x, -1)

Step 5 — Build nums1 answer

For each value in nums1:

[next_greater.get(x, -1) for x in nums1]


---

7. Invariant

🔥 Critical invariant

> The Stack contains elements from nums2 that have not yet found their next greater element, and the Stack is maintained in decreasing order from bottom to top.



For:

[1, 3, 4, 2]

after processing 4:

stack = [4]

After processing 2:

stack = [4, 2]

Notice:

4 > 2

The Stack is decreasing.

Why?

Because if the current value is greater than the top, we keep popping until the monotonic property is restored.


---

8. Complexity

Let:

n = len(nums2)
m = len(nums1)

Time: O(n + m)

Processing nums2:

Every element is:

Pushed at most once
Popped at most once

Therefore the total Stack work is:

O(n)

Then we construct the answer for nums1:

O(m)

Total:

O(n + m)

Why isn't the while loop O(n²)?

This is critical.

Consider:

while stack and x > stack[-1]:
    stack.pop()

It looks nested, but every element can only be popped once.

So across the entire algorithm:

n pushes
+
n pops
=
2n operations

Therefore:

O(n)


---

Space: O(n)

The Stack can contain up to n elements.

The HashMap can also contain up to n mappings.

Therefore:

O(n) + O(n)
= O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Searching from nums1

The actual next-greater relationships must be discovered in:

nums2

because that's where the right-side elements exist.

Process:

nums2 → build answers
nums1 → retrieve answers


---

🚨 Trap 2 — Confusing "greater" with "greater or equal"

The problem asks for:

>

not:

>=

So equal values do not resolve an element.


---

🚨 Trap 3 — Don't pop before checking the relationship

The key condition is:

x > stack[-1]

Meaning:

Current value > unresolved value

Therefore current value becomes its answer.


---

🚨 Trap 4 — The Stack is not storing the answers

This is subtle.

The Stack contains:

unresolved elements

The HashMap contains:

resolved answers

Think:

Stack
 ↓
Who is still waiting?

HashMap
 ↓
Who already got their answer?


---

🚨 Trap 5 — Don't think "Stack = previous element"

The Stack may contain multiple unresolved elements.

Example:

[1, 2, 3]

Before 3:

stack = [2]

But after more complicated sequences, several elements can remain unresolved.

The Stack represents a set of pending requests, not simply the previous element.


---

🔹 Block 2 — Efficient Code
~~~
class Solution:
    def nextGreaterElement(self, nums1: list[int], nums2: list[int]) -> list[int]:
        stack = []
        next_greater = {}

        for num in nums2:
            while stack and num > stack[-1]:
                smaller = stack.pop()
                next_greater[smaller] = num

            stack.append(num)

        return [next_greater.get(num, -1) for num in nums1]
~~~

~~~

from typing import List

class Solution:
    def nextGreaterElement(self, nums1: List[int], nums2: List[int]) -> List[int]:
        stack = []
        greater_element = {}

        # Build mapping of next greater elements for nums2
        for num in nums2:
            while stack and num > stack[-1]:
                smaller = stack.pop()
                greater_element[smaller] = num
            stack.append(num)

        # Build result for nums1
        result = []
        for i in nums1:
            if i in greater_element:
                result.append(greater_element[i])
            else:
                result.append(-1)
        return result


~~~

Time Complexity

O(n + m)

nums2 is processed in O(n).

nums1 is converted into the final answer in O(m).

Every Stack element is pushed and popped at most once.


Space Complexity

O(n)

The Stack and HashMap can each hold up to O(n) elements.

Interview Complexity Explanation

> "I process nums2 once with a monotonic decreasing Stack. Each element is pushed once and popped at most once, so the total processing is O(n). I store each resolved next-greater relationship in a HashMap and then answer each element of nums1 in O(1), giving O(n + m) overall time and O(n) auxiliary space."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def nextGreaterElement(self, nums1: list[int], nums2: list[int]) -> list[int]:
        stack = []
        next_greater = {}

        for num in nums2:
            while stack and num > stack[-1]:
                smaller = stack.pop()
                next_greater[smaller] = num

            stack.append(num)

        return [next_greater.get(num, -1) for num in nums1]


# Example input
nums1 = [4, 1, 2]
nums2 = [1, 3, 4, 2]

# Create Solution object
solution = Solution()

# Call the method
result = solution.nextGreaterElement(nums1, nums2)

# Print output
print("nums1:", nums1)
print("nums2:", nums2)
print("Output:", result)

Output

nums1: [4, 1, 2]
nums2: [1, 3, 4, 2]
Output: [-1, 3, -1]


---

🧪 Step-by-Step Dry Run

Input:

nums2 = [1, 3, 4, 2]

Initial:

stack = []
next_greater = {}


---

Step 1 — num = 1

Stack is empty.

Push:

stack = [1]

HashMap:

{}

Meaning:

1 is still waiting for a greater element.


---

Step 2 — num = 3

Check:

3 > stack[-1]
3 > 1

True.

Therefore:

1 → 3

Pop:

smaller = 1
stack = []

Store:

next_greater[1] = 3

Then push 3:

stack = [3]

State:

next_greater = {1: 3}


---

Step 3 — num = 4

Check:

4 > 3

True.

Therefore:

3 → 4

Pop:

stack = []

Store:

next_greater = {
    1: 3,
    3: 4
}

Push 4:

stack = [4]


---

Step 4 — num = 2

Check:

2 > 4

False.

Therefore 2 cannot resolve 4.

Push:

stack = [4, 2]

Final HashMap:

{
    1: 3,
    3: 4
}

Remaining:

stack = [4, 2]

Both never found a greater element.

Therefore:

4 → -1
2 → -1


---

## Dry-Run Table

~~~
Current	Stack Before	Comparison	Action	Stack After

1	[]	—	Push 1	[1]
3	[1]	3 > 1	1 → 3, pop	[3]
4	[3]	4 > 3	3 → 4, pop	[4]
2	[4]	2 > 4 ❌	Push 2	[4, 2]

~~~
HashMap:

1 → 3
3 → 4

Now query nums1:

nums1 = [4, 1, 2]

4

next_greater[4]

doesn't exist:

→ -1

1

next_greater[1] = 3

2

Missing:

→ -1

Final:

[-1, 3, -1]


---

🔹 Block 4 — Interview Q&A

Q1. Why is a monotonic Stack better than brute force here?

Model Answer:

> "The brute-force approach repeatedly scans to the right for every element, which can take O(n²). The monotonic Stack lets the current element resolve all smaller unresolved elements immediately. Since each element is pushed and popped at most once, the total work is O(n)."




---

Q2. What exactly does the Stack contain?

Model Answer:

> "It contains elements from nums2 that have not yet found their next greater element. Because smaller elements are removed when a greater value appears, the Stack remains monotonically decreasing."




---

Q3. Why is the algorithm O(n) even though there is a while loop inside a for loop?

Model Answer:

> "The inner loop doesn't repeatedly process the same elements. Every element is pushed once and can be popped at most once. Therefore there are at most O(n) total pushes and O(n) total pops, making the overall Stack processing O(n)."




---

Q4. Why do we process nums2 instead of nums1?

Model Answer:

> "nums2 contains the complete sequence in which next-greater relationships must be discovered. Once those relationships are precomputed in a HashMap, every query from nums1 can be answered in O(1)."




---

Q5. Why is the Stack decreasing?

Model Answer:

> "When a new value is greater than the Stack's top, the top has found its next greater element and is popped. We continue popping until the new value is no longer greater than the top. Therefore values remaining in the Stack are maintained in decreasing order."




---

Q6. How would you modify this for Next Smaller Element?

Model Answer:

> "I would reverse the comparison. Instead of popping while current > stack[-1], I would pop while current < stack[-1]. The overall monotonic Stack structure and O(n) amortized complexity remain the same."




---

🧠 Pattern Extraction

Problem Clue
"Next greater element to the right"
        ↓
Pattern
Monotonic Stack
        ↓
Data Structure
Decreasing Stack
        ↓
Invariant
Stack contains unresolved elements
in decreasing order
        ↓
Core Operation

current > stack[-1]
        ↓
stack[-1] has found its answer
        ↓
POP
        ↓
answer[stack[-1]] = current
        ↓
push current


---

🔥 Master Template

Value-Based Next Greater

stack = []
answer = {}

for x in nums:

    while stack and x > stack[-1]:
        previous = stack.pop()
        answer[previous] = x

    stack.append(x)

This is the template you should memorize.

Not the LC 496 code.

The mental trigger:

"Next greater"
      ↓
Who is waiting?
      ↓
Stack
      ↓
Current > top?
      ↓
YES → resolve top
      ↓
POP
      ↓
Repeat
      ↓
PUSH current


---

## 📈 Progress Update

 ## PATTERN 3 — Monotonic Stack

#	Problem	Status

8	LC 496 — Next Greater Element I	✅ COMPLETED
9	LC 739 — Daily Temperatures	⏭️ NEXT
10	LC 503 — Next Greater Element II	🔒
11	LC 1475 — Final Prices With a Special Discount	🔒


Current mastery progression

LC 496
Basic Next Greater
      ↓
Value-based Monotonic Stack
      ↓
LC 739
Index-based Monotonic Stack
      ↓
Distance to answer
      ↓
LC 503
Circular Monotonic Stack
      ↓
LC 1475
Next Smaller
      ↓
🔥 Complete Monotonic Stack Foundation


---

🧠 Senior Pattern Recognition

When an interview problem says:

> "For every element, find the first greater element to the right."



Your brain should not immediately think:

nested loops

It should think:

NEXT GREATER
      ↓
MONOTONIC STACK
      ↓
UNRESOLVED ELEMENTS
      ↓
CURRENT ELEMENT RESOLVES THEM
      ↓
while current > stack.top
      ↓
POP + RECORD ANSWER
      ↓
PUSH CURRENT

And the critical complexity insight:

Nested-looking code
        ≠
Automatically O(n²)

because:

Each element
    ↓
1 push maximum
+
1 pop maximum
    ↓
O(n) total


---

##⚡ One-Line Takeaway

> A Monotonic Stack turns "scan right until you find something greater" into an O(n) process by keeping unresolved elements and letting each new greater value resolve them.




LC 739 — Daily Temperatures

Pattern: Index-Based Monotonic Stack — Next Greater Element + Distance
Difficulty: Medium
Interview Importance: 🔥🔥🔥 Very High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

You are given temperatures for consecutive days.

For each day, find:

> How many days do I have to wait until a warmer temperature appears?



If no warmer day exists, return 0.

Example:

temperatures = [73, 74, 75, 71, 69, 72, 76, 73]

Output:

[1, 1, 4, 2, 1, 1, 0, 0]

For example:

73 → 74

takes:

1 day

For:

75 → 76

we have:

75
↓
71
↓
69
↓
72
↓
76

So the answer is:

4


---

2. Pattern Identification

The critical clue is:

> Find the next greater element to the right.



That immediately maps to:

Next Greater Element
        ↓
Monotonic Stack

But there is an important difference from LC 496.

LC 496 asks:

> What is the greater value?



LC 739 asks:

> How far away is the greater value?



Therefore, storing only values is insufficient.

We need:

🔥 INDEX

The key transformation

Instead of:

stack = [75, 71, 69]

we store:

stack = [2, 3, 4]

where those numbers are indices.

Then if index 5 resolves index 4:

5 - 4 = 1

That's the answer.


---

3. Senior Engineer Mindset

Translate the problem:

Problem wording
      ↓
"How many days until warmer?"
      ↓
Need next greater temperature
      ↓
Need DISTANCE to next greater
      ↓
Must remember positions
      ↓
Store indices
      ↓
Monotonic decreasing Stack

The critical interview thought

When the question asks:

> "How far away is the next greater/smaller element?"



your brain should immediately ask:

> "Do I need indices instead of values?"



Usually, yes.


---

4. Brute Force / Naive Approach

For every temperature, scan forward until finding a warmer temperature.

For example:

73 → scan 74
75 → scan 71 → 69 → 72 → 76

In the worst case, each element can scan almost the entire remaining array.

Therefore:

Time = O(n²)
Space = O(1)

The problem is repeated searching.

The Monotonic Stack eliminates that repeated work.


---

5. Key Insight

🔥 The Stack stores indices of temperatures still waiting for a warmer day.

Suppose:

temperatures = [73, 74, 75, 71, 69, 72, 76]

Process from left to right.

When we see:

72

we compare it with the unresolved temperatures:

69
71

Since:

72 > 69
72 > 71

72 resolves both.

So:

69 → 72
71 → 72

Their waiting times are:

5 - 4 = 1
5 - 3 = 2

Therefore:

answer[4] = 1
answer[3] = 2

The Stack doesn't store answers.

It stores:

> indices whose answers are not known yet.




---

6. Algorithm

Initialize:

answer = [0] * len(temperatures)
stack = []

The Stack stores indices.

For each index i:

Step 1 — Current temperature

current = temperatures[i]

Step 2 — Resolve previous colder temperatures

While:

stack and temperatures[i] > temperatures[stack[-1]]

the current temperature is warmer than the temperature represented by the Stack top.

Therefore:

previous = stack.pop()

Now calculate the distance:

answer[previous] = i - previous

Step 3 — Current day becomes unresolved

Push its index:

stack.append(i)

Step 4 — Remaining indices

At the end, anything still in the Stack has no warmer day.

Those answers remain:

0

because we initialized the answer array with zeros.


---

7. Invariant

🔥 Core invariant

> The Stack contains indices of unresolved temperatures, and their corresponding temperatures are in monotonically decreasing order from bottom to top.



Example:

temperatures = [73, 74, 75, 71, 69]

After processing 69:

stack = [2, 3, 4]

Temperatures:

75, 71, 69

Therefore:

75 > 71 > 69

The Stack is decreasing.


---

8. Complexity

Let:

n = len(temperatures)

Time: O(n)

Every index is:

Pushed → at most once
Popped → at most once

Therefore the total number of Stack operations is at most:

n pushes + n pops

which is:

O(n)

The while loop does not make this O(n²).

Space: O(n)

The Stack can contain up to n indices.

The answer array also contains n values.

Therefore auxiliary Stack space is:

O(n)

and the output itself is:

O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Storing temperatures instead of indices

Wrong for this problem:

stack.append(temperature)

You need the distance:

current_index - previous_index

Therefore:

stack.append(i)


---

🚨 Trap 2 — Reversing the comparison

For next warmer temperature:

temperatures[i] > temperatures[stack[-1]]

Current must be greater than the unresolved temperature.


---

🚨 Trap 3 — Forgetting the answer is a distance

Don't store:

answer[previous] = temperatures[i]

The question asks:

How many days?

So:

answer[previous] = i - previous


---

🚨 Trap 4 — Remaining Stack elements

You don't need a separate loop to assign zero.

Because:

answer = [0] * n

already handles them.


---

🚨 Trap 5 — Equal temperatures

If:

73
73

the second 73 is not warmer.

Therefore:

current > stack_temperature

not:

current >= stack_temperature


---

🔹 Block 2 — Efficient Code
~~~
class Solution:
    def dailyTemperatures(self, temperatures: list[int]) -> list[int]:
        answer = [0] * len(temperatures)
        stack = []

        for i, temperature in enumerate(temperatures):
            while stack and temperature > temperatures[stack[-1]]:
                previous = stack.pop()
                answer[previous] = i - previous

            stack.append(i)

        return answer
~~~


~~~

class Solution:
    def dailyTemperatures(self, temperatures: list[int]) -> list[int]:
        answer = [0] * len(temperatures)   # result array initialized with 0s
        stack = []                         # stack holds indices of unresolved temps

        for i, temperature in enumerate(temperatures):
            # While current temperature is greater than the temperature at stack top
            while stack and temperature > temperatures[stack[-1]]:
                previous = stack.pop()
                answer[previous] = i - previous   # distance to next warmer day

            stack.append(i)   # push current index

        return answer


~~~
Time Complexity

O(n)

Each index enters the Stack once and leaves it at most once.

Space Complexity

O(n)

The Stack can contain up to n indices, and the answer array contains n results.

Interview Complexity Explanation

> "I use a decreasing monotonic Stack of indices. When the current temperature is greater than the temperature at the Stack's top index, the current day resolves that previous day. The difference between the indices gives the waiting time. Since every index is pushed and popped at most once, the total time is O(n), with O(n) auxiliary space."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def dailyTemperatures(self, temperatures: list[int]) -> list[int]:
        answer = [0] * len(temperatures)
        stack = []

        for i, temperature in enumerate(temperatures):
            while stack and temperature > temperatures[stack[-1]]:
                previous = stack.pop()
                answer[previous] = i - previous

            stack.append(i)

        return answer


# Example input
temperatures = [73, 74, 75, 71, 69, 72, 76, 73]

# Create Solution object
solution = Solution()

# Call the method
result = solution.dailyTemperatures(temperatures)

# Print output
print("Temperatures:", temperatures)
print("Output:", result)

Output

Temperatures: [73, 74, 75, 71, 69, 72, 76, 73]
Output: [1, 1, 4, 2, 1, 1, 0, 0]


---

🧪 Step-by-Step Dry Run

Input:

index:         0   1   2   3   4   5   6   7
temperature:  73  74  75  71  69  72  76  73

Initial:

answer = [0, 0, 0, 0, 0, 0, 0, 0]
stack = []


---

Step 1 — Index 0, temperature 73

Stack empty.

Push index:

stack = [0]

Temperature represented:

[73]

73 is waiting for a warmer day.


---

Step 2 — Index 1, temperature 74

Compare:

74 > temperatures[0]
74 > 73

Yes.

Index 0 has found its warmer day.

Calculate:

1 - 0 = 1

Therefore:

answer[0] = 1

Pop:

stack = []

Push index 1:

stack = [1]

Current answer:

[1, 0, 0, 0, 0, 0, 0, 0]


---

Step 3 — Index 2, temperature 75

Compare:

75 > 74

Yes.

Resolve index 1:

2 - 1 = 1

Therefore:

answer[1] = 1

Stack:

[]

Push 2:

stack = [2]

Answer:

[1, 1, 0, 0, 0, 0, 0, 0]


---

Step 4 — Index 3, temperature 71

Compare:

71 > 75

False.

So 75 is still waiting.

Push 3:

stack = [2, 3]

Temperatures represented:

[75, 71]

Decreasing:

75 > 71


---

Step 5 — Index 4, temperature 69

Compare:

69 > 71

False.

Push:

stack = [2, 3, 4]

Represented temperatures:

[75, 71, 69]


---

Step 6 — Index 5, temperature 72

Now something important happens.

Compare with Stack top:

72 > 69

Yes.

Index 4 is resolved.

Distance:

5 - 4 = 1

Therefore:

answer[4] = 1

Pop:

stack = [2, 3]

Now compare again.

72 > 71

Yes.

Index 3 is resolved.

Distance:

5 - 3 = 2

Therefore:

answer[3] = 2

Pop:

stack = [2]

Now compare:

72 > 75

False.

Stop popping.

Push current index:

stack = [2, 5]

Answer:

[1, 1, 0, 2, 1, 0, 0, 0]


---

Step 7 — Index 6, temperature 76

Compare:

76 > 72

Yes.

Resolve index 5:

6 - 5 = 1

Therefore:

answer[5] = 1

Pop:

stack = [2]

Compare again:

76 > 75

Yes.

Resolve index 2:

6 - 2 = 4

Therefore:

answer[2] = 4

Pop:

stack = []

Push 6:

stack = [6]

Answer:

[1, 1, 4, 2, 1, 1, 0, 0]


---

Step 8 — Index 7, temperature 73

Compare:

73 > 76

False.

Push:

stack = [6, 7]

No future day exists after index 7.

Therefore:

answer[6] = 0
answer[7] = 0

Final:

[1, 1, 4, 2, 1, 1, 0, 0]


---

🔥 Dry-Run Summary

i	Temp	Stack Before	Resolved	Answer Update	Stack After

0	73	[]	—	—	[0]
1	74	[0]	0	ans[0]=1	[1]
2	75	[1]	1	ans[1]=1	[2]
3	71	[2]	—	—	[2,3]
4	69	[2,3]	—	—	[2,3,4]
5	72	[2,3,4]	4,3	ans[4]=1, ans[3]=2	[2,5]
6	76	[2,5]	5,2	ans[5]=1, ans[2]=4	[6]
7	73	[6]	—	—	[6,7]



---

🔹 Block 4 — Interview Q&A

Q1. Why does LC 739 require an index-based Stack?

Model Answer:

> "The problem asks for the number of days until a warmer temperature, not the temperature itself. Once a warmer temperature resolves an earlier index, I calculate the distance as current_index - previous_index. Therefore the Stack must store indices."




---

Q2. What does the Stack represent?

Model Answer:

> "It contains indices of days that haven't found a warmer temperature yet. Their corresponding temperatures are maintained in decreasing order, so when a warmer temperature arrives, it can resolve one or more pending days."




---

Q3. Why do we use a decreasing monotonic Stack?

Model Answer:

> "For the next greater problem, smaller temperatures should be resolved when a larger temperature arrives. By maintaining decreasing temperatures in the Stack, the current temperature can efficiently pop every smaller unresolved temperature."




---

Q4. Why is this O(n) instead of O(n²)?

Model Answer:

> "Although there's a while loop inside the traversal, every index is pushed once and popped at most once. Therefore the total number of Stack operations is linear, giving O(n) time."




---

Q5. What happens when two consecutive temperatures are equal?

Model Answer:

> "Equal temperatures aren't warmer, so I don't pop the Stack when they are equal. The condition must be strictly current > previous."




---

Q6. How would you solve the previous problem, LC 496, differently?

Model Answer:

> "The monotonic Stack mechanism is essentially the same. The main difference is that LC 496 asks for the next greater value, so a value-based Stack and HashMap are sufficient. LC 739 asks for the distance to that greater value, so I store indices instead."




---

🧠 Pattern Extraction

Problem Clue
"How many days until a warmer temperature?"
        ↓
Next Greater Element
        ↓
Monotonic Stack
        ↓
Need DISTANCE
        ↓
Store INDICES
        ↓
Current temperature > Stack-top temperature?
        ↓
YES
        ↓
Stack-top index found its answer
        ↓
current_index - previous_index
        ↓
POP
        ↓
Repeat
        ↓
PUSH current index


---

🔥 Master Template

Index-Based Next Greater

stack = []
answer = [0] * len(nums)

for i in range(len(nums)):

    while stack and nums[i] > nums[stack[-1]]:
        previous = stack.pop()

        answer[previous] = i - previous

    stack.append(i)

The difference from LC 496

LC 496:

Stack → values
Answer → greater value

LC 739:

Stack → indices
Answer → index distance

That distinction matters.


---

📈 Progress Update

PATTERN 3 — Monotonic Stack

#	Problem	Status

8	LC 496 — Next Greater Element I	✅
9	LC 739 — Daily Temperatures	✅ COMPLETED
10	LC 503 — Next Greater Element II	⏭️ NEXT
11	LC 1475 — Final Prices With a Special Discount	🔒


Current progression

LC 496
Value-Based Next Greater
        ↓
LC 739
Index-Based Next Greater
        ↓
Distance to Answer
        ↓
LC 503
Circular Next Greater
        ↓
LC 1475
Next Smaller


---

🧠 Senior Pattern Recognition

When you see:

> "For each element, find the next greater/smaller element and tell me how far away it is."



Your mental translation should be:

Next Greater / Smaller
        ↓
Monotonic Stack
        ↓
Question asks for POSITION / DISTANCE?
        ↓
Store INDICES
        ↓
Current resolves previous?
        ↓
POP
        ↓
Distance = current_index - previous_index

And remember the fundamental rule:

> The Stack stores unresolved work; the current element resolves that work.



That is the real Monotonic Stack pattern.


---

⚡ One-Line Takeaway

> LC 739 is LC 496 with one crucial upgrade: instead of storing values because we need the greater value, store indices because we need the distance to the next greater value.

LC 503 — Next Greater Element II

Pattern: Circular Array + Index-Based Monotonic Stack
Difficulty: Medium
Interview Importance: 🔥🔥 High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

LC 503 is almost the same problem as LC 496, but with one major change:

> The array is circular.



For every element, find the first greater element while moving to the right.

If you reach the end, you are allowed to continue from the beginning.

If no greater element exists, return -1.

Example

nums = [1, 2, 1]

Think of the array as:

┌───────────────┐
        ↓               │
[1, 2, 1] → [1, 2, 1] → ...

For the first 1:

1 → 2

For 2:

2 → nothing greater
→ -1

For the last 1:

1 → wrap around → 2

Therefore:

[2, -1, 2]


---

2. Pattern Identification

The phrase:

> Next Greater Element



still means:

Next Greater
     ↓
Monotonic Stack

But now we also see:

> Circular array



That introduces the second pattern:

Circular Array
      ↓
Simulate two passes
      ↓
2 × n traversal

So the complete recognition becomes:

Next Greater
      +
Circular Array
      ↓
Index-Based Monotonic Stack
      +
Virtual second pass


---

3. Senior Engineer Mindset

Translate the problem:

Problem wording
      ↓
"Next greater element"
      ↓
Monotonic Stack
      ↓
But array is circular
      ↓
Elements can see the beginning after the end
      ↓
Need to simulate another traversal
      ↓
Process 2n positions
      ↓
Use i % n to map back to real indices

The key question in an interview

Don't immediately duplicate the array.

Ask:

> "Can I simulate the circular traversal without actually creating another array?"



Yes.

Use:

i % n

For:

i = 0 1 2 3 4 5

when:

n = 3

the real indices become:

i:       0 1 2 3 4 5
i % n:   0 1 2 0 1 2

That gives us two logical passes.


---

4. Brute Force / Naive Approach

For every element, scan forward.

If you reach the end:

wrap back to index 0

and continue.

Worst case:

O(n)

search for each of:

n elements

Therefore:

O(n²)

The circular nature makes the brute force even more repetitive.


---

5. Key Insight

🔥 The array doesn't actually need to be duplicated.

Suppose:

nums = [1, 2, 1]
n = 3

Instead of creating:

[1, 2, 1, 1, 2, 1]

we simulate:

indices:
0 1 2 3 4 5

real:
0 1 2 0 1 2

using:

index = i % n

This means:

for i in range(2 * n):
    index = i % n

Now the Monotonic Stack can behave as though it is processing the circular array.


---

6. Algorithm

Initialize:

n = len(nums)
answer = [-1] * n
stack = []

The Stack stores indices.

Why indices?

Because we're following the LC 739 pattern:

Stack → unresolved indices

Step 1 — Simulate two passes

for i in range(2 * n):

The first pass processes the original array.

The second pass gives earlier elements a chance to find a greater value after wrapping around.


---

Step 2 — Convert virtual index to real index

index = i % n


---

Step 3 — Resolve smaller elements

while stack and nums[index] > nums[stack[-1]]:

If the current value is greater than the Stack-top value:

current
   ↓
resolves
   ↓
stack top

Therefore:

previous = stack.pop()
answer[previous] = nums[index]


---

Step 4 — Push only during the first pass

This is an important detail.

We need the second pass to resolve elements, but we don't want to keep pushing duplicate indices.

So:

if i < n:
    stack.append(index)

The second traversal is primarily for resolving remaining elements.


---

7. Invariant

> The Stack contains indices whose next greater element has not yet been found, and the corresponding values are maintained in decreasing order.



During the virtual second pass:

current value
      ↓
Can it resolve stack top?
      ↓
current > nums[stack[-1]]
      ↓
POP
      ↓
Record current as answer

The Stack therefore represents:

> Unresolved requests for a greater element.




---

8. Complexity

Let:

n = len(nums)

Time: O(n)

We iterate:

2n

times.

Since:

2n = O(n)

that part is linear.

More importantly, each index is:

pushed at most once
popped at most once

So Stack operations are also:

O(n)

Therefore:

O(n) + O(n)
= O(n)

Space: O(n)

The Stack can contain at most n indices.

The answer array contains n values.

Therefore auxiliary space is:

O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Actually duplicating the array

You could do:

nums = nums + nums

but it is unnecessary.

A cleaner interview solution is:

for i in range(2 * n):
    index = i % n

You simulate circularity without allocating another array.


---

🚨 Trap 2 — Processing only n elements

If you only do:

for i in range(n):

you completely miss wrap-around answers.

Example:

[1, 2, 1]

The last 1 needs to see the first 2.

That's why we need:

2 * n

iterations.


---

🚨 Trap 3 — Pushing during both passes

Don't blindly do:

stack.append(index)

during the second pass.

You can create duplicate indices and unnecessary work.

Use:

if i < n:
    stack.append(index)


---

🚨 Trap 4 — Confusing circularity with infinite processing

We only need one additional pass.

Why?

For any element, the first possible greater element can be found within at most:

n - 1

steps around the circle.

Therefore:

2n

positions are enough.


---

🚨 Trap 5 — Equal values

Again:

>

not:

>=

Equal values aren't greater.


---

🔹 Block 2 — Efficient Code
~~~
class Solution:
    def nextGreaterElements(self, nums: list[int]) -> list[int]:
        n = len(nums)
        answer = [-1] * n
        stack = []

        for i in range(2 * n):
            index = i % n

            while stack and nums[index] > nums[stack[-1]]:
                previous = stack.pop()
                answer[previous] = nums[index]

            if i < n:
                stack.append(index)

        return answer
~~~

~~~

class Solution:
    def nextGreaterElements(self, nums: list[int]) -> list[int]:
        n = len(nums)
        answer = [-1] * n          # default: no greater element
        stack = []                 # stack holds indices

        # Traverse twice to simulate circular array
        for i in range(2 * n):
            index = i % n

            # Resolve previous indices if current num is greater
            while stack and nums[index] > nums[stack[-1]]:
                previous = stack.pop()
                answer[previous] = nums[index]

            # Only push indices from first pass
            if i < n:
                stack.append(index)

        return answer


~~~


Time Complexity

O(n)

We perform 2n iterations, which is O(n), and every index is pushed and popped at most once.

Space Complexity

O(n)

The Stack contains at most n indices, while the answer array contains n results.

Interview Complexity Explanation

> "I simulate two passes over the circular array using i % n rather than physically duplicating the array. I maintain a decreasing monotonic Stack of indices. Every index is pushed once and popped at most once, so despite the 2n traversal, the total time is O(n) and the auxiliary space is O(n)."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program

class Solution:
    def nextGreaterElements(self, nums: list[int]) -> list[int]:
        n = len(nums)
        answer = [-1] * n
        stack = []

        for i in range(2 * n):
            index = i % n

            while stack and nums[index] > nums[stack[-1]]:
                previous = stack.pop()
                answer[previous] = nums[index]

            if i < n:
                stack.append(index)

        return answer


# Example input
nums = [1, 2, 1]

# Create Solution object
solution = Solution()

# Call the method
result = solution.nextGreaterElements(nums)

# Print output
print("Input:", nums)
print("Output:", result)

Output

Input: [1, 2, 1]
Output: [2, -1, 2]


---

🧪 Step-by-Step Dry Run

Input:

nums = [1, 2, 1]

Indices:

index:  0  1  2
value:  1  2  1

Initial:

answer = [-1, -1, -1]
stack = []

Because:

n = 3

we process:

2n = 6

virtual positions.


---

Step 1 — i = 0

index = 0 % 3 = 0
nums[index] = 1

Stack empty.

Push:

stack = [0]


---

Step 2 — i = 1

index = 1 % 3 = 1
nums[index] = 2

Compare:

2 > nums[0]
2 > 1

Yes.

Therefore index 0 has found its next greater element:

answer[0] = 2

Pop:

stack = []

Push current index:

stack = [1]

Current answer:

[2, -1, -1]


---

Step 3 — i = 2

index = 2 % 3 = 2
nums[index] = 1

Compare:

1 > nums[1]
1 > 2

False.

Push:

stack = [1, 2]

Current answer:

[2, -1, -1]

At this point:

index 1 → 2

has no greater element yet.

Index 2 also has not found one.


---

🔥 Now the Circular Part Begins

Step 4 — i = 3

index = 3 % 3 = 0

We are back at:

nums[0] = 1

But this is the second logical pass.

Stack:

[1, 2]

Current:

1

Compare:

1 > nums[2]
1 > 1

False.

Compare isn't performed against index 1 because the top remains index 2.

We don't push again because:

i < n

is false.

Stack remains:

[1, 2]


---

Step 5 — i = 4

index = 4 % 3 = 1

Current:

nums[1] = 2

Stack:

[1, 2]

Top:

index 2 → value 1

Compare:

2 > 1

Yes.

So:

answer[2] = 2

Pop:

stack = [1]

Now top is:

index 1 → value 2

Compare:

2 > 2

False.

Therefore index 1 remains unresolved.

Final:

answer = [2, -1, 2]


---

Step 6 — i = 5

index = 5 % 3 = 2

Current:

nums[2] = 1

Stack:

[1]

Compare:

1 > 2

False.

Nothing changes.

Final:

[2, -1, 2]


---

🔥 Dry-Run Table

i	Real Index i % n	Value	Stack Before	Resolved	Stack After

0	0	1	[]	—	[0]
1	1	2	[0]	0 → 2	[1]
2	2	1	[1]	—	[1,2]
3	0	1	[1,2]	—	[1,2]
4	1	2	[1,2]	2 → 2	[1]
5	2	1	[1]	—	[1]


Final:

answer = [2, -1, 2]


---

🔹 Block 4 — Interview Q&A

Q1. Why do we iterate 2n times?

Model Answer:

> "Because the array is circular, an element near the end may need to search through the beginning. Two logical passes are sufficient to give every element access to all positions to its right in the circular order. We simulate those passes using i % n."




---

Q2. Why don't we physically duplicate the array?

Model Answer:

> "Duplicating the array works, but it uses additional memory and isn't necessary. I can simulate the second copy with i % n, which keeps the implementation cleaner and avoids creating another O(n) array."




---

Q3. Why do we store indices instead of values?

Model Answer:

> "The index tells us which original element is unresolved, so the answer can be stored at the correct position. It also makes the Stack representation consistent with the index-based monotonic Stack pattern from Daily Temperatures."




---

Q4. Why do we only push during the first pass?

Model Answer:

> "The second pass exists to resolve elements that didn't find a greater value during the first pass. Those indices have already been pushed, so pushing them again is unnecessary and can introduce duplicates."




---

Q5. Why is this still O(n) even though we iterate 2n times?

Model Answer:

> "2n is still O(n). Additionally, each index is pushed at most once and popped at most once. Therefore the total number of Stack operations is linear."




---

Q6. What changes if we need the next smaller element instead?

Model Answer:

> "The circular traversal remains the same, but I reverse the comparison. Instead of popping while nums[index] > nums[stack[-1]], I pop while nums[index] < nums[stack[-1]]. The monotonic Stack principle remains unchanged."




---

🧠 Pattern Extraction

Problem Clue
"Next greater element"
        ↓
Monotonic Stack
        ↓
Problem Clue
"Circular array"
        ↓
Need a second logical pass
        ↓
2n traversal
        ↓
index = i % n
        ↓
Store unresolved INDICES
        ↓
current > nums[stack[-1]]?
        ↓
POP
        ↓
Record current value
        ↓
Push during first pass


---

🔥 Master Template

Circular Next Greater — Index-Based

stack = []
answer = [-1] * n

for i in range(2 * n):
    index = i % n

    while stack and nums[index] > nums[stack[-1]]:
        previous = stack.pop()
        answer[previous] = nums[index]

    if i < n:
        stack.append(index)

Memorize the structure, not the code:

Circular?
   ↓
2n traversal
   ↓
i % n
   ↓
Monotonic Stack
   ↓
Current resolves previous?
   ↓
POP
   ↓
Record answer
   ↓
Only push original indices


---

📈 Progress Update

PATTERN 3 — Monotonic Stack

#	Problem	Status

8	LC 496 — Next Greater Element I	✅
9	LC 739 — Daily Temperatures	✅
10	LC 503 — Next Greater Element II	✅ COMPLETED
11	LC 1475 — Final Prices With a Special Discount	⏭️ NEXT


Pattern progression

LC 496
Value-Based Next Greater
        ↓
LC 739
Index-Based Next Greater
        ↓
LC 503
Circular Next Greater
        ↓
LC 1475
Next Smaller
        ↓
🔥 Monotonic Stack Foundation Complete


---

🧠 Senior Pattern Recognition

You should now be able to distinguish the three problems:

LC 496

Next Greater
+
Need VALUE
        ↓
Value-Based Stack

LC 739

Next Greater
+
Need DISTANCE
        ↓
Index-Based Stack

LC 503

Next Greater
+
Need VALUE
+
Circular
        ↓
Index-Based Monotonic Stack
+
2n traversal
+
i % n

The reusable interview trigger is:

> "Next greater + circular array" → monotonic Stack + virtual second pass.




---

⚡ One-Line Takeaway

> LC 503 adds circularity to the Next Greater pattern: simulate two passes with i % n, let the monotonic Stack keep unresolved indices, and resolve them when a greater value appears.


LC 1475 — Final Prices With a Special Discount

Pattern: Next Smaller-or-Equal + Monotonic Stack
Difficulty: Easy
Interview Importance: 🔥🔥 High for Monotonic Stack foundations

The core condition is: for each prices[i], find the first element to its right that is <= prices[i] and subtract it as the discount. 


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

For every item:

> Look to the right and find the first price that is less than or equal to the current price.



That price becomes the discount.

Example:

prices = [8, 4, 6, 2, 3]

For 8:

8 → 4

So:

8 - 4 = 4

For 4:

4 → 6 → 2
          ↑

The first price <= 4 is 2.

Therefore:

4 - 2 = 2

Final:

[4, 2, 4, 2, 3]


---

2. Pattern Identification

This is the opposite direction of what we just learned.

We've already seen:

LC 496 → Next Greater
LC 739 → Next Greater + distance
LC 503 → Circular Next Greater

Now:

LC 1475
    ↓
Next Smaller OR Equal
    ↓
Monotonic Stack

The critical clue

The statement says:

> j > i and prices[j] <= prices[i]



Translate that immediately:

To the RIGHT
      ↓
FIRST
      ↓
SMALLER OR EQUAL
      ↓
Monotonic Stack

This is the important recognition skill.


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
Find first price ≤ current price on the right
      ↓
Next Smaller-or-Equal
      ↓
Monotonic Stack
      ↓
Process from right → left
      ↓
Maintain useful candidates
      ↓
Top of stack = nearest valid discount

Notice something important:

We don't actually need the index.

Unlike LC 739, the answer isn't a distance.

We only need the discount value.

So we can use a stack of values.


---

4. Brute Force / Naive Approach

For every item, scan everything to its right:

for i in range(n):
    for j in range(i + 1, n):
        if prices[j] <= prices[i]:
            ...
            break

Worst case:

i = 0 → scan n elements
i = 1 → scan n-1
i = 2 → scan n-2
...

Total work:

n + (n-1) + (n-2) + ...

which is:

O(n²)

The monotonic Stack removes these repeated scans.


---

5. Key Insight

🔥 The Stack keeps only prices that can still become someone's future discount.

Process from right to left.

Why?

For:

prices[i]

we only care about:

i + 1 → right side

If we've already processed the right side, the Stack contains possible discounts.

Suppose:

prices = [8, 4, 6, 2, 3]

Start from the right.

For 2:

stack = [2]

Now process 6.

2 <= 6, so:

2

is the first valid discount.

Now process 4.

2 <= 4, so:

2

is also the discount.

Now process 8.

Again:

2 <= 8

so 2 would be a candidate—but careful:

The actual first smaller/equal element to the right of 8 is 4, not 2.

This is exactly why the Stack must preserve nearest useful candidates, not simply the globally smallest value.

The monotonic structure ensures the top represents the relevant nearest candidate.


---

6. Algorithm

We'll traverse from right to left.

for i in range(n - 1, -1, -1):

Maintain a monotonic Stack.

For current price:

x = prices[i]

Step 1 — Remove impossible candidates

If:

stack[-1] > x

that Stack value cannot be the discount for x.

Why?

Because x itself is closer to future elements on the left and is smaller.

So pop:

while stack and stack[-1] > x:
    stack.pop()


---

Step 2 — Check the Stack top

After removing larger values:

if stack:
    prices[i] -= stack[-1]

The Stack top is the first useful smaller-or-equal price.


---

Step 3 — Add current price

stack.append(x)

The current price now becomes a possible discount for elements to its left.


---

7. Invariant

> The Stack contains candidate discount prices in non-decreasing order from bottom to top, and the top is the nearest valid smaller-or-equal candidate for the current price.



Example:

stack = [2, 3]

This means the candidates are ordered:

2 <= 3

When a smaller value arrives, larger candidates can become irrelevant and are removed.


---

8. Complexity

Time: O(n)

We process n prices.

The while loop looks dangerous, but every price can be:

pushed → once
popped → at most once

Therefore total Stack operations are at most proportional to:

2n

So:

O(n)

Not O(n²).

Space: O(n)

In the worst case, the Stack can hold all n prices.

Therefore:

O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — It is smaller OR equal

The condition is:

prices[j] <= prices[i]

Therefore the Stack logic must preserve equal values.

Use:

while stack and stack[-1] > x:

not:

while stack and stack[-1] >= x:


---

🚨 Trap 2 — Don't confuse this with Next Greater

For Next Greater:

current > stack[-1]

For Next Smaller-or-Equal:

current >= stack[-1]

Conceptually:

Greater:
pop smaller values

Smaller:
pop larger values


---

🚨 Trap 3 — Direction matters

You can solve this from the right:

right → left

because you need information about the right side.


---

🚨 Trap 4 — Don't accidentally use the minimum value

The problem asks for the first valid price, not the smallest price.

That distinction is fundamental.


---

🔹 Block 2 — Efficient Code
~~~
class Solution:
    def finalPrices(self, prices: list[int]) -> list[int]:
        stack = []

        for i in range(len(prices) - 1, -1, -1):
            current = prices[i]

            while stack and stack[-1] > current:
                stack.pop()

            if stack:
                prices[i] -= stack[-1]

            stack.append(current)

        return prices


~~~

~~~

class Solution:
    def finalPrices(self, prices: list[int]) -> list[int]:
        stack = []   # monotonic stack (non-decreasing)

        # Traverse from right to left
        for i in range(len(prices) - 1, -1, -1):
            current = prices[i]

            # Pop all larger elements (they can’t be discounts)
            while stack and stack[-1] > current:
                stack.pop()

            # If stack has a smaller/equal element, apply discount
            if stack:
                prices[i] -= stack[-1]

            # Push current price for future comparisons
            stack.append(current)

        return prices


~~~
This reverse-traversal value-stack approach directly implements the next-smaller-or-equal pattern. 

Time Complexity

O(n)

Every price enters the Stack once and can be removed once.

Space Complexity

O(n)

The Stack can contain up to n candidate prices.

Interview Complexity Explanation

> "I traverse from right to left and maintain a monotonic Stack of candidate discount prices. Larger values than the current price are discarded because they cannot be the first smaller-or-equal candidate. Each value is pushed and popped at most once, so the total time is O(n) and auxiliary space is O(n)."




---

🔹 Block 3 — Full Code + Dry Run

Fully Runnable Python Program
~~~
class Solution:
    def finalPrices(self, prices: list[int]) -> list[int]:
        stack = []

        for i in range(len(prices) - 1, -1, -1):
            current = prices[i]

            while stack and stack[-1] > current:
                stack.pop()

            if stack:
                prices[i] -= stack[-1]

            stack.append(current)

        return prices
~~~

# Example input
prices = [8, 4, 6, 2, 3]

# Create Solution object
solution = Solution()

# Call the function
result = solution.finalPrices(prices)

# Print output
print("Original prices:", [8, 4, 6, 2, 3])
print("Final prices:", result)

Output

Original prices: [8, 4, 6, 2, 3]
Final prices: [4, 2, 4, 2, 3]


---

🧪 Step-by-Step Dry Run

Input:

index:   0  1  2  3  4
price:   8  4  6  2  3

Initial:

stack = []


---

Step 1 — Index 4

current = 3

Stack is empty.

No discount.

Push:

stack = [3]

Prices:

[8, 4, 6, 2, 3]


---

Step 2 — Index 3

current = 2

Stack:

[3]

Check:

3 > 2

Yes.

3 cannot be a valid discount for 2.

Pop:

stack = []

No discount.

Push 2:

stack = [2]

Prices remain:

[8, 4, 6, 2, 3]


---

Step 3 — Index 2

current = 6

Stack:

[2]

Check:

2 > 6

False.

Therefore:

2 <= 6

So 2 is the discount.

Calculate:

6 - 2 = 4

Prices become:

[8, 4, 4, 2, 3]

Push original 6:

stack = [2, 6]


---

Step 4 — Index 1

current = 4

Stack:

[2, 6]

Top:

2 > 4

False.

Therefore 2 is valid.

Discount:

4 - 2 = 2

Prices:

[8, 2, 4, 2, 3]

Push 4:

stack = [2, 6, 4]


---

Step 5 — Index 0

current = 8

Stack:

[2, 6, 4]

Top:

4 > 8

False.

Therefore 4 is the first smaller-or-equal candidate.

Discount:

8 - 4 = 4

Final:

[4, 2, 4, 2, 3]


---

🔥 Dry-Run Table

Index	Current	Stack Before	Action	Final Price	Stack After

4	3	[]	No discount	3	[3]
3	2	[3]	Pop 3	2	[2]
2	6	[2]	Discount 2	4	[2,6]
1	4	[2,6]	Discount 2	2	[2,6,4]
0	8	[2,6,4]	Discount 4	4	[2,6,4,8]


Final:

[4, 2, 4, 2, 3]


---

🔹 Block 4 — Interview Q&A

Q1. What pattern is LC 1475 testing?

Model Answer:

> "It's a Next Smaller-or-Equal Element problem. The discount is defined as the first element to the right whose value is less than or equal to the current value, which maps directly to a monotonic Stack."




---

Q2. Why do you traverse from right to left?

Model Answer:

> "For each item I need information from its right side. Processing from right to left means that when I reach an item, the Stack already represents useful candidates from everything to its right."




---

Q3. Why do you pop while stack[-1] > current?

Model Answer:

> "Those larger values cannot serve as a smaller-or-equal discount for the current value. More importantly, once the current smaller value is encountered, those larger candidates are no longer useful for future elements that need a closer valid candidate."




---

Q4. Why is the condition > instead of >=?

Model Answer:

> "Because equal prices are valid discounts. The problem allows prices[j] <= prices[i]. Therefore equal values must remain in the Stack."




---

Q5. Why isn't the solution O(n²) because of the while loop?

Model Answer:

> "Each price is pushed once and popped at most once. So although an individual iteration may perform multiple pops, across the entire algorithm there are only O(n) total pops."




---

Q6. How is this different from LC 739?

Model Answer:

> "LC 739 searches for the next greater temperature and needs the distance, so we store indices. LC 1475 searches for the next smaller-or-equal value and only needs the discount value, so a value-based Stack is sufficient."




---

🧠 Pattern Extraction

Problem Clue
"First price to the right <= current price"
        ↓
Next Smaller-or-Equal
        ↓
Monotonic Stack
        ↓
Need only the discount VALUE
        ↓
Value-based Stack is enough
        ↓
Process right → left
        ↓
Remove impossible larger candidates
        ↓
Stack top = nearest valid discount
        ↓
Subtract discount


---

🔥 Master Template

Next Smaller-or-Equal — Right to Left

stack = []

for i in range(len(nums) - 1, -1, -1):
    current = nums[i]

    while stack and stack[-1] > current:
        stack.pop()

    if stack:
        # stack[-1] is next smaller-or-equal
        ...

    stack.append(current)

Index-based variant

If the problem asks for position/distance, store indices:

stack = []

for i in range(n - 1, -1, -1):

    while stack and nums[stack[-1]] > nums[i]:
        stack.pop()

    if stack:
        previous = stack[-1]
        # use previous index

    stack.append(i)

This distinction is important:

Need VALUE?
    ↓
Value Stack

Need INDEX / DISTANCE?
    ↓
Index Stack


---

📈 Progress Update

PATTERN 3 — Monotonic Stack

#	Problem	Status

8	LC 496 — Next Greater Element I	✅
9	LC 739 — Daily Temperatures	✅
10	LC 503 — Next Greater Element II	✅
11	LC 1475 — Final Prices With a Special Discount	✅ COMPLETED


Pattern 3 is now complete.

LC 496
Next Greater
     ↓
LC 739
Next Greater + Index Distance
     ↓
LC 503
Circular Next Greater
     ↓
LC 1475
Next Smaller-or-Equal
     ↓
🔥 Monotonic Stack Foundation Complete


---

🧠 Senior Pattern Recognition

You now need to recognize this matrix:

Problem wording	Pattern	Direction	Stack

Next greater value	Next Greater	Usually left → right	Decreasing
Next greater distance	Next Greater + Index	Left → right	Decreasing
Next greater circular	Circular Next Greater	2 passes	Decreasing
Next smaller/equal value	Next Smaller	Right → left	Increasing


The most important recognition rule:

"First greater/smaller element"
             ↓
      MONOTONIC STACK

Then ask:

Greater or smaller?
        ↓
Value or index?
        ↓
Left/right relationship?
        ↓
Circular?
        ↓
Choose exact template.


---

⚡ One-Line Takeaway

> LC 1475 is the “Next Smaller-or-Equal” version of the Monotonic Stack: process from right to left, discard larger useless candidates, and the Stack top becomes the first valid discount.



Perfect TALARI — let’s consolidate **PATTERN 3 — Monotonic Stack: Next Greater / Smaller** into one neat package. These are the **most important stack interview problems**, and you’ve already solved them. I’ll give you each **question number, problem statement (simplified), and clean solution** in one flow.

---

## ⭐ Monotonic Stack Pattern Problems

### 🔹 LC 496 — Next Greater Element I
**Problem:**  
Given two arrays `nums1` and `nums2` (where `nums1` is a subset of `nums2`), find the next greater element for each element in `nums1` from `nums2`. If none exists, return `-1`.

**Solution:**
```python
class Solution:
    def nextGreaterElement(self, nums1: list[int], nums2: list[int]) -> list[int]:
        stack = []
        next_greater = {}

        for num in nums2:
            while stack and num > stack[-1]:
                smaller = stack.pop()
                next_greater[smaller] = num
            stack.append(num)

        return [next_greater.get(num, -1) for num in nums1]
```

---

### 🔹 LC 739 — Daily Temperatures
**Problem:**  
Given a list of daily temperatures, return a list where each element is the number of days until a warmer temperature. If none, return `0`.

**Solution:**
```python
class Solution:
    def dailyTemperatures(self, temperatures: list[int]) -> list[int]:
        answer = [0] * len(temperatures)
        stack = []

        for i, temp in enumerate(temperatures):
            while stack and temp > temperatures[stack[-1]]:
                prev = stack.pop()
                answer[prev] = i - prev
            stack.append(i)

        return answer
```

---

### 🔹 LC 503 — Next Greater Element II
**Problem:**  
Given a circular array `nums`, return the next greater element for each element. If none exists, return `-1`.

**Solution:**
```python
class Solution:
    def nextGreaterElements(self, nums: list[int]) -> list[int]:
        n = len(nums)
        answer = [-1] * n
        stack = []

        for i in range(2 * n):
            index = i % n
            while stack and nums[index] > nums[stack[-1]]:
                prev = stack.pop()
                answer[prev] = nums[index]
            if i < n:
                stack.append(index)

        return answer
```

---

### 🔹 LC 1475 — Final Prices With a Special Discount
**Problem:**  
For each price in the array, subtract the next price that is **smaller or equal** to it (to the right). If none exists, keep the price unchanged.

**Solution:**
```python
class Solution:
    def finalPrices(self, prices: list[int]) -> list[int]:
        stack = []
        for i in range(len(prices) - 1, -1, -1):
            while stack and stack[-1] > prices[i]:
                stack.pop()
            if stack:
                prices[i] -= stack[-1]
            stack.append(prices[i])
        return prices
```

---

## 🌍 TALARI Injection Summary
- **LC 496:** Next Greater Element I → monotonic stack + dictionary.  
- **LC 739:** Daily Temperatures → monotonic stack + index distance.  
- **LC 503:** Next Greater Element II → circular array + stack.  
- **LC 1475:** Final Prices → next smaller element (discount).  

All four are **canonical monotonic stack problems** — the backbone of interview prep.

---

🔥 Would you like me to also prepare a **comparison table (Problem → Stack Behavior → Key Trick)** so you can instantly see the differences between these four patterns side by side?





# Pattern 4
# 🔵 PATTERN 4 — Previous Greater / Previous Smaller

| #  | Problem                         | Main Pattern                              | Priority |
| -- | ------------------------------- | ----------------------------------------- | -------- |
| 12 | **LC 901 — Online Stock Span**  | Previous Greater                          | 🔥🔥🔥   |
| 13 | **LC 739 — Daily Temperatures** | Closely related nearest-element reasoning | 🔥🔥     |



LC 901 — Online Stock Span

Pattern: Previous Greater + Monotonic Stack + Span Compression
Difficulty: Medium
Interview Importance: 🔥🔥🔥 Very High


---

🔹 Block 1 — Senior Insights

1. Problem Simplification

Every time a new stock price arrives, we need to answer:

> How many consecutive days ending today had a price less than or equal to today's price?



Example:

prices = [100, 80, 60, 70, 60, 75, 85]

The spans are:

100 → 1
80  → 1
60  → 1
70  → 2      # 60, 70
60  → 1
75  → 4      # 60, 70, 60, 75
85  → 6      # 60, 70, 60, 75, 80, 85

Output:

[1, 1, 1, 2, 1, 4, 6]

The important word is:

> consecutive



We don't care about every previous day independently.

We care about the continuous block immediately preceding today.


---

2. Pattern Identification

The key clue is:

> "How many consecutive previous prices are less than or equal to today's price?"



Translate it:

Previous
    ↓
Greater element
    ↓
Monotonic Stack

More precisely:

Today's price
      ↓
Look LEFT
      ↓
Find nearest previous price > today
      ↓
That greater price acts as a boundary
      ↓
Span = distance from today to that boundary

Example

For:

[100, 80, 60, 70, 60, 75]

When 75 arrives:

100  80  60  70  60  75
 ↑    ↑   ↑   ↑   ↑   ↑
                     today

The previous greater price is:

80

Everything between 80 and 75 is:

60, 70, 60, 75

Therefore:

span = 4


---

3. Senior Engineer Mindset

Mental translation:

Problem wording
      ↓
"Consecutive previous prices <= today"
      ↓
Need previous greater boundary
      ↓
Monotonic decreasing Stack
      ↓
But we're processing online
      ↓
Need to preserve span information
      ↓
Store (price, span)
      ↓
When current price >= stack price
      ↓
Collapse that entire previous block
      ↓
Add its span

🔥 The senior-level insight

A naive implementation asks:

> "How many previous elements do I need to inspect?"



The monotonic Stack asks:

> "Can I remember how many elements this previous element already represents?"



That's the trick behind LC 901.


---

4. Brute Force / Naive Approach

For every incoming price:

count = 1
j = current_index - 1

while j >= 0 and prices[j] <= current_price:
    count += 1
    j -= 1

This works.

But worst case:

[10, 20, 30, 40, 50, 60, ...]

For every new price, we scan many previous prices.

Total:

1 + 2 + 3 + ... + n

Therefore:

O(n²)

For an online data structure, that's unnecessary.


---

5. Key Insight

🔥 Span Compression

Suppose we've already processed:

100 → span 1
80  → span 1
60  → span 1
70  → span 2
60  → span 1

When 75 arrives:

75 >= 60

We can consume the previous 60:

span = 1

Then:

75 >= 70

Consume the 70 block:

span = 2

Then:

75 >= 60

Consume that block:

span = 1

Now:

75 < 80

Stop.

Total:

1 + 2 + 1 = 4

We don't individually walk through those four days.

We collapse their precomputed spans.

That's the core trick.


---

6. Algorithm

We'll maintain:

stack = []

Each entry contains:

(price, span)

The Stack is maintained in strictly decreasing price order from bottom to top.

Step 1 — Start today's span

Every day counts itself:

span = 1


---

Step 2 — Remove previous prices that are <= today's price

while stack and stack[-1][0] <= price:

Why?

Because today's price can absorb that previous block.

Take:

previous_price, previous_span = stack.pop()

Then:

span += previous_span

This is the compression step.


---

Step 3 — Push today's compressed block

stack.append((price, span))


---

Step 4 — Return the span

return span


---

7. Invariant

> The Stack contains compressed blocks of previous prices in strictly decreasing price order, and each block stores how many consecutive days it represents.



Example:

stack = [
    (100, 1),
    (80, 1),
    (70, 2)
]

means:

100 → represents 1 day
80  → represents 1 day
70  → represents 2 consecutive days

When a new price arrives:

current >= stack top
        ↓
top block is absorbed
        ↓
add its span
        ↓
continue


---

8. Complexity

Time: O(n) amortized

At first glance:

while stack:

looks like it could make the algorithm O(n²).

It doesn't.

Every incoming price is:

pushed exactly once

and can be:

popped at most once

So across all calls:

n pushes + n pops

at most.

Therefore total work is:

O(n)

or O(1) amortized per next() call.

This distinction matters because LC 901 is an online problem.


---

Space: O(n)

In the worst case, prices can continuously decrease:

100, 90, 80, 70, 60

Nothing gets popped.

Therefore the Stack can contain all n entries:

O(n)


---

9. Interview Tips / Traps

🚨 Trap 1 — Use <=, not <

The problem says previous prices less than or equal to today's price.

Therefore:

stack[-1][0] <= price

must be used.

If you use <, equal prices won't be absorbed.


---

🚨 Trap 2 — Don't store only prices

If you store:

stack = [100, 80, 70]

you lose the compressed span information.

The whole point is:

(price, span)


---

🚨 Trap 3 — Don't calculate span using only Stack length

This is wrong:

span = len(stack)

because one Stack entry may represent many days.

Example:

(70, 2)

represents two days.


---

🚨 Trap 4 — This is an online data structure

Unlike LC 739 or LC 503, we don't receive the entire array first.

The API is:

next(price)

Each call must immediately return the answer.

That is why the Stack must preserve enough historical information.


---

🚨 Trap 5 — The Stack is not simply "previous greater elements"

It stores:

previous greater boundaries
+
compressed spans

That second part is what makes LC 901 different from basic previous-greater problems.


---

🔹 Block 2 — Efficient Code
~~~
class StockSpanner:

    def __init__(self):
        self.stack = []

    def next(self, price: int) -> int:
        span = 1

        while self.stack and self.stack[-1][0] <= price:
            _, previous_span = self.stack.pop()
            span += previous_span

        self.stack.append((price, span))

        return span
~~~
Time Complexity

O(1) amortized per next() call.

A single call can pop multiple elements, but each stored block can be popped only once during its lifetime.

Across n calls:

n pushes + at most n pops
= O(n)

So the amortized cost of each call is O(1).

Space Complexity

O(n) in the worst case.

A strictly decreasing sequence prevents any popping, so all n prices may remain in the Stack.

Interview Complexity Explanation

> "Each call may pop several Stack entries, but every entry was pushed once and can be popped only once. Therefore the total work across n calls is O(n), giving O(1) amortized time per call, with O(n) worst-case space."




---

🔹 Block 3 — Full Code + Dry Run
~~~
Fully Runnable Python Program

class StockSpanner:

    def __init__(self):
        self.stack = []

    def next(self, price: int) -> int:
        span = 1

        while self.stack and self.stack[-1][0] <= price:
            _, previous_span = self.stack.pop()
            span += previous_span

        self.stack.append((price, span))

        return span
~~~

# Create the StockSpanner object
spanner = StockSpanner()

# Example prices
prices = [100, 80, 60, 70, 60, 75, 85]

# Process prices one at a time
for price in prices:
    result = spanner.next(price)
    print(f"Price: {price}, Span: {result}")

Output

Price: 100, Span: 1
Price: 80, Span: 1
Price: 60, Span: 1
Price: 70, Span: 2
Price: 60, Span: 1
Price: 75, Span: 4
Price: 85, Span: 6


---

🧪 Step-by-Step Dry Run

Input stream:

100, 80, 60, 70, 60, 75, 85

Initial:

stack = []


---

Step 1 — price = 100

Start:

span = 1

Stack empty.

Push:

stack = [(100, 1)]

Return:

1


---

Step 2 — price = 80

Start:

span = 1

Stack:

[(100, 1)]

Check:

100 <= 80

False.

Push:

stack = [
    (100, 1),
    (80, 1)
]

Return:

1


---

Step 3 — price = 60

Start:

span = 1

Stack:

[(100,1), (80,1)]

Check:

80 <= 60

False.

Push:

stack = [
    (100,1),
    (80,1),
    (60,1)
]

Return:

1


---

Step 4 — price = 70

Start:

span = 1

Stack:

[(100,1), (80,1), (60,1)]

Top:

60 <= 70

Yes.

Pop:

(60,1)

Add its span:

span = 1 + 1
     = 2

Now:

stack = [
    (100,1),
    (80,1)
]

Check again:

80 <= 70

False.

Push:

stack = [
    (100,1),
    (80,1),
    (70,2)
]

Return:

2

What did we just accomplish?

The (70, 2) block represents:

60 → 70

So we've compressed two days into one Stack entry.


---

Step 5 — price = 60

Start:

span = 1

Stack:

[(100,1), (80,1), (70,2)]

Check:

70 <= 60

False.

Push:

stack = [
    (100,1),
    (80,1),
    (70,2),
    (60,1)
]

Return:

1


---

Step 6 — price = 75

Start:

span = 1

Stack:

[
    (100,1),
    (80,1),
    (70,2),
    (60,1)
]

Top:

60 <= 75

Yes.

Pop:

(60,1)

Update:

span = 1 + 1
     = 2

Stack:

[
    (100,1),
    (80,1),
    (70,2)
]

Again:

70 <= 75

Yes.

Pop:

(70,2)

This is the important compression.

We don't individually process the two days represented by 70.

We simply add:

span = 2 + 2
     = 4

Stack:

[
    (100,1),
    (80,1)
]

Again:

80 <= 75

False.

Push:

stack = [
    (100,1),
    (80,1),
    (75,4)
]

Return:

4

Why 4?

The consecutive prices are:

60, 70, 60, 75

All are:

<= 75

Therefore:

span = 4


---

Step 7 — price = 85

Start:

span = 1

Stack:

[
    (100,1),
    (80,1),
    (75,4)
]

Top:

75 <= 85

Pop:

(75,4)

Update:

span = 1 + 4
     = 5

Stack:

[
    (100,1),
    (80,1)
]

Again:

80 <= 85

Pop:

(80,1)

Update:

span = 5 + 1
     = 6

Stack:

[(100,1)]

Again:

100 <= 85

False.

Push:

stack = [
    (100,1),
    (85,6)
]

Return:

6


---

~~~
🔥 Dry-Run Table

Price	Stack Before	Pops	Span	Stack After

100	[]	—	1	[(100,1)]
80	[(100,1)]	—	1	[(100,1),(80,1)]
60	[(100,1),(80,1)]	—	1	[(100,1),(80,1),(60,1)]
70	[..., (60,1)]	(60,1)	2	[(100,1),(80,1),(70,2)]
60	[..., (70,2)]	—	1	[..., (60,1)]
75	[..., (60,1),(70,2)]	(60,1),(70,2)	4	[(100,1),(80,1),(75,4)]
85	[(100,1),(80,1),(75,4)]	(75,4),(80,1)	6	[(100,1),(85,6)]

~~~
Final spans:

[1, 1, 1, 2, 1, 4, 6]


---

🔹 Block 4 — Interview Q&A

Q1. What exactly does the Stack represent?

Model Answer:

> "The Stack contains compressed groups of previous prices. Each entry stores a price and the number of consecutive days represented by that price. The prices remain strictly decreasing from bottom to top."




---

Q2. Why do you store (price, span) instead of just price?

Model Answer:

> "Because when a new price absorbs an older Stack entry, I need to know how many days that entry already represents. Storing the span lets me merge entire groups in O(1) instead of revisiting individual days."




---

Q3. Why can we safely add the popped span to the current span?

Model Answer:

> "The popped price is less than or equal to today's price, and its stored span represents a consecutive block of days that also satisfies the condition. Therefore that entire block belongs to today's span and can be added directly."




---

Q4. Why is the algorithm O(n) despite the while loop?

Model Answer:

> "Every price is pushed onto the Stack exactly once and popped at most once. So across the entire stream there are at most n pushes and n pops. That makes the total work O(n), or O(1) amortized per next() call."




---

Q5. Why do we stop when the Stack top is greater than today's price?

Model Answer:

> "That price is the nearest previous greater boundary. Since the Stack is maintained in decreasing order, everything below it is even greater, so no earlier price can extend today's consecutive span."




---

Q6. How would you modify this for "previous strictly smaller"?

Model Answer:

> "I'd reverse the comparison. Instead of popping while stack[-1][0] <= price, I'd pop while stack[-1][0] >= price. The same span-compression technique remains valid."




---

🧠 Pattern Extraction

Problem Clue
"Consecutive previous prices <= today's price"
            ↓
Previous Greater Boundary
            ↓
Monotonic Stack
            ↓
Online input
            ↓
Store (price, span)
            ↓
Current price >= stack top?
            ↓
POP compressed block
            ↓
Add its span
            ↓
Continue
            ↓
Push (current price, total span)

🔥 The reusable trick

Previous elements
      ↓
Some have already been summarized
      ↓
Store their span
      ↓
New element absorbs them
      ↓
Add their stored spans
      ↓
No need to revisit individual elements

This is monotonic-stack compression.


---

🔥 Master Template
~~~
class OnlineStructure:

    def __init__(self):
        self.stack = []

    def next(self, value):
        span = 1

        while self.stack and self.stack[-1][0] <= value:
            _, previous_span = self.stack.pop()
            span += previous_span

        self.stack.append((value, span))

        return span
~~~
Recognition template

"Previous"
    +
"Greater"
    +
"Consecutive count/span"
    +
"Online"
        ↓
Monotonic Stack
        ↓
Store (value, compressed span)


---

📈 Progress Update

🔵 PATTERN 4 — Previous Greater / Previous Smaller

#	Problem	Pattern	Status

12	LC 901 — Online Stock Span	Previous Greater + Span Compression	✅ COMPLETED
13	LC 739 — Daily Temperatures	Related nearest-element reasoning	⏭️ NEXT


Overall Monotonic Stack progression

PATTERN 3
Next Greater / Smaller
        ↓
LC 496 ✅
LC 739 ✅
LC 503 ✅
LC 1475 ✅
        ↓
PATTERN 4
Previous Greater / Smaller
        ↓
LC 901 ✅
        ↓
LC 739 ⏭️


---

🧠 Senior Pattern Recognition

You should now recognize the difference between these two forms:

LC 739

Current temperature
       ↓
Find NEXT greater
       ↓
Need INDEX DISTANCE
       ↓
Index-based Stack

LC 901

Current price
       ↓
Find PREVIOUS greater boundary
       ↓
Need CONSECUTIVE SPAN
       ↓
Compress previous blocks
       ↓
(value, span) Stack

The deeper pattern

Nearest-element problem
        ↓
Monotonic Stack
        ↓
If repeated history is needed
        ↓
Can we compress that history?
        ↓
Store metadata with each Stack entry

That is the real interview lesson from LC 901.


---

##⚡ One-Line Takeaway

> LC 901 is not just "Previous Greater": the key trick is compressing consecutive previous elements into (price, span) so an incoming price can absorb entire historical blocks in O(1) each.





# 🔴 PATTERN 5 — Advanced Monotonic Stack

These are the problems that prove whether you've actually mastered the pattern.

| #  | LeetCode  | Problem                        | Pattern               | Priority |
| -- | --------- | ------------------------------ | --------------------- | -------- |
| 14 | **LC 84** | Largest Rectangle in Histogram | Previous/Next Smaller | 🔥🔥🔥   |
| 15 | **LC 85** | Maximal Rectangle              | Histogram + Stack     | 🔥🔥     |
| 16 | **LC 42** | Trapping Rain Water            | Monotonic Stack       | 🔥🔥     |
