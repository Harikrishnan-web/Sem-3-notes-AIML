# 1. Informed Search Algorithms — DETAILED, EXAM-READY NOTES

---

## What is an informed (heuristic) search?

An **informed search** (aka *heuristic search*) uses extra problem-specific knowledge to guide search toward the goal.
That knowledge is supplied by a **heuristic function** (h(n)) that estimates “how close” node (n) is to a goal. Informed methods explore far fewer states than blind search for large spaces. 

---

## Heuristic function: definition & properties

* **Heuristic (h(n))**: a nonnegative estimate of the cost from node (n) to a goal. It returns a number; lower = “closer” to goal. 
* **Admissible heuristic**: (h(n) \le h^*(n)) for every node (n), where (h^*(n)) is the true least cost from (n) to a goal. Admissibility guarantees A* tree-search optimality. 
* **Consistent (monotone) heuristic**: for every edge ((n, n')) with step cost (c(n,n')),
  (h(n) \le c(n,n') + h(n')). Consistency implies admissibility and simplifies A* graph search (no need to re-open nodes). 

---

## Pure heuristic / best-first idea (intuition)

Pure heuristic search expands the node with the smallest (h(n)). It keeps two lists: **OPEN** (frontier) and **CLOSED** (expanded). On each iteration it removes the OPEN node with minimum (h), expands it, moves it to CLOSED, and adds unseen successors to OPEN. This is the basis of **Greedy Best-First Search**. 

---

## 1. Greedy Best-First Search — detailed + tree + step-by-step

**Evaluation function:** (f(n)=h(n)) (uses heuristic only). Not guaranteed optimal.

### When to pick it

* Use if you need speed and you have a heuristic that roughly points to the goal, and optimality is not required. 

### Step-by-step procedure (graph-search variant)

1. Put Start in OPEN with key (h(Start)). CLOSED = ∅.
2. Repeat while OPEN ≠ ∅:
   a. Remove node (n) from OPEN with smallest (h(n)).
   b. If `Goal(n)` → return solution (reconstruct via parent pointers).
   c. Put (n) in CLOSED.
   d. For each successor (s) of (n): if (s) not in OPEN and not in CLOSED, compute (h(s)) and add (s) to OPEN (store parent pointer).
3. If OPEN empties → failure. 

### Small tree example & expansion order

Tree (heuristics in brackets):

```
        S [7]
     /    |    \
  A[4]   B[6]   C[3]
         |         \
        F[2]       G[0]
```

* OPEN=[S]; pop S → add A,B,C (OPEN sorted by h: C(3),A(4),B(6))
* Pop C (3) → expand → adds G(0) → pop G → Goal found.

### Notes: pros/cons & complexity

* **Pros:** very fast if (h) points well; low thinking overhead.
* **Cons:** incomplete in worst cases, not optimal, can loop or behave like DFS.
* **Complexity (worst):** time/space up to (O(b^m)) where (m) = max depth (practically large). 

---

## 2. A* Search — detailed + tree + step-by-step + proof sketch of optimality

**Evaluation function:**
[
f(n) = g(n) + h(n)
]
where (g(n)) = cost from Start to (n) (exact so far), and (h(n)) = heuristic estimate to goal. A* balances cost so far and estimated remaining cost. 

### When to pick it

* Use A* when you need **optimal** shortest-cost paths and have an admissible heuristic. Widely used in planning, pathfinding, robotics. 

### Step-by-step procedure (graph-search variant)

1. OPEN = priority queue with Start (key (f(Start)=g(Start)+h(Start)=0+h(Start))). CLOSED = ∅.
2. Loop while OPEN not empty:
   a. Remove node (n) with smallest (f(n)) from OPEN.
   b. If `Goal(n)` true → return path and cost (g(n)).
   c. Add (n) to CLOSED.
   d. For each successor (s) of (n): compute tentative (g_s = g(n)+c(n,s)), (f_s = g_s + h(s)).

   * If (s) not in OPEN and not in CLOSED → set parent, g(s)=g_s, insert (s) into OPEN with priority (f_s).
   * Else if (s) is already in OPEN with (g_{\text{old}}>g_s): update parent and decrease key to (f_s).
   * Else if (s) in CLOSED with (g_{\text{old}}>g_s): remove from CLOSED and insert/update in OPEN (graph-search must handle this to maintain optimality unless (h) is consistent).
