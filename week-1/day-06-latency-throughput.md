. # Day 6: Latency & Throughput

> 🗓️ Day 6 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

---

## 🤔 What Are Latency & Throughput?

These are the **two most important performance metrics** in system design. Every design decision you make impacts one or both.

| Metric | Definition | Analogy |
|--------|-----------|---------|
| **Latency** | Time it takes for a single request to complete | Speed of one car on the highway |
| **Throughput** | Number of requests a system handles per unit of time | Number of cars per hour on the highway |

**Key insight:** Your app can be fast (low latency) but still crash under load (low throughput). You need both.

## 🍔 The Fast Food Analogy

Imagine a drive-thru restaurant:

| Metric | In the Restaurant |
|--------|------------------|
| **Latency** | Time from ordering to getting your burger (2 minutes per order) |
| **Throughput** | Total orders served per hour (200 orders/hour) |

- 1 cook: Each burger takes 2 min (low latency), but only 30 orders/hour (low throughput)
- 5 cooks: Still 2 min per burger, but now 150 orders/hour (high throughput!)
- Microwave burgers: 30 seconds per burger (lower latency), but quality drops

**Fast service doesn't automatically mean high capacity!**

## ⏱️ Latency — The Speed Metric

**Latency** is the total time taken for a request to travel from client → server → back to client.

### How Latency Is Measured:

| Unit | Used For |
|------|----------|
| **Nanoseconds (ns)** | Hardware-level operations |
| **Microseconds (μs)** | Memory access |
| **Milliseconds (ms)** | Network calls, API requests |
| **Seconds (s)** | Page load times |

### Latency Numbers Every Developer Should Know:

| Operation | Latency | Feel |
|-----------|---------|------|
| L1 Cache reference | 0.5 ns | Instant |
| Reading from RAM | 100 ns (0.1 ms) | Instant |
| Reading from SSD | 1 ms | Very fast |
| Reading from HDD | 10 ms | Fast |
| API call (same region) | 50 ms | Good |
| API call (cross-continent) | 200 ms | Noticeable |
| Slow database query | 1,000 ms (1 sec) | Bad — user feels it! |
| Page timeout | 3,000+ ms | User leaves! |

### Types of Latency:

```
Total Latency = Network Latency + Processing Latency + Queue Latency

Where:
- Network Latency    → Time for data to travel across the network
- Processing Latency → Time for server to process the request
- Queue Latency      → Time spent waiting in line (when server is busy)
```

### What Affects Latency:
- **Distance** — Further apart = higher latency (NY → Tokyo: ~200ms)
- **Network hops** — More routers/switches = more delay
- **Server processing** — Slow code or queries
- **Payload size** — More data = more transfer time

## 📊 Throughput — The Capacity Metric

**Throughput** is the rate at which a system processes work over a given period.

### How Throughput Is Measured:

| Unit | Context |
|------|---------|
| **Requests per second (RPS)** | Web servers & APIs |
| **Transactions per second (TPS)** | Databases |
| **Megabytes per second (MB/s)** | File transfers & streaming |
| **Queries per second (QPS)** | Search engines |

### Real-World Throughput Numbers:

| System | Throughput |
|--------|-----------|
| **Google Search** | ~99,000 searches/second |
| **Netflix** | Millions of concurrent streams |
| **Visa** | ~65,000 transactions/second |
| **WhatsApp** | ~100 billion messages/day |
| **Amazon** | ~100,000+ orders/minute (peak) |

### What Affects Throughput:
- **Server resources** — CPU, RAM, network bandwidth
- **Architecture** — Horizontal scaling increases throughput
- **Bottlenecks** — Slowest component limits overall throughput
- **Concurrency** — How many requests can be handled simultaneously

## 🔄 How They Relate — The 2x2 Matrix

| | High Throughput | Low Throughput |
|---|---|---|
| **Low Latency** | ✅ **THE DREAM** — Fast & handles millions (Google, CDNs) | ⚠️ Fast but limited — Quick for each user, few at a time (small blog) |
| **High Latency** | ⚠️ Slow but powerful — Handles tons of data slowly (batch processing) | ❌ **THE NIGHTMARE** — Slow AND can't handle traffic (overloaded server) |

**The goal:** Low latency + High throughput = great user experience at scale.

## 🛠️ How to Improve Each

### Reduce Latency:
| Strategy | How It Helps |
|----------|-------------|
| **Use a CDN** | Serve content from servers closer to users |
| **Add caching (Redis)** | Store frequent data in memory — no DB calls |
| **Optimize DB queries** | Use indexes, avoid N+1 queries |
| **Reduce payload size** | Send less data over the network (compression) |
| **Use connection pooling** | Reuse connections instead of creating new ones |

### Increase Throughput:
| Strategy | How It Helps |
|----------|-------------|
| **Scale horizontally** | Add more servers to handle more requests |
| **Use load balancers** | Distribute traffic evenly across servers |
| **Async processing** | Use message queues (Kafka, RabbitMQ) for heavy tasks |
| **Database sharding** | Split data across multiple database servers |
| **Optimize code** | Faster algorithms = more requests processed |

## 🔗 How This Connects to Previous Concepts

| Day | Concept | Connection |
|-----|---------|------------|
| Day 2 | Client-Server | Latency = time for request-response cycle |
| Day 3 | APIs | API response time is a latency measurement |
| Day 4 | SQL vs NoSQL | NoSQL often has higher throughput for reads |
| Day 5 | Scaling | Vertical scaling reduces latency; horizontal increases throughput |

## 💡 Key Takeaways

1. **Latency = speed per request** — measured in ms, lower is better
2. **Throughput = capacity per second** — measured in RPS, higher is better
3. A system can be **fast but crash under load** (low latency, low throughput)
4. **You need both** for a great user experience at scale
5. **CDN + Caching** reduces latency; **Scaling + Load Balancing** increases throughput
6. The goal: **maximize throughput with acceptable latency**

## 🔗 Resources

- [Latency & Throughput - GeeksforGeeks](https://www.geeksforgeeks.org/system-design/latency-in-system-design/)
- [Throughput vs Latency - Grokking System Design](https://grokkingthesystemdesign.com/blog/throughput-vs-latency/)
- [Latency vs Throughput - Design Gurus](https://www.designgurus.io/course-play/grokking-the-system-design-interview/doc/latency-vs-throughput)
- [Latency Numbers Every Programmer Should Know](https://gist.github.com/jboner/2841832)

## ➡️ What's Next?

**Day 7: Week 1 Recap** — We'll connect all 6 concepts into one big picture: System Design → Client-Server → APIs → Databases → Scaling → Latency & Throughput. Plus a master diagram showing how they all fit together!

---

⭐ Star this repo if you're learning along!

📬 Connect with me:
- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
