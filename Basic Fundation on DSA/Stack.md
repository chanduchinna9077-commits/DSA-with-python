
# 🔴 6. STACK — 10 Problems

### Patterns

```text
LIFO
Stack simulation
Parentheses
String processing
Min/Max tracking
Monotonic stack
Next greater
Previous greater
```

### Problems

1. Implement Stack
2. Push/Pop/Peek
3. Reverse String Using Stack
4. Balanced Parentheses
5. Remove Adjacent Duplicates
6. Min Stack Concept
7. Next Greater Element
8. Previous Greater Element
9. Next Smaller Element
10. Evaluate Basic Expression

For your assessment, **1–7 are the major priority**.

---

# 🔵 STACK — CONVERSATION 1

## Problems 1–4 — 🔒 Locked TopGun Version

We’ll use the **exact locked execution flow for every problem**:

1. Problem Statement
2. Problem Theory
3. Pattern Being Tested
4. ELI10 Intuition
5. Example
6. Algorithm — Step-by-Step
7. Python Solution — Built-in Methods
8. Python Solution — Without Built-in Methods
9. Line-by-Line Explanation
10. Detailed Dry Run / Table
11. Time Complexity
12. Space Complexity
13. Edge Cases
14. Common Mistakes / Traps
15. Pattern Recognition — **When you see X → think Y**

### 🔥 STACK ROADMAP — LOCKED

|  # | Problem                     | Main Pattern       |
| -: | --------------------------- | ------------------ |
|  1 | Implement Stack             | LIFO + Array/List  |
|  2 | Push / Pop / Peek           | Stack Operations   |
|  3 | Reverse String Using Stack  | LIFO Reversal      |
|  4 | Balanced Parentheses        | Matching + Stack   |
|  5 | Remove Adjacent Duplicates  | Stack Cancellation |
|  6 | Min Stack Concept           | Auxiliary Stack    |
|  7 | Next Greater Element        | Monotonic Stack    |
|  8 | Previous Greater Element    | Monotonic Stack    |
|  9 | Next Smaller Element        | Monotonic Stack    |
| 10 | Basic Expression Evaluation | Stack + Operators  |

---

# 🔹 PROBLEM 1 — IMPLEMENT A STACK

## 1. Problem Statement

Implement a basic **Stack** using a Python list.

The stack must support:

```text
push
pop
peek
is_empty
```

Example:

```text
push(10)
push(20)
push(30)

Stack:

30 ← TOP
20
10
```

Then:

```text
pop()
```

removes:

```text
30
```

---

# 2. Problem Theory

A **Stack** is a linear data structure that follows:

$$
\boxed{\text{LIFO}}
$$

### LIFO

**Last In, First Out**

The last element inserted is the first element removed.

Think of a stack of plates:

```text
   ┌─────┐ ← Last plate placed
   │ 30  │
   ├─────┤
   │ 20  │
   ├─────┤
   │ 10  │
   └─────┘
```

You cannot easily remove `10` first.

You remove:

```text
30 → 20 → 10
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: LIFO Data Structure

Whenever you see:

> Stack / LIFO / last inserted element / undo / matching brackets

think:

```text
STACK
 ↓
LIFO
 ↓
TOP
```

For Python:

```python
stack = []
```

The **end of the list** acts as the stack top.

---

# 4. ELI10 Intuition 🧒

Imagine putting books one on top of another:

```text
Book 3 ← top
Book 2
Book 1
```

You cannot take Book 1 without first removing Book 3 and Book 2.

That's Stack.

```text
INSERT → TOP
REMOVE → TOP
```

---

# 5. Example

Start:

```text
[]
```

Push `10`:

```text
[10]
```

Push `20`:

```text
[10, 20]
```

Push `30`:

```text
[10, 20, 30]
```

Top:

```text
30
```

Pop:

```text
30 removed
```

Stack becomes:

```text
[10, 20]
```

---

# 6. Algorithm — Step-by-Step

### Push

1. Receive an element.
2. Add it to the top.

### Pop

1. Check whether stack is empty.
2. If not, remove the top element.

### Peek

1. Check whether stack is empty.
2. Return the top element without removing it.

### Is Empty

Check whether stack contains zero elements.

---

# 7. Python Solution — Using Built-in Stack Operations

Python lists already support stack behavior.

```python
stack = []

# Push
stack.append(10)
stack.append(20)
stack.append(30)

print(stack)

# Peek
print(stack[-1])

# Pop
print(stack.pop())

# Stack after pop
print(stack)
```

Output:

```text
[10, 20, 30]
30
30
[10, 20]
```

### Important

Python does not have a special basic `Stack` keyword.

A list can efficiently implement one.

---

# 8. Python Solution — Without Direct Built-in Stack Methods

For understanding the data structure itself, we can create a class.

```python
class Stack:

    def __init__(self):
        self.items = []

    def push(self, value):
        self.items.append(value)

    def pop(self):
        if len(self.items) == 0:
            return None

        value = self.items[len(self.items) - 1]
        self.items = self.items[:len(self.items) - 1]

        return value

    def peek(self):
        if len(self.items) == 0:
            return None

        return self.items[len(self.items) - 1]

    def is_empty(self):
        return len(self.items) == 0


stack = Stack()

stack.push(10)
stack.push(20)
stack.push(30)

print(stack.peek())
print(stack.pop())
print(stack.peek())
print(stack.is_empty())
```

Output:

```text
30
30
20
False
```

### Important screening note

For actual Python interview code, `append()` and `pop()` are the normal and efficient way to implement a stack. The manual version above is for **understanding the mechanics**, not because you should avoid Python's list methods in real code.

---

# 9. Line-by-Line Explanation

### Constructor

```python
def __init__(self):
    self.items = []
```

Creates an empty stack.

Initially:

```text
[]
```

---

### Push

```python
def push(self, value):
    self.items.append(value)
```

Adds the new element at the end.

```text
[10]
[10, 20]
[10, 20, 30]
```

The end represents the top.

---

### Pop

```python
if len(self.items) == 0:
    return None
```

Prevents removing from an empty stack.

This condition is called **underflow protection**.

---

```python
value = self.items[len(self.items) - 1]
```

Gets the top element.

For:

```text
[10, 20, 30]
```

length is `3`.

Last index:

```text
3 - 1 = 2
```

Therefore:

```text
items[2] = 30
```

---

### Peek

```python
return self.items[len(self.items) - 1]
```

Returns the top without removing it.

---

### Is Empty

```python
return len(self.items) == 0
```

Returns:

```text
True
```

if empty.

Otherwise:

```text
False
```

---

# 10. Detailed Dry Run

Operations:

```text
push(10)
push(20)
push(30)
peek()
pop()
peek()
```

| Operation  | Stack        | Result |
| ---------- | ------------ | ------ |
| Start      | `[]`         | —      |
| `push(10)` | `[10]`       | —      |
| `push(20)` | `[10,20]`    | —      |
| `push(30)` | `[10,20,30]` | —      |
| `peek()`   | `[10,20,30]` | `30`   |
| `pop()`    | `[10,20]`    | `30`   |
| `peek()`   | `[10,20]`    | `20`   |

---

# 11. Time Complexity

For a Python list:

| Operation |       Complexity |
| --------- | ---------------: |
| Push      | `O(1)` amortized |
| Pop       |           `O(1)` |
| Peek      |           `O(1)` |
| Is Empty  |           `O(1)` |

---

# 12. Space Complexity

For `n` elements:

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Empty stack

```text
[]
```

`pop()` should not blindly access the last element.

---

### One element

```text
[10]
```

Pop gives:

```text
10
```

and stack becomes:

```text
[]
```

---

### Multiple elements

Always remove from the top:

```text
30 → 20 → 10
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Removing from the beginning

```python
stack.pop(0)
```

This is inefficient for a Python list.

Use:

```python
stack.pop()
```

---

### ❌ Mistake 2 — Forgetting underflow

Calling:

```python
stack.pop()
```

on an empty stack raises an error.

---

### ❌ Mistake 3 — Thinking stack is FIFO

Wrong:

```text
First In → First Out
```

That's a **Queue**.

Stack:

```text
Last In → First Out
```

---

# 15. Pattern Recognition

### When you see:

> Last inserted element must come out first

Think:

$$
\boxed{\text{STACK}}
$$

and:

```text
LIFO
```

### Python mental template

```python
stack = []

stack.append(x)   # PUSH
stack.pop()       # POP
stack[-1]         # PEEK
len(stack) == 0   # EMPTY
```

---

# 🔹 PROBLEM 2 — PUSH / POP / PEEK

## 1. Problem Statement

Implement and understand the three fundamental stack operations:

```text
Push
Pop
Peek
```

Given:

```text
[10, 20, 30]
```

perform:

```text
push(40)
peek()
pop()
peek()
```

---

# 2. Problem Theory

A stack has one important access point:

```text
TOP
```

All normal operations happen at the top.

### Push

Adds to top.

```text
[10,20,30]
        ↑
       TOP

push(40)

[10,20,30,40]
           ↑
          TOP
```

### Pop

Removes top.

```text
[10,20,30,40]
           ↑
          POP

[10,20,30]
        ↑
       TOP
```

### Peek

Looks at top without removing it.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Stack API

Memorize:

```text
PUSH  → insert
POP   → remove top
PEEK  → inspect top
```

---

# 4. ELI10 Intuition 🧒

Think about a pile of plates.

### Push

Put a plate on top.

### Pop

Take the top plate away.

### Peek

Look at the top plate without taking it.

---

# 5. Example

Initial:

```text
[10, 20, 30]
```

Push `40`:

```text
[10, 20, 30, 40]
```

Peek:

```text
40
```

Stack remains:

```text
[10,20,30,40]
```

Pop:

```text
40
```

Stack becomes:

```text
[10,20,30]
```

---

# 6. Algorithm — Step-by-Step

### Push

```text
Add element at top.
```

