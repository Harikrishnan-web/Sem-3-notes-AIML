**UNIT II – PROBLEM SOLVING**
**Topic 1: Informed Search Algorithms**

---

## 1. Informed Search Algorithms

### 1.1 Introduction

Informed search algorithms improve upon uninformed (blind) search methods by using **additional knowledge** about the problem domain.
This knowledge helps the agent decide **which node to expand next**, thereby reducing the size of the search space explored.

**Key idea:**
Instead of searching blindly, the algorithm uses an estimate of how close a state is to the goal.

**Also called:** Heuristic Search

**Why needed:**

* Uninformed search explores all possible paths
* Inefficient for large search spaces
* Informed search is faster and more practical

---

## 1.2 Heuristic Search

### Definition

A **heuristic** is a rule or function that guides the search toward the goal by estimating how close a state is to the goal.

### Heuristic Function

* Represented as **h(n)**
* Input: current state `n`
* Output: estimated cost to reach the goal from `n`
* Always **non-negative**

**Meaning:**
“How far am I from the goal?”

### Properties

* Heuristic may not give the best solution always
* Guarantees a *good* solution in reasonable time
* Crucial for large and complex problems

---

## 1.3 Admissible Heuristic

A heuristic is **admissible** if it never overestimates the true cost.

### Condition

```
h(n) ≤ h*(n)
```

Where:

* `h(n)` = heuristic estimated cost
* `h*(n)` = actual optimal cost to reach the goal

**Importance:**

* Required for optimality in A* search
* Ensures solution quality

---

## 1.4 Pure Heuristic Search

### Concept

* Simplest heuristic-based search
* Uses **only heuristic value h(n)** to expand nodes

### Data Structures

* **OPEN list** → nodes yet to be expanded
* **CLOSED list** → nodes already expanded

### Working

1. Choose node with **lowest h(n)**
2. Expand it
3. Move it to CLOSED list
4. Add successors to OPEN list
5. Repeat until goal is found

### Limitation

* Ignores path cost
* Not guaranteed optimal

---

## 1.5 Types of Informed Search Algorithms

Two major informed search algorithms:

1. **Greedy Best-First Search**
2. **A* Search**

---

## 1.6 Greedy Best-First Search (Best-First Search)

### Idea

Always expand the node that **appears closest to the goal**.

### Evaluation Function

```
f(n) = h(n)
```

Only heuristic value is considered.

### Nature

* Combines ideas of DFS and BFS
* Implemented using a **priority queue**

---

### Algorithm (Child-Friendly Explanation)

1. Put the start node in OPEN
2. If OPEN is empty → failure
3. Pick the node with smallest `h(n)`
4. Move it to CLOSED
5. Generate its children
6. If any child is the goal → success
7. Otherwise, add unexplored children to OPEN
8. Repeat

---

### Advantages

* Faster than BFS and DFS
* Uses guidance from heuristic
* Efficient in many cases

---

### Disadvantages

* Can behave like DFS in worst case
* Can get stuck in loops
* **Not optimal**
* **Not complete**

---

### Example (Greedy Best-First)

* Nodes expanded based only on `h(n)`
* Final path found:

```
S → B → F → G
```

---

### Complexity

* **Time Complexity:** `O(b^m)`
* **Space Complexity:** `O(b^m)`
* `b` = branching factor
* `m` = maximum depth

---

### Properties

* **Complete:** ❌ No
* **Optimal:** ❌ No

---

## 1.7 A* Search Algorithm

### Idea

A* combines:

* Actual cost from start
* Estimated cost to goal

### Evaluation Function

```
f(n) = g(n) + h(n)
```

Where:

* `g(n)` = cost from start to node `n`
* `h(n)` = heuristic estimate to goal

---

### Characteristics

* Combines **Uniform Cost Search** and **Greedy Search**
* Expands fewer nodes
* Produces optimal solution (with admissible heuristic)

---

### Algorithm (Very Simple Explanation)

1. Put start node in OPEN
2. If OPEN is empty → failure
3. Pick node with smallest `f(n)`
4. If it is goal → success
5. Expand node
6. For each child:

   * Compute `f(n)`
   * Add/update in OPEN
7. Move expanded node to CLOSED
8. Repeat

---

### Example (A*)

Using `f(n) = g(n) + h(n)`:

Final optimal path:

```
S → A → C → G
```

**Total cost = 6**

---

### Important Points

* Returns the first optimal path found
* Does not explore all paths
* Performance depends heavily on heuristic quality
* Expands nodes where:

```
f(n) ≤ f(goal)
```

---

### Completeness

A* is **complete** if:

* Branching factor is finite
* Step cost is positive and fixed

---

### Optimality Conditions

A* is optimal if:

1. **Admissible heuristic** (never overestimates)
2. **Consistent heuristic** (for graph search)

---

### Advantages

* Complete
* Optimal
* Efficient for complex problems
* Widely used in AI

---

### Disadvantages

* High memory usage
* Stores all generated nodes
* Not practical for very large state spaces
* Performance drops with poor heuristic

---

### Complexity

* **Time Complexity:** `O(b^d)`
* **Space Complexity:** `O(b^d)`
* `d` = depth of optimal solution

---

## 1.8 Comparison Summary

| Feature        | Greedy Best-First | A* Search |
| -------------- | ----------------- | --------- |
| Uses heuristic | Yes               | Yes       |
| Uses path cost | No                | Yes       |
| Complete       | No                | Yes       |
| Optimal        | No                | Yes       |
| Memory usage   | Moderate          | High      |
| Speed          | Fast              | Balanced  |

---

## 1.9 Final Result

* Informed search uses heuristics to guide search
* Greedy search is fast but unreliable
* A* search is the **best informed search algorithm**
* Heuristic quality directly affects performance
* Admissibility is key for optimality

---
