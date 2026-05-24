**Test Case ID:** TC-005

**Description:**
Verify that registration fails when passwords do not match.

**Preconditions:**
- The Register page is accessible.

**Steps:**
1. Navigate to `/register`.
2. Enter `anyuser` in the Username field.
3. Enter `Password1!` in the Password field.
4. Enter `DifferentPass1!` in the Confirm Password field.
5. Click "Register".

**Test Data:**
- Username: `anyuser`
- Password: `Password1!`
- Confirm Password: `DifferentPass1!`

**Expected Result:**
Form is re-rendered with a validation error on the Confirm Password field ("Passwords must match" or similar). No new account is created.
