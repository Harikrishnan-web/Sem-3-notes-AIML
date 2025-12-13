---

### **1. Game Theory (1.1)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **1. Game Theory (1.1)** |, |
| **Explanation** | **Game theory** deals with competitive environments where two or more agents have **conflicting goals**, giving rise to **adversarial search problems**. In the context of AI, researchers often concentrate on simplified games like chess or Go. The games most commonly studied are **deterministic, two-player, turn-taking, perfect information, zero-sum games**. "Zero-sum" means that what is good for one player is exactly as bad for the other (there is no "win-win" outcome). The two players are typically referred to as **MAX** and **MIN**. |,, |
| **Algorithm (Simplified)** | N/A (Concept/Definition) | |
| **Codes** | N/A | |
| **Diagrams** | N/A | |
| **Output/Result** | A game is formally defined by its elements: The initial state ($S_{0}$), the player whose turn it is (TO-MOVE(s)), the set of legal moves (ACTIONS(s)), the resulting state (RESULT(s, a)), a check if the game is over (IS-TERMINAL(s)), and a function defining the final numeric value (UTILITY(s, p)),. |, |

### **2. Optimal Decisions in Games (1.2)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **2. Optimal Decisions in Games (1.2)** |, |
| **Explanation** | Finding the optimal decision requires MAX to devise a **conditional plan** (or contingent strategy) that specifies a response to every possible move MIN might make. For games with multiple outcome scores, the needed algorithm is **minimax search**. The **minimax value** of a state is the maximum utility MAX can achieve, assuming that MIN plays optimally to minimize MAX's utility from that state onwards. |,, |
| **Algorithm (Simplified)** | **Minimax (The Worst-Case Planner):** The algorithm works backward from the game's end. **(1)** If it's MAX's turn, MAX picks the choice that leads to the **highest** score. **(2)** If it's MIN's turn, MIN picks the choice that leads to the **lowest** score (because MIN wants the worst result for MAX). By always assuming the opponent will pick the worst possible outcome for you, the algorithm finds the best guaranteed score,. |,, |
| **Codes** | `function MINIMAX-SEARCH(game, state) returns an action`<br>`function MAX-VALUE(game, state) returns a (utility, move) pair`<br>`function MIN-VALUE(game, state) returns a (utility, move) pair` (These functions perform a complete depth-first search to the leaves of the tree). |, |
| **Diagrams** | Figure 1.2: A two-ply game tree showing MAX nodes ($\Delta$) and MIN nodes ($\nabla$) labeled with their backed-up minimax values. | |
| **Output/Result** | The **minimax decision** is the action from the root node that leads to the state with the highest minimax value. The complexity of the minimax algorithm is exponential: $O(b^m)$, where 'b' is the branching factor and 'm' is the maximum depth. |, |

### **3. Alpha-Beta Search (1.2.3 and 1.3)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **3. Alpha-Beta Pruning (1.2.3)** | |
| **Explanation** | **Alpha-beta pruning** is a technique that computes the exact same optimal move as minimax but makes the search much more efficient by eliminating subtrees that are guaranteed to have no impact on the final decision,. It maintains two parameters: **$\alpha$**, which is the best (highest) choice found so far for MAX along the current path, and **$\beta$**, which is the best (lowest) choice found so far for MIN along the current path. |,, |
| **Algorithm (Simplified)** | **The Shortcut Hunter Algorithm:** This is Minimax, but smarter. **(1) Keep Score:** MAX keeps track of its current guaranteed best score ($\alpha$), and MIN keeps track of its current guaranteed best score ($\beta$). **(2) Pruning Rule:** If MAX is searching a branch and MIN finds a move that makes the score ($\beta$) worse than the score MAX has already guaranteed ($\alpha$), MAX knows it will never choose this branch, so the search stops immediately (pruning),. Likewise, if MIN is searching a branch and the score becomes better than MAX’s best score ($\alpha$), MIN knows MAX will never choose this path, so the search stops,. **(3) Move Ordering:** The search is fastest if we check the most promising moves first. This is because good move ordering (like trying capturing moves first) increases the chance of early pruning,. |,, |
| **Codes** | Full pseudocode for `ALPHA-BETA-SEARCH`, `MAX-VALUE`, and `MIN-VALUE` is provided. The core pruning logic includes the checks: `if $v\ge\beta$ then return v, move` (in MAX-VALUE) and `if $v\le\alpha$ then return v, move` (in MIN-VALUE),. |, |
| **Diagrams** | Figure 1.5: Stages showing the calculation and how the $\alpha$ and $\beta$ bounds are updated, demonstrating where pruning occurs (e.g., stopping the search below node C). | |
| **Output/Result** | Alpha-beta pruning can drastically reduce the number of nodes examined; with perfect move ordering, the time complexity becomes $O(b^{m/2})$ instead of $O(b^m)$, allowing the algorithm to search roughly twice as deep. To make use of limited time, search is often cut off early, and a **heuristic evaluation function (EVAL)** is applied to nonterminal states to estimate utility (H-MINIMAX),. |,, |

