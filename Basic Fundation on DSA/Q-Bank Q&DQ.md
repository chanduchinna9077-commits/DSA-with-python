# FINAL SYLLABUS


~~~

# 🥈 2. QUEUE / DEQUE — MUST MASTER

This is especially valuable because Queue connects directly to **BFS**, which connects to **Trees and Graphs**.

### 🔴 P0

- **LC 933 — Number of Recent Calls**
- **LC 232 — Implement Queue using Stacks**
- **LC 102 — Binary Tree Level Order Traversal**
- **LC 994 — Rotting Oranges**
- **LC 200 — Number of Islands** *(for BFS/DFS comparison)*

### 🟠 P1

- LC 239 — Sliding Window Maximum
- LC 622 — Design Circular Queue
- LC 649 — Dota2 Senate

### 🟡 P2

- LC 862 — Shortest Subarray with Sum at Least K

### 🔥 The key pattern

```text
Queue
 ↓
BFS
 ↓
Level-order
 ↓
Grid BFS
 ↓
Multi-source BFS
 ↓
Shortest unweighted path
```

So Queue should be learned **immediately before Graphs**.

---

~~~

LEVEL 1 — QUEUE
├── LC 933
├── LC 622
└── LC 225

LEVEL 2 — BASIC BFS
├── LC 1971
└── LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── LC 994
├── LC 542
└── LC 1162

LEVEL 4 — LEVEL BFS
├── LC 102
└── LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── LC 752

LEVEL 6 — STATE TRANSFORMATION BFS
├── LC 127
└── LC 433

LEVEL 7 — TREE → GRAPH
└── LC 863

LEVEL 8 — MONOTONIC DEQUE
└── LC 239 ⭐⭐⭐⭐⭐⭐

LEVEL 9 — MULTIPLE MONOTONIC DEQUES
└── LC 1438

LEVEL 10 — PREFIX + DEQUE
└── LC 862

LEVEL 11 — DP + DEQUE
└── LC 1696

~~~


Absolutely bro. We should **lock the Queue/Deque roadmap level-wise first**, exactly like the String/Hashing progression, and **only then solve each problem deeply in separate conversations**.

One important refinement: I would slightly reorganize the 18 problems into **levels based on the concept being learned**, rather than simply difficulty. That makes the progression much cleaner.

# 🟦 QUEUE / DEQUE — LOCKED LEVEL-WISE MASTER ROADMAP

## 🎯 Mission

The goal is not:

> "Solve 18 Queue problems."

The goal is:

> **Master Queue and Deque as algorithmic patterns, then recognize when BFS, Multi-Source BFS, Level BFS, State-Space BFS, or Monotonic Deque is the correct abstraction.**

The progression is:

```text
QUEUE
  ↓
QUEUE DESIGN
  ↓
BFS
  ↓
BFS + SHORTEST PATH
  ↓
GRID BFS
  ↓
MULTI-SOURCE BFS
  ↓
LEVEL-ORDER BFS
  ↓
STATE-SPACE BFS
  ↓
TREE ↔ GRAPH BFS
  ↓
DEQUE
  ↓
MONOTONIC DEQUE
  ↓
MULTIPLE DEQUES
  ↓
PREFIX SUM + DEQUE
  ↓
DP + DEQUE
```

---

# 🟢 LEVEL 1 — QUEUE FUNDAMENTALS

### Objective

Understand the Queue abstraction **before using it as a BFS engine**.

---

## 1. LC 933 — Number of Recent Calls

**Pattern:** Queue + Time Window
**Priority:** 🔥🔥🔥

### Learn

```text
Incoming event
      ↓
enqueue
      ↓
expired event?
      ↓
dequeue
```

### Core concept

**Queue as a time-ordered stream buffer.**

### Why first?

It is the cleanest introduction to:

* FIFO
* append
* remove from front
* maintaining a moving time range

---

## 2. LC 622 — Design Circular Queue

**Pattern:** Circular Queue
**Priority:** 🔥🔥

### Learn

```text
front
rear
size
capacity
wrap-around
```

Core formula:

```text
next = (index + 1) % capacity
```

### Core concept

**Queue implementation without repeatedly shifting elements.**

---

## 3. LC 225 — Implement Stack using Queues

**Pattern:** Queue-based Data Structure Design
**Priority:** 🔥

### Learn

* FIFO behavior
* abstraction
* operation transformation
* trade-offs

### Why third?

This is reinforcement of Queue mechanics rather than a major algorithmic pattern.

---

# 🟢 LEVEL 1 MASTERED

After Level 1:

```text
QUEUE
│
├── FIFO
├── Stream processing
├── Expiration
├── Circular buffer
└── Queue-based design
```

You should understand what a Queue **is**, independently of BFS.

---

# 🟡 LEVEL 2 — BASIC BFS

Now Queue becomes an algorithmic engine.

---

## 4. LC 1971 — Find if Path Exists in Graph

**Pattern:** Graph BFS
**Priority:** 🔥🔥🔥

### Learn

```text
Start
 ↓
Queue
 ↓
Explore neighbors
 ↓
Visited
 ↓
Queue next frontier
```

### Core concept

> **BFS = systematic frontier expansion.**

This is your foundational BFS problem.

---

# 🟡 LEVEL 2 — BFS + SHORTEST PATH

## 5. LC 1091 — Shortest Path in Binary Matrix

**Pattern:** Grid BFS + Shortest Path
**Priority:** 🔥🔥🔥🔥

### Learn

```text
cell = node
move = edge
queue = frontier
level = distance
```

### Core concept

> A grid is an implicit unweighted graph.

And:

> BFS finds the shortest path in an unweighted graph.

---

# 🟡 LEVEL 2 — BASIC BFS MASTERED

After:

```text
LC 1971
LC 1091
```

you should understand:

```text
Graph
 ↓
BFS
 ↓
Visited
 ↓
Queue
 ↓
Shortest distance
```

---

# 🟠 LEVEL 3 — MULTI-SOURCE BFS

This is one of the most important Queue patterns.

---

## 6. LC 994 — Rotting Oranges

**Pattern:** Multi-Source BFS
**Priority:** 🔥🔥🔥🔥🔥

### Learn

Multiple sources enter the queue initially:

```text
source 1 ─┐
source 2 ─┼──→ Queue
source 3 ─┘
```

Then:

```text
minute 0
minute 1
minute 2
...
```

### Core concept

> **All sources expand simultaneously.**

This is an absolute must-master BFS pattern.

---

## 7. LC 542 — 01 Matrix

**Pattern:** Multi-Source BFS + Distance
**Priority:** 🔥🔥🔥🔥🔥

### Learn

Instead of:

> How long until everything changes?

we ask:

> What is the distance from every cell to the nearest source?

Initialize all `0`s:

```text
all zeros
   ↓
initial queue
   ↓
BFS outward
   ↓
distance
```

### Core concept

> Multi-source BFS can compute the nearest-source distance for every node.

---

## 8. LC 1162 — As Far from Land as Possible

**Pattern:** Multi-Source BFS
**Priority:** 🔥🔥🔥

### Learn

Start from **all land cells**.

Expand toward water.

The final layer represents the farthest distance.

### Core concept

> The same Multi-Source BFS pattern can solve a farthest-distance problem by reversing the perspective.

---

# 🟠 LEVEL 3 MASTERED

You should now recognize:

```text
Multiple starting points
        ↓
Initialize queue with ALL sources
        ↓
BFS
        ↓
Level = distance
```

### Master Rule

> **If every source starts simultaneously, put every source into the queue before BFS begins.**

---

# 🟣 LEVEL 4 — LEVEL-ORDER BFS

Now we learn how Queue size represents a BFS layer.

---

## 9. LC 102 — Binary Tree Level Order Traversal

**Pattern:** Level-Order BFS
**Priority:** 🔥🔥🔥🔥🔥

Core technique:

```python
level_size = len(queue)

for _ in range(level_size):
    ...
```

### Learn

```text
Level 0
 ↓
Level 1
 ↓
Level 2
 ↓
Level 3
```

### Core concept

> **The queue contains the current frontier, and its size lets us isolate one level.**

---

## 10. LC 199 — Binary Tree Right Side View

**Pattern:** Level BFS + Boundary Selection
**Priority:** 🔥🔥

### Learn

Process one level:

```text
level
 ↓
process nodes
 ↓
identify boundary node
```

### Core concept

> Once you can isolate BFS levels, you can extract properties of each level.

---

# 🟣 LEVEL 4 MASTERED

You should now know:

```text
Queue
 ↓
BFS
 ↓
Level boundary
 ↓
level_size
 ↓
process one layer
```

This technique will repeatedly appear in:

* Trees
* Graphs
* Grid problems
* Multi-source BFS

---

# 🔴 LEVEL 5 — BFS + STATE SPACE

Now we move beyond explicitly provided graphs.

---

## 11. LC 752 — Open the Lock

**Pattern:** BFS + Implicit State Space
**Priority:** 🔥🔥🔥🔥🔥

This is a major conceptual jump.

There is no explicit adjacency list.

Instead:

```text
State = "0000"
```

Neighbors are generated by changing one wheel.

For example:

```text
0000
 ↓
0001
0010
0100
1000
...
```

### Learn

* State representation
* Neighbor generation
* Visited states
* Shortest number of moves
* Implicit graphs

### Core concept

> **A graph does not need to be explicitly given. Sometimes states themselves are nodes.**

---

# 🔴 LEVEL 6 — STATE TRANSFORMATION BFS

## 12. LC 127 — Word Ladder

**Pattern:** BFS + Implicit Graph + State Transformation
**Priority:** 🔥🔥🔥🔥🔥

This is a major interview problem.

State:

```text
word
```

Transition:

```text
change one character
```

Example:

```text
hit
 ↓
hot
 ↓
dot
 ↓
dog
 ↓
cog
```

### Learn

* Implicit graph
* Neighbor generation
* State transformation
* Visited optimization
* Shortest transformation sequence

### Core concept

> **BFS is ideal when every transformation has equal cost and we want the minimum number of transformations.**

---

## 13. LC 433 — Minimum Genetic Mutation

**Pattern:** BFS + State Transformation
**Priority:** 🔥🔥

Similar concept:

```text
state
 ↓
valid mutation
 ↓
new state
```

### Why include it?

Not because it introduces a new major pattern.

It reinforces:

> **State → valid neighbors → BFS**

This is a lower-priority reinforcement problem.

---

# 🔴 LEVEL 6 MASTERED

At this point:

```text
Explicit Graph
     ↓
Implicit Graph
     ↓
State Graph
     ↓
State Transformation
```

You should be able to recognize that a string, lock combination, mutation, configuration, etc. can be treated as a graph node.

---

# 🟤 LEVEL 7 — TREE ↔ GRAPH BFS

## 14. LC 863 — All Nodes Distance K in Binary Tree

**Pattern:** Tree → Graph + BFS
**Priority:** 🔥🔥🔥🔥

The tree normally gives:

```text
parent → child
```

But distance `K` can travel:

```text
       parent
       ↕
left ↔ node ↔ right
```

So we transform the representation:

```text
Tree
 ↓
Bidirectional Graph
 ↓
BFS from target
 ↓
Distance K
```

### Core concept

> **Sometimes the hardest part isn't BFS—the hardest part is changing the representation so BFS becomes possible.**

---

# 🟤 LEVEL 7 MASTERED

You should recognize:

```text
Tree problem
+
movement can go upward and downward
        ↓
Convert to graph
        ↓
BFS
```

---

# 🟦 LEVEL 8 — MONOTONIC DEQUE FOUNDATION

Now we make a **major conceptual transition**.

Queue/BFS was:

```text
"What should I process next?"
```

Deque problems become:

```text
"Which candidates are still useful?"
```

---

# 15. LC 239 — Sliding Window Maximum

## ⭐ ABSOLUTE MUST-MASTER

**Pattern:** Monotonic Deque
**Priority:** 🔥🔥🔥🔥🔥🔥

This is the **flagship Deque problem**.

Example:

```text
[1,3,-1,-3,5,3,6,7]
```

For every window of size `k`, find the maximum.

Naive:

```text
scan every window
```

→ `O(nk)`

Monotonic deque:

```text
O(n)
```

### Learn

* Store indices, not just values
* Expire old indices
* Remove dominated candidates
* Maintain decreasing order
* Front = maximum
* Amortized O(n)

### Core concept

> **Remove candidates that can never become the answer again.**

This is much deeper than "use deque."

---

# 🟦 LEVEL 9 — MULTIPLE MONOTONIC DEQUES

## 16. LC 1438 — Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit

**Pattern:** Sliding Window + Two Monotonic Deques
**Priority:** 🔥🔥🔥🔥🔥

Maintain:

```text
maxDeque
minDeque
```

Invariant:

```text
maximum - minimum <= limit
```

If invalid:

```text
left += 1
```

### Learn

* Increasing deque
* Decreasing deque
* Window expiration
* Simultaneous state maintenance
* Variable Sliding Window + Deque

### Core concept

> **Two different monotonic structures can maintain two different properties of the same window.**

---

# 🟦 LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE

## 17. LC 862 — Shortest Subarray with Sum at Least K

**Pattern:** Prefix Sum + Monotonic Deque
**Priority:** 🔥🔥🔥🔥🔥

This is a higher-level problem.

Combine:

```text
Prefix Sum
+
Monotonic Deque
```

Instead of maintaining window values, we maintain **candidate prefix sums**.

### Core concepts

* Prefix transformation
* Candidate dominance
* Monotonic increasing deque
* Removing useless candidates
* Shortest valid range

### Core lesson

> **Monotonic deque is a general candidate-optimization technique, not merely a Sliding Window Maximum trick.**

This problem is extremely valuable for advanced pattern recognition.

---

# 🟥 LEVEL 11 — DP + MONOTONIC DEQUE

## 18. LC 1696 — Jump Game VI

**Pattern:** Dynamic Programming + Monotonic Deque
**Priority:** 🔥🔥🔥🔥

The DP relation is conceptually:

```text
dp[i]
=
nums[i]
+
max(dp[j])
```

where `j` belongs to the previous `k` positions.

Naive:

```text
O(nk)
```

Monotonic deque:

```text
O(n)
```

### Learn

```text
DP
 ↓
Sliding candidate range
 ↓
Need maximum
 ↓
Monotonic Deque
 ↓
O(n)
```

### Core concept

> **Monotonic deque can optimize a DP transition over a sliding range.**

---

# 🏆 FINAL LOCKED LEVEL MAP

| Level  | Pattern                      | Problems           | Priority          |
| ------ | ---------------------------- | ------------------ | ----------------- |
| 🟢 L1  | Queue Fundamentals           | **933, 622, 225**  | 🔥–🔥🔥🔥         |
| 🟡 L2  | Basic BFS + Shortest Path    | **1971, 1091**     | 🔥🔥🔥–🔥🔥🔥🔥   |
| 🟠 L3  | Multi-Source BFS             | **994, 542, 1162** | 🔥🔥🔥–🔥🔥🔥🔥🔥 |
| 🟣 L4  | Level-Order BFS              | **102, 199**       | 🔥🔥–🔥🔥🔥🔥     |
| 🔴 L5  | Implicit State BFS           | **752**            | 🔥🔥🔥🔥🔥        |
| 🔴 L6  | State Transformation BFS     | **127, 433**       | 🔥🔥–🔥🔥🔥🔥🔥   |
| 🟤 L7  | Tree → Graph + BFS           | **863**            | 🔥🔥🔥🔥          |
| 🟦 L8  | Monotonic Deque              | **239**            | 🔥🔥🔥🔥🔥🔥      |
| 🟦 L9  | Multiple Monotonic Deques    | **1438**           | 🔥🔥🔥🔥🔥        |
| 🟦 L10 | Prefix Sum + Monotonic Deque | **862**            | 🔥🔥🔥🔥🔥        |
| 🟥 L11 | DP + Monotonic Deque         | **1696**           | 🔥🔥🔥🔥          |

---

# 🎯 THE EXACT LEARNING PROGRESSION

```text
                    QUEUE / DEQUE
                          │
          ┌───────────────┴────────────────┐
          │                                │
        QUEUE                             DEQUE
          │                                │
          ▼                                ▼
     Queue Basics                    Deque Basics
          │                                │
          ▼                                ▼
        BFS                         Monotonic Deque
          │                                │
     ┌────┼─────┐                    ┌─────┴─────┐
     ▼    ▼     ▼                    ▼           ▼
   Graph Grid  Tree               Window      Candidate
     │    │     │                 Maximum      Optimization
     │    │     │                    │           │
     ▼    ▼     ▼                    ▼           ▼
 State  Multi  Level              239          862
 Space  Source Order                 │
     │    │     │                    ▼
     └────┴─────┘                  1438
          │                           │
          ▼                           ▼
    Representation                  1696
    Transformation
```

---

# 🧠 PATTERN RECOGNITION SHEET

This is the part you should eventually memorize.

| If the problem says...                  | Think...                     |
| --------------------------------------- | ---------------------------- |
| Process events in arrival order         | Queue                        |
| Remove old time-based events            | Queue + Time Window          |
| Fixed-size reusable buffer              | Circular Queue               |
| Shortest path, unweighted graph         | BFS                          |
| Grid shortest path                      | Grid BFS                     |
| Several sources start simultaneously    | Multi-Source BFS             |
| Distance from nearest source            | Multi-Source BFS             |
| Process one tree level at a time        | Level-Order BFS              |
| Configuration/state transitions         | State-Space BFS              |
| Transform one state into another        | BFS                          |
| Need movement both up/down a tree       | Tree → Graph + BFS           |
| Maximum of every K-sized window         | Monotonic Deque              |
| Minimum/maximum maintained dynamically  | Monotonic Deque              |
| Window needs both min and max           | Two Monotonic Deques         |
| Shortest subarray + prefix sums         | Prefix Sum + Monotonic Deque |
| DP transition needs max/min over last K | DP + Monotonic Deque         |

---

# 🔥 THE FOUR BIG QUEUE/DEQUE IDEAS

Everything eventually reduces to four mental models.

## 1. FIFO Processing

```text
NEW WORK
   ↓
QUEUE
   ↓
OLDEST WORK FIRST
```

---

## 2. BFS Frontier

```text
CURRENT FRONTIER
       ↓
     QUEUE
       ↓
NEXT FRONTIER
       ↓
NEXT FRONTIER
```

---

## 3. Multi-Source Wave

```text
S S S S
↓ ↓ ↓ ↓
WAVE
↓ ↓ ↓ ↓
WAVE
↓ ↓ ↓ ↓
```

---

## 4. Monotonic Candidate Maintenance

```text
Candidates
    ↓
Remove expired
    ↓
Remove dominated
    ↓
Keep useful candidates
    ↓
Front = best candidate
```

This fourth idea is the most advanced and is the real reason **LC 239 → LC 1438 → LC 862 → LC 1696** is such a valuable progression.

---

# 🏆 MUST-MASTER VS REINFORCEMENT

To keep the curriculum high-ROI:

## 🔥🔥🔥🔥🔥 ABSOLUTE MUST MASTER

```text
LC 1971
LC 1091
LC 994
LC 542
LC 102
LC 752
LC 127
LC 239
LC 1438
LC 862
```

## 🔥🔥🔥 IMPORTANT

```text
LC 933
LC 622
LC 1162
LC 863
LC 1696
```

## 🔥 REINFORCEMENT

```text
LC 225
LC 199
LC 433
```

This does **not** mean the reinforcement problems are useless. They simply don't introduce as much new algorithmic knowledge.

---

# 🧩 HOW WE WILL SOLVE THEM

This roadmap is now **locked**.

For every individual problem, we will use the same deep execution system you've been using throughout the DSA program:

```text
BLOCK 1
Senior Insights
        ↓
BLOCK 2
Efficient Code
        ↓
BLOCK 3
Full Code + Detailed Dry Run
        ↓
BLOCK 4
Interview Q&A
        ↓
Pattern Extraction
        ↓
Master Template
        ↓
Complexity Derivation
        ↓
Edge Cases
        ↓
FAANG Follow-ups
        ↓
Senior Engineer Thinking
        ↓
ML/MLOps Application
        ↓
Mastery Check
```

**No reduction in depth.**

The roadmap only tells us **what to solve and in what order**.

---

# 🚨 IMPORTANT RULE FOR THE NEW CONVERSATIONS

When you open a new conversation for a specific Queue/Deque problem, paste the **DSA Master Continuation Prompt** we prepared earlier first.

Then simply say:

> **LC 933**

or:

> **LC 239**

The new conversation should understand:

```text
Queue/Deque Card 3
        ↓
Locked Level
        ↓
Current Problem
        ↓
Same four-block deep execution
        ↓
Same pattern-mastery philosophy
```

---

# 🟦 QUEUE / DEQUE — OFFICIAL LOCKED ROADMAP

```text
LEVEL 1 — QUEUE
├── LC 933
├── LC 622
└── LC 225

LEVEL 2 — BASIC BFS
├── LC 1971
└── LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── LC 994
├── LC 542
└── LC 1162

LEVEL 4 — LEVEL BFS
├── LC 102
└── LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── LC 752

LEVEL 6 — STATE TRANSFORMATION BFS
├── LC 127
└── LC 433

LEVEL 7 — TREE → GRAPH
└── LC 863

LEVEL 8 — MONOTONIC DEQUE
└── LC 239 ⭐⭐⭐⭐⭐⭐

LEVEL 9 — MULTIPLE MONOTONIC DEQUES
└── LC 1438

LEVEL 10 — PREFIX + DEQUE
└── LC 862

LEVEL 11 — DP + DEQUE
└── LC 1696
```

## 🔒 STATUS: ROADMAP LOCKED

**Next execution point: Level 1 → LC 933 — Number of Recent Calls.**

From here, we solve **one problem at a time**, at the same depth and structure as your previous DSA sessions.

Would you like to start with LC 933 and follow the locked roadmap from there?


# Level 1

# 🟢 LEVEL 1 — QUEUE FUNDAMENTALS

# LC 933 — Number of Recent Calls

> **Pattern:** Queue + Time Window
> **Difficulty:** Easy
> **Priority:** 🔥🔥🔥
> **Core skill:** FIFO + Expiration
> **This problem's purpose:** Build the foundation for **time-based queue processing**, which later appears in streaming systems, rate limiting, logs, event processing, and BFS.

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You receive calls at timestamps:

```text
t1, t2, t3, ...
```

For every new call at time `t`, return the number of calls that happened in:

```text
[t - 3000, t]
```

Important:

* The current call is included.
* Calls older than `t - 3000` must be removed.
* Calls arrive in chronological order.

### Example

Suppose:

```text
ping(1)
ping(100)
ping(3001)
ping(3002)
```

For `ping(3002)`, we care about:

```text
[2, 3002]
```

So:

```text
1      ❌ expired
100    ✅
3001   ✅
3002   ✅
```

Answer:

```text
3
```

---

## 2. Hidden Translation

The problem sounds like:

> "Count calls in the last 3000 milliseconds."

Translate that immediately into:

```text
Time window
+
Events arrive in order
+
Old events expire
+
Need efficient insertion/removal
```

That screams:

# 🚨 QUEUE

Why?

Because calls arrive chronologically.

The oldest call is always at the front.

So when a call becomes too old:

```text
POP FROM FRONT
```

And every new call goes to:

```text
PUSH TO BACK
```

That is exactly FIFO.

---

# 3. Why Brute Force Is Bad

A naive solution could store every timestamp and, for every `ping(t)`, scan the entire list:

```python
count = 0

for timestamp in calls:
    if t - 3000 <= timestamp <= t:
        count += 1
```

If there are `n` calls:

```text
ping 1 → scan 1
ping 2 → scan 2
ping 3 → scan 3
...
```

Total:

```text
O(1 + 2 + 3 + ... + n)
= O(n²)
```

We don't need to repeatedly inspect timestamps that we already know are too old.

---

# 4. Core Algorithmic Insight

Because timestamps are guaranteed to be **non-decreasing**, the queue maintains:

```text
oldest → newest
```

For every new timestamp `t`:

### Step 1 — Add current call

```python
queue.append(t)
```

### Step 2 — Remove expired calls

Any timestamp satisfying:

```text
timestamp < t - 3000
```

is outside the valid interval.

So:

```python
while queue[0] < t - 3000:
    queue.popleft()
```

### Step 3 — Remaining queue size

Everything remaining belongs to:

```text
[t - 3000, t]
```

Therefore:

```python
return len(queue)
```

---

# 5. The Mathematical Condition

Valid call:

Expired call:

Notice the strict `<`.

A call exactly at:

```text
t - 3000
```

is still valid.

### Example

For:

```text
t = 3001
```

window:

```text
[1, 3001]
```

So timestamp `1` is **valid**.

This is one of the most important edge cases.

---

# 6. Why `deque` Instead of Python List?

We need:

```text
append at back
remove from front
```

Python `list`:

```python
append()      → O(1)
pop(0)        → O(n)
```

Why is `pop(0)` expensive?

Because all remaining elements have to shift left.

Example:

```text
[10, 20, 30, 40, 50]
 ↑
remove
```

becomes:

```text
[20, 30, 40, 50]
```

The elements must be shifted.

---

`collections.deque` provides:

```python
append()      → O(1)
popleft()     → O(1)
```

So it is the natural data structure.

---

# 7. ELI10 Intuition

Imagine a line at a ticket counter.

Every person has a timestamp showing when they joined.

You only care about people who joined during the last 3000 milliseconds.

New person:

```text
→ enters back
```

Oldest person:

```text
← leaves front
```

Because everyone enters in order, you never need to check people in the middle.

The queue always looks like:

```text
OLDEST                         NEWEST
  ↓                              ↓
[ 100 ][ 500 ][ 1000 ][ 2500 ][ 3000 ]
   ↑
 remove expired from here
```

---

# 8. Pattern Intuition

This is the first important Queue pattern:

```text
EVENT STREAM
     ↓
ARRIVAL ORDER
     ↓
FIFO
     ↓
QUEUE
     ↓
EXPIRE OLD EVENTS
```

The key idea isn't really "count recent calls."

It's:

> **Maintain only the currently valid portion of a stream.**

This idea appears in:

* rate limiting
* API request tracking
* monitoring systems
* sliding time windows
* event streams
* log processing
* telemetry
* distributed systems
* cache expiration
* networking

---

# 9. Invariant

This is the most important interview concept.

After processing `ping(t)`:

> **Every timestamp in the queue belongs to `[t - 3000, t]`, and timestamps remain in chronological order.**

So:

```text
QUEUE INVARIANT
──────────────────────────────
oldest valid timestamp
        ↓
[ valid ][ valid ][ valid ][ valid ]
                              ↑
                         current time
```

Once this invariant is established:

```python
len(queue)
```

automatically gives the answer.

---

# 10. Why the `while` Loop?

You may wonder:

> Why not use `if`?

Because multiple calls can expire at once.

Example:

```text
queue = [1, 10, 20, 3000]
t = 6000
```

Valid range:

```text
[3000, 6000]
```

We need to remove:

```text
1
10
20
```

So:

```python
while queue[0] < t - 3000:
    queue.popleft()
```

not:

```python
if queue[0] < t - 3000:
    queue.popleft()
```

---

# 11. Recognition Rules

When you see:

### Signal 1

> "Recent events"

Think:

```text
Time Window
```

### Signal 2

> Events arrive chronologically

Think:

```text
Queue
```

### Signal 3

> Remove events older than X

Think:

```text
Queue + expiration
```

### Signal 4

> Need oldest event repeatedly

Think:

```text
FIFO
```

### Signal 5

> Add at one end, remove from the other

Think:

```text
Deque / Queue
```

---

# 12. Pattern Extraction

This problem gives us a reusable template:

```text
NEW EVENT
   ↓
ADD TO QUEUE
   ↓
REMOVE EXPIRED FRONT EVENTS
   ↓
QUEUE CONTAINS ONLY VALID EVENTS
   ↓
ANSWER FROM QUEUE
```

This is essentially a **time-based sliding window**.

---

# 13. Interview Traps

### Trap 1 — Using `<=`

Wrong:

```python
while queue[0] <= t - 3000:
```

That removes a call exactly 3000 ms old.

But that call is still inside the inclusive interval.

Correct:

```python
while queue[0] < t - 3000:
```

---

### Trap 2 — Using `list.pop(0)`

Technically possible, but inefficient.

Use:

```python
from collections import deque
```

---

### Trap 3 — Removing only one expired call

Wrong:

```python
if queue[0] < t - 3000:
    queue.popleft()
```

Correct:

```python
while queue[0] < t - 3000:
    queue.popleft()
```

---

### Trap 4 — Forgetting the current call

The current call belongs to the window.

Therefore:

```python
queue.append(t)
```

comes before expiration.

---

### Trap 5 — Thinking this is ordinary sliding window

It is related, but the window is based on **time**, not necessarily a fixed number of elements.

Compare:

```text
Fixed-size sliding window:
last K elements
```

versus:

```text
Time-based sliding window:
last X milliseconds
```

This distinction becomes important in real-world systems.

---

# ⚡ BLOCK 2 — EFFICIENT CODE

## Best Python 3 Solution

```python
from collections import deque


class RecentCounter:

    def __init__(self):
        self.queue = deque()

    def ping(self, t: int) -> int:
        self.queue.append(t)

        while self.queue[0] < t - 3000:
            self.queue.popleft()

        return len(self.queue)
```

---

## Complexity

Let `n` be the total number of calls.

### `append`

```python
queue.append(t)
```

takes:

```text
O(1)
```

### `popleft`

Each timestamp can be removed **only once**.

Even though we have a `while` loop, we don't get `O(n²)`.

Across all calls:

```text
each timestamp:
    enters queue once
    leaves queue once
```

Therefore total work is:

```text
O(n)
```

Amortized.

So:

### Time

```text
O(1) amortized per ping
O(n) total for n pings
```

### Space

At most `n` timestamps can temporarily be stored:

```text
O(n)
```

More precisely, space is proportional to the number of calls in the active 3000-ms window.

---

## Interview Justification

If the interviewer asks:

> "Why is the while loop still O(n)?"

Say:

> "Although a single `ping` can remove multiple timestamps, each timestamp is appended once and removed at most once. Therefore, across n operations, the total number of `popleft` operations is at most n, giving O(n) total time, or O(1) amortized time per operation."

That's the senior-level explanation.

---

# 💻 BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Code

```python
from collections import deque


class RecentCounter:

    def __init__(self):
        self.queue = deque()

    def ping(self, t: int) -> int:
        self.queue.append(t)

        while self.queue[0] < t - 3000:
            self.queue.popleft()

        return len(self.queue)


# Create object
counter = RecentCounter()

# Test calls
timestamps = [1, 100, 3001, 3002]

for t in timestamps:
    result = counter.ping(t)
    print(f"ping({t}) -> {result}")
```

### Output

```text
ping(1) -> 1
ping(100) -> 2
ping(3001) -> 3
ping(3002) -> 3
```

---

# 🔍 Detailed Dry Run

## Call 1

```text
ping(1)
```

Add:

```text
[1]
```

Window:

```text
[1 - 3000, 1]
=
[-2999, 1]
```

`1` is valid.

Answer:

```text
1
```

---

## Call 2

```text
ping(100)
```

Add:

```text
[1, 100]
```

Window:

```text
[-2900, 100]
```

Both are valid.

Answer:

```text
2
```

---

## Call 3

```text
ping(3001)
```

Add:

```text
[1, 100, 3001]
```

Window:

```text
[1, 3001]
```

Check front:

```text
1 < 1
```

False.

Therefore `1` remains.

Answer:

```text
3
```

### Important!

This proves the boundary condition:

```text
timestamp == t - 3000
```

is valid.

---

## Call 4

```text
ping(3002)
```

Add:

```text
[1, 100, 3001, 3002]
```

Window:

```text
[2, 3002]
```

Check front:

```text
1 < 2
```

True.

Remove:

```text
[100, 3001, 3002]
```

Check again:

```text
100 < 2
```

False.

Stop.

Answer:

```text
3
```

---

# 📊 Dry Run Table

|  `t` | Window Start | Queue Before Cleanup | Expired | Queue After Cleanup | Answer |
| ---: | -----------: | -------------------- | ------- | ------------------- | -----: |
|    1 |        -2999 | `[1]`                | none    | `[1]`               |      1 |
|  100 |        -2900 | `[1,100]`            | none    | `[1,100]`           |      2 |
| 3001 |            1 | `[1,100,3001]`       | none    | `[1,100,3001]`      |      3 |
| 3002 |            2 | `[1,100,3001,3002]`  | `1`     | `[100,3001,3002]`   |      3 |

---

# 🧠 Visual Understanding

Think of the queue as a moving time window:

```text
TIME →

1      100             3001     3002
|-------|----------------|--------|
        <---- 3000 ms ---->

At t = 3002:

Valid region:
       2 ---------------------- 3002
       ↑
    boundary

1  ❌
100 ✅
3001 ✅
3002 ✅
```

Therefore:

```text
[100, 3001, 3002]
```

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why is a queue the correct data structure?

### Answer

Because timestamps arrive in chronological order. The oldest timestamp is always at the front, and expired timestamps must be removed from the front. New timestamps are added to the back, which exactly matches FIFO behavior.

---

## Q2. Why use `deque` instead of a list?

### Answer

We need efficient insertion at the back and removal from the front.

```text
deque.append()  → O(1)
deque.popleft() → O(1)
```

A Python list's `pop(0)` is O(n) because remaining elements have to shift.

---

## Q3. Why is the condition `< t - 3000` instead of `<=`?

### Answer

The valid interval is inclusive:

```text
[t - 3000, t]
```

Therefore a timestamp exactly equal to `t - 3000` is still valid.

Only:

```text
timestamp < t - 3000
```

is expired.

---

## Q4. Why do we need `while` instead of `if`?

### Answer

Multiple timestamps may expire during a single call. Since all expired timestamps are guaranteed to be at the front due to chronological ordering, we repeatedly remove them until the front becomes valid.

---

## Q5. Isn't the while loop O(n) for every call?

### Answer

No. It is O(1) amortized.

Every timestamp:

```text
enters the queue once
leaves the queue at most once
```

So over `n` calls, there can be at most `n` removals.

Thus:

```text
Total = O(n)
Amortized per operation = O(1)
```

---

## Q6. What assumption makes this solution possible?

### Answer

The timestamps arrive in non-decreasing order.

That guarantees the queue is sorted from oldest to newest.

Therefore, once the front timestamp is valid, every later timestamp is automatically valid.

---

# 🧩 MASTER PATTERN

This is your first **Queue + Expiration** template:

```python
from collections import deque

queue = deque()

def process(t):
    queue.append(t)

    while queue[0] < t - WINDOW:
        queue.popleft()

    return len(queue)
```

Generalize:

```text
EVENT ARRIVES
     ↓
enqueue(event)
     ↓
while oldest event expired:
     dequeue()
     ↓
remaining queue = active events
```

---

# 🔥 SENIOR PATTERN RECOGNITION

When you see a problem involving:

```text
events
+
timestamps
+
recent
+
last X seconds
+
last X milliseconds
+
expire old requests
+
arrival order
```

Immediately ask:

> **Can I maintain active events using a FIFO queue?**

If yes:

```text
Queue + Time Window
```

---

# 🔗 CONNECTION TO SLIDING WINDOW

You already learned sliding-window string problems such as:

```text
LC 3
LC 424
LC 438
LC 567
```

Those use:

```text
LEFT ---------------- RIGHT
```

This problem uses a similar concept, but instead of moving a left pointer through an array:

```text
time window
    ↓
remove expired timestamps
```

So think:

```text
SLIDING WINDOW
       ↓
┌──────┴────────┐
│               │
Fixed/Index     Time-based
Window          Window
│               │
Two pointers    Queue
```

This is a very important bridge between **Sliding Window** and **Queue**.

---

# 🚀 REAL-WORLD ENGINEERING CONNECTION

This exact pattern appears in:

### API Rate Limiting

For example:

> Allow at most 100 requests in the last 60 seconds.

Maintain:

```text
queue = request timestamps
```

For each request:

```text
add timestamp
remove timestamps older than 60 seconds
check len(queue)
```

### Monitoring

```text
Recent errors
Recent requests
Recent events
Recent transactions
```

### Streaming Systems

```text
incoming events
       ↓
queue
       ↓
expire old events
       ↓
process active window
```

So this "Easy" LeetCode problem teaches a genuinely useful production pattern.

---

# 🧠 LEVEL 1 MASTER CHECK

After LC 933, you should be able to answer:

```text
Why Queue?
       ↓
FIFO

Why Deque?
       ↓
O(1) front removal

Why while?
       ↓
Multiple events can expire

Why chronological order?
       ↓
Front is always oldest

Why len(queue)?
       ↓
Queue invariant guarantees every remaining event is valid

Complexity?
       ↓
O(1) amortized / ping
O(n) total
O(n) worst-case space
```

---

# 📌 PROGRESS UPDATE

```text
QUEUE / DEQUE
│
├── 🟢 LEVEL 1 — Queue Fundamentals
│   │
│   ├── ✅ LC 933 — Number of Recent Calls  ← YOU ARE HERE
│   ├── ⬜ LC 622 — Design Circular Queue
│   └── ⬜ LC 225 — Implement Stack using Queues
│
├── 🟡 LEVEL 2 — Basic BFS
├── 🟠 LEVEL 3 — Multi-Source BFS
├── 🟣 LEVEL 4 — Level-Order BFS
├── 🔴 LEVEL 5 — Implicit State BFS
├── 🔴 LEVEL 6 — State Transformation BFS
├── 🟤 LEVEL 7 — Tree → Graph BFS
├── 🟦 LEVEL 8 — Monotonic Deque
├── 🟦 LEVEL 9 — Multiple Monotonic Deques
├── 🟦 LEVEL 10 — Prefix Sum + Deque
└── 🟥 LEVEL 11 — DP + Deque
```

## 🔑 One-Line Takeaway

> **When events arrive in chronological order and old events expire by time, maintain the active events with a FIFO queue: enqueue the new event, remove expired events from the front, and the remaining queue is your current time window.**

**Next locked problem → LC 622 — Design Circular Queue.**

Would you like to continue with LC 622, or do a quick mastery check on LC 933 first?

# 🟢 LEVEL 1 — QUEUE FUNDAMENTALS

# LC 622 — Design Circular Queue

> **Pattern:** Circular Queue / Circular Buffer
> **Priority:** 🔥🔥
> **Core skill:** `front`, `rear`, `size`, `capacity`, and wrap-around
> **Why we're doing it:** LC 933 taught you **FIFO + expiration**. LC 622 now teaches you how a queue can be implemented efficiently **without shifting elements**.

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You need to build your own queue with a fixed capacity `k`.

A normal queue follows:

```text
FIFO
First In → First Out
```

Operations:

```text
enQueue(value)
deQueue()
Front()
Rear()
isEmpty()
isFull()
```

The interesting part is:

> After reaching the end of the underlying array, can we reuse the empty positions at the beginning?

Yes.

That's the entire idea of a **circular queue**.

---

# 2. The Hidden Translation

Whenever you see:

> "Implement a queue with fixed capacity"

immediately think:

```text
Fixed-size storage
      ↓
No dynamic expansion
      ↓
Reuse freed positions
      ↓
Circular indexing
```

The key formula is:

This makes the array wrap around.

Example with capacity `5`:

```text
index:

0 → 1 → 2 → 3 → 4
↑               ↓
└───────────────┘
```

After index `4`:

```text
(4 + 1) % 5 = 0
```

So we go back to index `0`.

---

# 3. Why Not Use a Normal Array Queue?

Suppose:

```text
queue = [10, 20, 30, 40, 50]
```

Now dequeue:

```text
10 removed
```

A naive implementation might shift:

```text
[20, 30, 40, 50, _]
```

Then another:

```text
[30, 40, 50, _, _]
```

This causes unnecessary movement.

Instead, with a circular queue:

```text
[10, 20, 30, 40, 50]
 ↑
 front
```

Remove `10`:

```text
[_, 20, 30, 40, 50]
    ↑
   front
```

No shifting.

Then if we enqueue `60`:

```text
[60, 20, 30, 40, 50]
 ↑
 rear position reused
```

The physical array looks strange, but logically the queue is:

```text
20 → 30 → 40 → 50 → 60
```

That's the important distinction:

> **Physical array order does not have to equal logical queue order.**

---

# 4. Core State We Need

There are several possible implementations.

For interview clarity, we can maintain:

```text
front
rear
size
capacity
```

Meaning:

### `front`

Index of the first element.

```text
front → oldest element
```

### `rear`

Index where the **next element will be inserted**.

This convention is extremely useful.

### `size`

Number of currently stored elements.

### `capacity`

Maximum number of elements.

---

# 5. The Most Important Design Decision

There are two common ways to define `rear`.

### Convention A

`rear` = index of the last element.

### Convention B

`rear` = index of the next insertion position.

We'll use:

> **`rear` = next insertion position**

Why?

Because `enQueue` becomes extremely clean:

```python
queue[rear] = value
rear = (rear + 1) % capacity
size += 1
```

And `Rear()` becomes:

```text
last element = position before rear
```

Therefore:

The `+ k` avoids a negative index.

---

# 6. The Circular Queue Model

Suppose:

```text
capacity = 5
```

Initially:

```text
array = [_, _, _, _, _]

front = 0
rear  = 0
size  = 0
```

After enqueue `10`:

```text
array = [10, _, _, _, _]

front = 0
rear  = 1
size  = 1
```

After enqueue `20`:

```text
array = [10, 20, _, _, _]

front = 0
rear  = 2
size  = 2
```

After dequeue:

```text
array = [_, 20, _, _, _]

front = 1
rear  = 2
size  = 1
```

Now enqueue `30`:

```text
array = [_, 20, 30, _, _]

front = 1
rear  = 3
```

The queue logically is:

```text
20 → 30
```

---

# 7. Where the "Circular" Part Becomes Important

Suppose capacity is `5`.

We've reached:

```text
rear = 5
```

But index `5` doesn't exist.

Instead:

```text
rear = (5 + 1) % 5
```

Actually, when `rear == 4` and we insert there:

```text
rear = (4 + 1) % 5
     = 0
```

So:

```text
4 → 0
```

That's the wrap-around.

---

# 8. ELI10 Intuition

Imagine five chairs arranged in a circle:

```text
       0
   4       1

   3       2
```

People enter from the rear and leave from the front.

When the rear reaches chair `4`, it doesn't stop.

It goes back to chair `0`.

```text
0 → 1 → 2 → 3 → 4 → 0 → 1 → ...
```

But you cannot occupy a chair if all `k` chairs are currently occupied.

That's why we track:

```text
size
```

---

# 9. Why `size` Is Important

This is a major interview concept.

If we only stored:

```text
front
rear
```

then when:

```text
front == rear
```

we could have two situations:

### Situation 1 — Empty

```text
front == rear
```

### Situation 2 — Completely full

After wrapping around:

```text
front == rear
```

So `front == rear` alone is ambiguous.

Tracking `size` solves it:

```text
size == 0       → empty
size == capacity → full
```

This is one of the cleanest circular queue designs.

---

# 10. Invariant

After every valid operation:

```text
0 <= size <= capacity
```

and:

```text
front = location of oldest element
```

and:

```text
rear = next insertion position
```

This is the core invariant.

Everything else follows from it.

---

# 11. Operation Derivation

## `isEmpty()`

Obviously:

```python
return self.size == 0
```

---

## `isFull()`

```python
return self.size == self.capacity
```

---

## `enQueue(value)`

First:

```text
If full → fail
```

Otherwise:

```text
array[rear] = value
```

Move rear:

```text
rear = (rear + 1) % capacity
```

Increase size:

```text
size += 1
```

---

## `deQueue()`

First:

```text
If empty → fail
```

We don't actually need to erase the value.

Just move `front`:

```text
front = (front + 1) % capacity
```

Then:

```text
size -= 1
```

This is an important implementation insight:

> **Logical deletion does not require physical deletion.**

---

## `Front()`

If empty:

```text
-1
```

Otherwise:

```python
return array[front]
```

---

## `Rear()`

If empty:

```text
-1
```

Otherwise the last inserted element is immediately before `rear`.

Therefore:

```python
(rear - 1 + capacity) % capacity
```

---

# 12. Why Don't We Clear Values During `deQueue()`?

You might write:

```python
self.queue[self.front] = -1
```

You don't need to.

Because `size` tells us whether a location logically contains an active queue element.

The array is merely storage.

The queue's logical state is determined by:

```text
front
rear
size
```

This distinction is important in data-structure design.

---

# 13. Recognition Rules

When you see:

### "Fixed capacity queue"

Think:

```text
Circular Queue
```

### "Reuse freed array positions"

Think:

```text
Circular indexing
```

### "Avoid shifting"

Think:

```text
front pointer
```

### "Wrap around"

Think:

```text
(index + 1) % capacity
```

### "Need distinguish empty/full"

Think:

```text
size
```

---

# 14. Pattern Extraction

The pattern is:

```text
FIXED CAPACITY
      ↓
ARRAY
      ↓
FRONT + REAR
      ↓
MODULO WRAP-AROUND
      ↓
SIZE TRACKING
      ↓
O(1) QUEUE OPERATIONS
```

This is the foundation for:

* circular buffers
* producer/consumer queues
* streaming systems
* network buffers
* audio/video buffers
* embedded systems
* logging pipelines

---

# ⚡ BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

```python
class MyCircularQueue:

    def __init__(self, k: int):
        self.queue = [0] * k
        self.capacity = k
        self.front = 0
        self.rear = 0
        self.size = 0

    def enQueue(self, value: int) -> bool:
        if self.isFull():
            return False

        self.queue[self.rear] = value
        self.rear = (self.rear + 1) % self.capacity
        self.size += 1

        return True

    def deQueue(self) -> bool:
        if self.isEmpty():
            return False

        self.front = (self.front + 1) % self.capacity
        self.size -= 1

        return True

    def Front(self) -> int:
        if self.isEmpty():
            return -1

        return self.queue[self.front]

    def Rear(self) -> int:
        if self.isEmpty():
            return -1

        last_index = (self.rear - 1 + self.capacity) % self.capacity
        return self.queue[last_index]

    def isEmpty(self) -> bool:
        return self.size == 0

    def isFull(self) -> bool:
        return self.size == self.capacity
```

---

# Complexity

Every operation performs a constant number of operations.

### `enQueue`

```text
O(1)
```

### `deQueue`

```text
O(1)
```

### `Front`

```text
O(1)
```

### `Rear`

```text
O(1)
```

### `isEmpty`

```text
O(1)
```

### `isFull`

```text
O(1)
```

Space:

```text
O(k)
```

because we allocate an array of capacity `k`.

---

# 🎤 Interview Justification

If asked:

> "Why is this better than shifting elements?"

Say:

> "Instead of physically moving elements after every dequeue, I maintain a front pointer and reuse freed positions through modulo arithmetic. Every operation only updates a few indices and the size, so all queue operations are O(1)."

That's the key answer.

---

# 💻 BLOCK 3 — FULL CODE + DRY RUN

## Runnable Code

```python
class MyCircularQueue:

    def __init__(self, k: int):
        self.queue = [0] * k
        self.capacity = k
        self.front = 0
        self.rear = 0
        self.size = 0

    def enQueue(self, value: int) -> bool:
        if self.isFull():
            return False

        self.queue[self.rear] = value
        self.rear = (self.rear + 1) % self.capacity
        self.size += 1

        return True

    def deQueue(self) -> bool:
        if self.isEmpty():
            return False

        self.front = (self.front + 1) % self.capacity
        self.size -= 1

        return True

    def Front(self) -> int:
        if self.isEmpty():
            return -1

        return self.queue[self.front]

    def Rear(self) -> int:
        if self.isEmpty():
            return -1

        last_index = (self.rear - 1 + self.capacity) % self.capacity
        return self.queue[last_index]

    def isEmpty(self) -> bool:
        return self.size == 0

    def isFull(self) -> bool:
        return self.size == self.capacity


# Create a circular queue of capacity 3
q = MyCircularQueue(3)

print(q.enQueue(10))
print(q.enQueue(20))
print(q.enQueue(30))

print(q.Rear())
print(q.isFull())

print(q.deQueue())

print(q.enQueue(40))

print(q.Front())
print(q.Rear())
```

### Output

```text
True
True
True
30
True
True
True
20
40
```

---

# 🔍 Step-by-Step Dry Run

Capacity:

```text
k = 3
```

Initial:

```text
array = [0, 0, 0]

front = 0
rear  = 0
size  = 0
```

---

## Operation 1 — `enQueue(10)`

Check:

```text
size == capacity?
0 == 3 → False
```

Insert:

```text
array[0] = 10
```

Move rear:

```text
rear = (0 + 1) % 3
     = 1
```

Size:

```text
size = 1
```

State:

```text
array = [10, 0, 0]

front = 0
rear  = 1
size  = 1
```

Logical queue:

```text
10
```

---

## Operation 2 — `enQueue(20)`

Insert at:

```text
rear = 1
```

```text
array = [10, 20, 0]
```

Move:

```text
rear = 2
size = 2
```

State:

```text
front = 0
rear  = 2
size  = 2
```

Logical queue:

```text
10 → 20
```

---

## Operation 3 — `enQueue(30)`

Insert:

```text
array[2] = 30
```

Move rear:

```text
rear = (2 + 1) % 3
     = 0
```

Size:

```text
size = 3
```

State:

```text
array = [10, 20, 30]

front = 0
rear  = 0
size  = 3
```

Notice:

```text
front == rear
```

But the queue is **not empty**.

Why?

Because:

```text
size = 3 = capacity
```

Therefore it is full.

---

# 🚨 Critical Moment

This is exactly why we need `size`.

```text
front = 0
rear  = 0
```

could mean:

```text
EMPTY
```

or:

```text
FULL
```

But:

```text
size = 3
```

clearly tells us:

```text
FULL
```

---

## Operation 4 — `Rear()`

`rear = 0`.

The last element is immediately before it circularly.

Formula:

```text
(rear - 1 + capacity) % capacity
```

Therefore:

```text
(0 - 1 + 3) % 3
= 2 % 3
= 2
```

So:

```text
array[2] = 30
```

Answer:

```text
30
```

---

## Operation 5 — `deQueue()`

Remove logical front:

```text
front = 0
```

Move:

```text
front = (0 + 1) % 3
      = 1
```

Decrease size:

```text
size = 2
```

Array physically remains:

```text
[10, 20, 30]
```

But logically:

```text
10 is gone
```

Queue:

```text
20 → 30
```

This is an important distinction:

```text
physical array ≠ logical queue
```

---

# Operation 6 — `enQueue(40)`

Now:

```text
rear = 0
```

because it wrapped around.

Insert:

```text
array[0] = 40
```

Array becomes:

```text
[40, 20, 30]
```

Move rear:

```text
rear = (0 + 1) % 3
     = 1
```

Size:

```text
size = 3
```

Logical queue is:

```text
front = 1
```

Therefore:

```text
20 → 30 → 40
```

Even though the physical array says:

```text
40, 20, 30
```

That's the circular queue.

---

# 📊 Complete Dry Run Table

| Operation     | Array        | Front | Rear | Size | Logical Queue |
| ------------- | ------------ | ----: | ---: | ---: | ------------- |
| Initial       | `[0,0,0]`    |     0 |    0 |    0 | `[]`          |
| `enQueue(10)` | `[10,0,0]`   |     0 |    1 |    1 | `[10]`        |
| `enQueue(20)` | `[10,20,0]`  |     0 |    2 |    2 | `[10,20]`     |
| `enQueue(30)` | `[10,20,30]` |     0 |    0 |    3 | `[10,20,30]`  |
| `deQueue()`   | `[10,20,30]` |     1 |    0 |    2 | `[20,30]`     |
| `enQueue(40)` | `[40,20,30]` |     1 |    1 |    3 | `[20,30,40]`  |

---

# 🧠 Visualize the Wrap-Around

```text
Capacity = 3

        ┌───────────┐
        ↓           │
      [0] → [1] → [2]
       ↑             │
       └─────────────┘
```

Index movement:

```text
0 → 1 → 2 → 0 → 1 → 2 → ...
```

Mathematically:

```text
next = (current + 1) % k
```

This tiny formula is one of the most reusable formulas in data structures.

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. What makes a queue "circular"?

### Answer

The underlying storage is treated as circular. When the rear reaches the final array position, it wraps back to index `0` using modulo arithmetic.

```python
index = (index + 1) % capacity
```

This allows previously freed positions to be reused.

---

## Q2. Why do we need `size`?

### Answer

Because after wrap-around, `front == rear` can represent either an empty queue or a full queue.

Tracking `size` removes this ambiguity:

```text
size == 0       → empty
size == capacity → full
```

---

## Q3. Why don't you shift elements after dequeue?

### Answer

Shifting would cost O(k). Instead, I simply advance the `front` pointer. The removed location can later be reused when `rear` wraps around.

Therefore dequeue remains O(1).

---

## Q4. Why does `Rear()` use `(rear - 1 + capacity) % capacity`?

### Answer

Because I define `rear` as the **next insertion position**, not the current last element.

Therefore the last inserted element is immediately before `rear`, with circular wrap-around.

---

## Q5. Could we implement this using only `front` and `rear`?

### Answer

Yes, but we need another mechanism to distinguish full from empty, such as:

* a `size` variable
* reserving one slot
* an additional boolean flag

Using `size` is straightforward and makes the state explicit.

---

## Q6. What real-world systems use circular queues?

### Answer

Circular buffers are common in:

* network packet buffers
* producer-consumer systems
* streaming pipelines
* audio/video processing
* logging systems
* embedded systems
* operating-system buffers

They are particularly useful when memory capacity is fixed and we want O(1) insertion/removal.

---

# 🔥 LC 933 → LC 622 CONNECTION

This progression is intentional.

## LC 933

You learned:

```text
Events
 ↓
Chronological order
 ↓
Queue
 ↓
Remove expired front
```

Now LC 622:

```text
Queue
 ↓
Fixed capacity
 ↓
Array implementation
 ↓
Front/rear
 ↓
Circular reuse
```

So your Queue foundation is becoming:

```text
                 QUEUE
                   │
          ┌────────┴────────┐
          ↓                 ↓
      Dynamic            Fixed
      Queue               Queue
          │                 │
       LC 933             LC 622
          │                 │
    Time expiration    Circular buffer
```

---

# 🧩 MASTER TEMPLATE

Memorize the **logic**, not the exact code:

```python
class CircularQueue:

    def __init__(self, k):
        self.data = [0] * k
        self.capacity = k
        self.front = 0
        self.rear = 0
        self.size = 0

    def enQueue(self, value):
        if self.size == self.capacity:
            return False

        self.data[self.rear] = value
        self.rear = (self.rear + 1) % self.capacity
        self.size += 1

        return True

    def deQueue(self):
        if self.size == 0:
            return False

        self.front = (self.front + 1) % self.capacity
        self.size -= 1

        return True

    def Front(self):
        if self.size == 0:
            return -1

        return self.data[self.front]

    def Rear(self):
        if self.size == 0:
            return -1

        index = (self.rear - 1 + self.capacity) % self.capacity
        return self.data[index]
```

---

# 🚨 SENIOR-LEVEL PATTERN RECOGNITION

When you see:

```text
fixed memory
+
FIFO
+
reuse old positions
```

think:

# `Circular Buffer`

Then immediately derive:

```text
front
rear
size
capacity
```

and:

```text
next = (index + 1) % capacity
```

The deeper abstraction is:

> **A circular queue separates logical order from physical storage order.**

That is the real concept you should carry to interviews.

---

# 🧠 LEVEL 1 MASTERY CHECK

You should now be able to explain:

```text
Why queue?
    ↓
FIFO

Why circular?
    ↓
Reuse freed array positions

Why front?
    ↓
Track oldest element

Why rear?
    ↓
Track next insertion position

Why size?
    ↓
Distinguish empty/full

Why modulo?
    ↓
Wrap around

Why no shifting?
    ↓
Pointers provide O(1) movement

Complexity?
    ↓
All operations O(1)
Space O(k)
```

---

# 📌 PROGRESS UPDATE

```text
QUEUE / DEQUE
│
├── 🟢 LEVEL 1 — Queue Fundamentals
│   │
│   ├── ✅ LC 933 — Number of Recent Calls
│   ├── ✅ LC 622 — Design Circular Queue  ← YOU ARE HERE
│   └── ⬜ LC 225 — Implement Stack using Queues
│
├── 🟡 LEVEL 2 — Basic BFS
│   ├── ⬜ LC 1971
│   └── ⬜ LC 1091
│
├── 🟠 LEVEL 3 — Multi-Source BFS
│   ├── ⬜ LC 994
│   ├── ⬜ LC 542
│   └── ⬜ LC 1162
│
├── 🟣 LEVEL 4 — Level-Order BFS
│   ├── ⬜ LC 102
│   └── ⬜ LC 199
│
├── 🔴 LEVEL 5 — Implicit State BFS
│   └── ⬜ LC 752
│
├── 🔴 LEVEL 6 — State Transformation BFS
│   ├── ⬜ LC 127
│   └── ⬜ LC 433
│
├── 🟤 LEVEL 7 — Tree → Graph BFS
│   └── ⬜ LC 863
│
├── 🟦 LEVEL 8 — Monotonic Deque
│   └── ⬜ LC 239 ⭐
│
├── 🟦 LEVEL 9 — Multiple Monotonic Deques
│   └── ⬜ LC 1438
│
├── 🟦 LEVEL 10 — Prefix Sum + Deque
│   └── ⬜ LC 862
│
└── 🟥 LEVEL 11 — DP + Deque
    └── ⬜ LC 1696
```

## 🔑 One-Line Takeaway

> **A circular queue uses `front + rear + size` and modulo indexing to implement FIFO in fixed storage with O(1) operations while reusing positions freed by dequeues.**

### Next locked problem:

**LC 225 — Implement Stack using Queues** → Queue-based data-structure design.

Would you like to continue with LC 225, or do a quick mastery check on circular queues first?
# 🟢 LEVEL 1 — QUEUE FUNDAMENTALS

# LC 225 — Implement Stack using Queues

> **Pattern:** Queue-Based Data Structure Design
> **Priority:** 🔥
> **Core skill:** Using one FIFO abstraction to simulate a LIFO abstraction
> **Main lesson:** **When the underlying data structure doesn't provide the order you need, manipulate the order of elements until the required operation becomes possible.**

This is the final problem of **Queue Fundamentals** before we move into BFS.

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

A **stack** follows:

```text
LIFO
Last In → First Out
```

Example:

```text
push(10)
push(20)
push(30)
```

Stack:

```text
TOP
 ↓
30
20
10
```

So:

```text
pop() → 30
```

But a queue follows:

```text
FIFO
First In → First Out
```

If we put:

```text
10 → 20 → 30
```

into a queue:

```text
FRONT
  ↓
10 → 20 → 30
           ↑
          BACK
```

Normal queue operation gives:

```text
dequeue() → 10
```

But a stack needs:

```text
pop() → 30
```

So the fundamental problem is:

> **How can we rearrange a FIFO structure so that the newest element appears at the front?**

---

# 2. Hidden Translation

Whenever you see:

> "Implement X using Y"

don't immediately code.

Ask:

```text
What ordering does X require?
        ↓
What ordering does Y provide?
        ↓
What transformation makes Y behave like X?
```

Here:

```text
STACK
 ↓
LIFO

QUEUE
 ↓
FIFO
```

We need:

```text
FIFO
 ↓
rearrange
 ↓
LIFO
```

That is the whole problem.

---

# 3. Two Main Approaches

There are two classic designs.

## Approach A — Expensive `push`

Keep the newest element at the **front**.

When pushing:

```text
10
```

queue:

```text
10
```

Push `20`:

```text
20
10
```

Push `30`:

```text
30
20
10
```

Then:

```text
pop()
```

is simply:

```text
dequeue() → 30
```

So:

```text
push → O(n)
pop  → O(1)
```

---

## Approach B — Expensive `pop`

Keep insertion order:

```text
10 → 20 → 30
```

When popping, remove the first two elements and move them to the back:

```text
10 → 20 → 30
```

Move `10`:

```text
20 → 30 → 10
```

Move `20`:

```text
30 → 10 → 20
```

Now:

```text
30
```

is at the front.

Dequeue it.

So:

```text
push → O(1)
pop  → O(n)
```

Both are valid.

For LC 225, we'll use **Approach A: expensive push**, because it gives an especially clean invariant:

> **The front of the queue is always the top of the simulated stack.**

---

# 4. Why This Invariant Is Powerful

After every `push(x)`:

```text
queue.front == stack.top
```

Therefore:

```text
top()
```

becomes:

```python
queue[0]
```

and:

```text
pop()
```

becomes:

```python
popleft()
```

We have effectively converted:

```text
QUEUE
FIFO
```

into:

```text
STACK
LIFO
```

by maintaining the right ordering.

---

# 5. ELI10 Intuition

Imagine a line of people.

Normally:

```text
A → B → C
```

A queue makes `A` leave first.

But suppose every time a new person joins, you force everyone else to move behind them.

Add A:

```text
A
```

Add B:

```text
B → A
```

Add C:

```text
C → B → A
```

Now the newest person is always at the front.

Therefore:

```text
pop() → C
```

Exactly what a stack needs.

---

# 6. The Key Trick

Suppose current queue is:

```text
10 → 20
```

Push `30`.

First enqueue:

```text
10 → 20 → 30
```

Queue size is now `3`.

We want:

```text
30 → 10 → 20
```

So rotate the old elements:

```text
10 → 20 → 30
```

Move front to back:

```text
20 → 30 → 10
```

Again:

```text
30 → 10 → 20
```

Done.

The new element is now at the front.

---

# 7. Why Exactly `n` Rotations?

Suppose before insertion there are:

```text
n
```

elements.

After inserting the new element:

```text
n + 1
```

elements exist.

We need to move the **n old elements** behind the newly inserted element.

Therefore:

```python
for _ in range(len(queue) - 1):
    queue.append(queue.popleft())
```

Why `len(queue) - 1`?

Because the last element is the newly inserted element.

We don't want to rotate it.

---

# 8. State Invariant

After every operation:

```text id="8fq8xk"
QUEUE FRONT
     ↓
   STACK TOP
     ↓
[ newest → ... → oldest ]
```

This is the most important invariant.

Example:

```text
push(10)

[10]
 ↑
top
```

Then:

```text
push(20)

[20, 10]
 ↑
top
```

Then:

```text
push(30)

[30, 20, 10]
 ↑
top
```

Therefore:

```text
pop() → 30
pop() → 20
pop() → 10
```

LIFO achieved.

---

# 9. Why `deque`?

We need:

```text
append at back
remove from front
```

Both should be efficient.

Python's:

```python
collections.deque
```

provides:

```text
append()  → O(1)
popleft() → O(1)
```

So it is ideal.

---

# 10. Important Design Lesson

This problem is not really about memorizing a strange queue trick.

It teaches a much bigger engineering principle:

> **Data structures are abstractions with ordering guarantees. If the required ordering isn't directly available, you can transform the representation to maintain the required invariant.**

Here:

```text
Queue gives FIFO
        ↓
We manipulate ordering
        ↓
Queue behaves like LIFO
```

This idea appears everywhere in algorithms.

---

# 11. Complexity Derivation

Suppose there are `n` elements.

### `push`

We enqueue once:

```text
O(1)
```

Then rotate `n` elements:

```text
O(n)
```

Therefore:

```text
push = O(n)
```

### `pop`

Because the front is always the stack top:

```python
popleft()
```

takes:

```text
O(1)
```

### `top`

Read the front:

```text
O(1)
```

### `empty`

Check:

```text
O(1)
```

---

# 12. Amortized Complexity?

Important distinction:

Unlike LC 933, there is **no amortization trick that reduces push to O(1)** for this particular implementation.

Every `push` intentionally rotates the existing elements.

So:

```text
push → O(n)
pop  → O(1)
```

Worst-case and per-operation complexity are straightforward.

---

# 13. Alternative Design

You can reverse the trade-off.

Maintain:

```text
10 → 20 → 30
```

Then:

```text
push(30) → O(1)
```

but:

```text
pop()
```

must rotate:

```text
10 → 20 → 30
20 → 30 → 10
30 → 10 → 20
```

then remove `30`.

Therefore:

```text
push → O(1)
pop  → O(n)
top  → O(1)
```

This is also valid.

### Interview insight

If the interviewer asks:

> "Can you optimize push?"

You should immediately say:

> "Yes. I can move the reordering cost from push to pop. The two implementations trade off O(n) push versus O(n) pop."

---

# 14. Recognition Rules

When you see:

> Implement stack using queue(s)

Think:

```text
Need LIFO
+
Have FIFO
+
Need reorder
```

Then choose:

### Option 1

```text
Expensive push
Cheap pop
```

or:

### Option 2

```text
Cheap push
Expensive pop
```

The choice depends on which operation you want to optimize.

---

# 🚨 Interview Trap

Don't say:

> "A queue can behave like a stack."

That's incomplete.

The correct explanation is:

> "A queue naturally provides FIFO, so I explicitly reorder its elements after insertion to maintain the invariant that the newest element is at the front. That makes the queue's front equivalent to the stack's top."

That demonstrates understanding rather than memorization.

---

# ⚡ BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

```python
from collections import deque


class MyStack:

    def __init__(self):
        self.queue = deque()

    def push(self, x: int) -> None:
        self.queue.append(x)

        # Move all previous elements behind x
        for _ in range(len(self.queue) - 1):
            self.queue.append(self.queue.popleft())

    def pop(self) -> int:
        return self.queue.popleft()

    def top(self) -> int:
        return self.queue[0]

    def empty(self) -> bool:
        return len(self.queue) == 0
```

---

# Why This Code Works

Suppose:

```text
queue = [10, 20]
```

Call:

```python
push(30)
```

After append:

```text
[10, 20, 30]
```

Rotate `len(queue) - 1 = 2` times.

First:

```text
[20, 30, 10]
```

Second:

```text
[30, 10, 20]
```

Now:

```text
queue.front = 30
```

Therefore:

```text
top() → 30
pop() → 30
```

Exactly stack behavior.

---

# Complexity Table

| Operation | Complexity |
| --------- | ---------: |
| `push(x)` |   **O(n)** |
| `pop()`   |   **O(1)** |
| `top()`   |   **O(1)** |
| `empty()` |   **O(1)** |
| Space     |   **O(n)** |

Where `n` is the current number of elements.

---

# 🎤 Interview Justification

If asked:

> "Explain your design."

Say:

> "I'm using a deque as the underlying queue. After inserting a new value, I rotate all previous elements behind it. This maintains the invariant that the queue's front is always the stack's top. Therefore pop and top are O(1), while push is O(n)."

That's a strong interview answer.

---

# 💻 BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Code

```python
from collections import deque


class MyStack:

    def __init__(self):
        self.queue = deque()

    def push(self, x: int) -> None:
        self.queue.append(x)

        for _ in range(len(self.queue) - 1):
            self.queue.append(self.queue.popleft())

    def pop(self) -> int:
        return self.queue.popleft()

    def top(self) -> int:
        return self.queue[0]

    def empty(self) -> bool:
        return len(self.queue) == 0


# Create stack
stack = MyStack()

# Push elements
stack.push(10)
print("After push(10):", list(stack.queue))

stack.push(20)
print("After push(20):", list(stack.queue))

stack.push(30)
print("After push(30):", list(stack.queue))

# Top
print("top():", stack.top())

# Pop
print("pop():", stack.pop())
print("After pop():", list(stack.queue))

print("top():", stack.top())

print("pop():", stack.pop())
print("pop():", stack.pop())

print("empty():", stack.empty())
```

### Output

```text
After push(10): [10]
After push(20): [20, 10]
After push(30): [30, 20, 10]
top(): 30
pop(): 30
After pop(): [20, 10]
top(): 20
pop(): 20
pop(): 10
empty(): True
```

---

# 🔍 Detailed Dry Run

Start:

```text
queue = []
```

---

## Operation 1 — `push(10)`

Append:

```text
[10]
```

Number of old elements:

```text
len(queue) - 1 = 0
```

No rotation.

Result:

```text
FRONT
 ↓
[10]
```

Stack:

```text
TOP
 ↓
10
```

---

# Operation 2 — `push(20)`

Append:

```text
[10, 20]
```

Need:

```text
[20, 10]
```

Rotate once.

Remove front:

```text
10
```

Append it:

```text
[20, 10]
```

Now:

```text
FRONT
  ↓
20 → 10
```

Stack:

```text
TOP
 ↓
20
10
```

---

# Operation 3 — `push(30)`

Append:

```text
[20, 10, 30]
```

Need:

```text
[30, 20, 10]
```

### Rotation 1

Move `20`:

```text
[10, 30, 20]
```

### Rotation 2

Move `10`:

```text
[30, 20, 10]
```

Now:

```text
FRONT
 ↓
30 → 20 → 10
```

Stack:

```text
TOP
 ↓
30
20
10
```

---

# Operation 4 — `top()`

Front:

```text
30
```

Therefore:

```text
top() = 30
```

No modification.

---

# Operation 5 — `pop()`

Simply:

```python
popleft()
```

Remove:

```text
30
```

Queue:

```text
[20, 10]
```

Stack:

```text
TOP
 ↓
20
10
```

Correct.

---

# Operation 6 — `pop()`

Remove:

```text
20
```

Queue:

```text
[10]
```

---

# Operation 7 — `pop()`

Remove:

```text
10
```

Queue:

```text
[]
```

---

# Operation 8 — `empty()`

```text
len(queue) == 0
```

Therefore:

```text
True
```

---

# 📊 Complete Dry Run Table

| Operation  | Queue State  | Stack Interpretation | Result |
| ---------- | ------------ | -------------------- | ------ |
| Initial    | `[]`         | empty                | —      |
| `push(10)` | `[10]`       | `10`                 | —      |
| `push(20)` | `[20,10]`    | `20 → 10`            | —      |
| `push(30)` | `[30,20,10]` | `30 → 20 → 10`       | —      |
| `top()`    | `[30,20,10]` | top = `30`           | `30`   |
| `pop()`    | `[20,10]`    | `20 → 10`            | `30`   |
| `top()`    | `[20,10]`    | top = `20`           | `20`   |
| `pop()`    | `[10]`       | `10`                 | `20`   |
| `pop()`    | `[]`         | empty                | `10`   |
| `empty()`  | `[]`         | empty                | `True` |

---

# 🧠 Visual Transformation

The entire algorithm can be remembered visually:

```text
NORMAL QUEUE
10 → 20 → 30
↑           ↑
front      back
```

After `push(30)`:

```text
10 → 20 → 30
```

Rotate old elements:

```text
20 → 30 → 10
```

Rotate again:

```text
30 → 10 → 20
```

Now:

```text
STACK ORDER
30 → 20 → 10
↑
top
```

That's the trick.

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why is `push()` O(n)?

Because after inserting the new element, all previously existing elements must be moved behind it to make the new element the queue's front.

If there are `n` existing elements, we perform `n` rotations.

Therefore:

```text
O(n)
```

---

## Q2. Why is `pop()` O(1)?

Because we maintain the invariant:

```text
queue.front = stack.top
```

So removing the stack top is simply:

```python
queue.popleft()
```

which is O(1) with a deque.

---

## Q3. Can you implement it with two queues?

Yes.

One approach uses two queues and moves elements between them to ensure the newest element is available for pop.

But one queue is sufficient for this problem when we are willing to make `push()` O(n).

---

## Q4. Can you make `push()` O(1)?

Yes, but then `pop()` becomes O(n).

Keep elements in normal FIFO order:

```text
10 → 20 → 30
```

When popping, rotate the first `n-1` elements to the back until `30` reaches the front.

So:

```text
push → O(1)
pop  → O(n)
```

---

## Q5. Which design would you choose in production?

It depends on the workload.

If pushes are frequent and pops are rare:

```text
cheap push / expensive pop
```

may be preferable.

If pops are frequent:

```text
expensive push / cheap pop
```

may be preferable.

In an interview, explicitly state the trade-off rather than claiming one implementation is universally better.

---

## Q6. What is the deeper lesson from this problem?

The important concept is **maintaining an invariant through representation transformation**.

The queue itself remains FIFO, but we continuously rearrange its contents so that:

```text
queue front
     =
stack top
```

Once that invariant holds, stack operations become simple.

---

# 🔥 LC 933 → LC 622 → LC 225

You've now completed the entire **Queue Fundamentals** layer.

Look at what each problem taught:

### LC 933

```text
QUEUE
 ↓
FIFO
 ↓
TIME WINDOW
 ↓
EXPIRE OLD EVENTS
```

### LC 622

```text
QUEUE
 ↓
FIXED CAPACITY
 ↓
FRONT + REAR
 ↓
CIRCULAR INDEXING
 ↓
MODULO
```

### LC 225

```text
QUEUE
 ↓
FIFO
 ↓
REORDER
 ↓
SIMULATE LIFO
 ↓
DATA STRUCTURE DESIGN
```

So Level 1 is actually teaching three different dimensions:

```text
                 QUEUE
                   │
       ┌───────────┼───────────┐
       ↓           ↓           ↓
   Temporal      Memory      Abstraction
   Behavior      Layout       Design
       │           │           │
     LC933       LC622       LC225
```

---

# 🧩 LEVEL 1 MASTER TEMPLATE

You should now have these three mental templates.

## Template 1 — Queue + Expiration

```python
queue.append(event)

while queue[0] < current_time - window:
    queue.popleft()
```

**Recognition:**

```text
recent events
time window
expire old data
```

---

## Template 2 — Circular Queue

```python
index = (index + 1) % capacity
```

with:

```text
front
rear
size
capacity
```

**Recognition:**

```text
fixed capacity
reuse positions
circular buffer
```

---

## Template 3 — Queue → Stack

```python
queue.append(x)

for _ in range(len(queue) - 1):
    queue.append(queue.popleft())
```

Invariant:

```text
queue.front == stack.top
```

**Recognition:**

```text
implement LIFO using FIFO
```

---

# 🚨 SENIOR PATTERN RECOGNITION

The bigger lesson from Level 1 is:

```text
Don't ask:
"What code do I remember?"

Ask:
"What ordering does the problem require?"
```

### If requirement is:

```text
First come → first processed
```

Think:

# QUEUE

### If requirement is:

```text
Last come → first processed
```

Think:

# STACK

### If storage is fixed and reusable:

```text
QUEUE + MODULO
```

Think:

# CIRCULAR QUEUE

### If old events expire:

```text
QUEUE + TIME WINDOW
```

Think:

# QUEUE + EXPIRATION

### If you must implement one ordering using another:

```text
TRANSFORM ORDER
```

Think:

# DATA STRUCTURE DESIGN

---

# 🧠 LEVEL 1 — MASTERY CHECK

Before moving to BFS, you should be able to explain these **without looking at code**:

### 1. Why is Queue FIFO?

Because insertion happens at the back and removal happens at the front.

### 2. Why is LC 933 a queue?

Because timestamps arrive chronologically and expired elements are always removed from the oldest/front side.

### 3. Why is LC 622 circular?

Because fixed storage is reused by wrapping indices around using modulo.

### 4. Why does LC 622 need `size`?

To distinguish:

```text
empty
```

from:

```text
full
```

when `front == rear`.

### 5. Why does LC 225 require rotation?

Because a queue exposes the oldest element first, while a stack needs the newest element first.

### 6. What's the invariant in LC 225?

```text
queue.front == stack.top
```

If you can explain those six points, **Level 1 is conceptually complete.**

---

# 📌 PROGRESS UPDATE

```text
QUEUE / DEQUE
│
├── 🟢 LEVEL 1 — QUEUE FUNDAMENTALS
│   │
│   ├── ✅ LC 933 — Number of Recent Calls
│   ├── ✅ LC 622 — Design Circular Queue
│   └── ✅ LC 225 — Implement Stack using Queues  ← COMPLETE
│
├── 🟡 LEVEL 2 — BASIC BFS
│   │
│   ├── ⬜ LC 1971 — Find if Path Exists in Graph
│   └── ⬜ LC 1091 — Shortest Path in Binary Matrix
│
├── 🟠 LEVEL 3 — MULTI-SOURCE BFS
│   ├── ⬜ LC 994 — Rotting Oranges
│   ├── ⬜ LC 542 — 01 Matrix
│   └── ⬜ LC 1162 — As Far from Land as Possible
│
├── 🟣 LEVEL 4 — LEVEL-ORDER BFS
│   ├── ⬜ LC 102 — Binary Tree Level Order Traversal
│   └── ⬜ LC 199 — Binary Tree Right Side View
│
├── 🔴 LEVEL 5 — IMPLICIT STATE BFS
│   └── ⬜ LC 752 — Open the Lock
│
├── 🔴 LEVEL 6 — STATE TRANSFORMATION BFS
│   ├── ⬜ LC 127 — Word Ladder
│   └── ⬜ LC 433 — Minimum Genetic Mutation
│
├── 🟤 LEVEL 7 — TREE → GRAPH BFS
│   └── ⬜ LC 863 — All Nodes Distance K in Binary Tree
│
├── 🟦 LEVEL 8 — MONOTONIC DEQUE
│   └── ⬜ LC 239 — Sliding Window Maximum ⭐⭐⭐⭐⭐⭐
│
├── 🟦 LEVEL 9 — MULTIPLE MONOTONIC DEQUES
│   └── ⬜ LC 1438
│
├── 🟦 LEVEL 10 — PREFIX SUM + DEQUE
│   └── ⬜ LC 862
│
└── 🟥 LEVEL 11 — DP + DEQUE
    └── ⬜ LC 1696
```

# 🔑 ONE-LINE TAKEAWAY

> **LC 225 teaches that when a data structure gives you the wrong ordering, you can deliberately transform that ordering and maintain an invariant—in this case, keeping the newest element at the queue's front so FIFO can simulate LIFO.**

## 🚀 NEXT LOCKED STEP

**LEVEL 2 — BASIC BFS**

### **LC 1971 — Find if Path Exists in Graph**

This is the important transition:

```text
QUEUE
  ↓
QUEUE AS PROCESSING TOOL
  ↓
GRAPH
  ↓
BFS
  ↓
VISITED
  ↓
REACHABILITY
```

This is where **Queue stops being just a data structure and becomes an algorithmic engine.**

Would you like to start LC 1971 with the graph model first, or jump straight into the BFS template?



# LEVEL 2 — BASIC BFS
├── LC 1971
└── LC 1091


Absolutely bro. I'll regenerate **LC 1971** with the updated permanent structure. Everything stays at the same depth; the only structural addition is the mandatory **Algorithm — Step-by-Step** section immediately before the code.

# 🟡 LEVEL 2 — BASIC BFS

# LC 1971 — Find if Path Exists in Graph

> **Pattern:** Graph BFS + Visited Set
> **Priority:** 🔥🔥🔥
> **Difficulty:** Easy
> **Core Skill:** Graph Traversal + Queue + Reachability

The important transition from Level 1 is:

```text
QUEUE FUNDAMENTALS
        ↓
Queue as a processing mechanism
        ↓
GRAPH
        ↓
BFS
        ↓
REACHABILITY
```

LC 933 taught us **why a queue processes things in FIFO order**.

LC 622 taught us **how a queue can be implemented**.

LC 225 taught us **how ordering can be manipulated**.

Now LC 1971 teaches:

> **How FIFO ordering turns a queue into a graph-search algorithm.**

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given:

* `n` vertices numbered `0` through `n - 1`
* an undirected graph represented by `edges`
* a `source`
* a `destination`

You need to determine:

> **Is there any path from `source` to `destination`?**

Example:

```text
edges = [
    [0,1],
    [1,2],
    [2,3]
]
```

Graph:

```text
0 ─── 1 ─── 2 ─── 3
```

If:

```text
source = 0
destination = 3
```

then:

```text
0 → 1 → 2 → 3
```

exists.

Answer:

```text
True
```

---

# 2. Hidden Translation

The sentence:

> "Find if a path exists between two vertices."

should immediately become:

```text
PATH EXISTENCE
       ↓
GRAPH TRAVERSAL
       ↓
BFS / DFS
```

Because we're currently mastering Queue:

```text
GRAPH
  ↓
BFS
  ↓
QUEUE
```

This is the first major Queue → Algorithm connection.

---

# 3. What Is a Graph?

A graph consists of:

```text
VERTICES / NODES
+
EDGES / CONNECTIONS
```

For:

```text
edges = [
    [0,1],
    [1,2],
    [2,3]
]
```

we have:

```text
0 ─── 1 ─── 2 ─── 3
```

Vertices:

```text
0, 1, 2, 3
```

Edges:

```text
0—1
1—2
2—3
```

---

# 4. Why Is This an Undirected Graph?

This is extremely important.

If the input contains:

```text
[0, 1]
```

it means:

```text
0 → 1
```

and:

```text
1 → 0
```

are both possible.

Therefore:

```python
graph[0].append(1)
graph[1].append(0)
```

We need to store **both directions**.

For an undirected graph:

```text
[u, v]
```

means:

```text
u ↔ v
```

For a directed graph:

```text
u → v
```

we would only store:

```python
graph[u].append(v)
```

---

# 5. Why Do We Need an Adjacency List?

The input is an edge list:

```text
[[0,1], [1,2], [2,3]]
```

But BFS needs to repeatedly ask:

> "What can I visit from this node?"

For example:

```text
node = 1
```

We need:

```text
neighbors = [0,2]
```

So we transform:

```text
EDGE LIST
    ↓
ADJACENCY LIST
```

Result:

```text
0 → [1]
1 → [0,2]
2 → [1,3]
3 → [2]
```

Now neighbor lookup is direct.

---

# 6. Building the Adjacency List

Start:

```python
graph = [[] for _ in range(n)]
```

For:

```text
edges = [[0,1], [1,2], [2,3]]
```

process `[0,1]`:

```python
graph[0].append(1)
graph[1].append(0)
```

Now:

```text
0 → [1]
1 → [0]
```

Process `[1,2]`:

```text
1 → [0,2]
2 → [1]
```

Process `[2,3]`:

```text
2 → [1,3]
3 → [2]
```

Final:

```text
0 → [1]
1 → [0,2]
2 → [1,3]
3 → [2]
```

---

# 7. Why BFS?

BFS means:

# Breadth-First Search

It explores the graph outward from the source.

Suppose:

```text
       1
      / \
     2   3
    / \
   4   5
```

Starting from `1`:

```text
Level 0:
1

Level 1:
2, 3

Level 2:
4, 5
```

BFS processes:

```text
1 → 2 → 3 → 4 → 5
```

The exact order between nodes at the same level depends on adjacency ordering, but the **layer structure** is preserved.

---

# 8. Why Does a Queue Create BFS?

This is the most important concept in this problem.

Start:

```text
queue = [0]
```

Process `0`.

Suppose:

```text
graph[0] = [1,2]
```

Add:

```text
queue = [1,2]
```

Now `1` was discovered first, so FIFO says:

```text
process 1 first
```

Then its neighbors go to the **back**.

Therefore:

```text
earlier discovered
      ↓
processed earlier
      ↓
FIFO
      ↓
BFS
```

So the queue isn't just an implementation detail.

> **The queue is what enforces BFS's exploration order.**

---

# 9. ELI10 Intuition

Imagine dropping a stone into water.

The waves spread outward:

```text
             ○ ○ ○
          ○ ○ ○ ○ ○
       ○ ○ ○ S ○ ○ ○
          ○ ○ ○ ○ ○
             ○ ○ ○
```

`S` is the source.

BFS behaves similarly:

```text
source
  ↓
nearest nodes
  ↓
next layer
  ↓
next layer
  ↓
...
```

The queue stores the current **frontier** of this expanding wave.

---

# 10. What Is the BFS Frontier?

Suppose:

```text
      1
     / \
    2   3
   / \
  4   5
```

After processing `1`:

```text
visited = {1,2,3}
queue = [2,3]
```

The queue represents nodes that have been discovered but haven't yet expanded their own neighbors.

Therefore:

```text
QUEUE = CURRENT SEARCH FRONTIER
```

This concept becomes extremely important in:

* shortest path
* grid BFS
* multi-source BFS
* state-space BFS
* word ladder
* tree level-order traversal

---

# 11. Why Do We Need `visited`?

Graphs can contain cycles.

Example:

```text
0 ─── 1
│     │
└── 2 ┘
```

Starting from `0`:

```text
0 → 1 → 2 → 0 → 1 → 2 → ...
```

Without a visited set, the traversal can continue forever.

So:

```python
visited = set()
```

is required.

---

# 12. The Critical BFS Rule

Mark a node visited **when you enqueue it**.

Use:

```python
visited.add(neighbor)
queue.append(neighbor)
```

rather than:

```text
enqueue first
mark later
```

Why?

Because multiple nodes can discover the same neighbor.

Consider:

```text
    0
   / \
  1---2
```

From `0`:

```text
queue = [1,2]
```

When processing `1`, it sees `2`.

If `2` wasn't already marked visited, it could be added again.

By marking it when discovered:

```text
DISCOVER
   ↓
MARK VISITED
   ↓
ENQUEUE
```

we guarantee:

> **Every vertex enters the queue at most once.**

---

# 13. BFS State

There are three major pieces of state:

```text
graph
  ↓
What connections exist?

queue
  ↓
What nodes should I process next?

visited
  ↓
What nodes have already been discovered?
```

Visual:

```text
             GRAPH
               ↓
          CURRENT NODE
               ↓
           NEIGHBORS
               ↓
        ┌──────┴──────┐
        ↓             ↓
    VISITED         NEW
        ↓             ↓
      SKIP          MARK
                      ↓
                    QUEUE
```

---

# 14. BFS Invariant

The key invariant is:

> **Every node in `visited` has already been discovered, and every node in the queue has been discovered but is waiting to be processed.**

And most importantly:

> **No node is enqueued more than once.**

This guarantees:

```text
termination
+
efficient traversal
```

---

# 15. Why BFS Can Stop Early

Suppose we're searching for:

```text
destination = 5
```

When we discover:

```text
neighbor == 5
```

we can immediately return:

```python
True
```

We don't need to traverse the rest of the graph.

Because the question is only:

> "Does a path exist?"

not:

> "What are all reachable nodes?"

---

# 16. Could We Check Destination When Popping?

Yes.

You could write:

```python
node = queue.popleft()

if node == destination:
    return True
```

That's completely correct.

Another option is checking when discovering:

```python
if neighbor == destination:
    return True
```

Both are valid.

For a generic BFS template, checking after popping is often easier to remember:

```text
pop
 ↓
is this the target?
 ↓
yes → answer
no  → expand
```

We'll use that canonical form.

---

# 17. Why BFS and Not DFS?

For this particular problem:

```text
both BFS and DFS work
```

because we're only asking about reachability.

### DFS

```text
Go deep
 ↓
Backtrack
```

### BFS

```text
Expand outward
 ↓
Process frontier
```

BFS is chosen here because it establishes the pattern needed for the next problem:

```text
LC 1971
Path exists
     ↓
LC 1091
Shortest path
```

For an unweighted graph, BFS gives shortest distance naturally.

---

# 18. The Major BFS Insight

For **reachability**:

```text
BFS → Can I reach the target?
```

For **unweighted shortest path**:

```text
BFS → What is the minimum number of edges?
```

Why?

Because BFS processes nodes by increasing distance from the source.

```text
distance 0
    ↓
distance 1
    ↓
distance 2
    ↓
distance 3
```

Therefore the first time BFS reaches a node, it has reached it using the minimum number of edges.

We'll exploit this in LC 1091.

---

# 19. Complexity

Let:

```text
V = number of vertices
E = number of edges
```

### Building graph

Every edge is processed once.

For an undirected graph, each edge is stored twice:

```text
u → v
v → u
```

So:

```text
2E = O(E)
```

Therefore:

```text
Graph construction = O(E)
```

### BFS

Each vertex is discovered once:

```text
O(V)
```

Every adjacency entry is examined:

```text
O(E)
```

Therefore:

```text
BFS = O(V + E)
```

Total:

```text
O(V + E)
```

---

# 20. Space Complexity

Adjacency list:

```text
O(V + E)
```

Visited set:

```text
O(V)
```

Queue:

```text
O(V)
```

Total:

```text
O(V + E)
```

---

# 21. Recognition Rules

When you see:

### "Is there a path?"

```text
Graph traversal
```

### "Can I reach destination?"

```text
Reachability
```

### "Are these nodes connected?"

```text
BFS / DFS
```

### "Explore neighbors"

```text
Graph traversal
```

### "Shortest path in an unweighted graph"

```text
BFS
```

### "Minimum number of moves"

```text
BFS
```

### "Fewest steps"

```text
BFS
```

provided each move has equal cost.

---

# 22. Pattern Extraction

The reusable pattern is:

```text
EDGE LIST
    ↓
ADJACENCY LIST
    ↓
SOURCE
    ↓
QUEUE
    ↓
VISITED
    ↓
POP
    ↓
EXPLORE NEIGHBORS
    ↓
MARK + ENQUEUE
    ↓
REPEAT
```

This is your fundamental BFS engine.

---

# ⚙️ ALGORITHM — STEP-BY-STEP

Now convert the reasoning into an exact executable algorithm.

## Step 1 — Handle the trivial case

If:

```text
source == destination
```

we are already at the destination.

Return:

```text
True
```

---

## Step 2 — Build the adjacency list

Create:

```python
graph = [[] for _ in range(n)]
```

For every edge `[u, v]`:

```text
graph[u] ← v
graph[v] ← u
```

because the graph is undirected.

---

## Step 3 — Initialize BFS

Create a queue containing the source:

```text
queue = [source]
```

Create a visited set:

```text
visited = {source}
```

The source is already discovered.

---

## Step 4 — Process the queue

While the queue isn't empty:

```text
while queue:
```

remove the oldest discovered node:

```text
node = queue.popleft()
```

This is what gives us BFS ordering.

---

## Step 5 — Check whether we reached the destination

If:

```text
node == destination
```

return:

```text
True
```

---

## Step 6 — Explore all neighbors

For every:

```text
neighbor in graph[node]
```

check whether it has already been discovered.

If:

```text
neighbor in visited
```

skip it.

---

## Step 7 — Discover a new node

For an unvisited neighbor:

```text
visited.add(neighbor)
```

Then:

```text
queue.append(neighbor)
```

The order matters conceptually:

```text
DISCOVER
   ↓
MARK VISITED
   ↓
ENQUEUE
```

---

## Step 8 — Repeat

The queue now contains the next BFS frontier.

Continue:

```text
pop
 ↓
check
 ↓
expand
 ↓
mark
 ↓
enqueue
 ↓
repeat
```

---

## Step 9 — Queue becomes empty

If the queue becomes empty without finding `destination`:

```text
destination is unreachable
```

Return:

```text
False
```

---

# 💻 BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

```python
from collections import deque


class Solution:

    def validPath(self, n, edges, source, destination):

        # Already at destination
        if source == destination:
            return True

        # Build adjacency list
        graph = [[] for _ in range(n)]

        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)

        # BFS initialization
        queue = deque([source])
        visited = {source}

        while queue:

            node = queue.popleft()

            # Destination reached
            if node == destination:
                return True

            # Explore neighbors
            for neighbor in graph[node]:

                if neighbor in visited:
                    continue

                visited.add(neighbor)
                queue.append(neighbor)

        return False
```

---

# 🔍 Why This Is Efficient

### Adjacency list

Instead of repeatedly scanning all edges, we can directly access:

```python
graph[node]
```

to get the neighbors.

### `deque`

We need:

```python
popleft()
```

which is:

```text
O(1)
```

A Python list with:

```python
pop(0)
```

would be O(n).

### `visited`

Prevents duplicate traversal and cycles.

---

# ⏱️ Complexity

Let:

```text
V = vertices
E = edges
```

### Time

```text
Build graph → O(E)
BFS          → O(V + E)

Total        → O(V + E)
```

### Space

```text
Adjacency list → O(V + E)
Visited        → O(V)
Queue          → O(V)

Total          → O(V + E)
```

---

# 🎤 Interview Justification

If the interviewer says:

> "Explain your solution."

Give this:

> "I represent the undirected graph using an adjacency list. Then I perform BFS starting from the source using a deque. I maintain a visited set and mark nodes as soon as they're enqueued so each node is processed at most once. If the destination is dequeued, a path exists; if the queue becomes empty, it's unreachable. The overall complexity is O(V + E) time and O(V + E) space."

That's a strong interview-level answer.

---

~~~
from collections import deque   # Import deque for efficient queue operations (FIFO)

class Solution:

    def validPath(self, numberOfNodes, edgeList, sourceNode, destinationNode):

        # If source and destination are the same, path exists immediately
        if sourceNode == destinationNode:
            return True

        # -----------------------------
        # Step 1: Build adjacency list
        # -----------------------------
        graph = [[] for _ in range(numberOfNodes)]   # Create empty neighbor list for each node

        for startNode, endNode in edgeList:          # Iterate through each edge in the graph
            graph[startNode].append(endNode)         # Add connection from start → end
            graph[endNode].append(startNode)         # Add connection from end → start (undirected)

        # -----------------------------
        # Step 2: Initialize BFS
        # -----------------------------
        queue = deque([sourceNode])                  # Start BFS from the source node
        visitedNodes = {sourceNode}                  # Track visited nodes to avoid revisiting

        # -----------------------------
        # Step 3: BFS traversal
        # -----------------------------
        while queue:                                 # While there are nodes to process
            currentNode = queue.popleft()            # Pop from queue (FIFO order)

            # If we reached the destination → path exists
            if currentNode == destinationNode:
                return True

            # Explore all neighbors of the current node
            for neighborNode in graph[currentNode]:
                if neighborNode in visitedNodes:     # Skip already visited nodes
                    continue
                visitedNodes.add(neighborNode)       # Mark neighbor as visited
                queue.append(neighborNode)           # Add neighbor to queue for BFS

        # -----------------------------
        # Step 4: No path found
        # -----------------------------
        return False                                 # If BFS finishes without finding destination → no path


# -----------------------------
# Example usage
# -----------------------------

numberOfNodes = 6

edgeList = [
    [0, 1],
    [0, 2],
    [1, 3],
    [2, 4],
    [4, 5]
]

sourceNode = 0
destinationNode = 5

# Create object
solution = Solution()

# Call function
result = solution.validPath(
    numberOfNodes,
    edgeList,
    sourceNode,
    destinationNode
)

print("Path exists:", result)   # Expected output: True


~~~

# 💻 BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

```python
from collections import deque


class Solution:

    def validPath(self, n, edges, source, destination):

        if source == destination:
            return True

        # Build adjacency list
        graph = [[] for _ in range(n)]

        for u, v in edges:
            graph[u].append(v)
            graph[v].append(u)

        # BFS
        queue = deque([source])
        visited = {source}

        while queue:

            node = queue.popleft()

            if node == destination:
                return True

            for neighbor in graph[node]:

                if neighbor in visited:
                    continue

                visited.add(neighbor)
                queue.append(neighbor)

        return False


# -----------------------------
# Example
# -----------------------------

n = 6

edges = [
    [0, 1],
    [0, 2],
    [1, 3],
    [2, 4],
    [4, 5]
]

source = 0
destination = 5

# Create object
solution = Solution()

# Call function
result = solution.validPath(
    n,
    edges,
    source,
    destination
)

print("Path exists:", result)
```

### Output

```text
Path exists: True
```

---

# 🔍 STEP 1 — Build the Graph

Input:

```text
n = 6

edges:
0 — 1
0 — 2
1 — 3
2 — 4
4 — 5
```

Adjacency list:

```text
0 → [1, 2]
1 → [0, 3]
2 → [0, 4]
3 → [1]
4 → [2, 5]
5 → [4]
```

Visual:

```text
        3
        |
        1
        |
        0
        |
        2
        |
        4
        |
        5
```

with the important additional connection:

```text
0 — 2
```

So more accurately:

```text
        3
        |
        1
        |
        0
       / \
      2
      |
      4
      |
      5
```

---

# 🔍 STEP 2 — Initialize BFS

Source:

```text
0
```

Destination:

```text
5
```

Queue:

```text
[0]
```

Visited:

```text
{0}
```

State:

```text
queue   = [0]
visited = {0}
```

---

# 🔍 STEP 3 — Process Node `0`

Remove:

```text
0
```

Queue:

```text
[]
```

Check:

```text
0 == 5
```

False.

Neighbors:

```text
[1, 2]
```

---

### Neighbor `1`

Not visited.

Mark:

```text
visited = {0,1}
```

Enqueue:

```text
queue = [1]
```

---

### Neighbor `2`

Not visited.

Mark:

```text
visited = {0,1,2}
```

Enqueue:

```text
queue = [1,2]
```

Current state:

```text
queue   = [1,2]
visited = {0,1,2}
```

---

# 🔍 STEP 4 — Process Node `1`

Queue:

```text
[1,2]
```

Pop:

```text
1
```

Queue:

```text
[2]
```

Check:

```text
1 == 5
```

False.

Neighbors:

```text
[0,3]
```

`0`:

```text
already visited
```

Skip.

`3`:

```text
unvisited
```

Mark:

```text
visited = {0,1,2,3}
```

Enqueue:

```text
queue = [2,3]
```

---

# 🔍 STEP 5 — Process Node `2`

Queue:

```text
[2,3]
```

Pop:

```text
2
```

Queue:

```text
[3]
```

Neighbors:

```text
[0,4]
```

`0` is visited.

`4` is new.

Mark:

```text
visited = {0,1,2,3,4}
```

Queue:

```text
[3,4]
```

---

# 🔍 STEP 6 — Process Node `3`

Pop:

```text
3
```

Queue:

```text
[4]
```

Neighbor:

```text
1
```

Already visited.

Nothing added.

---

# 🔍 STEP 7 — Process Node `4`

Pop:

```text
4
```

Queue:

```text
[]
```

Neighbors:

```text
[2,5]
```

`2` is already visited.

`5` is new.

Add:

```text
visited = {0,1,2,3,4,5}
queue = [5]
```

---

# 🔍 STEP 8 — Process Node `5`

Pop:

```text
5
```

Check:

```text
5 == destination
```

Yes.

Therefore:

```text
return True
```

---

# 📊 Complete Dry Run Table

| Step | Popped | Queue After Pop | New Nodes   | Visited         |
| ---: | -----: | --------------- | ----------- | --------------- |
|    0 |      — | `[0]`           | —           | `{0}`           |
|    1 |    `0` | `[]`            | `1,2`       | `{0,1,2}`       |
|    2 |    `1` | `[2]`           | `3`         | `{0,1,2,3}`     |
|    3 |    `2` | `[3]`           | `4`         | `{0,1,2,3,4}`   |
|    4 |    `3` | `[4]`           | none        | `{0,1,2,3,4}`   |
|    5 |    `4` | `[]`            | `5`         | `{0,1,2,3,4,5}` |
|    6 |    `5` | `[]`            | destination | `{0,1,2,3,4,5}` |

Result:

```text
True
```

---

# 🧠 THE BFS FRONTIER

This is worth understanding deeply.

At the beginning:

```text
Frontier:
[0]
```

After processing `0`:

```text
Frontier:
[1,2]
```

After processing `1`:

```text
Frontier:
[2,3]
```

After processing `2`:

```text
Frontier:
[3,4]
```

After processing `3`:

```text
Frontier:
[4]
```

After processing `4`:

```text
Frontier:
[5]
```

Then:

```text
5 → destination
```

So BFS can be understood as:

> **Repeatedly consume the current frontier and generate the next frontier.**

The queue is the mechanism that stores that frontier.

---

# 🚨 CYCLE EXAMPLE

Consider:

```text
0 ─── 1
│     │
2 ─── 3
```

Start:

```text
0
```

Without `visited`:

```text
0 → 1 → 3 → 2 → 0 → 1 → 3 → ...
```

Infinite repetition.

With:

```python
visited = {0}
```

we get:

```text
0
 ↓
1,2
 ↓
3
```

When `3` encounters `0`:

```text
0 ∈ visited
```

so we skip it.

Therefore:

```text
visited
    ↓
cycle protection
+
duplicate prevention
```

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why does BFS use a queue?

### Answer

BFS needs to process nodes in the same order in which they are discovered. A queue provides FIFO ordering, so earlier discovered nodes are processed before later discovered nodes. This produces level-by-level graph exploration.

---

## Q2. Why do you need a visited set?

### Answer

Graphs can contain cycles and multiple paths can reach the same node. Without a visited set, nodes could be processed repeatedly or traversal could become infinite. Marking nodes when they are discovered ensures each node is enqueued at most once.

---

## Q3. Why mark visited when enqueuing rather than dequeuing?

### Answer

Because a node can be discovered by multiple neighbors before it gets dequeued. Marking it immediately when enqueued prevents duplicate queue entries and guarantees each node is scheduled for processing only once.

---

## Q4. Why use an adjacency list?

### Answer

BFS repeatedly needs the neighbors of the current node. An adjacency list gives direct access to those neighbors. Using the original edge list would require repeatedly scanning all edges, which can increase the complexity unnecessarily.

---

## Q5. Could DFS solve this problem?

### Answer

Yes. This is a reachability problem, so both DFS and BFS can determine whether a path exists. BFS is used here because the next problems build on BFS's ability to process graph states by increasing distance.

---

## Q6. Why is the complexity O(V + E)?

### Answer

Each vertex is discovered at most once, contributing O(V). Each adjacency entry is examined once, contributing O(E). Building the adjacency list also takes O(E). Therefore the total complexity is O(V + E).

---

# 🔥 BFS MASTER TEMPLATE

This is the template you should start memorizing conceptually.

```python
from collections import deque

queue = deque([source])
visited = {source}

while queue:

    node = queue.popleft()

    for neighbor in graph[node]:

        if neighbor in visited:
            continue

        visited.add(neighbor)
        queue.append(neighbor)
```

Don't memorize this as a code block only.

Understand the flow:

```text
SOURCE
  ↓
QUEUE
  ↓
POP
  ↓
NEIGHBORS
  ↓
UNVISITED?
  ↓
MARK
  ↓
QUEUE
  ↓
REPEAT
```

---

# 🧩 GRAPH BFS MASTER TEMPLATE

For an undirected graph:

```python
from collections import deque

graph = [[] for _ in range(n)]

for u, v in edges:
    graph[u].append(v)
    graph[v].append(u)

queue = deque([source])
visited = {source}

while queue:

    node = queue.popleft()

    for neighbor in graph[node]:

        if neighbor in visited:
            continue

        visited.add(neighbor)
        queue.append(neighbor)
```

Then modify the final logic depending on the problem.

### Reachability

```python
if node == destination:
    return True
```

### Shortest distance

Add a distance/level mechanism.

### Level processing

Use:

```python
level_size = len(queue)
```

### Multi-source BFS

Initialize queue with **all sources**.

### State-space BFS

Generate neighbors dynamically rather than from an explicit adjacency list.

This one template will evolve through the rest of your Queue/Deque roadmap.

---

# 🚨 SENIOR PATTERN RECOGNITION

When you see:

```text
GRAPH
+
SOURCE
+
DESTINATION
+
CAN REACH?
```

think:

# `BFS / DFS`

When you see:

```text
GRAPH
+
UNWEIGHTED
+
SHORTEST / MINIMUM / FEWEST
```

think:

# `BFS`

When you see:

```text
GRAPH
+
CYCLES
```

think:

# `VISITED`

When you see:

```text
EDGE LIST
```

and need neighbor traversal:

```text
EDGE LIST
    ↓
ADJACENCY LIST
```

When you see:

```text
QUEUE
+
GRAPH
```

think:

# `BFS`

---

# 🔗 LC 1971 → LC 1091

This is the most important progression.

## LC 1971

```text
GRAPH
 ↓
BFS
 ↓
QUEUE
 ↓
VISITED
 ↓
REACHABILITY
```

Then:

## LC 1091

```text
GRID
 ↓
IMPLICIT GRAPH
 ↓
CELL = NODE
 ↓
VALID MOVE = EDGE
 ↓
BFS
 ↓
LEVEL = DISTANCE
 ↓
SHORTEST PATH
```

The BFS engine remains almost the same.

Only the **representation of the graph** changes.

That's exactly what pattern mastery means:

> **Recognize the invariant algorithm underneath the changing problem surface.**

---

# 🧠 WHAT LC 1971 REALLY TAUGHT YOU

Don't leave this problem thinking:

> "I learned one graph problem."

You learned:

```text
1. Graph representation
        ↓
2. Adjacency list
        ↓
3. Queue as BFS frontier
        ↓
4. Visited for cycle protection
        ↓
5. Neighbor generation
        ↓
6. Reachability
        ↓
7. O(V + E) traversal
```

The deepest idea is:

> **BFS is controlled expansion of a frontier.**

---

# 📌 LEVEL 2 PROGRESS

```text
QUEUE / DEQUE
│
├── 🟢 LEVEL 1 — QUEUE FUNDAMENTALS
│   ├── ✅ LC 933 — Number of Recent Calls
│   ├── ✅ LC 622 — Design Circular Queue
│   └── ✅ LC 225 — Implement Stack using Queues
│
├── 🟡 LEVEL 2 — BASIC BFS
│   │
│   ├── ✅ LC 1971 — Find if Path Exists in Graph
│   └── ⬜ LC 1091 — Shortest Path in Binary Matrix  ← NEXT
│
├── 🟠 LEVEL 3 — MULTI-SOURCE BFS
│   ├── ⬜ LC 994
│   ├── ⬜ LC 542
│   └── ⬜ LC 1162
│
├── 🟣 LEVEL 4 — LEVEL-ORDER BFS
│   ├── ⬜ LC 102
│   └── ⬜ LC 199
│
├── 🔴 LEVEL 5 — IMPLICIT STATE BFS
│   └── ⬜ LC 752
│
├── 🔴 LEVEL 6 — STATE TRANSFORMATION BFS
│   ├── ⬜ LC 127
│   └── ⬜ LC 433
│
├── 🟤 LEVEL 7 — TREE → GRAPH BFS
│   └── ⬜ LC 863
│
├── 🟦 LEVEL 8 — MONOTONIC DEQUE
│   └── ⬜ LC 239 ⭐⭐⭐⭐⭐⭐
│
├── 🟦 LEVEL 9 — MULTIPLE MONOTONIC DEQUES
│   └── ⬜ LC 1438
│
├── 🟦 LEVEL 10 — PREFIX SUM + DEQUE
│   └── ⬜ LC 862
│
└── 🟥 LEVEL 11 — DP + DEQUE
    └── ⬜ LC 1696
```

# 🔑 ONE-LINE TAKEAWAY

> **LC 1971 teaches the fundamental BFS engine: represent the graph with adjacency lists, use a queue as the search frontier, mark nodes when discovered, and expand unvisited neighbors until the target is reached or the frontier is exhausted.**

### 🔒 Next locked problem

**LC 1091 — Shortest Path in Binary Matrix**

The new concept will be:

```text
EXPLICIT GRAPH
      ↓
IMPLICIT GRAPH
      ↓
GRID CELL = NODE
      ↓
MOVEMENT = EDGE
      ↓
BFS
      ↓
DISTANCE
      ↓
SHORTEST PATH
```

And I'll maintain **this exact structure and depth**, including the mandatory **Algorithm — Step-by-Step** section.

Would you like me to continue with LC 1091 using this exact structure and depth?



# 🚀 LC 1091 — Shortest Path in Binary Matrix

**Level 2 — Basic BFS**
**Pattern:** Grid BFS + Shortest Path
**Priority:** 🔥🔥🔥🔥
**Difficulty:** Medium

This is the **direct evolution of LC 1971**.

> **LC 1971:** Graph + BFS → “Can I reach the destination?”
> **LC 1091:** Grid + BFS → “What is the shortest distance to the destination?”

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given an `n × n` binary matrix:

```text
0 = open cell
1 = blocked cell
```

You start at:

```text
(0, 0)
```

and want to reach:

```text
(n-1, n-1)
```

You can move in **8 directions**:

```text
↖  ↑  ↗
←  X  →
↙  ↓  ↘
```

You can only move through `0`s.

Return the **length of the shortest path**.

If no path exists:

```text
return -1
```

---

# 2. 🔥 Hidden Translation

The most important interview skill is translating the problem into a known pattern.

When you see:

> **Shortest path in an unweighted grid**

Immediately think:

```text
GRID
 ↓
Each cell = NODE
 ↓
Each valid movement = EDGE
 ↓
All edges have equal cost
 ↓
BFS
```

This is exactly the graph logic from LC 1971.

The only difference is:

**LC 1971 explicitly gives you the graph.**

Here, the graph is **implicit**.

---

# 3. Grid → Graph Translation

Suppose:

```text
[
 [0,0,1],
 [1,0,0],
 [1,1,0]
]
```

Think of every open cell as a graph node.

```text
(0,0) —— (0,1)
          |
        (1,1) —— (1,2)
                   |
                 (2,2)
```

You don't actually build this graph.

Instead, when standing at:

```text
(r, c)
```

you generate its neighboring nodes using the 8 directions.

That's called an:

> **Implicit Graph**

---

# 4. Why BFS?

Suppose:

```text
S → A → B → D
```

The path length is `4` cells.

BFS explores:

```text
distance 1
    ↓
distance 2
    ↓
distance 3
    ↓
distance 4
```

Therefore, the **first time BFS reaches the destination, it has found the shortest path**.

Why?

Because BFS explores nodes in increasing distance from the source.

```text
        distance 1

    distance 2

        distance 3

            distance 4
```

This property is why BFS is perfect here.

---

# 5. Why Not DFS?

DFS can determine whether a path exists.

But DFS does **not naturally guarantee the shortest path**.

Example:

```text
        A
       / \
      B   C
      |   |
      D   E
       \ /
        F
```

DFS might discover:

```text
S → A → B → D → F
```

before:

```text
S → A → C → E → F
```

even if the second route is shorter.

You could make DFS work by exploring all possibilities, but that can become extremely expensive.

BFS gives shortest path directly.

---

# 6. Why Is This Different From LC 1971?

This distinction is extremely important.

### LC 1971

Question:

> Does a path exist?

You only need:

```text
visited
```

### LC 1091

Question:

> What is the shortest path?

You need:

```text
BFS
+
distance / level
```

So:

```text
LC 1971
Reachability
    ↓
BFS

LC 1091
Shortest distance
    ↓
BFS levels
```

---

# 7. ELI10 Intuition 🧒

Imagine you're standing in a maze.

You shout:

> "Everyone one step away from me, move!"

Then:

> "Everyone two steps away, move!"

Then:

> "Everyone three steps away, move!"

You expand outward like a wave.

```text
        3
      3 2 3
    3 2 1 2 3
      3 2 3
        3
```

The wave reaches the destination.

The number of the wave is the shortest distance.

That's BFS.

---

# 8. The Queue Is the Frontier

This connects directly to LC 1971.

In LC 1971:

```text
queue = nodes waiting to be explored
```

Here:

```text
queue = cells waiting to be explored
```

Example:

```text
queue

[(0,0)]
   ↓
[(0,1),(1,0),(1,1)]
   ↓
[next layer]
```

The queue represents the current exploration frontier.

---

# 9. Why 8 Directions?

Unlike a normal four-direction grid:

```text
↑
← X →
↓
```

this problem allows diagonals:

```text
↖ ↑ ↗
← X →
↙ ↓ ↘
```

So define:

```python
directions = [
    (-1, -1),
    (-1,  0),
    (-1,  1),
    ( 0, -1),
    ( 0,  1),
    ( 1, -1),
    ( 1,  0),
    ( 1,  1)
]
```

This is a very reusable grid-BFS template.

---

# 10. Important Early Rejection

Two cells must be open:

```text
grid[0][0] == 0
grid[n-1][n-1] == 0
```

If either is blocked:

```text
return -1
```

Because you cannot start or finish.

---

# 11. How Do We Track Distance?

There are two common approaches.

### Method 1 — Store distance in queue

```python
queue.append((r, c, distance))
```

Example:

```text
(0,0,1)
(0,1,2)
(1,1,2)
```

This is very explicit and easy to understand.

### Method 2 — BFS level counting

Process one entire BFS layer at a time:

```python
distance = 1

while queue:
    for _ in range(len(queue)):
        ...
    distance += 1
```

Both are valid.

For this problem, I recommend **storing distance in the queue** because it keeps the implementation straightforward.

---

# 12. Visited Strategy

We must prevent revisiting cells.

A very clean trick is:

```python
grid[nr][nc] = 1
```

when we enqueue a cell.

That converts:

```text
0 → 1
```

meaning:

> This cell has now been discovered/visited.

This avoids needing a separate `visited` matrix.

---

# 13. Why Mark When Enqueuing?

This is an important interview detail.

Suppose:

```text
A → B
C → B
```

If we wait until dequeuing to mark `B` visited:

```text
A discovers B
C also discovers B
```

Now `B` can enter the queue multiple times.

Instead:

```text
discover B
 ↓
mark B immediately
 ↓
enqueue B
```

Then anyone else sees:

```text
B is already visited
```

So:

> **Mark visited when enqueuing, not when dequeuing.**

This is the same principle from LC 1971.

---

# 14. Core Invariant

After each BFS operation:

> Every cell in the queue has already been discovered, every discovered cell has the shortest possible distance assigned to it, and no cell is enqueued more than once.

This invariant is the reason the algorithm is correct.

---

# 15. Mathematical View

Let:

```text
d(r,c)
```

represent the shortest number of cells needed to reach `(r,c)`.

For every valid neighbor:

```text
d(neighbor) = d(current) + 1
```

BFS guarantees that the first discovered distance is optimal.

---

# 16. Why the Answer Counts Cells, Not Edges

This is a subtle LC 1091 detail.

Suppose:

```text
(0,0) → (0,1) → (1,2)
```

There are:

```text
2 edges
```

but:

```text
3 cells
```

LeetCode asks for path **length in cells**.

So the starting cell has distance:

```text
1
```

not:

```text
0
```

Therefore:

```python
queue = deque([(0, 0, 1)])
```

---

# 17. Complexity

Let:

```text
n × n
```

be the grid.

Number of cells:

```text
n²
```

Each cell can be processed once.

For each cell we examine at most:

```text
8 directions
```

Therefore:

```text
O(8n²)
```

which simplifies to:

```text
O(n²)
```

Space:

```text
Queue → O(n²)
```

No separate visited matrix is required because we modify the grid.

Therefore:

```text
Time  = O(n²)
Space = O(n²)
```

---

# 18. Senior Pattern Recognition

When you see:

```text
grid
+
shortest path
+
equal movement cost
```

think:

```text
Grid BFS
```

When you see:

```text
grid
+
shortest distance
+
multiple starting points
```

think:

```text
Multi-Source BFS
```

That's coming next with:

🔥 **LC 994 — Rotting Oranges**

---

# ⚙️ ALGORITHM — STEP-BY-STEP

### Step 1 → Check start and destination

If either:

```text
grid[0][0] == 1
```

or:

```text
grid[n-1][n-1] == 1
```

return:

```text
-1
```

because the path cannot exist.

---

### Step 2 → Define the 8 possible movements

Create:

```text
(-1,-1)
(-1, 0)
(-1,+1)
( 0,-1)
( 0,+1)
(+1,-1)
(+1, 0)
(+1,+1)
```

Each represents one legal move.

---

### Step 3 → Initialize the BFS queue

Put the starting cell into the queue:

```text
(row, column, distance)
```

with:

```text
(0, 0, 1)
```

Distance is `1` because the path includes the starting cell.

---

### Step 4 → Mark the starting cell visited

Set:

```python
grid[0][0] = 1
```

Now it cannot be inserted again.

---

### Step 5 → Pop the next cell

Use:

```python
r, c, distance = queue.popleft()
```

This gives us the next cell in BFS order.

---

### Step 6 → Check whether it is the destination

If:

```python
r == n - 1 and c == n - 1
```

return:

```python
distance
```

Because BFS reaches cells in shortest-distance order.

---

### Step 7 → Generate all 8 neighbors

For each direction:

```python
nr = r + dr
nc = c + dc
```

---

### Step 8 → Validate the neighbor

A neighbor is usable only if:

```text
0 <= nr < n
0 <= nc < n
grid[nr][nc] == 0
```

This guarantees:

* inside the grid
* not blocked
* not already visited

---

### Step 9 → Mark before enqueueing

Set:

```python
grid[nr][nc] = 1
```

Then:

```python
queue.append((nr, nc, distance + 1))
```

---

### Step 10 → Continue BFS

Repeat until:

```text
destination found
```

or:

```text
queue becomes empty
```

---

### Step 11 → If queue becomes empty

There is no reachable path.

Return:

```text
-1
```

---

# 💻 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def shortestPathBinaryMatrix(self, grid):

        n = len(grid)

        # Start or destination is blocked
        if grid[0][0] == 1 or grid[n - 1][n - 1] == 1:
            return -1

        # Eight possible directions
        directions = [
            (-1, -1),
            (-1, 0),
            (-1, 1),
            (0, -1),
            (0, 1),
            (1, -1),
            (1, 0),
            (1, 1)
        ]

        # (row, column, distance)
        queue = deque([(0, 0, 1)])

        # Mark starting cell visited
        grid[0][0] = 1

        while queue:

            r, c, distance = queue.popleft()

            # Destination reached
            if r == n - 1 and c == n - 1:
                return distance

            # Explore all 8 neighbors
            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                # Valid and unvisited cell
                if (
                    0 <= nr < n
                    and 0 <= nc < n
                    and grid[nr][nc] == 0
                ):
                    grid[nr][nc] = 1

                    queue.append(
                        (nr, nc, distance + 1)
                    )

        return -1
```

---

## Complexity

There are `n²` cells.

Each cell:

```text
processed at most once
```

and checks:

```text
8 directions
```

Therefore:

```text
Time = O(n²)
```

The queue can contain up to `n²` cells:

```text
Space = O(n²)
```

The grid itself is modified in-place, so we don't need another `visited` matrix.

---

## 🎤 What to Say to the Interviewer

> "This is a shortest-path problem on an unweighted implicit graph. Each open grid cell represents a node and each of the eight legal movements represents an edge. Since all edges have equal cost, I use BFS. I mark cells visited when I enqueue them to prevent duplicates. Because BFS explores nodes in increasing distance order, the first time I reach the bottom-right cell gives the shortest path. The algorithm runs in O(n²) time and O(n²) auxiliary space."

That is a **strong interview answer**.

---

# 🧪 BLOCK 3 — FULL CODE + DRY RUN

Let's use:

```text
[
 [0,0,0],
 [1,1,0],
 [1,1,0]
]
```

Visualize it:

```text
S  .  .
X  X  .
X  X  D
```

Where:

```text
S = start
D = destination
X = blocked
. = open
```

Shortest path:

```text
(0,0)
   ↓
(0,1)
   ↘
  (1,2)
    ↓
  (2,2)
```

Answer:

```text
4
```

---

## Full Runnable Code

~~~
from collections import deque   # Import deque for efficient queue operations (FIFO)

class Solution:

    def shortestPathBinaryMatrix(self, grid):

        n = len(grid)   # Size of the grid (n x n)

        # If start or end cell is blocked (value = 1), no path exists
        if grid[0][0] == 1 or grid[n - 1][n - 1] == 1:
            return -1

        # All 8 possible directions (up, down, left, right, and diagonals)
        directions = [
            (-1, -1),   # top-left
            (-1, 0),    # up
            (-1, 1),    # top-right
            (0, -1),    # left
            (0, 1),     # right
            (1, -1),    # bottom-left
            (1, 0),     # down
            (1, 1)      # bottom-right
        ]

        # Initialize BFS queue with starting cell (row=0, col=0, distance=1)
        queue = deque([(0, 0, 1)])

        # Mark starting cell as visited by setting it to 1
        grid[0][0] = 1

        # BFS traversal
        while queue:

            currentRow, currentCol, currentDistance = queue.popleft()

            # If we reached bottom-right cell → return path length
            if currentRow == n - 1 and currentCol == n - 1:
                return currentDistance

            # Explore all 8 directions
            for deltaRow, deltaCol in directions:

                nextRow = currentRow + deltaRow
                nextCol = currentCol + deltaCol

                # Check boundaries and if cell is open (value = 0)
                if (
                    0 <= nextRow < n
                    and 0 <= nextCol < n
                    and grid[nextRow][nextCol] == 0
                ):
                    # Mark cell as visited
                    grid[nextRow][nextCol] = 1

                    # Add new cell to queue with incremented distance
                    queue.append(
                        (nextRow, nextCol, currentDistance + 1)
                    )

        # If BFS finishes without reaching destination → no path
        return -1


# -------------------------
# Example usage
# -------------------------

grid = [
    [0, 0, 0],
    [1, 1, 0],
    [1, 1, 0]
]

solution = Solution()

result = solution.shortestPathBinaryMatrix(grid)

print("Shortest Path Length:", result)   # Expected output: 4


~~~

```python
from collections import deque


class Solution:

    def shortestPathBinaryMatrix(self, grid):

        n = len(grid)

        if grid[0][0] == 1 or grid[n - 1][n - 1] == 1:
            return -1

        directions = [
            (-1, -1),
            (-1, 0),
            (-1, 1),
            (0, -1),
            (0, 1),
            (1, -1),
            (1, 0),
            (1, 1)
        ]

        queue = deque([(0, 0, 1)])

        grid[0][0] = 1

        while queue:

            r, c, distance = queue.popleft()

            if r == n - 1 and c == n - 1:
                return distance

            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                if (
                    0 <= nr < n
                    and 0 <= nc < n
                    and grid[nr][nc] == 0
                ):
                    grid[nr][nc] = 1

                    queue.append(
                        (nr, nc, distance + 1)
                    )

        return -1


# -------------------------
# Example
# -------------------------

grid = [
    [0, 0, 0],
    [1, 1, 0],
    [1, 1, 0]
]

solution = Solution()

result = solution.shortestPathBinaryMatrix(grid)

print("Shortest Path Length:", result)
```

### Output

```text
Shortest Path Length: 4
```

---

# 🔬 Detailed Dry Run

Initial:

```text
queue = [(0,0,1)]
```

Grid:

```text
0 0 0
1 1 0
1 1 0
```

We mark `(0,0)` visited:

```text
1 0 0
1 1 0
1 1 0
```

---

## Step 1

Pop:

```text
(0,0,1)
```

Possible neighbors:

```text
(-1,-1) ❌ outside
(-1, 0) ❌ outside
(-1, 1) ❌ outside
( 0,-1) ❌ outside
( 0, 1) ✅
( 1,-1) ❌ outside
( 1, 0) ❌ blocked
( 1, 1) ❌ blocked
```

Enqueue:

```text
(0,1,2)
```

Queue:

```text
[(0,1,2)]
```

---

## Step 2

Pop:

```text
(0,1,2)
```

Neighbors include:

```text
(0,0) → visited
(0,2) → valid
(1,0) → blocked
(1,1) → blocked
(1,2) → valid
```

Enqueue:

```text
(0,2,3)
(1,2,3)
```

Queue:

```text
[(0,2,3), (1,2,3)]
```

---

## Step 3

Pop:

```text
(0,2,3)
```

Neighbors:

```text
(0,1) → visited
(1,1) → blocked
(1,2) → already visited
```

Nothing new.

Queue:

```text
[(1,2,3)]
```

---

## Step 4

Pop:

```text
(1,2,3)
```

Neighbor:

```text
(2,2)
```

is valid.

Enqueue:

```text
(2,2,4)
```

Queue:

```text
[(2,2,4)]
```

---

## Step 5

Pop:

```text
(2,2,4)
```

This is:

```text
destination
```

Return:

```text
4
```

---

# 📊 Dry-Run Table

| Step | Popped Cell | Distance | New Cells     | Queue After         |
| ---: | ----------- | -------: | ------------- | ------------------- |
|    0 | —           |        — | `(0,0)`       | `[(0,0,1)]`         |
|    1 | `(0,0)`     |        1 | `(0,1)`       | `[(0,1,2)]`         |
|    2 | `(0,1)`     |        2 | `(0,2),(1,2)` | `[(0,2,3),(1,2,3)]` |
|    3 | `(0,2)`     |        3 | none          | `[(1,2,3)]`         |
|    4 | `(1,2)`     |        3 | `(2,2)`       | `[(2,2,4)]`         |
|    5 | `(2,2)`     |        4 | destination   | `[]`                |

Therefore:

```text
Answer = 4
```

---

# 🧠 Visual BFS Expansion

```text
Distance 1:

1 . .
X X .
X X .
```

Then:

```text
Distance 2:

1 2 .
X X .
X X .
```

Then:

```text
Distance 3:

1 2 3
X X 3
X X .
```

Then:

```text
Distance 4:

1 2 3
X X 3
X X 4
```

Destination reached at:

```text
4
```

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why BFS instead of DFS?

**Answer:**

Because this is a shortest-path problem on an unweighted graph.

BFS explores nodes in increasing distance from the source, so the first time we reach the destination, we have the shortest path.

DFS only guarantees reachability naturally; it does not guarantee shortest distance.

---

## Q2. Is this actually a graph problem?

**Answer:**

Yes.

The graph is implicit.

```text
cell = node
valid movement = edge
```

We don't explicitly build an adjacency list because each cell's neighbors can be generated from the eight direction vectors.

---

## Q3. Why are there 8 directions?

Because diagonal movement is allowed.

```text
↖ ↑ ↗
← X →
↙ ↓ ↘
```

So each cell has up to eight neighbors.

---

## Q4. Why mark visited when enqueueing?

To ensure a cell enters the queue only once.

If we waited until dequeue time, multiple neighboring cells could enqueue the same cell.

That could cause unnecessary work and complicate the BFS invariant.

---

## Q5. Why does the first time we reach the destination give the shortest path?

Because BFS processes states layer by layer:

```text
distance 1
    ↓
distance 2
    ↓
distance 3
    ↓
distance 4
```

Therefore, a later path cannot have a smaller distance than a path already discovered at an earlier BFS level.

---

## Q6. Why is the complexity O(n²)?

There are:

```text
n²
```

cells.

Each cell is visited at most once.

For each visited cell, we inspect exactly 8 possible directions.

So:

```text
O(n² × 8)
= O(n²)
```

---

# 🔥 THE BIG PATTERN CONNECTION

You should now see the progression:

```text
LC 1971
──────────────
Explicit Graph
     ↓
Queue
     ↓
BFS
     ↓
Visited
     ↓
Reachability
```

Now:

```text
LC 1091
──────────────
Implicit Graph
     ↓
Grid
     ↓
Cell = Node
     ↓
Movement = Edge
     ↓
Queue
     ↓
BFS
     ↓
Distance
     ↓
Shortest Path
```

And the next evolution:

```text
LC 994
──────────────
Multiple Sources
     ↓
All sources → Queue
     ↓
BFS
     ↓
Level = Time
```

This is why we're doing these problems in this exact order.

---

# 🧩 MASTER GRID BFS TEMPLATE

Memorize the **structure**, not the exact code:

```python
from collections import deque


queue = deque([(start_r, start_c, distance)])

visited[start_r][start_c] = True

directions = [
    (-1, -1),
    (-1, 0),
    (-1, 1),
    (0, -1),
    (0, 1),
    (1, -1),
    (1, 0),
    (1, 1)
]

while queue:

    r, c, distance = queue.popleft()

    if is_destination(r, c):
        return distance

    for dr, dc in directions:

        nr = r + dr
        nc = c + dc

        if is_valid(nr, nc) and not visited[nr][nc]:

            visited[nr][nc] = True

            queue.append(
                (nr, nc, distance + 1)
            )

return -1
```

---

# 🧠 SENIOR PATTERN RECOGNITION SHEET

| Problem Signal                  | Pattern          |
| ------------------------------- | ---------------- |
| Path exists in graph            | BFS/DFS          |
| Shortest path, unweighted graph | **BFS**          |
| Shortest path in grid           | **Grid BFS**     |
| Grid + 4 directions             | Grid BFS         |
| Grid + 8 directions             | Grid BFS         |
| Cell represents state           | Implicit graph   |
| Equal movement cost             | BFS              |
| First shortest destination      | BFS              |
| Multiple starting points        | Multi-Source BFS |
| Distance from nearest source    | Multi-Source BFS |
| Each BFS level represents time  | Multi-Source BFS |

---

# ⚠️ COMMON INTERVIEW TRAPS

### Trap 1 — Using DFS automatically

```text
"Path problem → DFS"
```

Not always.

If the question says:

> **shortest path**

and the graph is unweighted:

```text
BFS
```

---

### Trap 2 — Forgetting diagonal movement

Using only:

```python
[
    (-1,0),
    (1,0),
    (0,-1),
    (0,1)
]
```

is incorrect here.

Need all 8.

---

### Trap 3 — Starting distance at 0

The answer counts cells.

Therefore:

```python
queue = deque([(0,0,1)])
```

not:

```python
queue = deque([(0,0,0)])
```

---

### Trap 4 — Forgetting to mark visited

Without visited tracking:

```text
A → B
↑   ↓
└───┘
```

can cause repeated exploration.

---

### Trap 5 — Marking visited too late

Prefer:

```python
grid[nr][nc] = 1
queue.append(...)
```

rather than waiting until dequeue.

---

# 🏆 FINAL MASTERY

## Pattern Extraction

```text
Shortest Path
+
Unweighted Graph
        ↓
      BFS
```

For a grid:

```text
Grid
 ↓
Cell = Node
 ↓
Movement = Edge
 ↓
Implicit Graph
 ↓
BFS
```

---

## Master Template

```text
START
  ↓
Check blocked
  ↓
QUEUE
  ↓
Mark visited
  ↓
POP
  ↓
Destination?
  ↓
Generate neighbors
  ↓
Valid + unvisited?
  ↓
Mark
  ↓
Enqueue
  ↓
Repeat
```

---

## Senior Mental Model

The most important transformation is:

> **Don't see the matrix as a matrix. See it as an implicit graph.**

Once you make that translation, the solution becomes:

```text
Implicit Graph
      ↓
Unweighted
      ↓
Shortest Path
      ↓
BFS
```

---

## 📈 Progress Update

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091  ← COMPLETED

LEVEL 3 — MULTI-SOURCE BFS
├── ⬜ LC 994  ← NEXT
├── ⬜ LC 542
└── ⬜ LC 1162

LEVEL 4 — LEVEL BFS
├── ⬜ LC 102
└── ⬜ LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── ⬜ LC 752

...
```

# 🎯 One-Line Takeaway

> **LC 1091 = Convert the grid into an implicit unweighted graph, then use BFS because BFS reaches every cell in shortest-distance order.**

**Next locked problem → 🔥 LC 994 — Rotting Oranges: Multi-Source BFS + BFS Levels = Time.**

Would you like to continue with LC 994 and focus on how multi-source BFS turns each level into elapsed time?



# ========================================================================================================================================


# 🔥 LC 994 — Rotting Oranges

**Level 3 — Multi-Source BFS**
**Pattern:** Multi-Source BFS + Level Order = Time
**Priority:** 🔥🔥🔥🔥🔥
**Difficulty:** Medium

This is one of the **most important BFS problems** in the roadmap.

The key idea you must master here is:

> **When multiple sources start spreading simultaneously, put all sources into the queue first, then run BFS level by level.**

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You have a grid containing:

```text
0 → Empty
1 → Fresh orange
2 → Rotten orange
```

Every **minute**, a rotten orange makes its adjacent fresh oranges rotten.

Only **4 directions** count:

```text
    ↑
←   X   →
    ↓
```

Question:

> How many minutes are required until there are no fresh oranges left?

If some fresh oranges can **never** become rotten:

```python
return -1
```

---

# 2. 🔥 Hidden Translation

The phrase:

> "Every minute, rotten oranges rot adjacent fresh oranges."

should immediately trigger:

```text
SPREADING PROCESS
       ↓
MULTIPLE STARTING POINTS
       ↓
MULTI-SOURCE BFS
```

Why multiple sources?

Because imagine:

```text
2 1 1
1 1 1
1 1 2
```

There are **two rotten oranges initially**.

Both begin spreading **at the same time**.

Therefore:

```text
source 1 ─┐
          ├──→ BFS
source 2 ─┘
```

We don't run BFS from each rotten orange separately.

We put both into the **same queue**.

---

# 3. The Critical Difference: Single vs Multi-Source BFS

### LC 1091

One starting cell:

```text
        S
        ↓
      BFS
```

### LC 994

Several starting cells:

```text
S       S       S
 \      |      /
  \     |     /
      BFS
```

All sources begin simultaneously.

Therefore:

```python
queue = deque(all_rotten_oranges)
```

This is the defining idea.

---

# 4. 🧒 ELI10 Intuition

Imagine there are several fires in a forest.

```text
🔥 . . . . 🔥
. . . . . .
. . . . . .
🔥 . . . . .
```

All fires spread at the same time.

You don't say:

> "Let me completely simulate fire #1, then fire #2."

That would be wrong because the fires happen **simultaneously**.

Instead, you start all fires together.

```text
Minute 0:

🔥 . . . . 🔥
.  . . . . .
.  . . . . .
🔥 . . . . .
```

Then:

```text
Minute 1:

🔥 🔥 . . 🔥 🔥
🔥 . . . . 🔥
🔥 . . . . .
🔥 🔥 . . . .
```

Then:

```text
Minute 2:

🔥 🔥 🔥 . 🔥 🔥
🔥 🔥 . . 🔥 🔥
🔥 🔥 . . . 🔥
🔥 🔥 🔥 . . .
```

Every BFS level represents one minute.

---

# 5. 🔥 The Most Important Concept

In ordinary BFS:

```text
BFS level = distance
```

Here:

```text
BFS level = time
```

Because every transition takes exactly **one minute**.

Therefore:

```text
Level 0 → 0 minutes
Level 1 → 1 minute
Level 2 → 2 minutes
Level 3 → 3 minutes
```

This is one of the most reusable BFS patterns you'll learn.

---

# 6. Why Do We Put ALL Rotten Oranges in the Queue Initially?

Suppose:

```text
2 1 1 1 2
```

If we do:

```text
BFS from first rotten orange
then BFS from second rotten orange
```

we are treating them as if they happen sequentially.

But the actual process is:

```text
both start at minute 0
```

So:

```python
queue = deque([
    (0,0),
    (0,4)
])
```

means:

> These two sources are active at the same time.

That is exactly what multi-source BFS represents.

---

# 7. Why Not Run BFS Separately From Every Rotten Orange?

Suppose there are `R` rotten oranges.

Running BFS independently from each one could cost roughly:

```text
O(R × rows × cols)
```

and, more importantly, it doesn't naturally model simultaneous spreading.

Multi-source BFS processes the entire spreading process together:

```text
O(rows × cols)
```

because each cell changes state at most once.

---

# 8. Queue Initialization

This is the first major difference from LC 1091.

### LC 1091

```python
queue = deque([(0, 0)])
```

### LC 994

First scan the entire grid:

```python
for r in range(rows):
    for c in range(cols):
        if grid[r][c] == 2:
            queue.append((r, c))
```

So if:

```text
2 1 1
1 2 1
1 1 1
```

we get:

```text
queue = [
    (0,0),
    (1,1)
]
```

Both are sources.

---

# 9. Count Fresh Oranges

We need to know when the process is finished.

Maintain:

```python
fresh = number of fresh oranges
```

Whenever a fresh orange becomes rotten:

```python
fresh -= 1
```

When:

```python
fresh == 0
```

all oranges have successfully rotted.

This avoids rescanning the grid after every minute.

---

# 10. The Core State

We maintain:

```text id="i6r8u8"
queue
fresh
minutes
```

### `queue`

Contains oranges that can spread rot.

### `fresh`

How many fresh oranges remain.

### `minutes`

How many BFS levels have been processed.

---

# 11. BFS Level Processing

This is the most important coding pattern.

```python
while queue and fresh > 0:

    level_size = len(queue)

    for _ in range(level_size):

        r, c = queue.popleft()

        ...
    
    minutes += 1
```

Why:

```python
level_size = len(queue)
```

?

Because the queue contains all oranges that are rotten **at the beginning of the current minute**.

We process exactly those oranges.

Newly rotten oranges are added to the back of the queue.

They must wait until the **next minute**.

This is the key invariant.

---

# 12. 🔥 Why `level_size` Is Essential

Suppose:

```text
queue = [A, B]
```

At minute 1:

```text
A → C
B → D
```

After processing A and B:

```text
queue = [C, D]
```

C and D must **not immediately spread again** during minute 1.

They spread during minute 2.

Therefore we freeze:

```python
level_size = len(queue)
```

and process exactly that many elements.

This separates time correctly.

---

# 13. State Transition

For every rotten orange:

```text
current rotten
      ↓
check 4 neighbors
      ↓
neighbor == fresh?
      ↓
make it rotten
      ↓
fresh -= 1
      ↓
enqueue neighbor
```

The transition takes:

```text
1 minute
```

---

# 14. Why Do We Modify `1 → 2`?

When a fresh orange becomes rotten:

```python
grid[nr][nc] = 2
```

This serves as our visited marker.

We don't need a separate `visited` matrix.

This is the same optimization we used in LC 1091.

---

# 15. Important Invariant

The core invariant is:

> **At the beginning of each BFS level, every orange in the queue is rotten and capable of spreading during the current minute, while every orange that becomes rotten during this level belongs to the next minute.**

This invariant guarantees correct timing.

---

# 16. Why Does BFS Give the Minimum Time?

Consider a fresh orange.

Its minimum time to become rotten is:

```text
minimum number of edges from any initial rotten orange
```

Multi-source BFS simultaneously computes the distance from the **nearest source**.

Therefore:

```text
minimum distance from any rotten source
=
minimum rotting time
```

This is a powerful general principle.

---

# 17. Multi-Source BFS as "Distance From Nearest Source"

Think mathematically:

For every cell:

```text
distance(cell)
=
min(
    distance from source 1,
    distance from source 2,
    ...
)
```

Multi-source BFS calculates all these minimum distances simultaneously.

That's why the same pattern appears in:

```text
LC 994
LC 542
LC 1162
```

---

# 18. LC 994 → LC 542 → LC 1162

This progression is deliberate.

### LC 994

```text
Sources = rotten oranges
Question = how much time?
```

### LC 542

```text
Sources = zeros
Question = distance to nearest zero
```

### LC 1162

```text
Sources = land
Question = maximum distance to nearest land
```

The underlying engine is almost identical:

```text
MULTIPLE SOURCES
       ↓
QUEUE
       ↓
BFS
       ↓
DISTANCE FROM NEAREST SOURCE
```

---

# 19. Why 4 Directions?

Unlike LC 1091, diagonal movement is not allowed.

Use:

```python
directions = [
    (-1, 0),
    (1, 0),
    (0, -1),
    (0, 1)
]
```

Do **not** use diagonals.

---

# 20. Edge Cases

## Case 1 — No fresh oranges

```text
2 2
2 2
```

Nothing needs to rot.

Answer:

```text
0
```

---

## Case 2 — All fresh, no rotten

```text
1 1
1 1
```

No source exists.

Therefore:

```text
-1
```

---

## Case 3 — Isolated fresh orange

```text
2 0
0 1
```

The fresh orange can never be reached.

Answer:

```text
-1
```

---

## Case 4 — Single cell rotten

```text
[2]
```

Answer:

```text
0
```

---

## Case 5 — Single fresh orange

```text
[1]
```

No rotten source exists.

Answer:

```text
-1
```

---

# 21. Complexity Derivation

Let:

```text
R = number of rows
C = number of columns
```

Initial scan:

```text
O(RC)
```

BFS:

Each cell can become rotten at most once.

Each processed cell checks 4 directions:

```text
O(4RC)
```

Therefore:

```text
O(RC) + O(4RC)
```

which simplifies to:

```text
O(RC)
```

Space:

Worst case, the queue can contain many cells:

```text
O(RC)
```

Therefore:

```text
Time  = O(RC)
Space = O(RC)
```

---

# ⚙️ ALGORITHM — STEP-BY-STEP

This is the exact executable reasoning you should be able to derive during an interview.

### Step 1 → Scan the entire grid

For every cell:

```text
if cell == 2
    add it to queue

if cell == 1
    increment fresh count
```

Why?

Because **every initially rotten orange is a source**.

---

### Step 2 → Initialize time

```python
minutes = 0
```

No spreading has happened yet.

---

### Step 3 → Start BFS while sources exist and fresh oranges remain

```python
while queue and fresh > 0:
```

If there are no rotten oranges:

```text
queue = empty
```

there is nobody capable of spreading the rot.

---

### Step 4 → Freeze the current BFS level

```python
level_size = len(queue)
```

These are exactly the oranges that are rotten at the beginning of this minute.

---

### Step 5 → Process exactly this level

```python
for _ in range(level_size):
```

Do not process newly rotten oranges during the same level.

They belong to the next minute.

---

### Step 6 → Remove one rotten orange

```python
r, c = queue.popleft()
```

This orange spreads rot.

---

### Step 7 → Check its four neighbors

For each:

```text
up
down
left
right
```

calculate:

```python
nr = r + dr
nc = c + dc
```

---

### Step 8 → Validate neighbor

The neighbor must:

```text
be inside the grid
AND
be fresh
```

---

### Step 9 → Rot the fresh orange

```python
grid[nr][nc] = 2
```

Now it is officially rotten.

---

### Step 10 → Decrease fresh count

```python
fresh -= 1
```

One fewer fresh orange remains.

---

### Step 11 → Add newly rotten orange to queue

```python
queue.append((nr, nc))
```

But remember:

> It will spread during the **next** BFS level.

---

### Step 12 → Finish the current minute

After exactly `level_size` oranges have been processed:

```python
minutes += 1
```

One minute has elapsed.

---

### Step 13 → Check remaining fresh oranges

If:

```python
fresh == 0
```

everything successfully rotted.

Return:

```python
minutes
```

Otherwise, if BFS ends while:

```python
fresh > 0
```

some fresh oranges were unreachable.

Return:

```python
-1
```

---

# 💻 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def orangesRotting(self, grid):

        rows = len(grid)
        cols = len(grid[0])

        queue = deque()
        fresh = 0

        # Find all initial rotten oranges
        # and count fresh oranges.
        for r in range(rows):
            for c in range(cols):

                if grid[r][c] == 2:
                    queue.append((r, c))

                elif grid[r][c] == 1:
                    fresh += 1

        # Four possible directions
        directions = [
            (-1, 0),
            (1, 0),
            (0, -1),
            (0, 1)
        ]

        minutes = 0

        # Multi-source BFS
        while queue and fresh > 0:

            level_size = len(queue)

            # Process all oranges that were
            # rotten at the beginning of this minute.
            for _ in range(level_size):

                r, c = queue.popleft()

                for dr, dc in directions:

                    nr = r + dr
                    nc = c + dc

                    # Valid fresh neighbor
                    if (
                        0 <= nr < rows
                        and 0 <= nc < cols
                        and grid[nr][nc] == 1
                    ):

                        # Make it rotten
                        grid[nr][nc] = 2

                        # One fewer fresh orange
                        fresh -= 1

                        # It spreads during next minute
                        queue.append((nr, nc))

            # One BFS level = one minute
            minutes += 1

        # If fresh oranges remain, they are unreachable.
        if fresh > 0:
            return -1

        return minutes
```

---

# 🎤 Interview Justification

Say this:

> "This is a multi-source BFS problem because every initially rotten orange starts spreading simultaneously. I first put all rotten oranges into the queue and count the fresh oranges. Then I process the queue level by level, where each BFS level represents one minute. Whenever a rotten orange reaches a fresh neighbor, I convert it to rotten, decrement the fresh count, and enqueue it for the next level. If all fresh oranges become rotten, I return the elapsed levels; otherwise, I return -1. The complexity is O(R×C) time and O(R×C) space."

That's the senior-level explanation.

---

# 🧪 BLOCK 3 — FULL CODE + DRY RUN

Consider:

```text
[
    [2,1,1],
    [1,1,0],
    [0,1,1]
]
```

Visual:

```text
🔥 🟠 🟠
🟠 🟠 ⬜
⬜ 🟠 🟠
```

Where:

```text
2 = rotten
1 = fresh
0 = empty
```

Initially:

```text
queue = [(0,0)]
fresh = 6
minutes = 0
```

---

## Minute 1

Current queue:

```text
[(0,0)]
```

Process `(0,0)`.

Neighbors:

```text
(-1,0) ❌
(1,0)  🟠 → becomes rotten
(0,-1) ❌
(0,1)  🟠 → becomes rotten
```

Grid becomes:

```text
🔥 🔥 🟠
🔥 🟠 ⬜
⬜ 🟠 🟠
```

Queue:

```text
[(1,0), (0,1)]
```

Fresh:

```text
4
```

Minutes:

```text
1
```

---

# Minute 2

At the beginning:

```text
queue = [
    (1,0),
    (0,1)
]
```

Important:

```text
level_size = 2
```

Process exactly those two.

### Process `(1,0)`

Neighbor:

```text
(1,1)
```

becomes rotten.

### Process `(0,1)`

Neighbor:

```text
(0,2)
```

becomes rotten.

Grid:

```text
🔥 🔥 🔥
🔥 🔥 ⬜
⬜ 🟠 🟠
```

Queue:

```text
[(1,1), (0,2)]
```

Fresh:

```text
2
```

Minutes:

```text
2
```

---

# Minute 3

Queue:

```text
[(1,1), (0,2)]
```

Process `(1,1)`.

Neighbor:

```text
(2,1)
```

becomes rotten.

Process `(0,2)`.

No new fresh orange.

Grid:

```text
🔥 🔥 🔥
🔥 🔥 ⬜
⬜ 🔥 🟠
```

Queue:

```text
[(2,1)]
```

Fresh:

```text
1
```

Minutes:

```text
3
```

---

# Minute 4

Process:

```text
(2,1)
```

Neighbor:

```text
(2,2)
```

becomes rotten.

Grid:

```text
🔥 🔥 🔥
🔥 🔥 ⬜
⬜ 🔥 🔥
```

Fresh:

```text
0
```

Minutes:

```text
4
```

Answer:

```text
4
```

---

# 📊 Dry-Run Table

| Minute | Current Queue   | Newly Rotten  | Fresh Remaining |
| -----: | --------------- | ------------- | --------------: |
|      0 | `[(0,0)]`       | —             |               6 |
|      1 | `[(0,0)]`       | `(1,0),(0,1)` |               4 |
|      2 | `[(1,0),(0,1)]` | `(1,1),(0,2)` |               2 |
|      3 | `[(1,1),(0,2)]` | `(2,1)`       |               1 |
|      4 | `[(2,1)]`       | `(2,2)`       |               0 |

Therefore:

```text
Answer = 4
```

---

# 🔥 THE MOST IMPORTANT VISUAL

Think of BFS as a wave.

```text
Minute 0

2 . .
. . .
. . .
```

Then:

```text
Minute 1

2 2 .
2 . .
. . .
```

Then:

```text
Minute 2

2 2 2
2 2 .
. 2 .
```

Then:

```text
Minute 3

2 2 2
2 2 .
. 2 2
```

The wave expands simultaneously from every source.

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why is this multi-source BFS?

Because there are potentially multiple rotten oranges at time `0`.

They all begin spreading simultaneously.

Therefore, all of them must be inserted into the queue before BFS begins.

---

## Q2. Why do we process BFS level by level?

Because each level represents one minute.

```text
BFS level 0 → minute 0
BFS level 1 → minute 1
BFS level 2 → minute 2
...
```

Without level separation, we could accidentally allow a newly rotten orange to spread again during the same minute.

---

## Q3. Why not simply process the queue until empty and increment time for every orange?

Because multiple oranges spread **simultaneously**.

If the queue contains:

```text
A, B, C
```

processing A, then incrementing time, then B would incorrectly treat them as sequential events.

They belong to the same time layer.

---

## Q4. Why don't we need a visited array?

Because we mutate:

```python
1 → 2
```

when an orange is first reached.

Once it becomes `2`, another rotten orange won't process it as fresh again.

So the grid itself acts as the visited state.

---

## Q5. Why do we maintain `fresh`?

Without `fresh`, we would need to scan the entire grid after BFS to determine whether any fresh oranges remain.

The counter lets us know immediately:

```text
fresh == 0
```

means success.

---

## Q6. What happens if the queue becomes empty while `fresh > 0`?

That means there are still fresh oranges but no rotten orange capable of reaching them.

Therefore they are unreachable.

Return:

```python
-1
```

---

# 🧠 MASTER MULTI-SOURCE BFS TEMPLATE

This is the template I want you to recognize from now on:

```python
from collections import deque


queue = deque()

# Add ALL sources
for every cell:
    if cell is a source:
        queue.append(cell)


distance = 0

while queue:

    level_size = len(queue)

    for _ in range(level_size):

        current = queue.popleft()

        for neighbor in neighbors(current):

            if neighbor is valid and unvisited:

                mark visited
                queue.append(neighbor)

    distance += 1
```

The only things that change between problems are:

```text
source definition
neighbor definition
state transition
answer extraction
```

The BFS engine remains almost identical.

---

# 🔥 SINGLE-SOURCE vs MULTI-SOURCE

| Property             | LC 1091       | LC 994          |
| -------------------- | ------------- | --------------- |
| Sources              | 1             | Many            |
| Grid                 | Yes           | Yes             |
| BFS                  | Yes           | Yes             |
| Directions           | 8             | 4               |
| Distance             | Path length   | Time            |
| Queue initialization | One cell      | **All sources** |
| BFS levels           | Distance      | **Minutes**     |
| Visited              | Grid mutation | Grid mutation   |
| Complexity           | O(RC)         | O(RC)           |

---

# 🧠 PATTERN EXTRACTION

When you see:

> "Several things start simultaneously and spread outward."

Think:

```text
MULTI-SOURCE BFS
```

When you see:

> "Every minute..."

Think:

```text
BFS LEVELS = TIME
```

When you see:

> "Distance from nearest source..."

Think:

```text
MULTI-SOURCE BFS
```

When you see:

> "All sources begin at time 0..."

Think:

```text
PUT ALL SOURCES IN QUEUE FIRST
```

---

# 🏆 SENIOR ENGINEER MENTAL MODEL

The real abstraction is not "rotting oranges."

It's:

```text
                  MULTIPLE SOURCES
                        ↓
                 INITIAL FRONTIER
                        ↓
                      QUEUE
                        ↓
                SIMULTANEOUS BFS
                        ↓
                LEVEL-BY-LEVEL
                        ↓
              DISTANCE / TIME
                        ↓
          NEAREST SOURCE DISTANCE
```

That's the reusable algorithm.

---

# 📈 PROGRESS UPDATE

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994  ← COMPLETED
├── ⬜ LC 542  ← NEXT
└── ⬜ LC 1162
```

And the conceptual progression is now:

```text
LC 1971
Graph Reachability
       ↓
LC 1091
Single-Source Shortest Path
       ↓
LC 994
🔥 Multi-Source Shortest Time
       ↓
LC 542
Nearest Source Distance
       ↓
LC 1162
Maximum Nearest-Source Distance
```

# 🎯 ONE-LINE TAKEAWAY

> **LC 994 = Put every initial source into one queue, process BFS level-by-level, and interpret each level as one unit of time.**

**Next locked problem → 🔥 LC 542 — 01 Matrix**, where we remove the "rotting" story and expose the pure **multi-source BFS → nearest-source distance** pattern.

Would you like to tackle LC 542 with a dry run first, or derive the code template together?



Absolutely bro. We keep the **locked deep-dive format** exactly: Senior Insights → mandatory Algorithm → Efficient Code → Full Code + Dry Run → Interview Q&A → Pattern Extraction → Master Template → Senior Recognition → Progress Update → One-Line Takeaway.

# 🔥 LC 542 — 01 Matrix

**LEVEL 3 — MULTI-SOURCE BFS**
**Pattern:** Multi-Source BFS + Nearest-Source Distance
**Priority:** 🔥🔥🔥🔥🔥
**Difficulty:** Medium

This problem is extremely important because it removes the "rotting oranges" story from LC 994 and exposes the **pure algorithmic pattern**:

```text
ALL SOURCES
    ↓
INITIAL QUEUE
    ↓
MULTI-SOURCE BFS
    ↓
DISTANCE FROM NEAREST SOURCE
```

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given a binary matrix:

```text
0 → source
1 → cell that needs a distance
```

For **every `1`**, find the distance to its **nearest `0`**.

Movement is allowed in four directions:

```text
      ↑
      |
← ----X---- →
      |
      ↓
```

Return a matrix containing those minimum distances.

### Example

Input:

```text
[
    [0,0,0],
    [0,1,0],
    [1,1,1]
]
```

Output:

```text
[
    [0,0,0],
    [0,1,0],
    [1,2,1]
]
```

---

# 2. 🔥 Hidden Translation

The problem says:

> Find the distance from every `1` to the nearest `0`.

Don't think:

```text
"For every 1, search for a 0."
```

That's the naive direction.

Instead reverse the perspective:

```text
ALL 0s
  ↓
Become sources
  ↓
Expand simultaneously
  ↓
Reach every 1
  ↓
Assign shortest distance
```

This is the exact **multi-source BFS** pattern.

---

# 3. The Critical Connection to LC 994

We just solved:

### LC 994

```text
Rotten oranges
    ↓
Initial rotten oranges = sources
    ↓
Spread
    ↓
Minutes
```

Now:

### LC 542

```text
Zeros
    ↓
Sources
    ↓
Spread
    ↓
Distance
```

The BFS engine hasn't changed.

Only the **meaning of the source and answer** changed.

```text
LC 994:
source → rotten orange
distance → minutes

LC 542:
source → zero
distance → nearest-zero distance
```

This is exactly what pattern mastery looks like.

---

# 4. 🧒 ELI10 Intuition

Imagine every `0` is a fire station.

```text
🔥 . . . 🔥
. . . . .
. . . . .
```

Every fire station starts sending firefighters simultaneously.

A cell that is:

```text
1 step away
```

gets distance `1`.

A cell that is:

```text
2 steps away
```

gets distance `2`.

And so on.

The closest fire station reaches each cell first.

That first arrival is the shortest distance.

---

# 5. Why Multi-Source BFS?

Suppose:

```text
0 1 1 1 0
```

The middle cell has two possible sources:

```text
0 → 1 → 1
```

from the left:

```text
distance = 2
```

and:

```text
1 ← 1 ← 0
```

from the right:

```text
distance = 2
```

For every cell we really want:

```text
minimum distance from ANY zero
```

Mathematically:

```text
distance(cell)
=
min(
    distance(cell, zero₁),
    distance(cell, zero₂),
    ...
)
```

Multi-source BFS computes this minimum automatically.

---

# 6. Why Not BFS Separately From Every `1`?

Naive approach:

```text
for every 1:
    BFS until you find a 0
```

If there are many `1`s, we repeatedly explore the same cells.

Suppose the matrix has:

```text
R × C
```

cells.

In the worst case, we could perform a BFS for a large number of cells.

That can approach:

```text
O((RC)²)
```

which is far worse than necessary.

Multi-source BFS:

```text
O(RC)
```

because every cell is processed once.

---

# 7. Why Start From the `0`s Instead?

This is one of the most important conceptual tricks.

The question is:

> Distance of every `1` from its nearest `0`.

Instead of:

```text
1 → search for nearest 0
```

reverse it:

```text
0 → spread to nearest 1
```

Distance is symmetric in an unweighted grid:

```text
distance(A,B) = distance(B,A)
```

So spreading outward from all zeros simultaneously solves the problem.

This is a very powerful interview transformation.

---

# 8. BFS Wave Expansion

Example:

```text
0 1 1
1 1 1
1 1 1
```

Initially:

```text
0 . .
. . .
. . .
```

Distance `0`:

```text
0 0? 
```

More precisely, only the source itself has distance 0:

```text
0 ? ?
? ? ?
? ? ?
```

First BFS layer:

```text
0 1 ?
1 ? ?
? ? ?
```

Second:

```text
0 1 2
1 2 ?
2 ? ?
```

Third:

```text
0 1 2
1 2 3
2 3 ?
```

Every layer represents:

```text
distance from nearest zero
```

---

# 9. The Queue Contains the Frontier

Initially:

```text
queue = all zero cells
```

Then:

```text
queue
 ↓
process all current frontier cells
 ↓
discover next layer
 ↓
enqueue next layer
 ↓
repeat
```

The queue represents:

> **The boundary between cells whose distances are already known and cells that are waiting to receive their distance.**

---

# 10. Why All Zeros Must Enter the Queue First

Suppose:

```text
0 1 1 0
```

If we start only from the first zero:

```text
BFS from left zero
```

we don't immediately model the fact that the right zero is also a source at distance `0`.

Instead:

```python
queue = deque([
    (0,0),
    (0,3)
])
```

Both sources begin simultaneously.

Then the BFS naturally assigns the **nearest** source distance.

---

# 11. Distance Representation

We have two common implementations.

### Approach A — Separate distance matrix

Create:

```python
distance = [[-1] * cols for _ in range(rows)]
```

Then:

```text
0 cells → distance 0
neighbors → distance 1
...
```

This is very explicit and excellent for learning.

### Approach B — Modify the matrix

We could transform values during BFS.

However, LC 542 is naturally understood using a **distance matrix**, because the output itself is a distance matrix.

For mastery, we'll use:

```text
distance
+
queue
```

This makes the invariant extremely clear.

---

# 12. Initial State

For every zero:

```python
distance[r][c] = 0
queue.append((r,c))
```

For every one:

```python
distance[r][c] = -1
```

So:

```text
-1 = not discovered yet
0  = source
positive = shortest distance
```

---

# 13. Core Invariant

At all times:

> Every cell removed from the queue has its minimum possible distance from any source (`0` cell).

And:

> Every cell is enqueued at most once.

Why?

Because the first time BFS reaches an undiscovered cell, it reaches it through the shortest possible number of edges.

---

# 14. Why Is the First Distance Optimal?

Suppose a cell is first discovered at:

```text
distance = 3
```

Could another path reach it at distance `2` later?

No.

BFS processes:

```text
distance 0
↓
distance 1
↓
distance 2
↓
distance 3
```

So if a distance-2 path existed, BFS would have discovered that cell during the distance-2 layer first.

Therefore:

```text
first discovery = shortest distance
```

---

# 15. Why Use `distance[nr][nc] == -1`?

Because we need to know whether a cell has already been discovered.

```python
if distance[nr][nc] == -1:
```

means:

> This cell has not yet been reached by any source.

Then:

```python
distance[nr][nc] = distance[r][c] + 1
```

and enqueue it.

---

# 16. Why Not Update a Cell Multiple Times?

Suppose two zeros can reach the same cell.

The first BFS wave reaches it at the minimum distance.

Therefore:

```text
first discovery
    ↓
shortest distance
    ↓
never update again
```

This is another critical BFS principle.

---

# 17. Four Directions

LC 542 allows:

```text
up
down
left
right
```

Use:

```python
directions = [
    (-1, 0),
    (1, 0),
    (0, -1),
    (0, 1)
]
```

No diagonal movement.

---

# 18. What Does "Distance" Mean?

Distance means:

> Minimum number of valid moves needed to reach a zero.

Example:

```text
0 1 1
```

For the rightmost cell:

```text
0 → 1 → 1
```

Two moves.

Therefore:

```text
distance = 2
```

---

# 19. The Deepest Connection

LC 1091 taught:

```text
ONE SOURCE
    ↓
BFS
    ↓
Shortest path
```

LC 994 taught:

```text
MULTIPLE SOURCES
    ↓
BFS
    ↓
Time / distance
```

LC 542 now teaches:

```text
MULTIPLE SOURCES
    ↓
BFS
    ↓
DISTANCE TO NEAREST SOURCE
```

So:

```text
LC 1091
source → destination

LC 994
sources → spreading time

LC 542
sources → distance field
```

---

# 20. Distance Field

The output matrix can be viewed as a **distance field**.

Example:

```text
0 1 2
1 2 3
2 3 4
```

This tells us:

```text
distance 0 → source
distance 1 → one move away
distance 2 → two moves away
...
```

This concept appears in many real systems:

* path planning
* robotics
* game AI
* image processing
* geographic proximity calculations
* obstacle-distance maps

The algorithm is still:

```text
Multi-Source BFS
```

---

# 21. Real-World Interpretation

Imagine emergency stations:

```text
🏥       🏥
 . . . . .
 . . . . .
```

We want to know:

> How far is every location from its nearest hospital?

Put all hospitals into the queue.

Then BFS expands simultaneously.

The resulting matrix tells us:

```text
distance to nearest hospital
```

Same algorithm.

---

# 22. Important Edge Cases

### Case 1 — All zeros

```text
0 0
0 0
```

Output:

```text
0 0
0 0
```

Every cell is already a source.

---

### Case 2 — One zero

```text
0 1
1 1
```

Output:

```text
0 1
1 2
```

---

### Case 3 — One row

```text
0 1 1 1
```

Output:

```text
0 1 2 3
```

---

### Case 4 — One column

```text
0
1
1
```

Output:

```text
0
1
2
```

---

# 23. Complexity

Let:

```text
R = rows
C = columns
```

Initial scan:

```text
O(RC)
```

Every cell enters the queue at most once:

```text
O(RC)
```

Each cell checks four directions:

```text
O(4RC)
```

Therefore:

```text
O(RC)
```

Space:

Distance matrix:

```text
O(RC)
```

Queue:

```text
O(RC)
```

Therefore:

```text
Time  = O(RC)
Space = O(RC)
```

---

# ⚙️ ALGORITHM — STEP-BY-STEP

This is the exact reasoning you should be able to convert into code during an interview.

### Step 1 → Create the result matrix

Create:

```python
distance = [[-1] * cols for _ in range(rows)]
```

Meaning:

```text
-1 = undiscovered
```

---

### Step 2 → Create the queue

```python
queue = deque()
```

This will contain the BFS frontier.

---

### Step 3 → Scan the entire matrix

For every cell:

```text
if cell == 0
```

then it is a source.

---

### Step 4 → Add every zero to the queue

For each zero:

```python
queue.append((r, c))
```

This is the defining multi-source BFS operation.

---

### Step 5 → Give every source distance 0

```python
distance[r][c] = 0
```

Because every zero is already at distance zero from itself.

---

### Step 6 → Start BFS

While:

```python
while queue:
```

process the frontier.

---

### Step 7 → Pop one cell

```python
r, c = queue.popleft()
```

This cell already has its minimum distance.

---

### Step 8 → Examine its four neighbors

For each direction:

```python
nr = r + dr
nc = c + dc
```

---

### Step 9 → Check whether the neighbor is valid

The neighbor must:

```text
be inside the matrix
AND
distance[nr][nc] == -1
```

If distance is `-1`, nobody has discovered it yet.

---

### Step 10 → Assign its shortest distance

```python
distance[nr][nc] = distance[r][c] + 1
```

Because moving from the current cell to its neighbor costs exactly one step.

---

### Step 11 → Add it to the queue

```python
queue.append((nr, nc))
```

It becomes part of the next BFS frontier.

---

### Step 12 → Continue until queue is empty

Every reachable cell gets its minimum distance.

Since every cell in this problem is either `0` or `1`, and all `0`s are sources, every cell will eventually be reached.

---

### Step 13 → Return the distance matrix

```python
return distance
```

---

# 💻 BLOCK 2 — EFFICIENT CODE

```python id="m3c2xq"
from collections import deque


class Solution:

    def updateMatrix(self, mat):

        rows = len(mat)
        cols = len(mat[0])

        # Distance matrix.
        # -1 means not discovered yet.
        distance = [
            [-1] * cols
            for _ in range(rows)
        ]

        queue = deque()

        # Step 1:
        # Every 0 is a source.
        for r in range(rows):
            for c in range(cols):

                if mat[r][c] == 0:

                    distance[r][c] = 0
                    queue.append((r, c))

        # Four possible movements.
        directions = [
            (-1, 0),
            (1, 0),
            (0, -1),
            (0, 1)
        ]

        # Multi-source BFS.
        while queue:

            r, c = queue.popleft()

            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                # Valid and undiscovered neighbor.
                if (
                    0 <= nr < rows
                    and 0 <= nc < cols
                    and distance[nr][nc] == -1
                ):

                    distance[nr][nc] = (
                        distance[r][c] + 1
                    )

                    queue.append((nr, nc))

        return distance
```

---

## Complexity Derivation

Let the matrix contain:

```text
R × C
```

cells.

### Initial scan

Every cell is inspected once:

```text
O(RC)
```

### BFS

Every cell is inserted into the queue at most once:

```text
O(RC)
```

Every cell checks four directions:

```text
O(4RC)
```

Therefore:

```text
O(RC)
```

overall.

### Space

Distance matrix:

```text
O(RC)
```

Queue:

```text
O(RC)
```

Overall auxiliary space:

```text
O(RC)
```

---

# 🎤 Interview Justification

A strong answer:

> "This is a multi-source BFS problem. Instead of running a search from every `1`, I treat every `0` as a source and put all zeros into the queue initially with distance zero. BFS then expands simultaneously from all sources. The first time an undiscovered cell is reached, it has been reached through the nearest zero, so I assign its distance as the current distance plus one. Each cell is processed once, giving O(R×C) time and O(R×C) space."

---

# 🧪 BLOCK 3 — FULL CODE + DRY RUN

Let's use:

```text
[
    [0,0,0],
    [0,1,0],
    [1,1,1]
]
```

Visual:

```text
0 0 0
0 1 0
1 1 1
```

Sources:

```text
(0,0)
(0,1)
(0,2)
(1,0)
(1,2)
```

Only the `1`s need distances.

---

## Full Runnable Code

```python
from collections import deque


class Solution:

    def updateMatrix(self, mat):

        rows = len(mat)
        cols = len(mat[0])

        distance = [
            [-1] * cols
            for _ in range(rows)
        ]

        queue = deque()

        # Add every zero as a source.
        for r in range(rows):
            for c in range(cols):

                if mat[r][c] == 0:

                    distance[r][c] = 0
                    queue.append((r, c))

        directions = [
            (-1, 0),
            (1, 0),
            (0, -1),
            (0, 1)
        ]

        while queue:

            r, c = queue.popleft()

            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                if (
                    0 <= nr < rows
                    and 0 <= nc < cols
                    and distance[nr][nc] == -1
                ):

                    distance[nr][nc] = (
                        distance[r][c] + 1
                    )

                    queue.append((nr, nc))

        return distance


# -------------------------
# Example
# -------------------------

mat = [
    [0, 0, 0],
    [0, 1, 0],
    [1, 1, 1]
]

solution = Solution()

result = solution.updateMatrix(mat)

print("Distance Matrix:")

for row in result:
    print(row)
```

### Output

```text
Distance Matrix:
[0, 0, 0]
[0, 1, 0]
[1, 2, 1]
```

---

# 🔬 DETAILED DRY RUN

Initial matrix:

```text
0 0 0
0 1 0
1 1 1
```

Initial queue contains every zero:

```text
queue =
[
    (0,0),
    (0,1),
    (0,2),
    (1,0),
    (1,2)
]
```

Distance matrix:

```text
0  0  0
0 -1  0
-1 -1 -1
```

Notice:

```text
0 = source
-1 = not discovered
```

---

# Step 1 — Process `(0,0)`

Current distance:

```text
distance[0][0] = 0
```

Neighbors:

```text
(-1,0) → outside
(1,0)  → already discovered
(0,-1) → outside
(0,1)  → already discovered
```

No changes.

---

# Step 2 — Process `(0,1)`

Distance:

```text
0
```

Neighbors:

```text
(-1,1) → outside
(1,1)  → undiscovered
(0,0)  → discovered
(0,2)  → discovered
```

Therefore:

```text
distance[1][1] = 1
```

Queue now:

```text
[
    (0,2),
    (1,0),
    (1,2),
    (1,1)
]
```

Distance:

```text
0 0 0
0 1 0
-1 -1 -1
```

---

# Step 3 — Process `(0,2)`

Distance:

```text
0
```

Neighbors:

```text
(1,2) → already discovered
(0,1) → already discovered
```

Nothing new.

---

# Step 4 — Process `(1,0)`

Distance:

```text
0
```

Neighbors:

```text
(0,0) → discovered
(2,0) → undiscovered
(1,1) → discovered
```

Therefore:

```text
distance[2][0] = 1
```

Distance:

```text
0 0 0
0 1 0
1 -1 -1
```

---

# Step 5 — Process `(1,2)`

Distance:

```text
0
```

Neighbors:

```text
(0,2) → discovered
(2,2) → undiscovered
(1,1) → discovered
```

Therefore:

```text
distance[2][2] = 1
```

Distance:

```text
0 0 0
0 1 0
1 -1 1
```

---

# Step 6 — Process `(1,1)`

Distance:

```text
1
```

Neighbors:

```text
(0,1) → discovered
(2,1) → undiscovered
(1,0) → discovered
(1,2) → discovered
```

Therefore:

```text
distance[2][1] = 2
```

Distance:

```text
0 0 0
0 1 0
1 2 1
```

---

# Step 7

Now:

```text
queue =
[
    (2,0),
    (2,2),
    (2,1)
]
```

Process `(2,0)`.

All useful neighbors are already discovered.

---

# Step 8

Process `(2,2)`.

All useful neighbors are already discovered.

---

# Step 9

Process `(2,1)`.

All useful neighbors are already discovered.

Queue becomes:

```text
[]
```

BFS ends.

Final result:

```text
[
    [0,0,0],
    [0,1,0],
    [1,2,1]
]
```

---

# 📊 DRY-RUN TABLE

| Step | Popped  | Distance | Newly Discovered | Queue After                     |
| ---: | ------- | -------: | ---------------- | ------------------------------- |
|    0 | —       |        — | All zeros        | `(0,0),(0,1),(0,2),(1,0),(1,2)` |
|    1 | `(0,0)` |        0 | None             | remaining sources               |
|    2 | `(0,1)` |        0 | `(1,1)=1`        | sources + `(1,1)`               |
|    3 | `(0,2)` |        0 | None             | ...                             |
|    4 | `(1,0)` |        0 | `(2,0)=1`        | ...                             |
|    5 | `(1,2)` |        0 | `(2,2)=1`        | ...                             |
|    6 | `(1,1)` |        1 | `(2,1)=2`        | ...                             |
|    7 | `(2,0)` |        1 | None             | ...                             |
|    8 | `(2,2)` |        1 | None             | ...                             |
|    9 | `(2,1)` |        2 | None             | `[]`                            |

Final:

```text
0 0 0
0 1 0
1 2 1
```

---

# 🔥 VISUAL BFS WAVE

Initial sources:

```text
0 0 0
0 1 0
1 1 1
```

Distance 0:

```text
0 0 0
0 . 0
. . .
```

Distance 1:

```text
0 0 0
0 1 0
1 . 1
```

Distance 2:

```text
0 0 0
0 1 0
1 2 1
```

The waves are expanding from **all zeros simultaneously**.

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why do you start BFS from the zeros instead of the ones?

Because the question asks for the distance to the nearest zero.

Every zero is a source.

Running BFS simultaneously from all zeros computes the nearest-source distance for every cell in one traversal.

---

## Q2. Why not perform BFS separately for every `1`?

That repeats work.

If many cells are `1`, separate searches can repeatedly traverse the same regions.

Multi-source BFS processes the entire matrix in:

```text
O(RC)
```

---

## Q3. Why does the first time a cell is discovered give the nearest zero?

Because BFS explores the grid in increasing distance order.

All distance-0 sources are processed first, then distance-1 cells, then distance-2 cells, etc.

Therefore the first source to reach a cell must do so at minimum distance.

---

## Q4. Why put all zeros into the queue before starting BFS?

Because all zeros are sources at the same time.

Putting them into the queue initially represents simultaneous expansion.

This is the defining property of multi-source BFS.

---

## Q5. Why use `distance == -1` to determine whether a cell was visited?

It lets us combine:

```text
distance
+
visited
```

into one matrix.

```text
-1 → undiscovered
0+ → discovered
```

This avoids a separate visited matrix.

---

## Q6. Can this be solved with DFS?

You could attempt a DFS-based solution, but it is not the natural shortest-distance algorithm.

You would have to explore and compare paths, potentially causing much more work.

BFS directly provides shortest unweighted distance.

---

# 🧠 MASTER MULTI-SOURCE BFS TEMPLATE

This is the template you should now recognize across LC 994 and LC 542:

```python
from collections import deque


queue = deque()

# Add ALL sources
for r in range(rows):
    for c in range(cols):

        if is_source(r, c):

            distance[r][c] = 0
            queue.append((r, c))


while queue:

    r, c = queue.popleft()

    for dr, dc in directions:

        nr = r + dr
        nc = c + dc

        if (
            valid(nr, nc)
            and distance[nr][nc] == -1
        ):

            distance[nr][nc] = (
                distance[r][c] + 1
            )

            queue.append((nr, nc))
```

The reusable pieces are:

```text
SOURCE
NEIGHBOR
DISTANCE
VISITED
ANSWER
```

---

# 🔥 LC 994 vs LC 542

| Concept          | LC 994         | LC 542                |
| ---------------- | -------------- | --------------------- |
| Sources          | Rotten oranges | Zeros                 |
| Target           | Fresh oranges  | Ones                  |
| BFS              | Multi-source   | Multi-source          |
| Directions       | 4              | 4                     |
| Distance meaning | Minutes        | Nearest-zero distance |
| Initial queue    | All rotten     | All zeros             |
| State transition | `1 → 2`        | `-1 → distance`       |
| Level meaning    | Time           | Distance              |
| Result           | Integer        | Matrix                |
| Complexity       | O(RC)          | O(RC)                 |

The **algorithmic skeleton is almost identical**.

---

# 🧠 THE BIG PATTERN

You now need to internalize:

```text
Question:
"What is the distance from every cell to the nearest source?"

        ↓

Identify all sources.

        ↓

Put ALL sources into queue.

        ↓

Give sources distance 0.

        ↓

BFS outward.

        ↓

First discovery = shortest distance.
```

---

# ⚠️ COMMON INTERVIEW TRAPS

## Trap 1 — BFS from every `1`

Wrong direction.

Think:

```text
EVERY 0 = SOURCE
```

---

## Trap 2 — Only adding one zero

Incorrect.

You need:

```python
for every cell:
    if cell == 0:
        queue.append(cell)
```

---

## Trap 3 — Using DFS

Shortest unweighted distance → BFS.

---

## Trap 4 — Forgetting visited/discovered state

Without it, cells can be repeatedly processed.

Use:

```python
distance[nr][nc] == -1
```

---

## Trap 5 — Allowing diagonal movement

LC 542 uses:

```text
↑
← → 
↓
```

Not:

```text
↖ ↑ ↗
← X →
↙ ↓ ↘
```

---

## Trap 6 — Confusing "nearest zero" with "any zero"

The BFS guarantees the **minimum** distance because it expands in layers.

---

# 🏆 FINAL MASTERY SECTION

## Pattern Extraction

```text
Nearest Source
      ↓
Multiple Sources
      ↓
Put ALL Sources in Queue
      ↓
Multi-Source BFS
      ↓
First Discovery = Minimum Distance
```

---

# Master Template

```text
1. Identify all sources.
2. Put all sources into queue.
3. Set source distance = 0.
4. Mark all sources discovered.
5. BFS.
6. Generate neighbors.
7. Ignore invalid/discovered cells.
8. Assign current distance + 1.
9. Enqueue.
10. Repeat until queue is empty.
```

---

# 🧠 Senior Pattern Recognition

When the interviewer says:

> "Find the distance of every cell from the nearest..."

Immediately ask:

```text
What are the sources?
```

If movement is:

```text
unweighted
```

then:

```text
BFS
```

If there are multiple sources:

```text
Multi-Source BFS
```

So:

```text
Nearest X
+
Grid
+
Equal movement cost
        ↓
Multi-Source BFS
```

---

# 🔥 THE THREE BFS PROBLEMS NOW CONNECT

```text
                    BFS
                     │
          ┌──────────┴──────────┐
          │                     │
     Single Source         Multiple Sources
          │                     │
      LC 1091                 LC 994
          │                     │
   Shortest Path             Time
                                │
                                ↓
                              LC 542
                                │
                         Nearest Distance
```

And the fundamental abstraction is:

```text
              SOURCES
                 ↓
               QUEUE
                 ↓
          SIMULTANEOUS BFS
                 ↓
       DISTANCE PROPAGATION
                 ↓
        MINIMUM DISTANCE
```

---

# 📈 PROGRESS UPDATE

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994 — Rotting Oranges
├── ✅ LC 542 — 01 Matrix
└── ⬜ LC 1162 — As Far from Land as Possible ← NEXT
```

### What changes in LC 1162?

We've now learned:

```text
LC 994
Multiple sources → minimum time to spread

LC 542
Multiple sources → distance to nearest source

LC 1162
Multiple sources → find the MAXIMUM of those nearest-source distances
```

So the next problem is not a new BFS engine.

It is a **new answer-extraction pattern built on the same engine**:

```text
LAND = ALL SOURCES
      ↓
MULTI-SOURCE BFS
      ↓
DISTANCE TO NEAREST LAND
      ↓
MAXIMUM DISTANCE
```

# 🎯 ONE-LINE TAKEAWAY

> **LC 542 = Treat every `0` as a source, put all zeros into one queue, run multi-source BFS, and the first distance assigned to every `1` is its minimum distance to any zero.**

Would you like to tackle LC 1162 with the same full locked format, starting with the senior insights or the dry run?

# 🔥 LC 1162 — As Far from Land as Possible

**LEVEL 3 — MULTI-SOURCE BFS**
**Pattern:** Multi-Source BFS + Nearest-Source Distance + Maximum Distance
**Priority:** 🔥🔥🔥
**Difficulty:** Medium

This is the **third and final problem in our Multi-Source BFS progression**.

We have deliberately built this sequence:

```text
LC 994
Rotting Oranges
     ↓
Multiple sources
     ↓
BFS levels = time
```

```text
LC 542
01 Matrix
     ↓
Multiple sources
     ↓
BFS distance = nearest-source distance
```

```text
LC 1162
As Far from Land as Possible
     ↓
Multiple sources
     ↓
BFS distance = nearest-source distance
     ↓
MAXIMUM distance
```

So **LC 1162 is not a completely new algorithm**.

The BFS engine is already known.

The new skill is:

> **Compute distance from every water cell to its nearest land cell, then find the maximum of those distances.**

---

# 🧠 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given an `n × n` grid:

```text
1 = Land
0 = Water
```

For every water cell, calculate:

> How far is this water cell from its nearest land cell?

Then return the **maximum** such distance.

If the entire grid is land or the entire grid is water:

```python
return -1
```

---

## Example

Input:

```text
[
    [1,0,0],
    [0,0,0],
    [0,0,1]
]
```

Think:

```text
🏝️ 💧 💧
💧 💧 💧
💧 💧 🏝️
```

Distances from nearest land:

```text
0 1 1
1 2 1
1 1 0
```

The farthest water cell is the center:

```text
distance = 2
```

Therefore:

```text
answer = 2
```

---

# 2. 🔥 Hidden Translation

The wording might tempt you to think:

> "For every water cell, search for the nearest land."

That is the wrong direction.

Translate it into:

```text
LAND
 ↓
ALL LAND CELLS ARE SOURCES
 ↓
MULTI-SOURCE BFS
 ↓
DISTANCE TO NEAREST LAND
 ↓
TAKE MAXIMUM
```

That is the entire problem.

---

# 3. The Key Connection to LC 542

LC 542 asked:

> Find the distance from every cell to the nearest `0`.

We did:

```text
ALL 0s
 ↓
sources
 ↓
multi-source BFS
 ↓
distance matrix
```

LC 1162 asks:

> Find the distance from every water cell to the nearest land.

So simply change:

```text
LC 542:
0 = source

LC 1162:
1 = source
```

The BFS mechanism remains the same.

---

# 4. Why Land Is the Source

Suppose:

```text
1 0 0 0
```

Land is:

```text
1
```

The first water cell is:

```text
distance 1
```

The second:

```text
distance 2
```

The third:

```text
distance 3
```

So:

```text
1 0 0 0
0 1 2 3
```

Conceptually, land sends out a wave.

The first wave reaches nearby water.

The next wave reaches farther water.

---

# 5. 🧒 ELI10 Intuition

Imagine islands and ocean.

Every island has a signal tower:

```text
📡       📡
```

Every tower broadcasts simultaneously.

Water receives the signal.

The closest tower determines the distance.

Then we ask:

> Which water cell receives the signal **last**?

That cell is the:

> **farthest water from land.**

So:

```text
All islands
    ↓
Broadcast simultaneously
    ↓
BFS
    ↓
Distance of every water cell
    ↓
Largest distance
```

---

# 6. Why Multi-Source BFS?

Suppose:

```text
1 0 0 0 1
```

There are two land sources.

For the middle cell:

```text
1 → 0 → 0
```

distance from left land:

```text
2
```

From right land:

```text
0 ← 0 ← 1
```

distance:

```text
2
```

The required value is:

```text
min(distance from all land cells)
```

Multi-source BFS computes that automatically.

---

# 7. The Mathematical Problem

For every water cell `w`:

```text
distance(w)
=
min(
    distance(w, land₁),
    distance(w, land₂),
    ...
)
```

Then the final answer is:

```text
max(
    distance(w)
    for every water cell
)
```

So the problem is really:

```text
MIN over sources
        ↓
for each water cell
        ↓
then MAX over all water cells
```

This is a very important distinction.

---

# 8. Why "Maximum" Does NOT Mean Farthest From Every Land

This is a common conceptual mistake.

We don't calculate:

```text
maximum distance to land
```

for each water cell.

We calculate:

```text
minimum distance to land
```

for each water cell.

Then:

```text
maximum of those minimum distances
```

Formally:

```text
max_water [
    min_land [
        distance(water, land)
    ]
]
```

This is the exact mathematical meaning of the problem.

---

# 9. Why Not Run BFS From Every Water Cell?

Naive strategy:

```text
for every water cell:
    BFS until land found
```

If there are `N²` cells and each search can inspect `N²` cells:

```text
O(N⁴)
```

in the worst case.

That's unnecessary.

Multi-source BFS processes all cells together:

```text
O(N²)
```

---

# 10. Why the First Discovery Is Optimal

This is inherited directly from LC 542.

All land sources start at:

```text
distance = 0
```

Then BFS processes:

```text
distance 0
 ↓
distance 1
 ↓
distance 2
 ↓
distance 3
...
```

Therefore, when a water cell is first discovered:

```text
first discovery = nearest land
```

So we don't need to update it later.

---

# 11. BFS Wave Interpretation

Consider:

```text
1 0 0
0 0 0
0 0 0
```

Start:

```text
0 . .
. . .
. . .
```

After distance 1:

```text
0 1 .
1 . .
. . .
```

After distance 2:

```text
0 1 2
1 2 .
2 . .
```

After distance 3:

```text
0 1 2
1 2 3
2 3 .
```

The final farthest distance:

```text
3
```

---

# 12. Why We Don't Actually Need a Distance Matrix

This is an important improvement over LC 542.

In LC 542, the required output is:

```text
distance matrix
```

So we need to store every distance.

In LC 1162, we only need:

```text
maximum distance
```

Therefore we can maintain:

```python
distance
```

inside the queue.

For example:

```python
queue.append((r, c, 0))
```

Then:

```python
nr, nc, distance + 1
```

And:

```python
answer = max(answer, distance)
```

This allows us to avoid creating a separate `distance` matrix.

---

# 13. Two Valid Approaches

### Approach A — Distance Matrix

```text
grid
+
distance matrix
+
queue
```

Very similar to LC 542.

### Approach B — Level BFS

```text
grid
+
queue
+
levels
```

Because every BFS level represents a distance.

For LC 1162, **level-order BFS is particularly elegant** because we only need the final maximum distance.

---

# 14. Level-Based Solution

Initialize:

```python
distance = -1
```

Then:

```python
while queue:
    level_size = len(queue)

    for _ in range(level_size):
        ...
    
    distance += 1
```

Why start at `-1`?

Initially, all land cells are:

```text
distance = 0
```

After processing the land frontier:

```text
distance = 1
```

After processing the first water layer:

```text
distance = 2
```

etc.

An alternative is to initialize:

```python
distance = 0
```

and increment after each layer while returning `distance - 1` appropriately.

I prefer a formulation where the state explicitly represents the current distance.

---

# 15. Cleaner Alternative: Store Distance in Queue

We can simply do:

```python
queue = deque()

for every land:
    queue.append((r, c, 0))
```

Then:

```python
r, c, distance = queue.popleft()
```

For a new water cell:

```python
queue.append(
    (nr, nc, distance + 1)
)
```

And:

```python
answer = max(answer, distance + 1)
```

This is extremely easy to reason about.

---

# 16. Which Version Should You Master?

For **LC 1162**, master both concepts:

### Conceptual version

```text
Multi-source BFS levels
```

### Implementation version

```text
Queue stores (row, col, distance)
```

Why?

Because interviews may modify the problem.

For example:

> "Return the coordinates of the farthest cell."

or:

> "Return the distance and the cell."

Storing distance directly makes such modifications easy.

---

# 17. Early Impossibility Checks

There are two important cases.

### Entire grid is land

```text
1 1
1 1
```

There is no water.

Return:

```text
-1
```

### Entire grid is water

```text
0 0
0 0
```

There is no land source.

Return:

```text
-1
```

So we need both:

```text
at least one land
AND
at least one water
```

---

# 18. Why Modify Water `0 → 1`?

When we discover a water cell:

```python
grid[nr][nc] = 1
```

This means:

> This cell has already been discovered.

We can reuse the grid as our visited structure.

But notice the conceptual meaning:

Originally:

```text
1 = land
0 = water
```

During BFS:

```text
1 = already discovered
0 = undiscovered water
```

Once a water cell is discovered, changing it to `1` prevents duplicate insertion.

---

# 19. Core Invariant

The key invariant is:

> Every cell in the BFS queue has already been reached from some land cell, and the stored distance is the minimum distance from any land source.

Additionally:

> Every cell is enqueued at most once.

Therefore the BFS remains linear.

---

# 20. Why the Maximum Distance Is the Answer

After BFS, every water cell has a minimum distance to land.

We want:

```text
the water cell that is farthest from its nearest land
```

Therefore:

```text
answer = maximum minimum distance
```

Again:

```text
MAX(
    MIN(distance to each land)
)
```

This is the central mathematical interpretation.

---

# 21. Complexity

Let the grid be:

```text
n × n
```

There are:

```text
n²
```

cells.

Initial scan:

```text
O(n²)
```

Every cell enters the queue at most once.

Each cell checks 4 neighbors:

```text
O(4n²)
```

Therefore:

```text
Time = O(n²)
```

Queue can hold O(n²) cells:

```text
Space = O(n²)
```

No separate distance matrix is necessary.

---

# 22. Real-World Interpretation

Imagine:

```text
1 = hospital
0 = location
```

We want:

> What is the greatest distance any location is from its nearest hospital?

All hospitals become sources.

BFS expands simultaneously.

The final maximum distance tells us the location with the greatest nearest-hospital distance.

Same algorithm.

---

# ⚙️ ALGORITHM — STEP-BY-STEP

## Step 1 → Scan the entire grid

For every cell:

```text
if grid[r][c] == 1
```

add it to the queue.

These are our sources.

---

## Step 2 → Count land and water

Maintain:

```text
land_count
water_count
```

Why?

Because:

```text
no land → impossible
no water → impossible
```

Return `-1` in either case.

---

## Step 3 → Initialize all land as BFS sources

For every land cell:

```python
queue.append((r, c, 0))
```

The distance is `0` because land is the source.

---

## Step 4 → Start Multi-Source BFS

While the queue is not empty:

```python
while queue:
```

---

## Step 5 → Pop the current cell

```python
r, c, distance = queue.popleft()
```

This distance is already the minimum distance from any land cell.

---

## Step 6 → Explore four neighbors

For each:

```text
up
down
left
right
```

calculate:

```python
nr = r + dr
nc = c + dc
```

---

## Step 7 → Check boundaries

Require:

```text
0 <= nr < n
0 <= nc < n
```

---

## Step 8 → Check whether the neighbor is undiscovered water

Require:

```python
grid[nr][nc] == 0
```

---

## Step 9 → Mark it discovered

```python
grid[nr][nc] = 1
```

Now it cannot be added again.

---

## Step 10 → Assign its distance

```python
new_distance = distance + 1
```

Because moving one grid edge costs one unit.

---

## Step 11 → Update the answer

```python
answer = max(answer, new_distance)
```

We want the largest nearest-land distance.

---

## Step 12 → Enqueue the cell

```python
queue.append(
    (nr, nc, new_distance)
)
```

It becomes part of the BFS frontier.

---

## Step 13 → Finish BFS

Once the queue is empty, every water cell has been reached.

`answer` contains the largest distance.

Return it.

---

# 💻 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def maxDistance(self, grid):

        n = len(grid)

        queue = deque()

        land_count = 0
        water_count = 0

        # Find all land cells.
        # Every land cell is a BFS source.
        for r in range(n):
            for c in range(n):

                if grid[r][c] == 1:

                    land_count += 1

                    queue.append((r, c, 0))

                else:

                    water_count += 1

        # All land or all water.
        if land_count == 0 or water_count == 0:
            return -1

        directions = [
            (-1, 0),
            (1, 0),
            (0, -1),
            (0, 1)
        ]

        answer = 0

        # Multi-source BFS.
        while queue:

            r, c, distance = queue.popleft()

            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                # Valid undiscovered water cell.
                if (
                    0 <= nr < n
                    and 0 <= nc < n
                    and grid[nr][nc] == 0
                ):

                    # Mark as discovered.
                    grid[nr][nc] = 1

                    new_distance = distance + 1

                    # Track the farthest water cell.
                    answer = max(
                        answer,
                        new_distance
                    )

                    # Add to next BFS frontier.
                    queue.append(
                        (nr, nc, new_distance)
                    )

        return answer
```

---

# Complexity Derivation

### Initial scan

Every cell:

```text
n²
```

is inspected:

```text
O(n²)
```

### BFS

Every cell becomes discovered at most once.

For every cell, at most 4 directions are checked:

```text
O(4n²)
```

Therefore:

```text
O(n²)
```

overall.

### Space

Worst-case queue:

```text
O(n²)
```

No extra distance matrix is used.

Therefore:

```text
Time  = O(n²)
Space = O(n²)
```

---

# 🎤 Interview Justification

Say:

> "This is a multi-source BFS problem. Every land cell is an initial source at distance zero. I put all land cells into the queue before starting BFS. Then I expand simultaneously into water cells, assigning each newly discovered cell a distance one greater than its source frontier. Because BFS explores in increasing distance order, the first time a water cell is reached is its minimum distance to any land cell. I track the maximum of those distances because the problem asks for the water cell farthest from its nearest land. The algorithm is O(n²) time and O(n²) space."

That's the complete reasoning.

---

# 🧪 BLOCK 3 — FULL CODE + DRY RUN

Consider:

```text
[
    [1,0,0],
    [0,0,0],
    [0,0,1]
]
```

Visual:

```text
🏝️ 💧 💧
💧 💧 💧
💧 💧 🏝️
```

Land sources:

```text
(0,0)
(2,2)
```

Initial queue:

```text
[
    (0,0,0),
    (2,2,0)
]
```

---

## Full Runnable Code

```python
from collections import deque


class Solution:

    def maxDistance(self, grid):

        n = len(grid)

        queue = deque()

        land_count = 0
        water_count = 0

        for r in range(n):
            for c in range(n):

                if grid[r][c] == 1:

                    land_count += 1
                    queue.append((r, c, 0))

                else:

                    water_count += 1

        if land_count == 0 or water_count == 0:
            return -1

        directions = [
            (-1, 0),
            (1, 0),
            (0, -1),
            (0, 1)
        ]

        answer = 0

        while queue:

            r, c, distance = queue.popleft()

            for dr, dc in directions:

                nr = r + dr
                nc = c + dc

                if (
                    0 <= nr < n
                    and 0 <= nc < n
                    and grid[nr][nc] == 0
                ):

                    grid[nr][nc] = 1

                    new_distance = distance + 1

                    answer = max(
                        answer,
                        new_distance
                    )

                    queue.append(
                        (nr, nc, new_distance)
                    )

        return answer


# -------------------------
# Example
# -------------------------

grid = [
    [1, 0, 0],
    [0, 0, 0],
    [0, 0, 1]
]

solution = Solution()

result = solution.maxDistance(grid)

print("Maximum Distance:", result)
```

### Output

```text
Maximum Distance: 2
```

---

# 🔬 DETAILED DRY RUN

Initial grid:

```text
1 0 0
0 0 0
0 0 1
```

Sources:

```text
(0,0)
(2,2)
```

Queue:

```text
[(0,0,0), (2,2,0)]
```

---

# 🟢 BFS Layer 0

Both land cells:

```text
(0,0) → distance 0
(2,2) → distance 0
```

Visual:

```text
0 . .
. . .
. . 0
```

---

# 🟡 BFS Layer 1

From `(0,0)`:

```text
(1,0) → distance 1
(0,1) → distance 1
```

From `(2,2)`:

```text
(1,2) → distance 1
(2,1) → distance 1
```

Visual:

```text
0 1 .
1 . 1
. 1 0
```

Queue now contains:

```text
[
    (1,0,1),
    (0,1,1),
    (1,2,1),
    (2,1,1)
]
```

Current maximum:

```text
answer = 1
```

---

# 🔴 BFS Layer 2

Now process those four cells.

They meet at the center:

```text
(1,1)
```

The center is reached from multiple sides.

Its minimum distance from land is:

```text
2
```

So:

```text
answer = 2
```

Final distance structure:

```text
0 1 2
1 2 1
2 1 0
```

Therefore:

```text
answer = 2
```

---

# 📊 DRY-RUN TABLE

| BFS Layer | Cells Processed           | Newly Discovered          | Distance |
| --------: | ------------------------- | ------------------------- | -------: |
|         0 | `(0,0),(2,2)`             | `(1,0),(0,1),(1,2),(2,1)` |        1 |
|         1 | `(1,0),(0,1),(1,2),(2,1)` | `(1,1)`                   |        2 |
|         2 | `(1,1)`                   | None                      |        2 |

Final:

```text
0 1 2
1 2 1
2 1 0
```

Maximum:

```text
2
```

---

# 🧠 WHY THE CENTER IS 2

From the top-left land:

```text
(0,0)
   ↓
(1,0)
   ↓
(1,1)
```

Two moves.

From bottom-right:

```text
(2,2)
   ↑
(1,2)
   ↑
(1,1)
```

Again two moves.

Therefore:

```text
min(2,2) = 2
```

The center is the farthest water cell from its **nearest** land.

---

# 🎯 BLOCK 4 — INTERVIEW Q&A

## Q1. Why are all land cells inserted into the queue initially?

Because every land cell is a source at distance zero.

They all spread simultaneously.

This is multi-source BFS.

---

## Q2. Why don't we start BFS from every water cell?

Because that would repeat work.

Instead, reverse the problem:

```text
water → search for land
```

becomes:

```text
land → spread toward water
```

All land cells can be processed simultaneously using one BFS.

---

## Q3. Why does the first discovery give the nearest land distance?

BFS processes cells in increasing distance order.

All sources begin at distance zero.

Therefore:

```text
first discovery = minimum distance
```

---

## Q4. Why are we taking the maximum?

The problem asks:

> Which water cell is farthest from land?

But for each water cell, we first need its distance to its **nearest** land.

So the mathematical operation is:

```text
MAX over water cells
    of
MIN distance to land
```

---

## Q5. Why can we modify `grid`?

Once a water cell is discovered, we change:

```text
0 → 1
```

This prevents another BFS path from inserting it again.

So the grid itself acts as our visited structure.

---

## Q6. Why is all-land or all-water `-1`?

### All land

There is no water cell for which a distance can be calculated.

### All water

There is no land source.

In either case, the requested farthest water-to-land distance does not exist.

---

# 🔥 THE THREE-PROBLEM MASTER CHAIN

This is the most important part.

## LC 994

```text
Rotten oranges
      ↓
All rotten oranges = sources
      ↓
Multi-source BFS
      ↓
BFS level = minutes
```

---

## LC 542

```text
01 Matrix
      ↓
All zeros = sources
      ↓
Multi-source BFS
      ↓
BFS distance = nearest-zero distance
```

---

## LC 1162

```text
As Far from Land as Possible
      ↓
All land = sources
      ↓
Multi-source BFS
      ↓
BFS distance = nearest-land distance
      ↓
MAXIMUM distance
```

So:

```text
                MULTI-SOURCE BFS
                       ↓
            ┌──────────┼──────────┐
            ↓          ↓          ↓
          LC 994     LC 542     LC 1162
            ↓          ↓          ↓
          TIME      MIN DIST    MAX MIN DIST
```

---

# 🧠 MASTER MULTI-SOURCE BFS TEMPLATE

```python
from collections import deque


queue = deque()

# 1. Add ALL sources
for r in range(rows):
    for c in range(cols):

        if is_source(r, c):

            mark_source(r, c)

            queue.append(
                (r, c, 0)
            )


answer = 0

# 2. Multi-source BFS
while queue:

    r, c, distance = queue.popleft()

    for dr, dc in directions:

        nr = r + dr
        nc = c + dc

        if valid(nr, nc) and unvisited(nr, nc):

            mark_visited(nr, nc)

            new_distance = distance + 1

            answer = update_answer(
                answer,
                new_distance
            )

            queue.append(
                (nr, nc, new_distance)
            )

return answer
```

The problem-specific pieces are only:

```text
1. What is a source?
2. What is a valid neighbor?
3. How is a cell marked visited?
4. What answer do we extract?
```

The BFS engine stays the same.

---

# 🧠 PATTERN EXTRACTION

## Pattern 1 — "Several sources start simultaneously"

```text
ALL SOURCES
    ↓
QUEUE
    ↓
MULTI-SOURCE BFS
```

---

## Pattern 2 — "Distance from nearest source"

```text
ALL SOURCES
    ↓
BFS
    ↓
FIRST DISCOVERY
    ↓
MINIMUM DISTANCE
```

---

## Pattern 3 — "Farthest cell from nearest source"

```text
ALL SOURCES
    ↓
MULTI-SOURCE BFS
    ↓
DISTANCE TO NEAREST SOURCE
    ↓
TAKE MAXIMUM
```

That's exactly LC 1162.

---

# 🧠 SENIOR PATTERN RECOGNITION

When you see:

> "For every cell, find the distance to the nearest X."

Ask:

```text
What is X?
```

Then:

```text
X = source
```

If movement is unweighted:

```text
BFS
```

If there are multiple X:

```text
MULTI-SOURCE BFS
```

If they ask:

> "What is the farthest such cell?"

Then:

```text
MAXIMUM OF MINIMUM DISTANCES
```

So the complete recognition rule is:

```text
GRID
+
NEAREST SOURCE
+
MULTIPLE SOURCES
+
UNWEIGHTED MOVEMENT
        ↓
MULTI-SOURCE BFS
```

And if the question asks for the farthest:

```text
MULTI-SOURCE BFS
        ↓
MAX DISTANCE
```

---

# ⚠️ COMMON INTERVIEW TRAPS

## Trap 1 — BFS from every water cell

Don't.

Reverse the direction.

```text
❌ water → search land

✅ land → expand toward water
```

---

## Trap 2 — Starting with only one land cell

Wrong.

Every land cell is a source.

```python
for every land:
    queue.append(land)
```

---

## Trap 3 — Taking maximum distance from each land

Wrong mathematical interpretation.

We need:

```text
MAX(
    MIN(distance to land)
)
```

not:

```text
MIN(
    MAX(distance from land)
)
```

---

## Trap 4 — Forgetting the all-land case

```text
1 1
1 1
```

There is no water.

Return:

```text
-1
```

---

## Trap 5 — Forgetting the all-water case

```text
0 0
0 0
```

There is no source.

Return:

```text
-1
```

---

## Trap 6 — Using 8 directions

LC 1162 uses only:

```text
↑
← X →
↓
```

not diagonals.

---

## Trap 7 — Re-enqueueing already discovered water

Mark immediately:

```python
grid[nr][nc] = 1
```

before enqueueing.

---

# 🏆 FINAL MASTERY SECTION

## Pattern Extraction

```text
Farthest Water
      ↓
Distance to Nearest Land
      ↓
All Land = Sources
      ↓
Multi-Source BFS
      ↓
First Discovery = Minimum Distance
      ↓
Maximum of Those Distances
```

---

# Master Template

```text
1. Identify all sources.
2. Put ALL sources into queue.
3. Give sources distance 0.
4. Mark them discovered.
5. BFS simultaneously.
6. Generate neighbors.
7. Ignore invalid/discovered cells.
8. Assign distance + 1.
9. Mark before enqueue.
10. Track required answer.
11. Continue until queue empty.
```

---

# 🔥 The Three Multi-Source BFS Variations

| Problem     | Sources        | What BFS Measures        | Final Answer          |
| ----------- | -------------- | ------------------------ | --------------------- |
| **LC 994**  | Rotten oranges | Time to spread           | Maximum required time |
| **LC 542**  | Zeros          | Distance to nearest zero | Distance matrix       |
| **LC 1162** | Land           | Distance to nearest land | Maximum distance      |

The underlying algorithm:

```text
ALL SOURCES
     ↓
ONE QUEUE
     ↓
SIMULTANEOUS BFS
     ↓
NEAREST-SOURCE DISTANCE
```

Only the **answer extraction** changes.

---

# 📈 PROGRESS UPDATE

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994 — Rotting Oranges
├── ✅ LC 542 — 01 Matrix
└── ✅ LC 1162 — As Far from Land as Possible

LEVEL 4 — LEVEL-ORDER BFS
├── ⬜ LC 102 — Binary Tree Level Order Traversal ← NEXT
└── ⬜ LC 199 — Binary Tree Right Side View
```

Now we've completed the entire:

```text
🔥 LEVEL 3 — MULTI-SOURCE BFS
```

and mastered the progression:

```text
LC 994
Multi-source BFS → Time

       ↓

LC 542
Multi-source BFS → Nearest distance

       ↓

LC 1162
Multi-source BFS → Maximum nearest distance
```

The next conceptual jump is important:

```text
GRID BFS
   ↓
MULTI-SOURCE BFS
   ↓
TREE BFS
   ↓
LEVEL-ORDER BFS
```

# 🎯 ONE-LINE TAKEAWAY

> **LC 1162 = Treat every land cell as a simultaneous BFS source, compute each water cell's minimum distance to land, and return the maximum of those minimum distances.**

Would you like to continue with LC 102 next, or practice one more multi-source BFS variation first?




# LEVEL 4

# LEVEL 4 — LEVEL-ORDER BFS

```
LEVEL 4 — LEVEL-ORDER BFS
├── LC 102 — Binary Tree Level Order Traversal
└── LC 199 — Binary Tree Right Side View
```

# 🔵 LC 102 — Binary Tree Level Order Traversal

Difficulty: Medium Pattern: Binary Tree + Queue + BFS + Level Separation Priority: 🔥🔥🔥🔥🔥

# BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given the root of a binary tree.

Return the values of its nodes level by level, from left to right.

For example:

```
           3
          / \
         9   20
            /  \
           15   7
```

Expected output:

Python

Run

```
[
    [3],
    [9, 20],
    [15, 7]
]
```

The tree must be processed like this:

```
Level 0 → [3]
Level 1 → [9, 20]
Level 2 → [15, 7]
```

The key requirement is that nodes belonging to the same depth must be grouped together.

## 2. Hidden Translation — What Is the Problem Really Asking?

The important phrases are:

|
Problem phrase

|

Translation

|
| --- | --- |
|

“Level by level”

|

BFS

|
|

“Top to bottom”

|

Process shallow nodes first

|
|

“Left to right”

|

Preserve queue order

|
|

“Return each level separately”

|

Process one queue layer at a time

|
|

“Binary tree”

|

Each node has at most two children

|

The moment you see level by level, immediately think:

```
Binary Tree
     ↓
Queue
     ↓
BFS
     ↓
Process one level at a time
```

## 3. Why DFS Is Not the Natural First Choice

DFS explores one branch deeply before moving to another branch.

For example, preorder DFS might visit:

```
3 → 9 → 20 → 15 → 7
```

That traversal does not automatically group nodes by depth.

You can force DFS to track depths, but that adds extra bookkeeping.

BFS naturally processes nodes in increasing depth order:

```
Distance/depth 0
       ↓
Distance/depth 1
       ↓
Distance/depth 2
       ↓
Distance/depth 3
```

Therefore, BFS directly matches the problem requirement.

> DFS can solve this problem, but BFS expresses the intended structure more naturally.

## 4. ELI10 Intuition

Imagine children standing in school lines.

```
Principal
   ↓
Class 1 students
   ↓
Class 2 students
   ↓
Class 3 students
```

You must finish recording all students in one class before moving to the next class.

The queue works like a waiting line:

1. Put the root in the queue.

2. Take the first student.

3. Add their children to the line.

4. Process everyone currently in the line as one level.

5. Repeat.

The most important idea is:

> At the beginning of every iteration, the queue contains exactly one tree level.

## 5. Why a Queue Works

A queue follows FIFO:

> First In, First Out.

Suppose the root is `3`.

Initially:

```
Queue: [3]
```

Process `3`:

```
Queue: [9, 20]
```

The children of `3` are now waiting.

Process `9`:

```
Queue: [20]
```

Process `20`:

```
Queue: [15, 7]
```

The next nodes are exactly the nodes at the next depth.

This happens because a tree edge always moves us from one level to the next.

## 6. The Core Insight: Capture the Current Queue Size

This is the most important line in the solution:

Python

Run

```
level_size = len(queue)
```

Why?

Because the queue may change while we process the current level.

Example:

```
Before processing level 1:

Queue = [9, 20]
```

The queue length is `2`.

That means:

```
There are exactly 2 nodes in the current level.
```

While processing those two nodes, we may add their children:

```
After processing 9:
Queue = [20, ...]

After processing 20:
Queue = [15, 7, ...]
```

If we used a dynamic condition such as:

Python

Run

```
while queue:
```

for the inner loop, we would accidentally process the next level in the same group.

Therefore:

Python

Run

```
level_size = len(queue)

for _ in range(level_size):
    ...
```

freezes the boundary of the current level.

## 7. Pattern Intuition

The standard level-order BFS structure is:

```
while queue is not empty:

    level_size = number of nodes currently in queue
    current_level = []

    repeat level_size times:
        remove one node
        process the node
        add its children

    add current_level to answer
```

Visual model:

```
QUEUE
  ↓
SNAPSHOT CURRENT LEVEL SIZE
  ↓
PROCESS ONLY THAT MANY NODES
  ↓
COLLECT THEIR VALUES
  ↓
CHILDREN FORM THE NEXT LEVEL
  ↓
REPEAT
```

## 8. Why We Do Not Mark Nodes as Visited

In a normal graph, a node can have multiple incoming edges.

That means cycles and repeated visits are possible.

In a normal tree:

* Every child has exactly one parent.

* There are no cycles.

* A node is reached through only one path from the root.

Therefore, a separate `visited` set is unnecessary for a valid binary tree.

> Tree structure itself prevents repeated traversal.

## 9. Important Invariant

During the outer BFS loop:

> The queue contains nodes belonging to the next unprocessed frontier, while the first `level_size` nodes represent the current level.

More precisely:

1. Before processing a level, the queue contains exactly the nodes of that level.

2. `level_size` stores the number of nodes in that level.

3. The loop processes exactly those nodes.

4. Their children are appended for the next level.

5. The collected values form one complete level.

This invariant guarantees correct grouping.

## 10. Complexity Derivation

Let:

* `N` = number of nodes in the tree.

* `H` = height of the tree.

### Time complexity

Every node is:

* inserted into the queue once,

* removed from the queue once,

* processed once.

Therefore:

T(N)=O(N)T(N)=O(N)T(N)=O(N)

### Auxiliary space complexity

The queue can contain an entire tree level.

In a balanced tree, the largest level can contain approximately `N / 2` nodes.

Therefore, the queue requires:

O(N)O(N)O(N)

The output itself also contains all node values:

O(N)O(N)O(N)

For interview discussions, state:

* Time: `O(N)`

* Auxiliary space: `O(W)`, where `W` is the maximum width of the tree.

* Worst-case auxiliary space: `O(N)`

* Output space: `O(N)`

## 11. Important Edge Cases

|
Case

|

Expected result

|
| --- | --- |
|

`root = None`

|

`[]`

|
|

Only one node

|

`[[value]]`

|
|

Completely skewed tree

|

One value per level

|
|

Complete binary tree

|

Multiple values per level

|
|

Negative node values

|

Process normally

|
|

Duplicate node values

|

Process normally

|

Example of a left-skewed tree:

```
    1
   /
  2
 /
3
```

Output:

Python

Run

```
[[1], [2], [3]]
```

## 12. Industry Applications

Level-order traversal is useful in:

* Rendering hierarchical UI components.

* Processing organizational hierarchies.

* Traversing directory structures by depth.

* Analyzing dependency trees.

* Finding the minimum number of edges from the root to a node.

* Processing nodes in a tree-shaped workflow.

* Tree serialization and deserialization.

* Finding the maximum width of a binary tree.

In ML/MLOps, a similar pattern can appear when processing:

* Hierarchical feature groups.

* Dependency layers in workflow graphs.

* Staged execution pipelines.

* Tree-structured search spaces.

# ⚙️ ALGORITHM — STEP-BY-STEP

```
Step 1 → If the root is None, return an empty list.

Step 2 → Create an empty result list.

Step 3 → Create a queue and insert the root.

Step 4 → While the queue is not empty:

         Step 4.1 → Store the current queue length in level_size.

         Step 4.2 → Create an empty current_level list.

         Step 4.3 → Repeat level_size times:

                    a. Remove one node from the front of the queue.

                    b. Add its value to current_level.

                    c. If the node has a left child,
                       add the left child to the queue.

                    d. If the node has a right child,
                       add the right child to the queue.

         Step 4.4 → Add current_level to the result.

Step 5 → Return the result.
```

The crucial operation is:

Python

Run

```
level_size = len(queue)
```

It ensures that each inner loop processes only the current level.

# BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

Python

Run

```
from collections import deque


class Solution:
    def levelOrder(self, root):

        # If the tree is empty, return an empty list.
        if root is None:
            return []

        result = []

        # The queue initially contains only the root.
        queue = deque([root])

        # Continue until every node has been processed.
        while queue:

            # Capture the number of nodes in the current level.
            level_size = len(queue)

            # Store values belonging to this level.
            current_level = []

            # Process only the nodes that existed at
            # the beginning of this level.
            for _ in range(level_size):

                # Remove the oldest node.
                node = queue.popleft()

                # Store its value.
                current_level.append(node.val)

                # Add the left child for the next level.
                if node.left is not None:
                    queue.append(node.left)

                # Add the right child for the next level.
                if node.right is not None:
                    queue.append(node.right)

            # The current level is now complete.
            result.append(current_level)

        return result
```

## Complexity

* Time: `O(N)`

* Auxiliary space: `O(W)`, where `W` is the maximum tree width.

* Worst-case auxiliary space: `O(N)`

* Output space: `O(N)`

## Interview Justification

You can say:

> “Because the problem requires values grouped by depth, I use breadth-first search with a queue. At the beginning of each iteration, I capture the queue size, which represents the number of nodes in the current level. I process exactly that many nodes, collect their values, and enqueue their children for the next level. Every node is processed once, so the time complexity is O(N).”

# BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

Python

Run

```
from collections import deque


class TreeNode:

    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


class Solution:

    def levelOrder(self, root):

        if root is None:
            return []

        result = []

        queue = deque([root])

        while queue:

            level_size = len(queue)

            current_level = []

            for _ in range(level_size):

                node = queue.popleft()

                current_level.append(node.val)

                if node.left is not None:
                    queue.append(node.left)

                if node.right is not None:
                    queue.append(node.right)

            result.append(current_level)

        return result


# Construct the binary tree:

#           3
#          / \
#         9   20
#            /  \
#           15   7

root = TreeNode(3)

root.left = TreeNode(9)
root.right = TreeNode(20)

root.right.left = TreeNode(15)
root.right.right = TreeNode(7)


# Create the solution object.
solution = Solution()

# Call the function.
result = solution.levelOrder(root)

# Print the result.
print("Level Order Traversal:", result)
```

## Output

```
Level Order Traversal: [[3], [9, 20], [15, 7]]
```

## Detailed Dry Run

Input tree:

```
           3
          / \
         9   20
            /  \
           15   7
```

### Initial State

```
Queue  = [3]
Result = []
```

### Level 0

Python

Run

```
level_size = len(queue)

level_size = 1
```

The current level contains only node `3`.

|
Operation

|

Queue

|

Current level

|

Result

|
| --- | --- | --- | --- |
|

Start

|

`[3]`

|

`[]`

|

`[]`

|
|

Remove `3`

|

`[]`

|

`[3]`

|

`[]`

|
|

Add left child `9`

|

`[9]`

|

`[3]`

|

`[]`

|
|

Add right child `20`

|

`[9, 20]`

|

`[3]`

|

`[]`

|
|

Finish level

|

`[9, 20]`

|

—

|

`[[3]]`

|

### Level 1

```
level_size = 2
```

The current level contains exactly two nodes:

```
[9, 20]
```

#### Process node `9`

```
Queue before: [9, 20]
```

Remove `9`:

```
Queue: [20]
Current level: [9]
```

Node `9` has no children.

#### Process node `20`

Remove `20`:

```
Queue: []
Current level: [9, 20]
```

Add its children:

```
Queue: [15, 7]
```

|
Operation

|

Queue

|

Current level

|

Result

|
| --- | --- | --- | --- |
|

Start

|

`[9, 20]`

|

`[]`

|

`[[3]]`

|
|

Remove `9`

|

`[20]`

|

`[9]`

|

`[[3]]`

|
|

Remove `20`

|

`[]`

|

`[9, 20]`

|

`[[3]]`

|
|

Add `15`

|

`[15]`

|

`[9, 20]`

|

`[[3]]`

|
|

Add `7`

|

`[15, 7]`

|

`[9, 20]`

|

`[[3]]`

|
|

Finish level

|

`[15, 7]`

|

—

|

`[[3], [9, 20]]`

|

### Level 2

```
level_size = 2
```

The current level is:

```
[15, 7]
```

Neither node has children.

|
Operation

|

Queue

|

Current level

|

Result

|
| --- | --- | --- | --- |
|

Start

|

`[15, 7]`

|

`[]`

|

`[[3], [9, 20]]`

|
|

Remove `15`

|

`[7]`

|

`[15]`

|

`[[3], [9, 20]]`

|
|

Remove `7`

|

`[]`

|

`[15, 7]`

|

`[[3], [9, 20]]`

|
|

Finish level

|

`[]`

|

—

|

`[[3], [9, 20], [15, 7]]`

|

The queue is empty, so the algorithm terminates.

## Final Output

Python

Run

```
[[3], [9, 20], [15, 7]]
```

# BLOCK 4 — INTERVIEW Q&A

## Question 1: Why do we store `len(queue)` before processing a level?

Answer:

Because children are added to the queue while processing the current level.

If we do not freeze the queue size, we may process newly added children in the same level.

Python

Run

```
level_size = len(queue)
```

ensures that we process exactly the nodes belonging to the current level.

## Question 2: Why use `deque` instead of a normal Python list?

Answer:

We need to remove elements from the front of the queue.

For a list:

Python

Run

```
queue.pop(0)
```

takes `O(N)` time because the remaining elements must be shifted.

For a deque:

Python

Run

```
queue.popleft()
```

takes `O(1)` time.

Therefore, `deque` is the appropriate queue implementation in Python.

## Question 3: Can DFS solve this problem?

Answer:

Yes.

DFS can track the depth of each node and append its value to the corresponding result list.

However, BFS naturally processes nodes level by level, so it is the more direct solution for this problem.

## Question 4: Why is a visited set unnecessary?

Answer:

A valid binary tree has no cycles, and every node has only one parent.

Therefore, each node can be reached only once from the root.

A visited set is generally necessary for graphs, but not for an ordinary tree traversal.

## Question 5: What happens if the tree is completely skewed?

Example:

```
1
 \
  2
   \
    3
     \
      4
```

Output:

Python

Run

```
[[1], [2], [3], [4]]
```

The algorithm still works because each level contains only one node.

The time complexity remains `O(N)`.

## Question 6: How would you return the average value of each level?

Answer:

Instead of storing only the values, calculate the sum of each level.

Python

Run

```
averages = []

while queue:

    level_size = len(queue)
    level_sum = 0

    for _ in range(level_size):

        node = queue.popleft()
        level_sum += node.val

        if node.left:
            queue.append(node.left)

        if node.right:
            queue.append(node.right)

    averages.append(level_sum / level_size)
```

The BFS structure remains unchanged.

Only the aggregation logic changes.

# PATTERN EXTRACTION

## The Reusable Level-Order BFS Template

Python

Run

```
from collections import deque


def level_order(root):

    if root is None:
        return []

    result = []

    queue = deque([root])

    while queue:

        level_size = len(queue)

        current_level = []

        for _ in range(level_size):

            node = queue.popleft()

            current_level.append(node.val)

            if node.left:
                queue.append(node.left)

            if node.right:
                queue.append(node.right)

        result.append(current_level)

    return result
```

## What Changes in Variations?

|
Variation

|

Change

|
| --- | --- |
|

Level values

|

Append `node.val`

|
|

Level sum

|

Add values

|
|

Level average

|

Sum divided by `level_size`

|
|

Level maximum

|

Track maximum

|
|

Zigzag traversal

|

Reverse alternate levels

|
|

Right-side view

|

Store the last node of each level

|
|

Minimum depth

|

Stop at the first leaf

|
|

Maximum width

|

Track queue size

|

The BFS skeleton stays almost identical.

# SENIOR PATTERN RECOGNITION

When you see:

* “Return values level by level”

* “Group nodes by depth”

* “Traverse each level separately”

* “Print the tree one row at a time”

* “Process nodes from top to bottom”

Think:

```
BINARY TREE
    ↓
QUEUE
    ↓
BFS
    ↓
len(queue)
    ↓
PROCESS ONE LEVEL
    ↓
STORE RESULT
```

## Connection to Earlier Problems

You have already learned:

```
LC 1971
Graph → BFS → Reachability

LC 1091
Grid → BFS → Shortest Path

LC 994
Multiple Sources → BFS → Time

LC 542
Multiple Sources → BFS → Nearest Distance

LC 1162
Multiple Sources → BFS → Maximum Distance
```

Now:

```
LC 102
Tree → BFS → Level Separation
```

The underlying engine is the same:

Python

Run

```
queue.popleft()
```

The difference is what we track:

|
Problem

|

What BFS tracks

|
| --- | --- |
|

LC 1971

|

Reachability

|
|

LC 1091

|

Shortest distance

|
|

LC 994

|

Time by level

|
|

LC 542

|

Distance from nearest source

|
|

LC 1162

|

Maximum nearest-source distance

|
|

LC 102

|

Values grouped by level

|

# PROGRESS UPDATE

```
LEVEL 4 — LEVEL-ORDER BFS

├── ✅ LC 102 — Binary Tree Level Order Traversal
└── ⬜ LC 199 — Binary Tree Right Side View ← NEXT
```

# One-Line Takeaway

> Level-order traversal = BFS + queue-size snapshot + process exactly one level at a time.


# 🔵 LC 199 — Binary Tree Right Side View

Difficulty: Medium Pattern: Binary Tree + BFS + Level-Order Traversal Priority: 🔥🔥🔥🔥

# BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given the root of a binary tree.

Imagine standing on the right side of the tree.

Return the node values that are visible from that side, starting from the top and moving downward.

### Example

```
           1
          / \
         2   3
          \   \
           5   4
```

From the right side, you can see:

```
1
3
4
```

Therefore, the output is:

Python

Run

```
[1, 3, 4]
```

## 2. What Does “Right Side View” Really Mean?

The right-side view contains:

> The rightmost node at every level of the binary tree.

For the tree:

```
           1              Level 0 → 1
          / \
         2   3            Level 1 → 3
          \   \
           5   4          Level 2 → 4
```

The levels are:

```
Level 0 → [1]
Level 1 → [2, 3]
Level 2 → [5, 4]
```

We select the last node from each level:

```
[1, 3, 4]
```

This is the central insight:

```
Level-Order BFS
       ↓
Process each level
       ↓
Take the last node
       ↓
Right-side view
```

## 3. Connection to LC 102

You just solved LC 102 — Binary Tree Level Order Traversal.

LC 102 returns every node in every level:

Python

Run

```
[
    [1],
    [2, 3],
    [5, 4]
]
```

LC 199 asks for only one node per level:

Python

Run

```
[1, 3, 4]
```

Therefore:

> LC 199 is a direct variation of LC 102.

You do not need a new traversal algorithm.

You only need to change what you record.

|
Problem

|

What we store

|
| --- | --- |
|

LC 102

|

Every value in each level

|
|

LC 199

|

The last value in each level

|

## 4. ELI10 Intuition

Imagine every level is a row of children standing from left to right.

```
Row 1:       1
Row 2:       2   3
Row 3:       5   4
```

If you stand on the right side, the child at the far right of each row is visible.

So you select:

```
Row 1 → 1
Row 2 → 3
Row 3 → 4
```

You do not need to inspect the tree from a physical right-side position.

You only need to find the last node processed at each BFS level.

## 5. Why BFS Is a Natural Choice

BFS processes nodes level by level.

That is exactly what the problem requires because we need:

```
One answer per depth
```

At every level:

1. Find the number of nodes.

2. Process all nodes in that level.

3. Record the final node's value.

The final node processed at that level is the rightmost node because children are inserted in this order:

Python

Run

```
left child
right child
```

and the queue preserves FIFO order.

## 6. The Core Insight: Detect the Last Node

Suppose the queue contains the current level:

```
Queue = [2, 3]
```

Then:

Python

Run

```
level_size = 2
```

During the loop:

Python

Run

```
for i in range(level_size):
```

The last node is processed when:

Python

Run

```
i == level_size - 1
```

Therefore:

Python

Run

```
if i == level_size - 1:
    result.append(node.val)
```

This means:

> Append only the value of the last node in each level.

This is more memory-efficient than constructing the entire level list.

## 7. Two Valid Strategies

### Strategy A — Store the Last Node During BFS

Python

Run

```
for i in range(level_size):

    node = queue.popleft()

    if i == level_size - 1:
        result.append(node.val)
```

This is the standard and efficient approach.

### Strategy B — Enqueue Right Child First

You can also enqueue the right child before the left child:

Python

Run

```
if node.right:
    queue.append(node.right)

if node.left:
    queue.append(node.left)
```

Then the first node of every level is the rightmost visible node.

You can append the first node of each level.

However, this changes the traversal order and can be less intuitive when explaining a standard left-to-right BFS.

Recommended approach: Use Strategy A for LC 199.

## 8. Why the Last Node Is the Rightmost Node

Assume we process each node's children in this order:

```
Left child → Right child
```

For any level:

* Parents are processed from left to right.

* Their children are appended in left-to-right order.

* Therefore, the next level is queued from left to right.

Consequently:

```
Last node of the level = rightmost node of the level
```

This is true even when the tree is incomplete.

### Example

```
           1
          / \
         2   3
          \
           5
```

Level 2 contains only:

```
[5]
```

So `5` is visible from the right side.

The rightmost visible node does not have to be a node with a right child.

It is simply the rightmost existing node at that depth.

## 9. Important Invariant

At the beginning of each outer-loop iteration:

> The queue contains exactly the nodes of the current tree level in left-to-right order.

During the inner loop:

* `level_size` remains fixed.

* Each iteration removes one node from the current level.

* Children are queued for the next level.

* When `i == level_size - 1`, we are processing the rightmost node of the current level.

Thus, appending that node gives the correct right-side view value.

## 10. Why a Visited Set Is Unnecessary

This is a valid binary tree:

* There are no cycles.

* Every node has only one parent.

* Every node is reached once.

Therefore, a `visited` set is not needed.

The queue itself controls the traversal.

## 11. Complexity Derivation

Let `N` be the number of nodes.

### Time complexity

Every node is:

* inserted into the queue once,

* removed once,

* processed once.

Therefore:

T(N)=O(N)T(N)=O(N)T(N)=O(N)

### Auxiliary space

The queue stores at most one level of nodes.

If `W` is the maximum width of the tree:

Auxiliary space=O(W)\text{Auxiliary space}=O(W)Auxiliary space=O(W)

In the worst case:

O(W)=O(N)O(W)=O(N)O(W)=O(N)

The output contains one value per level. If the tree height is `H`, output space is:

O(H)O(H)O(H)

Therefore:

* Time: `O(N)`

* Auxiliary space: `O(W)`

* Worst-case auxiliary space: `O(N)`

* Output space: `O(H)`

## 12. Edge Cases

|
Tree shape

|

Output behavior

|
| --- | --- |
|

Empty tree

|

`[]`

|
|

Single node

|

`[root.val]`

|
|

Only left children

|

Last node at each level

|
|

Only right children

|

Every node is visible

|
|

Missing right child

|

Use the rightmost existing node

|
|

Duplicate values

|

Values are recorded normally

|

### Example: Left-Skewed Tree

```
    1
   /
  2
 /
3
```

Output:

Python

Run

```
[1, 2, 3]
```

### Example: Right-Skewed Tree

```
1
 \
  2
   \
    3
```

Output:

Python

Run

```
[1, 2, 3]
```

# ⚙️ ALGORITHM — STEP-BY-STEP

```
Step 1 → If root is None, return [].

Step 2 → Create an empty result list.

Step 3 → Create a queue and insert the root.

Step 4 → While the queue is not empty:

         Step 4.1 → Store the current queue length as level_size.

         Step 4.2 → Process exactly level_size nodes.

         Step 4.3 → For each node:

                    a. Remove the node from the front.

                    b. If this is the last node of the current level,
                       append its value to result.

                    c. Add the left child to the queue if it exists.

                    d. Add the right child to the queue if it exists.

Step 5 → Return result.
```

The key condition is:

Python

Run

```
if i == level_size - 1:
```

It identifies the rightmost node of the current level.

# BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

Python

Run

```
from collections import deque


class Solution:

    def rightSideView(self, root):

        # An empty tree has no visible nodes.
        if root is None:
            return []

        result = []

        # Start BFS with the root.
        queue = deque([root])

        while queue:

            # Number of nodes in the current level.
            level_size = len(queue)

            for i in range(level_size):

                # Remove the next node from the queue.
                node = queue.popleft()

                # The final node processed at this level
                # is the rightmost node.
                if i == level_size - 1:
                    result.append(node.val)

                # Add children for the next level.
                if node.left is not None:
                    queue.append(node.left)

                if node.right is not None:
                    queue.append(node.right)

        return result
```

## Complexity

* Time: `O(N)`

* Auxiliary space: `O(W)`, where `W` is the maximum width.

* Worst-case auxiliary space: `O(N)`

* Output space: `O(H)`, where `H` is the tree height.

## Interview Justification

You can say:

> “This is a level-order BFS problem. I process the tree one level at a time using a queue. Since children are inserted from left to right, the last node processed in each level is the rightmost node. I append only that node's value. Each node is processed once, so the time complexity is O(N), and the queue requires O(W) auxiliary space.”

# BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

Python

Run

```
from collections import deque


class TreeNode:

    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


class Solution:

    def rightSideView(self, root):

        if root is None:
            return []

        result = []

        queue = deque([root])

        while queue:

            level_size = len(queue)

            for i in range(level_size):

                node = queue.popleft()

                # Record only the last node of each level.
                if i == level_size - 1:
                    result.append(node.val)

                if node.left is not None:
                    queue.append(node.left)

                if node.right is not None:
                    queue.append(node.right)

        return result


# Construct the binary tree:

#           1
#          / \
#         2   3
#          \   \
#           5   4

root = TreeNode(1)

root.left = TreeNode(2)
root.right = TreeNode(3)

root.left.right = TreeNode(5)
root.right.right = TreeNode(4)


# Create the solution object.
solution = Solution()

# Call the function.
result = solution.rightSideView(root)

# Print the result.
print("Right Side View:", result)
```

## Output

```
Right Side View: [1, 3, 4]
```

## Detailed Dry Run

Input tree:

```
           1
          / \
         2   3
          \   \
           5   4
```

### Initial State

```
Queue  = [1]
Result = []
```

### Level 0

```
level_size = 1
```

|
`i`

|

Removed node

|

Queue after removal

|

Action

|
| --- | --- | --- | --- |
|

0

|

`1`

|

`[]`

|

`i == level_size - 1`, append `1`

|

Add children:

```
Queue = [2, 3]
Result = [1]
```

### Level 1

```
level_size = 2
```

The current level is:

```
[2, 3]
```

#### Process node `2`

```
i = 0
level_size - 1 = 1
```

Since:

Python

Run

```
0 != 1
```

we do not append `2`.

Node `2` has a right child `5`.

```
Queue = [3, 5]
```

#### Process node `3`

```
i = 1
level_size - 1 = 1
```

Since:

Python

Run

```
1 == 1
```

we append `3`.

Node `3` has a right child `4`.

```
Queue = [5, 4]
Result = [1, 3]
```

|
`i`

|

Removed node

|

Queue after children added

|

Result

|
| --- | --- | --- | --- |
|

0

|

`2`

|

`[3, 5]`

|

`[1]`

|
|

1

|

`3`

|

`[5, 4]`

|

`[1, 3]`

|

### Level 2

```
level_size = 2
```

Current level:

```
[5, 4]
```

#### Process node `5`

```
i = 0
```

It is not the last node of the level.

No children are added.

#### Process node `4`

```
i = 1
```

It is the last node of the level.

Append `4`.

```
Result = [1, 3, 4]
Queue = []
```

## Final Output

Python

Run

```
[1, 3, 4]
```

# BLOCK 4 — INTERVIEW Q&A

## Question 1: Why is the last node of each level visible from the right?

Answer:

Because BFS processes each level from left to right.

Therefore, the last node processed at a level is the rightmost existing node at that depth.

We record that node's value.

## Question 2: Can we solve LC 199 using DFS?

Answer:

Yes.

With DFS, we visit the right child before the left child and track the current depth.

The first node encountered at each depth is the rightmost visible node.

Python

Run

```
def rightSideView(root):

    result = []

    def dfs(node, depth):

        if node is None:
            return

        if depth == len(result):
            result.append(node.val)

        dfs(node.right, depth + 1)
        dfs(node.left, depth + 1)

    dfs(root, 0)

    return result
```

### DFS complexity

* Time: `O(N)`

* Auxiliary space: `O(H)` for recursion.

* Output space: `O(H)`

The key DFS idea is:

```
Visit right first.
The first node at each depth is visible.
```

## Question 3: What if we enqueue the right child before the left child?

Answer:

Then the first node processed at each level becomes the rightmost node.

For example:

Python

Run

```
if node.right:
    queue.append(node.right)

if node.left:
    queue.append(node.left)
```

Then we could append the first node of each level.

However, the usual left-to-right BFS is easier to connect with LC 102, so recording the last node is often clearer.

## Question 4: Is the right-side view always the tree's right boundary?

Answer:

No.

The right boundary consists of nodes along the outer right edge of the tree.

The right-side view contains the rightmost node at every depth.

These concepts can differ.

Example:

```
       1
      /
     2
      \
       3
```

The right-side view is:

Python

Run

```
[1, 2, 3]
```

Even though the tree has no right child at the root.

## Question 5: How is LC 199 different from LC 102?

Answer:

Both use level-order BFS.

* LC 102 stores every node value at every level.

* LC 199 stores only the final node value of every level.

The traversal framework is identical; the aggregation logic changes.

## Question 6: How would you return the left-side view instead?

Answer:

With normal left-to-right BFS, record the first node of each level:

Python

Run

```
if i == 0:
    result.append(node.val)
```

The rest of the BFS remains unchanged.

# PATTERN EXTRACTION

## Master Template — Rightmost Node Per Level

Python

Run

```
from collections import deque


def right_side_view(root):

    if root is None:
        return []

    result = []
    queue = deque([root])

    while queue:

        level_size = len(queue)

        for i in range(level_size):

            node = queue.popleft()

            if i == level_size - 1:
                result.append(node.val)

            if node.left:
                queue.append(node.left)

            if node.right:
                queue.append(node.right)

    return result
```

## Variations of the Same Pattern

|
Required output

|

What to record

|
| --- | --- |
|

Full level-order traversal

|

Every node

|
|

Left-side view

|

First node of each level

|
|

Right-side view

|

Last node of each level

|
|

Level maximum

|

Maximum value per level

|
|

Level minimum

|

Minimum value per level

|
|

Level sum

|

Sum of values per level

|
|

Level average

|

Sum divided by level size

|
|

Zigzag traversal

|

Reverse alternate levels

|

The key insight:

> The BFS traversal does not change. Only the information extracted from each level changes.

# SENIOR PATTERN RECOGNITION

When you see:

* “Visible from the right side”

* “Last node at each depth”

* “Rightmost node of every level”

* “One representative node per level”

* “View of the tree from one side”

Think:

```
BINARY TREE
    ↓
LEVEL-ORDER BFS
    ↓
CAPTURE level_size
    ↓
PROCESS ONE LEVEL
    ↓
SELECT LAST NODE
    ↓
RIGHT-SIDE VIEW
```

## Connection Across Your Queue Roadmap

```
LC 102
Tree → BFS → All nodes per level

LC 199
Tree → BFS → One selected node per level

LC 752
State → BFS → Minimum transformations

LC 127
Word states → BFS → Shortest transformation
```

The queue remains the central engine:

Python

Run

```
node = queue.popleft()
```

What changes is the state or result extracted from each BFS layer.

# PROGRESS UPDATE

```
LEVEL 4 — LEVEL-ORDER BFS

├── ✅ LC 102 — Binary Tree Level Order Traversal
└── ✅ LC 199 — Binary Tree Right Side View
```

# One-Line Takeaway

> LC 199 = LC 102's level-order BFS + record only the last node of every level.


# LEVEL 5

## LEVEL 5 — IMPLICIT STATE BFS
└── LC 752


# 🔵 LEVEL 5 — IMPLICIT STATE BFS

## LC 752 — Open the Lock

Difficulty: Medium Pattern: BFS + State-Space Search + Visited Set Priority: 🔥🔥🔥🔥🔥

This problem is a major transition from ordinary tree/grid BFS to searching through possible configurations.

Instead of moving between physical nodes in a graph, we move between states of a lock. Each valid one-step rotation creates an edge between two states. Our goal is to find the minimum number of moves from `"0000"` to `"0000"`'s target state while avoiding forbidden states.


# BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Statement

You have a lock with four rotating wheels.

Each wheel contains digits from `0` to `9`.

The lock initially shows:

```
0000
```

You can rotate exactly one wheel by one position per move:

* Increase a digit by `1`.

* Decrease a digit by `1`.

* Digits wrap around:

  * `9 → 0`

  * `0 → 9`

Some combinations are deadends. You cannot enter those combinations.

Given a target combination, return the minimum number of moves needed to reach it.

If the target cannot be reached, return `-1`.

## 2. Example

```
deadends = ["0201", "0101", "0102", "1212", "2002"]
target = "0202"
```

Output:

```
6
```

One possible shortest path is:

```
0000
  ↓
1000
  ↓
1100
  ↓
1200
  ↓
1201
  ↓
1202
  ↓
0202
```

Each transition changes exactly one wheel by one step.

## 3. Hidden Translation — What Is This Problem Really Asking?

The lock looks like a physical object, but algorithmically it is a state-space graph.

|
Lock concept

|

Graph concept

|
| --- | --- |
|

A four-digit combination

|

A graph node/state

|
|

Rotate one wheel once

|

An edge/transition

|
|

Starting combination `"0000"`

|

Source state

|
|

Target combination

|

Destination state

|
|

Deadend

|

Forbidden state

|
|

Number of wheel rotations

|

Path length

|
|

Minimum rotations

|

Shortest path

|

The real problem is:

```
STATE
  ↓
GENERATE VALID NEXT STATES
  ↓
BFS
  ↓
MINIMUM NUMBER OF MOVES
```

## 4. Why This Is Called “Implicit State BFS”

In previous problems, the graph was explicitly provided.

### LC 1971

You received edges:

Python

Run

```
edges = [[0, 1], [1, 2]]
```

You built an adjacency list.

### LC 752

No edge list is provided.

Instead, you must generate neighboring states yourself.

For example:

```
Current state: 0000
```

Possible next states:

```
1000
9000
0100
0900
0010
0090
0001
0009
```

There are exactly:

4×2=84 \times 2 = 84×2=8

possible one-move neighbors for every state.

Therefore, the graph is implicit.

> The edges exist conceptually, but we generate them when needed rather than storing the entire graph.

## 5. ELI10 Intuition

Imagine a four-wheel combination lock.

You are standing at:

```
0000
```

You can make only one tiny change at a time.

From `0000`, you can turn:

* The first wheel forward → `1000`

* The first wheel backward → `9000`

* The second wheel forward → `0100`

* The second wheel backward → `0900`

* And so on.

Imagine every combination is a room.

A move takes you from one room to a neighboring room.

BFS explores rooms in layers:

```
Move 0 → 0000

Move 1 → All combinations one move away

Move 2 → All combinations two moves away

Move 3 → All combinations three moves away
```

The first time BFS reaches the target, it has found the minimum number of moves.

## 6. Why BFS Is the Correct Algorithm

Every valid move costs exactly one move.

Therefore, this is an unweighted shortest-path problem.

BFS is ideal for unweighted graphs because it explores states in increasing distance from the starting state.

```
Distance 0
    ↓
Distance 1
    ↓
Distance 2
    ↓
Distance 3
```

If the target is first discovered at distance `d`, there cannot be a shorter path to it.

### Why DFS Is Not Suitable

DFS may follow a very long sequence of moves before discovering the target.

It does not guarantee that the first discovered path is the shortest.

You could use DFS with additional distance tracking, but that is unnecessary and less natural than BFS.

## 7. State Representation

Each state is a four-character string:

Python

Run

```
"0000"
"1234"
"9087"
```

A state has exactly four positions:

```
Index:  0 1 2 3
State:  1 2 3 4
```

For each position, we try:

```
digit + 1
digit - 1
```

The wraparound rules are:

```
9 + 1 → 0
0 - 1 → 9
```

The clean mathematical formula is:

next digit=(digit+change) mod 10\text{next digit}=(\text{digit}+\text{change}) \bmod 10next digit=(digit+change)mod10

where:

Python

Run

```
change = +1 or -1
```

In Python:

Python

Run

```
new_digit = (int(state[i]) + change) % 10
```

## 8. Generating the Eight Neighbors

Suppose:

Python

Run

```
state = "0000"
```

At each of the four positions, we try `+1` and `-1`.

### Position 0

```
1000
9000
```

### Position 1

```
0100
0900
```

### Position 2

```
0010
0090
```

### Position 3

```
0001
0009
```

Total:

```
8 neighbors
```

### Important Implementation Detail

Strings are immutable in Python.

Therefore, to modify one character:

1. Convert the string to a list.

2. Change one digit.

3. Convert it back to a string.

Example:

Python

Run

```
chars = list("0000")
chars[0] = "1"
new_state = "".join(chars)
```

## 9. Why We Need a Visited Set

The state graph contains cycles.

For example:

```
0000 → 1000 → 0000
```

Without a visited set, BFS could repeatedly revisit the same combinations.

That would cause:

* Duplicate work.

* Potentially unbounded processing.

* Unnecessary queue growth.

Therefore, we maintain:

Python

Run

```
visited = {"0000"}
```

Whenever we discover a new valid state:

1. Mark it visited immediately.

2. Add it to the queue.

This prevents the same state from being enqueued multiple times.

## 10. Why We Mark a State When Enqueuing

Use:

Python

Run

```
visited.add(next_state)
queue.append(next_state)
```

at the moment the state is discovered.

Do not wait until it is removed from the queue.

Why?

Suppose two different states can reach the same next state.

If we mark it only when dequeued, both parent states may enqueue it.

Marking at discovery guarantees:

> Every state enters the queue at most once.

This is the same principle you used in LC 1971.

## 11. Deadends Must Be Treated as Blocked States

Deadends are forbidden combinations.

We should never:

* Start from a deadend.

* Enter a deadend.

* Add a deadend to the queue.

Convert the list into a set for efficient lookup:

Python

Run

```
dead = set(deadends)
```

Then reject a generated state if:

Python

Run

```
next_state in dead
```

### Important Edge Case

If the starting state is forbidden:

Python

Run

```
deadends = ["0000"]
```

then the lock cannot be opened.

Return:

Python

Run

```
-1
```

This check must happen before starting BFS.

## 12. The Most Important Invariant

At any point during BFS:

> Every state in the queue is reachable from `"0000"` through valid, non-deadend transitions, and its stored distance is the minimum number of moves required to reach it.

Additionally:

* Every visited state has already been discovered.

* No deadend is processed.

* No state is enqueued more than once.

* BFS processes states in nondecreasing distance order.

This invariant guarantees that the first time we reach the target, the answer is optimal.

## 13. Two Ways to Track Distance

### Method A — Store `(state, distance)` in the Queue

Python

Run

```
queue = deque([("0000", 0)])
```

Each queue item contains:

```
(state, number_of_moves)
```

This is straightforward and easy to explain.

### Method B — Process BFS by Levels

Use:

Python

Run

```
steps = 0
```

Then process one queue layer at a time.

Both methods are valid.

For this problem, storing `(state, distance)` is simple and explicit.

## 14. Complexity Derivation

There are four wheels, and each wheel has ten possible digits.

Therefore, the maximum number of states is:

104=1000010^4=10000104=10000

Each state has exactly eight possible one-move transitions.

The number of neighbors per state is constant:

4×2=84 \times 2 = 84×2=8

Therefore:

T(V,E)=O(V+E)T(V,E)=O(V+E)T(V,E)=O(V+E)

Since:

E=8VE=8VE=8V

we get:

T(V)=O(V)T(V)=O(V)T(V)=O(V)

For a four-wheel lock:

* Time: `O(10⁴)` in the worst case.

* Auxiliary space: `O(10⁴)` for the queue and visited set.

* Deadend set: `O(D)`, where `D` is the number of deadends.

More generally, for `k` wheels and base `b`:

V=bkV=b^kV=bk

and each state has `2k` neighbors.

Thus:

T=O(kbk)T=O(kb^k)T=O(kbk)

For LC 752, `k = 4` and `b = 10`, so the search space is bounded and manageable.

# ⚙️ ALGORITHM — STEP-BY-STEP

```
Step 1 → Convert the deadends list into a set for O(1)-average lookup.

Step 2 → If "0000" is a deadend, return -1.

Step 3 → If the target is "0000", return 0.

Step 4 → Create a queue containing:
         ("0000", 0)

         The second value represents the number of moves.

Step 5 → Create a visited set containing "0000".

Step 6 → While the queue is not empty:

         Step 6.1 → Remove one state and its distance.

         Step 6.2 → For each of the four wheel positions:

                    a. Try rotating the wheel forward by one.

                    b. Try rotating the wheel backward by one.

         Step 6.3 → Generate the resulting state using modulo 10.

         Step 6.4 → If the new state is a deadend
                    or has already been visited,
                    skip it.

         Step 6.5 → If the new state equals the target,
                    return distance + 1.

         Step 6.6 → Mark the new state as visited.

         Step 6.7 → Add the new state and distance + 1
                    to the queue.

Step 7 → If BFS finishes without finding the target,
        return -1.
```

# BLOCK 2 — EFFICIENT CODE

## Best Clean Python 3 Solution

Python

Run

```
from collections import deque


class Solution:

    def openLock(self, deadends, target):

        dead = set(deadends)

        # The starting state is forbidden.
        if "0000" in dead:
            return -1

        # We are already at the target.
        if target == "0000":
            return 0

        queue = deque([("0000", 0)])
        visited = {"0000"}

        while queue:

            state, moves = queue.popleft()

            # Try changing each of the four wheels.
            for i in range(4):

                for change in (-1, 1):

                    # Convert the state into a mutable list.
                    chars = list(state)

                    # Rotate one wheel with wraparound.
                    new_digit = (int(chars[i]) + change) % 10
                    chars[i] = str(new_digit)

                    # Build the new state.
                    next_state = "".join(chars)

                    # Ignore forbidden or previously visited states.
                    if next_state in dead or next_state in visited:
                        continue

                    # We reached the target in one additional move.
                    if next_state == target:
                        return moves + 1

                    # Mark the state when it is discovered.
                    visited.add(next_state)

                    # Add it to the BFS queue.
                    queue.append((next_state, moves + 1))

        # The target cannot be reached.
        return -1
```

## Complexity

Let `V` be the number of possible lock combinations.

For this problem:

V=104V=10^4V=104

Each state generates eight neighbors.

* Time: `O(10⁴)` for the fixed four-wheel problem.

* Space: `O(10⁴ + D)`, where `D` is the number of deadends.

* More generally: Time `O(k × 10ᵏ)`, Space `O(10ᵏ + D)`.

Because each state is visited at most once and each state has only eight neighbors, the search remains bounded.

## Interview Justification

You can say:

> “I model each four-digit combination as a node in an implicit graph. Rotating one wheel forward or backward creates one of eight possible neighboring states. Since every move has equal cost, I use BFS to find the shortest path from `0000` to the target. I use a deadend set to reject forbidden states and a visited set to avoid cycles. There are at most `10⁴` states, and each state has eight neighbors, so the worst-case time and space are bounded by `O(10⁴)` for this fixed-size problem.”

# BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

Python

Run

```
from collections import deque


class Solution:

    def openLock(self, deadends, target):

        dead = set(deadends)

        if "0000" in dead:
            return -1

        if target == "0000":
            return 0

        queue = deque([("0000", 0)])
        visited = {"0000"}

        while queue:

            state, moves = queue.popleft()

            for i in range(4):

                for change in (-1, 1):

                    chars = list(state)

                    new_digit = (int(chars[i]) + change) % 10
                    chars[i] = str(new_digit)

                    next_state = "".join(chars)

                    if next_state in dead or next_state in visited:
                        continue

                    if next_state == target:
                        return moves + 1

                    visited.add(next_state)
                    queue.append((next_state, moves + 1))

        return -1


# Example input.
deadends = [
    "0201",
    "0101",
    "0102",
    "1212",
    "2002"
]

target = "0202"

# Create the solution object.
solution = Solution()

# Call the function.
result = solution.openLock(deadends, target)

# Print the answer.
print("Minimum moves:", result)
```

## Output

```
Minimum moves: 6
```

## Dry Run — Important BFS States

Input:

Python

Run

```
deadends = ["0201", "0101", "0102", "1212", "2002"]
target = "0202"
```

Starting state:

```
0000
```

Target:

```
0202
```

One shortest route is:

```
0000
  ↓
1000
  ↓
1100
  ↓
1200
  ↓
1201
  ↓
1202
  ↓
0202
```

### Step-by-Step Table

|
Move count

|

State

|

Action

|
| --- | --- | --- |
|

0

|

`0000`

|

Starting state

|
|

1

|

`1000`

|

Increase first wheel

|
|

2

|

`1100`

|

Increase second wheel

|
|

3

|

`1200`

|

Increase second wheel

|
|

4

|

`1201`

|

Increase fourth wheel

|
|

5

|

`1202`

|

Increase fourth wheel

|
|

6

|

`0202`

|

Increase first wheel with wraparound

|

At move `6`, the target is reached.

Therefore:

```
Answer = 6
```

## Understanding Wraparound

Suppose the current state is:

```
0000
```

If we decrease the first wheel:

Python

Run

```
(0 - 1) % 10
```

The result is:

Python

Run

```
9
```

So:

```
0000 → 9000
```

Similarly:

```
9999 → 0999
```

when the first wheel is increased.

Modulo arithmetic handles both boundaries cleanly.

## Neighbor Generation Example

For:

```
state = "0000"
```

the generated neighbors are:

```
1000
9000
0100
0900
0010
0090
0001
0009
```

The BFS does not need to construct all `10,000` states beforehand.

It creates neighbors only when a state is processed.

That is why the graph is called implicit.

# BLOCK 4 — INTERVIEW Q&A

## Question 1: Why is BFS guaranteed to find the minimum number of moves?

Answer:

Every wheel rotation has equal cost: one move.

BFS explores states in increasing order of distance from the starting state.

Therefore, when the target is first reached, it has been reached using the smallest possible number of moves.

## Question 2: Why don't we build the entire graph beforehand?

Answer:

The graph has up to `10,000` states, and each state has eight neighbors.

We could build it, but that is unnecessary.

The neighboring states can be generated directly from the current combination.

This saves preprocessing and is the standard approach for implicit graphs.

## Question 3: Why do we need both `dead` and `visited`?

Answer:

They represent different concepts:

* `dead` contains states that are forbidden by the problem.

* `visited` contains states that our BFS has already discovered.

A state can be valid but already visited.

A state can also be forbidden before we ever discover it.

Therefore, both sets are useful.

## Question 4: Why do we mark states as visited when adding them to the queue?

Answer:

Multiple states may generate the same neighbor.

If we wait until dequeuing, the same state may be inserted several times.

Marking it immediately when discovered guarantees that every state enters the queue at most once.

## Question 5: Why do we use modulo `10`?

Answer:

Each wheel contains digits from `0` through `9`.

Modulo `10` implements circular movement:

```
9 + 1 → 0
0 - 1 → 9
```

The formula is:

Python

Run

```
new_digit = (digit + change) % 10
```

## Question 6: Could we use DFS instead?

Answer:

DFS can determine whether a target is reachable, but it does not naturally guarantee the shortest path.

We could use more complex bookkeeping, but BFS is the correct standard technique because this is an unweighted shortest-path problem.

## Question 7: What if the target itself is a deadend?

Answer:

The target cannot be reached because deadends are forbidden states.

The BFS will never enter that state.

If no valid route exists, the algorithm returns:

Python

Run

```
-1
```

# PATTERN EXTRACTION

## Master Template — Implicit State BFS

Python

Run

```
from collections import deque


def shortest_state_path(start, target):

    queue = deque([(start, 0)])
    visited = {start}

    while queue:

        state, distance = queue.popleft()

        if state == target:
            return distance

        for next_state in generate_neighbors(state):

            if next_state in visited:
                continue

            if not is_valid(next_state):
                continue

            visited.add(next_state)
            queue.append((next_state, distance + 1))

    return -1
```

The most important function is:

Python

Run

```
generate_neighbors(state)
```

In LC 752, this means:

```
Change each wheel by +1 and -1.
```

## General State-Space BFS Structure

```
CURRENT STATE
      ↓
GENERATE POSSIBLE TRANSITIONS
      ↓
REMOVE INVALID STATES
      ↓
REMOVE VISITED STATES
      ↓
MARK NEW STATE VISITED
      ↓
ADD TO QUEUE
      ↓
REPEAT
```

# SENIOR PATTERN RECOGNITION

When you see:

* “Minimum moves”

* “Minimum transformations”

* “Change one component at a time”

* “Reach a target configuration”

* “Each operation has equal cost”

* “Generate all possible next configurations”

* “Avoid forbidden configurations”

Think:

```
CONFIGURATION = NODE
OPERATION = EDGE
      ↓
GENERATE NEIGHBORS
      ↓
BFS
      ↓
SHORTEST STATE TRANSFORMATION
```

## Examples of Similar Problems

|
Problem type

|

State

|

Transition

|
| --- | --- | --- |
|

Lock combinations

|

Four-digit string

|

Rotate one wheel

|
|

Word Ladder

|

Current word

|

Change one character

|
|

Genetic Mutation

|

DNA string

|

Change one gene

|
|

Sliding puzzle

|

Board configuration

|

Move a tile

|
|

Robot navigation

|

Position and orientation

|

Valid movement

|
|

Chess-like state search

|

Board configuration

|

Legal move

|

The key question is always:

> “What is one state, and what operations can produce a neighboring state?”

# CONNECTION TO YOUR PREVIOUS PROBLEMS

```
LC 1971
Explicit graph → BFS → Reachability

LC 1091
Grid as implicit graph → BFS → Shortest path

LC 994
Grid + multiple sources → BFS → Time

LC 102
Tree → BFS → Level grouping

LC 199
Tree → BFS → One node per level

LC 752
Configuration space → BFS → Minimum transformations
```

The queue operation is still the same:

Python

Run

```
state, distance = queue.popleft()
```

What changes is how we generate neighbors.

# COMMON INTERVIEW TRAPS

1. Forgetting the initial deadend check

   Python

   Run

   ```
   if "0000" in dead:
       return -1
   ```

2. Not handling the target `"0000"`

   The answer is `0` if the starting state is valid.

3. Forgetting wraparound

   ```
   0 → 9
   9 → 0
   ```

4. Changing more than one wheel per move

   Each transition must change exactly one digit.

5. Not using a visited set

   The state graph contains cycles.

6. Marking visited too late

   Mark states when enqueuing them.

7. Using DFS for a shortest-path problem

   BFS is the natural solution when every move has equal cost.

8. Treating deadends as merely visited

   Deadends are forbidden, not just previously explored.

# PROGRESS UPDATE

```
LEVEL 5 — IMPLICIT STATE BFS

└── ✅ LC 752 — Open the Lock
```

# One-Line Takeaway

> LC 752 = BFS on an implicit graph where each lock combination is a state and each one-wheel rotation is an edge.



# LEVEL 6 — STATE TRANSFORMATION BFS
├── LC 127
└── LC 433

# 🔥 LEVEL 6 — STATE TRANSFORMATION BFS

```text
LEVEL 6 — STATE TRANSFORMATION BFS

├── LC 127 — Word Ladder
└── LC 433 — Minimum Genetic Mutation
```

We are now extending the exact idea from **LC 752 — Open the Lock**.

```text
LC 752
State = "0000"
Transition = rotate one wheel

        ↓

LC 127
State = "hit"
Transition = change one character

        ↓

LC 433
State = "AACCGGTT"
Transition = change one gene
```

The algorithmic engine is the same:

```text
STATE
  ↓
GENERATE VALID NEXT STATES
  ↓
VISITED
  ↓
BFS
  ↓
SHORTEST TRANSFORMATION
```

---

# 🔵 LC 127 — Word Ladder

**Difficulty:** Hard
**Pattern:** BFS + Implicit Graph + State Transformation + Hash Set
**Priority:** ⭐⭐⭐⭐⭐⭐

---

# BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given:

```text
beginWord = "hit"
endWord   = "cog"
```

and a dictionary:

```text
["hot","dot","dog","lot","log","cog"]
```

You can change **exactly one character** at a time.

A valid transformation is:

```text
hit
 ↓
hot
 ↓
dot
 ↓
dog
 ↓
cog
```

Every intermediate word must exist in the dictionary.

The question asks:

> What is the minimum number of words in the transformation sequence?

Therefore:

```text
hit → hot → dot → dog → cog
```

has length:

```text
5
```

---

# 2. What Is the Real Graph?

This is **not explicitly given as a graph**.

Instead:

```text
Word = Node
One-character transformation = Edge
```

For example:

```text
hot
```

can connect to words such as:

```text
dot
lot
```

because they differ by exactly one character.

So conceptually:

```text
             dot
              |
hit —— hot —— dog —— cog
              |
             lot
```

The graph is hidden inside the word dictionary.

That's why this is:

> **Implicit Graph BFS.**

---

# 3. Why BFS?

The problem asks for the **shortest transformation sequence**.

Every transformation costs exactly:

```text
1 step
```

Therefore this is an **unweighted shortest-path problem**.

BFS explores:

```text
Distance 0
    ↓
Distance 1
    ↓
Distance 2
    ↓
Distance 3
```

Therefore the first time we reach `endWord`, we have found the shortest transformation.

---

# 4. ELI10 Intuition

Imagine a word-changing game.

You start with:

```text
HIT
```

You are allowed to change only one letter.

```text
HIT → HOT
```

Then:

```text
HOT → DOT
```

Then:

```text
DOT → DOG
```

Then:

```text
DOG → COG
```

Imagine every valid word is a room.

```text
HIT
 ↓
HOT
 ↓
DOT
 ↓
DOG
 ↓
COG
```

BFS asks:

> “Which words can I reach in 1 move? Then which words in 2 moves? Then 3?”

That guarantees the minimum number of transformations.

---

# 5. The Critical Part — Generating Neighbors

Suppose:

```text
word = "hot"
```

We need to generate every word that differs by exactly one character.

For position `0`:

```text
hot
aot
bot
cot
...
zot
```

For position `1`:

```text
hat
hbt
hct
...
hzt
```

For position `2`:

```text
hoa
hob
hoc
...
hoz
```

But most of these aren't necessarily valid words.

So we check:

```python
if candidate in word_set:
```

Only dictionary words are allowed.

---

# 6. Why a Hash Set Is Essential

Suppose the dictionary contains:

```python
wordList = [
    "hot",
    "dot",
    "dog",
    "lot",
    "log",
    "cog"
]
```

Convert it:

```python
word_set = set(wordList)
```

Now:

```python
candidate in word_set
```

takes **O(1) average time**.

Without a set, every generated word could require scanning the entire dictionary.

That would dramatically increase the running time.

---

# 7. The Search Space

Suppose each word has length `L`.

For every word:

```text
L positions
```

At every position:

```text
26 possible letters
```

We can avoid replacing the character with itself, so approximately:

```text
L × 25
```

candidate transformations per word.

For example:

```text
"hot"
```

has:

```text
3 × 25 = 75
```

possible one-character changes.

Only candidates present in the dictionary become actual graph neighbors.

---

# 8. The Deep Connection to LC 752

Compare them:

| LC 752        | LC 127                    |
| ------------- | ------------------------- |
| `"0000"`      | `"hit"`                   |
| Lock state    | Word state                |
| Rotate wheel  | Change character          |
| 8 neighbors   | Up to `L × 25` candidates |
| Deadends      | Dictionary restriction    |
| BFS           | BFS                       |
| Minimum moves | Minimum transformations   |

The abstraction is:

```text
Current State
      ↓
Generate all legal transitions
      ↓
BFS
```

This is exactly the **state-space BFS** pattern.

---

# 9. Important Definition: Transformation Sequence

For LC 127, two consecutive words must:

1. Have the same length.
2. Differ by exactly one character.
3. The transformed word must belong to the allowed dictionary.

For example:

```text
hot → dot
```

Valid.

```text
hot → dog
```

Invalid because more than one character differs.

---

# 10. Important Edge Case — endWord Missing

If:

```python
endWord not in wordList
```

then reaching it is impossible.

Therefore:

```python
return 0
```

This is an important early check.

---

# 11. Another Important Edge Case

If:

```text
beginWord == endWord
```

then the transformation sequence already starts at the target.

Depending on the LC 127 formulation, this case is generally not the central intended case because `endWord` is required to be different from `beginWord`, but robust reasoning should recognize that no transformation is needed.

---

# 12. Visited Handling

This is extremely important.

Once a word has been discovered:

```python
visited.add(next_word)
```

we should not enqueue it again.

Why?

Because transformation graphs contain cycles.

For example:

```text
hit → hot
hot → hit
```

Without visited tracking:

```text
hit → hot → hit → hot → hit ...
```

BFS would waste work indefinitely.

---

# 13. Better Optimization — Remove from the Set

For LC 127, we can use the dictionary set itself as the unvisited set.

When we discover a word:

```python
word_set.remove(candidate)
```

That means:

```text
remaining in set = not yet visited
```

This avoids maintaining two separate structures.

However, conceptually it is often clearer to explain this as:

```text
word_set = valid + unvisited candidates
```

and remove words once discovered.

---

# 14. Bidirectional BFS — Senior-Level Connection

LC 127 has a particularly important optimization:

```text
BFS from beginWord
+
BFS from endWord
```

Instead of exploring the entire search space from one side, search simultaneously from both sides.

Conceptually:

```text
BEGIN
 ↓
 ↓
 ↓
 ←
 ←
END
```

When the two frontiers meet, the shortest path has been found.

This can dramatically reduce the explored search space.

However, for mastering the foundational **state transformation BFS**, first understand ordinary BFS perfectly.

---

# 15. Why Bidirectional BFS Is Useful Here

Suppose the branching factor is approximately `B` and shortest path length is `D`.

Ordinary BFS roughly explores:

```text
B^D
```

states in the broad conceptual model.

Bidirectional BFS explores approximately:

```text
2 × B^(D/2)
```

which can be dramatically smaller.

This is why LC 127 is one of the classic problems where interviewers may ask:

> “Can you optimize your BFS?”

---

# 16. Invariant

At any point:

> Every word in the BFS queue has been reached through a valid transformation sequence, and BFS reaches words in nondecreasing transformation distance.

Additionally:

* Every discovered word is processed at most once.
* Every generated candidate differs by exactly one character.
* Only dictionary words are allowed.
* The first time `endWord` is reached gives the minimum sequence length.

---

# 17. Complexity Derivation

Let:

* `N` = number of words.
* `L` = length of each word.

For every word, we try:

```text
L positions × 26 letters
```

Therefore:

$$
O(N \times L \times 26)
$$

Since `26` is constant:

$$
O(NL)
$$

Hash set lookup is `O(1)` average.

Therefore the standard BFS solution is:

### Time

```text
O(N × L × 26)
≈ O(NL)
```

### Space

```text
O(N)
```

for the dictionary, queue, and visited/unvisited tracking.

---

# ⚙️ ALGORITHM — STEP-BY-STEP

```text id="f2j7r9"
Step 1 → If endWord is not present in wordList, return 0.

Step 2 → Convert wordList into a set for fast lookup.

Step 3 → Create a queue containing:
         (beginWord, transformation_length)

Step 4 → Remove beginWord from the available-word set
         so it cannot be visited again.

Step 5 → While the queue is not empty:

         Step 5.1 → Remove the current word and its distance.

         Step 5.2 → For every character position:

                    a. Try every letter from 'a' to 'z'.

                    b. Create the candidate word.

                    c. If the candidate exists in the
                       available-word set:

                           i. If it is endWord,
                              return distance + 1.

                          ii. Remove it from the set.

                         iii. Add it to the queue.

Step 6 → If BFS finishes without reaching endWord,
        return 0.
```

---

# BLOCK 2 — EFFICIENT CODE

```python id="wq0p2u"
from collections import deque

class Solution:

    def ladderLength(self, beginWord, endWord, wordList):

        # If target word is unavailable,
        # transformation is impossible.
        if endWord not in wordList:
            return 0

        # Set gives O(1) average lookup.
        words = set(wordList)

        # beginWord is already discovered.
        words.discard(beginWord)

        # Queue stores:
        # (current_word, transformation_length)
        queue = deque([(beginWord, 1)])

        while queue:

            word, length = queue.popleft()

            # Try changing every character.
            for i in range(len(word)):

                for char_code in range(ord('a'), ord('z') + 1):

                    char = chr(char_code)

                    # Skip replacing a character with itself.
                    if char == word[i]:
                        continue

                    # Build candidate word.
                    candidate = (
                        word[:i] +
                        char +
                        word[i + 1:]
                    )

                    # Candidate must be an unused dictionary word.
                    if candidate not in words:
                        continue

                    # Target reached.
                    if candidate == endWord:
                        return length + 1

                    # Mark as discovered immediately.
                    words.remove(candidate)

                    # Add next state to BFS.
                    queue.append((candidate, length + 1))

        return 0
```

---

## Complexity

Let:

```text
N = number of words
L = word length
```

For each of at most `N` words:

```text
L positions × 26 letters
```

Therefore:

```text
Time = O(N × L × 26)
     = O(NL)
```

Space:

```text
O(N)
```

for the word set and BFS queue.

---

# BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

```python id="1b7y6f"
from collections import deque


class Solution:

    def ladderLength(self, beginWord, endWord, wordList):

        if endWord not in wordList:
            return 0

        words = set(wordList)

        words.discard(beginWord)

        queue = deque([
            (beginWord, 1)
        ])

        while queue:

            word, length = queue.popleft()

            for i in range(len(word)):

                for char_code in range(
                    ord('a'),
                    ord('z') + 1
                ):

                    char = chr(char_code)

                    if char == word[i]:
                        continue

                    candidate = (
                        word[:i] +
                        char +
                        word[i + 1:]
                    )

                    if candidate not in words:
                        continue

                    if candidate == endWord:
                        return length + 1

                    words.remove(candidate)

                    queue.append(
                        (candidate, length + 1)
                    )

        return 0


# Input
beginWord = "hit"

endWord = "cog"

wordList = [
    "hot",
    "dot",
    "dog",
    "lot",
    "log",
    "cog"
]

# Create solution object
solution = Solution()

# Call function
result = solution.ladderLength(
    beginWord,
    endWord,
    wordList
)

print("Shortest Transformation Length:", result)
```

## Output

```text id="1x5z0m"
Shortest Transformation Length: 5
```

---

# Detailed Dry Run

Initial state:

```text
beginWord = "hit"
target    = "cog"
```

Available words:

```text
{hot, dot, dog, lot, log, cog}
```

---

## Distance 1

Queue:

```text
[("hit", 1)]
```

Process:

```text
hit
```

Generate valid neighbor:

```text
hot
```

Queue becomes:

```text
[("hot", 2)]
```

---

## Distance 2

Process:

```text
hot
```

Valid transformations include:

```text
dot
lot
```

Queue:

```text
[
    ("dot", 3),
    ("lot", 3)
]
```

---

## Distance 3

Process:

```text
dot
```

Generate:

```text
dog
```

Queue:

```text
[
    ("lot", 3),
    ("dog", 4)
]
```

Then `lot` can generate:

```text
log
```

Queue eventually contains:

```text
[
    ("dog", 4),
    ("log", 4)
]
```

---

## Distance 4

Process:

```text
dog
```

Generate:

```text
cog
```

Target found.

Therefore:

```text
length = 4 + 1
       = 5
```

Final transformation:

```text
hit
 ↓
hot
 ↓
dot
 ↓
dog
 ↓
cog
```

Answer:

```text
5
```

---

# BLOCK 4 — INTERVIEW Q&A

## Q1. Why is this an implicit graph?

**Answer:**

The problem doesn't provide edges explicitly.

Instead:

```text
Word = node
One-character difference = edge
```

We generate neighboring words dynamically.

---

## Q2. Why BFS instead of DFS?

**Answer:**

The objective is the minimum number of transformations. Every transformation costs one step, making this an unweighted shortest-path problem. BFS guarantees the first discovered target has minimum distance.

---

## Q3. Why use a set?

**Answer:**

We repeatedly ask:

```python
candidate in words
```

A hash set provides average `O(1)` membership checking.

---

## Q4. Why remove a word immediately after discovering it?

**Answer:**

Because BFS may reach the same word through multiple parents. Removing it immediately guarantees that it is enqueued only once.

---

## Q5. Why try 26 letters?

**Answer:**

Each position can contain any lowercase English letter. For every character position, we test all possible replacements and retain only dictionary words.

---

## Q6. How can LC 127 be optimized?

**Answer:**

Use **bidirectional BFS**, searching simultaneously from `beginWord` and `endWord`. The two search frontiers can meet much sooner than a one-sided BFS in large search spaces.

---

# PATTERN EXTRACTION

## State Transformation BFS Template

```python
from collections import deque

queue = deque([(start_state, 0)])
visited = {start_state}

while queue:

    state, distance = queue.popleft()

    if state == target:
        return distance

    for next_state in generate_neighbors(state):

        if next_state in visited:
            continue

        if not is_valid(next_state):
            continue

        visited.add(next_state)

        queue.append(
            (next_state, distance + 1)
        )

return -1
```

LC 752:

```text
generate_neighbors(lock)
```

means:

```text
rotate one wheel +1 / -1
```

LC 127:

```text
generate_neighbors(word)
```

means:

```text
change one character
```

That is the abstraction you need to master.

---

# 🔥 LC 433 — Minimum Genetic Mutation

**Difficulty:** Medium
**Pattern:** BFS + State Transformation + Hash Set
**Priority:** 🔥🔥🔥🔥

LC 433 is essentially a **smaller and cleaner version of LC 127**.

---

# BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You have a DNA string such as:

```text
"AACCGGTT"
```

Each character can be one of:

```text
A
C
G
T
```

You can mutate exactly **one gene** at a time.

For example:

```text
AACCGGTT
    ↓
AACCGCTA
```

provided the resulting mutation exists in the bank.

The objective:

> Find the minimum number of mutations required to transform `start` into `end`.

---

## 2. Graph Interpretation

Again:

```text
DNA string = Node
One-gene mutation = Edge
```

Example:

```text
AACCGGTT
    ↓
AACCGGTA
    ↓
AACCGCTA
```

Therefore:

```text
State
 ↓
Generate mutations
 ↓
Check bank
 ↓
BFS
 ↓
Minimum mutations
```

---

## 3. Why BFS?

Every mutation costs exactly:

```text
1
```

Therefore:

```text
Unweighted graph
       ↓
BFS
       ↓
Shortest transformation
```

This is identical to LC 127.

---

## 4. ELI10 Intuition

Imagine DNA as an 8-letter password.

You can change only one letter at a time.

```text
AACCGGTT
    ↓
AACCGGTA
    ↓
AACCGCTA
```

But you are only allowed to use passwords that appear in the mutation bank.

BFS explores all mutations requiring:

```text
1 mutation
```

then:

```text
2 mutations
```

then:

```text
3 mutations
```

The first time we reach the target is the minimum.

---

# 5. Why LC 433 Is Easier Than LC 127

There are only four possible gene characters:

```text
A C G T
```

LC 127 has:

```text
26 lowercase letters
```

So neighbor generation is smaller.

For every position:

```text
4 possible characters
```

instead of:

```text
26 possible characters
```

---

# 6. Neighbor Generation

Suppose:

```text
AACCGGTT
```

At each position, try:

```text
A
C
G
T
```

while skipping the current character.

For one position, at most:

```text
3
```

actual mutations.

Since there are `8` positions:

$$
8 \times 3 = 24
$$

maximum candidates per state.

Again, only mutations in the bank are valid.

---

# 7. Why a Set?

Convert:

```python
bank
```

into:

```python
bank_set = set(bank)
```

Then:

```python
candidate in bank_set
```

is average `O(1)`.

As soon as we discover a valid mutation, remove it from the set.

This prevents repeated processing.

---

# 8. Important Edge Case

If:

```python
end not in bank
```

the target cannot be reached.

Return:

```python
-1
```

This differs from LC 127, where the problem convention uses `0` when no transformation exists.

This is an important interview detail:

> **Algorithmic pattern can be identical while return-value conventions differ.**

---

# 9. Start Equals End

If:

```text
start == end
```

then:

```text
0 mutations
```

So return:

```python
0
```

---

# 10. Invariant

At every BFS level:

> Every DNA sequence in the queue can be reached from `start` using the recorded minimum number of mutations.

Every sequence is inserted at most once, and every transition changes exactly one gene.

---

# 11. Complexity Derivation

Let:

* `N` = number of sequences in the bank.
* `L` = DNA string length.

For each sequence:

```text
L positions
×
4 possible genes
```

Therefore:

$$
O(NL \times 4)
$$

Since `4` is constant:

$$
O(NL)
$$

For the actual LC 433 constraint where the gene length is fixed at `8`, this is effectively:

```text
O(N)
```

Space:

```text
O(N)
```

for the bank set and BFS queue.

---

# ⚙️ ALGORITHM — STEP-BY-STEP

```text id="w7w2qf"
Step 1 → If start == end, return 0.

Step 2 → If end is not in the bank, return -1.

Step 3 → Convert bank into a set.

Step 4 → Create a BFS queue containing:
         (start, 0)

Step 5 → Mark start as visited.

Step 6 → While the queue is not empty:

         Step 6.1 → Remove the current DNA sequence
                    and mutation count.

         Step 6.2 → For each position:

                    a. Try A, C, G, and T.

                    b. Skip the current gene.

                    c. Build the mutated sequence.

                    d. If it is not in the bank,
                       ignore it.

                    e. If it is the target,
                       return mutations + 1.

                    f. Remove it from the available set.

                    g. Add it to the queue with
                       mutations + 1.

Step 7 → If BFS finishes without reaching the target,
        return -1.
```

---

# BLOCK 2 — EFFICIENT CODE

```python id="a5j8p3"
from collections import deque

class Solution:

    def minMutation(self, start, end, bank):

        # No mutation is required.
        if start == end:
            return 0

        # Target must exist in the allowed bank.
        if end not in bank:
            return -1

        bank_set = set(bank)

        # Queue stores:
        # (DNA state, number of mutations)
        queue = deque([(start, 0)])

        # Start has already been discovered.
        bank_set.discard(start)

        genes = "ACGT"

        while queue:

            state, mutations = queue.popleft()

            for i in range(len(state)):

                for gene in genes:

                    # Do not replace a character with itself.
                    if gene == state[i]:
                        continue

                    # Generate next mutation.
                    next_state = (
                        state[:i] +
                        gene +
                        state[i + 1:]
                    )

                    # Mutation is not allowed.
                    if next_state not in bank_set:
                        continue

                    # Target reached.
                    if next_state == end:
                        return mutations + 1

                    # Mark discovered.
                    bank_set.remove(next_state)

                    # Add to BFS.
                    queue.append(
                        (next_state, mutations + 1)
                    )

        return -1
```

---

## Complexity

Let:

```text
N = number of bank sequences
L = sequence length
```

Each state generates:

```text
L × 4
```

candidates.

Therefore:

```text
Time = O(N × L × 4)
     = O(NL)
```

Since LC 433 uses fixed-length DNA strings:

```text
L = 8
```

so this is effectively:

```text
O(N)
```

Space:

```text
O(N)
```

---

# BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

```python id="7v0hcz"
from collections import deque


class Solution:

    def minMutation(self, start, end, bank):

        if start == end:
            return 0

        if end not in bank:
            return -1

        bank_set = set(bank)

        queue = deque([
            (start, 0)
        ])

        bank_set.discard(start)

        genes = "ACGT"

        while queue:

            state, mutations = queue.popleft()

            for i in range(len(state)):

                for gene in genes:

                    if gene == state[i]:
                        continue

                    next_state = (
                        state[:i] +
                        gene +
                        state[i + 1:]
                    )

                    if next_state not in bank_set:
                        continue

                    if next_state == end:
                        return mutations + 1

                    bank_set.remove(next_state)

                    queue.append(
                        (next_state, mutations + 1)
                    )

        return -1


# Example
start = "AACCGGTT"

end = "AACCGGTA"

bank = [
    "AACCGGTA"
]

solution = Solution()

result = solution.minMutation(
    start,
    end,
    bank
)

print("Minimum Mutations:", result)
```

## Output

```text
Minimum Mutations: 1
```

---

# Detailed Dry Run

Initial:

```text
Start = AACCGGTT
End   = AACCGGTA
```

Bank:

```text
AACCGGTA
```

Queue:

```text
[("AACCGGTT", 0)]
```

---

## Process `AACCGGTT`

We examine each position.

Eventually at position `7`:

```text
Current:
AACCGGTT

Change:
T → A
```

Result:

```text
AACCGGTA
```

This exists in the bank.

It is also the target.

Therefore:

```text
mutations + 1
=
0 + 1
=
1
```

Final answer:

```text
1
```

Transformation:

```text
AACCGGTT
     ↓
AACCGGTA
```

---

# BLOCK 4 — INTERVIEW Q&A

## Q1. Why is LC 433 a BFS problem?

**Answer:**

Each DNA sequence represents a state, and changing one gene represents one edge. Every mutation costs one step, so the problem is an unweighted shortest-path problem. BFS finds the minimum number of mutations.

---

## Q2. Why are there at most 24 neighbors?

There are:

```text
8 positions
```

and:

```text
4 possible genes
```

At each position, one of the four is already present, leaving at most three alternatives.

Therefore:

$$
8 \times 3 = 24
$$

possible actual mutations per state.

---

## Q3. Why do we need the bank?

Because not every theoretical mutation is allowed.

For example:

```text
AACCGGTT
```

could theoretically become many sequences, but only sequences present in `bank` are valid states.

---

## Q4. Why remove discovered mutations from the set?

To prevent revisiting them.

This is equivalent to a `visited` set.

```python
bank_set.remove(next_state)
```

means:

```text
This state has already been discovered.
```

---

## Q5. What is the biggest difference between LC 127 and LC 433?

The **state transformation rule** and alphabet differ:

```text
LC 127:
Word length L
Alphabet = 26 lowercase letters
Change one character

LC 433:
DNA length L
Alphabet = A/C/G/T
Change one gene
```

But the BFS architecture is essentially the same.

---

# 🔥 MASTER COMPARISON — LC 752 vs LC 127 vs LC 433

This is the part you should actually memorize conceptually.

| Feature      | LC 752           | LC 127                  | LC 433            |
| ------------ | ---------------- | ----------------------- | ----------------- |
| State        | 4-digit lock     | Word                    | DNA sequence      |
| Start        | `0000`           | `beginWord`             | `start`           |
| Target       | `target`         | `endWord`               | `end`             |
| Transition   | Rotate one wheel | Change one character    | Change one gene   |
| Alphabet     | `0–9`            | `a–z`                   | `A,C,G,T`         |
| Valid states | Not deadend      | In word list            | In bank           |
| Graph        | Implicit         | Implicit                | Implicit          |
| Algorithm    | BFS              | BFS                     | BFS               |
| Goal         | Minimum moves    | Minimum transformations | Minimum mutations |
| Visited      | Required         | Required                | Required          |

---

# 🧠 THE UNIVERSAL STATE-TRANSFORMATION PATTERN

```text
                 STATE
                   ↓
        What is one legal move?
                   ↓
          GENERATE NEIGHBORS
                   ↓
        Is neighbor VALID?
             ↙          ↘
           NO            YES
           ↓              ↓
         SKIP         VISITED?
                         ↙  ↘
                       YES   NO
                        ↓     ↓
                      SKIP   MARK
                              ↓
                            QUEUE
                              ↓
                             BFS
                              ↓
                       SHORTEST PATH
```

This is the real skill being tested.

---

# SENIOR PATTERN RECOGNITION

When a problem says:

> “Transform X into Y using the minimum number of operations.”

Immediately ask:

### 1. What is the state?

```text
Lock → "0000"
Word → "hit"
DNA → "AACCGGTT"
```

### 2. What is one transition?

```text
Lock → rotate one wheel
Word → change one character
DNA → change one gene
```

### 3. Is every operation equal cost?

If yes:

```text
BFS
```

### 4. Can states repeat?

If yes:

```text
visited
```

### 5. Are some states forbidden?

If yes:

```text
deadend / dictionary / bank
```

### 6. Can neighbors be explicitly stored?

If no:

```text
Implicit Graph
```

Then:

```text
Implicit Graph
      +
Equal-Cost Transitions
      +
Minimum Operations
      ↓
BFS
```

---

# CONNECTION TO YOUR QUEUE ROADMAP

You have now built the BFS progression deliberately:

```text
LC 1971
GRAPH
 ↓
BFS
 ↓
REACHABILITY
```

```text
LC 1091
GRID
 ↓
BFS
 ↓
SHORTEST PATH
```

```text
LC 994
MULTIPLE SOURCES
 ↓
BFS
 ↓
TIME
```

```text
LC 542
MULTIPLE SOURCES
 ↓
BFS
 ↓
NEAREST DISTANCE
```

```text
LC 1162
MULTIPLE SOURCES
 ↓
BFS
 ↓
MAXIMUM NEAREST DISTANCE
```

```text
LC 102
TREE
 ↓
BFS
 ↓
LEVELS
```

```text
LC 199
TREE
 ↓
BFS
 ↓
RIGHTMOST PER LEVEL
```

```text
LC 752
STATE
 ↓
GENERATE MOVES
 ↓
BFS
 ↓
MINIMUM MOVES
```

```text
LC 127
WORD STATE
 ↓
CHARACTER TRANSFORMATION
 ↓
BFS
 ↓
MINIMUM TRANSFORMATIONS
```

```text
LC 433
DNA STATE
 ↓
GENE TRANSFORMATION
 ↓
BFS
 ↓
MINIMUM MUTATIONS
```

The abstraction is becoming more important than the individual problems.

---

# FINAL MASTERY

## Pattern Extraction

```text
Minimum operations
        +
Each operation costs 1
        +
State can be represented explicitly
        +
Next states can be generated
        ↓
BFS STATE-SPACE SEARCH
```

---

## Master Template

```python
from collections import deque

def shortest_transformation(start, target):

    queue = deque([(start, 0)])
    visited = {start}

    while queue:

        state, distance = queue.popleft()

        if state == target:
            return distance

        for next_state in generate_neighbors(state):

            if next_state in visited:
                continue

            if not is_valid(next_state):
                continue

            visited.add(next_state)

            queue.append(
                (next_state, distance + 1)
            )

    return -1
```

---

## Senior Pattern Recognition

The interviewer's real question is usually not:

> “Do you know BFS?”

It is:

> **“Can you recognize that this problem secretly contains a graph?”**

For these three:

```text
LC 752 → lock combinations are nodes
LC 127 → words are nodes
LC 433 → DNA sequences are nodes
```

Then:

```text
One legal operation = one edge
```

and:

```text
Minimum operations = shortest path
```

Therefore:

```text
BFS
```

---

# 📊 PROGRESS UPDATE

```text
LEVEL 6 — STATE TRANSFORMATION BFS

├── ✅ LC 127 — Word Ladder
└── ✅ LC 433 — Minimum Genetic Mutation
```

Next in your locked roadmap:

```text
LEVEL 7 — TREE → GRAPH

└── LC 863 — All Nodes Distance K in Binary Tree
```

### One-Line Takeaway

> **LC 127 and LC 433 are the same core pattern as LC 752: turn each configuration into a graph state, generate one-move neighbors, prevent revisits, and use BFS to find the minimum transformation distance.**

Would you like to continue with LC 863, or would a compact comparison of LC 127 and LC 433 be more useful first?


# LEVEL 7 — TREE → GRAPH
└── LC 863

# 🔥 LEVEL 7 — TREE → GRAPH

# LeetCode 863 — All Nodes Distance K in Binary Tree

Medium

Tree + Graph + BFS

Queue Roadmap

> Goal: Given a binary tree, a target node, and an integer `k`, return all node values that are exactly `k` edges away from the target node.

# 🌳 Problem Statement

You are given:

* The root of a binary tree.

* A reference to a target node.

* An integer `k`.

Return the values of all nodes that are exactly `k` distance from the target.

## Example

```
                 3
               /   \
              5     1
             / \   / \
            6   2 0   8
               / \
              7   4

target = 5
k = 2
```

Nodes at distance `2` from node `5` are:

```
[7, 4, 1]
```

Why?

* `5 → 2 → 7`

* `5 → 2 → 4`

* `5 → 3 → 1`

# 🔹 BLOCK 1 — SENIOR INSIGHTS

## 1. Simplify the problem

The question is not simply:

> “Find the descendants of a node at distance `k`.”

It asks for nodes in every direction:

1. Down through the left child.

2. Down through the right child.

3. Up toward the parent.

4. Then down through the parent’s other branches.

A normal binary tree gives us only:

```
parent → children
```

But this problem requires movement in both directions:

```
             parent
            ↗      ↖
        child     child
```

Therefore, we need to convert the tree into a graph-like structure.

## 2. Hidden translation

The most important transformation is:

```
Binary Tree
     ↓
Add parent references
     ↓
Tree becomes an undirected graph
     ↓
Start BFS from target
     ↓
Stop at distance k
```

A tree is already a graph mathematically, but its usual node structure only stores child references.

We need to explicitly store the parent of each node so that we can move upward.

## 3. Why ordinary DFS is insufficient

Suppose the target is node `5`.

```
                 3
               /   \
              5     1
             / \
            6   2
```

From node `5`, the answer may include node `1`.

However, node `1` is not a descendant of `5`.

A downward-only traversal cannot reach it.

We need:

```
5 → 3 → 1
```

That is why we need parent links.

## 4. ELI10 intuition

Imagine that every room in a building has doors to nearby rooms.

Initially, each room knows only the rooms below it:

```
Room 3 knows Room 5 and Room 1.
Room 5 knows Room 6 and Room 2.
```

But Room `5` does not know how to return to Room `3`.

We give every room a parent address.

Now we can travel:

* Down to children.

* Up to the parent.

* Sideways through the parent to another branch.

Then we use BFS because BFS explores rooms in increasing distance:

```
Distance 0 → target
Distance 1 → immediate neighbors
Distance 2 → neighbors of neighbors
Distance 3 → ...
```

When we reach distance `k`, we have found every required node.

## 5. Graph representation

For this tree:

```
                 3
               /   \
              5     1
             / \   / \
            6   2 0   8
               / \
              7   4
```

The graph connections become:

```
3 ↔ 5
3 ↔ 1
5 ↔ 6
5 ↔ 2
1 ↔ 0
1 ↔ 8
2 ↔ 7
2 ↔ 4
```

Each connection is bidirectional.

For every node, its possible neighbors are:

```
node.left
node.right
node.parent
```

## 6. Core algorithmic insight

We need two phases:

### Phase 1 — Build parent references

Traverse the tree and record:

Python

Run

```
parent[child] = current_node
```

This allows us to move from a node to its parent.

### Phase 2 — BFS from the target

Start from the target node:

Python

Run

```
queue = [(target, 0)]
```

For every node, consider:

Python

Run

```
left
right
parent
```

Use a `visited` set to prevent returning to nodes that have already been explored.

## 7. Why do we need `visited`?

A tree has no cycles when viewed in its original downward direction.

But after adding parent links, we can travel in circles.

Example:

```
5 → 3 → 5 → 3 → ...
```

Without a visited set, BFS could repeatedly revisit the same nodes.

Therefore:

> Once a node has been discovered, mark it as visited immediately.

## 8. Important invariant

During BFS:

> Every node in the queue has been reached through a shortest path from the target, and its stored distance is the minimum number of edges required to reach it.

Because every edge has equal cost, BFS guarantees shortest distances.

## 9. Why BFS is the correct pattern

The problem contains these recognition signals:

|
Signal in problem

|

Algorithmic meaning

|
| --- | --- |
|

Distance measured in edges

|

Graph distance

|
|

Need to move upward and downward

|

Undirected graph

|
|

Find all nodes at exact distance `k`

|

BFS layers

|
|

Every movement costs one edge

|

Unweighted graph

|
|

Start from a target node

|

BFS source

|

Therefore:

```
Tree
 ↓
Parent Mapping
 ↓
Undirected Graph
 ↓
BFS
 ↓
Distance K
```

## 10. Complexity intuition

Let `N` be the number of nodes.

### Building parent references

Every node is visited once:

```
O(N)
```

### BFS

Every node is added to the queue at most once.

Each node has at most three neighbors:

```
left, right, parent
```

Therefore:

```
O(N)
```

### Total

```
Time  = O(N)
Space = O(N)
```

The space is required for:

* Parent mapping.

* Visited set.

* BFS queue.

* Result list.

## ⚙️ ALGORITHM — STEP-BY-STEP

```
Step 1 → If the root is empty, return [].

Step 2 → Create an empty parent map.

Step 3 → Traverse the tree and store each node's parent.

Step 4 → Create a BFS queue containing:
         (target, 0)

Step 5 → Create a visited set containing the target.

Step 6 → While the queue is not empty:

         a. Remove one node and its distance.

         b. If its distance equals k,
            collect its value.

         c. Otherwise, examine its neighbors:
            - left child
            - right child
            - parent

         d. Ignore missing or visited neighbors.

         e. Mark each new neighbor visited.

         f. Add each new neighbor to the queue
            with distance + 1.

Step 7 → Once the BFS reaches distance k,
         return the collected values.
```

A more efficient level-based version processes one complete BFS layer at a time:

```
Step 1 → Build parent references.

Step 2 → Put target in the queue.

Step 3 → Mark target as visited.

Step 4 → Repeat k times:

         a. Process exactly the current queue size.

         b. Add all unvisited neighbors
            of the current layer.

         c. Mark them visited.

Step 5 → After k layers, every node in the queue
         is exactly k edges from the target.

Step 6 → Return the values in the queue.
```

# ⚙️ BLOCK 2 — EFFICIENT CODE

Python

Run

```
from collections import deque


class Solution:

    def distanceK(self, root, target, k):

        if root is None:
            return []

        # -------------------------------------------------
        # Phase 1: Build parent references
        # -------------------------------------------------

        parent = {}

        queue = deque([root])

        while queue:

            node = queue.popleft()

            if node.left is not None:
                parent[node.left] = node
                queue.append(node.left)

            if node.right is not None:
                parent[node.right] = node
                queue.append(node.right)

        # -------------------------------------------------
        # Phase 2: BFS from the target
        # -------------------------------------------------

        queue = deque([target])
        visited = {target}

        distance = 0

        while queue:

            # Every node currently in the queue
            # belongs to the same distance level.
            level_size = len(queue)

            if distance == k:
                return [node.val for node in queue]

            for _ in range(level_size):

                node = queue.popleft()

                neighbors = [
                    node.left,
                    node.right,
                    parent.get(node)
                ]

                for neighbor in neighbors:

                    if neighbor is None:
                        continue

                    if neighbor in visited:
                        continue

                    visited.add(neighbor)
                    queue.append(neighbor)

            distance += 1

        return []
```

## Complexity

Let `N` be the number of nodes.

### Time complexity

Parent mapping visits every node once:

```
O(N)
```

The BFS also visits each node at most once:

```
O(N)
```

Total:

```
O(N) + O(N) = O(N)
```

### Space complexity

The following structures may contain up to `N` nodes:

* Parent map.

* BFS queue.

* Visited set.

* Output list.

Therefore:

```
Space: O(N)
```

## Interview justification

You can say:

> “The target-to-node distance must account for upward and downward movement. I first create parent references to convert the tree into an implicit undirected graph. Then I run BFS from the target because every edge has equal cost. BFS processes nodes level by level, so after `k` layers, the queue contains exactly the nodes at distance `k`. A visited set prevents cycles caused by parent-child movement.”

# 🔹 BLOCK 3 — FULL CODE + DRY RUN

## 1. Full runnable Python code

Python

Run

```
from collections import deque


class TreeNode:

    def __init__(self, val=0, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right


class Solution:

    def distanceK(self, root, target, k):

        if root is None:
            return []

        # -----------------------------------------------
        # Build parent references
        # -----------------------------------------------

        parent = {}

        queue = deque([root])

        while queue:

            node = queue.popleft()

            if node.left is not None:
                parent[node.left] = node
                queue.append(node.left)

            if node.right is not None:
                parent[node.right] = node
                queue.append(node.right)

        # -----------------------------------------------
        # BFS from target
        # -----------------------------------------------

        queue = deque([target])
        visited = {target}

        distance = 0

        while queue:

            level_size = len(queue)

            # All nodes currently in queue
            # are exactly 'distance' edges away.
            if distance == k:
                return [node.val for node in queue]

            for _ in range(level_size):

                node = queue.popleft()

                neighbors = [
                    node.left,
                    node.right,
                    parent.get(node)
                ]

                for neighbor in neighbors:

                    if neighbor is None:
                        continue

                    if neighbor in visited:
                        continue

                    visited.add(neighbor)
                    queue.append(neighbor)

            distance += 1

        return []


# -------------------------------------------------------
# Construct the binary tree
# -------------------------------------------------------

root = TreeNode(3)

root.left = TreeNode(5)
root.right = TreeNode(1)

root.left.left = TreeNode(6)
root.left.right = TreeNode(2)

root.right.left = TreeNode(0)
root.right.right = TreeNode(8)

root.left.right.left = TreeNode(7)
root.left.right.right = TreeNode(4)

# Target node is 5
target = root.left

# Distance
k = 2

# Execute solution
solution = Solution()
result = solution.distanceK(root, target, k)

print("Nodes at distance", k, ":", result)
```

### Output

```
Nodes at distance 2 : [7, 4, 1]
```

## 2. Dry-run tree

```
                 3
               /   \
              5     1
             / \   / \
            6   2 0   8
               / \
              7   4

target = 5
k = 2
```

## 3. Parent mapping

The algorithm builds:

|
Node

|

Parent

|
| --- | --- |
|

5

|

3

|
|

1

|

3

|
|

6

|

5

|
|

2

|

5

|
|

0

|

1

|
|

8

|

1

|
|

7

|

2

|
|

4

|

2

|

Now node `5` can move to:

```
6, 2, 3
```

## 4. BFS dry run

### Initial state

```
Queue   = [5]
Visited = {5}
Distance = 0
```

Node `5` is the target itself.

### Distance 0 → 1

Process node `5`.

Its neighbors are:

```
6, 2, 3
```

Add them to the queue.

```
Queue   = [6, 2, 3]
Visited = {5, 6, 2, 3}
Distance = 1
```

Tree movement:

```
             3
             |
             5
           /   \
          6     2
```

### Distance 1 → 2

Process nodes `6`, `2`, and `3`.

#### Process `6`

Neighbors:

```
None, None, 5
```

All are either missing or already visited.

#### Process `2`

Neighbors:

```
7, 4, 5
```

Add `7` and `4`.

#### Process `3`

Neighbors:

```
5, 1, None
```

Add `1`.

New queue:

```
Queue = [7, 4, 1]

Distance = 2
```

### Distance 2

The queue contains:

```
[7, 4, 1]
```

Every node in this queue is exactly two edges from the target.

Therefore, return:

```
[7, 4, 1]
```

## 5. BFS state table

|
Stage

|

Distance

|

Queue

|

Action

|
| --- | --- | --- | --- |
|

1

|

0

|

`[5]`

|

Start from target

|
|

2

|

1

|

`[6, 2, 3]`

|

Explore target's neighbors

|
|

3

|

2

|

`[7, 4, 1]`

|

Collect nodes at distance `2`

|

## 6. Visual understanding

```
Distance 0:

                 3
                 |
                 5  ← TARGET


Distance 1:

                 3
                 |
          6 ---- 5 ---- 2


Distance 2:

                 1

                 7
                 |
                 2

                 4
```

The exact-distance layer is:

```
7, 4, 1
```

# 🔹 BLOCK 4 — INTERVIEW Q&A

## Q1. Why do we need parent references?

Answer:

A binary tree node normally stores only its left and right children. However, nodes at distance `k` may lie above the target or in another branch.

Parent references allow movement from a node to its parent, converting the tree into an implicit undirected graph.

## Q2. Why is BFS preferred over DFS?

Answer:

Every edge has equal cost: one movement equals one edge.

BFS explores nodes in increasing distance order. Therefore, after processing `k` levels, we have exactly the nodes at distance `k`.

A DFS solution is possible, but it requires more complicated distance calculations and path tracking.

## Q3. Why is a visited set necessary if the original structure is a tree?

Answer:

The original tree has no cycles when traversed downward.

But after adding parent references, we can move back and forth:

```
5 → 3 → 5 → 3 → ...
```

The visited set prevents repeated exploration.

## Q4. Why do we check `distance == k` before processing the current level?

Answer:

At the beginning of a BFS iteration, all nodes in the queue belong to the same distance level.

If the current distance equals `k`, the queue already contains exactly the required nodes.

Expanding them would produce nodes at distance `k + 1`, which are not needed.

## Q5. Can we solve this without explicitly creating a parent dictionary?

Answer:

Yes, but we still need a way to identify the path from the root to the target.

One alternative is:

1. Find the path from the root to the target.

2. Perform DFS from the target.

3. Track the distance to ancestors.

4. Explore opposite subtrees while avoiding the path back to the target.

However, the parent-map plus BFS approach is simpler and easier to justify in an interview.

## Q6. What happens when `k = 0`?

Answer:

The target itself is the only node at distance zero.

The algorithm immediately returns:

Python

Run

```
[target.val]
```

## Q7. What is the difference between this problem and ordinary level-order traversal?

Answer:

Ordinary level-order traversal starts at the root and moves downward.

This problem starts at an arbitrary target and allows movement in three directions:

```
left child
right child
parent
```

Therefore, we first construct parent references and then run BFS from the target.

# 🧠 PATTERN EXTRACTION

## The reusable pattern

Whenever a tree problem contains:

* Distance from an arbitrary node.

* Movement toward ancestors.

* Nodes in other branches.

* A requirement to find nodes within or exactly at a distance.

Think:

```
TREE
 ↓
PARENT MAPPING
 ↓
IMPLICIT UNDIRECTED GRAPH
 ↓
BFS FROM TARGET
 ↓
DISTANCE-BASED ANSWER
```

# 🧩 MASTER TEMPLATE

Python

Run

```
from collections import deque


def nodes_at_distance_k(root, target, k):

    parent = {}

    # Build parent mapping
    queue = deque([root])

    while queue:

        node = queue.popleft()

        if node.left:
            parent[node.left] = node
            queue.append(node.left)

        if node.right:
            parent[node.right] = node
            queue.append(node.right)

    # BFS from target
    queue = deque([target])
    visited = {target}

    distance = 0

    while queue:

        if distance == k:
            return [node.val for node in queue]

        for _ in range(len(queue)):

            node = queue.popleft()

            neighbors = [
                node.left,
                node.right,
                parent.get(node)
            ]

            for neighbor in neighbors:

                if neighbor and neighbor not in visited:

                    visited.add(neighbor)
                    queue.append(neighbor)

        distance += 1

    return []
```

# 🎯 SENIOR PATTERN RECOGNITION

|
Problem clue

|

Recognize

|
| --- | --- |
|

“Distance from target node”

|

BFS from target

|
|

“Move upward in a tree”

|

Parent mapping

|
|

“Other branches may contain answers”

|

Tree → undirected graph

|
|

“Exactly `k` edges”

|

BFS level `k`

|
|

“Minimum number of edges”

|

BFS

|
|

“Avoid revisiting nodes”

|

Visited set

|

## Connection to previous problems

```
LC 1971
Graph reachability
       ↓
LC 1091
Grid as an implicit graph
       ↓
LC 752
State as an implicit graph
       ↓
LC 127 / LC 433
State transformation as an implicit graph
       ↓
LC 863
Tree converted into an implicit undirected graph
```

The central lesson is:

> A graph does not always arrive as an adjacency list. Sometimes you must discover or construct its edges yourself.

# 📈 PROGRESS UPDATE

```
LEVEL 7 — TREE → GRAPH

└── ✅ LC 863 — All Nodes Distance K in Binary Tree
```

Next in the roadmap:

```
LEVEL 8 — MONOTONIC DEQUE

└── LC 239 — Sliding Window Maximum ⭐⭐⭐⭐⭐⭐
```

## One-line takeaway

> When a tree problem requires movement both upward and downward from an arbitrary target, build parent links, treat the tree as an undirected graph, and use BFS to reach distance `k`.



# LEVEL 8 — MONOTONIC DEQUE

└── LC 239 — Sliding Window Maximum ⭐⭐⭐⭐⭐⭐
```

# 🔥 LEVEL 8 — MONOTONIC DEQUE

# LeetCode 239 — Sliding Window Maximum

Hard

Monotonic Deque

⭐⭐⭐⭐⭐⭐ Must Master

> Goal: Given an integer array `nums` and a window size `k`, return the maximum value in every contiguous window of size `k`.

# 🔹 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem statement

You are given:

Python

Run

```
nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3
```

A window of size `3` moves from left to right.

## Sliding window visualization

Window 1 of 6

Max: 3

## 1

0

## 3

1

## -1

2

## -3

3

## 5

4

## 3

5

## 6

6

## 7

7

← Previous

Window size: 3

Next →

The windows are:

|
Window

|

Maximum

|
| --- | --- |
|

`[1, 3, -1]`

|

3

|
|

`[3, -1, -3]`

|

3

|
|

`[-1, -3, 5]`

|

5

|
|

`[-3, 5, 3]`

|

5

|
|

`[5, 3, 6]`

|

6

|
|

`[3, 6, 7]`

|

7

|

Output:

Python

Run

```
[3, 3, 5, 5, 6, 7]
```

## 2. Why the brute-force approach fails

The straightforward approach is:

1. Move the window.

2. Scan all `k` elements.

3. Find the maximum.

There are approximately `n - k + 1` windows, and each scan costs `O(k)`.

Therefore:

O((n−k+1)k)O((n-k+1)k)O((n−k+1)k)

Worst-case complexity:

O(nk)\boxed{O(nk)}O(nk)

For a large array, repeatedly scanning the same elements is wasteful.

## 3. The key question

Instead of asking:

> “What is the maximum of the current window?”

Ask:

> “Which elements are still capable of becoming the maximum?”

This is the central idea of a monotonic deque.

## 4. ELI10 intuition

Imagine a competition between numbers.

For a maximum query:

* Bigger numbers are stronger candidates.

* A smaller number behind a bigger number is useless if the bigger number will remain in the window longer.

* Numbers that leave the window must be removed.

For example:

```
Current candidates: [3, 1, -2]
```

If `5` arrives:

```
[3, 1, -2, 5]
```

The values `-2`, `1`, and `3` are no longer useful as maximum candidates because `5` is bigger and newer.

We can remove them from the back.

The deque keeps only useful candidates in decreasing order.

## 5. Monotonic deque invariant

For the maximum problem, the deque stores indices, not values.

The indices satisfy two conditions:

### Condition 1 — Indices are increasing

The deque represents elements from left to right in the array.

### Condition 2 — Values are decreasing

```
nums[dq[0]] >= nums[dq[1]] >= nums[dq[2]] ...
```

Therefore:

```
Front → largest useful candidate
Back  → smallest useful candidate
```

The front always gives the maximum of the current window.

## 6. Why store indices instead of values?

Suppose:

Python

Run

```
nums = [5, 5, 5]
```

If we store only values, we cannot determine which `5` has expired.

Indices solve two problems:

1. Determine whether an element is outside the window.

2. Retrieve its value from `nums`.

The expiration rule is:

Python

Run

```
dq[0] <= i - k
```

If this is true, the index is outside the current window.

## 7. The two removal rules

At every index `i`, perform two types of cleanup.

### Rule A — Remove expired indices from the front

The current window is:

```
[i - k + 1, i]
```

Any index smaller than `i - k + 1` is expired.

Equivalent condition:

Python

Run

```
dq[0] <= i - k
```

Remove it from the front.

### Rule B — Remove dominated indices from the back

While:

Python

Run

```
nums[dq[-1]] <= nums[i]
```

remove the back index.

Why?

The new element is:

* At least as large.

* Newer.

* Able to remain in future windows longer.

Therefore, the old smaller or equal candidate can never become the maximum before the new element expires.

This is called domination.

## 8. Why do we remove equal values?

We use:

Python

Run

```
nums[dq[-1]] <= nums[i]
```

rather than only `<`.

If two values are equal, keeping the newer index is sufficient because it expires later.

For example:

```
Old candidate: value 5, index 2
New candidate: value 5, index 5
```

The newer `5` dominates the older `5`.

Keeping equal values is also valid, but removing them gives a cleaner deque.

## 9. Why is the front the maximum?

The deque maintains decreasing values:

```
[9, 7, 4, 2]
```

The largest value is always at the front.

After removing expired elements and dominated elements, the front is the largest valid candidate in the current window.

Thus:

Python

Run

```
nums[dq[0]]
```

is the window maximum.

## 10. Why is the algorithm O(n)?

At first glance, the nested `while` loop may look like `O(n²)`.

But each index:

* Enters the deque at most once.

* Leaves the deque at most once.

An index can be removed either:

* From the front because it expired.

* From the back because it was dominated.

It cannot be inserted repeatedly.

Therefore, across the entire algorithm, there are at most `n` insertions and at most `n` removals.

```
Total deque operations = O(n)
```

Hence:

Time=O(n)\boxed{\text{Time} = O(n)}Time=O(n)

Auxiliary deque space:

O(k)\boxed{O(k)}O(k)

Output space is `O(n - k + 1)`.

## 11. Pattern recognition

When you see:

* “Maximum in every window.”

* “Minimum in every window.”

* “Sliding window.”

* “Need an efficient solution better than `O(nk)`.”

* “Elements expire from the left.”

* “Keep only useful candidates.”

Think:

```
SLIDING WINDOW
      ↓
MONOTONIC DEQUE
      ↓
REMOVE EXPIRED
      ↓
REMOVE DOMINATED
      ↓
FRONT = BEST CANDIDATE
```

## 12. Maximum versus minimum

|
Query

|

Deque values

|
| --- | --- |
|

Sliding-window maximum

|

Decreasing

|
|

Sliding-window minimum

|

Increasing

|

For maximum:

Python

Run

```
while nums[dq[-1]] <= nums[i]:
    dq.pop()
```

For minimum:

Python

Run

```
while nums[dq[-1]] >= nums[i]:
    dq.pop()
```

The data structure is the same; the monotonic direction changes.

## ⚙️ ALGORITHM — STEP-BY-STEP

```
Step 1 → Create an empty deque to store indices.

Step 2 → Create an empty result list.

Step 3 → Iterate through every index i in nums.

Step 4 → Remove the front index if it is outside
         the current window.

Step 5 → While the deque is not empty and the value
         at its back is <= nums[i]:

         Remove the back index because it is dominated
         by the current element.

Step 6 → Append index i to the back of the deque.

Step 7 → If the first complete window has been formed
         (i >= k - 1):

         The front index points to the maximum.
         Append nums[dq[0]] to the result.

Step 8 → Return the result.
```

The three essential operations are:

```
1. Remove expired indices.
2. Remove dominated indices.
3. Read the maximum from the front.
```

# ⚙️ BLOCK 2 — EFFICIENT CODE

Python

Run

```
from collections import deque


class Solution:

    def maxSlidingWindow(self, nums, k):

        dq = deque()  # Stores useful indices
        result = []

        for i in range(len(nums)):

            # 1. Remove indices outside the window
            while dq and dq[0] <= i - k:
                dq.popleft()

            # 2. Remove dominated candidates
            while dq and nums[dq[-1]] <= nums[i]:
                dq.pop()

            # 3. Add the current index
            dq.append(i)

            # 4. Record maximum after first window forms
            if i >= k - 1:
                result.append(nums[dq[0]])

        return result
```

## Complexity analysis

Let `n = len(nums)`.

### Time

* Each index is appended once: `O(n)`.

* Each index is removed at most once: `O(n)`.

* Reading the front is `O(1)`.

Total:

O(n+n+n)=O(n)O(n+n+n)=\boxed{O(n)}O(n+n+n)=O(n)

### Space

The deque holds at most `k` indices:

O(k)\boxed{O(k)}O(k)

The result contains `n-k+1` values:

O(n−k+1)O(n-k+1)O(n−k+1)

Therefore:

* Auxiliary space: `O(k)`

* Including output: `O(n)`

## Interview justification

> “I use a monotonic decreasing deque of indices. Before inserting an index, I remove expired indices from the front and dominated smaller or equal values from the back. The front then always represents the maximum of the current window. Every index enters and leaves the deque at most once, giving `O(n)` time and `O(k)` auxiliary space.”

# 🔹 BLOCK 3 — FULL CODE + DRY RUN

## 1. Full runnable code

Python

Run

```
from collections import deque


class Solution:

    def maxSlidingWindow(self, nums, k):

        dq = deque()
        result = []

        for i in range(len(nums)):

            # Remove expired indices
            while dq and dq[0] <= i - k:
                dq.popleft()

            # Remove dominated indices
            while dq and nums[dq[-1]] <= nums[i]:
                dq.pop()

            # Add current index
            dq.append(i)

            # Record maximum when window size reaches k
            if i >= k - 1:
                result.append(nums[dq[0]])

        return result


# Example input
nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3

# Create object
solution = Solution()

# Call function
result = solution.maxSlidingWindow(nums, k)

# Print result
print("Sliding Window Maximum:", result)
```

### Output

```
Sliding Window Maximum: [3, 3, 5, 5, 6, 7]
```

## 2. Detailed dry run

Input:

Python

Run

```
nums = [1, 3, -1, -3, 5, 3, 6, 7]
k = 3
```

The deque stores indices.

The deque values are shown in parentheses.

### Index `i = 0`, value `1`

```
Window not complete yet.
```

Deque:

```
Indices: [0]
Values:  [1]
```

### Index `i = 1`, value `3`

Current value `3` dominates value `1`.

Remove index `0`.

Add index `1`.

Deque:

```
Indices: [1]
Values:  [3]
```

### Index `i = 2`, value `-1`

`-1` is smaller than `3`, so it does not dominate anything.

Add index `2`.

Deque:

```
Indices: [1, 2]
Values:  [3, -1]
```

The first window is now complete:

```
[1, 3, -1]
```

Maximum:

```
nums[1] = 3
```

Result:

```
[3]
```

### Index `i = 3`, value `-3`

The current window is:

```
[3, -1, -3]
```

No index has expired.

`-3` is smaller than `-1`, so append it.

Deque:

```
Indices: [1, 2, 3]
Values:  [3, -1, -3]
```

Maximum:

```
3
```

Result:

```
[3, 3]
```

### Index `i = 4`, value `5`

The current window is:

```
[-1, -3, 5]
```

#### Remove expired index

Index `1` is outside the window because:

```
1 <= 4 - 3
1 <= 1
```

Remove index `1`.

Deque:

```
[2, 3]
```

#### Remove dominated values

`nums[3] = -3 <= 5` → remove index `3`.

`nums[2] = -1 <= 5` → remove index `2`.

#### Add index `4`

Deque:

```
Indices: [4]
Values:  [5]
```

Maximum:

```
5
```

Result:

```
[3, 3, 5]
```

### Index `i = 5`, value `3`

Current window:

```
[-3, 5, 3]
```

No index expires.

`5` is greater than `3`, so no dominated candidate is removed.

Add index `5`.

Deque:

```
Indices: [4, 5]
Values:  [5, 3]
```

Maximum:

```
5
```

Result:

```
[3, 3, 5, 5]
```

### Index `i = 6`, value `6`

Current window:

```
[5, 3, 6]
```

#### Remove expired index

Index `3` is already absent.

#### Remove dominated values

```
3 <= 6 → remove index 5
5 <= 6 → remove index 4
```

Add index `6`.

Deque:

```
Indices: [6]
Values:  [6]
```

Maximum:

```
6
```

Result:

```
[3, 3, 5, 5, 6]
```

### Index `i = 7`, value `7`

Current window:

```
[3, 6, 7]
```

`7` dominates `6`.

Remove index `6`.

Add index `7`.

Deque:

```
Indices: [7]
Values:  [7]
```

Maximum:

```
7
```

Final result:

Python

Run

```
[3, 3, 5, 5, 6, 7]
```

## 3. Dry-run table

|
`i`

|

Value

|

Deque indices

|

Deque values

|

Output

|
| --- | --- | --- | --- | --- |
|

0

|

1

|

`[0]`

|

`[1]`

|

`[]`

|
|

1

|

3

|

`[1]`

|

`[3]`

|

`[]`

|
|

2

|

-1

|

`[1, 2]`

|

`[3, -1]`

|

`[3]`

|
|

3

|

-3

|

`[1, 2, 3]`

|

`[3, -1, -3]`

|

`[3, 3]`

|
|

4

|

5

|

`[4]`

|

`[5]`

|

`[3, 3, 5]`

|
|

5

|

3

|

`[4, 5]`

|

`[5, 3]`

|

`[3, 3, 5, 5]`

|
|

6

|

6

|

`[6]`

|

`[6]`

|

`[3, 3, 5, 5, 6]`

|
|

7

|

7

|

`[7]`

|

`[7]`

|

`[3, 3, 5, 5, 6, 7]`

|

# 🔹 BLOCK 4 — INTERVIEW Q&A

## Q1. Why is a deque better than a normal queue?

Answer:

A normal queue efficiently removes from the front and inserts at the back.

A monotonic deque must remove elements from both ends:

* Front: remove expired indices.

* Back: remove dominated candidates.

A deque supports both operations in `O(1)` amortized time.

## Q2. Why do we store indices instead of values?

Answer:

Indices allow us to:

1. Detect when an element leaves the window.

2. Access its value through `nums[index]`.

3. Handle duplicate values correctly.

Values alone cannot tell us whether a specific occurrence has expired.

## Q3. Why can a smaller element be removed permanently?

Answer:

Suppose the deque contains an older value `4`, and a new value `7` arrives.

The new `7` is:

* Larger than `4`.

* Newer than `4`.

* Able to remain in the window at least as long as `4`.

Therefore, `4` can never become the maximum while `7` is present.

The `4` is dominated and can be discarded.

## Q4. Why does the algorithm not become O(n²) because of the `while` loops?

Answer:

Each index is inserted once and removed at most once.

Although one iteration may remove many elements, those removals cannot happen again for those indices.

Across the entire array:

```
Total insertions = O(n)
Total removals   = O(n)
```

Therefore, the total time is `O(n)`.

## Q5. How would you solve sliding-window minimum?

Answer:

Maintain an increasing deque instead of a decreasing deque.

The removal rule changes to:

Python

Run

```
while dq and nums[dq[-1]] >= nums[i]:
    dq.pop()
```

The front then stores the minimum of the current window.

## Q6. What happens when `k = 1`?

Answer:

Every window contains exactly one element.

The result is the original array:

Python

Run

```
nums = [4, 2, 7]
k = 1

# Output:
[4, 2, 7]
```

The algorithm handles this naturally.

## Q7. Could we use a heap instead?

Answer:

Yes. A max-heap can track the largest candidate, but expired elements must be handled using lazy deletion.

A heap solution generally takes:

```
Time: O(n log k)
Space: O(k)
```

The monotonic deque improves the time complexity to:

```
Time: O(n)
Space: O(k)
```

## Q8. What is the main difference between a heap and a monotonic deque?

|
Feature

|

Heap

|

Monotonic deque

|
| --- | --- | --- |
|

Main purpose

|

Global priority

|

Window-based useful candidates

|
|

Ordering

|

Heap property

|

Fully monotonic values

|
|

Expired elements

|

Often lazy deletion

|

Explicit index removal

|
|

Time per operation

|

`O(log k)`

|

`O(1)` amortized

|
|

Sliding-window maximum

|

Suitable

|

Optimal linear solution

|

# 🧠 PATTERN EXTRACTION

## The monotonic deque template

```
For every new element:

    1. Remove expired indices from the front.

    2. Remove dominated indices from the back.

    3. Insert the current index.

    4. Read the best candidate from the front.
```

For maximum:

Python

Run

```
while dq and nums[dq[-1]] <= nums[i]:
    dq.pop()
```

For minimum:

Python

Run

```
while dq and nums[dq[-1]] >= nums[i]:
    dq.pop()
```

# 🧩 MASTER TEMPLATE

Python

Run

```
from collections import deque


def sliding_window_maximum(nums, k):

    dq = deque()
    result = []

    for i in range(len(nums)):

        # Remove expired indices
        while dq and dq[0] <= i - k:
            dq.popleft()

        # Maintain decreasing values
        while dq and nums[dq[-1]] <= nums[i]:
            dq.pop()

        # Add current index
        dq.append(i)

        # Record answer for complete windows
        if i >= k - 1:
            result.append(nums[dq[0]])

    return result
```

# 🎯 SENIOR PATTERN RECOGNITION

|
Problem clue

|

Recognize

|
| --- | --- |
|

Maximum in every fixed-size window

|

Decreasing monotonic deque

|
|

Minimum in every fixed-size window

|

Increasing monotonic deque

|
|

Elements expire from the left

|

Store indices

|
|

Need better than `O(nk)`

|

Maintain useful candidates

|
|

Maximum/minimum of a moving range

|

Monotonic deque

|
|

A new value dominates older weaker candidates

|

Remove from back

|
|

Front must represent the best valid candidate

|  |

# LEVEL 9 — MULTIPLE MONOTONIC DEQUES

## LeetCode 1438 — Longest Continuous Subarray With Absolute Diff ≤ Limit

**Difficulty:** Medium
**Pattern:** Sliding Window + Two Monotonic Deques
**Importance:** 🔥🔥🔥🔥🔥
**Prerequisite:** LC 239 — Sliding Window Maximum

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given:

```text
nums = [8, 2, 4, 7]
limit = 4
```

We need the **longest contiguous subarray** where:

```text
maximum - minimum <= limit
```

For example:

```text
[2, 4]
```

has:

```text
max = 4
min = 2

4 - 2 = 2 <= 4
```

So it is valid.

But:

```text
[8, 2, 4]
```

has:

```text
max = 8
min = 2

8 - 2 = 6 > 4
```

So it is invalid.

The answer is the **maximum length of any valid window**.

For the example:

```text
nums = [8, 2, 4, 7]
limit = 4
```

the longest valid subarray is:

```text
[2, 4, 7]
```

because:

```text
7 - 2 = 5
```

Actually, that is invalid.

The valid longest windows are:

```text
[8]       → 8 - 8 = 0
[2,4,7]   → 7 - 2 = 5 ❌
[2,4]     → 4 - 2 = 2
[4,7]     → 7 - 4 = 3
```

Therefore the answer is:

```text
2
```

This is an important example because it exposes the exact condition we must maintain.

---

# 2. Hidden Translation

The problem says:

> Find the longest continuous subarray where the difference between the maximum and minimum is at most `limit`.

Translate it:

```text
Longest Subarray
        ↓
Sliding Window
        ↓
Need MAX of current window
        +
Need MIN of current window
        ↓
Two Monotonic Deques
        ↓
Maintain:
max(window) - min(window) <= limit
```

This is the direct evolution of LC 239.

---

# 3. Why One Monotonic Deque Is Not Enough

LC 239 asked:

> What is the maximum of this window?

So we needed:

```text
One decreasing deque
```

LC 1438 asks:

> What is the maximum AND minimum of this window?

Therefore we need:

```text
Maximum deque
+
Minimum deque
```

Specifically:

```text
maxDeque → decreasing values
minDeque → increasing values
```

---

# 4. ELI10 Intuition

Imagine a group of students standing in a line.

We want the largest group where:

```text
tallest student - shortest student <= allowed difference
```

As we expand the group:

```text
right pointer →
```

we add new students.

If the group becomes too different:

```text
maximum - minimum > limit
```

we move the left pointer:

```text
left pointer →
```

until the group becomes valid again.

The difficult part is:

> How do we know the tallest and shortest students quickly?

We use two queues:

```text
MAX DEQUE
front = largest candidate

MIN DEQUE
front = smallest candidate
```

So at any time:

```text
max = nums[maxDeque[0]]
min = nums[minDeque[0]]
```

Then validity is simply:

```text
max - min <= limit
```

---

# 5. The Two Deques

This is the most important concept of LC 1438.

## Maximum deque

Values must remain decreasing:

```text
[9, 7, 4, 2]
```

Therefore:

```python
while maxDeque and nums[maxDeque[-1]] <= nums[right]:
    maxDeque.pop()
```

The front contains the maximum.

---

## Minimum deque

Values must remain increasing:

```text
[2, 4, 7, 9]
```

Therefore:

```python
while minDeque and nums[minDeque[-1]] >= nums[right]:
    minDeque.pop()
```

The front contains the minimum.

---

# 6. Why Store Indices?

Just like LC 239, we store:

```text
indices
```

not values.

Why?

Because when the left side of the window moves, we need to know whether the candidate has expired.

Suppose:

```text
nums = [4, 2, 7]
```

If index `0` leaves the window, we need to know:

```text
Which candidate was at index 0?
```

Therefore the deques contain:

```text
indices
```

and values are accessed using:

```python
nums[index]
```

---

# 7. The Sliding Window Invariant

At every moment, our window is:

```text
[left ... right]
```

and we want to maintain:

```text
max(nums[left:right+1])
-
min(nums[left:right+1])
<= limit
```

The algorithm maintains this invariant:

> After shrinking the window, the current window is valid.

Then:

```text
answer = max(answer, right - left + 1)
```

---

# 8. Why Do We Shrink From the Left?

Suppose:

```text
max - min > limit
```

The current window is invalid.

Adding more elements cannot fix the problem because the old maximum and minimum are still present.

Therefore we must remove elements from the left:

```text
left += 1
```

until:

```text
max - min <= limit
```

Again, the key sliding-window principle is:

```text
Expand right
    ↓
Check validity
    ↓
Invalid?
    ↓
Move left
    ↓
Valid again
    ↓
Record length
```

---

# 9. The Most Important Insight

The algorithm does **not** recompute:

```text
max(window)
min(window)
```

from scratch.

Instead:

```text
maxDeque → maintains maximum
minDeque → maintains minimum
```

Therefore checking the condition is:

```python
nums[maxDeque[0]] - nums[minDeque[0]] <= limit
```

which is:

```text
O(1)
```

---

# 10. Why Do We Remove Dominated Elements?

Consider the maximum deque.

Suppose:

```text
maxDeque values = [8, 5, 3]
```

A new value `7` arrives.

The `3` is dominated because:

```text
7 > 3
```

and `7` is newer.

The `3` can never become the maximum while `7` is still available.

So:

```text
[8, 5, 3]
        ↓ add 7
[8, 5]
```

then:

```text
[8, 5, 7]
```

Since `7 > 5`, `5` is also dominated:

```text
[8]
```

then:

```text
[8, 7]
```

---

For the minimum deque, the logic is reversed.

If:

```text
[2, 5, 8]
```

and `4` arrives:

```text
8 >= 4 → remove 8
5 >= 4 → remove 5
```

Now:

```text
[2, 4]
```

The minimum remains at the front.

---

# 11. Why Does This Stay O(n)?

There are two `while` loops for each index, which can look like:

```text
O(n²)
```

But this is an amortized-analysis problem.

Each index:

```text
enters maxDeque once
leaves maxDeque once

enters minDeque once
leaves minDeque once
```

So across the entire array:

```text
Maximum deque:
    O(n) insertions
    O(n) removals

Minimum deque:
    O(n) insertions
    O(n) removals
```

Therefore:

```text
Total = O(n)
```

The two deques do not create an `O(n²)` algorithm.

---

# 12. Why This Is Called Multiple Monotonic Deques

LC 239:

```text
One sliding window
       ↓
One required extreme
       ↓
One monotonic deque
```

LC 1438:

```text
One sliding window
       ↓
Maximum + Minimum required
       ↓
Two monotonic deques
```

This is the exact progression:

```text
LC 239
Sliding Window Maximum
        ↓
Monotonic Deque
        ↓
LC 1438
Longest Valid Window
        ↓
Maximum Deque + Minimum Deque
```

---

# 13. Recognition Rules

When you see:

```text
Longest subarray
+
contiguous
+
maximum - minimum <= limit
```

immediately think:

```text
Sliding Window
+
Maximum Deque
+
Minimum Deque
```

More generally:

| Problem signal                     | Pattern              |
| ---------------------------------- | -------------------- |
| Longest contiguous subarray        | Sliding Window       |
| Window validity depends on maximum | Max Deque            |
| Window validity depends on minimum | Min Deque            |
| `max - min <= limit`               | Two Monotonic Deques |
| Need better than O(nk)             | Maintain candidates  |

---

# 14. Important Edge Cases

### Case 1 — One element

```text
nums = [5]
limit = 0
```

Answer:

```text
1
```

---

### Case 2 — All equal

```text
nums = [4,4,4,4]
limit = 0
```

Answer:

```text
4
```

---

### Case 3 — Strict limit

```text
nums = [1,3]
limit = 1
```

Window:

```text
[1,3]

3 - 1 = 2 > 1
```

So answer:

```text
1
```

---

### Case 4 — Large limit

If:

```text
max - min <= limit
```

for the entire array, answer is simply:

```text
len(nums)
```

---

# ⚙️ ALGORITHM — STEP-BY-STEP

```text
Step 1 → Initialize:
         left = 0
         answer = 0

Step 2 → Create two empty deques:

         maxDeque
         → decreasing values

         minDeque
         → increasing values

Step 3 → Move the right pointer from left to right.

Step 4 → Insert nums[right] into maxDeque.

         Before insertion:
         remove smaller or equal values from the back.

Step 5 → Insert nums[right] into minDeque.

         Before insertion:
         remove larger or equal values from the back.

Step 6 → Check whether the current window is valid:

         nums[maxDeque[0]] - nums[minDeque[0]] <= limit

Step 7 → If the window is invalid:

         while max - min > limit:

             If maxDeque[0] == left:
                 remove it.

             If minDeque[0] == left:
                 remove it.

             left += 1

Step 8 → Now the window is valid.

Step 9 → Calculate:

         current_length = right - left + 1

Step 10 → Update:

         answer = max(answer, current_length)

Step 11 → Continue until right reaches the end.

Step 12 → Return answer.
```

---

# 🔹 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def longestSubarray(self, nums, limit):

        maxDeque = deque()
        minDeque = deque()

        left = 0
        answer = 0

        for right in range(len(nums)):

            # -----------------------------------------
            # Maintain decreasing deque for MAX
            # -----------------------------------------
            while maxDeque and nums[maxDeque[-1]] <= nums[right]:
                maxDeque.pop()

            maxDeque.append(right)

            # -----------------------------------------
            # Maintain increasing deque for MIN
            # -----------------------------------------
            while minDeque and nums[minDeque[-1]] >= nums[right]:
                minDeque.pop()

            minDeque.append(right)

            # -----------------------------------------
            # Shrink window while invalid
            # -----------------------------------------
            while nums[maxDeque[0]] - nums[minDeque[0]] > limit:

                # Remove expired MAX candidate
                if maxDeque[0] == left:
                    maxDeque.popleft()

                # Remove expired MIN candidate
                if minDeque[0] == left:
                    minDeque.popleft()

                left += 1

            # -----------------------------------------
            # Current window is valid
            # -----------------------------------------
            answer = max(answer, right - left + 1)

        return answer
```

## Time Complexity

Let:

```text
n = len(nums)
```

Every index is:

```text
inserted once into maxDeque
removed at most once from maxDeque

inserted once into minDeque
removed at most once from minDeque
```

Therefore:

```text
Maximum deque operations = O(n)
Minimum deque operations = O(n)
Sliding window movement = O(n)
```

Total:

```text
O(n)
```

## Space Complexity

Each deque contains at most `O(n)` indices in the worst case.

Therefore auxiliary space is:

```text
O(n)
```

More specifically, each deque can contain at most the current window's candidates, so its size is bounded by the window length and therefore by `n`.

## Interview Justification

Say this:

> “I use a variable-size sliding window because I need the longest contiguous subarray satisfying a condition. The condition depends on both the maximum and minimum of the current window, so I maintain two monotonic deques: a decreasing deque for the maximum and an increasing deque for the minimum. When `max - min` exceeds the limit, I move the left pointer and remove expired indices from either deque. Each index enters and leaves each deque at most once, giving O(n) time.”

---

# 🔹 BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

```python
from collections import deque


class Solution:

    def longestSubarray(self, nums, limit):

        maxDeque = deque()
        minDeque = deque()

        left = 0
        answer = 0

        for right in range(len(nums)):

            # Maintain decreasing deque.
            # Front = maximum value.
            while maxDeque and nums[maxDeque[-1]] <= nums[right]:
                maxDeque.pop()

            maxDeque.append(right)

            # Maintain increasing deque.
            # Front = minimum value.
            while minDeque and nums[minDeque[-1]] >= nums[right]:
                minDeque.pop()

            minDeque.append(right)

            # Shrink until window becomes valid.
            while nums[maxDeque[0]] - nums[minDeque[0]] > limit:

                if maxDeque[0] == left:
                    maxDeque.popleft()

                if minDeque[0] == left:
                    minDeque.popleft()

                left += 1

            # Current window is valid.
            current_length = right - left + 1

            answer = max(answer, current_length)

        return answer


# -----------------------------------------
# Example
# -----------------------------------------

nums = [10, 1, 2, 4, 7, 2]
limit = 5

solution = Solution()

result = solution.longestSubarray(nums, limit)

print("Longest Valid Subarray Length:", result)
```

### Output

```text
Longest Valid Subarray Length: 4
```

The longest valid subarray is:

```text
[2, 4, 7, 2]
```

because:

```text
max = 7
min = 2

7 - 2 = 5
```

which satisfies:

```text
5 <= limit
```

---

# Detailed Dry Run

Input:

```text
nums  = [10, 1, 2, 4, 7, 2]
limit = 5
```

We maintain:

```text
maxDeque → decreasing values
minDeque → increasing values
```

---

## Step 1 — right = 0

Value:

```text
10
```

Max deque:

```text
[10]
```

Min deque:

```text
[10]
```

Condition:

```text
10 - 10 = 0 <= 5
```

Window:

```text
[10]
```

Length:

```text
1
```

Answer:

```text
1
```

---

## Step 2 — right = 1

Value:

```text
1
```

### Max deque

`1` is smaller than `10`.

```text
[10, 1]
```

### Min deque

`1` is smaller than `10`, so `10` is dominated.

```text
[1]
```

Condition:

```text
10 - 1 = 9
```

Invalid:

```text
9 > 5
```

Shrink from left.

`left = 0`.

`10` is the front of maxDeque, so remove it.

```text
maxDeque = [1]
```

Move:

```text
left = 1
```

Now:

```text
1 - 1 = 0
```

Valid.

Window:

```text
[1]
```

Length:

```text
1
```

Answer:

```text
1
```

---

## Step 3 — right = 2

Value:

```text
2
```

### Max deque

```text
[1]
```

Since:

```text
1 <= 2
```

remove `1`.

Then add `2`.

```text
maxDeque = [2]
```

### Min deque

```text
[1]
```

`1 < 2`, so keep it.

```text
minDeque = [1, 2]
```

Condition:

```text
2 - 1 = 1 <= 5
```

Valid.

Window:

```text
[1, 2]
```

Length:

```text
2
```

Answer:

```text
2
```

---

## Step 4 — right = 3

Value:

```text
4
```

Max deque:

```text
[4]
```

because `4` dominates `2`.

Min deque:

```text
[1, 2, 4]
```

Condition:

```text
4 - 1 = 3 <= 5
```

Valid.

Window:

```text
[1, 2, 4]
```

Length:

```text
3
```

Answer:

```text
3
```

---

## Step 5 — right = 4

Value:

```text
7
```

Max deque:

```text
[7]
```

because `7` dominates `4`.

Min deque:

```text
[1, 2, 4, 7]
```

Condition:

```text
7 - 1 = 6
```

Invalid.

```text
6 > 5
```

So move `left`.

Current:

```text
left = 1
```

The element at index `1` is `1`.

It is the front of `minDeque`, so remove it.

```text
minDeque = [2, 4, 7]
```

Move:

```text
left = 2
```

Now:

```text
max = 7
min = 2

7 - 2 = 5
```

Valid.

Current window:

```text
[2, 4, 7]
```

Length:

```text
3
```

Answer remains:

```text
3
```

---

## Step 6 — right = 5

Value:

```text
2
```

### Max deque

Current:

```text
[7]
```

`7 > 2`, so keep it.

```text
maxDeque = [7, 2]
```

### Min deque

Current:

```text
[2, 4, 7]
```

The new `2` is equal to the old `2`.

Because we use:

```python
>=
```

the older `2` is removed.

```text
[4, 7]
```

Then append the new `2`:

```text
minDeque = [2]
```

Condition:

```text
7 - 2 = 5
```

Valid.

Current window:

```text
[2, 4, 7, 2]
```

Length:

```text
4
```

Answer:

```text
4
```

Final result:

```text
4
```

---

# Dry Run Table

| right | value | maxDeque values | minDeque values | Window      | Valid? | Answer |
| ----: | ----: | --------------- | --------------- | ----------- | ------ | -----: |
|     0 |    10 | `[10]`          | `[10]`          | `[10]`      | ✓      |      1 |
|     1 |     1 | `[1]`           | `[1]`           | `[1]`       | ✓      |      1 |
|     2 |     2 | `[2]`           | `[1,2]`         | `[1,2]`     | ✓      |      2 |
|     3 |     4 | `[4]`           | `[1,2,4]`       | `[1,2,4]`   | ✓      |      3 |
|     4 |     7 | `[7]`           | `[2,4,7]`       | `[2,4,7]`   | ✓      |      3 |
|     5 |     2 | `[7,2]`         | `[2]`           | `[2,4,7,2]` | ✓      |  **4** |

Final:

```text
answer = 4
```

---

# 🔹 BLOCK 4 — INTERVIEW Q&A

## Q1. Why do we need two deques?

Because the validity condition requires both:

```text
maximum
```

and:

```text
minimum
```

A single monotonic deque can efficiently maintain one extreme. Therefore:

```text
maxDeque → maximum
minDeque → minimum
```

---

## Q2. Why is maxDeque decreasing?

Because we want the largest candidate at the front:

```text
[10, 7, 5, 2]
 ↑
 MAX
```

Whenever a new value is larger than values at the back, those smaller values are dominated and removed.

---

## Q3. Why is minDeque increasing?

Because we want the smallest candidate at the front:

```text
[2, 5, 7, 10]
 ↑
 MIN
```

When a smaller value arrives, larger values behind it can no longer become the minimum while the new value remains in the window.

---

## Q4. Why do we check `max - min > limit`?

The required condition is:

```text
absolute difference between maximum and minimum <= limit
```

Since:

```text
maximum >= minimum
```

we know:

```text
abs(max - min) = max - min
```

Therefore we only need:

```python
max_value - min_value > limit
```

to detect an invalid window.

---

## Q5. Why don't we reset the deques when the window becomes invalid?

Because only the elements that have moved outside the left boundary need to disappear.

The deques already contain the correct useful candidates.

We simply:

```text
move left
+
remove expired indices
```

This preserves the amortized `O(n)` complexity.

---

## Q6. Why can equal values be removed?

Suppose the min deque contains:

```text
index 2 → value 5
```

and a newer:

```text
index 7 → value 5
```

arrives.

The older `5` can be discarded because the newer `5`:

* has the same value,
* becomes valid later,
* expires later.

The same reasoning applies to the max deque.

---

## Q7. What if `limit = 0`?

Then:

```text
max - min <= 0
```

Since:

```text
max >= min
```

we must have:

```text
max == min
```

Therefore the window can contain only equal values.

Example:

```text
[4,4,4]
```

is valid.

But:

```text
[4,4,5]
```

is invalid.

---

## Q8. Could we solve this using a balanced BST?

Yes.

A balanced ordered structure could maintain the minimum and maximum dynamically:

```text
insert → O(log n)
delete → O(log n)
min/max → O(1) or O(log n)
```

But Python does not have a built-in balanced BST equivalent to C++ `multiset`.

The monotonic deque solution is more direct for this exact sliding-window condition and achieves:

```text
O(n)
```

---

# 🧠 PATTERN EXTRACTION

LC 239 taught:

```text
Sliding Window
      ↓
Need MAX
      ↓
One Monotonic Deque
```

LC 1438 extends it:

```text
Sliding Window
      ↓
Need MAX + MIN
      ↓
Two Monotonic Deques
```

The reusable structure is:

```text
                 WINDOW
                   ↓
          ┌────────┴────────┐
          ↓                 ↓
     MAX DEQUE          MIN DEQUE
     decreasing          increasing
          ↓                 ↓
       maximum           minimum
          └────────┬────────┘
                   ↓
              max - min
                   ↓
             Is window valid?
                   ↓
          YES             NO
           ↓               ↓
      expand right     move left
```

---

# 🧩 MASTER TEMPLATE

```python
from collections import deque


def longest_valid_window(nums, limit):

    maxDeque = deque()
    minDeque = deque()

    left = 0
    answer = 0

    for right in range(len(nums)):

        # Maximum deque: decreasing
        while maxDeque and nums[maxDeque[-1]] <= nums[right]:
            maxDeque.pop()

        maxDeque.append(right)

        # Minimum deque: increasing
        while minDeque and nums[minDeque[-1]] >= nums[right]:
            minDeque.pop()

        minDeque.append(right)

        # Restore validity
        while nums[maxDeque[0]] - nums[minDeque[0]] > limit:

            if maxDeque[0] == left:
                maxDeque.popleft()

            if minDeque[0] == left:
                minDeque.popleft()

            left += 1

        # Valid window
        answer = max(answer, right - left + 1)

    return answer
```

This is the template you should memorize conceptually:

```text
MAX DEQUE → decreasing
MIN DEQUE → increasing

right expands
left shrinks

max - min > limit
        ↓
    shrink left

valid
  ↓
update answer
```

---

# 🎯 SENIOR PATTERN RECOGNITION

The strongest recognition rule is:

```text
"Longest contiguous subarray"
+
"maximum and minimum"
+
"constraint between them"
```

Immediately think:

```text
VARIABLE SLIDING WINDOW
        +
MAX MONOTONIC DEQUE
        +
MIN MONOTONIC DEQUE
```

Compare the three queue/deque problems:

| Problem     | Main Pattern           | Data Structure               |
| ----------- | ---------------------- | ---------------------------- |
| LC 239      | Sliding Window Maximum | 1 decreasing deque           |
| **LC 1438** | Longest valid window   | **2 monotonic deques**       |
| LC 862      | Shortest subarray ≥ K  | Prefix Sum + monotonic deque |

The conceptual progression is:

```text
LC 239
   ↓
Maintain one extreme
   ↓
LC 1438
   ↓
Maintain two extremes
   ↓
LC 862
   ↓
Combine prefix sums with monotonic deque
```

---

# 📈 PROGRESS UPDATE

```text
LEVEL 9 — MULTIPLE MONOTONIC DEQUES

└── ✅ LC 1438 — Longest Continuous Subarray
             With Absolute Diff ≤ Limit
```

Queue/Deque roadmap:

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994
├── ✅ LC 542
└── ✅ LC 1162

LEVEL 4 — LEVEL-ORDER BFS
├── ✅ LC 102
└── ✅ LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── ✅ LC 752

LEVEL 6 — STATE TRANSFORMATION BFS
├── ✅ LC 127
└── ✅ LC 433

LEVEL 7 — TREE → GRAPH
└── ✅ LC 863

LEVEL 8 — MONOTONIC DEQUE
└── ✅ LC 239

LEVEL 9 — MULTIPLE MONOTONIC DEQUES
└── ✅ LC 1438

LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE
└── ⬜ LC 862

LEVEL 11 — DP + MONOTONIC DEQUE
└── ⬜ LC 1696
```

# One-Line Takeaway

> **When a variable sliding window must simultaneously track its maximum and minimum, maintain a decreasing max-deque and an increasing min-deque; shrink from the left whenever `max - min > limit`.**

# LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE

## LeetCode 862 — Shortest Subarray with Sum at Least K

**Difficulty:** Hard
**Pattern:** Prefix Sum + Monotonic Deque
**Importance:** 🔥🔥🔥🔥🔥
**Prerequisites:** Prefix Sum + Sliding Window + Monotonic Deque

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given an integer array `nums` and an integer `k`.

You need to find the **length of the shortest non-empty contiguous subarray** whose sum is at least `k`.

Example:

```text
nums = [2, -1, 2]
k = 3
```

The entire array:

```text
[2, -1, 2]
```

has sum:

```text
2 + (-1) + 2 = 3
```

So the answer is:

```text
3
```

---

Consider:

```text
nums = [1, 2, 3, 4]
k = 7
```

Possible valid subarrays include:

```text
[1,2,3,4] → 10
[2,3,4]   → 9
[3,4]     → 7
```

The shortest is:

```text
[3,4]
```

Length:

```text
2
```

Answer:

```text
2
```

---

# 2. Why This Problem Is Difficult

At first glance, this looks like a normal sliding-window problem.

You might think:

```text
left = 0
right = 0

expand right
if sum >= k:
    move left
```

That works when all numbers are **non-negative**.

But LC 862 allows negative numbers.

Example:

```text
nums = [2, -1, 2]
```

The sum can:

```text
increase
decrease
increase
```

So the normal sliding-window invariant breaks.

This is the critical recognition:

> **Negative numbers destroy the standard positive-number sliding-window technique.**

We need another way to calculate subarray sums efficiently.

---

# 3. Prefix Sum Transformation

Define:

```text
prefix[i] = sum of nums[0:i]
```

For:

```text
nums = [2, -1, 2]
```

we create:

```text
prefix = [0, 2, 1, 3]
```

Why the initial `0`?

Because:

```text
prefix[0] = 0
```

represents the sum before the array begins.

---

## The crucial formula

For a subarray:

```text
nums[i ... j-1]
```

its sum is:

```text
prefix[j] - prefix[i]
```

Therefore the condition:

```text
subarray sum >= k
```

becomes:

```text
prefix[j] - prefix[i] >= k
```

Rearrange:

```text
prefix[j] - prefix[i] >= k
```

means:

```text
prefix[i] <= prefix[j] - k
```

This transforms the problem into a relationship between prefix sums.

---

# 4. ELI10 Intuition

Imagine a bank account.

`prefix[i]` is your money balance after processing the first `i` elements.

Suppose:

```text
prefix[j] = 10
```

and you need a subarray with sum at least:

```text
K = 7
```

We need an earlier prefix value satisfying:

```text
10 - prefix[i] >= 7
```

Therefore:

```text
prefix[i] <= 3
```

So we are looking for an earlier prefix that is:

1. **small enough** to make the difference at least `K`;
2. **as recent as possible** so that the resulting subarray is as short as possible.

That second requirement is why the deque becomes important.

---

# 5. The Problem Becomes

For every current prefix sum `prefix[j]`, find an earlier index `i` such that:

```text
prefix[j] - prefix[i] >= k
```

and minimize:

```text
j - i
```

So there are two competing requirements:

```text
Need prefix[i] small
+
Need i as large as possible
```

This is exactly where the monotonic deque helps.

---

# 6. Why a Monotonic Deque?

We maintain indices of prefix sums.

The deque will satisfy:

```text
prefix[dq[0]] <= prefix[dq[1]] <= prefix[dq[2]] ...
```

So the prefix sums are **increasing**.

Therefore:

```text
front = smallest useful prefix sum
```

Why do we want the smallest prefix?

Because:

```text
prefix[j] - prefix[i]
```

becomes larger when `prefix[i]` is smaller.

---

# 7. The Two Critical Deque Operations

There are two different reasons to remove indices.

## Rule 1 — Found a valid subarray

If:

```text
prefix[j] - prefix[dq[0]] >= k
```

then we have found a valid subarray.

Its length is:

```text
j - dq[0]
```

We record it.

But then something powerful happens.

The current front index is no longer useful.

Why?

Suppose:

```text
i = dq[0]
```

and it already produces a valid subarray ending at `j`.

For future positions:

```text
j+1, j+2, ...
```

the index `i` is older than every other candidate.

If another index can produce a valid subarray, that newer index will create a **shorter** subarray.

Therefore we can remove the front.

```python
dq.popleft()
```

This is a very important greedy observation.

---

# 8. Rule 2 — Remove Dominated Prefix Sums

Suppose the deque contains:

```text
index 2 → prefix = 5
index 4 → prefix = 3
```

The newer prefix:

```text
index 4
prefix = 3
```

dominates the older:

```text
index 2
prefix = 5
```

Why?

For any future prefix `prefix[j]`:

```text
prefix[j] - 3
```

is always at least:

```text
prefix[j] - 5
```

And index `4` is newer.

Therefore index `2` can never produce a better shortest subarray than index `4`.

So remove the older dominated candidate.

The rule is:

```python
while dq and prefix[dq[-1]] >= prefix[j]:
    dq.pop()
```

This maintains:

```text
prefix values increasing
```

---

# 9. The Complete Pattern

At every prefix index `j`:

```text
1. Remove valid candidates from the FRONT.
2. Remove dominated candidates from the BACK.
3. Add current prefix index to the BACK.
```

More precisely:

```text
             Current prefix[j]
                    ↓
        ┌───────────┴───────────┐
        ↓                       ↓
Valid difference?        Dominated candidates?
        ↓                       ↓
 Remove FRONT             Remove BACK
        └───────────┬───────────┘
                    ↓
              Append j
```

---

# 10. Why Prefix Sum Is Necessary

Normal sliding window relies on this assumption:

> Adding an element makes the sum larger or equal.

That is true only when:

```text
nums[i] >= 0
```

LC 862 allows:

```text
nums[i] < 0
```

Therefore:

```text
right += 1
```

can actually **decrease** the sum.

Prefix sums solve this because every subarray sum can always be represented as:

```text
prefix[j] - prefix[i]
```

regardless of whether the numbers are positive or negative.

---

# 11. Example of Negative Numbers

Consider:

```text
nums = [2, -1, 2]
k = 3
```

Prefix sums:

```text
index:   0   1   2   3
prefix:  0   2   1   3
```

At `j = 3`:

```text
prefix[3] = 3
```

We need:

```text
3 - prefix[i] >= 3
```

Therefore:

```text
prefix[i] <= 0
```

Index `0` has:

```text
prefix[0] = 0
```

So:

```text
3 - 0 = 3
```

The subarray is:

```text
nums[0:3]
=
[2,-1,2]
```

Length:

```text
3
```

Answer:

```text
3
```

---

# 12. Important Invariant

At every iteration:

> The deque contains candidate prefix indices in increasing index order and increasing prefix-sum order, and every removed candidate is provably unable to produce a better answer than a candidate that replaced it.

This is the senior-level invariant.

---

# 13. Why the Front Is Special

The front represents the **smallest useful prefix sum**.

Therefore it has the greatest chance of satisfying:

```text
prefix[j] - prefix[i] >= k
```

When it satisfies the condition, we calculate:

```text
j - i
```

Then remove it and check the next candidate.

Because the deque is ordered by prefix sum, the front gives us the strongest candidate for reaching `K`.

---

# 14. Why the Algorithm Is O(n)

Again, the `while` loops might look dangerous.

But each prefix index:

```text
enters deque once
```

and can leave:

```text
from front once
```

or:

```text
from back once
```

It can never be reinserted.

Therefore:

```text
Total insertions = O(n)
Total removals   = O(n)
```

So:

```text
Time = O(n)
```

Prefix array:

```text
Space = O(n)
```

Deque:

```text
O(n)
```

Total auxiliary space:

```text
O(n)
```

---

# 15. Recognition Rules

When you see:

```text
Shortest subarray
+
sum >= K
+
negative numbers allowed
```

think:

```text
PREFIX SUM
      ↓
SUBARRAY SUM = prefix[j] - prefix[i]
      ↓
Need shortest distance j - i
      ↓
MONOTONIC DEQUE
```

This is one of the most important advanced sliding-window patterns in your roadmap.

---

# ⚙️ ALGORITHM — STEP-BY-STEP

```text
Step 1 → Build the prefix sum array.

         prefix[0] = 0

         prefix[i + 1] =
             prefix[i] + nums[i]

Step 2 → Create an empty deque.

         It stores prefix indices.

Step 3 → Iterate j from 0 to n.

Step 4 → While the deque is not empty and:

         prefix[j] - prefix[dq[0]] >= k

         we have found a valid subarray.

Step 5 → Update the shortest length:

         answer = min(answer, j - dq[0])

Step 6 → Remove dq[0].

         That older candidate cannot produce
         a better future answer.

Step 7 → Maintain increasing prefix sums.

         While:

         prefix[dq[-1]] >= prefix[j]

         remove dq[-1].

         The newer index dominates the older one.

Step 8 → Add j to the back of the deque.

Step 9 → Continue until every prefix index
         has been processed.

Step 10 → If no valid subarray exists,
          return -1.

Step 11 → Otherwise return the shortest length.
```

---

# 🔹 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def shortestSubarray(self, nums, k):

        n = len(nums)

        # -----------------------------------------
        # Build prefix sums
        # -----------------------------------------

        prefix = [0] * (n + 1)

        for i in range(n):
            prefix[i + 1] = prefix[i] + nums[i]

        # -----------------------------------------
        # Monotonic deque
        # Stores prefix indices
        # Prefix values remain increasing
        # -----------------------------------------

        dq = deque()

        answer = n + 1

        # -----------------------------------------
        # Process every prefix index
        # -----------------------------------------

        for j in range(n + 1):

            # -------------------------------------
            # Rule 1:
            # Remove valid candidates from front
            # -------------------------------------

            while dq and prefix[j] - prefix[dq[0]] >= k:

                answer = min(
                    answer,
                    j - dq[0]
                )

                dq.popleft()

            # -------------------------------------
            # Rule 2:
            # Remove dominated candidates
            # -------------------------------------

            while dq and prefix[dq[-1]] >= prefix[j]:
                dq.pop()

            # -------------------------------------
            # Add current prefix index
            # -------------------------------------

            dq.append(j)

        # -----------------------------------------
        # Return answer
        # -----------------------------------------

        return answer if answer <= n else -1
```

---

## Complexity Analysis

### Prefix sum construction

We process every element once:

```text
O(n)
```

### Deque processing

Each prefix index:

```text
enters once
leaves at most once
```

Therefore:

```text
O(n)
```

Total:

```text
O(n) + O(n)
=
O(n)
```

### Space

Prefix array:

```text
O(n)
```

Deque:

```text
O(n)
```

Therefore:

```text
Time  = O(n)
Space = O(n)
```

---

## Interview Justification

A strong interview explanation:

> “Because negative values are allowed, a normal sliding window cannot maintain the sum monotonically. I convert the problem using prefix sums, where the sum of subarray `[i, j)` is `prefix[j] - prefix[i]`. For each `j`, I need the largest possible `i` satisfying `prefix[i] <= prefix[j] - K`. I maintain candidate prefix indices in a monotonically increasing deque. Valid candidates are removed from the front after updating the answer, while dominated larger prefix sums are removed from the back. Each index enters and leaves once, giving O(n) time.”

---

# 🔹 BLOCK 3 — FULL CODE + DRY RUN

## Full Runnable Python Code

```python
from collections import deque


class Solution:

    def shortestSubarray(self, nums, k):

        n = len(nums)

        # Build prefix sum array
        prefix = [0] * (n + 1)

        for i in range(n):
            prefix[i + 1] = prefix[i] + nums[i]

        # Monotonic deque
        dq = deque()

        # Impossible value initially
        answer = n + 1

        for j in range(n + 1):

            # -------------------------------------
            # Find valid shortest subarrays
            # -------------------------------------

            while dq and prefix[j] - prefix[dq[0]] >= k:

                current_length = j - dq[0]

                answer = min(
                    answer,
                    current_length
                )

                dq.popleft()

            # -------------------------------------
            # Remove dominated prefix sums
            # -------------------------------------

            while dq and prefix[dq[-1]] >= prefix[j]:
                dq.pop()

            # Add current prefix index
            dq.append(j)

        # Return answer
        if answer == n + 1:
            return -1

        return answer


# -----------------------------------------
# Example
# -----------------------------------------

nums = [2, -1, 2]
k = 3

solution = Solution()

result = solution.shortestSubarray(nums, k)

print("Shortest Subarray Length:", result)
```

### Output

```text
Shortest Subarray Length: 3
```

---

# Detailed Dry Run

Input:

```text
nums = [2, -1, 2]
k = 3
```

---

## Step 1 — Build Prefix Sum

Start:

```text
prefix[0] = 0
```

After `2`:

```text
prefix[1] = 2
```

After `-1`:

```text
prefix[2] = 1
```

After `2`:

```text
prefix[3] = 3
```

Therefore:

```text
Index:   0   1   2   3
Prefix:  0   2   1   3
```

---

## Step 2 — j = 0

```text
prefix[0] = 0
```

Deque is empty.

Add:

```text
dq = [0]
```

---

## Step 3 — j = 1

```text
prefix[1] = 2
```

Check valid condition:

```text
2 - prefix[0] >= 3
```

```text
2 - 0 >= 3
```

```text
2 >= 3
```

False.

Now check domination.

```text
prefix[0] >= prefix[1]
```

```text
0 >= 2
```

False.

Add index `1`:

```text
dq = [0, 1]
```

Prefix values:

```text
[0, 2]
```

Increasing.

---

## Step 4 — j = 2

```text
prefix[2] = 1
```

### Check valid candidate

Front:

```text
dq[0] = 0
```

Calculate:

```text
1 - 0 = 1
```

Not enough:

```text
1 < 3
```

### Remove dominated candidates

Back:

```text
dq[-1] = 1
```

Prefix:

```text
prefix[1] = 2
prefix[2] = 1
```

Since:

```text
2 >= 1
```

index `1` is dominated.

Remove:

```text
dq = [0]
```

Now add index `2`:

```text
dq = [0, 2]
```

Prefix values:

```text
[0, 1]
```

---

## Step 5 — j = 3

```text
prefix[3] = 3
```

Check front:

```text
prefix[3] - prefix[0]
=
3 - 0
=
3
```

We have:

```text
3 >= k
```

Therefore we found a valid subarray.

Length:

```text
3 - 0 = 3
```

Update:

```text
answer = 3
```

Remove index `0`:

```text
dq = [2]
```

Now check front again:

```text
prefix[3] - prefix[2]
=
3 - 1
=
2
```

Not enough:

```text
2 < 3
```

No more valid candidate.

Now check domination:

```text
prefix[2] >= prefix[3]
```

```text
1 >= 3
```

False.

Add index `3`:

```text
dq = [2, 3]
```

Final answer:

```text
3
```

---

# Dry-Run Table

| `j` | `prefix[j]` | Deque indices | Deque prefix values | Action               | Answer |
| --: | ----------: | ------------- | ------------------- | -------------------- | -----: |
|   0 |           0 | `[0]`         | `[0]`               | Add 0                |      — |
|   1 |           2 | `[0,1]`       | `[0,2]`             | Add 1                |      — |
|   2 |           1 | `[0,2]`       | `[0,1]`             | Remove dominated 1   |      — |
|   3 |           3 | `[2,3]`       | `[1,3]`             | `3-0 >= 3`, length 3 |  **3** |

---

# Second Important Example

Consider:

```text
nums = [1, 2, 3, 4]
k = 7
```

Prefix:

```text
[0, 1, 3, 6, 10]
```

At:

```text
j = 4
prefix[4] = 10
```

We need:

```text
10 - prefix[i] >= 7
```

So:

```text
prefix[i] <= 3
```

The candidate:

```text
prefix[2] = 3
```

produces:

```text
10 - 3 = 7
```

Subarray:

```text
nums[2:4]
=
[3,4]
```

Length:

```text
4 - 2 = 2
```

Answer:

```text
2
```

This demonstrates the main purpose of the deque:

```text
Find a sufficiently small prefix
+
prefer the latest possible index
=
shortest valid subarray
```

---

# 🔹 BLOCK 4 — INTERVIEW Q&A

## Q1. Why can't we use a normal sliding window?

Because negative numbers are allowed.

For positive numbers:

```text
expand right → sum increases
shrink left  → sum decreases
```

This gives a predictable sliding-window invariant.

With negative numbers:

```text
expand right → sum might decrease
```

So the normal two-pointer technique is not reliable.

Prefix sums remove this problem.

---

## Q2. What does `prefix[j] - prefix[i]` represent?

It represents:

```text
sum(nums[i:j])
```

because:

```text
prefix[j]
=
nums[0] + ... + nums[j-1]
```

and:

```text
prefix[i]
=
nums[0] + ... + nums[i-1]
```

Subtracting gives:

```text
nums[i] + ... + nums[j-1]
```

---

## Q3. Why is the deque increasing by prefix value?

We want to remove dominated candidates.

Suppose:

```text
i < j
```

and:

```text
prefix[i] >= prefix[j]
```

Then `j` is better than `i` because:

1. `prefix[j]` is smaller or equal.
2. `j` is newer.
3. For every future endpoint `x`:

```text
prefix[x] - prefix[j]
>=
prefix[x] - prefix[i]
```

4. The subarray using `j` is shorter.

Therefore `i` can never be the optimal candidate.

---

## Q4. Why do we remove a candidate from the front after finding a valid subarray?

Suppose:

```text
prefix[j] - prefix[i] >= k
```

We found a valid subarray of length:

```text
j - i
```

For any future endpoint `x > j`, candidate `i` is older.

A newer valid candidate can produce a shorter subarray.

Therefore keeping `i` cannot improve the answer.

This is a greedy dominance argument.

---

## Q5. Why is this still O(n) despite two `while` loops?

Because every prefix index enters the deque exactly once.

After entering, it can leave only once:

```text
front → valid candidate
```

or:

```text
back → dominated candidate
```

Therefore:

```text
O(n) insertions
+
O(n) removals
=
O(n)
```

---

## Q6. What happens if no valid subarray exists?

The initial answer is set to an impossible value:

```python
answer = n + 1
```

If it remains unchanged:

```text
answer == n + 1
```

we return:

```text
-1
```

---

## Q7. What is the connection between LC 239, LC 1438, and LC 862?

This is the progression you need to recognize:

```text
LC 239
Sliding Window Maximum
        ↓
One Monotonic Deque
```

then:

```text
LC 1438
Longest Valid Window
        ↓
Maximum + Minimum
        ↓
Two Monotonic Deques
```

then:

```text
LC 862
Shortest Subarray ≥ K
        ↓
Negative numbers
        ↓
Prefix Sum
        ↓
Monotonic Deque
```

So LC 862 is not a random new technique.

It combines two concepts:

```text
Prefix Sum
+
Monotonic Deque
```

---

# 🧠 PATTERN EXTRACTION

The core transformation is:

```text
Subarray sum >= K
        ↓
prefix[j] - prefix[i] >= K
        ↓
prefix[i] <= prefix[j] - K
        ↓
Find the best previous prefix
        ↓
Minimize j - i
        ↓
Monotonic Deque
```

The most important conceptual distinction:

```text
LC 239 / LC 1438
        ↓
Deque maintains EXTREME VALUES

LC 862
        ↓
Deque maintains CANDIDATE PREFIX INDICES
```

That distinction is critical.

---

# 🧩 MASTER TEMPLATE

```python
from collections import deque


def shortest_subarray_at_least_k(nums, k):

    n = len(nums)

    # Prefix sums
    prefix = [0] * (n + 1)

    for i in range(n):
        prefix[i + 1] = prefix[i] + nums[i]

    dq = deque()

    answer = n + 1

    for j in range(n + 1):

        # 1. Find valid subarrays
        while dq and prefix[j] - prefix[dq[0]] >= k:

            answer = min(
                answer,
                j - dq[0]
            )

            dq.popleft()

        # 2. Remove dominated prefixes
        while dq and prefix[dq[-1]] >= prefix[j]:
            dq.pop()

        # 3. Add current prefix
        dq.append(j)

    return answer if answer <= n else -1
```

Memorize the logic, not the code:

```text
PREFIX SUM
    ↓
Current prefix - old prefix >= K?
    ↓
YES → update answer + pop front
    ↓
Remove larger/equal prefixes from back
    ↓
Push current prefix
```

---

# 🎯 SENIOR PATTERN RECOGNITION

When you see:

```text
Shortest subarray
+
sum >= K
+
negative numbers allowed
```

your immediate thought should be:

```text
❌ Normal sliding window

        ↓

✅ Prefix Sum

        ↓

Subarray sum:
prefix[j] - prefix[i]

        ↓

Need:
prefix[i] <= prefix[j] - K

        ↓

Need shortest j - i

        ↓

✅ Increasing Monotonic Deque
```

### Three-Level Monotonic Deque Mastery

| Level        | Problem    | What deque maintains         |
| ------------ | ---------- | ---------------------------- |
| Level 8      | LC 239     | Maximum candidate            |
| Level 9      | LC 1438    | Maximum + minimum candidates |
| **Level 10** | **LC 862** | **Prefix-sum candidates**    |

This is the important jump:

```text
LC 239
"Which value is the maximum?"

        ↓

LC 1438
"Which values are the maximum and minimum?"

        ↓

LC 862
"Which previous prefix gives the shortest valid subarray?"
```

---

# 📈 PROGRESS UPDATE

```text
LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE

└── ✅ LC 862 — Shortest Subarray with Sum at Least K
```

Current Queue/Deque roadmap:

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994
├── ✅ LC 542
└── ✅ LC 1162

LEVEL 4 — LEVEL-ORDER BFS
├── ✅ LC 102
└── ✅ LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── ✅ LC 752

LEVEL 6 — STATE TRANSFORMATION BFS
├── ✅ LC 127
└── ✅ LC 433

LEVEL 7 — TREE → GRAPH
└── ✅ LC 863

LEVEL 8 — MONOTONIC DEQUE
└── ✅ LC 239

LEVEL 9 — MULTIPLE MONOTONIC DEQUES
└── ✅ LC 1438

LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE
└── ✅ LC 862

LEVEL 11 — DP + MONOTONIC DEQUE
└── ⬜ LC 1696
```

# One-Line Takeaway

> **When negative numbers break normal sliding-window sum logic, convert subarray sums into prefix-sum differences and use an increasing monotonic deque to keep only the prefix candidates that can produce the shortest valid subarray.**

Would you like to continue with LC 1696 next, or practice LC 862 with a few custom dry runs?


Absolutely, bro. **LC 1696 will be taught at the full locked depth — no reduction in any section.**

# LEVEL 11 — DP + MONOTONIC DEQUE

## LeetCode 1696 — Jump Game VI

**Difficulty:** Medium
**Pattern:** Dynamic Programming + Sliding Window Maximum + Monotonic Deque
**Importance:** 🔥🔥🔥🔥🔥
**Roadmap Position:** Final problem in Queue/Deque Mastery

This problem is especially important because it connects **DP transition optimization** with the **monotonic deque pattern**.

---

# 🔹 BLOCK 1 — SENIOR INSIGHTS

## 1. Problem Simplification

You are given:

```text
nums = [1, -1, -2, 4, -7, 3]
k = 2
```

You start at index `0`.

From index `i`, you can jump to any index:

```text
i + 1
i + 2
...
i + k
```

You must reach:

```text
index n - 1
```

Your score is the sum of the values of all visited positions.

We need:

> **Maximum possible score when reaching the last index.**

---

## 2. Simple Example

Suppose:

```text
nums = [1, -1, -2, 4]
k = 2
```

Possible paths include:

```text
0 → 1 → 3

score = 1 + (-1) + 4
      = 4
```

or:

```text
0 → 2 → 3

score = 1 + (-2) + 4
      = 3
```

Therefore:

```text
answer = 4
```

---

# 3. The Hidden DP Structure

The critical question is:

> What is the best score for reaching each index?

Define:

```text
dp[i] = maximum score obtainable when reaching index i
```

Then consider how we can reach index `i`.

We can come from:

```text
i - 1
i - 2
...
i - k
```

Therefore:

```text
dp[i] = nums[i] + max(
    dp[i-1],
    dp[i-2],
    ...
    dp[i-k]
)
```

This is the fundamental recurrence.

---

# 4. ELI10 Intuition

Imagine that every position is a platform.

```text
0     1     2     3     4     5
●     ●     ●     ●     ●     ●
```

You can jump at most `k` platforms forward.

For every platform `i`, ask:

> “Among the previous `k` platforms that I could have jumped from, which one gives me the highest score?”

Take that best score and add the current platform's value.

So:

```text
best previous score
        +
current value
        =
best score at current position
```

The problem is that the recurrence appears to require scanning up to `k` previous DP values for every index.

That would be:

```text
O(nk)
```

We need to optimize that maximum lookup.

---

# 5. Why Naive DP Is Too Slow

The direct DP is:

```python
dp[i] = nums[i] + max(dp[i-k:i])
```

For every `i`, we may inspect up to `k` elements.

Therefore:

```text
n positions
×
up to k previous positions
=
O(nk)
```

If:

```text
n = 100,000
k = 50,000
```

then this becomes enormous.

We need:

```text
O(n)
```

or close to it.

---

# 6. The Connection to LC 239

This is the most important connection.

LC 239 asked:

> What is the maximum value inside the current sliding window?

Here we ask:

> What is the maximum DP value inside the previous `k` positions?

That is structurally the same problem.

LC 239:

```text
nums window
↓
maximum
↓
monotonic deque
```

LC 1696:

```text
dp window
↓
maximum
↓
monotonic deque
```

Therefore:

> **The monotonic deque is not only for raw array values. It can optimize a DP transition whenever the transition requires a sliding-window maximum or minimum.**

---

# 7. DP Recurrence

The recurrence is:

```text
dp[i] = nums[i] + max(dp[j])
```

where:

```text
i-k <= j < i
```

More precisely:

```text
dp[i] = nums[i] + max(
    dp[max(0, i-k)],
    ...
    dp[i-1]
)
```

The maximum is taken over the previous `k` reachable positions.

---

# 8. The Real Bottleneck

The recurrence itself is easy.

The expensive operation is:

```text
max(
    dp[i-k],
    dp[i-k+1],
    ...
    dp[i-1]
)
```

If we calculate this from scratch for every `i`:

```text
O(k)
```

per index.

Instead, maintain:

```text
monotonic decreasing deque
```

whose front always contains the index of the largest useful DP value.

Then:

```python
dp[dq[0]]
```

gives the required maximum in:

```text
O(1)
```

---

# 9. Why the Deque Is Decreasing

Suppose:

```text
dp values:

[10, 7, 4, 2]
```

We want:

```text
maximum
```

Therefore we maintain:

```text
dp[dq[0]] >= dp[dq[1]] >= dp[dq[2]] ...
```

The front is always the best previous state.

When a new DP value arrives, if it is greater than or equal to values at the back, those older states are dominated.

---

# 10. What Does "Dominated" Mean Here?

Suppose:

```text
index 3 → dp[3] = 5
index 5 → dp[5] = 8
```

The newer state has:

```text
dp[5] > dp[3]
```

and is also newer.

For future index `i`, both may be candidates only if they remain within the previous `k` positions.

But index `5`:

* has a higher score;
* expires later.

Therefore index `3` can never be better than index `5`.

So index `3` can be removed.

This is exactly the same domination principle from LC 239.

---

# 11. Two Responsibilities of the Deque

At every index `i`, the deque performs two types of cleanup.

## Responsibility 1 — Remove expired indices

Only the previous `k` positions can be used.

For current index `i`, a previous index `j` is valid when:

```text
i - j <= k
```

Therefore:

```text
j >= i - k
```

If:

```text
dq[0] < i - k
```

the index is too old.

Remove it:

```python
dq.popleft()
```

---

## Responsibility 2 — Remove dominated DP values

Before adding `i`, maintain decreasing DP values:

```python
while dq and dp[dq[-1]] <= dp[i]:
    dq.pop()
```

The current index has a DP score at least as good as the old candidate and will expire later.

Therefore the old candidate is useless.

---

# 12. The DP Invariant

The most important invariant is:

> Before calculating `dp[i]`, the deque contains only reachable previous indices in the range `[i-k, i-1]`, and their DP values are monotonically decreasing.

Therefore:

```text
dp[dq[0]]
```

is always:

```text
maximum dp value among all legal previous positions
```

This gives the recurrence in O(1).

---

# 13. ELI10 Version of the Deque

Imagine the previous `k` positions are competing for the right to be the parent of the current position.

Only one thing matters:

```text
Who has the highest score?
```

Suppose candidates are:

```text
index 2 → score 5
index 3 → score 9
index 4 → score 4
```

We keep:

```text
[9, 4]
```

if index `3` dominates index `2`.

Then a new candidate with score `10` arrives:

```text
[9, 4]
```

becomes:

```text
[10]
```

because `10` is:

* better;
* newer.

This is exactly what the monotonic deque does.

---

# 14. Why This Is DP + Monotonic Deque

The two concepts have distinct responsibilities.

### DP

Determines:

```text
What is the best score at each index?
```

### Monotonic deque

Efficiently determines:

```text
What is the best previous DP state?
```

Together:

```text
DP
 ↓
Need max of previous k states
 ↓
Sliding-window maximum
 ↓
Monotonic deque
 ↓
O(n)
```

---

# 15. Why We Do Not Need a Separate Sliding Window Variable

The current index `i` automatically defines the valid range:

```text
[i-k, i-1]
```

So expiration is based on:

```python
i - k
```

The deque itself tracks the candidates.

---

# 16. Initialization

We start at index `0`.

There is no previous position.

Therefore:

```text
dp[0] = nums[0]
```

And initially:

```text
deque = [0]
```

Then for:

```text
i = 1
```

the best previous state is simply:

```text
dp[0]
```

---

# 17. Example DP Calculation

Take:

```text
nums = [1, -1, -2, 4]
k = 2
```

Start:

```text
dp[0] = 1
```

For index `1`:

Previous valid positions:

```text
[0]
```

Therefore:

```text
dp[1] = nums[1] + dp[0]
      = -1 + 1
      = 0
```

For index `2`:

Previous valid positions:

```text
[0, 1]
```

Their DP values:

```text
1, 0
```

Maximum:

```text
1
```

Therefore:

```text
dp[2] = -2 + 1
      = -1
```

For index `3`:

Previous valid positions:

```text
[1, 2]
```

Their DP values:

```text
0, -1
```

Maximum:

```text
0
```

Therefore:

```text
dp[3] = 4 + 0
      = 4
```

Answer:

```text
4
```

---

# 18. Why Greedy Alone Does Not Work

You cannot simply choose the largest `nums[i]`.

Example:

```text
nums = [10, -100, 50]
k = 2
```

You need to consider:

```text
10 → 50
```

rather than blindly maximizing every immediate jump.

The optimal choice depends on the **accumulated score**, which is exactly why DP is required.

---

# 19. Why BFS Is Not the Right Tool

This is technically a graph-like jump problem:

```text
0 → 1,2,...
```

But the goal is not:

```text
minimum number of jumps
```

Instead, it is:

```text
maximum accumulated score
```

Edges do not represent equal-cost movement in the objective.

Therefore:

```text
BFS ❌
```

The natural formulation is:

```text
DP ✅
```

with deque optimization.

---

# 20. Why a Heap Could Work

We could maintain the maximum DP value using a max-heap.

That would give approximately:

```text
O(n log k)
```

But the monotonic deque takes advantage of the fact that:

* indices expire from the left;
* dominated candidates can be permanently removed.

Therefore:

```text
Heap:
O(n log k)

Monotonic deque:
O(n)
```

The deque is the optimal pattern here.

---

# 21. Complexity Derivation

### DP values

We calculate one DP value for every index:

```text
O(n)
```

### Deque insertions

Each index enters once:

```text
O(n)
```

### Deque removals

Each index leaves at most once:

```text
O(n)
```

Therefore:

```text
O(n) + O(n) + O(n)
=
O(n)
```

Space:

```text
dp array = O(n)
deque    = O(k)
```

Total:

```text
O(n)
```

If we needed only the final score, some DP storage can potentially be optimized, but the standard LeetCode solution keeps the DP array for clarity.

---

# 22. Recognition Rules

When you see:

```text
Maximum score
+
current state depends on previous k states
+
transition contains max/min
```

think:

```text
DP
 ↓
Sliding Window Maximum/Minimum
 ↓
Monotonic Deque
```

Strong signals:

| Problem clue                              | Recognition        |
| ----------------------------------------- | ------------------ |
| `dp[i] = value + max(previous k dp)`      | Monotonic deque    |
| `dp[i] = value + min(previous k dp)`      | Increasing deque   |
| Only last `k` states matter               | Sliding DP window  |
| Need O(n) instead of O(nk)                | Deque optimization |
| Previous states expire                    | Queue/deque        |
| Better state dominates older weaker state | Monotonic deque    |

---

# ⚙️ ALGORITHM — STEP-BY-STEP

```text
Step 1 → Let dp[i] represent the maximum score
         obtainable when reaching index i.

Step 2 → Initialize:

         dp[0] = nums[0]

Step 3 → Put index 0 into a decreasing deque.

         The deque stores candidate indices.

Step 4 → For every index i from 1 to n - 1:

         A. Remove indices from the front that
            are outside the jump range.

            Remove while:

            dq[0] < i - k

         B. The front now contains the index
            with the maximum valid dp value.

         C. Calculate:

            dp[i] = nums[i] + dp[dq[0]]

         D. Remove dominated candidates from
            the back.

            While:

            dp[dq[-1]] <= dp[i]

            remove dq[-1].

         E. Add index i to the deque.

Step 5 → After processing all indices,
         return dp[n - 1].
```

---

# 🔹 BLOCK 2 — EFFICIENT CODE

```python
from collections import deque


class Solution:

    def maxResult(self, nums, k):

        n = len(nums)

        # dp[i] = maximum score when reaching index i
        dp = [0] * n

        # Starting position
        dp[0] = nums[0]

        # Stores candidate indices.
        # dp values remain decreasing.
        dq = deque([0])

        for i in range(1, n):

            # -----------------------------------------
            # 1. Remove indices outside jump range
            # -----------------------------------------

            while dq and dq[0] < i - k:
                dq.popleft()

            # -----------------------------------------
            # 2. Best previous DP state is at front
            # -----------------------------------------

            dp[i] = nums[i] + dp[dq[0]]

            # -----------------------------------------
            # 3. Remove dominated candidates
            # -----------------------------------------

            while dq and dp[dq[-1]] <= dp[i]:
                dq.pop()

            # -----------------------------------------
            # 4. Add current index
            # -----------------------------------------

            dq.append(i)

        return dp[n - 1]
```

---

## Complexity Analysis

Let:

```text
n = len(nums)
```

### DP computation

There is one calculation per index:

```text
O(n)
```

### Deque operations

Each index:

```text
enters deque once
leaves deque at most once
```

Therefore:

```text
O(n)
```

Total:

```text
O(n)
```

### Space

DP array:

```text
O(n)
```

Deque:

```text
O(k)
```

Therefore:

```text
O(n + k)
```

Since:

```text
k <= n
```

we can simplify this to:

```text
O(n)
```

### Final Complexity

```text
Time  = O(n)
Space = O(n)
```

---

## Interview Justification

A strong answer:

> “I define `dp[i]` as the maximum score obtainable when reaching index `i`. The recurrence is `dp[i] = nums[i] + max(dp[j])` for `j` in `[i-k, i-1]`. A naive implementation scans up to `k` previous states for every index, giving O(nk). Since this transition is a sliding-window maximum over DP states, I maintain the candidate indices in a decreasing monotonic deque. The front always contains the best reachable previous state, and each index enters and leaves once, reducing the complexity to O(n).”

---

# 🔹 BLOCK 3 — FULL CODE + DETAILED DRY RUN

## Full Runnable Python Code

```python
from collections import deque


class Solution:

    def maxResult(self, nums, k):

        n = len(nums)

        # -----------------------------------------
        # DP array
        # -----------------------------------------

        dp = [0] * n

        # Starting position
        dp[0] = nums[0]

        # -----------------------------------------
        # Monotonic decreasing deque
        #
        # Front = index with maximum dp value
        # among currently reachable positions.
        # -----------------------------------------

        dq = deque([0])

        # -----------------------------------------
        # Process every position
        # -----------------------------------------

        for i in range(1, n):

            # -------------------------------------
            # Remove expired indices.
            #
            # We can jump at most k positions.
            # -------------------------------------

            while dq and dq[0] < i - k:
                dq.popleft()

            # -------------------------------------
            # Best previous state is at front.
            # -------------------------------------

            dp[i] = nums[i] + dp[dq[0]]

            # -------------------------------------
            # Remove dominated DP states.
            # -------------------------------------

            while dq and dp[dq[-1]] <= dp[i]:
                dq.pop()

            # -------------------------------------
            # Add current state.
            # -------------------------------------

            dq.append(i)

        return dp[n - 1]


# -----------------------------------------
# Example
# -----------------------------------------

nums = [1, -1, -2, 4, -7, 3]
k = 2

solution = Solution()

result = solution.maxResult(nums, k)

print("Maximum Score:", result)
```

### Output

```text
Maximum Score: 7
```

---

# Example Tree of Possible Jumps

For:

```text
nums = [1, -1, -2, 4, -7, 3]
k = 2
```

possible movement looks like:

```text
0 ─────→ 1 ─────→ 2 ─────→ 3 ─────→ 4 ─────→ 5
│         │         │         │         │
└──────→ 2         3         4         5
```

At every position, you may jump:

```text
+1
```

or:

```text
+2
```

---

# Step-by-Step DP Calculation

## Index 0

```text
nums[0] = 1
```

Therefore:

```text
dp[0] = 1
```

Deque:

```text
[0]
```

DP:

```text
[1]
```

---

## Index 1

Current value:

```text
nums[1] = -1
```

Valid previous positions:

```text
0
```

Best previous DP:

```text
dp[0] = 1
```

Therefore:

```text
dp[1] = -1 + 1
      = 0
```

Now compare:

```text
dp[0] = 1
dp[1] = 0
```

No domination.

Deque:

```text
[0, 1]
```

DP:

```text
[1, 0]
```

---

## Index 2

Current:

```text
nums[2] = -2
```

Valid previous indices:

```text
0, 1
```

Deque:

```text
[0, 1]
```

Maximum DP:

```text
dp[0] = 1
```

Therefore:

```text
dp[2] = -2 + 1
      = -1
```

Now:

```text
dp[1] = 0
dp[2] = -1
```

No domination.

Deque:

```text
[0, 1, 2]
```

---

## Index 3

Current:

```text
nums[3] = 4
```

Valid previous indices:

```text
1, 2
```

Index `0` is expired because:

```text
0 < 3 - 2
0 < 1
```

Remove index `0`.

Deque:

```text
[1, 2]
```

Values:

```text
dp[1] = 0
dp[2] = -1
```

Best:

```text
dp[1] = 0
```

Therefore:

```text
dp[3] = 4 + 0
      = 4
```

Now `dp[3] = 4` dominates:

```text
dp[2] = -1
dp[1] = 0
```

Remove both.

Deque:

```text
[3]
```

DP:

```text
[1, 0, -1, 4]
```

---

## Index 4

Current:

```text
nums[4] = -7
```

Valid previous indices:

```text
2, 3
```

Deque currently:

```text
[3]
```

Index `3` is valid.

Therefore:

```text
dp[4] = -7 + dp[3]
      = -7 + 4
      = -3
```

Compare:

```text
dp[3] = 4
dp[4] = -3
```

`4` is still better.

Deque:

```text
[3, 4]
```

---

## Index 5

Current:

```text
nums[5] = 3
```

Valid previous indices:

```text
3, 4
```

Deque:

```text
[3, 4]
```

Best:

```text
dp[3] = 4
```

Therefore:

```text
dp[5] = 3 + 4
      = 7
```

Now:

```text
dp[5] = 7
```

dominates:

```text
dp[4] = -3
dp[3] = 4
```

Remove both.

Deque:

```text
[5]
```

Final:

```text
dp = [1, 0, -1, 4, -3, 7]
```

Answer:

```text
dp[5] = 7
```

---

# Detailed Dry-Run Table

| `i` | `nums[i]` | Valid previous indices | Best previous DP | `dp[i]` | Deque after processing |
| --: | --------: | ---------------------- | ---------------: | ------: | ---------------------- |
|   0 |         1 | —                      |                — |   **1** | `[0]`                  |
|   1 |        -1 | `[0]`                  |                1 |   **0** | `[0,1]`                |
|   2 |        -2 | `[0,1]`                |                1 |  **-1** | `[0,1,2]`              |
|   3 |         4 | `[1,2]`                |                0 |   **4** | `[3]`                  |
|   4 |        -7 | `[2,3]`                |                4 |  **-3** | `[3,4]`                |
|   5 |         3 | `[3,4]`                |                4 |   **7** | `[5]`                  |

Final:

```text
dp = [1, 0, -1, 4, -3, 7]

answer = 7
```

---

# Why the Deque Changed So Dramatically at Index 3

This is worth understanding deeply.

Before index `3`:

```text
dp values:

index 0 → 1
index 1 → 0
index 2 → -1
```

Deque:

```text
[0, 1, 2]
```

Then:

```text
dp[3] = 4
```

Now:

```text
4 > 1
4 > 0
4 > -1
```

And index `3` is newer.

Therefore every previous candidate is dominated.

So:

```text
[0,1,2]
```

becomes:

```text
[3]
```

This is exactly why the deque can stay small.

---

# 🔹 BLOCK 4 — INTERVIEW Q&A

## Q1. What is the DP recurrence?

**Answer:**

Let:

```text
dp[i]
```

be the maximum score obtainable when reaching index `i`.

Since we can jump at most `k` positions:

```text
dp[i] = nums[i] + max(dp[j])
```

where:

```text
i-k <= j < i
```

The initial state is:

```text
dp[0] = nums[0]
```

---

## Q2. Why is the naive DP O(nk)?

For every index `i`, we inspect up to `k` previous DP states:

```text
dp[i-k], ..., dp[i-1]
```

Therefore:

```text
n indices × k candidates
=
O(nk)
```

The monotonic deque reduces the maximum lookup to amortized O(1).

---

## Q3. Why does the deque store indices instead of DP values?

We need indices for two reasons:

### 1. Expiration

We need to determine whether:

```text
index < i-k
```

### 2. Retrieve DP value

The actual value is:

```python
dp[index]
```

Therefore indices are necessary.

---

## Q4. Why is the deque decreasing by DP value?

We need:

```text
maximum dp
```

at the front.

Therefore:

```text
dp[dq[0]]
>=
dp[dq[1]]
>=
dp[dq[2]]
```

The front is always the best candidate.

---

## Q5. Why can we remove a smaller DP state from the back?

Suppose:

```text
old index = j
new index = i
```

where:

```text
j < i
```

and:

```text
dp[j] <= dp[i]
```

For future positions, `i` is:

* at least as good in score;
* newer;
* therefore able to remain usable at least as long.

So `j` can never provide a better transition.

Hence:

```python
dq.pop()
```

is safe.

---

## Q6. Why do we remove expired indices before calculating `dp[i]`?

Because the jump constraint is:

```text
i - j <= k
```

Therefore:

```text
j >= i-k
```

Any index:

```text
j < i-k
```

cannot reach `i`.

Using it would violate the problem's jump constraint.

---

## Q7. Could we use a max-heap instead?

Yes.

A heap can maintain the largest DP state among recent positions.

But it costs:

```text
O(log k)
```

per insertion/removal.

Therefore:

```text
Heap:
O(n log k)
```

whereas:

```text
Monotonic deque:
O(n)
```

The deque is better because expired and dominated candidates can be removed deterministically.

---

## Q8. Why isn't this BFS?

Although each index can be viewed as a node with edges to the next `k` positions, the objective is:

```text
maximize accumulated score
```

not:

```text
minimize number of edges
```

BFS is naturally suited to shortest paths in unweighted graphs.

Here the problem is better represented as:

```text
DP
```

with a sliding-window maximum optimization.

---

## Q9. What if the recurrence required a minimum instead?

Suppose the recurrence were:

```text
dp[i] = nums[i] + min(previous k dp values)
```

Then we would use an **increasing monotonic deque**:

```python
while dq and dp[dq[-1]] >= dp[i]:
    dq.pop()
```

So:

```text
Maximum DP transition
→ decreasing deque

Minimum DP transition
→ increasing deque
```

---

## Q10. What is the connection between LC 1696 and LC 239?

This is one of the most important interview connections.

LC 239:

```text
max(nums[i-k+1 ... i])
```

LC 1696:

```text
max(dp[i-k ... i-1])
```

They are structurally identical.

The only difference is that LC 1696 applies the sliding-window maximum to **DP states** instead of raw array values.

---

# 🧠 PATTERN EXTRACTION

The complete progression is:

```text
LC 239
Sliding Window Maximum
        ↓
Monotonic Deque
        ↓
LC 1438
Maximum + Minimum
        ↓
Two Monotonic Deques
        ↓
LC 862
Prefix Sum + Deque
        ↓
LC 1696
DP + Deque
```

The deeper abstraction is:

> **A monotonic deque is a general optimization tool whenever a state transition repeatedly asks for the maximum or minimum over a moving range.**

---

# 🧩 MASTER TEMPLATE

## DP + Maximum Monotonic Deque

```python
from collections import deque


def dp_with_monotonic_deque(nums, k):

    n = len(nums)

    dp = [0] * n

    dp[0] = nums[0]

    dq = deque([0])

    for i in range(1, n):

        # Remove states that are too old.
        while dq and dq[0] < i - k:
            dq.popleft()

        # Best previous state.
        dp[i] = nums[i] + dp[dq[0]]

        # Remove dominated states.
        while dq and dp[dq[-1]] <= dp[i]:
            dq.pop()

        # Add current state.
        dq.append(i)

    return dp[n - 1]
```

The conceptual template is:

```text
1. Define DP state.
2. Write the recurrence.
3. Identify max/min over previous K states.
4. Recognize sliding-window optimization.
5. Maintain candidate indices in a monotonic deque.
6. Remove expired states.
7. Remove dominated states.
8. Use deque front for optimal transition.
9. Compute current DP.
10. Continue.
```

---

# 🎯 SENIOR PATTERN RECOGNITION

The strongest recognition signal is:

```text
dp[i]
=
something
+
max/min(dp[j])
```

where:

```text
j belongs to a moving window of size K
```

Immediately think:

```text
DP
 ↓
Sliding Window Transition
 ↓
Monotonic Deque
```

### Maximum version

```text
dp[i] = value + max(dp[i-k ... i-1])
```

Use:

```text
DECREASING DEQUE
```

### Minimum version

```text
dp[i] = value + min(dp[i-k ... i-1])
```

Use:

```text
INCREASING DEQUE
```

---

# The Queue/Deque Mastery Chain

You have now completed the entire conceptual progression:

```text
LEVEL 1
QUEUE FUNDAMENTALS
        ↓
LC 933
LC 622
LC 225

LEVEL 2
BASIC BFS
        ↓
LC 1971
LC 1091

LEVEL 3
MULTI-SOURCE BFS
        ↓
LC 994
LC 542
LC 1162

LEVEL 4
LEVEL-ORDER BFS
        ↓
LC 102
LC 199

LEVEL 5
IMPLICIT STATE BFS
        ↓
LC 752

LEVEL 6
STATE TRANSFORMATION BFS
        ↓
LC 127
LC 433

LEVEL 7
TREE → GRAPH
        ↓
LC 863

LEVEL 8
MONOTONIC DEQUE
        ↓
LC 239

LEVEL 9
MULTIPLE MONOTONIC DEQUES
        ↓
LC 1438

LEVEL 10
PREFIX SUM + MONOTONIC DEQUE
        ↓
LC 862

LEVEL 11
DP + MONOTONIC DEQUE
        ↓
LC 1696
```

---

# 📈 PROGRESS UPDATE

```text
LEVEL 11 — DP + MONOTONIC DEQUE

└── ✅ LC 1696 — Jump Game VI
```

Your complete Queue/Deque roadmap is now:

```text
LEVEL 1 — QUEUE FUNDAMENTALS
├── ✅ LC 933
├── ✅ LC 622
└── ✅ LC 225

LEVEL 2 — BASIC BFS
├── ✅ LC 1971
└── ✅ LC 1091

LEVEL 3 — MULTI-SOURCE BFS
├── ✅ LC 994
├── ✅ LC 542
└── ✅ LC 1162

LEVEL 4 — LEVEL-ORDER BFS
├── ✅ LC 102
└── ✅ LC 199

LEVEL 5 — IMPLICIT STATE BFS
└── ✅ LC 752

LEVEL 6 — STATE TRANSFORMATION BFS
├── ✅ LC 127
└── ✅ LC 433

LEVEL 7 — TREE → GRAPH
└── ✅ LC 863

LEVEL 8 — MONOTONIC DEQUE
└── ✅ LC 239

LEVEL 9 — MULTIPLE MONOTONIC DEQUES
└── ✅ LC 1438

LEVEL 10 — PREFIX SUM + MONOTONIC DEQUE
└── ✅ LC 862

LEVEL 11 — DP + MONOTONIC DEQUE
└── ✅ LC 1696
```

# One-Line Takeaway

> **When a DP recurrence needs the maximum or minimum of the previous `K` DP states, recognize it as a sliding-window optimization and use a monotonic deque to reduce an `O(nk)` DP to `O(n)`.**

Would you like to continue with a full-depth problem that uses the minimum version of this pattern, or stay with maximum-based DP for one more example?


