---

# **1)INTRODUCTION TO ARTIFICIAL INTELLIGENCE – TOP-SCORING NOTES**

---

## **1. Definition of Artificial Intelligence**

**Artificial Intelligence (AI)** is a branch of computer science that creates **machines capable of performing tasks that normally require human intelligence** such as learning, reasoning, problem-solving, perception, and decision-making.

AI = **Artificial (man-made) + Intelligence (thinking ability)**
AI exists when machines show **human-like skills**: learning from experience, adapting, solving problems, making decisions.

---

## **2. Why Artificial Intelligence?**

AI is important because it can:

* Solve real-world problems (healthcare, traffic, marketing, environment).
* Power virtual assistants (Siri, Google Assistant).
* Work in dangerous environments (mines, ocean, space).
* Enable new technologies like autonomous cars, smart robots, advanced analytics.
* Increase efficiency, speed, and accuracy in complex tasks.

---

## **3. Goals of Artificial Intelligence**

1. **Replicate human intelligence**
2. **Solve knowledge-intensive tasks**
3. **Link perception ↔ action rationally**
4. Build machines capable of tasks requiring human intelligence

   * Driving
   * Chess
   * Surgery planning
   * Theorem proving
5. Create systems that can learn, explain, advise, and adapt autonomously.

---

## **4. What Comprises Artificial Intelligence?**

AI requires many disciplines because intelligence involves:

* **Reasoning**
* **Learning**
* **Problem-solving**
* **Perception**
* **Language understanding**

Disciplines contributing to AI:

* **Mathematics**
* **Biology**
* **Psychology**
* **Sociology**
* **Computer Science**
* **Neuroscience**
* **Statistics**

---

## **5. Advantages of Artificial Intelligence**

* **High accuracy, fewer errors**
* **High speed**, faster decision-making
* **Highly reliable**; repeat tasks consistently
* Works in **risky areas** (bomb disposal, space, oceans)
* **Digital assistants** for automation
* Useful for **public utilities** (self-driving cars, facial recognition, NLP)

---

## **6. Disadvantages of Artificial Intelligence**

* **High cost** (hardware, software, maintenance)
* **Cannot think creatively/outside the box**
* **No emotions or feelings**
* **Increased dependency** on machines
* **Lack of originality**—cannot match human creativity

---

## **7. History of Artificial Intelligence (Quick Timeline)**

**1943–1952 (Maturation):**

* 1943: McCulloch & Pitts – Artificial Neuron model
* 1949: Hebb – Hebbian learning
* 1950: Alan Turing – Turing Test

**1952–1956 (Birth of AI):**

* 1955: Logic Theorist (first AI program)
* 1956: Term “Artificial Intelligence” coined by John McCarthy

**1956–1974 (Golden Years):**

* 1966: First chatbot **ELIZA**
* 1972: First humanoid robot **Wabot-1**

**1974–1980 (First AI Winter):** Low funding, low interest.

**1980–1987 (AI Boom):** Expert systems became popular.

**1987–1993 (Second AI Winter):** Expert systems failed commercially.

**1993–2011 (Emergence of Intelligent Agents):**

* 1997: **Deep Blue** defeats chess champion Kasparov
* 2002: Roomba (AI vacuum)
* 2006: AI enters business world

**2011–Present (Deep Learning Era):**

* 2011: IBM Watson wins Jeopardy
* 2012: Google Now
* 2014: Eugene Goostman passes limited Turing test
* 2018: IBM Project Debater
* Google Duplex, autonomous cars, large language models

---

## **8. Types of AI (Two Major Classifications)**

### **A. Based on Capabilities**

1. **Narrow AI (Weak AI)**

   * Performs one specific task
   * Examples: Siri, Alexa, Chess engine, Speech recognition

2. **General AI**

   * Human-level intelligence
   * Can perform any intellectual task
   * Does not exist yet (under research)

3. **Super AI**

   * Surpasses human intelligence
   * Hypothetical; future concept
   * Can think, reason, plan better than humans

---

### **B. Based on Functionality**

1. **Reactive Machines**

   * No memory
   * Only respond to current input
   * Example: Deep Blue, AlphaGo

2. **Limited Memory**

   * Stores temporary data
   * Example: Self-driving cars

3. **Theory of Mind**

   * Understand emotions, beliefs, intentions
   * Still under research

