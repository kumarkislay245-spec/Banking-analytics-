![Banking Analytics Banner](banking_readme_banner.png)

# 🏦 Banking Analytics

> Analyzing banking data to uncover customer trends, transaction behavior, and financial performance using SQL, Python, and Power BI.

---

## 📌 Overview

This project performs end-to-end analysis on a banking dataset to derive actionable business insights. It covers data cleaning, exploratory data analysis (EDA), SQL-based querying, and data visualization — helping simulate how banks can leverage data for smarter decisions.

---

## 🎯 Objectives

- Understand **customer behavior** and segment high-value customers
- Analyze **transaction patterns** — deposits, withdrawals, and account activity
- Evaluate **loan distribution** across customer segments
- Detect **financial trends** to support risk management
- Present findings through **interactive dashboards**

---

## 🗂️ Dataset

The dataset includes the following key entities:

| Table / Feature     | Description                                      |
|---------------------|--------------------------------------------------|
| Customer Details    | Demographics, account type, customer ID          |
| Account Info        | Balances, account status, account creation date  |
| Transactions        | Transaction type, amount, date, channel          |
| Loan Records        | Loan type, amount, repayment status              |

> ⚠️ *The dataset used is for educational/analytical purposes only.*

---

## 📊 Dashboard Screenshots

### 🎯 Problem Statement
![Problem Statement](img1_problem_statement.png)

---

### 🏠 Home — Overview Dashboard
![Home Dashboard](img2_home_male.png)

![Home Dashboard — Female Filter](img3_home_female.png)

---

### 💰 Loan Analysis
![Loan Analysis](img4_loan_analysis.png)

---

### 🏦 Deposit Analysis
![Deposit Analysis](img5_deposit_analysis.png)

---

### ⚠️ Risk Insights
![Risk Insights](img6_risk_insights.png)

---

### 🧠 Data Insights
![Data Insights](img7_data_insights.png)

---

### 📋 Action Plan
![Action Plan](img8_action_plan.png)

---

## 🔍 Key Analyses

### 1. 👥 Customer Segmentation
- Identify high-value customers based on balance and transaction frequency
- Segment by account type and activity level

### 2. 💳 Transaction Analysis
- Trends in deposits vs. withdrawals over time
- High-frequency transaction detection
- Channel-wise transaction breakdown (online, branch, ATM)

### 3. 🏠 Loan Analysis
- Distribution of loan amounts by customer segment
- Loan approval vs. default patterns
- Risk profiling based on repayment behavior

### 4. 📊 Account Activity
- Dormant vs. active account identification
- Balance trend analysis over time

---

## 🛠️ Tools & Technologies

| Category         | Tools                              |
|------------------|------------------------------------|
| Language         | Python, SQL                        |
| Data Processing  | Pandas, NumPy                      |
| Visualization    | Matplotlib, Power BI               |
| Database         | PostgreSQL                         |
| IDE              | Jupyter Notebook, VS Code          |
| Productivity     | MS Excel                           |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2-binary jupyter
```

### Clone the Repository

```bash
git clone https://github.com/your-username/banking-analytics.git
cd banking-analytics
```

### Run the Notebook

```bash
jupyter notebook notebooks/banking_analytics.ipynb
```

### SQL Setup

```sql
CREATE DATABASE banking;
-- Connect and run your schema/data import scripts
```

---

## 📁 Project Structure

```
banking-analytics/
│
├── data/
│   ├── raw/                        # Raw dataset files
│   └── cleaned/                    # Cleaned & processed data
│
├── notebooks/
│   └── banking_analytics.ipynb    # Main analysis notebook
│
├── sql/
│   ├── schema.sql                  # Table creation scripts
│   └── queries.sql                 # Analysis queries
│
├── dashboards/
│   └── banking_dashboard.pbix     # Power BI dashboard
│
├── screenshots/                   # Dashboard screenshots
│
└── README.md
```

---

## 💡 Sample SQL Queries

```sql
-- Top 10 high-value customers by balance
SELECT customer_id, name, account_type, balance
FROM customers
ORDER BY balance DESC
LIMIT 10;

-- Monthly transaction trend
SELECT DATE_FORMAT(transaction_date, '%Y-%m') AS month,
       SUM(CASE WHEN type = 'deposit' THEN amount ELSE 0 END) AS total_deposits,
       SUM(CASE WHEN type = 'withdrawal' THEN amount ELSE 0 END) AS total_withdrawals
FROM transactions
GROUP BY month
ORDER BY month;

-- Loan default rate by customer segment
SELECT segment,
       COUNT(*) AS total_loans,
       SUM(CASE WHEN status = 'defaulted' THEN 1 ELSE 0 END) AS defaults,
       ROUND(SUM(CASE WHEN status = 'defaulted' THEN 1 ELSE 0 END) * 100.0 / COUNT(*), 2) AS default_rate
FROM loans
JOIN customers USING(customer_id)
GROUP BY segment;
```

---

## 📈 Results & Insights

- 🔎 Checking Accounts & Bank Deposits have **extremely high correlation (0.84)** — indicating low-risk, stable customers
- 💼 Business Lending correlates moderately with Bank Loans — **dual credit exposure risk zone**
- ⚠️ Male customers show **higher probability of credit default** than females
- 📊 European customers hold the **highest total loans (1.94bn)** across all nationalities
- 💳 Females distribute credit across 2–3 cards (lower risk); males concentrate on 1 card (higher pressure)

---

## 🧠 Business Impact

| Insight                            | Business Value                                   |
|------------------------------------|--------------------------------------------------|
| High-value customer identification | Targeted retention & loyalty programs            |
| Loan default risk profiling        | Improved credit risk management                  |
| Gender-based risk weighting        | Tailored underwriting and credit products        |
| Loyalty classification analysis    | Tiered rewards and re-engagement strategies      |
| Occupation-based risk patterns     | Flexible EMI structures for irregular income     |

---

## 👤 Author

**Kislay Kumar**
B.Tech Chemical Engineering — NIT Warangal (2028)
📧 kumarkislay245@gmail.com

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

*⭐ If you found this project useful, consider giving it a star!*
