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
| Database         | MySQL                              |
| IDE              | Jupyter Notebook, VS Code          |
| Productivity     | MS Excel, AI Tools                 |

---

## 🚀 Getting Started

### Prerequisites

```bash
pip install pandas numpy matplotlib scikit-learn jupyter
```

### Clone the Repository

```bash
git clone https://github.com/your-username/banking-analytics.git
cd banking-analytics
```

### Run the Notebook

```bash
jupyter notebook banking_analytics.ipynb
```

### SQL Setup

```sql
-- Import your dataset into MySQL
CREATE DATABASE banking_analytics;
USE banking_analytics;
-- Run schema.sql to create tables
SOURCE schema.sql;
```

---

## 📁 Project Structure

```
banking-analytics/
│
├── data/
│   ├── raw/                  # Raw dataset files
│   └── cleaned/              # Cleaned & processed data
│
├── notebooks/
│   └── banking_analytics.ipynb   # Main analysis notebook
│
├── sql/
│   ├── schema.sql            # Table creation scripts
│   └── queries.sql           # Analysis queries
│
├── dashboards/
│   └── banking_dashboard.pbix    # Power BI dashboard
│
├── visuals/                  # Exported charts & graphs
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

- 🔎 Identified the **top 15% of customers** contributing to over 60% of total deposits
- 📉 Detected a **seasonal dip** in transaction volume during Q1
- ⚠️ Found **higher loan default rates** among customers with low account activity
- 📊 Power BI dashboard provides real-time drill-down by region, account type, and time period

---

## 🧠 Business Impact

| Insight                          | Business Value                                  |
|----------------------------------|-------------------------------------------------|
| High-value customer identification | Targeted retention & loyalty programs          |
| Loan default risk profiling       | Improved credit risk management                |
| Transaction trend analysis        | Optimized staffing and operational planning    |
| Dormant account detection         | Re-engagement campaigns to recover revenue     |

---

## 👤 Author

**Kislay Kumar**  
B.Tech Chemical Engineering — NIT Warangal (2028)  
📧 kumarkislay245@gmail.com  
🔗 [LinkedIn](https://linkedin.com) | [GitHub](https://github.com)

---

## 📄 License

This project is open-source and available under the [MIT License](LICENSE).

---

*⭐ If you found this project useful, consider giving it a star!*
