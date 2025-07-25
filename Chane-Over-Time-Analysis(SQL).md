
##  CHANGE OVER TIME ANALYSIS

# 📊 SQL Query and Output: Yearly Average Price Trend

## 💻 SQL Code

```sql
SELECT 
    strftime('%Y', "Host Since") AS host_year,
    AVG(Price) AS avg_price
FROM airbnb
WHERE "Host Since" IS NOT NULL AND Price IS NOT NULL
GROUP BY host_year
ORDER BY host_year;
```

---

## 📈 Query Output (Sample)

| host_year | avg_price |
|-----------|-----------|
| 2018      | 920.50    |
| 2019      | 975.30    |
| 2020      | 890.45    |
| 2021      | 1030.10   |
| 2022      | 1115.25   |
| 2023      | 1102.30   |
| 2024      | 1180.75   |

---

## 📎 Notes
- This query calculates the average Airbnb listing price for each year since hosts joined the platform.
- The data is grouped by the year extracted from the "Host Since" column.
- This output helps visualize trends in pricing over time.
