
## PERFORMANCE ANALYSIS

# 📊 SQL Query and Output: Yearly Average Price Comparison

## 💻 SQL Code

```sql
WITH yearly_prices AS (
    SELECT 
        strftime('%Y', "Host Since") AS host_year,
        AVG(Price) AS avg_price
    FROM airbnb
    WHERE "Host Since" IS NOT NULL AND Price IS NOT NULL
    GROUP BY host_year
)
SELECT 
    curr.host_year AS current_year,
    curr.avg_price AS current_avg_price,
    prev.avg_price AS previous_avg_price,
    (curr.avg_price - prev.avg_price) AS price_diff,
    ROUND(((curr.avg_price - prev.avg_price) * 100.0) / prev.avg_price, 2) AS percent_change
FROM yearly_prices curr
JOIN yearly_prices prev
    ON CAST(curr.host_year AS INTEGER) = CAST(prev.host_year AS INTEGER) + 1
ORDER BY curr.host_year DESC
LIMIT 1;
```

---

## 📈 Query Output (Sample)

| current_year | current_avg_price | previous_avg_price | price_diff | percent_change |
|--------------|-------------------|--------------------|------------|----------------|
| 2024         | 1180.75           | 1102.30            | 78.45      | 7.12           |

---

## 📎 Notes
- This query calculates the average Airbnb listing price per year.
- It compares the latest year with the previous one, showing the absolute difference and percent change.
- Useful for identifying year-over-year trends in listing prices.
