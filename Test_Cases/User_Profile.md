# 👤 User Profile

**Feature:** Profile & Address Management  
**Environment:** Staging | Chrome 124  
**Tested by:** Paola Fermin

---

## 1. Profile Updates

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PRF-01 | Update display name | 1. Go to Profile settings <br> 2. Edit the name field <br> 3. Click "Save changes" | Name updated; success toast: "Profile updated successfully" | ✅ Pass |
| PRF-02 | Update email to one already in use | 1. Go to Profile settings <br> 2. Enter an email belonging to another account <br> 3. Click "Save changes" | Error: "This email is already associated with another account" | ✅ Pass |
| PRF-03 | Save profile with empty required field | 1. Go to Profile settings <br> 2. Clear the name field <br> 3. Click "Save changes" | Inline error: "Name cannot be empty" | ❌ Fail — profile saved with empty name field |

---

## 2. Password Change

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PRF-04 | Change password with valid data | 1. Go to Security settings <br> 2. Enter current password <br> 3. Enter new password and confirm it <br> 4. Click "Update password" | Password updated; user remains logged in; confirmation message shown | ✅ Pass |
| PRF-05 | Change password with wrong current password | 1. Go to Security settings <br> 2. Enter an incorrect current password <br> 3. Click "Update password" | Error: "Current password is incorrect" | ✅ Pass |

---

## 3. Address Management

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| PRF-06 | Add a new shipping address | 1. Go to Addresses section <br> 2. Click "Add new address" <br> 3. Fill in all fields <br> 4. Click "Save address" | Address saved and appears in the address list | ✅ Pass |
