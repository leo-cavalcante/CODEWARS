# **5KYU** - Calculating Running Total
```sql
SELECT 
  DATE(created_at) AS date,
  COUNT(id)::int AS count,
  (SUM(COUNT(id)) OVER (ORDER BY DATE(created_at)))::int AS total
FROM posts
GROUP BY date
ORDER BY date ASC
```