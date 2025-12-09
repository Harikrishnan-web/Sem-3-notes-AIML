# **SECTION 1 — PARALLEL DATABASES (EXTREMELY DETAILED)**

---

## **1.1 Definition and Concept**

A **Parallel Database System** is a database system built on **multiple processors connected through a parallel computing architecture** working simultaneously to execute queries, store data, and process transactions.
Its goal is to achieve **High Throughput, Reduced Response Time, Scalability, and Fault Tolerance**.

➡ Keyword: **Parallel DB = Divide Work + Execute Simultaneously + Merge Results**

---

## **1.2 Evolution of Parallel Databases**

| Generation       | Features                          |
| ---------------- | --------------------------------- |
| Traditional DBMS | Single CPU                        |
| Client-Server DB | Multiple clients accessing server |
| Parallel DBMS    | Multi-processor execution         |
| Cloud-scale DB   | Elastic scaling                   |

Parallel DBs arose because:

* Data size grew from **GB → TB → PB**
* Single CPU systems became bottlenecks
* Businesses required **real-time analytics**

---

## **1.3 Why Parallel Processing Is Required?**

| Need                         | Explanation              |
| ---------------------------- | ------------------------ |
| Large scale data → Big Data  | Social media, e-commerce |
| Real-time analytics          | Stock market, IoT        |
| Faster decision making       | AI/ML                    |
| Cloud + distributed business | Global organizations     |
| Cost reduction               | commodity hardware       |

➡ Parallel DBs are foundation for: **Google Search, Facebook, Amazon Analytics, Banking**

---

## **1.4 Architecture of Parallel Databases (Full Detailed)**

Parallel DB architecture depends on how **processors share memory and disks**.

---

### **1.4.1 Shared Memory Architecture**

* All processors share **one main memory & one disk**
* Multiple CPUs but **single address space**
* Locking & buffer management shared

**Advantages**

* Fast communication
* Easy database programming
* Low latency access

**Disadvantages**

* Not scalable beyond limited processors
* Memory contention → bottleneck

**Use Cases**: Small enterprises, low data OLTP, vertical servers

---

### **1.4.2 Shared Disk Architecture**

* Each processor has **local memory** but **shared disk**
* Multiple CPUs access same storage → cluster environment

**Advantages**

* High availability → if one node fails, others continue
* Easier load redistribution

**Disadvantages**

* Disk becomes contention bottleneck
* Expensive shared storage infrastructure

**Used In:** Oracle RAC, IBM Cluster File System

---

### **1.4.3 Shared Nothing Architecture (MOST IMPORTANT)**

* Independent **node = CPU + Memory + Disk**
* Nodes communicate via network
* No sharing → only messages

**Benefits**

| Feature             | Benefit            |
| ------------------- | ------------------ |
| No resource sharing | No bottleneck      |
| Add nodes cheaply   | Linear scalability |
| Best for Big Data   | Cloud scale        |

➡ Used by **Hadoop, Cassandra, HBase, Google BigQuery, Amazon Dynamo**

**Drawback**

* Expensive inter-node communication
* Complex query planning

---

### **1.4.4 Hierarchical / Hybrid Architecture**

* Combination of shared-nothing + shared-disk
* Designed for custom workloads

**Example:** Databases in cloud + on-premise mix

---

## **1.5 Types of Parallelism in Databases (VERY IMPORTANT)**

| Type                        | Meaning                        | Example        |
| --------------------------- | ------------------------------ | -------------- |
| **Inter-query parallelism** | Different queries run parallel | Multiple users |
| **Intra-query parallelism** | One query executed in parts    | Large SELECT   |
| **Inter-operator**          | Pipeline: output → next        | Filter → Join  |
| **Intra-operator**          | Single operator parallel       | Parallel join  |

➡ Intra-operator is the heart of parallel query optimization.

---

## **1.6 Data Storage Management in Parallel DB**

### **1.6.1 Data Partitioning**

Partition = Divide table into fragments to store parallelly.

| Type       | Concept       | Use              |
| ---------- | ------------- | ---------------- |
| Horizontal | rows split    | Distributed load |
| Vertical   | columns split | Reduce I/O       |
| Range      | value based   | Salary/Date      |
| Hash       | hash(key)     | Uniform load     |
| Composite  | mix           | Cloud DB         |

