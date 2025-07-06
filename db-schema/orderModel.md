

This model stores placed orders, each containing one or more products with tracking, pricing, and shipping information.

---

## 🧱 Schema Fields

| Field           | Type     | Description                                 |
|------------------|----------|---------------------------------------------|
| `user`           | ObjectId | Refers to the user who placed the order     |
| `shippingAddress`| Object   | Full delivery address                       |
| `items`          | Array    | List of products in the order               |
| `itemsTotal`     | Number   | Total product price (sum of all items)      |
| `shippingTotal`  | Number   | Total shipping fees                         |
| `tax`            | Number   | Tax (e.g., 10% of itemsTotal + shipping)    |
| `orderTotal`     | Number   | Final price (items + shipping + tax)        |
| `status`         | String   | Overall order status                        |
| `paymentStatus`  | String   | Payment completion state                    |

---

## 🧩 Subschema: Order Item

| Field              | Type     | Description                            |
|--------------------|----------|----------------------------------------|
| `productId`         | ObjectId | Refers to product                      |
| `name`              | String   | Product name (copied for snapshot)     |
| `image`             | String   | Product image URL                      |
| `priceCents`        | Number   | Price per unit at time of ordering     |
| `quantity`          | Number   | No. of units ordered                   |
| `deliveryDays`      | Number   | Delivery speed chosen                  |
| `shippingFee`       | Number   | Shipping fee per item                  |
| `estimatedDelivery` | Date     | Expected delivery date                 |
| `status`            | String   | Status per item (see below)            |

### Status Options

| Order Item Status | Description         |
|-------------------|---------------------|
| `pending`         | Order placed        |
| `processing`      | Being prepared      |
| `shipped`         | Out for delivery    |
| `delivered`       | Successfully reached|
| `cancelled`       | Cancelled by user/admin |

---

## 🏷️ Payment Status

| Value     | Meaning                            |
|-----------|------------------------------------|
| `pending` | Not paid yet (COD or failure)      |
| `paid`    | Successfully paid (Razorpay)       |
| `failed`  | Payment attempt failed             |

---

## 📬 Shipping Address

| Field       | Type     |
|-------------|----------|
| `fullName`  | String   |
| `address`   | String   |
| `city`      | String   |
| `state`     | String   |
| `postalCode`| String   |
| `country`   | String   |
| `phone`     | String   |

---

## 🔄 Notes

- Status is managed per-item; overall `status` is derived
- Orders are normalized for API responses (`/mine`, `/id`, `/admin`)
- `timestamps: true` auto-adds `createdAt`, `updatedAt`

---
> Maintained by **Astik Shah** 
🔗 **Back to Index** → [models.md](./models.md)
```

---

