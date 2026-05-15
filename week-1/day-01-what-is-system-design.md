# Day 1 — What is System Design?

## What is it?

System design is the process of planning **how** your application will work at a high level — before you write a single line of code. It's about deciding where data will be stored, how users will connect, what happens when a million users show up, and how different services talk to each other.

**Coding is laying bricks. System design is drawing the blueprint.**

## Why does it matter?

- It's the **#1 topic** in senior engineering interviews
- You'll build faster, more reliable applications
- You move from "coder" to "architect" — the person who sees the big picture
- Developers who understand system design get promoted faster

Even with real production experience (I've built POS systems, food delivery platforms, real-time chat), formally studying system design helps you connect the dots between what you've done and why it works.

## How does it work?

When you open Instagram:

```
1. Your phone (CLIENT) sends a request
       ↓
2. It travels through the internet via an API
       ↓
3. A LOAD BALANCER routes it to the right server
       ↓
4. A SERVER processes the request
       ↓
5. A CACHE checks if the data is already available
       ↓
6. A DATABASE fetches what's needed
       ↓
7. A CDN serves the images from a nearby location
       ↓
8. The feed appears on your screen
```

System design = planning how ALL these pieces connect and scale.

### The core questions system design answers:

- **Where** will data be stored? → Database choices
- **How** will users connect? → APIs, protocols
- **What** happens when traffic spikes? → Scaling strategies
- **What** if a server goes down? → Reliability, redundancy
- **How** do different services talk? → Communication patterns

## Coding vs System design

| Coding | System Design |
|--------|--------------|
| How to implement a feature | How to structure the whole application |
| Solving one problem | Solving for millions of users |
| "Make this function work" | "Make this system reliable at scale" |
| Data structures & algorithms | Architecture & infrastructure |
| Runs on your laptop | Runs on hundreds of servers |

## The building blocks (what we'll learn in 30 days)

- **Client & Server** — who asks, who answers
- **APIs** — how systems talk to each other
- **Databases** — where data lives (SQL vs NoSQL)
- **Cache** — making things faster
- **Load Balancer** — distributing traffic
- **CDN** — serving content globally
- **Message Queues** — handling async work
- **Sharding, Replication, CAP Theorem** — reliability at scale
- **Real-world designs** — URL shortener, chat system, notification service, and more

## Diagram

![Day 1 — What is System Design](diagrams/day-01.png)

## Key questions for interviews

1. **What is system design?** → Planning the architecture of a software system to handle scale, reliability, and performance.
2. **Why not just code and figure it out later?** → Changing architecture after building is 10x harder than planning upfront.
3. **When do you need system design?** → Anytime your system serves more than a handful of users, or needs to be reliable, fast, and maintainable.

## What I learned today

_[Your personal reflection here]_

## Resources

- [ByteByteGo — System Design 101](https://blog.bytebytego.com/)
- Chapter 1 of *System Design Interview* by Alex Xu
- [NeetCode — System Design for Beginners](https://neetcode.io)

---

*Tomorrow: Day 2 — Client-Server Architecture*
