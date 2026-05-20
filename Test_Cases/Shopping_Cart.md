# 🛒 Shopping Cart

**Feature:** Cart Management  
**Environment:** Staging | Chrome 124  
**Tested by:** Paola Fermin

---

## 1. Add to Cart

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CART-01 | Add a product to the cart | 1. Go to a product detail page <br> 2. Click "Add to cart" | Product appears in cart; cart counter increments by 1 | ✅ Pass |
| CART-02 | Add an out-of-stock product | 1. Go to a product marked as "Out of stock" <br> 2. Observe the page | "Add to cart" button is disabled; message: "Currently unavailable" | ✅ Pass |
| CART-03 | Add same product twice | 1. Go to a product detail page <br> 2. Click "Add to cart" <br> 3. Click "Add to cart" again | Quantity updates to 2 in the cart; no duplicate line item created | ❌ Fail — product added as two separate line items |

---

## 2. Update & Remove

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CART-04 | Increase product quantity in cart | 1. Go to cart <br> 2. Click "+" next to a product | Quantity increases by 1; subtotal recalculates correctly | ✅ Pass |
| CART-05 | Decrease quantity to zero | 1. Go to cart <br> 2. Click "−" until quantity reaches 0 | Product is removed from cart automatically | ✅ Pass |
| CART-06 | Remove a product manually | 1. Go to cart <br> 2. Click the remove/trash icon next to a product | Product is removed; cart updates; if cart is empty, message: "Your cart is empty" | ✅ Pass |

---

## 3. Cart Persistence

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| CART-07 | Cart persists after page refresh | 1. Add a product to cart <br> 2. Refresh the browser | Cart still contains the same product and quantity | ⚠️ Blocked — depends on AUTH-08 session fix |
