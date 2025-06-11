# 📡 Using `curl` for HTTP Requests
`curl` is a command-line tool used to transfer data to or from a server using URL syntax. It's widely used to test and interact with APIs directly from the terminal.
---
## 🧠 What is `curl`?
`curl` stands for **Client URL**. It supports many protocols such as `HTTP`, `HTTPS`, `FTP`, and more. It's extremely useful when you're:
- Testing endpoints during API development
- Sending HTTP requests
- Debugging request/response data
- Automating interactions with web services

Official documentation: [https://curl.se/docs/](https://curl.se/docs/)
---
## 🛠️ Basic Syntax
```bash
curl [options] [URL]
```
You provide the URL and use flags (options) to configure things like HTTP method, headers, and body data.
---
## 🔁 Common `curl` Flags and Shortcuts
| Flag          | Description                                                      |
|---------------|------------------------------------------------------------------|
| `-X`          | Specifies the HTTP method (`GET`, `POST`, `PUT`, `DELETE`, etc.) |
| `-H`          | Sets a request header (e.g., `Content-Type`)                     |
| `-d`          | Sends data in the request body (used with `POST`, `PUT`, etc.)   |
| `-i`          | Includes the response headers in the output                      |
| `-I` or `--head` | Sends a `HEAD` request, only fetching headers                |
---
## 🧪 Example Requests Using JSONPlaceholder
JSONPlaceholder is a free fake API for testing and prototyping.

### 1. 🔍 GET request (default)
```bash
curl https://jsonplaceholder.typicode.com/posts/1
```
### 2. 📬 POST request with JSON body
```bash
curl -X POST https://jsonplaceholder.typicode.com/posts \
  -H "Content-Type: application/json" \
  -d '{"title":"foo","body":"bar","userId":1}'
```
### 3. 🗑 DELETE request
```bash
curl -X DELETE https://jsonplaceholder.typicode.com/posts/1
```
### 4. 📝 PUT request with JSON
```bash
curl -X PUT https://jsonplaceholder.typicode.com/posts/1 \
  -H "Content-Type: application/json" \
  -d '{"id":1,"title":"updated","body":"new content","userId":1}'
```
---
## 🔎 Tips
- Use `-i` to see **both headers and body**:
  ```bash
  curl -i https://jsonplaceholder.typicode.com/posts/1
  ```
- Use `-I` or `--head` to fetch **only headers**:
  ```bash
  curl -I https://jsonplaceholder.typicode.com/posts/1
  ```
---
## ✅ Summary
`curl` is an essential tool in the developer's toolbox when working with APIs. Its simplicity, flexibility, and power make it ideal for:
- Sending requests
- Debugging APIs
- Automating HTTP workflows

> 📚 Refer to the official documentation for more: [https://curl.se/docs/](https://curl.se/docs/)