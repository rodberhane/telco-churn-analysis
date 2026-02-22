# telco-churn-analysis
# 📊 Telco Customer Churn Analysis & Prediction

**Author:** Rodas Berhane  
**Tools:** Python · SQL · Tableau  
**Dataset:** IBM Telco Customer Churn Dataset (7,043 rows · 50 columns)  
**Live Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/rodiiberhane/viz/churnpredictionviz/Dashboard1)

---

## 📌 Project Overview

Customer churn — when a customer stops using a service — is one of the most costly problems for subscription-based businesses. Acquiring a new customer costs 5 to 7 times more than retaining an existing one. This project analyses historical customer data from a telecommunications company to identify the key drivers of churn and visualize patterns that can help a business take proactive retention action.

**The core question this project answers:**  
*Who is most likely to leave, and why?*

---

## 🎯 Aim & Business Value

- Identify which customer segments have the highest churn risk
- Understand how contract type, tenure, internet service, and payment method influence churn
- Provide actionable business insights through interactive visualizations
- Lay the foundation for a predictive machine learning model (see companion ML project)

---

## 🗂️ Project Structure

```
telco-churn-analysis/
│
├── data/
│   ├── telco.csv                  # Raw dataset (original)
│   └── telco_clean.csv            # Cleaned dataset (Python output)
│
├── notebooks/
│   └── churn_analysis.ipynb       # Full Python cleaning and query notebook
│
├── queries/
│   ├── churn_by_contract.csv      # SQL query results
│   ├── churn_by_internet.csv
│   ├── churn_by_payment.csv
│   └── churn_by_tenure.csv
│
├── dashboard/
│   └── Telco_Churn_Dashboard.twbx # Tableau workbook
│
└── README.md
```

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|------|---------|
| Python (Pandas) | Data cleaning and preprocessing |
| SQL (DuckDB) | Data querying and aggregation |
| Tableau Public | Interactive dashboard and visualization |
| Jupyter Notebook | Development environment |

---

## 🧹 Step 1 — Data Cleaning (Python)

The raw dataset contained missing values, irrelevant columns, and data leakage risks. Python and Pandas were used to clean and prepare the data.

**Issues fixed:**
- `Offer` column: 3,877 null values → filled with "No Offer"
- `Internet Type` column: 1,526 null values → filled with "No Internet"
- Dropped data leakage columns: `Churn Score`, `CLTV`, `Customer Status`, `Churn Category`, `Churn Reason`
- Dropped irrelevant location columns: `Country`, `State`, `City`, `Zip Code`, `Latitude`, `Longitude`, `Population`

**Output:** `telco_clean.csv` — clean, analysis-ready dataset

---

## 🔍 Step 2 — Data Querying (SQL)

Four analytical SQL queries were written using DuckDB and Pandas to extract key business metrics from the cleaned dataset:

- **Churn by Contract Type** — identifies which contract length has highest churn rate
- **Churn by Internet Type** — compares churn across DSL, Fiber Optic and No Internet
- **Churn by Payment Method** — analyses churn rate by how customers pay
- **Churn by Tenure** — measures how churn rate changes over customer lifetime

Each query calculates: Total Customers, Total Churned, and Churn Rate Percentage.

---

## 📊 Step 3 — Visualization (Tableau)

An interactive dashboard was built in Tableau Public with four key visualizations:

### Chart 1 — Churn by Contract Type (Bar Chart)
Month-to-month customers churn at **45.84%** compared to just **2.55%** for two-year contract customers. This highlights contract length as the single strongest retention lever.

### Chart 2 — Churn by Tenure (Line Chart with Trend Line)
Churn rate starts at over **60%** for customers in their first month and declines steadily to near **0%** by month 72. The negative trend line confirms a strong inverse relationship between tenure and churn — the first 12 months are the most critical retention window.

### Chart 3 — Churn by Payment Method (Horizontal Bar Chart)
Customers paying by Mailed Check churn at **36.88%** while Credit Card users churn at only **14.48%**, suggesting customers using modern digital payment methods are more engaged and loyal.

### Chart 4 — Geographic Distribution (Symbol Map)
Maps churn distribution across customer locations, revealing geographic concentration patterns in churn behaviour.

---

## 💡 Key Business Insights

1. **Contract type is the strongest churn predictor** — businesses should incentivize customers to move from month-to-month to annual contracts
2. **The first 12 months are critical** — onboarding programs and early loyalty rewards could significantly reduce early churn
3. **Fiber Optic customers churn more despite premium service** — pricing relative to perceived value needs review
4. **Digital payment methods correlate with lower churn** — encouraging customers to switch to credit card or auto-pay could improve retention

---


## 📁 Dataset Source

IBM Telco Customer Churn Dataset — available on [Kaggle](https://www.kaggle.com/datasets/alfathterry/telco-customer-churn-11-1-3)

---

*This project is part of a larger end-to-end data analytics portfolio. A companion machine learning project builds a predictive churn model using the same dataset with Logistic Regression, Random Forest, and XGBoost, deployed as a Streamlit web application.*
