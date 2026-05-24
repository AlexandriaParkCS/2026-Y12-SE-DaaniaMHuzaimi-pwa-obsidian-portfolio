**Test Case ID:** TC-009

**Description:**
Verify IDOR protection: a user cannot edit another user's sleep entry by manipulating the URL.

**Preconditions:**
- User `testuser` is logged in.
- User `otheruser` has a sleep entry with a known `entry_id` (e.g. ID = 1).
- `testuser` does not own entry ID 1.

**Steps:**
1. Log in as `testuser`.
2. Manually navigate to `/edit/1` (the ID of `otheruser`'s entry).

**Test Data:**
- URL: `/edit/1`
- Logged in as: `testuser` (not the owner of entry 1)

**Expected Result:**
Server returns a 404 Not Found response. The edit form for `otheruser`'s entry is not displayed.
