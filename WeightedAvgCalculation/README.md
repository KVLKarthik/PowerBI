# ⚖️ Weighted Average Metrics in Power BI

## 📌 Overview
This Power BI report demonstrates **two types of weighted average calculations**—by month and by product—using DAX measures. These measures are especially useful when aggregating values like revenue, KPIs, or rates in proportion to their total share.

---

## 🧠 DAX Measures Explained

### 1. WA MONTHLY
Calculates a **weighted average across months**, based on total sales for each month relative to the annual sales.

```dax
WA MONTHLY = 
VAR ANNUALSALES = 
    CALCULATE([Total Sales], ALL('Calendar'[Month], 'Calendar'[Index]))

VAR MONTLYTABLE = 
    ADDCOLUMNS(
        SUMMARIZE(Sales, 'Calendar'[Year], 'Calendar'[Month]),
        "MONTHLYSALES", [Total Sales],
        "WT", [Total Sales] / ANNUALSALES
    )

RETURN SUMX(MONTLYTABLE, [WT] * [MONTHLYSALES])


### PRODUCT SALES WA = 
VAR ANNUALSALES = 
    CALCULATE([Total Sales], ALL(Products[Product Code], Products[Product]))

VAR SUMMMARISEDTABLE = 
    ADDCOLUMNS(
        SUMMARIZE(Sales, Products[Product], 'Calendar'[Year]),
        "SALESWT", [Total Sales] / ANNUALSALES,
        "MONTHLYSALES", [Total Sales]
    )

RETURN SUMX(SUMMMARISEDTABLE, [SALESWT] * [MONTHLYSALES])
