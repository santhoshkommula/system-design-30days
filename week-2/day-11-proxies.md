# Day 11: Proxy vs Reverse Proxy

> 🗓️ Day 11 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is a Proxy?

A **proxy** is a server that acts as an **intermediary** between two parties in a network. Instead of communicating directly, one side talks through the proxy. There are two types that do opposite things.

## 🧠 The Analogy

|Type             |Analogy                                                           |
|-----------------|------------------------------------------------------------------|
|**Forward Proxy**|Your friend ordering food for you — the restaurant never sees you |
|**Reverse Proxy**|A receptionist at a company — you never see the employees directly|

## ➡️ Forward Proxy (Proxy Server)

A **forward proxy** sits between the **client** and the **internet**. It acts on behalf of the client.

### How It Works:

```
You (Client) → Forward Proxy → Internet (Servers)
                  ↑
          Hides YOUR identity
          Server sees the proxy, not you
```

### What It Does:

|Function                 |Description                                          |
|-------------------------|-----------------------------------------------------|
|**Hides your identity**  |Server sees proxy’s IP, not yours                    |
|**Bypasses restrictions**|Access blocked content via a proxy in another country|
|**Caches content**       |Stores web pages locally for faster repeat access    |
|**Filters content**      |Companies/schools block certain websites             |
|**Logging & monitoring** |Track what employees/students access                 |

### Use Cases:

- **VPN services** — Hide your IP while browsing
- **Corporate firewalls** — Block social media at work
- **School networks** — Filter inappropriate content
- **Web scraping** — Rotate IPs to avoid getting blocked

### Popular Forward Proxies:

- **Squid Proxy** — Open-source, widely used
- **VPN services** — NordVPN, ExpressVPN (act as forward proxies)
- **TOR Browser** — Routes through multiple proxies for anonymity

## ⬅️ Reverse Proxy

A **reverse proxy** sits between the **internet** and the **backend servers**. It acts on behalf of the servers.

### How It Works:

```
Client (Users) → Reverse Proxy → Backend Servers
                     ↑
             Hides the SERVERS
             Client sees the proxy, not the servers
```

### What It Does:

|Function           |Description                                         |
|-------------------|----------------------------------------------------|
|**Load balancing** |Distributes traffic across multiple servers (Day 8!)|
|**Security**       |Hides backend server IPs from attackers             |
|**SSL termination**|Handles HTTPS encryption/decryption                 |
|**Caching**        |Caches responses for faster delivery (Day 9!)       |
|**Compression**    |Compresses responses to reduce bandwidth            |
|**Rate limiting**  |Prevents abuse by limiting requests per user        |

### Use Cases:

- **Web applications** — Nginx/Apache in front of app servers
- **Microservices** — Route `/api` to backend, `/images` to CDN
- **DDoS protection** — Cloudflare absorbs attack traffic
- **SSL offloading** — Handle HTTPS at the proxy, not at every server

### Popular Reverse Proxies:

- **Nginx** — Most popular, used by ~34% of all websites
- **Cloudflare** — CDN + reverse proxy + DDoS protection
- **HAProxy** — High-performance TCP/HTTP proxy
- **AWS ALB** — Application Load Balancer
- **Traefik** — Popular in Docker/Kubernetes environments
- **Apache HTTP Server** — Classic, with mod_proxy

## ⚔️ Forward vs Reverse — Head to Head

|Aspect       |Forward Proxy                      |Reverse Proxy                      |
|-------------|-----------------------------------|-----------------------------------|
|**Position** |In front of clients                |In front of servers                |
|**Protects** |The client (you)                   |The server (backend)               |
|**Hides**    |Client’s identity/IP               |Server’s identity/IP               |
|**Used by**  |End users, companies               |Websites, APIs, services           |
|**Purpose**  |Privacy, access control, filtering |Security, load balancing, caching  |
|**Who knows**|Server doesn’t know the real client|Client doesn’t know the real server|
|**Examples** |VPN, Squid, corporate firewalls    |Nginx, Cloudflare, AWS ALB         |
|**Direction**|Client → Proxy → Internet          |Internet → Proxy → Servers         |

### The One-Line Difference:

> **Forward proxy:** Ensures no server ever communicates directly with the client.
> **Reverse proxy:** Ensures no client ever communicates directly with the server.

## 🔗 How Reverse Proxy Connects Everything

The reverse proxy is actually a **super-concept** that ties together many things we’ve learned:

|Day   |Concept       |How Reverse Proxy Relates                |
|------|--------------|-----------------------------------------|
|Day 8 |Load Balancers|Reverse proxy IS a load balancer         |
|Day 9 |Caching       |Reverse proxy caches responses           |
|Day 10|CDN           |CDN acts as a reverse proxy at the edge  |
|Day 3 |APIs          |API requests pass through reverse proxies|

## 🌍 Real-World Examples

|Tool                  |Type         |What It Does                                         |
|----------------------|-------------|-----------------------------------------------------|
|**VPN**               |Forward Proxy|Hides your IP when browsing the internet             |
|**Nginx**             |Reverse Proxy|Routes traffic to backend servers, handles SSL       |
|**Cloudflare**        |Reverse Proxy|Protects websites, caches content, blocks DDoS       |
|**Corporate Firewall**|Forward Proxy|Blocks employees from accessing social media         |
|**TOR Browser**       |Forward Proxy|Routes through multiple proxies for maximum anonymity|

## 💡 Key Takeaways

1. **Forward proxy = hides the client**, sits between client and internet
1. **Reverse proxy = hides the server**, sits between internet and backend
1. Forward proxy is used for **privacy, access control, and filtering**
1. Reverse proxy is used for **load balancing, security, SSL, and caching**
1. **Nginx** is the most popular reverse proxy (~34% of websites)
1. A reverse proxy **connects** load balancing (Day 8), caching (Day 9), and CDN (Day 10)

## 🔗 Resources

- [Proxy vs Reverse Proxy — AlgoMaster](https://medium.com/algomaster-io/proxy-vs-reverse-proxy-d73a2eecbb2b)
- [Forward vs Reverse Proxy — EnjoyAlgorithms](https://www.enjoyalgorithms.com/blog/proxies-in-system-design/)
- [Proxy vs Reverse Proxy — System Design School](https://systemdesignschool.io/blog/proxy-vs-reverse-proxy)
- [Forward vs Reverse Proxy — StrongDM](https://www.strongdm.com/blog/difference-between-proxy-and-reverse-proxy)

## ➡️ What’s Next?

**Day 12: Database Indexing** — Your database has 10 million rows. Without indexing, every search checks ALL of them. Indexing is like the index page of a book — it tells you exactly where to find what you need.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)