### **1.6.2 Problems in Partitioning**

| Problem                  | Result               |
| ------------------------ | -------------------- |
| Data skew                | few nodes overloaded |
| Hotspot                  | repeated access      |
| Uneven hash distribution | imbalance            |

➡ Solution: **Dynamic repartitioning**, Cost-based planning.

---

### **1.6.3 Replication**

* Keep copies for **availability**
* Improves **read**, increases **update cost**

| Type           | Feature            |
| -------------- | ------------------ |
| Full           | High speed, costly |
| Partial        | Balanced           |
| No replication | Faster writes      |

---

### **1.6.4 Parallel Indexing**

* Global index: across nodes
* Local index: per partition
* Bitmap index: low cardinality columns

---

## **1.7 Parallel Transaction Processing**

### **Transaction Problems in Parallel DB**

* Deadlock
* Lost updates
* Inconsistent reads
* Non-serializable cycles

➡ Need concurrency control.

---

### **Concurrency Control Methods**

| Method             | Concept                       |
| ------------------ | ----------------------------- |
| 2PL                | Acquire locks → release later |
| Timestamp ordering | Assign time ordering          |
| Optimistic         | Detect conflict late          |

---

### **Commit Protocols**

| Protocol | Phases           | Issue        |
| -------- | ---------------- | ------------ |
| **2PC**  | Vote → Commit    | Blocking     |
| **3PC**  | Added Pre-commit | Non-blocking |

---

## **1.8 Parallel Query Processing and Optimization**

### Stages

1. Query Parsing
2. Logical Optimization
3. Parallel Execution Plan
4. Scheduling
5. Result merging

---

### Parallel Join Algorithms (**MOST EXAM ASKED**)

| Join                | When used          |
| ------------------- | ------------------ |
| Hash partition join | Large data         |
| Repartition join    | No prior partition |
| Broadcast join      | Small table        |
| Sort merge          | Sorted data        |

---

### **Issues in Parallel Querying**

| Issue            | Description          |
| ---------------- | -------------------- |
| Data skew        | Uneven work          |
| Load balancing   | Must allocate fairly |
| Network overhead | expensive            |
| Synchronization  | waiting problem      |

---

## **1.9 Fault Tolerance in Parallel DB**

* Checkpoint
* Log-based recovery
* Commit protocols
* Replication

---

## **1.10 Advantages & Disadvantages**

| Advantages       | Disadvantages     |
| ---------------- | ----------------- |
| High speed       | Complex           |
| Scalability      | Expensive network |
| Large DB support | Skilled design    |
| Load balance     | Debugging hard    |

---
## 🔥 **SECTION 2 — DISTRIBUTED DATABASES (EXTREMELY DETAILED — ALL SUBTOPICS COVERED)**

---

# **2.1 INTRODUCTION**

A **Distributed Database System (DDBMS)** is a collection of **logically related databases** distributed across multiple **geographical locations**, connected through a **communication network**, but functioning as a **single unified system**.

➡ **KEY CONCEPT:**
**Distributed DB = Stored at many sites BUT behaves like one database**

---

# **2.2 GOALS OF DISTRIBUTED DATABASES**

| Goal                 | Description                     |
| -------------------- | ------------------------------- |
| Reliability          | If one node fails, system works |
| Availability         | Data accessible anytime         |
| Local autonomy       | Each site controls its data     |
| Improved performance | Local queries faster            |
| Scalability          | Add new sites easily            |
| Resource sharing     | Share CPU, disk, network        |

➡ Supports modern **global organizations, e-commerce, cloud applications**.

---

# **2.3 FEATURES OF DISTRIBUTED DATABASES**

* **Location transparency** → User doesn’t need to know where data stored
* **Replication transparency** → Copies managed automatically
* **Fragmentation transparency** → Data divided but accessed fully
* **Concurrent access management**
* **Distributed query optimization**
* **Distributed recovery**

➡ **Transparency = The system hides complexity from users**

---

# **2.4 ARCHITECTURE OF DISTRIBUTED DATABASES**

Distributed systems differ by how nodes are organized and controlled.

---

## **2.4.1 Types of Distributed DB Systems**

