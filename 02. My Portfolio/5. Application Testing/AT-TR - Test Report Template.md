**Test Date:** 25/11/2025

**Results:**

| Test Case     | Description                                             | Outcome | Notes                                                                                                       |
| ------------- | ------------------------------------------------------- | ------- | ----------------------------------------------------------------------------------------------------------- |
| [[AT-TC-001]] | Valid login redirects to dashboard                      | Pass    |                                                                                                             |
| [[AT-TC-002]] | Wrong password shows generic error                      | Pass    |                                                                                                             |
| [[AT-TC-003]] | Nonexistent username shows same generic error           | Pass    | Confirmed user enumeration prevention working                                                               |
| [[AT-TC-004]] | Register with valid credentials                         | Pass    |                                                                                                             |
| [[AT-TC-005]] | Register with mismatched passwords fails                | Pass    |                                                                                                             |
| [[AT-TC-006]] | Unauthenticated access to /dashboard redirects to login | Pass    |                                                                                                             |
| [[AT-TC-007]] | Log valid sleep entry                                   | Pass    | Initially failed. Edit form showed wrong datetime format. Fixed `strftime('%Y-%m-%dT%H:%M')` before re-run. |
| [[AT-TC-008]] | Wake before bedtime rejected by validator               | Pass    |                                                                                                             |
| [[AT-TC-009]] | IDOR protection on edit 404 for other user's entry      | Pass    |                                                                                                             |
| [[AT-TC-010]] | Theme cycles correctly and persists on refresh          | Pass    |                                                                                                             |
| [[AT-TC-011]] | Edit own sleep entry                                    | Pass    |                                                                                                             |
| [[AT-TC-012]] | Delete own sleep entry with confirmation                | Pass    |                                                                                                             |
| [[AT-TC-013]] | Set sleep goal                                          | Pass    |                                                                                                             |
| [[AT-TC-014]] | PWA installable — manifest and SW valid in DevTools     | Pass    |                                                                                                             |
| [[AT-TC-015]] | App loads offline from service worker cache             | Pass    |                                                                                                             |


