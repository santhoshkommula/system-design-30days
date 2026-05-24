# Day 9: Caching

> 🗓️ Day 9 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

---

## 🤔 What is Caching?

**Caching** is the process of storing a copy of data in a **temporary, fast storage location** (usually RAM) so future requests can be served faster without going to the slower original source (database, API, etc.).

> **The fastest database query is the one you never make.**

## 🗄️ The Desk Analogy

| Scenario | What Happens |
|----------|-------------|
| **Without Cache** | Every time you need a file, you walk to the filing cabinet. Slow. Repetitive. |
| **With Cache** | You keep frequently used files right on your desk. Instant access. |

**Cache = your desk. Database = the filing cabinet.**

## ⚡ Why Caching Matters

| Benefit | Impact |
|---------|--------|
| **Reduces latency** | Responses go from 500ms to 5ms (100x faster) |
| **Lowers DB load** | 90% fewer database queries |
| **Improves scalability** | Handle more users with same hardware |
| **Saves money** | Less server resources needed |

## 🔄 How Caching Works

### Cache HIT (Data found — fast path):
```
User requests data
       ↓
Check the cache
       ↓
Data IS in cache ✅
       ↓
Return instantly! (5ms)
```

### Cache MISS (Data not found — slow path):
```
User requests data
       ↓
Check the cache
       ↓
Data NOT in cache ❌
       ↓
Query the database (500ms)
       ↓
Store result in cache for next time
       ↓
Return to user
```

**Key metric:** **Cache Hit Ratio** = Hits / (Hits + Misses). A good cache has 90%+ hit ratio.

## 🏗️ Types of Caching

### 1. Browser Cache
- **What:** Browser stores images, CSS, JS, fonts locally
- **Speed:** Fastest — no network request needed at all
- **Example:** Revisiting a website loads instantly because assets are cached

### 2. CDN Cache
- **What:** Content cached at edge servers worldwide (we'll cover this in Day 10!)
- **Speed:** Very fast — content served from nearest location
- **Example:** Netflix streams from a server near you, not from their HQ

### 3. Application Cache (Most Important for System Design)
- **What:** App stores frequently accessed data in memory using tools like Redis or Memcached
- **Speed:** Extremely fast — data in RAM, not on disk
- **Example:** Instagram caches your feed data in Redis

### 4. Database Cache
- **What:** Database internally caches repeated query results
- **Speed:** Fast — avoids re-executing the same query
- **Example:** MySQL query cache stores results of identical queries

## 📋 Caching Strategies

### 1. Cache-Aside (Lazy Loading) — Most Common!
```
App checks cache → Miss → App queries DB → App writes to cache
```
- **How:** App manages the cache. On miss, fetch from DB and store in cache.
- **Pros:** Simple, only caches what's needed
- **Cons:** First request is always slow (cold cache)
- **Use when:** Read-heavy workloads

### 2. Write-Through
```
App writes to cache AND DB at the same time
```
- **How:** Every write goes to cache and DB simultaneously
- **Pros:** Cache is always in sync with DB
- **Cons:** Slower writes (double write), caches data that may never be read
- **Use when:** Data consistency is critical

### 3. Write-Back (Write-Behind)
```
App writes to cache only → Cache writes to DB later (async)
```
- **How:** Writes go to cache first, DB is updated asynchronously
- **Pros:** Super fast writes
- **Cons:** Risk of data loss if cache crashes before DB sync
- **Use when:** Write-heavy workloads where speed matters most

### 4. Read-Through
```
App asks cache → Cache fetches from DB automatically on miss
```
- **How:** Cache sits in front of DB and manages fetching automatically
- **Pros:** App code is simpler (doesn't talk to DB directly)
- **Cons:** First request still slow
- **Use when:** You want the cache to manage itself

## ⚠️ Caching Challenges

| Challenge | Description | Solution |
|-----------|-------------|----------|
| **Stale data** | Cached data becomes outdated | TTL (Time-To-Live) — auto-expire after X seconds |
| **Cache invalidation** | When to remove/update cached data | Event-driven invalidation on data change |
| **Cache stampede** | Many requests hit DB when cache expires | Lock + single fetch pattern |
| **Memory limits** | Cache can't store everything | Eviction policies (LRU, LFU) |
| **Cold start** | Empty cache after restart | Cache warming — pre-load popular data |

## 🔄 Cache Eviction Policies

When cache is full, which data do you remove?

| Policy | Strategy | When to Use |
|--------|----------|-------------|
| **LRU** (Least Recently Used) | Remove the oldest accessed item | Most common, general purpose |
| **LFU** (Least Frequently Used) | Remove the least accessed item | When frequency matters |
| **FIFO** (First In, First Out) | Remove the oldest added item | Simple, predictable |
| **TTL** (Time-To-Live) | Remove after a set time | When freshness is important |

## 🛠️ Popular Caching Tools

| Tool | Type | Notes |
|------|------|-------|
| **Redis** | In-memory, key-value store | Most popular. Supports data structures, persistence |
| **Memcached** | In-memory, key-value store | Simpler, faster for basic caching |
| **Varnish** | HTTP reverse proxy cache | Great for caching web pages |
| **Cloudflare** | CDN + edge cache | Caches at network edge worldwide |

## 🌍 Real-World Examples

| Company | How They Use Caching |
|---------|---------------------|
| **Netflix** | Caches movie thumbnails, metadata in Redis |
| **Instagram** | Caches entire feed and stories in memory |
| **Google** | Pre-caches search results for popular queries |
| **Amazon** | Caches product pages, prices, recommendations |
| **Twitter/X** | Caches timelines in Redis for instant loading |

## 🔗 How This Connects to Previous Concepts

| Day | Concept | Connection |
|-----|---------|------------|
| Day 3 | APIs | Cache API responses to avoid repeated computation |
| Day 4 | Databases | Cache sits in front of DB to reduce queries |
| Day 6 | Latency | Caching is the #1 way to reduce latency |
| Day 8 | Load Balancers | Cache + LB together = fast AND scalable |

## 💡 Key Takeaways

1. **Cache = fast temporary storage** (usually RAM)
2. **Cache Hit = instant**, Cache Miss = slow then cache it for next time
3. **Cache-Aside** is the most common strategy (check cache → miss → fetch from DB → store in cache)
4. **Redis** is the most popular caching tool
5. **TTL and eviction policies** handle stale data and memory limits
6. Caching is the **first optimization** you add to any slow system

## 🔗 Resources

- [Caching in System Design — Design Gurus](https://www.designgurus.io/answers/detail/how-does-caching-work-and-what-are-common-caching-strategies-in-system-design)
- [Caching Strategies — Jobaaj Learnings](https://www.jobaajlearnings.com/blog/caching-strategies-in-system-design)
- [Caching Concept — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/caching-system-design-concept-for-beginners/)
- [Redis Documentation](https://redis.io/docs/)

## ➡️ What's Next?

**Day 10: CDN (Content Delivery Network)** — Your website loads in 3 seconds in the US but 10 seconds in India. CDNs fix this by serving content from servers nearest to the user.

---

⭐ Star this repo if you're learning along!

📬 Connect with me:
- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
