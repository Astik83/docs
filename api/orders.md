
# 📦 Order Routes — `/api/orders`

This document covers all API endpoints related to **order creation**, **user order history**, **admin management**, and **granular item-level status/cancellation**.

---

## 👤 User Routes *(Requires Login)*

| Method | Endpoint                                              | Description                                 |
|--------|-------------------------------------------------------|---------------------------------------------|
| POST   | `/api/orders`                                         | Create a new order from user's cart         |
| GET    | `/api/orders/mine`                                    | Get all orders placed by the logged-in user |
| GET    | `/api/orders/:id`                                     | Get details of a specific order             |
| PUT    | `/api/orders/:id/cancel`                              | Cancel the **entire** order                 |
| PUT    | `/api/orders/:orderId/items/:productId/cancel`        | Cancel a **specific item** in the order     |

---

## 🛡️ Admin Routes *(Requires Admin Role)*

| Method | Endpoint                                              | Description                                 |
|--------|-------------------------------------------------------|---------------------------------------------|
| GET    | `/api/orders`                                         | Get all orders across all users             |
| PUT    | `/api/orders/:id/status`                              | ❌ Deprecated: update whole order status     |
| PUT    | `/api/orders/:orderId/items/:productId/status`        | Update status of a **specific item**        |
| PUT    | `/api/orders/:orderId/items/:productId/cancel`        | Cancel a **specific item** in any order     |

---

## 📤 Create Order Example

```http
POST /api/orders
Authorization: Bearer <token>
Content-Type: application/json

{
  "shippingAddress": {
    "line1": "123 Street",
    "city": "Mumbai",
    "postalCode": "400001",
    "country": "India"
  }
}
````

**Success Response:**

```json
{
  "_id": "64fe89c2...",
  "user": "64fa9d...",
  "shippingAddress": { ... },
  "items": [
    {
      "productId": "64fabc...",
      "name": "USB Hub",
      "quantity": 2,
      "deliveryDays": 3,
      "shippingFee": 99,
      "priceCents": 2999,
      "status": "pending"
    }
  ],
  "itemsTotal": 5998,
  "shippingTotal": 99,
  "tax": 609,
  "orderTotal": 6706,
  "status": "pending",
  "createdAt": "2025-07-06T...",
  "updatedAt": "2025-07-06T..."
}
```

---

## 🗃️ Get All User Orders

```http
GET /api/orders/mine
Authorization: Bearer <token>
```

```json
[
  {
    "_id": "64fe89c2...",
    "items": [
      { "productId": "...", "status": "pending", ... }
    ],
    "status": "pending"
  }
]
```

---

## 🛑 Cancel Entire Order

```http
PUT /api/orders/64fe89c2/cancel
```

✅ Will set **all items** and `order.status = cancelled`

```json
{
  "message": "Order cancelled successfully",
  "order": {
    "_id": "...",
    "status": "cancelled",
    "items": [ { ..., "status": "cancelled" } ]
  }
}
```

❌ Fails if already shipped/delivered.

---

## ❌ Cancel a Specific Product in Order

```http
PUT /api/orders/64fe89c2/items/64abc33/cancel
```

✅ Cancels only the item (if not yet shipped):

```json
{
  "message": "Item cancelled successfully",
  "order": {
    "_id": "...",
    "items": [
      { "productId": "...", "status": "cancelled" },
      ...
    ],
    "status": "pending"
  }
}
```

---

## ⚙️ Admin: Update Item Status

```http
PUT /api/orders/64fe89c2/items/64abc33/status
Content-Type: application/json

{
  "status": "shipped"
}
```

✅ Success Response:

```json
{
  "message": "Item status updated successfully",
  "order": {
    "_id": "...",
    "status": "shipped",
    "items": [
      { "productId": "...", "status": "shipped" },
      ...
    ]
  }
}
```

❌ Will error on:

* Invalid status (only: `pending`, `processing`, `shipped`, `delivered`, `cancelled`)
* Already delivered or cancelled items

---


## 📘 Notes

* ✅ Each item in an order has its own status (`pending`, `processing`, `shipped`, etc.).
* ⚠️ If all items are cancelled → `order.status = cancelled`
* 🔄 If all are delivered → `order.status = delivered`
* 🔼 Otherwise → highest active item status becomes the order’s status
* 🧠 You should use **item-level logic** for order tracking and fulfillment

---
> 👤 Maintained by **Astik Shah**
🔗 **Back to API Index** → [api-routes.md](./api-routes.md)

```



