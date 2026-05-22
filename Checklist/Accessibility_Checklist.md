# ♿ Accessibility Checklist

Basic accessibility validation based on WCAG 2.1 Level AA. Use this checklist during exploratory sessions or pre-release reviews to catch the most common accessibility issues.

---

## ⌨️ Keyboard Navigation

- [ ] All interactive elements are reachable using Tab key
- [ ] Tab order follows a logical, top-to-bottom left-to-right flow
- [ ] Focus indicator is always visible — no element loses focus ring
- [ ] Forms can be fully completed and submitted using keyboard only
- [ ] Modals trap focus while open and return focus when closed
- [ ] Escape key closes modals, dropdowns, and drawers

---

## 🔊 Screen Reader

- [ ] All images have descriptive `alt` text — not empty or generic ("image")
- [ ] Decorative images have `alt=""` so they are skipped by screen readers
- [ ] All form inputs have an associated `<label>` or `aria-label`
- [ ] Error messages are announced after form submission
- [ ] Page has a meaningful `<title>` tag
- [ ] Headings follow a logical hierarchy (H1 → H2 → H3)

---

## 🎨 Color & Contrast

- [ ] Body text contrast ratio is at least 4.5:1
- [ ] Large text (18px+) contrast ratio is at least 3:1
- [ ] Interactive elements (buttons, links) meet contrast requirements
- [ ] Information is not conveyed by color alone — always includes a label, icon, or pattern
- [ ] Focus states have sufficient contrast against the background

---

## 📱 Mobile Accessibility

- [ ] Touch targets are at least 44×44 CSS px
- [ ] Elements are not too close together — accidental taps are unlikely
- [ ] Pinch-to-zoom is not disabled (`user-scalable=no` is not used)
- [ ] Content is readable without horizontal scrolling at 320px width

---

## 🧩 Semantic Structure

- [ ] Page uses semantic HTML elements (`<nav>`, `<main>`, `<footer>`, `<button>`)
- [ ] Links have descriptive text — no "click here" or "read more" alone
- [ ] Tables have proper `<th>` headers if used
- [ ] Lists use `<ul>` or `<ol>` — not styled `<div>` elements

---

🧠 *Tools that help: DevTools Accessibility panel, NVDA (screen reader), Colour Contrast Analyser.*
