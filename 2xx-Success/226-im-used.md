<h1 align="center">🧮 226 IM Used</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-226-green?style=for-the-badge&logo=http" alt="226 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=code" alt="Success Type Badge" />
</p>

---

## 📖 Definition

The **226 IM Used** status code means that the server has successfully completed a  
`GET` request, and the response **includes one or more instance-manipulations**  
applied to the current instance of the resource.

This is part of the **HTTP Delta Encoding** extension (RFC 3229).

> 💬 In simple words:  
> “Here is the resource you asked for — but optimized, transformed, or partially modified.”

---

## 🧩 What Are Instance-Manipulations (IM)?

Instance-manipulations are **transformations** applied to a resource *before* returning it.  
Examples include:

- Delta encoding (only differences sent)  
- Patch-like transformations  
- Optimized/partial data  
- Bandwidth-saving techniques  

They help reduce:

- Response size  
- Bandwidth usage  
- Redundant data transfer  

---

## 💻 Example — Delta Response

A client wants to update its cached version of a document.  
It sends:

**Client Request:**

```http
GET /doc HTTP/1.1
A-IM: vcdiff
```

**Server Response:**

```http
HTTP/1.1 226 IM Used
IM: vcdiff
Content-Type: application/vcdiff
```

```text
(delta changes here...)
```

🎯 Meaning:
Instead of sending the full document, the server sends only the **changes**.

---

## 🧠 Real-Life Analogy

Imagine you have a notebook with 100 pages.
The teacher updates only 3 pages, and instead of giving you the whole notebook again,
they hand you only the updated pages.

That’s **226 IM Used** — return only what changed.

---

## 🚀 Common Use Cases

| Scenario                  | Benefit                     |
| ------------------------- | --------------------------- |
| Software updates          | Only send changed bytes     |
| Document sync             | Avoid full file transfer    |
| Version control over HTTP | Patch-level updates         |
| Cache revalidation        | Lighter incremental updates |

---

## ⚙️ Developer Notes

- Rarely seen in mainstream REST APIs.

- Mostly used in:

  - CDN optimizations

  - Cloud sync systems

  - Delta-update systems

  - Bandwidth-sensitive applications

- Requires client support for IM via the `A-IM` header.

### Key Headers

| Header | Purpose                                        |
| ------ | ---------------------------------------------- |
| `A-IM` | What instance manipulations the client accepts |
| `IM`   | What manipulations were applied by the server  |

---

## 🧪 Example — cURL Request Supporting Delta Encoding

```bash
curl -H "A-IM: vcdiff" <https://example.com/data>
```

**Response:**

```http
HTTP/1.1 226 IM Used
IM: vcdiff
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

- MDN Docs — 226 IM Used

- RFC 3229 — Delta Encoding in HTTP
