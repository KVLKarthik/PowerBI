# ⬅️ Refer to Previous Row using Power Query

## 🧠 Overview
This model demonstrates how to retrieve a **previous row’s value** in Power Query (M language) using index-based logic and a self-merge.

---

## 🪜 Steps
1. Added an Index column to the data
2. Duplicated the base table and shifted Index by -1
3. Merged the tables using `Index = IndexPrev + 1`
4. Expanded the column to bring in the previous value

---

## 📁 Files
- `PreviousRow.pbix` — Includes both DUMMY DATA and logic to fetch previous row values

---

## 📚 Reference  
Tutorial structure based on standard M techniques for row-wise logic
https://www.youtube.com/@GoodlyChandeep/videos
