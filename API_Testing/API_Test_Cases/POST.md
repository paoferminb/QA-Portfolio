# Test Cases – POST Requests

**Tool:** Postman  
**Environment:** Staging  
**Base URL:** `https://api.example-shop.com/v1`

---

## POST /orders (Create Order)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `POST /orders` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Happy Path | Place order with valid data | 1. Authenticate <br> 2. Send `POST /orders` with valid `customer_id`, `items[]`, and `shipping_address` | `201 Created`, body contains `id`, `status: pending`, `total`, `created_at` | ✅ Pass |
| Validation | Missing required field `items` | 1. Authenticate <br> 2. Send `POST /orders` without the `items` field | `400 Bad Request` | ✅ Pass |
| Business Logic | Order includes out-of-stock product | 1. Authenticate <br> 2. Send `POST /orders` with a product that has `stock: 0` | `422 Unprocessable Entity` | ✅ Pass |
| Edge Case | Order with `quantity: 0` | 1. Authenticate <br> 2. Send `POST /orders` with `{ "product_id": "prod-001", "quantity": 0 }` | `400 Bad Request` | ❌ Fail — order is created with quantity 0 |

---

## POST /users/register (Register User)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Happy Path | Register with valid data | 1. Send `POST /users/register` with valid name, email, and password | `201 Created`, body contains `id`, `name`, `email`, `created_at` — no password exposed | ✅ Pass |
| Conflict | Register with existing email | 1. Send `POST /users/register` with an already registered email | `409 Conflict` | ✅ Pass |
| Validation | Invalid email format | 1. Send `POST /users/register` with `email: "notanemail"` | `400 Bad Request` | ✅ Pass |
| Validation | Password too short | 1. Send `POST /users/register` with a 4-character password | `400 Bad Request` | ✅ Pass |
| Edge Case | Extra unknown fields in body | 1. Send `POST /users/register` with valid fields plus `{ "admin": true }` | `201 Created` — unknown fields ignored; role not elevated | ❌ Fail — `admin: true` accepted and role set to admin |

---

## POST /products/:id/reviews (Create Review)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `POST /products/prod-001/reviews` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer who hasn't purchased the product | 1. Authenticate as customer with no purchase history for this product <br> 2. Send `POST` with review data | `403 Forbidden` | ✅ Pass |
| Happy Path | Submit valid review | 1. Authenticate as customer who purchased the product <br> 2. Send `POST` with `{ "rating": 5, "comment": "Great product!" }` | `201 Created`, body contains `id`, `product_id`, `rating`, `comment`, `created_at` | ✅ Pass |
| Conflict | Submit duplicate review | 1. Authenticate <br> 2. Submit a review for a product already reviewed by the same customer | `409 Conflict` | ✅ Pass |
| Edge Case | Rating outside allowed range | 1. Authenticate <br> 2. Send `POST` with `{ "rating": 10 }` | `422 Unprocessable Entity` | ✅ Pass |
