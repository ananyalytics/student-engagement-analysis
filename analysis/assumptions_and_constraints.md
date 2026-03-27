# Assumptions

## 1. Snapshot-Based Dataset Assumption

The dataset represents a **snapshot of student data at a single point in time**, not a full historical activity log.

Therefore:

* Trends (Pre vs Post 2025) are based on **last login date**
* Subscription activity is inferred from **start and cancellation dates**
* Engagement behavior is **assumed based on total activity counts**

This means trend analysis reflects **distribution changes**, not true time-series behavior.

---

## 2. Engagement Level Classification Assumption

Students were classified into **Low, Medium, and High Engagement** categories based on:

* Videos Watched
* Assignments Completed
* Forum Posts
* Quiz Attempts

This classification assumes:

* These four metrics adequately represent student engagement
* All engagement activities contribute equally to overall engagement
* Engagement thresholds used are reasonable proxies for behavior

This is a **rule-based classification**, not a machine learning model.

---

## 3. Subscription Duration Calculation Assumption

Subscription Duration was calculated as:

```
Subscription Duration = Cancellation Date – Subscription Start Date
```

For students without a cancellation date:

* Cancellation Date was replaced with **TODAY()**
* These students were assumed to have **active subscriptions**

This assumes:

* Students without cancellation dates are still subscribed
* Duration calculated using TODAY() is a reasonable estimate of active duration

---

## 4. Trend Benchmark Period Assumption

Students were grouped into:

* **Pre-2025**
* **Post-2025**

Based on:

* Last Login Date Year

This assumes:

* Last login activity reflects the student's engagement period
* Students active after 2025 represent **recent engagement trends**
* Students active before 2025 represent **earlier engagement patterns**

---

## 5. Equal Weight Engagement Assumption

Engagement activities such as:

* Watching videos
* Completing assignments
* Posting in forums
* Attempting quizzes

Were treated as **equally important** in determining engagement level.

In reality:

* Some activities may contribute more to learning outcomes than others
* But equal weighting simplifies classification and analysis

---

# Constraints

## 1. No True Time-Series Data

The dataset does not contain:

* Daily activity logs
* Monthly activity logs
* Historical engagement tracking

Because of this:

* True engagement trends over time cannot be calculated
* Only **snapshot comparisons** can be performed

This limits the ability to perform:

* Cohort analysis
* Retention curves
* Engagement growth over time

---

## 2. No Revenue Data

The dataset does not include:

* Subscription price
* Revenue per student
* Discounts
* Payment history

Because of this:

* Financial impact of churn cannot be calculated
* Revenue-based KPIs cannot be created
* Customer Lifetime Value cannot be computed

Analysis is therefore **engagement-focused, not revenue-focused**.

---

## 3. No Course Difficulty or Content Data

The dataset does not include:

* Course difficulty level
* Course category
* Instructor quality
* Course length
* Content type

Therefore:

* Engagement differences cannot be attributed to course quality or difficulty
* Only student behavior metrics can be analyzed

---

## 4. No Demographic or Background Data

The dataset does not contain:

* Age
* Education level
* Country
* Profession
* Prior experience

Because of this:

* Segmentation analysis is limited
* Behavioral differences across demographics cannot be studied

---

## 5. Engagement Metrics Are Quantitative Only

Engagement is measured only through:

* Counts (videos, assignments, posts, quizzes)

The dataset does not include:

* Student satisfaction
* Course ratings
* Feedback
* Learning outcomes
* Completion quality

Therefore:

* Engagement quality cannot be measured
* Only engagement quantity can be analyzed

---

# Summary

## Key Assumptions

* Dataset is a snapshot, not time-series
* Engagement level is rule-based classification
* Students without cancellation dates are active
* Last login date represents engagement period
* Engagement activities are equally weighted

## Key Constraints

* No historical activity logs
* No revenue data
* No course difficulty/content data
* No demographic data
* Engagement quality not measured

---

**Note:** Despite these assumptions and constraints, the dataset provides sufficient information to analyze student engagement behavior, subscription patterns, and churn risk indicators, which form the basis of the benchmarks and insights developed in this project.

---

**Project:** Student Engagement Analysis

**Document Purpose:** Metric transparency and analytical clarity

**Author:** Ananya Jha
