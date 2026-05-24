Data dictionary for all entity attributes in the database schema (excluding primary keys and foreign keys).

***User***

| Attribute     | Data Type | Description                                                                                                            | Example                        |
| ------------- | --------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| Email         | String    | A unique identifier chosen by the user at registration. No real name required.                                         | daania@gmail.com               |
| Password_hash | String    | bcrypt hash of the user's password. Generated with a unique random salt per user. Never stores the plaintext password. | $2b$12$1R6AjTNK2E6T1KCZp1.Cx.. |

***Sleep entry***

| Attribute | Data Type | Description                                                                                             | Exaemple                       |
| --------- | --------- | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| Bedtime   | DateTime  | Monetary amount. Negative values indicate outflow and positive indicate inflow of funds.                | 2026-05-19 23:00:00            |
| Waketime  | DateTime  | The date and time the user woke up. Must be after `bedtime` (validated on input).                       | 2026-05-20 07:30:00            |
| Quality   | Interger  | A self-reported sleep quality rating on a scale of 1 (Poor) to 5 (Excellent).                           | 4                              |
| Notes     | Text      | Optional free-text notes about the sleep entry. HTML tags are stripped before storage (XSS prevention). | Woke up once during the night. |

**SleepGoal**

| Attribute      | Data Type | Description                                                                                             | Exaemple                       |
| -------------- | --------- | ------------------------------------------------------------------------------------------------------- | ------------------------------ |
| Targeted_hours | float     | The user's personal target for nightly sleep duration, in decimal hours.                                | 8.0, 7.5                       |

***Calculated/ derived values (not stored)***
The following values are derived at runtime from stored data and are not stored in the database to avoid data redundancy:

| Value            | Derived from                           | Method                               |     |
| ---------------- | -------------------------------------- | ------------------------------------ | --- |
| duration (hours) | `wake_time - bedtime`                  | `SleepEntry.calculate_duration()`    |     |
| quality_label    | `quality` integer                      | `SleepEntry.quality_label` property  |     |
| quality_colour   | `quality` integer                      | `SleepEntry.quality_colour` property |     |
| avg_duration     | list of `calculate_duration()` results | calculated in dashboard route        |     |
| avg_quality      | list of `quality` values               | calculated in dashboard route        |     |

