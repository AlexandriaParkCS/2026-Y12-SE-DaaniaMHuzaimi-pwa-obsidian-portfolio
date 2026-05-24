**Test Case ID:** TC-011

**Description:**
Verify that a logged-in user can edit an existing sleep entry they own.

**Preconditions:**
- User `testuser` is logged in and has at least one sleep entry.
- The History page is accessible at `/history`.

**Steps:**
1. Navigate to `/history`.
2. Click the "Edit" button on the most recent entry.
3. Change the Quality rating from `4` to `5`.
4. Click "Save Changes".

**Test Data:**
- Updated Quality: `5`

**Expected Result:**
User is redirected to `/history`. The edited entry now shows quality "Excellent". The bedtime and wake time are unchanged.
