# Dataset Understanding

## Dataset Source

**Dataset Name:** IBM Telco Customer Churn Dataset

**Source:** Kaggle / IBM

**Problem Type:** Binary Classification

**Target Variable:** Churn

**Total Rows:** 7043

**Total Columns:** 33

---

## Feature Description

| Feature           | Description                                        |
| ----------------- | -------------------------------------------------- |
| CustomerID        | Unique identifier for each customer                |
| Count             | Count of customer records (usually 1 for each row) |
| Country           | Customer's country                                 |
| State             | Customer's state/province                          |
| City              | Customer's city                                    |
| Zip Code          | Postal code of customer                            |
| Lat Long          | Combined latitude and longitude coordinates        |
| Latitude          | Geographic latitude                                |
| Longitude         | Geographic longitude                               |
| Gender            | Customer gender                                    |
| Senior Citizen    | Whether customer is a senior citizen (Yes/No)      |
| Partner           | Whether customer has a partner                     |
| Dependents        | Whether customer has dependents                    |
| Tenure Months     | Number of months customer stayed with company      |
| Phone Service     | Whether customer uses phone service                |
| Multiple Lines    | Whether customer has multiple phone lines          |
| Internet Service  | Type of internet service                           |
| Online Security   | Whether online security service is subscribed      |
| Online Backup     | Whether online backup service is subscribed        |
| Device Protection | Whether device protection service is subscribed    |
| Tech Support      | Whether technical support service is subscribed    |
| Streaming TV      | Whether streaming TV service is subscribed         |
| Streaming Movies  | Whether streaming movies service is subscribed     |
| Contract          | Customer contract type                             |
| Paperless Billing | Whether paperless billing is enabled               |
| Payment Method    | Customer payment method                            |
| Monthly Charges   | Monthly bill amount                                |
| Total Charges     | Total amount charged during customer lifetime      |
| Churn Label       | Target variable (Yes/No)                           |
| Churn Value       | Numeric representation of churn (0/1)              |
| Churn Score       | Company-generated churn risk score                 |
| CLTV              | Customer Lifetime Value                            |
| Churn Reason      | Reason customer left the company                   |

---

## Dataset Summary

* Total Records: 7043
* Total Features: 33
* Missing Values Present: Yes (Churn Reason)
* Duplicate Records: 0

### Data Types

* Object (Categorical): 24
* Integer: 6
* Float: 3

---

## Numerical Features

| Feature         |
| --------------- |
| Count           |
| Zip Code        |
| Latitude        |
| Longitude       |
| Tenure Months   |
| Monthly Charges |
| Total Charges   |
| Churn Value     |
| Churn Score     |
| CLTV            |

---

## Categorical Features

| Feature           |
| ----------------- |
| CustomerID        |
| Country           |
| State             |
| City              |
| Lat Long          |
| Gender            |
| Senior Citizen    |
| Partner           |
| Dependents        |
| Phone Service     |
| Multiple Lines    |
| Internet Service  |
| Online Security   |
| Online Backup     |
| Device Protection |
| Tech Support      |
| Streaming TV      |
| Streaming Movies  |
| Contract          |
| Paperless Billing |
| Payment Method    |
| Churn Label       |
| Churn Reason      |

---

## Feature Categories

### Demographic Features

* Gender
* Senior Citizen
* Partner
* Dependents

### Geographic Features

* Country
* State
* City
* Zip Code
* Latitude
* Longitude

### Service Features

* Phone Service
* Multiple Lines
* Internet Service
* Online Security
* Online Backup
* Device Protection
* Tech Support
* Streaming TV
* Streaming Movies

### Financial Features

* Monthly Charges
* Total Charges
* CLTV

### Contract Features

* Contract
* Paperless Billing
* Payment Method

### Target Features

* Churn Label
* Churn Value

---

## Missing Values Analysis

| Feature            | Missing Values |
| ------------------ | -------------- |
| Churn Reason       | 5174           |
| All Other Features | 0              |

### Observation

Only the `Churn Reason` feature contains missing values.

This behavior is expected because churn reasons are only recorded for customers who have already left the company.

The feature will likely be excluded from predictive modeling because:

* It contains a large number of missing values.
* It becomes available only after churn occurs.
* It introduces target leakage.

---

## Duplicate Records Analysis

No duplicate records were found in the dataset.

**Duplicate Count:** 0

This indicates that each row represents a unique customer record.

---

## Target Variable Analysis

| Churn Status | Percentage |
| ------------ | ---------- |
| No (0)       | 73.46%     |
| Yes (1)      | 26.54%     |

### Observation

The dataset is moderately imbalanced.

Most customers remain with the company, while approximately one-fourth of customers churn.

This imbalance should be considered during model evaluation and may require techniques such as:

* Class Weights
* Oversampling
* SMOTE

Accuracy alone may not be a reliable metric.

Metrics such as Precision, Recall, and F1-Score should be emphasized during model evaluation.

---

## Dataset Quality Assessment

### Strengths

* Large dataset containing 7043 customer records.
* No duplicate records.
* No missing values except in Churn Reason.
* Contains demographic, geographic, service, contract, and financial information.
* Suitable for both supervised and unsupervised learning tasks.

### Challenges

* Moderately imbalanced target variable.
* Large number of categorical features requiring encoding.
* Presence of potential data leakage features.
* Geographic features may require careful preprocessing.

---

## Potential Data Leakage

The following columns may leak information about the target variable and should be investigated before model training.

| Feature      | Reason                                      |
| ------------ | ------------------------------------------- |
| Churn Label  | Duplicate representation of target          |
| Churn Score  | Appears to be a precomputed churn indicator |
| Churn Reason | Available only after customer churns        |

These features will likely be removed before training.

---

## Preliminary Feature Removal Candidates

| Feature      | Reason                                |
| ------------ | ------------------------------------- |
| CustomerID   | Unique identifier                     |
| Count        | Constant value                        |
| Lat Long     | Redundant with Latitude and Longitude |
| Churn Label  | Duplicate target                      |
| Churn Score  | Data leakage                          |
| Churn Reason | Data leakage                          |

### Additional Observation

The `Count` column contains a single constant value for all observations and provides no predictive information.

Final decisions regarding feature removal will be made after Exploratory Data Analysis (EDA).

---

## Exploratory Data Analysis Objectives

The EDA phase will focus on:

1. Understanding churn distribution.
2. Investigating relationships between customer attributes and churn.
3. Identifying important predictive features.
4. Detecting outliers and anomalies.
5. Exploring geographic churn patterns.
6. Understanding service usage patterns among churned customers.
7. Preparing insights for feature engineering.

---

## Exploratory Data Analysis Questions

1. Does tenure affect churn?
2. Does contract type affect churn?
3. Does monthly charge affect churn?
4. Are senior citizens more likely to churn?
5. Which services are most associated with churn?
6. Do geographic regions show different churn patterns?
7. Which customer segments have the highest churn risk?
8. Which features appear most influential for churn prediction?
9. Are there hidden customer groups that can be discovered through clustering?
10. What insights can be leveraged to improve customer retention strategies?
