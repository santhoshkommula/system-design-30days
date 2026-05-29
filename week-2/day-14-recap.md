# Day 14: Week 2 Recap — Making Systems Faster

> 🗓️ Day 14 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🎉 Week 2 Complete!

This week was all about **speed, performance, and reliability**. Here’s how all 6 concepts connect.

## 🏗️ The Complete Week 2 Architecture

```
                   ┌─────────────┐
                   │    Users    │
                   └──────┬──────┘
                          │
                   ┌──────▼──────┐
                   │ CDN (Day 10)│  ← Static files served here
                   └──────┬──────┘
                          │
                   ┌──────▼──────────┐
                   │Rev Proxy (Day 11)│  ← SSL, security, routing
                   └──────┬──────────┘
                          │
                   ┌──────▼──────────┐
                   │Load Bal (Day 8) │  ← Distributes traffic
                   └───┬────────┬───┘
                       │        │
              ┌────────▼──┐ ┌──▼────────┐
              │ Server +  │ │ Server +  │
              │Cache Day 9│ │Cache Day 9│  ← Redis for speed
              └─────┬─────┘ └─────┬─────┘
                    │             │
         ┌──────────▼─────────────▼──────────┐
         │                                    │
   ┌─────▼──────────┐         ┌──────────────▼──┐
   │  Primary DB    │ ──────→ │   Replicas      │
   │  Indexed Day 12│         │   Day 13        │
   │  (Writes)      │         │   (Reads)       │
   └────────────────┘         └─────────────────┘
```

## 📋 Day-by-Day Quick Recap

### Day 8: Load Balancers

**One-liner:** Distributes traffic across servers so no one server gets overwhelmed.

- Toll booth analogy — multiple lanes, not one
- Algorithms: Round Robin, Least Connections, Weighted, IP Hash
- Layer 4 (fast, basic) vs Layer 7 (smart, content-based)

### Day 9: Caching

**One-liner:** Stores data in fast memory (RAM) — turns 500ms queries into 5ms.

- Desk vs filing cabinet analogy
- Cache Hit (instant) vs Cache Miss (slow, then cache it)
- Strategies: Cache-Aside, Write-Through, Write-Back, Read-Through
- Tool: Redis (most popular)

### Day 10: CDN

**One-liner:** Serves content from the server nearest to the user worldwide.

- Convenience store analogy — local stores, not one warehouse
- Origin server (source) vs Edge servers (cached copies)
- Pull CDN (on demand) vs Push CDN (pre-loaded)

### Day 11: Proxy vs Reverse Proxy

**One-liner:** Forward proxy hides the client, reverse proxy hides the server.

- Forward proxy = friend ordering for you (hides you)
- Reverse proxy = receptionist (hides the employees)
- Nginx is the most popular reverse proxy (~34% of websites)

### Day 12: Database Indexing

**One-liner:** Sorted pointers that let databases find data without scanning every row.

- Book index analogy — flip to the back, find the page
- B-Tree = most common structure
- Tradeoff: faster reads, slower writes

### Day 13: Database Replication

**One-liner:** Copies data across multiple servers — if one dies, others survive.

- Notebook photocopy analogy
- Primary-Replica: one writes, many read
- Sync (consistent) vs Async (fast)

## 🔗 Week 2 Cheat Sheet

|Term                 |Definition                        |
|---------------------|----------------------------------|
|**Load Balancer**    |Distributes traffic across servers|
|**Round Robin**      |Sends requests one by one         |
|**Cache**            |Fast temporary storage (RAM)      |
|**Cache Hit / Miss** |Found in cache / not found        |
|**CDN**              |Edge servers near users worldwide |
|**Forward Proxy**    |Hides the client                  |
|**Reverse Proxy**    |Hides the server                  |
|**Index**            |Sorted pointers for fast lookup   |
|**B-Tree**           |Most common index structure       |
|**Replication**      |Data copies across servers        |
|**Primary-Replica**  |One writes, many read             |
|**Sync Replication** |All copies updated simultaneously |
|**Async Replication**|Copies updated later (faster)     |

## 🎬 How Netflix Uses All 6 Concepts

|Concept           |Netflix’s Implementation                        |
|------------------|------------------------------------------------|
|**Load Balancers**|Routes millions of concurrent streams           |
|**Caching**       |EVCache stores movie metadata in memory         |
|**CDN**           |Open Connect CDN in 1000+ locations             |
|**Reverse Proxy** |Zuul gateway routes all API traffic             |
|**Indexing**      |Indexes on user, title, genre for instant search|
|**Replication**   |Data replicated across 3+ AWS regions           |

## 📊 Week 1 + Week 2 Combined

|Week      |Theme                |Concepts                                                                       |
|----------|---------------------|-------------------------------------------------------------------------------|
|**Week 1**|Building Blocks      |System Design, Client-Server, APIs, SQL vs NoSQL, Scaling, Latency & Throughput|
|**Week 2**|Making Systems Faster|Load Balancers, Caching, CDN, Proxies, Indexing, Replication                   |

**14 concepts down. 16 to go. Almost halfway!**

## 📅 What’s Coming in Week 3: Designing for Reliability

|Day   |Topic                    |
|------|-------------------------|
|Day 15|Database Sharding        |
|Day 16|CAP Theorem              |
|Day 17|Consistency Patterns     |
|Day 18|Message Queues           |
|Day 19|Microservices vs Monolith|
|Day 20|API Gateway              |
|Day 21|Week 3 Recap             |

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)