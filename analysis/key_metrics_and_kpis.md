# Key Metrics & KPIs

This document defines the **core metrics and KPIs** used across the **Primary Benchmark** and **Trend Benchmark** dashboards. All definitions and values are derived from the **visuals and KPI cards shown in the dashboards**, without introducing external assumptions.

---

## 1. Average Engagement

* **Definition:** Average of `Avg_Time_Spent` across all relevant students.
* **Displayed Value (Trend Benchmark):** ~40.8
* **Dashboard Usage:** KPI Card
* **Interpretation:** Represents the overall engagement intensity of the platform at a snapshot level.
* **Why It Matters:** Serves as a baseline health metric against which other engagement segments and trends are compared.

---

## 2. Average Engagement Before Subscription

* **Definition:** Average engagement for students during the **pre-subscription period**.
* **Displayed Value:** ~28.6
* **Dashboard Usage:** KPI Card + Subscription Period Chart
* **Interpretation:** Measures user engagement prior to paid conversion.
* **Why It Matters:** Acts as a baseline to evaluate the impact of subscription conversion on engagement.

---

## 3. Average Engagement After Subscription

* **Definition:** Average engagement for students during the **post-subscription period**.
* **Displayed Value:** ~47.6
* **Dashboard Usage:** KPI Card + Subscription Period Chart
* **Interpretation:** Indicates how engagement changes once users move to a paid plan.
* **Why It Matters:** Quantifies the engagement uplift associated with subscription conversion.

---

## 4. Engagement Level

* **Definition:** Categorical classification of students into **High, Medium, or Low** engagement tiers based on engagement values.
* **Dashboard Usage:** Slicers, charts, and KPI segmentation
* **Interpretation:** Simplifies continuous engagement data into interpretable behavioral segments.
* **Why It Matters:** Enables benchmark comparisons, tenure analysis, and churn risk identification.

---

## 5. Median User Tenure by Engagement Level

* **Definition:** Median subscription duration (in days) grouped by engagement level.
* **Displayed Values (Primary Benchmark):**

  * High: ~906 days
  * Medium: ~606 days
  * Low: ~434 days
* **Dashboard Usage:** Line / Column Chart
* **Interpretation:** Shows how long users remain subscribed across engagement tiers.
* **Why It Matters:** Establishes engagement as a strong predictor of long-term retention.

---

## 6. Average Subscription Duration

* **Definition:** Average number of days between enrollment date and cancellation date (or current date for active users).
* **Displayed Value (Trend Benchmark):** ~348 days
* **Dashboard Usage:** KPI Card
* **Interpretation:** Represents typical subscription lifespan across the platform.
* **Why It Matters:** High-level retention metric useful for lifecycle and revenue planning.

---

## 7. Average Subscription Duration by Engagement Level

* **Definition:** Average subscription duration segmented by engagement tier.
* **Displayed Values (Primary Benchmark Cards):**

  * High: ~906 days
  * Medium: ~606 days
  * Low: ~434 days
* **Dashboard Usage:** KPI Cards
* **Interpretation:** Demonstrates tenure differences across behavioral segments.
* **Why It Matters:** Helps prioritize engagement-driven retention strategies.

---

## 8. Student Engagement Distribution by Subscription Tier

* **Definition:** Count of students by engagement level, split by subscription type (Free, Basic, Premium).
* **Dashboard Usage:** Clustered Column Chart
* **Interpretation:** Shows how engagement varies across monetization tiers.
* **Why It Matters:** Identifies which subscription types are associated with deeper engagement.

---

## 9. Inactive Status

* **Definition:** Binary indicator of whether a student is currently inactive.
* **Dashboard Usage:** Box-and-whisker chart and clustered column chart
* **Interpretation:** Distinguishes disengaged or churn-risk users from active ones.
* **Why It Matters:** Strong signal for churn analysis and retention intervention.

---

## 10. Subscription Duration by Active Status

* **Definition:** Average subscription duration split by inactive vs active users.
* **Dashboard Observation:** Active users show significantly longer tenure than inactive users.
* **Dashboard Usage:** Column Chart
* **Interpretation:** Highlights the retention impact of sustained activity.
* **Why It Matters:** Reinforces activity and engagement as key levers for reducing churn.

---

## 11. Monthly Engagement (by Year)

* **Definition:** Average engagement grouped by `Last_Login_Month` and `Last_Login_Year`.
* **Dashboard Usage:** Clustered Column Chart
* **Interpretation:** Compares engagement levels across months and years.
* **Why It Matters:** Reveals temporal variation and potential seasonality in engagement.

---

## 12. Most Recent Activity Date

* **Definition:** Maximum value of the last login date across all students.
* **Displayed Value:** 03/11/2025
* **Dashboard Usage:** KPI Card
* **Interpretation:** Indicates the freshness of activity data.
* **Why It Matters:** Confirms data recency and dashboard relevance.

---

## Metric Design Notes

* All metrics are calculated on **snapshot-level data**, not event-level logs.
* Engagement metrics represent **aggregated averages**, not session-by-session behavior.
* Free users are excluded from subscription-period comparisons where applicable.

---

**Project:** Student Engagement Analysis
**Document Purpose:** Metric transparency and analytical clarity
**Author:** Ananya Jha
