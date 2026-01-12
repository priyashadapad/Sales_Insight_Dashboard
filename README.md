# Sales Insights Dashboard | Power BI & SQL

## 📌 Project Overview
This project analyzes sales performance using **SQL** for data exploration and validation, and **Power BI** for ETL, data modeling, and visualization.
The objective is to transform raw transactional data into **actionable business insights**, enabling stakeholders to track revenue trends, identify high-performing markets, and analyze customer contributions.
________________________________________
## 🛠 Tools & Technologies
- **SQL (MySQL Workbench)** – Data exploration, validation, and business logic checks  
- **Power BI** – ETL, data modeling, and interactive dashboard development  
- **Power Query** – Data cleaning, transformation, and standardization  
- **DAX** – Creation of KPIs and dynamic measures  
________________________________________
## 🗂 Dataset Description
The sales database consists of the following tables:

- **customers** – Customer-level information  
- **date** – Date dimension (year, month, etc.)  
- **markets** – Market and regional details  
- **products** – Product information  
- **transactions** – Sales transaction records  

### Sample SQL Validation Queries
- SELECT COUNT(*) FROM customers;
- SELECT * FROM transactions;
- SELECT DISTINCT currency FROM transactions;
________________________________________

## 🔍 Initial Data Analysis (SQL)
Before loading data into Power BI, exploratory analysis was performed in MySQL Workbench to understand data structure and quality.

Key Findings:
-	Presence of negative and zero sales values
-	Multiple representations of currency (INR, INR\r, USD, USD\r)
-	Revenue variations across years and markets

Example Query:

**Chennai market revenue for the year 2020**

SELECT *
FROM transactions
JOIN date ON transactions.order_date = date.date
WHERE date.year = '2020'
AND market_code = 'MARK001';
________________________________________

## 🔄 ETL & Data Cleaning (Power BI)
All major transformations were handled using Power Query as part of a structured ETL (Extract, Transform, Load) process.

Data Cleaning Steps:

- Removed transactions with negative or zero sales_amount
- Eliminated blank and null values
- Standardized currency values:
   -	Merged INR and INR\r
   -	Merged USD and USD\r
- Converted USD to INR, as the business operates only in the Indian market
-	Ensured consistent data types across all columns
________________________________________

## 💱 Currency Standardization Validation (SQL)

SELECT DISTINCT currency FROM transactions;

SELECT * FROM transactions WHERE currency = 'INR';

SELECT * FROM transactions WHERE currency = 'INR\r';

SELECT * FROM transactions WHERE currency = 'USD';

SELECT * FROM transactions WHERE currency = 'USD\r';
________________________________________

## 📐 Key Measures & KPIs (DAX)

Key business metrics were created using DAX:
- Total Revenue
-	Total Sales Quantity
-	Revenue by Market
-	Revenue Trend (Year / Month)
-	Top 5 Customers by Revenue

These measures dynamically update based on slicers and filters.
________________________________________

## 📊 Dashboard Features

The Power BI dashboard provides:
-	💰 Revenue and Sales KPIs
-	📍 Market-wise Revenue Analysis
-	📈 Time-based Revenue Trends (Year, Quarter, Month, Day)
-	🧍 Top 5 Customers by Revenue
-	🗓 Interactive slicers for year and date filtering
________________________________________

## 📷 Dashboard Preview
<img width="1162" height="732" alt="image" src="https://github.com/user-attachments/assets/5a86dc83-8e3d-41e0-9dae-c2ab36ce5fe4" />

________________________________________
## 🚀 Business Insights
-	Delhi NCR is the highest revenue-contributing market
-	Revenue peaked around 2018 and declined in subsequent years
-	A small group of customers contributes a large share of total revenue
-	Data inconsistencies significantly impacted raw metrics, highlighting the importance of ETL
