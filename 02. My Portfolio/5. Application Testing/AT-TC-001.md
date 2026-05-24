**Test Case ID:** TC-001

**Description:**
Verify that a registered user can log in with valid credentials and is redirected to the dashboard.

**Preconditions:**
- User email `test@gmail.com` exists with password `Password1!`.
- The Login page is accessible at `/login`.

**Steps:**
1. Navigate to `/login`.
2. Enter `test@gmail.com` in the Email field.
3. Enter `Password1!` in the Password field.
4. Click the "Sign In" button.

**Test Data:**
- Email: `test@gmail.com`
- Password: `Password1!`

**Expected Result:**
User is redirected to `/dashboard` and the navigation bar shows the logged-in state (Dashboard, Log Sleep, History, Sleep Goal, Sign out links visible).
