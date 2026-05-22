# 🧪 Functional Checklist

This checklist helps validate core functionality of the e-commerce platform. Use it during exploratory sessions, smoke runs, or quick feature readiness reviews before formal test execution.

---

## 📥 Input Validation

- [ ] Required fields are marked and validated before submission
- [ ] Inline error messages appear for missing or invalid input
- [ ] Fields only accept allowed characters and formats
- [ ] Character limits are enforced (e.g. name, comment fields)
- [ ] Dropdowns and selectors have appropriate default states

---

## 🖱️ UI Interaction

- [ ] All buttons trigger the correct action on click
- [ ] Modals and drawers open and close correctly
- [ ] Disabled buttons cannot be clicked and show correct cursor
- [ ] Loading states appear while async requests are in progress
- [ ] Toast notifications appear and dismiss as expected

---

## 🔄 Navigation Flows

- [ ] All main nav links lead to the correct pages
- [ ] Back navigation preserves previous state (e.g. scroll position, filters)
- [ ] Redirects after login lead to the intended destination
- [ ] Logout returns user to the home or login page
- [ ] Invalid URLs return a proper 404 page

---

## 📋 Form Behavior

- [ ] Form submission triggers the correct action
- [ ] Forms do not submit with missing required fields
- [ ] Multi-step forms retain data when navigating between steps
- [ ] Reset or cancel actions clear or discard data correctly
- [ ] Autofill works where applicable without breaking layout

---

## 🛒 E-Commerce Specific

- [ ] Products can be added to cart from listing and detail pages
- [ ] Cart updates correctly when quantity is changed or item removed
- [ ] Checkout flow completes end-to-end with valid data
- [ ] Order appears in history immediately after placement
- [ ] Out-of-stock products cannot be added to cart

---

## 🧼 Error & Edge Case Handling

- [ ] Empty search returns a clear "no results" message
- [ ] API failures show a user-friendly error — no raw messages exposed
- [ ] Session timeout redirects user to login with a message
- [ ] Submitting a form twice does not create duplicate records
- [ ] Applying an expired or invalid discount code shows an error

---

## 🧩 Integration Points

- [ ] Payment provider responds correctly in test mode
- [ ] Order confirmation email is triggered after purchase
- [ ] Cart state is preserved after authentication

---

🧠 *Use alongside test cases for deeper validation. Link any findings to your bug reports.*
