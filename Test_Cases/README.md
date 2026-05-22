# 🧪 Test Cases

Functional test cases for the web platform, organized by feature area. All tests were executed manually on staging environment.

---

## 📁 Structure

```text
Test_Cases/
├── Accessibility.md        keyboard navigation, screen reader, color contrast
├── Authentication.md       login, registration, session handling
├── Checkout.md             order placement, shipping, payment
├── Product_Catalog.md      search, filters, product detail
├── Responsive.md           Responsive across devices
├── Shopping_Cart.md        add, remove, quantity updates
├── UI_Elements.md          buttons, forms, layout, notifications
└── User_Profile.md         profile edits, password, addresses
```

---

## 📂 Explore

| File | Description |
|---|---|
| [Accessibility.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Accessibility.md) | Keyboard nav, screen reader, color contrast |
| [Authentication.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Authentication.md) | Login, registration, session handling |
| [Checkout.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Checkout.md) | Order placement, shipping, payment |
| [Product_Catalog.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Product_Catalog.md) | Search, filters, product detail |
| [Responsive.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Responsive.md) | Responsive across devices|
| [Shopping_Cart.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/Shopping_Cart.md) | Add, remove, quantity updates |
| [UI_Elements.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/UI_Elements.md) | Buttons, forms, layout, notifications |
| [User_Profile.md](https://github.com/paoferminb/QA-Portfolio/blob/main/Test_Cases/User_Profile.md) | Profile edits, password, addresses |

---

## 📋 Test Case Format

| Column | Description |
|---|---|
| **ID** | Unique identifier per feature (e.g. `AUTH-01`) |
| **Scenario** | What is being tested |
| **Steps** | Numbered actions to reproduce |
| **Expected Result** | What should happen |
| **Actual Result** | ✅ Pass / ❌ Fail / ⚠️ Blocked |

---

## 📊 Coverage Summary

| File | TCs | Fails | Blocked |
|---|---|---|---|
| Accessibility.md | 8 | 3 | 1 |
| Authentication.md | 8 | 1 | 1 |
| Checkout.md | 8 | 1 | 0 |
| Product_Catalog.md | 7 | 1 | 0 |
| Shopping_Cart.md | 7 | 1 | 1 |
| UI_Elements.md | 11 | 2 | 1 |
| User_Profile.md | 6 | 1 | 0 |
| **Total** | **55** | **10** | **4** |

---

## 🛠️ Tools & Environment

| Item | Detail |
|---|---|
| **Test management** | Testmo / TestRail |
| **Bug tracking** | Jira |
| **Browsers** | Chrome 124, Firefox 125, Safari 17 |
| **Cross-device** | BrowserStack (iOS 17, Android 14) |
| **Accessibility** | NVDA screen reader, DevTools accessibility panel |
| **Environment** | Staging |

