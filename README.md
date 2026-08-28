# Project : Customer Churn Analysis & Revenue Impact

In this Project I have engineered an end-to-end churn analytics pipeline for an OTT subscription platform by integrating multi-table subscriber data across acquisition type, contract structure, and plan tier (20+ KPIs). Uncovered a significant churn disparity between monthly and annual contract segments, quantified MRR leakage and CLTV erosion attributed to high-risk cohorts, and delivered a data-backed contract-migration retention strategy to reduce involuntary subscriber loss.


**The Business Challenge/ The Problem Statement:**

In the hyper-competitive OTT landscape (Netflix, Hotstar, Prime), retention is the only way to survive. As a Business and Data Analyst I want to identifying high-risk subscribers using a multi-dimensional dataset (Customer demographics, Subscription tiers, and Support escalations).


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

## Data Analysis Insight

1. Churn rate: 28.57% | Retention rate: 71.43% 
2. Average tenure of customers is ~1,527 days (~4.2 years).
3. Plan Type — Basic plan is the weak point
    Basic: 60% churn
    Standard: 22.22% churn
    Premium: 14.29% churn (lowest)
    → Customers on the cheapest plan churn 4x more than Premium customers.
4.Subscription Type — Referral customers are the biggest risk, and least valuable
    Referral: 83.33% churn, but only ₹1,524 total CLTV across the group
    Paid: 16.67% churn, ₹7,410 CLTV
    Organic: 0% churn, and the highest CLTV at ₹8,360
    strongest finding: organic customers are both the most loyal and the most valuable, while referral-acquired customers churn hardest and contribute the least revenue — worth revisiting the referral program.
5.Geography — churn and revenue don't move together
    Karnataka: 100% churn (but small revenue base — ₹1,420)
    Meghalaya: 66.67% churn
    Telangana: 50% churn
    Uttar Pradesh & Maharashtra: 0% churn, and the two highest-revenue states (₹4,140 and ₹3,027)
    → High-churn states aren't your high-revenue states here, which matters for prioritizing retention spend.
6.Revenue Impact
    ARPU: ₹18.85/month
    Revenue at risk from churned customers: ₹73.94/month combined
    Interestingly, churned customers had a lower average monthly charge (₹12.32) than the overall ARPU — cheaper-plan customers are leaving, not your highest payers.
7. % Revenue loss = 18%
    monthly vs annual churn = 55.6% vs 8.3%
8. Support & Escalations
    Escalation rate: 19.05% of interactions
    Correlation between escalation and churn: 0.47 — a moderate positive relationship, suggesting escalated support tickets are a real (though not sole) churn driver.
    Average complaints per customer: 0.43.
9. Most of the churn happened in the month of Sep 2024 and, most affected state is Karnataka



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

## Visualization Output

  <img width="692" height="315" alt="Monthly churn trend" src="https://github.com/user-attachments/assets/e9c89a37-b037-44c2-9ee6-e38ee791a5ca" />
  <img width="1024" height="508" alt="weekwise_churn_trend" src="https://github.com/user-attachments/assets/f3192456-2e2c-4058-9557-84ba8cd5eccb" />
  <img width="846" height="393" alt="Churn by plan_type" src="https://github.com/user-attachments/assets/ad7542d0-e4cd-45d6-8d37-c374cc74ae59" />
  <img width="1010" height="392" alt="Churn count by state" src="https://github.com/user-attachments/assets/a9db8f91-7b7c-46e6-a1d3-85112e4aab73" />
  <img width="1001" height="392" alt="Churn by state1" src="https://github.com/user-attachments/assets/9138dfbf-820d-410f-af60-1c1423c99581" />
  <img width="610" height="501" alt="heatmap (correlation matrix)" src="https://github.com/user-attachments/assets/6650f9f9-e2a3-4309-98f3-107141f134d2" />
  <img width="1476" height="1476" alt="pairplot -relationship in a dataset" src="https://github.com/user-attachments/assets/6f4d8ddc-0196-4845-801b-818a04180e84" />
  <img width="1596" height="490" alt="catplot or facegrid plot" src="https://github.com/user-attachments/assets/11db255e-6f38-404c-baa5-8781d53cb150" />









