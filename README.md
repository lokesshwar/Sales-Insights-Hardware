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
In this project, we analyzed sales data for AtliQ Hardware, an India-based company that supplies computer hardware and peripherals to clients like Surge Stores and Nomad Stores across the country. Headquartered in Delhi, AtliQ Hardware operates multiple regional offices throughout India.

The company’s Sales Director was facing significant challenges in tracking sales performance amidst a rapidly growing market. Despite having regional managers for North, South, and Central India, he relied on verbal updates during phone calls to understand regional performance. These conversations lacked data-backed insights, leaving him frustrated as overall sales continued to decline without a clear understanding of the underlying issues.

To address this problem, the Sales Director sought a simple, data-driven solution to monitor performance and make informed decisions. Our project aimed to create an interactive sales dashboard using Power BI. This tool provides real-time insights, enabling the Sales Director to track regional performance effectively, identify trends, and drive data-informed strategies to boost sales growth.

---
## 🧩 Data Discovery
**Project Planning (AIMS Grid):**
- **Purpose:** Provide sales insights to support decision-making and reduce manual data gathering.
- **Stakeholders:** Sales Director, Marketing, Analytics, and IT teams.
- **End Result:** An automated sales dashboard for real-time insights.
- **Success Criteria:** Time savings and improved decision-making from data insights.

---
## 🗃️ Data Analysis using SQL
Completed the Data discovery and then used mySQL for data analysis.

SQL database dump is in db_dump.sql file above. Download db_dump.sql file to your local computer

Importing Data to MySQL workbench.
The import of data is done from an already existing MySQL file. This file has to be loaded into MySQL workbench for further data analysis.

Analysis of data by looking into different tables and reflecting garbage values

We can see that garbage value that the table market cantains certain values which are incorrect.

`SELECT * FROM sales.market;`

And then we can check that transacation table we can see that ceratin negative value in amount which is not possible. and we can see that certain transactions are in USD. Hence, filtration of that is also needed by converting into INR.

`SELECT * FROM sales.transactions;`

Analysis of different SQL statement on data base

1.To find of all customers records

`SELECT * FROM sales.customers;`

2.To find total number of customers

`SELECT count(*) From sales.customers;`

3.To find transactions for Chennai market (market code for chennai is Mark001

`SELECT * FROM sales.transactions where market_code='Mark001';`

4.To find distrinct product codes that were sold in chennai

`SELECT distinct product_code FROM sales.transactions where market_code='Mark001';`

5.To find transactions for Chennai market (market code for chennai is Mark002

`SELECT * FROM sales.transactions where market_code='Mark002';`

6.To find distrinct product codes that were sold in mumbai

`SELECT distinct product_code FROM sales.transactions where market_code='Mark002';`

7.To find transactions where currency is US dollars

`SELECT * from sales.transactions where currency="USD";`

8.To find transactions in 2020 join by date table

SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020;

8.To find transactions in 2019 join by date table

`SELECT sales.transactions.*, sales.date.* FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019;`

9.To find total revenue in year 2020,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`

10.To find total revenue in year 2019,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2019 and sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r";`

11.To find total revenue in year 2020, January Month,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`

12.To find total revenue in year 2020, February Month,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`

13.To find total revenue in year 2019, January Month,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="January" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`

14.To find total revenue in year 2019, February Month,

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.date.month_name="February" and (sales.transactions.currency="INR\r" or sales.transactions.currency="USD\r");`

15.To find total revenue in year 2020 in Chennai

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark001";`

16.To find total revenue in year 2020 in Mumbai

`SELECT SUM(sales.transactions.sales_amount) FROM sales.transactions INNER JOIN sales.date ON sales.transactions.order_date=sales.date.date where sales.date.year=2020 and sales.transactions.market_code="Mark002";`

Similarly, if we want different of any other particular city the market code of that city is used on the mysql workbench.

---
## 🔧 Data Cleaning and ETL
In this process, we are work on data cleaning and ETL.

Step 1: Connect the MySQL database with the PowerBI desktop.

Step 2: Loading data into the Power BI deskstop. This step load all the tables and created in the data base. This load option will connect with the SQL and pull all the records into power BI environment.

In that model view looking up for model which form the star schema.

Setp 3: Transform data with the help of Power Query

Perform filtration in market’s table: In the tables perform when we click on the transform data option, we are directed to Power query editor. Power query editor is where we perform out ETL.and then we can perform data transformation i.e. Data Cleaning, Data Wrangling, Data Munging. we need to filter the rows where the values are null and filtering the data and deselecting the blank option.

Perform filtration in Transaction’s table: In the table perform when we check the query in the MySQL to filter some negative values and also 0 values that appears in the table, the desired output is received.and we will perform the similar filtration in PowerBI. we have deselecting the values, don’t want in the table. The result after filtration. the zero values represent some garbage values which is not possible so we need to clean that data.

Convert USD into INR in the transaction’s table: the AtliQ Hardware only works in India so the USD values are not possible. we need to convert those USD values into INR by using some formulas. Add new column - Conditional column - normalized currency where sales amount will be in INR

In power query editore finding the total values having USD as currency.
 `=Table.AddColumn(#"Filtered Rows", "norm_sales_amount",each if [currency] = "USD" then [sales_amount]*75 else [sales_amount]`
 using this correct formula of the conversion,and converted the USD currency into INR.

In MySQL Workbench find that there are duplicates of USD and INR
 `SELECT count(*) from sales.transactions where sales.transactions.currency="INR\r";` 
 150000 - can't removed as it is large amount

 `SELECT count(*) from sales.transactions where sales.transactions.currency="INR";` 
 279 - we can remove it as it is small record and can be considered as bad data

 `SELECT count(*) from sales.transactions where sales.transactions.currency="USD\r";` 

 `SELECT count(*) from sales.transactions where sales.transactions.currency="USD";`

 `SELECT * from sales.transactions where sales.transactions.currency='USD\r' or sales.transactions.currency='USD';`
 we can see that it is duplicate and for analysis its better to delete anyone of them so lets delete USD and keep USD/r. finally we will keep data with INR/r and USD/r-

---
## 📊 Data Modeling
Created a star schema for optimized analysis with related tables for transactions, products, customers, and markets.

---
## 📈 Data Analysis (DAX)
Measures used in all visualization are:

Key Measures:

- Profit Margin % = DIVIDE([Total Profit Margin],[Revenue],0)
- Profit Margin Contribution % = DIVIDE([Total Profit Margin],CALCULATE([Total Profit Margin],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))
- Revenue = SUM('sales transactions'[sales_amount])
- Revenue Contribution % = DIVIDE([Revenue],CALCULATE([Revenue],ALL('sales products'),ALL('sales customers'),ALL('sales markets')))
- Revenue LY = CALCULATE([Revenue],SAMEPERIODLASTYEAR('sales date'[date]))
- sales quntity = SUM('sales transactions'[sales_qty])
- Total Profit Margin = SUM('Sales transactions'[Profit_Margin])
- Profit Target:

Profit Target1 = GENERATESERIES(-0.05, 0.15, 0.01)
Profit Target Value = SELECTEDVALUE('Profit Target1'[Profit Target])
Target Diff = [Profit Margin %]-'Profit Target1'[Profit Target Value]

---
## 📊 Dashboard and Report
Built an interactive Power BI dashboard to visualize sales performance, customer trends, and market profitability.

---
## 🛠️ Tools and Technologies Used
- MySQL (Data Analysis)
- Microsoft Power BI (Visualization)
- Power Query Editor (ETL)
- DAX (Data Analysis Expressions)
