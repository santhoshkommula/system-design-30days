# 🏗 System Design — 30 Days Challenge

> Learning system design from scratch, one concept per day. Notes, diagrams, and mini implementations.
>
> By [Santhosh Kommula](https://github.com/santhoshkommula) — Full Stack Developer at Roadeazy Inc

[![30 Day Challenge](https://img.shields.io/badge/challenge-30%20days-blue)]()
[![Topics](https://img.shields.io/badge/topics-30-green)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

---

## Why this repo?

I'm a full stack developer with experience building real-time systems, food delivery platforms, POS architectures, and computer vision applications. But I never formally studied system design — so I'm doing it now, in public.

Every day for 30 days: one concept, clear notes, a diagram, and (in Week 4) mini implementations.

Star this repo to follow along. Fork it if you want to do the challenge yourself.

---

## 📅 Roadmap

### Week 1 — The Foundations (Days 1-7)

| Day | Topic | Notes | Diagram | Key takeaway |
|-----|-------|-------|---------|-------------|
| 1 | What is System Design? | [notes](week-1/day-01-what-is-system-design.md) | [diagram](week-1/diagrams/day-01.png) | It's not about code — it's about how pieces connect at scale |
| 2 | Client-Server Architecture | [notes](week-1/day-02-client-server.md) | [diagram](week-1/diagrams/day-02.png) | Everything on the internet is a client asking a server |
| 3 | What is an API? | [notes](week-1/day-03-apis.md) | [diagram](week-1/diagrams/day-03.png) | APIs are contracts between systems |
| 4 | Databases: SQL vs NoSQL | [notes](week-1/day-04-sql-vs-nosql.md) | [diagram](week-1/diagrams/day-04.png) | Choose based on data shape, not hype |
| 5 | Vertical vs Horizontal Scaling | [notes](week-1/day-05-scaling.md) | [diagram](week-1/diagrams/day-05.png) | Scale up has a ceiling; scale out is the way |
| 6 | Latency & Throughput | [notes](week-1/day-06-latency-throughput.md) | [diagram](week-1/diagrams/day-06.png) | Fast != high capacity — you need both |
| 7 | Week 1 Recap | [notes](week-1/day-07-recap.md) | — | Connecting all 6 concepts together |

### Week 2 — Making Systems Faster (Days 8-14)

| Day | Topic | Notes | Diagram | Key takeaway |
|-----|-------|-------|---------|-------------|
| 8 | Load Balancers | [notes](week-2/day-08-load-balancers.md) | [diagram](week-2/diagrams/day-08.png) | Distribute traffic so no single server dies |
| 9 | Caching | [notes](week-2/day-09-caching.md) | [diagram](week-2/diagrams/day-09.png) | The fastest query is the one you never make |
| 10 | CDN | [notes](week-2/day-10-cdn.md) | [diagram](week-2/diagrams/day-10.png) | Serve content from the nearest location |
| 11 | Proxy vs Reverse Proxy | [notes](week-2/day-11-proxies.md) | [diagram](week-2/diagrams/day-11.png) | Forward hides the client; reverse hides the server |
| 12 | Database Indexing | [notes](week-2/day-12-indexing.md) | [diagram](week-2/diagrams/day-12.png) | An index turns O(n) into O(log n) |
| 13 | Database Replication | [notes](week-2/day-13-replication.md) | [diagram](week-2/diagrams/day-13.png) | Your safety net when the primary goes down |
| 14 | Week 2 Recap | [notes](week-2/day-14-recap.md) | — | Caching + CDN + LB + replication together |

### Week 3 — Designing for Reliability (Days 15-21)

| Day | Topic | Notes | Diagram | Key takeaway |
|-----|-------|-------|---------|-------------|
| 15 | Database Sharding | [notes](week-3/day-15-sharding.md) | [diagram](week-3/diagrams/day-15.png) | Split one big DB into many smaller ones |
| 16 | CAP Theorem | [notes](week-3/day-16-cap-theorem.md) | [diagram](week-3/diagrams/day-16.png) | Pick 2 of 3: consistency, availability, partition tolerance |
| 17 | Message Queues | [notes](week-3/day-17-message-queues.md) | [diagram](week-3/diagrams/day-17.png) | Decouple producers from consumers |
| 18 | Microservices vs Monolith | [notes](week-3/day-18-microservices.md) | [diagram](week-3/diagrams/day-18.png) | Start monolith, split when you have a reason |
| 19 | API Gateway | [notes](week-3/day-19-api-gateway.md) | [diagram](week-3/diagrams/day-19.png) | One door for all your microservices |
| 20 | Consistent Hashing | [notes](week-3/day-20-consistent-hashing.md) | [diagram](week-3/diagrams/day-20.png) | Add/remove servers without reshuffling everything |
| 21 | Week 3 Recap | [notes](week-3/day-21-recap.md) | — | Building blocks of reliable distributed systems |

### Week 4 — Real-World System Designs (Days 22-30)

| Day | Topic | Notes | Diagram | Mini project |
|-----|-------|-------|---------|-------------|
| 22 | Design: URL Shortener | [notes](week-4/day-22-url-shortener.md) | [diagram](week-4/diagrams/day-22.png) | [code](projects/url-shortener/) |
| 23 | Design: Rate Limiter | [notes](week-4/day-23-rate-limiter.md) | [diagram](week-4/diagrams/day-23.png) | [code](projects/rate-limiter/) |
| 24 | Design: Chat System | [notes](week-4/day-24-chat-system.md) | [diagram](week-4/diagrams/day-24.png) | [code](projects/chat-system/) |
| 25 | Design: Notification Service | [notes](week-4/day-25-notifications.md) | [diagram](week-4/diagrams/day-25.png) | [code](projects/notification-service/) |
| 26 | Design: News Feed | [notes](week-4/day-26-news-feed.md) | [diagram](week-4/diagrams/day-26.png) | — |
| 27 | Design: Search Autocomplete | [notes](week-4/day-27-autocomplete.md) | [diagram](week-4/diagrams/day-27.png) | — |
| 28 | Design: Distributed Cache | [notes](week-4/day-28-distributed-cache.md) | [diagram](week-4/diagrams/day-28.png) | — |
| 29 | Design: Video Streaming | [notes](week-4/day-29-video-streaming.md) | [diagram](week-4/diagrams/day-29.png) | — |
| 30 | Final Recap & Reflection | [notes](week-4/day-30-final-recap.md) | — | — |

---

## 📁 Repo structure

```
system-design-30days/
├── README.md
├── LICENSE
├── week-1/
│   ├── day-01-what-is-system-design.md
│   ├── day-02-client-server.md
│   ├── ...
│   └── diagrams/
├── week-2/
├── week-3/
├── week-4/
├── projects/
│   ├── url-shortener/
│   ├── rate-limiter/
│   ├── chat-system/
│   └── notification-service/
└── resources/
    └── references.md
```

---

## 📝 Daily note template

```markdown
# Day X — [Topic Name]

## What is it?
## Why does it matter?
## How does it work?
## Diagram
## Real-world examples
## Trade-offs (Pros vs Cons)
## Key interview questions
## What I learned today
## Resources
```

---

## 📚 References

- *Designing Data-Intensive Applications* — Martin Kleppmann
- *System Design Interview* — Alex Xu (Vol 1 & 2)
- [ByteByteGo YouTube](https://youtube.com/@ByteByteGo)
- [NeetCode System Design](https://neetcode.io)

---

## License

MIT

---

*Follow the journey: [YouTube](https://www.youtube.com/@santhosh.kommula) · [Instagram](https://www.instagram.com/santhoshkommula.dev) · [LinkedIn](https://www.linkedin.com/in/swamy-santhosh-866407292)*
