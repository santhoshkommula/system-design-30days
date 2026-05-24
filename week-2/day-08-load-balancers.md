# Day 8: Load Balancers

> 🗓️ Day 8 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

---

## 🤔 What is a Load Balancer?

A **Load Balancer** is a device or software that **distributes incoming network traffic across multiple servers** to ensure no single server gets overwhelmed. It sits between the client and the server pool, acting as the **single entry point** for all requests.

## 🚗 The Toll Booth Analogy

| Scenario | What Happens |
|----------|-------------|
| **Without Load Balancer** | One toll booth for all cars — huge queue, slow, if it breaks nobody gets through |
| **With Load Balancer** | Multiple toll booths — traffic split evenly, fast, one breaks others still work |

## ⚙️ What Does a Load Balancer Do?

| Function | Description |
|----------|-------------|
| **Distributes traffic** | Splits requests across servers evenly |
| **Health checks** | Periodically tests if servers are alive and healthy |
| **Prevents overload** | No single server gets crushed by too many requests |
| **Improves availability** | If one server dies, traffic reroutes to healthy ones |
| **SSL termination** | Can handle HTTPS encryption/decryption |
| **Session persistence** | Can ensure a user stays on the same server |

## 🔄 How It Works — Step by Step

```
Step 1: User sends a request → example.com
             ↓
Step 2: Load Balancer receives it (single entry point)
             ↓
Step 3: LB picks the best server (using an algorithm)
             ↓
Step 4: Server processes the request
             ↓
Step 5: Response goes back through LB → User
```

**Key point:** The user never knows how many servers exist behind the load balancer. They only know `example.com`.

## 🧮 Load Balancing Algorithms

### Static Algorithms (don't consider server state):

| Algorithm | How It Works | When to Use |
|-----------|-------------|-------------|
| **Round Robin** | Sends requests one-by-one: A → B → C → A → B → C | All servers have equal power |
| **Weighted Round Robin** | Servers with more power get proportionally more traffic | Servers have different capacities |
| **IP Hash** | User's IP determines which server they go to (always the same) | When session persistence is needed |

### Dynamic Algorithms (consider current server state):

| Algorithm | How It Works | When to Use |
|-----------|-------------|-------------|
| **Least Connections** | Picks the server with fewest active connections | Requests have varying processing times |
| **Least Response Time** | Picks the server with fastest recent response time | When speed is the top priority |
| **Resource Based** | Picks the server with most available CPU/RAM | Servers handle very different workloads |

## 🏗️ Types: Layer 4 vs Layer 7

| Feature | Layer 4 (Transport) | Layer 7 (Application) |
|---------|--------------------|-----------------------|
| **Routes based on** | IP address & port number | URL, headers, cookies, content |
| **Sees** | TCP/UDP packets only | Full HTTP request |
| **Speed** | Very fast (no content inspection) | Slightly slower (reads content) |
| **Intelligence** | Basic routing | Smart routing |
| **Use case** | High-speed, simple traffic | Microservices, complex routing |
| **Example** | AWS NLB, HAProxy (TCP mode) | AWS ALB, Nginx, Cloudflare |

### When to use which:
- **Layer 4:** When you need raw speed and simple distribution (gaming, streaming)
- **Layer 7:** When you need content-based routing (`/api` → backend servers, `/images` → CDN)

## 🌍 Real-World Examples

| Company | How They Use Load Balancers |
|---------|---------------------------|
| **Netflix** | Routes millions of streams to nearest, least-loaded server |
| **Amazon** | Spins up servers on Black Friday, LB distributes traffic instantly |
| **Google** | Distributes searches across data centers worldwide |
| **Uber** | Routes ride requests to nearest available server in your region |

## ⚠️ Challenges

| Challenge | Solution |
|-----------|---------|
| **Single point of failure** | Use multiple load balancers (active-passive or active-active) |
| **Added latency** | Small overhead per request hop — usually negligible |
| **Complexity** | SSL certificates, health checks, configuration management |
| **Session persistence** | Use sticky sessions or IP hash algorithm |

## 🔗 Popular Load Balancers

| Name | Type | Notes |
|------|------|-------|
| **Nginx** | Software (L7) | Most popular, also serves as reverse proxy |
| **HAProxy** | Software (L4/L7) | High performance, widely used |
| **AWS ALB** | Cloud (L7) | Application Load Balancer — content-based |
| **AWS NLB** | Cloud (L4) | Network Load Balancer — ultra fast |
| **Cloudflare** | Cloud (L7) | Also provides CDN and DDoS protection |

## 🔗 How This Connects to Previous Concepts

| Day | Concept | Connection |
|-----|---------|------------|
| Day 2 | Client-Server | LB sits between client and servers |
| Day 3 | APIs | API requests go through the load balancer |
| Day 5 | Horizontal Scaling | LB is what makes scaling out possible |
| Day 6 | Throughput | LB increases throughput by distributing load |

## 💡 Key Takeaways

1. A load balancer **distributes traffic** across multiple servers
2. **Round Robin** is the simplest algorithm — sends requests one by one
3. **Layer 4 = fast** (routes by IP), **Layer 7 = smart** (routes by content)
4. LB enables **horizontal scaling** (Day 5) — it's the key component
5. **Health checks** detect dead servers and reroute traffic automatically

## 🔗 Resources

- [Load Balancers for Beginners — Medium](https://medium.com/@shashwatwrites/system-design-load-balancers-for-beginners-d60d4dbf8d78)
- [Load Balancing Algorithms — AlgoMaster](https://algomaster.io/learn/system-design/load-balancing-algorithms)
- [Introduction to Load Balancing — Design Gurus](https://www.designgurus.io/course-play/grokking-system-design-fundamentals/doc/introduction-to-load-balancing)
- [Load Balancer — Towards Data Science](https://towardsdatascience.com/system-design-load-balancer-9a3582176f9b/)

## ➡️ What's Next?

**Day 9: Caching** — The #1 speed hack for any system. The fastest database query is the one you never make. We'll learn how caching stores frequently accessed data in memory for lightning-fast responses.

---

⭐ Star this repo if you're learning along!

📬 Connect with me:
- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
