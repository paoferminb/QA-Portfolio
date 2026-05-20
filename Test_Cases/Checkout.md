# 💳 Checkout

**Feature:** Order Placement & Confirmation  
**Environment:** Staging | Chrome 124  
**Tested by:** Paola Fermin

---

## 1. Order Placement

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CHK-01 | Complete checkout with valid data | 1. Add a product to cart <br> 2. Go to checkout <br> 3. Enter valid shipping address and payment details <br> 4. Click "Place order" | Order is placed; confirmation page shown with order ID and summary | ✅ Pass |
| CHK-02 | Checkout with empty cart | 1. Go directly to checkout URL with empty cart | Redirect to cart page; message: "Your cart is empty" | ✅ Pass |
| CHK-03 | Checkout without logging in | 1. Add a product to cart without logging in <br> 2. Go to checkout | Redirect to login page; cart is preserved after login | ❌ Fail — cart is cleared after login redirect |

---

## 2. Shipping

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CHK-04 | Submit checkout with missing shipping field | 1. Go to checkout <br> 2. Leave "Street address" blank <br> 3. Click "Place order" | Inline error: "Please enter your street address" | ✅ Pass |
| CHK-05 | Enter invalid zip code | 1. Go to checkout <br> 2. Enter "ABC" as zip code <br> 3. Click "Place order" | Inline error: "Please enter a valid zip code" | ✅ Pass |

---

## 3. Payment

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CHK-06 | Pay with valid test card | 1. Complete checkout form <br> 2. Enter test card `4242 4242 4242 4242` <br> 3. Click "Place order" | Payment accepted; order confirmation displayed | ✅ Pass |
| CHK-07 | Pay with declined card | 1. Complete checkout form <br> 2. Enter declined test card `4000 0000 0000 0002` <br> 3. Click "Place order" | Error: "Your card was declined. Please try another payment method." | ✅ Pass |
| CHK-08 | Confirm order appears in order history | 1. Place an order successfully <br> 2. Go to "My Orders" in user profile | New order appears at the top with correct status "Pending" | ✅ Pass |
