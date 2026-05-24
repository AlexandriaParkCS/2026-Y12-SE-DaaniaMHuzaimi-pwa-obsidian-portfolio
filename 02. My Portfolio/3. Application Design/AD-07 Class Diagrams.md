The following class diagram models the key objects and their relationships that support secure, user-specific sleep tracking in SleepTracker

![[Screenshot 2026-05-25 060407.png]]
The User class represents individuals who register and interact with the application. Each user can own multiple SleepEntry objects (one-to-many composition) and at most one SleepGoal (one-to-one composition). The composition relationship (filled diamond) indicates that SleepEntry and SleepGoal instances cannot exist independently of a User  they are destroyed when the User is deleted (`cascade='all, delete-orphan'`).

The SleepEntry class encapsulates all data for a single recorded night of sleep. Business logic for derived values (duration calculation, quality labelling) is kept inside the class as methods and properties, following the principle of keeping data and the operations on that data together.

The SleepGoal class is intentionally minimal it stores only the `targetHours` value. Keeping it as a separate entity (rather than a column on the `User` table) allows it to be absent (null state represented by no record) without requiring a nullable column on the users table.

This class structure is consistent with the Level 1 DFD (Process 3: Sleep Management) and the ERD in AD-05  all three documents describe the same underlying domain model from different perspectives.
