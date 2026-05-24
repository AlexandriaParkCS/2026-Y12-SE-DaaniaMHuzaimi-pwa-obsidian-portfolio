***Login/Register***
The Login/Register process is a critical component of SleepTracker, enabling secure access and personalised sleep data management. This process allows new users to create accounts and existing users to authenticate to access their data.

***Summary of user Registration***
**Input**
- Username 
- Email
- Password 
- Confirm Password 
**Process**
1. Validate form using Flask-WTF: check all fields are present, password and confirm_password match (`EqualTo` validator)
2. Sanitise username using `sanitise()` strip HTML tags (XSS prevention)
3. Query database: check if a `User` record with the same username already exists
4. If username exists: reject with flash message "Username already taken"
5. If username is available: create new `User` object, call `user.set_password(password)` which runs `bcrypt.generate_password_hash()` and stores the hash
6. Commit new user to the database
7. Redirect to login page with success flash message
**Output**
- Success: redirect to `/login` with "Account created, please log in" message
- Failure: re-render register form with specific validation error messages

***Summary of user Login***
**Input**
- Email (plain text)
- Password (plain text)

**Process**
1. Validate form using Flask-WTF: check fields are not empty
2. Query database: retrieve `User` record where `email` matches
3. If no user found: show generic error (prevent user enumeration)
4. If user found: call `user.check_password(password)` which runs `bcrypt.check_password_hash()`
5. If password does not match: show same generic error "Incorrect email or password"
6. If password matches: call `session.clear()` (prevent session fixation), then set `session['user_id'] = user.id`
7. Redirect to dashboard

**Output**
- Success: redirect to `/dashboard` with session established
- Failure: re-render login form with "Invalid username or password" (same message regardless of which field was wrong)

***Summary of user Login***
The Sleep Entry Logging process handles the creation of a new sleep record for the authenticated user.

**Input**
- Bedtime (datetime-local field  date and time)
- Wake Time (datetime-local field date and time)
- Quality (integer select, 1–5)
- Notes (free text, optional, max ~500 characters)

**Process**
1. Verify user is authenticated via `@login_required` decorator
2. Validate form using Flask-WTF: check bedtime and wake_time are present and valid datetime format
3. Run custom validator `validate_wake_time()`: confirm `wake_time > bedtime`; if not, raise `ValidationError`
4. Sanitise `notes` field using `sanitise()` strip HTML tags
5. Create new `SleepEntry` object with `user_id=session['user_id']`, `bedtime`, `wake_time`, `quality`, `notes`
6. Commit to database
7. Redirect to history page

**Output**
- Success: redirect to `/history` with "Sleep entry saved!" flash message
- Failure (invalid form): re-render log form with validation error messages
- Failure (unauthenticated): redirect to `/login`
