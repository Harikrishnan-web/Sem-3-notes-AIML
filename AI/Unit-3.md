# Game Theory: Optimal Decisions and Alpha-Beta Search

This detailed guide covers **Game Theory**, **Optimal Decisions (Minimax)**, and **Alpha-Beta Search** in depth, breaking down every sub-topic found in your material. Each section includes a **Technical Analysis** (for exams) and a **Child-Friendly Explanation** (for intuition), along with algorithms and text-based diagrams.

***

## Topic 1: Game Theory in AI
**Technical Analysis**:
Game theory in AI analyzes competitive environments where multiple agents (players) have conflicting goals. The most common type studied is the **Deterministic, Two-Player, Zero-Sum Game**.
*   **Zero-Sum**: One player's gain is the other's loss. There is no "win-win". The total utility is constant (usually 0).
*   **Perfect Information**: Both players see the entire board (e.g., Chess, Go).
*   **Formal Elements**:
    1.  **$S_0$**: Initial state.
    2.  **TO-MOVE(s)**: Whose turn it is.
    3.  **ACTIONS(s)**: Legal moves.
    4.  **RESULT(s, a)**: New state after a move.
    5.  **IS-TERMINAL(s)**: True if game over.
    6.  **UTILITY(s, p)**: Final score (e.g., +1 win, 0 loss).

**Child-Friendly Explanation (The Tug-of-War)**:
Imagine a game of Tug-of-War.
*   **Zero-Sum**: If you pull the rope 1 meter to your side, your friend *loses* 1 meter. You can't both get the rope!
*   **Perfect Information**: You can see exactly where your friend is standing. No secrets.
*   **Goal**: You want to get the highest score (Win), and your friend wants you to get the lowest score (Lose).

***

## Topic 2: Optimal Decisions (Minimax Search)
<img src="Sources/minimax.png" alt="A screenshot" width="400" height="200">
### 2.1 The Minimax Algorithm
**Technical Analysis**:
MAX tries to maximize the utility, and MIN tries to minimize it. The **Minimax Value** of a state is the best achievable utility assuming **perfect play** from the opponent.
*   **MAX Node**: Value is the **Maximum** of its children.
*   **MIN Node**: Value is the **Minimum** of its children.
*   **Complexity**: Time $O(b^m)$, Space $O(bm)$ (where $b$=branching factor, $m$=max depth). Impractical for deep games like Chess without optimization.

**Child-Friendly Explanation (The Cake Split)**:
You (MAX) and your greedy brother (MIN) share a cake.
*   **Your Move**: You cut the cake into two pieces.
*   **His Move**: He chooses which piece *he* wants (leaving you the other one).
*   **Strategy**: If you cut one giant piece and one tiny piece, he will take the giant one, leaving you the tiny one. Bad!
*   **Optimal Decision**: You cut two equal pieces. Now, no matter what he picks, you get a decent piece. You "minimized" the damage he could do.
<img src="Sources/minutil.png" alt="A screenshot" width="400" height="200">
**Algorithm (Better Version)**:
```python
def minimax(state, depth, is_max):
    if depth == 0 or is_terminal(state):
        return evaluation(state)
    
    if is_max:
        max_eval = -infinity
        for move in get_moves(state):
            eval = minimax(make_move(state, move), depth - 1, False)
            max_eval = max(max_eval, eval)
        return max_eval
    else:
        min_eval = +infinity
        for move in get_moves(state):
            eval = minimax(make_move(state, move), depth - 1, True)
            min_eval = min(min_eval, eval)
        return min_eval
```

### 2.2 Multiplayer Games
**Technical Analysis**:
In games with 3+ players (A, B, C), a single value isn't enough. We use a **Utility Vector** $\langle v_A, v_B, v_C \rangle$.
*   At a node where player C moves, C chooses the action that maximizes the $3^{rd}$ component of the vector (their own score).
*   **Alliances**: Players in weak positions might cooperate (implicitly or explicitly) to attack a strong player, emerging from selfish optimization.

**Child-Friendly Explanation**:
Imagine a 3-player video game. If Player A is super strong, Players B and C might stop fighting each other and team up to beat A first. They do this selfishly to survive, not because they are friends!

***

