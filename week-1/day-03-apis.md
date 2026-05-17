# Day 3: What is an API?

> 🗓️ Day 3 of 30 — 30-Day System Design Challenge
> 📱 Follow along: [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292) | [YouTube](https://youtube.com/@santhosh.kommula) | [Instagram](https://instagram.com/santhoshkommula.dev)

-----

## 🤔 What is an API?

**API** stands for **Application Programming Interface**.

It’s a set of rules that allows two software applications to communicate with each other. Think of it as a **messenger** or **bridge** between systems.

## 🍽️ The Waiter Analogy (Revisited)

In Day 2, we talked about the restaurant analogy. Now let’s zoom in on the **waiter**:

|Role       |Restaurant                   |In Tech                  |
|-----------|-----------------------------|-------------------------|
|**You**    |The customer                 |Client (your app/browser)|
|**Waiter** |Takes your order, brings food|**The API**              |
|**Kitchen**|Prepares the food            |Server + Database        |

**Why can’t you just go into the kitchen yourself?**

1. You don’t have access (security)
1. The waiter knows the menu (API documentation)
1. The waiter speaks both your language and the kitchen’s (data translation)

> **The API is the ONLY way the client can communicate with the server.** Just like the waiter is the only way you can get food from the kitchen.

## 🔤 Breaking Down the Name

|Word           |Meaning                                    |
|---------------|-------------------------------------------|
|**Application**|Any software — Instagram, Google, your app |
|**Programming**|Code that makes it work                    |
|**Interface**  |The point of connection between two systems|

**Simple definition:** An API is a set of rules that lets two applications talk to each other.

## ⚙️ How Does an API Work?

Let’s walk through a real example — searching for weather:

```
Step 1: You open a weather app
         → You're the CLIENT
              ↓
Step 2: App sends a REQUEST via API
         → "Give me weather for Mumbai"
              ↓
Step 3: API delivers request to server
         → Translates & routes your request
              ↓
Step 4: Server processes the request
         → Fetches weather data from database
              ↓
Step 5: Server sends RESPONSE via API
         → {"temp": "32°C", "condition": "sunny"}
              ↓
Step 6: App displays the weather to you
         → You see: 32°C and Sunny! ☀️
```

## 🔧 HTTP Methods (API Verbs)

APIs use **HTTP methods** to tell the server what action to perform. There are 4 main methods:

|Method    |Action              |Example             |Analogy           |
|----------|--------------------|--------------------|------------------|
|**GET**   |Read / Fetch data   |“Show me all users” |Reading a book    |
|**POST**  |Create new data     |“Add a new user”    |Writing a new page|
|**PUT**   |Update existing data|“Change user’s name”|Editing a page    |
|**DELETE**|Remove data         |“Delete this user”  |Tearing a page out|

Together, these map to **CRUD operations**:

- **C**reate → POST
- **R**ead → GET
- **U**pdate → PUT
- **D**elete → DELETE

### Example API Calls:

```
GET    /api/users          → Get all users
GET    /api/users/123      → Get user with ID 123
POST   /api/users          → Create a new user
PUT    /api/users/123      → Update user 123
DELETE /api/users/123      → Delete user 123
```

## 📦 What Does an API Return? (JSON)

APIs typically return data in **JSON** (JavaScript Object Notation) format:

**Request:**

```
GET /api/users/123
"Hey server, give me info about user 123"
```

**Response:**

```json
{
  "id": 123,
  "name": "Santhosh",
  "role": "Full Stack Developer",
  "followers": 1500,
  "status": "active"
}
```

### What is JSON?

|Feature    |Detail                    |
|-----------|--------------------------|
|Full name  |JavaScript Object Notation|
|Format     |Key-value pairs           |
|Readable by|Both humans and machines  |
|Used by    |Almost every modern API   |
|Alternative|XML (older, more verbose) |

## 🌍 Real-World API Examples

|App/Service            |What Happens                         |API Call                     |
|-----------------------|-------------------------------------|-----------------------------|
|**Weather App**        |Fetches forecast for your city       |`GET /weather?city=Mumbai`   |
|**Login with Google**  |Verifies your Google account         |`POST /auth/google`          |
|**Online Payment**     |Charges your card via Stripe/Razorpay|`POST /payments/charge`      |
|**Google Maps in Uber**|Gets directions from A to B          |`GET /directions?from=A&to=B`|
|**Social Media Share** |Posts a tweet via Twitter API        |`POST /tweets/create`        |

## 📋 API vs API Endpoint vs API Documentation

|Term        |What It Is                                                     |
|------------|---------------------------------------------------------------|
|**API**     |The entire system for communication                            |
|**Endpoint**|A specific URL where you send requests (e.g., `/api/users`)    |
|**API Docs**|The “menu” — tells you what endpoints exist and how to use them|
|**API Key** |Your “ID card” — proves you’re authorized to use the API       |

## 🔒 API Authentication

Not all APIs are public. Many require authentication:

|Method          |How It Works                                   |
|----------------|-----------------------------------------------|
|**API Key**     |A unique key you include in requests           |
|**Bearer Token**|A token (like a password) in the request header|
|**OAuth 2.0**   |Login via Google/GitHub — the gold standard    |
|**Basic Auth**  |Username + password (simple but less secure)   |

## 💡 Key Takeaways

1. **API = the waiter** between client and server
1. **GET, POST, PUT, DELETE** = the 4 main actions (CRUD)
1. APIs return data in **JSON format**
1. Every app you use is **powered by APIs**
1. **API documentation** is the menu — always read it first

## 🔗 Resources

- [REST API Introduction - GeeksforGeeks](https://www.geeksforgeeks.org/node-js/rest-api-introduction/)
- [What is REST? - freeCodeCamp](https://www.freecodecamp.org/news/what-is-rest-rest-api-definition-for-beginners/)
- [What is a RESTful API? - AWS](https://aws.amazon.com/what-is/restful-api/)
- [REST API Examples - Postman](https://blog.postman.com/rest-api-examples/)
- Practice with free APIs: [JSONPlaceholder](https://jsonplaceholder.typicode.com/), [Dog API](https://dog.ceo/dog-api/)

## ➡️ What’s Next?

**Day 4: SQL vs NoSQL Databases** — Where does all this data actually live? We’ll compare structured (SQL) vs flexible (NoSQL) databases and learn when to use which.

-----

⭐ Star this repo if you’re learning along!

📬 Connect with me:

- [LinkedIn](https://linkedin.com/in/swamy-santhosh-866407292)
- [YouTube](https://youtube.com/@santhosh.kommula)
- [Instagram](https://instagram.com/santhoshkommula.dev)
