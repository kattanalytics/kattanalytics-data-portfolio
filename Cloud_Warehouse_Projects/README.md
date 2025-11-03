# Cloud Warehouse Projects (Snowflake + Azure Integration)  
Author : Kathryn Starkey

## Overview

This project demonstrates how I use Snowflake and Azure Blob Storage together to design and manage cloud-based data workflows.
It showcases my ability to stage, load, query, and analyze data in a scalable cloud environment — supporting the type of data quality and monitoring responsibilities essential in a Data Support or Data Engineering role.

The dataset used is the Superstore Sales dataset, loaded into Snowflake and queried for business insights such as profitability, regional performance, and customer trends.  

---

## Objectives

- Load and manage data in Snowflake using cloud-based storage.
- Create and validate staging areas for raw data using Azure Blob Storage.
- Perform SQL-based analytics on warehouse data.
- Visualize and prepare the data for Power BI reporting integration.

---

## Tools & Technologies
| Category | Tools |
|-----------|-------|
| Data Warehouse | Snowflake |
| Cloud Storage |	Azure Blob |
| Querying | SQL |
| Visualization |	Power BI |
| Version Control |	GitHub |

## Data Workflow
1. Azure Staging
  - Created a Blob Container in Azure Storage.
  - Uploaded the SampleSuperstore.csv dataset.
  - Generated a SAS Token to securely connect Snowflake to Azure Blob.
2. Snowflake Integration
  - Configured an external stage in Snowflake to pull data from Azure Blob.
  - Loaded the staged file into a Snowflake table (SUPERSTORE_RAW).
  - Verified successful data ingestion through row counts and sampling queries.
3. Querying & Analysis
  - Used SQL within Snowflake to aggregate and analyze sales performance, profit distribution, and growth trends.
4. Validation & Monitoring
  - Checked data integrity between source and Snowflake table.
  - Monitored query performance and cost optimization options.



## SQL Analysis Highlights

1.  Total Sales and Profit by Region
```sql
SELECT Region, 
       SUM(Sales) AS total_sales, 
       SUM(Profit) AS total_profit
FROM PORTFOLIO_DB.PUBLIC.SALES_SUPERSTORE
GROUP BY Region
ORDER BY total_sales DESC;
```
[View Result](results/total_sales_and_profit_by_region_p_db.csv)

---

2. Top 10 Customers by Profit
  ```sql
SELECT 
    CUSTOMER_NAME,
    ROUND(SUM(PROFIT), 2) AS TOTAL_PROFIT
FROM SUPERSTORE_RAW
GROUP BY CUSTOMER_NAME
ORDER BY TOTAL_PROFIT DESC
LIMIT 10;
```

 📌 Highlights ranking logic and customer-level profitability.

[View Result](results/top_10_customers_by_profit_ss_a.csv)

---

3. Year-Over-Year Sales Growth
  ```sql
  SELECT 
    YEAR(ORDER_DATE) AS YEAR,
    ROUND(SUM(SALES), 2) AS TOTAL_SALES,
    ROUND(
        (SUM(SALES) - LAG(SUM(SALES)) OVER (ORDER BY YEAR(ORDER_DATE))) 
        / NULLIF(LAG(SUM(SALES)) OVER (ORDER BY YEAR(ORDER_DATE)), 0) * 100, 
        2
    ) AS YOY_GROWTH_PERCENT
  FROM SUPERSTORE_RAW
  GROUP BY YEAR(ORDER_DATE)
  ORDER BY YEAR;
  ```

  📌 Applies window functions and lag logic for time-series growth analysis.

[View Result](results/year_over_year_sales_growth_ss_a.csv)

---

4. Most Profitable Product in Each Category
```sql
SELECT CATEGORY,
       PRODUCT_NAME,
       SUM(PROFIT) AS TOTAL_PROFIT
FROM PORTFOLIO_DB.PUBLIC.SALES_SUPERSTORE
GROUP BY CATEGORY, PRODUCT_NAME
QUALIFY ROW_NUMBER() OVER (PARTITION BY CATEGORY ORDER BY SUM(PROFIT) DESC) = 1
ORDER BY TOTAL_PROFIT DESC;
```

📌 Uses window partitioning and ranking to isolate top performers. 

[View Result](profitability_by_category_plus_product_level_p_db.csv)

---

5. Regional Contribution to Total Sales
  ```sql
SELECT 
    REGION,
    ROUND(SUM(SALES), 2) AS TOTAL_SALES,
    ROUND(
        SUM(SALES) / SUM(SUM(SALES)) OVER () * 100, 
        2
    ) AS PERCENT_OF_TOTAL
FROM SUPERSTORE_RAW
GROUP BY REGION
ORDER BY TOTAL_SALES DESC;
```

 📌 Which region drives revenue? This is common in BI dashboards

[View Result](results/regional_contribution_to_total_sales_ss_a.csv)

---

## Project Structure  
Cloud_Warehouse_Projects/
│
├── queries/       # Snowflake SQL scripts
├── results/       # Query outputs and screenshots
└── README.md      # Project documentation

---

## Key Takeaways
- Hands-on experience with cloud data loading and validation.
- Strong understanding of Snowflake integration with Azure.
- Demonstrates SQL proficiency using window, date, and ranking functions.
- Builds foundation for automated data pipelines and Power BI connectivity.

---

Author: Kathryn Starkey   
📧 kathrynstarkey.data@gmail.com   
🌐 GitHub Portfolio

---
