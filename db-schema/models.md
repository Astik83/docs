# 🧩 Data Models Overview — ShopSphere

This document serves as an index of all core data models used in the ShopSphere backend. Each model is defined using Mongoose and stored in the `/models` directory.

---

## 🗂️ Available Models

| Model Name     | File                           | Description                                  |
|----------------|--------------------------------|----------------------------------------------|
| 👤 User        | [`userMmodel.md`](./userMmodel.md)         | Manages user credentials, roles, and auth    |
| 🛍️ Product     | [`productMmodel.md`](./productMmodel.md)     | Stores all product-related information       |
| 🛒 Cart        | [`cartMmodel.md`](./cartMmodel.md)           | Temporary storage for items before checkout  |
| 📦 Order       | [`orderMmodel.md`](./orderMmodel.md)         | Captures confirmed purchases and status      |
| 💬 ChatLog     | [`chatMmodel.md`](./chatMmodel.md)           | Logs chatbot questions and responses         |
| ❤️ HealthLog   | [`healthMmodel.md`](./healthMmodel.md)       | Tracks API health logs (optional)            |

---

> 🔍 Click on any model name to view its schema structure, validation rules, and relationships.
