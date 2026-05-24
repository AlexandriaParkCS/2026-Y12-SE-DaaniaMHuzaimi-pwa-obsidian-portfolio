***Sign in/Register Experience***

The Sign-In and Register pages are key entry points for all users of SleepTracker. They are designed to be simple, secure, and user-friendly, making it easy for individuals to begin tracking and improving their sleep habits.
![[Screenshot 2026-05-24 202757.png]]
New users access the Register page from the main login page via the "Sign Up" link. Returning users enter their credentials directly on the Login page. Both pages use a responsive single-column card layout, ensuring compatibility across mobile and desktop devices.

The Register page includes a form with fields for username, password, and password confirmation, as well as clear label elements and placeholder text to guide user input.  Validation feedback is included on form submission, such as "Passwords must match" or "Username is already taken." Security is prioritised by hiding all password fields. After successfully registering, the user is forwarded to the Login page and sent a success message. After successfully checking in, the user is routed to the Dashboard, where they may start monitoring and assessing their sleep statistics.


***Dashboard***
The Dashboard serves as the home screen for verified users. It is meant to provide an immediate, brief summary of recent sleep statistics without the user having to browse to a separate site

![[Screenshot 2026-05-24 202926.png]]
The dashboard's top three stat cards (average sleep duration, average quality rating, and last night's sleep quality label) are followed by a ZenQuotes API-generated motivational wellness phrase. If the user has no previous entries, a polite prompt encourages them to enter their first sleep entry.

The visual hierarchy directs the user's attention from top to bottom, while consistent Bootstrap 5.3 styling in the user's preferred theme (dark, light, or purple) confirms the app's identity across all pages.