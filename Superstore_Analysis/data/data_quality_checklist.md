# 🧾 Data Quality Checklist Template

**Project Name:**  
**Dataset Name:**  
**Date Reviewed:**  
**Reviewed By:**  

---

## 🗂️ Data Source Overview

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Source identified | Dataset origin documented (e.g., SQL DB, Excel export, API, etc.) | ☐ | |
| Data owner known | Contact or department identified | ☐ | |
| Purpose clarified | Business or analytical goal of dataset understood | ☐ | |
| Update frequency | Known schedule for refresh or new data | ☐ | |

---

## 🧱 Structure and Schema

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Columns correctly labeled | Names are consistent and meaningful | ☐ | |
| Data types verified | Numeric, date, text, boolean as expected | ☐ | |
| Record count logged | Initial row count recorded | ☐ | |
| Keys identified | Unique ID or composite key verified | ☐ | |

---

## 🚫 Missing or Invalid Data

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Missing values checked | NULLs, blanks, “N/A”, or placeholder text reviewed | ☐ | |
| Replacement plan created | Strategy for missing values (impute, drop, flag) | ☐ | |
| Required fields complete | Critical fields (IDs, dates) are filled | ☐ | |

---

## 🔁 Duplicates

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Duplicates checked | Based on key columns | ☐ | |
| Duplicates resolved | Retained or removed appropriately | ☐ | |

---

## 📏 Range and Format Validation

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Numeric values valid | No negatives where not expected | ☐ | |
| Dates valid | No impossible or future dates | ☐ | |
| Categorical values consistent | Standardized codes and spelling | ☐ | |

---

## 🎯 Accuracy Cross-Check

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Totals or aggregates verified | Sample sums match reference reports | ☐ | |
| Spot-checked records valid | Compared against external or trusted sources | ☐ | |

---

## ⏱️ Timeliness

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Data recency confirmed | Dates within acceptable timeframe | ☐ | |
| Update lag acceptable | Time delay between collection and availability noted | ☐ | |

---

## 🧾 Documentation

| Checkpoint | Description | Status | Notes |
|-------------|-------------|--------|-------|
| Cleaning steps logged | All modifications clearly described | ☐ | |
| Data assumptions stated | Documented any known limitations | ☐ | |
| Version tracked | Version number or timestamp of dataset recorded | ☐ | |

---

### ✅ Final Review Summary

**Data ready for analysis:** ☐ Yes ☐ No  
**Issues remaining:**  

---