### **4. Monte Carlo Tree Search (MCTS) (1.4)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **4. Monte Carlo Tree Search (1.4)** | |
| **Explanation** | **MCTS** is a strategy favored for games like Go that have a very high branching factor or where developing a strong heuristic evaluation function is difficult,. Instead of using evaluation functions, MCTS estimates a state's value as the **average utility** over a number of **simulations** (or playouts) of complete games starting from that state. MCTS maintains a balance between **exploration** (trying states with few playouts but high uncertainty) and **exploitation** (focusing on states that have performed well). |,, |
| **Algorithm (Simplified)** | **The Trial-and-Error Loop:** MCTS grows a search tree by repeating four steps,: **(1) SELECTION:** Start at the root and choose moves down the tree until a leaf node is reached, guided by a policy like UCT (Upper Confidence Bounds applied to Trees). **(2) EXPANSION:** Create a new child node from the selected leaf. **(3) SIMULATION (Playout):** Play a full, simulated game from that new child node, using a playout policy, until the game ends. **(4) BACK-PROPAGATION:** Update the statistics (number of wins and total playouts) for all nodes along the path from the new child up to the root, based on the simulation result. |,,,, |
| **Codes** | `function MONTE-CARLO-TREE-SEARCH(state) returns an action`<br>The UCB1 selection formula is: $UCB1(n)=\frac{U(n)}{N(n)}+C\times\sqrt{\frac{log~N(PARENr(n))}{N(n)}}$. |, |
| **Diagrams** | Figure 1.10: Depicts one iteration of the MCTS cycle, showing Selection (a), Expansion and Simulation (b), and Backpropagation (c). | |
| **Output/Result** | The algorithm repeats the MCTS cycle until time runs out, then returns the move leading to the node with the **highest number of playouts**. The time to compute a playout is linear in the depth of the game tree, enabling many playouts. |, |

### **5. Stochastic Games (1.5)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **5. Stochastic Games (1.5)** | |
| **Explanation** | **Stochastic games** involve a random element, such as dice throwing (like in Backgammon),. Because of this chance element, the standard game tree must be extended to include **chance nodes** (represented as circles) in addition to MAX and MIN nodes. Since outcomes are not certain, we cannot use a definite minimax value, but rather calculate the **expected value** of a position. |,,, |
| **Algorithm (Simplified)** | **Expectiminimax (The Weighted Average Planner):** This algorithm is the same as Minimax, but introduces a rule for chance events. **(1)** MAX and MIN nodes still choose to maximize and minimize, respectively. **(2) Chance Nodes (Circles):** For chance events (like dice rolls), the value is calculated as the **weighted average** of all possible outcomes. The value of each outcome (e.g., rolling a 6-5) is multiplied by its specific probability (e.g., $1/18$), and these products are summed up to find the expected score. |, |
| **Codes** | `EXPECTIMINIMAX(s) = ... Σr P(r) EXPECTIMINIMAX (RESULT(s, r)) if To-Move(s) = CHANCE` | |
| **Diagrams** | Figure 1.13: Schematic game tree for backgammon showing chance nodes (circles) branching according to dice roll probabilities (e.g., $1/36$ for doubles, $1/18$ for non-doubles). | |
| **Output/Result** | The optimal decision is the move leading to the highest **expectiminimax value**. Search complexity is high: $O(b^m n^m)$, where 'n' is the number of distinct chance rolls (e.g., $n=21$ for two dice), often making deep search impractical,. Evaluation functions used in these games must return values that are positively linearly correlated with the probability of winning. |,,, |

### **6. Partially Observable Games (1.6)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **6. Partially Observable Games (1.6)** |, |
| **Explanation** | **Partially observable games** are characterized by **imperfect information** or the "fog of war," where players lack full knowledge of the board state,. Examples include Battleship and Kriegspiel (a chess variant where pieces are invisible to the opponent),. Optimal play requires the agent to reason about the **belief state**—the set of all possible actual board states consistent with current knowledge,. |,,,, |
| **Algorithm (Simplified)** | **Averaging Over Clairvoyance (Simple Trick):** This method simplifies the problem by treating the beginning of the game (like a card deal) as the only chance node, assuming that after that event, the game suddenly becomes fully observable (clairvoyant),. It calculates the average utility over all possible configurations of missing information. *Warning:* This approach often fails because it ignores the need to gather information, hide information, or bluff. |,,, |
| **Codes** | N/A | |
| **Diagrams** | Figure 1.15: Shows how a combination of "probing moves" in Kriegspiel narrows down the possible locations of the opponent's pieces (the belief state). | |
| **Output/Result** | A **guaranteed checkmate** strategy in Kriegspiel must succeed for *every* possible board state currently in the belief state. Programs often use evaluation functions that resemble those for observable games but include a component favoring a smaller belief state (less uncertainty). |, |