### Pop

```text
If empty → handle underflow.
Otherwise remove top.
```

### Peek

```text
If empty → handle empty stack.
Otherwise return top.
```

---

# 7. Python Solution — Built-in List

```python
stack = [10, 20, 30]

# PUSH
stack.append(40)

# PEEK
print(stack[-1])

# POP
removed = stack.pop()

print(removed)
print(stack)
```

Output:

```text
40
40
[10, 20, 30]
```

---

# 8. Python Solution — Manual Implementation

```python
class Stack:

    def __init__(self):
        self.items = []

    def push(self, value):
        self.items.append(value)

    def pop(self):
        if len(self.items) == 0:
            return None

        last_index = len(self.items) - 1
        value = self.items[last_index]

        del self.items[last_index]

        return value

    def peek(self):
        if len(self.items) == 0:
            return None

        last_index = len(self.items) - 1

        return self.items[last_index]


stack = Stack()

stack.push(10)
stack.push(20)
stack.push(30)
stack.push(40)

print(stack.peek())
print(stack.pop())
print(stack.peek())
```

Output:

```text
40
40
30
```

---

# 9. Line-by-Line Explanation

```python
stack.push(10)
```

Stack:

```text
[10]
```

---

```python
stack.push(20)
```

Stack:

```text
[10,20]
```

---

```python
stack.push(30)
```

Stack:

```text
[10,20,30]
```

---

```python
stack.push(40)
```

Stack:

```text
[10,20,30,40]
```

Top:

```text
40
```

---

```python
stack.peek()
```

Returns:

```text
40
```

But stack remains:

```text
[10,20,30,40]
```

---

```python
stack.pop()
```

Removes:

```text
40
```

Stack becomes:

```text
[10,20,30]
```

---

# 10. Detailed Dry Run

| Step | Operation  | Stack           | Return |
| ---: | ---------- | --------------- | -----: |
|    1 | `push(10)` | `[10]`          |      — |
|    2 | `push(20)` | `[10,20]`       |      — |
|    3 | `push(30)` | `[10,20,30]`    |      — |
|    4 | `push(40)` | `[10,20,30,40]` |      — |
|    5 | `peek()`   | `[10,20,30,40]` |   `40` |
|    6 | `pop()`    | `[10,20,30]`    |   `40` |
|    7 | `peek()`   | `[10,20,30]`    |   `30` |

---

# 11. Time Complexity

```text
push → O(1)
pop  → O(1)
peek → O(1)
```

---

# 12. Space Complexity

For `n` elements:

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Peek empty stack

Should handle:

```text
[]
```

rather than blindly accessing `stack[-1]`.

### Pop empty stack

This is:

```text
Stack Underflow
```

---

# 14. Common Mistakes / Traps

### ❌ Confusing pop and peek

```text
peek → looks
pop  → removes
```

This distinction is frequently tested.

---

# 15. Pattern Recognition

Whenever you see:

```text
insert at top → push
remove top → pop
see top → peek
```

---

# 🔹 PROBLEM 3 — REVERSE A STRING USING STACK

## 1. Problem Statement

Given a string, reverse it using a stack.

### Example

```text
Input:
"hello"

Output:
"olleh"
```

---

# 2. Problem Theory

A stack follows:

```text
LIFO
```

A string reversal needs:

```text
Last character → first
Second-last → second
...
```

That's exactly what LIFO gives us.

---

# 3. Pattern Being Tested

## 🔥 Pattern: LIFO Reversal

Whenever you see:

> Reverse something using a stack

Think:

```text
Push everything
      ↓
Pop everything
      ↓
Reversed order
```

---

# 4. ELI10 Intuition 🧒

Put letters into a pile:

```text
h
e
l
l
o ← TOP
```

Now remove from top:

```text
o
l
l
e
h
```

Result:

```text
olleh
```

---

# 5. Example

Input:

```text
"CAT"
```

Push:

```text
C
A
T ← top
```

Pop:

```text
T
A
C
```

Result:

```text
"TAC"
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty stack.
2. Traverse every character.
3. Push each character.
4. Create an empty result.
5. While stack isn't empty:

   * pop the top character.
   * append it to result.
6. Return result.

---

# 7. Python Solution — Built-in Approach

Python slicing can reverse a string:

```python
text = "hello"

result = text[::-1]

print(result)
```

Output:

```text
olleh
```

But this does **not** test stack knowledge.

---

# 8. Python Solution — Using Stack

```python
def reverse_string(text):

    stack = []

    # Push characters
    for char in text:
        stack.append(char)

    result = ""

    # Pop characters
    while len(stack) > 0:
        result += stack.pop()

    return result


text = "hello"

print(reverse_string(text))
```

Output:

```text
olleh
```

---

# 9. Line-by-Line Explanation

```python
stack = []
```

Create empty stack.

---

```python
for char in text:
```

Read every character.

For:

```text
hello
```

we get:

```text
h
e
l
l
o
```

---

```python
stack.append(char)
```

Push each character.

Final stack:

```text
[h,e,l,l,o]
```

Top:

```text
o
```

---

```python
result = ""
```

Creates the final string.

---

```python
while len(stack) > 0:
```

Continue while elements remain.

---

```python
result += stack.pop()
```

Take characters from top.

Order:

```text
o
l
l
e
h
```

Therefore:

```text
olleh
```

---

# 10. Detailed Dry Run

Input:

```text
hello
```

### Push phase

| Character | Stack         |
| --------- | ------------- |
| `h`       | `[h]`         |
| `e`       | `[h,e]`       |
| `l`       | `[h,e,l]`     |
| `l`       | `[h,e,l,l]`   |
| `o`       | `[h,e,l,l,o]` |

### Pop phase

| Pop | Stack       | Result  |
| --- | ----------- | ------- |
| `o` | `[h,e,l,l]` | `o`     |
| `l` | `[h,e,l]`   | `ol`    |
| `l` | `[h,e]`     | `oll`   |
| `e` | `[h]`       | `olle`  |
| `h` | `[]`        | `olleh` |

Final:

```text
olleh
```

---

# 11. Time Complexity

Push all characters:

$$
O(n)
$$

Pop all characters:

$$
O(n)
$$

Total:

$$
\boxed{O(n)}
$$

---

# 12. Space Complexity

Stack stores all characters:

$$
\boxed{O(n)}
$$

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

### Spaces

```text
"hello world"
```

The stack reverses everything, including the space:

```text
"dlrow olleh"
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using queue logic

Queue gives FIFO.

We need LIFO.

---

### ❌ Mistake 2 — Pushing and immediately popping

If you do:

```python
stack.append(char)
stack.pop()
```

you don't build the reverse.

You need to push **everything first**, then pop.

---

# 15. Pattern Recognition

### When you see:

> Reverse using a stack

Think:

```text
PUSH ALL
   ↓
POP ALL
   ↓
REVERSED
```

---

# 🔹 PROBLEM 4 — BALANCED PARENTHESES

## 1. Problem Statement

Given a string containing:

```text
()
{}
[]
```

determine whether the brackets are balanced.

### Example 1

```text
Input:
"()"

Output:
True
```

### Example 2

```text
Input:
"({[]})"

Output:
True
```

### Example 3

```text
Input:
"([)]"

Output:
False
```

---

# 2. Problem Theory

A bracket is balanced when:

1. Every opening bracket has a closing bracket.
2. The closing bracket matches the correct type.
3. Brackets close in the correct order.

For example:

```text
({[]})
```

Opening:

```text
(
{
[
```

Then they must close in reverse:

```text
]
}
)
```

This is exactly **LIFO**.

---

# 3. Pattern Being Tested

## 🔥🔥 Pattern: Matching + Stack

This is one of the most important basic Stack interview patterns.

Whenever you see:

> Parentheses / brackets / matching / nested brackets

think:

```text
STACK
```

Why?

Because the **most recently opened bracket must close first**.

---

# 4. ELI10 Intuition 🧒

Imagine opening boxes:

```text
Box A
  Box B
    Box C
```

You must close:

```text
Box C
Box B
Box A
```

You can't close A before C.

That's:

```text
LIFO
```

Stack naturally handles this.

---

# 5. Example

Input:

```text
"{[()]}"
```

Process:

```text
{ → push
[ → push
( → push
) → matches (
] → matches [
} → matches {
```

Everything matches.

Therefore:

```text
True
```

---

# 6. Algorithm — Step-by-Step

We maintain a stack of opening brackets.

### Step 1

If character is:

```text
(
[
{
```

push it.

### Step 2

If character is closing:

```text
)
]
}
```

check:

1. Is stack empty?
2. Does the top opening bracket match?

If not:

```text
False
```

### Step 3

After processing the entire string:

```text
stack empty → True
stack not empty → False
```

---

# 7. Python Solution — Using Built-in Dictionary

```python
def is_balanced(text):

    stack = []

    pairs = {
        ')': '(',
        ']': '[',
        '}': '{'
    }

    for char in text:

        if char in "([{":
            stack.append(char)

        elif char in ")]}":

            if len(stack) == 0:
                return False

            if stack[-1] != pairs[char]:
                return False

            stack.pop()

    return len(stack) == 0


print(is_balanced("({[]})"))
print(is_balanced("([)]"))
```

Output:

```text
True
False
```

---

# 8. Python Solution — Without Dictionary

For beginner understanding, we can explicitly check each pair:

```python
def is_balanced(text):

    stack = []

    for char in text:

        if char == '(' or char == '[' or char == '{':
            stack.append(char)

        elif char == ')':

            if len(stack) == 0:
                return False

            if stack[-1] != '(':
                return False

            stack.pop()

        elif char == ']':

            if len(stack) == 0:
                return False

            if stack[-1] != '[':
                return False

            stack.pop()

        elif char == '}':

            if len(stack) == 0:
                return False

            if stack[-1] != '{':
                return False

            stack.pop()

    return len(stack) == 0


print(is_balanced("({[]})"))
```

