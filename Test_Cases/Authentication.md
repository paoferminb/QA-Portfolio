# 🔐 Authentication

**Feature:** Login & Registration  
**Environment:** Staging | Chrome 124  
**Tested by:** Paola Fermin

---

## 1. Registration

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| AUTH-01 | Register with valid data | 1. Go to Sign Up page <br> 2. Enter valid name, email, and password <br> 3. Click "Create account" | Account created; user is redirected to dashboard | ✅ Pass |
| AUTH-02 | Register with existing email | 1. Go to Sign Up page <br> 2. Enter an already registered email <br> 3. Click "Create account" | Error: "An account with this email already exists" | ✅ Pass |
| AUTH-03 | Register with invalid email format | 1. Go to Sign Up page <br> 2. Enter `userexample.com` as email <br> 3. Click "Create account" | Inline validation error: "Please enter a valid email address" | ✅ Pass |
| AUTH-04 | Register with empty fields | 1. Go to Sign Up page <br> 2. Leave all fields blank <br> 3. Click "Create account" | All required fields highlighted; error: "This field is required" | ❌ Fail — form submitted with no validation message |

---

## 2. Login

| ID | Scenario | Steps | Expected Result | Actual Result |
|---|---|---|---|---|
| AUTH-05 | Login with valid credentials | 1. Go to Login page <br> 2. Enter registered email and correct password <br> 3. Click "Log in" | User is authenticated and redirected to home page | ✅ Pass |
| AUTH-06 | Login with wrong password | 1. Go to Login page <br> 2. Enter valid email with incorrect password <br> 3. Click "Log in" | Error: "Invalid email or password" | ✅ Pass |
| AUTH-07 | Login with non-existent email | 1. Go to Login page <br> 2. Enter an email not in the system <br> 3. Click "Log in" | Error: "Invalid email or password" | ✅ Pass |
| AUTH-08 | Session persistence after browser refresh | 1. Log in successfully <br> 2. Refresh the browser | User remains logged in; session not lost | ⚠️ Blocked — session config under review by dev team |
