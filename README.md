
# Retail-Sales-Profit-Analysis-Dashboard.

This project showcases a Power BI dashboard built using a public retail dataset from Kaggle to analyze business performance across categories, departments, and regions.


## Problem Statement

- The company found it difficult to track sales and profit across regions, departments, and product categories.  
- Their reporting process was manual, time-consuming, and not interactive.  
- They lacked a clear view of key performance metrics to support quick decision-making.  
- It was hard to identify underperforming areas and understand business trends in real time.



---

## 🛠️ Tools Used
- **Power BI**
- **SQL** (Joins, Views, Filters)
- **DAX** (`USERELATIONSHIP()`, `RELATED()`)
- **Data Modeling** (Star Schema)

---

## 🔄 Process Overview

### 1. **Data Source**
- Used a public dataset from **Kaggle** containing sales transactions, product details, and regional information.

### 2. **Data Cleaning (SQL)**
- Removed nulls, duplicates, and standardized values.
- Joined multiple tables to create a unified sales view.


-- Remove rows with null Customer_ID
``SELECT * FROM sales_data
WHERE Customer_ID IS NOT NULL;``

-- Remove duplicate rows
`SELECT DISTINCT * FROM sales_data;`

-- Standardize Product Category names
`SELECT Product_ID,UPPER(TRIM(Product_Category)) AS Clean_Category
FROM product_data;`

-- Join Sales with Product and Region tables
`SELECT 
    s.Sale_ID,
    s.Date,
    s.Product_ID,
    p.Product_Name,
    r.Region_Name,
    s.Sales,
    s.Profit
FROM sales_data s
JOIN product_data p ON s.Product_ID = p.Product_ID
JOIN region_data r ON s.Region_ID = r.Region_ID;`

3. **Data Modeling**  
   - Built a star schema with one fact table and multiple dimension tables in Power BI.

4. **DAX Calculations**  
   - Created KPIs: Total Sales, Profit, GM%, YoY Growth using DAX.
   - Used `USERELATIONSHIP()` and `RELATED()` for time intelligence and lookup calculations.

5. **Dashboard Features**  
   - Slicers for Region, Category, Year
   - KPI Cards, Trend Charts, Category-wise performance
   - Drill-down visuals for detailed analysis

## Solution

- Built a Power BI dashboard using a sample retail dataset from Kaggle.  
- Cleaned and prepared the data using SQL to remove duplicates and fix inconsistencies.  
- Designed a star schema model to connect sales, products, regions, and time data efficiently.  
- Created key metrics like Total Sales, Profit, GM%, and YoY Growth using DAX formulas.  
- Added interactive filters for Region, Category, and Year to make the dashboard easy to explore.  
- Included visuals like KPI cards, trend charts, and drill-downs to help identify business insights quickly.




