SleepTracker will be a Python-Flask-based Progressive Web Application (PWA) that allows users to:
- Register and log in securely with a username and hashed password
- Log sleep entries (bedtime, wake time, quality rating 1–5, optional notes)
- Edit or delete past sleep entries
- Set a personal nightly sleep goal (e.g. 8 hours)
- View a dashboard with sleep stats and a motivational wellness quote
- Delete their account and all associated data at any time

***Proposed solution***
	My proposed solution is to create a website that helps people track their sleep in a simple and easy way. The website will allow users to record when they go to bed and when they wake up, so they can see how many hours of sleep they are getting each night. 

***Key features***
	The key features of SleepTracker are:
Functional: 
	User authentication, sleep entry logging, sleep history with full CRUD, sleep goal management, dashboard statistics, external wellness quote API (ZenQuotes).
	
Performance: 
	Fast page loads, responsive layout for mobile and desktop users, offline access via service workers caching.

Security:
	bcrypt password hashing, CSRF protection on all forms (Flask-WTF),  has in put sanitisation (XSS prevention), `login_required` decorator on all data routes, IDOR protection on edit/delete (ownership verification), session fixation prevention, generic login error messages (user enumeration prevention), cascade delete on account removal.

Privacy: 
	No email address collected. Users may delete their account and all data at any time. A privacy policy page that explains all data practices. Compliant with the Australian Privacy Act 1988.

***User Experience***
	The interface uses Bootstrap 5.3 with a mobile-first responsive layout. Three colour themes (dark, light, purple) are available and toggled via a button in the navigation bar, with the preference stored in localStorage so it persists between visits. The app is installable from the browser ("Add to Home Screen") and loads from cache when offline.

***Technologies***
	Backend: Python, Flask, SQLAlchemy, Flask-WTF 
	Frontend: HTML5, CSS3, Bootstrap, JavaScript
	Database: SQLite3
	Authentication: bcrypt, Flash-WTF (CSRF)
	External API: ZenQuotes (`zenquotes.io/api/today`)
	Version control: Git + GitHub
