# 🎯 Percentile Calculations in Power BI

## 🧠 Overview

This report implements **salary percentile logic** across an employee dataset. Using DAX, it calculates each individual's **overall percentile**, **occupation-level percentile**, and **salary rank** within their occupation.

Useful for salary benchmarking, performance distribution, and comparative workforce analysis.

---

## 📈 Measures Explained

### 1. 🧮 `EMPLOYEE COUNT`
Total employees per occupation (ignores all other filters):

```DAX
EMPLOYEE COUNT = 
CALCULATE(
    COUNTROWS(Data),
    ALLEXCEPT(Data, Data[Occupation])
)


2. 🔢 RANK SALARY
Ranks employees by salary within the same occupation:

DAX
Copy
Edit
RANK SALARY = 
RANKX(
    FILTER(ALL(Data), Data[Occupation] = MAX(Data[Occupation])),
    CALCULATE(SUM(Data[Salary])),
    ,
    ASC,
    Dense
)
3. 🌍 OverAllPercentile
Employee percentile across all occupations:

DAX
Copy
Edit
OverAllPercentile = 
VAR CurrentSalary = SELECTEDVALUE(Data[Salary])
RETURN
IF(
    HASONEVALUE(Data[Id No]),
    COALESCE(
        DIVIDE(
            CALCULATE(
                COUNTROWS(Data),
                FILTER(
                    ALL(Data),
                    Data[Salary] < CurrentSalary)
            ),
            CALCULATE(COUNTROWS(Data), ALL(Data))
        ),
        0
    )
)
4. 👥 OCCUPATION PERCENTILE
Employee percentile within their own occupation:

DAX
Copy
Edit
OCCUPATION PERCENTILE = 
VAR CurrentSalary = SELECTEDVALUE(Data[Salary])
RETURN
IF(
    HASONEVALUE(Data[Id No]),
    COALESCE(
        DIVIDE(
            CALCULATE(
                COUNTROWS(Data),
                FILTER(
                    ALLEXCEPT(Data, Data[Occupation]),
                    Data[Salary] < CurrentSalary)
            ),
            CALCULATE(
                COUNTROWS(Data),
                ALLEXCEPT(Data, Data[Occupation])
            )
        ),
        0
    )
)
📊 Use Case
📉 Salary distribution dashboards

👥 Team-level percentile tracking

🎓 Student or performance percentile mapping

📂 File Included
PercentileCalc.pbix — Power BI file with visuals and all four measures implemented

🙌 Credit
https://www.youtube.com/@GoodlyChandeep/videos