Output:

```text
True
```

---

# 9. Line-by-Line Explanation

```python
stack = []
```

Stores opening brackets.

---

```python
if char in "([{":
```

Checks whether current character is an opening bracket.

---

```python
stack.append(char)
```

Store it because we need to match it later.

---

```python
elif char in ")]}":
```

We found a closing bracket.

---

```python
if len(stack) == 0:
    return False
```

A closing bracket without an opening bracket is invalid.

Example:

```text
")"
```

---

```python
if stack[-1] != pairs[char]:
```

Check whether the most recent opening bracket is the correct matching bracket.

Example:

```text
stack = ['(', '[']
char = ')'
```

Top:

```text
[
```

but `)` requires:

```text
(
```

Therefore:

```text
False
```

---

```python
stack.pop()
```

Matching pair found.

Remove the opening bracket.

---

```python
return len(stack) == 0
```

If anything remains, there are unmatched opening brackets.

---

# 10. Detailed Dry Run

Input:

```text
"({[]})"
```

| Character | Action          | Stack |
| --------- | --------------- | ----- |
| `(`       | Push            | `(`   |
| `{`       | Push            | `({`  |
| `[`       | Push            | `({[` |
| `]`       | Match `[` → pop | `({`  |
| `}`       | Match `{` → pop | `(`   |
| `)`       | Match `(` → pop | `[]`  |

Final stack:

```text
[]
```

Therefore:

```text
True
```

---

# 🔥 Dry Run — Invalid Example

Input:

```text
"([)]"
```

| Character | Action                      | Stack |
| --------- | --------------------------- | ----- |
| `(`       | Push                        | `(`   |
| `[`       | Push                        | `([`  |
| `)`       | Expected `(` but top is `[` | ❌     |

Immediately:

```text
False
```

This is why a simple count of brackets isn't enough.

---

# 11. Time Complexity

Every character is processed once.

$$
\boxed{O(n)}
$$

---

# 12. Space Complexity

In the worst case, all characters are opening brackets.

Therefore:

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Empty string

```text
""
```

Technically balanced:

```text
True
```

---

### Single opening bracket

```text
"("
```

Stack isn't empty:

```text
False
```

---

### Single closing bracket

```text
")"
```

No matching opening bracket:

```text
False
```

---

### Correct nesting

```text
"{[()]}"
```

→ `True`

---

### Wrong order

```text
"([)]"
```

→ `False`

---

### Different bracket types

```text
"{]"
```

→ `False`

---

# 14. Common Mistakes / Traps

## ❌ Trap 1 — Only counting brackets

For:

```text
"([)]"
```

the counts are technically:

```text
( = 1
) = 1
[ = 1
] = 1
```

But it's still invalid.

Why?

Because **order matters**.

---

## ❌ Trap 2 — Checking any opening bracket

You must check the **top**:

```python
stack[-1]
```

not any random opening bracket.

---

## ❌ Trap 3 — Forgetting final stack check

Input:

```text
"((("
```

No mismatch occurs during traversal.

But stack contains:

```text
(((
```

Therefore:

```text
False
```

---

# 15. Pattern Recognition

### When you see:

```text
parentheses
brackets
nested symbols
matching pairs
valid parentheses
```

Immediately think:

$$
\boxed{\text{STACK}}
$$

Mental algorithm:

```text
Opening → PUSH

Closing →
    stack empty? → False
    top mismatch? → False
    otherwise POP

End →
    stack empty? True
    otherwise False
```

---

# 🧠 STACK — CONVERSATION 1 MASTER PATTERN MAP

You have now learned the four fundamental Stack patterns.

### Problem 1 — Implement Stack

```text
LIFO
↓
Top
↓
Push / Pop / Peek
```

### Problem 2 — Stack Operations

```text
push → append
pop → remove top
peek → inspect top
```

### Problem 3 — Reverse String

```text
Push everything
↓
Pop everything
↓
Reverse
```

### Problem 4 — Balanced Parentheses

```text
Opening → Push
Closing → Match top + Pop
```

---

# 🔥 STACK MASTER RECOGNITION

| Question wording     | Think              |
| -------------------- | ------------------ |
| Last in, first out   | Stack              |
| Push/pop             | Stack              |
| Top element          | Stack              |
| Reverse using stack  | Push all → Pop all |
| Parentheses          | Stack              |
| Matching brackets    | Stack              |
| Nested brackets      | Stack              |
| Undo operations      | Stack concept      |
| Backtracking history | Stack concept      |

---

# 📊 TOPGUN PROGRESS

```text
ARRAYS             10/10 ✅
STRINGS            10/10 ✅
HASHING            10/10 ✅
SEARCHING          10/10 ✅
RECURSION          10/10 ✅
2D ARRAYS/MATRIX   10/10 ✅
STACK               4/10 🔵
─────────────────────────────
TOTAL              64/70
```

## 🔒 Next locked batch

### **STACK — CONVERSATION 2 → Problems 5–8**

```text
5. Remove Adjacent Duplicates
6. Min Stack Concept
7. Next Greater Element
8. Previous Greater Element
```

This batch is where Stack moves from **basic operations → actual interview patterns**, especially **monotonic stack**.

Would you like to continue with Stack Problems 5–8 next?
# 🔵 STACK — CONVERSATION 2

## Problems 5–8 — 🔒 LOCKED TOPGUN VERSION

We continue with the **same locked execution flow for every problem**:

1. Problem Statement
2. Problem Theory
3. Pattern Being Tested
4. ELI10 Intuition
5. Example
6. Algorithm — Step-by-Step
7. Python Solution — Built-in Methods
8. Python Solution — Without Built-in Methods
9. Line-by-Line Explanation
10. Detailed Dry Run / Table
11. Time Complexity
12. Space Complexity
13. Edge Cases
14. Common Mistakes / Traps
15. Pattern Recognition — **When you see X → think Y**

### 🔥 STACK ROADMAP

|     # | Problem                        | Main Pattern           |
| ----: | ------------------------------ | ---------------------- |
|     1 | Implement Stack                | LIFO + List            |
|     2 | Push / Pop / Peek              | Stack Operations       |
|     3 | Reverse String                 | LIFO Reversal          |
|     4 | Balanced Parentheses           | Matching + Stack       |
| **5** | **Remove Adjacent Duplicates** | **Stack Cancellation** |
| **6** | **Min Stack Concept**          | **Auxiliary Stack**    |
| **7** | **Next Greater Element**       | **Monotonic Stack**    |
| **8** | **Previous Greater Element**   | **Monotonic Stack**    |
|     9 | Next Smaller Element           | Monotonic Stack        |
|    10 | Basic Expression Evaluation    | Stack + Operators      |

---

# 🔹 PROBLEM 5 — REMOVE ADJACENT DUPLICATES

## 1. Problem Statement

Given a string, repeatedly remove **adjacent duplicate characters** until no adjacent duplicates remain.

### Example

```text
Input:
"abbaca"

Output:
"ca"
```

Why?

```text
abbaca
 ↑↑
remove "bb"

→ aaca

 ↑↑
remove "aa"

→ ca
```

Final:

```text
ca
```

---

# 2. Problem Theory

This problem is a perfect example of **Stack Cancellation**.

Whenever the current character is the same as the character at the top of the stack:

```text
current == stack[-1]
```

we remove the top.

Otherwise, we push the current character.

### Core idea

```text
Same as top?
    ↓
   YES → POP
    ↓
    NO → PUSH
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Stack Cancellation

This is an important pattern.

Think:

```text
current element
      ↓
compare with TOP
      ↓
same?
 ┌────┴────┐
YES       NO
 ↓         ↓
POP       PUSH
```

The stack represents the **current surviving characters**.

---

# 4. ELI10 Intuition 🧒

Imagine children standing in a line.

If two neighboring children have the same name:

```text
A B B C
  ↑ ↑
```

they cancel each other.

Now:

```text
A C
```

The stack helps us keep track of the latest surviving character.

---

# 5. Example

Input:

```text
"abbaca"
```

Process:

```text
a → push
b → push
b → top is b → pop
a → top is a → pop
c → push
a → push
```

Stack becomes:

```text
[c, a]
```

Result:

```text
"ca"
```

---

# 6. Algorithm — Step-by-Step

1. Create an empty stack.
2. Traverse each character.
3. If stack is not empty and:

   ```text
   stack[-1] == current
   ```

   then pop.
4. Otherwise push the character.
5. At the end, convert the stack into a string.
6. Return the result.

### Pseudocode

```text
stack = []

for character in string:

    if stack is not empty AND top == character:
        pop
    else:
        push character

return stack
```

---

# 7. Python Solution — Using Built-in Methods

```python
def remove_duplicates(text):

    stack = []

    for char in text:

        if stack and stack[-1] == char:
            stack.pop()
        else:
            stack.append(char)

    return "".join(stack)


print(remove_duplicates("abbaca"))
```

Output:

```text
ca
```

Here:

```python
"".join(stack)
```

converts:

```text
['c', 'a']
```

into:

```text
"ca"
```

---

# 8. Python Solution — Without Built-in Convenience

```python
def remove_duplicates(text):

    stack = []

    for char in text:

        if len(stack) > 0:

            top_index = len(stack) - 1

            if stack[top_index] == char:
                stack = stack[:top_index]
                continue

        stack.append(char)

    result = ""

    for char in stack:
        result += char

    return result


print(remove_duplicates("abbaca"))
```

Output:

```text
ca
```

### Important

The first solution is the **professional Python solution**.

The second is primarily for understanding the underlying logic without relying on `join()`.

---

# 9. Line-by-Line Explanation

```python
stack = []
```

Creates the stack.

---

```python
for char in text:
```

Process one character at a time.

---

```python
if stack and stack[-1] == char:
```

Two conditions:

1. Stack isn't empty.
2. Current character equals stack top.

For example:

```text
stack = [a, b]
char = b
```

Top:

```text
b
```

So they cancel.

---

```python
stack.pop()
```

Remove the duplicate top character.

---

```python
else:
    stack.append(char)
