# 📊 Sprint 02 — Test Report

**Project:** E-Commerce Platform  
**Sprint:** 02 — Post-Launch Iteration  
**Sprint dates:** 2026-05-05 → 2026-05-16  
**Report date:** 2026-05-16  
**Prepared by:** Paola Fermin — QA Specialist  
**Environment:** Staging (STG) → Production (Prod)  
**Build:** v1.0.2

> 🔒 *Fictional report created for portfolio purposes.*

---

## 1. Sprint Summary

Sprint 02 focused on validating fixes for all bugs found in Sprint 01, plus two new features: discount code application on checkout and product reviews. A targeted regression was executed on the areas impacted by fixes, followed by a controlled smoke test in Production after deployment.

**New features tested this sprint:**
- `POST /orders/:id/discount` — apply discount code
- `POST /products/:id/reviews` — submit product review

---

## 2. Execution Metrics

### Overall

| Metric | Value |
|---|---|
| Total test cases executed | 48 |
| ✅ Passed | 44 |
| ❌ Failed | 2 |
| ⚠️ Blocked | 2 |
| Pass rate | **91.7%** |
| Fail rate | 4.2% |
| Blocked rate | 4.2% |

### By Type

| Type | Total | ✅ Pass | ❌ Fail | ⚠️ Blocked |
|---|---|---|---|---|
| Regression (bug re-test) | 12 | 11 | 1 | 0 |
| New features | 16 | 14 | 1 | 1 |
| Responsive (targeted) | 8 | 7 | 0 | 1 |
| Production smoke | 12 | 12 | 0 | 0 |

---

## 3. Bug Re-Test Results

| Bug | Title | Result | Notes |
|---|---|---|---|
| BUG-001 | Empty form fields submit without validation | ✅ Fixed | Validation now triggers on all required fields |
| BUG-002 | Duplicate line items in cart | ✅ Fixed | Same product now updates quantity correctly |
| BUG-003 | Product listing overflows at 360px | ✅ Fixed | Horizontal scroll eliminated |
| BUG-004 | Filter apply button hidden on mobile | ✅ Fixed | Filter now opens as full-screen drawer |
| BUG-005 | Cart cleared after login redirect | ✅ Fixed | Cart persists through authentication |
| BUG-006 | Profile saved with empty name | ✅ Fixed | Validation added; empty name blocked |
| BUG-007 | Category + price filter combination | ❌ Still failing | Fix attempted but issue persists |
| BUG-008 | PATCH /orders empty body returns 200 | ✅ Fixed | Now returns 400 as expected |
| BUG-009 | PATCH /products price 0 accepted | ✅ Fixed | Now returns 422 |
| BUG-010 | GET /products out-of-range page returns 404 | ✅ Fixed | Now returns 200 with empty array |
| BUG-011 | Out-of-stock badge color only | ✅ Fixed | Badge now includes text label "Out of stock" |
| BUG-012 | Missing alt text on product images | ✅ Fixed | All product images have descriptive alt text |

**Fix rate: 11/12 (91.7%)**

---

## 4. Results by Area

| Area | TCs | ✅ | ❌ | ⚠️ | Status |
|---|---|---|---|---|---|
| Bug re-test — Auth & Forms | 4 | 4 | 0 | 0 | ✅ Resolved |
| Bug re-test — Cart & Checkout | 3 | 3 | 0 | 0 | ✅ Resolved |
| Bug re-test — API PATCH | 2 | 2 | 0 | 0 | ✅ Resolved |
| Bug re-test — Filters | 1 | 0 | 1 | 0 | 🔴 Persists |
| Bug re-test — Accessibility | 2 | 2 | 0 | 0 | ✅ Resolved |
| New feature — Discount codes | 6 | 5 | 1 | 0 | 🟡 Attention |
| New feature — Product reviews | 10 | 9 | 0 | 1 | 🟡 Attention |
| Responsive — targeted re-test | 8 | 7 | 0 | 1 | 🟡 Attention |
| Production smoke | 12 | 12 | 0 | 0 | ✅ Pass |
| **Total** | **48** | **44** | **2** | **2** | |

---

## 5. Bugs Found This Sprint

| ID | Title | Area | Severity | Status |
|---|---|---|---|---|
| BUG-007 | Category + price filter combination still not applied | Product Catalog | 🟠 High | Open — carried over |
| BUG-013 | Discount code accepted on already-delivered orders | Checkout — Discount | 🟠 High | Open |

**Summary:**

| Severity | Count |
|---|---|
| 🔴 Critical | 0 |
| 🟠 High | 2 |
| 🟡 Medium | 0 |
| 🟢 Low | 0 |

---

## 6. Key Findings

### ✅ Strong sprint recovery
11 out of 12 bugs from Sprint 01 were resolved and verified. The critical cart loss bug (BUG-005) was confirmed fixed — the core purchase funnel is now stable end-to-end.

### 🟠 BUG-007 persists — filter logic needs deeper investigation
The combined category + price filter has been attempted twice without success. This points to a logic issue in how filters are composed on the frontend, likely needing a deeper dev investigation rather than a surface fix.

### 🟠 Discount code missing order state validation
BUG-013 found during new feature testing: a discount code can be applied to an already-delivered order. This is a business logic gap — discount application should be blocked once the order is in a final state.

### 🚀 Production smoke — all clear
All 12 smoke test cases passed in Production. Core flows (login, add to cart, checkout, order confirmation) work correctly in the live environment with real infrastructure.

### ⚠️ Blocked — tap target spec still undefined
RES-16 remains blocked because the design spec has not defined a minimum tap target size. This should be agreed upon by the team and added to the design system to unblock testing.

---

## 7. Blocked Items

| TC | Reason | Owner |
|---|---|---|
| RES-16 — Tap target size | Min size not defined in design spec | Design team |
| Review auth — customer purchase validation | Purchase history check not yet implemented in STG | Dev team |

---

## 8. Release Recommendation

| Gate | Status |
|---|---|
| All Critical TCs passed | ✅ |
| Zero open Critical bugs | ✅ |
| High bugs fixed or accepted with sign-off | ✅ BUG-007 accepted; BUG-013 logged for Sprint 03 |
| Production smoke passed | ✅ |
| Core purchase funnel validated | ✅ |

### ✅ GO

The platform is stable and ready for continued operation. The two open High bugs are understood and accepted by the team for the next sprint. No Critical issues remain.

**Recommended for Sprint 03:**
- Investigate BUG-007 (filter logic) with a dedicated dev session
- Fix BUG-013 (discount on delivered orders)
- Unblock RES-16 by aligning on tap target spec with design

---

*Report prepared by Paola Fermin · QA Specialist · Sprint 02*