| Type                    | Description            |
| ----------------------- | ---------------------- |
| **Homogeneous DDBMS**   | Same DBMS at all sites |
| **Heterogeneous DDBMS** | Different DBMS & OS    |
| **Federated**           | Partial sharing        |
| **Multidatabase**       | Fully independent DB   |

---

## **2.4.2 Architectural Models**

| Model             | Explanation                      |
| ----------------- | -------------------------------- |
| **Client/Server** | Server stores DB, client queries |
| **Peer-to-Peer**  | All nodes equal                  |
| **Multi-tier**    | Middleware                       |
| **Cloud-based**   | Virtual nodes                    |

➡ Modern systems use **cloud-based distributed DB**

---

# **2.5 DISTRIBUTED DATABASE DESIGN**

Design components:

| Concept       | Meaning         |
| ------------- | --------------- |
| Fragmentation | Divide table    |
| Replication   | Copy fragments  |
| Allocation    | Assign to sites |

---

## **2.5.1 Fragmentation**

Fragmentation = Breaking a relation into smaller pieces.

| Type                         | Meaning                    | Reconstruction |
| ---------------------------- | -------------------------- | -------------- |
| **Horizontal fragmentation** | Rows divided               | UNION          |
| **Vertical fragmentation**   | Columns divided            | JOIN           |
| **Mixed fragmentation**      | Both horizontal + vertical | Both           |

➡ Example: Store branch employees at location branch.

---

## **2.5.2 Replication**

Replication = Storing copies of fragments at multiple sites.

| Replication Type        | Advantage   | Disadvantage     |
| ----------------------- | ----------- | ---------------- |
| **Full replication**    | Fast reads  | High update cost |
| **Partial replication** | Balanced    | Some delay       |
| **No replication**      | Fast writes | Low availability |

➡ Replication improves reliability but increases update cost.

---

## **2.5.3 Data Allocation**

* Centralized allocation
* Fragment allocation
* Replicated allocation
* Dynamic allocation (AI-based allocation)

➡ System decides where to place each fragment.

---

# **2.6 DISTRIBUTED TRANSACTION PROCESSING**

Transaction in distributed DB may access multiple sites.

➡ **Local Transaction** → one site
➡ **Global Transaction** → multiple sites through **coordinator**

---

## **2.6.1 Responsibilities in Distributed Transaction**

| Component              | Role               |
| ---------------------- | ------------------ |
| Coordinator            | Manage transaction |
| Subordinate sites      | Execute part       |
| Log manager            | Recovery logs      |
| Commit protocol engine | Controls commit    |

---

## **2.6.2 Distributed Concurrency Control**

Problems occur due to:

* Lost update
* Inconsistent reads
* Dirty reads
* Phantoms

Methods:

| Method          | Concept         |
| --------------- | --------------- |
| Distributed 2PL | Lock at sites   |
| Timestamp       | Based on TS     |
| Optimistic      | Validate later  |
| Quorum-Based    | Majority voting |

---

## **2.6.3 Replication Concurrency Problems**

| Problem              | Explanation |
| -------------------- | ----------- |
| Write-write conflict | Two updates |
| Write-read conflict  | Dirty read  |
| Read-read conflict   | Consistency |

➡ Quorum read/write solves conflicts:
`R + W > N`

---

# **2.7 DISTRIBUTED COMMIT PROTOCOLS**

---

## **Two-Phase Commit (2PC)**

| Phase   | Operation       |
| ------- | --------------- |
| Phase 1 | Prepare (vote)  |
| Phase 2 | Commit or Abort |

➡ **Disadvantage:** Blocking — site waits.

---

## **Three-Phase Commit (3PC)**

Adds **Pre-Commit phase**
➡ Non-blocking
➡ More network messages → cost

---

# **2.8 DISTRIBUTED QUERY PROCESSING**

Goals:

* Reduce communication
* Reduce response time
* Minimize remote access

Steps:

1. Query decomposition
2. Data localization
3. Global optimization
4. Execution strategy

---

## **Distributed Query Optimization Methods**

| Optimization      | Approach                |
| ----------------- | ----------------------- |
| Rule-based        | Using heuristics        |
| Cost-based        | Based on cost           |
| Semi-join         | Reduce transferred data |
| Bloom filter join | Filter early            |

➡ **Semi-join** is used to reduce network traffic.

---