```

If there isn't a matching adjacent character, keep the character.

---

```python
return "".join(stack)
```

Convert the remaining stack into the final string.

---

# 10. Detailed Dry Run

Input:

```text
"abbaca"
```

| Character | Stack Before | Action  | Stack After |
| --------- | ------------ | ------- | ----------- |
| `a`       | `[]`         | Push    | `[a]`       |
| `b`       | `[a]`        | Push    | `[a,b]`     |
| `b`       | `[a,b]`      | Pop `b` | `[a]`       |
| `a`       | `[a]`        | Pop `a` | `[]`        |
| `c`       | `[]`         | Push    | `[c]`       |
| `a`       | `[c]`        | Push    | `[c,a]`     |

Final:

```text
ca
```

---

# 11. Time Complexity

Every character is pushed at most once and popped at most once.

Therefore:

$$
\boxed{O(n)}
$$

Not `O(n²)`.

Why?

Even though there is a loop containing a pop, each character can only be popped once.

---

# 12. Space Complexity

Worst case, no duplicates exist.

Example:

```text
abcdef
```

Stack contains all characters.

$$
\boxed{O(n)}
$$

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

---

### One character

```text
"a"
```

Output:

```text
"a"
```

---

### All duplicates

```text
"aaaa"
```

Process:

```text
a → push
a → pop
a → push
a → pop
```

Result:

```text
""
```

---

### No duplicates

```text
"abcde"
```

Result:

```text
"abcde"
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Comparing with the previous input character

The important comparison is:

```python
stack[-1] == char
```

not simply:

```python
text[i-1] == text[i]
```

Why?

Because after cancellation, a new adjacency can appear.

Example:

```text
abbaca
```

After removing `bb`:

```text
aaca
```

Now the two `a`s become adjacent.

The stack naturally handles this.

---

### ❌ Mistake 2 — Removing both manually

The stack already represents the surviving characters.

Only the top matching character needs to be popped.

---

# 15. Pattern Recognition

### When you see:

> Remove adjacent duplicates / cancel matching neighboring elements

Think:

$$
\boxed{\text{STACK CANCELLATION}}
$$

Mental template:

```python
for x in data:

    if stack and stack[-1] == x:
        stack.pop()
    else:
        stack.append(x)
```

---

# 🔹 PROBLEM 6 — MIN STACK CONCEPT

## 1. Problem Statement

Design a stack that supports:

```text
push(x)
pop()
top()
get_min()
```

where:

```text
get_min()
```

returns the **minimum element currently in the stack**.

Example:

```text
push(5)
push(3)
push(7)
push(2)
```

Stack:

```text
2 ← TOP
7
3
5
```

Minimum:

```text
2
```

---

# 2. Problem Theory

A normal stack can give us:

```text
top
```

in `O(1)`.

But how do we get the minimum?

A naive solution:

```python
min(stack)
```

takes:

$$
O(n)
$$

We want:

```text
get_min() → O(1)
```

### Solution

Use **two stacks**:

```text
Main Stack
Min Stack
```

The second stack keeps track of the minimum values.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Auxiliary Stack

Whenever you see:

> Stack + need another property in O(1)

think:

```text
MAIN STACK
     +
AUXILIARY STACK
```

For Min Stack:

```text
main_stack → actual elements
min_stack  → current minimum
```

---

# 4. ELI10 Intuition 🧒

Imagine a stack of numbers:

```text
5
3
7
2
```

You want to instantly know:

> "What's the smallest number?"

Instead of searching the whole stack every time, maintain a second little notebook:

```text
Minimum history
5
3
3
2
```

The top of the notebook always tells you the current minimum.

---

# 5. Example

Operations:

```text
push(5)
push(3)
push(7)
push(2)
```

Main stack:

```text
5
3
7
2
```

Min stack:

```text
5
3
3
2
```

Therefore:

```text
get_min() = 2
```

Pop `2`:

Main:

```text
5
3
7
```

Min:

```text
5
3
3
```

Now:

```text
get_min() = 3
```

---

# 6. Algorithm — Step-by-Step

## Push

When pushing `x`:

1. Push `x` into main stack.
2. If min stack is empty:

   * push `x`.
3. Otherwise:

   * compare `x` with current minimum.
   * push the smaller value into min stack.

## Pop

1. Pop from main stack.
2. Pop from min stack.

## Top

Return main stack top.

## Get Min

Return min stack top.

---

# 7. Python Solution — Using Built-in Methods

```python
class MinStack:

    def __init__(self):
        self.stack = []
        self.min_stack = []

    def push(self, value):

        self.stack.append(value)

        if len(self.min_stack) == 0:
            self.min_stack.append(value)
        else:
            current_min = self.min_stack[-1]

            if value < current_min:
                self.min_stack.append(value)
            else:
                self.min_stack.append(current_min)

    def pop(self):

        if len(self.stack) == 0:
            return None

        self.min_stack.pop()

        return self.stack.pop()

    def top(self):

        if len(self.stack) == 0:
            return None

        return self.stack[-1]

    def get_min(self):

        if len(self.min_stack) == 0:
            return None

        return self.min_stack[-1]


s = MinStack()

s.push(5)
s.push(3)
s.push(7)
s.push(2)

print(s.get_min())
print(s.pop())
print(s.get_min())
```

Output:

```text
2
2
3
```

---

# 8. Python Solution — Without `min()`

The above solution already avoids Python's `min()` function.

The important operation is:

```python
if value < current_min:
```

We manually maintain the minimum.

---

# 9. Line-by-Line Explanation

### Constructor

```python
self.stack = []
self.min_stack = []
```

Two stacks.

---

### Push

```python
self.stack.append(value)
```

Store the actual value.

---

```python
if len(self.min_stack) == 0:
```

If this is the first element.

---

```python
self.min_stack.append(value)
```

That value is automatically the minimum.

---

Otherwise:

```python
current_min = self.min_stack[-1]
```

Retrieve the previous minimum.

---

```python
if value < current_min:
    self.min_stack.append(value)
else:
    self.min_stack.append(current_min)
```

Store the **minimum so far**.

---

### Pop

```python
self.min_stack.pop()
```

Remove the minimum history corresponding to the removed element.

Then:

```python
return self.stack.pop()
```

Remove the actual value.

---

### Get Min

```python
return self.min_stack[-1]
```

The top of `min_stack` is always the current minimum.

---

# 10. Detailed Dry Run

Operations:

```text
push(5)
push(3)
push(7)
push(2)
pop()
```

### Push 5

```text
Main: [5]
Min:  [5]
```

Minimum:

```text
5
```

---

### Push 3

Compare:

```text
3 < 5
```

Yes.

```text
Main: [5,3]
Min:  [5,3]
```

Minimum:

```text
3
```

---

### Push 7

Compare:

```text
7 < 3
```

No.

Store previous minimum:

```text
Main: [5,3,7]
Min:  [5,3,3]
```

---

### Push 2

Compare:

```text
2 < 3
```

Yes.

```text
Main: [5,3,7,2]
Min:  [5,3,3,2]
```

Minimum:

```text
2
```

---

### Pop

Remove `2`.

```text
Main: [5,3,7]
Min:  [5,3,3]
```

Minimum:

```text
3
```

---

# 11. Time Complexity

| Operation | Complexity |
| --------- | ---------: |
| Push      |     `O(1)` |
| Pop       |     `O(1)` |
| Top       |     `O(1)` |
| Get Min   |     `O(1)` |

This is the key objective.

---

# 12. Space Complexity

Two stacks store up to `n` elements.

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Empty stack

`get_min()` should be handled safely.

---

### One element

```text
push(10)
```

Minimum:

```text
10
```

---

### Duplicate minimum

```text
push(2)
push(2)
```

Both minimum states should be maintained.

```text
Main: [2,2]
Min:  [2,2]
```

Pop once:

```text
Main: [2]
Min:  [2]
```

Minimum remains:

```text
2
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Calling `min(stack)` every time

```python
min(stack)
```

takes:

$$
O(n)
$$

and defeats the purpose.

---

### ❌ Mistake 2 — Only storing new minimums

Suppose:

```text
push 5
push 3
push 7
```

If `min_stack` contains only:

```text
[5,3]
```

then after popping `7`, it happens to work.

But more complicated state management becomes error-prone.

The clean beginner/interview pattern is:

```text
one min value per main-stack element
```

---

# 15. Pattern Recognition

### When you see:

> Stack + minimum/maximum must be available in O(1)

Think:

```text
MAIN STACK
+
AUXILIARY STACK
```

For Min Stack:

```text
min_stack[-1]
```

is the current minimum.

---

# 🔹 PROBLEM 7 — NEXT GREATER ELEMENT

## 1. Problem Statement

For every element in an array, find the **first greater element to its right**.

If no greater element exists, return `-1`.

### Example

```text
Input:
[4, 5, 2, 10]

