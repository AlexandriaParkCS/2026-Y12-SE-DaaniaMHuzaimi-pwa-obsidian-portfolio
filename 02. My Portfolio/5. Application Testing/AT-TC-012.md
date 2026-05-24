**Test Case ID:** TC-012

**Description:**
Verify that a logged-in user can delete a sleep entry they own, with a confirmation prompt.

**Preconditions:**
- User `testuser` is logged in and has at least one sleep entry in history.

**Steps:**
1. Navigate to `/history`.
2. Note the number of entries displayed.
3. Click the "Delete" button on the most recent entry.
4. Click "OK" on the browser confirmation dialog.

**Test Data:**
- None.

**Expected Result:**
The deleted entry no longer appears in `/history`. The total number of entries has decreased by one. A success flash message is displayed.
