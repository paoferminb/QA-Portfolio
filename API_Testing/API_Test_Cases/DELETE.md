# Test Cases – DELETE Requests

**Tool:** Postman  
**Environment:** Staging  
**Base URL:** `https://api.example-shop.com/v1`

---

## DELETE /products/:id

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Delete without token | 1. Send `DELETE /products/prod-002` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer role attempts deletion | 1. Authenticate as customer <br> 2. Send `DELETE /products/prod-002` | `403 Forbidden` | ✅ Pass |
| Happy Path | Admin deletes existing product | 1. Authenticate as admin <br> 2. Send `DELETE /products/prod-002` | `204 No Content`, empty body | ✅ Pass |
| Conflict | Delete product with active orders | 1. Authenticate as admin <br> 2. Send `DELETE` on a product linked to a pending order | `409 Conflict` | ✅ Pass |
| Edge Case | Delete already deleted product | 1. Authenticate as admin <br> 2. Send `DELETE` on a previously deleted product ID | `404 Not Found` | ❌ Fail — returns `204` instead |

---

## DELETE /orders/:id

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Delete without token | 1. Send `DELETE /orders/ord-1043` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer deletes another customer's order | 1. Authenticate as customer A <br> 2. Send `DELETE` on an order owned by customer B | `403 Forbidden` | ✅ Pass |
| Happy Path | Customer cancels own pending order | 1. Authenticate as customer <br> 2. Send `DELETE /orders/ord-1043` | `204 No Content`, empty body | ✅ Pass |
| Business Logic | Delete order already shipped | 1. Authenticate as customer <br> 2. Send `DELETE` on an order with `status: shipped` | `422 Unprocessable Entity` | ✅ Pass |
| Edge Case | Delete with malformed order ID | 1. Authenticate as customer <br> 2. Send `DELETE /orders/!!!invalid` | `400 Bad Request` | ✅ Pass |

---

## DELETE /products/:id/reviews/:id

| Test Type | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| Authentication | Delete review without token | 1. Send `DELETE /products/prod-001/reviews/rev-301` with no Authorization header | `401 Unauthorized` | ✅ Pass |
| Authorization | Customer deletes another user's review | 1. Authenticate as customer A <br> 2. Send `DELETE` on a review created by customer B | `403 Forbidden` | ✅ Pass |
| Happy Path | Customer deletes own review | 1. Authenticate as customer <br> 2. Send `DELETE /products/prod-001/reviews/rev-301` | `204 No Content`, empty body | ✅ Pass |
| Functional | Deleted review no longer appears in product | 1. Delete a review <br> 2. Send `GET /products/prod-001/reviews` | Review is not present in the response | ✅ Pass |
| Edge Case | Delete review on non-existent product | 1. Authenticate as customer <br> 2. Send `DELETE /products/prod-999/reviews/rev-301` | `404 Not Found` | ⚠️ Blocked — product validation not implemented |
