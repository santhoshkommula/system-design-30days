# Day 12: Database Indexing

> 🗓️ Day 12 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is Database Indexing?

A **database index** is a separate data structure that stores **sorted pointers** to your actual data, allowing the database to find rows without scanning the entire table.

> **Without an index:** Searching 10M rows = check all 10M (full table scan).
> **With an index:** Jump straight to the matching row (indexed lookup).

## 📖 The Book Analogy

|Scenario         |What Happens                                                           |
|-----------------|-----------------------------------------------------------------------|
|**Without Index**|Looking for “Database” in a 500-page book? Read every page from page 1.|
|**With Index**   |Flip to the index: “Database — pages 42, 87, 156.” Jump directly there.|

## ⚙️ How Indexing Works

```
Step 1: You create an index on a column (e.g., email)
Step 2: DB builds a sorted B-Tree data structure
Step 3: When you query → SELECT * FROM users WHERE email = 'x@mail.com'
Step 4: DB searches the B-Tree index (log N time)
Step 5: Index points to the exact row → return instantly
```

**Without index:** O(N) — scan all rows. **With index:** O(log N) — binary search through sorted tree.

## 🏗️ Types of Indexes

|Type               |Description                       |Example                          |
|-------------------|----------------------------------|---------------------------------|
|**Primary Index**  |Auto-created on primary key       |`id` column — every table has one|
|**Secondary Index**|Created on any other column       |Index on `email` or `username`   |
|**Composite Index**|Index on multiple columns together|Index on `(city, age)`           |
|**Unique Index**   |Ensures no duplicate values       |Unique index on `email`          |
|**Full-Text Index**|Searches inside text content      |Search blog post body text       |

## 🌳 B-Tree: The Most Common Index Structure

Most databases (MySQL, PostgreSQL, etc.) use **B-Trees** for indexing:

- Balanced tree structure with sorted keys
- Each node can have multiple children
- Search, insert, delete all in **O(log N)** time
- Great for range queries (`WHERE age > 25 AND age < 50`)

## ⚖️ The Tradeoff

|Aspect         |With Index                    |Without Index                |
|---------------|------------------------------|-----------------------------|
|**Read speed** |Very fast (O(log N))          |Slow (O(N) full scan)        |
|**Write speed**|Slower (index must be updated)|Faster (no index to maintain)|
|**Storage**    |Uses extra disk space         |No extra space               |
|**Best for**   |Read-heavy workloads          |Write-heavy, small tables    |

## ✅ When to Index

**Index these columns:**

- Primary keys (auto-indexed)
- Foreign keys (used in JOINs)
- Columns in WHERE clauses
- Columns used for ORDER BY / GROUP BY

**Don’t index:**

- Small tables (full scan is fast enough)
- Columns with lots of NULL values
- Columns you rarely query
- Tables with very heavy write operations

## 🌍 Real-World Examples

|Company      |What They Index            |Result                             |
|-------------|---------------------------|-----------------------------------|
|**Amazon**   |`product_id`               |Find any product in milliseconds   |
|**Gmail**    |`sender`, `date`, `subject`|Search billions of emails instantly|
|**Uber**     |`location`, `driver_id`    |Find nearest driver in real-time   |
|**Instagram**|`user_id`, `timestamp`     |Load feed sorted by time           |

## 🔗 How This Connects

|Day  |Concept      |Connection                               |
|-----|-------------|-----------------------------------------|
|Day 4|SQL Databases|Indexing is a core SQL optimization      |
|Day 6|Latency      |Indexes dramatically reduce query latency|
|Day 9|Caching      |Cache + Index = maximum read speed       |

## 💡 Key Takeaways

1. **Index = book’s index page** — sorted pointers to actual data
1. **Faster reads** (100x or more), but **slower writes** (tradeoff)
1. **B-Tree** is the most common index structure
1. Index columns you **search/sort/join on often**
1. Don’t over-index — too many indexes hurt write performance

## 🔗 Resources

- [How DB Indexes Work — Medium](https://medium.com/databases-in-simple-words/how-database-indexes-work-in-simple-words-f22558869c03)
- [DB Indexing — System Design School](https://systemdesignschool.io/blog/database-indexing)
- [DB Indexing — EnjoyAlgorithms](https://www.enjoyalgorithms.com/blog/database-indexing-in-system-design/)
- [DB Indexing for Interviews — Hello Interview](https://www.hellointerview.com/learn/system-design/core-concepts/db-indexing)

## ➡️ What’s Next?

**Day 13: Database Replication** — Your safety net when servers die. We’ll learn how Primary-Replica and Multi-Master replication keep your data alive and your app running 24/7.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)