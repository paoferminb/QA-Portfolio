# API Test Cases

Structured test cases organized by HTTP method. Each file covers multiple endpoints with 5 scenarios each: Authentication, Authorization, Happy Path, Validation/Business Logic, and Edge Cases.

---

## TC_DELETE.md
Tests for resource deletion across 3 endpoints.

- **DELETE /products/:id** — verifies admin-only access, conflict when product has active orders, and correct handling of an already-deleted resource.
- **DELETE /orders/:id** — covers customer cancellation, rejection of shipped orders, and malformed ID handling.
- **DELETE /products/:id/reviews/:id** — validates own-review deletion, cross-user restrictions, and behavior when the parent product doesn't exist.

---

## TC_GET.md
Tests for data retrieval across 3 endpoints.

- **GET /products** — covers paginated listing, category filtering, empty results on out-of-range page, and special characters in query params.
- **GET /orders/:id** — validates ownership enforcement, non-existent ID handling, and malformed ID format.
- **GET /users/:id** — verifies own profile access, cross-user restriction, admin override, and that password is never exposed in the response.

---

## TC_PATCH.md
Tests for partial updates across 3 endpoints.

- **PATCH /orders/:id** — covers valid status transitions, invalid transitions, role restrictions, and empty body handling.
- **PATCH /users/:id** — validates email update, duplicate email conflict, and undefined behavior for same-value updates.
- **PATCH /products/:id** — tests admin-only price update, wrong data type, and price set to zero.

---

## TC_POST.md
Tests for resource creation across 3 endpoints.

- **POST /orders** — covers happy path, missing fields, out-of-stock conflict, and quantity set to zero.
- **POST /users/register** — validates successful registration, duplicate email, format errors, and injection of unknown fields like `admin: true`.
- **POST /products/:id/reviews** — tests purchase-based authorization, duplicate review conflict, and rating out of allowed range.

---

## TC_PUT.md
Tests for full resource replacement across 3 endpoints.

- **PUT /products/:id** — verifies all fields are required, partial payloads are rejected, and identical payloads still refresh `updated_at`.
- **PUT /users/:id** — covers full profile replacement, email conflict, and empty string on required field.
- **PUT /orders/:id/shipping** — validates replacement on pending orders, rejection on shipped orders, and missing field handling.
