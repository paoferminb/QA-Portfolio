# 🔄 Regression Test Plan — E-Commerce Platform

**Version:** 1.0  
**Prepared by:** Paola Fermin — QA Specialist  
**Triggered by:** End of sprint / pre-release to STG or Production  
**Scope:** Critical business flows

> 🔒 *This document is fictional and created for portfolio purposes.*

---

## Table of Contents

- [🔄 Regression Test Plan — E-Commerce Platform](#-regression-test-plan--e-commerce-platform)
  - [1. Objective](#1-objective)
  - [2. Entry Criteria](#2-entry-criteria)
  - [3. Exit Criteria](#3-exit-criteria)
  - [4. Regression Scope](#4-regression-scope)
    - [🔴 Critical Flows — Always Run](#-critical-flows--always-run)
      - [AUTH — Authentication](#auth--authentication)
      - [CART — Shopping Cart](#cart--shopping-cart)
      - [CHK — Checkout](#chk--checkout)
      - [API — Critical Endpoints](#api--critical-endpoints)
    - [🟠 High Priority Flows — Run on Impacted Areas](#-high-priority-flows--run-on-impacted-areas)
      - [PROD — Product Catalog](#prod--product-catalog)
      - [PRF — User Profile](#prf--user-profile)
      - [API — High Priority Endpoints](#api--high-priority-endpoints)
    - [🟡 Spot Check — Run When Relevant Changes Detected](#-spot-check--run-when-relevant-changes-detected)
  - [5. Test Execution](#5-test-execution)
  - [6. Bug Severity Classification](#6-bug-severity-classification)
  - [7. Regression Report Template](#7-regression-report-template)

## 1. Objective

Ensure that new changes introduced during the sprint do not break previously validated functionality. Regression is executed before every release to Staging and Production.

---

## 2. Entry Criteria

- All sprint tickets have reached *Accepted (Dev)*
- No open Critical or High severity bugs in the current sprint
- Test environment is stable and seeded with valid test data
- Build has been deployed to STG

---

## 3. Exit Criteria

- 100% of Critical flow test cases executed
- Zero open Critical bugs
- High severity bugs reviewed and accepted by the team or fixed
- Test report delivered before release sign-off

---

## 4. Regression Scope

### 🔴 Critical Flows — Always Run

These flows are executed every regression cycle without exception.

#### AUTH — Authentication
| TC | Scenario |
|---|---|
| AUTH-01 | Register with valid data |
| AUTH-05 | Login with valid credentials |
| AUTH-06 | Login with wrong password returns error |

#### CART — Shopping Cart
| TC | Scenario |
|---|---|
| CART-01 | Add product to cart |
| CART-04 | Increase product quantity |
| CART-06 | Remove product manually |

#### CHK — Checkout
| TC | Scenario |
|---|---|
| CHK-01 | Complete checkout with valid data |
| CHK-06 | Pay with valid test card |
| CHK-07 | Pay with declined card returns error |
| CHK-08 | Order appears in order history after purchase |

#### API — Critical Endpoints
| TC | Scenario |
|---|---|
| GET-01 | GET /products returns paginated list |
| POST-01 | POST /orders creates order successfully |
| DELETE-03 | DELETE /orders cancels pending order |
| PATCH-03 | PATCH /orders updates status correctly |

---

### 🟠 High Priority Flows — Run on Impacted Areas

Run when related areas have been modified during the sprint.

#### PROD — Product Catalog
| TC | Scenario | Trigger |
|---|---|---|
| PROD-01 | Search for existing product | Search or catalog changes |
| PROD-04 | Filter by category | Filter logic changes |
| PROD-07 | View product detail page | Product page changes |

#### PRF — User Profile
| TC | Scenario | Trigger |
|---|---|---|
| PRF-01 | Update display name | Profile or account changes |
| PRF-04 | Change password successfully | Auth or security changes |
| PRF-06 | Add new shipping address | Address or checkout changes |

#### API — High Priority Endpoints
| TC | Scenario | Trigger |
|---|---|---|
| GET-02 | GET /orders/:id returns correct order | Order changes |
| POST-02 | POST /users/register creates user | Auth changes |
| PUT-03 | PUT /orders/:id/shipping replaces address | Shipping changes |

---

### 🟡 Spot Check — Run When Relevant Changes Detected

| Area | Scenarios to spot check |
|---|---|
| UI Elements | Button states, form validation, toast notifications |
| Accessibility | Keyboard navigation, alt text on new images |
| Responsive | Checkout and cart on mobile viewports |

---

## 5. Test Execution

| Step | Detail |
|---|---|
| **Environment** | Staging (STG) |
| **Devices** | Chrome desktop + iPhone 12 (BrowserStack) |
| **Data** | Pre-seeded test accounts and products |
| **API validation** | Postman collection run against STG base URL |
| **DB spot check** | SQL queries to verify order and user records |
| **Duration** | ~4 hours for full critical suite |

---

## 6. Bug Severity Classification

| Severity | Definition | Action |
|---|---|---|
| 🔴 Critical | Blocks core user journey (can't checkout, can't login) | Block release |
| 🟠 High | Major feature broken, workaround exists | Fix before release or get sign-off |
| 🟡 Medium | Minor functional issue, low user impact | Log for next sprint |
| 🟢 Low | Cosmetic or edge case | Backlog |

---

## 7. Regression Report Template

At the end of each regression cycle, a summary is shared with the team:

```
Sprint: [Sprint number]
Date: [Date]
Environment: STG

Total TCs executed: X
  ✅ Pass: X
  ❌ Fail: X
  ⚠️ Blocked: X

Critical bugs found: X
High bugs found: X

Release recommendation: ✅ GO / ❌ NO-GO
Notes: [Any relevant observations]
```
