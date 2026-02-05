# Column Definitions – Student Engagement Analysis

This document defines each column used in the **Student Engagement Analysis** dataset. It helps to clearly understand the relationships, data type, and role of every field.

---

## 1. `Student_Id`

* **Description:** Unique student identifier (ID) used to distinguish individual users in the dataset.
* **Data Type:** String
* **Example:** `STU001`
* **Role:** Primary key for user-level aggregation and segmentation.

---

## 2. `Sub_Type`

* **Description:** Type of subscription plan chosen by the student.
* **Data Type:** Categorical
* **Possible Values:** `Basic`, `Premium`, `Free`
* **Role:** Used to compare engagement, satisfaction, and churn across subscription tiers.

---

## 3. `Enrollment_Date`

* **Description:** Original date on which the student enrolled in the platform.
* **Data Type:** Date
* **Role:** Used to compute subscription duration, trend analysis, and lifecycle metrics.

---

## 4. `Cancellation_Date`

* **Description:** Date on which the student cancelled their subscription, if applicable.
* **Data Type:** Date (Nullable)
* **Role:** Key driver for churn analysis and retention benchmarking.

---

## 5. `Inactive`

* **Description:** Indicates whether the student is currently inactive.
* **Data Type:** Boolean
* **Possible Values:** `TRUE`, `FALSE`
* **Role:** Binary status flag for identifying churned or disengaged users.

---

## 6. `Last_login`

* **Description:** Last recorded login timestamp of the student (raw source field).
* **Data Type:** DateTime (Nullable)
* **Role:** Initially intended to measure recent activity; later replaced by cleaned fields.
* **Note:** Contains a high proportion of missing values.

---

## 7. `Avg_Time_Spent`

* **Description:** Average time spent per session by the student.
* **Data Type:** Integer (Minutes)
* **Role:** Core engagement metric used in primary and trend benchmarks.

---

## 8. `Satisfaction_Score`

* **Description:** Self-reported satisfaction rating provided by the student.
* **Data Type:** Integer (Ordinal)
* **Scale:** 1 (Very Low) – 10 (Very High)
* **Role:** Used to correlate engagement with perceived value and churn likelihood.

---

## 9. `Signup_Date`

* **Description:** Date on which the student initially signed up on the platform.
* **Data Type:** Date
* **Role:** Used for user acquisition analysis and time-to-enrollment calculations.

---

## 10. `Last_Login_Updated`

* **Description:** Cleaned and standardized version of the last login date.
* **Data Type:** DateTime (Nullable)
* **Role:** Used in dashboards to evaluate recency and active-user definitions.

---

## 11. `Enrollment_Date_Updated`

* **Description:** Cleaned and standardized enrollment date used for analysis consistency.
* **Data Type:** Date
* **Role:** Preferred field for all enrollment-based calculations and benchmarks.

---

## 12. `Cancellation_Date_Updated`

* **Description:** Cleaned and standardized cancellation date.
* **Data Type:** Date (Nullable)
* **Role:** Preferred field for churn timing, retention curves, and survival-style analysis.

---

## Notes on Data Modeling

* Raw date fields are preserved for traceability; all analysis use the *_Updated columns.
* The dataset is modeled at a **student-level grain** (one row per student).