# **2.9 DISTRIBUTED DATABASE — ADVANTAGES & DISADVANTAGES**

| Advantages              | Disadvantages        |
| ----------------------- | -------------------- |
| Local autonomy          | Very complex         |
| High availability       | Expensive            |
| Faster local processing | Deadlock risk        |
| Reliability             | Security difficult   |
| Scalable                | Replication conflict |

---
## 🔥 SECTION 3 — **NoSQL Databases (FULL + DETAILED)**

---

# **3.1 INTRODUCTION TO NOSQL**

**NoSQL** stands for **“Not Only SQL"**, referencing a class of database systems that **do not follow the traditional relational model** and **do not use fixed schema tables**.
They are designed for:

* **Big Data**
* **Distributed data storage**
* **High availability**
* **Horizontal scaling**
* **Unstructured / Semi-structured data**

➡ **KEY CONCEPT:**
Relational DB scales **vertically** (bigger machine)
NoSQL DB scales **horizontally** (more machines)

Examples: **MongoDB, Cassandra, Redis, Neo4j, DynamoDB**

---

# **3.2 Why NoSQL? (Need)**

Traditional SQL fails when:

* Data is **unstructured (JSON, video, logs, IoT streams)**
* DB size becomes petabytes
* Cloud-scale users (Millions of users simultaneously)

| SQL DB          | NoSQL DB    |
| --------------- | ----------- |
| Fixed schema    | Schema-less |
| Join operations | No joins    |
| Vertical scale  | Horizontal  |
| ACID            | BASE        |
| Single server   | Clusters    |

➡ Designed for **Web, Mobile, ML Analytics, IoT**

---

# **3.3 CHARACTERISTICS OF NOSQL DATABASES**

| Feature          | Description             |
| ---------------- | ----------------------- |
| Schema-less      | JSON or key-value pairs |
| Horizontal scale | Add servers easily      |
| Replication      | Built-in                |
| No join overhead | Faster                  |
| BASE principle   | Eventual consistency    |
| Polyglot         | Use multiple DB types   |

---

# **3.4 ACID vs BASE (IMPORTANT)**

| Property     | ACID (RDBMS) | BASE (NoSQL) |
| ------------ | ------------ | ------------ |
| Consistency  | Immediate    | Eventual     |
| Availability | Medium       | High         |
| Scalability  | Vertical     | Horizontal   |
| Transactions | Relational   | Distributed  |
| Guarantee    | Strong       | Approximate  |
| Model        | Traditional  | Big Data     |

➡ **BASE** = **Basically Available, Soft State, Eventually Consistent**

---

# **3.5 TYPES OF NOSQL DATABASES**

---

## **3.5.1 KEY-VALUE DATABASES**

| Feature   | Value                  |
| --------- | ---------------------- |
| Structure | key → value            |
| Speed     | Very fast              |
| Use Case  | Cache, sessions        |
| Example   | Redis, Amazon DynamoDB |

➡ Works like **hashmap on steroids**.

---

## **3.5.2 DOCUMENT DATABASES**

| Item        | Description      |
| ----------- | ---------------- |
| Data Format | JSON / BSON      |
| Query       | Document search  |
| Feature     | Embedded docs    |
| Example     | MongoDB, CouchDB |

➡ Best for **Web apps, API databases**

---

## **3.5.3 COLUMN-FAMILY DATABASES**

| Item      | Description             |
| --------- | ----------------------- |
| Structure | Column groups           |
| Query     | Column-wise read        |
| Strength  | Analytics               |
| Example   | Apache Cassandra, HBase |

➡ Used by **Netflix, Spotify, Facebook**

---

## **3.5.4 GRAPH DATABASES** *(More deep in SECTION 5)*

| Feature   | Description     |
| --------- | --------------- |
| Structure | Nodes + Edges   |
| Use       | Social networks |
| Example   | Neo4j           |

➡ Relationship-first database.

---

# **3.6 INTERNAL STORAGE MODEL OF NOSQL**

| Model     | How stores     |
| --------- | -------------- |
| Key–Value | Hash table     |
| Document  | JSON store     |
| Column    | SSTables       |
| Graph     | Adjacency list |

➡ NoSQL uses **shared-nothing architecture** → massively scalable.

---

# **3.7 Advantages & Disadvantages**

