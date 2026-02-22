# Telco Customer Churn Analysis: From Raw Data to Business Insight

**By Rodas Berhane** | MSc Business Analytics Candidate, UCD Smurfit Dublin  
**Tools Used:** Python · Pandas · SQL · Tableau  
**Dataset:** IBM Telco Customer Churn — 7,043 customers · 40 features  
**Live Dashboard:** [View on Tableau Public](https://public.tableau.com/app/profile/rodiiberhane/viz/churnpredictionviz/Dashboard1)  
**GitHub:** [github.com/rodberhane](https://github.com/rodberhane)

---

## The Problem

Every subscription business faces the same silent threat — customers quietly walking out the door. In telecoms, this is called **churn**, and it costs the industry billions every year. The brutal truth is that acquiring a new customer costs 5 to 7 times more than keeping an existing one. Yet most businesses only find out a customer has left after it's already too late.

This project set out to answer one question:

> *"Who is most likely to leave — and what does the data tell us about why?"*

---

## The Approach

Rather than jumping straight into visualization, I treated this like a real analyst workflow — starting with messy raw data and working through every layer before a single chart was drawn.

### Step 1 — Data Cleaning (Python & Pandas)

The raw dataset arrived with 50 columns and several data quality issues that would have produced misleading results if left unaddressed:

- **3,877 missing values** in the `Offer` column — filled with "No Offer" to reflect customers on no promotional plan
- **1,526 missing values** in `Internet Type` — filled with "No Internet" for customers without internet service
- **Data leakage risk** — columns like `Churn Score`, `CLTV`, `Churn Category` and `Churn Reason` were dropped entirely. These fields are only populated *after* a customer has already churned, meaning a real predictive model would never have access to them. Keeping them would have produced artificially inflated results
- **Irrelevant location columns** removed — `Country`, `State`, `Zip Code`, `Latitude`, `Longitude`, `Population` were dropped to keep the analysis focused on behavioural and service features

**Output:** A clean, analysis-ready dataset of 7,043 customers across 40 meaningful features.

### Step 2 — Data Querying (SQL with Pandas)

With clean data in hand, four targeted SQL-style queries were written to extract the key business metrics driving churn:

- Churn rate by **Contract Type**
- Churn rate by **Internet Service Type**
- Churn rate by **Payment Method**
- Churn rate trend by **Customer Tenure**

Each query calculated total customers, total churned, and churn rate percentage — transforming 7,000 rows into clear, actionable summaries.

### Step 3 — Visualization (Tableau)

The cleaned and queried data was connected directly to Tableau to build an interactive dashboard telling the full churn story across four visualizations.

---

## What the Data Revealed

### Finding 1 — Contract Type is the Strongest Churn Signal

Month-to-month customers churn at a staggering **45.84%** compared to just **10.71%** for one-year contracts and **2.55%** for two-year contracts. This single finding alone has massive business implications — the flexibility customers demand most is also the biggest churn risk the business carries.

**Business implication:** Incentivizing customers to commit to annual or two-year contracts — through discounts, loyalty perks, or bundled services — could reduce churn by up to 43 percentage points among the most at-risk segment.

### Finding 2 — The First 12 Months Are Make or Break

The tenure line chart tells a compelling story. Churn starts at over **62%** in month one and follows a clear downward trend across 72 months, bottoming out near zero for long-term customers. The negative trend line confirms what retention specialists already know — if you can keep a customer beyond their first year, you are likely to keep them for life.

**Business implication:** The onboarding experience is everything. Investment in early customer success programs, welcome offers, and proactive support in the first 90 days would have the highest return on investment of any retention strategy.

### Finding 3 — Payment Method Signals Customer Engagement

Customers paying by Mailed Check churn at **36.88%** while Credit Card users churn at just **14.48%** — a gap of over 22 percentage points. This is not coincidental. Customers who set up automatic digital payments are demonstrably more engaged and more invested in the relationship with the business.

**Business implication:** Encouraging customers to switch to automatic payment methods — through small incentives or a simplified setup experience — could meaningfully reduce churn without changing the product or price at all.

### Finding 4 — Geographic Concentration of Churn

The symbol map reveals that churn is not evenly distributed geographically. Certain cities show higher churn concentrations, pointing to possible regional factors such as local competition, service quality inconsistencies, or demographic patterns that warrant further investigation.

**Business implication:** A regional marketing or retention strategy targeting high-churn cities could be more cost-effective than a blanket national campaign.

---

## Key Takeaways

| Driver | Churn Rate | Business Action |
|--------|-----------|-----------------|
| Month-to-Month Contract | 45.84% | Incentivize annual contracts |
| Tenure < 12 Months | 60%+ | Invest in onboarding and early retention |
| Mailed Check Payment | 36.88% | Encourage digital auto-pay |
| Fiber Optic Internet | Higher than DSL | Review pricing vs perceived value |
| Two-Year Contract | 2.55% | Reward and protect loyal customers |

---

## What's Next

This analysis is the foundation of a larger end-to-end project. The next phase builds a **machine learning model** — using Logistic Regression, Random Forest, and XGBoost — that takes a customer's profile and predicts their individual probability of churning in real time. The model is then deployed as a **Streamlit web application**, turning the insights from this analysis into a live, interactive business tool.

Together, the Tableau dashboard answers *"what happened and why"* while the ML app answers *"who is at risk next."*

---

## Tools & Technologies

| Tool | Role in Project |
|------|----------------|
| Python (Pandas) | Data cleaning, null handling, feature selection |
| SQL (Pandas GroupBy) | Aggregation queries and churn rate calculations |
| Tableau Public | Interactive dashboard and data storytelling |
| Jupyter Notebook | Development and documentation environment |

---

## About the Author

I am Rodas Berhane, an Applied Mathematics graduate with a minor in Computer Science, currently completing my MSc in Business Analytics at UCD Michael Smurfit Graduate Business School in Dublin. I am passionate about turning complex data into clear business decisions — and this project is one example of that in practice.

- 🔗 [LinkedIn](https://www.linkedin.com/in/rodasokubagabir)
- 🐙 [GitHub](https://github.com/rodberhane)
- 📊 [Tableau Public](https://public.tableau.com/app/profile/rodiiberhane)
- 📧 rodas.okubagabir@ucdconnect.ie
