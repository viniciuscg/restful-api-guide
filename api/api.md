# What is an API?

## 📘 Definition
**API** stands for **Application Programming Interface**. It's a set of rules and protocols that allow different software systems to communicate with each other.

Think of it as a **contract** between two applications: one side provides data or functionality, and the other consumes it.

## 🔗 Real-World Analogy
Imagine an API as a **restaurant menu**:
- The **menu** lists what you can order (endpoints).
- You tell the **waiter** (API request) what you want.
- The **kitchen** (server) prepares it.
- The waiter brings your **food** (API response).

You don't need to know how the kitchen works—you just follow the menu!

## 🌐 Web APIs
A **Web API** allows applications to talk over the internet using HTTP. When people refer to APIs in modern web development, they often mean **RESTful APIs**.

## 🚀 RESTful APIs
**REST (Representational State Transfer)** is an architectural style that defines how to structure web APIs using standard HTTP methods:

| HTTP Method | Description          | Example       |
|-------------|----------------------|---------------|
| `GET`       | Read data            | `/users`      |
| `POST`      | Create new data      | `/users`      |
| `PUT`       | Update existing data | `/users/123`  |
| `DELETE`    | Remove data          | `/users/123`  |

REST APIs usually respond with **JSON** data.

## 🔧 How It's Used
Applications use APIs to:
- Fetch or send data to a server
- Authenticate users
- Integrate with third-party services (e.g., payment, maps, weather)
- Communicate between microservices

## 🛠️ Example
Here’s what a simple API request looks like:
```http
GET /users/1 HTTP/1.1
Host: api.example.com
```

Response (JSON):
```json
{
  "id": 1,
  "name": "Vinicius",
  "email": "vinicius@example.com"
}
```

## 📄 Why APIs Matter
- 🔁 **Reusability**: Code is easier to maintain and reuse
- 🤝 **Interoperability**: Systems can work together
- ⚙️ **Automation**: Enables scripts, bots, and apps to act without manual input
- 🌍 **Connectivity**: Powers the modern web and mobile apps

## ✅ Summary
- An API defines how two systems communicate.
- REST APIs are the most common type used on the web.
- APIs use HTTP verbs and JSON to exchange data.
- They're essential for modern software development.