4. **Self-Aware AI**

   * Has consciousness
   * Future concept; does not exist

---

## **9. Applications of Artificial Intelligence (Exam-Focused List)**

### **1. Astronomy** – Understand universe, model cosmic events

### **2. Healthcare** – Diagnosis, prediction, medical imaging

### **3. Gaming** – Strategic games like chess, Go

### **4. Finance** – Trading algorithms, fraud detection, chatbots

### **5. Data Security** – Cybersecurity (spam detection, threat detection)

### **6. Social Media** – Trend analysis, recommendations, content filtering

### **7. Travel & Transport** – Route suggestions, AI chatbots

### **8. Automotive** – Self-driving cars, driver assistance

### **9. Robotics** – Intelligent humanoids like Sophia, Erica

### **10. Entertainment** – Netflix/Amazon recommendations

### **11. Agriculture** – Crop monitoring, predictive analytics

### **12. E-Commerce** – Product recommendations, automation

### **13. Education** – Automated grading, virtual tutors

---
# **2)AGENTS AND ENVIRONMENTS – EXAM-READY NOTES**

---

## **Agents in Artificial Intelligence**

An **agent** is anything that **perceives** its environment through **sensors** and **acts** upon that environment using **actuators**.

**Agent cycle:**
**Perceive → Think → Act**

### **Types of Agents (Examples)**

* **Human Agent:**
  Sensors – eyes, ears
  Actuators – hands, legs, speech
* **Robotic Agent:**
  Sensors – camera, infrared, NLP
  Actuators – motors
* **Software Agent:**
  Sensors – keystrokes, file input
  Actuators – display, logs

---

## **Sensors, Actuators, Effectors**

* **Sensors**: Detect changes in environment (camera, mic, temperature sensor).
* **Actuators**: Convert energy into motion (motors, wheels, gears).
* **Effectors**: Parts that effect the environment (legs, arms, fingers, screen).

---

## **Agent Environment**

* Environment = everything surrounding the agent but not part of it.
* It provides conditions for sensing and acting.
* Most environments are **non-deterministic** and dynamic.

---

## **Intelligent Agents**

An **intelligent agent** is an autonomous system that uses sensors & actuators to achieve goals and can learn from the environment.

### **Rules for an AI agent**

1. Must perceive the environment
2. Use observations to make decisions
3. Decisions must result in actions
4. Actions must be **rational**

---

## **Characteristics of Intelligent Agent**

* **Autonomy**
* **Reactivity**
* **Pro-activeness** (goal-driven)
* **Social ability** (interact with other agents)
* **Adaptability/Learning ability**

---

## **Types of Agent Programs**

1. **Simple Reflex Agents**
2. **Model-Based Reflex Agents**
3. **Goal-Based Agents**
4. **Utility-Based Agents**
5. **Learning Agents**

---

## **1. Simple Reflex Agents**

* Act only based on **current percept**
* Ignore percept history
* Works only in **fully observable** environments
* Based on **Condition–Action rules**

**Problems:**

* Limited intelligence
* No memory
* Not adaptable

---

## **2. Model-Based Reflex Agents**

* Work in **partially observable** environments
* Maintain **internal state**
* Use **model of the world**
* Update state using:

  * How world evolves
  * How actions affect world

---

## **3. Goal-Based Agents**

* Use goals to decide actions
* Compare future states → choose action leading to goal
* Use **searching and planning**
* More flexible than simple/model-based agents

---

## **4. Utility-Based Agents**

* Handle multiple options
* Use **utility function**: maps state → numeric value
* Choose action giving **highest utility**
* Useful when multiple goals or trade-offs exist

---

## **5. Learning Agents**

Components:

* **Learning Element** (learn from experience)
* **Critic** (gives feedback)
* **Performance Element** (selects actions)
* **Problem Generator** (suggests exploratory actions)

---

## **Rational Agent**

A rational agent chooses actions that **maximize performance measure**.

Rationality depends on:

* Performance measure
* Prior knowledge
* Possible actions
* Percept sequence

---

## **Nature of Environments (8 Key Properties)**

### **1. Fully Observable vs Partially Observable**

Fully: agent senses entire environment
Partially: only partial knowledge

### **2. Deterministic vs Stochastic**

Deterministic: next state predictable
Stochastic: randomness involved

### **3. Episodic vs Sequential**

