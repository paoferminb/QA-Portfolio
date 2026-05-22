# 🔌 API Checklist

Validation checklist for REST API testing. Use this during exploratory API sessions or as a quick sanity check before marking an endpoint as tested.

---

## 🔐 Authentication & Authorization

- [ ] Requests without a token return `401 Unauthorized`
- [ ] Requests with an expired token return `401 Unauthorized`
- [ ] Requests with a valid token return the expected response
- [ ] A user cannot access another user's resources — returns `403 Forbidden`
- [ ] A lower-privilege role cannot perform admin-only actions — returns `403 Forbidden`

---

## 📥 Request Validation

- [ ] Missing required fields return `400 Bad Request`
- [ ] Wrong data types (e.g. string instead of number) return `400 Bad Request`
- [ ] Empty request body on PATCH/PUT returns `400 Bad Request`
- [ ] Extra unknown fields in the body are ignored — not saved or cause errors
- [ ] Invalid query parameter values return `400 Bad Request`

---

## 📤 Response Validation

- [ ] Successful responses return the correct HTTP status code
- [ ] Response body contains all expected fields
- [ ] Sensitive fields (password, tokens) are never exposed in responses
- [ ] `created_at` and `updated_at` timestamps are present where expected
- [ ] Paginated responses include `page`, `limit`, `total`, and `total_pages`

---

## 🔁 CRUD Behavior

- [ ] POST creates a new record — confirmed via GET after creation
- [ ] PUT replaces all fields — partial payload is rejected
- [ ] PATCH updates only the specified fields — other fields remain unchanged
- [ ] DELETE removes the resource — GET returns `404` after deletion
- [ ] Duplicate POST requests return `409 Conflict` where applicable

---

## 🧼 Error Handling

- [ ] Non-existent resource returns `404 Not Found`
- [ ] Business logic violations return `422 Unprocessable Entity`
- [ ] Conflict scenarios (duplicate data) return `409 Conflict`
- [ ] Error responses include a descriptive message — no raw stack traces
- [ ] Server errors return `500` and do not expose internal details

---

## 🗄️ Database Verification

- [ ] POST side effects are confirmed in the DB (record created with correct values)
- [ ] DELETE side effects are confirmed in the DB (record removed or soft-deleted)
- [ ] PATCH updates only the expected columns — others unchanged
- [ ] No duplicate records exist after repeated identical requests

---

🧠 *Run requests in Postman. Validate DB side effects using TablePlus or DBeaver.*