3. If OPEN empties → failure. 

### Small tree example & iterations

Edge costs + heuristics:

```
S
├─A (cost 1) h(A)=5  => f=1+5=6
└─B (cost 2) h(B)=3  => f=2+3=5
B→G (cost 4) h(G)=0  => total g=6 f=6
A→G (cost 9) h(G)=0  => total g=10 f=10
```

Iterations:

1. OPEN: S(f= h(S)). Expand S → add A(f=6), B(f=5).
2. Pop B(f=5) → expand → add G(g=6,f=6). OPEN now {A(f=6), G(f=6)}.
3. Pop G (tie-break may pick G) → Goal reached with optimal cost 6. 

---

### Proof sketch of A* optimality (tree-search, with admissible (h)):

(Concise, exam-style)

Assume A* returns a goal node (G) with path cost (g(G)). Suppose there exists an optimal goal (G^*) with cost (g^* < g(G)). Let (n) be the first node on the optimal path to (G^*) that is not yet expanded when A* pops (G). Because A* selects nodes by minimum (f), when it popped (G), every node (x) in OPEN had (f(x) \ge f(G) = g(G)). For node (n) on the optimal path,
[
f(n) = g(n) + h(n) \le g(n) + h^*(n) = g^* \quad(\text{since } h \text{ admissible})
]
and because (g(n) \le g^*), we get (f(n) \le g^* < g(G) = f(G)), contradicting that all OPEN nodes had (f \ge f(G)). Therefore no such better (G^*) can exist; A* must have found an optimal path. (Graph-search variant requires consistency to avoid re-opening issues.) 

---

## A*: completeness, optimality, complexity & practical notes

* **Complete:** if branching factor finite and every step cost ≥ ε > 0. 
* **Optimal:** with an **admissible** heuristic for tree-search; for graph-search, heuristic must be **consistent** to avoid re-opening or extra bookkeeping. 
* **Time complexity:** exponential in general; actual nodes expanded depend heavily on heuristic quality — in worst case (O(b^d)).
* **Space complexity:** A* keeps OPEN and CLOSED → often (O(b^d)) memory; this is the main practical limitation for very large problems. 

---

## Comparative evaluation (concise)

| Criterion |          Greedy Best-First |                                           A* |
| --------- | -------------------------: | -------------------------------------------: |
| Uses (g)? |              No (only (h)) |                                  Yes ((g+h)) |
| Optimal?  |                         No |                    Yes (with admissible (h)) |
| Complete? |             Not guaranteed | Yes (with finite branching & positive costs) |
| Speed     | Often faster (if (h) good) |         Slower than greedy but finds optimal |
| Memory    |               Can be large |  Usually larger (stores all generated nodes) |

---

## Design & implementation tips (quick checklist)

* Use **graph-search** (OPEN/CLOSED) when states repeat; ensure handling of improved (g)-values (re-open or maintain consistent heuristic). 
* Choose **heuristic** carefully: admissible and as close as possible to true cost (more informed → fewer expansions). 
* Tie-breaking: prefer larger (g) or smaller (h) depending on whether you want deeper or cheaper solutions first.
* If memory is prohibitive, consider memory-saving variants (IDA*, SMA*, or iterative deepening on (f)-cost). (Textbook notes discuss practical workarounds.) 

---

## Example exam questions (and one-line model answers)

* **Define heuristic search.**
  *Answer:* A search that uses a heuristic function (h(n)) providing extra knowledge (estimate to goal) to guide the search. 
* **Define A* search.**
  *Answer:* A best-first search using (f(n)=g(n)+h(n)) that is optimal with an admissible heuristic. 
* **Give proof sketch of A* optimality.**
  *Answer:* (Use the admissibility contradiction argument above — see the proof sketch.) 

---

## Sources (from your PDF)

Material and examples in these notes are taken and distilled from your uploaded lecture material on Informed Search Algorithms (Greedy best-first, A*, heuristics, proofs, examples). See the PDF sections on Informed Search, Greedy Best-First, and A* for the original wording and iteration examples.

