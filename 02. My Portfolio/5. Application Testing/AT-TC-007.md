**Test Case ID:** TC-007

**Description:**
Verify that a logged-in user can log a valid sleep entry.

**Preconditions:**
- User `testuser` is logged in.
- The Log Sleep page is accessible at `/log`.

**Steps:**
1. Navigate to `/log`.
2. Enter `2026-05-19T23:00` in the Bedtime field.
3. Enter `2026-05-20T07:30` in the Wake Time field.
4. Select `4` from the Quality dropdown.
5. Enter `Felt well rested.` in the Notes field.
6. Click "Save Entry".

**Test Data:**
- Bedtime: `2026-05-19T23:00`
- Wake Time: `2026-05-20T07:30`
- Quality: `4`
- Notes: `Felt well rested.`

**Expected Result:**
User is redirected to `/history`. A new entry appears showing bedtime 11:00 PM, wake time 7:30 AM, duration 8.5 hours, quality "Great".
