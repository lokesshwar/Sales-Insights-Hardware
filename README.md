
# Sales Insights of Hardware Business (Power BI Project)

## Table of Contents:
- Problem Statement
- Data Discovery
- Data Analysis using SQL
- Data Cleaning and ETL (Extract, Transform, Load)
- Data Modeling
- Data Analysis (DAX)
- Dashboard and Report
- Tools and Technologies Used

---
## 📝 Problem Statement
The sales director of a hardware business is facing challenges tracking sales performance as overall sales are declining. Insights from regional managers are verbal and lack data-backed proof. The director needs a data visualization tool to monitor sales trends and support data-driven decision-making. This project delivers a Power BI dashboard to address these challenges.

---
## 🧩 Data Discovery
**Project Planning (AIMS Grid):**
- **Purpose:** Provide sales insights to support decision-making and reduce manual data gathering.
- **Stakeholders:** Sales Director, Marketing, Analytics, and IT teams.
- **End Result:** An automated sales dashboard for real-time insights.
- **Success Criteria:** Time savings and improved decision-making from data insights.

---
## 🗃️ Data Analysis using SQL
Performed data analysis using SQL queries to identify trends and outliers:
- Total customers and transactions per market.
- Market-specific sales analysis (e.g., Chennai, Mumbai).
- Yearly and monthly revenue trends.
- Filtered out invalid records (e.g., negative sales amounts, non-INR transactions).

---
## 🔧 Data Cleaning and ETL
**Steps:**
- Connected MySQL database to Power BI.
- Performed data cleaning using Power Query (filtered nulls, removed duplicates, and converted USD to INR).
- Applied transformations to normalize sales amounts.

---
## 📊 Data Modeling
Created a star schema for optimized analysis with related tables for transactions, products, customers, and markets.

---
## 📈 Data Analysis (DAX)
**Key Measures Used:**
- **Revenue:** `SUM('Sales'[sales_amount])`
- **Profit Margin %:** `DIVIDE([Total Profit Margin],[Revenue],0)`
- **Revenue Contribution %:** `DIVIDE([Revenue],CALCULATE([Revenue],ALL('Sales')))`

---
## 📊 Dashboard and Report
Built an interactive Power BI dashboard to visualize sales performance, customer trends, and market profitability.

---
## 🛠️ Tools and Technologies Used
- MySQL (Data Analysis)
- Microsoft Power BI (Visualization)
- Power Query Editor (ETL)
- DAX (Data Analysis Expressions)