Output:
[5, 10, 10, -1]
```

Explanation:

```text
4 → next greater = 5
5 → next greater = 10
2 → next greater = 10
10 → no greater element = -1
```

---

# 2. Problem Theory

This is the first major **Monotonic Stack** problem.

For every element:

> "Who is the first bigger number on my right?"

A brute-force solution checks all elements to the right.

That takes:

$$
O(n^2)
$$

We can solve it in:

$$
O(n)
$$

using a stack.

---

# 3. Pattern Being Tested

# 🔥🔥 Pattern: Monotonic Decreasing Stack

When searching for:

```text
NEXT GREATER
```

think:

```text
MONOTONIC STACK
```

We process from **right to left**.

The stack stores possible greater candidates.

---

# 4. ELI10 Intuition 🧒

Imagine standing in a line of people.

For each person, you ask:

> "Who is the first taller person to my right?"

You don't care about people who are shorter than the current person.

They cannot be the answer.

So we remove them.

That's exactly what the stack does.

---

# 5. Example

```text
[4, 5, 2, 10]
```

Start from the right.

For `10`:

```text
No one to right
→ -1
```

For `2`:

```text
10 is greater
→ 10
```

For `5`:

```text
2 is smaller → remove
10 is greater → 10
```

For `4`:

```text
2 is smaller → remove
5 is greater → 5
```

Answer:

```text
[5,10,10,-1]
```

---

# 6. Algorithm — Step-by-Step

Process from right to left.

For each element `x`:

### Step 1

While stack isn't empty and:

```text
stack[-1] <= x
```

pop it.

Why?

Because it cannot be the next greater element for `x` or earlier smaller elements.

### Step 2

If stack is empty:

```text
answer[i] = -1
```

Otherwise:

```text
answer[i] = stack[-1]
```

### Step 3

Push `x`.

---

# 7. Python Solution — Built-in List

```python
def next_greater(arr):

    n = len(arr)

    result = [-1] * n

    stack = []

    for i in range(n - 1, -1, -1):

        while stack and stack[-1] <= arr[i]:
            stack.pop()

        if stack:
            result[i] = stack[-1]

        stack.append(arr[i])

    return result


arr = [4, 5, 2, 10]

print(next_greater(arr))
```

Output:

```text
[5, 10, 10, -1]
```

---

# 8. Python Solution — Without `[-1] * n`

```python
def next_greater(arr):

    n = len(arr)

    result = []

    for i in range(n):
        result.append(-1)

    stack = []

    i = n - 1

    while i >= 0:

        while len(stack) > 0 and stack[-1] <= arr[i]:
            stack.pop()

        if len(stack) > 0:
            result[i] = stack[-1]

        stack.append(arr[i])

        i -= 1

    return result


arr = [4, 5, 2, 10]

print(next_greater(arr))
```

Output:

```text
[5, 10, 10, -1]
```

---

# 9. Line-by-Line Explanation

```python
result = [-1] * n
```

Initially assume every element has no greater element.

---

```python
for i in range(n - 1, -1, -1):
```

Process:

```text
right → left
```

---

```python
while stack and stack[-1] <= arr[i]:
```

Remove elements that are not greater than current.

---

```python
stack.pop()
```

Discard useless candidates.

---

```python
if stack:
    result[i] = stack[-1]
```

If something remains, the top is the nearest valid greater candidate.

---

```python
stack.append(arr[i])
```

Current element becomes a candidate for elements further left.

---

# 10. Detailed Dry Run

Input:

```text
[4,5,2,10]
```

### Start

```text
Stack = []
Result = [-1,-1,-1,-1]
```

---

### `10`

Stack empty.

```text
result[3] = -1
stack = [10]
```

---

### `2`

Top:

```text
10 > 2
```

So:

```text
result[2] = 10
stack = [10,2]
```

---

### `5`

Top:

```text
2 <= 5
```

Pop `2`.

```text
stack = [10]
```

Now:

```text
10 > 5
```

Therefore:

```text
result[1] = 10
```

Push `5`:

```text
stack = [10,5]
```

---

### `4`

Top:

```text
5 > 4
```

Therefore:

```text
result[0] = 5
```

Push `4`.

Final:

```text
result = [5,10,10,-1]
```

---

# 11. Time Complexity

This is the key monotonic-stack insight.

Every element:

* enters the stack once
* leaves the stack at most once

Therefore total stack operations are linear.

$$
\boxed{O(n)}
$$

Not `O(n²)`.

---

# 12. Space Complexity

Worst case stack contains all elements:

$$
\boxed{O(n)}
$$

Result array also uses `O(n)`.

Overall auxiliary/output space:

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Empty

```text
[]
```

→ `[]`

### One element

```text
[5]
```

→ `[-1]`

### Strictly increasing

```text
[1,2,3,4]
```

→

```text
[2,3,4,-1]
```

### Strictly decreasing

```text
[4,3,2,1]
```

→

```text
[-1,-1,-1,-1]
```

### Duplicates

```text
[2,2,3]
```

→

```text
[3,3,-1]
```

Because equal values are not **greater**.

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Processing left to right with the same logic

For the basic Next Greater Element pattern, the cleanest template is:

```text
right → left
```

---

### ❌ Mistake 2 — Using `<` instead of `<=`

We need **strictly greater**.

Therefore:

```python
stack[-1] <= arr[i]
```

must be removed.

---

### ❌ Mistake 3 — Thinking every stack element is a valid answer

The stack only contains useful candidates.

The while loop removes dominated elements.

---

# 15. Pattern Recognition

### When you see:

> Next Greater Element

Immediately think:

```text
MONOTONIC STACK
+
RIGHT → LEFT
+
POP smaller/equal
```

Mental template:

```python
for i in range(n - 1, -1, -1):

    while stack and stack[-1] <= arr[i]:
        stack.pop()

    if stack:
        result[i] = stack[-1]

    stack.append(arr[i])
```

🔥 **Memorize this.**

---

# 🔹 PROBLEM 8 — PREVIOUS GREATER ELEMENT

## 1. Problem Statement

For every element, find the **first greater element to its left**.

If none exists, return `-1`.

### Example

```text
Input:
[4, 5, 2, 10]

Output:
[-1, -1, 5, -1]
```

Explanation:

```text
4 → nothing greater on left → -1

5 → 4 is smaller → -1

2 → 5 is the first greater on left → 5

10 → everyone on left is smaller → -1
```

---

# 2. Problem Theory

This is closely related to Next Greater Element.

The difference:

```text
Next Greater:
look RIGHT

Previous Greater:
look LEFT
```

For Previous Greater, we can process the array:

```text
LEFT → RIGHT
```

using a monotonic stack.

---

# 3. Pattern Being Tested

## 🔥 Pattern: Previous Greater + Monotonic Stack

Think:

```text
PREVIOUS
   ↓
LEFT → RIGHT
```

And:

```text
GREATER
   ↓
remove smaller/equal candidates
```

---

# 4. ELI10 Intuition 🧒

Imagine each person asks:

> "Who was the first taller person before me?"

You maintain a stack of useful people from the left.

If someone shorter than the current person is on top, that shorter person cannot help the current person.

Remove them.

---

# 5. Example

```text
[4,5,2,10]
```

Start:

```text
stack = []
```

### 4

No previous element:

```text
-1
```

Push `4`.

---

### 5

Top `4` is smaller.

Remove it.

Nothing remains:

```text
-1
```

Push `5`.

---

### 2

Top is:

```text
5
```

and:

```text
5 > 2
```

Answer:

```text
5
```

Push `2`.

---

### 10

Top `2` smaller → pop.

Top `5` smaller → pop.

Stack empty.

Answer:

```text
-1
```

---

# 6. Algorithm — Step-by-Step

Process left to right.

For every `x`:

1. While stack isn't empty and:

   ```text
   stack[-1] <= x
   ```

   pop.
2. If stack is empty:

   ```text
   answer = -1
   ```
3. Otherwise:

   ```text
   answer = stack[-1]
   ```
4. Push `x`.

---

# 7. Python Solution — Built-in List

```python
def previous_greater(arr):

    result = [-1] * len(arr)

    stack = []

    for i in range(len(arr)):

        while stack and stack[-1] <= arr[i]:
            stack.pop()

        if stack:
            result[i] = stack[-1]

        stack.append(arr[i])

    return result


arr = [4, 5, 2, 10]

print(previous_greater(arr))
```

Output:

```text
[-1, -1, 5, -1]
```

---

# 8. Python Solution — Without Convenience Initialization

```python
def previous_greater(arr):

    result = []

    for i in range(len(arr)):
        result.append(-1)

    stack = []

    i = 0

    while i < len(arr):

        while len(stack) > 0 and stack[len(stack) - 1] <= arr[i]:
            stack.pop()

        if len(stack) > 0:
            result[i] = stack[len(stack) - 1]

        stack.append(arr[i])

        i += 1

    return result


arr = [4, 5, 2, 10]

print(previous_greater(arr))
```

Output:

```text
[-1, -1, 5, -1]
```

---

# 9. Line-by-Line Explanation

```python
result = [-1] * len(arr)
```

Assume no previous greater element initially.

---

```python
for i in range(len(arr)):
```

Process:

```text
LEFT → RIGHT
```

---

```python
while stack and stack[-1] <= arr[i]:
```

Remove smaller/equal candidates.

---

```python
stack.pop()
```

They cannot be the previous greater element for the current value.

---

```python
if stack:
    result[i] = stack[-1]
```

The remaining top is the nearest useful greater element.

---

```python
stack.append(arr[i])
```

Current value becomes a candidate for future elements.

---

# 10. Detailed Dry Run

Input:

```text
[4,5,2,10]
```

Initial:

```text
Stack = []
Result = [-1,-1,-1,-1]
```

### Element `4`

No previous:

```text
Result = [-1,-1,-1,-1]
Stack = [4]
```

---

### Element `5`

Top:

```text
4 <= 5
```

Pop.

Stack:

```text
[]
```

No greater:

```text
Result = [-1,-1,-1,-1]
```

Push:

```text
Stack = [5]
```

---

### Element `2`

Top:

```text
5 > 2
```

So:

```text
Result = [-1,-1,5,-1]
```

Push:

```text
Stack = [5,2]
```

---

### Element `10`

Top:

```text
2 <= 10
```

Pop.

Then:

```text
5 <= 10
```

Pop.

Stack:

```text
[]
```

Therefore:

```text
Result = [-1,-1,5,-1]
```

Push `10`.

Final:

```text
[-1,-1,5,-1]
```

---

# 11. Time Complexity

Each element is pushed once and popped at most once.

$$
\boxed{O(n)}
$$

---

# 12. Space Complexity

Stack + result:

$$
\boxed{O(n)}
$$

---

# 13. Edge Cases

### Empty array

```text
[]
```

→ `[]`

### One element

```text
[7]
```

→ `[-1]`

### Increasing

```text
[1,2,3,4]
```

→

```text
[-1,-1,-1,-1]
```

No previous element is greater.

### Decreasing

```text
[4,3,2,1]
```

→

```text
[-1,4,3,2]
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Using the Next Greater template unchanged

