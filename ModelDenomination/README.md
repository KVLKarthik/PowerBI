# 💰 Model Denomination in Power BI

## 🧠 Overview

This Power BI report demonstrates how to **dynamically scale key financial metrics** (like Selling Price, COGS, and Profit) using a slicer-driven **denomination model** — toggling between Units, Thousands, and Millions.

---

## 🔧 How It Works

- A **'DENOM TABLE'** was created with values:
  - `1` → Units  
  - `1000` → Thousands  
  - `1000000` → Millions  

- A slicer allows users to choose the denomination, which affects all key metrics.

- **Sample DAX used for dynamic scaling:**

```DAX
SELLING PRICE = 
CALCULATE(
    SUMX(Sales, Sales[Units] * Sales[Price])
) / 'DENOM TABLE'[DENOM]

## 📚 Source

Concept built from basics in the [Goodly Chandeep](https://www.youtube.com/@GoodlyChandeep/videos) tutorial series on DAX fundamentals.

