
# 🔄 ShopSphere Workflow Diagram

This document visualizes the core logic and flows behind the ShopSphere platform — from user authentication to order lifecycle, admin operations, chatbot assistance, and security layers.

---

## 🧩 Full System Flowchart

```mermaid
%% ShopSphere Workflow Diagram
flowchart TD
    subgraph Auth[👤 User Authentication]
        direction TB
        A[Register] -->|Submit name/email/password| B(Send OTP)
        B --> C[Verify Email]
        C -->|Success| D[Account Created]
        
        E[Login] -->|Email+Password| F{Checks}
        F -->|Verified?| G[Yes]
        F -->|Locked?| H[No]
        F -->|Password?| I[Correct]
        G --> J[Issue Tokens]
        H --> K[Block Access]
        I --> J
        J -->|accessToken + refreshToken| K[Authenticated]
    end

    subgraph CartOrder[🛒 Cart → Order]
        direction LR
        L[Add to Cart] -->|POST /api/cart| M[Cart Items:\nproductId, quantity\ndeliveryDays, shippingFee]
        M --> N[Checkout]
        N -->|POST /api/orders| O[Create Order]
        O --> P[Clear Cart]
        O --> Q{Payment?}
        Q -->|Razorpay| R[Verify Payment\npending → paid]
        Q -->|Other| S[Update Status]
    end

    subgraph OrderLifecycle[📦 Order Lifecycle]
        direction TB
        T[View Orders] -->|GET /api/orders/mine| U[List Orders]
        U --> V[View Order] -->|GET /api/orders/:id| W[Order Details]
        W --> X{Cancellation?}
        X -->|Full Order| Y[PUT /orders/:id/cancel]
        X -->|Single Item| Z[PUT /orders/:orderId/items/:productId/cancel]
        style X stroke:#f00,stroke-width:2px
    end

    subgraph Admin[🛠️ Admin Flow]
        direction LR
        AA[Admin Dashboard] --> AB[View Users]
        AA --> AC[Manage Products]
        AA --> AD[View Orders]
        AD --> AE[Update Status]
        AE -->|pending ➔| AF[processing]
        AF -->|➔| AG[shipped]
        AG -->|➔| AH[delivered]
        style AA stroke:#ff0,stroke-width:3px
    end

    subgraph Chatbot[🤖 AI Chatbot]
        direction TB
        BA[User Query] --> BB{Local RAG}
        BB -->|Match Found| BC[Immediate Answer]
        BB -->|No Match| BD[External LLM]
        BD --> BE[Groq/DeepSeek]
        BE --> BF[Response]
        style BA stroke:#0f0
    end

    subgraph Security[🔐 Security]
        direction RL
        CA[JWT Tokens] 
        CB[Refresh Rotation]
        CC[Email OTP]
        CD[Rate Limiting]
        CE[bcrypt Hashing]
        CF[Input Sanitization]
        CG[RBAC]
    end

    Auth -->|User Auth| CartOrder
    CartOrder -->|Order Created| OrderLifecycle
    Admin -->|Manage| OrderLifecycle
    Chatbot -->|Assist| CartOrder
    Security -->|Protects| Auth
    Security -->|Secures| CartOrder
```

---

## 🧠 Notes

- 📍 **Red stroke** on cancellation = critical path
- 💛 **Yellow stroke** on Admin = privileged access
- ✅ Chatbot is marked green as entry point for support

---
> Maintained by **Astik Shah**
🧭 **Back to Index** → [index.md](./index.md)
````


