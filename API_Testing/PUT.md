# Test Cases – PUT Requests

**Tool:** Postman  
**Environment:** Staging  
**Base URL:** `https://api.example-shop.com/v1`

---

## PUT /products/:id (Full Product Update)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PUT /products/prod-001` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer role attempts full update | 1. Authenticate as customer <br> 2. Send `PUT` with complete product payload | `403 Forbidden` | ✅ Pass |
| Happy Path | Admin sends full valid payload | 1. Authenticate as admin <br> 2. Send `PUT /products/prod-001` with all required fields | `200 OK`, all fields updated, `updated_at` refreshed | ✅ Pass |
| Validation | Missing one required field | 1. Authenticate as admin <br> 2. Send `PUT` with payload missing `description` | `400 Bad Request` — PUT requires all fields | ❌ Fail — partial payload accepted, missing field set to null |
| Edge Case | Send identical payload (no changes) | 1. Authenticate as admin <br> 2. Send `PUT` with exact same data already stored | `200 OK`, `updated_at` refreshed even with no data change | ✅ Pass |

---

## PUT /users/:id (Full Profile Replacement)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PUT /users/cust-88` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer updates another user | 1. Authenticate as customer A <br> 2. Send `PUT` on customer B's ID | `403 Forbidden` | ✅ Pass |
| Happy Path | Full valid profile replacement | 1. Authenticate <br> 2. Send `PUT /users/cust-88` with all required fields | `200 OK`, all fields replaced, `updated_at` refreshed | ✅ Pass |
| Conflict | Update email to one already in use | 1. Authenticate <br> 2. Send `PUT` with an email belonging to another account | `409 Conflict` | ✅ Pass |
| Edge Case | Send empty string for required field | 1. Authenticate <br> 2. Send `PUT` with `{ "name": "" }` | `400 Bad Request` | ❌ Fail — profile saved with empty name |

---

## PUT /orders/:id/shipping (Replace Shipping Address)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `PUT /orders/ord-1043/shipping` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer updates another customer's shipping | 1. Authenticate as customer A <br> 2. Send `PUT` on an order owned by customer B | `403 Forbidden` | ✅ Pass |
| Happy Path | Replace shipping on pending order | 1. Authenticate <br> 2. Send `PUT` with all required address fields | `200 OK`, shipping address fully replaced | ✅ Pass |
| Business Logic | Update shipping on shipped order | 1. Authenticate <br> 2. Send `PUT` on an order with `status: shipped` | `422 Unprocessable Entity` | ✅ Pass |
| Edge Case | Missing `zip_code` field | 1. Authenticate <br> 2. Send `PUT` with all fields except `zip_code` | `400 Bad Request` — all fields required for PUT | ✅ Pass |
