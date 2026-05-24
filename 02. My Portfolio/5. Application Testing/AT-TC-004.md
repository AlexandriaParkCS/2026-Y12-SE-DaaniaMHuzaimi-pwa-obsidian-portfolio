**Test Case ID:** TC-004

**Description:**
Verify that a new user can register with valid, unique credentials.

**Preconditions:**
- Username `newuser2026` does not exist in the database.
- The Register page is accessible at `/register`.

**Steps:**
1. Navigate to `/register`.
2. Enter `newuser2026` in the Username field.
3. Enter `SecurePass1!` in the Password field.
4. Enter `SecurePass1!` in the Confirm Password field.
5. Click "Register".

**Test Data:**
- Username: `newuser2026`
- Password: `SecurePass1!`
- Confirm Password: `SecurePass1!`

**Expected Result:**
User is redirected to `/login` with a success flash message. The account `newuser2026` now exists in the database with a bcrypt-hashed password (not plaintext).
