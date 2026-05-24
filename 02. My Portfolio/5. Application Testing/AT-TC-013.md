**Test Case ID:** TC-013

**Description:**
Verify that a user can set a sleep goal and it is saved and displayed correctly.

**Preconditions:**
- User `testuser` is logged in.
- Navigate to `/goal`.

**Steps:**
1. Navigate to `/goal`.
2. Enter `8.0` in the Target Hours field.
3. Click "Save Goal".

**Test Data:**
- Target Hours: `8.0`

**Expected Result:**
The goal page reloads or redirects with a success flash message. The Target Hours field shows `8.0`. The goal is stored in the database for `testuser`.
