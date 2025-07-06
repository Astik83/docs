

This document explains all middleware related to authentication, refresh tokens, email verification, and role-based access control in the **ShopSphere** backend.

---

## 🔐 Authentication Middleware

### ✅ `protect` — *Require Login*

> Verifies the **access token** and attaches the authenticated user to `req.user`.

#### 🧪 Usage

```js
router.get('/profile', protect, getUserProfile);
```

#### ⚙️ Behavior

- 🔍 Looks for token in:
  - 🍪 `req.cookies.jwt`
  - 🪪 `Authorization` header (`Bearer <token>`)
  - 🔗 `req.query.token`
- ✅ Verifies JWT
- 📅 Checks:
  - If email is verified (`user.isEmailVerified`)
  - If password changed after token was issued
- 🚫 Returns `401` or `403` if token is invalid, expired, or user unauthorized

---

## 🔄 Refresh Token Middleware

### 🔁 `verifyRefreshToken` — *Refresh Access Token*

> Validates **refresh tokens** and allows issuing new access tokens.

#### 🧪 Usage

```js
router.post('/auth/refresh', verifyRefreshToken, handleTokenRefresh);
```

#### ⚙️ Behavior

- Accepts token from:
  - 🍪 `req.cookies.refreshToken`
  - 📥 `req.body.refreshToken`
- Verifies using `REFRESH_TOKEN_SECRET`
- Ensures token is in `user.refreshTokens` array
- 🚫 Returns `401` if token is invalid, revoked, or expired

---

## 🎭 Role-Based Access Control (RBAC)

### 🧑‍⚖️ `role(...roles)` — *Allow Listed Roles Only*

> Grants access to specified roles (e.g., `admin`, `manager`, etc.)

#### 🧪 Usage

```js
router.delete('/admin-only', protect, role('admin'), deleteSomething);
```

#### 🚫 Returns

- `403 Forbidden` if user’s role is not in the allowed list

---

### 👑 `admin` — *Admin Shortcut*

> Shortcut middleware for `role('admin')`

#### 🧪 Usage

```js
router.get('/admin/dashboard', protect, admin, getDashboardData);
```

---

## 📧 Email Verification Enforcement

### 🔒 `verifiedOnly` — *Require Verified Email*

> Ensures the user has a verified email before proceeding.

#### 🧪 Usage

```js
router.get('/restricted', protect, verifiedOnly, getRestrictedContent);
```

- 🚫 Returns `403` if `user.isEmailVerified` is `false`

---

## 👥 Optional Authentication

### 👤 `optionalAuth` — *Allow Guests & Logged-in Users*

> Parses JWT token if present and sets `req.user`. Ignores invalid tokens silently.

#### 🧪 Usage

```js
router.get('/products', optionalAuth, getProducts);
```

✅ Great for:
- Public routes with optional personalization (wishlist, recommendations)
- Pages where login is not mandatory

---

## ⚠️ Status Codes Used

All middleware respond with status codes defined in a shared utility:

```ts
STATUS_CODES = {
  UNAUTHORIZED: 401,  // 🔐 Token missing or invalid
  FORBIDDEN: 403      // ⛔ Access denied (role/email not allowed)
}
```

---

## 🛠️ Dev Tools & Behavior

| Mode        | Behavior                                                                 |
|-------------|--------------------------------------------------------------------------|
| 🛠️ Development | Logs errors verbosely for debugging                                  |
| 🚀 Production  | Suppresses token parsing errors in `optionalAuth` for silent fallback |

---
> Maintained by **Astik Shah**
🔗 **Back to API Index** → [📁 api-routes.md](./api-routes.md)
````

