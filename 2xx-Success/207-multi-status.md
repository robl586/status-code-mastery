<h1 align="center">🧩 207 Multi-Status</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-207-green?style=for-the-badge&logo=http" alt="207 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=list-tree" alt="Success Badge" />
</p>

---

## 📖 Definition

The **207 Multi-Status** response indicates that the server is returning **multiple status codes** for multiple independent operations — all inside a single response body.

Used **primarily in WebDAV**, where a request may involve:

- Multiple files  
- Multiple actions  
- A batch of operations  

Each part of the response has its **own status code**, typically returned in **XML format**.

> 💬 **In simple words:**  
> “I processed multiple items — here’s the status for each one.”

---

## 🧩 Why 207 Multi-Status Exists

WebDAV operations often involve:

- Copying multiple files  
- Deleting multiple files  
- Updating folder structures  
- Checking permissions  

Since each file may succeed or fail independently, a **single HTTP status code** (like 200 or 400) is not enough.

So HTTP introduced **207 Multi-Status** to provide a **detailed multi-result report**.

---

## 💻 Example — Multi-File Operation (WebDAV)

**Client Request:**

```http
PROPFIND /webdav/files/ HTTP/1.1
Depth: 1
```

**Server Response (simplified):**

```http
HTTP/1.1 207 Multi-Status
Content-Type: application/xml
```

```xml
<multistatus xmlns="DAV:">
  <response>
    <href>/webdav/files/file1.txt</href>
    <status>HTTP/1.1 200 OK</status>
  </response>
  <response>
    <href>/webdav/files/file2.txt</href>
    <status>HTTP/1.1 404 Not Found</status>
  </response>
  <response>
    <href>/webdav/files/file3.txt</href>
    <status>HTTP/1.1 403 Forbidden</status>
  </response>
</multistatus>
```

**🎯 Meaning:**

- `file1.txt` → Found

- `file2.txt` → Missing

- `file3.txt` → Permission denied

All inside one HTTP response.

---

## 🧠 Real-Life Analogy

Imagine your teacher checking multiple assignments and sending you a report:

| Assignment | Status                   |
| ---------- | ------------------------ |
| Math HW    | ✔️ Done                  |
| Science HW | ❌ Missing                |
| English HW | 🔒 Not allowed to submit |

That entire report = **207 Multi-Status**.

---

## 🚀 Common Use Cases

| Scenario                | Reason                                 |
| ----------------------- | -------------------------------------- |
| Bulk file operations    | Each file may have a different outcome |
| Folder sync             | Cloud storage sync checks              |
| WebDAV batch actions    | COPY, MOVE, PROPFIND                   |
| Multi-permission checks | Each resource returns its own status   |

---

## ⚙️ Developer Notes

- Response is usually **XML** (because of WebDAV).

- Can return **200**, **404**, **403**, **409**, etc., inside the same body.

- Not commonly seen in normal REST APIs.

- Powerful for **file servers**, **cloud storage**, and **enterprise sync tools**.

---

## 🧪 Example: Multi-Delete Request

```http
DELETE /webdav/bulk-delete HTTP/1.1
```

**Response:**

```http
HTTP/1.1 207 Multi-Status
```

**Body:**

```xml
<multistatus>
  <response>
    <href>/docs/a.pdf</href>
    <status>HTTP/1.1 204 No Content</status>
  </response>
  <response>
    <href>/docs/b.pdf</href>
    <status>HTTP/1.1 404 Not Found</status>
  </response>
</multistatus>
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

- MDN Docs — 207 Multi-Status

- RFC 4918 — WebDAV Extensions
