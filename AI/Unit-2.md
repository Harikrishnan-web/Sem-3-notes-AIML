# Unit-2 Problem Solving

---

# **1. Informed Search Algorithms**

---

## **1.1 Introduction to Informed Search Algorithms**

Informed search algorithms are an improvement over uninformed search algorithms.

* Uninformed search algorithms search the entire search space without any additional knowledge.
* Informed search algorithms use **extra knowledge** such as:

  * Distance from the goal
  * Path cost
  * Information on how to reach the goal node
* This knowledge helps the agent:

  * Explore fewer nodes
  * Reach the goal more efficiently
* These algorithms are very useful for **large search spaces**
* Since they use heuristics, they are also called **heuristic search algorithms**

---

## **1.2 Heuristic Search**

### **Heuristic Function**

* A heuristic is a function used in informed search
* It finds the **most promising path**
* It takes the **current state** as input
* It produces an **estimate of how close the agent is to the goal**
* Represented as:

```
h(n)
```

Where:

* `n` is the current node
* `h(n)` estimates the cost of the optimal path from `n` to the goal
* The value of `h(n)` is always **positive**

### **Properties**

* Heuristic methods may not always give the best solution
* They guarantee a **good solution in reasonable time**
* Heuristic function estimates closeness to the goal

---

## **1.3 Admissibility of Heuristic Function**

A heuristic is admissible if:

```
h(n) ≤ h*(n)
```

Where:

* `h(n)` = heuristic cost
* `h*(n)` = estimated (actual optimal) cost

This means:

* Heuristic cost should be **less than or equal to** the actual cost

---

## **1.4 Pure Heuristic Search**

Pure heuristic search is the **simplest form** of heuristic search.

### **Characteristics**

* Nodes are expanded based only on `h(n)`
* Uses two lists:

  * **OPEN list** → nodes not yet expanded
  * **CLOSED list** → nodes already expanded

### **Working**

* Select node with lowest heuristic value
* Expand it
* Move it to CLOSED list
* Add successors to OPEN list
* Continue until goal state is found

---

## **1.5 Types of Informed Search Algorithms**

Two main informed search algorithms are discussed:

1. **Best First Search (Greedy Search)**
2. **A* Search Algorithm**

---

## **1.6 Best-First Search Algorithm (Greedy Search)**
<img src="Sources/BFS 1.png" alt="A screenshot" width="400" height="200">
### **Definition**

* Always selects the path that appears best at the moment
* Combines features of **DFS** and **BFS**
* Uses heuristic function to guide search

### **Evaluation Function**

```
f(n) = h(n)
```

Where:

* `h(n)` = estimated cost from node `n` to the goal

### **Implementation**

* Implemented using a **priority queue**

---

### **Algorithm (Steps)**

1. Place the starting node in the OPEN list
2. If OPEN list is empty, stop and return failure
3. Remove node `n` from OPEN with lowest `h(n)` and place it in CLOSED
4. Expand node `n` and generate successors
5. If any successor is goal, return success
6. Otherwise:

   * Evaluate successors
   * Add unvisited nodes to OPEN list
7. Repeat from Step 2

<img src="Sources/BFS 2.png" alt="A screenshot" width="400" height="200">
---

### **Advantages**

* Combines benefits of BFS and DFS
* More efficient than BFS and DFS

---

### **Disadvantages**

* Can behave like DFS in worst case
* Can get stuck in loops
* Not optimal

---

### **Example (Greedy Best-First Search)**

* Nodes expanded using `f(n) = h(n)`
* Uses OPEN and CLOSED lists

Final solution path:

```
S → B → F → G
```

---

### **Complexity**

* **Time Complexity:** `O(b^m)`
* **Space Complexity:** `O(b^m)`
* `b` = branching factor
* `m` = maximum depth

---

### **Properties**

* **Complete:** No
* **Optimal:** No

---

## **1.7 A* Search Algorithm**

### **Definition**

* Most commonly known form of best-first search
* Uses:

  * Heuristic function `h(n)`
  * Cost to reach node `g(n)`
* Combines features of:

  * Uniform Cost Search
  * Greedy Best-First Search

---

### **Evaluation Function**

```
f(n) = g(n) + h(n)
```

Where:

* `g(n)` = cost from start to node `n`
* `h(n)` = estimated cost to goal

---

### **Characteristics**

* Expands fewer nodes
* Finds shortest path
* Terminates when goal node is found

---

### **Algorithm (Steps)**

1. Place starting node in OPEN list
2. If OPEN list is empty, return failure
3. Select node with smallest `f(n)`

   * If it is goal, return success
4. Expand node and generate successors
5. For each successor:

   * Compute evaluation function
   * Add or update OPEN list
6. Move expanded node to CLOSED
7. Repeat from Step 2

---

### **Example (A* Search)**

Using `f(n) = g(n) + h(n)`

Final optimal path:

```
S → A → C → G
```

Cost:

```
6
```

---

### **Points to Remember**

* Returns first occurring path
* Does not search remaining paths
* Efficiency depends on heuristic quality
* Expands nodes satisfying:

```
f(n) ≤ f(goal)
```

---

### **Completeness**

A* is complete if:

* Branching factor is finite
* Cost of every action is fixed

---

### **Optimality Conditions**

A* is optimal if:

1. Heuristic is **admissible**
2. Heuristic is **consistent** (for graph search)

---

### **Advantages**

* Optimal
* Complete
* Solves complex problems

---

### **Disadvantages**

* High memory requirement
* Stores all generated nodes
* Not practical for very large problems

---

### **Complexity**

* **Time Complexity:** `O(b^d)`
* **Space Complexity:** `O(b^d)`
* `d` = depth of solution

---

## **Final Result**

* Informed search uses heuristics to guide search
* Greedy Best-First Search is fast but not optimal
* A* Search is optimal and complete when conditions are met
* Heuristic quality directly affects performance

---