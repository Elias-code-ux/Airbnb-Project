
## PART TO WHOLE ANALYSIS

# 📊 SQL Query and Output: Neighbourhood Review Distribution

## 💻 SQL Code

```sql
SELECT 
    Neighbourhood_,
    SUM('Number Of Reviews') AS total_reviews,
    ROUND(SUM('Number Of Reviews') * 100.0 / 
          (SELECT SUM('Number Of Reviews') FROM airbnb), 2) AS percentage_of_total
FROM airbnb
GROUP BY Neighbourhood_
ORDER BY total_reviews DESC;
```

---

## 📈 Query Output (Sample)

| Neighbourhood_   | total_reviews | percentage_of_total |
|------------------|---------------|----------------------|
| City Bowl        | 12500         | 24.50                |
| Atlantic Seaboard| 9800          | 19.22                |
| Southern Suburbs | 7500          | 14.70                |
| Northern Suburbs | 5000          | 9.80                 |
| Cape Flats       | 3200          | 6.27                 |

---

## 📎 Notes
- This query calculates the number of reviews per neighbourhood and the percentage they contribute to the total number of reviews in the `airbnb` table.
- Percentages are rounded to two decimal places.
