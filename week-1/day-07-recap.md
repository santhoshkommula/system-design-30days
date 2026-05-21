# Day 7: Week 1 Recap — The Building Blocks

> 🗓️ Day 7 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

---

## 🎉 Week 1 Complete!

We covered 6 foundational concepts this week. Here's how they all connect.

## 📝 Week 1 In One Sentence

> **"A Client sends a request through an API to a Server, which reads from a Database, all designed to Scale with low Latency and high Throughput."**

That's System Design.

## 🗺️ The Master Architecture

Here's how all 6 concepts fit together in a real system:

```
                    ┌─────────────────┐
                    │   User (Client) │  ← Day 2: Client-Server
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │    API Layer    │  ← Day 3: REST APIs
                    │ GET/POST/PUT/DEL│
                    └────────┬────────┘
                             │
                    ┌────────▼────────┐
                    │  Load Balancer  │  ← Day 5: Horizontal Scaling
                    └──┬──────┬───┬───┘
                       │      │   │
                ┌──────▼─┐ ┌─▼──┐ ┌▼──────┐
                │Server 1│ │ S2 │ │Server 3│  ← Day 5: Scale Out
                └──┬─────┘ └─┬──┘ └──┬────┘
                   │         │       │
              ┌────▼─────────▼───────▼────┐
              │                           │
        ┌─────▼──────┐         ┌──────────▼─┐
        │ SQL Database│         │NoSQL Database│  ← Day 4: SQL vs NoSQL
        │ (PostgreSQL)│         │  (MongoDB)   │
        └─────────────┘         └──────────────┘

        ◄─── Latency: Speed per request (ms) ───►  ← Day 6
        ◄─── Throughput: Requests/second ────────►  ← Day 6

        ╔═══════════════════════════════════════╗
        ║  Day 1: System Design = Planning      ║
        ║         all of the above              ║
        ╚═══════════════════════════════════════╝
```

## 📋 Day-by-Day Quick Recap

### Day 1: What is System Design?
**One-liner:** Planning HOW your app works at a high level — the blueprint before the building.

| Key Point | Detail |
|-----------|--------|
| What it is | The process of designing system architecture |
| Analogy | Coding = laying bricks, System Design = the blueprint |
| Why it matters | Interviews, building better apps, thinking like an architect |

### Day 2: Client-Server Architecture
**One-liner:** Client asks, Server answers — every app follows this pattern.

| Key Point | Detail |
|-----------|--------|
| Client | Anything that requests data (browser, app) |
| Server | Anything that responds with data (backend) |
| Cycle | Request → Process → Response |
| Architecture | 3-Tier is the standard (Client → App Server → Database) |

### Day 3: What is an API?
**One-liner:** The waiter between client and server — GET, POST, PUT, DELETE.

| Key Point | Detail |
|-----------|--------|
| API | Application Programming Interface — bridge between systems |
| Methods | GET (read), POST (create), PUT (update), DELETE (remove) |
| CRUD | Create, Read, Update, Delete |
| Data format | JSON (JavaScript Object Notation) |

### Day 4: SQL vs NoSQL
**One-liner:** SQL = structured tables, NoSQL = flexible documents. Choose based on your data.

| Key Point | SQL | NoSQL |
|-----------|-----|-------|
| Structure | Tables (rows & columns) | Documents, key-value, graph |
| Schema | Fixed | Flexible |
| Scaling | Vertical | Horizontal |
| Best for | Relationships, transactions | Big data, real-time apps |
| Examples | MySQL, PostgreSQL | MongoDB, Redis |

### Day 5: Vertical vs Horizontal Scaling
**One-liner:** Scale UP (bigger server) or Scale OUT (more servers). Most systems use both.

| Key Point | Vertical | Horizontal |
|-----------|----------|------------|
| Method | Upgrade one server | Add more servers |
| Analogy | Stronger worker | More workers |
| Limit | Hardware ceiling | Virtually unlimited |
| Complexity | Simple | Complex |
| Real path | Start here → | → Transition here |

### Day 6: Latency & Throughput
**One-liner:** Latency = speed per request. Throughput = capacity per second. You need both.

| Key Point | Latency | Throughput |
|-----------|---------|------------|
| Measures | Speed (time) | Capacity (volume) |
| Unit | Milliseconds (ms) | Requests/second (RPS) |
| Analogy | Speed of one car | Cars per hour on highway |
| Goal | Lower is better | Higher is better |

## 🔗 Week 1 Cheat Sheet

| Term | Definition |
|------|-----------|
| **System Design** | Blueprint of your application |
| **Client** | Requests data (browser, app) |
| **Server** | Responds with data (backend) |
| **API** | Bridge between client & server |
| **SQL** | Structured, tables, relationships |
| **NoSQL** | Flexible, documents, scalable |
| **Vertical Scaling** | Bigger machine (scale up) |
| **Horizontal Scaling** | More machines (scale out) |
| **Latency** | Speed per request (ms) |
| **Throughput** | Requests per second (RPS) |
| **CRUD** | Create, Read, Update, Delete |
| **JSON** | API data format |
| **ACID** | SQL transaction guarantees |
| **3-Tier Architecture** | Client → App Server → Database |

## 🌍 How Instagram Uses All 6 Concepts

| Concept | How Instagram Uses It |
|---------|----------------------|
| **System Design** | Planned architecture to handle billions of users |
| **Client-Server** | Your app (client) sends requests to Instagram's servers |
| **APIs** | GET (fetch feed), POST (upload photo), DELETE (remove post) |
| **SQL + NoSQL** | SQL for user accounts & payments; NoSQL (Cassandra) for feeds & activity |
| **Horizontal Scaling** | Thousands of servers across data centers worldwide |
| **Latency & Throughput** | Feed loads in <200ms; serves 2B+ users |

## 💡 Top 3 Lessons From Week 1

1. **System Design isn't scary** — it's just planning how things connect
2. **Every concept builds on the previous one** — the learning compounds
3. **Learning in public forces deeper understanding** — if you can explain it, you know it

## 📅 What's Coming in Week 2: Making Systems F aster

| Day | Topic | Teaser |
|-----|-------|--------|
| Day 8 | Load Balancers | The traffic police of the internet |
| Day 9 | Caching | The #1 speed hack for any system |
| Day 10 | CDN | Serve content from the nearest location |
| Day 11 | Proxy vs Reverse Proxy | Two proxies that do opposite things |
| Day 12 | Database Indexing | Finding data fast in millions of rows |
| Day 13 | Database Replication | Your safety net when servers die |
| Day 14 | Week 2 Recap | Connecting it all together again |

---

⭐ Star this repo if you're learning along!

📬 Connect with me:
- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
