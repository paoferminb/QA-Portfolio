# 🧪 Test Cases

Functional test cases organized by platform and feature area.

## Structure

```
Test_Cases/
└── Web/                  web platform test cases
    ├── Authentication/
    ├── Product_Catalog/
    ├── Shopping_Cart/
    ├── Checkout/
    ├── User_Profile/
    ├── UI_Elements/
    └── Accessibility/
```

## Test Case Format

| Column | Description |
|---|---|
| **ID** | Unique identifier per feature (e.g. `AUTH-01`) |
| **Scenario** | What is being tested |
| **Steps** | Numbered actions to reproduce |
| **Expected Result** | What should happen |
| **Actual Result** | ✅ Pass / ❌ Fail / ⚠️ Blocked |

## Tools & Environment

| Item | Detail |
|---|---|
| **Test management** | Testmo / TestRail / Xray|
| **Bug tracking** | Jira / ClickUp |
| **Browsers** | Chrome 124, Firefox 125, Safari 17 |
| **Cross-device** | BrowserStack (iOS 17, Android 14) |
| **Accessibility** | NVDA screen reader, DevTools accessibility panel |
| **Environment** | Staging |

## Coverage Summary

| Folder | TCs | Fails | Blocked |
|---|---|---|---|
| Authentication | 8 | 1 | 1 |
| Product_Catalog | 7 | 1 | 0 |
| Shopping_Cart | 7 | 1 | 1 |
| Checkout | 8 | 1 | 0 |
| User_Profile | 6 | 1 | 0 |
| UI_Elements | 11 | 2 | 1 |
| Accessibility | 8 | 3 | 1 |
| **Total** | **55** | **10** | **4** |

