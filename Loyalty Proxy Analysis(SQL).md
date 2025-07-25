# Retention or Loyalty Proxy: Repeat Host Behavior

This query tracks how long hosts have stayed on the platform and how many listings/reviews they have accumulated. It helps identify loyal hosts based on their activity.

## SQL Query Used

```sql
SELECT 
    "Host Id",
    MIN("Host Since") AS first_seen,
    COUNT(*) AS total_listings,
    SUM("Number Of Reviews") AS total_reviews
FROM airbnb
GROUP BY "Host Id"
ORDER BY total_reviews DESC
LIMIT 10;
```

## Output Table

|   Host Id | first_seen   |   total_listings |   total_reviews |
|----------:|:-------------|-----------------:|----------------:|
|         3 | 2017-10-10   |                2 |             160 |
|         6 | 2016-12-01   |                2 |             120 |
|         1 | 2018-01-01   |                2 |              80 |
|        10 | 2018-06-06   |                1 |              45 |
|         2 | 2019-05-15   |                1 |              40 |
|         8 | 2019-11-11   |                1 |              25 |
|         4 | 2020-03-20   |                1 |              20 |
|         9 | 2020-08-08   |                1 |              15 |
|         7 | 2022-01-01   |                1 |              10 |
|         5 | 2021-07-01   |                1 |               5 |


## Note

- The `MIN("Host Since")` finds the earliest date the host appeared.
- `COUNT(*)` counts total listings by the host.
- `SUM("Number Of Reviews")` shows total reviews across listings.
- This proxy helps track retention and loyalty behavior of hosts on the platform.
