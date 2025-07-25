#  Cumulative Analysis

This report performs a cumulative price analysis using a window function to observe how prices accumulate as we go down the sorted list.

## SQL Query Used

```sql
SELECT 
    Neighbourhood,
    "Property Type" AS property_type,
    SUM(Price) AS total_price,
    SUM(SUM(Price)) OVER (
        ORDER BY SUM(Price) 
        ROWS BETWEEN UNBOUNDED PRECEDING AND CURRENT ROW
    ) AS cumulative_price
FROM airbnb
WHERE Price IS NOT NULL
GROUP BY Neighbourhood, "Property Type"
ORDER BY total_price;
```

## Output Table

| Neighbourhood   | property_type   |   total_price |   cumulative_price |
|:----------------|:----------------|--------------:|-------------------:|
| Suburbs         | Apartment       |            80 |                 80 |
| Downtown        | Apartment       |           100 |                180 |
| City Center     | House           |           200 |                380 |
| City Center     | Apartment       |           250 |                630 |
| Suburbs         | House           |           320 |                950 |
| Downtown        | Loft            |           430 |               1380 |