---
# 2. Local Search and Optimization Problems — DETAILED, STEP-BY-STEP, EXAM-READY NOTES

---

## Quick overview (one line)

**Local search** methods move from a single current state to neighbouring states to **find high-quality solutions** (optimization) while keeping **very little memory** — ideal for huge or continuous search spaces. 

---

## 2.1 Core idea & landscape metaphor

* **State-space landscape:** each state = point; objective/fitness = elevation. Goal = global maximum (or minimum for cost). Hill-climbing = climb to a peak; gradient descent = go down to a valley. 

Simple landscape picture (conceptual):

```
   peak (global)
     /\
    /  \
---/----\---  plateau
  /      \
 S        local peak (local maximum)
```

---

## 2.2 Hill-Climbing family — basics

**Basic hill-climbing algorithm (general):**

1. Start with a state S (often random).
2. Generate neighbors of current state.
3. If any neighbor has higher value, move to the best neighbor (or choose probabilistically depending on variant).
4. Repeat until no improvement (stuck at a peak). 

**Properties:** very low memory (keeps just current state), fast local improvements, but **not systematic** — can miss large regions of space. 

---

## 2.3 Variants of hill-climbing (what they do and step-by-step)

### A. Simple (greedy) hill-climbing (also called steepest-ascent)

* **Step-by-step:**

  1. Evaluate all neighbors.
  2. Move to neighbor with **highest** objective (if strictly better).
  3. Stop when no neighbor improves the objective.
* **Pros:** fast progress when neighbor improvements exist.
* **Cons:** gets stuck at **local maxima**, **ridges**, **plateaus**.

### B. Stochastic hill-climbing

* **Step-by-step:**

  1. Generate set of uphill neighbors.
  2. Choose one at random (possibly weighted by steepness).
* **When to use:** when many neighbors; increases diversity and sometimes finds better peaks. 

### C. First-choice hill-climbing

* **Step-by-step:**

  1. Generate neighbors randomly until you find one that is better; immediately move there.
* **Advantage:** efficient when branching factor huge (don’t evaluate all neighbors). 

### D. Random-restart hill-climbing

* **Step-by-step:**

  1. Repeat: pick random start → run hill-climbing → if goal/acceptable solution found stop else restart.
* **Key point:** makes hill-climbing **complete with probability 1** (eventual success probability → 1 over many restarts). Expected restarts ≈ 1/p where p = success probability of one run. Example: for 8-queens p ≈ 0.14 → ~7 restarts expected.

### E. Allowing sideways moves

* Permit moves that do not improve value (helps escape plateaus/shoulders), possibly with a limit on consecutive sideways moves to avoid infinite wandering. Significantly increases success rate in many problems (8-queens example improved from 14% → 94%). 

---

## 2.4 Common problems of hill-climbing (what they are and how they trap search)

* **Local maxima:** a peak higher than its neighbors but below global maximum — hill-climbing stops here. 
* **Ridges:** sequence of local maxima separated so that direct neighbor moves go downhill; greedy moves fail to follow a ridge without complex moves. 
* **Plateaus:** flat regions with no gradient; search wanders and may stall (could be a shoulder allowing escape or a flat local maximum — ambiguous). 

Illustration (conceptual):

```
 local max    plateau    ridge
   /\          ____     / / / 
  /  \        /    \   / / /
 /    \______/      \_/ / /
S
```

**Fixes:** stochastic moves, sideways moves with limits, random restarts, simulated annealing, beam/genetic methods.

---

## 2.5 Simulated Annealing (detailed, with math & schedule)

**Idea:** combine hill-climbing with random exploration so occasional downhill moves allow escape from local maxima; gradually reduce randomness (temperature) to converge.

**Algorithm (step-by-step):**

