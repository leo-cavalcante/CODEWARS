# **6KYU** - SQL Basics: Simple JOIN and RANK
```sql
SELECT
  p.id,
  p.name,
  COUNT(s.id) AS sale_count,
  RANK() OVER (ORDER BY COUNT(s.id) desc) AS sale_rank
FROM people p
JOIN sales s
ON p.id = s.people_id
GROUP BY 
  p.id,
  p.name
```