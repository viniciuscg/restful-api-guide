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