| Advantages           | Disadvantages          |
| -------------------- | ---------------------- |
| Scales horizontally  | No standard interface  |
| High availability    | Weak consistency       |
| Handles unstructured | Complex to query       |
| Fast processing      | Limited ad hoc queries |

➡ Trade-off based on **CAP**, covered next.

---

# **3.8 USE CASES OF NoSQL**

| Domain       | Use                 |
| ------------ | ------------------- |
| Social media | Graph relations     |
| Banking      | Fraud analytics     |
| Gaming       | Live leaderboards   |
| IoT          | Sensor data         |
| E-commerce   | Recommendations     |
| ML           | Model training data |

---
## 🔥 SECTION 4 — CAP THEOREM (FULL + DETAILED + REAL-WORLD EXAMPLES)

---

# **4.1 Introduction to CAP Theorem**

The **CAP Theorem** (Brewer’s Theorem) states:

📌 **A distributed database can guarantee ONLY TWO out of the following THREE properties at the same time**:

| C | Consistency |
| A | Availability |
| P | Partition Tolerance |

➡ When a network failure occurs (partition), system **must sacrifice either Consistency or Availability**.

---

# **4.2 CAP Theorem Components (Detailed)**

---

### **4.2.1 Consistency**

➡ Every read receives the **most recent write**.

Example:
If `A → Balance is updated`, every user sees the new balance.

| SQL RDBMS | Supports strong consistency |
| NoSQL AP DB | Eventual |

---

### **4.2.2 Availability**

➡ Every request receives a response — **even if old or stale**.

If one node fails → another returns older copy but provides answer.

Example: **Shopping site shows yesterday’s available stock rather than no result**

---

### **4.2.3 Partition Tolerance**

➡ System continues functioning even if nodes **cannot communicate** due to network failure (partition).

Example:

* Node in USA cannot reach node in India because network cable breakdown
* System must operate independently

➡ Partition tolerance is **mandatory in global distributed systems**.

---

# **4.3 CAP Triangle (Explain like diagram)**

```
          Consistency (C)
              /\
             /  \
            /    \
           /      \
Availability ------ Partition Tolerance
                     (A)                  (P)
```

➡ A system **cannot sit in the center**; choices are required.

---

# **4.4 CAP Trade-Off Combinations**

| Combination | Meaning                                   |
| ----------- | ----------------------------------------- |
| **CA**      | Consistency + Availability (no partition) |
| **CP**      | Consistency + Partition Tolerance         |
| **AP**      | Availability + Partition Tolerance        |

---

## **4.4.1 CA System (Consistency + Availability)**

* Works only if there are **no partitions**
* **Centralized databases**
* Rare in real world

Example:
**Single server SQL database**

➡ When network fails → SYSTEM FAILS, not acceptable.

---

## **4.4.2 CP System (Consistency + Partition Tolerance)**

➡ System sacrifices availability but keeps accuracy.

Example:

* **MongoDB (when configured as CP)**
* **Google BigTable**
* **HBase**
* **Redis (cluster mode)**

Use case: **Banking, Stock Control**

➡ Better to **delay response** than return wrong data.

---

## **4.4.3 AP System (Availability + Partition Tolerance)**

➡ Always responds but data may be temporary inconsistent.

Examples:

* **Cassandra**
* **DynamoDB**
* **Riak**

Real use: **Social media likes count, cached timeline**
➡ Seeing 100 likes instead of 102 is acceptable.

---

# **4.5 CAP in Real-World System Designs**

| System         | CAP Choice | Why                    |
| -------------- | ---------- | ---------------------- |
| Banking        | CP         | Must be correct        |
| YouTube Views  | AP         | Count can update later |
| Amazon Cart    | AP         | Always visible         |
| ATMs           | CP         | Consistent balance     |
| Messaging Apps | AP         | Temporary offline OK   |

---

# **4.6 Relation Between CAP & BASE**

| Term                 | Part of CAP             | Related NoSQL concept |
| -------------------- | ----------------------- | --------------------- |
| Eventual consistency | Sacrifice Consistency   | BASE                  |
| High availability    | Guarantee response      | AP                    |
| Partition tolerance  | Required in distributed | NoSQL                 |

➡ BASE model chosen because **eventual consistency acceptable** in most modern web applications.

---



