**Test Case ID:** TC-014

**Description:**
Verify that the PWA is installable in Chrome (manifest and service worker both valid).

**Preconditions:**
- App is running and accessible in Chrome.
- Chrome version supports PWA installation.

**Steps:**
1. Open the app in Chrome.
2. Open Chrome DevTools -> Application -> Manifest.
3. Check for any manifest errors.
4. Open Chrome DevTools -> Application ->Service Workers.
5. Check the service worker status.
6. Look for the install icon in the Chrome address bar (or check DevTools ->Application -> Manifest -> "Add to Home Screen").

**Test Data:**
- None.

**Expected Result:**
DevTools Manifest panel shows no errors; app name, icons (192px and 512px), and start URL are correctly listed. Service Worker status shows "Activated and is running". Install option is available in the address bar or DevTools.