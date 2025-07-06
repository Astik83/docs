
# 🤖 Chatbot Route — `/api/chat`

This document describes the API endpoint for interacting with the AI-powered chatbot built into the ShopSphere platform. The chatbot helps users with product queries, orders, platform usage, and general assistance.

---

## 🌐 Public Route *(Rate Limited)*

| Method | Endpoint    | Description                      |
|--------|-------------|----------------------------------|
| POST   | `/api/chat` | Submit a user query to chatbot   |

### 📥 Request Body

```json
{
  "message": "Do you have running shoes under ₹2000?"
}
````

### 📤 Response Body

```json
{
  "reply": "Yes! We have several running shoes under ₹2000. Would you like me to show the top-rated ones?"
}
```

---

## 🛡️ Security & Rate Limits

* 🔐 **Protected via:** `helmet`, `cors`, and input sanitization
* ⏱️ **Rate Limit:** 100 requests per 15 minutes per IP
* 🧼 Basic filtering for offensive/inappropriate messages
* 🧠 Skips localhost rate limit in development mode

---

## 🧠 Chatbot Behavior

* ✅ Uses **local QA JSON (RAG-style)** for domain-specific responses
* 🤖 Falls back to **external LLM (via API)** if local match fails
* 🧠 Stateless endpoint — no chat history is stored

---

## 🧩 Use Cases

* Product recommendations
* Delivery & return policy help
* General platform FAQs
* Voice assistant extensions (future-ready)

---
> 👤 Maintained by **Astik Shah**
🧭 **Back to API Index** → [api-routes.md](./api-routes.md)

````


