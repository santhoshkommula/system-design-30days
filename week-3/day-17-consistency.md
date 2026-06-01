# Day 17: Consistency Patterns

> 🗓️ Day 17 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What Are Consistency Patterns?

Consistency patterns define **how fresh data must be** when read from a distributed system. They determine whether every read sees the absolute latest write, or whether slightly stale data is acceptable.

> Your bank balance must be exact. Your Instagram like count can be off by a few for a moment. Different needs = different patterns.

## 🔄 The Replication Lag Problem

In distributed systems, data is replicated across multiple nodes. When you write to one node, the others take time to update.

```
Step 1: You write data to Node A
Step 2: Node A has the new value ✅
Step 3: Nodes B and C still have the OLD value ❌
Step 4: Until the update propagates...
Step 5: Reads from B or C return STALE data
```

This is **replication lag** — and consistency patterns decide how to handle it.

## 💪 Strong Consistency

**Definition:** Every read returns the most recent write. All nodes always reflect the same data.

|Characteristic  |Detail                                       |
|----------------|---------------------------------------------|
|**Accuracy**    |Always returns the latest value              |
|**Speed**       |Slower — must sync replicas before confirming|
|**Availability**|Lower — if a node is down, writes may block  |
|**Reasoning**   |Simple — behaves like a single database      |
|**Also called** |Linearizability                              |

**Properties:**

- **Read-after-write:** if a write succeeds, the next read includes it
- **Linearizability:** operations appear in a single global order
- **Single-copy semantics:** acts as if there’s only one copy of data

**Use for:**

- Banking & financial systems (balances must be accurate)
- Inventory management (can’t sell the same item twice)
- Distributed locking (locks must be exclusive)
- Unique ID generation (no duplicates allowed)

## 🌊 Eventual Consistency

**Definition:** Data syncs across nodes over time. Temporary inconsistencies are allowed, but all replicas eventually converge to the same value.

|Characteristic  |Detail                                      |
|----------------|--------------------------------------------|
|**Availability**|High — always responds, even during failures|
|**Speed**       |Fast — doesn’t wait for all replicas        |
|**Freshness**   |Reads may return stale data briefly         |
|**Scalability** |Excellent — great for massive systems       |

**How it works:**

- Data is replicated **asynchronously** across servers
- Changes propagate over time (usually seconds)
- The system converges to the same state eventually
- Implemented via multi-leader or leaderless replication

**Use for:**

- Social media (likes, comments, follower counts)
- DNS (record changes propagate over hours)
- Shopping carts (sync across devices)
- Analytics & view counts

## ⚔️ Strong vs Eventual — Head to Head

|Aspect            |Strong       |Eventual                |
|------------------|-------------|------------------------|
|**Data freshness**|Always latest|May be stale            |
|**Speed**         |Slower       |Faster                  |
|**Availability**  |Lower        |Higher                  |
|**Scalability**   |Harder       |Easier                  |
|**Complexity**    |Simpler logic|Conflict handling needed|
|**CAP fit**       |CP systems   |AP systems              |

## 📊 The Consistency Spectrum

Consistency isn’t just two options — it’s a range from strict to relaxed:

|Level                    |Description                         |Example                            |
|-------------------------|------------------------------------|-----------------------------------|
|**Strong / Linearizable**|Everyone sees latest instantly      |Banking, distributed locks         |
|**Causal Consistency**   |Related events stay in order        |Comment threads, chat replies      |
|**Read-Your-Writes**     |You always see your own updates     |Edit your profile, see it instantly|
|**Monotonic Reads**      |You never see older data after newer|Reading a timeline                 |
|**Eventual Consistency** |Syncs over time, may be stale       |Like counts, DNS, view counts      |

## 🌍 Real-World Examples

|System             |Model              |Why                             |
|-------------------|-------------------|--------------------------------|
|**Bank Balance**   |Strong             |Must be exact every time        |
|**Instagram Likes**|Eventual           |Off by a few for seconds is fine|
|**Google Docs**    |Strong-ish (Causal)|You see your edits instantly    |
|**DNS**            |Eventual           |New records propagate over hours|
|**Stock Trading**  |Strong             |Price accurate to the cent      |
|**Amazon Cart**    |Eventual           |Syncs across your devices       |

## ⚖️ How to Choose

Ask yourself: **“What happens if a user sees stale data for a few seconds?”**

- **Catastrophic** (wrong bank balance, double-booking) → **Strong**
- **No big deal** (slightly old like count) → **Eventual**

Most large systems use **both** — strong consistency for critical paths (payments) and eventual consistency for everything else (feeds, counts).

## 🔗 How This Connects to Previous Concepts

|Day   |Concept    |Connection                                 |
|------|-----------|-------------------------------------------|
|Day 13|Replication|Sync replication = strong; async = eventual|
|Day 16|CAP Theorem|CP = strong consistency; AP = eventual     |
|Day 15|Sharding   |Each shard chooses its consistency model   |

## 💡 Key Takeaways

1. **Strong = always latest data**, but slower and less available
1. **Eventual = fast and available**, but may return stale data briefly
1. It’s a **spectrum** — strong, causal, read-your-writes, eventual
1. **Match the model to your use case** — not every feature needs strong consistency
1. Most systems use **both** — strong for critical data, eventual for the rest

## 🔗 Resources

- [Strong vs Eventual Consistency — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/strong-vs-eventual-consistency-in-system-design/)
- [Strong vs Eventual — AlgoMaster](https://algomaster.io/learn/system-design/strong-vs-eventual-consistency)
- [Consistency Patterns — systemdesign.one](https://systemdesign.one/consistency-patterns/)
- [Eventual vs Strong — Design Gurus](https://www.designgurus.io/blog/eventual-vs-strong-consistency)

## ➡️ What’s Next?

**Day 18: Message Queues** — Not every request needs an instant response. Message queues let services communicate asynchronously, handle traffic spikes, and retry on failure. We’ll learn how they decouple systems.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)