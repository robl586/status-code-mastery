<h1 align="center">⏳ 202 Accepted</h1>

<p align="center">
  <img src="https://img.shields.io/badge/Status%20Code-202-yellowgreen?style=for-the-badge&logo=http" alt="202 Accepted Badge" />
  <img src="https://img.shields.io/badge/Type-Success-lightgreen?style=for-the-badge&logo=task" alt="Success Type Badge" />
</p>

---

## 📖 Definition

The **202 Accepted** status code means that the server has **received the request**,  
but **has not yet finished processing it**.

Processing will happen **asynchronously**, and the result may not be immediately available.

> 💬 **In simple terms:**  
> “I got your request and will work on it, but it’s not done yet.” ⚙️

---

## 🧩 When Do We Use 202?

Use **202 Accepted** when:

- The request triggers a **long-running background job**  
- Immediate response is not possible  
- The server will process the action **later**  
- The client should **not wait** for a final response right away  

**Common in:**

- Payment processing  
- Email sending  
- Report generation  
- Video processing / encoding  
- Queue-based systems (RabbitMQ, Kafka, SQS)  

---

## 💻 Example 1 — Processing a Payment

**Request:**

```http
POST /api/payments HTTP/1.1
Content-Type: application/json

{
  "amount": 999,
  "method": "upi"
}
```

**Response:**

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
  "message": "Payment is being processed.",
  "statusCheckUrl": "/api/payments/status/1289"
}
```

🎯 Meaning: Payment is accepted for processing, but not completed yet.

---

## 💻 Example 2 — Generating a Report

**Request:**

```http
POST /api/reports/annual HTTP/1.1
```

**Response:**

```http
HTTP/1.1 202 Accepted
Retry-After: 30
```

⏱️ The report will take time, and the client may check after 30 seconds.

---

## 🧠 Real-Life Analogy

Imagine dropping off your phone for repair 🔧
The technician says:

> “We’ve accepted your device. It will take some time.”

That’s 202 Accepted — you are in the queue but the work isn't done yet.

---

## 🚀 Common Use Cases

| Scenario                    | Example                              |
| --------------------------- | ------------------------------------ |
| Email verification          | “Email sent. Check again later.”     |
| Background video processing | Thumbnail or HD version generation   |
| Asynchronous API jobs       | ML model training, data export, etc. |
| Queue-based actions         | Tasks consumed by worker services    |

---

## ⚙️ Developer Notes

- The server should not send the final result within 202.

- Include a way to check the job status, such as:

  - `statusCheckUrl`

  - Job ID

  - Queue token

- Ideal for microservices and async-based architectures.

- Prevents client timeouts for long operations.

---

## 🧪 Example: Job Status Check Pattern

**202 Response:**

```http
{
  "jobId": "task-5463",
  "check": "/api/jobs/task-5463"
}
```

**Later (client checks):**

```http
GET /api/jobs/task-5463
```

**Server responds:**

```http
HTTP/1.1 200 OK
{
  "status": "completed",
  "result": "Report ready to download"
}
```

---

## 📚 References

- MDN Docs – 202 Accepted

- RFC 9110 – Asynchronous Response Semantics
