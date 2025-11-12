# 📚 Data Dictionary Template

**Project Name:**  
**Dataset Name:**  
**Date Created:**  
**Last Updated:**  
**Reviewed By:**  

---

## 🧾 Dataset Overview

| Field | Description |
|--------|-------------|
| Data Source | (e.g., Superstore Sales Database, API, Public Dataset, etc.) |
| Number of Records |  |
| Number of Columns |  |
| Data Refresh Frequency | (e.g., Daily, Monthly, Static) |
| Primary Key(s) | (Unique identifiers for records) |
| Related Tables / Datasets | (List any foreign key relationships or joins) |
| Notes | (General remarks about data quality or structure) |

---

## 🧱 Column Definitions

| Column Name | Data Type | Example Value | Description | Notes / Validation Rules |
|--------------|------------|----------------|--------------|----------------------------|
| `Order_ID` | Text / String | `CA-2018-152156` | Unique identifier for each order | Must be unique |
| `Order_Date` | Date | `2018-11-08` | Date when the order was placed | Should not be future-dated |
| `Customer_ID` | Text / String | `CG-12520` | Unique identifier for the customer | Must match ID in Customer table |
| `Sales` | Numeric / Float | `261.96` | Revenue from the order | Should be non-negative |
| `Discount` | Numeric / Float | `0.08` | Discount rate applied | Between 0 and 1 |
| `Profit` | Numeric / Float | `41.9136` | Profit per order | Can be negative if loss |
| `Region` | Text / String | `West` | Geographic sales region | One of {East, West, South, Central} |
| `Category` | Text / String | `Furniture` | Product category | Limited to known list |
| `Sub-Category` | Text / String | `Chairs` | Product sub-category | Must map to a valid category |
| `Quantity` | Integer | `2` | Number of items sold | Greater than 0 |

---

## ⚙️ Data Validation Rules (Optional)

| Validation Check | Description | Status | Notes |
|------------------|-------------|--------|-------|
| Primary Key Uniqueness | Each record has a unique key | ☐ | |
| Referential Integrity | Foreign keys match related tables | ☐ | |
| Data Type Consistency | All columns match expected types | ☐ | |
| Range / Boundary Conditions | Numeric and date fields within logical limits | ☐ | |
| Missing Values | No unexpected NULLs or blanks | ☐ | |
| Business Logic Validation | Metrics make sense (e.g., Profit = Sales - Cost) | ☐ | |

---

## 🗒️ Notes and Assumptions

- Example: All financial fields rounded to two decimal places.  
- Example: Historical data from before 2015 excluded due to format changes.  
- Example: Data joined from multiple sources—see `source_mapping.md` for lineage.  

---

