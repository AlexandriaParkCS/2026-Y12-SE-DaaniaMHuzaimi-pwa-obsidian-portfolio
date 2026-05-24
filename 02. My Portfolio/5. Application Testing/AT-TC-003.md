**Test Case ID:** TC-003

**Description:**
Verify that login fails with a nonexistent username and shows the same generic error message.

**Preconditions:**
- The Login page is accessible.
- Email `ghost_user@gmail.com` does not exist in the database.

**Steps:**
1. Navigate to `/login`.
2. Enter `ghost_user@gmail.com` in the Email field.
3. Enter `AnyPassword1` in the Password field.
4. Click "Sign In".

**Test Data:**
- Email: `ghost_user@gmail.com`
- Password: `AnyPassword1`

**Expected Result:**
User remains on `/login`. The message "Invalid username or password." is displayed identical to TC-002, revealing nothing about whether the username exists.