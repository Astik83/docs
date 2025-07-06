
# ❤️ Health Check Route — `/health`

This route confirms that the ShopSphere API server is operational. Ideal for uptime monitors like UptimeRobot, BetterStack, or internal dashboards.

---

## 🔍 Endpoint

| Method | Endpoint   | Description                               |
|--------|------------|-------------------------------------------|
| GET    | `/health`  | Returns basic server status and metadata  |

---

## 📤 Sample Response

```json
{
  "status": "ok",
  "environment": "production",
  "timestamp": "2025-07-06T08:14:03.123Z"
}
````

### 🔑 Fields

* ✅ `status`: `"ok"` when the service is healthy
* 🌍 `environment`: `"development"` or `"production"`
* ⏱️ `timestamp`: ISO 8601 format of current server time

---

## 🔒 Authentication

* ❌ No authentication required
* ✅ Safe for public usage (doesn’t expose secrets)

---

## 🔧 Usage Examples

* Deployment health check (CI/CD)
* Load balancer or API gateway probe
* Uptime tracking with alerting

---
> 👤 Maintained by **Astik Shah**
🧭 **Back to API Index** → [api-routes.md](./api-routes.md)

```


