# Day 16: CAP Theorem

> 🗓️ Day 16 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is the CAP Theorem?

The **CAP Theorem** (Brewer’s Theorem) states that a distributed system can guarantee only **two out of three** properties at the same time: **Consistency**, **Availability**, and **Partition Tolerance**.

> Introduced by Eric Brewer in 2000 and formally proven by Gilbert and Lynch in 2002.

## 🏧 The ATM Analogy

Imagine two ATMs connected to one bank. The network between them breaks.

You withdraw $80 from ATM 1. Balance: $20. But ATM 2 still shows $100 — it can’t sync.

|Choice               |What Happens                                                     |Who Chooses This|
|---------------------|-----------------------------------------------------------------|----------------|
|**CP (Consistency)** |Block ATM 2 until sync is fixed. Correct data, but ATM 2 is DOWN.|Banks           |
|**AP (Availability)**|Let ATM 2 keep working. Both work, but data is STALE.            |Social media    |

**You MUST tolerate partitions (P).** So the real choice is: C or A.

## 🔤 What C, A, P Mean

### C — Consistency

Every read receives the **most recent write** or an error. All nodes see the same data at the same time.

**Example:** After you update your bank balance, every system shows the new balance immediately.

### A — Availability

Every request receives a **response** (not an error), without guarantee it contains the most recent data.

**Example:** The system always responds, even if some nodes have slightly outdated data.

### P — Partition Tolerance

The system continues to **operate despite network partitions** — when nodes can’t communicate with each other.

**Example:** Even if the connection between US and EU servers breaks, the system keeps working.

## 🔺 The Three Combinations

### CP — Consistency + Partition Tolerance

|Aspect       |Detail                                                                   |
|-------------|-------------------------------------------------------------------------|
|**Behavior** |Always returns correct data, but may become unavailable during partitions|
|**Sacrifice**|Availability — some requests get errors or timeouts                      |
|**Use for**  |Banking, payments, inventory, financial systems                          |
|**Databases**|MongoDB, HBase, Redis, Zookeeper                                         |

### AP — Availability + Partition Tolerance

|Aspect       |Detail                                                           |
|-------------|-----------------------------------------------------------------|
|**Behavior** |Always responds, but data may be stale during partitions         |
|**Sacrifice**|Consistency — different nodes may show different data temporarily|
|**Use for**  |Social media, DNS, shopping carts, real-time feeds               |
|**Databases**|Cassandra, DynamoDB, CouchDB, Riak                               |

### CA — Consistency + Availability

|Aspect       |Detail                                                   |
|-------------|---------------------------------------------------------|
|**Behavior** |Perfect data + always online, but can’t handle partitions|
|**Reality**  |Only works on single-node systems (not truly distributed)|
|**Use for**  |Single-server databases, small applications              |
|**Databases**|PostgreSQL, MySQL (single server only)                   |


> **Important:** In any real distributed system, partitions WILL happen. So CA is not a practical option for distributed systems. The real choice is always **CP or AP**.

## 🌍 How Real Companies Choose

|Company      |Feature         |Choice|Why                                  |
|-------------|----------------|------|-------------------------------------|
|**Banks**    |Account balance |CP    |Wrong balance = lawsuits             |
|**Instagram**|Like count      |AP    |Stale count for a few seconds is fine|
|**Amazon**   |Shopping cart   |AP    |Cart must always work, syncs later   |
|**Amazon**   |Order processing|CP    |Orders must be 100% accurate         |
|**WhatsApp** |Message delivery|AP    |Messages delivered eventually        |
|**Google**   |Search index    |AP    |Slightly stale results are acceptable|


> **Key insight:** The same company can choose differently for different features! Amazon uses CP for orders but AP for shopping carts.

## ⚠️ Common Misconceptions

|Misconception                         |Reality                                                                      |
|--------------------------------------|-----------------------------------------------------------------------------|
|“You always sacrifice one”            |The tradeoff only matters DURING a network partition. Normally you get all 3.|
|“CA is a valid distributed option”    |In distributed systems, partitions will happen. P is mandatory.              |
|“It’s a permanent, system-wide choice”|Different parts of your system can make different choices                    |
|“CAP means you get exactly 2”         |It’s more nuanced — it’s about what happens during failures                  |

## 🔗 How CAP Connects to Previous Concepts

|Day   |Concept     |Connection                                              |
|------|------------|--------------------------------------------------------|
|Day 4 |SQL vs NoSQL|SQL databases lean CP; NoSQL databases often lean AP    |
|Day 5 |Scaling     |Horizontal scaling creates network partitions           |
|Day 13|Replication |Sync replication = CP; Async replication = AP           |
|Day 15|Sharding    |Shards across servers = partitions; must choose CP or AP|

## 💡 Key Takeaways

1. **C** = every read gets the latest data
1. **A** = system always responds
1. **P** = works despite network splits (mandatory in distributed systems)
1. The real choice is **CP** (correct data) vs **AP** (always available)
1. **Same company, different choices** — CP for payments, AP for feeds
1. CAP tradeoff only kicks in **during network partitions**, not during normal operation

## 🔗 Resources

- [CAP Theorem — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/cap-theorem-in-system-design/)
- [CAP Theorem — BMC](https://www.bmc.com/blogs/cap-theorem/)
- [CAP Theorem Explained — PingCAP](https://www.pingcap.com/article/understanding-cap-theorem-basics-in-distributed-systems/)
- [CAP Theorem — daily.dev](https://daily.dev/blog/cap-theorem-explained-consistency-availability-partition-tolerance/)

## ➡️ What’s Next?

**Day 17: Consistency Patterns** — Strong Consistency vs Eventual Consistency. How do systems decide when “close enough” is good enough? We’ll explore the spectrum from strict to relaxed consistency.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)