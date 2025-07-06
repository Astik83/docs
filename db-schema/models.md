# 🧩 Data Models Overview — ShopSphere

This document serves as an index of all core data models used in the ShopSphere backend. Each model is defined using Mongoose and stored in the `/models` directory.

---

## 🗂️ Available Models

| Model Name     | File                           | Description                                  |
|----------------|--------------------------------|----------------------------------------------|
| 👤 User        | [`userModel.md`](./userModel.md)         | Manages user credentials, roles, and auth    |
| 🛍️ Product     | [`productModel.md`](./productModel.md)     | Stores all product-related information       |
| 🛒 Cart        | [`cartModel.md`](./cartModel.md)           | Temporary storage for items before checkout  |
| 📦 Order       | [`orderModel.md`](./orderModel.md)         | Captures confirmed purchases and status      |
| 💬 ChatLog     | [`chatModel.md`](./chatModel.md)           | Logs chatbot questions and responses         |
| ❤️ HealthLog   | [`healthModel.md`](./healthModel.md)       | Tracks API health logs (optional)            |

---

> 🔍 Click on any model name to view its schema structure, validation rules, and relationships.
