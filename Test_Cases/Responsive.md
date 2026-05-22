# 📱 Responsive Testing

**Feature:** Responsive behavior across devices and resolutions  
**Environment:** Staging | BrowserStack  
**Tested by:** Paola Fermin

---

## Devices & Resolutions Tested

| Device | Resolution | Type |
|---|---|---|
| Desktop — Full HD | 1920×1080 | Desktop |
| Desktop — MacBook Pro | 1512×982 | Desktop |
| Desktop — Small laptop | 1280×720 | Desktop |
| iPhone 16 Pro Max | 430×932 CSS px | Mobile iOS |
| iPhone 12 | 390×844 CSS px | Mobile iOS |
| Samsung S21 5G | 360×800 CSS px | Mobile Android |

---

## 1. Navigation & Layout

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-01 | Hamburger menu appears on mobile | 1. Open the site on iPhone 12 (390px) <br> 2. Observe the navigation bar | Desktop nav is hidden; hamburger icon is visible and tappable | ✅ Pass |
| RES-02 | Hamburger menu opens and all links are accessible | 1. Open on iPhone 12 <br> 2. Tap the hamburger icon <br> 3. Tap each nav link | Menu slides open; all links are reachable and functional | ✅ Pass |
| RES-03 | No horizontal scroll on any mobile resolution | 1. Open each main page on 360px, 390px, and 430px <br> 2. Scroll horizontally | No horizontal overflow; content stays within viewport | ❌ Fail — product listing page overflows at 360px |
| RES-04 | Footer renders correctly on mobile | 1. Open the site on Samsung S21 5G <br> 2. Scroll to the bottom | Footer columns stack vertically; links are tappable; no overlap | ✅ Pass |
| RES-05 | Layout adapts correctly at 1280×720 | 1. Open product listing on small laptop resolution <br> 2. Observe grid layout | Product grid shows 3 columns; no broken elements | ✅ Pass |

---

## 2. Product Catalog

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-06 | Product cards display correctly on mobile | 1. Open product listing on iPhone 12 <br> 2. Scroll through the catalog | Cards display in single column; image, name, and price are visible without truncation | ✅ Pass |
| RES-07 | Filter panel is accessible on mobile | 1. Open product listing on iPhone 12 <br> 2. Tap the filter button | Filter panel opens as a drawer or modal; options are selectable; apply button is visible | ❌ Fail — apply button is hidden behind keyboard on small screens |
| RES-08 | Product detail page renders on mobile | 1. Tap a product on iPhone 16 Pro Max <br> 2. Observe the detail page | Product image, name, price, description, and "Add to cart" button are all visible without scrolling past the fold | ✅ Pass |

---

## 3. Shopping Cart

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-09 | Cart page is usable on mobile | 1. Add a product and go to cart on Samsung S21 5G <br> 2. Interact with quantity controls and remove button | All controls are tappable; quantity updates correctly; layout doesn't break | ✅ Pass |
| RES-10 | Cart icon shows correct item count on all resolutions | 1. Add 2 products <br> 2. Check cart icon on 360px, 1280px, and 1920px | Badge with item count is visible at all resolutions | ✅ Pass |

---

## 4. Checkout

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-11 | Checkout form is usable on mobile | 1. Go to checkout on iPhone 12 <br> 2. Fill in shipping and payment fields using mobile keyboard | Fields are reachable; keyboard doesn't cover active input; no fields hidden behind virtual keyboard | ⚠️ Blocked — keyboard behavior varies by device; needs physical device confirmation |
| RES-12 | "Place order" button is always visible on mobile | 1. Go to checkout on Samsung S21 5G <br> 2. Fill in the form | CTA button is visible without zooming or horizontal scroll | ✅ Pass |
| RES-13 | Order confirmation page renders on mobile | 1. Complete checkout on iPhone 16 Pro Max <br> 2. Observe confirmation page | Order ID, summary, and "Continue shopping" button are all visible and correctly stacked | ✅ Pass |

---

## 5. Authentication

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-14 | Login form is usable on mobile | 1. Open login page on iPhone 12 <br> 2. Tap email field, type, then move to password <br> 3. Tap "Log in" | Fields are accessible; keyboard doesn't obscure the submit button; form submits correctly | ✅ Pass |
| RES-15 | Registration form renders correctly on small screens | 1. Open registration page on Samsung S21 5G (360px) <br> 2. Scroll through the form | All fields and the submit button are visible; no elements cut off | ❌ Fail — "Create account" button partially hidden at 360px |

---

## 6. Touch & Tap Targets

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| RES-16 | Buttons meet minimum tap target size | 1. Inspect primary buttons on mobile using DevTools <br> 2. Verify size | All interactive elements are at least 44×44 CSS px (Apple HIG / WCAG recommendation) | ⚠️ Blocked — design spec doesn't define minimum tap target size |
| RES-17 | Links in navigation are easy to tap | 1. Open mobile menu on iPhone 12 <br> 2. Attempt to tap each nav link | Links are spaced enough to avoid accidental taps; no mis-taps needed | ✅ Pass |
