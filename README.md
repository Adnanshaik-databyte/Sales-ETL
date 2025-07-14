# 🛒 Sales Analytics Project - Databricks Lakehouse

## 📌 Project Overview

This project analyzes retail sales data using a structured, multi-layered data pipeline on **Databricks**. The goal is to uncover key business insights, such as profit-draining categories, regional trends, customer behavior, and seasonal product performance. The final output is a series of dashboards built on clean, aggregated data.

---

## 🎯 Objectives

- Identify **low-performing product categories**
- Optimize **inventory turnover** and regional sales
- Analyze **seasonal trends** and **customer frequency**
- Deliver **actionable insights** through dashboards

---

## 🛠 Technologies Used

- **Databricks (Community Edition)**
- **PySpark**
- **SQL (Databricks SQL)**
- **Delta Lake**
- **Tableau / Power BI** (for dashboarding)

---

## 🗃 Data Pipeline Architecture

### 1. 🔹 **Raw Layer (Bronze Table)**
- Ingest raw CSV/Parquet files into Databricks using Auto Loader
- Store in Delta format with schema inference
- Minimal transformation: basic parsing and deduplication

### 2. 🔸 **Clean Layer (Silver Table)**
- Apply data cleaning and transformations
- Handle nulls, correct data types, and filter inconsistencies
- Create new columns like `Profit`, `Margin`, `Month`, `Customer_Type`

### 3. 🥇 **Aggregated Layer (Gold Table)**
- Perform grouped aggregations for metrics:
  - Total Sales
  - Profit by City, Category, Product
  - New vs Returning Customer Revenue
- Optimize using **partitioning**, **Z-Ordering**, and **caching**

---

## 📊 Key Dashboards & Visualizations

| Visualization | Description |
|---------------|-------------|
| 📈 Sales Trend Over Time | Monthly revenue pattern |
| 🥇 Top Products by Sales | Best-selling items |
| 🌍 Regional Sales Distribution | Sales by city or location |
| 📦 Category-Level Profitability | Highlighting loss-making categories |
| 👥 Customer Frequency | New vs returning customers |
| 💸 Discount Effectiveness | Impact of discounts on profit margins |
| 🧊 Heatmap of Product-Region Performance | Identify high/low performing zones |
| 📅 Seasonality Analysis | Monthly/quarterly product trends |
| 📐 Inventory Turnover Metrics | Stock velocity by category |
| 🎯 AOV (Avg. Order Value) | Per customer or per city |

---

## 📈 Sample Queries

```sql
-- Total profit by category
SELECT Product_Category, SUM(Profit) AS Total_Profit
FROM silver_sales
GROUP BY Product_Category
ORDER BY Total_Profit ASC;
-- Monthly revenue trend
SELECT MONTH(Sale_Date) AS Month, SUM(Sales) AS Revenue
FROM silver_sales
GROUP BY Month
ORDER BY Month;
🔮 Future Scope
Add forecasting models for sales and demand planning

Integrate with external APIs (e.g., weather, promotions)

Real-time dashboard updates using streaming data

Advanced segmentation (e.g., RFM analysis, cohort modeling)

Implement CI/CD pipelines for automated data workflows

🙋‍♂️ Author
Shaik Adnan
Data Analyst | Databricks Enthusiast
🔗 LinkedIn-www.linkedin.com/in/mohammed-adnan-shaik 
