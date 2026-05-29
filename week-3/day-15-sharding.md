# Day 15: Database Sharding

> 🗓️ Day 15 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is Database Sharding?

**Sharding** is the process of splitting a large database into smaller, more manageable pieces called **shards**, and distributing them across multiple servers. Each shard holds a subset of the total data, and together they form the complete dataset.

> **Partitioning** organizes data inside one database. **Sharding** distributes data across multiple databases/servers.

## 📚 The Library Analogy

|Scenario            |What Happens                                                    |
|--------------------|----------------------------------------------------------------|
|**Without Sharding**|One giant library with 10M books. Everyone crowds in. Slow.     |
|**With Sharding**   |3 branch libraries: A-I, J-R, S-Z. Go to the relevant one. Fast.|

## 🔑 Key Terms

|Term                   |Definition                                            |
|-----------------------|------------------------------------------------------|
|**Shard**              |A smaller chunk of the full database                  |
|**Shard Key**          |The column used to decide which shard a row belongs to|
|**Horizontal Sharding**|Split rows across servers (most common)               |
|**Vertical Sharding**  |Split columns across servers                          |
|**Logical Shard**      |The data partition itself                             |
|**Physical Shard**     |The server that stores the logical shard              |

## 🎯 Sharding Strategies

### 1. Range-Based Sharding

- **How:** Split by value ranges of the shard key
- **Example:** Users A-I → Shard 1, J-R → Shard 2, S-Z → Shard 3
- **Pros:** Simple to implement, good for range queries
- **Cons:** Can create hotspots (uneven distribution)

### 2. Hash-Based Sharding

- **How:** Apply a hash function to the shard key
- **Example:** `hash(user_id) % 3` = shard number (0, 1, or 2)
- **Pros:** Even distribution of data across shards
- **Cons:** Range queries become difficult, resharding is complex

### 3. Directory-Based Sharding

- **How:** A lookup table maps each record to its shard
- **Example:** Lookup: user 123 → Shard 2, user 456 → Shard 1
- **Pros:** Very flexible, any mapping strategy possible
- **Cons:** Lookup table becomes a bottleneck and single point of failure

### 4. Geographic Sharding

- **How:** Split by user location or region
- **Example:** US data → US shard, EU data → EU shard, Asia → Asia shard
- **Pros:** Low latency for regional users, data residency compliance
- **Cons:** Uneven distribution if traffic varies by region

## ⚙️ How Sharding Works — Step by Step

```
Step 1: Choose a shard key (e.g., user_id)
Step 2: Apply a sharding strategy (hash, range, directory)
Step 3: When a write comes in → route to the correct shard
Step 4: Each shard stores only its subset of data
Step 5: When a query comes in → app determines which shard to ask
```

## ⚠️ Challenges of Sharding

|Challenge              |Description                                   |Mitigation                                      |
|-----------------------|----------------------------------------------|------------------------------------------------|
|**Cross-shard queries**|JOINs across shards are slow and complex      |Design schema to minimize cross-shard needs     |
|**Hotspots**           |One shard gets disproportionate traffic       |Use hash-based sharding for even distribution   |
|**Rebalancing**        |Adding/removing shards requires data migration|Use consistent hashing to minimize data movement|
|**Complexity**         |App must know which shard to query            |Use a routing layer or proxy                    |
|**Transactions**       |ACID across shards is extremely difficult     |Use saga pattern or accept eventual consistency |

## 📊 Sharding vs Partitioning vs Replication

|Aspect   |Sharding                 |Partitioning                |Replication                    |
|---------|-------------------------|----------------------------|-------------------------------|
|**What** |Split data across servers|Split data within one server|Copy data to multiple servers  |
|**Why**  |Handle massive datasets  |Improve query performance   |High availability, read scaling|
|**Where**|Multiple database servers|Single database server      |Multiple copies of same data   |

## 🌍 Real-World Examples

|Company      |Shard Key        |Strategy                                           |
|-------------|-----------------|---------------------------------------------------|
|**Instagram**|`user_id`        |Hash-based — each shard holds a group of users     |
|**Uber**     |Geographic region|Geographic — US, EU, Asia on separate shards       |
|**Discord**  |`guild_id`       |Hash-based — each Discord server on its own shard  |
|**Amazon**   |Product category |Range-based — electronics, books, clothes separated|
|**MongoDB**  |Configurable     |Built-in sharding with automatic balancing         |

## 🔗 How This Connects to Previous Concepts

|Day   |Concept           |Connection                                  |
|------|------------------|--------------------------------------------|
|Day 4 |SQL vs NoSQL      |NoSQL databases often have built-in sharding|
|Day 5 |Horizontal Scaling|Sharding IS horizontal scaling for databases|
|Day 8 |Load Balancers    |Route queries to the correct shard          |
|Day 12|Indexing          |Each shard has its own indexes              |
|Day 13|Replication       |Each shard can also be replicated for safety|

## 💡 Key Takeaways

1. **Sharding = splitting rows across multiple database servers**
1. **Shard key** decides where each piece of data lives
1. **Hash-based** gives the most even distribution
1. **Don’t shard prematurely** — it adds significant complexity
1. Many real systems use **sharding + replication + indexing** together

## 🔗 Resources

- [Database Sharding — AWS](https://aws.amazon.com/what-is/database-sharding/)
- [Database Sharding — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/database-sharding-a-system-design-concept/)
- [Sharding vs Partitioning — DataCamp](https://www.datacamp.com/blog/sharding-vs-partitioning)
- [Sharding Guide — Design Gurus](https://www.designgurus.io/answers/detail/what-is-data-partitioning-and-what-are-common-strategies-for-partitioning-data)

## ➡️ What’s Next?

**Day 16: CAP Theorem** — You can’t have it all. Every distributed system must choose between Consistency, Availability, and Partition Tolerance. Understanding CAP is key to designing reliable systems.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