Episodic: actions independent (image classification)
Sequential: past actions matter (driving)

### **4. Static vs Dynamic**

Static: environment does not change during decision
Dynamic: it changes (taxi driving)

### **5. Discrete vs Continuous**

Discrete: finite actions/percepts (chess)
Continuous: infinite states (robot navigation)

### **6. Single Agent vs Multi-Agent**

Single: one agent alone
Multi: multiple agents (games, traffic)

### **7. Known vs Unknown**

Known: agent knows rules
Unknown: must learn rules

### **8. Accessible vs Inaccessible**

Accessible: full sensor access
Inaccessible: hidden information

---

## **Structure of an Intelligent Agent**

Agent = **Architecture + Agent Program**

* **Architecture:** Physical platform (robot, computer)
* **Agent Program:** Maps percept → action
  **f : P* → A**

---

## **PEAS Representation**

A framework to define an agent:

* **P** – Performance Measure
* **E** – Environment
* **A** – Actuators
* **S** – Sensors

### **Example: Self-driving Car**

* P: Safety, time, comfort, legality
* E: Roads, vehicles, pedestrians
* A: Steering, brake, accelerator
* S: Cameras, GPS, lidar, speedometer

---
# **3)CONCEPT OF RATIONALITY – EXAM-READY NOTES**

---

## **Rational Agent**

A **rational agent** is an agent that **does the right action** to maximize its **performance measure** based on the information it has.

A rational agent:

* Has clear preferences
* Handles uncertainty
* Chooses action giving **best expected outcome**
* Uses optimal decision-making strategies

---

## **What Determines Rationality?**

Rationality depends on four main factors:

1. **Performance Measure**
   Defines success criteria of the agent.
   Example: For a vacuum cleaner – cleanliness, battery efficiency.

2. **Prior Knowledge**
   What the agent already knows about the environment.

3. **Possible Actions**
   All actions available to the agent at a given moment.

4. **Percept Sequence**
   Complete history of everything the agent has perceived so far.

---

## **Rational Action**

A **rational action** is the action that **maximizes expected performance**, considering:

* Percepts
* Knowledge
* Action constraints
* Outcomes

In reinforcement learning, rationality = maximizing reward:

* Best action → positive reward
* Wrong action → negative reward

---

# **NATURE OF ENVIRONMENTS – EXAM-READY NOTES**

---

An environment is the **world in which an agent operates**.
According to Russell & Norvig, environments can be classified using **8 properties**.

---

## **1. Fully Observable vs Partially Observable**

* **Fully Observable**:
  Agent’s sensors can access the *complete* environment state.
  Example: Chess.

* **Partially Observable**:
  Only limited information is available.
  Example: Driving in fog.

---

## **2. Deterministic vs Stochastic**

* **Deterministic**:
  Next state is fully predictable from current state + action.
  Example: Puzzle games.

* **Stochastic**:
  Randomness involved; outcome not fully predictable.
  Example: Taxi driving, real-world robotics.

---

## **3. Episodic vs Sequential**

* **Episodic**:
  Each action is independent.
  No need to consider past actions.
  Example: Image classification.

* **Sequential**:
  Future actions depend on past actions.
  Example: Chess, navigation.

---

## **4. Static vs Dynamic**

* **Static**:
  Environment does not change while the agent is deciding.
  Example: Crossword puzzles.

* **Dynamic**:
  Environment changes on its own.
  Example: Self-driving cars.

---

## **5. Discrete vs Continuous**

* **Discrete**:
  Finite number of percepts and actions.
  Example: Board games.

* **Continuous**:
  Infinite states, continuous sensor values.
  Example: Robot movement, temperature control.

---

## **6. Single-Agent vs Multi-Agent**

* **Single-Agent**:
  Only one agent acting.
  Example: Crossword-solving robot.

* **Multi-Agent**:
  Multiple agents interact or compete.
  Example: Traffic environment, multiplayer games.

---

## **7. Known vs Unknown**

* **Known**:
  Agent knows rules, results of actions.

* **Unknown**:
  Agent must learn how the environment works.

---

## **8. Accessible vs Inaccessible**

* **Accessible**:
  Agent gets complete and accurate information.
  Example: Empty room with temperature sensor.

* **Inaccessible**:
  Agent receives limited or noisy information.
  Example: Weather prediction.

