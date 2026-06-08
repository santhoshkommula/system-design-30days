# Day 21: Week 3 Recap — Designing for Reliability

> 🗓️ Day 21 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🎉 Week 3 Complete!

This week was about **scaling and reliability** — how systems handle massive data, survive failures, and stay online. Here’s how it all connects.

## 🗺️ The Big Picture

```
                  ┌─────────────┐
                  │   Clients   │
                  └──────┬──────┘
                         │
              ┌──────────▼──────────┐
              │ API Gateway (Day 19)│  ← Single entry, auth, routing
              └──────────┬──────────┘
                         │
              ┌──────────▼──────────┐
              │ Microservices(Day18)│  ← Independent services
              └───┬─────────────┬───┘
                  │             │
          ┌───────▼───┐   ┌────▼──────┐
          │ Service A │   │ Service B │
          │ + Queue   │   │ + Queue   │  ← Message Queues (Day 17)
          │ (Day 17)  │   │           │
          └─────┬─────┘   └─────┬─────┘
                │               │
        ┌───────▼───────────────▼───────┐
        │  Sharded DB (Day 15)          │  ← Consistent Hashing (Day 20)
        │  + CAP choice (Day 16)        │     distributes the data
        └───────────────────────────────┘

        Week 3 = Reliability at Scale:
        Distribute, decouple, and survive failures.
```

## 📋 Day-by-Day Recap

### Day 15: Database Sharding

**One-liner:** Split one giant database into smaller pieces across servers.

- Library branches analogy (A-I, J-R, S-Z)
- Strategies: range-based, hash-based, directory, geographic
- Challenge: cross-shard queries, hotspots

### Day 16: CAP Theorem

**One-liner:** You can only guarantee two of Consistency, Availability, Partition tolerance.

- The ATM dilemma when the network splits
- CP = correct data (banking); AP = always online (social media)
- Partition tolerance is mandatory in distributed systems

### Day 17: Message Queues

**One-liner:** Services communicate asynchronously through a buffer.

- Producer → Queue → Consumer
- Restaurant ticket-rail analogy
- Point-to-Point vs Publish-Subscribe; Kafka vs RabbitMQ

### Day 18: Microservices vs Monolith

**One-liner:** One big app or many small independent services.

- Swiss Army knife vs toolbox
- Start with a monolith, split when you have a reason
- Netflix, Amazon migrated; Shopify stayed modular monolith

### Day 19: API Gateway

**One-liner:** A single front door to all your backend services.

- Receptionist analogy
- Handles routing, auth, rate limiting, caching, aggregation
- Different from a load balancer (knows business logic)

### Day 20: Consistent Hashing

**One-liner:** Add or remove servers while moving the fewest keys possible.

- Hash ring with servers + keys
- Only k/N keys move when scaling
- Virtual nodes for even distribution

## 🔗 Week 3 Cheat Sheet

|Term                  |Definition                                            |
|----------------------|------------------------------------------------------|
|**Sharding**          |Split data across multiple servers                    |
|**Shard Key**         |Decides which shard data goes to                      |
|**CAP Theorem**       |Pick 2: Consistency, Availability, Partition tolerance|
|**CP**                |Correct data, may go offline                          |
|**AP**                |Always online, may be stale                           |
|**Message Queue**     |Async buffer between services                         |
|**Producer/Consumer** |Sends / processes messages                            |
|**Pub-Sub**           |One message, many consumers                           |
|**Monolith**          |One unified application                               |
|**Microservices**     |Many small independent services                       |
|**API Gateway**       |Single entry point for clients                        |
|**Consistent Hashing**|Scale without reshuffling all data                    |
|**Virtual Nodes**     |Multiple ring positions per server                    |

## 🚗 How Uber Uses All 6 Concepts

|Concept               |Uber’s Implementation                               |
|----------------------|----------------------------------------------------|
|**Sharding**          |Trip data sharded by city/region                    |
|**CAP Theorem**       |AP for driver locations (fast updates matter most)  |
|**Message Queues**    |Ride requests queued and matched to drivers         |
|**Microservices**     |Separate services: pricing, maps, payments, matching|
|**API Gateway**       |One entry point for rider and driver apps           |
|**Consistent Hashing**|Distributes load and data across servers            |

## 📊 Progress: 21 Days, 70% Complete!

|Week      |Theme                    |Concepts                                                    |
|----------|-------------------------|------------------------------------------------------------|
|**Week 1**|Building Blocks          |Design, Client-Server, APIs, SQL/NoSQL, Scaling, Latency    |
|**Week 2**|Making Systems Faster    |Load Balancers, Caching, CDN, Proxies, Indexing, Replication|
|**Week 3**|Designing for Reliability|Sharding, CAP, Queues, Microservices, Gateway, Hashing      |

## 📅 What’s Coming in Week 4: Real-World System Designs

This is where everything comes together — we’ll design actual systems!

|Day   |Topic                       |
|------|----------------------------|
|Day 22|Design a URL Shortener      |
|Day 23|Design Rate Limiting        |
|Day 24|Design a Chat System        |
|Day 25|Design a News Feed          |
|Day 26|Design a Notification System|
|Day 27|Design Blob/File Storage    |
|Day 28|Week 4 Recap                |

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)