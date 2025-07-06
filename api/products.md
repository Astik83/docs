
# 🛍️ Product Routes — `/api/products`

This document covers all API endpoints related to **product listing**, **search**, and **admin product management** in the ShopSphere platform.

---

### 🔓 Public Routes (No Auth Required)

| Method | Endpoint                 | Description                              |
|--------|--------------------------|------------------------------------------|
| GET    | `/api/products`          | Fetch all products (no pagination yet)   |
| GET    | `/api/products/search?q=term` | Search by name, description, or keywords |
| GET    | `/api/products/:id`      | Get a single product by ID               |

---

### 🛡️ Admin Routes (Requires Admin Role)

| Method | Endpoint                  | Description                    |
|--------|---------------------------|--------------------------------|
| POST   | `/api/products`           | Add a new product              |
| POST   | `/api/products/import`    | Bulk import multiple products  |
| PUT    | `/api/products/:id`       | Update product by ID           |
| DELETE | `/api/products/:id`       | Delete product by ID           |

> ✅ Requires `Authorization: Bearer <admin-token>`

---

### 🔍 `/api/products/search` — Smart Search

**Description**:  
Searches by partial match (`RegExp`) across:
- `name`
- `description`
- `keywords`

**Example:**

```http
GET /api/products/search?q=kitchen
````

**Returns:**

```json
[
  {
    "id": "8c9c52b5-5a19-4bcb-a5d1-158a74287c53",
    "image": "images/products/3-piece-cooking-set.jpg",
    "name": "3 Piece Non-Stick, Black Cooking Pot Set",
    "rating": { "stars": 4.5, "count": 175 },
    "priceCents": 3499,
    "keywords": ["kitchen", "cookware"],
    "category": "Home & Kitchen"
  },
  ...
]
```

> ℹ️ Returns a max of 10 results for performance.

---

### 🧾 Example: Create Product (Admin Only)

```http
POST /api/products
Authorization: Bearer <admin-token>
Content-Type: application/json

{
  "image": "images/products/mug.jpg",
  "name": "Ceramic Coffee Mug",
  "rating": { "stars": 4.2, "count": 85 },
  "priceCents": 899,
  "keywords": ["mug", "coffee", "drinkware"]
}
```

**Success Response:**

```json
{
  "message": "✅ Product created",
  "data": {
    "_id": "64b92fce8730ab8932e47f00",
    "image": "images/products/mug.jpg",
    "name": "Ceramic Coffee Mug",
    "rating": { "stars": 4.2, "count": 85 },
    "priceCents": 899,
    "keywords": ["mug", "coffee", "drinkware"],
    "createdBy": "64a12d..."
  }
}
```

---

### ⚠️ Error Responses

| Code | Message                   | Reason                        |
| ---- | ------------------------- | ----------------------------- |
| 400  | `Missing required fields` | Required data not provided    |
| 404  | `Product not found`       | Invalid or deleted product ID |

---


### 📘 Notes

* All product routes use `asyncHandler` for error catching.
* `createProduct` validates all fields and throws `400 Bad Request` on missing input.
* `getProductById` returns `404` if ID doesn't match any record.
* Search is flexible with **partial, case-insensitive** matches.

---

> 👤 Maintained by **Astik Shah**
> For related APIs, see [`cart.md`](./cart.md), or [`orders.md`](./orders.md)

```

---





