# 🎨 UI Elements

**Feature:** Visual consistency and interactive component behavior  
**Environment:** Staging | Chrome 124, Firefox 125  
**Tested by:** Paola Fermin

---

## 1. Buttons

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| UI-01 | Primary button hover state | 1. Go to any page with a primary button <br> 2. Hover over the button | Button changes to hover style (color/shadow shift) as per design spec | ✅ Pass |
| UI-02 | Disabled button is not clickable | 1. Find a disabled button (e.g. "Add to cart" on out-of-stock product) <br> 2. Click it | Nothing happens; cursor shows not-allowed; no action triggered | ✅ Pass |
| UI-03 | Loading state on form submit | 1. Fill in a form (e.g. checkout) <br> 2. Click submit button | Button shows loading spinner and becomes disabled while request is in progress | ❌ Fail — button remains active during request; can be clicked multiple times |

---

## 2. Forms

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| UI-04 | Required field inline error | 1. Go to any form with required fields <br> 2. Leave a required field empty <br> 3. Click submit | Inline error appears below the field; field border turns red | ✅ Pass |
| UI-05 | Input field character limit | 1. Go to a field with a max length (e.g. name field) <br> 2. Paste text exceeding the limit | Input is truncated at max character count; no crash or silent overflow | ⚠️ Blocked — max length not defined in current spec |
| UI-06 | Dropdown opens and selects correctly | 1. Click on a dropdown (e.g. country selector) <br> 2. Select an option | Dropdown opens with full list; selected option appears in the field; dropdown closes | ✅ Pass |

---

## 3. Navigation & Layout

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| UI-07 | Active nav item is highlighted | 1. Navigate to different pages (Home, Products, Cart) <br> 2. Observe the navigation bar | Current page link is visually highlighted (bold or underline) | ✅ Pass |
| UI-08 | Mobile hamburger menu opens | 1. Open the app on a mobile viewport (< 768px) <br> 2. Click the hamburger icon | Navigation menu slides in; all links are accessible | ✅ Pass |
| UI-09 | Page layout on tablet viewport | 1. Resize browser to tablet width (~768px) <br> 2. Browse product listing page | Layout adapts to 2-column grid; no overflow or broken elements | ❌ Fail — product cards overflow container at 768px width |

---

## 4. Feedback & Notifications

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| UI-10 | Success toast appears after action | 1. Add a product to cart | Toast notification appears: "Item added to your cart" and disappears after 3 seconds | ✅ Pass |
| UI-11 | Error state displayed on failed request | 1. Simulate a failed API call (e.g. disconnect network) <br> 2. Try to load the product listing | Error message shown on page: "Something went wrong. Please try again." | ✅ Pass |
