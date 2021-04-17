# **4KYU** - Calculating Month-Over-Month Percentage Growth Rate
```sql
WITH months_table AS
  (SELECT
    TO_CHAR(created_at, 'YYYY-MM-01')::DATE AS date,
    count(id) AS count,
    LAG(COUNT(id),1) OVER (ORDER BY TO_CHAR(created_at, 'YYYY-MM-01')::DATE) AS previous_month
  FROM posts
  GROUP BY date
  ORDER BY date)
  
SELECT
  date,
  count,
  TRIM(TO_CHAR(((count-previous_month)::float/previous_month)*100, '990D9%')) AS percent_growth
FROM months_table
```