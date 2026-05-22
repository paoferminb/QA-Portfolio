# 📊 QA Metrics Queries

Queries used to pull testing and defect data for sprint reports and retrospectives.

---

## 1. Count open bugs by severity

```sql
SELECT severity, COUNT(*) AS total
FROM bug_reports
WHERE status = 'open'
GROUP BY severity
ORDER BY severity;
```

---

## 2. Count bugs found per sprint

```sql
SELECT sprint, COUNT(*) AS bugs_found
FROM bug_reports
GROUP BY sprint
ORDER BY sprint;
```

---

## 3. Count bugs by area

```sql
SELECT area, COUNT(*) AS total
FROM bug_reports
WHERE sprint = 'Sprint_01'
GROUP BY area
ORDER BY total DESC;
```

**Use case:** Identify which feature area had the most defects in a sprint — helps prioritize testing focus for the next cycle.

---

## 4. List all open High and Critical bugs

```sql
SELECT id, title, area, severity, created_at
FROM bug_reports
WHERE status = 'open'
  AND severity IN ('critical', 'high')
ORDER BY severity, created_at;
```

---

## 5. Bug fix rate per sprint

```sql
SELECT sprint,
       COUNT(*) AS total_bugs,
       SUM(CASE WHEN status = 'closed' THEN 1 ELSE 0 END) AS fixed,
       SUM(CASE WHEN status = 'open' THEN 1 ELSE 0 END) AS open
FROM bug_reports
GROUP BY sprint
ORDER BY sprint;
```

---

## 6. Most affected products (bugs linked to a product)

Using INNER JOIN to connect bug reports with the products they affect.

```sql
SELECT p.name AS product_name, COUNT(b.id) AS bug_count
FROM bug_reports b
INNER JOIN products p ON b.product_id = p.id
GROUP BY p.name
ORDER BY bug_count DESC;
```

**Use case:** Spot which products or features accumulate the most defects over time.

---

## 7. Orders placed during a test run (data cleanup check)

```sql
SELECT id, customer_id, status, total, created_at
FROM orders
WHERE customer_id IN ('cust-test-01', 'cust-test-02')
  AND created_at >= '2026-05-05'
ORDER BY created_at DESC;
```

**Use case:** Identify test data created during a sprint to clean up the staging database after a test run.
