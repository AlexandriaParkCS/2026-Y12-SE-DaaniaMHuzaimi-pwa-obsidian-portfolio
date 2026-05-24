**Test Case ID:** TC-010

**Description:**
Verify that the theme toggle cycles correctly through all three themes and that the selected theme persists after a page refresh.

**Preconditions:**
- User `testuser` is logged in.
- Current theme is "dark" (default).

**Steps:**
1. Navigate to `/dashboard`.
2. Note the current theme (dark -> moon icon ☾).
3. Click the theme toggle button once.
4. Note the new theme (light ->sun icon ☀).
5. Click the theme toggle button again.
6. Note the new theme (purple -> heart icon ♥).
7. Click the theme toggle button again.
8. Note the new theme (back to dark ->moon icon ☾).
9. Set theme to purple by clicking twice from dark.
10. Refresh the page.

**Test Data:**
- None.

**Expected Result:**
Steps 3–8: Theme cycles dark -> light -> purple -> dark as expected, with the correct icon for each state.
Step 10: After refresh, the purple theme is still active confirming `localStorage` persistence.
