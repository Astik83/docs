# 🛍️ ShopSphere — Full Stack eCommerce Platform(https://shop-sphere-eta-sand.vercel.app/)

> **Production-ready eCommerce solution** featuring secure authentication, AI-powered support(not added yet), and a full admin panel.
> Developed by **Astik Shah** using React, Node.js, and MongoDB.

---

<div align="center">

[![React](https://img.shields.io/badge/React-18.2-blue?logo=react)](https://react.dev/)
[![Node.js](https://img.shields.io/badge/Node.js-20-green?logo=nodedotjs)](https://nodejs.org/)
[![MongoDB](https://img.shields.io/badge/MongoDB-7.0-green?logo=mongodb)](https://www.mongodb.com/)
[![License](https://img.shields.io/badge/License-MIT-blue)](./LICENSE)

</div>

---

## 🌟 Key Features

| Feature                | Description                                 | Tech Used                             |
| ---------------------- | ------------------------------------------- | ------------------------------------- |
| **🔐 Auth System**     | Email OTP, JWT, refresh token rotation      | JWT, bcrypt, Nodemailer               |
| **🛒 Cart & Checkout** | Smart cart with per-item shipping & fees    | React Context, MongoDB                |
| **💳 Payments**        | Stripe payment                              | Stripe                |
| **📊 Admin Panel**     | Manage users, orders, products              | React, Mongoose                       |
| **🤖 AI Chatbot**      | RAG-based AI assistant with fallback to LLM | Groq,                   |
| **⏳ Auto Cleanup**     | Cron jobs to remove stale/unverified data   | node-cron                             |
| **🔒 Security**        | RBAC, rate limiting, input sanitization     | Helmet, validator, express-rate-limit |

---

## 📚 Documentation Index

| Document              | Description                      | Link                                             |
| --------------------- | -------------------------------- | ------------------------------------------------ |
| **System Overview**   | Architecture & modules           | [`overview.md`](./overview.md)                   |
| **API Reference**     | Full route docs                  | [`api-routes.md`](./api/api-routes.md)               |
| **Database Schema**   | Mongoose schemas                 | [`db-schema.md`](./db-schema)                 |
| **Workflow Diagram**  | Visual flow of app               | [`workflow.md`](./workflows.md)                   |
| **Middleware Guide**  | Auth, RBAC, optional login, etc. | [`middleware.md`](./middleware.md)               |
| **Frontend Packages** | React dependency list            | [`packages-frontend.md`](./packages/frontend.md) |
| **Backend Packages**  | Node.js dependency list          | [`packages-backend.md`](./packages/backend.md)   |

---

## 🚀 Tech Stack

### Frontend (React + Vite)

```mermaid
graph LR
    A[Vite] --> B[React 18]
    B --> C[React Router v7]
    B --> D[Axios]
    B --> E[Context API]
    B --> F[React Icons]
    B --> G[TailwindCSS]
    style A fill:#646cff,stroke:#000
    style B fill:#61dafb,stroke:#000
```

### Backend (Node.js)

```mermaid
graph LR
    H[Express.js] --> I[Mongoose]
    H --> J[JWT Auth]
    H --> K[Nodemailer]
    H --> L[Razorpay SDK]
    H --> M[bcryptjs]
    H --> N[node-cron]
    style H fill:#68a063,stroke:#000
```

---

## ⚙️ Setup Guide

### 1. Clone Repositories

```bash
# Frontend
git clone https://github.com/your-repo/ecommerce-frontend.git
cd ecommerce-frontend

# Backend
git clone https://github.com/your-repo/ecommerce-backend.git
cd ecommerce-backend
```

### 2. Configure Environment

**.env (Backend)**

```env
MONGODB_URI=mongodb://localhost:27017/shopsphere
JWT_SECRET=your_secure_jwt_secret
RAZORPAY_KEY_ID=rzp_test_xxxxxxxx
RAZORPAY_KEY_SECRET=xxxxxxxxxxxxxxxx
EMAIL_USER=your@email.com
EMAIL_PASS=app_password
```

**.env (Frontend)**

```env
VITE_API_BASE_URL=http://localhost:5000/api
VITE_RAZORPAY_KEY_ID=rzp_test_xxxxxxxx
```

### 3. Install Dependencies & Start

```bash
# Backend
npm install
npm run dev

# Frontend
npm install
npm run dev
```

### 4. Seed Initial Data

```bash
# Run MongoDB seed script
npm run seed
```

---

## 🤖 AI Chatbot Flow

```mermaid
flowchart LR
    User[User Query] --> RAG{Local RAG}
    RAG -->|Match| Response[Answer from DB]
    RAG -->|No Match| LLM[Fallback to LLM]
    LLM --> Groq[Groq API]
    LLM --> DeepSeek[DeepSeek API]
    Groq --> Response
    DeepSeek --> Response
```

---

## 🔐 Security Overview

| Layer                | Technique                       | Tools Used               |
| -------------------- | ------------------------------- | ------------------------ |
| **Auth**             | JWT + Refresh token rotation    | HTTP-only cookies        |
| **Input Validation** | Sanitize & validate user input  | validator, sanitize-html |
| **Access Control**   | Role-based authorization (RBAC) | Middleware               |
| **Rate Limiting**    | Prevent brute-force attacks     | express-rate-limit       |
| **Hashing**          | Password encryption             | bcrypt (12 salt rounds)  |
| **Email Security**   | Time-sensitive OTP verification | Nodemailer, token expiry |

---



---

## ✨ Connect

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Astik_Shah-blue?logo=linkedin)](https://www.linkedin.com/in/astik-shah-04aa46344/)


> For educational and portfolio use only.
