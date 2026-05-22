# 🚀 Release Checklist

Pre-release validation checklist. Run this before every deployment to staging or production to confirm quality gates are met.

---

## 🔐 Authentication & Access

- [ ] Login works for all roles: customer, admin
- [ ] Session timeout is enforced and handled gracefully
- [ ] Expired or invalid tokens return `401 Unauthorized`
- [ ] Unauthorized access to restricted resources returns `403 Forbidden`
- [ ] Password reset flow works end-to-end

---

## 🛒 Core Purchase Funnel

- [ ] Customer can search and find a product
- [ ] Product can be added to cart from listing and detail pages
- [ ] Cart updates correctly (quantity, remove, totals)
- [ ] Checkout completes with valid shipping and payment data
- [ ] Order confirmation page displays with correct order details
- [ ] Order appears in customer's order history immediately after placement

---

## 🔌 API Validation

- [ ] All new or modified endpoints return correct HTTP status codes
- [ ] Required field validation returns `400 Bad Request`
- [ ] Unauthorized requests return `401` or `403` as appropriate
- [ ] Response body contains all expected fields
- [ ] No sensitive data (passwords, tokens) exposed in responses

---

## 💾 Data Integrity

- [ ] New records created via API appear correctly in the database
- [ ] No duplicate records exist after repeated requests
- [ ] Deleted records are no longer retrievable via GET
- [ ] Timestamps (`created_at`, `updated_at`) are correct

---

## 📱 Responsive & Cross-Browser

- [ ] Core flows tested on Chrome and Safari latest
- [ ] No horizontal scroll on mobile viewports (360px, 390px, 430px)
- [ ] Forms and CTAs fully visible on mobile without zooming
- [ ] Hamburger menu works correctly on small screens

---

## ♿ Accessibility Baseline

- [ ] All form inputs have associated labels
- [ ] Product images have descriptive alt text
- [ ] Key flows are completable using keyboard only
- [ ] No information conveyed by color alone

---

## 🚦 Go / No-Go

| Gate | Status |
|---|---|
| All Critical test cases passed | ⬜ |
| Zero open Critical bugs | ⬜ |
| High bugs fixed or accepted with team sign-off | ⬜ |
| Core purchase funnel validated end-to-end | ⬜ |
| API responses verified | ⬜ |
| DB integrity checks passed | ⬜ |
| Responsive baseline confirmed | ⬜ |

> ✅ **GO** — All gates met. Safe to release.  
> ❌ **NO-GO** — One or more gates failed. Release blocked.
