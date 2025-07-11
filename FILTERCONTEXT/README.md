# 🔍 Filter Context in Power BI

## 🧠 Overview

This Power BI file illustrates how **Filter Context** operates within visuals. It helps understand how DAX measures like `Total Sales` return different results based on the current row/column filters in a visual — such as by **Month** and **Product Category**.

---

## 📊 What’s Inside

- Matrix visual with:
  - Rows: `Month`
  - Columns: `Product Category`
  - Values: `Total Sales` (measure)
- Totals calculated dynamically based on filter intersections

---

## 💡 Learning Purpose

- Understand how `CALCULATE` behaves under filter context
- Observe how context changes for totals vs individual cells
- Explore how slicers or other visuals can modify filter context dynamically

---

## 📂 File Included

- `FilterContext.pbix` — Power BI file with matrix visual to demonstrate filter context behavior

---

## 📚 Source

Concept built from basics in the [Goodly Chandeep](https://www.youtube.com/@GoodlyChandeep/videos) tutorial series on DAX fundamentals.