Next:

```text
RIGHT → LEFT
```

Previous:

```text
LEFT → RIGHT
```

---

### ❌ Mistake 2 — Keeping smaller values

For greater-element problems:

```python
while stack[-1] <= current:
    stack.pop()
```

Smaller/equal values are useless.

---

# 15. Pattern Recognition

### When you see:

> Previous Greater Element

Think:

```text
PREVIOUS
 ↓
LEFT → RIGHT
 ↓
MONOTONIC STACK
 ↓
POP smaller/equal
```

---

# 🧠 STACK CONVERSATION 2 — MASTER PATTERN MAP

You have now learned four significantly more important Stack patterns.

---

## 5️⃣ Remove Adjacent Duplicates

```text
Current == Stack Top
        ↓
       POP

Otherwise
        ↓
       PUSH
```

Pattern:

$$
\boxed{\text{Stack Cancellation}}
$$

---

## 6️⃣ Min Stack

```text
Main Stack
    +
Min Stack
```

Pattern:

$$
\boxed{\text{Auxiliary Stack}}
$$

Goal:

```text
get_min() → O(1)
```

---

## 7️⃣ Next Greater Element

```text
RIGHT → LEFT
```

Pattern:

$$
\boxed{\text{Monotonic Stack}}
$$

Template:

```python
for i in range(n - 1, -1, -1):

    while stack and stack[-1] <= arr[i]:
        stack.pop()

    if stack:
        result[i] = stack[-1]

    stack.append(arr[i])
```

---

## 8️⃣ Previous Greater Element

```text
LEFT → RIGHT
```

Pattern:

$$
\boxed{\text{Monotonic Stack}}
$$

Template:

```python
for i in range(n):

    while stack and stack[-1] <= arr[i]:
        stack.pop()

    if stack:
        result[i] = stack[-1]

    stack.append(arr[i])
```

---

# 🔥 CRITICAL MONOTONIC STACK RULE

You should now recognize this instantly:

```text
NEXT GREATER
        ↓
RIGHT → LEFT

PREVIOUS GREATER
        ↓
LEFT → RIGHT
```

And both use:

```text
while top <= current:
    pop
```

because smaller/equal elements cannot be the required **greater** candidate.

---

# 🎯 TOPGUN "WHEN YOU SEE X → THINK Y"

| Question wording           | Think                         |
| -------------------------- | ----------------------------- |
| Remove adjacent duplicates | Stack cancellation            |
| Current minimum in stack   | Auxiliary min stack           |
| Next greater               | Monotonic stack, right → left |
| Previous greater           | Monotonic stack, left → right |
| Parentheses                | Matching stack                |
| Reverse using stack        | Push all → pop all            |
| Last-in-first-out          | Stack                         |
| Top element                | `stack[-1]`                   |

---

# ⚠️ SENIOR SCREENING TRAPS

### Trap 1 — `pop()` is not the same as `peek()`

```text
pop  → removes
peek → only looks
```

---

### Trap 2 — Equal elements

For **strictly greater**:

```python
while stack[-1] <= current:
```

Equal values must be removed.

---

### Trap 3 — Direction

```text
NEXT     → look right
PREVIOUS → look left
```

---

### Trap 4 — Why O(n), not O(n²)?

Because in a monotonic stack:

```text
Each element:
    PUSH at most once
    POP at most once
```

Therefore:

$$
O(n+n)=O(n)
$$

This is the key reason monotonic-stack solutions are powerful.

---

# 📊 TOPGUN DSA PROGRESS

```text
ARRAYS             10/10 ✅
STRINGS            10/10 ✅
HASHING            10/10 ✅
SEARCHING          10/10 ✅
RECURSION          10/10 ✅
2D ARRAYS/MATRIX   10/10 ✅
STACK               8/10 🔵
─────────────────────────────
TOTAL              68/70 🔥
```

## 🔒 Remaining Stack Problems

### STACK — CONVERSATION 3

```text
9. Next Smaller Element
10. Basic Expression Evaluation
```

Then the final Stack mastery will include:

```text
🔥 Complete Stack Pattern Recognition
🧠 Master Templates
⚠️ Screening Traps
🎯 Stack Mini Test
📊 Final 10/10 completion
```

The next major jump is **Next Smaller + Expression Evaluation**, completing the Stack pattern family.

Would you like to continue with Stack Problems 9–10 next?

# 🟦 STACK — CONVERSATION 3

## Problems 9–10 + Complete Stack Mastery

We are continuing the **locked Stack roadmap** without reducing the depth.

### Current Stack Progress

| Problem | Topic                      | Pattern               | Status |
| ------- | -------------------------- | --------------------- | ------ |
| 1       | Implement Stack            | LIFO                  | ✅      |
| 2       | Push / Pop / Peek          | Stack Operations      | ✅      |
| 3       | Reverse String             | LIFO Reversal         | ✅      |
| 4       | Balanced Parentheses       | Matching + Stack      | ✅      |
| 5       | Remove Adjacent Duplicates | Stack Cancellation    | ✅      |
| 6       | Min Stack                  | Auxiliary Stack       | ✅      |
| 7       | Next Greater Element       | Monotonic Stack       | ✅      |
| 8       | Previous Greater Element   | Monotonic Stack       | ✅      |
| **9**   | **Next Smaller Element**   | **Monotonic Stack**   | 🔵     |
| **10**  | **Expression Evaluation**  | **Stack + Operators** | 🔵     |

---

# 🔵 PROBLEM 9 — NEXT SMALLER ELEMENT

## 1. Problem Statement

Given an array, for every element find the **first smaller element to its right**.

If there is no smaller element to the right, return `-1`.

### Example

```text
Input:
[4, 5, 2, 10]

Output:
[2, 2, -1, -1]
```

Why?

```text
4 → first smaller on right = 2
5 → first smaller on right = 2
2 → nothing smaller on right = -1
10 → nothing smaller on right = -1
```

---

# 2. Problem Theory

The brute-force approach is straightforward.

For every element:

```text
look at everything to its right
find the first smaller element
```

Example:

```text
4  5  2  10
↑
look → 5 → 2
           ↑
        smaller
```

But this can take:

```text
O(n²)
```

because every element may scan many elements.

The important interview pattern is:

> **Next Smaller → Monotonic Stack**

This reduces the solution to:

```text
O(n)
```

---

# 3. Pattern Being Tested

## 🔥 Pattern: Monotonic Stack

Specifically:

> **Next Smaller Element → scan RIGHT → LEFT + monotonic increasing stack**

We process from the right because the answer lies on the **right side**.

---

# 4. ELI10 Intuition

Imagine you are standing in a line of numbers.

For every number, you ask:

> "Who is the first person behind me who is shorter than me?"

Instead of repeatedly looking backward, we maintain a stack of useful candidates.

For:

```text
4  5  2  10
```

Start from the right:

```text
10
```

No one is behind it.

Then:

```text
2
```

10 is bigger than 2, so 10 cannot be the smaller answer for 2.

Then:

```text
5
```

2 is smaller than 5.

So:

```text
answer = 2
```

Then:

```text
4
```

2 is smaller than 4.

So:

```text
answer = 2
```

Final:

```text
[2, 2, -1, -1]
```

---

# 5. Example

```text
arr = [4, 5, 2, 10]
```

We want:

```text
4 → ?
5 → ?
2 → ?
10 → ?
```

Answers:

```text
4 → 2
5 → 2
2 → -1
10 → -1
```

Therefore:

```text
[2, 2, -1, -1]
```

---

# 6. Algorithm — Step-by-Step

This is the most important section.

### Step 1

Create result array filled with `-1`.

```python
result = [-1] * n
```

### Step 2

Create an empty stack.

```python
stack = []
```

### Step 3

Traverse from **right to left**.

```python
for i in range(n - 1, -1, -1):
```

Why?

Because we need elements on the right.

### Step 4

Remove elements that are not smaller.

```python
while stack and stack[-1] >= arr[i]:
    stack.pop()
```

Why?

We need:

```text
stack top < current element
```

So anything:

```text
>= current
```

cannot be the answer.

### Step 5

If stack is not empty:

```python
result[i] = stack[-1]
```

The top is now the nearest valid smaller candidate.

### Step 6

Push the current element.

```python
stack.append(arr[i])
```

### Core Template

```text
NEXT SMALLER

Scan → RIGHT TO LEFT

while stack and stack.top >= current:
    pop

if stack:
    answer = stack.top

push current
```

---

# 7. Python Solution — Using Built-in Methods

```python
def next_smaller(arr):
    n = len(arr)
    result = [-1] * n
    stack = []

    for i in range(n - 1, -1, -1):

        while stack and stack[-1] >= arr[i]:
            stack.pop()

        if stack:
            result[i] = stack[-1]

        stack.append(arr[i])

    return result


arr = [4, 5, 2, 10]

print(next_smaller(arr))
```

### Output

```text
[2, 2, -1, -1]
```

---

# 8. Python Solution — Without Built-in Stack Methods

For screening preparation, it is useful to understand what the stack actually does internally.

We can simulate the stack using an array and a `top` pointer.

```python
def next_smaller_manual(arr):

    n = len(arr)

    result = [-1] * n

    stack = [0] * n
    top = -1

    for i in range(n - 1, -1, -1):

        while top >= 0 and stack[top] >= arr[i]:
            top -= 1

        if top >= 0:
            result[i] = stack[top]

        top += 1
        stack[top] = arr[i]

    return result


arr = [4, 5, 2, 10]

print(next_smaller_manual(arr))
```