---
# **5)STRUCTURE OF AGENTS – EXAM-READY NOTES**

---

## **Structure of an Intelligent Agent**

An agent is defined as:

**Agent = Architecture + Agent Program**

### **1. Architecture**

* The physical machinery on which the agent runs
* Examples: Robot body, computer hardware, sensors, actuators

### **2. Agent Program**

* Software that implements the agent function
* Maps **percepts → actions**
* Executes on the architecture

### **3. Agent Function**

* A mathematical function that defines agent’s behavior
* **f : P* → A**

  * P*: all percept sequences
  * A: set of actions

---

## **Key Components in the Structure**

1. **Sensors** – collect percepts from environment
2. **Actuators** – perform actions
3. **Internal Model** – stores knowledge (if applicable)
4. **Goals/Utilities** – determine desired outcomes
5. **Memory/Internal State** – holds past percepts
6. **Decision-Making Unit** – converts percepts to actions

---

# **PROBLEM-SOLVING AGENTS – EXAM-READY NOTES**

---

## **Definition**

A **problem-solving agent** is a **goal-based agent** that uses **search algorithms** to find action sequences that lead to the goal.

It uses **atomic representations**, meaning states are treated as indivisible units.

---

## **Steps in Problem-Solving**

1. **Formulate goal**
2. **Formulate problem**
3. **Search for solution**
4. **Execute solution**
5. **Evaluate performance**

---

## **Components of a Search Problem**

1. **Initial State**
2. **Actions**
3. **Transition Model**
4. **State Space**
5. **Goal Test**
6. **Path Cost Function**

---

## **Measuring Performance of Search Algorithms**

1. **Completeness** – Finds a solution if one exists
2. **Optimality** – Finds the best (lowest cost) solution
3. **Time Complexity** – How long it takes
4. **Space Complexity** – Memory required

---

## **Important Problem-Solving Examples**

* Chess
* Travelling Salesman Problem
* Tower of Hanoi
* Water Jug Problem
* N-Queens Problem

---

## **Search Terminologies**

* **Search Space** – Set of all possible states
* **Search Tree** – Tree built during search
* **Solution** – Sequence of actions to reach goal
* **Optimal Solution** – Solution with minimum path cost

---
# **6)UNINFORMED SEARCH ALGORITHMS – EXAM-READY NOTES**

---

# **Uninformed Search (Blind Search)**

Uninformed search strategies do **not use any domain knowledge** such as distance to goal or heuristic values.

They only use:

* Initial state
* Actions
* Goal test
* State space structure

They explore the search space **brute-force** until the goal is found.

---

# **TYPES OF UNINFORMED SEARCH ALGORITHMS**

---

# **1. Breadth-First Search (BFS)**

### **Definition**

Searches **level by level** starting from the root.
Expands all nodes at the current depth before going deeper.

### **Key Points**

* Uses **FIFO Queue**
* Finds **shallowest solution first**
* Complete and optimal (if all edge costs equal)

### **Advantages**

* Always finds a solution
* Finds **minimum steps solution**

### **Disadvantages**

* Very high memory usage
* Slow if solution is deep

### **Complexity**

* Time: **O(bᵈ)**
* Space: **O(bᵈ)**
  b = branching factor, d = depth of shallowest goal

---

# **2. Depth-First Search (DFS)**

### **Definition**

Expands the **deepest node first** before backtracking.

### **Key Points**

* Uses **Stack** (LIFO)
* Goes deep along one path
* Backtracks when dead end

### **Advantages**

* Low memory: **O(bm)**
* Faster in many cases if the right path is deep

### **Disadvantages**

* Can go into **infinite loops**
* Not complete for infinite depth
* Not optimal

### **Complexity**

* Time: **O(bᵐ)**
* Space: **O(bᵐ)**
  m = maximum depth

---

# **3. Depth-Limited Search (DLS)**

### **Definition**

DFS with a **fixed depth limit ℓ**.
Nodes deeper than ℓ are not expanded.

### **Advantages**

* Avoids infinite loops
* Less memory

### **Disadvantages**

* May miss solutions below limit
* Incomplete if ℓ < goal depth
* Not optimal

### **Complexity**

* Time: **O(b^ℓ)**
* Space: **O(bℓ)**

---

# **4. Iterative Deepening Depth-First Search (IDDFS)**

### **Definition**

