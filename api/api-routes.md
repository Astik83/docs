
# 🔌 API Routes Index — ShopSphere

This document serves as the **Table of Contents** for all backend API routes in the ShopSphere eCommerce platform. Each module is separated into its own markdown file for clarity and scalability.

---

## 📁 API Route Docs Structure

| Section       | Description                                      | Link                      |
|---------------|--------------------------------------------------|---------------------------|
| 👤 Users       | Register, login, profile management, admin users | [`users.md`](./users.md)  |
| 🛍️ Products    | Browse, search, add/edit/delete products         | [`products.md`](./products.md) |
| 🛒 Cart         | Add, update, delete cart items                   | [`cart.md`](./cart.md)    |
| 📦 Orders       | Place, cancel, update orders (user/admin)        | [`orders.md`](./orders.md)|
| 🤖 Chatbot     | AI assistant for user queries (optional module)  | [`chat.md`](./chat.md)    |
| ❤️ Health      | Simple uptime check for monitoring               | [`health.md`](./health.md)|

---

## 🧩 Route Prefix

All API routes are prefixed with:

```

/api

```

For example:
- `POST /api/users/login`
- `GET /api/products`
- `POST /api/cart`

---

## 📌 Recommended Reading Order

For new developers or integrators, follow this sequence for the best understanding:

1. [`users.md`](./users.md)
2. [`products.md`](./products.md)
3. [`cart.md`](./cart.md)
4. [`orders.md`](./orders.md)
5. [`chat.md`](./chat.md) *(optional module)*
6. [`health.md`](./health.md)

---

> ✍️ Maintained by **Astik Shah**  
> For feedback, updates, or issues — please refer to the main [`README.md`](../README.md) or reach out to the maintainer.

```



