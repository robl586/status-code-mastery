<h1 align="center">🏗️ 201 Created</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-201-green?style=for-the-badge&logo=http" alt="201 Created Badge" />
  <img src="https://img.shields.io/badge/Type-Success-brightgreen?style=for-the-badge&logo=check-circle" alt="Success Type Badge" />
</p>

---

## 📖 Definition

The **201 Created** status code indicates that the request has been successfully fulfilled and **a new resource has been created** on the server.

This is the *standard* response for **POST** requests that create new entries in a database.

> 💬 **Meaning:**  
> “Your request worked, and I created something new for you!” 🎉

---

## 🧩 When to Use 201

Use **201 Created** when:

- A **new user** is registered  
- A **new blog post** is created  
- A **new product** is added  
- A **new order** is generated  

The server should ideally include:

- `Location` header → URL of newly created resource  
- A response body (optional but recommended)

---

## 💻 Example 1 — Creating a User

**Request:**

```http
POST /api/users HTTP/1.1
Content-Type: application/json

{
  "name": "Anirudha",
  "email": "anirudha@example.com"
}
```

**Response:**

```http
HTTP/1.1 201 Created
Location: /api/users/42
Content-Type: application/json

{
  "id": 42,
  "name": "Anirudha",
  "email": "anirudha@example.com"
}
```

🎉 Meaning: A new user was successfully created with ID 42.

---

## 💻 Example 2 — Creating a Product

**Request:**

```http
POST /api/products HTTP/1.1
Content-Type: application/json

{
  "name": "Mechanical Keyboard",
  "price": 2999
}
```

**Response:**

```http
HTTP/1.1 201 Created
Location: /api/products/7
```

🎯 Resource created, and the server tells us where to find it.

---

## 🧠 Real-Life Analogy

Imagine going to a tailor and saying:

> “Can you stitch a new shirt for me?” 👕

They say:

> “Done! Here’s your shirt and the receipt!”

That’s 201 Created — a request that results in something new being made.

---

## 🚀 Common Use Cases

| Scenario                  | Example         |
| ------------------------- | --------------- |
| User signup               | `/api/register` |
| Adding a new todo item    | `/api/todos`    |
| Creating a checkout order | `/api/orders`   |
| Uploading a new file      | `/api/upload`   |

---

⚙️ Developer Tips

- Always use 201 for successfully created resources.

- Never return 200 OK for creation — it's incorrect REST design.

- Include the Location header whenever possible:

    ```http
    Location: /api/resource/<new_id>
    ```

- You may include the created object in the response (recommended).

---

## 🧪 cURL Example

```bash
curl -i -X POST <https://example.com/api/posts> \
  -H "Content-Type: application/json" \
  -d '{"title": "My First Post", "content": "Hello!"}'
```

Output:

```http
HTTP/1.1 201 Created
Location: /api/posts/15
```

---

## 🔗 Related Codes

- [200 OK](./200-ok.md) ✅ OK

- [201 Created](./201-created.md) | 🏗️

- [202 Accepted](./202-accepted.md) | ⏳

- [203 Non-Authoritative Information](./203-non-authoritative-information.md) | 🧾

- [204 No Content](./204-no-content.md) | 🚫

- [205 Reset Content](./205-reset-content.md) | 🔄

- [206 Partial Content](./206-partial-content.md) | 📦

- [207 Multi-Status](./207-multi-status.md) | 🧩

- [208 Already Reported](./208-already-reported.md) | 🔁

- [226 IM Used](./226-im-used.md) | 🧮

---

## 📚 References

- MDN Docs – 201 Created

- RFC 9110 – Successful Responses
