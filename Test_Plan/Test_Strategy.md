# 🗂️ Test Strategy — E-Commerce Platform

**Version:** 1.0  
**Prepared by:** Paola Fermin — QA Specialist  
**Environment:** Staging → Production  
**Methodology:** Agile / Scrum

> 🔒 *This document is fictional and created for portfolio purposes. All names, platforms, and data are made up.*

---

## 1. Introduction & Scope

The platform under test is a web-based e-commerce application that allows users to browse products, manage a cart, place orders, and manage their account. The QA scope covers the full purchase funnel from product discovery to order confirmation, as well as account management and API integrations.

### In Scope
- Product catalog: search, filters, product detail pages
- Shopping cart: add, update, remove items
- Checkout: shipping, payment, order confirmation
- User authentication: registration, login, session management
- User profile: personal data, address book, order history
- REST API: all endpoints used by the frontend
- Responsive behavior: desktop and mobile resolutions
- Basic accessibility: WCAG 2.1 AA

### Out of Scope
- Payment gateway internal processing (third-party)
- Admin panel
- Performance and load testing
- Automated testing (current phase)

---

## 2. Priorities

| Priority | Area | Reason |
|---|---|---|
| 🔴 Critical | Checkout & payment flow | Direct business impact |
| 🔴 Critical | Authentication & session | Security and access control |
| 🟠 High | Cart management | Core user journey |
| 🟠 High | API endpoints | Frontend depends entirely on them |
| 🟡 Medium | Product catalog & filters | High traffic area |
| 🟡 Medium | Responsive behavior | Large mobile user base |
| 🟢 Low | Accessibility | Compliance and usability |

---

## 3. Testing Types

| Type | In Scope | Notes |
|---|---|---|
| Functional Testing | ✅ | Component and end-to-end |
| API Testing | ✅ | REST endpoints via Postman |
| Regression Testing | ✅ | Critical flows each sprint |
| Exploratory Testing | ✅ | 30-min sessions per feature |
| Responsive Testing | ✅ | Desktop + mobile resolutions |
| Accessibility Testing | ✅ | WCAG 2.1 AA basics |
| Visual Testing | ✅ | Design fidelity validation |
| Performance Testing | ❌ | Out of scope |
| Security Testing | ❌ | Out of scope |
| Automation | ❓ | Under consideration |

---

## 4. Target Platforms & Compatibility

### Desktop Resolutions (in scope)
| Resolution | Description |
|---|---|
| 1280×720 | Small laptop / HD |
| 1512×982 | MacBook Pro |
| 1920×1080 | Full HD / Large desktop |

### Mobile Devices (in scope)
| Device | Resolution |
|---|---|
| iPhone 12 | 390×844 CSS px |
| iPhone 16 Pro Max | 430×932 CSS px |
| Samsung S21 5G | 360×800 CSS px |

### Browsers (in scope)
- Chrome — latest version
- Safari — latest version
- Firefox — latest version

*Other browsers or legacy versions are out of scope unless otherwise requested.*

---

## 5. Test Environments

| Environment | Purpose |
|---|---|
| **Development (Dev)** | Active feature testing during sprint |
| **Staging (STG)** | Pre-release validation, regression runs |
| **Production (Prod)** | Controlled smoke testing post-deploy |

Production testing is controlled and coordinated with the team. Real user data is never used in test flows.

---

## 6. Sprint Structure

1 sprint = 2 weeks / 10 working days

| Days | QA Activities |
|---|---|
| Days 1–5 | Ticket review, requirement clarification, design review, test case design |
| Days 6–10 | Test execution, bug reporting, regression, exploratory testing |

Each sprint starts with Sprint Planning and closes with a test summary report delivered to the team.

---

## 7. Ticket Lifecycle

```
Backlog → Refinement → To Do → In Progress → Ready To Test (Dev)
→ Testing → Accepted (Dev) → Ready To Test (STG) → Accepted (STG) → Closed
```

**QA activities:**
- Early feedback and clarification during Refinement
- Test execution begins when ticket reaches *Ready To Test*
- Regression validation before STG sign-off
- Final verification in Production when applicable

**Definition of Closed:**
- Validated and accepted in Dev and STG
- No critical or high severity issues open
- Production smoke confirms feature works in real conditions

---

## 8. Risk Areas

| Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|
| Cart state lost on session change | Medium | High | Explicit test + session validation |
| Duplicate orders on payment retry | Low | Critical | Idempotency test + DB check |
| API returns stale data after update | Medium | High | Chain GET after PUT/PATCH |
| Mobile layout breaks on new viewport | Medium | Medium | BrowserStack regression each sprint |
| Checkout blocked by third-party downtime | Low | Critical | Mock fallback test + error message validation |

---

## 9. Tools

| Tool | Purpose |
|---|---|
| **Jira** | Sprint and ticket management |
| **Testmo** | Test case management and reporting |
| **Postman** | API testing — requests, environments, assertions |
| **BrowserStack** | Cross-browser and device compatibility |
| **TablePlus / DBeaver** | Backend data validation via SQL |
| **AWS CloudWatch** | Server-side log analysis |
| **DevTools** | Network inspection, console errors |
| **Figma** | Design reference for visual validation |

---

## 10. Deliverables

| Deliverable | When | Where |
|---|---|---|
| Test Scenarios Inventory | Maintained each sprint | Testmo |
| Sprint Test Report | End of each sprint | Shared with team |
| Bug Reports | As found during execution | Jira |
| Regression Suite | Updated each sprint | Testmo |
