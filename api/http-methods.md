
# HTTP Methods

Following REST constraints and HTTP evolution, originally only three methods were present: `GET`, `POST`, and `HEAD`. Later, with HTTP/1.1, more methods were introduced such as `OPTIONS`, `PUT`, `DELETE`, `TRACE`, and `CONNECT`. The `PATCH` method was recognized as a valid HTTP method by an RFC afterward.

## 1. GET
**Purpose**: Retrieve data from the server (read-only).  
**Idempotent**: Yes  
**Safe**: Yes  

**Example**:  
```bash
curl -X GET https://jsonplaceholder.typicode.com/posts/1
```

## 2. POST
**Purpose**: Send data to the server to create a new resource.  
**Idempotent**: No  
**Safe**: No  

**Example**:  
```bash
curl -X POST https://jsonplaceholder.typicode.com/posts -H "Content-Type: application/json" -d '{"title": "foo", "body": "bar", "userId": 1}'
```

## 3. HEAD
**Purpose**: Similar to GET, but only retrieves the headers.  
**Idempotent**: Yes  
**Safe**: Yes  

**Example**:  
```bash
curl -I https://jsonplaceholder.typicode.com/posts/1
```

## 4. PUT
**Purpose**: Replace an existing resource or create it if it doesn’t exist.  
**Idempotent**: Yes  
**Safe**: No  

**Example**:  
```bash
curl -X PUT https://jsonplaceholder.typicode.com/posts/1 -H "Content-Type: application/json" -d '{"id": 1, "title": "updated", "body": "new body", "userId": 1}'
```

## 5. DELETE
**Purpose**: Remove a resource from the server.  
**Idempotent**: Yes  
**Safe**: No  

**Example**:  
```bash
curl -X DELETE https://jsonplaceholder.typicode.com/posts/1
```

## 6. OPTIONS
**Purpose**: Returns the HTTP methods supported by the server for a specific URL.  
**Idempotent**: Yes  
**Safe**: Yes  

**Example**:  
```bash
curl -X OPTIONS https://jsonplaceholder.typicode.com/posts/1 -i
```

## 7. TRACE
**Purpose**: Echoes the received request (used for diagnostics).  
**Idempotent**: Yes  
**Safe**: Yes  

**Example**:  
```bash
curl -X TRACE https://example.com
```

## 8. CONNECT
**Purpose**: Used to establish a tunnel (usually for HTTPS over HTTP proxies).  
**Idempotent**: No  
**Safe**: No  

_Not commonly used in REST APIs._

## 9. PATCH
**Purpose**: Applies partial modifications to a resource.  
**Idempotent**: No (usually)  
**Safe**: No  

**Example**:  
```bash
curl -X PATCH https://jsonplaceholder.typicode.com/posts/1 -H "Content-Type: application/json" -d '{"title": "patched"}'
```

---

## 🔐 Safe Methods

**Definition:**  
A method is considered **safe** if it is **read-only** — meaning it does **not modify resources on the server**.

### ✅ Safe Methods
| Method | Description                                |
|--------|--------------------------------------------|
| `GET`  | Retrieves data. Does not change state.     |
| `HEAD` | Same as GET but returns only headers.      |
| `OPTIONS` | Describes communication options.        |

These methods are safe because they **shouldn’t have side effects**. Even though a server *could* do something on a GET request (e.g., track usage), the HTTP standard assumes they won’t.

---

## 🔁 Idempotent Methods

**Definition:**  
A method is **idempotent** if making the same request **once or multiple times** results in **the same effect** on the server.

### ✅ Idempotent Methods
| Method     | Why it's idempotent                                                |
|------------|---------------------------------------------------------------------|
| `GET`      | Multiple reads won’t change anything.                              |
| `HEAD`     | Returns headers; no state changes.                                 |
| `PUT`      | Uploading the same data repeatedly results in the same resource.   |
| `DELETE`   | Deleting the same resource multiple times still results in "gone". |
| `OPTIONS`  | Only returns metadata; no state change.                            |

> Note: Even though `DELETE` can trigger logs or other server-side processes, **its core effect (removing a resource)** remains the same no matter how many times it's called — which qualifies it as idempotent.

---

## ❌ Non-idempotent and Non-safe

| Method   | Why it's **not** safe or idempotent               |
|----------|---------------------------------------------------|
| `POST`   | Submits data that usually **creates** a resource or triggers processing. Multiple calls may create multiple entries. |
| `PATCH`  | Partially updates a resource. Multiple identical calls might result in different states depending on how the server applies the changes. |
| `CONNECT`, `TRACE` | Used for tunneling or diagnostics. They may change underlying state or are not repeatable safely. |

---

## 🧠 Summary Table

| Method   | Safe | Idempotent |
|----------|------|------------|
| GET      | ✅   | ✅         |
| HEAD     | ✅   | ✅         |
| OPTIONS  | ✅   | ✅         |
| PUT      | ❌   | ✅         |
| DELETE   | ❌   | ✅         |
| POST     | ❌   | ❌         |
| PATCH    | ❌   | ❌         |
| TRACE    | ❌   | ❌         |
| CONNECT  | ❌   | ❌         |

---

**References:**
- [RFC 7231 Section 4.2.1 - Safe Methods](https://datatracker.ietf.org/doc/html/rfc7231#section-4.2.1)
- [RFC 7231 Section 4.2.2 - Idempotent Methods](https://datatracker.ietf.org/doc/html/rfc7231#section-4.2.2)