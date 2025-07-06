Here is a clean, well-documented **`usermodel.md`** file for your ShopSphere platform, covering all fields, features, and behavior of the user schema — with clear headings, emojis, and security notes.

---

### 📄 `usermodel.md`

````md
# 👤 User Model — `models/userModel.js`

This document describes the structure, fields, and functionality of the `User` model used for authentication, email verification, password reset, and account management in ShopSphere.

---

## 🧱 Schema Fields

| Field                   | Type     | Description                                             |
|------------------------|----------|---------------------------------------------------------|
| `name`                 | String   | User's full name (2–50 characters)                     |
| `email`                | String   | Unique, lowercase, validated email                     |
| `password`             | String   | Hashed password (min 8 chars, `select: false`)         |
| `isEmailVerified`      | Boolean  | Whether user has verified their email                  |
| `role`                 | String   | `user` (default) or `admin`                            |
| `emailVerificationOTP`| String   | Hashed OTP used for email verification (`select: false`) |
| `otpExpiry`            | Date     | Expiry time for the OTP                                |
| `passwordChangedAt`    | Date     | Used to invalidate old tokens after password change    |
| `passwordResetToken`   | String   | Hashed reset token (`select: false`)                   |
| `passwordResetExpires` | Date     | Reset token expiration time                            |
| `loginAttempts`        | Number   | Tracks failed login attempts                           |
| `lockUntil`            | Date     | Account lockout expiry if login fails too often        |
| `refreshTokens`        | Array    | List of issued refresh tokens (multi-device support)   |
| `otpAttempts`          | Number   | Track incorrect OTP submissions                        |
| `otpRequestCount`      | Number   | Rate limit OTP requests                                |
| `otpRequestTime`       | Date     | Time of last OTP request                               |
| `isActive`             | Boolean  | Whether the account is active                          |
| `lastLogin`            | Date     | Timestamp of last successful login                     |

---

## 🔐 Security Features

- ✅ **Password hashing** using `bcrypt` with salt rounds (`12`)
- ✅ OTPs and reset tokens are securely hashed using `SHA-256`
- ✅ **Account lockout** after 5 failed attempts for 15 mins
- ✅ Refresh token rotation support
- ✅ Sensitive fields are **excluded from JSON responses**

---

## 🔧 Virtual Fields

| Virtual        | Description                                  |
|----------------|----------------------------------------------|
| `auditLog`     | Returns an object with login/password stats  |

---

## 🧠 Instance Methods

| Method                     | Description                                               |
|----------------------------|-----------------------------------------------------------|
| `matchPassword(password)`  | Compares input password with stored hash                 |
| `changedPasswordAfter(ts)` | Checks if token was issued before latest password change |
| `createEmailVerificationOTP()` | Generates a 6-digit OTP, sets expiry, returns raw OTP |
| `verifyEmailOTP(otp)`      | Verifies OTP against stored hash and expiry              |
| `createPasswordResetToken()` | Generates and stores hashed password reset token       |
| `incrementLoginAttempts()` | Increments login attempts and applies lock if needed     |
| `resetLoginAttempts()`     | Clears lock and resets counter after successful login    |
| `isLocked()`               | Returns true if account is locked                        |
| `isOTPExpired()`           | Checks if OTP is expired                                 |

---

## 🧪 Hooks & Middleware

| Type       | Purpose                                                                 |
|------------|-------------------------------------------------------------------------|
| `pre('save')` | - Lowercase email <br> - Hash password <br> - Set passwordChangedAt  |
| `post('save')`| Converts duplicate key and validation errors to friendly messages    |
| `toJSON()`    | Removes sensitive fields from response object                        |

---

## 🧩 Sample Output (After Login)

```json
{
  "_id": "60faab3b8b1f1c001f932a80",
  "name": "Astik Shah",
  "email": "astik@example.com",
  "isEmailVerified": true,
  "role": "user",
  "createdAt": "2025-07-06T08:00:00Z",
  "updatedAt": "2025-07-06T08:01:00Z",
  "auditLog": {
    "lastPasswordChange": "2025-07-06T07:59:59Z",
    "accountCreated": "2025-07-06T08:00:00Z",
    "lastLogin": "2025-07-06T08:01:00Z",
    "isLocked": false
  }
}
````

---

## 📌 Notes

* All passwords, OTPs, and tokens are never stored in plaintext.
* Refresh token support allows concurrent sessions per device.
* Designed with flexibility for production (10-min OTPs) and dev/test (30-min OTPs).

---
> Maintained by **Astik Shah** 
🔙 **Back to Models Index** → [models.md](./models.md)
🔗 **Back to API Index** → [api-routes.md](./api-routes.md)

```



