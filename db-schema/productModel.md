
This model defines how product information is stored in the database.

---

## 🧱 Schema Fields

| Field       | Type     | Description                              |
|-------------|----------|------------------------------------------|
| `image`     | String   | Product image URL                        |
| `name`      | String   | Name/title of the product                |
| `rating`    | Object   | `{ stars: Number, count: Number }`       |
| `priceCents`| Number   | Price in paise (₹100 = 10000)            |
| `keywords`  | [String] | Tags used for search filtering           |
| `category`  | String   | Predefined product category              |
| `createdBy` | ObjectId | Refers to the admin who created product  |

### 📦 Category Enum

```ts
['All', 'Electronics', 'Clothing', 'Home & Kitchen', 'Beauty', 'Books', 'Toys', 'Sports', 'Other']
````

---

## 🧩 Subschema: `rating`

| Field   | Type   | Description         |
| ------- | ------ | ------------------- |
| `stars` | Number | Avg. rating (0–5)   |
| `count` | Number | Number of reviewers |

---

## 🛠️ Notes

* `timestamps: true` adds `createdAt` and `updatedAt`.
* Optimized for listing, filtering, and search indexing.
* Related to user via `createdBy` (admin user).

---
> Maintained by **Astik Shah** 
🔗 **Back to Index** → [models.md](./models.md)

````



