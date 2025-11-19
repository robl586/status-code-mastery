<h1 align="center">🔁 208 Already Reported</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-208-green?style=for-the-badge&logo=http" alt="208 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=repeat" alt="Success Type Badge" />
</p>

---

## 📖 Definition

The **208 Already Reported** status code indicates that members of a WebDAV binding  
have **already been enumerated** in a previous response,  
and **will not be included again** in the current reply.

This is used to avoid **duplicate entries**, especially when resources contain multiple bindings  
or appear in different parts of a tree structure.

> 💬 In simple words:  
> “This item was already listed earlier — no need to repeat it.”

---

## 🧩 Why 208 Exists

In WebDAV, a single resource may be accessible via multiple paths (multiple “bindings”).  
When running a PROPFIND or multi-status request, the same resource could appear more than once.

To prevent duplication, the server responds:
**208 Already Reported**  
for every resource that has already been provided earlier in the multi-status document.

---

## 💻 Example — WebDAV Multi-Status Tree

**Client Request:**

```http
PROPFIND /webdav/root HTTP/1.1
Depth: infinite
```

**Server Response (simplified):**

```http
HTTP/1.1 207 Multi-Status
Content-Type: application/xml
```

```xml
<multistatus xmlns="DAV:">
  <response>
    <href>/webdav/root/fileA.txt</href>
    <status>HTTP/1.1 200 OK</status>
  </response>

  <response>
    <href>/webdav/root/duplicate/fileA.txt</href>
    <status>HTTP/1.1 208 Already Reported</status>
  </response>
</multistatus>
```

**🎯 Meaning:**
`fileA.txt` already appeared in the first response,
so it will not be fully described again.

---

## 🧠 Real-Life Analogy

Imagine you're taking attendance in a classroom.
You call out a student's name, and they say “present.”
Later you accidentally call their name again — they reply:

> You already marked me earlier!”

That's **208 Already Reported** — avoid repeating the same entry.

---

## 🚀 Common Use Cases

| Scenario                                  | Why 208?                                   |
| ----------------------------------------- | ------------------------------------------ |
| Directory trees with duplicate bindings   | Avoid listing the same file multiple times |
| WebDAV PROPFIND operations                | Large tree scans                           |
| Version-controlled or linked file systems | File appears in multiple places            |
| Cloud storage sync tools                  | Prevent repeated metadata                  |

---

## ⚙️ Developer Notes

- Appears only in the **response body** of a **207 Multi-Status** response.

- You will never see 208 as a standalone top-level HTTP status.

- Helps reduce response size when resources appear multiple times.

- Rare outside WebDAV and complex file systems.

---

## 🧪 Example of Repeated Resource

```xml
<response>
  <href>/folderA/report.docx</href>
  <status>HTTP/1.1 200 OK</status>
</response>

<response>
  <href>/folderB/linked/report.docx</href>
  <status>HTTP/1.1 208 Already Reported</status>
</response>
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

- MDN Docs — 208 Already Reported

- RFC 5842 — WebDAV Bindings Extension
