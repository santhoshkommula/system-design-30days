# Day 13: Database Replication

> 🗓️ Day 13 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is Database Replication?

**Database replication** is the process of **copying and maintaining data across multiple database servers** so they stay in sync. If one server fails, others continue serving — ensuring high availability and data safety.

> **Single database = single point of failure. Replication = your safety net.**

## 📓 The Notebook Analogy

|Scenario               |What Happens                                                  |
|-----------------------|--------------------------------------------------------------|
|**Without Replication**|All notes in ONE notebook. Lose it? Everything gone.          |
|**With Replication**   |Photocopy notes to 3 friends. Lose yours? Friends have copies!|

## ⚡ Why Replicate?

|Benefit                    |How                                    |
|---------------------------|---------------------------------------|
|**High availability**      |One DB dies, others keep serving       |
|**Better read performance**|Read from any replica, not just primary|
|**Disaster recovery**      |Data backed up across locations        |
|**Reduced latency**        |Replicas near users = faster reads     |
|**Backup**                 |Replicas serve as live backups         |

## 🏗️ Replication Models

### 1. Primary-Replica (Master-Slave) — Most Common

```
Client (Writes) ──→ Primary (Master) ──→ Replica 1
                                     ──→ Replica 2
Client (Reads) ───→ Replica 1            ──→ Replica 3
Client (Reads) ───→ Replica 2
Client (Reads) ───→ Replica 3
```

|Aspect      |Details                             |
|------------|------------------------------------|
|**Writes**  |ALL go to Primary only              |
|**Reads**   |Can go to any Replica               |
|**Sync**    |Primary copies changes to Replicas  |
|**Failover**|Primary dies → promote a Replica    |
|**Best for**|Read-heavy applications (most apps!)|

### 2. Multi-Master (Master-Master)

```
Master 1 (US) ←──sync──→ Master 2 (EU)
  ↑ Writes                  ↑ Writes
  ↑ Reads                   ↑ Reads
```

|Aspect       |Details                                             |
|-------------|----------------------------------------------------|
|**Writes**   |Both masters accept writes                          |
|**Reads**    |Both masters handle reads                           |
|**Sync**     |Masters sync with each other                        |
|**Best for** |Global apps needing writes from multiple regions    |
|**Challenge**|Write conflicts (both edit same data simultaneously)|


> **Most apps start with Primary-Replica.** Multi-Master is for specific global needs.

## 🔄 Synchronous vs Asynchronous Replication

### Synchronous

|Aspect         |Details                                       |
|---------------|----------------------------------------------|
|**How**        |Write to primary AND replicas at the same time|
|**Consistency**|100% — all copies always match                |
|**Speed**      |Slower (waits for all replicas to confirm)    |
|**Use for**    |Banking, payments, financial data             |
|**Risk**       |If a replica is slow, all writes slow down    |

### Asynchronous

|Aspect         |Details                                    |
|---------------|-------------------------------------------|
|**How**        |Write to primary first, replicas sync later|
|**Consistency**|Eventual — slight delay on replicas        |
|**Speed**      |Faster (don’t wait for replicas)           |
|**Use for**    |Social media, feeds, analytics             |
|**Risk**       |Replica data may be slightly stale         |

## ⚠️ Challenges

|Challenge           |Description                          |Solution                                     |
|--------------------|-------------------------------------|---------------------------------------------|
|**Replication lag** |Replicas fall behind the primary     |Monitor lag, use sync for critical data      |
|**Write conflicts** |Two masters write to same row        |Conflict resolution rules, use single-primary|
|**Failover**        |Promoting a replica when primary dies|Automated failover tools                     |
|**Data consistency**|Replicas may have stale data         |Choose sync vs async based on needs          |

## 🌍 Real-World Examples

|Company      |Replication Type             |Why                                   |
|-------------|-----------------------------|--------------------------------------|
|**Netflix**  |Async replicas across regions|Stream from the nearest copy          |
|**Amazon**   |Sync for orders and payments |Your payment is never lost            |
|**Instagram**|Async for feeds and stories  |Fast loads, slight delay is acceptable|
|**Banks**    |Sync replication for balances|Balance must always be accurate       |
|**GitHub**   |Replicas for read scaling    |Millions of repo views per day        |

## 🔗 How This Connects

|Day   |Concept       |Connection                                     |
|------|--------------|-----------------------------------------------|
|Day 4 |SQL vs NoSQL  |Both support replication                       |
|Day 5 |Scaling       |Replication is horizontal scaling for databases|
|Day 6 |Throughput    |Replicas increase read throughput              |
|Day 8 |Load Balancers|LB routes reads across replicas                |
|Day 12|Indexing      |Each replica also has indexes                  |

## 💡 Key Takeaways

1. **Replication = copying data** across multiple database servers
1. **Primary-Replica:** one writes, many read — most common model
1. **Sync = consistent but slow**, Async = fast but eventually consistent
1. **Replicas improve read performance** and provide fault tolerance
1. Replication is your **2 AM safety net** — if one dies, others survive

## 🔗 Resources

- [DB Replication — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/database-replication-and-their-types-in-system-design/)
- [Master-Slave Replication — Medium](https://dennylesmana.medium.com/master-slave-replication-database-concept-for-beginners-300b3f9a8228)
- [Master-Slave Architecture — Medium](https://medium.com/@techsuneel99/database-replication-master-slave-architecture-1a1246397a22)
- [Replication Types — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/types-of-database-replication-system-design/)

## ➡️ What’s Next?

**Day 14: Week 2 Recap** — We’ll tie together Load Balancers, Caching, CDN, Proxies, Indexing, and Replication into one master architecture diagram. Plus a Week 2 cheat sheet!

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)