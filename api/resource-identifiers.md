# Resource Identifiers in Web APIs

This document explains the key concepts used in identifying and addressing resources in web-based systems, especially APIs.

---

## 🧩 What Are Resources?

In the context of RESTful APIs, **resources** are the entities or topics we want to manipulate. Each resource is identified by a noun, such as:

- `user`
- `printer`
- `invoice`

Example: in `api/user`, **`user`** is the resource name.

> Always name your resources using nouns, not verbs.

---

## 🌐 What Is a URI?

**URI** stands for **Uniform Resource Identifier**.

It is a string of characters that uniquely identifies a resource in your application.

**Example:** `www.api.com/user` is a URI — it points to a user resource.

---

## 📍 What Is a URL?

**URL** stands for **Uniform Resource Locator**.

It is a type of URI that also includes the protocol, defining the complete address to locate a resource.

**Example:** `https://www.mywebsite.com/user` is a URL.

> A URL is a URI, but not all URIs are URLs.

---

## 🧾 What Is a URN?

**URN** stands for **Uniform Resource Name**.

It is used to uniquely and persistently identify a resource, independent of its location.

### 📘 Syntax of a URN (RFC 2141):
```
URN ::= "urn:" <NID> ":" <NSS>
```

- `<NID>` = Namespace Identifier
- `<NSS>` = Namespace Specific String

### 🧪 Examples:

- `urn:isbn:0451450523` → Identifies the book *The Last Unicorn* by its ISBN.
- `urn:lex:br:federal:lei:2008-06-19;11705` → Identifies Brazil's "Lei Seca" (Federal Law 11.705/2008).

### 🔄 URN Resolvers:

A **URN resolver** translates a URN into one or more URLs.

**Example resolver:** [http://www.lexml.gov.br/urn](http://www.lexml.gov.br/urn)

Resolvers can be:

- **Local**: Resolved internally by a specific system.
- **Centralized**: Resolved by a public or government resolver.
- **Federated**: Local resolver delegates to a central resolver if it cannot resolve a URN.

---

## 🌍 What Is an IRI?

**IRI** stands for **Internationalized Resource Identifier**.

It is a generalization of URI that allows non-ASCII characters (like ç, ñ, ü, 漢字, etc.).

**Example:** `https://exemplo.com/ação`

> IRIs are important for supporting globalized content and languages beyond basic ASCII.

---

## Summary Table

| Term | Stands For | Purpose | Example |
|------|-------------|---------|---------|
| URI | Uniform Resource Identifier | Identifies a resource | `/user/123` |
| URL | Uniform Resource Locator | Full path to access the resource | `https://api.com/user/123` |
| URN | Uniform Resource Name | Unique and persistent naming | `urn:isbn:0451450523` |
| IRI | Internationalized Resource Identifier | URI supporting global characters | `https://exemplo.com/ação` |