.The application stores its data in a SQLite database (`runtime/db/sleep.db`) with the following structure.

![[Entity Relationship Diagram.drawio.png]]

The model enables secure user authentication, individual sleep tracking, and the ability to set personal sleep goals.

The User entity represents people who register and use the application. Each user is uniquely identified by a username. Passwords are not stored in plain text; instead, a bcrypt hash is saved for security. A single user can have multiple SleepEntries and a maximum of one SleepGoal.

The SleepEntry entity records a single night of sleep data for a user: the bedtime, wake time, a quality rating (1–5), and optional notes. The duration is not stored it is calculated at runtime using `calculate_duration()` to avoid data redundancy.

The SleepGoal entity stores the user's target nightly sleep duration in hours. Each user has at most one goal record; updating the goal overwrites the existing record rather than creating a new one.

The foreign key relationships between entities, combined with `cascade='all, delete-orphan'` on the SQLAlchemy relationships, ensure that deleting a user record automatically removes all associated sleep entries and goals preserving data integrity and supporting the user's right to erasure.
