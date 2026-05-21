# 🔌 API Testing

This section documents manual API testing performed on fictional e-commerce and healthcare platforms. It includes request examples organized by HTTP method and a dedicated folder with structured test cases.

---

## 📁 Structure

```text
API_Testing/
├── API_Test_Cases/         structured test cases organized by method
├── DELETE/                 resource deletion and conflict handling
├── GET/                    retrieve resources, filters, pagination
├── PATCH/                  partial updates
├── POST/                   resource creation and input validation
└── PUT/                    full resource replacement
```

---

## 📂 Explore

| Folder | Description |
|---|---|
| [API_Test_Cases/](../../tree/main/API_Testing/API_Test_Cases) | Structured test cases by method |
| [DELETE/](../../tree/main/API_Testing/DELETE) | Deletion, conflict and permission scenarios |
| [GET/](../../tree/main/API_Testing/GET) | List, filter, paginate, retrieve by ID |
| [PATCH/](../../tree/main/API_Testing/PATCH) | Partial updates, field-level validation |
| [POST/](../../tree/main/API_Testing/POST) | Create resources, validate required fields |
| [PUT/](../../tree/main/API_Testing/PUT) | Full replacement, enforce all fields required |

---

## 🔧 HTTP Methods

| Method | Purpose | Typical Success Code |
|---|---|---|
| `DELETE` | Remove a resource | `204 No Content` |
| `GET` | Retrieve one or multiple resources | `200 OK` |
| `PATCH` | Partially update a resource | `200 OK` |
| `POST` | Create a new resource | `201 Created` |
| `PUT` | Replace an entire resource | `200 OK` |

---

## 📋 Status Codes Reference

| Code | Meaning | When it appears |
|---|---|---|
| `200 OK` | Request successful | GET, PUT, PATCH |
| `201 Created` | Resource created | POST |
| `204 No Content` | Success, no body returned | DELETE |
| `400 Bad Request` | Invalid input or missing fields | Any |
| `401 Unauthorized` | Missing or invalid auth token | Any |
| `403 Forbidden` | Authenticated but not allowed | Any |
| `404 Not Found` | Resource doesn't exist | GET, PUT, PATCH, DELETE |
| `409 Conflict` | Duplicate or state conflict | POST, DELETE |
| `422 Unprocessable Entity` | Valid format but invalid business logic | POST, PATCH |

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **AWS CloudWatch** | Validate async flows and server-side logs |
| **DevTools (Network tab)** | Inspect requests and responses directly in the browser |
| **Postman** | Build and execute requests, manage environments, write assertions |
| **Swagger / OpenAPI** | Read endpoint documentation and validate contracts |
| **TablePlus / DBeaver** | Confirm API side effects in the database via SQL |
