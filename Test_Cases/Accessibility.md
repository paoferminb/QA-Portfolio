# ♿ Accessibility

**Feature:** Basic accessibility compliance (WCAG 2.1 AA)  
**Environment:** Staging | Chrome 124 + screen reader (NVDA)  
**Tested by:** Paola Fermin

---

## 1. Keyboard Navigation

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| A11Y-01 | Tab through interactive elements | 1. Open the home page <br> 2. Press Tab repeatedly | Focus moves through all interactive elements (links, buttons, inputs) in logical order; focus is always visible | ✅ Pass |
| A11Y-02 | Submit form using keyboard only | 1. Go to Login page <br> 2. Tab to the email field, type email <br> 3. Tab to password field, type password <br> 4. Press Tab to reach "Log in" button <br> 5. Press Enter | Form submits successfully without using the mouse | ✅ Pass |
| A11Y-03 | Escape closes modal | 1. Open a modal (e.g. product quick view) <br> 2. Press Escape | Modal closes; focus returns to the element that opened it | ❌ Fail — modal closes but focus moves to top of page |

---

## 2. Screen Reader

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| A11Y-04 | Images have descriptive alt text | 1. Inspect product images using browser DevTools <br> 2. Check `alt` attribute on all `<img>` tags | All product images have meaningful alt text (not empty or "image") | ❌ Fail — several product images have `alt=""` |
| A11Y-05 | Form fields have associated labels | 1. Inspect form inputs on Login and Register pages <br> 2. Check that each `<input>` has a linked `<label>` or `aria-label` | Every input is properly labeled and announced by screen reader | ✅ Pass |
| A11Y-06 | Error messages are announced | 1. Submit a form with invalid data <br> 2. Listen with screen reader (NVDA) | Error message is announced immediately after form submission | ⚠️ Blocked — NVDA version mismatch in test environment |

---

## 3. Color & Contrast

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| A11Y-07 | Text contrast ratio meets WCAG AA | 1. Use browser DevTools accessibility panel <br> 2. Check contrast ratio on body text and buttons | Contrast ratio ≥ 4.5:1 for normal text; ≥ 3:1 for large text | ✅ Pass |
| A11Y-08 | Information not conveyed by color alone | 1. Identify UI elements that use color to convey status (e.g. form errors, stock badges) <br> 2. Check if a secondary indicator exists | Error states use both red color AND an icon or label — not color alone | ❌ Fail — out-of-stock badge uses color only, no text or icon |
