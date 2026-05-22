# 📊 Sprint 01 — Test Report

**Project:** E-Commerce Platform  
**Sprint:** 01 — Pre-Launch Validation  
**Sprint dates:** 2026-04-21 → 2026-05-02  
**Report date:** 2026-05-02  
**Prepared by:** Paola Fermin — QA Specialist  
**Environment:** Staging (STG)  
**Build:** v0.9.1

> 🔒 *Fictional report created for portfolio purposes.*

---

## 1. Sprint Summary

This sprint covered the first full regression cycle prior to the platform's initial launch. All core features were tested: authentication, product catalog, shopping cart, checkout, user profile, and REST API endpoints. Responsive and accessibility testing were also included.

---

## 2. Execution Metrics

### Overall

| Metric | Value |
|---|---|
| Total test cases executed | 72 |
| ✅ Passed | 55 |
| ❌ Failed | 12 |
| ⚠️ Blocked | 5 |
| Pass rate | **76.4%** |
| Fail rate | 16.7% |
| Blocked rate | 6.9% |

### By Type

| Type | Total | ✅ Pass | ❌ Fail | ⚠️ Blocked |
|---|---|---|---|---|
| Functional | 36 | 30 | 5 | 1 |
| API | 24 | 19 | 4 | 1 |
| Responsive | 12 | 6 | 3 | 3 |

---

## 3. Results by Area

| Area | TCs | ✅ | ❌ | ⚠️ | Status |
|---|---|---|---|---|---|
| Authentication | 8 | 7 | 0 | 1 | 🟡 Attention |
| Product Catalog | 7 | 6 | 1 | 0 | 🟡 Attention |
| Shopping Cart | 7 | 5 | 1 | 1 | 🟡 Attention |
| Checkout | 8 | 7 | 1 | 0 | 🟡 Attention |
| User Profile | 6 | 5 | 1 | 0 | 🟡 Attention |
| Accessibility | 8 | 5 | 2 | 1 | 🔴 Risk |
| UI Elements | 11 | 9 | 1 | 1 | 🟡 Attention |
| Responsive | 12 | 6 | 3 | 3 | 🔴 Risk |
| API — GET | 5 | 4 | 1 | 0 | 🟡 Attention |
| API — POST | 5 | 4 | 1 | 0 | 🟡 Attention |
| API — PATCH | 5 | 3 | 2 | 0 | 🔴 Risk |
| API — PUT | 5 | 4 | 1 | 0 | 🟡 Attention |
| API — DELETE | 5 | 5 | 0 | 0 | ✅ Pass |
| **Total** | **72** | **55** | **12** | **5** | |

**Legend:** ✅ All pass · 🟡 Minor issues · 🔴 Risk area

---

## 4. Bugs Found

| ID | Title | Area | Severity | Status |
|---|---|---|---|---|
| BUG-001 | Empty form fields submit without validation on register | Authentication | 🟠 High | Open |
| BUG-002 | Duplicate line items when adding same product twice to cart | Shopping Cart | 🟠 High | Open |
| BUG-003 | Product listing overflows viewport at 360px (horizontal scroll) | Responsive | 🟠 High | Open |
| BUG-004 | Filter panel apply button hidden behind keyboard on mobile | Responsive | 🟠 High | Open |
| BUG-005 | Cart cleared after login redirect from checkout | Checkout | 🔴 Critical | Open |
| BUG-006 | Profile saved with empty name field — no validation | User Profile | 🟠 High | Open |
| BUG-007 | Combination of category + price filter not applied correctly | Product Catalog | 🟠 High | Open |
| BUG-008 | PATCH /orders — empty body `{}` returns 200 OK instead of 400 | API — PATCH | 🟠 High | Open |
| BUG-009 | PATCH /products — price set to 0 accepted without error | API — PATCH | 🟠 High | Open |
| BUG-010 | GET /products — page beyond total returns 404 instead of empty array | API — GET | 🟡 Medium | Open |
| BUG-011 | Out-of-stock badge uses color only, no text or icon (a11y) | Accessibility | 🟡 Medium | Open |
| BUG-012 | Alt text missing on several product images | Accessibility | 🟡 Medium | Open |

**Summary:**

| Severity | Count |
|---|---|
| 🔴 Critical | 1 |
| 🟠 High | 8 |
| 🟡 Medium | 3 |
| 🟢 Low | 0 |

---

## 5. Key Findings

### 🔴 Critical — Cart loss on login redirect
Users who reach checkout without being logged in are redirected to login, but the cart is cleared after authentication. This directly breaks the purchase funnel and must be resolved before launch.

### 🟠 Input validation gaps
Multiple forms (registration, profile) accept empty required fields without triggering validation. This points to a systemic gap in frontend validation — not isolated to one screen.

### 🟠 API contract issues on PATCH
Two PATCH endpoints (`/orders` and `/products`) accept invalid inputs — empty body and price of zero — without returning an error. This suggests missing server-side validation that could lead to data inconsistencies.

### 📱 Responsive testing at 360px is a risk area
The smallest mobile resolution (Samsung S21 5G at 360px) shows layout issues in two critical areas: product listing overflow and registration button hidden. With mobile traffic expected to be significant, these need to be addressed pre-launch.

### ♿ Accessibility baseline not fully met
Color-only status indicators and missing alt text are foundational WCAG 2.1 AA failures. These are low-effort fixes but high-impact for users with visual impairments.

---

## 6. Blocked Items

| TC | Reason |
|---|---|
| AUTH-08 — Session persistence | Session config under review by dev team |
| CART-07 — Cart persistence after refresh | Depends on AUTH-08 session fix |
| RES-11 — Checkout form on mobile keyboard | Needs physical device confirmation |
| RES-16 — Tap target size | Min size not defined in design spec |
| A11Y-06 — Error messages announced by screen reader | NVDA version mismatch in test environment |

---

## 7. Release Recommendation

| Gate | Status |
|---|---|
| All Critical TCs passed | ❌ — BUG-005 open |
| Zero open Critical bugs | ❌ — 1 Critical open |
| High bugs fixed or accepted | ❌ — 8 High open |
| API contract validated | ❌ — 2 High issues in PATCH |
| Responsive baseline met | ❌ — 360px issues unresolved |

### ⚠️ Conditional GO

The platform is **not ready for launch** in its current state. The critical cart loss bug (BUG-005) alone blocks the release. Once BUG-005 and the High severity responsive issues are resolved, a targeted re-test is recommended before proceeding.

**Minimum required before launch:**
- BUG-005 fixed and re-tested ✅
- BUG-003 and BUG-004 resolved or accepted with sign-off ✅
- BUG-002 (duplicate cart items) fixed ✅

---

*Report prepared by Paola Fermin · QA Specialist · Sprint 01*