## Topic 3: Alpha-Beta Pruning
<img src="Sources/alphabeta.png" alt="A screenshot" width="400" height="200">
### 3.1 The Concept
**Technical Analysis**:
Alpha-Beta Pruning returns the **exact same result** as Minimax but runs faster by ignoring (pruning) branches that don't affect the decision.
*   **$\alpha$ (Alpha)**: The best (highest) value MAX has found so far.
*   **$\beta$ (Beta)**: The best (lowest) value MIN has found so far.
*   **Pruning Condition**:
    *   **Beta Cutoff**: At a MAX node, if value $\geq \beta$, stop. (MIN won't let us get here).
    *   **Alpha Cutoff**: At a MIN node, if value $\leq \alpha$, stop. (MAX won't choose this path).

**Child-Friendly Explanation (The Shopping Trip)**:
You (MAX) want a cool toy. Dad (MIN) wants to spend the least money.
1.  Store A has a toy for **\$50**. You know you can get at least this. ($\alpha = 50$).
2.  Store B's first toy costs **\$20**.
3.  **STOP!** Don't check the rest of Store B. Dad will pick the \$20 toy (or something even cheaper). Since \$20 is worse than the \$50 you already found, you will never go to Store B.

### 3.2 Diagram (Text-Based)
```text
       [Root MAX] 
      /     |    
     /      |    (Pruned)
  [B: MIN] [C: MIN] ---X--- [D]
   /  \      /  
  3   12    2    (x, y skipped)
  
1. Root checks B. B sees 3 and 12. B picks 3. Root has Alpha=3.
2. Root checks C. C sees 2. 
3. Since 2 < 3, Root knows C is bad.
4. Root STOPS checking C's other children (x, y). They are PRUNED.
```

***

## Topic 4: Move Ordering & Advanced Search

### 4.1 Move Ordering
**Technical Analysis**:
The order in which you check moves matters. If you check the best moves first, Alpha-Beta is much more efficient ($O(b^{m/2})$).
*   **Killer Move Heuristic**: The move that caused a cutoff at the same depth in a previous search is likely to be good again. Try it first.
*   **Iterative Deepening**: Search depth 1, then 2, then 3... Use the best move from depth $d-1$ as the first guess for depth $d$.
*   **Transposition Tables**: A hash table (cache) storing previous board states so you don't re-analyze the same position reached via a different path.

**Child-Friendly Explanation**:
If you are looking for your lost keys, do you search the whole house randomly? No! You check the "most likely" places first (pockets, table). If you find them there, you save hours of searching. Move ordering is just "checking the best spots first."

### 4.2 Heuristic Alpha-Beta Search
**Technical Analysis**:
We can't search to the very end of Chess. We stop early and guess.
*   **H-MINIMAX**: Replaces `UTILITY(s)` with `EVAL(s)` when depth limit is reached.
*   **Cutoff Test**: Replaces `IS-TERMINAL(s)`. Returns true if depth > limit or time is up.

***

## Topic 5: Evaluation Functions

### 5.1 Weighted Linear Functions
**Technical Analysis**:
How do we guess who is winning? We use features $f_i$ (e.g., number of pawns) and weights $w_i$.
$$ \text{EVAL}(s) = w_1 f_1(s) + w_2 f_2(s) + \dots + w_n f_n(s) $$
*   Example (Chess): Pawn=1, Bishop=3, Rook=5, Queen=9.
*   **Machine Learning**: Modern engines learn these weights from millions of games.

**Child-Friendly Explanation**:
How do you know who is winning a soccer game if the score is 0-0? You look at "clues": Who has the ball more? Who is shooting more? You give points for these clues to guess the winner.

***

## Topic 6: Cutting Off Search (Common Problems)

### 6.1 Quiescence Search
**Technical Analysis**:
Don't stop the search in the middle of a "wild" exchange (e.g., in the middle of a capture sequence). The evaluation will be wrong.
*   **Solution**: Continue searching only "noisy" moves (captures) until the board is "quiet" (quiescent).

### 6.2 The Horizon Effect
**Technical Analysis**:
The program sees a bad event (loss of a Queen) coming at depth 6. It makes a silly move (sacrificing a pawn) to push the Queen loss to depth 8 (beyond its "horizon"). It thinks it saved the Queen, but it just delayed the inevitable and lost a pawn too.
*   **Solution**: **Singular Extensions**. If one move is clearly better, search it deeper than others.

**Child-Friendly Explanation**:
Imagine you have to clean your room by 5 PM. You throw a tantrum to delay it. You think "Yay, I don't have to clean right now!" but actually, you just have to clean later *and* you're in trouble for the tantrum. You just pushed the problem "over the horizon."

***

## Topic 7: Forward Pruning (Risky Search)

### 7.1 Beam Search & PROBCUT
**Technical Analysis**:
Standard Alpha-Beta is "safe" (it never misses the best move). **Forward Pruning** is "risky" (it ignores moves that *look* bad but might be good).
*   **Beam Search**: Only keep the top $n$ best moves at each level.
*   **PROBCUT (Probabilistic Cut)**: Uses statistics to prune branches that are *probably* (but not surely) worse than Alpha/Beta.
*   **Late Move Reduction**: If move ordering is good, moves late in the list are probably bad. Search them with less depth to save time.

**Child-Friendly Explanation**:
Instead of reading every book in the library to find a fact, you only read the books with "Science" in the title. You *might* miss a fact hidden in a "History" book, but you save a lot of time.

***

## Topic 8: Search vs. Lookup

### 8.1 Opening Books & Endgame Databases
**Technical Analysis**:
*   **Opening Books**: For the first 10-15 moves, computers don't search. They look up the best moves from a database of human expert games.
*   **Endgame Databases**: Computers have "solved" endgames with few pieces (e.g., 7 pieces). They know the perfect move for every single position by working backward from checkmate (Retrograde Analysis).

**Child-Friendly Explanation**:
*   **Opening**: Like memorizing the answers to a spelling test. You don't have to "think" about how to spell "Cat", you just know it.
*   **Endgame**: Like a map. If there are only a few pieces left, the computer has a perfect map that shows exactly how to win from anywhere.

***

### Final Summary Table
| Topic | Key Concept | Child-Friendly Analogy |
| :--- | :--- | :--- |
| **Game Theory** | Modeling conflict & decisions. | Tug-of-War (Zero-Sum). |
| **Minimax** | Maximize gain, assuming opponent minimizes it. | Sharing a cake with a greedy brother. |
| **Alpha-Beta** | Pruning useless branches. Exact same result as Minimax. | Stopping shopping once you find a "good enough" price. |
| **Horizon Effect** | Delaying inevitable loss beyond search depth. | Throwing a tantrum to delay chores. |
| **Quiescence** | Searching until the board is stable. | Waiting for the dust to settle before judging. |

[1](https://ppl-ai-file-upload.s3.amazonaws.com/web/direct-files/attachments/68867823/c503cf35-48da-436b-88d7-58db65c6824a/3.pdf)