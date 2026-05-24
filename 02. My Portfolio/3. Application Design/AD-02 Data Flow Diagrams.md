***Context diagram***

The application interacts with a number of external entities (actors) as shown on the following Context Diagram.
![[Context diagram.drawio.png]]
The actors include:
- **User:** The user is the main person interacting with the SleepTracker application. They can create an account, log in, record their sleeping habits, and view their progress through features such as the dashboard, sleep history, and goal tracking.
- **Database:** SleepTracker uses a SQLite database called `sleep.db` to store important information, including user accounts, sleep records, and sleep goals. The application manages all database interactions using SQLAlchemy ORM.
- **ZenQuotes API:** SleepTracker connects to the ZenQuotes API (`zenquotes.io/api/`) to display a daily motivational or wellness quote on the dashboard. If the API is unavailable, the application will instead show a default backup quote.

***Level 1 Data flow diagram***
![[Level One diagram.drawio.png]]
Users are required to create an account and log in before accessing any sleep-tracking features. During registration, users must enter a username, email address, and password. The password is securely encrypted using bcrypt before being stored in the database. When logging in, the entered credentials are checked against the stored encrypted password to verify the user’s identity.

Once authenticated, users are taken to the Dashboard, where they can view their most recent sleep entries and overall sleep statistics, such as average sleep duration and sleep quality. The dashboard also displays a motivational wellness quote retrieved from the ZenQuotes API. Static files such as CSS, JavaScript, and images are cached by the service worker, allowing some features of the application to remain accessible offline.

Users can also manage their sleep information through the Sleep Management system, where they are able to add, edit, and delete sleep entries, as well as set personal sleep goals. All data entered into the system is securely processed using CSRF protection, IDOR ownership checks, and SQLAlchemy parameterised queries to help prevent unauthorised access and SQL injection attacks.