1. Initialize state S and **temperature schedule** T(t) (high initially, slowly decreasing).
2. Repeat until termination:

   * Pick a random neighbor S' of current S.
   * Let Δ = value(S') − value(S) (for minimization use cost difference; sign may invert).
   * If Δ > 0 (improvement) → accept S' unconditionally.
   * Else accept S' with probability (p = e^{\Delta / T}) (if maximizing, Δ negative when worse; use (e^{\Delta/T})).
   * Decrease T according to schedule.
3. Return best state seen.

**Acceptance probability:** (p = e^{\Delta E/T}) (Boltzmann factor); larger negative Δ (worse moves) less likely; higher T allows worse moves early.

**Cooling schedule:** T must decrease slowly enough (e.g., logarithmic schedules) for theoretical guarantee. If cooled **slowly enough**, simulated annealing will find global optimum with probability → 1 (in limit). In practice, practical schedules used trade optimality for speed.

**When to use:** large combinatorial optimization (VLSI, scheduling), continuous optimization where escaping local optima is critical. 

---

## 2.6 Local beam search and stochastic beam search

### Local beam search (k-beam)

* **Step-by-step:**

  1. Start with **k** randomly chosen states.
  2. At each iteration generate **all successors of all k** states.
  3. If any successor is goal → stop. Else select the **k best successors** (by value) to be the new k states.
* **Behavior:** shares information among parallel searches — good searches “attract” resources. 

**Limitation:** lack of diversity — states can cluster in one region and converge to same local peak (becoming k-times slower hill climb). 

### Stochastic beam search

* **Variant:** instead of taking top-k deterministic successors, **sample k** successors **with probability proportional to their fitness** (increases diversity). Works like stochastic hill-climbing but with population. 

---

## 2.7 Evolutionary algorithms (Genetic Algorithms) — detailed

**Metaphor:** population of candidate solutions evolves by selection, crossover (recombination), and mutation — an instance of stochastic beam search with crossover.

**Representation:** individuals encoded as strings (binary, integer, real, or program trees). 

**GA cycle (step-by-step):**

1. **Initialize** population of N individuals (random).
2. **Evaluate** fitness of each individual.
3. **Selection:** pick parents (e.g., fitness-proportionate / tournament selection).
4. **Crossover (recombination):** choose crossover point(s), combine parents’ genes to create offspring (ρ is number of parents; usually 2).
5. **Mutation:** with small probability mutate bits/genes to maintain diversity.
6. **Replacement:** form new population (various schemes: generational, steady-state).
7. Repeat until termination (max generations or fitness threshold).

**Why works:** crossover recombines useful building blocks (schemas). If certain substrings (schemas) have above-average fitness, their instances proliferate — GA exploits this to assemble good solutions. 

**Pros/cons:**

* Pros: explores multiple areas simultaneously, good at combining partial solutions.
* Cons: many hyperparameters (pop size, crossover/mutation rates), can converge prematurely (loss of diversity). 

**Example:** 8-queens encoded as string of 8 numbers (row positions), crossover swaps substrings, mutation randomly moves a queen in a column. 

---

## 2.8 First-choice hill-climbing & random sampling methods

* **First-choice:** generate successors one by one until a better one found → move immediately (saves time for high branching). 
* **Random walk:** purely random neighbor selection — guaranteed to find global optimum eventually (finite space) but very slow. Used sometimes as exploration or in simulated annealing (random moves accepted sometimes).

---

## 2.9 Performance metrics & probabilistic analysis

* **Expected restarts:** if single hill run has success probability p, expected restarts = 1/p. For 8-queens, p ≈ 0.14 (without sideways) → ≈ 7 restarts; with sideways moves p ≈ 0.94 → ~1.06 restarts. Expected total steps computed from success + failure costs.

---

## 2.10 Local search in continuous spaces — gradients & methods

**Context:** states = real-valued vectors (x \in \mathbb{R}^n); objective (f(x)).

### Empirical / discretized approaches

* **Discretize** continuous space (grid) to get finite branching, or **sample** neighbors randomly (small δ moves) — yields empirical gradient (measure fitness difference between nearby points). Steepest-ascent hill-climbing on discretization ≈ empirical gradient ascent. 

### Analytic gradient methods

* **Gradient ascent/descent:** compute gradient (\nabla f(x)), move (x \leftarrow x + \alpha \nabla f(x)) (α = step size). Choice of α critical. 
* **Line search:** pick α by searching along gradient direction (often doubling until decrease). 
* **Newton–Raphson for optimization:** use Hessian matrix (H) to update via (x \leftarrow x - H^{-1}\nabla f(x)) (matrix form) — converges fast near optimum but requires second derivatives and inverse of Hessian; heavy for high dimensions. 

### Issues & fixes

* Same topology problems (local maxima, ridges, plateaus) appear in continuous space. Random restarts and simulated annealing help. High dimensionality complicates search — often empirical gradients and convex optimization tools used when possible.

---

## 2.11 Constrained optimization, linear & convex programming

* **Constrained optimization:** variables must satisfy constraints (e.g., airports inside country, non-lake).
* **Linear programming (LP):** linear objective + linear inequality constraints forming convex polytope → polynomial-time solvable and extremely practical.
* **Convex optimization:** objective convex over convex constraint region → global optimum found efficiently under broad conditions. Many ML/control problems reduce to convex programs. Use appropriate optimization solvers when problem fits this class. 

---

## 2.12 Online local search & learning real-time A* (LRTA*) connections

* **Online local search:** agent must act while learning environment — cannot teleport for restarts. Simple hill-climbing is already online but gets stuck. Random walks help but may be slow. 

* **LRTA***: maintain local cost estimates (H(s)) (initially heuristic h(s)); as agent moves update H(s) based on neighbors and observed costs; select apparently best neighbor using updated costs. This encourages exploration and can escape local traps via updated estimates. LRTA* guaranteed to find goal in finite safely-explorable domains; complexity often much better in practice than naive methods.

---

## 2.13 Practical tips & exam checklist (step-by-step)

1. **Identify problem type:** discrete vs continuous; constrained vs unconstrained; cost vs fitness.
2. **Choose algorithm based on needs:**

   * Very low memory + quick: hill-climbing (with restarts).
   * Need escape local optima: simulated annealing or GA.
   * Need population/combination of building blocks: genetic algorithms / beam search.
   * Continuous differentiable objective: gradient methods (Newton, line search).
3. **Tuning:** step size α, cooling schedule T(t), population size, mutation rate, beam width k — crucial for performance.
4. **Mitigate traps:** allow sideways moves, use stochastic choices, random-restarts, maintain diversity (beam/GA), or adjust acceptance probability (annealing).

---

## 2.14 Short exam-style Q&A (model answers)

* **Define hill-climbing.**
  A local search that keeps a single current state and moves to a neighbor with higher objective until no neighbor is better. 

* **What is simulated annealing?**
  A stochastic hill-climbing method that sometimes accepts worse moves with probability (e^{\Delta/T}); temperature T decreases over time to concentrate on global optima.

* **Give two limitations of local beam search.**

  1. Can lose diversity and cluster into one region (converging to same local maxima). 2. If k too small, may miss other promising regions; if k too large, memory/time blowup. (Stochastic beam alleviates some issues.) 

* **Why use genetic algorithms?**
  They maintain a population, use crossover to combine useful building blocks (schemas), and apply mutation for diversity — effective on many combinatorial optimization tasks.

---

## Sources (from your uploaded PDF)

Content above distilled from the Local Search & Optimization chapter of your PDF (sections on hill-climbing variants, simulated annealing, beam search, evolutionary algorithms, continuous local search, LRTA*, and summary).

---
Below is your **Topic 3: Local Search in Continuous Spaces**, written in **simple, child-friendly, step-by-step explanation**, fully **detailed**, and based **only on the pdf** (all content captured without skipping anything).
**No extra messages.**

---

# **3. Local Search in Continuous Spaces**

(Full detailed explanation, simple, step-by-step)

---

## **1. What is a Continuous Space?**

* A *continuous space* means the agent can move in infinitely many small steps.
* Example: Moving an airport anywhere on a map — you can place it at any coordinate like (1.2, 3.89), not only full-grid positions.
* This makes the branching factor **infinite** — because there are endless possible next states.

Most algorithms like BFS, DFS, A*, etc., **cannot handle infinite branching**, except:

* **First-choice hill climbing**
* **Simulated annealing**

---

## **2. Why Do We Need Local Search Here?**

Because continuous spaces are infinite, we cannot expand all successors.
So we use **local search**, which:

* Looks only at nearby states
* Moves step-by-step
* Uses very little memory
* Works well even when the space is huge

---

## **3. Example Problem (from PDF)**

**Placing 3 airports in Romania such that cities have minimum total distance to nearest airport.**

* A state = 6 numbers

  * (x₁, y₁), (x₂, y₂), (x₃, y₃)
* This is a **6-dimensional** space.
* We want to **minimize** the sum of squared distances:

  * Every city chooses the nearest airport
  * That distance is squared
  * All are added

So:
Higher value = worse solution
Lower value = better solution

---

## **4. Understanding Objective Function f(x)**

Let:

* x = all six coordinates
* Ci = set of cities closest to airport i

Then:
f(x) = Σ (distance(city, nearest airport))²

We can compute this **locally**, meaning:

* If we move airports *slightly*, Ci does not change
* If we move airports *too far*, city assignment changes → Ci must be recalculated.

---

## **5. Two Ways to Search Continuous Spaces**

---

### **A. Method 1: Discretizing the Space**

Instead of infinite choices, we restrict movements:

* Make a rectangular grid
* Grid spacing = δ (delta)
* Each variable (x₁, y₁, …) can be increased or decreased by δ
* Since we have 6 variables, each can go +δ or –δ → **12 successors**

This makes local search possible.

Another option:

* Pick a random direction
* Move by δ
* Check whether objective improves → empirical gradient

This is called an **empirical gradient method**.

---

### **B. Method 2: Using Calculus (Gradient Methods)**

If function f(x) is mathematically nice, we can compute:

* The **gradient ∇f** → tells direction of steepest increase
* For minimization, we move **downhill** (negative direction)
* For maximization, move **uphill**

The gradient vector tells both:

* **Direction**
* **Steepness**

---

## **6. Using Gradient for Steepest Ascent / Descent**

Update rule:

x(new) = x(old) + α ∇f(x)

Where:

* α = step size (small constant)
* If α too small → slow
* If α too big → overshoots, jumps past optimum

To fix this, we use **line search**:

* Keep doubling α
* Stop when f(x) gets worse
* Last good point becomes new state

---

## **7. Newton–Raphson Method**

Sometimes we want the point where **gradient = 0**:

∇f(x) = 0

Newton–Raphson solves equations faster than simple gradient steps.
It uses:

x(new) = x(old) – [Hessian⁻¹ × gradient]

This method uses:

* Gradient
* Curvature of function (Hessian matrix)

It converges much faster but needs more calculations.

---

## **8. Problems in Continuous Landscapes (same as discrete)**

Local search still gets stuck due to:

### **1. Local Maxima / Local Minima**

* You reach a “small hill” or “small valley”
* Cannot escape without random changes

### **2. Ridges**

* Narrow paths where moving straight up is impossible
* Algorithm must zig-zag

### **3. Plateaus**

* Completely flat region
* No gradient → algorithm gets lost

Solutions:

* Random restarts
* Simulated annealing

---

## **9. Challenges in High Dimensions**

* Continuous spaces with many variables are huge
* Easy to get lost
* Hard to visualize
* Algorithms need careful tuning

---

## **10. Constrained Optimization**

Sometimes solutions must satisfy rules:

Examples:

* Airport must be inside Romania
* Must be on land
* Must stay within boundaries

Types:

### **Linear Programming**

* Constraints = straight-line inequalities
* Objective = linear
* Polynomial time solutions
* Very widely used

### **Convex Optimization**

* Constraint region must be convex
* Objective must be convex
* Guaranteed unique global optimum
* Efficient even with thousands of variables
* Used heavily in ML and control theory

---

## **11. Summary (Child-friendly)**

* Continuous spaces have infinite possibilities
* Local search works by checking nearby places
* We can either:

  * Break space into a grid (discretize)
  * Or use calculus (gradients, Newton method)
* Problems like plateaus, ridges, local maxima still occur
* Tools like simulated annealing and random restart help escape traps
* Constrained optimization adds rules (like being inside borders)
* Linear and convex optimization are powerful and efficient

---
