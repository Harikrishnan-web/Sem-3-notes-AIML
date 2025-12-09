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



