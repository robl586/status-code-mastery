<h1 align="center">🔄 205 Reset Content</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-205-green?style=for-the-badge&logo=http" alt="205 Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=refresh-cw" alt="Success Badge" />
</p>

---

## 📖 Definition

The **205 Reset Content** status code means that the server successfully processed the request,  
and now instructs the **client to reset its form, UI, or input fields** back to their default state.

Unlike **204 No Content**, which simply means “nothing to return,”  
this one means:

> 💬 **“Request successful — now reset your view/form/input.”**  

---

## 🧩 When to Use 205

Use **205 Reset Content** when:

- A form submission should clear all input fields  
- A UI action requires a clean state  
- The client must reset its document view  
- A "refresh" or "reset" operation is triggered  

It’s ideal for **browser-based** interactions.

---

## 💻 Example 1 — Resetting a Form

**Client Request:**

```http
POST /api/contact-form HTTP/1.1
Content-Type: application/json

{
  "name": "Anirudha",
  "message": "I want to know more about your service."
}
```

**Server Response:**

```http
HTTP/1.1 205 Reset Content
```

🎯 Meaning:
The form was submitted successfully. Now the client must reset/clear it.

---

## 💻 Example 2 — UI Reset After Action

**Request:**

A dashboard triggers a “Reset Filters” API call.

```http
POST /api/dashboard/reset-filters
```

**Response:**

```http
HTTP/1.1 205 Reset Content
```

The client should:

- Clear input fields

- Reset dropdowns

- Remove date-range filters

---

## 🧠 Real-Life Analogy

You fill out a feedback form and submit it.
After submission, the form clears itself — ready for another response.

That is **205 Reset Content**.

---

## 🚀 Common Use Cases

| Scenario                | Why 205?                   |
| ----------------------- | -------------------------- |
| Contact form submission | Clear fields after sending |
| Feedback form           | Reset UI automatically     |
| Search filters reset    | Clear selections           |
| Editor or viewer reset  | Restore initial state      |

---

## ⚙️ Developer Notes

- A response body must NOT be included with a 205.

- Browsers receiving a 205 will:

  - Clear form fields

  - Reset UI state

  - Reload interactive elements

- 204 vs 205:

  - 204 No Content → Nothing more to do

  - 205 Reset Content → Do something: reset UI

---

## 🧪 Example Using JavaScript Fetch

```js
fetch("/api/submit", {
  method: "POST",
  body: JSON.stringify({ message: "hello" }),
  headers: { "Content-Type": "application/json" },
}).then((res) => {
  if (res.status === 205) {
    form.reset(); // Reset form UI
  }
});
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

- MDN Docs – 205 Reset Content

- RFC 9110 – HTTP Semantics
