# Day 19: API Gateway

> 🗓️ Day 19 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is an API Gateway?

An **API Gateway** is a single entry point that sits between clients and your backend services. It acts as a **reverse proxy**, accepting all client requests, routing them to the appropriate microservice, and handling cross-cutting concerns like authentication, rate limiting, and caching.

> When you have dozens of microservices, clients shouldn’t need to know about all of them. The gateway is the one address they talk to.

## 🏢 The Receptionist Analogy

|Scenario               |What Happens                                                                                                 |
|-----------------------|-------------------------------------------------------------------------------------------------------------|
|**Without API Gateway**|Client must know every service’s address — like knocking on every door in a company to find the right person.|
|**With API Gateway**   |Client talks to ONE front desk. A receptionist routes you to the right person. One address for everything.   |

## 🎭 Think of It As…

|Role                  |What It Does                                                       |
|----------------------|-------------------------------------------------------------------|
|**Traffic Controller**|Routes each request to the correct backend service                 |
|**Security Guard**    |Checks authentication/authorization before letting requests through|
|**Translator**        |Handles different protocols and data formats                       |
|**Receptionist**      |Provides one door for all client requests                          |

## ⚙️ What an API Gateway Handles

|Function                |Description                                            |
|------------------------|-------------------------------------------------------|
|**Routing**             |Directs requests to the right service based on URL/path|
|**Authentication**      |Verifies identity (JWT, OAuth, API keys)               |
|**Authorization**       |Enforces access control policies                       |
|**Rate Limiting**       |Limits requests per client to prevent abuse            |
|**Load Balancing**      |Distributes requests across service instances          |
|**Caching**             |Stores frequent responses to reduce latency            |
|**Request Aggregation** |Combines multiple service calls into one response      |
|**Logging & Monitoring**|Tracks requests, latency, and error rates              |
|**SSL Termination**     |Handles HTTPS encryption/decryption                    |


> These are called **cross-cutting concerns** — instead of every microservice implementing auth and rate limiting, the gateway does it once for all.

## 🦸 Superpower: Request Aggregation

One of the most powerful features. A single client request can fetch data from **multiple services** and combine the results.

### Example: Loading a profile page

```
Step 1: Client asks gateway for the profile page
Step 2: Gateway calls User service     → name, photo
Step 3: Gateway calls Posts service    → recent posts
Step 4: Gateway calls Friends service  → friend list
Step 5: Gateway combines all 3 into ONE response
```

**Result:** The client makes 1 request instead of 3. Fewer round trips = faster app, especially on mobile networks.

This pattern is also called **Backend for Frontend (BFF)** when you build a gateway tailored to a specific client (e.g., one gateway optimized for mobile, another for web).

## ⚖️ API Gateway vs Load Balancer

|Aspect                  |API Gateway                           |Load Balancer                   |
|------------------------|--------------------------------------|--------------------------------|
|**Layer**               |Layer 7 (application)                 |Layer 4 or 7                    |
|**Routes by**           |URL path, content, headers            |IP, port (or basic rules)       |
|**Knows business logic**|Yes                                   |No                              |
|**Features**            |Auth, rate limit, aggregation, caching|Just traffic distribution       |
|**Example**             |`/users` → User service               |Spread requests across 3 servers|


> **Key insight:** They’re not competitors. An API Gateway often **uses a load balancer internally** to distribute traffic across instances of each service.

## 🛠️ Popular API Gateways

|Tool                    |Type       |Notes                                        |
|------------------------|-----------|---------------------------------------------|
|**Amazon API Gateway**  |Managed    |Serverless, integrates with AWS Lambda       |
|**Kong**                |Open-source|Plugin-based, highly extensible, very popular|
|**NGINX**               |Self-hosted|High performance, also a reverse proxy       |
|**Apigee (Google)**     |Enterprise |API management, analytics, monetization      |
|**Azure API Management**|Managed    |Microsoft Azure ecosystem                    |
|**Spring Cloud Gateway**|Library    |Popular in Java/Spring microservices         |

## ✅ Benefits

- **Simplifies clients** — one endpoint instead of many
- **Centralizes security** — auth in one place, not every service
- **Reduces client complexity** — aggregation means fewer calls
- **Hides internal structure** — clients don’t see your service layout
- **Easier to evolve** — change services without breaking clients

## ⚠️ Drawbacks

- **Single point of failure** — if the gateway goes down, everything is unreachable (mitigate with multiple gateway instances)
- **Added latency** — one extra hop per request
- **Can become a bottleneck** — must be scaled carefully
- **Development coupling** — teams may need to coordinate gateway changes

## 🔗 How This Connects to Previous Concepts

|Day   |Concept       |Connection                                     |
|------|--------------|-----------------------------------------------|
|Day 3 |APIs          |The gateway is the front door for all your APIs|
|Day 8 |Load Balancers|Gateway uses load balancing internally         |
|Day 9 |Caching       |Gateway caches common responses                |
|Day 11|Reverse Proxy |An API gateway IS a specialized reverse proxy  |
|Day 18|Microservices |Gateways are essential for microservices       |

## 💡 Key Takeaways

1. **API Gateway = single entry point** for all client requests
1. Handles **auth, rate limiting, routing, caching** — cross-cutting concerns
1. **Request aggregation** combines multiple service calls into one
1. **Different from a load balancer** — gateway knows business logic, LB just distributes
1. Essential for **microservices** — clients talk to one door, not 50 services
1. Watch out for it becoming a **single point of failure** — run multiple instances

## 🔗 Resources

- [Role of API Gateway — GeeksforGeeks](https://www.geeksforgeeks.org/system-design/what-is-the-role-of-api-gateway-in-microservices/)
- [API Gateway Pattern — Microservices.io](https://microservices.io/patterns/apigateway.html)
- [API Gateway vs Direct Communication — Microsoft](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/architect-microservice-container-applications/direct-client-to-microservice-communication-versus-the-api-gateway-pattern)
- [API Gateway Microservices — Gravitee](https://www.gravitee.io/blog/api-gateway-microservices-optimizing-architecture)

## ➡️ What’s Next?

**Day 20: Consistent Hashing** — When you add or remove a server, how do you avoid reshuffling ALL your data? Consistent hashing is the elegant algorithm behind distributed caches, databases, and load balancers.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)