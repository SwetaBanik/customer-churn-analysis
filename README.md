# Project : Customer Churn Analysis & Revenue Impact

In this Project I have engineered an end-to-end churn analytics pipeline for an OTT subscription platform by integrating multi-table subscriber data across acquisition type, contract structure, and plan tier (20+ KPIs). Uncovered a significant churn disparity between monthly and annual contract segments, quantified MRR leakage and CLTV erosion attributed to high-risk cohorts, and delivered a data-backed contract-migration retention strategy to reduce involuntary subscriber loss.


**The Business Challenge/ The Problem Statement:**

In the hyper-competitive OTT landscape (Netflix, Hotstar, Prime), retention is the only way to survive. As a Business and Data Analyst I want to identifying high-risk subscribers using a multi-dimensional dataset (Customer demographics, Subscription tiers, and Support escalations).

**Approach**

An end-to-end exploratory data analysis of available database containing customer, subscription, and support-ticket data. 
The project covers:
1. Data cleaning
2. Feature engineering
3. KPI calculation
4. visualization
to understand who is churning, why, and where revenue is at risk.

## 📌 Project Overview

An end-to-end exploratory data analysis of `customer_churn.db` SQLite database containing customer, subscription, and support-ticket data. 
The project covers:
1. Data cleaning
2. Feature engineering
3. KPI calculation
4. visualization
to understand who is churning, why, and where revenue is at risk.

`customer_churn.db` is the Project database which contains three tables:

- Table 1: **customer** — customer demographics (name, dob, gender, country, state, etc.)
- Table 2: **subscription** — subscription details (plan_type, contract_type, subscription_start_date, renewal_date, cancellation_date, monthly_charges, cltv, churn_score, etc.)
- Table 3: **support** — support ticket history (complaint_date, escalations, csat_score)

In this project I have
- Cleand and standardized raw data (renaming columns, fixing dtypes,standardizing categorical values, imputing missing `country` from `state`)
- Joined the three tables into a single analysis-ready dataset
- Engineered new features: `churn_flag`, customer `age`, `tenure_days`, `complaint_count`, `Escalation` (encoded), and `churn_risk` segments
- Calculated key churn KPIs
- Visualized churn trends and relationships with matplotlib and seaborn

## 📊 Key Metrics Calculated

|                        Metric                  | Description                                          |
|------------------------------------------------|------------------------------------------------------|
|                    Churn Rate / Retention Rate | % of customers who cancelled vs. retained            |
| Churn by Plan Type / State / Subscription Type | Segmented churn rates                                |
|                                           ARPU | Average Revenue Per User (avg. monthly charges)      |
|                                Revenue at Risk | Total monthly charges tied to churned customers      |
|                          Customer Age & Tenure | Derived from DOB and subscription dates              |
|                                Escalation Rate | % of customers with an escalated support ticket      |
|                   Escalation–Churn Correlation | Relationship between escalations and churn           |
|                            Churn Risk Segments | Low / Medium / High, based on `churn_score`          |

## 📈 Visualizations

- Monthly & weekly churn trend (time series)
- Churn rate by plan type and by state (bar charts)
- Correlation heatmap of encoded features
- Pairplot of numeric/encoded features
- Catplot: monthly charges by plan type, gender, and churn risk
- Pivot tables summarizing churn, revenue, and customer counts by plan type

## 🗂️ Project Structure

```
churn-analysis/
├── README.md                             # Project Overview
├── churnanalysis.ipynb                   # main analysis notebook
├── customer_churn.db                     # database file
└── exported_churn_data.csv               # exported CSVs / summary outputs
└── .ipynb_checkpoints    
└── Data Visualization                    # Visualization output


```

## 🛠️ Tech Stack

- Python 3
- pandas, numpy
- matplotlib, seaborn
- sqlite3
- Jupyter Notebook

