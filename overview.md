# 🛍️ ShopSphere — Project Overview

## 📝 Introduction

**ShopSphere** is a full-stack 🧱 eCommerce platform built using the **MERN** stack (MongoDB, Express.js, React, Node.js). It supports all essential eCommerce functionalities such as product browsing, secure user authentication, cart management, checkout with payment integration, order tracking, and an admin dashboard for management.

This project is designed to be:
- 🔄 **Reusable** across various business domains
- 🔐 **Secure**, with JWT authentication and OTP-based email verification
- 🛒 **User-friendly**, featuring a modern, responsive UI/UX
- 🧠 **Extendable**, with optional AI chatbot support

---

## 🛠️ Tech Stack

| 🧩 Layer      | ⚙️ Technology                                                                 |
|--------------|-------------------------------------------------------------------------------|
| 🎨 Frontend   | React, Tailwind CSS, React Router DOM, Axios                                 |
| 🧠 Backend    | Node.js, Express.js                                                          |
| 💾 Database   | MongoDB with Mongoose                                                        |
| 🔐 Auth       | JWT (Access & Refresh Tokens), OTP (via Email)                               |
| 💳 Payment    | Razorpay (Stripe integration planned)                                        |
| ☁️ Hosting    | Vercel (Frontend), Render/Railway (Backend), MongoDB Atlas (Database)        |

---

## 🌟 Major Features

### 👤 User Features
- ✉️ Register with email verification (OTP)
- 🔐 JWT-based login/logout with refresh tokens
- 🔍 Browse products with images, descriptions, and ratings
- 🛒 Manage cart (add, update, remove items)
- 🚚 Choose delivery options per product
- 💳 Checkout via Razorpay
- 📦 View order history and status
- 🧾 Manage profile (name, password)

### 🛠️ Admin Features
- 👥 Manage users (view, edit, delete)
- 🛍️ Manage products (add, update, delete)
- 📦 Manage orders (view, update delivery status)
- 📊 Admin dashboard (future enhancement)

### 📦 Product Features
- 🖼️ Product images, title, description, price, rating
- 🏷️ Categories, stock, and shipping fee options
- 🔎 Filter and sort products

### 🛒 Cart & Orders
- 🔐 Cart saved per user session
- 🚚 Orders store delivery type/status per item
- 💳 Razorpay integration for payments
- ✅ Admin control over each product's delivery status

---

## 🛡️ Security Features

- 🔁 JWT access & refresh token rotation
- 📧 OTP-based email verification
- 🚫 Rate limiting (login/register/OTP routes)
- 🧹 Input validation and HTML sanitization
- 🛑 Protected/private/admin-only routes via middleware
- 🔑 Passwords hashed using bcrypt
- 🪖 Secure headers using Helmet

---

## 🤖 AI Chatbot (Optional Module)

- 🗨️ Friendly chatbot for platform/product queries
- 🧠 RAG-style logic using indexed data + LLM fallback
- ♻️ Reusable chatbot backend, pluggable frontend widget
- ⚙️ Easy product data integration

---

## 📌 Use Cases

- 🛍️ Online store for physical/digital products
- 🧑‍💼 Admin-driven product/order management
- 🎓 Academic project, 🧪 MVP, or 💼 commercial starter base

---

## 🚀 Project Goals

- 🧱 Build a modular, scalable eCommerce platform
- 🔄 Support complete order-to-delivery lifecycle
- 👨‍💻 Provide a clean, maintainable codebase
- 👥 Enable collaboration and learning

---

## 📁 Next Steps

Refer to the following docs for implementation:

- [`api-routes.md`](./api-routes.md) – 📡 Backend route structure
- [`frontend.md`](./frontend.md) – 🧑‍🎨 UI structure and routing
- [`setup.md`](./setup.md) – ⚙️ Setup and environment config
- [`packages.md`](./packages.md) – 📦 Package usage explanation
- [`workflows.md`](./workflows.md) – 🔁 Development & deployment flow

---

> Maintained by **Astik Shah**  
> For contributions or support, check the `README.md` or the official repository.
