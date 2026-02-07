# Analysis Workflow

This document outlines the **end-to-end analytical workflow** followed to build the Student Engagement Analysis dashboards. It covers both **Google Sheets (data preparation)** and **Power BI (data modeling, analysis, and visualization)** steps, in the exact sequence they were performed.

---

## Data Consolidation & Cleaning (Google Sheets)

### 1. Data Consolidation

* Combined all three CSV files into a **single Google Sheet**, organized as **multiple sheets** (one per dataset).
* Converted each dataset range into a **Google Sheets Table** to improve readability, structured referencing, and downstream consistency.

---

### 2. Date Format Standardization

* Identified date parsing issues in the **Engagement Data** due to UK format (`DD-MM-YYYY`).
* Converted all dates to **US format (`MM-DD-YYYY`)** to avoid column type errors during Power BI import.

---

### 3. Null Value Cleaning

* Observed literal `NULL / null` strings in date fields.
* Used the following Google Sheets formula to clean date columns:

```
=IF(OR(F2="NULL", F2="null"), "", F2)
```

* Applied this logic to:

  * `last_login`
  * `enrollment_date`
  * `cancellation_date`

**Outcome:** Clean, blank values instead of invalid strings.

---

### 4. Final Dataset Preparation

* Exported the cleaned and consolidated file as **`Student Engagement Data.xls`** for Power BI ingestion.

---

## Data Modeling & Primary Benchmark Analysis (Power BI)

### 5. Data Loading

* Loaded `Student Engagement Data.xls` into Power BI.
* Verified column data types and corrected date fields that initially loaded as **whole numbers**.

---

### 6. Engagement Level Classification (DAX)

* Created a calculated column **`Engagement Level`** using DAX to bucket students into engagement tiers.
* This column was a foundational dimension for primary benchmarks.

---

### 7. Primary Benchmark 1: Engagement vs Subscription Tier

* Identified the first benchmark question:

> **Does higher engagement correlate with higher conversion to paid subscriptions?**

* Visualized using a **clustered column chart**:

  * *Student Engagement Distribution by Subscription Tier*

---

### 8. Subscription Duration Calculation & Error Handling

* Created a calculated column for **Subscription Duration** using:

  * `Cancellation Date – Enrollment Date`

* Encountered **negative duration values** due to missing or inconsistent cancellation dates.

---

### 9. Data Quality Fix: Clean Cancellation Date

* Created a new column **Clean Cancellation Date** using DAX:

  * Replaced missing cancellation dates with **today’s date**
* Recalculated subscription duration using the cleaned date field.

**Outcome:**

* Eliminated negative durations
* Returned `NULL` instead of invalid values

---

### 10. Primary Benchmark 2: Engagement vs Subscription Tenure

* Used the cleaned **Subscription Duration** and **Engagement Level** to plot:

  * *Median User Tenure by Engagement Level*

---

### 11. Primary Benchmark 3: Engagement vs Inactivity

* Created a **clustered column chart** comparing engagement vs inactive status. 
* Analyzed inactivity patterns across engagement levels.

---

### 12. Supporting Insights & Filters

* Added a **donut chart** to show student count by subscription type.
* Inserted KPI cards for:

  * Average subscription days by engagement level
* Added an **Engagement Level slicer** for interactivity.

---

## Trend Benchmark Analysis (Temporal Engagement)

### 13. Snapshot-Level Data Constraint

* Recognized that the dataset is **snapshot-level**, not event-level.
* Concluded that true time-series analysis per student was not feasible.

**Design Decision:**

* Performed **month-over-month comparisons** based on students’ *last login activity*.

---

### 14. Temporal Feature Engineering (DAX)

* Created new DAX columns:

  * `Last_Login_Year`
  * `Last_Login_Month`
  * `Login_Month_Number`

* Sorted `Last_Login_Month` using:

  * *Column Tools → Sort by Column → Login_Month_Number*

---

### 15. Engagement Trend Visualization

* Built a **clustered column chart**:

  * Engagement by Month and Year

---

### 16. Subscription Period Classification

* Created a DAX column **`Subscription_Period`** to identify:

  * Pre-subscription
  * Post-subscription

* Filtered out **Free users**, as they were never enrolled or subscribed.

---

### 17. Pre vs Post Subscription Analysis

* Created a clustered column chart comparing:

  * Average engagement before vs after subscription

---

### 18. Trend Benchmark KPIs & Filters

* Added slicers for:

  * Month
  * Year

* Added KPI cards for:

  * Average engagement
  * Most recent activity date
  * Average engagement before subscription
  * Average engagement after subscription
  * Average subscription duration

---

## Dashboard Refinement & Visual Consistency

### 19. Layout & Canvas Standardization

* Identified inconsistent **canvas sizes** between Primary and Trend benchmark pages.
* Re-aligned layouts, resized visuals, and standardized spacing.

---

### 20. Final Visual Polish

* Re-arranged charts and KPIs for visual hierarchy.
* Ensured consistent typography, spacing, and alignment across pages.

---

**Note:** *DAX logics documented separately via screenshots in project assets.* 
