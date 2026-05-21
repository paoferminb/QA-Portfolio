# Test Cases – PATCH Requests

**Tool:** Postman  
**Environment:** Staging  
**Base URL:** `https://api.example-shop.com/v1`

---

## PATCH /orders/:id (Update Order Status)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PATCH /orders/ord-1042` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer tries to update status | 1. Authenticate as customer <br> 2. Send `PATCH` with `{ "status": "shipped" }` | `403 Forbidden` | ✅ Pass |
| Happy Path | Admin updates order to valid next status | 1. Authenticate as admin <br> 2. Send `PATCH /orders/ord-1042` with `{ "status": "shipped" }` | `200 OK`, response shows updated `status` and refreshed `updated_at` | ✅ Pass |
| Business Logic | Invalid status transition | 1. Authenticate as admin <br> 2. Send `PATCH` with `{ "status": "delivered" }` on a `pending` order | `422 Unprocessable Entity` | ✅ Pass |
| Edge Case | Send empty body `{}` | 1. Authenticate as admin <br> 2. Send `PATCH /orders/ord-1042` with empty JSON body | `400 Bad Request` | ❌ Fail — returns `200 OK` with no changes |

---

## PATCH /users/:id (Partial Profile Update)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PATCH /users/cust-88` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer updates another user's profile | 1. Authenticate as customer A <br> 2. Send `PATCH` on customer B's ID | `403 Forbidden` | ✅ Pass |
| Happy Path | Update email only | 1. Authenticate <br> 2. Send `PATCH /users/cust-88` with `{ "email": "new@example.com" }` | `200 OK`, only `email` and `updated_at` change; other fields unchanged | ✅ Pass |
| Conflict | Update email to one already in use | 1. Authenticate <br> 2. Send `PATCH` with an email belonging to another account | `409 Conflict` | ✅ Pass |
| Edge Case | Update with same current email | 1. Authenticate <br> 2. Send `PATCH` with the exact same email already on the account | `422 Unprocessable Entity` | ⚠️ Blocked — behavior not yet defined in spec |

---

## PATCH /products/:id (Update Price)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PATCH /products/prod-001` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer role attempts price update | 1. Authenticate as customer <br> 2. Send `PATCH` with `{ "price": 49.99 }` | `403 Forbidden` | ✅ Pass |
| Happy Path | Admin updates price | 1. Authenticate as admin <br> 2. Send `PATCH /products/prod-001` with `{ "price": 54.99 }` | `200 OK`, `price` updated; other fields unchanged | ✅ Pass |
| Validation | Price sent as string | 1. Authenticate as admin <br> 2. Send `PATCH` with `{ "price": "free" }` | `400 Bad Request` | ✅ Pass |
| Edge Case | Price set to zero | 1. Authenticate as admin <br> 2. Send `PATCH` with `{ "price": 0 }` | `422 Unprocessable Entity` | ❌ Fail — returns `200 OK` and saves price as 0 |
