# Dynamic Measure Selection using Slicer (Power BI)

This example shows how to **switch between multiple measures dynamically using a slicer** in Power BI with DAX.

---

## ✅ Steps:

1. Created a **Date Table** (Start → End) with Month, Quarter, Year, and index.
2. Built a **Measures Table**:

   * Total Sales
   * Total Units
   * Total Transactions
   * Unique Selling Points
3. Added a **Slicer Table** for user selection.
4. Created two DAX measures:

   ```DAX
   UserSelection = SELECTEDVALUE('SlicerTable'[Measure Name])

   CalculationMeasure =
   SWITCH(
     [UserSelection],
     "Total Sales", [Total Sales],
     "Total Units", [Total Units],
     "Total Transactions", [Total Transactions],
     "Unique Selling Points", [Unique Selling Points]
   )
   ```


📌 Credit
Inspired by https://www.youtube.com/watch?v=c0mPvzkf6i0&list=PLr7RyN24TvNYzETX26HxTzzLr2qMH-iT9&index=9
