**Test Case ID:** TC-015

**Description:**
Verify that the app loads correctly when offline (service worker cache-first strategy).

**Preconditions:**
- User has visited the app at least once while online (assets cached).
- App is running.

**Steps:**
1. Navigate to `/dashboard` while online.
2. Open Chrome DevTools -> Network -> check "Offline" checkbox.
3. Refresh the page.

**Test Data:**
- None.

**Expected Result:**
The dashboard page loads from the service worker cache. CSS, JavaScript, and icons are all served correctly. A "You are offline" banner may appear (if implemented in `app.js`). The page does not show a Chrome "No internet" dinosaur error.