Performs DFS with increasing depth limits:
ℓ = 0, 1, 2, … until the goal is found.

### **Key Points**

* Combines **completeness of BFS**
* With **low memory of DFS**

### **Advantages**

* Complete
* Optimal if all edges have same cost
* Memory efficient

### **Disadvantages**

* Re-explores upper levels repeatedly (but cost acceptable)

### **Complexity**

* Time: **O(bᵈ)**
* Space: **O(bd)**

---

# **5. Uniform Cost Search (UCS)**

### **Definition**

Expands node with **lowest path cost g(n)**.
Used when actions have different costs.

### **Key Points**

* Uses **Priority Queue**
* Always expands least-cost path first
* Equivalent to BFS if all costs equal

### **Advantages**

* Optimal
* Complete (if cost > 0)

### **Disadvantages**

* Can be slow
* High memory consumption

### **Complexity**

* Time: **O(b^(1 + C*/ε))**
* Space: **Same as time**
  C* = optimal solution cost
  ε = minimum step cost

---

# **6. Bidirectional Search**

### **Definition**

Runs two simultaneous searches:

* From initial state
* From goal state
  Stops when the two meet.

### **Advantages**

* Very fast
* Less memory

### **Disadvantages**

* Hard to implement
* Goal state must be known
* Hard to ensure two frontiers meet

### **Complexity**

* Time: **O(b^(d/2))**
* Space: **O(b^(d/2))**

---
# UNINFORMED & INFORMED SEARCH — SIMPLE STEP-BY-STEP EXPLANATIONS WITH TREES

---

## LEGEND (used in all trees)

* `S` = Start
* `G` = Goal
* `→` = edge / action
* `Frontier` = nodes waiting to be expanded
* `Explored` = nodes already expanded

---

# UNINFORMED SEARCH (no heuristic)

### 1) Breadth-First Search (BFS) — step by step (easy)

Tree:

```
        S
      / | \
     A  B  C
    / \    |
   D   E   G
```

Steps:

1. Put `S` in Frontier: `[S]`.
2. Remove front of Frontier → expand `S`. Add children in order → Frontier: `[A, B, C]`.
3. Remove `A` → expand `A` → add `D, E` → Frontier: `[B, C, D, E]`.
4. Remove `B` → expand `B` (no new) → Frontier: `[C, D, E]`.
5. Remove `C` → expand `C` → add `G` → Frontier: `[D, E, G]`.
6. Remove `D`, then `E`. When `G` is removed, check goal → found.
   Why it works: expands level by level, so it finds the shallowest solution first.
   Memory: stores whole frontier (may be large).

---

### 2) Depth-First Search (DFS) — step by step (easy)

Same tree.
Steps:

1. Put `S` in Frontier (stack): `[S]`.
2. Pop top → expand `S`. Push children so leftmost is popped first → Frontier: `[A, B, C]` (top is `A`).
3. Pop `A` → expand → push `D, E` → Frontier: `[D, E, B, C]` (top `D`).
4. Pop `D` → expand (leaf) → no new → Frontier: `[E, B, C]`.
5. Pop `E` → expand → Frontier: `[B, C]`.
6. Pop `B` → expand → Frontier: `[C]`.
7. Pop `C` → expand → push `G` → Frontier: `[G]`.
8. Pop `G` → goal found.
   Why it works: goes deep along one branch before backtracking.
   Risk: can go infinitely deep or miss shorter solution. Uses little memory.

---

### 3) Depth-Limited Search (DLS) — step by step (easy)

Same tree, set depth limit `L = 1` (only expand root and its children).
Steps:

1. Start at `S` (depth 0). Frontier: `[S]`.
2. Expand `S` → add `A, B, C` (depth 1). Do not expand nodes at depth > 1.
3. Check each at depth 1 only. If goal is deeper than `L`, DLS will fail/cutoff.
   Why use it: prevents infinite descent. If goal depth ≤ L, it can find it.

---

### 4) Iterative Deepening DFS (IDDFS) — step by step (easy)

Uses DLS repeatedly with increasing `L`.
Steps:

1. Run DLS with `L=0`. If goal found, stop.
2. If not, run DLS with `L=1`.
3. If not, run DLS with `L=2`, and so on until goal found.
   Why: combines BFS completeness and DFS low memory. Repeats shallow work but memory stays small.

---

### 5) Uniform-Cost Search (UCS) — step by step (easy)

