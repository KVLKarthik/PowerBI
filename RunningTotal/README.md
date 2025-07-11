# 📊 Running Total in Power BI

## 🧠 Overview
This report demonstrates how to create a **running total** of sales over time using DAX. It's useful for tracking cumulative values across dates, months, or years in line graphs or KPIs.

---

## 🔍 DAX Measure
```dax
Running Total = 
CALCULATE(
    [Total Sales],
    FILTER(
        ALLSELECTED('Date'),
        'Date'[Date] <= MAX('Date'[Date])
    )
)