### **7. Constraint Satisfaction Problems (CSPs) (2.1)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **7. Constraint Satisfaction Problems (CSPs) (2.1)** |, |
| **Explanation** | A **Constraint Satisfaction Problem (CSP)** uses a **factored representation** for states, meaning it views the state as a set of variables, each having a value. A CSP consists of three components: **X** (a set of variables), **D** (a set of domains, which are the allowable values for each variable), and **C** (a set of constraints, defining allowable combinations of values). A **solution** is a **consistent, complete assignment**—meaning every variable has a value, and no constraints are violated. |,, |
| **Algorithm (Simplified)** | N/A (Concept/Definition) | |
| **Codes** | N/A | |
| **Diagrams** | Figure 2.1(b): Shows the constraint graph for the map-coloring problem, where nodes are variables (regions) and edges connect variables that are constrained (neighboring regions),. Figure 2.2(b): Shows a constraint **hypergraph** for a cryptarithmetic problem, where squares (hypernodes) represent n-ary constraints involving multiple variables,. |,,, |
| **Output/Result** | Constraints can be: **Unary** (restricts one variable, e.g., SA $\ne$ green); **Binary** (relates two variables, e.g., SA $\ne$ NSW); or **Global** (involves arbitrary number of variables, e.g., Alldiff, where all variables must have distinct values). Solving a CSP is generally NP-complete. |,, |

### **8. Constraint Propagation (2.2)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **8. Constraint Propagation (2.2)** |, |
| **Explanation** | **Constraint propagation** is an inference technique that uses constraints to reduce the number of legal values in variables' domains, minimizing the effort needed for search. The process enforces **local consistency** across the constraint graph, eliminating inconsistent values. **Node consistency** ensures all values satisfy unary constraints. **Arc consistency (2-consistency)** ensures that for every value of one variable, there is a consistent value for a second variable connected by a binary constraint,. **Path consistency (3-consistency)** tightens binary constraints by examining triples of variables,. |,,,,, |
| **Algorithm (Simplified)** | **AC-3 (Arc Consistency 3):** This algorithm makes sure all pairs of connected variables (arcs) are consistent. **(1) Queue Setup:** Start with a list (queue) containing every directed connection line (arc) in the graph. **(2) Revise:** Pull an arc $(X_{i}, X_{j})$ from the queue. If $X_{i}$ has an option that is impossible to satisfy based on $X_{j}$'s current options, erase that option from $X_{i}$'s list. **(3) Ripple Effect:** If $X_{i}$'s options were reduced, put all arcs pointing *into* $X_{i}$ back onto the queue, because $X_{i}$'s new restrictions might cause problems for its neighbors. **(4) Termination:** Repeat until the queue is empty. If any variable's list of options becomes empty, we know there is no solution,. |,, |
| **Codes** | Full pseudocode for `AC-3(csp)` and `REVISE(csp, Xi, Xj)` is provided,. |, |
| **Diagrams** | N/A | |
| **Output/Result** | Constraint propagation can significantly reduce domain sizes, making subsequent search faster. In complex global constraints (like resource constraints), **bounds propagation** is used, where domains are reduced by adjusting the upper and lower bounds of integer variables,. |,, |

