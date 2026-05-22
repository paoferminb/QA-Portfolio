# 🐛 Bug Investigation Queries

Queries used to confirm bugs at the database level and gather evidence for bug reports.

---

## BUG-002 — Duplicate line items in cart

Check if the same product appears more than once in a single order.

```sql
SELECT order_id, product_id, COUNT(*) AS occurrences
FROM order_items
GROUP BY order_id, product_id
HAVING COUNT(*) > 1;
```

**Evidence:** Query returned rows — confirmed duplicate line items exist for the same product in a single order.

---

## BUG-005 — Cart cleared after login redirect

Check if orders or cart sessions are being lost for a specific customer.

```sql
SELECT *
FROM cart_sessions
WHERE customer_id = 'cust-88'
ORDER BY created_at DESC;
```

**What to check:**
- No active cart session exists after the customer logged in
- Session `expires_at` is in the past or the row was deleted

---

## BUG-006 — Profile saved with empty name

Check if any users have an empty or null name in the database.

```sql
SELECT id, name, email, created_at
FROM users
WHERE name = '' OR name IS NULL;
```

**Evidence:** Query returned 1 row — confirmed a user account exists with an empty name field.

---

## BUG-007 — Combined filters not working

Check that products in the electronics category are within the expected price range to rule out a data issue.

```sql
SELECT id, name, category, price
FROM products
WHERE category = 'electronics'
  AND price BETWEEN 20 AND 60
ORDER BY price ASC;
```

**What to check:**
- Products exist in this range (rules out empty data as the cause)
- If the API returns different results, the issue is in the filter logic, not the data

---

## BUG-009 — Price set to 0 accepted by API

Check if any products have a price of 0 or less in the database.

```sql
SELECT id, name, price, updated_at
FROM products
WHERE price <= 0;
```

**Evidence:** Query returned 1 row — `prod-001` had `price = 0` after the PATCH call, confirming the API accepted an invalid value.

---

## BUG-013 — Discount applied to delivered order

Check if any discount codes were applied to orders that are already in a final state.

```sql
SELECT o.id AS order_id, o.status, d.code, d.applied_at
FROM orders o
INNER JOIN discounts d ON d.order_id = o.id
WHERE o.status IN ('delivered', 'cancelled');
```

**Evidence:** Query returned rows — discount codes were successfully applied to delivered orders, confirming the missing state validation.

---

## General — Check timestamps make sense

Useful when investigating data inconsistencies or race conditions.

```sql
SELECT id, status, created_at, updated_at
FROM orders
WHERE updated_at < created_at;
```

**What to check:**
- No rows should be returned — `updated_at` should never be earlier than `created_at`
