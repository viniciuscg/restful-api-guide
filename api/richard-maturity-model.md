# Richardson Maturity Model (RMM)

The Richardson Maturity Model (RMM) is a way to grade your API according to the constraints of REST. It was developed by Leonard Richardson to help evaluate how RESTful a web service is. The model is divided into four levels (0 to 3), each representing a higher degree of RESTful maturity.

---

## Level 0: The Swamp of POX (Plain Old XML)

At this level, the API typically uses a single endpoint with a single HTTP method, often POST. All operations (create, read, update, delete) are done through this endpoint and the request's body determines the action.

### Characteristics
- Single URI for all actions
- Single HTTP method (usually POST)
- Often uses XML or JSON in the body to indicate actions

### Example
```
POST /api
{
  "operation": "getUser",
  "id": "123"
}
```

---

## Level 1: Resources

At this level, the API exposes multiple URIs representing different resources. Each resource is given its own endpoint. However, it might still use only one HTTP method (usually POST) for all operations.

### Characteristics
- Uses distinct URIs for different resources
- Still uses a single HTTP method

### Example
```
POST /users
POST /orders
```

---

## Level 2: HTTP Verbs

This level introduces the use of standard HTTP methods (GET, POST, PUT, DELETE, PATCH) according to their semantic meaning. This enhances clarity and alignment with REST principles.

### Characteristics
- Multiple URIs for different resources
- Use of multiple HTTP methods appropriately

### Example
```
GET /users/123        --> Retrieve user
POST /users           --> Create new user
PUT /users/123        --> Replace user data
PATCH /users/123      --> Update partial user data
DELETE /users/123     --> Delete user
```

---

## Level 3: Hypermedia Controls (HATEOAS)

Hypermedia As The Engine Of Application State (HATEOAS) is introduced. This level ensures that a client can dynamically navigate the API via hyperlinks provided in the responses. This allows a decoupled interaction where the client doesn’t need prior knowledge of the API structure.

### Characteristics
- Hypermedia links in responses
- Enables discoverability and dynamic navigation

### Example Response
```json
{
  "id": "123",
  "name": "John",
  "links": [
    { "rel": "self", "href": "/users/123" },
    { "rel": "orders", "href": "/users/123/orders" }
  ]
}
```

---

## Summary

| Level | Feature                          | Description                                                                 |
|-------|----------------------------------|-----------------------------------------------------------------------------|
| 0     | Single Endpoint + POST           | No REST features, just tunneling through POST                              |
| 1     | Resources                        | Uses URIs to identify resources                                             |
| 2     | HTTP Verbs                       | Proper use of HTTP methods (GET, POST, PUT, DELETE, etc.)                  |
| 3     | HATEOAS                          | Hypermedia links for dynamic discoverability of actions and related data   |

---

## Why Use RMM?

- Helps measure and improve RESTful compliance
- Encourages best practices in API design
- Provides a clear maturity path for teams developing web services

---

## References

- Leonard Richardson’s original presentation
- RESTful Web Services by Leonard Richardson and Sam Ruby