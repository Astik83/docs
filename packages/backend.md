# 🛠️ Backend Packages — `ecommerce-backend`

This document lists all backend dependencies used in the ShopSphere Node.js + Express + MongoDB project, along with installation commands and usage notes.

---

## 📦 Install All Core Dependencies

```bash
npm install express mongoose jsonwebtoken bcryptjs cookie-parser dotenv cors helmet express-rate-limit sanitize-html validator express-async-handler nodemailer nodemailer-express-handlebars envalid node-cron winston
```

| Package                       | Purpose                                                             |
|-------------------------------|---------------------------------------------------------------------|
| **express**                   | Core web framework                                                  |
| **mongoose**                  | MongoDB ORM/ODM for schema and queries                              |
| **jsonwebtoken**              | JWT creation/verification for auth                                  |
| **bcryptjs**                  | Hashing and comparing passwords                                     |
| **cookie-parser**             | Parses cookies (used for refresh token auth)                        |
| **dotenv**                    | Loads `.env` config into `process.env`                              |
| **cors**                      | Enables CORS (Cross-Origin Resource Sharing)                        |
| **helmet**                    | Sets secure HTTP headers                                            |
| **express-rate-limit**        | Rate limiting middleware for brute force protection                 |
| **sanitize-html**             | Prevents malicious HTML injection (XSS defense)                     |
| **validator**                 | Validates/sanitizes inputs like email, passwords, etc.              |
| **express-async-handler**     | Simplifies error handling in async routes                           |
| **nodemailer**                | Sends emails (OTP, reset, order updates, etc.)                      |
| **nodemailer-express-handlebars** | Handlebars templating for email bodies                     |
| **envalid**                   | Validates and enforces required `.env` variables                    |
| **node-cron**                 | Schedules jobs (e.g., delete unverified users)                      |
| **winston**                   | Advanced logger with file/console transports                        |

---

## 🧪 Install Dev Dependencies

```bash
npm install -D nodemon jest mocha chai supertest
```

| Package       | Used For                                         |
|---------------|--------------------------------------------------|
| **nodemon**   | Auto-restarts server on code changes             |
| **jest**      | Unit testing framework (if chosen)               |
| **mocha**     | Alternative test runner                          |
| **chai**      | Assertion library (used with Mocha)              |
| **supertest** | API endpoint testing with assertions             |

---


## 🧼 Recommended .env Setup

Example `.env` (see [env.example.md](./env.example.md) for full docs):

```
PORT=5000
MONGO_URI=your-mongo-uri
JWT_SECRET=your-jwt-secret
REFRESH_TOKEN_SECRET=your-refresh-secret
NODE_ENV=development
```

---
> Maintained by **Astik Shah** 
🔗 **Back to Index** → [index.md](./index.md)