### **9. Backtracking Search for CSP (2.3)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **9. Backtracking Search for CSP (2.3)** |, |
| **Explanation** | **Backtracking search** is a recursive, depth-first approach that builds a solution by assigning values to variables one at a time,. It exploits the **commutativity** of CSPs (assignment order doesn't affect the final state), ensuring the search tree has a manageable size of $d^n$ leaves, instead of $n! \cdot d^n$. |,, |
| **Algorithm (Simplified)** | **The Smart Backtracker:** This algorithm uses heuristics to guess efficiently: **(1) Choose Variable (Fail-First):** Use the **Minimum-Remaining-Values (MRV)** heuristic to pick the variable with the fewest remaining legal values. (This makes failure happen sooner, pruning the tree faster.) Use the **Degree heuristic** as a tie-breaker, picking the variable involved in the most constraints. **(2) Choose Value (Fail-Last):** Use the **Least-Constraining-Value** heuristic to try the value that removes the fewest options from the neighboring variables. **(3) Propagate:** After assigning a value, run an inference check like **Forward Checking** (which deletes inconsistent values from neighbors' domains) or **MAC** (which maintains full arc consistency),. **(4) Backjump:** If the search fails, instead of just undoing the most recent move (**chronological backtracking**), use **conflict-directed backjumping** to skip irrelevant variables and jump directly back to the variable that actually caused the conflict,. |,,,,, |
| **Codes** | Full pseudocode for `BACKTRACKING-SEARCH(csp)` and `BACKTRACK(csp, assignment)` is provided, showcasing the recursive structure and the use of heuristics and inference functions,. |, |
| **Diagrams** | Figure 2.7: Shows the progress of forward checking in map coloring, demonstrating how domains are reduced after each assignment, leading to early detection of failure. | |
| **Output/Result** | Backtracking search returns a solution (a complete, consistent assignment) or failure. Efficiency is improved by **constraint learning**, which identifies and records combinations of assignments that lead to contradictions (**no-goods**) to avoid exploring them again,. |,, |

### **10. Local Search for CSP (2.4)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **10. Local Search for CSP (2.4)** | |
| **Explanation** | Local search for CSPs uses a **complete-state formulation**, starting with a full assignment (which usually violates constraints) and iteratively improving it by changing the value of one variable at a time. This approach is often highly effective, even for massive problems like the N-queens problem and Hubble Space Telescope scheduling,. |,, |
| **Algorithm (Simplified)** | **MIN-CONFLICTS (The Fix-It Algorithm):** **(1) Start Full:** Begin with a complete assignment where every variable has a value. **(2) Pick Problem:** Randomly choose a variable that is currently violating a constraint,. **(3) Best Fix:** Change the value of that variable to the option that causes the **minimum number of conflicts** (violated constraints) with all other variables (the **min-conflicts heuristic**),. **(4) Repeat:** Keep fixing the conflicts until no constraints are violated. |,, |
| **Codes** | Full pseudocode for `MIN-CONFLICTS (csp, max_steps)` is provided,. |, |
| **Diagrams** | Figure 2.8: Illustrates the min-conflicts heuristic applied to an 8-queens problem, showing how a queen is moved to the row with the lowest conflict count. | |
| **Output/Result** | Local search returns a solution if found within the maximum allowed steps. Techniques used to escape flat search areas (plateaus) include **constraint weighting** (incrementing the weight of frequently violated constraints to introduce better topography) and **tabu search** (forbidding the return to recently visited states),. |,, |

### **11. Structure of CSP (2.5)**

| Element | Content | Citation |
| :--- | :--- | :--- |
| **Topic Title with Number** | **11. Structure of CSP (2.5)** | |
| **Explanation** | The overall difficulty of solving a CSP is strongly tied to the topology of its constraint graph. Finding ways to decompose a problem based on its structure can lead to immense computational savings,. If the graph decomposes into **independent subproblems** (disconnected components), they can be solved separately. **Tree-structured CSPs** (where any two variables are connected by only one path) are the most efficient, solvable in time linear in the number of variables. |,,,, |
| **Algorithm (Simplified)** | **TREE-CSP-SOLVER (The Linear Solver):** This solves tree-structured CSPs without backtracking. **(1) Order:** Choose a root variable and order all other variables so that each child comes after its parent (**topological sort**). **(2) Pre-processing:** Work backward through the ordering, enforcing **directional arc consistency (DAC)** between each child and its parent,. **(3) Assignment:** Work forward through the ordering, assigning any remaining consistent value to each variable. Since DAC guarantees that a valid option exists for every variable, the search moves linearly without failure,. |,, |
| **Codes** | Full pseudocode for `TREE-CSP-SOLVER(csp)` is provided,. |, |
| **Diagrams** | Figure 2.12: Illustrates **Cutset Conditioning**, showing how removing South Australia (SA) breaks the constraint graph into two smaller, unconnected trees. Figure 2.13: Illustrates a **Tree Decomposition**, where sets of variables are grouped into nodes to form a tree structure. |, |
| **Output/Result** | Tree-structured CSPs are solved in $O(nd^2)$ time,. General CSPs can be reduced to trees using: **Cutset Conditioning** (assigning values to a small set of variables, the cycle cutset, to break cycles), or **Tree Decomposition** (transforming the graph into a tree of subproblems). Tree decomposition is efficient if the **tree width** (size of the largest node minus one) of the graph is small, resulting in $O(nd^{w+1})$ time complexity,. |,,,,, |