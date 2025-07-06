# 🔄 ShopSphere Workflow Diagram

```mermaid
%% ShopSphere Core Workflows
flowchart TD
    subgraph Auth[👤 Authentication]
        direction TB
        reg[Register] -->|Submit details| otp[Send OTP]
        otp --> verify[Verify Email]
        verify -->|Success| acct[Account Created]
        
        login[Login] -->|Credentials| checks{System Checks}
        checks -->|Verified?| yes[Yes]
        checks -->|Locked?| no[No]
        checks -->|Password?| correct[Correct]
        yes --> tokens[Issue Tokens]
        no --> block[Block Access]
        correct --> tokens
    end

    subgraph Cart[🛒 Cart Management]
        direction LR
        add[Add to Cart] -->|POST /cart| items[Cart Items]
        items --> checkout[Checkout]
        checkout -->|POST /orders| create[Create Order]
        create --> clear[Clear Cart]
        create --> payment{Payment?}
        payment -->|Razorpay| verify[Verify Payment]
        payment -->|Other| status[Update Status]
    end

    subgraph Orders[📦 Order Lifecycle]
        direction TB
        view[View Orders] -->|GET /orders/mine| list[List]
        list --> detail[View Order] -->|GET /orders/:id| info[Details]
        info --> cancel{Cancel?}
        cancel -->|Full| full[PUT /:id/cancel]
        cancel -->|Item| item[PUT /:orderId/items/:productId/cancel]
        style cancel stroke:#f00
    end

    subgraph Admin[🛠️ Admin]
        direction LR
        dash[Admin Dashboard] --> users[View Users]
        dash --> products[Manage Products]
        dash --> orders[View Orders]
        orders --> update[Update Status]
        update -->|pending →| processing[processing]
        processing -->|→| shipped[shipped]
        shipped -->|→| delivered[delivered]
    end

    subgraph Bot[🤖 Chatbot]
        direction TB
        query[User Query] --> rag{Local RAG}
        rag -->|Match| answer[Immediate Response]
        rag -->|No Match| llm[External LLM]
        llm --> response[Generate Answer]
    end

    subgraph Security[🔐 Security]
        direction RL
        jwt[JWT Tokens]
        refresh[Token Rotation]
        otp[Email OTP]
        rate[Rate Limiting]
        hash[bcrypt]
        sanitize[Input Sanitization]
        rbac[Role-Based Access]
    end

    Auth -->|Auth| Cart
    Cart -->|Create| Orders
    Admin -->|Manage| Orders
    Bot -->|Support| Cart
    Security -->|Protects| Auth
    Security -->|Secures| Cart