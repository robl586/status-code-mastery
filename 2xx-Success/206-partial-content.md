<h1 align="center">📦 206 Partial Content</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-206-green?style=for-the-badge&logo=http" alt="206 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=download" alt="Success Type Badge" />
</p>

---

## 📖 Definition

The **206 Partial Content** status code means the server is **successfully returning only a portion** of the resource that the client requested.

This happens when the client sends a `Range` header asking for **specific parts of a file**, such as:

- Partial file downloads  
- Resume downloads  
- Streaming video/audio  
- Chunked media delivery  

> 💬 **In simple terms:**  
> “Here is the part of the file you asked for — not the whole thing.”

---

## 🧩 Why 206 Exists

Downloading entire files can be:

- Slow  
- Expensive  
- Interrupted  
- Unnecessary for streaming  

So HTTP allows clients to request just a piece of a file —  
and servers respond with **206 Partial Content**.

---

## 💻 Example 1 — Range Request for a File

**Client Request:**

```http
GET /videos/movie.mp4 HTTP/1.1
Range: bytes=0-999
```

**Server Response:**

```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 0-999/2000000
Content-Type: video/mp4
```

🎯 Meaning: Client asked for the first 1000 bytes — server delivered exactly that.

---

## 💻 Example 2 — Resuming a Download

If your internet disconnects mid-download, your browser sends:

```http
Range: bytes=100000-
```

The server responds:

```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 100000-1999999/2000000
```

The browser continues downloading from the point it left off.

---

🧠 Real-Life Analogy

Imagine reading a PDF textbook, and you say:

> “Show me pages 50–60 only.”

The librarian gives you only those pages, not the whole book.

That’s **206 Partial Content 📚✨**

---

## 🚀 Common Use Cases

| Scenario            | Why 206 is used            |
| ------------------- | -------------------------- |
| Video streaming     | Load only needed chunks    |
| Audio streaming     | Play while buffering       |
| Resume downloads    | Pick up where you left off |
| Large file transfer | Conserve bandwidth         |
| Cloud storage       | Access partial datasets    |

---

⚙️ Developer Notes

- 206 requires a Range header from the client.

- The server must include:

  - `Content-Range`

  - `Content-Length`

- If the server does not support Range, it may return:

  - 200 OK (full content)

  - 416 Range Not Satisfiable (invalid range)

- Popular file servers (S3, Nginx, Apache) heavily rely on 206.

---

## 🧪 Example: Using cURL

```bash
curl -i https://example.com/file.zip -H "Range: bytes=0-500"
```

Output:

```http
HTTP/1.1 206 Partial Content
Content-Range: bytes 0-500/800000
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

- MDN Docs – 206 Partial Content

- RFC 9110 – Range & Partial Requests
