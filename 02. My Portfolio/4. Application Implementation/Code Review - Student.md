**Reviewer Name:** Grace Cho-Triganza
**Date:** 19 May 2026
**Module/Feature:** Authentication Blueprint  `routes/auth.py`

**Code Summary:**
This module implements the user authentication system for SleepTracker. It provides `/register`, `/login`, `/logout`, and `/delete_account` routes as a Flask Blueprint, along with a `login_required` decorator and `sanitise()` helper function. Passwords are hashed using bcrypt; all forms are protected with CSRF tokens via Flask-WTF.

**Strengths:**
- Clear and consistent variable naming throughout (`user`, `form`, `existing_user`)  improves readability without needing comments to understand intent.
- Security features are correctly layered: `sanitise()` strips HTML on input, bcrypt hashes passwords before storage, `session.clear()` prevents session fixation, and a generic error message prevents user enumeration.
- `@login_required` decorator uses `@wraps(f)` from `functools`, correctly preserving Flask's internal route name mapping.
- `cascade='all, delete-orphan'` on the User model means `/delete_account` removes all user data in a single `db.session.delete(user)` call  clean and privacy-compliant.
- Docstrings present on all functions explaining purpose, parameters, and security reasoning.

**Issues Found:**
- The `RegistrationForm` password field has no minimum length validator a user could register with a single-character password.
- `sanitise()` uses a basic regex to strip HTML tags but does not handle encoded HTML entities (e.g. `&lt;script&gt;`). For a school project this is acceptable, but a production app should use the `bleach` library.
- 
**Recommendations:**

- Add `Length(min=8, message='Password must be at least 8 characters.')` to the `PasswordField` validator in `forms.py`.
- Note `bleach` as a future improvement in a code comment above `sanitise()` for transparency.

