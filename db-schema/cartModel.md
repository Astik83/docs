## 📄 `cartmodel.md`



This model defines how individual users’ carts are stored and updated.

---

## 🧱 Schema Fields

| Field      | Type     | Description                        |
|------------|----------|------------------------------------|
| `userId`   | ObjectId | Refers to user (unique per user)   |
| `items`    | Array    | List of products with quantity, delivery info |

---

## 🧩 Subschema: Cart Item

| Field             | Type     | Description                            |
|------------------|----------|----------------------------------------|
| `productId`       | ObjectId | Refers to the product                  |
| `quantity`        | Number   | No. of units (min: 1)                  |
| `deliveryDays`    | Number   | Delivery time in days (chosen)        |
| `shippingFee`     | Number   | Fee for shipping (calculated)         |
| `estimatedDelivery`| Date    | Expected delivery date                |

---

## 🔒 Constraints

- Only **one cart per user** (`unique: true` on `userId`)
- `items` array can be updated with PUT requests via `/api/cart/:productId`

---

## 🔁 Behavior Notes

- Items persist until checkout
- Cart auto-clears after successful order
- Quantity and delivery are user-selectable

---
> Maintained by **Astik Shah** 
🔗 **Back to Index** → [models.md](./models.md)
````



