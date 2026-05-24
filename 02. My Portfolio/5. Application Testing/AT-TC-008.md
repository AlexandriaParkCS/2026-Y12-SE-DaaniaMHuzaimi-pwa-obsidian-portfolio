**Test Case ID:** TC-008

**Description:**
Verify that a sleep entry is rejected when wake time is before bedtime (custom validator).

**Preconditions:**
- User `testuser` is logged in.

**Steps:**
1. Navigate to `/log`.
2. Enter `2026-05-20T08:00` in the Bedtime field.
3. Enter `2026-05-20T06:00` in the Wake Time field (earlier than bedtime).
4. Select `3` from the Quality dropdown.
5. Click "Save Entry".

**Test Data:**
- Bedtime: `2026-05-20T08:00`
- Wake Time: `2026-05-20T06:00`

**Expected Result:**
Form is re-rendered with a validation error on the Wake Time field ("Wake time must be after bedtime" or similar). No entry is saved to the database.