Tree with costs:

```
S
├─A (cost 1)
│  └─G (cost 9)   path S→A→G cost = 1+9 = 10
└─B (cost 2)
   └─G (cost 4)   path S→B→G cost = 2+4 = 6
```

Steps:

1. Put `S` with cost 0 in Frontier (priority by path cost).
2. Pop lowest-cost node (`S`), expand → add `A (g=1)`, `B (g=2)`.
3. Pop lowest `A (g=1)`, expand → add `G (g=10)`.
4. Frontier has `B (g=2)` and `G (g=10)`. Pop `B (g=2)`, expand → add `G (g=6)`.
5. Frontier has `G (g=6)` and `G (g=10)`. Pop smallest `G (g=6)` → goal found with optimal cost 6.
   Why: always expands the least-cost path so it finds lowest-cost solution even if deeper.

---

### 6) Bidirectional Search — step by step (easy)

Tree (conceptual):

```
Start side: S → A → D
Goal side:  G → F → D
Meeting at D
```

Steps:

1. Start two searches: forward from `S`, backward from `G`.
2. Expand one layer from `S` and one from `G` alternately.
3. After expansions, check whether the frontiers intersect (a common node).
4. If they meet at node `M` (e.g., `D`), join forward path `S→...→M` and backward path `M→...→G` to form full path.
   Why: can be much faster (roughly square root of single search) but needs to be able to generate predecessors from goal.

---

# INFORMED (HEURISTIC) SEARCH (uses estimate to goal `h(n)`)

### 1) Greedy Best-First Search — step by step (easy)

Tree with heuristic values `h(n)` (lower = closer to goal):

```
        S(h=7)
      /   |   \
   A(4)  B(6)  C(3)
          |
         G(0)
```

Steps:

1. Put `S` in Frontier prioritized by `h` → Frontier: `[S(h7)]`.
2. Expand `S` → add `A(h4), B(h6), C(h3)`.
3. Always pop node with smallest `h`: pop `C(h3)` first → expand; if `G` generated, pop it next → goal.
   Why: chooses nodes that "look" closest to goal. Fast but can make wrong choices because it ignores cost so far.

---

### 2) A* Search — step by step (easy)

Uses `f(n) = g(n) + h(n)` where `g` = cost so far, `h` = heuristic.

Tree example (costs on edges + h values):

```
S
├─A (cost1, h=5)   f = g+h = 1+5 = 6
└─B (cost2, h=3)   f = 2+3 = 5
B → G (cost4, h=0) final g=6, f=6
A → G (cost9, h=0) final g=10, f=10
```

Steps:

1. Put `S` in Frontier with `g=0, f=h(S)`.
2. Pop node with smallest `f`. Expand S → produce A(f=6), B(f=5).
3. Pop B (f=5) → expand → add G with `g=6, f=6`.
4. Frontier now has A(f=6) and G(f=6). Pop the goal node `G` when it has smallest `f` and `Goal(G)` → found optimal path with cost 6.
   Why: balances cost so far and estimate to goal; if `h` is admissible (never overestimates), A* is guaranteed optimal.

---

# SIMPLE COMPARISON (one-line each)

* **BFS:** level-by-level, finds shortest number-of-step solution, high memory.
* **DFS:** go deep, low memory, may not find shortest, may loop.
* **DLS:** DFS with cutoff; avoids infinite depth, may miss solution below cutoff.
* **IDDFS:** repeated DLS with increasing cutoff; complete + low memory.
* **UCS:** expands lowest total-cost so far; optimal for varying costs.
* **Bidirectional:** two-sided search; fast if you can search backwards.
* **Greedy:** picks node that seems closest (h); fast but not guaranteed optimal.
* **A*:** uses g+h; optimal with admissible h and usually most efficient.

---

# HOW TO FOLLOW THESE STEPS DURING EXAM (quick checklist)

1. Identify `Start`, `Goal`, actions, costs (if any), and any heuristic `h`.
2. Choose algorithm (BFS/DFS/IDDFS/UCS/A*/Greedy/Bidirectional) by constraints: memory, optimality, cost info, ability to run backward.
3. Simulate frontier expansions step by step (pop → expand → add successors).
4. Stop when you pop a node and it satisfies the goal test (that node is the solution node).
5. Reconstruct path using parent links (or by tracing steps you expanded).

---




