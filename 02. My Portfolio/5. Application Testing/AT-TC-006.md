**Test Case ID:** TC-006

**Description:**
Verify that an unauthenticated user cannot access the dashboard and is redirected to login.

**Preconditions:**
- User is not logged in (no active session).

**Steps:**
1. Ensure no user is logged in (open a fresh private/incognito window or log out first).
2. Navigate directly to `/dashboard`.

**Test Data:**
- None.

**Expected Result:**
User is redirected to `/login`. The dashboard content is not displayed.