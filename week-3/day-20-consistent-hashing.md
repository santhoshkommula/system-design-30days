# Day 20: Consistent Hashing

> 🗓️ Day 20 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is Consistent Hashing?

**Consistent hashing** is a distributed systems technique that maps both **servers (nodes)** and **data (keys)** onto a circular **hash ring**. It minimizes the number of keys that need to move when servers are added or removed — solving a major problem in distributed systems.

> When the cluster size changes, only **k/N** keys need to move (k = keys, N = nodes), instead of nearly all of them.

## ❌ The Problem with Normal Hashing

The naive approach to distributing keys across servers:

```
server = hash(key) % N     (N = number of servers)
```

This works fine — **until N changes**:

|Stage           |Formula              |Result                            |
|----------------|---------------------|----------------------------------|
|**Before**      |`hash(key) % 3`      |Keys spread across S0, S1, S2     |
|**Add a server**|`hash(key) % 4`      |The modulo changes for EVERY key  |
|**Result**      |Almost ALL keys remap|Cache misses everywhere — disaster|

In a distributed cache, this means a near-total cache wipe every time you scale. Unacceptable.

## ✅ The Solution: The Hash Ring

Instead of modulo, we use a **circular hash space** (the ring):

```
Steps:
1. Hash each server → a position on the ring
2. Hash each key    → a position on the ring
3. Each key belongs to the FIRST server found clockwise
```

### Example:

```
        S1 (top)
       /        \
   key•          •
     |    RING    |
   S2 •          • S3
       \        /
         (keys)
```

A key hashed between S1 and S2 (going clockwise) is stored on **S2** — the next node clockwise.

## 🎯 Why It’s Better

When a server is added or removed, **only nearby keys move**:

|Event              |What Happens                                            |
|-------------------|--------------------------------------------------------|
|**Add a server**   |It only takes keys from its immediate clockwise neighbor|
|**Remove a server**|Its keys move to the next server clockwise              |
|**Keys moved**     |Only ~k/N (a small fraction), not all of them           |
|**Rest of ring**   |Completely untouched                                    |

This is the key advantage: **scaling doesn’t trigger a mass reshuffle.**

## 🔁 Virtual Nodes (VNodes)

### The Problem

With only a few servers, the ring can be **uneven**. One server might end up responsible for 60% of the ring while another holds 10%. This creates **hotspots**.

### The Solution

Place each physical server at **multiple points** on the ring using multiple hashes:

```
Server A → A1, A2, A3, ... (many positions)
Server B → B1, B2, B3, ...
Server C → C1, C2, C3, ...
```

- More positions = smoother, more even distribution
- When a new node joins, it absorbs small chunks from **many** nodes (not just one neighbor)
- Real systems use **100–200 virtual nodes** per physical server

> Virtual nodes are the secret to making consistent hashing actually balanced in practice.

## ⚠️ Hotspots (A Remaining Challenge)

Even with virtual nodes, **popular keys** can overload a node. Example: a Taylor Swift concert in a ticketing system generates 100x the reads of any other event. Consistent hashing distributes keys evenly, **not traffic**.

**Mitigations:**

- **Read replicas:** replicate popular keys across multiple nodes
- **Caching:** cache hot keys at a higher layer
- **Dedicated nodes:** give very hot keys their own capacity

## 📊 Pros & Cons

### Pros

|Advantage                 |Detail                            |
|--------------------------|----------------------------------|
|Minimal data movement     |Only k/N keys move when scaling   |
|Scales horizontally       |Add/remove nodes smoothly         |
|No single point of failure|Decentralized by design           |
|Great for caches & DBs    |Distributed caches, databases, LBs|

### Cons

|Disadvantage      |Detail                                |
|------------------|--------------------------------------|
|Complexity        |Harder to implement than modulo       |
|Hotspots          |Popular keys can still overload a node|
|Memory overhead   |Virtual nodes use extra memory        |
|Cascading failures|A failing node can overload neighbors |

## 🌍 Who Uses Consistent Hashing

|System                       |How They Use It                               |
|-----------------------------|----------------------------------------------|
|**Apache Cassandra**         |Distributes data partitions across the cluster|
|**Amazon DynamoDB**          |Partitions data using consistent hashing      |
|**Discord**                  |Routes users/guilds to chat servers           |
|**CDNs (Akamai, Cloudflare)**|Map content to edge cache servers             |
|**Memcached clients**        |Distribute keys across cache nodes            |
|**Riak, Couchbase**          |Data partitioning in distributed databases    |

## 🔗 How This Connects to Previous Concepts

|Day   |Concept       |Connection                                         |
|------|--------------|---------------------------------------------------|
|Day 8 |Load Balancers|Consistent hashing routes requests to servers      |
|Day 9 |Caching       |Distributed caches use it to place keys            |
|Day 13|Replication   |Keys are replicated to the next N nodes on the ring|
|Day 15|Sharding      |It’s an elegant way to assign data to shards       |

## 💡 Key Takeaways

1. **Normal hashing** (`% N`) moves ALL keys when the server count changes
1. **Consistent hashing** places servers + keys on a **hash ring**
1. Adding/removing a node only moves **~k/N keys** — a tiny fraction
1. **Virtual nodes** spread each server across many ring positions for balance
1. **Hotspots** can still happen with popular keys — use replicas/caching
1. It powers **Cassandra, DynamoDB, CDNs**, and distributed caches

## 🔗 Resources

- [Consistent Hashing — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/consistent-hashing/)
- [Consistent Hashing Explained — AlgoMaster](https://blog.algomaster.io/p/consistent-hashing-explained)
- [Consistent Hashing — Hello Interview](https://www.hellointerview.com/learn/system-design/core-concepts/consistent-hashing)
- [Design Consistent Hashing — ByteByteGo](https://bytebytego.com/courses/system-design-interview/design-consistent-hashing)

## ➡️ What’s Next?

**Day 21: Week 3 Recap** — We’ll tie together Sharding, CAP Theorem, Message Queues, Microservices, API Gateway, and Consistent Hashing into one big picture of how reliable, scalable systems are designed.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)