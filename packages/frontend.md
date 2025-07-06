
# 🧩 Frontend Packages — `ecommerce-project`

This document lists the essential frontend packages used in the **ShopSphere** app and provides instructions to install them using `npm`.

---

## 📦 Required Dependencies

Install all app-level dependencies using:

```bash
npm install react react-dom react-router-dom axios react-icons react-toastify
```

| Package             | Purpose                                           |
|---------------------|---------------------------------------------------|
| **react**           | Core library for building user interfaces         |
| **react-dom**       | DOM rendering utilities for React                 |
| **react-router-dom**| Client-side routing (v7)                          |
| **axios**           | HTTP client for REST API calls                    |
| **react-icons**     | Popular icon packs (Feather, FontAwesome, etc.)  |
| **react-toastify**  | Toast notifications (success, error, etc.)       |

---

## 🛠️ Dev Tools & Linting

Install Vite + linting tools using:

```bash
npm install -D vite @vitejs/plugin-react eslint @eslint/js eslint-plugin-react-hooks eslint-plugin-react-refresh
```

| Package                   | Purpose                                         |
|---------------------------|-------------------------------------------------|
| **vite**                  | Build tool and dev server                       |
| **@vitejs/plugin-react**  | JSX and HMR support for Vite                    |
| **eslint**                | JavaScript linter                               |
| **@eslint/js**            | ESLint base rules                               |
| **eslint-plugin-react-hooks** | Enforces correct usage of React hooks     |
| **eslint-plugin-react-refresh** | Enables Fast Refresh w/ ESLint         |

---

## 🧪 Optional (for TypeScript Users Only)

```bash
npm install -D @types/react @types/react-dom
```

| Package              | Used for                     |
|----------------------|------------------------------|
| **@types/react**     | TypeScript types for React   |
| **@types/react-dom** | TypeScript types for DOM API |

---

## 🚀 Scripts Overview

```bash
npm run dev       # Start Vite development server
npm run build     # Build project for production
npm run preview   # Preview built output
npm run lint      # Lint the codebase
```

---
> Maintained by **Astik Shah**
🔗 **Back to Index** → [index.md](./index.md)
````


