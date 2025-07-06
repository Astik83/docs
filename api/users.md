

# 👤 User Routes — `/api/users`

This document covers all **user-related API endpoints** for authentication, profile management, password reset, and admin-level user management.

---

## 🔓 Public Routes (No Auth Required)

| Method | Endpoint                           | Description                             |
|--------|------------------------------------|-----------------------------------------|
| POST   | `/api/users/register`              | Register a new user                     |
| POST   | `/api/users/verify-email`          | Verify email using OTP                  |
| POST   | `/api/users/resend-otp`            | Resend OTP to the user's email          |
| POST   | `/api/users/login`                 | Log in and receive access/refresh tokens |
| POST   | `/api/users/refresh-token`         | Refresh access token via refresh token |
| POST   | `/api/users/forgot-password`       | Send password reset link to email       |
| PATCH  | `/api/users/reset-password/:token` | Reset password using emailed token      |

---

## 🧑‍💻 Protected Routes (Requires JWT)

| Method | Endpoint             | Description                        |
|--------|----------------------|------------------------------------|
| GET    | `/api/users/profile` | Get logged-in user's profile       |
| PUT    | `/api/users/profile` | Update user name and/or password   |
| DELETE | `/api/users/account` | Delete user account permanently    |
| POST   | `/api/users/logout`  | Logout and invalidate tokens       |

> ✅ Requires valid JWT in `Authorization: Bearer <token>`  
> or stored in `HTTP-only cookie` (depending on frontend strategy)

---

## 👮‍♂️ Admin Routes (Requires Admin Role)

| Method | Endpoint                    | Description                         |
|--------|-----------------------------|-------------------------------------|
| GET    | `/api/users/admin/users`    | Get list of all registered users    |
| DELETE | `/api/users/admin/user/:id` | Delete specific user by ID          |

> 🔐 Requires both authentication and admin role verification.

---

## 🧠 How It Works (Simplified Flow)

```mermaid
graph TD
  A[User Registers] --> B[OTP Sent to Email]
  B --> C[User Verifies Email]
  C --> D[User Logs In]
  D --> E[Server Returns Access + Refresh Tokens]
  E --> F[Client Stores Tokens & Makes Authenticated Requests]
````

---

## 📌 Login Request/Response Details

### 🔐 Request

```http
POST /api/users/login
Content-Type: application/json

{
  "email": "user@example.com",
  "password": "yourPassword123"
}
```

### ✅ Successful Response

```json
{
  "success": true,
  "data": {
    "_id": "64d0f7c4a1234567890ab123",
    "name": "Astik Shah",
    "email": "user@example.com",
    "isEmailVerified": true
  },
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

### 📎 Notes:

* `accessToken` is typically stored in memory or a header (`Authorization: Bearer ...`)
* `refreshToken` can be stored in HTTP-only cookies or secure storage for silent refresh
* On failed login:

  * Locked accounts return `429 Too Many Requests`
  * Invalid password returns `401 Unauthorized`
  * Unverified email returns `403 Forbidden`

---

## 🧾 Additional Notes

* Tokens are generated using secure JWT strategy.
* Passwords are hashed with `bcryptjs`.
* Login attempts are tracked to prevent brute-force.
* Users must verify their email before gaining full access.
* Rate-limiting protects login and OTP endpoints.

---

> 👤 Maintained by **Astik Shah**
> For related APIs, see [`products.md`](./products.md), [`cart.md`](./cart.md), or [`orders.md`](./orders.md)

```

---


