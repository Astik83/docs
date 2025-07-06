
# 🛒 Cart Routes — `/api/cart`

This document outlines all routes related to the shopping cart functionality in the **ShopSphere** platform.  
All routes are **protected** and require the user to be authenticated via JWT (httpOnly cookie or Bearer token).

---

## 🔐 Protected Routes (Requires Login)

| Method | Endpoint                   | Description                                 |
|--------|----------------------------|---------------------------------------------|
| POST   | `/api/cart`                | Add a product to the cart                   |
| GET    | `/api/cart`                | Fetch all items in the user's cart          |
| DELETE | `/api/cart`                | Clear all items from the cart               |
| PUT    | `/api/cart/:productId`     | Update quantity or delivery details         |
| DELETE | `/api/cart/:productId`     | Remove a specific product from the cart     |

> 🛡️ All routes use `protect` middleware. Tokens are validated server-side.

---

## 🧾 Cart Item Structure

Each cart item includes:

| Field              | Type     | Description                                      |
|-------------------|----------|--------------------------------------------------|
| `productId`        | ObjectId | Reference to the product                        |
| `quantity`         | Number   | Number of units                                 |
| `deliveryDays`     | Number   | Delivery time in days (e.g., 3, 7)              |
| `shippingFee`      | Number   | Shipping fee in cents                           |
| `estimatedDelivery`| Date     | Estimated delivery date (auto-calculated)       |

---

## 🧪 Example Requests

### ➕ Add to Cart

```http
POST /api/cart
Content-Type: application/json
Authorization: Bearer <access_token>

{
  "productId": "64b123...",
  "quantity": 2,
  "deliveryDays": 5,
  "shippingFee": 150
}
````

**Success Response:**

```json
{
  "success": true,
  "cart": {
    "_id": "64f87c3...",
    "userId": "64f87aa...",
    "items": [
      {
        "_id": "64f87c4...",
        "productId": "64b123...",
        "quantity": 2,
        "deliveryDays": 5,
        "shippingFee": 150,
        "estimatedDelivery": "2025-07-11T00:00:00.000Z"
      }
    ]
  }
}
```

---

### 🔁 Update Cart Item

```http
PUT /api/cart/64b123...
Content-Type: application/json

{
  "quantity": 3,
  "deliveryDays": 3,
  "shippingFee": 99
}
```

---

### 📦 Get Cart with Expanded Product Info

```http
GET /api/cart?expand=product
```

**Expanded Response:**

```json
{
  "success": true,
  "cart": {
    "_id": "64f87c3...",
    "items": [
      {
        "productId": {
          "_id": "64b123...",
          "name": "Bluetooth Speaker",
          "priceCents": 2599,
          "image": "images/products/speaker.jpg",
          "stock": 23
        },
        "quantity": 1,
        "deliveryDays": 3,
        "shippingFee": 100,
        "estimatedDelivery": "2025-07-09T00:00:00.000Z"
      }
    ]
  }
}
```

---

## ❌ Common Error Responses

### Missing Fields

```json
{
  "success": false,
  "error": "productId, deliveryDays, and shippingFee are required"
}
```

### Product Not Found in Cart

```json
{
  "success": false,
  "error": "Item not found in cart"
}
```

### Invalid Product ID

```json
{
  "success": false,
  "error": "Product not found"
}
```

---

## ⚙️ Behavior Notes

* 🧍 Each cart is unique per user (`req.user._id`).
* ✅ Adding the same product again **updates** the quantity.
* 🗑️ `DELETE /api/cart` clears the entire cart.
* 📦 Delivery method is required when adding/updating items.
* 🧠 `GET /api/cart?expand=product` populates product info (name, price, image).

---

> 👤 Maintained by **Astik Shah**
> For related APIs, see  [`orders.md`](./orders.md)

```


