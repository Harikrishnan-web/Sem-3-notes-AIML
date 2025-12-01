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


