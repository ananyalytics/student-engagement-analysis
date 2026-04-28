# 📊 DAX Measures & Queries

This document provides a detailed explanation of the DAX measures and calculated columns used in the **Power BI**.

The goal of these metrics is to analyze **user satisfaction, engagement behavior, and churn trends**.

---

# 🔹 DAX Measures

## 1. Average Satisfaction Score

```DAX
Average Satisfaction Score = AVERAGE(engagement_data[satisfaction_score])
```

* Calculates the average satisfaction score across all users.

* Provides a quick snapshot of overall user sentiment toward the platform.


## 2. Churn Rate

```DAX
Churn Rate = 
DIVIDE(
    CALCULATE(
        COUNTROWS(engagement_data),
        engagement_data[Activity] = "Churned"
    ),
    COUNTROWS(engagement_data)
)
```

* Computes the proportion of users who have churned.

* Helps to measure retention performance.


## 3. Churn Rate %

```DAX
Churn Rate % = FORMAT([Churn Rate], "0.0%")
```

* Formats churn rate into percentage format for visualization.


## 4. Low Engagement Ratio

```DAX
Low Engagement = 
DIVIDE(
    CALCULATE(
        COUNTROWS(engagement_data),
        engagement_data[Engagement_class] = "Low"
    ),
    COUNTROWS(engagement_data)
)
```

* Calculates the percentage of users with low engagement.

* Low engagement users are the **highest churn risk segment**.


## 5. Low Engagement %

```DAX
Low Engagement % = FORMAT([Low Engagement], "0.0%")
```

* Formats low engagement ratio into percentage.


## 6. Total Users

```DAX
Total Users = COUNTROWS(engagement_data)
```

* Counts total users in the dataset.


---

# 🔹 Calculated Columns

## 7. Last Login Month

```DAX
Last Login Month = FORMAT(engagement_data[Last log in], "MMM")
```

* Extracts month name (Jan, Feb, etc.) from last login date.

* Used for time-based trend analysis.


## 8. Last Login Year

```DAX
Last Login Year = YEAR(engagement_data[Last log in])
```

* Extracts year from last login date.


## 9. Month Number (Sorting Column)

```DAX
Month Number = MONTH(engagement_data[Last log in])
```

* Returns numeric month (1–12).

* Used to **sort month names correctly** in visuals.


## 10. Subscription Phase

```DAX
Subscription Phase = 
IF(
    ISBLANK(engagement_data[Enrollment_date]),
    "No Subscription",
    IF(
        engagement_data[Last log in] < engagement_data[Enrollment_date],
        "Pre-Subscription",
        "Post-Subscription"
    )
)
```

* Classifies users based on their activity relative to subscription.

* Helps analyze behavioral changes before and after conversion.

**Categories:**

* **No Subscription** → No enrollment data
* **Pre-Subscription** → Activity before subscribing
* **Post-Subscription** → Activity after subscribing

---