Output:

```text
[2, 2, -1, -1]
```

---

# 9. Line-by-Line Explanation

Consider:

```python
n = len(arr)
```

Gets the array size.

---

```python
result = [-1] * n
```

Initially assume:

> No smaller element exists.

Example:

```text
[-1, -1, -1, -1]
```

---

```python
stack = []
```

Creates our monotonic stack.

---

```python
for i in range(n - 1, -1, -1):
```

Moves:

```text
right → left
```

For:

```text
[4, 5, 2, 10]
```

Order:

```text
10 → 2 → 5 → 4
```

---

```python
while stack and stack[-1] >= arr[i]:
```

If stack top is:

```text
greater than or equal to current
```

it cannot be a smaller answer.

---

```python
stack.pop()
```

Remove useless candidate.

---

```python
if stack:
```

If a valid smaller candidate remains...

---

```python
result[i] = stack[-1]
```

The nearest valid smaller candidate becomes the answer.

---

```python
stack.append(arr[i])
```

Current element becomes a candidate for elements further left.

---

```python
return result
```

Return final answers.

---

# 10. Detailed Dry Run

Input:

```text
[4, 5, 2, 10]
```

Initial:

```text
result = [-1, -1, -1, -1]
stack = []
```

### Step 1 — `10`

```text
current = 10
stack = []
```

Nothing to remove.

No smaller element exists.

```text
result = [-1, -1, -1, -1]
stack = [10]
```

---

### Step 2 — `2`

```text
current = 2
stack = [10]
```

Check:

```text
10 >= 2
```

Yes.

Pop:

```text
stack = []
```

No candidate remains.

Therefore:

```text
result = [-1, -1, -1, -1]
```

Push 2:

```text
stack = [2]
```

---

### Step 3 — `5`

```text
current = 5
stack = [2]
```

Check:

```text
2 >= 5
```

False.

Therefore:

```text
answer = 2
```

```text
result = [-1, 2, -1, -1]
```

Push:

```text
stack = [2, 5]
```

---

### Step 4 — `4`

```text
current = 4
stack = [2, 5]
```

Check top:

```text
5 >= 4
```

Yes.

Pop:

```text
stack = [2]
```

Now:

```text
2 >= 4
```

False.

Therefore:

```text
answer = 2
```

Final:

```text
result = [2, 2, -1, -1]
```

### Dry Run Table

|  i | Current | Stack before | Popped | Answer | Stack after |
| -: | ------: | ------------ | ------ | -----: | ----------- |
|  3 |      10 | `[]`         | —      |     -1 | `[10]`      |
|  2 |       2 | `[10]`       | 10     |     -1 | `[2]`       |
|  1 |       5 | `[2]`        | —      |      2 | `[2,5]`     |
|  0 |       4 | `[2,5]`      | 5      |      2 | `[2,4]`     |

Final:

```text
[2, 2, -1, -1]
```

---

# 11. Time Complexity

```text
O(n)
```

At first this may look like:

```text
while loop inside for loop
```

and therefore:

```text
O(n²)
```

But it is **not**.

Every element:

```text
is pushed at most once
is popped at most once
```

Therefore total stack operations are proportional to `n`.

```text
Time = O(n)
```

---

# 12. Space Complexity

The stack can contain up to `n` elements.

```text
Space = O(n)
```

Result array also uses:

```text
O(n)
```

So auxiliary space remains:

```text
O(n)
```

---

# 13. Edge Cases

### Empty array

```text
[]
```

Output:

```text
[]
```

### One element

```text
[5]
```

Output:

```text
[-1]
```

### Increasing array

```text
[1, 2, 3, 4]
```

Output:

```text
[-1, -1, -1, -1]
```

### Decreasing array

```text
[4, 3, 2, 1]
```

Output:

```text
[3, 2, 1, -1]
```

### Duplicate values

```text
[5, 5, 3]
```

For strict smaller:

```text
[3, 3, -1]
```

This is why we use:

```python
>=
```

not:

```python
>
```

---

# 14. Common Mistakes / Traps

### ❌ Mistake 1 — Traversing left to right

Next means:

```text
RIGHT
```

Therefore:

```text
RIGHT → LEFT
```

---

### ❌ Mistake 2 — Wrong comparison

For **Next Smaller**:

```python
while stack and stack[-1] >= current:
```

For **Next Greater**:

```python
while stack and stack[-1] <= current:
```

Remember:

```text
Greater → remove smaller/equal
Smaller → remove greater/equal
```

---

### ❌ Mistake 3 — Using `>` instead of `>=`

For strict smaller:

```python
stack[-1] >= current
```

Equal values cannot be the answer.

---

# 15. Pattern Recognition

## 🔥 When you see:

> "Next smaller element"

Think immediately:

```text
Monotonic Stack
      ↓
Right to Left
      ↓
Pop >= current
      ↓
Stack top = answer
```

### Stack Pattern Map

```text
NEXT GREATER
→ Right to Left
→ pop <= current

NEXT SMALLER
→ Right to Left
→ pop >= current

PREVIOUS GREATER
→ Left to Right
→ pop <= current

PREVIOUS SMALLER
→ Left to Right
→ pop >= current
```

This four-pattern table is extremely important.

---

# 🟢 PROBLEM 10 — BASIC EXPRESSION EVALUATION

Now we move to the final Stack problem.

The screening-level version we will master is:

> **Evaluate a Postfix Expression using a Stack.**

This is one of the cleanest ways to understand how stacks handle operators.

---

# 1. Problem Statement

Given a postfix expression, evaluate it.

Example:

```text
"2 3 +"
```

means:

```text
2 + 3
```

Answer:

```text
5
```

Another example:

```text
"2 3 1 * +"
```

means:

```text
2 + (3 × 1)
```

Answer:

```text
5
```

---

# 2. Problem Theory

There are different ways to write expressions.

### Infix

Normal mathematical notation:

```text
2 + 3
```

### Prefix

Operator comes first:

```text
+ 2 3
```

### Postfix

Operator comes after operands:

```text
2 3 +
```

Postfix is very stack-friendly.

Why?

When we see a number:

```text
push it
```

When we see an operator:

```text
take the top two numbers
perform operation
push result
```

---

# 3. Pattern Being Tested

## 🔥 Pattern:

```text
Expression Evaluation
        ↓
Stack
        ↓
Operands → push
Operator → pop two → calculate → push result
```

This is a classic stack application.

---

# 4. ELI10 Intuition

Imagine a pile of numbers.

Expression:

```text
2 3 + 
```

First:

```text
push 2
```

Stack:

```text
[2]
```

Then:

```text
push 3
```

Stack:

```text
[2, 3]
```

Now we see:

```text
+
```

Take:

```text
3
2
```

Calculate:

```text
2 + 3 = 5
```

Put 5 back:

```text
[5]
```

Done.

---

# 5. Example

Input:

```text
"2 3 1 * +"
```

Process:

```text
2 → push
3 → push
1 → push
* → 3 × 1 = 3
+ → 2 + 3 = 5
```

Answer:

```text
5
```

---

# 6. Algorithm — Step-by-Step

### Step 1

Create an empty stack.

```python
stack = []
```

### Step 2

Read every token from left to right.

### Step 3

If token is a number:

```text
push it
```

### Step 4

If token is an operator:

```text
right = pop()
left = pop()
```

### Step 5

Perform operation.

```text
left operator right
```

### Step 6

Push the result.

### Step 7

After processing all tokens:

```text
stack[-1]
```

is the final answer.

---

# 7. Python Solution — Using Built-in Methods

```python
def evaluate_postfix(expression):
    stack = []

    tokens = expression.split()

    for token in tokens:

        if token.isdigit():
            stack.append(int(token))

        else:
            right = stack.pop()
            left = stack.pop()

            if token == "+":
                result = left + right

            elif token == "-":
                result = left - right

            elif token == "*":
                result = left * right

            elif token == "/":
                result = int(left / right)

            stack.append(result)

    return stack[-1]


expression = "2 3 1 * +"

print(evaluate_postfix(expression))
```

Output:

```text
5
```

---

# 8. Python Solution — Without Built-in Convenience Methods

We can manually scan the expression.

For a basic screening problem, assume tokens are separated by spaces.

```python
def evaluate_postfix_manual(expression):

    stack = []
    number = ""

    i = 0

    while i < len(expression):

        char = expression[i]

        if char != " ":

            if char.isdigit():
                number = ""

                while i < len(expression) and expression[i] != " ":
                    number += expression[i]
                    i += 1

                value = 0

                for digit in number:
                    value = value * 10 + (ord(digit) - ord('0'))

                stack.append(value)
                continue

            else:
                right = stack.pop()
                left = stack.pop()

                if char == "+":
                    result = left + right

                elif char == "-":
                    result = left - right

                elif char == "*":
                    result = left * right

                elif char == "/":
                    result = int(left / right)

                stack.append(result)

        i += 1

    return stack[-1]


expression = "2 3 1 * +"

print(evaluate_postfix_manual(expression))
```

Output:

```text
5
```

For the **TopGun basic screening**, the first version is the one you should remember.

---

# 9. Line-by-Line Explanation

```python
stack = []
```

Creates the operand stack.

---

```python
tokens = expression.split()
```

Converts:

```text
"2 3 1 * +"
```

into:

```text
["2", "3", "1", "*", "+"]
```

---

```python
for token in tokens:
```

Process tokens from left to right.

---

```python
if token.isdigit():
```

Check whether the token is a number.

---

```python
stack.append(int(token))
```

Push the number.

---

When we encounter an operator:

```python
right = stack.pop()
```

Take the most recent operand.

---

```python
left = stack.pop()
```

Take the operand before it.

### Critical:

For subtraction and division:

```text
left - right
left / right
```

NOT:

```text
right - left
right / left
```

---

Then:

```python
if token == "+":
```

Perform addition.

Similarly:

```python
-
*
/
```

---

```python
stack.append(result)
```

Put the result back into the stack.

---

```python
return stack[-1]
```

The final result is on top.

---

# 10. Detailed Dry Run

Expression:

```text
2 3 1 * +
```

### Initial

```text
stack = []
```

### Token `2`

Number → push.

```text
stack = [2]
```

### Token `3`

Push.

```text
stack = [2, 3]
```

### Token `1`

Push.

```text
stack = [2, 3, 1]
```

### Token `*`

Pop:

```text
right = 1
left = 3
```

Calculate:

```text
3 * 1 = 3
```

Push:

```text
stack = [2, 3]
```

### Token `+`

Pop:

```text
right = 3
left = 2
```

Calculate:

```text
2 + 3 = 5
```

Push:

```text
stack = [5]
```

Final:

```text
5
```

### Dry Run Table

| Token | Action  | Stack     |
| ----- | ------- | --------- |
| `2`   | Push    | `[2]`     |
| `3`   | Push    | `[2,3]`   |
| `1`   | Push    | `[2,3,1]` |
| `*`   | `3 × 1` | `[2,3]`   |
| `+`   | `2 + 3` | `[5]`     |

Final answer:

```text
5
```

---

# 11. Time Complexity

There are `n` tokens.

Each token is processed once.

Therefore:

```text
Time = O(n)
```

---

# 12. Space Complexity

In the worst case, the stack contains all operands.

```text
Space = O(n)
```

---

# 13. Edge Cases

### Single number

```text
"10"
```

Answer:

```text
10
```

### Addition

```text
"5 3 +"
```

Answer:

```text
8
```

### Subtraction

```text
"5 3 -"
```

Answer:

```text
2
```

Notice:

```text
5 - 3
```

not:

```text
3 - 5
```

### Multiplication

```text
"5 3 *"
```

Answer:

```text
15
```

### Division

```text
"10 2 /"
```

Answer:

```text
5
```

### Multiple operations

```text
"2 3 1 * +"
```

Answer:

```text
5
```

---

# 14. Common Mistakes / Traps

## ❌ Trap 1 — Reversing operands

Wrong:

```python
left = stack.pop()
right = stack.pop()
```

Then:

```text
left - right
```

would be wrong.

Correct:

```python
right = stack.pop()
left = stack.pop()
```

Then:

```text
left - right
```

---

## ❌ Trap 2 — Forgetting to push the result

After:

```text
3 × 4 = 12
```

we must:

```text
push 12
```

Otherwise the next operator cannot use it.

---

## ❌ Trap 3 — Treating operators like numbers

Numbers:

```text
push
```

Operators:

```text
pop → calculate → push
```

---

# 15. Pattern Recognition

When you see:

> "Evaluate postfix expression"

Immediately think:

```text
STACK
```

Then:

```text
NUMBER
→ PUSH

OPERATOR
→ POP RIGHT
→ POP LEFT
→ CALCULATE
→ PUSH RESULT
```

---

# 🟣 STACK — COMPLETE MASTER PATTERN MAP

We have now completed all **10 Stack problems**.

## Problem → Pattern

|  # | Problem                    | Core Pattern      |
| -: | -------------------------- | ----------------- |
|  1 | Implement Stack            | LIFO              |
|  2 | Push / Pop / Peek          | Stack Operations  |
|  3 | Reverse String             | LIFO Reversal     |
|  4 | Balanced Parentheses       | Matching          |
|  5 | Remove Adjacent Duplicates | Cancellation      |
|  6 | Min Stack                  | Auxiliary Stack   |
|  7 | Next Greater               | Monotonic Stack   |
|  8 | Previous Greater           | Monotonic Stack   |
|  9 | Next Smaller               | Monotonic Stack   |
| 10 | Expression Evaluation      | Stack + Operators |

---

# 🔥 THE 4 MONOTONIC STACK PATTERNS

This is the most important Stack interview memory.

| Problem              | Direction    | Pop Condition |
| -------------------- | ------------ | ------------- |
| **Next Greater**     | Right → Left | `<= current`  |
| **Next Smaller**     | Right → Left | `>= current`  |
| **Previous Greater** | Left → Right | `<= current`  |
| **Previous Smaller** | Left → Right | `>= current`  |

### Memorize this:

```text
NEXT
→ look RIGHT
→ scan RIGHT → LEFT

PREVIOUS
→ look LEFT
→ scan LEFT → RIGHT
```

And:

```text
GREATER
→ remove smaller/equal

SMALLER
→ remove greater/equal
```

---

# 🧠 STACK MASTER TEMPLATE 1 — Basic Stack

```python
stack = []

# Push
stack.append(x)

# Pop
x = stack.pop()

# Peek
top = stack[-1]

# Empty
if not stack:
    ...
```

---

# 🧠 STACK MASTER TEMPLATE 2 — Matching Brackets

```text
Opening bracket
→ PUSH

Closing bracket
→ check TOP
→ POP if matching
```

Recognition:

```text
(), {}, []
nested brackets
matching brackets
balanced parentheses
```

→ **STACK**

---

# 🧠 STACK MASTER TEMPLATE 3 — Cancellation

```python
for x in arr:

    if stack and stack[-1] == x:
        stack.pop()

    else:
        stack.append(x)
```

Recognition:

```text
remove adjacent duplicates
cancel pairs
undo neighboring elements
```

→ **STACK**

---

# 🧠 STACK MASTER TEMPLATE 4 — Monotonic Stack

```python
for i in range(...):

    while stack and CONDITION:
        stack.pop()

    if stack:
        answer[i] = stack[-1]

    stack.append(arr[i])
```

The key is the **pop condition**.

---

# 🧠 STACK MASTER TEMPLATE 5 — Expression Evaluation

```text
number
→ PUSH

operator
→ POP right
→ POP left
→ calculate
→ PUSH result
```

Recognition:

```text
postfix
expression evaluation
operators
calculator using stack
```

→ **STACK**

---

# 🚨 TOPGUN SCREENING — STACK TRAPS

These are the mistakes I would specifically watch for in a basic DSA coding assessment.

### 1. Using a queue for a LIFO problem

```text
LIFO → Stack
FIFO → Queue
```

### 2. Forgetting empty-stack checks

Before:

```python
stack[-1]
```

make sure the stack isn't empty.

### 3. Wrong monotonic comparison

Remember:

```text
Next Greater → pop <=
Next Smaller → pop >=
```

### 4. Wrong direction

```text
Next → Right → Left scan
Previous → Left → Right scan
```

### 5. Wrong expression operand order

Always:

```text
right = pop()
left = pop()

left operator right
```

---

# 🏆 STACK PATTERN RECOGNITION CHEAT SHEET

```text
LIFO
↓
STACK
```

```text
Reverse
↓
STACK
```

```text
Balanced brackets
↓
STACK
```

```text
Matching nested symbols
↓
STACK
```

```text
Adjacent cancellation
↓
STACK
```

```text
Need minimum while push/pop stays O(1)
↓
AUXILIARY STACK
```

```text
Next Greater
↓
MONOTONIC STACK
```

```text
Next Smaller
↓
MONOTONIC STACK
```

```text
Previous Greater
↓
MONOTONIC STACK
```

```text
Previous Smaller
↓
MONOTONIC STACK
```

```text
Postfix expression
↓
STACK
```

---

# 🧪 STACK MINI TEST — TOPGUN LEVEL

Try these **without looking at the answers first**.

### Q1

What data structure follows:

```text
Last In → First Out
```

### Q2

What does this do?

```python
stack.append(10)
```

### Q3

What is the output?

```python
stack = [10, 20, 30]
stack.pop()
```

### Q4

Which data structure is suitable for:

```text
([{}])
```

checking balanced brackets?

### Q5

For:

```text
[4, 5, 2, 10]
```

what is the Next Smaller Element array?

### Q6

For:

```text
[4, 5, 2, 10]
```

what is the Previous Greater Element array?

### Q7

Which direction should we scan for **Next Greater**?

### Q8

For Next Greater, what do we pop?

### Q9

Evaluate:

```text
5 3 +
```

### Q10

Evaluate:

```text
5 3 -
```

---

# ✅ MINI TEST ANSWERS

### Q1

```text
Stack
```

### Q2

```text
Push 10
```

### Q3

```text
30
```

Remaining:

```text
[10, 20]
```

### Q4

```text
Stack
```

### Q5

```text
[2, 2, -1, -1]
```

### Q6

```text
[-1, -1, 5, -1]
```

### Q7

```text
Right → Left
```

### Q8

```text
smaller/equal elements
```

```python
stack[-1] <= current
```

### Q9

```text
8
```

### Q10

```text
2
```

---

# 🟢 STACK — FINAL MASTERY STATUS

```text
STACK
│
├── Basic LIFO
│   ├── Implement Stack
│   └── Push / Pop / Peek
│
├── Stack Applications
│   ├── Reverse String
│   ├── Balanced Parentheses
│   └── Adjacent Duplicate Removal
│
├── Auxiliary Stack
│   └── Min Stack
│
├── Monotonic Stack
│   ├── Next Greater
│   ├── Previous Greater
│   └── Next Smaller
│
└── Expression Processing
    └── Postfix Evaluation
```

## 🔥 FINAL PROGRESS

```text
ARRAYS             10/10 ✅
STRINGS            10/10 ✅
HASHING            10/10 ✅
SEARCHING          10/10 ✅
RECURSION          10/10 ✅
2D ARRAYS/MATRIX   10/10 ✅
STACK              10/10 ✅
--------------------------------
TOTAL              70/70 ✅
```

**Stack is now fully covered for the locked TopGun basic-DSA track.**

The next topic in your remaining basic DSA roadmap is **Queue / Deque**, where the important patterns will be **FIFO, queue simulation, BFS, level-order traversal, and deque operations**.

Would you like to continue with Queue / Deque next, or take the Stack mini test first?


