# 🔍 Data Validation Queries

Queries used to confirm that API calls created, updated, or deleted the correct records in the database.

---

## 1. Verify a new order was created

After `POST /orders`, confirm the record exists with the correct values.

```sql
SELECT *
FROM orders
WHERE customer_id = 'cust-88'
ORDER BY created_at DESC
LIMIT 5;
```

**What to check:**
- `status` = `pending`
- `total` matches the expected amount
- `created_at` is recent (within the last few minutes)

---

## 2. Verify order items were saved correctly

```sql
SELECT *
FROM order_items
WHERE order_id = 'ord-1043';
```

**What to check:**
- Each product in the request appears as a row
- `quantity` and `price` match what was sent in the request

---

## 3. Verify a user was registered

After `POST /users/register`, confirm the account exists.

```sql
SELECT id, name, email, role, created_at
FROM users
WHERE email = 'laura@example.com';
```

**What to check:**
- Record exists with correct `name`, `email`, and `role`
- `password` column is NOT selected — never expose it in logs or reports

---

## 4. Verify a product was updated

After `PUT /products/prod-001`, confirm all fields were replaced.

```sql
SELECT *
FROM products
WHERE id = 'prod-001';
```

**What to check:**
- All fields match the payload sent in the request
- `updated_at` is more recent than `created_at`

---

## 5. Verify a record was deleted

After `DELETE /orders/ord-1043`, confirm the record no longer exists.

```sql
SELECT *
FROM orders
WHERE id = 'ord-1043';
```

**What to check:**
- Query returns 0 rows
- If soft delete is used, check `deleted_at` is not null instead

---

## 6. Verify stock was decremented after order

```sql
SELECT id, name, stock
FROM products
WHERE id = 'prod-001';
```

**What to check:**
- `stock` decreased by the quantity ordered
- Run this before and after placing the order to compare

---

## 7. Verify order status was updated

After `PATCH /orders/ord-1042` with `status: shipped`.

```sql
SELECT id, status, updated_at
FROM orders
WHERE id = 'ord-1042';
```

**What to check:**
- `status` = `shipped`
- `updated_at` reflects the time of the API call
