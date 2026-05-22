# Test Cases – GET Requests

**Tool:** Postman  
**Environment:** Staging  
**Base URL:** `https://api.example-shop.com/v1`

---

## GET /products (Product List)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `GET /products` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Happy Path | Retrieve paginated product list | 1. Authenticate <br> 2. Send `GET /products?page=1&limit=10` | `200 OK`, body contains `products[]`, `total`, `page`, `total_pages` | ✅ Pass |
| Filtering | Filter by valid category | 1. Authenticate <br> 2. Send `GET /products?category=electronics` | `200 OK`, all returned products have `category: electronics` | ✅ Pass |
| Edge Case | Request page beyond total | 1. Authenticate <br> 2. Send `GET /products?page=999` | `200 OK` with empty `products: []` | ❌ Fail — returns `404` instead of empty array |
| Edge Case | Filter with special characters in query | 1. Authenticate <br> 2. Send `GET /products?category=electr%00nics` | `400 Bad Request` | ✅ Pass |

---

## GET /orders/:id (Order by ID)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `GET /orders/ord-1042` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer requests another customer's order | 1. Authenticate as customer A <br> 2. Send `GET` on an order owned by customer B | `403 Forbidden` | ✅ Pass |
| Happy Path | Retrieve own order by valid ID | 1. Authenticate as customer <br> 2. Send `GET /orders/ord-1042` | `200 OK`, body contains `id`, `status`, `items[]`, `total` | ✅ Pass |
| Validation | Non-existent order ID | 1. Authenticate <br> 2. Send `GET /orders/ord-0000` | `404 Not Found` | ✅ Pass |
| Edge Case | Malformed ID format | 1. Authenticate <br> 2. Send `GET /orders/!!!` | `400 Bad Request` | ✅ Pass |

---

## GET /users/:id (User Profile)

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Request without token | 1. Send `GET /users/cust-88` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer accesses another user's profile | 1. Authenticate as customer A <br> 2. Send `GET /users/cust-99` | `403 Forbidden` | ✅ Pass |
| Happy Path | Retrieve own profile | 1. Authenticate <br> 2. Send `GET /users/cust-88` | `200 OK`, body contains `id`, `name`, `email`, `role` | ✅ Pass |
| Security | Password not exposed in response | 1. Authenticate <br> 2. Send `GET /users/cust-88` <br> 3. Inspect response body | No `password` or `password_hash` field in response | ✅ Pass |
| Edge Case | Admin retrieves any user profile | 1. Authenticate as admin <br> 2. Send `GET /users/cust-88` | `200 OK` with full profile data | ✅ Pass |
