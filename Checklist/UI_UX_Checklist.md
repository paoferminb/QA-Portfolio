# 🎨 UI/UX Checklist

Visual consistency and usability validation checklist. Use during design review, exploratory testing, or pre-release checks to catch visual and interaction issues.

---

## 🖼️ Visual Consistency

- [ ] Font sizes, weights, and families match the design spec
- [ ] Colors match the defined palette — no off-brand shades
- [ ] Spacing and padding are consistent across similar components
- [ ] Icons are consistent in style and size throughout the interface
- [ ] Component states (default, hover, active, disabled, error) match design

---

## 🖱️ Interactions & Feedback

- [ ] Clickable elements have a visible hover state
- [ ] Buttons show a loading state while a request is in progress
- [ ] Success actions trigger a confirmation (toast, message, or redirect)
- [ ] Error states are clearly communicated — not silent failures
- [ ] Destructive actions (delete, cancel) require confirmation before executing

---

## 📐 Layout & Alignment

- [ ] Elements are aligned to the grid — no unexpected offsets
- [ ] Text does not overflow its container on any resolution
- [ ] Images maintain correct aspect ratio and do not stretch
- [ ] Cards and list items are consistent in height and padding
- [ ] Empty states (no results, no orders) have a helpful message and visual

---

## 📱 Responsive Behavior

- [ ] Layout adapts correctly at desktop, tablet, and mobile breakpoints
- [ ] No horizontal scroll appears on mobile viewports
- [ ] Navigation collapses into a hamburger menu on small screens
- [ ] Text remains readable — no truncation of essential content
- [ ] Forms and CTAs are fully visible without zooming on mobile

---

## ✍️ Content & Copy

- [ ] All visible text is free of spelling and grammar errors
- [ ] Button labels are clear and action-oriented (e.g. "Place order", not "Submit")
- [ ] Error messages are helpful — they tell the user what to do, not just what went wrong
- [ ] Placeholder text is present in form fields where useful
- [ ] Page titles and headings accurately describe the content

---

## 🔄 User Flow & Usability

- [ ] The user can complete the main flows without needing instructions
- [ ] Key CTAs are visible without scrolling on desktop and mobile
- [ ] Progress is clearly indicated in multi-step flows (e.g. checkout steps)
- [ ] The user can recover from errors without losing their data
- [ ] Confirmation pages give the user a clear next action

---

🧠 *Use Figma as design reference. Compare implementation against spec for each component.*
