---

## **1. Introduction to Artificial Intelligence (AI)**

### **1.1 What is Artificial Intelligence?**

Artificial Intelligence (AI) is a branch of computer science that **makes machines intelligent**.

**In very simple words:**
AI teaches machines **how to think, learn, decide, and solve problems** like humans.

**Formal definition (exam keyword):**

> Artificial Intelligence is the study of creating intelligent machines that can perceive their environment, reason, learn, and take actions to achieve goals.

### **What makes a machine intelligent?**

An AI machine can:

* Learn from experience
* Reason logically
* Solve problems
* Make decisions
* Understand language
* Perceive the world (vision, sound)

### **Why AI is important?**

* Solves complex real‑world problems
* Works faster and more accurately than humans
* Operates in dangerous places
* Reduces human effort
* Forms the base for future technologies

---

## **2. Agents and Environments**

### **2.1 What is an Agent?**

An **agent** is anything that:

* **Perceives** its environment using sensors
* **Acts** on the environment using actuators

**Simple example:**
A human sees with eyes (sensors) and moves hands (actuators).

### **Agent Cycle (Very Important)**

Perceive → Think → Act → Repeat

### **Examples of Agents**

| Agent          | Sensors           | Actuators     |
| -------------- | ----------------- | ------------- |
| Human          | Eyes, ears        | Hands, legs   |
| Robot          | Camera, IR sensor | Motors        |
| Software agent | Keyboard, files   | Screen output |

---

### **2.2 Sensors, Actuators, Effectors**

**Sensor:**

* Detects changes in the environment
* Examples: camera, microphone, keyboard

**Actuator:**

* Converts energy into movement or action
* Examples: motors, wheels, speakers

**Effectors:**

* Parts that directly affect the environment
* Examples: arms, legs, wheels, display screen

---

### **2.3 Environment**

The **environment** is everything **outside the agent**.

It provides:

* Information to sense
* Space to act

**Example:**
For a vacuum cleaner agent, the room is the environment.

---

## **3. Concept of Rationality**

### **3.1 What is a Rational Agent?**

A **rational agent** always chooses the **best possible action** to maximize its success.

**In child language:**
A rational agent always tries to **do the right thing at the right time**.

### **Rational Action**

An action is rational if it:

* Maximizes performance measure
* Uses available information
* Considers past percepts

### **Rationality depends on:**

1. Performance measure
2. Agent’s knowledge of environment
3. Available actions
4. Percept sequence

⚠️ Rational ≠ Perfect (agent works with what it knows)

---

## **4. Nature of Environments**

An environment can be classified based on how it behaves from the agent’s point of view.

### **4.1 Fully Observable vs Partially Observable**

* **Fully observable:** Agent sees complete environment
* **Partially observable:** Agent sees only part of environment

Example:

* Chess → Fully observable
* Driving → Partially observable

---

### **4.2 Deterministic vs Stochastic**

* **Deterministic:** Same action → Same result
* **Stochastic:** Same action → Different results

Example:

* Chess → Deterministic
* Weather system → Stochastic

---

### **4.3 Episodic vs Sequential**

* **Episodic:** Each action independent
* **Sequential:** Current action affects future

Example:

* Image classification → Episodic
* Chess → Sequential

---

### **4.4 Static vs Dynamic**

* **Static:** Environment does not change while thinking
* **Dynamic:** Environment changes continuously

Example:

* Crossword → Static
* Taxi driving → Dynamic

---

### **4.5 Discrete vs Continuous**

* **Discrete:** Finite states and actions
* **Continuous:** Infinite states/actions

Example:

* Chess → Discrete
* Self‑driving car → Continuous

---

### **4.6 Single‑Agent vs Multi‑Agent**

* **Single‑agent:** Only one agent
* **Multi‑agent:** Multiple agents interact

Example:

* Puzzle → Single‑agent
* Football game → Multi‑agent

---

## **5. Structure of an AI Agent**

### **Agent Structure Formula (Very Important)**

> **Agent = Architecture + Agent Program**

### **Architecture**

* Physical hardware or software platform
* Examples: robot body, computer system

### **Agent Function**

* Maps percepts to actions
* Representation:

f : P* → A

### **Agent Program**

* Implementation of agent function
* Runs on architecture

---

## **6. Problem Solving Agents**

### **6.1 What is a Problem‑Solving Agent?**

A problem‑solving agent is a **goal‑based agent** that:

* Defines a problem
* Searches for a solution
* Executes actions to reach the goal

### **Examples of Problems**

* Chess
* Tower of Hanoi
* Water Jug problem
* N‑Queen problem

---

### **6.2 Steps in Problem Solving**

1. Define initial state
2. Define goal state
3. Define actions
4. Search solution
5. Execute action sequence

---

### **6.3 Measuring Problem‑Solving Performance**

**Completeness:**

* Will it always find a solution if one exists?

**Optimality:**

* Will it find the best solution?

**Time Complexity:**

* How long does it take?

**Space Complexity:**

* How much memory does it use?

---


